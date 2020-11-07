---
ms.date: 02/03/2020
keywords: PowerShell, Core
title: Versions historik för moduler och cmdletar
description: Den här artikeln innehåller moduler och cmdletar som ingår i olika versioner av PowerShell.
ms.openlocfilehash: 43ea0cde106e9f0aafe9c18726589f931724b35f
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94342866"
---
# <a name="release-history-of-modules-and-cmdlets"></a>Versions historik för moduler och cmdletar

Den här artikeln innehåller moduler och cmdletar som ingår i olika versioner av PowerShell. Det här är en sammanfattning av information som finns i viktig information. Mer detaljerad information finns i versions anteckningarna:

- [Nyheter i PowerShell 7.0](what-s-new-in-powershell-70.md)
- [Nyheter i PowerShell 6.2](what-s-new-in-powershell-core-62.md)
- [Nyheter i PowerShell 6,1](what-s-new-in-powershell-core-61.md)
- [Nyheter i PowerShell 6,0](what-s-new-in-powershell-core-60.md)
- [Bryta ändringar i PowerShell 6,0](breaking-changes-ps6.md)
- [Kända problem i PowerShell 6,0](known-issues-ps6.md)

Detta är ett pågående arbete. Hjälp oss att uppdatera den här informationen.

## <a name="module-release-history"></a>Versions historik för modul

|         Modulnamn/PS-version          |   5,1   |   6.x   |   7.0   |   7.1   |     Anteckning     |
| ----------------------------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| CimCmdlets                                | &check; | &check; | &check; | &check; | Endast Windows |
| ISE (lanserades i 2,0)                   | &check; |         |         |         | Endast Windows |
| Microsoft. PowerShell. Archive              | &check; | &check; | &check; | &check; |              |
| Microsoft. PowerShell. Core                 | &check; | &check; | &check; | &check; |              |
| Microsoft. PowerShell. Diagnostics          | &check; | &check; | &check; | &check; | Endast Windows |
| Microsoft. PowerShell. Host                 | &check; | &check; | &check; | &check; |              |
| Microsoft. PowerShell. LocalAccounts        | &check; |         |         |         | Endast Windows |
| Microsoft. PowerShell. Management           | &check; | &check; | &check; | &check; |              |
| Microsoft. PowerShell. ODataUtils           | &check; |         |         |         | Endast Windows |
| Microsoft. PowerShell. operation. Validation | &check; |         |         |         | Endast Windows |
| Microsoft. PowerShell. Security             | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.Utility              | &check; | &check; | &check; | &check; |              |
| Microsoft. WsMan. Management                | &check; | &check; | &check; | &check; | Endast Windows |
| PackageManagement                         | &check; | &check; | &check; | &check; |              |
| PowershellGet                             | &check; | &check; | &check; | &check; |              |
| PSDesiredStateConfiguration               | &check; | &check; | &check; | &check; |              |
| PSDiagnostics                             | &check; | &check; | &check; | &check; | Endast Windows |
| PSReadline 1. x                            | &check; |         |         |         | Endast Windows |
| PSReadline 2. x                            |         | &check; | &check; | &check; |              |
| PSScheduledJob                            | &check; |         |         |         | Endast Windows |
| PSWorkflow                                | &check; |         |         |         | Endast Windows |
| PSWorkflowUtility                         | &check; |         |         |         | Endast Windows |
| ThreadJob                                 |         | &check; | &check; | &check; | Kan installeras i PowerShell 5,1 |

## <a name="cmdlet-release-history"></a>Versions historik för cmdlet

### <a name="cimcmdlets"></a>CimCmdlets

|         Cmdlet-namn         |   5,1   |   6.x   |   7.0   |   7.1   |     Anteckning     |
| --------------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Export-BinaryMiLog          | &check; | &check; | &check; | &check; | Endast Windows |
| Get-CimAssociatedInstance   | &check; | &check; | &check; | &check; | Endast Windows |
| Get-CimClass                | &check; | &check; | &check; | &check; | Endast Windows |
| Get-CimInstance             | &check; | &check; | &check; | &check; | Endast Windows |
| Get-CimSession              | &check; | &check; | &check; | &check; | Endast Windows |
| Import-BinaryMiLog          | &check; | &check; | &check; | &check; | Endast Windows |
| Invoke-CimMethod            | &check; | &check; | &check; | &check; | Endast Windows |
| New-CimInstance             | &check; | &check; | &check; | &check; | Endast Windows |
| New-CimSession              | &check; | &check; | &check; | &check; | Endast Windows |
| New-CimSessionOption        | &check; | &check; | &check; | &check; | Endast Windows |
| Register-CimIndicationEvent | &check; | &check; | &check; | &check; | Endast Windows |
| Remove-CimInstance          | &check; | &check; | &check; | &check; | Endast Windows |
| Remove-CimSession           | &check; | &check; | &check; | &check; | Endast Windows |
| Set-CimInstance             | &check; | &check; | &check; | &check; | Endast Windows |

### <a name="ise-introduced-in-20"></a>ISE (lanserades i 2,0)

|    Cmdlet-namn    |   5,1   | 6.x  |  7.0  |  7.1  |     Anteckning     |
| ----------------- | :-----: | :--- | :---: | :---: | ------------ |
| Get-IseSnippet    | &check; |      |       |       | Endast Windows |
| Import-IseSnippet | &check; |      |       |       | Endast Windows |
| New-IseSnippet    | &check; |      |       |       | Endast Windows |

### <a name="microsoftpowershellarchive"></a>Microsoft. PowerShell. Archive

