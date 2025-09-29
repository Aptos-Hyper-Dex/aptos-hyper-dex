> Homepage is English README. You can view the [简体中文](./README_ZH.md) versions.

# HyperPerp - Decentralized Perpetual Exchange on Aptos

## Project Name

**HyperPerp** - High-Performance Decentralized Perpetual Trading Platform

## Project Description

HyperPerp is a decentralized perpetual exchange built on the Aptos blockchain, featuring a hybrid architecture of **off-chain matching + on-chain settlement**. The project addresses trust issues in traditional centralized exchanges while achieving high-performance trading through an off-chain matching engine.

### Core Features
- **Perpetual Trading**: Support for perpetual contracts of mainstream assets like BTC, ETH (testnet)
- **Off-chain Matching Engine**: High-performance order matching system based on Rust
- **On-chain Fund Management**: Using Move smart contracts to ensure fund security
- **Risk Management System**: Including margin management
- **Modern Frontend**: Responsive trading interface based on Next.js

### Problems Solved
1. **Trust Issues**: Achieving decentralization through blockchain technology, with user funds managed by smart contracts
2. **Performance Issues**: Balancing security and performance through off-chain matching + on-chain settlement architecture
3. **User Experience**: Providing smooth trading experience similar to centralized exchanges
4. **Fund Security**: All fund operations executed on-chain, transparent and auditable

## Aptos Blockchain Integration

### Move Smart Contract Modules
The project fully leverages Aptos Move language features to build a complete perpetual contract system:

- **`perp_engine`**: Perpetual contract engine, handling batch settlement and trade execution
- **`vault_coin`**: Fund custody vault, using Aptos Coin standard to manage USDC
- **`positions`**: Position management module, tracking user long/short positions
- **`account`**: User account management, including collateral and unrealized PnL
- **`oracle_adapter`**: Price oracle adapter, supporting multiple price sources
- **`market_registry`**: Market parameter management, supporting dynamic addition of trading pairs
- **`liquidation`**: Liquidation mechanism, automatically handling risky positions
- **`events`**: Event system, recording all trades and state changes
- **`gov`**: Governance module, supporting multi-signature and permission management

### On-chain Interaction Features
- **Batch Settlement**: Efficient batch trade settlement through `apply_batch` function
- **Event Listening**: Real-time state updates using Aptos event system
- **Resource Management**: Using Move resource model to ensure fund security
- **Permission Control**: Fine-grained permission management based on Aptos account model

## Tech Stack

### Frontend Technology
- **Framework**: Next.js 14.2.3 + React 18
- **UI Library**: Radix UI + Tailwind CSS

### Backend Technology
- **Matching Engine**: Rust + Tokio async runtime
- **Database**: PostgreSQL + SQLx ORM
- **API Framework**: Axum Web framework
- **Cache**: Redis (optional)
- **Message Queue**: Tokio Channels

### Blockchain Technology
- **Smart Contracts**: Move language
- **Blockchain**: Aptos testnet
- **Development Tools**: Aptos CLI + Aptos SDK
- **Indexer**: Rust

## Installation and Running Guide

### Environment Requirements
- Node.js 18+ 
- Rust 1.75+
- PostgreSQL 14+
- Aptos CLI

### Quick Start

#### 1. Clone the Project
```bash
git clone https://github.com/your-username/aptos-hyper-dex.git
cd aptos-hyper-dex
```

#### 2. Deploy Smart Contracts
```bash
cd move/contracts/hyperperp
# Install dependencies
npm install

# Run tests
npm run test

# Deploy to testnet
./sh_scripts/deploy.sh
```

#### 3. Start Matching Engine
```bash
cd rust-matching-engine

# Install dependencies
cargo build --release

# Configure environment variables
cp .env.example .env
# Edit .env file

# Start database
docker-compose up -d postgres

# Run matching engine
cargo run
```

#### 4. Start Frontend Application
```bash
cd next-app

# Install dependencies
npm install

# Start development server
npm run dev
```

