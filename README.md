# Detect-TeamsPresence.ps1

# Description:
The purpose of this script is to help identify if the status of Teams desktop is stuck in out of office

# Invoke-DetectTeamsPresence
The main functions is Invoke-DetectTeamsPresence and all other functions within perform one specific check to determin if it requires remediation

# Confirm-Teams
The function Confirm-Teams will detect if Teams is installed by checking the registry path:

HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\Teams

if the path exist then it will verify the value of the registry key DefaultIMApp in the path:

HKCU:\SOFTWARE\IM Providers - value should bee "Teams"

# Confirm-TLBFile
The function Confirm-TLBFile verifies the existence of $env:USERPROFILE\AppData\local\microsoft\TeamsPresenceAddin\Uc.tlb for 64 bits Teams installation

# Confirm-OfficeKeys
function Confirm-OfficeKeys verify the registry value for eachpath stored in (Data) key 
Each path has its own value:

HKCU:\SOFTWARE\Classes\TypeLib\{B9AA1F11-F480-4054-A84E-B5D9277E40A8}\1.0 - value should be "Unified Collaboration API 1.0 Type Library"

HKCU:\SOFTWARE\Classes\TypeLib\{B9AA1F11-F480-4054-A84E-B5D9277E40A8}\1.0\0\Win64 - value should be "C:\Users\<username>\AppData\Local\Microsoft\TeamsPresenceAddin\Uc.tlb"

HKCU:\SOFTWARE\Classes\TypeLib\{B9AA1F11-F480-4054-A84E-B5D9277E40A8}\1.0\FLAGS - value should be 0

HKCU:\SOFTWARE\Classes\TypeLib\{B9AA1F11-F480-4054-A84E-B5D9277E40A8}\1.0\HELPDIR - value should be "C:\Users\<username>\AppData\Local\Microsoft\TeamsPresenceAddin\Uc.tlb"
