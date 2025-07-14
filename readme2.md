# Complete WSL Development Environment Setup Guide

## Initial Setup

### 1. Install WSL and Ubuntu
```powershell
# In PowerShell (Admin):
wsl --install
```
- After restart, open Ubuntu from Start Menu
- Set up username and password

### 2. Essential System Setup
```bash
# Update system
sudo apt update && sudo apt upgrade -y

# Install essential development tools
sudo apt install build-essential git curl wget unzip tree -y
```

### 3. Node.js Setup
```bash
# Add NodeSource repository and install Node.js
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt install nodejs -y

# Verify installation
node --version
```

### 4. Python Setup
```bash
# Install Python and pip
sudo apt install python3 python3-pip -y
```

### 5. GitHub CLI Setup
```bash
# Install GitHub CLI
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg
sudo chmod go+r /usr/share/keyrings/githubcli-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null
sudo apt update
sudo apt install gh -y
```

## Git Configuration

### 1. Basic Git Setup
```bash
# Set global Git credentials
git config --global user.name "your-username"
git config --global user.email "your-email@example.com"

# Configure git to store credentials
git config --global credential.helper store
```

### 2. SSH Setup for GitHub
```bash
# Generate SSH key
ssh-keygen -t ed25519 -C "your-email@example.com"

# Start SSH agent
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519

# Display public key to copy to GitHub
cat ~/.ssh/id_ed25519.pub
```

### 3. Add SSH Key to GitHub
1. Go to GitHub.com → Settings → SSH and GPG keys
2. Click "New SSH key"
3. Paste your public key
4. Save

## Repository Setup

### 1. Create and Clone Repository
```bash
# Create project directory
mkdir ~/Code && cd ~/Code

# Clone with SSH
git clone git@github.com:username/repo-name.git
cd repo-name

# Or initialize new repository
git init
git remote add origin git@github.com:username/repo-name.git
```

### 2. Fix Common WSL Git Issues
```bash
# Fix permissions if needed
sudo chown -R $USER:$USER .git/

# Fix "dubious ownership" error
git config --global --add safe.directory "*"
```

### 3. Branch Management
```bash
# Create and switch to development branch
git checkout -b develop

# Push to GitHub with upstream tracking
git push --set-upstream origin develop
```

## VS Code Integration
1. Install VS Code on Windows
2. Install "WSL" extension in VS Code
3. Open project from WSL:
```bash
code .
```

## Best Practices
1. Keep projects in Linux filesystem (`~/Code/`) not Windows
2. Use SSH for GitHub authentication
3. Run VS Code using `code .` from WSL terminal
4. Always create a development branch for new projects
5. Fix permissions immediately if you encounter issues

## Troubleshooting
- If git commands fail with permission errors:
  ```bash
  sudo chown -R $USER:$USER .git/
  ```
- If git complains about "dubious ownership":
  ```bash
  git config --global --add safe.directory "*"
  ```
- If GitHub authentication fails, ensure:
  1. SSH key is properly added to GitHub
  2. Using SSH URLs for remotes
  3. SSH agent is running
