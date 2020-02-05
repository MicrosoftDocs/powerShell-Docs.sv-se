---
ms.date: 02/03/2020
keywords: PowerShell, Core
title: Versions historik för moduler och cmdletar
ms.openlocfilehash: e421201d74da2cc74b1bd57529fb3c3e5245ecae
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995443"
---
# <a name="release-history-of-modules-and-cmdlets"></a>Versions historik för moduler och cmdletar

Den här artikeln innehåller moduler och cmdletar som levereras med olika versioner av PowerShell. Det här är en sammanfattning av information som finns i viktig information. Mer detaljerad information finns i versions anteckningarna:

- [Nyheter i PowerShell Core 6,2](what-s-new-in-powershell-core-62.md)
- [Nyheter i PowerShell Core 6,1](what-s-new-in-powershell-core-61.md)
- [Nyheter i PowerShell Core 6,0](what-s-new-in-powershell-core-60.md)
- [Bryta ändringar i PowerShell Core 6,0](breaking-changes-ps6.md)
- [Kända problem i PowerShell Core 6,0](known-issues-ps6.md)

Detta är ett pågående arbete. Hjälp oss att uppdatera den här informationen.

## <a name="module-release-history"></a>Versions historik för modul

|         Modulnamn/PS-version          |   5,1   |   6.x   |   7.0   |   7.1   |     Obs!     |
| ----------------------------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| CimCmdlets                                | &check; | &check; | &check; | &check; | Endast Windows |
| ISE (lanserades i 2,0)                   | &check; |         |         |         | Endast Windows |
| Microsoft. PowerShell. Archive              | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.Core                 | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.Diagnostics          | &check; | &check; | &check; | &check; | Endast Windows |
| Microsoft. PowerShell. Host                 | &check; | &check; | &check; | &check; |              |
| Microsoft. PowerShell. LocalAccounts        | &check; |         |         |         | Endast Windows |
| Microsoft.PowerShell.Management           | &check; | &check; | &check; | &check; |              |
| Microsoft. PowerShell. ODataUtils           | &check; |         |         |         | Endast Windows |
| Microsoft. PowerShell. operation. Validation | &check; |         |         |         | Endast Windows |
| Microsoft.PowerShell.Security             | &check; | &check; | &check; | &check; |              |
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
| ThreadJob                                 |         | &check; | &check; | &check; |              |

## <a name="cmdlet-release-history"></a>Versions historik för cmdlet

### <a name="cimcmdlets"></a>CimCmdlets

|         Cmdlet-namn         |   5,1   |   6.x   |   7.0   |   7.1   |     Obs!     |
| --------------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Exportera – BinaryMiLog          | &check; | &check; | &check; | &check; | Endast Windows |
| Get-CimAssociatedInstance   | &check; | &check; | &check; | &check; | Endast Windows |
| Get-CimClass                | &check; | &check; | &check; | &check; | Endast Windows |
| Get-CimInstance             | &check; | &check; | &check; | &check; | Endast Windows |
| Get-CimSession              | &check; | &check; | &check; | &check; | Endast Windows |
| Importera – BinaryMiLog          | &check; | &check; | &check; | &check; | Endast Windows |
| Invoke-CimMethod            | &check; | &check; | &check; | &check; | Endast Windows |
| New-CimInstance             | &check; | &check; | &check; | &check; | Endast Windows |
| New-CimSession              | &check; | &check; | &check; | &check; | Endast Windows |
| New-CimSessionOption        | &check; | &check; | &check; | &check; | Endast Windows |
| Registrera – CimIndicationEvent | &check; | &check; | &check; | &check; | Endast Windows |
| Remove-CimInstance          | &check; | &check; | &check; | &check; | Endast Windows |
| Remove-CimSession           | &check; | &check; | &check; | &check; | Endast Windows |
| Set-CimInstance             | &check; | &check; | &check; | &check; | Endast Windows |

### <a name="ise-introduced-in-20"></a>ISE (lanserades i 2,0)

|    Cmdlet-namn    |   5,1   | 6.x  |  7.0  |  7.1  |     Obs!     |
| ----------------- | :-----: | :--- | :---: | :---: | ------------ |
| Get-IseSnippet    | &check; |      |       |       | Endast Windows |
| Importera – IseSnippet | &check; |      |       |       | Endast Windows |
| New-IseSnippet    | &check; |      |       |       | Endast Windows |


### <a name="microsoftpowershellarchive"></a>Microsoft. PowerShell. Archive

|   Cmdlet-namn    |   5,1   |   6.x   |   7.0   |   7.1   | Obs! |
| ---------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Komprimera – arkivera | &check; | &check; | &check; | &check; |      |
| Expandera – arkivera   | &check; | &check; | &check; | &check; |      |

### <a name="microsoftpowershellcore"></a>Microsoft.PowerShell.Core

