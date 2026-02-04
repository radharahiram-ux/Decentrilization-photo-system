# Outstanding Token (OUT) - Complete ERC-20 Platform

A professional, feature-rich ERC-20 token smart contract with an interactive React frontend for token management, minting, burning, and advanced controls.

## 📋 Features

### Smart Contract (Solidity)
- ✅ **ERC-20 Standard**: Full OpenZeppelin ERC20 implementation
- ✅ **Minting & Burning**: Create new tokens and burn existing ones
- ✅ **Transaction Tax**: Configurable 5% fee on transfers
- ✅ **Anti-Whale Protection**: Maximum wallet limit (2% of supply)
- ✅ **Blacklist/Whitelist**: Address-level restriction controls
- ✅ **Pausable**: Emergency stop mechanism
- ✅ **Tax Exemptions**: Exempt specific addresses from fees
- ✅ **Max Supply Cap**: Hard limit of 1 billion tokens
- ✅ **Emergency Withdrawals**: Recover stuck tokens/ETH

### Frontend (React)
- 🎨 Modern, responsive UI with gradient design
- 💼 MetaMask wallet integration
- 💰 Real-time balance checking
- 📊 Token information dashboard
- 🔄 Transfer tokens functionality
- 🔥 Burn tokens (any user)
- ⚙️ Owner controls (mint, pause, configure)
- 📱 Mobile-friendly design
- ⚡ Real-time transaction status

## 🚀 Quick Start

### Prerequisites
- Node.js (v16+)
- npm or yarn
- MetaMask browser extension
- Testnet ETH or MATIC for gas fees

### Installation

1. **Clone or Download the Project**
```bash
cd "decentrilization photo system"
```

2. **Install Dependencies**
```bash
npm install:all
# This installs both root and client dependencies
```

Or separately:
```bash
# Install Hardhat dependencies
npm install

# Install React dependencies
cd client
npm install
cd ..
```

### Configuration

1. **Create .env file** (copy from .env.example)
```bash
cp .env.example .env
```

2. **Configure your deployment parameters:**
   - Add your PRIVATE_KEY to .env
   - Add RPC URLs for your chosen network
   - Add ETHERSCAN_API_KEY (optional, for contract verification)

3. **Update deployment parameters** in `scripts/deployToken.js`:
   - `tokenName`: Your token name
   - `tokenSymbol`: Your token symbol (e.g., OUT, MTK, WETH)
   - `taxWallet`: Address to receive transaction fees
   - `initialSupply`: Initial token amount to mint

## 📦 Project Structure

```
decentrilization photo system/
├── contracts/
│   └── OutstandingToken.sol          # Main smart contract
├── scripts/
│   └── deployToken.js                # Deployment script
├── test/
│   └── Lock.js                       # Test file
├── client/
│   ├── src/
│   │   ├── components/               # React components
│   │   │   ├── Balance.js
│   │   │   ├── Burn.js
│   │   │   ├── Mint.js
│   │   │   ├── Transfer.js
│   │   │   ├── TokenInfo.js
│   │   │   └── WalletConnect.js
│   │   ├── utils/
│   │   │   ├── Web3Utils.js          # Web3 interactions
│   │   │   └── abi/ContractABI.js    # Contract ABI
│   │   ├── App.js                    # Main app component
│   │   ├── App.css                   # Styling
│   │   └── index.js
│   └── package.json
├── hardhat.config.js                 # Hardhat configuration
├── package.json                      # Root package.json
└── .env.example                      # Environment template
```

## 🛠️ Smart Contract Deployment

### Deploy to Local Network (for testing)

```bash
# Start local Hardhat node
npx hardhat node

# In another terminal, deploy
npx hardhat run scripts/deployToken.js --network localhost
```

### Deploy to Testnet (Recommended First)

**Mumbai Testnet (Polygon)**
```bash
npx hardhat run scripts/deployToken.js --network mumbai
```

**Goerli Testnet (Ethereum)**
```bash
npx hardhat run scripts/deployToken.js --network goerli
```

**Sepolia Testnet (Ethereum)**
```bash
npx hardhat run scripts/deployToken.js --network sepolia
```

### Deploy to Mainnet (Production)

```bash
npx hardhat run scripts/deployToken.js --network polygon
# or
npx hardhat run scripts/deployToken.js --network ethereum
```

⚠️ **WARNING**: Always test on testnet first!

## 🎨 Running the Frontend

### Development Mode
```bash
cd client
npm start
```

Runs at `http://localhost:3000`

### Production Build
```bash
cd client
npm run build
```

## 🔐 Contract Interaction

### Connect MetaMask

1. Install MetaMask extension
2. Import your wallet with private key or seed phrase
3. Switch to desired network (Mumbai, Goerli, Sepolia, Polygon, or Ethereum)
4. Click "Connect Wallet" in the app

### Import Token to MetaMask

