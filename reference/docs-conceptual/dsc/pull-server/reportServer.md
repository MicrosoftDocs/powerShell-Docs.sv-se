---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Använda en DSC-rapportserver
description: Den lokala Configuration Manager (LCM) för en nod kan konfigureras för att skicka rapporter om dess konfigurations status till en pull-server som sedan kan frågas för att hämta dessa data.
ms.openlocfilehash: 58ff1684bbe1d23fa68296aa56dd94ba6bc5b148
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92653720"
---
# <a name="using-a-dsc-report-server"></a>Använda en DSC-rapportserver

Gäller för: Windows PowerShell 5,0

> [!IMPORTANT]
> Hämtnings servern (Windows Feature *DSC-tjänst* ) är en komponent som stöds av Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner. Vi rekommenderar att du börjar överföra hanterade klienter till [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inklusive funktioner utöver hämtnings servern på Windows Server) eller någon av de community-lösningar som anges [här](pullserver.md#community-solutions-for-pull-service).
>
> [!NOTE]
> Rapport servern som beskrivs i det här avsnittet är inte tillgänglig i PowerShell 4,0.

Den lokala Configuration Manager (LCM) för en nod kan konfigureras för att skicka rapporter om dess konfigurations status till en pull-server som sedan kan frågas för att hämta dessa data. Varje gången noden kontrollerar och tillämpar en konfiguration skickas en rapport till rapport servern. Dessa rapporter lagras i en databas på servern och kan hämtas genom att anropa rapport webb tjänsten.
Varje rapport innehåller information, till exempel vilka konfigurationer som har tillämpats och om de lyckades, vilka resurser som använts, eventuella fel som har utlösts och start-och slut tider.

## <a name="configuring-a-node-to-send-reports"></a>Konfigurera en nod för att skicka rapporter

Du anger att en nod ska skicka rapporter till en server med hjälp av ett **ReportServerWeb** -block i nodens LCM-konfiguration (information om hur du konfigurerar LCM finns i [konfigurera den lokala Configuration Manager](../managing-nodes/metaConfig.md)). Servern som noden skickar rapporter till måste konfigureras som en webb hämtnings Server (du kan inte skicka rapporter till en SMB-resurs). Information om hur du konfigurerar en hämtnings Server finns i [Konfigurera en DSC-webb hämtnings Server](pullServer.md). Rapport servern kan vara samma tjänst som noden hämtar konfigurationer och hämtar resurser, eller så kan den vara en annan tjänst.

I **ReportServerWeb** -blocket anger du URL: en för pull-tjänsten och en registrerings nyckel som är känd för servern.

Följande konfiguration konfigurerar en nod för att hämta konfigurationer från en tjänst och skicka rapporter till en tjänst på en annan server.

```powershell
[DSCLocalConfigurationManager()]
configuration ReportClientConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode          = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded   = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = 'https://CONTOSO-PULL:8080/PSDSCPullServer.svc'
            RegistrationKey    = 'bbb9778f-43f2-47de-b61e-a0daff474c6d'
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL               = 'http://CONTOSO-REPORT:8080/PSDSCPullServer.svc'
            RegistrationKey         = 'ba39daaa-96c5-4f2f-9149-f95c46460faa'
            AllowUnsecureConnection = $true
        }
    }
}

ReportClientConfig
```

Följande konfiguration konfigurerar en nod att använda en enskild server för konfigurationer, resurser och rapportering.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }



        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfig
