# Quick Start: Pinata IPFS Integration

## 5-Minute Setup

### Step 1: Get Pinata API Keys (2 min)

```bash
1. Visit: https://www.pinata.cloud
2. Create Free Account
3. Click "API Keys" → "+ New Key"
4. Copy API Key and API Secret
```

### Step 2: Add Keys to App (1 min)

Create `client/.env.local`:
```env
REACT_APP_PINATA_API_KEY=your_key_here
REACT_APP_PINATA_SECRET_KEY=your_secret_here
```

### Step 3: Restart App (1 min)

```bash
cd client
npm start
```

### Step 4: Upload Photo (1 min)

1. Connect MetaMask wallet
2. Click "Select Photo"
3. Choose image file
4. Click "Upload to IPFS"
5. Done! ✅

## File Structure

```
client/src/
├── components/
│   └── PhotoUpload.js          # Photo upload UI
├── utils/
│   └── PinataService.js        # IPFS service
├── styles/
│   └── PhotoUpload.css         # Component styles
└── App.js                       # Updated with PhotoUpload
```

## Supported Image Formats

- JPEG/JPG
- PNG
- WebP
- GIF
- SVG
- BMP

## Common Commands

```bash
# Install dependencies
npm install

# Run app
npm start

# Build for production
npm run build

# Test Pinata connection
curl "https://api.pinata.cloud/data/testAuthentication" \
  -H "pinata_api_key: YOUR_API_KEY" \
  -H "pinata_secret_api_key: YOUR_SECRET_KEY"
```

## File Size Limits

- Max upload: 50MB (configured)
- Max storage (free): 1GB total
- Gateway accessible: Always

## API Endpoints Used

```javascript
POST /pinning/pinFileToIPFS        // Upload file
POST /pinning/pinJSONToIPFS        // Upload metadata
DELETE /pinning/unpin/{ipfsHash}   // Remove file
GET /data/testAuthentication       // Test connection
```

## Example IPFS Hash

```
QmXxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

### Access via Gateway
```
https://gateway.pinata.cloud/ipfs/QmXxxx...
```

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Keys not working | Check `.env.local` exists in `client/` folder |
| Upload fails | Check file size < 50MB |
| Image won't load | Wait 30s for IPFS propagation |
| API error | Verify keys are correct in Pinata dashboard |

## Next Steps

✅ Upload photos to IPFS
✅ Share IPFS hashes with others
✅ Monitor usage in Pinata dashboard
✅ Store hashes on smart contract
✅ Build decentralized photo gallery

## Docs

- [Full Pinata Guide](./PINATA_GUIDE.md)
- [Pinata Docs](https://docs.pinata.cloud)
- [IPFS Docs](https://docs.ipfs.tech)
