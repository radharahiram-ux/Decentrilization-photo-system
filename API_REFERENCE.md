# Outstanding Token - API & Function Reference

## Web3 Utilities API

All Web3 interactions are handled through `client/src/utils/Web3Utils.js`

### Initialization Functions

#### `initializeWeb3()`
Initialize Web3 connection with MetaMask provider.

```javascript
import { initializeWeb3 } from './utils/Web3Utils';

await initializeWeb3();
```

**Returns**: Signer object
**Throws**: "MetaMask is not installed"

---

#### `requestAccounts()`
Request user to connect wallet accounts.

```javascript
const accounts = await requestAccounts();
```

**Returns**: Array of account addresses
**Example**: `["0x123...", "0x456..."]`

---

#### `getAccount()`
Get currently connected account address.

```javascript
const userAddress = await getAccount();
```

**Returns**: Connected account address (string)

---

#### `connectContract(contractAddress)`
Connect to deployed smart contract instance.

```javascript
import { connectContract } from './utils/Web3Utils';

connectContract("0xYourContractAddress");
```

**Parameters**:
- `contractAddress` (string): Deployed contract address

**Returns**: Contract instance

---

### Token Information Functions

#### `getTokenDetails()`
Retrieve all token information.

```javascript
const details = await getTokenDetails();
```

**Returns**: Object containing:
```javascript
{
  name: "Outstanding Token",
  symbol: "OUT",
  totalSupply: "1000000.0",
  decimals: 18,
  taxFee: "5",
  maxWalletAmount: "20000000.0",
  taxWallet: "0x...",
  isPaused: false,
  maxSupply: "1000000000.0"
}
```

---

#### `getBalance(address)`
Get token balance for an address.

```javascript
const balance = await getBalance("0x123...");
```

**Parameters**:
- `address` (string): Wallet address to check

**Returns**: Balance in tokens (string, formatted with 18 decimals)
**Example**: "1500.5" means 1500.5 OUT tokens

---

### Transaction Functions

#### `transferTokens(toAddress, amount)`
Send tokens to another address.

```javascript
const txHash = await transferTokens(
  "0xRecipientAddress",
  "100.5"  // Amount in tokens
);
```

**Parameters**:
- `toAddress` (string): Recipient wallet address
- `amount` (string): Amount in tokens

**Returns**: Transaction hash
**Throws**: 
- "Sender is blacklisted"
- "Recipient is blacklisted"
- "Exceeds max wallet"

**Note**: 5% tax applied automatically

---

#### `burnTokens(amount)`
Permanently destroy your own tokens.

```javascript
const txHash = await burnTokens("50");
```

**Parameters**:
- `amount` (string): Amount in tokens to burn

**Returns**: Transaction hash
**Note**: Removed from circulation permanently

---

#### `mintTokens(toAddress, amount)`
Create new tokens (owner only).

```javascript
const txHash = await mintTokens("0x123...", "1000");
```

**Parameters**:
- `toAddress` (string): Recipient address
- `amount` (string): Amount to mint

**Returns**: Transaction hash
**Throws**: 
- "Only owner can mint"
- "Exceeds max supply"

---

### Configuration Functions (Owner Only)

#### `setTaxFee(newFee)`
Change transaction tax percentage.

```javascript
await setTaxFee(3);  // Set to 3%
```

**Parameters**:
- `newFee` (number): New tax percentage (0-10)

**Constraints**: Max 10%, min 0%

---

#### `setTaxWallet(newWallet)`
Change tax recipient wallet.

```javascript
await setTaxWallet("0xNewWalletAddress");
```

**Parameters**:
- `newWallet` (string): New wallet address

**Throws**: "Cannot be zero address"

---

#### `setMaxWalletAmount(amount)`
Set maximum tokens a wallet can hold.

```javascript
await setMaxWalletAmount("50000000");  // 50M tokens
```