```

> [!NOTE]
> Du kan namnge den webb tjänst du vill när du konfigurerar en hämtnings Server, men egenskapen **ServerURL** måste matcha tjänst namnet.

## <a name="getting-report-data"></a>Hämtar rapport data

Rapporter som skickas till pull-servern registreras i en databas på servern. Rapporterna är tillgängliga via anrop till webb tjänsten. Om du vill hämta rapporter för en speciell nod skickar du en HTTP-begäran till rapport webb tjänsten i följande format:

`http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentId='MyNodeAgentId')/Reports`

Där `MyNodeAgentId` är AgentId för den nod som du vill hämta rapporter för. Du kan hämta AgentID för en nod genom att anropa [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) på den noden.

Rapporterna returneras som en matris med JSON-objekt.

Följande skript returnerar rapporterna för noden där den körs:

```powershell
function GetReport
{
    param
    (
        $AgentId = "$((glcm).AgentId)",
        $serviceURL = "http://CONTOSO-REPORT:8080/PSDSCPullServer.svc"
    )

    $requestUri = "$serviceURL/Nodes(AgentId= '$AgentId')/Reports"
    $request = Invoke-WebRequest -Uri $requestUri  -ContentType "application/json;odata=minimalmetadata;streaming=true;charset=utf-8" `
               -UseBasicParsing -Headers @{Accept = "application/json";ProtocolVersion = "2.0"} `
               -ErrorAction SilentlyContinue -ErrorVariable ev
    $object = ConvertFrom-Json $request.content
    return $object.value
}
```

## <a name="viewing-report-data"></a>Visa rapport data

Om du ställer in en variabel till resultatet av **GetReport** -funktionen kan du Visa enskilda fält i ett element i matrisen som returneras:

```powershell
$reports = GetReport
$reports[1]
```

```output
JobId                : 019dfbe5-f99f-11e5-80c6-001dd8b8065c
OperationType        : Consistency
RefreshMode          : Pull
Status               : Success
ReportFormatVersion  : 2.0
ConfigurationVersion : 2.0.0
StartTime            : 04/03/2016 06:21:43
EndTime              : 04/03/2016 06:22:04
RebootRequested      : False
Errors               : {}
StatusData           : {{"StartDate":"2016-04-03T06:21:43.7220000-07:00","IPV6Addresses":["2001:4898:d8:f2f2:852b:b255:b071:283b","fe80::852b:b255:b071
                       :283b%12","::2000:0:0:0","::1","::2000:0:0:0"],"DurationInSeconds":"21","JobID":"{019DFBE5-F99F-11E5-80C6-001DD8B8065C}","Curren
                       tChecksum":"A7797571CB9C3AF4D74C39A0FDA11DAF33273349E1182385528FFC1E47151F7F","MetaData":"Author: configAuthor; Name:
                       Sample_ArchiveFirewall; Version: 2.0.0; GenerationDate: 04/01/2016 15:23:30; GenerationHost: CONTOSO-PullSrv;","RebootRequested":"False
                       ","Status":"Success","IPV4Addresses":["10.240.179.151","127.0.0.1"],"LCMVersion":"2.0","ResourcesNotInDesiredState":[{"SourceInf
                       o":"C:\\ReportTest\\Sample_xFirewall_AddFirewallRule.ps1::23::9::xFirewall","ModuleName":"xNetworking","DurationInSeconds":"8.785",
                       "InstanceName":"Firewall","StartDate":"2016-04-03T06:21:56.4650000-07:00","ResourceName":"xFirewall","ModuleVersion":"2.7.0.0","
                       RebootRequested":"False","ResourceId":"[xFirewall]Firewall","ConfigurationName":"Sample_ArchiveFirewall","InDesiredState":"False
                       "}],"NumberOfResources":"2","Type":"Consistency","HostName":"CONTOSO-PULLCLI","ResourcesInDesiredState":[{"SourceInfo":"C:\\ReportTest\\Sample_xFirewall_AddFirewallRule.ps1::16::9::Archive","ModuleName":"PSDesiredStateConfiguration","DurationInSeconds":"1.848",
                       "InstanceName":"ArchiveExample","StartDate":"2016-04-03T06:21:56.4650000-07:00","ResourceName":"Archive","ModuleVersion":"1.1","
                       RebootRequested":"False","ResourceId":"[Archive]ArchiveExample","ConfigurationName":"Sample_ArchiveFirewall","InDesiredState":"T
                       rue"}],"MACAddresses":["00-1D-D8-B8-06-5C","00-00-00-00-00-00-00-E0"],"MetaConfiguration":{"AgentId":"52DA826D-00DE-4166-8ACB-73F2B46A7E00",
                       "ConfigurationDownloadManagers":[{"SourceInfo":"C:\\ReportTest\\LCMConfig.ps1::14::9::ConfigurationRepositoryWeb","A
                       llowUnsecureConnection":"True","ServerURL":"http://CONTOSO-PullSrv:8080/PSDSCPullServer.svc","RegistrationKey":"","ResourceId":"[Config
                       urationRepositoryWeb]CONTOSO-PullSrv","ConfigurationNames":["ClientConfig"]}],"ActionAfterReboot":"ContinueConfiguration","LCMCo
                       mpatibleVersions":["1.0","2.0"],"LCMState":"Idle","ResourceModuleManagers":[],"ReportManagers":[{"AllowUnsecureConnection":"True
                       ","RegistrationKey":"","ServerURL":"http://CONTOSO-PullSrv:8080/PSDSCPullServer.svc","ResourceId":"[ReportServerWeb]CONTOSO-PullSrv","S
                       ourceInfo":"C:\\ReportTest\\LCMConfig.ps1::24::9::ReportServerWeb"}],"StatusRetentionTimeInDays":"10","LCMVersion":"2.0","Config
                       urationMode":"ApplyAndMonitor","RefreshFrequencyMins":"30","RebootNodeIfNeeded":"True","RefreshMode":"Pull","DebugMode":["NONE"]
                       ,"LCMStateDetail":"","AllowModuleOverwrite":"False","ConfigurationModeFrequencyMins":"15"},"Locale":"en-US","Mode":"Pull"}}
AdditionalData       : {}
```

Som standard sorteras rapporterna efter **JobID** . För att få den senaste rapporten kan du sortera rapporterna genom att fallande **StartTime** -egenskapen och hämta det första elementet i matrisen:

```powershell
$reportsByStartTime = $reports | Sort-Object {$_."StartTime" -as [DateTime] } -Descending
$reportMostRecent = $reportsByStartTime[0]
```

Observera att egenskapen **StatusData** är ett objekt med ett antal egenskaper. Det är där mycket av rapporterings data är. Nu ska vi titta på de enskilda fälten för egenskapen **StatusData** för den senaste rapporten:

```powershell
$statusData = $reportMostRecent.StatusData | ConvertFrom-Json
$statusData
```

```output
StartDate                  : 2016-04-04T11:21:41.2990000-07:00
IPV6Addresses              : {2001:4898:d8:f2f2:852b:b255:b071:283b, fe80::852b:b255:b071:283b%12, ::2000:0:0:0, ::1...}
DurationInSeconds          : 25
JobID                      : {135D230E-FA92-11E5-80C6-001DD8B8065C}
CurrentChecksum            : A7797571CB9C3AF4D74C39A0FDA11DAF33273349E1182385528FFC1E47151F7F
MetaData                   : Author: configAuthor; Name: Sample_ArchiveFirewall; Version: 2.0.0; GenerationDate: 04/01/2016 15:23:30; GenerationHost:
                             CONTOSO-PullSrv;
RebootRequested            : False
Status                     : Success
IPV4Addresses              : {10.240.179.151, 127.0.0.1}
LCMVersion                 : 2.0
ResourcesNotInDesiredState : {@{SourceInfo=C:\ReportTest\Sample_xFirewall_AddFirewallRule.ps1::23::9::xFirewall; ModuleName=xNetworking;
                             DurationInSeconds=10.725; InstanceName=Firewall; StartDate=2016-04-04T11:21:55.7200000-07:00; ResourceName=xFirewall;
                             ModuleVersion=2.7.0.0; RebootRequested=False; ResourceId=[xFirewall]Firewall; ConfigurationName=Sample_ArchiveFirewall;
                             InDesiredState=False}}
NumberOfResources          : 2
Type                       : Consistency
HostName                   : CONTOSO-PULLCLI
ResourcesInDesiredState    : {@{SourceInfo=C:\ReportTest\Sample_xFirewall_AddFirewallRule.ps1::16::9::Archive; ModuleName=PSDesiredStateConfiguration;
                             DurationInSeconds=2.672; InstanceName=ArchiveExample; StartDate=2016-04-04T11:21:55.7200000-07:00; ResourceName=Archive;
                             ModuleVersion=1.1; RebootRequested=False; ResourceId=[Archive]ArchiveExample; ConfigurationName=Sample_ArchiveFirewall;
                             InDesiredState=True}}
MACAddresses               : {00-1D-D8-B8-06-5C, 00-00-00-00-00-00-00-E0}
MetaConfiguration          : @{AgentId=52DA826D-00DE-4166-8ACB-73F2B46A7E00; ConfigurationDownloadManagers=System.Object[];
                             ActionAfterReboot=ContinueConfiguration; LCMCompatibleVersions=System.Object[]; LCMState=Idle;
                             ResourceModuleManagers=System.Object[]; ReportManagers=System.Object[]; StatusRetentionTimeInDays=10; LCMVersion=2.0;
                             ConfigurationMode=ApplyAndMonitor; RefreshFrequencyMins=30; RebootNodeIfNeeded=True; RefreshMode=Pull;
                             DebugMode=System.Object[]; LCMStateDetail=; AllowModuleOverwrite=False; ConfigurationModeFrequencyMins=15}
Locale                     : en-US
Mode                       : Pull
```

Bland annat visar detta att den senaste konfigurationen som kallas två resurser och att en av dem var i önskat tillstånd, och en av dem var inte. Du kan få en mer lättläst utdata av bara egenskapen **ResourcesNotInDesiredState** :

```powershell
$statusData.ResourcesInDesiredState
```

```output
SourceInfo        : C:\ReportTest\Sample_xFirewall_AddFirewallRule.ps1::16::9::Archive
ModuleName        : PSDesiredStateConfiguration
DurationInSeconds : 2.672
InstanceName      : ArchiveExample
StartDate         : 2016-04-04T11:21:55.7200000-07:00
ResourceName      : Archive
ModuleVersion     : 1.1
RebootRequested   : False
ResourceId        : [Archive]ArchiveExample
ConfigurationName : Sample_ArchiveFirewall
InDesiredState    : True
```

Observera att de här exemplen är avsedda att ge dig en uppfattning om vad du kan göra med rapport data. En introduktion till hur du arbetar med JSON i PowerShell finns i [spela med JSON och PowerShell](https://devblogs.microsoft.com/scripting/playing-with-json-and-powershell/).

## <a name="see-also"></a>Se även

[Konfigurera den lokala Configuration Manager](../managing-nodes/metaConfig.md)

[Konfigurera en DSC-webb hämtnings Server](pullServer.md)

[Konfigurera en pullklient med konfigurationsnamn](pullClientConfigNames.md)
