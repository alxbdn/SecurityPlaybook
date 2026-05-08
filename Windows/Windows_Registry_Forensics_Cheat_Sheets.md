# Windows Registry Forensics Cheatsheet

## System Info and Accounts

| Artifact / Description | Registry Key / Path |
| :--- | :--- |
| **OS Version** | `SOFTWARE\Microsoft\Windows NT\CurrentVersion` |
| **Current Control Set** | `HKLM\SYSTEM\CurrentControlSet`<br>`SYSTEM\Select\Current`<br>`SYSTEM\Select\LastKnownGood` |
| **Computer Name** | `SYSTEM\CurrentControlSet\Control\ComputerName\ComputerName` |
| **Time Zone Information** | `SYSTEM\CurrentControlSet\Control\TimeZoneInformation` |
| **Network Interfaces & Past Networks** | `SYSTEM\CurrentControlSet\Services\Tcpip\Parameters\Interfaces` |
| **Autostart Programs (Autoruns)** | `NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Run`<br>`NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\RunOnce`<br>`SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce`<br>`SOFTWARE\Microsoft\Windows\CurrentVersion\policies\Explorer\Run`<br>`SOFTWARE\Microsoft\Windows\CurrentVersion\Run` |
| **SAM Hive & User Information** | `SAM\Domains\Account\Users` |

---

## File/Folder Usage or Knowledge

| Artifact / Description | Registry Key / Path |
| :--- | :--- |
| **Recent Files** | `NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\RecentDocs` |
| **Office Recent Files** | `NTUSER.DAT\Software\Microsoft\Office\VERSION`<br>`NTUSER.DAT\Software\Microsoft\Office\VERSION\UserMRU\LiveID_####\FileMRU` |
| **ShellBags** | `USRCLASS.DAT\Local Settings\Software\Microsoft\Windows\Shell\Bags`<br>`USRCLASS.DAT\Local Settings\Software\Microsoft\Windows\Shell\BagMRU`<br>`NTUSER.DAT\Software\Microsoft\Windows\Shell\BagMRU`<br>`NTUSER.DAT\Software\Microsoft\Windows\Shell\Bags` |
| **Open/Save & Last Visited Dialog MRUs** | `NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\ComDlg32\OpenSavePIDlMRU`<br>`NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\ComDlg32\LastVisitedPidIMRU` |
| **Windows Explorer Address/Search Bars** | `NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\TypedPaths`<br>`NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\WordWheelQuery` |

---

## External/USB Device Forensics

| Artifact / Description | Registry Key / Path |
| :--- | :--- |
| **Device Identification** | `SYSTEM\CurrentControlSet\Enum\USBSTOR`<br>`SYSTEM\CurrentControlSet\Enum\USB` |
| **First/Last Times** | `SYSTEM\CurrentControlSet\Enum\USBSTOR\Ven_Prod_Version\USBSerial#\Properties\{83da6326-97a6-4088-9453-a19231573b29}\####`<br><ul><li>`0064` = first connection</li><li>`0066` = last connection</li><li>`0067` = last removal</li></ul> |
| **USB Device Volume Name** | `SOFTWARE\Microsoft\Windows Portable Devices\Devices` |

---

## Evidence of Execution

| Artifact / Description | Registry Key / Path |
| :--- | :--- |
| **UserAssist** | `NTUSER.DAT\Software\Microsoft\Windows\Currentversion\Explorer\UserAssist\{GUID}\Count` |
| **ShimCache** | `SYSTEM\CurrentControlSet\Control\Session Manager\AppCompatCache` |
| **AmCache** | `Amcache.hve\Root\File\{Volume GUID}\` |
| **BAM/DAM** | `SYSTEM\CurrentControlSet\Services\bam\UserSettings\{SID}`<br>`SYSTEM\CurrentControlSet\Services\dam\UserSettings\{SID}` |

---
> **Credits / Learn More:** [TryHackMe - Windows Forensics 1](https://tryhackme.com/room/windowsforensics1)