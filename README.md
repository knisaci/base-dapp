# 🔵 Base L2 dApp

A lightweight, zero-dependency smart contract interface built on **Base Mainnet**. No React, no Node.js, no build tools — just a single HTML file you can open in any browser.

🌐 **Live Demo:** [knisaci.github.io/base-dapp](https://knisaci.github.io/base-dapp)

---

## ✨ Features

- 🔗 **Connect MetaMask** — auto-switches to Base Mainnet (chainId 8453)
- 📖 **Read** any smart contract function (`view` / `pure`)
- ✍️ **Write** — send transactions to any contract function
- 📦 **Deploy** — paste bytecode and deploy contracts directly from the browser
- 🔍 **Explorer links** — every transaction links to [basescan.org](https://basescan.org)

---

## 🚀 Quick Start

### Option 1 — Open directly in your browser
```bash
git clone https://github.com/knisaci/base-dapp.git
cd base-dapp
open index.html
```

### Option 2 — Use the live version
Visit 👉 [knisaci.github.io/base-dapp](https://knisaci.github.io/base-dapp)

No installation required.

---

## 🛠 How to Use

### 1. Connect Wallet
- Click **Connect Wallet**
- MetaMask will prompt you to approve and switch to **Base Mainnet**
- Your address and ETH balance will appear

### 2. Read a Contract
- Go to the **Read** tab
- Enter a contract address (e.g. any deployed contract on Base)
- Enter the function signature (e.g. `getMessage()` or `balanceOf(address)`)
- Add arguments if needed (comma-separated)
- Click **Call Function**

### 3. Write to a Contract
- Go to the **Write** tab
- Enter the contract address and function signature (e.g. `setMessage(string)`)
- Enter arguments and optional ETH value to send
- Click **Send Transaction** and confirm in MetaMask

### 4. Deploy a Contract
- Go to the **Deploy** tab
- Paste your compiled contract bytecode
- Add ABI-encoded constructor arguments if needed
- Click **Deploy Contract** and confirm in MetaMask
- The deployed contract address appears automatically once confirmed

---

## 🧪 Example Contract

Try it with this simple `Message` contract:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.19;

contract Message {
    string private message;
    address public lastSender;
    uint256 public updateCount;

    constructor(string memory _initialMessage) {
        message = _initialMessage;
        lastSender = msg.sender;
        updateCount = 0;
    }

    function getMessage() public view returns (string memory) {
        return message;
    }

    function setMessage(string memory _newMessage) public {
        message = _newMessage;
        lastSender = msg.sender;
        updateCount += 1;
    }
}
```

Compile it on [remix.ethereum.org](https://remix.ethereum.org), copy the bytecode, and deploy it using the **Deploy tab** in the dApp.

Then use the **Read** tab with `getMessage()` and the **Write** tab with `setMessage(string)` to interact with it.

---

## 🔧 Tech Stack

| Layer | Technology |
|---|---|
| Frontend | Plain HTML, CSS, JavaScript |
| Wallet | MetaMask (EIP-1193) |
| ABI Encoding | [ethers.js v6](https://docs.ethers.org) (loaded from CDN) |
| Network | Base Mainnet (chainId 8453) |
| Hosting | GitHub Pages |

---

## 🌐 Network Details

| Setting | Value |
|---|---|
| Network | Base Mainnet |
| Chain ID | 8453 |
| RPC URL | https://mainnet.base.org |
| Explorer | https://basescan.org |

---

## 📁 Project Structure

```
base-dapp/
└── index.html    # Entire app — wallet, read, write, deploy
```

---

## 🤝 Contributing

Contributions are welcome! Here's how:

1. Fork this repo
2. Create a feature branch: `git checkout -b feature/my-feature`
3. Commit your changes: `git commit -m 'Add my feature'`
4. Push to the branch: `git push origin feature/my-feature`
5. Open a Pull Request

---

## 💡 Roadmap

- [ ] Add ABI import (JSON paste)
- [ ] Transaction history log
- [ ] Support for ERC-20 token interactions
- [ ] WalletConnect support
- [ ] Dark/light theme toggle

---

## 📄 License

MIT — free to use, fork, and build on.

---

## 🔵 Built on Base

This project is part of the [Base](https://base.org) ecosystem — an Ethereum L2 built by Coinbase.

[![Built on Base](https://img.shields.io/badge/Built%20on-Base-0052FF?style=flat&logo=coinbase)](https://base.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![Live Demo](https://img.shields.io/badge/Live-Demo-brightgreen)](https://knisaci.github.io/base-dapp)