|            Cmdlet-namn            |   5,1   |   6.x   |   7.0   |   7.1   |            Obs!            |
| --------------------------------- | :-----: | :-----: | :-----: | :-----: | -------------------------- |
| Lägg till-historik                       | &check; | &check; | &check; | &check; |                            |
| Add-PSSnapin                      | &check; |         |         |         | Endast Windows               |
| Rensa – historik                     | &check; | &check; | &check; | &check; |                            |
| Rensa värd                        | &check; | &check; | &check; | &check; |                            |
| Anslut – PSSession                 | &check; | &check; | &check; | &check; | Endast Windows               |
| Fel sökning – jobb                         | &check; | &check; | &check; | &check; |                            |
| Disable-ExperimentalFeature       |         |   6.2   | &check; | &check; |                            |
| Disable-PSRemoting                | &check; | &check; | &check; | &check; | Endast Windows               |
| Disable-PSSessionConfiguration    | &check; | &check; | &check; | &check; | Endast Windows               |
| Koppla från-PSSession              | &check; | &check; | &check; | &check; | Endast Windows               |
| Aktivera – ExperimentalFeature        |         |   6.2   | &check; | &check; |                            |
| Enable-PSRemoting                 | &check; | &check; | &check; | &check; | Endast Windows               |
| Aktivera – PSSessionConfiguration     | &check; | &check; | &check; | &check; | Endast Windows               |
| Retur-PSHostProcess               | &check; | &check; | &check; | &check; | Linux-stöd har lagts till i 6,2 |
| Retur-PSSession                   | &check; | &check; | &check; | &check; |                            |
| Avsluta-PSHostProcess                | &check; | &check; | &check; | &check; | Linux-stöd har lagts till i 6,2 |
| Avsluta-PSSession                    | &check; | &check; | &check; | &check; |                            |
| Exportera-konsol                    | &check; |         |         |         | Endast Windows               |
| Exportera – ModuleMember               | &check; | &check; | &check; | &check; |                            |
| -Objekt                    | &check; | &check; | &check; | &check; |                            |
| Get-Command                       | &check; | &check; | &check; | &check; |                            |
| Get-ExperimentalFeature           |         |   6.2   | &check; | &check; |                            |
| Get – hjälp                          | &check; | &check; | &check; | &check; |                            |
| Hämta historik                       | &check; | &check; | &check; | &check; |                            |
| Hämta jobb                           | &check; | &check; | &check; | &check; |                            |
| Hämta modul                        | &check; | &check; | &check; | &check; |                            |
| Get-PSHostProcessInfo             | &check; | &check; | &check; | &check; | Linux-stöd har lagts till i 6,2 |
| Get-PSSession                     | &check; | &check; | &check; | &check; |                            |
| Get-PSSessionCapability           | &check; | &check; | &check; | &check; |                            |
| Get-PSSessionConfiguration        | &check; | &check; | &check; | &check; |                            |
| Get-PSSnapin                      | &check; |         |         |         | Endast Windows               |
| Get-verb                          | &check; |         |         |         | Endast Windows               |
| Importera-modul                     | &check; | &check; | &check; | &check; |                            |
| Invoke-kommando                    | &check; | &check; | &check; | &check; |                            |
| Anropa-historik                    | &check; | &check; | &check; | &check; |                            |
| Ny modul                        | &check; | &check; | &check; | &check; |                            |
| New-ModuleManifest                | &check; | &check; | &check; | &check; |                            |
| New-PSRoleCapabilityFile          | &check; | &check; | &check; | &check; |                            |
| New-PSSession                     | &check; | &check; | &check; | &check; |                            |
| New-PSSessionConfigurationFile    | &check; | &check; | &check; | &check; | Endast Windows               |
| New-PSSessionOption               | &check; | &check; | &check; | &check; |                            |
| New-PSTransportOption             | &check; | &check; | &check; | &check; |                            |
| Ut-standard                       | &check; | &check; | &check; | &check; |                            |
| Ut-värd                          | &check; | &check; | &check; | &check; |                            |
| Ut-null                          | &check; | &check; | &check; | &check; |                            |
| Mottagning – jobb                       | &check; | &check; | &check; | &check; |                            |
| Ta emot – PSSession                 | &check; | &check; | &check; | &check; | Endast Windows               |
| Registrera – ArgumentCompleter        | &check; | &check; | &check; | &check; |                            |
| Registrera – PSSessionConfiguration   | &check; | &check; | &check; | &check; | Endast Windows               |
| Ta bort – jobb                        | &check; | &check; | &check; | &check; |                            |
| Ta bort modul                     | &check; | &check; | &check; | &check; |                            |
| Remove-PSSession                  | &check; | &check; | &check; | &check; |                            |
| Remove-PSSnapin                   | &check; |         |         |         | Endast Windows               |
| Återuppta – jobb                        | &check; |         |         |         |                            |
| Spara – hjälp                         | &check; | &check; | &check; | &check; |                            |
| Set-PSDebug                       | &check; | &check; | &check; | &check; |                            |
| Set-PSSessionConfiguration        | &check; | &check; | &check; | &check; | Endast Windows               |
| Set-StrictMode                    | &check; | &check; | &check; | &check; |                            |
| Start – jobb                         | &check; | &check; | &check; | &check; |                            |
| Stoppa – jobb                          | &check; | &check; | &check; | &check; |                            |
| Pausa – jobb                       | &check; |         |         |         | Endast Windows               |
| Test-ModuleManifest               | &check; | &check; | &check; | &check; |                            |
| Test-PSSessionConfigurationFile   | &check; | &check; | &check; | &check; | Endast Windows               |
| Avregistrera-PSSessionConfiguration | &check; | &check; | &check; | &check; | Endast Windows               |
| Uppdatera – hjälp                       | &check; | &check; | &check; | &check; |                            |
| Wait-Job                          | &check; | &check; | &check; | &check; |                            |
| Where-objekt                      | &check; | &check; | &check; | &check; |                            |

### <a name="microsoftpowershelldiagnostics"></a>Microsoft.PowerShell.Diagnostics

|  Cmdlet-namn   |   5,1   |   6.x   |   7.0   |   7.1   |     Obs!     |
| -------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Exportera – räknare | &check; |         |         |         | Endast Windows |
| Hämta räknare    | &check; |         | &check; | &check; | Endast Windows |
| Get-WinEvent   | &check; | &check; | &check; | &check; | Endast Windows |
| Importera – räknare | &check; |         |         |         | Endast Windows |
| New-WinEvent   | &check; | &check; | &check; | &check; | Endast Windows |

### <a name="microsoftpowershellhost"></a>Microsoft. PowerShell. Host

