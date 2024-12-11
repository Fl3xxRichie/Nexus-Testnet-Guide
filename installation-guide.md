# Nexus CLI Installation Guide

A comprehensive guide for installing and running the Nexus CLI on Android, Windows, and macOS.

## Table of Contents
- [Android Installation (Termux)](#android-installation-termux)
- [Windows Installation](#windows-installation)
- [macOS Installation](#macos-installation)
- [Troubleshooting](#troubleshooting)

## Android Installation (Termux)

### Prerequisites
- Android device running Android 7.0 or higher
- At least 2GB of free storage
- Stable internet connection

### Step 1: Install Termux
1. Uninstall Termux if you got it from Play Store
2. Download and install F-Droid from: https://f-droid.org
3. Install Termux from F-Droid

### Step 2: Set Up Termux
```bash
# Update Termux packages
pkg update
pkg upgrade -y

# Install required packages
pkg install proot-distro
pkg install curl
pkg install wget
```

### Step 3: Install Ubuntu on Termux
```bash
# Install Ubuntu
proot-distro install ubuntu

# Login to Ubuntu
proot-distro login ubuntu
```

### Step 4: Install Dependencies in Ubuntu
```bash
# Update package list
apt update
apt upgrade -y

# Install essential build tools
apt install -y build-essential
apt install -y clang
apt install -y make
apt install -y gcc
apt install -y pkg-config

# Install required libraries
apt install -y libssl-dev
apt install -y libcrypto++-dev
apt install -y libc6-dev
apt install -y zlib1g-dev

# Set up library paths
export LD_LIBRARY_PATH=/usr/lib:/usr/local/lib
export PKG_CONFIG_PATH=/usr/lib/pkgconfig:/usr/local/lib/pkgconfig
```

### Step 5: Install Nexus CLI
```bash
curl https://cli.nexus.xyz/ | sh
```

## Windows Installation

### Prerequisites
- Windows 10 version 2004 or higher (Build 19041 or higher)
- 4GB RAM minimum
- Administrator privileges

### Step 1: Install WSL
1. Open PowerShell as Administrator and run:
```powershell
wsl --install
```
2. Restart your computer
3. After restart, run:
```powershell
wsl --set-default-version 2
```

### Step 2: Install Ubuntu
1. Open Microsoft Store
2. Search for "Ubuntu"
3. Click "Get" or "Install"
4. Launch Ubuntu
5. Set up username and password

### Step 3: Install Dependencies
```bash
# Update package list
sudo apt update
sudo apt upgrade -y

# Install required packages
sudo apt install -y build-essential
sudo apt install -y pkg-config
sudo apt install -y libssl-dev
sudo apt install -y libcrypto++-dev
sudo apt install -y gcc
sudo apt install -y libc6-dev
sudo apt install -y zlib1g-dev
```

### Step 4: Install Nexus CLI
```bash
curl https://cli.nexus.xyz/ | sh
```

## macOS Installation

### Prerequisites
- macOS 10.15 or higher
- Command Line Tools for Xcode

### Step 1: Install Homebrew (if not installed)
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### Step 2: Install Dependencies
```bash
# Install required packages
brew install openssl
brew install pkg-config

# Link OpenSSL
brew link openssl --force
```

### Step 3: Install Nexus CLI
```bash
curl https://cli.nexus.xyz/ | sh
```

## Running the Program

### Starting the Program
```bash
nexus
```

### Keeping the Program Running
```bash
# Run in background
nohup nexus &

# Auto-restart if crashes
while true; do
    nexus
    sleep 1
done
```

## Troubleshooting

### Common Issues and Solutions

#### Android/Termux Issues
1. "linker cc not found":
```bash
apt install -y build-essential
```

2. SSL/Crypto errors:
```bash
apt install -y libssl-dev libcrypto++-dev
```

#### Windows Issues
1. WSL installation fails:
```powershell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

2. Library errors:
```bash
sudo apt install --reinstall build-essential libssl-dev
```

#### macOS Issues
1. OpenSSL errors:
```bash
brew reinstall openssl
export LIBRARY_PATH=$LIBRARY_PATH:/usr/local/opt/openssl/lib/
```

### General Troubleshooting Steps
1. Check if program is running:
```bash
ps aux | grep nexus
```

2. Kill existing instances:
```bash
pkill nexus
```

3. Clear temporary files:
```bash
rm -rf ~/.nexus/temp/*
```

## Support and Updates

### Getting Help
- Twitter: https://twitter.com/flexxrichie


### Checking for Updates
```bash
nexus update
```


