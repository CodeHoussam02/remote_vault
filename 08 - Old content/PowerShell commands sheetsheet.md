
### **File and Directory Management**

| Command                       | Description                        | Example                                                                                                                                           |
| ----------------------------- | ---------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| `New-Item`                    | Create a new file or directory     | `New-Item -Path . -Name "file.txt" -ItemType "File"` ---------- `new-item -Path 'c:\users\houss\Desctop\houssamBechar_tp_py' -ItemType Directory` |
| `Get-ChildItem` (alias: `ls`) | List contents of a directory       | `Get-ChildItem -Path .`                                                                                                                           |
| `Remove-Item`                 | Delete a file or directory         | `Remove-Item -Path "file.txt"`                                                                                                                    |
| `Copy-Item`                   | Copy a file or directory           | `Copy-Item -Path "file.txt" -Destination "backup.txt"`                                                                                            |
| `Move-Item`                   | Move or rename a file or directory | `Move-Item -Path "file.txt" -Destination "file2.txt"`                                                                                             |
| `Rename-Item`                 | Rename a file or directory         | `Rename-Item -Path "file.txt" -NewName "newfile.txt"`                                                                                             |
| `Set-Location` (alias: `cd`)  | Change the current directory       | `Set-Location -Path "C:\Users"`                                                                                                                   |
| `Get-Content` (alias: `cat`)  | Display the contents of a file     | `Get-Content -Path "file.txt"`                                                                                                                    |
| `Set-Content`                 | Overwrite content in a file        | `Set-Content -Path "file.txt" -Value "Hello World"`                                                                                               |
| `Add-Content`                 | Append content to a file           | `Add-Content -Path "file.txt" -Value "New Line"`                                                                                                  |

---

### **System Management**

|Command|Description|Example|
|---|---|---|
|`Get-Process`|Display running processes|`Get-Process`|
|`Stop-Process`|Stop a running process|`Stop-Process -Name "notepad"`|
|`Start-Process`|Start a new process|`Start-Process -FilePath "notepad.exe"`|
|`Get-Service`|List all services|`Get-Service`|
|`Start-Service`|Start a service|`Start-Service -Name "Spooler"`|
|`Stop-Service`|Stop a service|`Stop-Service -Name "Spooler"`|
|`Restart-Service`|Restart a service|`Restart-Service -Name "Spooler"`|

---

### **User and Group Management**

|Command|Description|Example|
|---|---|---|
|`Get-LocalUser`|List all local users|`Get-LocalUser`|
|`New-LocalUser`|Create a new local user|`New-LocalUser -Name "NewUser" -Password (ConvertTo-SecureString -AsPlainText "Password123" -Force)`|
|`Remove-LocalUser`|Delete a local user|`Remove-LocalUser -Name "NewUser"`|
|`Add-LocalGroupMember`|Add a user to a group|`Add-LocalGroupMember -Group "Administrators" -Member "NewUser"`|
|`Get-LocalGroupMember`|List members of a group|`Get-LocalGroupMember -Group "Administrators"`|

---

### **Network Management**

|Command|Description|Example|
|---|---|---|
|`Test-Connection` (alias: `ping`)|Ping a host|`Test-Connection -ComputerName "google.com"`|
|`Get-NetIPAddress`|Display IP addresses|`Get-NetIPAddress`|
|`New-NetIPAddress`|Assign a new IP address|`New-NetIPAddress -InterfaceAlias "Ethernet" -IPAddress "192.168.1.100" -PrefixLength 24 -DefaultGateway "192.168.1.1"`|
|`Get-NetAdapter`|Display network adapter details|`Get-NetAdapter`|
|`Restart-Computer`|Restart the computer|`Restart-Computer`|
|`Shutdown-Computer`|Shut down the computer|`Stop-Computer`|

---

### **System Information**

|Command|Description|Example|
|---|---|---|
|`Get-ComputerInfo`|Display system information|`Get-ComputerInfo`|
|`Get-EventLog`|Display event logs|`Get-EventLog -LogName "System"`|
|`Get-HotFix`|List installed updates|`Get-HotFix`|
|`Get-WmiObject`|Display hardware information|`Get-WmiObject -Class Win32_Processor`|

---

### **Scripting and Variables**

|Command|Description|Example|
|---|---|---|
|`$VariableName = "Value"`|Declare and assign a variable|`$Name = "Houssam"`|
|`Write-Output`|Print output to the console|`Write-Output "Hello, $Name"`|
|`Read-Host`|Prompt for user input|`$Input = Read-Host "Enter your name"`|
|`If-Else`|Conditional statement|`if ($x -eq 5) { "It's 5" } else { "Not 5" }`|
|`ForEach-Object`|Loop through each object|`Get-Process|

---

### **Useful Aliases**

|Alias|Full Command|
|---|---|
|`ls`|`Get-ChildItem`|
|`cd`|`Set-Location`|
|`rm`|`Remove-Item`|
|`cp`|`Copy-Item`|
|`mv`|`Move-Item`|
|`cat`|`Get-Content`|
|`pwd`|`Get-Location`|