|   Cmdlet-namn    |   5,1   |   6.x   |   7.0   |   7.1   | Obs! |
| ---------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Start-avskrift | &check; | &check; | &check; | &check; |      |
| Stopp-avskrift  | &check; | &check; | &check; | &check; |      |

### <a name="microsoftpowershelllocalaccounts"></a>Microsoft. PowerShell. LocalAccounts

|       Cmdlet-namn       |   5,1   | 6.x  |  7.0  |  7.1  |     Obs!     |
| ----------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Add-LocalGroupMember    | &check; |      |       |       | Endast Windows |
| Disable-lokal användare       | &check; |      |       |       | Endast Windows |
| Aktivera – lokal användare        | &check; |      |       |       | Endast Windows |
| Get-LocalGroup          | &check; |      |       |       | Endast Windows |
| Get-LocalGroupMember    | &check; |      |       |       | Endast Windows |
| Get-lokal användare           | &check; |      |       |       | Endast Windows |
| New-LocalGroup          | &check; |      |       |       | Endast Windows |
| New-lokal användare           | &check; |      |       |       | Endast Windows |
| Ta bort-LocalGroup       | &check; |      |       |       | Endast Windows |
| Remove-LocalGroupMember | &check; |      |       |       | Endast Windows |
| Remove-lokal användare        | &check; |      |       |       | Endast Windows |
| Byt namn – lokal       | &check; |      |       |       | Endast Windows |
| Byt namn – lokal användare        | &check; |      |       |       | Endast Windows |
| Set-LocalGroup          | &check; |      |       |       | Endast Windows |
| Set-lokal användare           | &check; |      |       |       | Endast Windows |

### <a name="microsoftpowershellmanagement"></a>Microsoft.PowerShell.Management

|          Cmdlet-namn          |   5,1   |   6.x   |   7.0   |   7.1   |               Obs!               |
| ----------------------------- | :-----: | :-----: | :-----: | :-----: | -------------------------------- |
| Lägg till dator                  | &check; |         |         |         | Endast Windows                     |
| Lägg till innehåll                   | &check; | &check; | &check; | &check; |                                  |
| Checkpoint-Computer           | &check; |         |         |         | Endast Windows                     |
| Rensa innehåll                 | &check; | &check; | &check; | &check; |                                  |
| Rensa-EventLog                | &check; |         |         |         | Endast Windows                     |
| Rensa objekt                    | &check; | &check; | &check; | &check; |                                  |
| Clear-ItemProperty            | &check; | &check; | &check; | &check; |                                  |
| Clear-RecycleBin              | &check; |         | &check; | &check; | Endast Windows                     |
| Slutförd transaktion          | &check; |         |         |         | Endast Windows                     |
| Konvertera-sökväg                  | &check; | &check; | &check; | &check; |                                  |
| Kopiera objekt                     | &check; | &check; | &check; | &check; |                                  |
| Kopiera – ItemProperty             | &check; | &check; | &check; | &check; |                                  |
| Fel sökning – process                 | &check; | &check; | &check; | &check; |                                  |
| Disable-ComputerRestore       | &check; |         |         |         | Endast Windows                     |
| Aktivera – ComputerRestore        | &check; |         |         |         | Endast Windows                     |
| Get-ChildItem                 | &check; | &check; | &check; | &check; |                                  |
| Hämta Urklipp                 | &check; |         | &check; | &check; | Stöds inte på macOS           |
| Get-ComputerInfo              | &check; | &check; | &check; | &check; |                                  |
| Get-ComputerRestorePoint      | &check; |         |         |         | Endast Windows                     |
| Hämta innehåll                   | &check; | &check; | &check; | &check; |                                  |
| Get-ControlPanelItem          | &check; |         |         |         | Endast Windows                     |
| Get-EventLog                  | &check; |         |         |         | Endast Windows                     |
| Hämta snabb korrigering                    | &check; |         | &check; | &check; | Endast Windows                     |
| Hämta objekt                      | &check; | &check; | &check; | &check; |                                  |
| Get-ItemProperty              | &check; | &check; | &check; | &check; |                                  |
| Get-ItemPropertyValue         | &check; | &check; | &check; | &check; |                                  |
| Get-location                  | &check; | &check; | &check; | &check; |                                  |
| Hämta process                   | &check; | &check; | &check; | &check; |                                  |
| Get-PSDrive                   | &check; | &check; | &check; | &check; |                                  |
| Get-PSProvider                | &check; | &check; | &check; | &check; |                                  |
| Get-Service                   | &check; | &check; | &check; | &check; | Endast Windows                     |
| Get-TimeZone                  | &check; | &check; | &check; | &check; |                                  |
| Hämta transaktion               | &check; |         |         |         | Endast Windows                     |
| Get-WmiObject                 | &check; |         |         |         | Endast Windows                     |
| Anropa-objekt                   | &check; | &check; | &check; | &check; |                                  |
| Invoke-WmiMethod              | &check; |         |         |         | Endast Windows                     |
| Anslut till sökväg                     | &check; | &check; | &check; | &check; |                                  |
| Begränsning-EventLog                | &check; |         |         |         | Endast Windows                     |
| Flytta objekt                     | &check; | &check; | &check; | &check; |                                  |
| Move-ItemProperty             | &check; | &check; | &check; | &check; |                                  |
| Ny-EventLog                  | &check; |         |         |         | Endast Windows                     |
| Nytt objekt                      | &check; | &check; | &check; | &check; |                                  |
| New-ItemProperty              | &check; | &check; | &check; | &check; |                                  |
| New-PSDrive                   | &check; | &check; | &check; | &check; |                                  |
| New-Service                   | &check; | &check; | &check; | &check; | Endast Windows                     |
| New-WebServiceProxy           | &check; |         |         |         | Endast Windows                     |
| Pop-location                  | &check; | &check; | &check; | &check; |                                  |
| Push-plats                 | &check; | &check; | &check; | &check; |                                  |
| Registrera – WmiEvent             | &check; |         |         |         | Endast Windows                     |
| Ta bort dator               | &check; |         |         |         | Endast Windows                     |
| Ta bort-EventLog               | &check; |         |         |         | Endast Windows                     |
| Ta bort objekt                   | &check; | &check; | &check; | &check; |                                  |
| Remove-ItemProperty           | &check; | &check; | &check; | &check; |                                  |
| Remove-PSDrive                | &check; | &check; | &check; | &check; |                                  |
| Remove-service                |         | &check; | &check; | &check; | Endast Windows                     |
| Remove-WmiObject              | &check; |         |         |         | Endast Windows                     |
| Byt namn – dator               | &check; | &check; | &check; | &check; |                                  |
| Byt namn – objekt                   | &check; | &check; | &check; | &check; |                                  |
| Byt namn – ItemProperty           | &check; | &check; | &check; | &check; |                                  |
| Återställ-ComputerMachinePassword | &check; |         |         |         | Endast Windows                     |
| Lös-sökväg                  | &check; | &check; | &check; | &check; |                                  |
| Starta om datorn              | &check; | &check; | &check; | &check; |                                  |
| Restart-Service               | &check; | &check; | &check; | &check; | Endast Windows                     |
| Återställa-dator              | &check; |         |         |         | Endast Windows                     |
| Resume-Service                | &check; | &check; | &check; | &check; | Endast Windows                     |
| Ange Urklipp                 | &check; |         | &check; | &check; |                                  |
| Ange innehåll                   | &check; | &check; | &check; | &check; |                                  |
| Ange objekt                      | &check; | &check; | &check; | &check; |                                  |
| Set-ItemProperty              | &check; | &check; | &check; | &check; |                                  |
| Ange plats                  | &check; | &check; | &check; | &check; |                                  |
| Set-Service                   | &check; | &check; | &check; | &check; | Endast Windows                     |
| Ange-TimeZone                  | &check; | &check; | &check; | &check; |                                  |
| Set-WmiInstance               | &check; |         |         |         | Endast Windows                     |
| Visa ControlPanelItem         | &check; |         |         |         | Endast Windows                     |
| Visa-EventLog                 | &check; |         |         |         | Endast Windows                     |
| Dela-sökväg                    | &check; | &check; | &check; | &check; |                                  |
| Start process                 | &check; | &check; | &check; | &check; |                                  |
| Start-Service                 | &check; | &check; | &check; | &check; | Endast Windows                     |
| Starta transaktion             | &check; |         |         |         | Endast Windows                     |
| Stoppa – dator                 | &check; | &check; | &check; | &check; | Stöd för Linux/macOS har lagts till i 7,0 |
| Stoppa – process                  | &check; | &check; | &check; | &check; |                                  |
| Stop-Service                  | &check; | &check; | &check; | &check; | Endast Windows                     |
| Suspend-Service               | &check; | &check; | &check; | &check; | Endast Windows                     |
| Test-ComputerSecureChannel    | &check; |         |         |         | Endast Windows                     |
| Test-Connection               | &check; | &check; | &check; | &check; |                                  |
| Test-sökväg                     | &check; | &check; | &check; | &check; |                                  |
| Ångra-transaktion              | &check; |         |         |         | Endast Windows                     |
| Använd transaktion               | &check; |         |         |         | Endast Windows                     |
| Vänta-process                  | &check; | &check; | &check; | &check; | Fungerar inte på Linux/macOS     |
| Skriv-EventLog                | &check; |         |         |         | Endast Windows                     |

