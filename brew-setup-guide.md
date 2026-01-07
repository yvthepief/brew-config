# Homebrew Package Migration Guide

## Export packages from current machine
```bash
# Generate Brewfile with descriptions
brew bundle dump --describe --force

# Optional: Check what's installed
brew list --formula  # Command-line tools
brew list --cask     # GUI applications
```

## Set up new machine
```bash
# 1. Install Homebrew (if needed)
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# 2. Copy Brewfile to new machine, then install everything
brew bundle install

# 3. Optional: Install only specific types
brew bundle install --no-cask     # Only formulae, skip GUI apps
brew bundle install --no-vscode   # Skip VS Code extensions
```

## Maintenance commands
```bash
# Update Brewfile with new packages
brew bundle dump --describe --force

# Check what would be installed/updated
brew bundle check

# Cleanup packages not in Brewfile
brew bundle cleanup --force

# Update all packages
brew update && brew upgrade
```

## Tips
- Keep your Brewfile in version control (git) for easy syncing
- Run `brew bundle dump --describe --force` periodically to update it
- The `--describe` flag adds helpful comments about what each package does