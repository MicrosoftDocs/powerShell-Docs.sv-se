---
title: PowerShell 7-modulens kompatibilitet
ms.date: 02/03/2020
description: Den här artikeln visar statusen för PowerShell 7 med PowerShell-moduler publicerade för andra Microsoft-produkter.
ms.openlocfilehash: f845b33881c93fa076d97adf101f4f3e006df73b
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501634"
---
# <a name="powershell-7-module-compatibility"></a>PowerShell 7-modulens kompatibilitet

Den här artikeln innehåller en lista med PowerShell-moduler som publicerats av Microsoft. De här modulerna ger hantering och stöd för olika Microsoft-produkter och-tjänster. Dessa moduler har uppdaterats för att fungera internt med PowerShell 7 eller testas för kompatibilitet med PowerShell 7. Den här listan kommer att uppdateras med ny information när fler moduler identifieras och testas.

Om du har information om att dela eller problem med specifika moduler, så kan du skicka ett problem i [WindowsCompatibility-lagrings platsen](https://github.com/PowerShell/WindowsCompatibility).

## <a name="windows-management-modules"></a>Windows Management-moduler

Windows Management-modulen installeras på olika sätt beroende på Windows-versionen och hur modulen paketerades för den versionen.

Använd funktions namnet med cmdleten [Install-WindowsFeature](/powershell/module/servermanager/install-windowsfeature) som administratör på Windows Server. Exempel:

```powershell
Install-WindowsFeature -Name ActiveDirectory
```

I Windows 10 görs Windows Management-moduler tillgängliga som Windows- **valfria funktioner** eller **Windows-funktioner**. Följande kommandon måste köras från en upphöjd session med hjälp av **Kör som-administratör**.

- För valfria Windows-funktioner

  Kör följande kommando för att få en lista över valfria funktioner:

  ```powershell
  Get-WindowsOptionalFeature -Online
  ```

  Så här installerar du funktionen:

  ```powershell
  Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V-Management-PowerShell
  ```

  Mer information finns i:

  - [Get-WindowsOptionalFeature](/powershell/module/dism/get-windowsoptionalfeature)
  - [Aktivera – WindowsOptionalFeature](/powershell/module/dism/enable-windowsoptionalfeature)

- För Windows-funktioner

  Kör följande kommando för att få en lista över Windows-funktioner:

  ```powershell
  Get-WindowsCapability -online
  ```

  Observera att namnet på funktions paketet slutar med `~~~~0.0.1.0` . Du måste använda det fullständiga namnet för att installera funktionen:

  ```powershell
  Add-WindowsCapability -Online -Name Rsat.ServerManager.Tools~~~~0.0.1.0
  ```

  Mer information finns i:

  - [Get-WindowsCapability](/powershell/module/dism/get-windowscapability)
  - [Add-WindowsCapability](/powershell/module/dism/add-windowscapability)

### <a name="module-list"></a>Lista över moduler

| Modulnamn                        | Status                               | Operativ system som stöds                       |
| ---------------------------------- | ------------------------------------ | ---------------------------------- |
| ActiveDirectory                    | Internt kompatibel                  | Windows Server 1809 + med RSAT-AD-PowerShell<br>Windows 10 1809 + med RSAT. ActiveDirectory. DS-LDS. tools |
| ADDSDeployment                     | Fungerar med kompatibilitetsläge       |  Windows Server 2019 1809 +         |
| ADFS                               | Testat med kompatibilitetsläge    |                                    |
| AppBackgroundTask                  | Internt kompatibel                  | Windows 10-1903 +                   |
| AppLocker                          | Testat med kompatibilitetsläge    |                                    |
| AppvClient                         | Testat med kompatibilitetsläge    |                                    |
| Appx                               | Internt kompatibel                  | Windows Server 1809 +<br>Windows 10-1809 + |
| AssignedAccess                     | Internt kompatibel                  | Windows 10-1809 +                   |
| BestPractices                      | Stöds inte av kompatibilitetsläge |                                    |
| BitLocker                          | Internt kompatibel                  | Windows Server 1809 + med BitLocker<br>Windows 10-1809 + |
| BitsTransfer                       | Internt kompatibel                  | Windows Server-20H1<br>Windows 10-20H1 |
| BootEventCollector                 | Testat med kompatibilitetsläge    |                                        |
| BranchCache                        | Internt kompatibel                  | Windows Server 1809 +<br>Windows 10-1809 + |
| CimCmdlets                         | Internt kompatibel                  | Inbyggd i PowerShell 7 |
| ClusterAwareUpdating               | Testat med kompatibilitetsläge    |                         |
| ConfigCI                           | Testat med kompatibilitetsläge    |                         |
| Defender                           | Internt kompatibel                  | Windows Server 1809 +<br>Windows 10-1809 +  |
| DeliveryOptimization               | Internt kompatibel                  | Windows Server 1903 +<br>Windows 10-1903 +  |
| DFSN                               | Internt kompatibel                  | Windows Server 1809 + med FS-DFS-namnrymd<br>Windows 10 1809 + med RSAT. FailoverCluster. Management. tools |
| DFSR                               | Testat med kompatibilitetsläge    |                                   |
| Server                         | Testat med kompatibilitetsläge    |                                   |
| DirectAccessClientComponents       | Internt kompatibel                  | Windows Server 1809 +<br>Windows 10-1809 +  |
| Kommandoradssyntax                               | Internt kompatibel                  | Windows Server 1903 +<br>Windows 10-1903 +  |
| DnsClient                          | Internt kompatibel                  | Windows Server 1809 +<br>Windows 10-1809 +  |
| DNS Server                          | Internt kompatibel                  | Windows Server 1809 + med DNS eller RSAT-DNS-Server<br>Windows 10 1809 + med RSAT. DNS. tools |
| EventTracingManagement             | Internt kompatibel                  | Windows Server 1809 +<br>Windows 10-1809 +  |
| FailoverClusters                   | Testat med kompatibilitetsläge    |                                  |
| FailoverClusterSet                 | Testat med kompatibilitetsläge    |                                  |
| FileServerResourceManager          | Internt kompatibel                  | Windows Server 1809 + med FS – Resource Manager |
| GroupPolicy                        | Testat med kompatibilitetsläge    |                                               |
| HgsClient                          | Internt kompatibel                  | Windows Server 1903 + med Hyper-V eller RSAT-skärmad-VM-tools<br>Windows 10 1903 + med RSAT. skärmade. VM. tools |
| HgsDiagnostics                     | Internt kompatibel                  | Windows Server 1809 + med Hyper-V eller RSAT-skärmad-VM-tools<br>Windows 10 1809 + med RSAT. skärmade. VM. tools |
| Hyper-V                            | Internt kompatibel                  | Windows Server 1809 + med Hyper-V – PowerShell<br>Windows 10 1809 + med Microsoft-Hyper-V-Management – PowerShell |
| Administrationsmodul                  | Testat med kompatibilitetsläge    |                                               |
| Standarder                      | Internt kompatibel                  | Windows Server 1903 +<br>Windows 10-1903 +      |
| IpamServer                         | Testat med kompatibilitetsläge    |                                               |
| iSCSI                              | Testat med kompatibilitetsläge    |                                               |
| IscsiTarget                        | Testat med kompatibilitetsläge    |                                               |
| ISE                                | Testat med kompatibilitetsläge    |                                               |
| KDs                                | Internt kompatibel                  | Windows Server-20H1<br>Windows 10-20H1        |
| Microsoft. PowerShell. Archive       | Internt kompatibel                  | Inbyggd i PowerShell 7                       |
| Microsoft. PowerShell. Diagnostics   | Internt kompatibel                  | Inbyggd i PowerShell 7                       |
| Microsoft. PowerShell. Host          | Internt kompatibel                  | Inbyggd i PowerShell 7                       |
| Microsoft. PowerShell. LocalAccounts | Internt kompatibel                  | Windows Server 1809 +<br>Windows 10-1809 +      |
| Microsoft. PowerShell. Management    | Internt kompatibel                  | Inbyggd i PowerShell 7                       |
| Microsoft. PowerShell. ODataUtils    | Testat med kompatibilitetsläge    |                                               |
| Microsoft. PowerShell. Security      | Internt kompatibel                  | Inbyggd i PowerShell 7                       |
| Microsoft.PowerShell.Utility       | Internt kompatibel                  | Inbyggd i PowerShell 7                       |
| Microsoft. WSMan. Management         | Internt kompatibel                  | Inbyggd i PowerShell 7                       |
| MMAgent                            | Internt kompatibel                  | Windows Server 1809 +<br>Windows 10-1809 +      |
| MPIO                               | Internt kompatibel                  | Windows Server 1809 + med multipath-IO        |
| MsDtc                              | Testat med kompatibilitetsläge    |                                               |
| NetAdapter                         | Internt kompatibel                  | Windows Server 1809 +<br>Windows 10-1809 +      |
| NetConnection                      | Internt kompatibel                  | Windows Server 1809 +<br>Windows 10-1809 +      |
| NetEventPacketCapture              | Internt kompatibel                  | Windows Server 1809 +<br>Windows 10-1809 +      |
| NetLbfo                            | Internt kompatibel                  | Windows Server 1809 +<br>Windows 10-1809 +      |
| NetLldpAgent                       | Testat med kompatibilitetsläge    |                                               |
| NetNat                             | Internt kompatibel                  | Windows Server 1809 +<br>Windows 10-1809 +      |
| NetQos                             | Internt kompatibel                  | Windows Server 1809 +<br>Windows 10-1809 +      |
| Netsäkerhet                        | Internt kompatibel                  | Windows Server 1809 +<br>Windows 10-1809 +      |
| NetSwitchTeam                      | Internt kompatibel                  | Windows Server 1809 +<br>Windows 10-1809 +      |
| Nettcpip                           | Internt kompatibel                  | Windows Server 1809 +<br>Windows 10-1809 +      |
| NetWNV                             | Testat med kompatibilitetsläge    |                                               |
| NetworkConnectivityStatus          | Internt kompatibel                  | Windows Server 1809 +<br>Windows 10-1809 +      |
| NetworkController                  | Testat med kompatibilitetsläge    |                                               |
| NetworkControllerDiagnostics       | Testat med kompatibilitetsläge    |                                               |
| NetworkLoadBalancingClusters       | Testat med kompatibilitetsläge    |                                               |
| NetworkSwitchManager               | Internt kompatibel                  | Windows Server 1809 +<br>Windows 10-1809 +      |
| NetworkTransition                  | Internt kompatibel                  | Windows Server 1809 +<br>Windows 10-1809 +      |
| NFS                                | Internt kompatibel                  | Windows Server 1809 +<br>Windows 10 1809 + med RSAT. ServerManager. tools |
| PackageManagement                  | Internt kompatibel                  | Inbyggd i PowerShell 7                       |
| PcsvDevice                         | Internt kompatibel                  | Windows Server 1809 +<br>Windows 10-1809 +      |
| PersistentMemory                   | Testat med kompatibilitetsläge    |                                               |
| PKI                                | Testat med kompatibilitetsläge    |                                               |
| PnpDevice                          | Internt kompatibel                  | Windows Server 1809 +<br>Windows 10-1809 +      |
| PowerShellGet                      | Internt kompatibel                  | Inbyggd i PowerShell 7                       |
| PrintManagement                    | Internt kompatibel                  | Windows Server 1903 + med Print-Services<br>Windows 10-1903 +  |
| ProcessMitigations                 | Internt kompatibel                  | Windows Server 1903 +<br>Windows 10-1903 +      |
| Etablering                       | Testat med kompatibilitetsläge    |                                               |
| PSDesiredStateConfiguration        | Delvis                            | Inbyggd i PowerShell 7                       |
| PSDiagnostics                      | Internt kompatibel                  | Inbyggd i PowerShell 7                       |
| PSScheduledJob                     | Stöds inte av kompatibilitetsläge | Inbyggt i PowerShell 5,1                     |
| PSWorkflow                         | Testat med kompatibilitetsläge    |                                               |
| PSWorkflowUtility                  | Testat med kompatibilitetsläge    |                                               |
| RemoteAccess                       | Testat med kompatibilitetsläge    |                                               |
| RemoteDesktop                      | Testat med kompatibilitetsläge    |                                               |
| ScheduledTasks                     | Internt kompatibel                  | Windows Server 1809 +<br>Windows 10-1809 +      |
| SecureBoot                         | Internt kompatibel                  | Windows Server 1809 +<br>Windows 10-1809 +      |
| ServerCore                         | Testat med kompatibilitetsläge    |                                               |
| ServerManager                      | Internt kompatibel                  | Windows Server 1809 +<br>Windows 10 1809 + med RSAT. ServerManager. tools<br>_Se anteckningar nedan_ |
| ServerManagerTasks                 | Testat med kompatibilitetsläge    |                                               |
| ShieldedVMDataFile                 | Internt kompatibel                  | Windows Server 1903 + med RSAT-avskärmade-VM-tools<br>Windows 10 1903 + med RSAT. skärmade. VM. tools |
| ShieldedVMProvisioning             | Internt kompatibel                  | Windows Server 1809 + med HostGuardian<br>Windows 10 1809 + med HostGuardian  |
| ShieldedVMTemplate                 | Internt kompatibel                  | Windows Server 1809 + med RSAT-avskärmade-VM-tools<br>Windows 10 1809 + med RSAT. skärmade. VM. tools |
| SmbShare                           | Internt kompatibel                  | Windows Server 1809 +<br>Windows 10-1809 +      |
| SmbWitness                         | Internt kompatibel                  | Windows Server 1809 +<br>Windows 10-1809 +      |
| SMISConfig                         | Internt kompatibel                  | Windows Server 1903 + med WindowsStorageManagementService |
| SMS                                | Testat med kompatibilitetsläge    |                                               |
| SoftwareInventoryLogging           | Internt kompatibel                  | Windows Server 1809 +                          |
| StartLayout                        | Internt kompatibel                  | Windows Server 1809 + med Skriv bords miljö<br>Windows 10-1809 + |
| Storage                            | Internt kompatibel                  | Windows Server 1809 +<br>Windows 10-1809 +      |
| StorageBusCache                    | Testat med kompatibilitetsläge    |                                               |
| StorageMigrationService            | Testat med kompatibilitetsläge    |                                               |
| StorageQOS                         | Internt kompatibel                  | Windows Server 1809 + med RSAT-klustring – PowerShell<br>Windows 10 1809 + med RSAT. FailoverCluster. Management. tools |
| StorageReplica                     | Testat med kompatibilitetsläge    |                                               |
| SyncShare                          | Internt kompatibel                  | Windows Server 1809 + med FS-SyncShareService |
| SystemInsights                     | Testat med kompatibilitetsläge    |                                               |
| TLS                                | Testat med kompatibilitetsläge    |                                               |
| TroubleshootingPack                | Internt kompatibel                  | Windows 10-1903 +                              |
| TrustedPlatformModule              | Internt kompatibel                  | Windows Server 1809 +<br>Windows 10-1809 +      |
| UEV                                | Internt kompatibel                  | Windows Server? En framtida version av server med Skriv bords miljö?<br>Windows 10-1903 + |
| UpdateServices                     | Stöds inte av kompatibilitetsläge |                                               |
| VpnClient                          | Internt kompatibel                  | Windows Server 1809 +<br>Windows 10-1809 +      |
| Wdac                               | Internt kompatibel                  | Windows Server 1809 +<br>Windows 10-1809 +      |
| Webadministration                  | Testat med kompatibilitetsläge    |                                               |
| WHEA                               | Internt kompatibel                  | Windows Server 1903 +<br>Windows 10-1903 +      |
| WindowsDeveloperLicense            | Internt kompatibel                  | Windows Server 1809 + med Skriv bords miljö<br>Windows 10-1809 + |
| WindowsErrorReporting              | Internt kompatibel                  | Windows Server 1809 +<br>Windows 10-1809 +      |
| WindowsSearch                      | Internt kompatibel                  | Windows 10-1903 +                              |
| WindowsServerBackup                | Internt kompatibel                  | Windows Server-19H2 med Windows-Server – säkerhets kopiering |
| WindowsUpdate                      | Internt kompatibel                  | Windows Server 1809 +<br>Windows 10-1809 +       |
| WindowsUpdateProvider              | Internt kompatibel                  | Windows Server 1809 +<br>Windows 10-1809 +       |

## <a name="notes"></a>Anteckningar

### <a name="servermanager-module"></a>ServerManager-modul

Modulen har vissa mindre kompatibilitetsproblem med formaterade utdata i PowerShell 7. Till exempel `Get-WindowsFeature` returnerar cmdleten rätt objekt med alla egenskaper, men standardformateringen för visningen gör att vissa egenskaper visas som tomma. De faktiska värdena är tillgängliga i objekt egenskaperna med `Select-Object` eller direkt medlems åtkomst.

