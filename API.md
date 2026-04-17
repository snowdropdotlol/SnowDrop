# SnowDrop API Documentation

The SnowDrop API allows for interactions with the Blizzard Engine, orchestrating zero-gas distributions, and managing Frost Scores.

## Overview

**Base URL**: `https://api.snowdrop.lol/v1`  
**Authentication**: Bearer Token required for authenticated endpoints.

---

## 1. Distribution Engine

### POST /v1/distro/freeze

Initiates the deposit and commit phase for a new token drop.

**Description**: Registers a new targeted token for processing in the Vault. The protocol validates the token's origin, ensuring a minimum USD threshold for liquidation.

**Headers**:
- `Authorization`: Bearer `<api_key>`

**Parameters (JSON)**:
| Name | Type | Required | Description |
|------|------|----------|-------------|
| `token_address` | string | Yes | The SPL token address assigned |
| `drop_percentage` | number | Yes | Percentage of supply to drop (e.g., 20.0) |
| `authorized_wallet`| string | Yes | Developer wallet initiating the freeze |

**Response (200 OK)**:
```json
{
  "vault_address": "vAULTx...",
  "status": "AWAITING_DEPOSIT",
  "expected_melt_fee": "2.5%",
  "minimum_deposit_amount": "50_000_000"
}
```

---

## 2. Intelligence & Scoring

### GET /v1/oracle/frost-score

Retrieves the Frost Score of a specific Solana wallet address. Integrating the Frost Oracle API.

**Description**: Fetches the wallet's reliability metrics, filtering out sybil farms, analyzing hold duration, and evaluating cross-project activity.

**Parameters (Query)**:
| Name | Type | Required | Description |
|------|------|----------|-------------|
| `wallet` | string | Yes | The public key string of the user |
| `depth` | integer| No | The history depth to consider (default 30 days) |

**Response (200 OK)**:
```json
{
  "wallet": "7Hkj...K3",
  "frost_score": 98,
  "modifiers": {
    "diamond_hand": true,
    "sybil_cluster": false,
    "cross_project_txs": 42
  },
  "tier": "STORM"
}
```

---

## 3. Revenue & Dashboard

### GET /v1/stats/global

Fetches the overarching metrics for the SnowDrop project.

**Description**: Used to populate the Frost Dashboard with real-time volume and protocol participation.

**Response (200 OK)**:
```json
{
  "total_volume_sol": "1240500.00",
  "projects_frosted": 342,
  "live_snow_stream": [
    { "ticker": "UNC", "percentage": 30.0, "status": "FROSTED" },
    { "ticker": "XYZ", "percentage": null, "status": "MELTING" }
  ]
}
```

---

## Errors & Rate Limiting

The API operates under standard HTTP response codes.
- `400 Bad Request`: Validation failure on the SPL configuration.
- `401 Unauthorized`: API key is invalid or lacks Tier permission.
- `429 Too Many Requests`: Standard rate limit of 100 req/min for free tiers, 1000 req/min for STORM tier limits.
