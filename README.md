<div align="center">

# SNOWDROP ($SDROP)

**"Every token deserves a clean drop. Let it snow."**

Autonomous airdrop distribution infrastructure for Solana's Pump.fun ecosystem. We turn bundled supply into verified community airdrops — zero gas, zero trust issues.

[![App](https://img.shields.io/badge/App-snowdrop.lol-blue?style=for-the-badge)](https://snowdrop.lol)
[![Twitter](https://img.shields.io/badge/Twitter-@snowdropdotlol-1DA1F2?style=for-the-badge)](https://twitter.com/snowdropdotlol)
[![Docs](https://img.shields.io/badge/Docs-View_Documentation-green?style=for-the-badge)](./WHITEPAPER.md)
[![Chain](https://img.shields.io/badge/Chain-Solana-black?style=for-the-badge)](#)

</div>

## What is SnowDrop?

SnowDrop solves the fundamental issue of token generation launches: distributed supply without developer friction. By utilizing a self-funding swap mechanism (The Melt) and advanced AI-scored wallet targeting (via the Frost Oracle API), SnowDrop ensures that genuine, active wallets receive tokens without requiring the project deployer to pre-fund distribution gas.

### Core Mechanics

| Mechanic                             | Description                                                                                                                            |
| ------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------- |
| **Zero-Gas Distribution (The Melt)** | Auto-swaps 2.5% of deposited tokens to SOL via Jupiter to fund the network gas for bulk distribution.                                  |
| **Frost Score (AI Filter)**          | Utilizes the Frost Oracle API to score network wallets based on holding duration and cross-project activity, eliminating bot clusters. |
| **Sustainable Tokenomics**           | Fees are directed to a 20% SOL revenue share for holders and a 20% $SDROP buyback and burn standard.                                   |

### Token / Holder Tiers

| Tier         | Requirement  | Features                                                                    |
| ------------ | ------------ | --------------------------------------------------------------------------- |
| 🧊 **Flake** | 0.01% Supply | Eligible for basic SnowDrops, Basic Frost Dashboard access                  |
| ❄️ **Frost** | 0.1% Supply  | Flake features + 25% Fee discount on Drop submissions, Early-Alert tracking |
| 🌨️ **Storm** | 0.5% Supply  | Frost features + 20% Fee-Share Pool access, Premium API access              |
| 🏔️ **Peak**  | 1.0% Supply  | Storm features + Voting rights, Whitelabel Frosted badge issuance           |

## How It Works

```text
┌────────────────────────────────────────────────────────────────────────┐
│                    THE AUTO-DISTRIBUTION PIPELINE                      │
│                                                                        │
│   STEP 1: DEPOSIT & COMMIT (The Freeze)                                │
│   [Developer sends 10%-40% supply to Vault, verified from launch]      │
│              │                                                         │
│              ▼                                                         │
│   STEP 2: THE MELT (Self-Funding Gas)                                  │
│   [Auto-liquidates 2.5% of deposited tokens to SOL via Jupiter]        │
│              │                                                         │
│              ▼                                                         │
│   STEP 3: THE FROST SCORE (AI Filter)                                  │
│   [Integrates Frost Oracle to identify real users vs. bot clusters]    │
│              │                                                         │
│              ▼                                                         │
│   STEP 4: THE SNOWDROP (Distribution)                                  │
│   [Autonomous multi-send to scored wallets. Issues "Frosted" Badge]    │
│                                                                        │
└────────────────────────────────────────────────────────────────────────┘
```

## Architecture

```text
┌────────────────────────────────────────────────────────────────────────┐
│                    SYSTEM BACKEND ARCHITECTURE                         │
│                                                                        │
│   ┌─────────────┐      ┌─────────────┐      ┌─────────────┐          │
│   │  Vault Bot   │────▶ │  Pricing    │────▶ │  Jup Swap   │          │
│   │  (Monitor)   │      │  Engine     │      │  (The Melt) │          │
│   └─────────────┘      └─────────────┘      └─────────────┘          │
│          │                    │                    │                   │
│          ▼                    ▼                    ▼                   │
│   ┌─────────────┐      ┌─────────────┐      ┌─────────────┐          │
│   │ Frost Oracle│─────▶│  Distro     │─────▶│  Helius RPC │          │
│   │ (Score API) │      │  Engine     │      │  (Webhooks) │          │
│   └─────────────┘      └─────────────┘      └─────────────┘          │
│          │                                                            │
│          ▼                                                            │
│   ┌─────────────┐                                                     │
│   │  Database   │  ← Frost Scores, Drop history, Wallet DB           │
│   │  (Database) │                                                     │
│   └─────────────┘                                                     │
│                                                                        │
└────────────────────────────────────────────────────────────────────────┘
```

## Tech Stack

| Component           | Technology       | Rationale                                   |
| ------------------- | ---------------- | ------------------------------------------- |
| **Backend Runtime** | Node.js / Bun    | High performance asynchronous I/O           |
| **RPC & Indexing**  | Helius           | Reliable Solana webhooks and parsing        |
| **Database**        | Database         | Relational data integrity for user profiles |
| **Liquidation**     | Jupiter API      | Best route execution for The Melt phase     |
| **Scoring Engine**  | Frost Oracle API | External AI synergy for Sybil detection     |

## Phased Roadmap

| Phase             | Milestone      | Description                                                                                               |
| ----------------- | -------------- | --------------------------------------------------------------------------------------------------------- |
| **1. First Snow** | MVP Launch     | Token fair launch. Basic Blizzard Engine and Dashboard Alpha deployment.                                  |
| **2. The Storm**  | Revenue Engine | Activation of Frost Score targeting via Oracle. SOL fee-share processing, token buybacks, and bot alerts. |
| **3. Avalanche**  | B2B Scale      | Expansions to Base network, Raydium direct drops, Peak Tier DAO voting, and Launchpad B2B integrations.   |

## Reference Links

| Resource     | Link                                                           |
| ------------ | -------------------------------------------------------------- |
| Website      | [snowdrop.lol](https://snowdrop.lol)                           |
| GitHub       | [github.com/snowdropdotlol](https://github.com/snowdropdotlol) |
| Architecture | [ARCHITECTURE.md](./ARCHITECTURE.md)                           |
| Whitepaper   | [WHITEPAPER.md](./WHITEPAPER.md)                               |
| Security     | [SECURITY.md](./SECURITY.md)                                   |

<br>
<div align="center">
<sub><b>Disclaimer</b>: SnowDrop and the $SDROP token operate as utility software within the decentralized Solana ecosystem. Cryptocurrencies are volatile; use experimental DeFi infrastructure at your own risk. Every token deserves a clean drop. Let it snow.</sub>
</div>
