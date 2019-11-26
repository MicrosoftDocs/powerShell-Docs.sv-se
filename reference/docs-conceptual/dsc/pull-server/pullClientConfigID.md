---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguration, installation
title: 'Konfigurera en pull-klient med hjälp av konfigurations-ID: n i PowerShell 5,0 och senare'
ms.openlocfilehash: bd173a1079b916c450a0292dca7a595a9bcff985
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417228"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a><span data-ttu-id="eb2cc-103">Konfigurera en pull-klient med hjälp av konfigurations-ID: n i PowerShell 5,0 och senare</span><span class="sxs-lookup"><span data-stu-id="eb2cc-103">Set up a Pull Client using Configuration IDs in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="eb2cc-104">Gäller för: Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="eb2cc-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="eb2cc-105">Hämtnings servern (Windows Feature *DSC-tjänst*) är en komponent som stöds av Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="eb2cc-106">Vi rekommenderar att du börjar överföra hanterade klienter till [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inklusive funktioner utöver hämtnings servern på Windows Server) eller någon av de community-lösningar som anges [här](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="eb2cc-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="eb2cc-107">Innan du konfigurerar en pull-klient bör du konfigurera en hämtnings Server.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="eb2cc-108">Även om den här ordningen inte krävs, hjälper den med fel sökning och hjälper dig att se till att registreringen lyckades.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="eb2cc-109">Om du vill konfigurera en hämtnings Server kan du använda följande guider:</span><span class="sxs-lookup"><span data-stu-id="eb2cc-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="eb2cc-110">Konfigurera en DSC SMB-pull-server</span><span class="sxs-lookup"><span data-stu-id="eb2cc-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="eb2cc-111">Konfigurera en DSC HTTP-pull-server</span><span class="sxs-lookup"><span data-stu-id="eb2cc-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="eb2cc-112">Varje målnod kan konfigureras för att ladda ned konfigurationer, resurser och till och med rapportera dess status.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="eb2cc-113">I avsnitten nedan visas hur du konfigurerar en pull-klient med en SMB-resurs eller HTTP DSC-pull-server.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="eb2cc-114">När nodens LCM uppdateras, kommer den att kontakta den konfigurerade platsen för att ladda ned alla tilldelade konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="eb2cc-115">Om det inte finns några nödvändiga resurser på noden hämtas de automatiskt från den konfigurerade platsen.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="eb2cc-116">Om noden har kon figurer ATS med en [rapport Server](reportServer.md), kommer den att rapportera statusen för åtgärden.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> [!NOTE]
> <span data-ttu-id="eb2cc-117">Det här avsnittet gäller för PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-117">This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="eb2cc-118">Information om hur du konfigurerar en pull-klient i PowerShell 4,0 finns i [Konfigurera en pull-klient med konfigurations-ID i PowerShell 4,0](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="eb2cc-118">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="eb2cc-119">Konfigurera LCM för pull-klienten</span><span class="sxs-lookup"><span data-stu-id="eb2cc-119">Configure the pull client LCM</span></span>

<span data-ttu-id="eb2cc-120">Om du kör något av exemplen nedan skapas en ny mapp med namnet **PullClientConfigID** och en metaconfiguration MOF-fil placeras där.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-120">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="eb2cc-121">I det här fallet får MOF-filen metaconfiguration namnet `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="eb2cc-122">Om du vill använda konfigurationen anropar du cmdleten **set-DscLocalConfigurationManager** med **sökvägen** inställd på platsen för MOF-filen för metaconfiguration.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="eb2cc-123">Exempel:</span><span class="sxs-lookup"><span data-stu-id="eb2cc-123">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="eb2cc-124">Konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="eb2cc-124">Configuration ID</span></span>

<span data-ttu-id="eb2cc-125">I exemplen nedan anges egenskapen **ConfigurationID** för LCM till ett **GUID** som tidigare har skapats för detta ändamål.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-125">The examples below sets the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="eb2cc-126">**ConfigurationID** är vad LCM använder för att hitta rätt konfiguration på hämtnings servern.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-126">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="eb2cc-127">MOF-konfigurationsfilen på hämtnings servern måste namnges `ConfigurationID.mof`, där *ConfigurationID* är värdet för egenskapen **CONFIGURATIONID** för målnoden LCM.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-127">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="eb2cc-128">Mer information finns i [publicera konfigurationer till en pull-server (v4/V5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="eb2cc-128">For more information see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="eb2cc-129">Du kan skapa ett slumpmässigt **GUID** med hjälp av exemplet nedan eller med hjälp av cmdleten [New-GUID](/powershell/module/microsoft.powershell.utility/new-guid) .</span><span class="sxs-lookup"><span data-stu-id="eb2cc-129">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="eb2cc-130">Mer information om hur du använder **GUID** i din miljö finns i [Planera för GUID](/powershell/scripting/dsc/secureserver#guids).</span><span class="sxs-lookup"><span data-stu-id="eb2cc-130">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/scripting/dsc/secureserver#guids).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="eb2cc-131">Konfigurera en pull-klient för att hämta konfigurationer</span><span class="sxs-lookup"><span data-stu-id="eb2cc-131">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="eb2cc-132">Varje klient måste konfigureras i **pull** -läge och tilldelas URL-adressen till pull-servern där konfigurationen lagras.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-132">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="eb2cc-133">Om du vill göra detta måste du konfigurera den lokala Configuration Manager (LCM) med nödvändig information.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-133">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="eb2cc-134">Om du vill konfigurera LCM skapar du en särskild typ av konfiguration, dekorerat med attributet **DSCLocalConfigurationManager** .</span><span class="sxs-lookup"><span data-stu-id="eb2cc-134">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="eb2cc-135">Mer information om hur du konfigurerar LCM finns i [Konfigurera den lokala Configuration Manager](../managing-nodes/metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="eb2cc-135">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="eb2cc-136">HTTP DSC-hämtnings Server</span><span class="sxs-lookup"><span data-stu-id="eb2cc-136">HTTP DSC Pull Server</span></span>

<span data-ttu-id="eb2cc-137">Följande skript konfigurerar LCM att hämta konfigurationer från en server med namnet CONTOSO-PullSrv.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-137">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }
    }
}
PullClientConfigID
```

<span data-ttu-id="eb2cc-138">I skriptet definierar **ConfigurationRepositoryWeb** -blocket hämtnings servern.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-138">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="eb2cc-139">**ServerURL** anger URL: en för DSC-pull</span><span class="sxs-lookup"><span data-stu-id="eb2cc-139">The **ServerUrl** specifies the url of the DSC Pull</span></span>

### <a name="smb-share"></a><span data-ttu-id="eb2cc-140">SMB-resurs</span><span class="sxs-lookup"><span data-stu-id="eb2cc-140">SMB Share</span></span>

<span data-ttu-id="eb2cc-141">Följande skript konfigurerar LCM för att hämta konfigurationer från SMB-resursen `\\SMBPullServer\Pull`.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-141">The following script configures the LCM to pull configurations from the SMB Share `\\SMBPullServer\Pull`.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\Pull'
        }
    }
}
PullClientConfigID
```

