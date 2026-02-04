# Outstanding Token - Complete Deployment Guide

## Step 1: Project Setup

### 1.1 Install Dependencies

```bash
# Install root dependencies (Hardhat)
npm install

# Install client dependencies (React)
cd client
npm install
cd ..

# OR use the convenience script
npm run install:all
```

### 1.2 Verify Installation

```bash
# Check Hardhat installation
npx hardhat --version

# Check Node version (should be v16+)
node --version

# Check npm version
npm --version
```

## Step 2: Configure Environment

### 2.1 Create .env File

```bash
cp .env.example .env
```

### 2.2 Edit .env with Your Details

```
PRIVATE_KEY=your_private_key_without_0x
MUMBAI_RPC_URL=https://rpc-mumbai.maticvigil.com/
GOERLI_RPC_URL=https://goerli.infura.io/v3/YOUR_INFURA_KEY
SEPOLIA_RPC_URL=https://sepolia.infura.io/v3/YOUR_INFURA_KEY
ETHERSCAN_API_KEY=your_etherscan_api_key
```

### 2.3 Get Required Keys

1. **Private Key**: From MetaMask
   - Open MetaMask → Settings → Security & Privacy
   - Click "Reveal Secret Recovery Phrase" or account export
   - Copy private key (WITHOUT the "0x" prefix)

2. **RPC URL**: From Infura (Free)
   - Go to https://www.infura.io
   - Sign up for free account
   - Create new project
   - Copy HTTPS endpoint

3. **Etherscan API Key**: (Optional, for verification)
   - Go to https://etherscan.io/apis
   - Sign up and create API key

## Step 3: Compile Smart Contract

```bash
# Compile contract
npx hardhat compile

# You should see:
# ✓ Compiled successfully (123 contracts)
```

## Step 4: Deploy to Testnet

### Option A: Mumbai Testnet (Recommended - Fastest/Cheapest)

```bash
# Get testnet MATIC from faucet
# https://faucet.polygon.technology

# Deploy to Mumbai
npx hardhat run scripts/deployToken.js --network mumbai

# Output will show:
# OutstandingToken deployed to: 0x...
```

### Option B: Goerli Testnet

```bash
# Get testnet ETH from faucet
# https://goerlifaucet.com

# Deploy to Goerli
npx hardhat run scripts/deployToken.js --network goerli
```

### Option C: Sepolia Testnet

```bash
# Get testnet ETH from faucet
# https://sepolia-faucet.pk910.de

# Deploy to Sepolia
npx hardhat run scripts/deployToken.js --network sepolia
```

## Step 5: Verify Deployment

### 5.1 Check Deployment Files

```bash
# Check if deployment.json was created
cat deployment.json

# Should show:
# {
#   "network": "mumbai",
#   "contractAddress": "0x...",
#   "deployerAddress": "0x...",
#   ...
# }
```

### 5.2 Verify on Block Explorer

1. Go to appropriate explorer:
   - Mumbai: https://mumbai.polygonscan.com
   - Goerli: https://goerli.etherscan.io
   - Sepolia: https://sepolia.etherscan.io

2. Search for your contract address

3. Confirm:
   - ✓ Contract created
   - ✓ Initial supply minted
   - ✓ Token details correct

### 5.3 Verify in Contract Explorer

```bash
# View contract info
npx hardhat verify --network mumbai YOUR_CONTRACT_ADDRESS \
  "Outstanding Token" "OUT" "0xYourTaxWallet" "1000000"
```

## Step 6: Import Token to MetaMask

### 6.1 Automatic Import

1. In MetaMask, click "Import Tokens"
2. Paste contract address from deployment.json
3. Token details auto-fill
4. Click "Import"

### 6.2 Manual Import

If auto-import doesn't work:

1. Click "Add Token" in MetaMask
2. Fill in:
   - **Token Contract Address**: Your contract address
   - **Token Symbol**: OUT (or your symbol)
   - **Decimals**: 18
3. Click "Add Custom Token"

### 6.3 Verify Token Appears

- Token should now appear in MetaMask
- Shows balance (usually all tokens go to deployer)
- You can now transfer/send the token

## Step 7: Start Frontend Application

### 7.1 Update Contract Address (if needed)

In `client/src/App.js`, verify contract address:

```javascript
const [contractAddress, setContractAddress] = useState(
  "0xYourContractAddress" // Update this!
);
```

Or it will auto-load from deployment.json if in public folder.

### 7.2 Start React App

```bash
cd client
npm start

# Opens at http://localhost:3000
```

### 7.3 Connect Wallet

1. Click "Connect Wallet"
2. MetaMask popup appears
3. Select account and network
4. Click "Connect"
5. App loads token information

## Step 8: Test All Features