### <a name="microsoftpowershellodatautils"></a>Microsoft. PowerShell. ODataUtils

|        Cmdlet-namn        |   5,1   | 6.x  |  7.0  |  7.1  |     Obs!     |
| ------------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Exportera – ODataEndpointProxy | &check; |      |       |       | Endast Windows |

### <a name="microsoftpowershelloperationvalidation"></a>Microsoft. PowerShell. operation. Validation

|        Cmdlet-namn         |   5,1   | 6.x  |  7.0  |  7.1  |     Obs!     |
| -------------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Get-OperationValidation    | &check; |      |       |       | Endast Windows |
| Invoke-OperationValidation | &check; |      |       |       | Endast Windows |

### <a name="microsoftpowershellsecurity"></a>Microsoft.PowerShell.Security

|        Cmdlet-namn        |   5,1   |   6.x   |   7.0   |   7.1   |                  Obs!                   |
| ------------------------- | :-----: | :-----: | :-----: | :-----: | --------------------------------------- |
| ConvertFrom – SecureString  | &check; | &check; | &check; | &check; |                                         |
| ConvertTo – SecureString    | &check; | &check; | &check; | &check; |                                         |
| Get-ACL                   | &check; | &check; | &check; | &check; | Endast Windows                            |
| Get-AuthenticodeSignature | &check; | &check; | &check; | &check; | Endast Windows                            |
| Get-CmsMessage            | &check; | &check; | &check; | &check; | Endast Windows                            |
| Get-Credential            | &check; | &check; | &check; | &check; |                                         |
| Get-ExecutionPolicy       | &check; | &check; | &check; | &check; | Returnerar **obegränsade** på Linux/MacOS |
| Get-PfxCertificate        | &check; | &check; | &check; | &check; |                                         |
| New-FileCatalog           | &check; | &check; | &check; | &check; | Endast Windows                            |
| Skydda – CmsMessage        | &check; | &check; | &check; | &check; | Endast Windows                            |
| Ange ACL                   | &check; | &check; | &check; | &check; | Endast Windows                            |
| Set-AuthenticodeSignature | &check; | &check; | &check; | &check; | Endast Windows                            |
| Set-ExecutionPolicy       | &check; | &check; | &check; | &check; | Händer ingenting på Linux/macOS             |
| Test-FileCatalog          | &check; | &check; | &check; | &check; | Endast Windows                            |
| Ta bort skydd-CmsMessage      | &check; | &check; | &check; | &check; | Endast Windows                            |