<span data-ttu-id="eb2cc-142">I skriptet definierar **ConfigurationRepositoryShare** -blocket pull-servern, som i det här fallet bara är en SMB-resurs.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-142">In the script, the **ConfigurationRepositoryShare** block defines the pull server, which in this case, is just an SMB share.</span></span>

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="eb2cc-143">Konfigurera en pull-klient för att ladda ned resurser</span><span class="sxs-lookup"><span data-stu-id="eb2cc-143">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="eb2cc-144">Om du bara anger **ConfigurationRepositoryWeb** -eller **ConfigurationRepositoryShare** -blocket i LCM-konfigurationen (som i föregående exempel) hämtar pull-klienten resurser från samma plats som den hämtar sina konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-144">If you specify only the **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous examples), the pull client will pull resources from the same location it retrieves its configurations.</span></span> <span data-ttu-id="eb2cc-145">Du kan också ange separata platser för resurser.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-145">You can also specify separate locations for resources.</span></span> <span data-ttu-id="eb2cc-146">Om du vill ange en resurs plats som en separat server använder du **ResourceRepositoryWeb** -blocket.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-146">To specify a resource location as a separate server, use the **ResourceRepositoryWeb** block.</span></span> <span data-ttu-id="eb2cc-147">Om du vill ange en resurs plats som en SMB-resurs använder du **ResourceRepositoryShare** -blocket.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-147">To specify a resource location as an SMB share, use the **ResourceRepositoryShare** block.</span></span>

> [!NOTE]
> <span data-ttu-id="eb2cc-148">Du kan kombinera **ConfigurationRepositoryWeb** med **ResourceRepositoryShare** eller **ConfigurationRepositoryShare** med **ResourceRepositoryWeb**.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-148">You can combine **ConfigurationRepositoryWeb** with **ResourceRepositoryShare** or **ConfigurationRepositoryShare** with **ResourceRepositoryWeb**.</span></span> <span data-ttu-id="eb2cc-149">Exempel på detta visas inte nedan.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-149">Examples of this are not shown below.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="eb2cc-150">HTTP DSC-hämtnings Server</span><span class="sxs-lookup"><span data-stu-id="eb2cc-150">HTTP DSC Pull Server</span></span>

<span data-ttu-id="eb2cc-151">Följande metaconfiguration konfigurerar en pull-klient för att hämta konfigurationerna från **contoso-PullSrv** och dess resurser från **contoso-ResourceSrv**.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-151">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

### <a name="smb-share"></a><span data-ttu-id="eb2cc-152">SMB-resurs</span><span class="sxs-lookup"><span data-stu-id="eb2cc-152">SMB Share</span></span>

