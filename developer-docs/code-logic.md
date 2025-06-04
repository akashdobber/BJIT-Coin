# 🧠 Code Logic & Design - BJITCoin

## 🪙 Token Overview

**BJITCoin** is an ERC-20 token with a total supply of **50,000,000,000 (50B)** and 18 decimals.

| Attribute    | Value          |
| ------------ | -------------- |
| Name         | BJITCoin       |
| Symbol       | BJIT           |
| Decimals     | 18             |
| Total Supply | 50,000,000,000 |

---

## 🔧 Core ERC-20 Functions

### ✅ `name()`, `symbol()`, `decimals()`

Standard metadata functions for wallet and UI integration.

### 🔁 `transfer()`

Safely transfers tokens from sender to recipient with event emission.

### 🛂 `approve()`

Authorizes a spender to transfer tokens on behalf of the owner.

### 📜 `allowance()`

Reads the approved amount a spender can use.

### 🧾 `transferFrom()`

Allows delegated transfers using prior approval.

### 📊 `totalSupply()`

Returns the fixed token supply.

### 💼 `balanceOf()`

Reads balance of any account.

---

## 🚀 Functional Capabilities

BJITCoin is:

- **Interoperable** with wallets, exchanges, and DeFi protocols
- **Secure** with event emissions and validation
- **Ready for integration** across real-world business systems

---

## ⚙️ Smart Contract Optimization

| Optimization Technique      | Benefit                                    |
| --------------------------- | ------------------------------------------ |
| 🧵 Custom Errors (ERC-6093) | Lower gas by avoiding long revert strings  |
| 🧮 `unchecked` Blocks       | Gas savings for safe arithmetic operations |
| 🔍 `pure`/`view` Modifiers  | Gas optimization and semantic clarity      |
| 🧊 Immutable Constants      | Reduces runtime and deployment gas costs   |
| ♾ EIP-717 Allowance Pattern | Allows for infinite approvals              |

BJITCoin smart contract is **lean**, **secure**, and **optimized for gas efficiency**.
