# 📄 BaseBuzz Whitepaper

## Abstract

BaseBuzz is a decentralized social protocol on the Base network that transforms meme culture into a financial and reputational economy. It enables users to post, mint, and trade meme content in real-time, where every interaction is onchain and tied to gamified, tokenized mechanics.

<p align="center">
  <img src="./docs/line-diagram-basebuzz-core.svg" alt="BaseBuzz Protocol Flow Diagram" width="600" />
</p>

---

## Purpose

BaseBuzz aims to:

- Reward attention and creativity through speculative token mechanics
- Create an open, censorship-resistant meme exchange
- Enable reputation-based discovery and monetization
- Integrate seamlessly with Web3 identity, marketplaces, and tokenomics
- Provide high protocol survivability through zero admin, burned keys, and no external dependencies

---

## Why Base?

- 🟦 Fast and low-cost L2 with strong Coinbase backing
- 📈 Surging adoption from normies, builders, and retail wallets
- 🔐 Better regulatory alignment than other chains
- 🛠 Tools like Aerodrome, BaseScan, and Farcaster already thriving

**BaseBuzz lives on Base because it’s the most normie-ready and infra-friendly chain in crypto.**

> Base is where crypto becomes culture.

---

## Normies vs Natives

BaseBuzz is designed to serve **both audiences**:

| Users       | Features Tailored For Them                                    |
| ----------- | ------------------------------------------------------------- |
| **Normies** | Dead-simple UI, no KYC, meme-posting flow, one-click mint     |
| **Natives** | Bonding curves, last-buy-wins, badge logic, wallet reputation |

Each layer is modular. Design-first UX makes normies feel safe. Protocol-first infra gives power to natives.

---

## Protocol Design

BaseBuzz consists of multiple core components:

### 1. Post Engine

- Submissions: Text, image, or video
- Storage: Supabase or IPFS, referenced by unique hash
- Optional minting: Triggered via UI or game mechanic

### 2. Mint Engine

- Mint Type: Zora-style ERC721 with embedded bonding curve
- Pricing Formula: `P(n) = a + b * n`
  - `P`: Mint price at mint `n`
  - `a`: Base price (set per campaign)
  - `b`: Slope (controls inflation)
- Royalties: Adjustable per mint, routed to creator wallet

### 3. Reputation Engine

- Scores: XP per interaction (mints, buys, posts, engagement)
- Sources: Onchain data (Alchemy RPC), in-app (Supabase logs)
- NFT Badges: Issued per tier (non-transferable)
- Multichain Indexing: Tracks wallets across 9 chains

### 4. FOMO Mechanics

BaseBuzz uses FOMO to encourage active participation and speculation:

- **Last Buy Wins**: If no one buys in X mins, the last buyer earns a reward
- **Flash Mint**: Short discount windows triggered by random activity
- **Mystery Mint**: Hidden bonuses for random mints (e.g. extra BUZZ or NFT drop)
- **Streak Bonuses**: Users who mint multiple memes in a row unlock XP boosts

Mathematically:

- Let `T_last` be the timestamp of last buy
- Let `Δt` be time since last buy
- Reward triggers if `Δt >= FOMO_TIMEOUT`
- Reward value: `R = reward_pool * (w / W)` where:
  - `w`: winner’s XP
  - `W`: total XP of eligible participants

### 5. Marketplace Integration

- All minted posts are tradable on Base-native NFT marketplaces
- Aggregator: Feed into NFT APIs (Reservoir, Zora, LooksRare)
- Metadata standard: ERC721 + embedded BUZZ ranking + mint history
- Price heatmaps displayed in-app via charting modules

---

## Gameification & Loyalty

BaseBuzz layers gamification on top of protocol mechanics:

- **Achievements**: Based on mints, streaks, rep, leaderboard ranking
- **Streaks**: Continuous daily activity unlocks boosts
- **Quests**: Seasonal or event-based tasks (e.g. mint 5 viral memes)
- **Loot Drops**: Random airdrops for highly active wallets
- **Leaderboards**: Tied to reputation and FOMO wins

### Game XP Formula:

Let `XP = aE + bM + cS + dR`

- `E`: Engagement actions (likes, replies, reposts)
- `M`: Meme mints
- `S`: Streak days
- `R`: Reputation level
- `a, b, c, d`: Adjustable weights

---

## Regulatory Model

BaseBuzz is designed to minimize regulatory risk:

- **Fixed supply token** ($BUZZ), no inflation
- **No custodial services** — users always hold assets
- **Open-source smart contracts** — keys burned on deployment
- **Marketplace and reward systems** are voluntary and user-triggered
- **BUZZ token** has utility (access, upgrades, reputation), not dividends or profit-sharing

KYC is not required for participation, as the protocol operates permissionlessly. Rewards are distributed automatically via smart contract logic based on wallet behavior.

---

## Governance

- DAO planned after user adoption threshold (e.g. 10,000 wallets)
- Proposals will cover:
  - XP weighting
  - Mint price curve parameters
  - FOMO timer durations
  - Badge criteria
- $BUZZ will be the governance token

---

## Developer API & Infrastructure Focus

BaseBuzz is a protocol-first platform. Its goal is to empower the community to:

- Build custom meme marketplaces
- Create niche forks (e.g., music memes, AI mints, reputation games)
- Extend post types with custom metadata
- Run off-chain or ZK reputation proofs

### API Targets:

- Post/mint metadata fetch
- Wallet rep scoring
- Badge + leaderboard indexing
- Mint stream subscriptions (SSE/WebSocket)

Success for BaseBuzz means spawning **hundreds of apps** using the protocol. DIY layers are a feature, not a bug.

---

## Future Roadmap

- **Reputation Marketplace**: Trade rep-based NFTs for whitelist access
- **AI-Meme Generator**: Trigger meme creation on reply with prompt
- **Onchain Feed Oracle**: Open protocol for app builders to read meme stats
- **ZK Reputation Proofs**: Allow wallets to prove rep level without doxing full wallet
- **Bridge to Farcaster**: Allow BaseBuzz mints from social posts

---

> BaseBuzz is not a platform. It’s a protocol for attention markets — built on DeFi principles, wrapped in memes, and designed for high survivability.
