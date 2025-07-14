# WSL Ubuntu Environment Guide

## Accessing WSL Ubuntu

### From PowerShell
```powershell
wsl
```

### From Windows Terminal
1. Open Windows Terminal
2. Click dropdown arrow → Ubuntu
   - Or use keyboard shortcut: Ctrl + Shift + 2

## Navigation

### Essential Commands
1. Go to Ubuntu home directory:
```bash
cd ~
```

2. Check current location:
```bash
pwd
```

3. List files and directories:
```bash
ls
```

## File System Structure

### Ubuntu File System
- Home directory: `/home/yourusername`
- Projects directory: `/home/yourusername/projects`

### Accessing Windows Files
- Windows C: drive: `/mnt/c`
- Your Windows user folder: `/mnt/c/Users/cruze`
- Windows Code folder: `/mnt/c/Users/cruze/Code`

## Best Practices
1. Use Ubuntu home directory (`~`) for Linux development
2. Keep Linux-specific projects in `/home/yourusername/projects`
3. Access Windows files through `/mnt/c` when needed
4. Use Linux commands only on Linux file system for better performance

## Development Environment
Your development environment includes:
- build-essential tools
- git
- curl
- wget
- nodejs & npm
- python3 & pip

## Quick Reference
```bash
# Update system
sudo apt update && sudo apt upgrade

# Check versions
node --version
python3 --version
git --version

# Create new project
mkdir ~/projects/new-project
cd ~/projects/new-project
```

