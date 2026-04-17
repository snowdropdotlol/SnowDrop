# Architecture Decision Record and C4 Model

## Status

Accepted

## Context

SnowDrop requires a decentralized, automated pipeline to handle thousands of token transfers across Solana without requiring the initiator to hold or spend SOL for gas. We require high throughput, sybil resistance, and a specialized liquidation engine to cover operational costs autonomously.

## Decision

We utilize a Node.js/Bun distributed microservice model integrating Helius for RPCs, Jupiter for liquidity staging, and our Frost Oracle for AI-scored wallet targeting.

## Container Diagram

```mermaid
C4Container
    title Container Diagram for SnowDrop Automated Distribution

    Person(developer, "Project Developer", "Initiates the token drop")
    Person(holder, "Snowcatcher", "Receives the dropped tokens")

    System_Boundary(snowdrop, "Blizzard Engine") {
        Container(frontend, "Frost Dashboard", "Next.JS, React", "Provides the user interface for tracking drops and stats")
        Container(vaultBot, "Vault Service", "Node.js (Bun)", "Monitors deposits securely and stages balances")
        Container(meltEngine, "Pricing & Liquidation Engine", "Node.js", "Triggers the 2.5% token-to-SOL conversion")
        Container(distroEngine, "Distribution Engine", "Rust/Node", "Handles high-throughput batched multi-send transactions")
        ContainerDb(database, "Database", "PostgreSQL", "Stores Frost Scores, historical drops, and tier mappings")
    }

    System_Ext(jupiter, "Jupiter API", "On-chain Solana liquidations")
    System_Ext(helius, "Helius RPC", "Network state and webhooks")
    System_Ext(oracle, "Frost Oracle API", "External artificial intelligence wallet scoring")

    Rel(developer, frontend, "Connects wallet and configures drop")
    Rel(frontend, vaultBot, "Submits drop parameters")
    Rel(vaultBot, helius, "Listens to on-chain vault txs")
    Rel(vaultBot, meltEngine, "Schedules liquidation")
    Rel(meltEngine, jupiter, "Executes token-to-SOL swaps")
    Rel(distroEngine, oracle, "Requests wallet sybil checks/scans")
    Rel(distroEngine, helius, "Broadcasts batched distribution TXs")
    Rel(distroEngine, database, "Records transaction status")
    Rel(database, frontend, "Provides leaderboard and stream data")
    Rel(distroEngine, holder, "Delivers tokens", "Solana Network")
```

## Containers Details

### Frost Dashboard

- **Type**: Web Application
- **Technology**: Next.js, Vercel
- **Description**: Displays the total SOL volume distributed, projects frosted, and personal Frost Scores.

### Vault Service

- **Type**: Background Job Queue
- **Technology**: Bun / Node.js
- **Description**: Secure memory space for indexing inbound SPL tokens before distribution. Limits access based on authorization keys.

### Pricing & Liquidation Engine (The Melt)

- **Type**: Processing Service
- **Technology**: Node.js
- **Description**: The core differentiator. Takes 2.5% of any inbound token and queries Jupiter API for the optimal route to swap to SOL.

### Distribution Engine

- **Type**: Transaction Broadcaster
- **Technology**: Rust / Node.js
- **Description**: Processes thousands of wallet addresses, chunks them into viable Solana transaction limits, and signs them using the vault's derived SOL balance.
