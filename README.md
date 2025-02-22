# PowerShell Scripting Guide

PowerShell is a powerful scripting language for Windows, used for automation, system administration, and task automation. This tutorial will cover the basics, from writing your first script to advanced scripting techniques.

## 1️⃣ What is PowerShell?
PowerShell is a command-line shell and scripting language built on .NET. It is more powerful than the traditional Windows Command Prompt (CMD) because it supports automation, object-oriented scripting, and system administration tasks.

- **File extension for PowerShell scripts:** `.ps1`
- **To check the PowerShell version, run:**

```powershell
$PSVersionTable
```

## 2️⃣ Running a PowerShell Script
By default, PowerShell restricts running scripts for security reasons.

### Enable Script Execution
To allow script execution, run the following command as an administrator:

```powershell
Set-ExecutionPolicy RemoteSigned
```

#### Options:
- **Restricted (default)** → No scripts can run.
- **RemoteSigned** → Locally created scripts can run, but downloaded scripts need a signature.
- **Unrestricted** → All scripts can run.

### Executing a Script
1. Save the script as `script.ps1`
2. Open PowerShell and navigate to the script directory:

```powershell
cd C:\Path\To\Your\Script
```

3. Run the script:

```powershell
.\script.ps1
```

## 3️⃣ Writing Your First Script
Create a simple script `hello.ps1`:

```powershell
Write-Output "Hello, PowerShell!"
```

Run it:

```powershell
.\hello.ps1
```

### Output:
```
Hello, PowerShell!
```

## 4️⃣ Variables in PowerShell
Define variables using `$`:

```powershell
$Name = "Ankit"
$Age = 22
Write-Output "Hello, my name is $Name and I am $Age years old."
```

## 5️⃣ Conditional Statements (If-Else)
```powershell
$number = 10
if ($number -gt 5) {
    Write-Output "The number is greater than 5"
} else {
    Write-Output "The number is 5 or less"
}
```

## 6️⃣ Loops in PowerShell

### For Loop
```powershell
for ($i=1; $i -le 5; $i++) {
    Write-Output "Iteration $i"
}
```

### While Loop
```powershell
$counter = 1
while ($counter -le 5) {
    Write-Output "Counter: $counter"
    $counter++
}
```

### Foreach Loop (Loop Through an Array)
```powershell
$names = @("Alice", "Bob", "Charlie")
foreach ($name in $names) {
    Write-Output "Hello, $name"
}
```

## 7️⃣ Functions in PowerShell
Functions allow code reuse:

```powershell
function Greet {
    param ($name)
    Write-Output "Hello, $name!"
}

Greet "Ankit"
```

## 8️⃣ Working with Files and Folders

### Creating a File
```powershell
New-Item -Path "C:\Users\Public\testfile.txt" -ItemType File
```

### Writing to a File
```powershell
"Hello, World!" | Out-File -FilePath "C:\Users\Public\testfile.txt"
```

### Reading a File
```powershell
Get-Content "C:\Users\Public\testfile.txt"
```

### Deleting a File
```powershell
Remove-Item "C:\Users\Public\testfile.txt"
```

## 9️⃣ Getting System Information

### Get Running Processes
```powershell
Get-Process
```

### Get Installed Services
```powershell
Get-Service
```

### Get System Information
```powershell
Get-ComputerInfo
```

## 🔟 Automating Tasks with Scheduled Scripts
You can run PowerShell scripts automatically using Task Scheduler:

1. Open Task Scheduler (`taskschd.msc`).
2. Click **Create Basic Task** → Name it → Click **Next**.
3. Select **Trigger** (Daily, Weekly, etc.).
4. Select **Action** → Choose **Start a Program**.
5. Browse to `PowerShell.exe` and add script path:

```powershell
powershell.exe -File "C:\Path\To\Your\Script.ps1"
```

6. Click **Finish**.

## 🔹 Advanced Topics (For Later Learning)
✅ Working with JSON, CSV, XML
✅ Managing Users & Groups in Active Directory
✅ Network Commands for troubleshooting
✅ Automating Windows Tasks

## 🎯 Conclusion
Now you know how to write, run, and automate PowerShell scripts. Start by writing simple scripts and then move to advanced automation.

Would you like help with a specific script? 🚀
