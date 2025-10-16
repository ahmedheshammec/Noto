## When to Use This Guide

Use this nuclear approach when you encounter these npm errors with global packages:

- `ENOTEMPTY: directory not empty, rename`
- `EACCES: permission denied, rename`
- `EPERM: operation not permitted, rename`
- `EBUSY: resource busy or locked, rename`

## The Problem

NPM tries to update packages "atomically" by:

1. Downloading new version to temp location
2. Renaming old directory to backup name ← **Often fails here**
3. Renaming new directory to final location
4. Deleting backup

On macOS (and sometimes Windows/Linux), step 2 can fail due to:

- Extended attributes (macOS quarantine flags)
- File locks from IDEs or other processes
- Permission oddities
- Antivirus interference

## The Nuclear Solution Template

### 1. Create the Base Script

```bash
# Create the directory if it doesn't exist
mkdir -p ~/bin

# Create the template script
cat > ~/bin/fix-npm-package-template.sh << 'EOF'
#!/bin/bash
set -e

PACKAGE_NAME="$1"
PACKAGE_SCOPE="$2"

if [ -z "$PACKAGE_NAME" ]; then
    echo "Usage: $0 <package-name> [scope]"
    echo "Examples:"
    echo "  $0 claude-code @anthropic-ai"
    echo "  $0 typescript"
    echo "  $0 create-react-app"
    exit 1
fi

echo "🧹 Using nuclear approach to fix $PACKAGE_NAME..."

# Remove all traces of the package
if [ -n "$PACKAGE_SCOPE" ]; then
    echo "Removing scoped package: $PACKAGE_SCOPE/$PACKAGE_NAME..."
    rm -rf ~/.nvm/versions/node/v*/lib/node_modules/$PACKAGE_SCOPE/
    rm -f ~/.nvm/versions/node/v*/bin/$PACKAGE_NAME
    rm -rf ~/.nvm/versions/node/v*/lib/node_modules/$PACKAGE_SCOPE/.*
    FULL_PACKAGE="$PACKAGE_SCOPE/$PACKAGE_NAME"
else
    echo "Removing package: $PACKAGE_NAME..."
    rm -rf ~/.nvm/versions/node/v*/lib/node_modules/$PACKAGE_NAME/
    rm -f ~/.nvm/versions/node/v*/bin/$PACKAGE_NAME
    rm -rf ~/.nvm/versions/node/v*/lib/node_modules/.$PACKAGE_NAME*
    FULL_PACKAGE="$PACKAGE_NAME"
fi

# Clean npm thoroughly
echo "Cleaning npm cache..."
npm cache clean --force
rm -rf ~/.npm-cache 2>/dev/null || true

# Fresh install
echo "📦 Installing $FULL_PACKAGE fresh..."
npm install -g "$FULL_PACKAGE"

echo "✅ Done!"
if command -v "$PACKAGE_NAME" &> /dev/null; then
    echo "Version: $($PACKAGE_NAME --version 2>/dev/null || echo 'Installed successfully')"
else
    echo "Package installed successfully (no --version command available)"
fi
EOF

chmod +x ~/bin/fix-npm-package-template.sh
```

### 2. Create Package-Specific Scripts

For each problematic package, create a dedicated script:

#### Example: TypeScript

```bash
cat > ~/bin/fix-typescript.sh << 'EOF'
#!/bin/bash
set -e

echo "🧹 Using nuclear approach to fix TypeScript..."

# Remove all traces
rm -rf ~/.nvm/versions/node/v*/lib/node_modules/typescript/
rm -f ~/.nvm/versions/node/v*/bin/tsc
rm -f ~/.nvm/versions/node/v*/bin/tsserver
rm -rf ~/.nvm/versions/node/v*/lib/node_modules/.typescript*

# Clean and reinstall
npm cache clean --force
rm -rf ~/.npm-cache 2>/dev/null || true
npm install -g typescript

echo "✅ Done!"
tsc --version
EOF

chmod +x ~/bin/fix-typescript.sh
```

#### Example: Create React App

```bash
cat > ~/bin/fix-create-react-app.sh << 'EOF'
#!/bin/bash
set -e

echo "🧹 Using nuclear approach to fix Create React App..."

# Remove all traces
rm -rf ~/.nvm/versions/node/v*/lib/node_modules/create-react-app/
rm -f ~/.nvm/versions/node/v*/bin/create-react-app
rm -rf ~/.nvm/versions/node/v*/lib/node_modules/.create-react-app*

# Clean and reinstall
npm cache clean --force
rm -rf ~/.npm-cache 2>/dev/null || true
npm install -g create-react-app

echo "✅ Done!"
create-react-app --version
EOF

chmod +x ~/bin/fix-create-react-app.sh
```