#### 5. Start Indexer (Optional)
```bash
# Rust version (recommended for production)
cd rust-indexer
cargo run --release

# TypeScript version (for development)
cd ts-indexer
npm start
```

### Detailed Configuration

#### Environment Variables Configuration
```bash
# Database configuration
DATABASE_URL=postgresql://username:password@localhost:5432/hyperperp

# Aptos configuration
APTOS_NODE_URL=https://fullnode.testnet.aptoslabs.com/v1
APTOS_ADMIN_ADDRESS=0x...
APTOS_CONTRACT_ADDRESS=0x...

# Server configuration
SERVER_HOST=127.0.0.1
SERVER_PORT=8080
```

#### Wallet Configuration
1. Log in to the exchange (Aptos-Hyper-dex)
2. Automatically connect to Aptos testnet
3. Get test tokens USDC by deploying [Mint-Cypto-Testnet](https://github.com/Aptos-Hyper-Dex/Mint-Cypto-Testnet).

## Project Highlights/Innovation Points

### 1. Hybrid Architecture Design
- **Off-chain Matching**: Achieving millisecond-level order matching, supporting high-concurrency trading
- **On-chain Settlement**: Ensuring fund security and immutable trades
- **Optimal Balance**: Balancing performance and decentralization features

### 2. High-Performance Matching Engine
- **In-memory Order Book**: Efficient order management based on BTreeMap
- **Price-Time Priority**: Standard exchange matching algorithm
- **Batch Settlement**: Reducing on-chain transaction fees and latency
- **Event-Driven**: Real-time trading status updates

### 3. Complete Risk Management System
- **Dynamic Margin**: Supporting differentiated margin requirements for different assets

### 4. Modern Development Experience
- **Type Safety**: End-to-end TypeScript support
- **Real-time Updates**: WebSocket connections for real-time data synchronization
- **Responsive Design**: Supporting desktop and mobile trading
- **Developer Friendly**: Complete test suite and documentation

### 5. Scalable Architecture
- **Modular Design**: Independent deployment and scaling of components
- **Multi-chain Support**: Architecture supports expansion to other blockchains
- **Plugin System**: Supporting custom order types and trading strategies

## Future Development Plans

### Short-term Goals
- **Automatic Liquidation**: Real-time monitoring of position risks, automatic liquidation triggering
- **Price Protection**: Preventing price manipulation and abnormal trades
- **Multi-layer Validation**: Multiple risk checks before, during, and after trades
- **Mainnet Deployment**: Complete Aptos mainnet deployment and audit
- **More Trading Pairs**: Support for mainstream assets like ETH, SOL
- **Mobile Application**: Develop native mobile trading application
- **API Openness**: Provide public API for third-party integration

### Medium-term Goals
- **Advanced Order Types**: Support for stop-loss, take-profit, iceberg orders, etc.
- **Social Trading**: Support for copy trading and strategy sharing
- **Institutional Services**: Provide institutional-grade trading and risk control tools

### Long-term Vision
- **Decentralized Governance**: Achieve completely decentralized protocol governance
- **Layer 2 Integration**: Support Aptos Layer 2 solutions
- **Derivatives Expansion**: Support more derivatives like options, futures
- **Ecosystem Building**: Build a complete DeFi ecosystem

## Team Members

- Chacha @chachaxw
- CryptoTyson @debugzhao
- timerring @timerring

## Demo Videos/Screenshots

### Feature Screenshots

![](./orderbook.png)

![](./orders.png)

1. **Trading Interface**: Modern order book and trading panel
2. **Position Management**: Real-time position monitoring and risk management
3. **Fund Management**: Secure deposit and withdrawal process
4. **Mobile Adaptation**: Responsive design supporting various devices

### Technical Demo (Offline Presentation)
- **Trading Flow Demo**: Complete process from opening to closing positions
- **Performance Testing**: High-concurrency trading stress test results

---

**HyperPerp** - Building the Next Generation Decentralized Derivatives Trading Platform
