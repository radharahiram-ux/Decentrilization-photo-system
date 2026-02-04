#!/bin/bash
# Outstanding Token - Quick Command Reference

# ============================================
# SETUP & INSTALLATION
# ============================================

# Install all dependencies
npm install:all

# Install individual parts
npm install                    # Install Hardhat dependencies
cd client && npm install       # Install React dependencies

# ============================================
# SMART CONTRACT OPERATIONS
# ============================================

# Compile smart contract
npx hardhat compile

# Run tests
npx hardhat test

# Start local Hardhat node
npx hardhat node

# ============================================
# DEPLOYMENT COMMANDS
# ============================================

# Deploy to Mumbai Testnet
npm run deploy:mumbai

# Deploy to Goerli Testnet
npm run deploy:goerli

# Deploy to Sepolia Testnet
npm run deploy:sepolia

# Deploy to Polygon Mainnet
npm run deploy:polygon

# Or use general deploy
npx hardhat run scripts/deployToken.js --network mumbai

# ============================================
# FRONTEND OPERATIONS
# ============================================

# Start development server
npm run client

# Build for production
npm run client:build

# Or navigate to client
cd client
npm start                      # Development
npm run build                  # Production
npm test                       # Tests

# ============================================
# HARDHAT COMMANDS
# ============================================

# List available accounts
npx hardhat accounts

# Show network configuration
npx hardhat networks

# Get help
npx hardhat help
npx hardhat help compile
npx hardhat help run

# Clean build artifacts
npx hardhat clean

# ============================================
# ENVIRONMENT SETUP
# ============================================

# Create .env file from example
cp .env.example .env

# Edit environment variables
# Add your:
# - PRIVATE_KEY
# - RPC URLs
# - API KEYS

# ============================================
# TESTING COMMANDS
# ============================================

# Run all tests
npx hardhat test

# Run specific test file
npx hardhat test test/OutstandingToken.js

# Run with coverage
npx hardhat coverage

# Run tests with more details
npx hardhat test --verbose

# ============================================
# VERIFICATION & CHECKING
# ============================================

# Verify contract on Etherscan (after deployment)
npx hardhat verify --network mumbai DEPLOYED_ADDRESS \
  "Outstanding Token" "OUT" "0xTaxWallet" "1000000"

# Check if contracts compile
npx hardhat compile --check

# Show gas report
npx hardhat test --gas-report

# ============================================
# DEBUGGING
# ============================================

# Run hardhat console
npx hardhat console

# Connect to local node console
npx hardhat console --network localhost

# View contract in Remix
# Copy contract code and go to https://remix.ethereum.org

# ============================================
# DEVELOPMENT WORKFLOW
# ============================================

# 1. Start local node in one terminal
npx hardhat node

# 2. In another terminal, deploy
npx hardhat run scripts/deployToken.js --network localhost

# 3. In third terminal, start frontend
cd client
npm start

# 4. Open browser to http://localhost:3000

# ============================================
# USEFUL UTILITIES
# ============================================

# Get test network ETH/MATIC
# Mumbai: https://faucet.polygon.technology
# Goerli: https://goerlifaucet.com
# Sepolia: https://sepolia-faucet.pk910.de

# View on block explorer
# Mumbai: https://mumbai.polygonscan.com/address/YOUR_ADDRESS
# Goerli: https://goerli.etherscan.io/address/YOUR_ADDRESS
# Sepolia: https://sepolia.etherscan.io/address/YOUR_ADDRESS
# Mainnet: https://etherscan.io/address/YOUR_ADDRESS

# ============================================
# IMPORTANT PATHS
# ============================================

# Smart Contract
# Location: contracts/OutstandingToken.sol

# Deployment Script
# Location: scripts/deployToken.js

# Frontend App
# Location: client/src/App.js

# Web3 Utilities
# Location: client/src/utils/Web3Utils.js

# Components
# Location: client/src/components/

# Configuration
# Location: hardhat.config.js

# ============================================
# ENVIRONMENT VARIABLES NEEDED
# ============================================