### <a name="microsoftpowershellutility"></a>Microsoft.PowerShell.Utility

|        Cmdlet-namn        |   5,1   |   6.x   |   7.0   |   7.1   |                   Obs!                    |
| ------------------------- | :-----: | :-----: | :-----: | :-----: | ----------------------------------------- |
| Lägg till medlem                | &check; | &check; | &check; | &check; |                                           |
| Lägg till typ                  | &check; | &check; | &check; | &check; |                                           |
| Clear-Variable            | &check; | &check; | &check; | &check; |                                           |
| Jämför objekt            | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-CSV           | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom – JSON          | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom – markdown      |         |   6.1   | &check; | &check; |                                           |
| ConvertFrom-SddlString    | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-sträng        | &check; |         |         |         |                                           |
| ConvertFrom-StringData    | &check; | &check; | &check; | &check; |                                           |
| Convert-String            | &check; |         |         |         |                                           |
| ConvertTo-Csv             | &check; | &check; | &check; | &check; |                                           |
| ConvertTo-Html            | &check; | &check; | &check; | &check; |                                           |
| ConvertTo-Json            | &check; | &check; | &check; | &check; |                                           |
| ConvertTo-Xml             | &check; | &check; | &check; | &check; |                                           |
| Felsök – körnings utrymme            | &check; | &check; | &check; | &check; |                                           |
| Disable-PSBreakpoint      | &check; | &check; | &check; | &check; |                                           |
| Disable-RunspaceDebug     | &check; | &check; | &check; | &check; |                                           |
| Aktivera – PSBreakpoint       | &check; | &check; | &check; | &check; |                                           |
| Aktivera – RunspaceDebug      | &check; | &check; | &check; | &check; |                                           |
| Exportera-alias              | &check; | &check; | &check; | &check; |                                           |
| Exportera – CliXml             | &check; | &check; | &check; | &check; |                                           |
| Export-Csv                | &check; | &check; | &check; | &check; |                                           |
| Exportera – FormatData         | &check; | &check; | &check; | &check; |                                           |
| Exportera – PSSession          | &check; | &check; | &check; | &check; |                                           |
| Format-Custom             | &check; | &check; | &check; | &check; |                                           |
| Format-Hex                | &check; | &check; | &check; | &check; |                                           |
| Format-List               | &check; | &check; | &check; | &check; |                                           |
| Format-Table              | &check; | &check; | &check; | &check; |                                           |
| Format-Wide               | &check; | &check; | &check; | &check; |                                           |
| Get-alias                 | &check; | &check; | &check; | &check; |                                           |
| Get-Culture               | &check; | &check; | &check; | &check; |                                           |
| Hämta datum                  | &check; | &check; | &check; | &check; |                                           |
| Get-Error                 |         |         | &check; | &check; |                                           |
| Hämta händelse                 | &check; | &check; | &check; | &check; | Inga händelse källor är tillgängliga på Linux/macOS |
| Get-EventSubscriber       | &check; | &check; | &check; | &check; |                                           |
| Get-FileHash              | &check; | &check; | &check; | &check; |                                           |
| Get-FormatData            | &check; | &check; | &check; | &check; |                                           |
| Hämta värd                  | &check; | &check; | &check; | &check; |                                           |
| Get-MarkdownOption        |         |   6.1   | &check; | &check; |                                           |
| Hämta medlem                | &check; | &check; | &check; | &check; |                                           |
| Get-PSBreakpoint          | &check; | &check; | &check; | &check; |                                           |
| Get-PSCallStack           | &check; | &check; | &check; | &check; |                                           |
| Hämta slumpmässiga                | &check; | &check; | &check; | &check; |                                           |
| Get-körnings utrymme              | &check; | &check; | &check; | &check; |                                           |
| Get-RunspaceDebug         | &check; | &check; | &check; | &check; |                                           |
| Get-TraceSource           | &check; | &check; | &check; | &check; |                                           |
| Get-TypeData              | &check; | &check; | &check; | &check; |                                           |
| Get-värdet             | &check; | &check; | &check; | &check; |                                           |
| Hämta unika                | &check; | &check; | &check; | &check; |                                           |
| Hämta drift tid                |         | &check; | &check; | &check; |                                           |
| Get-Variable              | &check; | &check; | &check; | &check; |                                           |
| Get-verb                  |         | &check; | &check; | &check; |                                           |
| Gruppera objekt              | &check; | &check; | &check; | &check; |                                           |
| Importera-alias              | &check; | &check; | &check; | &check; |                                           |
| Importera – CliXml             | &check; | &check; | &check; | &check; |                                           |
| Import-Csv                | &check; | &check; | &check; | &check; |                                           |
| Importera – LocalizedData      | &check; | &check; | &check; | &check; |                                           |
| Importera – PowerShellDataFile | &check; | &check; | &check; | &check; |                                           |
| Importera – PSSession          | &check; | &check; | &check; | &check; |                                           |
| Invoke-uttryck         | &check; | &check; | &check; | &check; |                                           |
| Invoke-RestMethod         | &check; | &check; | &check; | &check; |                                           |
| Anropa-webbegäran         | &check; | &check; | &check; | &check; |                                           |
| Anslut till sträng               |         | &check; | &check; | &check; |                                           |
| Measure-Command           | &check; | &check; | &check; | &check; |                                           |
| Mått – objekt            | &check; | &check; | &check; | &check; |                                           |
| Nytt-alias                 | &check; | &check; | &check; | &check; |                                           |
| Ny händelse                 | &check; | &check; | &check; | &check; | Inga händelse källor är tillgängliga på Linux/macOS |
| New-Guid                  | &check; | &check; | &check; | &check; |                                           |
| Nytt – objekt                | &check; | &check; | &check; | &check; |                                           |
| New-TemporaryFile         | &check; | &check; | &check; | &check; |                                           |
| New-TimeSpan              | &check; | &check; | &check; | &check; |                                           |
| Ny variabel              | &check; | &check; | &check; | &check; |                                           |
| Ut-fil                  | &check; | &check; | &check; | &check; |                                           |
| Out-GridView              | &check; |         | &check; | &check; |                                           |
| Out-Printer               | &check; |         | &check; | &check; |                                           |
| Out-sträng                | &check; | &check; | &check; | &check; |                                           |
| Read-Host                 | &check; | &check; | &check; | &check; |                                           |
| Registrera – EngineEvent      | &check; | &check; | &check; | &check; | Inga händelse källor är tillgängliga på Linux/macOS |
| Registrera – ObjectEvent      | &check; | &check; | &check; | &check; |                                           |
| Ta bort-alias              |         | &check; | &check; | &check; |                                           |
| Ta bort händelse              | &check; | &check; | &check; | &check; | Inga händelse källor är tillgängliga på Linux/macOS |
| Remove-PSBreakpoint       | &check; | &check; | &check; | &check; |                                           |
| Remove-TypeData           | &check; | &check; | &check; | &check; |                                           |
| Ta bort variabel           | &check; | &check; | &check; | &check; |                                           |
| Select-Object             | &check; | &check; | &check; | &check; |                                           |
| Select-String             | &check; | &check; | &check; | &check; |                                           |
| Select-XML                | &check; | &check; | &check; | &check; |                                           |
| Skicka meddelande          | &check; | &check; | &check; | &check; |                                           |
| Set-alias                 | &check; | &check; | &check; | &check; |                                           |
| Ange datum                  | &check; | &check; | &check; | &check; |                                           |
| Set-MarkdownOption        |         |   6.1   | &check; | &check; |                                           |
| Set-PSBreakpoint          | &check; | &check; | &check; | &check; |                                           |
| Set-TraceSource           | &check; | &check; | &check; | &check; |                                           |
| Set-Variable              | &check; | &check; | &check; | &check; |                                           |
| Visa-kommando              | &check; |         | &check; | &check; |                                           |
| Visa markdown             |         |   6.1   | &check; | &check; |                                           |
| Sortera objekt               | &check; | &check; | &check; | &check; |                                           |
| Start-vilo läge               | &check; | &check; | &check; | &check; |                                           |
| Tee – objekt                | &check; | &check; | &check; | &check; |                                           |
| Test-JSON                 |         | &check; | &check; | &check; |                                           |
| Spåra-kommando             | &check; | &check; | &check; | &check; |                                           |
| Avblockera – fil              | &check; | &check; | &check; | &check; | Stöd har lagts till för macOS i 7,0            |
| Avregistrera-händelse          | &check; | &check; | &check; | &check; | Inga händelse källor är tillgängliga på Linux/macOS |
| Uppdatera – FormatData         | &check; | &check; | &check; | &check; |                                           |
| Update-List               | &check; |         | &check; | &check; |                                           |
| Uppdatera – TypeData           | &check; | &check; | &check; | &check; |                                           |
| Vänta – fel sökning             | &check; | &check; | &check; | &check; |                                           |
| Vänta-händelse                | &check; | &check; | &check; | &check; |                                           |
| Skriv-debug               | &check; | &check; | &check; | &check; |                                           |
| Skriv-fel               | &check; | &check; | &check; | &check; |                                           |
| Skriv värd                | &check; | &check; | &check; | &check; |                                           |
| Skriv information         | &check; | &check; | &check; | &check; |                                           |
| Skriva-utdata              | &check; | &check; | &check; | &check; |                                           |
| Skriv förlopp            | &check; | &check; | &check; | &check; |                                           |
| Skriv-verbose             | &check; | &check; | &check; | &check; |                                           |
| Skriv varning             | &check; | &check; | &check; | &check; |                                           |

