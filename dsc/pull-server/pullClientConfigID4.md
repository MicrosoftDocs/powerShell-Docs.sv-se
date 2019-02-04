---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguration, installation
title: Ställa in en Pull-klient med hjälp av konfigurations-ID i PowerShell 4.0
ms.openlocfilehash: 9adc767e91ff19d373c122a0d493e7b8703d5476
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685482"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-40"></a><span data-ttu-id="3869a-103">Ställa in en Pull-klient med hjälp av konfigurations-ID i PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="3869a-103">Set up a Pull Client using Configuration IDs in PowerShell 4.0</span></span>

><span data-ttu-id="3869a-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="3869a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3869a-105">Pull-servern (Windows-funktionen *DSC-tjänst*) är en stöds komponent i Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner.</span><span class="sxs-lookup"><span data-stu-id="3869a-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="3869a-106">Rekommenderar vi att du påbörjar övergången hanterade klienter [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inklusive funktioner utöver Pull-servern på Windows Server) eller en av community-lösningar visas [här](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="3869a-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="3869a-107">Innan du konfigurerar en pullklient, bör du ställa in en pull-server.</span><span class="sxs-lookup"><span data-stu-id="3869a-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="3869a-108">Även om den här ordningen inte är obligatoriskt, hjälper till med felsökning och hjälper dig att säkerställa att registreringen har lyckats.</span><span class="sxs-lookup"><span data-stu-id="3869a-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="3869a-109">Om du vill konfigurera en pull-server kan du använda följande guider:</span><span class="sxs-lookup"><span data-stu-id="3869a-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="3869a-110">Konfigurera en DSC SMB-Hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="3869a-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="3869a-111">Konfigurera en DSC HTTP-Hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="3869a-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="3869a-112">Varje målnoden kan konfigureras för att hämta konfigurationer, resurser, och även rapportera statusen.</span><span class="sxs-lookup"><span data-stu-id="3869a-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="3869a-113">I avsnitten nedan visar hur du konfigurerar en hämtningsklient med en SMB-resursen eller HTTP DSC-Hämtningsservern.</span><span class="sxs-lookup"><span data-stu-id="3869a-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="3869a-114">När nodens LCM uppdaterar kommer det att kontakta konfigurerade platsen för att hämta alla tilldelade konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="3869a-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="3869a-115">Om alla nödvändiga resurser inte finns på noden, kommer den automatiskt hämta dem från den konfigurerade platsen.</span><span class="sxs-lookup"><span data-stu-id="3869a-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="3869a-116">Om noden är konfigurerad med en [Report Server](reportServer.md), kommer den sedan att rapportera status för åtgärden.</span><span class="sxs-lookup"><span data-stu-id="3869a-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="3869a-117">Konfigurera en pullklient LCM</span><span class="sxs-lookup"><span data-stu-id="3869a-117">Configure the pull client LCM</span></span>

<span data-ttu-id="3869a-118">Kör något av exemplen nedan skapar en ny utdata-mapp med namnet **PullClientConfigID** och det placerar en metaconfiguration MOF-fil.</span><span class="sxs-lookup"><span data-stu-id="3869a-118">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="3869a-119">I det här fallet metaconfiguration MOF-filen namnet `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="3869a-119">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="3869a-120">Om du vill tillämpa konfigurationen av genom att anropa den **Set-DscLocalConfigurationManager** cmdlet, med den **sökväg** inställd på platsen för metaconfiguration MOF-filen.</span><span class="sxs-lookup"><span data-stu-id="3869a-120">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="3869a-121">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="3869a-121">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="3869a-122">Konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="3869a-122">Configuration ID</span></span>

<span data-ttu-id="3869a-123">Exemplen nedan set den **ConfigurationID** egenskapen för MGM om du vill en **Guid** som tidigare hade skapats för detta ändamål.</span><span class="sxs-lookup"><span data-stu-id="3869a-123">The examples below set the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="3869a-124">Den **ConfigurationID** är vad LCM används för att hitta lämplig konfiguration på hämtningsservern.</span><span class="sxs-lookup"><span data-stu-id="3869a-124">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="3869a-125">MOF-konfigurationsfilen på hämtningsservern måste ha namnet `ConfigurationID.mof`, där *ConfigurationID* är värdet för den **ConfigurationID** egenskapen för den målnoden MGM.</span><span class="sxs-lookup"><span data-stu-id="3869a-125">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="3869a-126">Mer information finns i [publicera konfigurationer för att en Pull-servern (v4/v5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="3869a-126">For more information, see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="3869a-127">Du kan skapa ett slumpmässigt **Guid** med hjälp av exemplet nedan.</span><span class="sxs-lookup"><span data-stu-id="3869a-127">You can create a random **Guid** using the example below.</span></span>

```powershell
[System.Guid]::NewGuid()
```

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="3869a-128">Konfigurera en Pull-klient för att ladda ned konfigurationer</span><span class="sxs-lookup"><span data-stu-id="3869a-128">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="3869a-129">Varje klient måste konfigureras i **Pull** läge och angivna pull-serveradress där dess konfiguration lagras.</span><span class="sxs-lookup"><span data-stu-id="3869a-129">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="3869a-130">Då har du konfigurerar den lokala Configuration Manager (LCM) med informationen som krävs.</span><span class="sxs-lookup"><span data-stu-id="3869a-130">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="3869a-131">Om du vill konfigurera LCM måste du skapa en särskild typ av konfiguration med en **LocalConfigurationManager** block.</span><span class="sxs-lookup"><span data-stu-id="3869a-131">To configure the LCM, you create a special type of configuration, with a **LocalConfigurationManager** block.</span></span> <span data-ttu-id="3869a-132">Läs mer om hur du konfigurerar LCM [konfigurerar den lokala Konfigurationshanteraren](../managing-nodes/metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="3869a-132">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig4.md).</span></span>

## <a name="http-dsc-pull-server"></a><span data-ttu-id="3869a-133">HTTP DSC Pull Server</span><span class="sxs-lookup"><span data-stu-id="3869a-133">HTTP DSC Pull Server</span></span>

<span data-ttu-id="3869a-134">Om pull-servern har konfigurerats som en webbtjänst kan du ställa in den **DownloadManagerName** till **WebDownloadManager**.</span><span class="sxs-lookup"><span data-stu-id="3869a-134">If the pull server is set up as a web service, you set the **DownloadManagerName** to **WebDownloadManager**.</span></span> <span data-ttu-id="3869a-135">Den **WebDownloadManager** kräver att du anger en **ServerUrl** till den **DownloadManagerCustomData** nyckel.</span><span class="sxs-lookup"><span data-stu-id="3869a-135">The **WebDownloadManager** requires that you specify a **ServerUrl** to the **DownloadManagerCustomData** key.</span></span> <span data-ttu-id="3869a-136">Du kan också ange ett värde för **AllowUnsecureConnection**, som i exemplet nedan.</span><span class="sxs-lookup"><span data-stu-id="3869a-136">You can also specify a value for **AllowUnsecureConnection**, as in the example below.</span></span> <span data-ttu-id="3869a-137">Följande skript konfigurerar LCM pull konfigurationer från en server med namnet ”PullServer”.</span><span class="sxs-lookup"><span data-stu-id="3869a-137">The following script configures the LCM to pull configurations from a server named "PullServer".</span></span>

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
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = “TRUE”}
    }
}
PullClientConfigId -Output "."
```

## <a name="smb-share"></a><span data-ttu-id="3869a-138">SMB Share</span><span class="sxs-lookup"><span data-stu-id="3869a-138">SMB Share</span></span>

<span data-ttu-id="3869a-139">Om pull-servern har konfigurerats som en SMB-filresurs, i stället för en webbtjänst kan du ställa in den **DownloadManagerName** till **DscFileDownloadManager** snarare än **WebDownLoadManager**.</span><span class="sxs-lookup"><span data-stu-id="3869a-139">If the pull server is set up as an SMB file share, rather than a web service, you set the **DownloadManagerName** to **DscFileDownloadManager** rather than the **WebDownLoadManager**.</span></span> <span data-ttu-id="3869a-140">Den **DscFileDownloadManager** kräver att du anger en **SourcePath** -egenskapen i den **DownloadManagerCustomData**.</span><span class="sxs-lookup"><span data-stu-id="3869a-140">The **DscFileDownloadManager** requires that you specify a **SourcePath** property in the **DownloadManagerCustomData**.</span></span> <span data-ttu-id="3869a-141">Följande skript konfigurerar MGM om du vill dra konfigurationer från en SMB-filresurs som heter ”SmbDscShare” på en server med namnet ”CONTOSO-SERVER”.</span><span class="sxs-lookup"><span data-stu-id="3869a-141">The following script configures the LCM to pull configurations from an SMB share named "SmbDscShare" on a server named "CONTOSO-SERVER".</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="3869a-142">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="3869a-142">Next Steps</span></span>

<span data-ttu-id="3869a-143">När pull-klienten har konfigurerats kan använda du följande guider för att utföra nästa steg:</span><span class="sxs-lookup"><span data-stu-id="3869a-143">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="3869a-144">Publicera konfigurationer till en Pull-Server (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="3869a-144">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="3869a-145">Paket- och ladda upp resurser till en Pull-Server (v4)</span><span class="sxs-lookup"><span data-stu-id="3869a-145">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="3869a-146">Se även</span><span class="sxs-lookup"><span data-stu-id="3869a-146">See Also</span></span>

- [<span data-ttu-id="3869a-147">Konfigurera en DSC-webbpullserver</span><span class="sxs-lookup"><span data-stu-id="3869a-147">Set up a DSC web pull server</span></span>](pullServer.md)
- [<span data-ttu-id="3869a-148">Konfigurera en DSC SMB-hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="3869a-148">Set up a DSC SMB pull server</span></span>](pullServerSMB.md)