<span data-ttu-id="eb2cc-153">I följande exempel visas en metaconfiguration som konfigurerar en-klient för att hämta konfigurationer från SMB-resursen `\\SMBPullServer\Configurations`och resurser från SMB-resursen `\\SMBPullServer\Resources`.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-153">The following example shows a metaconfiguration that sets up a client to pull configurations from the SMB share `\\SMBPullServer\Configurations`, and resources from the SMB share `\\SMBPullServer\Resources`.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\Configurations'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

#### <a name="automatically-download-resources-in-push-mode"></a><span data-ttu-id="eb2cc-154">Hämta resurser automatiskt i push-läge</span><span class="sxs-lookup"><span data-stu-id="eb2cc-154">Automatically download Resources in Push Mode</span></span>

<span data-ttu-id="eb2cc-155">Från och med PowerShell 5,0 kan pull-klienter Ladda ned moduler från en SMB-resurs, även när de har kon figurer ATS för **push** -läge.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-155">Beginning in PowerShell 5.0, your pull clients can download modules from an SMB share, even when they are configured for **Push** mode.</span></span> <span data-ttu-id="eb2cc-156">Detta är särskilt användbart i scenarier där du inte vill konfigurera en hämtnings Server.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-156">This is especially useful in scenarios where you do not want to set up a Pull Server.</span></span> <span data-ttu-id="eb2cc-157">**ResourceRepositoryShare** -blocket kan användas utan att ange en **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-157">The **ResourceRepositoryShare** block can be used without specifying a **ConfigurationRepositoryShare**.</span></span> <span data-ttu-id="eb2cc-158">I följande exempel visas en metaconfiguration som konfigurerar en klient för att hämta resurser från en SMB-resurs `\\SMBPullServer\Resources`.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-158">The following example shows a metaconfiguration that sets up a client to pull resources from an SMB Share `\\SMBPullServer\Resources`.</span></span> <span data-ttu-id="eb2cc-159">När noden överförs till **en konfiguration** hämtas alla nödvändiga resurser automatiskt från den angivna resursen.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-159">When the Node is **PUSHED** a configuration, it will automatically download any required resources, from the share specified.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="eb2cc-160">Konfigurera en pull-klient för att rapportera status</span><span class="sxs-lookup"><span data-stu-id="eb2cc-160">Set up a Pull Client to report status</span></span>

<span data-ttu-id="eb2cc-161">Som standard skickar noder inte rapporter till en konfigurerad hämtnings Server.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-161">By default, Nodes will not send reports to a configured Pull Server.</span></span> <span data-ttu-id="eb2cc-162">Du kan använda en enda hämtnings Server för konfigurationer, resurser och rapportering, men du måste skapa ett **ReportRepositoryWeb** -block för att ställa in rapportering.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-162">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="eb2cc-163">HTTP DSC-hämtnings Server</span><span class="sxs-lookup"><span data-stu-id="eb2cc-163">HTTP DSC Pull Server</span></span>

<span data-ttu-id="eb2cc-164">I följande exempel visas en metaconfiguration som konfigurerar en klient för att hämta konfigurationer och resurser och skicka rapporterings data till en enda pull-server.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-164">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

<span data-ttu-id="eb2cc-165">Om du vill ange en rapport Server använder du ett **ReportRepositoryWeb** -block.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-165">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="eb2cc-166">En rapport Server kan inte vara en SMB-server.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-166">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="eb2cc-167">Följande metaconfiguration konfigurerar en pull-klient för att hämta konfigurationerna från **contoso-PullSrv** och dess resurser från **contoso-ResourceSrv**, och för att skicka status rapporter till **contoso-ReportSrv**:</span><span class="sxs-lookup"><span data-stu-id="eb2cc-167">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

### <a name="smb-share"></a><span data-ttu-id="eb2cc-168">SMB-resurs</span><span class="sxs-lookup"><span data-stu-id="eb2cc-168">SMB Share</span></span>

<span data-ttu-id="eb2cc-169">En rapport Server kan inte vara en SMB-resurs.</span><span class="sxs-lookup"><span data-stu-id="eb2cc-169">A report server cannot be an SMB share.</span></span>

## <a name="next-steps"></a><span data-ttu-id="eb2cc-170">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="eb2cc-170">Next Steps</span></span>

<span data-ttu-id="eb2cc-171">När pull-klienten har kon figurer ATS kan du använda följande guider för att utföra nästa steg:</span><span class="sxs-lookup"><span data-stu-id="eb2cc-171">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="eb2cc-172">Publicera konfigurationer till en pull-server (v4/V5)</span><span class="sxs-lookup"><span data-stu-id="eb2cc-172">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="eb2cc-173">Paketera och ladda upp resurser till en pull-server (v4)</span><span class="sxs-lookup"><span data-stu-id="eb2cc-173">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="eb2cc-174">Se även</span><span class="sxs-lookup"><span data-stu-id="eb2cc-174">See Also</span></span>

* [<span data-ttu-id="eb2cc-175">Konfigurera en pull-klient med konfigurations namn</span><span class="sxs-lookup"><span data-stu-id="eb2cc-175">Setting up a pull client with configuration names</span></span>](pullClientConfigNames.md)
