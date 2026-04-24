# SnowDrop API Reference

The SnowDrop API allows developers and high-tier $SDROP holders to programmatically interact with the Blizzard distribution engine and Frost AI scoring system.

## GET /api/v1/drops/status

Get the status of a specific token drop.

**Parameters:**
| Name | Type | Required | Description |
|------|------|----------|-------------|
| tokenAddress | string | Yes | The Solana address of the token being distributed |

**Response:**
- 200: Drop status object `{"status": "melting|distributing|completed", "progress": 85}`
- 404: Drop not found

## POST /api/v1/drops/commit

Initiate a new drop for a Pump.fun token.

**Parameters:**
| Name | Type | Required | Description |
|------|------|----------|-------------|
| tokenAddress | string | Yes | The token to drop |
| amount | number | Yes | Total amount deposited ($50 USD min) |
| signature | string | Yes | The transaction signature of the deposit |

**Response:**
- 201: Drop successfully queued for The Melt and distribution.
- 400: Invalid deposit or $50 minimum not met.

## GET /api/v1/frost/score

Get the Frost AI score for a specific wallet address. *(Requires Storm or Peak tier holding).*

**Parameters:**
| Name | Type | Required | Description |
|------|------|----------|-------------|
| walletAddress | string | Yes | The target Solana wallet address |

**Response:**
- 200: Frost Score object `{"score": 92, "sybilProbability": 0.01}`
- 403: Unauthorized (tier too low)
