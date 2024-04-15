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