|   Cmdlet-namn    |   5,1   |   6.x   |   7.0   |   7.1   | Anteckning |
| ---------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Compress-Archive | &check; | &check; | &check; | &check; |      |
| Expand-Archive   | &check; | &check; | &check; | &check; |      |

### <a name="microsoftpowershellcore"></a>Microsoft. PowerShell. Core

|            Cmdlet-namn            |   5,1   |   6.x   |   7.0   |   7.1   |            Anteckning            |
| --------------------------------- | :-----: | :-----: | :-----: | :-----: | -------------------------- |
| Add-History                       | &check; | &check; | &check; | &check; |                            |
| Add-PSSnapin                      | &check; |         |         |         | Endast Windows               |
| Clear-History                     | &check; | &check; | &check; | &check; |                            |
| Clear-Host                        | &check; | &check; | &check; | &check; |                            |
| Connect-PSSession                 | &check; | &check; | &check; | &check; | Endast Windows               |
| Debug-Job                         | &check; | &check; | &check; | &check; |                            |
| Disable-ExperimentalFeature       |         |   6,2   | &check; | &check; |                            |
| Disable-PSRemoting                | &check; | &check; | &check; | &check; | Endast Windows               |
| Disable-PSSessionConfiguration    | &check; | &check; | &check; | &check; | Endast Windows               |
| Disconnect-PSSession              | &check; | &check; | &check; | &check; | Endast Windows               |
| Enable-ExperimentalFeature        |         |   6,2   | &check; | &check; |                            |
| Enable-PSRemoting                 | &check; | &check; | &check; | &check; | Endast Windows               |
| Enable-PSSessionConfiguration     | &check; | &check; | &check; | &check; | Endast Windows               |
| Enter-PSHostProcess               | &check; | &check; | &check; | &check; | Linux-stöd har lagts till i 6,2 |
| Enter-PSSession                   | &check; | &check; | &check; | &check; |                            |
| Exit-PSHostProcess                | &check; | &check; | &check; | &check; | Linux-stöd har lagts till i 6,2 |
| Exit-PSSession                    | &check; | &check; | &check; | &check; |                            |
| Export-Console                    | &check; |         |         |         | Endast Windows               |
| Export-ModuleMember               | &check; | &check; | &check; | &check; |                            |
| ForEach-Object                    | &check; | &check; | &check; | &check; |                            |
| Get-Command                       | &check; | &check; | &check; | &check; |                            |
| Get-ExperimentalFeature           |         |   6,2   | &check; | &check; |                            |
| Get-Help                          | &check; | &check; | &check; | &check; |                            |
| Get-History                       | &check; | &check; | &check; | &check; |                            |
| Get-Job                           | &check; | &check; | &check; | &check; |                            |
| Get-Module                        | &check; | &check; | &check; | &check; |                            |
| Get-PSHostProcessInfo             | &check; | &check; | &check; | &check; | Linux-stöd har lagts till i 6,2 |
| Get-PSSession                     | &check; | &check; | &check; | &check; |                            |
| Get-PSSessionCapability           | &check; | &check; | &check; | &check; |                            |
| Get-PSSessionConfiguration        | &check; | &check; | &check; | &check; |                            |
| Get-PSSnapin                      | &check; |         |         |         | Endast Windows               |
| Get-Verb                          | &check; |         |         |         | Flyttad till Microsoft. PowerShell. Utility 6.0 + |
| Import-Module                     | &check; | &check; | &check; | &check; |                            |
| Invoke-Command                    | &check; | &check; | &check; | &check; |                            |
| Invoke-History                    | &check; | &check; | &check; | &check; |                            |
| New-Module                        | &check; | &check; | &check; | &check; |                            |
| New-ModuleManifest                | &check; | &check; | &check; | &check; |                            |
| New-PSRoleCapabilityFile          | &check; | &check; | &check; | &check; |                            |
| New-PSSession                     | &check; | &check; | &check; | &check; |                            |
| New-PSSessionConfigurationFile    | &check; | &check; | &check; | &check; | Endast Windows               |
| New-PSSessionOption               | &check; | &check; | &check; | &check; |                            |
| New-PSTransportOption             | &check; | &check; | &check; | &check; |                            |
| Out-Default                       | &check; | &check; | &check; | &check; |                            |
| Out-Host                          | &check; | &check; | &check; | &check; |                            |
| Out-Null                          | &check; | &check; | &check; | &check; |                            |
| Receive-Job                       | &check; | &check; | &check; | &check; |                            |
| Receive-PSSession                 | &check; | &check; | &check; | &check; | Endast Windows               |
| Register-ArgumentCompleter        | &check; | &check; | &check; | &check; |                            |
| Register-PSSessionConfiguration   | &check; | &check; | &check; | &check; | Endast Windows               |
| Remove-Job                        | &check; | &check; | &check; | &check; |                            |
| Remove-Module                     | &check; | &check; | &check; | &check; |                            |
| Remove-PSSession                  | &check; | &check; | &check; | &check; |                            |
| Remove-PSSnapin                   | &check; |         |         |         | Endast Windows               |
| Resume-Job                        | &check; |         |         |         |                            |
| Save-Help                         | &check; | &check; | &check; | &check; |                            |
| Set-PSDebug                       | &check; | &check; | &check; | &check; |                            |
| Set-PSSessionConfiguration        | &check; | &check; | &check; | &check; | Endast Windows               |
| Set-StrictMode                    | &check; | &check; | &check; | &check; |                            |
| Start-Job                         | &check; | &check; | &check; | &check; |                            |
| Stop-Job                          | &check; | &check; | &check; | &check; |                            |
| Suspend-Job                       | &check; |         |         |         | Endast Windows               |
| Test-ModuleManifest               | &check; | &check; | &check; | &check; |                            |
| Test-PSSessionConfigurationFile   | &check; | &check; | &check; | &check; | Endast Windows               |
| Unregister-PSSessionConfiguration | &check; | &check; | &check; | &check; | Endast Windows               |
| Update-Help                       | &check; | &check; | &check; | &check; |                            |
| Wait-Job                          | &check; | &check; | &check; | &check; |                            |
| Where-Object                      | &check; | &check; | &check; | &check; |                            |