# Required for deployment:
# PRIVATE_KEY=your_private_key_here

# Optional RPC URLs:
# MUMBAI_RPC_URL=https://rpc-mumbai.maticvigil.com/
# GOERLI_RPC_URL=https://goerli.infura.io/v3/YOUR_KEY
# SEPOLIA_RPC_URL=https://sepolia.infura.io/v3/YOUR_KEY
# POLYGON_RPC_URL=https://polygon-rpc.com/
# ETH_RPC_URL=https://mainnet.infura.io/v3/YOUR_KEY

# Optional API Keys:
# ETHERSCAN_API_KEY=your_api_key_here

# ============================================
# NETWORK CHAIN IDS
# ============================================

# 31337   - Localhost (for local testing)
# 5       - Goerli Testnet (Ethereum)
# 11155111 - Sepolia Testnet (Ethereum)
# 80001   - Mumbai Testnet (Polygon)
# 137     - Polygon Mainnet
# 1       - Ethereum Mainnet

# ============================================
# TROUBLESHOOTING COMMANDS
# ============================================

# Clear cache and rebuild
npx hardhat clean
npx hardhat compile

# Fix npm issues
rm -rf node_modules package-lock.json
npm install

# Fix client issues
cd client
rm -rf node_modules package-lock.json
npm install
cd ..

# Check Node version
node --version     # Should be v16+

# Check npm version
npm --version

# Show hardhat config
npx hardhat config

# ============================================
# PRODUCTION DEPLOYMENT CHECKLIST
# ============================================

# 1. Test thoroughly
npx hardhat test

# 2. Compile
npx hardhat compile

# 3. Deploy to testnet first
npx hardhat run scripts/deployToken.js --network sepolia

# 4. Verify on testnet
npx hardhat verify --network sepolia YOUR_ADDRESS ...

# 5. Test frontend with testnet contract

# 6. Security review
# - Review contract code
# - Check gas optimization
# - Verify error handling

# 7. Deploy to mainnet
npx hardhat run scripts/deployToken.js --network polygon

# 8. Verify on mainnet
npx hardhat verify --network polygon YOUR_ADDRESS ...

# 9. Monitor and maintain
# - Check transaction logs
# - Monitor contract events
# - Track gas usage

# ============================================
# QUICK REFERENCE - COMMON TASKS
# ============================================

# Task: Setup project from scratch
# $ npm install:all
# $ cp .env.example .env
# $ [Edit .env with your keys]
# $ npx hardhat compile

# Task: Deploy to testnet
# $ npx hardhat run scripts/deployToken.js --network mumbai
# $ [Copy contract address]

# Task: Run frontend
# $ npm run client
# $ [Opens localhost:3000]

# Task: Run tests
# $ npx hardhat test

# Task: Get help
# $ npx hardhat help
# $ cat README_TOKEN.md
# $ cat DEPLOYMENT_GUIDE.md

# Task: Switch network
# [In MetaMask extension - click network selector]

# Task: Import token to MetaMask
# [Click Add Token → Paste contract address → Confirm]

# ============================================
# PERFORMANCE COMMANDS
# ============================================

# Check gas usage
npx hardhat test --gas-report

# Optimize contracts
# [Manually optimize Solidity code]
# [Use gas optimization techniques]

# Check contract size
npx hardhat size-contracts

# ============================================
# SECURITY COMMANDS
# ============================================

# Run static analysis
npx hardhat check

# Test security
npx hardhat test --grep "security"

# Audit dependencies
npm audit

# ============================================
# MONITORING & LOGS
# ============================================

# View node logs
npx hardhat node --verbose

# Save logs to file
npx hardhat test > test-results.log

# Monitor contract on explorer
# Etherscan: https://etherscan.io
# PolygonScan: https://polygonscan.com

# ============================================

# For more information:
# - README_TOKEN.md - Feature documentation
# - DEPLOYMENT_GUIDE.md - Step-by-step setup
# - API_REFERENCE.md - Function reference
# - PROJECT_SUMMARY.md - Project overview
