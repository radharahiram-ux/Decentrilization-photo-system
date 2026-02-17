## Decentrilization-photo-system

<div align="center">

![Token Banner](https://img.shields.io/badge/Blockchain-ERC--20-blue?style=for-the-badge&logo=ethereum)
![Solidity](https://img.shields.io/badge/Solidity-0.8.20-363636?style=for-the-badge&logo=solidity)
![React](https://img.shields.io/badge/React-18.0-61DAFB?style=for-the-badge&logo=react)
![Hardhat](https://img.shields.io/badge/Hardhat-2.19-FFF100?style=for-the-badge&logo=ethereum)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

**A professional, feature-rich ERC-20 token with advanced controls and stunning React frontend**

[Features](#-features) • [Quick Start](#-quick-start) • [Documentation](#-documentation) • [Demo](#-demo)

</div>

---

## 📖 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Quick Start](#-quick-start)
- [Installation](#-installation)
- [Configuration](#-configuration)
- [Deployment](#-deployment)
- [Frontend Setup](#-frontend-setup)
- [Contract Functions](#-contract-functions)
- [Testing](#-testing)
- [Security](#-security)
- [Troubleshooting](#-troubleshooting)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🎯 Overview

**Outstanding Token (OUT)** is a production-ready ERC-20 token platform built with enterprise-grade security and user experience in mind. It combines robust smart contract architecture with an intuitive React frontend for seamless token management.

### Why Outstanding Token?

✨ **Production Ready** - Battle-tested code with OpenZeppelin contracts  
🛡️ **Secure** - Built-in anti-whale, blacklist, and pause mechanisms  
🎨 **Beautiful UI** - Modern React interface with gradient design  
⚡ **Fast** - Optimized gas usage and efficient transactions  
📱 **Responsive** - Works perfectly on desktop and mobile  
🔧 **Customizable** - Easy to configure and extend

---

## ✨ Features

### 🔐 Smart Contract Features

<table>
<tr>
<td width="50%">

#### Core Functionality
- ✅ **ERC-20 Standard Compliance**
- ✅ **Minting & Burning Mechanism**
- ✅ **Configurable Transaction Tax (0-10%)**
- ✅ **Max Supply Cap (1 Billion)**
- ✅ **18 Decimal Precision**

</td>
<td width="50%">

#### Advanced Security
- 🛡️ **Anti-Whale Protection (2% max)**
- 🚫 **Blacklist System**
- ✅ **Whitelist System**
- ⏸️ **Pausable Transfers**
- 💰 **Emergency Withdrawals**

</td>
</tr>
</table>

### 🎨 Frontend Features

| Feature | Description |
|---------|-------------|
| 💼 **Wallet Integration** | Seamless MetaMask connection |
| 💰 **Balance Checking** | Real-time token balance display |
| 🔄 **Token Transfers** | Send tokens with live status |
| 🔥 **Token Burning** | Destroy tokens from your balance |
| ⚙️ **Owner Controls** | Mint, pause, configure (owner only) |
| 📊 **Token Dashboard** | View supply, tax rate, and limits |
| 📱 **Mobile Optimized** | Responsive design for all devices |
| ⚡ **Live Updates** | Real-time transaction feedback |

---

## 🛠️ Tech Stack

<div align="center">

### Smart Contract
![Solidity](https://img.shields.io/badge/Solidity-363636?style=flat&logo=solidity&logoColor=white)
![OpenZeppelin](https://img.shields.io/badge/OpenZeppelin-4A28E6?style=flat&logo=openzeppelin&logoColor=white)
![Hardhat](https://img.shields.io/badge/Hardhat-FFF100?style=flat&logo=ethereum&logoColor=black)

### Frontend
![React](https://img.shields.io/badge/React-61DAFB?style=flat&logo=react&logoColor=black)
![Web3.js](https://img.shields.io/badge/Web3.js-F16822?style=flat&logo=web3.js&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)

### Tools & Services
![MetaMask](https://img.shields.io/badge/MetaMask-F6851B?style=flat&logo=metamask&logoColor=white)
![Ethereum](https://img.shields.io/badge/Ethereum-3C3C3D?style=flat&logo=ethereum&logoColor=white)
![Polygon](https://img.shields.io/badge/Polygon-8247E5?style=flat&logo=polygon&logoColor=white)

</div>

---

## 🚀 Quick Start

### Prerequisites

Before you begin, ensure you have:

- ✅ Node.js v16 or higher
- ✅ npm or yarn package manager
- ✅ MetaMask browser extension
- ✅ Testnet ETH/MATIC for gas fees

### One-Line Installation
```bash
git clone <repository-url> && cd "decentrilization photo system" && npm run install:all
```

---

## 📦 Installation

### Step 1: Clone the Repository
```bash
git clone <repository-url>
cd "decentrilization photo system"
```

### Step 2: Install Dependencies

**Option A: Install Everything at Once**
```bash
npm run install:all
```

**Option B: Install Separately**
```bash
# Backend dependencies
npm install

# Frontend dependencies
cd client
npm install
cd ..
```

### Step 3: Verify Installation
```bash
npm run verify
```

---

## ⚙️ Configuration

### 1. Environment Setup

Create your `.env` file from the template:
```bash
cp .env.example .env
```

### 2. Configure Environment Variables

Edit `.env` with your details:
```env
# 🔑 Wallet Configuration
PRIVATE_KEY=your_wallet_private_key_here

# 🌐 Network RPC URLs
MUMBAI_RPC_URL=https://rpc-mumbai.maticvigil.com/
POLYGON_RPC_URL=https://polygon-rpc.com/
GOERLI_RPC_URL=https://goerli.infura.io/v3/YOUR_INFURA_KEY
SEPOLIA_RPC_URL=https://sepolia.infura.io/v3/YOUR_INFURA_KEY
ETHEREUM_RPC_URL=https://mainnet.infura.io/v3/YOUR_INFURA_KEY

# 📝 Block Explorer API Keys (for verification)
ETHERSCAN_API_KEY=your_etherscan_api_key
POLYGONSCAN_API_KEY=your_polygonscan_api_key
```

### 3. Customize Token Parameters

Edit `scripts/deployToken.js`:
```javascript
const tokenName = "Outstanding Token";      // Your token name
const tokenSymbol = "OUT";                  // Your token symbol
const taxWallet = "0xYourTaxWalletAddress"; // Tax recipient
const initialSupply = ethers.parseEther("1000000"); // Initial supply
```

---

## 🚢 Deployment

### Local Development Network

**Step 1: Start Hardhat Node**
```bash
npx hardhat node
```

**Step 2: Deploy (in new terminal)**
```bash
npx hardhat run scripts/deployToken.js --network localhost
```

### Testnet Deployment (Recommended First!)

<table>
<tr>
<td width="33%">

#### Polygon Mumbai
```bash
npx hardhat run scripts/deployToken.js --network mumbai
```

</td>
<td width="33%">

#### Ethereum Goerli
```bash
npx hardhat run scripts/deployToken.js --network goerli
```

</td>
<td width="33%">

#### Ethereum Sepolia
```bash
npx hardhat run scripts/deployToken.js --network sepolia
```

</td>
</tr>
</table>

### Mainnet Deployment
```bash
# Polygon Mainnet
npx hardhat run scripts/deployToken.js --network polygon

# Ethereum Mainnet
npx hardhat run scripts/deployToken.js --network ethereum
```

> ⚠️ **WARNING**: Always test thoroughly on testnet before deploying to mainnet!

### Verify Contract on Block Explorer
```bash
npx hardhat verify --network <network-name> <contract-address> <constructor-args>
```

**Example:**
```bash
npx hardhat verify --network mumbai 0x123...abc "Outstanding Token" "OUT" "0xTaxWallet" "1000000000000000000000000"
```

---

## 🎨 Frontend Setup

### Development Mode
```bash
cd client
npm start
```

🌐 Opens at `http://localhost:3000`

### Production Build
```bash
cd client
npm run build
```

### Update Contract Address

After deployment, update `client/src/utils/Web3Utils.js`:
```javascript
const CONTRACT_ADDRESS = "0xYourDeployedContractAddress";
```

---

## 📋 Contract Functions

### 🌍 Public Functions (Anyone Can Call)

| Function | Parameters | Description | Example |
|----------|-----------|-------------|---------|
| `transfer` | `address to, uint256 amount` | Send tokens to another address | `transfer("0x123...", 100)` |
| `burn` | `uint256 amount` | Destroy your own tokens | `burn(50)` |
| `approve` | `address spender, uint256 amount` | Allow spending of your tokens | `approve("0x456...", 200)` |
| `balanceOf` | `address account` | Check token balance | `balanceOf("0x789...")` |
| `allowance` | `address owner, address spender` | Check approved amount | `allowance("0xA...", "0xB...")` |

### 👑 Owner-Only Functions

| Function | Parameters | Description | Notes |
|----------|-----------|-------------|-------|
| `mint` | `address to, uint256 amount` | Create new tokens | Max 1B total supply |
| `setTaxFee` | `uint256 fee` | Change transaction tax | 0-10% allowed |
| `setTaxWallet` | `address wallet` | Update tax recipient | Must be valid address |
| `setMaxWalletAmount` | `uint256 amount` | Adjust whale protection | Minimum 1% of supply |
| `setBlacklist` | `address user, bool status` | Block/unblock addresses | Prevents transfers |
| `setWhitelist` | `address user, bool status` | Exempt from max wallet | No limit for whitelisted |
| `setTaxExempt` | `address user, bool status` | Exempt from tax | No fees charged |
| `pause` | - | Stop all transfers | Emergency use only |
| `unpause` | - | Resume transfers | Reverses pause |
| `withdrawStuckTokens` | `address token` | Recover stuck ERC20s | Emergency recovery |
| `withdrawStuckETH` | - | Recover stuck ETH | Emergency recovery |

---

## 🔌 MetaMask Integration

### Connect Wallet

1. **Install MetaMask** extension for your browser
2. **Import/Create** your wallet
3. **Switch Network** to desired blockchain
4. **Click "Connect Wallet"** in the app
5. **Approve** the connection request

### Add Token to MetaMask

#### Automatic Method (Recommended)

1. Click **"Add Token"** button in MetaMask
2. Select **"Custom Token"**
3. Paste your **contract address**
4. Token details auto-fill
5. Click **"Add Token"**

#### Manual Method
```
Contract Address: 0xYourContractAddress
Token Symbol: OUT
Decimals: 18
```

---

## 🌐 Supported Networks

| Network | Chain ID | Currency | Block Explorer | Faucet |
|---------|----------|----------|----------------|--------|
| 🏠 Localhost | 31337 | ETH | - | - |
| 🧪 Goerli | 5 | GoerliETH | etherscan.io | [Faucet](https://goerlifaucet.com) |
| 🧪 Sepolia | 11155111 | SepoliaETH | etherscan.io | [Faucet](https://sepolia-faucet.pk910.de) |
| 🧪 Mumbai | 80001 | MATIC | polygonscan.com | [Faucet](https://faucet.polygon.technology) |
| 🟣 Polygon | 137 | MATIC | polygonscan.com | - |
| 🔷 Ethereum | 1 | ETH | etherscan.io | - |

---

## 🧪 Testing

### Run All Tests
```bash
npx hardhat test
```

### Run Specific Test
```bash
npx hardhat test test/Token.test.js
```

### Coverage Report
```bash
npx hardhat coverage
```

### Gas Report
```bash
REPORT_GAS=true npx hardhat test
```

---

## 🔒 Security

### Best Practices Implemented

✅ **OpenZeppelin Contracts** - Industry-standard security  
✅ **ReentrancyGuard** - Prevents reentrancy attacks  
✅ **Ownable** - Centralized admin control  
✅ **Pausable** - Emergency stop mechanism  
✅ **SafeMath** - Overflow protection (built-in Solidity 0.8+)  

### Security Checklist

- [ ] ✅ Never expose private keys
- [ ] ✅ Use hardware wallet for mainnet
- [ ] ✅ Test on testnet first
- [ ] ✅ Audit smart contract code
- [ ] ✅ Verify contract on block explorer
- [ ] ✅ Monitor transactions regularly
- [ ] ✅ Keep dependencies updated
- [ ] ✅ Use `.env` for sensitive data
- [ ] ✅ Enable 2FA on accounts
- [ ] ✅ Backup deployment information

### Audit Recommendations

For production deployments, consider:
- Professional smart contract audit
- Bug bounty program
- Multi-signature wallet for owner
- Time-locked administrative functions

---

## 📁 Project Structure
```
decentrilization photo system/
│
├── 📜 contracts/
│   └── OutstandingToken.sol          # Main ERC-20 smart contract
│
├── 📝 scripts/
│   └── deployToken.js                # Deployment script
│
├── 🧪 test/
│   └── Lock.js                       # Test suite
│
├── 🎨 client/
│   ├── public/
│   │   ├── index.html
│   │   └── favicon.ico
│   ├── src/
│   │   ├── components/
│   │   │   ├── Balance.js            # Balance checker
│   │   │   ├── Burn.js               # Burn tokens
│   │   │   ├── Mint.js               # Mint tokens (owner)
│   │   │   ├── Transfer.js           # Transfer tokens
│   │   │   ├── TokenInfo.js          # Token information
│   │   │   └── WalletConnect.js      # Wallet connection
│   │   ├── utils/
│   │   │   ├── Web3Utils.js          # Web3 helper functions
│   │   │   └── abi/
│   │   │       └── ContractABI.js    # Contract ABI
│   │   ├── App.js                    # Main application
│   │   ├── App.css                   # Styling
│   │   └── index.js                  # Entry point
│   └── package.json
│
├── ⚙️ hardhat.config.js              # Hardhat configuration
├── 📦 package.json                   # Dependencies
├── 🔐 .env.example                   # Environment template
├── 📖 README.md                      # This file
└── 📄 LICENSE                        # MIT License
```

---

## 🐛 Troubleshooting

### MetaMask Issues

<details>
<summary><b>❌ Wallet Not Connecting</b></summary>

**Solutions:**
- Ensure MetaMask is installed and unlocked
- Refresh the browser page
- Check if already connected to another site
- Verify correct network is selected
- Clear browser cache
</details>

<details>
<summary><b>❌ Wrong Network</b></summary>

**Solutions:**
- Click network dropdown in MetaMask
- Select correct network (Mumbai, Goerli, etc.)
- Add custom network if needed
- Verify RPC URL is correct
</details>

### Transaction Issues

<details>
<summary><b>❌ Insufficient Gas</b></summary>

**Solutions:**
- Get testnet tokens from faucet
- Check gas price is set correctly
- Ensure sufficient balance for fees
- Try increasing gas limit
</details>

<details>
<summary><b>❌ Transaction Failed</b></summary>

**Possible Causes:**
- Invalid recipient address
- Address is blacklisted
- Insufficient token balance
- Max wallet limit exceeded
- Contract is paused

**Check:**
```javascript
// Verify address is valid
web3.utils.isAddress(address)

// Check if blacklisted
await contract.methods.blacklist(address).call()

// Check balance
await contract.methods.balanceOf(yourAddress).call()
```
</details>

### Contract Issues

<details>
<summary><b>❌ Contract Not Showing</b></summary>

**Solutions:**
- Verify you're on correct network
- Check contract address is correct
- Wait for blockchain confirmation
- Try manual token import
- Clear MetaMask cache
</details>

<details>
<summary><b>❌ Deployment Failed</b></summary>

**Solutions:**
- Check `.env` configuration
- Verify private key is correct
- Ensure sufficient gas balance
- Check network RPC URL
- Review constructor parameters
</details>

---

## 📊 Token Economics

| Parameter | Value | Description |
|-----------|-------|-------------|
| **Name** | Outstanding Token | Full token name |
| **Symbol** | OUT | Token ticker |
| **Decimals** | 18 | Standard precision |
| **Max Supply** | 1,000,000,000 | Hard cap (1 billion) |
| **Initial Supply** | Configurable | Set in deployment |
| **Tax Rate** | 5% (default) | Configurable 0-10% |
| **Max Wallet** | 2% of supply | Anti-whale protection |

---

## 🔗 Useful Resources

### Documentation
- 📘 [Solidity Docs](https://docs.soliditylang.org)
- 📗 [OpenZeppelin Docs](https://docs.openzeppelin.com)
- 📙 [Hardhat Docs](https://hardhat.org/docs)
- 📕 [Web3.js Docs](https://web3js.readthedocs.io)
- 📓 [React Docs](https://react.dev)

### Tools
- 🦊 [MetaMask](https://metamask.io)
- 🔍 [Etherscan](https://etherscan.io)
- 🟣 [PolygonScan](https://polygonscan.com)
- 🎨 [Remix IDE](https://remix.ethereum.org)
- ⛽ [Gas Tracker](https://etherscan.io/gastracker)

### Get Testnet Tokens
- 💧 [Mumbai Faucet](https://faucet.polygon.technology)
- 💧 [Goerli Faucet](https://goerlifaucet.com)
- 💧 [Sepolia Faucet](https://sepolia-faucet.pk910.de)

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. **Fork** the repository
2. **Create** your feature branch (`git checkout -b feature/AmazingFeature`)
3. **Commit** your changes (`git commit -m 'Add some AmazingFeature'`)
4. **Push** to the branch (`git push origin feature/AmazingFeature`)
5. **Open** a Pull Request

### Coding Standards

- Follow Solidity style guide
- Write comprehensive tests
- Document all functions
- Use meaningful variable names
- Add comments for complex logic

---

## 📜 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.
```
MIT License

Copyright (c) 2024 Outstanding Token

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files...
```

---

## 🎉 Deployment Checklist

### Pre-Deployment

- [ ] ✅ All tests passing
- [ ] ✅ Code reviewed and audited
- [ ] ✅ `.env` configured correctly
- [ ] ✅ Token parameters finalized
- [ ] ✅ Testnet deployment successful
- [ ] ✅ Frontend tested with contract
- [ ] ✅ Gas estimates calculated

### Post-Deployment

- [ ] ✅ Contract verified on explorer
- [ ] ✅ Token imported to MetaMask
- [ ] ✅ All functions tested
- [ ] ✅ Owner controls verified
- [ ] ✅ Tax system working
- [ ] ✅ Blacklist/whitelist tested
- [ ] ✅ Emergency functions tested
- [ ] ✅ Documentation updated
- [ ] ✅ Contract address saved
- [ ] ✅ Backup created

---

## 📞 Support & Community

- 💬 **Discord**: [Join our community](#)
- 🐦 **Twitter**: [@OutstandingToken](#)
- 📧 **Email**: support@outstandingtoken.com
- 📖 **Wiki**: [Documentation](#)
- 🐛 **Issues**: [GitHub Issues](#)

---

## 🌟 Acknowledgments

Built with ❤️ using:
- [OpenZeppelin](https://openzeppelin.com) - Secure smart contract library
- [Hardhat](https://hardhat.org) - Ethereum development environment
- [React](https://react.dev) - UI framework
- [Web3.js](https://web3js.org) - Ethereum JavaScript API
- [MetaMask](https://metamask.io) - Crypto wallet

---

<div align="center">

### ⭐ Star this repo if you find it useful!

**Made with 💎 by the Outstanding Token Team**

[⬆ Back to Top](#-outstanding-token-out---complete-erc-20-platform)

</div>