### <a name="microsoftpowershelldiagnostics"></a>Microsoft. PowerShell. Diagnostics

|  Cmdlet-namn   |   5,1   |   6.x   |   7.0   |   7.1   |     Anteckning     |
| -------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Export-Counter | &check; |         |         |         | Endast Windows |
| Get-Counter    | &check; |         | &check; | &check; | Endast Windows |
| Get-WinEvent   | &check; | &check; | &check; | &check; | Endast Windows |
| Import-Counter | &check; |         |         |         | Endast Windows |
| New-WinEvent   | &check; | &check; | &check; | &check; | Endast Windows |

### <a name="microsoftpowershellhost"></a>Microsoft. PowerShell. Host

|   Cmdlet-namn    |   5,1   |   6.x   |   7.0   |   7.1   | Anteckning |
| ---------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Start-Transcript | &check; | &check; | &check; | &check; |      |
| Stop-Transcript  | &check; | &check; | &check; | &check; |      |

### <a name="microsoftpowershelllocalaccounts"></a>Microsoft. PowerShell. LocalAccounts

|       Cmdlet-namn       |   5,1   | 6.x  |  7.0  |  7.1  |     Anteckning     |
| ----------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Add-LocalGroupMember    | &check; |      |       |       | Endast Windows |
| Disable-LocalUser       | &check; |      |       |       | Endast Windows |
| Enable-LocalUser        | &check; |      |       |       | Endast Windows |
| Get-LocalGroup          | &check; |      |       |       | Endast Windows |
| Get-LocalGroupMember    | &check; |      |       |       | Endast Windows |
| Get-LocalUser           | &check; |      |       |       | Endast Windows |
| New-LocalGroup          | &check; |      |       |       | Endast Windows |
| New-LocalUser           | &check; |      |       |       | Endast Windows |
| Remove-LocalGroup       | &check; |      |       |       | Endast Windows |
| Remove-LocalGroupMember | &check; |      |       |       | Endast Windows |
| Remove-LocalUser        | &check; |      |       |       | Endast Windows |
| Rename-LocalGroup       | &check; |      |       |       | Endast Windows |
| Rename-LocalUser        | &check; |      |       |       | Endast Windows |
| Set-LocalGroup          | &check; |      |       |       | Endast Windows |
| Set-LocalUser           | &check; |      |       |       | Endast Windows |

### <a name="microsoftpowershellmanagement"></a>Microsoft. PowerShell. Management

