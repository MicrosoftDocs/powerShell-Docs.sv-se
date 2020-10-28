---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguration, installation
title: 'Konfigurera en pull-klient med hjälp av konfigurations-ID: n i PowerShell 5,0 och senare'
description: 'Den här artikeln beskriver hur du konfigurerar en pull-klient med hjälp av konfigurations-ID: n i PowerShell 5,0 och senare'
ms.openlocfilehash: 601858c08ce9a893a8941823d27fef3a60882b48
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664316"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a><span data-ttu-id="d4f13-104">Konfigurera en pull-klient med hjälp av konfigurations-ID: n i PowerShell 5,0 och senare</span><span class="sxs-lookup"><span data-stu-id="d4f13-104">Set up a Pull Client using Configuration IDs in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="d4f13-105">Gäller för: Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="d4f13-105">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d4f13-106">Hämtnings servern (Windows Feature *DSC-tjänst* ) är en komponent som stöds av Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner.</span><span class="sxs-lookup"><span data-stu-id="d4f13-106">The Pull Server (Windows Feature *DSC-Service* ) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="d4f13-107">Vi rekommenderar att du börjar överföra hanterade klienter till [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inklusive funktioner utöver hämtnings servern på Windows Server) eller någon av de community-lösningar som anges [här](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="d4f13-107">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="d4f13-108">Innan du konfigurerar en pull-klient bör du konfigurera en hämtnings Server.</span><span class="sxs-lookup"><span data-stu-id="d4f13-108">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="d4f13-109">Även om den här ordningen inte krävs, hjälper den med fel sökning och hjälper dig att se till att registreringen lyckades.</span><span class="sxs-lookup"><span data-stu-id="d4f13-109">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="d4f13-110">Om du vill konfigurera en hämtnings Server kan du använda följande guider:</span><span class="sxs-lookup"><span data-stu-id="d4f13-110">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="d4f13-111">Konfigurera en DSC SMB-hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="d4f13-111">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="d4f13-112">Konfigurera en DSC HTTP-hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="d4f13-112">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="d4f13-113">Varje målnod kan konfigureras för att ladda ned konfigurationer, resurser och till och med rapportera dess status.</span><span class="sxs-lookup"><span data-stu-id="d4f13-113">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="d4f13-114">I avsnitten nedan visas hur du konfigurerar en pull-klient med en SMB-resurs eller HTTP DSC-pull-server.</span><span class="sxs-lookup"><span data-stu-id="d4f13-114">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="d4f13-115">När nodens LCM uppdateras, kommer den att kontakta den konfigurerade platsen för att ladda ned alla tilldelade konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="d4f13-115">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="d4f13-116">Om det inte finns några nödvändiga resurser på noden hämtas de automatiskt från den konfigurerade platsen.</span><span class="sxs-lookup"><span data-stu-id="d4f13-116">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="d4f13-117">Om noden har kon figurer ATS med en [rapport Server](reportServer.md), kommer den att rapportera statusen för åtgärden.</span><span class="sxs-lookup"><span data-stu-id="d4f13-117">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> [!NOTE]
> <span data-ttu-id="d4f13-118">Det här avsnittet gäller för PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="d4f13-118">This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="d4f13-119">Information om hur du konfigurerar en pull-klient i PowerShell 4,0 finns i [Konfigurera en pull-klient med konfigurations-ID i PowerShell 4,0](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="d4f13-119">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="d4f13-120">Konfigurera LCM för pull-klienten</span><span class="sxs-lookup"><span data-stu-id="d4f13-120">Configure the pull client LCM</span></span>

<span data-ttu-id="d4f13-121">Om du kör något av exemplen nedan skapas en ny mapp med namnet **PullClientConfigID** och en metaconfiguration MOF-fil placeras där.</span><span class="sxs-lookup"><span data-stu-id="d4f13-121">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="d4f13-122">I det här fallet får MOF-filen metaconfiguration namnet `localhost.meta.mof` .</span><span class="sxs-lookup"><span data-stu-id="d4f13-122">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="d4f13-123">Om du vill använda konfigurationen anropar du cmdleten **set-DscLocalConfigurationManager** med **sökvägen** inställd på platsen för MOF-filen för metaconfiguration.</span><span class="sxs-lookup"><span data-stu-id="d4f13-123">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="d4f13-124">Exempel:</span><span class="sxs-lookup"><span data-stu-id="d4f13-124">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="d4f13-125">Konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="d4f13-125">Configuration ID</span></span>

<span data-ttu-id="d4f13-126">I exemplen nedan anges egenskapen **ConfigurationID** för LCM till ett **GUID** som tidigare har skapats för detta ändamål.</span><span class="sxs-lookup"><span data-stu-id="d4f13-126">The examples below sets the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="d4f13-127">**ConfigurationID** är vad LCM använder för att hitta rätt konfiguration på hämtnings servern.</span><span class="sxs-lookup"><span data-stu-id="d4f13-127">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="d4f13-128">MOF-konfigurationsfilen på hämtnings servern måste namnges `ConfigurationID.mof` , där *ConfigurationID* är värdet för egenskapen **ConfigurationID** för målnoden LCM.</span><span class="sxs-lookup"><span data-stu-id="d4f13-128">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="d4f13-129">Mer information finns i [publicera konfigurationer till en pull-server (v4/V5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="d4f13-129">For more information see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="d4f13-130">Du kan skapa ett slumpmässigt **GUID** med hjälp av exemplet nedan eller med hjälp av cmdleten [New-GUID](/powershell/module/microsoft.powershell.utility/new-guid) .</span><span class="sxs-lookup"><span data-stu-id="d4f13-130">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="d4f13-131">Mer information om hur du använder **GUID** i din miljö finns i [Planera för GUID](secureserver.md#guids).</span><span class="sxs-lookup"><span data-stu-id="d4f13-131">For more information about using **Guids** in your environment, see [Plan for Guids](secureserver.md#guids).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="d4f13-132">Konfigurera en pull-klient för att hämta konfigurationer</span><span class="sxs-lookup"><span data-stu-id="d4f13-132">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="d4f13-133">Varje klient måste konfigureras i **pull** -läge och tilldelas URL-adressen till pull-servern där konfigurationen lagras.</span><span class="sxs-lookup"><span data-stu-id="d4f13-133">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="d4f13-134">Om du vill göra detta måste du konfigurera den lokala Configuration Manager (LCM) med nödvändig information.</span><span class="sxs-lookup"><span data-stu-id="d4f13-134">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="d4f13-135">Om du vill konfigurera LCM skapar du en särskild typ av konfiguration, dekorerat med attributet **DSCLocalConfigurationManager** .</span><span class="sxs-lookup"><span data-stu-id="d4f13-135">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="d4f13-136">Mer information om hur du konfigurerar LCM finns i [Konfigurera den lokala Configuration Manager](../managing-nodes/metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="d4f13-136">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="d4f13-137">HTTP DSC-hämtnings Server</span><span class="sxs-lookup"><span data-stu-id="d4f13-137">HTTP DSC Pull Server</span></span>

<span data-ttu-id="d4f13-138">Följande skript konfigurerar LCM att hämta konfigurationer från en server med namnet CONTOSO-PullSrv.</span><span class="sxs-lookup"><span data-stu-id="d4f13-138">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

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

<span data-ttu-id="d4f13-139">I skriptet definierar **ConfigurationRepositoryWeb** -blocket hämtnings servern.</span><span class="sxs-lookup"><span data-stu-id="d4f13-139">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="d4f13-140">**ServerURL** anger URL: en för DSC-pull</span><span class="sxs-lookup"><span data-stu-id="d4f13-140">The **ServerUrl** specifies the url of the DSC Pull</span></span>

### <a name="smb-share"></a><span data-ttu-id="d4f13-141">SMB-resurs</span><span class="sxs-lookup"><span data-stu-id="d4f13-141">SMB Share</span></span>

<span data-ttu-id="d4f13-142">Följande skript konfigurerar LCM för att hämta konfigurationer från SMB-resursen `\\SMBPullServer\Pull` .</span><span class="sxs-lookup"><span data-stu-id="d4f13-142">The following script configures the LCM to pull configurations from the SMB Share `\\SMBPullServer\Pull`.</span></span>

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

<span data-ttu-id="d4f13-143">I skriptet definierar **ConfigurationRepositoryShare** -blocket pull-servern, som i det här fallet bara är en SMB-resurs.</span><span class="sxs-lookup"><span data-stu-id="d4f13-143">In the script, the **ConfigurationRepositoryShare** block defines the pull server, which in this case, is just an SMB share.</span></span>

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="d4f13-144">Konfigurera en pull-klient för att ladda ned resurser</span><span class="sxs-lookup"><span data-stu-id="d4f13-144">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="d4f13-145">Om du bara anger **ConfigurationRepositoryWeb** -eller **ConfigurationRepositoryShare** -blocket i LCM-konfigurationen (som i föregående exempel) hämtar pull-klienten resurser från samma plats som den hämtar sina konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="d4f13-145">If you specify only the **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous examples), the pull client will pull resources from the same location it retrieves its configurations.</span></span> <span data-ttu-id="d4f13-146">Du kan också ange separata platser för resurser.</span><span class="sxs-lookup"><span data-stu-id="d4f13-146">You can also specify separate locations for resources.</span></span> <span data-ttu-id="d4f13-147">Om du vill ange en resurs plats som en separat server använder du **ResourceRepositoryWeb** -blocket.</span><span class="sxs-lookup"><span data-stu-id="d4f13-147">To specify a resource location as a separate server, use the **ResourceRepositoryWeb** block.</span></span> <span data-ttu-id="d4f13-148">Om du vill ange en resurs plats som en SMB-resurs använder du **ResourceRepositoryShare** -blocket.</span><span class="sxs-lookup"><span data-stu-id="d4f13-148">To specify a resource location as an SMB share, use the **ResourceRepositoryShare** block.</span></span>

> [!NOTE]
> <span data-ttu-id="d4f13-149">Du kan kombinera **ConfigurationRepositoryWeb** med **ResourceRepositoryShare** eller **ConfigurationRepositoryShare** med **ResourceRepositoryWeb** .</span><span class="sxs-lookup"><span data-stu-id="d4f13-149">You can combine **ConfigurationRepositoryWeb** with **ResourceRepositoryShare** or **ConfigurationRepositoryShare** with **ResourceRepositoryWeb** .</span></span> <span data-ttu-id="d4f13-150">Exempel på detta visas inte nedan.</span><span class="sxs-lookup"><span data-stu-id="d4f13-150">Examples of this are not shown below.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="d4f13-151">HTTP DSC-hämtnings Server</span><span class="sxs-lookup"><span data-stu-id="d4f13-151">HTTP DSC Pull Server</span></span>

<span data-ttu-id="d4f13-152">Följande metaconfiguration konfigurerar en pull-klient för att hämta konfigurationerna från **contoso-PullSrv** och dess resurser från **contoso-ResourceSrv** .</span><span class="sxs-lookup"><span data-stu-id="d4f13-152">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv** .</span></span>

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

### <a name="smb-share"></a><span data-ttu-id="d4f13-153">SMB-resurs</span><span class="sxs-lookup"><span data-stu-id="d4f13-153">SMB Share</span></span>

<span data-ttu-id="d4f13-154">I följande exempel visas en metaconfiguration som konfigurerar en-klient för att hämta konfigurationer från SMB `\\SMBPullServer\Configurations` -resursen och resurser från SMB-resursen `\\SMBPullServer\Resources` .</span><span class="sxs-lookup"><span data-stu-id="d4f13-154">The following example shows a metaconfiguration that sets up a client to pull configurations from the SMB share `\\SMBPullServer\Configurations`, and resources from the SMB share `\\SMBPullServer\Resources`.</span></span>

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

#### <a name="automatically-download-resources-in-push-mode"></a><span data-ttu-id="d4f13-155">Hämta resurser automatiskt i push-läge</span><span class="sxs-lookup"><span data-stu-id="d4f13-155">Automatically download Resources in Push Mode</span></span>

<span data-ttu-id="d4f13-156">Från och med PowerShell 5,0 kan pull-klienter Ladda ned moduler från en SMB-resurs, även när de har kon figurer ATS för **push** -läge.</span><span class="sxs-lookup"><span data-stu-id="d4f13-156">Beginning in PowerShell 5.0, your pull clients can download modules from an SMB share, even when they are configured for **Push** mode.</span></span> <span data-ttu-id="d4f13-157">Detta är särskilt användbart i scenarier där du inte vill konfigurera en hämtnings Server.</span><span class="sxs-lookup"><span data-stu-id="d4f13-157">This is especially useful in scenarios where you do not want to set up a Pull Server.</span></span> <span data-ttu-id="d4f13-158">**ResourceRepositoryShare** -blocket kan användas utan att ange en **ConfigurationRepositoryShare** .</span><span class="sxs-lookup"><span data-stu-id="d4f13-158">The **ResourceRepositoryShare** block can be used without specifying a **ConfigurationRepositoryShare** .</span></span> <span data-ttu-id="d4f13-159">I följande exempel visas en metaconfiguration som konfigurerar en-klient för att hämta resurser från en SMB-resurs `\\SMBPullServer\Resources` .</span><span class="sxs-lookup"><span data-stu-id="d4f13-159">The following example shows a metaconfiguration that sets up a client to pull resources from an SMB Share `\\SMBPullServer\Resources`.</span></span> <span data-ttu-id="d4f13-160">När noden överförs till **en konfiguration** hämtas alla nödvändiga resurser automatiskt från den angivna resursen.</span><span class="sxs-lookup"><span data-stu-id="d4f13-160">When the Node is **PUSHED** a configuration, it will automatically download any required resources, from the share specified.</span></span>

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

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="d4f13-161">Konfigurera en pull-klient för att rapportera status</span><span class="sxs-lookup"><span data-stu-id="d4f13-161">Set up a Pull Client to report status</span></span>

<span data-ttu-id="d4f13-162">Som standard skickar noder inte rapporter till en konfigurerad hämtnings Server.</span><span class="sxs-lookup"><span data-stu-id="d4f13-162">By default, Nodes will not send reports to a configured Pull Server.</span></span> <span data-ttu-id="d4f13-163">Du kan använda en enda hämtnings Server för konfigurationer, resurser och rapportering, men du måste skapa ett **ReportRepositoryWeb** -block för att ställa in rapportering.</span><span class="sxs-lookup"><span data-stu-id="d4f13-163">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="d4f13-164">HTTP DSC-hämtnings Server</span><span class="sxs-lookup"><span data-stu-id="d4f13-164">HTTP DSC Pull Server</span></span>

<span data-ttu-id="d4f13-165">I följande exempel visas en metaconfiguration som konfigurerar en klient för att hämta konfigurationer och resurser och skicka rapporterings data till en enda pull-server.</span><span class="sxs-lookup"><span data-stu-id="d4f13-165">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

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

<span data-ttu-id="d4f13-166">Om du vill ange en rapport Server använder du ett **ReportRepositoryWeb** -block.</span><span class="sxs-lookup"><span data-stu-id="d4f13-166">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="d4f13-167">En rapport Server kan inte vara en SMB-server.</span><span class="sxs-lookup"><span data-stu-id="d4f13-167">A report server cannot be an SMB server.</span></span> <span data-ttu-id="d4f13-168">Följande metaconfiguration konfigurerar en pull-klient för att hämta konfigurationerna från **contoso-PullSrv** och dess resurser från **contoso-ResourceSrv** , och för att skicka status rapporter till **contoso-ReportSrv** :</span><span class="sxs-lookup"><span data-stu-id="d4f13-168">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv** , and to send status reports to **CONTOSO-ReportSrv** :</span></span>

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

### <a name="smb-share"></a><span data-ttu-id="d4f13-169">SMB-resurs</span><span class="sxs-lookup"><span data-stu-id="d4f13-169">SMB Share</span></span>

<span data-ttu-id="d4f13-170">En rapport Server kan inte vara en SMB-resurs.</span><span class="sxs-lookup"><span data-stu-id="d4f13-170">A report server cannot be an SMB share.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d4f13-171">Efterföljande moment</span><span class="sxs-lookup"><span data-stu-id="d4f13-171">Next Steps</span></span>

<span data-ttu-id="d4f13-172">När pull-klienten har kon figurer ATS kan du använda följande guider för att utföra nästa steg:</span><span class="sxs-lookup"><span data-stu-id="d4f13-172">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="d4f13-173">Publicera konfigurationer till en hämtningsserver (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="d4f13-173">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="d4f13-174">Paketera och ladda upp resurser till en hämtningsserver (v4)</span><span class="sxs-lookup"><span data-stu-id="d4f13-174">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="d4f13-175">Se även</span><span class="sxs-lookup"><span data-stu-id="d4f13-175">See Also</span></span>

- [<span data-ttu-id="d4f13-176">Konfigurera en pull-klient med konfigurations namn</span><span class="sxs-lookup"><span data-stu-id="d4f13-176">Setting up a pull client with configuration names</span></span>](pullClientConfigNames.md)