### <a name="microsoftwsmanmanagement"></a>Microsoft. WsMan. Management

|      Cmdlet-namn       |   5,1   |   6.x   |   7.0   |   7.1   |     Obs!     |
| ---------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Anslut-WSMan          | &check; | &check; | &check; | &check; | Endast Windows |
| Disable-WSManCredSSP   | &check; | &check; | &check; | &check; | Endast Windows |
| Koppla från-WSMan       | &check; | &check; | &check; | &check; | Endast Windows |
| Aktivera – WSManCredSSP    | &check; | &check; | &check; | &check; | Endast Windows |
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

|       Cmdlet-namn        |   5,1   |   6.x   |   7.0   |   7.1   | Obs! |
| ------------------------ | :-----: | :-----: | :-----: | :-----: | ---- |
| Sök-paket             | &check; | &check; | &check; | &check; |      |
| Find-PackageProvider     | &check; | &check; | &check; | &check; |      |
| Get-Package              | &check; | &check; | &check; | &check; |      |
| Get-PackageProvider      | &check; | &check; | &check; | &check; |      |
| Get-PackageSource        | &check; | &check; | &check; | &check; |      |
| Importera – PackageProvider   | &check; | &check; | &check; | &check; |      |
| Installera paket          | &check; | &check; | &check; | &check; |      |
| Installera-PackageProvider  | &check; | &check; | &check; | &check; |      |
| Registrera – PackageSource   | &check; | &check; | &check; | &check; |      |
| Spara paket             | &check; | &check; | &check; | &check; |      |
| Set-PackageSource        | &check; | &check; | &check; | &check; |      |
| Avinstallera paket        | &check; | &check; | &check; | &check; |      |
| Unregister-PackageSource | &check; | &check; | &check; | &check; |      |