### Test Transfer

1. Get a test address (create another MetaMask account)
2. Click "Transfer Tokens"
3. Enter address and amount
4. Click "Transfer"
5. Verify:
   - Transaction appears in MetaMask
   - Token balance decreases by amount + 5% tax
   - Recipient receives tokens

### Test Burn

1. Enter amount to burn
2. Click "Burn"
3. Verify tokens are permanently removed

### Test Mint (Owner Only)

1. Enter recipient address and amount
2. Click "Mint"
3. Verify tokens are created (if owner)

### Test Balance Check

1. Click "Refresh" button
2. Verify balance updates

### Test Token Info

1. View "Token Information" card
2. Verify all details match deployment

## Step 9: Advanced Configuration (Owner Only)

Once connected as owner, you can:

### Change Tax Fee

```javascript
// Via web3utils
await setTaxFee(3); // Set to 3%
```

### Change Tax Wallet

```javascript
await setTaxWallet("0xNewWalletAddress");
```

### Blacklist/Whitelist Addresses

```javascript
await setBlacklist("0xAddress", true);  // Block address
await setWhitelist("0xAddress", true);  // Exempt from limits
```

### Pause/Unpause Contract

```javascript
await pauseContract();   // Stop all transfers
await unpauseContract(); // Resume transfers
```

## Step 10: Deploy to Mainnet (Production)

⚠️ **CRITICAL**: Only do this after extensive testing!

### 10.1 Final Checks

- [ ] All features tested on testnet
- [ ] Contract verified on block explorer
- [ ] Security audit completed (recommended)
- [ ] Sufficient mainnet balance (ETH/MATIC + gas)
- [ ] Private key secured
- [ ] Emergency procedures documented

### 10.2 Mainnet Deployment

```bash
# For Polygon Mainnet
npx hardhat run scripts/deployToken.js --network polygon

# For Ethereum Mainnet
npx hardhat run scripts/deployToken.js --network ethereum
```

### 10.3 Verify Mainnet Deployment

```bash
# Verify on Etherscan
npx hardhat verify --network ethereum YOUR_CONTRACT_ADDRESS \
  "Outstanding Token" "OUT" "0xTaxWallet" "1000000"

# Or on Polygonscan
npx hardhat verify --network polygon YOUR_CONTRACT_ADDRESS \
  "Outstanding Token" "OUT" "0xTaxWallet" "1000000"
```

## Troubleshooting

### Error: "Cannot find module 'dotenv'"

```bash
npm install dotenv
```

### Error: "Failed to connect to network"

1. Check .env RPC URL is correct
2. Verify PRIVATE_KEY is set
3. Test RPC URL in browser (should return JSON)

### Error: "Insufficient Balance"

1. Get testnet tokens from faucet
2. Wait for transactions to confirm
3. Verify correct account selected in MetaMask

### Error: "Contract Compilation Failed"

```bash
# Clear build artifacts
rm -rf artifacts/
rm -rf cache/

# Recompile
npx hardhat compile
```

### MetaMask Won't Connect

1. Refresh browser (Ctrl+R or Cmd+R)
2. Unlock MetaMask
3. Check network selection matches deployment network
4. Try restarting MetaMask

### Token Not Showing Balance After Transfer

1. Wait 30 seconds for block confirmation
2. Click "Refresh" button in app
3. Try manual import in MetaMask
4. Check if address is blacklisted

## Common Issues & Solutions

| Issue | Solution |
|-------|----------|
| "Nonce too low" | Increment nonce or reset account in MetaMask settings |
| "Gas limit exceeded" | Increase gas limit or reduce transaction size |
| "Out of gas" | Increase gas price in MetaMask |
| "Already imported token" | Remove token first, then re-import |
| "Invalid contract address" | Double-check address for typos |
| "Rate limit exceeded" | Wait a few seconds, reduce request frequency |

## Next Steps

1. **Customize**:
   - Change token name/symbol
   - Adjust tax rate
   - Modify max wallet limit

2. **Enhance**:
   - Add more frontend features
   - Implement governance
   - Add staking mechanism

3. **Promote**:
   - Share contract address
   - Create token listing
   - Market token launch

4. **Secure**:
   - Get professional audit
   - Use multi-sig wallet for owner
   - Document procedures

## Support Resources

- **Hardhat Docs**: https://hardhat.org/docs
- **OpenZeppelin**: https://docs.openzeppelin.com
- **Solidity**: https://docs.soliditylang.org
- **MetaMask**: https://docs.metamask.io
- **Web3.js**: https://web3js.readthedocs.io
- **Ethers.js**: https://docs.ethers.org

---

**Deployment complete!** 🎉

Your Outstanding Token is now live and ready to use.
