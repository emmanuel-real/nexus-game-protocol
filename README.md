# Nexus Game Protocol

### Decentralized Gaming Framework for Bitcoin Layer 2 (Built on Stacks)


## Overview

The **Nexus Game Protocol** is a fully on-chain, decentralized gaming infrastructure designed for Bitcoin Layer 2 environments, powered by the Stacks blockchain. It leverages Bitcoin’s security and finality while offering powerful tools for developers to build, manage, and reward players in immersive, decentralized games.

This smart contract suite supports in-game assets (NFTs), avatars, world-building, experience leveling systems, leaderboards, and Bitcoin-denominated rewards.

Built to scale Web3 gaming, Nexus empowers true digital ownership and transparent incentive structures — laying the groundwork for the next evolution of trust-minimized gaming.

## Key Features

- **Game Asset NFTs:**  
  Mint and manage powerful, customizable NFTs representing in-game items.
  
- **Player Avatars:**  
  Each player owns a unique NFT avatar with experience points, levels, achievements, and asset loadouts.

- **World Creation:**  
  Developers can create and manage decentralized game worlds with custom entry requirements and reward pools.

- **Experience and Leveling System:**  
  Built-in progression system using experience points and levels, capped at **Level 100**.

- **Leaderboard Management:**  
  Maintain on-chain player rankings, scores, and track rewards distribution in a verifiable way.

- **Reward Distribution:**  
  Distribute Bitcoin-based rewards to top players automatically according to their leaderboard rank and performance.

- **Administrative Controls:**  
  Protocol admins can configure key settings like protocol fees, leaderboard size, and manage protocol upgrades.

- **Security and Validation:**  
  Extensive input validation and strict role-based access controls ensure robustness against invalid states and unauthorized actions.

- **Bitcoin Layer 2 Native:**  
  All interactions align with Stacks and Bitcoin final settlement models.

## Technical Specifications

### Error Constants

- Predefined detailed error codes for every major failure condition (e.g., unauthorized access, invalid input, reward errors).
- Example: `ERR-NOT-AUTHORIZED`, `ERR-INVALID-AVATAR`, `ERR-TRANSFER-FAILED`, etc.

### Game Mechanics Parameters

- **Max Level:** 100
- **Max Experience per Level:** 1000 XP
- **Base XP Requirement per Level:** 100 XP

### Core Data Structures

- **Non-Fungible Tokens (NFTs):**
  - `nexus-asset` — Game items with attributes like rarity, power level, world binding.
  - `nexus-avatar` — Unique player representations tied to achievements and worlds.

- **Maps (Stateful Storage):**
  - `nexus-asset-metadata`
  - `avatar-metadata`
  - `game-worlds`
  - `leaderboard`
  - `protocol-admin-whitelist`

### Validation Functions

- Strict format and range checking for names, descriptions, attributes, scores, power levels, etc.
- Enforces rarity types: `"common"`, `"uncommon"`, `"rare"`, `"epic"`, `"legendary"`.

### Administrative Configuration

- **Protocol Fee (Default 10):** Fee charged for game interactions.
- **Max Leaderboard Entries (Default 50):** Size of active player rankings.
- **Total Prize Pool:** Tracked for Bitcoin reward allocations.

## How It Works

### 1. Setup Protocol

An admin initializes the protocol by setting base fees and maximum leaderboard entries.

```clojure
(initialize-protocol (entry-fee uint) (max-entries uint))
```

### 2. Create Game World

Game developers create virtual worlds with customizable entry criteria and reward pools.

```clojure
(create-game-world (name (string-ascii 50)) (description (string-ascii 200)) (entry-requirement uint))
```

### 3. Mint Game Assets

Admins mint in-game assets as NFTs, which players can own, trade, and equip.

```clojure
(mint-nexus-asset (name) (description) (rarity) (power-level) (world-id) (attributes))
```

### 4. Create Player Avatars

Players create their unique avatars to interact with game worlds and assets.

```clojure
(create-avatar (name (string-ascii 50)) (world-access (list 10 uint)))
```

### 5. Experience Gain and Leveling

Players earn experience through gameplay, leveling up based on experience thresholds.

```clojure
(update-avatar-experience (avatar-id uint) (experience-gained uint))
```

### 6. Leaderboard and Score Management

Admins update player scores after tournaments or game events.

```clojure
(update-player-score (player principal) (new-score uint))
```

### 7. Reward Distribution

Top players are rewarded proportionally to their scores in Bitcoin (via Stacks BTC bridging).

```clojure
(distribute-bitcoin-rewards)
```

## Security Model

- **Admin-Only Operations:** Critical functions restricted to whitelisted protocol admins.
- **NFT Ownership Enforcement:** Only owners can transfer their assets.
- **Input Validation:** Mandatory validation on names, descriptions, attributes, scores, experience values, etc.
- **Leaderboard Protection:** Size-limited, with strict insertion/update rules to avoid leaderboard overflow.
- **Reward Safeguards:** Only valid and eligible players receive Bitcoin rewards.

## Requirements

- **Blockchain:** Stacks 2.1+
- **Language:** Clarity Smart Contract Language
- **Bitcoin Layer 2 Compatible:** Via Stacks integration

## Future Extensions

- **Multi-World Portals:** Allow avatars to travel between different games/worlds.
- **Asset Lending/Borrowing:** Enable peer-to-peer NFT rentals for games.
- **Dynamic NFT Assets:** Items that upgrade or change based on in-game events.
- **Tournament Framework:** On-chain competitive events with auto-generated brackets and reward pools.

## Contributions

We welcome contributions and suggestions!  
Please open an issue or submit a pull request with your ideas for improvement.

## Acknowledgements

Built on the foundations of:

- **Stacks Blockchain** — Smart contracts for Bitcoin
- **Clarity Language** — Predictable, decidable smart contract language
- **Bitcoin Security** — Final settlement anchoring

## Get ready to build the future of decentralized gaming — secured by Bitcoin
