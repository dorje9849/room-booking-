# ⬡ RoomChain — Decentralised Room Booking DApp

> **CN6035 Mobile & Distributed Systems — DApp Project**  
> Blockchain-based room booking on Ethereum with a React frontend.

[![CI](https://github.com/YOUR_USERNAME/roomchain/actions/workflows/ci.yml/badge.svg)](https://github.com/YOUR_USERNAME/roomchain/actions)
[![Solidity](https://img.shields.io/badge/Solidity-0.8.24-363636?logo=solidity)](https://soliditylang.org)
[![Hardhat](https://img.shields.io/badge/Hardhat-2.19-yellow)](https://hardhat.org)
[![React](https://img.shields.io/badge/React-18-61DAFB?logo=react)](https://react.dev)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

---

## 📐 Architecture

```
roomchain/
├── contracts/
│   └── RoomChain.sol          # Solidity smart contract
├── scripts/
│   └── deploy.js              # Deploy + seed demo rooms
├── test/
│   └── RoomChain.test.js      # 28 Mocha/Chai test cases
├── frontend/
│   └── src/
│       ├── components/        # React pages & UI
│       ├── hooks/             # useWeb3 context
│       ├── utils/             # Helpers
│       └── contracts/         # ABI + address artifact
├── hardhat.config.js
└── .github/workflows/ci.yml
```

---

## ✨ Features

| Feature | Details |
|---|---|
| **List Rooms** | Host deploys room with type, price per night, max guests |
| **Book Rooms** | Guest selects dates, pays exact ETH for number of nights |
| **Overlap Protection** | Smart contract blocks double bookings for same dates |
| **Cancel & Refund** | Full refund >48 h · 50% refund within 48 h |
| **Check-in / Check-out** | Host records guest arrival and departure on-chain |
| **Toggle Availability** | Host enables/disables listing at any time |
| **Earnings Withdrawal** | Pull-pattern ETH withdrawal for room owners |
| **Platform Fee** | 3% fee in basis points, adjustable by contract owner |
| **Admin Controls** | Pause/unpause, platform fee withdrawal |

---

## 🚀 Quick Start

### Prerequisites

| Tool | Version |
|---|---|
| Node.js | ≥ 18 |
| MetaMask | Latest (Chrome extension) |
| Git | Any |

### 1. Clone & Install

```bash
git clone https://github.com/YOUR_USERNAME/roomchain.git
cd roomchain
npm install
cd frontend && npm install && cd ..
```

### 2. Compile

```bash
npm run compile
```

### 3. Run Tests

```bash
npm test
```

### 4. Start Local Blockchain (new terminal)

```bash
npm run node
```

Copy a private key from the printed list — import it into MetaMask.

### 5. Deploy Contract + Seed Rooms

```bash
npm run deploy:local
```

### 6. Configure MetaMask

- Network Name: `Hardhat Local`
- RPC URL: `http://127.0.0.1:8545`
- Chain ID: `31337`
- Symbol: `ETH`

### 7. Start Frontend

```bash
npm start
```

Open **http://localhost:3000**

---

## 🌐 Sepolia Deployment

```bash
cp .env.example .env
# Fill in PRIVATE_KEY and SEPOLIA_RPC_URL
npm run deploy:sepolia
```

Update `TARGET_CHAIN` in `frontend/src/hooks/useWeb3.js` to `11155111`.

---

## 🧪 Code Quality

```bash
npm run lint:sol    # Solidity linting
npm run lint:js     # JavaScript linting
npm run coverage    # Test coverage report
```

---

## 📜 Smart Contract Functions

| Function | Access | Description |
|---|---|---|
| `listRoom(...)` | Public | List a new room |
| `bookRoom(roomId, checkIn, checkOut)` | Public, payable | Book for date range |
| `cancelBooking(bookingId)` | Guest | Cancel with refund policy |
| `checkIn(bookingId)` | Room owner | Record guest check-in |
| `checkOut(bookingId)` | Room owner | Record guest check-out |
| `setRoomAvailability(roomId, bool)` | Room owner | Toggle listing |
| `withdrawEarnings()` | Room owner | Pull ETH earnings |
| `setPlatformFee(bps)` | Contract owner | Update fee |
| `pause() / unpause()` | Contract owner | Circuit breaker |
| `isAvailable(roomId, ci, co)` | View | Check date availability |
| `calculateCost(roomId, ci, co)` | View | Compute total cost |

---

## 🗂 Tech Stack

| Layer | Technology |
|---|---|
| Smart Contract | Solidity 0.8.24, OpenZeppelin 5 |
| Dev Environment | Hardhat 2.19 |
| Testing | Mocha, Chai, hardhat-network-helpers |
| Coverage | solidity-coverage |
| Frontend | React 18, React Router v6 |
| Wallet / Chain | ethers.js v6, MetaMask |
| Notifications | react-hot-toast |
| CI/CD | GitHub Actions |
| Linting | Solhint, ESLint |

---

## 📄 License

MIT © RoomChain — CN6035 Project
