# 🧭 Design Decisions - BJITCoin

## 📋 Project Management – Why We Use JIRA

We followed an **Agile methodology** using **JIRA** for task management and team coordination.

### ✅ Benefits

- 📌 **Task Structuring**

  - Epics → User Stories → Subtasks
  - Clear mapping to Git branches and PRs

- 🏃‍♂️ **Sprint Planning**

  - Sprint boards, retrospectives, and burndown charts

- 🤝 **Team Collaboration**

  - Improved transparency and accountability

- 🐞 **Bug Tracking**
  - Efficient resolution and root cause tracking

JIRA streamlined our team workflow, boosted productivity, and enabled agile delivery.

---

## 📦 Tech Stack Overview

| Layer                  | Technology Used            |
| ---------------------- | -------------------------- |
| **Smart Contracts**    | Solidity + OpenZeppelin    |
| **Dev Framework**      | Hardhat                    |
| **Testing & Debug**    | Ethers.js + Mocha + Chai   |
| **Deployment**         | Hardhat + Infura / Alchemy |
| **Project Management** | JIRA + GitHub Projects     |

## ⚙️ Why We Use Hardhat

We selected [Hardhat](https://hardhat.org/) as our development environment after evaluating Truffle, Foundry, and Brownie.

### ✅ Benefits

- 💡 **Developer Experience**  
  Better error messages, TypeScript support, and inbuilt Ethers.js.

- 🔌 **Rich Plugin Ecosystem**

  - `@nomicfoundation/hardhat-toolbox`
  - `hardhat-gas-reporter`
  - `hardhat-ethers`
  - `hardhat-verify`

- 🧪 **Local Network Simulation**  
  Runs a fast local Ethereum node for testing.

- 🔍 **Advanced Debugging**  
  Stack traces, revert reasons, and console logs.

Hardhat enabled rapid development, testing, and deployment with zero compromise on dev ergonomics.

## ⚙️ Step-by-Step Hardhat Setup

### 1️⃣ Install Hardhat

```bash
npm install --save-dev hardhat
```

### 2️⃣ Install Essential Plugins

```bash
npm install --save-dev @nomicfoundation/hardhat-toolbox
npm install --save-dev @nomicfoundation/hardhat-ethers
npm install --save-dev @nomicfoundation/hardhat-ignition
npm install --save-dev @nomicfoundation/hardhat-ignition-ethers
npm install --save-dev @nomicfoundation/hardhat-network-helpers
npm install --save-dev @nomicfoundation/hardhat-verify
npm install --save-dev @typechain/hardhat
npm install --save-dev hardhat
npm install --save-dev hardhat-gas-reporter
```

### 3️⃣ Install OpenZeppelin contracts

```bash
npm install @openzeppelin/contracts
```

### 4️⃣ Configure hardhat.config.ts

```ts
import { HardhatUserConfig } from 'hardhat/config';
import '@nomicfoundation/hardhat-toolbox';
import * as dotenv from 'dotenv';
import 'solidity-coverage';
import 'hardhat-gas-reporter';
import '@nomicfoundation/hardhat-verify';

// Load environment variables from a .env file
dotenv.config();

const SEPOLIA_RPC_URL = process.env.SEPOLIA_RPC_URL || ''; // Add your Sepolia RPC URL in the .env file
const PRIVATE_KEY = process.env.PRIVATE_KEY || ''; // Add your wallet's private key in the .env file
const MNEMONIC = process.env.MNEMONIC || '';

const config: HardhatUserConfig = {
  solidity: {
    compilers: [
      {
        version: '0.8.28',
        settings: {
          optimizer: {
            enabled: true,
            runs: 200,
          },
        },
      },
      {
        version: '0.5.15',
      },
    ],
  },
  networks: {
    sepolia: {
      url: SEPOLIA_RPC_URL,
      accounts: {
        mnemonic: MNEMONIC,
      },
    },
    local: {
      url: 'http://127.0.0.1:8545',
    },
  },
  gasReporter: {
    enabled: true,
  },
  etherscan: {
    apiKey: process.env.ETHERSCAN_API_KEY,
  },
};

export default config;
```

## ⛏️ Smart Contract Optimization Decisions

We focused on **gas efficiency** and **clarity**.

| Optimization                 | Description                                                                   |
| ---------------------------- | ----------------------------------------------------------------------------- |
| 🧵 **Custom Errors**         | Saves gas vs `require()` strings using `error` declarations                   |
| 🚫 **Unchecked Blocks**      | Used in safe arithmetic to skip overflow checks and save gas                  |
| 👁️‍🗨️ **Pure/View**             | Functions correctly marked for compiler optimization                          |
| 🏷️ **Constants**             | Metadata (name, symbol, supply) declared as constants                         |
| 🔄 **Conditional Approvals** | Skips `allowance--` if `maxUint256` is set (EIP-717)                          |
| 📢 **Optional Events**       | `_approve()` includes optional `emitEvent` flag to skip redundant logs        |
| 🔁 **Unified \_update()**    | Core logic for `mint`, `burn`, and `transfer` centralized for maintainability |

---

## 🧪 Testing Philosophy

We used a Test-Driven Development (TDD) strategy.

| Tool                    | Purpose                    |
| ----------------------- | -------------------------- |
| 🔁 Mocha + Chai         | Unit testing               |
| 🧬 hardhat-gas-reporter | Gas efficiency analysis    |
| 📈 solidity-coverage    | Test coverage >95% ensured |

---

## 🧠 Summary of Core Design Principles

| Principle               | Description                                                            |
| ----------------------- | ---------------------------------------------------------------------- |
| 🔐 **Security First**   | Used OpenZeppelin and followed Solidity security best practices        |
| 🧱 **Modular Design**   | Contract split for future extensibility (staking, governance, burning) |
| ⚡ **Gas Optimization** | Focused on low-cost deployment and runtime savings                     |
| 👨‍💻 **Developer UX**     | Smooth local workflow via Hardhat, Ethers.js, and TypeScript           |
| 📈 **Agile Execution**  | JIRA enabled sprint-based, traceable, and collaborative delivery       |

---
