
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

## 8. Complete List of PowerShell Networking Commands

### 8.1 Network Configuration Commands

View Network Information:

```powershell
Get-NetIPConfiguration
Get-NetIPAddress
Get-NetAdapter
Get-NetAdapterStatistics
Get-NetAdapter | Select-Object Name, MacAddress
```

Modify Network Configuration:

```powershell
Set-NetIPAddress -InterfaceAlias "Ethernet" -IPAddress "192.168.1.100" -PrefixLength 24 -DefaultGateway "192.168.1.1"
Set-NetIPInterface -InterfaceAlias "Wi-Fi" -Dhcp Enabled
Rename-NetAdapter -Name "Ethernet" -NewName "OfficeLAN"
Disable-NetAdapter -Name "Wi-Fi" -Confirm:$false
Enable-NetAdapter -Name "Wi-Fi"
```

### 8.2 Network Testing & Troubleshooting

```powershell
Test-Connection -ComputerName google.com -Count 4
Test-NetConnection -ComputerName google.com
Test-NetConnection -Port 443 -ComputerName google.com
(Invoke-WebRequest -Uri "http://ifconfig.me/ip").Content
```

### 8.3 DNS & Hostname Commands

```powershell
Get-DnsClientServerAddress
Resolve-DnsName google.com
Set-DnsClientServerAddress -InterfaceAlias "Wi-Fi" -ServerAddresses ("8.8.8.8", "8.8.4.4")
Get-Host | Select-Object ComputerName
```

### 8.4 Firewall Commands

View Firewall Rules:

```powershell
Get-NetFirewallRule
Get-NetFirewallRule -DisplayName "Allow8080"
Get-NetFirewallProfile
```

Modify Firewall Rules:

```powershell
New-NetFirewallRule -DisplayName "Allow8080" -Direction Inbound -Action Allow -Protocol TCP -LocalPort 8080
Remove-NetFirewallRule -DisplayName "Allow8080"
Set-NetFirewallProfile -Profile Domain,Public,Private -Enabled False
```

### 8.5 Port Scanning & Monitoring

```powershell
Get-NetTCPConnection | Where-Object { $_.State -eq "Listen" }
Get-NetTCPConnection -LocalPort 80
Get-NetTCPConnection | Sort-Object LocalPort
```

Port Scan a Remote Host:

```powershell
$ports = 20..1000
$target = "192.168.1.1"

foreach ($port in $ports) {
    if (Test-NetConnection -ComputerName $target -Port $port -InformationLevel Quiet) {
        Write-Host "Port $port is open on $target"
    }
}
```

## Conclusion
Now, you have PowerShell installed and running on Parrot OS with powerful networking commands! 🎯

