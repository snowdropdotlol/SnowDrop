# Security & Threat Model

SnowDrop manages assets transitioning from a concentrated developer wallet to thousands of disparate wallets. Ensuring zero loss, data integrity, and pipeline safety is paramount.

## DevSecOps Context

- **Pipeline Integrity**: Zero trust validation across all internal microservices. The Melt Engine will only process commands originating from the Vault Service.
- **Supply Chain**: Minimal dependencies. Critical smart contract interactions occur directly via tested RPC nodes (Helius).

## Threat Model (STRIDE Application)

| Threat                     | Target              | Mitigation                                                                                                                        |
| -------------------------- | ------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| **Spoofing**               | Target Endpoint     | The Distributor must authenticate using zero-knowledge HMACs when querying the API to avoid injected fraudulent wallet addresses. |
| **Tampering**              | The Melt            | Slippage limits and path protections are hardcoded to avoid MEV sandwich attacks on the 2.5% liquidation swap.                    |
| **Repudiation**            | Deposit Flow        | Helius webhooks confirm on-chain finality before any status change reflects in the database.                                      |
| **Information Disclosure** | Competitor Analysis | Wallet score weights and precise sybil logic utilized by the Frost network remain heavily obfuscated.                             |
| **Denial of Service**      | API Endpoints       | Cloudflare shielding, API rate limiting via Database rules, separating premium Tier endpoints.                                    |
| **Elevation of Privilege** | Dashboard Admin     | Hard separation of UI databases from transactional cold-wallets.                                                                  |

## IDOR and Bypass Prevention

SnowDrop handles multi-tenant project launches.

- **Requirement:** User A cannot query or mutate the release parameters of User B's token drop.
- **Mitigation:** Every API call modifying drop configuration mandates a secondary cryptographic signature originating from the token's deployer wallet on Solana. Admin SDKs possess isolated boundary restrictions, explicitly blocking the overwriting of `authorized_wallet` parameters post-creation.

## Data Flow

- **Client -> UI**: HTTPS, wallet signatures.
- **UI -> API**: Bearer tokens, strict parameter sanitization.
- **API -> Oracle Engine**: Encrypted internal protocols, enforcing data classification boundaries.
- **Melt Engine -> Chain**: Signed transactions transmitted through private RPC endpoints to obscure them from public mempool frontrunners where possible.

## Contingency Planning

In the event of network congestion on Solana, the Distribution Engine implements a robust retry matrix with exponential backoff. Unspent SOL from "The Melt" is securely recycled or remitted according to protocol parameter rules.