### 3. Add Convenient Aliases

Add these to your `~/.zshrc` or `~/.bashrc`:

```bash
cat >> ~/.zshrc << 'EOF'

# NPM Package Fix Aliases
alias npm-fix='~/bin/fix-npm-package-template.sh'
alias fix-claude='~/bin/fix-claude-npm.sh'
alias fix-typescript='~/bin/fix-typescript.sh'
alias fix-cra='~/bin/fix-create-react-app.sh'

# Generic npm troubleshooting
alias npm-nuclear='npm cache clean --force && rm -rf ~/.npm-cache ~/.npm/_logs 2>/dev/null || true'
alias npm-check-global='npm list -g --depth=0'
alias npm-outdated-global='npm outdated -g'
EOF

source ~/.zshrc
```

## Usage Examples

### Using the Template Script

```bash
# For scoped packages
npm-fix claude-code @anthropic-ai
npm-fix sdk @anthropic-ai

# For regular packages
npm-fix typescript
npm-fix create-react-app
npm-fix nodemon
```

### Using Package-Specific Scripts

```bash
fix-claude
fix-typescript
fix-cra
```

## Pre-Nuclear Diagnostic Steps

Before going nuclear, try these steps to identify the issue:

### 1. Check What's Running

```bash
# Check for processes using the package
lsof | grep package-name || echo "No processes found"

# Check for IDE integrations
ps aux | grep -i "vscode\|pycharm\|webstorm\|intellij" || echo "No IDEs running"
```

### 2. Check Extended Attributes (macOS)

```bash
# Check for quarantine flags
xattr -l ~/.nvm/versions/node/v*/lib/node_modules/package-name

# Remove quarantine if present
xattr -r -d com.apple.quarantine ~/.nvm/versions/node/v*/lib/node_modules/package-name 2>/dev/null || true
```

### 3. Check Permissions

```bash
# Check ownership
ls -la ~/.nvm/versions/node/v*/lib/node_modules/ | grep package-name

# Fix permissions if needed
chown -R $(whoami) ~/.nvm/versions/node/v*/lib/node_modules/package-name
```

### 4. Try Gentle Fix First

```bash
# Sometimes this works without going nuclear
npm cache clean --force
npm uninstall -g package-name
npm install -g package-name
```

## When NOT to Use Nuclear Approach

- **Production servers**: Always try gentle methods first
- **Shared systems**: Other users might be affected
- **Corporate environments**: May have package management policies
- **When you're unsure**: Test on a non-critical system first

## Prevention Tips

1. **Close IDEs before updating** packages they integrate with
2. **Keep npm updated**: `npm install -g npm@latest`
3. **Use package managers like Volta** or **fnm** instead of nvm for better isolation
4. **Consider using npx** instead of global installs for tools you use occasionally

## Alternative: Switch to npx

For packages you don't use constantly, consider using npx instead:

```bash
# Instead of global install
npm install -g create-react-app
create-react-app my-app

# Use npx (always latest version)
npx create-react-app my-app

# Create aliases for convenience
alias cra='npx create-react-app'
alias tsc='npx typescript'
```

## Troubleshooting the Nuclear Scripts

If the nuclear script fails:

1. **Check the paths**: Make sure your Node.js installation paths match the script
2. **Run with verbose output**: Add `set -x` after `set -e` in the script
3. **Check disk space**: `df -h` to ensure you have space
4. **Try manual cleanup**: Run each `rm` command individually to see which fails

## Quick Reference Card

Save this as a comment in your shell config:

```bash
# NPM Nuclear Fix Quick Reference
# ENOTEMPTY error -> npm-fix package-name [scope]
# IDE running -> Close IDE first, then npm-fix
# Permission issues -> chown -R $(whoami) ~/.nvm/versions/node/v*/lib/node_modules/
# Quarantine (macOS) -> xattr -r -d com.apple.quarantine package-path
# Complete reset -> npm-nuclear && npm install -g package-name
```

---

**Remember**: The nuclear approach is a last resort, but it's extremely reliable when npm's update mechanism fails. Most of the time, it's faster than debugging the underlying cause!
