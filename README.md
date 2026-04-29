# 🔵 Base Hub — Smart Contract Toolkit

A lightweight, zero-dependency dApp toolkit built on **Base Mainnet**. No React, no Node.js, no build tools — just plain HTML files you can open in any browser.

🌐 **Live:** [knisaci.github.io/base-dapp](https://knisaci.github.io/base-dapp)  
🏗️ **Builder:** [knisaci.github.io/base-dapp/builder.html](https://knisaci.github.io/base-dapp/builder.html)

[![Built on Base](https://img.shields.io/badge/Built%20on-Base-0052FF?style=flat&logo=coinbase)](https://base.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![Live Demo](https://img.shields.io/badge/Live-Demo-brightgreen)](https://knisaci.github.io/base-dapp)

---

## 📦 Pages

| Page | URL | Description |
|---|---|---|
| `index.html` | `/` | Smart contract interface — read, write, deploy |
| `builder.html` | `/builder.html` | No-code contract builder — deploy with a form |

---

## ✨ Features

### 📖 Smart Contract Interface (`index.html`)
- 🔗 **Connect MetaMask** — auto-switches to Base Mainnet (chainId 8453)
- 📖 **Read** any contract function (`view` / `pure`) with example presets
- ✍️ **Write** — send transactions with live argument detection
- 🚀 **Deploy** — paste bytecode and deploy via a step-by-step guide
- 💡 **Tooltips** on every field explaining what to enter
- 🔍 **Explorer links** — every transaction links to [basescan.org](https://basescan.org)

### 🏗️ No-Code Contract Builder (`builder.html`)
- 💾 **Simple Storage** — deploy a string storage contract with a custom initial message
- 🪙 **ERC-20 Token** — launch your own fungible token (name, symbol, supply, decimals)
- 🖼️ **ERC-721 NFT** — deploy an NFT collection (name, symbol, optional base URI)
- 📋 **Live preview** — deployment details update as you type
- ➕ **Add to MetaMask** — one-click token import after ERC-20 deploy
- No Remix, no Solidity knowledge, no command line needed

---

## 🚀 Quick Start

### Option 1 — Clone and open locally
```bash
git clone https://github.com/knisaci/base-dapp.git
cd base-dapp
open index.html        # Smart contract interface
open builder.html      # No-code builder
```

### Option 2 — Use the live version
- Interface 👉 [knisaci.github.io/base-dapp](https://knisaci.github.io/base-dapp)
- Builder 👉 [knisaci.github.io/base-dapp/builder.html](https://knisaci.github.io/base-dapp/builder.html)

No installation required.

---

## 🛠 How to Use

### Smart Contract Interface

**1. Connect Wallet**
- Click **Connect Wallet**
- MetaMask prompts you to approve and switch to **Base Mainnet**
- Your address and ETH balance appear

**2. Read a Contract**
- Go to the **Read** tab
- Enter a contract address and function signature (e.g. `getMessage()` or `balanceOf(address)`)
- Click **Call Function** — result appears below

**3. Write to a Contract**
- Go to the **Write** tab
- Enter contract address, function signature (e.g. `setMessage(string)`), and arguments
- Click **Send Transaction** and confirm in MetaMask

**4. Deploy a Contract**
- Go to the **Deploy** tab
- Paste compiled bytecode from [Remix IDE](https://remix.ethereum.org)
- Follow the 4-step guide — constructor args, ETH value, then deploy
- Contract address appears automatically once confirmed

---

### No-Code Contract Builder

**1. Pick a template** — Simple Storage, ERC-20, or ERC-721  
**2. Fill in the form** — name, symbol, supply, initial message, etc.  
**3. Review the live preview** — see exactly what will be deployed  
**4. Click Deploy** — MetaMask confirms, contract is live on Base Mainnet  
**5. Use the result buttons** — copy address, view on Basescan, add token to MetaMask

---

## 🧪 Example Contract

Test the interface with this simple `Message` contract:

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

Compile on [remix.ethereum.org](https://remix.ethereum.org), copy the bytecode, and deploy via the **Deploy tab**. Then read with `getMessage()` and write with `setMessage(string)`.

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
├── index.html      # Smart contract interface (read, write, deploy)
├── builder.html    # No-code contract builder (ERC-20, NFT, storage)
└── README.md
```

---

## 🤝 Contributing

Contributions are welcome!

1. Fork this repo
2. Create a feature branch: `git checkout -b feature/my-feature`
3. Commit your changes: `git commit -m 'Add my feature'`
4. Push: `git push origin feature/my-feature`
5. Open a Pull Request

---

## 💡 Roadmap

- [x] Smart contract read / write / deploy
- [x] No-code contract builder (ERC-20, ERC-721, Storage)
- [x] Live deployment preview
- [x] Tooltip hints and function presets
- [ ] ABI JSON import
- [ ] Transaction history log
- [ ] WalletConnect support
- [ ] Contract verification checker via Basescan API
- [ ] Event log viewer

---

## 📄 License

MIT — free to use, fork, and build on.

---

## 🔵 Built on Base

This project is part of the [Base](https://base.org) ecosystem — an Ethereum L2 built by Coinbase.

> Built with 💙 on Base Mainnet
