  # Powershell RTFM

Get-Help: It displays information about PowerShell commands and concepts. 

Get-Process: This command retrieves information about the processes running on a local or remote computer, such as process ID, name, CPU usage, and more.

Get-Command: This cmdlet gets all commands that are installed on the computer, including cmdlets, aliases, functions, filters, scripts, and applications. It's handy for finding PowerShell commands available to you.


# Powershell Navigation

Print your current location on the screen: Get-Location

Print the content of your current directory: Get-ChildItem

Print the content of your root (C: if you're running windows, / for linux): Get-ChildItem c:\

Go into your home folder (C:\Users\Username or /home/Username): Set-Location C:\Users\Bibi

Print the content of your home: Get-ChildItem $HOME

Those commands are pretty long to type, do you know any shorter way to do it?
<img width="507" alt="Capture d’écran 2024-04-15 à 11 16 38" src="https://github.com/FloretteSimon/BeCode/assets/155719677/41cdcf47-86ce-4a82-bfdb-240d86bbceef">
- dir for Get-ChildItem
- pwd for Get-Location
- cd for Set-Location


# Powershell File Operations

Create a file named story1.txt: ni -Type File story1.txt short for New-Item -ItemType File story1.txt 

Type echo "Hello World" > story1.txt

Print the content of the file: gc .\story1.txt short for Get-Content .\story2.txt

Create a folder named story: ni -Type d story short for New-Item -ItemType Directory story

Move story1.txt inside story: mv .\story1.txt\ .\story\ short fort Move-Item .\story1.txt\ .\story\

Copy story1.txt as story2.txt: cp story1.txt story2.txt short for Copy-Item story1.txt story2.txt

Print both files: gc story1.txt, story2.txt

Rename story2.txt as me.txt: ren story2.txt me.txt short for Rename-Item story2.txt me.txt

Append me.txt and add "I am a junior at Becode": ac me.txt "I am a junior at Becode" short for Add-Content me.txt "I am a junior at Becode"

Remove the folder story with it's content: rm story short for Remove-Item story


# Powershell Permissions

Create a file: ni NewFile

Check the owner and the groups: Get-Acl 

Change the file owner to the built-in administrator (administrator account is disabled by default, check how to enable it. Don't forget to set a strong password!): 
- elu -Name "Administrator" short for Enable-LocalUser -Name "Administrator"
- slu -Name "Administrator" -Password (ConvertTo-SecureString "BeCode" -AsPlainText -Force) short for Set-LocalUser -Name "Administrator" -Password (ConvertTo-SecureString "BeCode" -AsPlainText -Force)
- $acl = Get-Acl -Path "new.txt"
- $newOwner.SetOwner($newOwner)
- Set-Acl -Path "new.txt" -AclObject $acl
- acl.owner

https://petri.com/how-to-use-powershell-to-manage-folder-permissions/




# Powershell Package Management

Install the PSWindowsUpdate module:
- Check if the Module is Installed: First, confirm whether the "PSWindowsUpdate" module is installed on your system. :
  
    Get-Module -Name PSWindowsUpdate -ListAvailable
  
- Install the Module: Install-Module -Name PSWindowsUpdate

- Import the Module: Import-Module -Name PSWindowsUpdate

- Check Execution Policy: Ensure that your PowerShell execution policy allows script execution: Get-ExecutionPolicy


Type Get-WindowsUpdate to check for updates

Type Get-WindowsUpdate to check for updates

Install Chocolatey: 
- Enable Execution of PowerShell Scripts (if not already enabled): Set-ExecutionPolicy Bypass -Scope Process -Force

- Install Chocolatey: Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
  
    The command consists of multiple parts:
  
    Set-ExecutionPolicy Bypass -Scope Process -Force: Bypasses the execution policy.
  
    [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072: Updates the security protocol to ensure compatibility with Chocolatey's installation script. This step is necessary due to changes in security protocols over time.
  
    iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1')): Invokes the execution of the Chocolatey installation script downloaded from the specified URL using Invoke-Expression (abbreviated as iex). This downloads and executes the script.

- Verify Installation: choco -?

  Install VLC from Chocolatey:

  - Before installing VLC, ensure that there is a Chocolatey package available for it: choco search vlc
  - Install VLC Package: choco install vlc
  - Verify Installation: vlc


Get-WindowsOptionalFeature -Online

dism.exe /Online /Enable-Feature /All /FeatureName:Microsoft-Hyper-V


# Powershell Environment Variables

Type echo $env:computername: 

<img width="393" alt="Capture d’écran 2024-04-15 à 15 37 19" src="https://github.com/FloretteSimon/BeCode/assets/155719677/d9d94ca8-59d0-43b7-a71f-42ab68e3abcd">

Create a variable by typing $env:test = "hello powershell". Check the variable you just created the same way you did with the computer name

<img width="410" alt="Capture d’écran 2024-04-15 à 15 38 40" src="https://github.com/FloretteSimon/BeCode/assets/155719677/f2beb3f5-bbfe-4670-81cb-d5ef98cfa49b">


Now we will add something to this variable by typing $env:test += " Becode". Check the variable

















