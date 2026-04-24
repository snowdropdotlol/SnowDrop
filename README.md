<div align="center">

# ❄️ SnowDrop

**Every token deserves a clean drop.**

Autonomous airdrop distribution infrastructure for Solana's Pump.fun ecosystem. We turn bundled supply into verified community airdrops — dev pays 1% total, community gets 99%.

[![Website](https://img.shields.io/badge/Website-snowdrops.lol-blue?style=flat-square)](https://snowdrops.lol)
[![Twitter](https://img.shields.io/badge/Twitter-@snowdropdotlol-1DA1F2?style=flat-square&logo=twitter&logoColor=white)](https://x.com/snowdropdotlol)
[![Chain](https://img.shields.io/badge/Chain-Solana-14F195?style=flat-square&logo=solana&logoColor=white)](#)
[![Version](https://img.shields.io/badge/Version-1.0.0-blue?style=flat-square)](#)

</div>

## What is SnowDrop?

SnowDrop ($SDROP) is an autonomous, self-funding distribution pipeline. Developers deposit their tokens, and the system automatically routes 99% to the top holders of that token. The remaining 1% covers gas entirely via a Jupiter swap and performs a tier-weighted buyback for $SDROP holders. Friction is absolute zero.

## The Blizzard Engine (Core Mechanics)

| Feature                   | Description                                                                                                      |
| ------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| **Zero-Gas Distribution** | 0.3% of the deposit is automatically swapped to SOL via Jupiter to cover all network fees. Developers pay 0 SOL. |
| **99% Payout**            | The remaining 99% is instantly distributed to the top 100 organic holders of the deposited token.                |
| **Frost AI Targeting**    | Built-in AI engine filters out sybil clusters and bot farms, ensuring drops only reach real diamond hands.       |
| **$SDROP Buyback**        | 0.7% of every deposit is bought back as $SDROP and dropped to existing $SDROP holders.                           |

## Holder Tiers

Hold $SDROP to unlock the Frost Dashboard and catch tier-weighted drops.

| Tier         | Holding | Features                                          |
| ------------ | ------- | ------------------------------------------------- |
| 🧊 **Flake** | 0.01%   | Eligible for tier-weighted drops, Basic Dashboard |
| ❄️ **Frost** | 0.1%    | Early Alerts (2m), 25% Fee discount               |
| 🌨️ **Storm** | 0.5%    | Higher drop weight, Frost AI Premium API          |
| 🏔️ **Peak**  | 1.0%    | Voting rights, Whitelabel Frosted badge           |

## How It Works

```text
┌────────────────────────────────────────────────────────────────────────┐
│                    THE AUTO-DISTRIBUTION PIPELINE                      │
│                                                                        │
│   STEP 1: THE FREEZE (Deposit)                                         │
│   Dev sends supply to Vault ($50 min value).                           │
│              │                                                         │
│              ▼                                                         │
│   STEP 2: THE MELT (Self-Funding)                                      │
│   0.3% swapped to SOL (Gas) | 0.7% swapped to $SDROP (Buyback)         │
│              │                                                         │
│              ▼                                                         │
│   STEP 3: FROST SCORE (Filter)                                         │
│   AI removes bots. Ranks top 100 diamond hands.                        │
│              │                                                         │
│              ▼                                                         │
│   STEP 4: THE SNOWDROP (Distribute)                                    │
│   99% drops to top holders. Buyback drops to $SDROP holders.           │
│                                                                        │
└────────────────────────────────────────────────────────────────────────┘
```

## Architecture

```text
┌────────────────────────────────────────────────────────────────────────┐
│   ┌─────────────┐      ┌─────────────┐      ┌─────────────┐          │
│   │  Vault Bot   │────▶ │  Pricing    │────▶ │  Jup Swap   │          │
│   └─────────────┘      └─────────────┘      └─────────────┘          │
│          │                                         │                   │
│          ▼                                         ▼                   │
│   ┌─────────────┐      ┌─────────────┐      ┌─────────────┐          │
│   │  Frost AI   │─────▶│  Distro     │─────▶│  Helius RPC │          │
│   └─────────────┘      └─────────────┘      └─────────────┘          │
│          │                                                            │
│          ▼                                                            │
│   ┌─────────────┐                                                     │
│   │  Database   │  ← Frost Scores, Drop history, Wallet metrics      │
│   └─────────────┘                                                     │
└────────────────────────────────────────────────────────────────────────┘
```

## Tech Stack

| Component      | Technology                  |
| -------------- | --------------------------- |
| **Frontend**   | React, Next.js, TailwindCSS |
| **Backend**    | Node.js, Bun                |
| **Database**   | PostgreSQL                  |
| **Blockchain** | Solana Mainnet, Helius RPC  |
| **Swaps**      | Jupiter API                 |

## Roadmap

1. **First Snow (Weeks 1-4):** $SDROP Fair Launch, MVP Blizzard Engine, Dashboard Alpha.
2. **The Storm (Months 2-3):** Frost AI Engine live, Telegram Bot alerts, advanced anti-sybil.
3. **Avalanche (Months 4-6):** Cross-platform support (Base, Raydium), DAO governance, SDK release.

---

<div align="center">
  <sub>Powered by Frost AI • <a href="https://snowdrops.lol">snowdrops.lol</a></sub>
</div>
