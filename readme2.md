# WSL Development Environment - Complete Setup Guide

## Prerequisites
- Windows 10 version 2004+ or Windows 11
- Administrator access

## 1. Install WSL and Ubuntu
```powershell
# In PowerShell (Run as Administrator):
wsl --install
```
**After installation:**
1. Restart your computer
2. Open Ubuntu from Start Menu
3. Create username and password when prompted

## 2. Access Your WSL Environment

### Quick Access Methods
```powershell
# From PowerShell
wsl

# From Windows Terminal
# Use Ctrl + Shift + 2 or select Ubuntu from dropdown
```

### Essential Navigation
```bash
# Go to home directory
cd ~

# Check current location
pwd

# List files and directories
ls -la
```

## 3. System Setup and Essential Tools
```bash
# Update system packages
sudo apt update && sudo apt upgrade -y

# Install essential development tools
sudo apt install build-essential git curl wget unzip tree python3-venv python3-full -y
```

## 4. Development Environment Setup

### Node.js Installation
```bash
# Install Node.js LTS
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt install nodejs -y

# Verify installation
node --version
npm --version
```

### Python Environment
```bash
# Python is already installed, verify versions
python3 --version
pip3 --version

# Create virtual environments as needed
python3 -m venv ~/venvs/myproject
source ~/venvs/myproject/bin/activate
```

## 5. Git Configuration

### Basic Git Setup
```bash
# Set global Git credentials
git config --global user.name "your-username"
git config --global user.email "your-email@example.com"

# Configure git to store credentials
git config --global credential.helper store
```

### SSH Setup for GitHub
```bash
# Generate SSH key
ssh-keygen -t ed25519 -C "your-email@example.com"

# Start SSH agent
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519

# Display public key to copy to GitHub
cat ~/.ssh/id_ed25519.pub
```

### Add SSH Key to GitHub
1. Go to GitHub.com → Settings → SSH and GPG keys
2. Click "New SSH key"
3. Paste your public key
4. Save

## 6. Project Directory Setup

### Create Development Structure
```bash
# Create projects directory in Ubuntu home
mkdir ~/Code
cd ~/Code

# Clone repository with SSH
git clone git@github.com:username/repo-name.git
cd repo-name

# Or initialize new repository
git init
git remote add origin git@github.com:username/repo-name.git
```

### File System Best Practices
- **Ubuntu projects**: Keep in `~/Code/` (Linux filesystem)
- **Windows access**: Via `/mnt/c/Users/username/`
- **Performance**: Use Linux filesystem for WSL projects

## 7. VS Code Integration
```bash
# Install VS Code on Windows first
# Install "WSL" extension in VS Code
# Open project from WSL terminal:
code .
```

## 8. Essential WSL Commands

### Navigation & File Management
```bash
# Home directory
cd ~

# Check location
pwd

# List files with details
ls -la

# File permissions
chmod +x filename
sudo chown -R $USER:$USER directory/
```

### System Management
```bash
# Check system info
uname -a
lsb_release -a

# Check versions
node --version
python3 --version
git --version

# Process management
ps aux
htop
```

## 9. Troubleshooting Common Issues

### Git Permission Issues
```bash
# Fix file ownership
sudo chown -R $USER:$USER .git/

# Fix "dubious ownership" error
git config --global --add safe.directory "*"
```

### Python Virtual Environment Issues
```bash
# For externally-managed-environment error:
python3 -m venv venv
source venv/bin/activate
pip install package-name
```

### WSL Performance
- Keep projects in Linux filesystem (`~/Code/`)
- Use WSL2 for better performance
- Avoid Windows antivirus scanning WSL directories

## Quick Reference

### Daily Workflow
```bash
# Start WSL
wsl

# Navigate to project
cd ~/Code/your-project

# Activate Python virtual environment (if needed)
source venv/bin/activate

# Open in VS Code
code .

# Git workflow
git status
git add .
git commit -m "your message"
git push
```

### Environment Verification
```bash
# Check all installations
node --version && npm --version
python3 --version && pip3 --version
git --version
code --version
```
