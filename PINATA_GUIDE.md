# Pinata IPFS Integration Guide

## Overview

This project now includes **Pinata IPFS integration** for decentralized photo storage. Pinata makes it easy to store files on IPFS (InterPlanetary File System) with a simple API and robust infrastructure.

## What is Pinata?

**Pinata** is an IPFS (InterPlanetary File System) pinning service that allows you to:
- Upload files permanently to IPFS
- Access files via a reliable gateway
- Manage metadata alongside your files
- Ensure your content is always available

## Features

### Photo Upload Component
- **Decentralized Storage**: Upload photos to IPFS via Pinata
- **Metadata Management**: Store descriptions and file info with your photos
- **IPFS Gateway Access**: View photos directly from IPFS
- **Hash Copying**: Easy access to IPFS hashes for sharing
- **Progress Tracking**: Real-time upload progress indicator
- **Validation**: File type and size validation

### PinataService Utility
A complete service for managing IPFS operations:
- Upload files to IPFS
- Store JSON metadata
- Retrieve gateway URLs
- Test Pinata connection
- Unpin files when needed

## Setup Instructions

### 1. Create Pinata Account

Visit [Pinata.cloud](https://www.pinata.cloud) and create a free account:

```
1. Go to https://www.pinata.cloud
2. Sign up with email or OAuth
3. Verify your email
4. Navigate to API Keys section
```

### 2. Generate API Keys

Once logged in:

```
1. Click "API Keys" in the left sidebar
2. Click "+ New Key"
3. Select "Admin" permissions
4. Give it a name (e.g., "Outstanding Token App")
5. Create the key
6. Copy both "API Key" and "API Secret"
```

### 3. Configure Environment Variables

Update your `.env.local` file in the `client` directory:

```env
REACT_APP_PINATA_API_KEY=your_pinata_api_key_here
REACT_APP_PINATA_SECRET_KEY=your_pinata_secret_key_here
```

**Important**: Create a `.env.local` file in the `client/` directory, NOT the root directory.

Example `.env.local`:
```env
REACT_APP_PINATA_API_KEY=c7a9d8f7e8c9b1a2
REACT_APP_PINATA_SECRET_KEY=3f4e5d6c7b8a9f0e1d2c3b4a5f6e7d8c9b0a1f2e
```

### 4. Restart the Application

After adding environment variables, restart your React app:

```bash
cd client
npm start
```

## Usage

### Upload a Photo

1. **Open the Application**: Navigate to `http://localhost:3000`
2. **Connect Wallet**: Click "Connect Wallet" and approve MetaMask
3. **Navigate to Photo Upload**: The PhotoUpload component appears after wallet connection
4. **Select a Photo**: Click "Select Photo" and choose an image file
5. **Add Description** (optional): Add a description for your photo
6. **Click Upload**: Click "Upload to IPFS"
7. **Wait for Upload**: Monitor the progress bar (0-100%)
8. **View Result**: Once complete, see your photo in the "Uploaded Photos" section

### Access Your Photos

The component displays:
- **Photo Preview**: Thumbnail image
- **File Information**: Name, size, description
- **IPFS Hash**: Complete hash in monospace
- **View on IPFS**: Button to open photo on gateway
- **Copy Hash**: Button to copy hash to clipboard

### Using the PinataService Directly

```javascript
import PinataService from './utils/PinataService';

// Upload a file
const ipfsHash = await PinataService.uploadFile(file, 'my-photo');

// Upload JSON metadata
const metadataHash = await PinataService.uploadJSON({
  title: 'My Photo',
  description: 'A beautiful photo',
  tags: ['nature', 'landscape']
});

// Get gateway URL
const url = PinataService.getGatewayURL(ipfsHash);
// https://gateway.pinata.cloud/ipfs/QmXxxx...

// Test connection
const isConnected = await PinataService.testConnection();
```

## IPFS Concepts

### What is IPFS?

IPFS (InterPlanetary File System) is a peer-to-peer protocol for storing and accessing files, websites, applications, and data. Key concepts:

- **Content-Addressed**: Files are identified by their hash (cryptographic fingerprint)
- **Decentralized**: No single point of failure
- **Permanent**: Content remains accessible as long as peers pin it
- **Global Network**: Access files from anywhere in the world

### IPFS Hash (Content ID)

An IPFS hash looks like:
```
QmXxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

This hash is:
- **Unique**: Changes if file content changes
- **Permanent**: Same file always has same hash
- **Verifiable**: Content can be verified against hash

### Gateway URLs

Access IPFS content via HTTP gateway:
```
https://gateway.pinata.cloud/ipfs/QmXxxx...
```

Other popular gateways:
- `https://ipfs.io/ipfs/QmXxxx...`
- `https://cloudflare-ipfs.com/ipfs/QmXxxx...`
- `https://dweb.link/ipfs/QmXxxx...`

## File Size Limits

- **Pinata Free Plan**: Up to 1GB total storage
- **Upload Limit**: 100MB per file
- **Component Limit**: 50MB validation in app

## Pricing

### Pinata Plans

**Free Tier**:
- 1 GB storage
- Standard IPFS features
- Community support
- Great for development/testing

**Pro Plan** (Pay-as-you-go):
- Unlimited storage
- Bandwidth charges apply
- Priority support
- Advanced features

### Cost Estimation

Storage is typically $0.015 per GB per month (varies by plan).
Bandwidth has additional charges.

## Troubleshooting

### Issue: "Pinata API keys not configured"

**Solution**: 
```
1. Check .env.local exists in client/ directory
2. Verify REACT_APP_PINATA_API_KEY is set
3. Verify REACT_APP_PINATA_SECRET_KEY is set
4. Restart the React app (npm start)
```

### Issue: "Upload fails silently"

**Solutions**:
1. **Check file size**: Must be less than 50MB
2. **Check file type**: Must be a valid image format
3. **Check API keys**: Verify keys are correct
4. **Check quota**: Ensure Pinata account has storage available
5. **Check network**: Verify internet connection

### Issue: "Photo won't display from IPFS"

**Solutions**:
1. **Wait for propagation**: IPFS can take time to propagate
2. **Try different gateway**: Use alternative gateway URL
3. **Check IPFS hash**: Verify hash is correct
4. **Verify Pinata status**: Log into Pinata dashboard

## Best Practices

### Security

1. **Never expose keys publicly**:
   ```javascript
   // WRONG - Never do this!
   const key = "my_api_key_here";
   
   // RIGHT - Use environment variables
   const key = process.env.REACT_APP_PINATA_API_KEY;
   ```

2. **Use restricted keys in production**:
   - Create separate API keys for different apps
   - Use "Custom" permissions, not "Admin"
   - Restrict by IP if possible

### Storage Management

1. **Monitor storage usage**: Check Pinata dashboard regularly
2. **Implement unpinning**: Remove old files when no longer needed
3. **Backup hashes**: Store important IPFS hashes
4. **Use metadata**: Include descriptive information with files

### Performance

1. **Optimize image sizes**: Compress photos before upload
2. **Use WebP format**: More efficient than PNG/JPG
3. **Implement caching**: Cache gateway URLs
4. **Progressive loading**: Show spinner during upload

## Integration with Smart Contract

Store IPFS hashes on blockchain:

```solidity
// Smart Contract example
mapping(address => string[]) public userPhotos;

function storePhotoHash(string memory ipfsHash) public {
    userPhotos[msg.sender].push(ipfsHash);
}
```

JavaScript integration:
```javascript
const ipfsHash = await PinataService.uploadFile(file);
await contract.storePhotoHash(ipfsHash);
```

## Resources

- **Pinata Documentation**: https://docs.pinata.cloud
- **IPFS Docs**: https://docs.ipfs.tech
- **IPFS Gateway List**: https://ipfs.github.io/public-gateway-checker
- **Pinata Pricing**: https://www.pinata.cloud/pricing

## Support

### Pinata Support
- Documentation: https://docs.pinata.cloud
- Status Page: https://status.pinata.cloud
- Community: Discord, Twitter, GitHub

### IPFS Support
- Documentation: https://docs.ipfs.tech
- Community: Discuss.IPFS.io
- GitHub: https://github.com/ipfs

## Next Steps

1. ✅ Create Pinata account
2. ✅ Generate API keys
3. ✅ Set environment variables
4. ✅ Start uploading photos
5. ✅ Share IPFS hashes with others
6. ✅ Integrate with smart contract for permanent storage

---

**Ready to go decentralized?** Start uploading photos to IPFS today!
