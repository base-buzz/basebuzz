# 🧱 BaseBuzz Technical Architecture

## 🔧 Stack Overview

| Layer       | Stack / Tooling                                           |
| ----------- | --------------------------------------------------------- |
| Frontend    | Next.js (App Router), ShadCN UI, Tailwind CSS             |
| Wallet      | RainbowKit + Wagmi (v2), viem, Ethers                     |
| Backend API | Node.js (custom SIWE JWT flow), Supabase (Postgres + RLS) |
| Chain       | Base Mainnet (EVM-compatible, L2)                         |
| Indexing    | Alchemy RPC (multi-chain wallet activity across 9 chains) |
| Hosting     | Vercel (frontend), local runner (wallet rep indexer)      |

---

## 🔄 Core Modules

### 1. UI App (Private)

**Repo:** `base-buzz/ui` (private)

- Degen Mode: Meme feed, spin & mint games, FOMO meter
- Pro Mode: Advanced charting, trader dashboards, badge matrix
- Auth: RainbowKit + custom SIWE + Supabase user
- Theming: Tailwind + dark mode by default

### 2. Smart Contracts

**Repo:** [basebuzz-contracts](https://github.com/base-buzz/basebuzz-contracts)

- ERC20: $BUZZ fixed supply token (1B)
- ERC721: Meme NFT minting w/ bonding curve logic
- FOMO Contracts:
  - Last Buy Wins
  - Flash Mint Timer
  - Leaderboard payout

### 3. Supabase Backend

- Schema includes: `posts`, `badges`, `wallet_profiles`, `xp_events`
- RLS protects all sensitive reads/writes per authenticated wallet
- Webhooks connected to chain events via server-side MCP indexer

### 4. Wallet Reputation Indexer

- Local job runner (Node)
- Reads tx history via Alchemy RPC
- Weighs activity into XP categories:
  - Trades
  - Holds
  - Meme minting
  - Badge collection
  - On-chain reactions

### 5. Agent Layer (Bots)

- OpenAI-powered reply bots for meme posts
- Personalities set via traits (degen, wholesome, chaotic, AI-dev, etc)
- Responds only to public posts (never origin)
- Posts randomized to simulate organic interaction

---

## 📊 FOMO & Reward Logic

All game mechanics are **onchain + deterministic**:

### Last Buy Wins (LBW)

- Every buy resets timer `T_last`
- If `Δt > TIMEOUT`, previous buyer wins from reward pool
- Pool funded via minting % + random loot injections

### Flash Mint Windows

- Every `N` mints = opens a 5-minute 50% discount window
- Mints inside window are tracked and rank boosts granted

### Streak & Heat Mechanics

- Daily activity triggers XP bonuses
- Meme posts gain “heat” from:
  - Mints
  - Likes/replies
  - BUZZ-based reputation multiplier

### Badge Issuance Logic

- Triggered by wallet crossing XP threshold
- Non-transferrable NFT, image tiered by rank
- Stored onchain, pulled via Supabase mirror

---

## 🛠 Dev & Builder Infrastructure

- **Mint Feed API** – SSE stream for live mint events
- **Wallet Rank API** – Endpoint to fetch badge + rep by wallet
- **Post Metadata API** – JSON endpoint for meme post content
- **Webhooks** – Supabase triggers on insert/update for real-time events
- **Zora Compatibility** – All NFTs use standard ERC721 metadata

---

## 🎯 Infrastructure Philosophy

> BaseBuzz is not a consumer app — it’s an open protocol with a killer frontend.

- Apps can fork, remix, or plug in directly
- DIY meme markets, badge-based whitelists, and rep-powered games
- No admin keys, all contracts immutable

**Design Principles:**

- 🧩 Composable
- ⚙️ Modular
- 🏁 Fast
- 🧠 Minimal backend dependency
- 🔐 Everything signed, nothing assumed

---

> The BaseBuzz protocol is built for builders. We don’t own the memes. The chain does.