|          Cmdlet-namn          |   5,1   |   6.x   |   7.0   |   7.1   |               Anteckning               |
| ----------------------------- | :-----: | :-----: | :-----: | :-----: | -------------------------------- |
| Add-Computer                  | &check; |         |         |         | Endast Windows                     |
| Add-Content                   | &check; | &check; | &check; | &check; |                                  |
| Checkpoint-Computer           | &check; |         |         |         | Endast Windows                     |
| Clear-Content                 | &check; | &check; | &check; | &check; |                                  |
| Clear-EventLog                | &check; |         |         |         | Endast Windows                     |
| Clear-Item                    | &check; | &check; | &check; | &check; |                                  |
| Clear-ItemProperty            | &check; | &check; | &check; | &check; |                                  |
| Clear-RecycleBin              | &check; |         | &check; | &check; | Endast Windows                     |
| Complete-Transaction          | &check; |         |         |         | Endast Windows                     |
| Convert-Path                  | &check; | &check; | &check; | &check; |                                  |
| Copy-Item                     | &check; | &check; | &check; | &check; |                                  |
| Copy-ItemProperty             | &check; | &check; | &check; | &check; |                                  |
| Debug-Process                 | &check; | &check; | &check; | &check; |                                  |
| Disable-ComputerRestore       | &check; |         |         |         | Endast Windows                     |
| Enable-ComputerRestore        | &check; |         |         |         | Endast Windows                     |
| Get-ChildItem                 | &check; | &check; | &check; | &check; |                                  |
| Get-Clipboard                 | &check; |         | &check; | &check; | Stöds inte på macOS           |
| Get-ComputerInfo              | &check; | &check; | &check; | &check; | Endast Windows                     |
| Get-ComputerRestorePoint      | &check; |         |         |         | Endast Windows                     |
| Get-Content                   | &check; | &check; | &check; | &check; |                                  |
| Get-ControlPanelItem          | &check; |         |         |         | Endast Windows                     |
| Get-EventLog                  | &check; |         |         |         | Endast Windows                     |
| Get-HotFix                    | &check; |         | &check; | &check; | Endast Windows                     |
| Get-Item                      | &check; | &check; | &check; | &check; |                                  |
| Get-ItemProperty              | &check; | &check; | &check; | &check; |                                  |
| Get-ItemPropertyValue         | &check; | &check; | &check; | &check; |                                  |
| Get-Location                  | &check; | &check; | &check; | &check; |                                  |
| Get-Process                   | &check; | &check; | &check; | &check; |                                  |
| Get-PSDrive                   | &check; | &check; | &check; | &check; |                                  |
| Get-PSProvider                | &check; | &check; | &check; | &check; |                                  |
| Get-Service                   | &check; | &check; | &check; | &check; | Endast Windows                     |
| Get-TimeZone                  | &check; | &check; | &check; | &check; | Endast Windows                     |
| Get-Transaction               | &check; |         |         |         | Endast Windows                     |
| Get-WmiObject                 | &check; |         |         |         | Endast Windows                     |
| Invoke-Item                   | &check; | &check; | &check; | &check; |                                  |
| Invoke-WmiMethod              | &check; |         |         |         | Endast Windows                     |
| Join-Path                     | &check; | &check; | &check; | &check; |                                  |
| Limit-EventLog                | &check; |         |         |         | Endast Windows                     |
| Move-Item                     | &check; | &check; | &check; | &check; |                                  |
| Move-ItemProperty             | &check; | &check; | &check; | &check; |                                  |
| New-EventLog                  | &check; |         |         |         | Endast Windows                     |
| New-Item                      | &check; | &check; | &check; | &check; |                                  |
| New-ItemProperty              | &check; | &check; | &check; | &check; |                                  |
| New-PSDrive                   | &check; | &check; | &check; | &check; |                                  |
| New-Service                   | &check; | &check; | &check; | &check; | Endast Windows                     |
| New-WebServiceProxy           | &check; |         |         |         | Endast Windows                     |
| Pop-Location                  | &check; | &check; | &check; | &check; |                                  |
| Push-Location                 | &check; | &check; | &check; | &check; |                                  |
| Register-WmiEvent             | &check; |         |         |         | Endast Windows                     |
| Remove-Computer               | &check; |         |         |         | Endast Windows                     |
| Remove-EventLog               | &check; |         |         |         | Endast Windows                     |
| Remove-Item                   | &check; | &check; | &check; | &check; |                                  |
| Remove-ItemProperty           | &check; | &check; | &check; | &check; |                                  |
| Remove-PSDrive                | &check; | &check; | &check; | &check; |                                  |
| Remove-Service                |         | &check; | &check; | &check; | Endast Windows                     |
| Remove-WmiObject              | &check; |         |         |         | Endast Windows                     |
| Rename-Computer               | &check; | &check; | &check; | &check; | Endast Windows                     |
| Rename-Item                   | &check; | &check; | &check; | &check; |                                  |
| Rename-ItemProperty           | &check; | &check; | &check; | &check; |                                  |
| Reset-ComputerMachinePassword | &check; |         |         |         | Endast Windows                     |
| Resolve-Path                  | &check; | &check; | &check; | &check; |                                  |
| Restart-Computer              | &check; | &check; | &check; | &check; | Stöd för Linux/macOS har lagts till i 7,1 |
| Restart-Service               | &check; | &check; | &check; | &check; | Endast Windows                     |
| Restore-Computer              | &check; |         |         |         | Endast Windows                     |
| Resume-Service                | &check; | &check; | &check; | &check; | Endast Windows                     |
| Set-Clipboard                 | &check; |         | &check; | &check; |                                  |
| Set-Content                   | &check; | &check; | &check; | &check; |                                  |
| Set-Item                      | &check; | &check; | &check; | &check; |                                  |
| Set-ItemProperty              | &check; | &check; | &check; | &check; |                                  |
| Set-Location                  | &check; | &check; | &check; | &check; |                                  |
| Set-Service                   | &check; | &check; | &check; | &check; | Endast Windows                     |
| Set-TimeZone                  | &check; | &check; | &check; | &check; | Endast Windows                     |
| Set-WmiInstance               | &check; |         |         |         | Endast Windows                     |
| Show-ControlPanelItem         | &check; |         |         |         | Endast Windows                     |
| Show-EventLog                 | &check; |         |         |         | Endast Windows                     |
| Split-Path                    | &check; | &check; | &check; | &check; |                                  |
| Start-Process                 | &check; | &check; | &check; | &check; |                                  |
| Start-Service                 | &check; | &check; | &check; | &check; | Endast Windows                     |
| Start-Transaction             | &check; |         |         |         | Endast Windows                     |
| Stop-Computer                 | &check; | &check; | &check; | &check; | Stöd för Linux/macOS har lagts till i 7,1 |
| Stop-Process                  | &check; | &check; | &check; | &check; |                                  |
| Stop-Service                  | &check; | &check; | &check; | &check; | Endast Windows                     |
| Suspend-Service               | &check; | &check; | &check; | &check; | Endast Windows                     |
| Test-ComputerSecureChannel    | &check; |         |         |         | Endast Windows                     |
| Test-Connection               | &check; | &check; | &check; | &check; |                                  |
| Test-Path                     | &check; | &check; | &check; | &check; |                                  |
| Undo-Transaction              | &check; |         |         |         | Endast Windows                     |
| Use-Transaction               | &check; |         |         |         | Endast Windows                     |
| Wait-Process                  | &check; | &check; | &check; | &check; | Fungerar inte på Linux/macOS     |
| Write-EventLog                | &check; |         |         |         | Endast Windows                     |

### <a name="microsoftpowershellodatautils"></a>Microsoft. PowerShell. ODataUtils

|        Cmdlet-namn        |   5,1   | 6.x  |  7.0  |  7.1  |     Anteckning     |
| ------------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Export-ODataEndpointProxy | &check; |      |       |       | Endast Windows |

### <a name="microsoftpowershelloperationvalidation"></a>Microsoft. PowerShell. operation. Validation

