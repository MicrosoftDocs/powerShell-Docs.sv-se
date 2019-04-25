---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguration, installation
title: Konfigurera en Pull-klient som använder konfigurations-ID i PowerShell 5.0 och senare
ms.openlocfilehash: 14db98d240bc87aca3ee985db08c14b7c65d8bb8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079497"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a><span data-ttu-id="cddba-103">Konfigurera en Pull-klient som använder konfigurations-ID i PowerShell 5.0 och senare</span><span class="sxs-lookup"><span data-stu-id="cddba-103">Set up a Pull Client using Configuration IDs in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="cddba-104">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="cddba-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cddba-105">Pull-servern (Windows-funktionen *DSC-tjänst*) är en stöds komponent i Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner.</span><span class="sxs-lookup"><span data-stu-id="cddba-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="cddba-106">Rekommenderar vi att du påbörjar övergången hanterade klienter [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inklusive funktioner utöver Pull-servern på Windows Server) eller en av community-lösningar visas [här](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="cddba-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="cddba-107">Innan du konfigurerar en pullklient, bör du ställa in en pull-server.</span><span class="sxs-lookup"><span data-stu-id="cddba-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="cddba-108">Även om den här ordningen inte är obligatoriskt, hjälper till med felsökning och hjälper dig att säkerställa att registreringen har lyckats.</span><span class="sxs-lookup"><span data-stu-id="cddba-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="cddba-109">Om du vill konfigurera en pull-server kan du använda följande guider:</span><span class="sxs-lookup"><span data-stu-id="cddba-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="cddba-110">Konfigurera en DSC SMB-Hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="cddba-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="cddba-111">Konfigurera en DSC HTTP-Hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="cddba-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="cddba-112">Varje målnoden kan konfigureras för att hämta konfigurationer, resurser, och även rapportera statusen.</span><span class="sxs-lookup"><span data-stu-id="cddba-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="cddba-113">I avsnitten nedan visar hur du konfigurerar en hämtningsklient med en SMB-resursen eller HTTP DSC-Hämtningsservern.</span><span class="sxs-lookup"><span data-stu-id="cddba-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="cddba-114">När nodens LCM uppdaterar kommer det att kontakta konfigurerade platsen för att hämta alla tilldelade konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="cddba-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="cddba-115">Om alla nödvändiga resurser inte finns på noden, kommer den automatiskt hämta dem från den konfigurerade platsen.</span><span class="sxs-lookup"><span data-stu-id="cddba-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="cddba-116">Om noden är konfigurerad med en [Report Server](reportServer.md), kommer den sedan att rapportera status för åtgärden.</span><span class="sxs-lookup"><span data-stu-id="cddba-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> [!NOTE]
> <span data-ttu-id="cddba-117">Det här avsnittet gäller för PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="cddba-117">This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="cddba-118">Information om hur du konfigurerar en pullklient i PowerShell 4.0 finns i [konfigurera en hämtningsklient med konfigurations-ID i PowerShell 4.0](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="cddba-118">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="cddba-119">Konfigurera en pullklient LCM</span><span class="sxs-lookup"><span data-stu-id="cddba-119">Configure the pull client LCM</span></span>

<span data-ttu-id="cddba-120">Kör något av exemplen nedan skapar en ny utdata-mapp med namnet **PullClientConfigID** och det placerar en metaconfiguration MOF-fil.</span><span class="sxs-lookup"><span data-stu-id="cddba-120">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="cddba-121">I det här fallet metaconfiguration MOF-filen namnet `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="cddba-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="cddba-122">Om du vill tillämpa konfigurationen av genom att anropa den **Set-DscLocalConfigurationManager** cmdlet, med den **sökväg** inställd på platsen för metaconfiguration MOF-filen.</span><span class="sxs-lookup"><span data-stu-id="cddba-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="cddba-123">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="cddba-123">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="cddba-124">Konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="cddba-124">Configuration ID</span></span>

<span data-ttu-id="cddba-125">Exemplen nedan anger den **ConfigurationID** egenskapen för MGM om du vill en **Guid** som tidigare hade skapats för detta ändamål.</span><span class="sxs-lookup"><span data-stu-id="cddba-125">The examples below sets the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="cddba-126">Den **ConfigurationID** är vad LCM används för att hitta lämplig konfiguration på hämtningsservern.</span><span class="sxs-lookup"><span data-stu-id="cddba-126">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="cddba-127">MOF-konfigurationsfilen på hämtningsservern måste ha namnet `ConfigurationID.mof`, där *ConfigurationID* är värdet för den **ConfigurationID** egenskapen för den målnoden MGM.</span><span class="sxs-lookup"><span data-stu-id="cddba-127">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="cddba-128">Mer information finns i [publicera konfigurationer för att en Pull-servern (v4/v5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="cddba-128">For more information see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="cddba-129">Du kan skapa ett slumpmässigt **Guid** i exemplet nedan eller genom att använda den [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cddba-129">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="cddba-130">Mer information om hur du använder **GUID** i din miljö, se [planera för GUID](/powershell/dsc/secureserver#guids).</span><span class="sxs-lookup"><span data-stu-id="cddba-130">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/dsc/secureserver#guids).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="cddba-131">Konfigurera en Pull-klient för att ladda ned konfigurationer</span><span class="sxs-lookup"><span data-stu-id="cddba-131">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="cddba-132">Varje klient måste konfigureras i **Pull** läge och angivna pull-serveradress där dess konfiguration lagras.</span><span class="sxs-lookup"><span data-stu-id="cddba-132">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="cddba-133">Då har du konfigurerar den lokala Configuration Manager (LCM) med informationen som krävs.</span><span class="sxs-lookup"><span data-stu-id="cddba-133">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="cddba-134">Om du vill konfigurera LCM måste du skapa en särskild typ av konfiguration, dekorerad med den **DSCLocalConfigurationManager** attribut.</span><span class="sxs-lookup"><span data-stu-id="cddba-134">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="cddba-135">Läs mer om hur du konfigurerar LCM [konfigurerar den lokala Konfigurationshanteraren](../managing-nodes/metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="cddba-135">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="cddba-136">HTTP DSC Pull Server</span><span class="sxs-lookup"><span data-stu-id="cddba-136">HTTP DSC Pull Server</span></span>

<span data-ttu-id="cddba-137">Följande skript konfigurerar LCM pull konfigurationer från en server med namnet ”CONTOSO-PullSrv”.</span><span class="sxs-lookup"><span data-stu-id="cddba-137">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

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

<span data-ttu-id="cddba-138">I skriptet den **ConfigurationRepositoryWeb** block definierar hämtningsservern.</span><span class="sxs-lookup"><span data-stu-id="cddba-138">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="cddba-139">Den **ServerUrl** anger URL: en för DSC-Pull</span><span class="sxs-lookup"><span data-stu-id="cddba-139">The **ServerUrl** specifies the url of the DSC Pull</span></span>

### <a name="smb-share"></a><span data-ttu-id="cddba-140">SMB Share</span><span class="sxs-lookup"><span data-stu-id="cddba-140">SMB Share</span></span>

<span data-ttu-id="cddba-141">Följande skript konfigurerar LCM pull konfigurationer från SMB-resurs `\\SMBPullServer\Pull`.</span><span class="sxs-lookup"><span data-stu-id="cddba-141">The following script configures the LCM to pull configurations from the SMB Share `\\SMBPullServer\Pull`.</span></span>

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

<span data-ttu-id="cddba-142">I skriptet den **ConfigurationRepositoryShare** block definierar pull-servern, som i det här fallet är bara en SMB-resurs.</span><span class="sxs-lookup"><span data-stu-id="cddba-142">In the script, the **ConfigurationRepositoryShare** block defines the pull server, which in this case, is just an SMB share.</span></span>

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="cddba-143">Konfigurera en Pull-klient för att hämta resurser</span><span class="sxs-lookup"><span data-stu-id="cddba-143">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="cddba-144">Om du anger bara den **ConfigurationRepositoryWeb** eller **ConfigurationRepositoryShare** blockera i din LCM-konfiguration (som i föregående exempel), pull-klienten hämtar resurser från samma plats som den hämtar dess konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="cddba-144">If you specify only the **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous examples), the pull client will pull resources from the same location it retrieves its configurations.</span></span> <span data-ttu-id="cddba-145">Du kan också ange olika platser för resurser.</span><span class="sxs-lookup"><span data-stu-id="cddba-145">You can also specify separate locations for resources.</span></span> <span data-ttu-id="cddba-146">Om du vill ange en plats för resurser som en separat server, använder den **ResourceRepositoryWeb** block.</span><span class="sxs-lookup"><span data-stu-id="cddba-146">To specify a resource location as a separate server, use the **ResourceRepositoryWeb** block.</span></span> <span data-ttu-id="cddba-147">Om du vill ange en plats för resurser som en SMB-filresurs, använder den **ResourceRepositoryShare** block.</span><span class="sxs-lookup"><span data-stu-id="cddba-147">To specify a resource location as an SMB share, use the **ResourceRepositoryShare** block.</span></span>

> [!NOTE]
> <span data-ttu-id="cddba-148">Du kan kombinera **ConfigurationRepositoryWeb** med **ResourceRepositoryShare** eller **ConfigurationRepositoryShare** med **ResourceRepositoryWeb** .</span><span class="sxs-lookup"><span data-stu-id="cddba-148">You can combine **ConfigurationRepositoryWeb** with **ResourceRepositoryShare** or **ConfigurationRepositoryShare** with **ResourceRepositoryWeb**.</span></span> <span data-ttu-id="cddba-149">Exempel på detta visas inte nedan.</span><span class="sxs-lookup"><span data-stu-id="cddba-149">Examples of this are not shown below.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="cddba-150">HTTP DSC Pull Server</span><span class="sxs-lookup"><span data-stu-id="cddba-150">HTTP DSC Pull Server</span></span>

<span data-ttu-id="cddba-151">Följande metaconfiguration konfigurerar en pullklient för att få dess konfigurationerna från **CONTOSO PullSrv** och dess resurser från **CONTOSO ResourceSrv**.</span><span class="sxs-lookup"><span data-stu-id="cddba-151">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**.</span></span>

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

### <a name="smb-share"></a><span data-ttu-id="cddba-152">SMB Share</span><span class="sxs-lookup"><span data-stu-id="cddba-152">SMB Share</span></span>

<span data-ttu-id="cddba-153">I följande exempel visas en metaconfiguration som ställer in en klient ska pull konfigurationer från SMB-resurs `\\SMBPullServer\Configurations`, och resurser från SMB-resurs `\\SMBPullServer\Resources`.</span><span class="sxs-lookup"><span data-stu-id="cddba-153">The following example shows a metaconfiguration that sets up a client to pull configurations from the SMB share `\\SMBPullServer\Configurations`, and resources from the SMB share `\\SMBPullServer\Resources`.</span></span>

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

#### <a name="automatically-download-resources-in-push-mode"></a><span data-ttu-id="cddba-154">Hämta automatiskt resurser i Push-läge</span><span class="sxs-lookup"><span data-stu-id="cddba-154">Automatically download Resources in Push Mode</span></span>

<span data-ttu-id="cddba-155">Från och med PowerShell 5.0, pull-klienter kan ladda ned moduler från en SMB-resurs, även när de är konfigurerade för **Push** läge.</span><span class="sxs-lookup"><span data-stu-id="cddba-155">Beginning in PowerShell 5.0, your pull clients can download modules from an SMB share, even when they are configured for **Push** mode.</span></span> <span data-ttu-id="cddba-156">Detta är särskilt användbart i scenarier där du inte vill konfigurera en Pull-servern.</span><span class="sxs-lookup"><span data-stu-id="cddba-156">This is especially useful in scenarios where you do not want to set up a Pull Server.</span></span> <span data-ttu-id="cddba-157">Den **ResourceRepositoryShare** block kan användas utan att ange en **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="cddba-157">The **ResourceRepositoryShare** block can be used without specifying a **ConfigurationRepositoryShare**.</span></span> <span data-ttu-id="cddba-158">I följande exempel visas en metaconfiguration som ställer in en klient till pull-resurser från en SMB-resurs `\\SMBPullServer\Resources`.</span><span class="sxs-lookup"><span data-stu-id="cddba-158">The following example shows a metaconfiguration that sets up a client to pull resources from an SMB Share `\\SMBPullServer\Resources`.</span></span> <span data-ttu-id="cddba-159">När noden är **PUSHED** en konfiguration för den hämtar automatiskt alla nödvändiga resurser från den resurs som anges.</span><span class="sxs-lookup"><span data-stu-id="cddba-159">When the Node is **PUSHED** a configuration, it will automatically download any required resources, from the share specified.</span></span>

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

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="cddba-160">Ställa in en Pull-klient för att rapportera status</span><span class="sxs-lookup"><span data-stu-id="cddba-160">Set up a Pull Client to report status</span></span>

<span data-ttu-id="cddba-161">Som standard skickar noder inte rapporter till en konfigurerad Pull-Server.</span><span class="sxs-lookup"><span data-stu-id="cddba-161">By default, Nodes will not send reports to a configured Pull Server.</span></span> <span data-ttu-id="cddba-162">Du kan använda en enda pull-server för konfigurationer, resurser och rapportering, men du måste skapa en **ReportRepositoryWeb** förhindra om du vill konfigurera rapportering.</span><span class="sxs-lookup"><span data-stu-id="cddba-162">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="cddba-163">HTTP DSC Pull Server</span><span class="sxs-lookup"><span data-stu-id="cddba-163">HTTP DSC Pull Server</span></span>

<span data-ttu-id="cddba-164">I följande exempel visas en metaconfiguration som ställer in en klient till pull-konfigurationer och resurser och skicka rapportdata till en enda pull-server.</span><span class="sxs-lookup"><span data-stu-id="cddba-164">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

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

<span data-ttu-id="cddba-165">Om du vill ange en rapportserver som du använder en **ReportRepositoryWeb** block.</span><span class="sxs-lookup"><span data-stu-id="cddba-165">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="cddba-166">En rapportserver får inte vara en SMB-server.</span><span class="sxs-lookup"><span data-stu-id="cddba-166">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="cddba-167">Följande metaconfiguration konfigurerar en pullklient för att få dess konfigurationerna från **CONTOSO PullSrv** och dess resurser från **CONTOSO ResourceSrv**, samt skicka statusrapporter till  **CONTOSO-ReportSrv**:</span><span class="sxs-lookup"><span data-stu-id="cddba-167">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

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

### <a name="smb-share"></a><span data-ttu-id="cddba-168">SMB Share</span><span class="sxs-lookup"><span data-stu-id="cddba-168">SMB Share</span></span>

<span data-ttu-id="cddba-169">En rapportserver får inte vara en SMB-resurs.</span><span class="sxs-lookup"><span data-stu-id="cddba-169">A report server cannot be an SMB share.</span></span>

## <a name="next-steps"></a><span data-ttu-id="cddba-170">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="cddba-170">Next Steps</span></span>

<span data-ttu-id="cddba-171">När pull-klienten har konfigurerats kan använda du följande guider för att utföra nästa steg:</span><span class="sxs-lookup"><span data-stu-id="cddba-171">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="cddba-172">Publicera konfigurationer till en Pull-Server (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="cddba-172">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="cddba-173">Paket- och ladda upp resurser till en Pull-Server (v4)</span><span class="sxs-lookup"><span data-stu-id="cddba-173">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="cddba-174">Se även</span><span class="sxs-lookup"><span data-stu-id="cddba-174">See Also</span></span>

* [<span data-ttu-id="cddba-175">Konfigurera en hämtningsklient med konfigurationsnamn</span><span class="sxs-lookup"><span data-stu-id="cddba-175">Setting up a pull client with configuration names</span></span>](pullClientConfigNames.md)
