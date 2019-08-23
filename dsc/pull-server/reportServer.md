---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Använda en DSC-rapportserver
ms.openlocfilehash: 1ccd4f96b782b41b7d7c953735cb41b3ba3d2bce
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986547"
---
# <a name="using-a-dsc-report-server"></a><span data-ttu-id="15731-103">Använda en DSC-rapportserver</span><span class="sxs-lookup"><span data-stu-id="15731-103">Using a DSC report server</span></span>

<span data-ttu-id="15731-104">Gäller för: Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="15731-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="15731-105">Hämtnings servern (Windows Feature *DSC-tjänst*) är en komponent som stöds av Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner.</span><span class="sxs-lookup"><span data-stu-id="15731-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="15731-106">Vi rekommenderar att du börjar överföra hanterade klienter till [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inklusive funktioner utöver hämtnings servern på Windows Server) eller någon av de community-lösningar som anges [här](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="15731-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>
>
> [!NOTE]
> <span data-ttu-id="15731-107">Rapport servern som beskrivs i det här avsnittet är inte tillgänglig i PowerShell 4,0.</span><span class="sxs-lookup"><span data-stu-id="15731-107">The report server described in this topic is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="15731-108">Den lokala Configuration Manager (LCM) för en nod kan konfigureras för att skicka rapporter om dess konfigurations status till en pull-server, som sedan kan frågas för att hämta dessa data.</span><span class="sxs-lookup"><span data-stu-id="15731-108">The Local Configuration Manager (LCM) of a node can be configured to send reports about its configuration status to a pull server, which can then be queried to retrieve that data.</span></span> <span data-ttu-id="15731-109">Varje gången noden kontrollerar och tillämpar en konfiguration skickas en rapport till rapport servern.</span><span class="sxs-lookup"><span data-stu-id="15731-109">Each time the node checks and applies a configuration, it sends a report to the report server.</span></span> <span data-ttu-id="15731-110">Dessa rapporter lagras i en databas på servern och kan hämtas genom att anropa rapport webb tjänsten.</span><span class="sxs-lookup"><span data-stu-id="15731-110">These reports are stored in a database on the server, and can be retrieved by calling the reporting web service.</span></span> <span data-ttu-id="15731-111">Varje rapport innehåller information, till exempel vilka konfigurationer som har tillämpats och om de lyckades, vilka resurser som använts, eventuella fel som har utlösts och start-och slut tider.</span><span class="sxs-lookup"><span data-stu-id="15731-111">Each report contains information such as what configurations were applied and whether they succeeded, the resources used, any errors that were thrown, and start and finish times.</span></span>

## <a name="configuring-a-node-to-send-reports"></a><span data-ttu-id="15731-112">Konfigurera en nod för att skicka rapporter</span><span class="sxs-lookup"><span data-stu-id="15731-112">Configuring a node to send reports</span></span>

<span data-ttu-id="15731-113">Du anger att en nod ska skicka rapporter till en server med hjälp av ett **ReportServerWeb** -block i nodens LCM-konfiguration (information om hur du konfigurerar LCM finns i [konfigurera den lokala Configuration Manager](../managing-nodes/metaConfig.md)).</span><span class="sxs-lookup"><span data-stu-id="15731-113">You tell a node to send reports to a server by using a **ReportServerWeb** block in the node's LCM configuration (for information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md)).</span></span> <span data-ttu-id="15731-114">Servern som noden skickar rapporter till måste konfigureras som en webb hämtnings Server (du kan inte skicka rapporter till en SMB-resurs).</span><span class="sxs-lookup"><span data-stu-id="15731-114">The server to which the node sends reports must be set up as a web pull server (you cannot send reports to an SMB share).</span></span> <span data-ttu-id="15731-115">Information om hur du konfigurerar en hämtnings Server finns i [Konfigurera en DSC-webb hämtnings Server](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="15731-115">For information about setting up a pull server, see [Setting up a DSC web pull server](pullServer.md).</span></span> <span data-ttu-id="15731-116">Rapport servern kan vara samma tjänst som noden hämtar konfigurationer och hämtar resurser, eller så kan den vara en annan tjänst.</span><span class="sxs-lookup"><span data-stu-id="15731-116">The report server can be the same service from which the node pulls configurations and gets resources, or it can be a different service.</span></span>

<span data-ttu-id="15731-117">I **ReportServerWeb** -blocket anger du URL: en för pull-tjänsten och en registrerings nyckel som är känd för servern.</span><span class="sxs-lookup"><span data-stu-id="15731-117">In the **ReportServerWeb** block, you specify the URL of the pull service and a registration key that is known to the server.</span></span>

<span data-ttu-id="15731-118">Följande konfiguration konfigurerar en nod för att hämta konfigurationer från en tjänst och skicka rapporter till en tjänst på en annan server.</span><span class="sxs-lookup"><span data-stu-id="15731-118">The following configuration configures a node to pull configurations from one service, and send reports to a service on a different server.</span></span>

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

<span data-ttu-id="15731-119">Följande konfiguration konfigurerar en nod att använda en enskild server för konfigurationer, resurser och rapportering.</span><span class="sxs-lookup"><span data-stu-id="15731-119">The following configuration configures a node to use a single server for configurations, resources, and reporting.</span></span>

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
> <span data-ttu-id="15731-120">Du kan namnge den webb tjänst du vill när du konfigurerar en hämtnings Server, men egenskapen **ServerURL** måste matcha tjänst namnet.</span><span class="sxs-lookup"><span data-stu-id="15731-120">You can name the web service whatever you want when you set up a pull server, but the **ServerURL** property must match the service name.</span></span>

## <a name="getting-report-data"></a><span data-ttu-id="15731-121">Hämtar rapport data</span><span class="sxs-lookup"><span data-stu-id="15731-121">Getting report data</span></span>

<span data-ttu-id="15731-122">Rapporter som skickas till pull-servern registreras i en databas på servern.</span><span class="sxs-lookup"><span data-stu-id="15731-122">Reports sent to the pull server are entered into a database on the server.</span></span> <span data-ttu-id="15731-123">Rapporterna är tillgängliga via anrop till webb tjänsten.</span><span class="sxs-lookup"><span data-stu-id="15731-123">The reports are available through calls to the web service.</span></span> <span data-ttu-id="15731-124">Om du vill hämta rapporter för en speciell nod skickar du en HTTP-begäran till rapport webb tjänsten i följande format:`http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentId='MyNodeAgentId')/Reports`</span><span class="sxs-lookup"><span data-stu-id="15731-124">To retrieve reports for a specific node, send an HTTP request to the report web service in the following form: `http://CONTOSO-REPORT:8080/PSDSCReportServer.svc/Nodes(AgentId='MyNodeAgentId')/Reports`</span></span>
<span data-ttu-id="15731-125">där `MyNodeAgentId` är AgentId för den nod som du vill hämta rapporter för.</span><span class="sxs-lookup"><span data-stu-id="15731-125">where `MyNodeAgentId` is the AgentId of the node for which you want to get reports.</span></span> <span data-ttu-id="15731-126">Du kan hämta AgentID för en nod genom att anropa [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) på den noden.</span><span class="sxs-lookup"><span data-stu-id="15731-126">You can get the AgentID for a node by calling [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) on that node.</span></span>

<span data-ttu-id="15731-127">Rapporterna returneras som en matris med JSON-objekt.</span><span class="sxs-lookup"><span data-stu-id="15731-127">The reports are returned as an array of JSON objects.</span></span>

<span data-ttu-id="15731-128">Följande skript returnerar rapporterna för noden där den körs:</span><span class="sxs-lookup"><span data-stu-id="15731-128">The following script returns the reports for the node on which it is run:</span></span>

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

## <a name="viewing-report-data"></a><span data-ttu-id="15731-129">Visa rapport data</span><span class="sxs-lookup"><span data-stu-id="15731-129">Viewing report data</span></span>

<span data-ttu-id="15731-130">Om du ställer in en variabel till resultatet av **GetReport** -funktionen kan du Visa enskilda fält i ett element i matrisen som returneras:</span><span class="sxs-lookup"><span data-stu-id="15731-130">If you set a variable to the result of the **GetReport** function, you can view the individual fields in an element of the array that is returned:</span></span>

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

<span data-ttu-id="15731-131">Som standard sorteras rapporterna efter **JobID**.</span><span class="sxs-lookup"><span data-stu-id="15731-131">By default, the reports are sorted by **JobID**.</span></span> <span data-ttu-id="15731-132">För att få den senaste rapporten kan du sortera rapporterna genom att fallande StartTime -egenskapen och hämta det första elementet i matrisen:</span><span class="sxs-lookup"><span data-stu-id="15731-132">To get the most recent report, you can sort the reports by descending **StartTime** property, and then get the first element of the array:</span></span>

```powershell
$reportsByStartTime = $reports | Sort-Object {$_."StartTime" -as [DateTime] } -Descending
$reportMostRecent = $reportsByStartTime[0]
```

<span data-ttu-id="15731-133">Observera att egenskapen **StatusData** är ett objekt med ett antal egenskaper.</span><span class="sxs-lookup"><span data-stu-id="15731-133">Notice that the **StatusData** property is an object with a number of properties.</span></span> <span data-ttu-id="15731-134">Det är där mycket av rapporterings data är.</span><span class="sxs-lookup"><span data-stu-id="15731-134">This is where much of the reporting data is.</span></span> <span data-ttu-id="15731-135">Nu ska vi titta på de enskilda fälten för egenskapen **StatusData** för den senaste rapporten:</span><span class="sxs-lookup"><span data-stu-id="15731-135">Let's look at the individual fields of the **StatusData** property for the most recent report:</span></span>

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

<span data-ttu-id="15731-136">Bland annat visar detta att den senaste konfigurationen som kallas två resurser och att en av dem var i önskat tillstånd, och en av dem var inte.</span><span class="sxs-lookup"><span data-stu-id="15731-136">Among other things, this shows that the most recent configuration called two resources, and that one of them was in the desired state, and one of them was not.</span></span> <span data-ttu-id="15731-137">Du kan få en mer lättläst utdata av bara egenskapen **ResourcesNotInDesiredState** :</span><span class="sxs-lookup"><span data-stu-id="15731-137">You can get a more readable output of just the **ResourcesNotInDesiredState** property:</span></span>

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

<span data-ttu-id="15731-138">Observera att de här exemplen är avsedda att ge dig en uppfattning om vad du kan göra med rapport data.</span><span class="sxs-lookup"><span data-stu-id="15731-138">Note that these examples are meant to give you an idea of what you can do with report data.</span></span> <span data-ttu-id="15731-139">En introduktion till hur du arbetar med JSON i PowerShell finns i [spela med JSON och PowerShell](https://blogs.technet.microsoft.com/heyscriptingguy/2015/10/08/playing-with-json-and-powershell/).</span><span class="sxs-lookup"><span data-stu-id="15731-139">For an introduction on working with JSON in PowerShell, see [Playing with JSON and PowerShell](https://blogs.technet.microsoft.com/heyscriptingguy/2015/10/08/playing-with-json-and-powershell/).</span></span>

## <a name="see-also"></a><span data-ttu-id="15731-140">Se även</span><span class="sxs-lookup"><span data-stu-id="15731-140">See Also</span></span>

[<span data-ttu-id="15731-141">Konfigurera den lokala Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="15731-141">Configuring the Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)

[<span data-ttu-id="15731-142">Konfigurera en DSC-webb hämtnings Server</span><span class="sxs-lookup"><span data-stu-id="15731-142">Setting up a DSC web pull server</span></span>](pullServer.md)

[<span data-ttu-id="15731-143">Konfigurera en pullklient med konfigurationsnamn</span><span class="sxs-lookup"><span data-stu-id="15731-143">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
