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

Enable-WindowsOptionalFeature -FeatureName Hyper-V -Online

or

dism.exe /Online /Enable-Feature /All /FeatureName:Microsoft-Hyper-Vµ


# Powershell Environment Variables

Type echo $env:computername: 

<img width="393" alt="Capture d’écran 2024-04-15 à 15 37 19" src="https://github.com/FloretteSimon/BeCode/assets/155719677/d9d94ca8-59d0-43b7-a71f-42ab68e3abcd">

Create a variable by typing $env:test = "hello powershell". Check the variable you just created the same way you did with the computer name

<img width="410" alt="Capture d’écran 2024-04-15 à 15 38 40" src="https://github.com/FloretteSimon/BeCode/assets/155719677/f2beb3f5-bbfe-4670-81cb-d5ef98cfa49b">


Now we will add something to this variable by typing $env:test += " Becode". Check the variable

There is one really important environment variable : $env:path. This variable store the location where windows looks for files that are not in your current folder. For example, if you call VSCode from the powershell terminal, it opens it even if the executable isn't present in the current folder. That's because the path to the vscode's executable is stored in $env:path. Now download an executable software (rufus for example) and copy it on your desktop. If you try from a command line to launch it, it will fail with a command not found (if you are not in the same folder).

- Invoke-WebRequest -Uri "https://github.com/pbatard/rufus/releases/download/v3.15/rufus-3.15.exe" -OutFile "$env:TEMP\rufus.exe"

- Copy-Item -Path "$env:TEMP\rufus.exe" -Destination "$env:USERPROFILE\Desktop\rufus.exe"

Try to happen the $env:path to add the path to rufus' executable (It should be something like this if you copied it on your desktop : C:\Users\Username\Desktop)

$rufusPath = "$env:C:\Users\flore\Desktop\rufus.exe"

if (-not ($env:Path -split ';' | Select-String -Pattern "$env:flore\Desktop")) {
    $env:Path += ";$rufusPath"
    [System.Environment]::SetEnvironmentVariable("Path", $env:Path, "User")
}


Assigning a value to $rufusPath:


$rufusPath = "$env:C:\Users\flore\Desktop\rufus.exe"
This line of code creates a variable named $rufusPath and assigns it the value of the path to the Rufus executable. The path is constructed using string interpolation ("$env:...") to insert the value of the environment variable $env:C:\Users\flore\Desktop\rufus.exe.
Checking if Rufus path is not already in $env:Path:


if (-not ($env:Path -split ';' | Select-String -Pattern "$env:flore\Desktop")) {
This line starts an if statement that checks whether the path to the Rufus executable ($env:flore\Desktop) is already included in the $env:Path environment variable.
$env:Path -split ';' splits the value of $env:Path into an array of individual paths using semicolon (;) as the delimiter.
Select-String -Pattern "$env:flore\Desktop" searches for the pattern "$env:flore\Desktop" (which resolves to the path to the desktop folder of the user named "flore") in the array of paths.
-not negates the condition, so the if block will execute if the path is not found in $env:Path.
Adding Rufus path to $env:Path:


$env:Path += ";$rufusPath"
This line of code appends the path to the Rufus executable ($rufusPath) to the $env:Path environment variable. The semicolon (;) acts as a delimiter between paths.
Updating the environment variable:


[System.Environment]::SetEnvironmentVariable("Path", $env:Path, "User")
This line uses the [System.Environment]::SetEnvironmentVariable() method to update the value of the Path environment variable with the modified $env:Path.
The third argument "User" specifies that the change should be applied to the user-level environment variables. This ensures that the change persists for the current user session.


In summary, this script checks if the path to the Rufus executable is already included in the system's PATH environment variable. If not, it adds the path to the Rufus executable to the PATH variable and updates the environment variable to reflect the change, ensuring that the Rufus executable can be executed from any directory without specifying its full path.



https://learn.microsoft.com/en-us/windows/deployment/usmt/usmt-recognized-environment-variables