**Parameters**:
- `amount` (string): New max wallet amount

**Constraints**: Must be ≥ 1% of total supply

---

#### `setBlacklist(address, isBlacklisted)`
Block or unblock an address from trading.

```javascript
// Block an address
await setBlacklist("0x123...", true);

// Unblock an address
await setBlacklist("0x123...", false);
```

**Parameters**:
- `address` (string): Target address
- `isBlacklisted` (boolean): true to block, false to unblock

---

#### `setWhitelist(address, isWhitelisted)`
Exempt an address from wallet limits.

```javascript
// Whitelist an address
await setWhitelist("0x123...", true);

// Remove from whitelist
await setWhitelist("0x123...", false);
```

**Parameters**:
- `address` (string): Target address
- `isWhitelisted` (boolean): true to exempt, false to remove

---

### Control Functions (Owner Only)

#### `pauseContract()`
Stop all token transfers (emergency).

```javascript
await pauseContract();
```

**Effect**: No one can transfer tokens until unpaused

---

#### `unpauseContract()`
Resume token transfers.

```javascript
await unpauseContract();
```

**Effect**: Normal operations resume

---

### Status Check Functions

#### `checkBlacklist(address)`
Check if address is blacklisted.

```javascript
const isBlacklisted = await checkBlacklist("0x123...");
```

**Parameters**:
- `address` (string): Address to check

**Returns**: boolean

---

#### `checkWhitelist(address)`
Check if address is whitelisted.

```javascript
const isWhitelisted = await checkWhitelist("0x123...");
```

**Parameters**:
- `address` (string): Address to check

**Returns**: boolean

---

#### `checkTaxExempt(address)`
Check if address is tax exempt.

```javascript
const isTaxExempt = await checkTaxExempt("0x123...");
```

**Parameters**:
- `address` (string): Address to check

**Returns**: boolean

---

### Network Functions

#### `switchNetwork(chainId)`
Switch MetaMask to different network.

```javascript
await switchNetwork(80001);  // Switch to Mumbai
```

**Common Chain IDs**:
```javascript
31337  // Localhost
5      // Goerli
11155111  // Sepolia
80001  // Mumbai
137    // Polygon Mainnet
1      // Ethereum Mainnet
```

---

## React Component API

### WalletConnect Component

```jsx
<WalletConnect
  isConnected={boolean}
  account={string}
  onConnect={function}
/>
```

**Props**:
- `isConnected`: Is wallet connected
- `account`: Connected wallet address
- `onConnect`: Callback when connect button clicked

**Display**: Shows address or connect button

---

### Balance Component

```jsx
<Balance userAddress={string} />
```

**Props**:
- `userAddress`: Address to check balance for

**Display**: Current balance with refresh button

---

### TokenInfo Component

```jsx
<TokenInfo />
```

**Display**: Token statistics and information

---

### Transfer Component

```jsx
<Transfer onSuccess={function} />
```

**Props**:
- `onSuccess`: Callback on successful transfer

**Inputs**:
- Recipient address
- Amount to send

---

### Burn Component

```jsx
<Burn onSuccess={function} />
```

**Props**:
- `onSuccess`: Callback on successful burn

**Inputs**:
- Amount to burn

---

### Mint Component

```jsx
<Mint onSuccess={function} />
```

**Props**:
- `onSuccess`: Callback on successful mint

**Inputs**:
- Recipient address
- Amount to mint

---

## Error Handling

### Common Errors and Solutions

```javascript
try {
  await transferTokens(address, amount);
} catch (error) {
  if (error.message.includes("blacklist")) {
    // Address is blacklisted
  } else if (error.message.includes("max wallet")) {
    // Would exceed max wallet
  } else if (error.message.includes("Insufficient")) {
    // Not enough balance
  } else if (error.message.includes("Contract is paused")) {
    // Contract is paused
  }
}
```

---

## Integration Examples

### React Component Example