### <a name="powershellget"></a>PowershellGet

|           Cmdlet-namn           |   5,1   |   6.x   |   7.0   |   7.1   | Obs! |
| ------------------------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Sök-kommando                    | &check; | &check; | &check; | &check; |      |
| Find-Dscresource Keyword Supports                | &check; | &check; | &check; | &check; |      |
| Sök-modul                     | &check; | &check; | &check; | &check; |      |
| Find-RoleCapability             | &check; | &check; | &check; | &check; |      |
| Sök – skript                     | &check; | &check; | &check; | &check; |      |
| Get-CredsFromCredentialProvider |         | &check; | &check; | &check; |      |
| Get-InstalledModule             | &check; | &check; | &check; | &check; |      |
| Get-InstalledScript             | &check; | &check; | &check; | &check; |      |
| Get-PSRepository                | &check; | &check; | &check; | &check; |      |
| Installera-modul                  | &check; | &check; | &check; | &check; |      |
| Installera – skript                  | &check; | &check; | &check; | &check; |      |
| New-ScriptFileInfo              | &check; | &check; | &check; | &check; |      |
| Publicera-modul                  | &check; | &check; | &check; | &check; |      |
| Publicera – skript                  | &check; | &check; | &check; | &check; |      |
| Registrera – PSRepository           | &check; | &check; | &check; | &check; |      |
| Spara-modul                     | &check; | &check; | &check; | &check; |      |
| Spara – skript                     | &check; | &check; | &check; | &check; |      |
| Set-PSRepository                | &check; | &check; | &check; | &check; |      |
| Test-ScriptFileInfo             | &check; | &check; | &check; | &check; |      |
| Avinstallera-modul                | &check; | &check; | &check; | &check; |      |
| Avinstallera – skript                | &check; | &check; | &check; | &check; |      |
| Avregistrera-PSRepository         | &check; | &check; | &check; | &check; |      |
| Update-modul                   | &check; | &check; | &check; | &check; |      |
| Uppdatera – ModuleManifest           | &check; | &check; | &check; | &check; |      |
| Uppdatera skript                   | &check; | &check; | &check; | &check; |      |
| Uppdatera – ScriptFileInfo           | &check; | &check; | &check; | &check; |      |

### <a name="psdesiredstateconfiguration"></a>PSDesiredStateConfiguration

|                Cmdlet-namn                 |   5,1   |   6.x   |   7.0   |   7.1   |     Obs!     |
| ------------------------------------------ | :-----: | :-----: | :-----: | :-----: | ------------ |
| Add-NodeKeys                               |         | &check; |         |         |              |
| ConvertTo – MOFInstance                      |         | &check; |         |         |              |
| Disable-DscDebug                           | &check; |         |         |         | Endast Windows |
| Aktivera – DscDebug                            | &check; |         |         |         | Endast Windows |
| Generera – VersionInfo                       |         | &check; |         |         |              |
| Get-CompatibleVersionAddtionaPropertiesStr |         | &check; |         |         |              |
| Get-ComplexResourceQualifier               |         | &check; |         |         |              |
| Get-ConfigurationErrorCount                |         | &check; |         |         |              |
| Get-DscConfiguration                       | &check; |         |         |         | Endast Windows |
| Get-DscConfigurationStatus                 | &check; |         |         |         | Endast Windows |
| Get-DscLocalConfigurationManager           | &check; |         |         |         | Endast Windows |
| Get-Dscresource Keyword Supports                            | &check; | &check; | &check; | &check; |              |
| Get-DSCResourceModules                     |         | &check; |         |         |              |
| Get-EncryptedPassword                      |         | &check; |         |         |              |
| Get-InnerMostErrorRecord                   |         | &check; |         |         |              |
| Get-MofInstanceName                        |         | &check; |         |         |              |
| Get-MofInstanceText                        |         | &check; |         |         |              |
| Get-PositionInfo                           |         | &check; |         |         |              |
| Get-PSCurrentConfigurationNode             |         | &check; |         |         |              |
| Get-PSDefaultConfigurationDocument         |         | &check; |         |         |              |
| Get-PSMetaConfigDocumentInstVersionInfo    |         | &check; |         |         |              |
| Get-PSMetaConfigurationProcessed           |         | &check; |         |         |              |
| Get-PSTopConfigurationName                 |         | &check; |         |         |              |
| Get-PublicKeyFromFile                      |         | &check; |         |         |              |
| Get-PublicKeyFromStore                     |         | &check; |         |         |              |
| Initiera-ConfigurationRuntimeState       |         | &check; |         |         |              |
| Invoke-Dscresource Keyword Supports                         | &check; |         | &check; | &check; |              |
| New-DSCCheckSum                            | &check; | &check; | &check; | &check; |              |
| Publicera – DscConfiguration                   | &check; |         |         |         | Endast Windows |
| Remove-DscConfigurationDocument            | &check; |         |         |         | Endast Windows |
| Restore-DscConfiguration                   | &check; |         |         |         | Endast Windows |
| Set-DscLocalConfigurationManager           | &check; |         |         |         | Endast Windows |
| Set-NodeExclusiveResources                 |         | &check; |         |         |              |
| Set-NodeManager                            |         | &check; |         |         |              |
| Set-NodeResources                          |         | &check; |         |         |              |
| Set-NodeResourceSource                     |         | &check; |         |         |              |
| Set-PSCurrentConfigurationNode             |         | &check; |         |         |              |
| Set-PSDefaultConfigurationDocument         |         | &check; |         |         |              |
| Set-PSMetaConfigDocInsProcessedBeforeMeta  |         | &check; |         |         |              |
| Set-PSMetaConfigVersionInfoV2              |         | &check; |         |         |              |
| Set-PSTopConfigurationName                 |         | &check; |         |         |              |
| Start-DscConfiguration                     | &check; |         |         |         | Endast Windows |
| Stop-DscConfiguration                      | &check; |         |         |         | Endast Windows |
| Test-ConflictingResources                  |         | &check; |         |         |              |
| Test-DscConfiguration                      | &check; |         |         |         | Endast Windows |
| Test-ModuleReloadRequired                  |         | &check; |         |         |              |
| Test-MofInstanceText                       |         | &check; |         |         |              |
| Test-NodeManager                           |         | &check; |         |         |              |
| Test-NodeResources                         |         | &check; |         |         |              |
| Test-NodeResourceSource                    |         | &check; |         |         |              |
| Uppdatera – ConfigurationDocumentRef            |         | &check; |         |         |              |
| Uppdatera – ConfigurationErrorCount             |         | &check; |         |         |              |
| Uppdatera – DependsOn                           |         | &check; |         |         |              |
| Uppdatera – DscConfiguration                    | &check; |         |         |         | Endast Windows |
| Uppdatera – LocalConfigManager                  |         | &check; |         |         |              |
| Uppdatera – ModuleVersion                       |         | &check; |         |         |              |
| ValidateUpdate – ConfigurationData           |         | &check; |         |         |              |
| Skriv logg                                  |         | &check; |         |         |              |
| Write-MetaConfigFile                       |         | &check; |         |         |              |
| Write-NodeMOFFile                          |         | &check; |         |         |              |