|        Cmdlet-namn         |   5,1   | 6.x  |  7.0  |  7.1  |     Anteckning     |
| -------------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Get-OperationValidation    | &check; |      |       |       | Endast Windows |
| Invoke-OperationValidation | &check; |      |       |       | Endast Windows |

### <a name="microsoftpowershellsecurity"></a>Microsoft. PowerShell. Security

|        Cmdlet-namn        |   5,1   |   6.x   |   7.0   |   7.1   |                  Anteckning                   |
| ------------------------- | :-----: | :-----: | :-----: | :-----: | --------------------------------------- |
| ConvertFrom-SecureString  | &check; | &check; | &check; | &check; |                                         |
| ConvertTo-SecureString    | &check; | &check; | &check; | &check; |                                         |
| Get-Acl                   | &check; | &check; | &check; | &check; | Endast Windows                            |
| Get-AuthenticodeSignature | &check; | &check; | &check; | &check; | Endast Windows                            |
| Get-CmsMessage            | &check; | &check; | &check; | &check; | Stöd för Linux/macOS tillagt i 7,1    |
| Get-Credential            | &check; | &check; | &check; | &check; |                                         |
| Get-ExecutionPolicy       | &check; | &check; | &check; | &check; | Returnerar **obegränsade** på Linux/MacOS |
| Get-PfxCertificate        | &check; | &check; | &check; | &check; |                                         |
| New-FileCatalog           | &check; | &check; | &check; | &check; | Endast Windows                            |
| Protect-CmsMessage        | &check; | &check; | &check; | &check; | Stöd för Linux/macOS tillagt i 7,1    |
| Set-Acl                   | &check; | &check; | &check; | &check; | Endast Windows                            |
| Set-AuthenticodeSignature | &check; | &check; | &check; | &check; | Endast Windows                            |
| Set-ExecutionPolicy       | &check; | &check; | &check; | &check; | Händer ingenting på Linux/macOS             |
| Test-FileCatalog          | &check; | &check; | &check; | &check; | Endast Windows                            |
| Unprotect-CmsMessage      | &check; | &check; | &check; | &check; | Stöd för Linux/macOS tillagt i 7,1    |

### <a name="microsoftpowershellutility"></a>Microsoft.PowerShell.Utility

