---
title: PowerShell 7-modulens kompatibilitet
ms.date: 02/03/2020
ms.openlocfilehash: 1f7a2f4fa04e07b8f56635d0a39e580924ae0134
ms.sourcegitcommit: d34841a44742af1123da007fefbdc24a2f1762dd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/07/2020
ms.locfileid: "78926201"
---
# <a name="powershell-7-module-compatibility"></a>PowerShell 7-modulens kompatibilitet

Den här artikeln innehåller en lista med PowerShell-moduler som publicerats av Microsoft och som ger hantering och stöd för olika Microsoft-produkter och-tjänster. Dessa moduler har uppdaterats för att fungera internt med PowerShell 7 eller testas för kompatibilitet med PowerShell 7.

Den här listan kommer att uppdateras med ny information när fler moduler identifieras och testas. Om du har information om att dela eller problem med specifika moduler, så kan du skicka ett problem i [WindowsCompatibility](https://github.com/PowerShell/WindowsCompatibility) -lagringsplatsen.

## <a name="windows-management-modules"></a>Windows Management-moduler

Windows Management-modulerna installeras på olika sätt beroende på vilken typ av Windows och hur modulen paketerades. Dessa moduler måste installeras från en utökad PowerShell-session med alternativet **Kör som administratör** .

På Windows Server använder du funktions namnet med [Install-WindowsFeature](/powershell/module/servermanager/install-windowsfeature) för att installera modulen. Exempel:

```powershell
Install-WindowsFeature -Name ActiveDirectory
```

I Windows 10 måste du använda en av dessa cmdlets, beroende på paket typen:
- [Aktivera – WindowsOptionalFeature](/powershell/module/dism/enable-windowsoptionalfeature)
- [Add-WindowsCapability](/powershell/module/dism/add-windowscapability)

För moduler som installeras som Windows-funktioner:

```powershell
Enable-WindowsOptionalFeature -Online -FeatureName FooFeatureName
```

För moduler som installeras som Windows-funktioner måste du lägga till `~~~~0.0.1.0` i slutet av paket namnet. Exempel:

```powershell
Add-WindowsCapability -Online -Name Rsat.ServerManager.Tools~~~~0.0.1.0
```

### <a name="activedirectory"></a>ActiveDirectory

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 + med RSAT-AD-PowerShell
- Windows 10-version: 1809 + med RSAT. ActiveDirectory. DS-LDS. tools

### <a name="adfs"></a>ADFS

Status: avtestat med kompatibilitetsläge

### <a name="appbackgroundtask"></a>AppBackgroundTask

Status: internt kompatibel

Kompatibel med:

- Windows 10-version: 1903 +

### <a name="applocker"></a>AppLocker

Status: avtestat med kompatibilitetsläge

### <a name="appvclient"></a>AppvClient

Status: avtestat med kompatibilitetsläge

### <a name="appx"></a>Appx

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 +
- Windows 10-version: 1809 +

### <a name="assignedaccess"></a>AssignedAccess

Status: internt kompatibel

Kompatibel med:

- Windows 10-version: 1809 +

### <a name="bestpractices"></a>BestPractices

Status: avtestat med kompatibilitetsläge

### <a name="bitlocker"></a>BitLocker

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 + med BitLocker
- Windows 10-version: 1809 +

### <a name="bitstransfer"></a>BitsTransfer

Status: internt kompatibel

Kompatibel med:

- Server version: 20H1
- Windows 10-version: 20H1

### <a name="booteventcollector"></a>BootEventCollector

Status: avtestat med kompatibilitetsläge

### <a name="branchcache"></a>BranchCache

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 +
- Windows 10-version: 1809 +

### <a name="cimcmdlets"></a>CimCmdlets

Status: internt kompatibel

Kompatibel med:

- Inbyggd i PowerShell 7

### <a name="clusterawareupdating"></a>ClusterAwareUpdating

Status: avtestat med kompatibilitetsläge

### <a name="configci"></a>ConfigCI

Status: avtestat med kompatibilitetsläge

### <a name="defender"></a>Defender

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 +
- Windows 10-version: 1809 +

### <a name="deliveryoptimization"></a>DeliveryOptimization

Status: internt kompatibel

Kompatibel med:

- Server version: 1903 +
- Windows 10-version: 1903 +

### <a name="dfsn"></a>DFSN

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 + med FS-DFS-namnrymd
- Windows 10-version: 1809 + med RSAT. FailoverCluster. Management. tools

### <a name="dfsr"></a>DFSR

Status: avtestat med kompatibilitetsläge

### <a name="dhcpserver"></a>Server

Status: avtestat med kompatibilitetsläge

### <a name="directaccessclientcomponents"></a>DirectAccessClientComponents

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 +
- Windows 10-version: 1809 +

### <a name="dism"></a>Kommandoradssyntax

Status: internt kompatibel

Kompatibel med:

- Server version: 1903 +
- Windows 10-version: 1903 +

### <a name="dnsclient"></a>DnsClient

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 +
- Windows 10-version: 1809 +

### <a name="dnsserver"></a>DnsServer

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 + med DNS eller RSAT-DNS-Server
- Windows 10-version: 1809 + med RSAT. DNS. tools

### <a name="eventtracingmanagement"></a>EventTracingManagement

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 +
- Windows 10-version: 1809 +

### <a name="failoverclusters"></a>FailoverClusters

Status: avtestat med kompatibilitetsläge

### <a name="failoverclusterset"></a>FailoverClusterSet

Status: avtestat med kompatibilitetsläge

### <a name="fileserverresourcemanager"></a>FileServerResourceManager

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 + med FS – Resource Manager

### <a name="grouppolicy"></a>GroupPolicy

Status: avtestat med kompatibilitetsläge

### <a name="hgsclient"></a>HgsClient

Status: internt kompatibel

Kompatibel med:

- Server version: 1903 + med Hyper-V eller RSAT-skärmad-VM-tools
- Windows 10-version: 1903 + med RSAT. skärmad. VM. tools

### <a name="hgsdiagnostics"></a>HgsDiagnostics

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 + med Hyper-V eller RSAT-skärmad-VM-tools
- Windows 10-version: 1809 + med RSAT. skärmad. VM. tools

### <a name="hyper-v"></a>Hyper-V

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 + med Hyper-V – PowerShell
- Windows 10-version: 1809 + med Microsoft-Hyper-V-Management – PowerShell

### <a name="iisadministration"></a>Administrationsmodul

Status: avtestat med kompatibilitetsläge

### <a name="international"></a>Standarder

Status: internt kompatibel

Kompatibel med:

- Server version: 1903 +
- Windows 10-version: 1903 +

### <a name="ipamserver"></a>IpamServer

Status: avtestat med kompatibilitetsläge

### <a name="iscsi"></a>iSCSI

Status: avtestat med kompatibilitetsläge

### <a name="iscsitarget"></a>IscsiTarget

Status: avtestat med kompatibilitetsläge

### <a name="ise"></a>ISE

Status: avtestat med kompatibilitetsläge

### <a name="kds"></a>KDs

Status: internt kompatibel

Kompatibel med:

- Server version: 20H1
- Windows 10-version: 20H1

### <a name="microsoftpowershellarchive"></a>Microsoft. PowerShell. Archive

Status: internt kompatibel

Kompatibel med:

- Inbyggd i PowerShell 7

### <a name="microsoftpowershelldiagnostics"></a>Microsoft.PowerShell.Diagnostics

Status: internt kompatibel

Kompatibel med:

- Inbyggd i PowerShell 7

### <a name="microsoftpowershellhost"></a>Microsoft.PowerShell.Host

Status: internt kompatibel

Kompatibel med:

- Inbyggd i PowerShell 7

### <a name="microsoftpowershelllocalaccounts"></a>Microsoft. PowerShell. LocalAccounts

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 +
- Windows 10-version: 1809 +

### <a name="microsoftpowershellmanagement"></a>Microsoft.PowerShell.Management

Status: internt kompatibel

Kompatibel med:

- Inbyggd i PowerShell 7

### <a name="microsoftpowershellodatautils"></a>Microsoft. PowerShell. ODataUtils

Status: avtestat med kompatibilitetsläge

### <a name="microsoftpowershellsecurity"></a>Microsoft.PowerShell.Security

Status: internt kompatibel

Kompatibel med:

- Inbyggd i PowerShell 7

### <a name="microsoftpowershellutility"></a>Microsoft.PowerShell.Utility

Status: internt kompatibel

Kompatibel med:

- Inbyggd i PowerShell 7

### <a name="microsoftwsmanmanagement"></a>Microsoft.WSMan.Management

Status: internt kompatibel

Kompatibel med:

- Inbyggd i PowerShell 7

### <a name="mmagent"></a>MMAgent

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 +
- Windows 10-version: 1809 +

### <a name="mpio"></a>MPIO

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 + med multipath-IO

### <a name="msdtc"></a>MsDtc

Status: avtestat med kompatibilitetsläge

### <a name="netadapter"></a>NetAdapter

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 +
- Windows 10-version: 1809 +

### <a name="netconnection"></a>NetConnection

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 +
- Windows 10-version: 1809 +

### <a name="neteventpacketcapture"></a>NetEventPacketCapture

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 +
- Windows 10-version: 1809 +

### <a name="netlbfo"></a>NetLbfo

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 +
- Windows 10-version: 1809 +

### <a name="netlldpagent"></a>NetLldpAgent

Status: avtestat med kompatibilitetsläge

### <a name="netnat"></a>NetNat

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 +
- Windows 10-version: 1809 +

### <a name="netqos"></a>NetQos

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 +
- Windows 10-version: 1809 +

### <a name="netsecurity"></a>Netsäkerhet

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 +
- Windows 10-version: 1809 +

### <a name="netswitchteam"></a>NetSwitchTeam

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 +
- Windows 10-version: 1809 +

### <a name="nettcpip"></a>Nettcpip

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 +
- Windows 10-version: 1809 +

### <a name="netwnv"></a>NetWNV

Status: avtestat med kompatibilitetsläge

### <a name="networkconnectivitystatus"></a>NetworkConnectivityStatus

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 +
- Windows 10-version: 1809 +

### <a name="networkcontroller"></a>NetworkController

Status: avtestat med kompatibilitetsläge

### <a name="networkcontrollerdiagnostics"></a>NetworkControllerDiagnostics

Status: avtestat med kompatibilitetsläge

### <a name="networkloadbalancingclusters"></a>NetworkLoadBalancingClusters

Status: avtestat med kompatibilitetsläge

### <a name="networkswitchmanager"></a>NetworkSwitchManager

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 +
- Windows 10-version: 1809 +

### <a name="networktransition"></a>NetworkTransition

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 +
- Windows 10-version: 1809 +

### <a name="nfs"></a>NFS

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 +
- Windows 10-version: 1809 + med RSAT. ServerManager. tools

### <a name="packagemanagement"></a>PackageManagement

Status: internt kompatibel

Kompatibel med:

- Inbyggd i PowerShell 7

### <a name="pcsvdevice"></a>PcsvDevice

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 +
- Windows 10-version: 1809 +

### <a name="persistentmemory"></a>PersistentMemory

Status: avtestat med kompatibilitetsläge

### <a name="pki"></a>PKI

Status: avtestat med kompatibilitetsläge

### <a name="pnpdevice"></a>PnpDevice

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 +
- Windows 10-version: 1809 +

### <a name="powershellget"></a>PowerShellGet

Status: internt kompatibel

Kompatibel med:

- Inbyggd i PowerShell 7

### <a name="printmanagement"></a>PrintManagement

Status: internt kompatibel

Kompatibel med:

- Server version: 1903 + med utskrifts tjänster
- Windows 10-version: 1903 +

### <a name="processmitigations"></a>ProcessMitigations

Status: internt kompatibel

Kompatibel med:

- Server version: 1903 +
- Windows 10-version: 1903 +

### <a name="provisioning"></a>Etablering

Status: avtestat med kompatibilitetsläge

### <a name="psdesiredstateconfiguration"></a>PSDesiredStateConfiguration

Status: delvis

Kompatibel med:

- Inbyggd i PowerShell 7

### <a name="psdiagnostics"></a>PSDiagnostics

Status: internt kompatibel

Kompatibel med:

- Inbyggd i PowerShell 7

### <a name="psscheduledjob"></a>PSScheduledJob

Status: fungerar inte med kompatibilitetsläge

Kompatibel med:

- Inbyggt i PowerShell 5,1

### <a name="psworkflow"></a>PSWorkflow

Status: avtestat med kompatibilitetsläge

### <a name="psworkflowutility"></a>PSWorkflowUtility

Status: avtestat med kompatibilitetsläge

### <a name="remoteaccess"></a>RemoteAccess

Status: avtestat med kompatibilitetsläge

### <a name="remotedesktop"></a>RemoteDesktop

Status: avtestat med kompatibilitetsläge

### <a name="scheduledtasks"></a>ScheduledTasks

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 +
- Windows 10-version: 1809 +

### <a name="secureboot"></a>SecureBoot

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 +
- Windows 10-version: 1809 +

### <a name="servercore"></a>ServerCore

Status: avtestat med kompatibilitetsläge

### <a name="servermanager"></a>ServerManager

Status: avtestat med kompatibilitetsläge

### <a name="servermanagertasks"></a>ServerManagerTasks

Status: avtestat med kompatibilitetsläge

### <a name="shieldedvmdatafile"></a>ShieldedVMDataFile

Status: internt kompatibel

Kompatibel med:

- Server version: 1903 + med RSAT-skärmad-VM-tools
- Windows 10-version: 1903 + med RSAT. skärmad. VM. tools

### <a name="shieldedvmprovisioning"></a>ShieldedVMProvisioning

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 + med HostGuardian
- Windows 10-version: 1809 + med HostGuardian

### <a name="shieldedvmtemplate"></a>ShieldedVMTemplate

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 + med RSAT-skärmad-VM-tools
- Windows 10-version: 1809 + med RSAT. skärmad. VM. tools

### <a name="smbshare"></a>SmbShare

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 +
- Windows 10-version: 1809 +

### <a name="smbwitness"></a>SmbWitness

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 +
- Windows 10-version: 1809 +

### <a name="smisconfig"></a>SMISConfig

Status: internt kompatibel

Kompatibel med:

- Server version: 1903 + med WindowsStorageManagementService

### <a name="sms"></a>SMS

Status: avtestat med kompatibilitetsläge

### <a name="softwareinventorylogging"></a>SoftwareInventoryLogging

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 +

### <a name="startlayout"></a>StartLayout

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 + med Skriv bords miljö
- Windows 10-version: 1809 +

### <a name="storage"></a>Storage

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 +
- Windows 10-version: 1809 +

### <a name="storagebuscache"></a>StorageBusCache

Status: avtestat med kompatibilitetsläge

### <a name="storagemigrationservice"></a>StorageMigrationService

Status: avtestat med kompatibilitetsläge

### <a name="storageqos"></a>StorageQOS

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 + med RSAT-Clustering – PowerShell
- Windows 10-version: 1809 + med RSAT. FailoverCluster. Management. tools

### <a name="storagereplica"></a>StorageReplica

Status: avtestat med kompatibilitetsläge

### <a name="syncshare"></a>SyncShare

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 + med FS-SyncShareService

### <a name="systeminsights"></a>SystemInsights

Status: avtestat med kompatibilitetsläge

### <a name="tls"></a>TLS

Status: avtestat med kompatibilitetsläge

### <a name="troubleshootingpack"></a>TroubleshootingPack

Status: internt kompatibel

Kompatibel med:

- Windows 10-version: 1903 +

### <a name="trustedplatformmodule"></a>TrustedPlatformModule

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 +
- Windows 10-version: 1809 +

### <a name="uev"></a>UEV

Status: internt kompatibel

Kompatibel med:

- Server version:?? En framtida version av server med Skriv bords miljö?
- Windows 10-version: 1903 +

### <a name="updateservices"></a>UpdateServices

Status: fungerar inte med kompatibilitetsläge

### <a name="vpnclient"></a>VpnClient

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 +
- Windows 10-version: 1809 +

### <a name="wdac"></a>Wdac

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 +
- Windows 10-version: 1809 +

### <a name="webadministration"></a>Webadministration

Status: avtestat med kompatibilitetsläge

### <a name="whea"></a>WHEA

Status: internt kompatibel

Kompatibel med:

- Server version: 1903 +
- Windows 10-version: 1903 +

### <a name="windowsdeveloperlicense"></a>WindowsDeveloperLicense

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 + med Skriv bords miljö
- Windows 10-version: 1809 +

### <a name="windowserrorreporting"></a>WindowsErrorReporting

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 +
- Windows 10-version: 1809 +

### <a name="windowssearch"></a>WindowsSearch

Status: internt kompatibel

Kompatibel med:

- Windows 10-version: 1903 +

### <a name="windowsserverbackup"></a>WindowsServerBackup

Status: internt kompatibel

Kompatibel med:

- Server version: 19H2 med Windows-Server – säkerhets kopiering

### <a name="windowsupdate"></a>WindowsUpdate

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 +
- Windows 10-version: 1809 +

### <a name="windowsupdateprovider"></a>WindowsUpdateProvider

Status: internt kompatibel

Kompatibel med:

- Server version: 1809 +
- Windows 10-version: 1809 +
