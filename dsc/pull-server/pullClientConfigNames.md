---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Ställa in en Pull-klient med konfigurationsnamn i PowerShell 5.0 och senare
ms.openlocfilehash: d591e2a757130ccecaf4eaf9f363f607fca82b93
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058204"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a><span data-ttu-id="e72d6-103">Ställa in en Pull-klient med konfigurationsnamn i PowerShell 5.0 och senare</span><span class="sxs-lookup"><span data-stu-id="e72d6-103">Set up a Pull Client using Configuration Names in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="e72d6-104">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e72d6-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e72d6-105">Pull-servern (Windows-funktionen *DSC-tjänst*) är en stöds komponent i Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner.</span><span class="sxs-lookup"><span data-stu-id="e72d6-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="e72d6-106">Rekommenderar vi att du påbörjar övergången hanterade klienter [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inklusive funktioner utöver Pull-servern på Windows Server) eller en av community-lösningar visas [här](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="e72d6-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="e72d6-107">Innan du konfigurerar en pullklient, bör du ställa in en pull-server.</span><span class="sxs-lookup"><span data-stu-id="e72d6-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="e72d6-108">Även om den här ordningen inte är obligatoriskt, hjälper till med felsökning och hjälper dig att säkerställa att registreringen har lyckats.</span><span class="sxs-lookup"><span data-stu-id="e72d6-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="e72d6-109">Om du vill konfigurera en pull-server kan du använda följande guider:</span><span class="sxs-lookup"><span data-stu-id="e72d6-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="e72d6-110">Konfigurera en DSC SMB-Hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="e72d6-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="e72d6-111">Konfigurera en DSC HTTP-Hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="e72d6-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="e72d6-112">Varje målnoden kan konfigureras för att hämta konfigurationer, resurser, och även rapportera statusen.</span><span class="sxs-lookup"><span data-stu-id="e72d6-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="e72d6-113">I avsnitten nedan visar hur du konfigurerar en hämtningsklient med en SMB-resursen eller HTTP DSC-Hämtningsservern.</span><span class="sxs-lookup"><span data-stu-id="e72d6-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="e72d6-114">När nodens LCM uppdaterar kommer det att kontakta konfigurerade platsen för att hämta alla tilldelade konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="e72d6-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="e72d6-115">Om alla nödvändiga resurser inte finns på noden, kommer den automatiskt hämta dem från den konfigurerade platsen.</span><span class="sxs-lookup"><span data-stu-id="e72d6-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="e72d6-116">Om noden är konfigurerad med en [Report Server](reportServer.md), kommer den sedan att rapportera status för åtgärden.</span><span class="sxs-lookup"><span data-stu-id="e72d6-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> [!NOTE]
> <span data-ttu-id="e72d6-117">Det här avsnittet gäller för PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="e72d6-117">This topic applies to PowerShell 5.0.</span></span>
> <span data-ttu-id="e72d6-118">Information om hur du konfigurerar en pullklient i PowerShell 4.0 finns i [konfigurera en hämtningsklient med konfigurations-ID i PowerShell 4.0](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="e72d6-118">For information on setting up a pull client in PowerShell 4.0, see [Set up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="e72d6-119">Konfigurera en pullklient LCM</span><span class="sxs-lookup"><span data-stu-id="e72d6-119">Configure the pull client LCM</span></span>

<span data-ttu-id="e72d6-120">Kör något av exemplen nedan skapar en ny utdata-mapp med namnet **PullClientConfigName** och det placerar en metaconfiguration MOF-fil.</span><span class="sxs-lookup"><span data-stu-id="e72d6-120">Executing any of the examples below creates a new output folder named **PullClientConfigName** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="e72d6-121">I det här fallet metaconfiguration MOF-filen namnet `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="e72d6-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="e72d6-122">Om du vill tillämpa konfigurationen av genom att anropa den **Set-DscLocalConfigurationManager** cmdlet, med den **sökväg** inställd på platsen för metaconfiguration MOF-filen.</span><span class="sxs-lookup"><span data-stu-id="e72d6-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="e72d6-123">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="e72d6-123">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a><span data-ttu-id="e72d6-124">Konfigurationsnamn</span><span class="sxs-lookup"><span data-stu-id="e72d6-124">Configuration Name</span></span>

<span data-ttu-id="e72d6-125">Exemplen nedan anger den **ConfigurationName** egenskapen för LCM till namnet på en tidigare kompilerad konfiguration som skapats för detta ändamål.</span><span class="sxs-lookup"><span data-stu-id="e72d6-125">The examples below sets the **ConfigurationName** property of the LCM to the name of a previously compiled Configuration, created for this purpose.</span></span> <span data-ttu-id="e72d6-126">Den **ConfigurationName** är vad LCM används för att hitta lämplig konfiguration på hämtningsservern.</span><span class="sxs-lookup"><span data-stu-id="e72d6-126">The **ConfigurationName** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="e72d6-127">MOF-konfigurationsfilen på hämtningsservern måste ha namnet `<ConfigurationName>.mof`, i det här fallet ”ClientConfig.mof”.</span><span class="sxs-lookup"><span data-stu-id="e72d6-127">The configuration MOF file on the pull server must be named `<ConfigurationName>.mof`, in this case, "ClientConfig.mof".</span></span> <span data-ttu-id="e72d6-128">Mer information finns i [publicera konfigurationer för att en Pull-servern (v4/v5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="e72d6-128">For more information, see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="e72d6-129">Konfigurera en Pull-klient för att ladda ned konfigurationer</span><span class="sxs-lookup"><span data-stu-id="e72d6-129">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="e72d6-130">Varje klient måste konfigureras i **Pull** läge och angivna pull-serveradress där dess konfiguration lagras.</span><span class="sxs-lookup"><span data-stu-id="e72d6-130">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="e72d6-131">Då har du konfigurerar den lokala Configuration Manager (LCM) med informationen som krävs.</span><span class="sxs-lookup"><span data-stu-id="e72d6-131">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="e72d6-132">Om du vill konfigurera LCM måste du skapa en särskild typ av konfiguration, dekorerad med den **DSCLocalConfigurationManager** attribut.</span><span class="sxs-lookup"><span data-stu-id="e72d6-132">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="e72d6-133">Läs mer om hur du konfigurerar LCM [konfigurerar den lokala Konfigurationshanteraren](../managing-nodes/metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="e72d6-133">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

<span data-ttu-id="e72d6-134">Följande skript konfigurerar LCM pull konfigurationer från en server med namnet ”CONTOSO-PullSrv”.</span><span class="sxs-lookup"><span data-stu-id="e72d6-134">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

- <span data-ttu-id="e72d6-135">I skriptet den **ConfigurationRepositoryWeb** block definierar hämtningsservern.</span><span class="sxs-lookup"><span data-stu-id="e72d6-135">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="e72d6-136">Den **ServerURL** egenskap anger slutpunkten för pull-servern.</span><span class="sxs-lookup"><span data-stu-id="e72d6-136">The **ServerURL** property specifies the endpoint for the pull server.</span></span>

- <span data-ttu-id="e72d6-137">Den **RegistrationKey** egenskapen är en delad nyckel mellan alla klientnoder för en pull-server och den pull-servern.</span><span class="sxs-lookup"><span data-stu-id="e72d6-137">The **RegistrationKey** property is a shared key between all client nodes for a pull server and that pull server.</span></span> <span data-ttu-id="e72d6-138">Samma värde lagras i en fil på hämtningsservern.</span><span class="sxs-lookup"><span data-stu-id="e72d6-138">The same value is stored in a file on the pull server.</span></span>
  > [!NOTE]
  > <span data-ttu-id="e72d6-139">Registreringsnycklar fungerar bara med **web** pull-servrar.</span><span class="sxs-lookup"><span data-stu-id="e72d6-139">Registration keys work only with **web** pull servers.</span></span> <span data-ttu-id="e72d6-140">Du måste fortfarande använda **ConfigurationID** med en **SMB** hämtningsservern.</span><span class="sxs-lookup"><span data-stu-id="e72d6-140">You must still use **ConfigurationID** with an **SMB** pull server.</span></span>
  > <span data-ttu-id="e72d6-141">Information om hur du konfigurerar en pull-server med hjälp av **ConfigurationID**, se [konfigurera en hämtningsklient med konfigurations-ID](pullClientConfigId.md)</span><span class="sxs-lookup"><span data-stu-id="e72d6-141">For information about configuring a pull server by using **ConfigurationID**, see [Setting up a pull client using configuration ID](pullClientConfigId.md)</span></span>

- <span data-ttu-id="e72d6-142">Den **ConfigurationNames** egenskapen är en matris som anger namnen på de konfigurationer som är avsedd för klient-nod.</span><span class="sxs-lookup"><span data-stu-id="e72d6-142">The **ConfigurationNames** property is an array that specifies the names of the configurations intended for the client node.</span></span>
  ><span data-ttu-id="e72d6-143">**Obs:** Om du anger fler än ett värde i den **ConfigurationNames**, måste du även ange **PartialConfiguration** blockerar i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="e72d6-143">**Note:** If you specify more than one value in the **ConfigurationNames**, you must also specify **PartialConfiguration** blocks in your configuration.</span></span>
  ><span data-ttu-id="e72d6-144">Läs om hur partiella konfigurationer [PowerShell Desired State Configuration partiella konfigurationer](partialConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="e72d6-144">For information about partial configurations, see [PowerShell Desired State Configuration partial configurations](partialConfigs.md).</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
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
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="e72d6-145">Konfigurera en Pull-klient för att hämta resurser</span><span class="sxs-lookup"><span data-stu-id="e72d6-145">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="e72d6-146">Om du anger bara en **ConfigurationRepositoryWeb** eller **ConfigurationRepositoryShare** blockera i din LCM-konfiguration (som i föregående exempel), pull-klienten hämtar resurser från samma plats där MOF-filerna lagras.</span><span class="sxs-lookup"><span data-stu-id="e72d6-146">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from same location where your ".mof" files are stored.</span></span> <span data-ttu-id="e72d6-147">Du kan också ange olika platser där klienter kan hämta resurser.</span><span class="sxs-lookup"><span data-stu-id="e72d6-147">You can also specify different locations where clients can download resources.</span></span> <span data-ttu-id="e72d6-148">Om du vill ange resursservern du använda antingen en **ResourceRepositoryWeb** (för en webbpullserver) eller en **ResourceRepositoryShare** block (för SMB-pullserver).</span><span class="sxs-lookup"><span data-stu-id="e72d6-148">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>

<span data-ttu-id="e72d6-149">I följande exempel visas en metaconfiguration som ställer in en klient att ladda ned konfigurationer från en Pull-servern och resurser från en SMB-resurs.</span><span class="sxs-lookup"><span data-stu-id="e72d6-149">The following example shows a metaconfiguration that sets up a client to download configurations from a Pull Server, and resources from an SMB share.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
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

        ResourceRepositoryShare SMBResources
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="e72d6-150">Ställa in en Pull-klient för att rapportera status</span><span class="sxs-lookup"><span data-stu-id="e72d6-150">Set up a Pull Client to report status</span></span>

<span data-ttu-id="e72d6-151">Du kan använda en enda pull-server för konfigurationer, resurser och rapportering.</span><span class="sxs-lookup"><span data-stu-id="e72d6-151">You can use a single pull server for configurations, resources, and reporting.</span></span> <span data-ttu-id="e72d6-152">Rapportering har inte konfigurerats för klienter som standard.</span><span class="sxs-lookup"><span data-stu-id="e72d6-152">Reporting is not configured for clients by default.</span></span> <span data-ttu-id="e72d6-153">Om du vill konfigurera en klient för att rapportera status, måste du skapa en **ReportRepositoryWeb** block.</span><span class="sxs-lookup"><span data-stu-id="e72d6-153">To configure a client to report status, you have to create a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="e72d6-154">I följande exempel visas en metaconfiguration som ställer in en klient till pull-konfigurationer och resurser och skicka rapportdata till en enda pull-server.</span><span class="sxs-lookup"><span data-stu-id="e72d6-154">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

> [!NOTE]
> <span data-ttu-id="e72d6-155">En rapportserver får inte vara en SMB-resurs.</span><span class="sxs-lookup"><span data-stu-id="e72d6-155">A report server cannot be an SMB share.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
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

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a><span data-ttu-id="e72d6-156">Se även</span><span class="sxs-lookup"><span data-stu-id="e72d6-156">See Also</span></span>

* [<span data-ttu-id="e72d6-157">Konfigurera en hämtningsklient med konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="e72d6-157">Setting up a pull client with configuration ID</span></span>](PullClientConfigNames.md)
* [<span data-ttu-id="e72d6-158">Konfigurera en DSC-webbpullserver</span><span class="sxs-lookup"><span data-stu-id="e72d6-158">Setting up a DSC web pull server</span></span>](pullServer.md)