|        Cmdlet-namn        |   5,1   |   6.x   |   7.0   |   7.1   |                   Anteckning                    |
| ------------------------- | :-----: | :-----: | :-----: | :-----: | ----------------------------------------- |
| Add-Member                | &check; | &check; | &check; | &check; |                                           |
| Add-Type                  | &check; | &check; | &check; | &check; |                                           |
| Clear-Variable            | &check; | &check; | &check; | &check; |                                           |
| Compare-Object            | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-Csv           | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-Json          | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-Markdown      |         |   6.1   | &check; | &check; |                                           |
| ConvertFrom-SddlString    | &check; | &check; | &check; | &check; | Endast Windows                              |
| ConvertFrom-String        | &check; |         |         |         |                                           |
| ConvertFrom-StringData    | &check; | &check; | &check; | &check; |                                           |
| Convert-String            | &check; |         |         |         |                                           |
| ConvertTo-Csv             | &check; | &check; | &check; | &check; |                                           |
| ConvertTo-Html            | &check; | &check; | &check; | &check; |                                           |
| ConvertTo-Json            | &check; | &check; | &check; | &check; |                                           |
| ConvertTo-Xml             | &check; | &check; | &check; | &check; |                                           |
| Debug-Runspace            | &check; | &check; | &check; | &check; |                                           |
| Disable-PSBreakpoint      | &check; | &check; | &check; | &check; |                                           |
| Disable-RunspaceDebug     | &check; | &check; | &check; | &check; |                                           |
| Enable-PSBreakpoint       | &check; | &check; | &check; | &check; |                                           |
| Enable-RunspaceDebug      | &check; | &check; | &check; | &check; |                                           |
| Export-Alias              | &check; | &check; | &check; | &check; |                                           |
| Export-Clixml             | &check; | &check; | &check; | &check; |                                           |
| Export-Csv                | &check; | &check; | &check; | &check; |                                           |
| Export-FormatData         | &check; | &check; | &check; | &check; |                                           |
| Export-PSSession          | &check; | &check; | &check; | &check; |                                           |
| Format-Custom             | &check; | &check; | &check; | &check; |                                           |
| Format-Hex                | &check; | &check; | &check; | &check; |                                           |
| Format-List               | &check; | &check; | &check; | &check; |                                           |
| Format-Table              | &check; | &check; | &check; | &check; |                                           |
| Format-Wide               | &check; | &check; | &check; | &check; |                                           |
| Get-Alias                 | &check; | &check; | &check; | &check; |                                           |
| Get-Culture               | &check; | &check; | &check; | &check; |                                           |
| Get-Date                  | &check; | &check; | &check; | &check; |                                           |
| Get-Error                 |         |         | &check; | &check; |                                           |
| Get-Event                 | &check; | &check; | &check; | &check; | Inga händelse källor är tillgängliga på Linux/macOS |
| Get-EventSubscriber       | &check; | &check; | &check; | &check; |                                           |
| Get-FileHash              | &check; | &check; | &check; | &check; |                                           |
| Get-FormatData            | &check; | &check; | &check; | &check; |                                           |
| Get-Host                  | &check; | &check; | &check; | &check; |                                           |
| Get-MarkdownOption        |         |   6.1   | &check; | &check; |                                           |
| Get-Member                | &check; | &check; | &check; | &check; |                                           |
| Get-PSBreakpoint          | &check; | &check; | &check; | &check; |                                           |
| Get-PSCallStack           | &check; | &check; | &check; | &check; |                                           |
| Get-Random                | &check; | &check; | &check; | &check; |                                           |
| Get-Runspace              | &check; | &check; | &check; | &check; |                                           |
| Get-RunspaceDebug         | &check; | &check; | &check; | &check; |                                           |
| Get-TraceSource           | &check; | &check; | &check; | &check; |                                           |
| Get-TypeData              | &check; | &check; | &check; | &check; |                                           |
| Get-UICulture             | &check; | &check; | &check; | &check; |                                           |
| Get-Unique                | &check; | &check; | &check; | &check; |                                           |
| Get-Uptime                |         | &check; | &check; | &check; |                                           |
| Get-Variable              | &check; | &check; | &check; | &check; |                                           |
| Get-Verb                  |         | &check; | &check; | &check; | Flyttad från Microsoft. PowerShell. Core     |
| Group-Object              | &check; | &check; | &check; | &check; |                                           |
| Import-Alias              | &check; | &check; | &check; | &check; |                                           |
| Import-Clixml             | &check; | &check; | &check; | &check; |                                           |
| Import-Csv                | &check; | &check; | &check; | &check; |                                           |
| Import-LocalizedData      | &check; | &check; | &check; | &check; |                                           |
| Import-PowerShellDataFile | &check; | &check; | &check; | &check; |                                           |
| Import-PSSession          | &check; | &check; | &check; | &check; |                                           |
| Invoke-Expression         | &check; | &check; | &check; | &check; |                                           |
| Invoke-RestMethod         | &check; | &check; | &check; | &check; |                                           |
| Invoke-WebRequest         | &check; | &check; | &check; | &check; |                                           |
| Join-String               |         | &check; | &check; | &check; |                                           |
| Measure-Command           | &check; | &check; | &check; | &check; |                                           |
| Measure-Object            | &check; | &check; | &check; | &check; |                                           |
| New-Alias                 | &check; | &check; | &check; | &check; |                                           |
| New-Event                 | &check; | &check; | &check; | &check; | Inga händelse källor är tillgängliga på Linux/macOS |
| New-Guid                  | &check; | &check; | &check; | &check; |                                           |
| New-Object                | &check; | &check; | &check; | &check; |                                           |
| New-TemporaryFile         | &check; | &check; | &check; | &check; |                                           |
| New-TimeSpan              | &check; | &check; | &check; | &check; |                                           |
| New-Variable              | &check; | &check; | &check; | &check; |                                           |
| Out-File                  | &check; | &check; | &check; | &check; |                                           |
| Out-GridView              | &check; |         | &check; | &check; | Endast Windows                              |
| Out-Printer               | &check; |         | &check; | &check; | Endast Windows                              |
| Out-String                | &check; | &check; | &check; | &check; |                                           |
| Read-Host                 | &check; | &check; | &check; | &check; |                                           |
| Register-EngineEvent      | &check; | &check; | &check; | &check; | Inga händelse källor är tillgängliga på Linux/macOS |
| Register-ObjectEvent      | &check; | &check; | &check; | &check; |                                           |
| Remove-Alias              |         | &check; | &check; | &check; |                                           |
| Remove-Event              | &check; | &check; | &check; | &check; | Inga händelse källor är tillgängliga på Linux/macOS |
| Remove-PSBreakpoint       | &check; | &check; | &check; | &check; |                                           |
| Remove-TypeData           | &check; | &check; | &check; | &check; |                                           |
| Remove-Variable           | &check; | &check; | &check; | &check; |                                           |
| Select-Object             | &check; | &check; | &check; | &check; |                                           |
| Select-String             | &check; | &check; | &check; | &check; |                                           |
| Select-Xml                | &check; | &check; | &check; | &check; |                                           |
| Send-MailMessage          | &check; | &check; | &check; | &check; |                                           |
| Set-Alias                 | &check; | &check; | &check; | &check; |                                           |
| Set-Date                  | &check; | &check; | &check; | &check; |                                           |
| Set-MarkdownOption        |         |   6.1   | &check; | &check; |                                           |
| Set-PSBreakpoint          | &check; | &check; | &check; | &check; |                                           |
| Set-TraceSource           | &check; | &check; | &check; | &check; |                                           |
| Set-Variable              | &check; | &check; | &check; | &check; |                                           |
| Show-Command              | &check; |         | &check; | &check; | Endast Windows                              |
| Show-Markdown             |         |   6.1   | &check; | &check; |                                           |
| Sort-Object               | &check; | &check; | &check; | &check; |                                           |
| Start-Sleep               | &check; | &check; | &check; | &check; |                                           |
| Tee-Object                | &check; | &check; | &check; | &check; |                                           |
| Test-Json                 |         | &check; | &check; | &check; |                                           |
| Trace-Command             | &check; | &check; | &check; | &check; |                                           |
| Unblock-File              | &check; | &check; | &check; | &check; | Stöd har lagts till för macOS i 7,0            |
| Unregister-Event          | &check; | &check; | &check; | &check; | Inga händelse källor är tillgängliga på Linux/macOS |
| Update-FormatData         | &check; | &check; | &check; | &check; |                                           |
| Update-List               | &check; |         | &check; | &check; |                                           |
| Update-TypeData           | &check; | &check; | &check; | &check; |                                           |
| Wait-Debugger             | &check; | &check; | &check; | &check; |                                           |
| Wait-Event                | &check; | &check; | &check; | &check; |                                           |
| Write-Debug               | &check; | &check; | &check; | &check; |                                           |
| Write-Error               | &check; | &check; | &check; | &check; |                                           |
| Write-Host                | &check; | &check; | &check; | &check; |                                           |
| Write-Information         | &check; | &check; | &check; | &check; |                                           |
| Write-Output              | &check; | &check; | &check; | &check; |                                           |
| Write-Progress            | &check; | &check; | &check; | &check; |                                           |
| Write-Verbose             | &check; | &check; | &check; | &check; |                                           |
| Write-Warning             | &check; | &check; | &check; | &check; |                                           |

