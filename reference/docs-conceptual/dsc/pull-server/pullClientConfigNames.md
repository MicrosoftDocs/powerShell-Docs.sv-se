---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Konfigurera en pull-klient med hjälp av konfigurations namn i PowerShell 5,0 och senare
ms.openlocfilehash: d591e2a757130ccecaf4eaf9f363f607fca82b93
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71941721"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a><span data-ttu-id="0efd2-103">Konfigurera en pull-klient med hjälp av konfigurations namn i PowerShell 5,0 och senare</span><span class="sxs-lookup"><span data-stu-id="0efd2-103">Set up a Pull Client using Configuration Names in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="0efd2-104">Gäller för: Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="0efd2-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0efd2-105">Hämtnings servern (Windows Feature *DSC-tjänst*) är en komponent som stöds av Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner.</span><span class="sxs-lookup"><span data-stu-id="0efd2-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="0efd2-106">Vi rekommenderar att du börjar överföra hanterade klienter till [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inklusive funktioner utöver hämtnings servern på Windows Server) eller någon av de community-lösningar som anges [här](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="0efd2-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="0efd2-107">Innan du konfigurerar en pull-klient bör du konfigurera en hämtnings Server.</span><span class="sxs-lookup"><span data-stu-id="0efd2-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="0efd2-108">Även om den här ordningen inte krävs, hjälper den med fel sökning och hjälper dig att se till att registreringen lyckades.</span><span class="sxs-lookup"><span data-stu-id="0efd2-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="0efd2-109">Om du vill konfigurera en hämtnings Server kan du använda följande guider:</span><span class="sxs-lookup"><span data-stu-id="0efd2-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="0efd2-110">Konfigurera en DSC SMB-pull-server</span><span class="sxs-lookup"><span data-stu-id="0efd2-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="0efd2-111">Konfigurera en DSC HTTP-pull-server</span><span class="sxs-lookup"><span data-stu-id="0efd2-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="0efd2-112">Varje målnod kan konfigureras för att ladda ned konfigurationer, resurser och till och med rapportera dess status.</span><span class="sxs-lookup"><span data-stu-id="0efd2-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="0efd2-113">I avsnitten nedan visas hur du konfigurerar en pull-klient med en SMB-resurs eller HTTP DSC-pull-server.</span><span class="sxs-lookup"><span data-stu-id="0efd2-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="0efd2-114">När nodens LCM uppdateras, kommer den att kontakta den konfigurerade platsen för att ladda ned alla tilldelade konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="0efd2-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="0efd2-115">Om det inte finns några nödvändiga resurser på noden hämtas de automatiskt från den konfigurerade platsen.</span><span class="sxs-lookup"><span data-stu-id="0efd2-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="0efd2-116">Om noden har kon figurer ATS med en [rapport Server](reportServer.md), kommer den att rapportera statusen för åtgärden.</span><span class="sxs-lookup"><span data-stu-id="0efd2-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> [!NOTE]
> <span data-ttu-id="0efd2-117">Det här avsnittet gäller för PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="0efd2-117">This topic applies to PowerShell 5.0.</span></span>
> <span data-ttu-id="0efd2-118">Information om hur du konfigurerar en pull-klient i PowerShell 4,0 finns i [Konfigurera en pull-klient med konfigurations-ID i PowerShell 4,0](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="0efd2-118">For information on setting up a pull client in PowerShell 4.0, see [Set up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="0efd2-119">Konfigurera LCM för pull-klienten</span><span class="sxs-lookup"><span data-stu-id="0efd2-119">Configure the pull client LCM</span></span>

<span data-ttu-id="0efd2-120">Om du kör något av exemplen nedan skapas en ny mapp med namnet **PullClientConfigName** och en metaconfiguration MOF-fil placeras där.</span><span class="sxs-lookup"><span data-stu-id="0efd2-120">Executing any of the examples below creates a new output folder named **PullClientConfigName** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="0efd2-121">I det här fallet får MOF-filen metaconfiguration namnet `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="0efd2-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="0efd2-122">Om du vill använda konfigurationen anropar du cmdleten **set-DscLocalConfigurationManager** med **sökvägen** inställd på platsen för MOF-filen för metaconfiguration.</span><span class="sxs-lookup"><span data-stu-id="0efd2-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="0efd2-123">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="0efd2-123">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a><span data-ttu-id="0efd2-124">Konfigurations namn</span><span class="sxs-lookup"><span data-stu-id="0efd2-124">Configuration Name</span></span>

<span data-ttu-id="0efd2-125">I exemplen nedan anges egenskapen **ConfigurationName** för LCM till namnet på en tidigare kompilerad konfiguration som skapats för det här ändamålet.</span><span class="sxs-lookup"><span data-stu-id="0efd2-125">The examples below sets the **ConfigurationName** property of the LCM to the name of a previously compiled Configuration, created for this purpose.</span></span> <span data-ttu-id="0efd2-126">**ConfigurationName** är vad LCM använder för att hitta rätt konfiguration på hämtnings servern.</span><span class="sxs-lookup"><span data-stu-id="0efd2-126">The **ConfigurationName** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="0efd2-127">MOF-konfigurationsfilen på hämtnings servern måste ha namnet `<ConfigurationName>.mof`, i det här fallet "ClientConfig. MOF".</span><span class="sxs-lookup"><span data-stu-id="0efd2-127">The configuration MOF file on the pull server must be named `<ConfigurationName>.mof`, in this case, "ClientConfig.mof".</span></span> <span data-ttu-id="0efd2-128">Mer information finns i [publicera konfigurationer till en pull-server (v4/V5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="0efd2-128">For more information, see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="0efd2-129">Konfigurera en pull-klient för att hämta konfigurationer</span><span class="sxs-lookup"><span data-stu-id="0efd2-129">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="0efd2-130">Varje klient måste konfigureras i **pull** -läge och tilldelas URL-adressen till pull-servern där konfigurationen lagras.</span><span class="sxs-lookup"><span data-stu-id="0efd2-130">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="0efd2-131">Om du vill göra detta måste du konfigurera den lokala Configuration Manager (LCM) med nödvändig information.</span><span class="sxs-lookup"><span data-stu-id="0efd2-131">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="0efd2-132">Om du vill konfigurera LCM skapar du en särskild typ av konfiguration, dekorerat med attributet **DSCLocalConfigurationManager** .</span><span class="sxs-lookup"><span data-stu-id="0efd2-132">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="0efd2-133">Mer information om hur du konfigurerar LCM finns i [Konfigurera den lokala Configuration Manager](../managing-nodes/metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="0efd2-133">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

<span data-ttu-id="0efd2-134">Följande skript konfigurerar LCM att hämta konfigurationer från en server med namnet CONTOSO-PullSrv.</span><span class="sxs-lookup"><span data-stu-id="0efd2-134">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

- <span data-ttu-id="0efd2-135">I skriptet definierar **ConfigurationRepositoryWeb** -blocket hämtnings servern.</span><span class="sxs-lookup"><span data-stu-id="0efd2-135">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="0efd2-136">Egenskapen **ServerURL** anger slut punkten för hämtnings servern.</span><span class="sxs-lookup"><span data-stu-id="0efd2-136">The **ServerURL** property specifies the endpoint for the pull server.</span></span>

- <span data-ttu-id="0efd2-137">Egenskapen **RegistrationKey** är en delad nyckel mellan alla klient-noder för en pull-server och den hämtnings servern.</span><span class="sxs-lookup"><span data-stu-id="0efd2-137">The **RegistrationKey** property is a shared key between all client nodes for a pull server and that pull server.</span></span> <span data-ttu-id="0efd2-138">Samma värde lagras i en fil på hämtnings servern.</span><span class="sxs-lookup"><span data-stu-id="0efd2-138">The same value is stored in a file on the pull server.</span></span>
  > [!NOTE]
  > <span data-ttu-id="0efd2-139">Registrerings nycklar fungerar bara med **webb** hämtnings servrar.</span><span class="sxs-lookup"><span data-stu-id="0efd2-139">Registration keys work only with **web** pull servers.</span></span> <span data-ttu-id="0efd2-140">Du måste fortfarande använda **ConfigurationID** med en **SMB** -pull-server.</span><span class="sxs-lookup"><span data-stu-id="0efd2-140">You must still use **ConfigurationID** with an **SMB** pull server.</span></span>
  > <span data-ttu-id="0efd2-141">Information om hur du konfigurerar en pull-server med hjälp av **ConfigurationID**finns i [Konfigurera en pull-klient med konfigurations-ID](pullClientConfigId.md)</span><span class="sxs-lookup"><span data-stu-id="0efd2-141">For information about configuring a pull server by using **ConfigurationID**, see [Setting up a pull client using configuration ID](pullClientConfigId.md)</span></span>

- <span data-ttu-id="0efd2-142">Egenskapen **ConfigurationNames** är en matris som anger namnen på de konfigurationer som är avsedda för-klient-noden.</span><span class="sxs-lookup"><span data-stu-id="0efd2-142">The **ConfigurationNames** property is an array that specifies the names of the configurations intended for the client node.</span></span>
  ><span data-ttu-id="0efd2-143">**Obs:** Om du anger fler än ett värde i **ConfigurationNames**måste du också ange **PartialConfiguration** -block i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="0efd2-143">**Note:** If you specify more than one value in the **ConfigurationNames**, you must also specify **PartialConfiguration** blocks in your configuration.</span></span>
  ><span data-ttu-id="0efd2-144">Information om ofullständiga konfigurationer finns i [PowerShell Desired State Configuration del konfigurationer](partialConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="0efd2-144">For information about partial configurations, see [PowerShell Desired State Configuration partial configurations](partialConfigs.md).</span></span>

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

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="0efd2-145">Konfigurera en pull-klient för att ladda ned resurser</span><span class="sxs-lookup"><span data-stu-id="0efd2-145">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="0efd2-146">Om du bara anger ett **ConfigurationRepositoryWeb** -eller **ConfigurationRepositoryShare** -block i LCM-konfigurationen (som i föregående exempel) hämtar pull-klienten resurser från samma plats där dina ". MOF"-filer lagras.</span><span class="sxs-lookup"><span data-stu-id="0efd2-146">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from same location where your ".mof" files are stored.</span></span> <span data-ttu-id="0efd2-147">Du kan också ange olika platser där klienter kan ladda ned resurser.</span><span class="sxs-lookup"><span data-stu-id="0efd2-147">You can also specify different locations where clients can download resources.</span></span> <span data-ttu-id="0efd2-148">Om du vill ange en resurs Server använder du antingen en **ResourceRepositoryWeb** (för en webb hämtnings Server) eller ett **ResourceRepositoryShare** -block (för en SMB-pull-server).</span><span class="sxs-lookup"><span data-stu-id="0efd2-148">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>

<span data-ttu-id="0efd2-149">I följande exempel visas en metaconfiguration som konfigurerar en-klient för att hämta konfigurationer från en pull-server och resurser från en SMB-resurs.</span><span class="sxs-lookup"><span data-stu-id="0efd2-149">The following example shows a metaconfiguration that sets up a client to download configurations from a Pull Server, and resources from an SMB share.</span></span>

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

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="0efd2-150">Konfigurera en pull-klient för att rapportera status</span><span class="sxs-lookup"><span data-stu-id="0efd2-150">Set up a Pull Client to report status</span></span>

<span data-ttu-id="0efd2-151">Du kan använda en enda hämtnings Server för konfigurationer, resurser och rapportering.</span><span class="sxs-lookup"><span data-stu-id="0efd2-151">You can use a single pull server for configurations, resources, and reporting.</span></span> <span data-ttu-id="0efd2-152">Rapportering är inte konfigurerat för klienter som standard.</span><span class="sxs-lookup"><span data-stu-id="0efd2-152">Reporting is not configured for clients by default.</span></span> <span data-ttu-id="0efd2-153">Om du vill konfigurera en klient så att den rapporterar status måste du skapa ett **ReportRepositoryWeb** -block.</span><span class="sxs-lookup"><span data-stu-id="0efd2-153">To configure a client to report status, you have to create a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="0efd2-154">I följande exempel visas en metaconfiguration som konfigurerar en klient för att hämta konfigurationer och resurser och skicka rapporterings data till en enda pull-server.</span><span class="sxs-lookup"><span data-stu-id="0efd2-154">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

> [!NOTE]
> <span data-ttu-id="0efd2-155">En rapport Server kan inte vara en SMB-resurs.</span><span class="sxs-lookup"><span data-stu-id="0efd2-155">A report server cannot be an SMB share.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0efd2-156">Se även</span><span class="sxs-lookup"><span data-stu-id="0efd2-156">See Also</span></span>

* [<span data-ttu-id="0efd2-157">Konfigurera en pull-klient med konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="0efd2-157">Setting up a pull client with configuration ID</span></span>](PullClientConfigNames.md)
* [<span data-ttu-id="0efd2-158">Konfigurera en DSC-webb hämtnings Server</span><span class="sxs-lookup"><span data-stu-id="0efd2-158">Setting up a DSC web pull server</span></span>](pullServer.md)