**Automatic (Recommended):**
1. Click "Add Token" in MetaMask
2. Paste contract address
3. Token details auto-fill
4. Confirm import

**Manual:**
1. Contract Address: `0x...` (from deployment)
2. Token Symbol: `OUT` (or your symbol)
3. Decimals: `18`

## 📊 Contract Functions

### Public Functions (Anyone)

| Function | Description |
|----------|-------------|
| `transfer(address, uint256)` | Send tokens to another address |
| `burn(uint256)` | Destroy your own tokens |
| `approve(address, uint256)` | Allow spending of your tokens |
| `balanceOf(address)` | Check token balance |

### Owner Functions

| Function | Description |
| `mint(address, uint256)` | Create new tokens (max 1 billion) |
| `setTaxFee(uint256)` | Change transaction tax (0-10%) |
| `setTaxWallet(address)` | Change tax recipient |
| `setMaxWalletAmount(uint256)` | Adjust whale protection limit |
| `setBlacklist(address, bool)` | Block/unblock addresses |
| `setWhitelist(address, bool)` | Exempt from max wallet limit |
| `pause()` | Stop all transfers |
| `unpause()` | Resume transfers |

## 🧪 Testing

```bash
npx hardhat test
```

## 📝 Contract Details

- **Token Standard**: ERC-20
- **Decimals**: 18 (standard)
- **Max Supply**: 1,000,000,000 (1 billion)
- **Default Tax**: 5%
- **Max Wallet**: 2% of total supply
- **Owner**: Deployer wallet (transferable)

## 🌐 Supported Networks

| Network | Chain ID | RPC Endpoint |
|---------|----------|------------|
| Localhost | 31337 | http://127.0.0.1:8545 |
| Goerli Testnet | 5 | https://goerli.infura.io/v3/ |
| Sepolia Testnet | 11155111 | https://sepolia.infura.io/v3/ |
| Mumbai Testnet | 80001 | https://rpc-mumbai.maticvigil.com/ |
| Polygon Mainnet | 137 | https://polygon-rpc.com/ |
| Ethereum Mainnet | 1 | https://mainnet.infura.io/v3/ |

## 🔗 Useful Links

- **Remix IDE**: https://remix.ethereum.org
- **MetaMask**: https://metamask.io
- **Etherscan**: https://etherscan.io
- **PolygonScan**: https://polygonscan.com
- **OpenZeppelin Docs**: https://docs.openzeppelin.com
- **Solidity Docs**: https://docs.soliditylang.org
- **Hardhat Docs**: https://hardhat.org

### Get Testnet Tokens
- **Mumbai Faucet**: https://faucet.polygon.technology
- **Goerli Faucet**: https://goerlifaucet.com
- **Sepolia Faucet**: https://sepolia-faucet.pk910.de

## 🔒 Security Best Practices

1. **Never expose your private key** - Use environment variables
2. **Test on testnet first** - Always test before mainnet deployment
3. **Audit smart contracts** - Consider professional audit for production
4. **Use hardware wallet** - For mainnet deployments
5. **Monitor transactions** - Check gas prices and network congestion
6. **Verify contract** - Publish source code on block explorers
7. **Keep dependencies updated** - Regularly update npm packages

## ⚠️ Important Notes

- Transaction fees are **5%** by default (configurable 0-10%)
- Max wallet limit is **2%** of total supply (anti-whale protection)
- Contract owner has significant control - protect your deploying wallet
- Pausing contract freezes all transfers
- No minimum or maximum transfer amounts (except max wallet)

## 🚨 Troubleshooting

### MetaMask Not Connecting
- Ensure MetaMask is installed and unlocked
- Try refreshing the page
- Check if wallet is already connected
- Verify network selection

### Insufficient Gas
- Check if you have enough testnet tokens
- Get faucet tokens from network-specific faucet
- Increase gas limit in MetaMask

### Transaction Failed
- Verify recipient address is valid
- Check if address is blacklisted
- Ensure you have sufficient balance
- Verify max wallet limit not exceeded

### Contract Not Showing Tokens
- Ensure you're on correct network
- Verify contract address is correct
- Try manual token import in MetaMask
- Wait a few moments for blockchain confirmation

## 📞 Support

For issues or questions:
1. Check the troubleshooting section
2. Review OpenZeppelin documentation
3. Check Hardhat documentation
4. Consult Solidity docs for contract questions

## 📄 License

MIT License - See LICENSE file for details

## 🎉 Deployment Checklist

- [ ] Test on testnet successfully
- [ ] Verify contract on block explorer
- [ ] Import token to MetaMask
- [ ] Test all functions (transfer, burn, mint)
- [ ] Test blacklist/whitelist
- [ ] Test pause/unpause
- [ ] Review security implications
- [ ] Backup deployment info
- [ ] Document contract address
- [ ] Ready for mainnet (if applicable)

---

**Outstanding Token Platform** - Built with Hardhat, Solidity, and React