### <a name="psdiagnostics"></a>PSDiagnostics

|         Cmdlet-namn          |   5,1   |   6.x   |   7.0   |   7.1   |     Obs!     |
| ---------------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Disable-PSTrace              | &check; |   6.2   | &check; | &check; | Endast Windows |
| Disable-PSWSManCombinedTrace | &check; |   6.2   | &check; | &check; | Endast Windows |
| Disable-WSManTrace           | &check; | &check; | &check; | &check; | Endast Windows |
| Aktivera – PSTrace               | &check; | &check; | &check; | &check; | Endast Windows |
| Aktivera – PSWSManCombinedTrace  | &check; | &check; | &check; | &check; | Endast Windows |
| Aktivera – WSManTrace            | &check; |   6.2   | &check; | &check; | Endast Windows |
| Get-LogProperties            | &check; |   6.2   | &check; | &check; | Endast Windows |
| Set-LogProperties            | &check; |   6.2   | &check; | &check; | Endast Windows |
| Starta spårning                  | &check; |   6.2   | &check; | &check; | Endast Windows |
| Stoppa – spåra                   | &check; |   6.2   | &check; | &check; | Endast Windows |

### <a name="psreadline"></a>PSReadline

|         Cmdlet-namn         |   5,1   |   6.x   |   7.0   |   7.1   | Obs! |
| --------------------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Get-PSReadlineKeyHandler    | &check; | &check; | &check; | &check; |      |
| Get-PSReadlineOption        | &check; | &check; | &check; | &check; |      |
| PSConsoleHostReadline       | &check; | &check; | &check; | &check; |      |
| Remove-PSReadlineKeyHandler | &check; | &check; | &check; | &check; |      |
| Set-PSReadlineKeyHandler    | &check; | &check; | &check; | &check; |      |
| Set-PSReadlineOption        | &check; | &check; | &check; | &check; |      |

### <a name="psscheduledjob"></a>PSScheduledJob

|       Cmdlet-namn       |   5,1   | 6.x  |  7.0  |  7.1  |     Obs!     |
| ----------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Add-JobTrigger          | &check; |      |       |       | Endast Windows |
| Disable-JobTrigger      | &check; |      |       |       | Endast Windows |
| Disable-ScheduledJob    | &check; |      |       |       | Endast Windows |
| Aktivera – JobTrigger       | &check; |      |       |       | Endast Windows |
| Aktivera – ScheduledJob     | &check; |      |       |       | Endast Windows |
| Get-JobTrigger          | &check; |      |       |       | Endast Windows |
| Get-ScheduledJob        | &check; |      |       |       | Endast Windows |
| Get-ScheduledJobOption  | &check; |      |       |       | Endast Windows |
| New-JobTrigger          | &check; |      |       |       | Endast Windows |
| New-ScheduledJobOption  | &check; |      |       |       | Endast Windows |
| Registrera – ScheduledJob   | &check; |      |       |       | Endast Windows |
| Remove-JobTrigger       | &check; |      |       |       | Endast Windows |
| Set-JobTrigger          | &check; |      |       |       | Endast Windows |
| Set-ScheduledJob        | &check; |      |       |       | Endast Windows |
| Set-ScheduledJobOption  | &check; |      |       |       | Endast Windows |
| Avregistrera-ScheduledJob | &check; |      |       |       | Endast Windows |

### <a name="psworkflow--psworkflowutility"></a>PSWorkflow & PSWorkflowUtility

|          Cmdlet-namn          |   5,1   | 6.x  |  7.0  |  7.1  |     Obs!     |
| ----------------------------- | :-----: | :--- | :---: | :---: | ------------ |
| New-PSWorkflowExecutionOption | &check; |      |       |       | Endast Windows |
| New-PSWorkflowSession         | &check; |      |       |       | Endast Windows |
| Invoke-arbetsflöde             | &check; |      |       |       | Endast Windows |

### <a name="threadjob"></a>ThreadJob

|   Cmdlet-namn   |  5,1  |   6.x   |   7.0   |   7.1   | Obs! |
| --------------- | :---: | :-----: | :-----: | :-----: | ---- |
| Start-ThreadJob |       | &check; | &check; | &check; |      |
