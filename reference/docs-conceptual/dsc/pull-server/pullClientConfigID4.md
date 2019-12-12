---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguration, installation
title: 'Konfigurera en pull-klient med konfigurations-ID: n i PowerShell 4,0'
ms.openlocfilehash: 9259c624c8725f7d76f61e9ad7caa42e1bfa308c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71942785"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-40"></a><span data-ttu-id="6bc1a-103">Konfigurera en pull-klient med konfigurations-ID: n i PowerShell 4,0</span><span class="sxs-lookup"><span data-stu-id="6bc1a-103">Set up a Pull Client using Configuration IDs in PowerShell 4.0</span></span>

><span data-ttu-id="6bc1a-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="6bc1a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6bc1a-105">Hämtnings servern (Windows Feature *DSC-tjänst*) är en komponent som stöds av Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner.</span><span class="sxs-lookup"><span data-stu-id="6bc1a-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="6bc1a-106">Vi rekommenderar att du börjar överföra hanterade klienter till [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inklusive funktioner utöver hämtnings servern på Windows Server) eller någon av de community-lösningar som anges [här](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="6bc1a-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="6bc1a-107">Innan du konfigurerar en pull-klient bör du konfigurera en hämtnings Server.</span><span class="sxs-lookup"><span data-stu-id="6bc1a-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="6bc1a-108">Även om den här ordningen inte krävs, hjälper den med fel sökning och hjälper dig att se till att registreringen lyckades.</span><span class="sxs-lookup"><span data-stu-id="6bc1a-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="6bc1a-109">Om du vill konfigurera en hämtnings Server kan du använda följande guider:</span><span class="sxs-lookup"><span data-stu-id="6bc1a-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="6bc1a-110">Konfigurera en DSC SMB-pull-server</span><span class="sxs-lookup"><span data-stu-id="6bc1a-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="6bc1a-111">Konfigurera en DSC HTTP-pull-server</span><span class="sxs-lookup"><span data-stu-id="6bc1a-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="6bc1a-112">Varje målnod kan konfigureras för att ladda ned konfigurationer, resurser och till och med rapportera dess status.</span><span class="sxs-lookup"><span data-stu-id="6bc1a-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="6bc1a-113">I avsnitten nedan visas hur du konfigurerar en pull-klient med en SMB-resurs eller HTTP DSC-pull-server.</span><span class="sxs-lookup"><span data-stu-id="6bc1a-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="6bc1a-114">När nodens LCM uppdateras, kommer den att kontakta den konfigurerade platsen för att ladda ned alla tilldelade konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="6bc1a-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="6bc1a-115">Om det inte finns några nödvändiga resurser på noden hämtas de automatiskt från den konfigurerade platsen.</span><span class="sxs-lookup"><span data-stu-id="6bc1a-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="6bc1a-116">Om noden har kon figurer ATS med en [rapport Server](reportServer.md), kommer den att rapportera statusen för åtgärden.</span><span class="sxs-lookup"><span data-stu-id="6bc1a-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="6bc1a-117">Konfigurera LCM för pull-klienten</span><span class="sxs-lookup"><span data-stu-id="6bc1a-117">Configure the pull client LCM</span></span>

<span data-ttu-id="6bc1a-118">Om du kör något av exemplen nedan skapas en ny mapp med namnet **PullClientConfigID** och en metaconfiguration MOF-fil placeras där.</span><span class="sxs-lookup"><span data-stu-id="6bc1a-118">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="6bc1a-119">I det här fallet får MOF-filen metaconfiguration namnet `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="6bc1a-119">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="6bc1a-120">Om du vill använda konfigurationen anropar du cmdleten **set-DscLocalConfigurationManager** med **sökvägen** inställd på platsen för MOF-filen för metaconfiguration.</span><span class="sxs-lookup"><span data-stu-id="6bc1a-120">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="6bc1a-121">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="6bc1a-121">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="6bc1a-122">Konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="6bc1a-122">Configuration ID</span></span>

<span data-ttu-id="6bc1a-123">I exemplen nedan anges egenskapen **ConfigurationID** för LCM till ett **GUID** som tidigare har skapats för detta ändamål.</span><span class="sxs-lookup"><span data-stu-id="6bc1a-123">The examples below set the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="6bc1a-124">**ConfigurationID** är vad LCM använder för att hitta rätt konfiguration på hämtnings servern.</span><span class="sxs-lookup"><span data-stu-id="6bc1a-124">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="6bc1a-125">MOF-konfigurationsfilen på hämtnings servern måste namnges `ConfigurationID.mof`, där *ConfigurationID* är värdet för egenskapen **CONFIGURATIONID** för målnoden LCM.</span><span class="sxs-lookup"><span data-stu-id="6bc1a-125">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="6bc1a-126">Mer information finns i [publicera konfigurationer till en pull-server (v4/V5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="6bc1a-126">For more information, see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="6bc1a-127">Du kan skapa ett slumpmässigt **GUID** med hjälp av exemplet nedan.</span><span class="sxs-lookup"><span data-stu-id="6bc1a-127">You can create a random **Guid** using the example below.</span></span>

```powershell
[System.Guid]::NewGuid()
```

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="6bc1a-128">Konfigurera en pull-klient för att hämta konfigurationer</span><span class="sxs-lookup"><span data-stu-id="6bc1a-128">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="6bc1a-129">Varje klient måste konfigureras i **pull** -läge och tilldelas URL-adressen till pull-servern där konfigurationen lagras.</span><span class="sxs-lookup"><span data-stu-id="6bc1a-129">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="6bc1a-130">Om du vill göra detta måste du konfigurera den lokala Configuration Manager (LCM) med nödvändig information.</span><span class="sxs-lookup"><span data-stu-id="6bc1a-130">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="6bc1a-131">Om du vill konfigurera LCM skapar du en särskild typ av konfiguration med ett **LocalConfigurationManager** -block.</span><span class="sxs-lookup"><span data-stu-id="6bc1a-131">To configure the LCM, you create a special type of configuration, with a **LocalConfigurationManager** block.</span></span> <span data-ttu-id="6bc1a-132">Mer information om hur du konfigurerar LCM finns i [Konfigurera den lokala Configuration Manager](../managing-nodes/metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="6bc1a-132">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig4.md).</span></span>

## <a name="http-dsc-pull-server"></a><span data-ttu-id="6bc1a-133">HTTP DSC-hämtnings Server</span><span class="sxs-lookup"><span data-stu-id="6bc1a-133">HTTP DSC Pull Server</span></span>

<span data-ttu-id="6bc1a-134">Om hämtnings servern har kon figurer ATS som en webb tjänst ställer du in **DownloadManagerName** på **WebDownloadManager**.</span><span class="sxs-lookup"><span data-stu-id="6bc1a-134">If the pull server is set up as a web service, you set the **DownloadManagerName** to **WebDownloadManager**.</span></span> <span data-ttu-id="6bc1a-135">**WebDownloadManager** kräver att du anger en **ServerURL** till **DownloadManagerCustomData** -nyckeln.</span><span class="sxs-lookup"><span data-stu-id="6bc1a-135">The **WebDownloadManager** requires that you specify a **ServerUrl** to the **DownloadManagerCustomData** key.</span></span> <span data-ttu-id="6bc1a-136">Du kan också ange ett värde för **AllowUnsecureConnection**, som i exemplet nedan.</span><span class="sxs-lookup"><span data-stu-id="6bc1a-136">You can also specify a value for **AllowUnsecureConnection**, as in the example below.</span></span> <span data-ttu-id="6bc1a-137">Följande skript konfigurerar LCM för att hämta konfigurationer från en server med namnet "PullServer".</span><span class="sxs-lookup"><span data-stu-id="6bc1a-137">The following script configures the LCM to pull configurations from a server named "PullServer".</span></span>

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "WebDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = "TRUE"}
    }
}
PullClientConfigId -Output "."
```

## <a name="smb-share"></a><span data-ttu-id="6bc1a-138">SMB-resurs</span><span class="sxs-lookup"><span data-stu-id="6bc1a-138">SMB Share</span></span>

<span data-ttu-id="6bc1a-139">Om hämtnings servern har kon figurer ATS som en SMB-filresurs i stället för en webb tjänst anger du **DownloadManagerName** till **DscFileDownloadManager** snarare än **WebDownLoadManager**.</span><span class="sxs-lookup"><span data-stu-id="6bc1a-139">If the pull server is set up as an SMB file share, rather than a web service, you set the **DownloadManagerName** to **DscFileDownloadManager** rather than the **WebDownLoadManager**.</span></span> <span data-ttu-id="6bc1a-140">**DscFileDownloadManager** kräver att du anger en **SourcePath** -egenskap i **DownloadManagerCustomData**.</span><span class="sxs-lookup"><span data-stu-id="6bc1a-140">The **DscFileDownloadManager** requires that you specify a **SourcePath** property in the **DownloadManagerCustomData**.</span></span> <span data-ttu-id="6bc1a-141">Följande skript konfigurerar LCM för att hämta konfigurationer från en SMB-resurs med namnet "SmbDscShare" på en server med namnet "CONTOSO-SERVER".</span><span class="sxs-lookup"><span data-stu-id="6bc1a-141">The following script configures the LCM to pull configurations from an SMB share named "SmbDscShare" on a server named "CONTOSO-SERVER".</span></span>

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "DscFileDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "\\CONTOSO-SERVER\SmbDscShare"}
    }
}
PullClientConfigId -Output "."
```

## <a name="next-steps"></a><span data-ttu-id="6bc1a-142">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="6bc1a-142">Next Steps</span></span>

<span data-ttu-id="6bc1a-143">När pull-klienten har kon figurer ATS kan du använda följande guider för att utföra nästa steg:</span><span class="sxs-lookup"><span data-stu-id="6bc1a-143">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="6bc1a-144">Publicera konfigurationer till en pull-server (v4/V5)</span><span class="sxs-lookup"><span data-stu-id="6bc1a-144">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="6bc1a-145">Paketera och ladda upp resurser till en pull-server (v4)</span><span class="sxs-lookup"><span data-stu-id="6bc1a-145">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="6bc1a-146">Se även</span><span class="sxs-lookup"><span data-stu-id="6bc1a-146">See Also</span></span>

- [<span data-ttu-id="6bc1a-147">Konfigurera en DSC-webb hämtnings Server</span><span class="sxs-lookup"><span data-stu-id="6bc1a-147">Set up a DSC web pull server</span></span>](pullServer.md)
- [<span data-ttu-id="6bc1a-148">Konfigurera en DSC SMB-pull-server</span><span class="sxs-lookup"><span data-stu-id="6bc1a-148">Set up a DSC SMB pull server</span></span>](pullServerSMB.md)