### <a name="microsoftwsmanmanagement"></a>Microsoft. WsMan. Management

|      Cmdlet-namn       |   5,1   |   6.x   |   7.0   |   7.1   |     Anteckning     |
| ---------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Connect-WSMan          | &check; | &check; | &check; | &check; | Endast Windows |
| Disable-WSManCredSSP   | &check; | &check; | &check; | &check; | Endast Windows |
| Disconnect-WSMan       | &check; | &check; | &check; | &check; | Endast Windows |
| Enable-WSManCredSSP    | &check; | &check; | &check; | &check; | Endast Windows |
| Get-WSManCredSSP       | &check; | &check; | &check; | &check; | Endast Windows |
| Get-WSManInstance      | &check; | &check; | &check; | &check; | Endast Windows |
| Invoke-WSManAction     | &check; | &check; | &check; | &check; | Endast Windows |
| New-WSManInstance      | &check; | &check; | &check; | &check; | Endast Windows |
| New-WSManSessionOption | &check; | &check; | &check; | &check; | Endast Windows |
| Remove-WSManInstance   | &check; | &check; | &check; | &check; | Endast Windows |
| Set-WSManInstance      | &check; | &check; | &check; | &check; | Endast Windows |
| Set-WSManQuickConfig   | &check; | &check; | &check; | &check; | Endast Windows |
| Test-WSMan             | &check; | &check; | &check; | &check; | Endast Windows |

### <a name="packagemanagement"></a>PackageManagement

|       Cmdlet-namn        |   5,1   |   6.x   |   7.0   |   7.1   | Anteckning |
| ------------------------ | :-----: | :-----: | :-----: | :-----: | ---- |
| Find-Package             | &check; | &check; | &check; | &check; |      |
| Find-PackageProvider     | &check; | &check; | &check; | &check; |      |
| Get-Package              | &check; | &check; | &check; | &check; |      |
| Get-PackageProvider      | &check; | &check; | &check; | &check; |      |
| Get-PackageSource        | &check; | &check; | &check; | &check; |      |
| Import-PackageProvider   | &check; | &check; | &check; | &check; |      |
| Installationspaket          | &check; | &check; | &check; | &check; |      |
| Install-PackageProvider  | &check; | &check; | &check; | &check; |      |
| Register-PackageSource   | &check; | &check; | &check; | &check; |      |
| Save-Package             | &check; | &check; | &check; | &check; |      |
| Set-PackageSource        | &check; | &check; | &check; | &check; |      |
| Uninstall-Package        | &check; | &check; | &check; | &check; |      |
| Unregister-PackageSource | &check; | &check; | &check; | &check; |      |

### <a name="powershellget"></a>PowershellGet

|           Cmdlet-namn           |   5,1   |   6.x   |   7.0   |   7.1   | Anteckning |
| ------------------------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Find-Command                    | &check; | &check; | &check; | &check; |      |
| Find-DscResource                | &check; | &check; | &check; | &check; |      |
| Find-Module                     | &check; | &check; | &check; | &check; |      |
| Find-RoleCapability             | &check; | &check; | &check; | &check; |      |
| Find-Script                     | &check; | &check; | &check; | &check; |      |
| Get-CredsFromCredentialProvider |         | &check; | &check; | &check; |      |
| Get-InstalledModule             | &check; | &check; | &check; | &check; |      |
| Get-InstalledScript             | &check; | &check; | &check; | &check; |      |
| Get-PSRepository                | &check; | &check; | &check; | &check; |      |
| Install-Module                  | &check; | &check; | &check; | &check; |      |
| Install-Script                  | &check; | &check; | &check; | &check; |      |
| New-ScriptFileInfo              | &check; | &check; | &check; | &check; |      |
| Publish-Module                  | &check; | &check; | &check; | &check; |      |
| Publish-Script                  | &check; | &check; | &check; | &check; |      |
| Register-PSRepository           | &check; | &check; | &check; | &check; |      |
| Save-Module                     | &check; | &check; | &check; | &check; |      |
| Save-Script                     | &check; | &check; | &check; | &check; |      |
| Set-PSRepository                | &check; | &check; | &check; | &check; |      |
| Test-ScriptFileInfo             | &check; | &check; | &check; | &check; |      |
| Uninstall-Module                | &check; | &check; | &check; | &check; |      |
| Uninstall-Script                | &check; | &check; | &check; | &check; |      |
| Unregister-PSRepository         | &check; | &check; | &check; | &check; |      |
| Update-Module                   | &check; | &check; | &check; | &check; |      |
| Update-ModuleManifest           | &check; | &check; | &check; | &check; |      |
| Update-Script                   | &check; | &check; | &check; | &check; |      |
| Update-ScriptFileInfo           | &check; | &check; | &check; | &check; |      |

### <a name="psdesiredstateconfiguration"></a>PSDesiredStateConfiguration

