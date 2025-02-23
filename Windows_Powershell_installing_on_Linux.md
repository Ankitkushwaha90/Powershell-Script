
# Installing PowerShell on Parrot Linux

PowerShell is available for Linux, including Parrot OS. Here’s how you can install and use PowerShell on Parrot Linux.

## 1. Install PowerShell on Parrot Linux

### Step 1: Update System Packages
Before installing PowerShell, update your system:

```bash
sudo apt update && sudo apt upgrade -y
```

### Step 2: Install Required Dependencies
PowerShell requires `libssl1.1`, which might not be available in Parrot OS by default. Install it manually:

```bash
sudo apt install -y wget apt-transport-https software-properties-common
```

### Step 3: Add Microsoft Repository

```bash
wget -q https://packages.microsoft.com/config/debian/11/packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
sudo apt update
```

### Step 4: Install PowerShell

```bash
sudo apt install -y powershell
```

## 2. Running PowerShell
After installation, launch PowerShell using:

```bash
pwsh
```

You should see a PowerShell prompt like this:

```powershell
PS /home/user>
```

## 3. Verify PowerShell Installation
Check the installed version of PowerShell:

```powershell
$PSVersionTable
```

## 4. Uninstall PowerShell (If Needed)
If you want to remove PowerShell from Parrot Linux:

```bash
sudo apt remove --purge powershell -y
sudo apt autoremove -y
```

## 5. Running PowerShell Scripts on Parrot Linux
PowerShell scripts (`.ps1` files) can be executed like this:

```powershell
pwsh script.ps1
```

If you face execution policy errors, allow scripts to run:

```powershell
Set-ExecutionPolicy Unrestricted -Scope Process
```

## 6. Install PowerShell Modules
You can install PowerShell modules for networking, security, and automation:

```powershell
Install-Module -Name PowerShellGet -Force -Scope CurrentUser
```

## 7. Using PowerShell for Networking in Linux
PowerShell works with Linux networking commands and PowerShell cmdlets:

```powershell
Test-NetConnection -ComputerName google.com
Get-NetIPAddress
```

However, some Windows-specific networking cmdlets may not work on Linux.

## Conclusion
Now, you have PowerShell installed and running on Parrot OS! 🎯

