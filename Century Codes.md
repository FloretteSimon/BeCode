https://underthewire.tech/century-1
First level: century1@century.underthewire.tech
Password: century1

## Century 1 -> 2: 
- $PSVersionTable.BuildVersion.ToString()
- 10.0.14393.5582

## Century 2 -> 3:
- Get-ChildItem
- 443
- Get-Alias wget
- Invoke-WebRequest

mdp: invoke-webrequest443

## Century 3 -> 4
- (Get-ChildItem).count
- 123

## Century 4 -> 5
- Get-ChildItem -Filter "* *"
- Can You Open Me
- cd '.\Can You Open Me'
- 34182

mdp:34182

## Century 5 -> 6
- Get-ADDomain | select Name
- underthewire
- dir
- 3347

mdp: underthewire3347

## Century 6 -> 7
- (Get-ChildItem -Directory).count
- 197

mdp: 197

## Century 7 -> 8
- Get-ChildItem ..\ -Recurse -File -Filter readme* | get-content
- 7points

mdp: 7points

## Century 8 -> 9
- (Get-Content .\unique.txt | Sort-Object -Unique).count
- 696

mdp: 696

## Century 9 -> 10
- (Get-Content .\Word_File.txt) -split" " | Select-Object -Index 160
- pierid

mdp: pierid

## Century 10 -> 11
- Get-Service "Windows Update"
- Get-WmiObject -Query "select * from win32_service where name = 'wuauserv'" | Select-Object *
  
Get-WmiObject -Query "select * from win32_service where name = 'wuauserv'" : Cette partie de la commande utilise l'option -Query pour exécuter une requête WMI. La requête "select * from win32_service where name = 'wuauserv'" spécifie que nous voulons récupérer toutes les propriétés (*) de la classe Win32_Service où le nom du service est wuauserv.

Select-Object * : Cette partie de la commande sélectionne toutes les propriétés de l'objet récupéré par Get-WmiObject. Cela inclut toutes les informations sur le service Windows Update (wuauserv), telles que son nom, son état, son type de démarrage, etc.

- (Get-WmiObject -Query "select * from win32_service where name = 'wuauserv'" | Select-Object *).Description
- (Get-WmiObject -Query "select * from win32_service where name = 'wuauserv'" | Select-Object *).Description
- $description = (Get-WmiObject -Query "select * from win32_service where name = 'wuauserv'" | Select-Object *).Description
- $description -split" " | Select-Object -Index 9
- Windows
- updates

mdp: windowsupdates110

## Century 11 -> 12
-  Get-ChildItem -Recurse -Hidden -File -ErrorAction SilentlyContinue -Name Desktop, Downloads, Documents, Pictures, Music, Videos
-  secret_sauce

mdp: secret_sauce

## Century 12 -> 13
https://learn.microsoft.com/en-us/powershell/module/activedirectory/get-addomaincontroller?view=windowsserver2022-ps

https://learn.microsoft.com/en-us/powershell/module/activedirectory/get-adcomputer?view=windowsserver2022-ps&source=post_page-----6fe886134d06--------------------------------

-  Get-ADDomainController
-  Get-ADComputer UTW -Properties Description
-  Description       : i_authenticate

mdp: i_authenticate_things

## Century 13 -> 14
- (Get-Content .\countmywords -Delimiter ' ').count

or

- ((get-content .\countmywords) -split " ").count

mdp: 755

## Century 14 -> 15
- ((get-content .\countpolos -Delimiter ' ') | findstr ^polo). count
- 158

mdp: 153