|                Cmdlet-namn                 |   5,1   |   6.x   |   7.0   |   7.1   |     Anteckning     |
| ------------------------------------------ | :-----: | :-----: | :-----: | :-----: | ------------ |
| Disable-DscDebug                           | &check; |         |         |         | Endast Windows |
| Enable-DscDebug                            | &check; |         |         |         | Endast Windows |
| Get-DscConfiguration                       | &check; |         |         |         | Endast Windows |
| Get-DscConfigurationStatus                 | &check; |         |         |         | Endast Windows |
| Get-DscLocalConfigurationManager           | &check; |         |         |         | Endast Windows |
| Get-DscResource                            | &check; | &check; | &check; | &check; |              |
| Invoke-DscResource                         | &check; |         | &check; | &check; |              |
| New-DSCCheckSum                            | &check; | &check; | &check; | &check; |              |
| Publish-DscConfiguration                   | &check; |         |         |         | Endast Windows |
| Remove-DscConfigurationDocument            | &check; |         |         |         | Endast Windows |
| Restore-DscConfiguration                   | &check; |         |         |         | Endast Windows |
| Set-DscLocalConfigurationManager           | &check; |         |         |         | Endast Windows |
| Start-DscConfiguration                     | &check; |         |         |         | Endast Windows |
| Stop-DscConfiguration                      | &check; |         |         |         | Endast Windows |
| Test-DscConfiguration                      | &check; |         |         |         | Endast Windows |
| Update-DscConfiguration                    | &check; |         |         |         | Endast Windows |

### <a name="psdiagnostics"></a>PSDiagnostics

|         Cmdlet-namn          |   5,1   |   6.x   |   7.0   |   7.1   |     Anteckning     |
| ---------------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Disable-PSTrace              | &check; |   6,2   | &check; | &check; | Endast Windows |
| Disable-PSWSManCombinedTrace | &check; |   6,2   | &check; | &check; | Endast Windows |
| Disable-WSManTrace           | &check; | &check; | &check; | &check; | Endast Windows |
| Enable-PSTrace               | &check; | &check; | &check; | &check; | Endast Windows |
| Enable-PSWSManCombinedTrace  | &check; | &check; | &check; | &check; | Endast Windows |
| Enable-WSManTrace            | &check; |   6,2   | &check; | &check; | Endast Windows |
| Get-LogProperties            | &check; |   6,2   | &check; | &check; | Endast Windows |
| Set-LogProperties            | &check; |   6,2   | &check; | &check; | Endast Windows |
| Start-Trace                  | &check; |   6,2   | &check; | &check; | Endast Windows |
| Stop-Trace                   | &check; |   6,2   | &check; | &check; | Endast Windows |

### <a name="psreadline"></a>PSReadline

|         Cmdlet-namn         |   5,1   |   6.x   |   7.0   |   7.1   | Anteckning |
| --------------------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Get-PSReadlineKeyHandler    | &check; | &check; | &check; | &check; |      |
| Get-PSReadlineOption        | &check; | &check; | &check; | &check; |      |
| PSConsoleHostReadline       | &check; | &check; | &check; | &check; |      |
| Remove-PSReadlineKeyHandler | &check; | &check; | &check; | &check; |      |
| Set-PSReadlineKeyHandler    | &check; | &check; | &check; | &check; |      |
| Set-PSReadlineOption        | &check; | &check; | &check; | &check; |      |

### <a name="psscheduledjob"></a>PSScheduledJob

|       Cmdlet-namn       |   5,1   | 6.x  |  7.0  |  7.1  |     Anteckning     |
| ----------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Add-JobTrigger          | &check; |      |       |       | Endast Windows |
| Disable-JobTrigger      | &check; |      |       |       | Endast Windows |
| Disable-ScheduledJob    | &check; |      |       |       | Endast Windows |
| Enable-JobTrigger       | &check; |      |       |       | Endast Windows |
| Enable-ScheduledJob     | &check; |      |       |       | Endast Windows |
| Get-JobTrigger          | &check; |      |       |       | Endast Windows |
| Get-ScheduledJob        | &check; |      |       |       | Endast Windows |
| Get-ScheduledJobOption  | &check; |      |       |       | Endast Windows |
| New-JobTrigger          | &check; |      |       |       | Endast Windows |
| New-ScheduledJobOption  | &check; |      |       |       | Endast Windows |
| Register-ScheduledJob   | &check; |      |       |       | Endast Windows |
| Remove-JobTrigger       | &check; |      |       |       | Endast Windows |
| Set-JobTrigger          | &check; |      |       |       | Endast Windows |
| Set-ScheduledJob        | &check; |      |       |       | Endast Windows |
| Set-ScheduledJobOption  | &check; |      |       |       | Endast Windows |
| Unregister-ScheduledJob | &check; |      |       |       | Endast Windows |

### <a name="psworkflow--psworkflowutility"></a>PSWorkflow & PSWorkflowUtility

|          Cmdlet-namn          |   5,1   | 6.x  |  7.0  |  7.1  |     Anteckning     |
| ----------------------------- | :-----: | :--- | :---: | :---: | ------------ |
| New-PSWorkflowExecutionOption | &check; |      |       |       | Endast Windows |
| New-PSWorkflowSession         | &check; |      |       |       | Endast Windows |
| Invoke-AsWorkflow             | &check; |      |       |       | Endast Windows |

### <a name="threadjob"></a>ThreadJob

|   Cmdlet-namn   |  5,1  |   6.x   |   7.0   |   7.1   | Anteckning |
| --------------- | :---: | :-----: | :-----: | :-----: | ---- |
| Start-ThreadJob |       | &check; | &check; | &check; | Kan installeras i PowerShell 5,1 |