```jsx
import { getBalance, transferTokens } from './utils/Web3Utils';

function MyComponent() {
  const [balance, setBalance] = useState('0');

  useEffect(() => {
    async function loadBalance() {
      const bal = await getBalance(userAddress);
      setBalance(bal);
    }
    loadBalance();
  }, [userAddress]);

  const handleTransfer = async (to, amount) => {
    try {
      const txHash = await transferTokens(to, amount);
      console.log('Transfer successful:', txHash);
    } catch (error) {
      console.error('Transfer failed:', error);
    }
  };

  return (
    <div>
      <p>Balance: {balance} OUT</p>
      <button onClick={() => handleTransfer(to, 10)}>
        Send 10 OUT
      </button>
    </div>
  );
}
```

---

### Full Flow Example

```jsx
import { 
  initializeWeb3,
  requestAccounts,
  connectContract,
  getTokenDetails,
  transferTokens 
} from './utils/Web3Utils';

async function executeTransaction() {
  try {
    // 1. Initialize Web3
    await initializeWeb3();

    // 2. Request account access
    const accounts = await requestAccounts();
    
    // 3. Connect to contract
    connectContract("0x...");

    // 4. Get token info
    const details = await getTokenDetails();
    console.log('Token:', details.name);

    // 5. Execute transfer
    const txHash = await transferTokens(
      "0xRecipient...",
      "100"
    );
    console.log('Transaction:', txHash);

  } catch (error) {
    console.error('Error:', error);
  }
}
```

---

## Best Practices

### 1. Always Initialize Web3
```javascript
await initializeWeb3();
await requestAccounts();
```

### 2. Check Connection Before Operations
```javascript
const account = await getAccount();
if (!account) {
  // Show connect button
}
```

### 3. Handle Errors Gracefully
```javascript
try {
  await transferTokens(to, amount);
  showSuccess('Transfer successful!');
} catch (error) {
  showError('Transfer failed: ' + error.message);
}
```

### 4. Verify User Action
```javascript
const confirmed = window.confirm(
  `Send ${amount} OUT to ${to}?`
);
if (confirmed) {
  await transferTokens(to, amount);
}
```

### 5. Monitor Gas Prices
```javascript
// Always let user confirm in MetaMask
// Warn about high gas prices
```

---

## Constants

```javascript
// Token Details
const MAX_SUPPLY = "1000000000";     // 1 billion
const DECIMALS = 18;
const DEFAULT_TAX = 5;              // 5%
const MAX_TAX = 10;                 // 10% max
const MAX_WALLET_PERCENTAGE = 2;    // 2% of supply

// Chain IDs
const NETWORKS = {
  LOCALHOST: 31337,
  GOERLI: 5,
  SEPOLIA: 11155111,
  MUMBAI: 80001,
  POLYGON: 137,
  ETHEREUM: 1
};
```

---

## Testing

### Unit Test Example

```javascript
describe('TokenTransfer', () => {
  it('should transfer with tax', async () => {
    const txHash = await transferTokens(addr, "100");
    expect(txHash).toBeDefined();
  });

  it('should reject blacklisted addresses', async () => {
    await expect(
      transferTokens(blacklistedAddr, "100")
    ).rejects.toThrow('blacklisted');
  });
});
```

---

## Deployment Checklist

- [ ] All functions tested
- [ ] Error handling verified
- [ ] Gas optimization reviewed
- [ ] Security audit complete
- [ ] Documentation updated
- [ ] Team trained
- [ ] Monitoring set up
- [ ] Backup procedures documented

---

## Additional Resources

- [OpenZeppelin Docs](https://docs.openzeppelin.com)
- [ethers.js Documentation](https://docs.ethers.org)
- [Solidity by Example](https://solidity-by-example.org)
- [Web3 Development Guide](https://ethereum.org/developers)

---

**API Version**: 1.0.0
**Last Updated**: 2024
