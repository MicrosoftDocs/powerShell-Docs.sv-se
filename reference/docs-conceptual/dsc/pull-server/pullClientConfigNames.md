---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Konfigurera en pull-klient med hjälp av konfigurations namn i PowerShell 5,0 och senare
description: Artikeln beskriver hur du konfigurerar en pull-klient med hjälp av konfigurations namn i PowerShell 5,0 och senare
ms.openlocfilehash: db2b08605dd8bc7e48d9d5153861ce9b36118e21
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644907"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a><span data-ttu-id="bd1d7-104">Konfigurera en pull-klient med hjälp av konfigurations namn i PowerShell 5,0 och senare</span><span class="sxs-lookup"><span data-stu-id="bd1d7-104">Set up a Pull Client using Configuration Names in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="bd1d7-105">Gäller för: Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="bd1d7-105">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bd1d7-106">Hämtnings servern (Windows Feature *DSC-tjänst* ) är en komponent som stöds av Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner.</span><span class="sxs-lookup"><span data-stu-id="bd1d7-106">The Pull Server (Windows Feature *DSC-Service* ) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="bd1d7-107">Vi rekommenderar att du börjar överföra hanterade klienter till [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inklusive funktioner utöver hämtnings servern på Windows Server) eller någon av de community-lösningar som anges [här](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="bd1d7-107">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="bd1d7-108">Innan du konfigurerar en pull-klient bör du konfigurera en hämtnings Server.</span><span class="sxs-lookup"><span data-stu-id="bd1d7-108">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="bd1d7-109">Även om den här ordningen inte krävs, hjälper den med fel sökning och hjälper dig att se till att registreringen lyckades.</span><span class="sxs-lookup"><span data-stu-id="bd1d7-109">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="bd1d7-110">Om du vill konfigurera en hämtnings Server kan du använda följande guider:</span><span class="sxs-lookup"><span data-stu-id="bd1d7-110">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="bd1d7-111">Konfigurera en DSC SMB-hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="bd1d7-111">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="bd1d7-112">Konfigurera en DSC HTTP-hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="bd1d7-112">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="bd1d7-113">Varje målnod kan konfigureras för att ladda ned konfigurationer, resurser och till och med rapportera dess status.</span><span class="sxs-lookup"><span data-stu-id="bd1d7-113">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="bd1d7-114">I avsnitten nedan visas hur du konfigurerar en pull-klient med en SMB-resurs eller HTTP DSC-pull-server.</span><span class="sxs-lookup"><span data-stu-id="bd1d7-114">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="bd1d7-115">När nodens LCM uppdateras, kommer den att kontakta den konfigurerade platsen för att ladda ned alla tilldelade konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="bd1d7-115">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="bd1d7-116">Om det inte finns några nödvändiga resurser på noden hämtas de automatiskt från den konfigurerade platsen.</span><span class="sxs-lookup"><span data-stu-id="bd1d7-116">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="bd1d7-117">Om noden har kon figurer ATS med en [rapport Server](reportServer.md), kommer den att rapportera statusen för åtgärden.</span><span class="sxs-lookup"><span data-stu-id="bd1d7-117">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> [!NOTE]
> <span data-ttu-id="bd1d7-118">Det här avsnittet gäller för PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="bd1d7-118">This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="bd1d7-119">Information om hur du konfigurerar en pull-klient i PowerShell 4,0 finns i [Konfigurera en pull-klient med konfigurations-ID i PowerShell 4,0](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="bd1d7-119">For information on setting up a pull client in PowerShell 4.0, see [Set up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="bd1d7-120">Konfigurera LCM för pull-klienten</span><span class="sxs-lookup"><span data-stu-id="bd1d7-120">Configure the pull client LCM</span></span>

<span data-ttu-id="bd1d7-121">Om du kör något av exemplen nedan skapas en ny mapp med namnet **PullClientConfigName** och en metaconfiguration MOF-fil placeras där.</span><span class="sxs-lookup"><span data-stu-id="bd1d7-121">Executing any of the examples below creates a new output folder named **PullClientConfigName** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="bd1d7-122">I det här fallet får MOF-filen metaconfiguration namnet `localhost.meta.mof` .</span><span class="sxs-lookup"><span data-stu-id="bd1d7-122">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="bd1d7-123">Om du vill använda konfigurationen anropar du cmdleten **set-DscLocalConfigurationManager** med **sökvägen** inställd på platsen för MOF-filen för metaconfiguration.</span><span class="sxs-lookup"><span data-stu-id="bd1d7-123">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="bd1d7-124">Exempel:</span><span class="sxs-lookup"><span data-stu-id="bd1d7-124">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a><span data-ttu-id="bd1d7-125">Konfigurations namn</span><span class="sxs-lookup"><span data-stu-id="bd1d7-125">Configuration Name</span></span>

<span data-ttu-id="bd1d7-126">I exemplen nedan anges egenskapen **ConfigurationName** för LCM till namnet på en tidigare kompilerad konfiguration som skapats för det här ändamålet.</span><span class="sxs-lookup"><span data-stu-id="bd1d7-126">The examples below sets the **ConfigurationName** property of the LCM to the name of a previously compiled Configuration, created for this purpose.</span></span> <span data-ttu-id="bd1d7-127">**ConfigurationName** är vad LCM använder för att hitta rätt konfiguration på hämtnings servern.</span><span class="sxs-lookup"><span data-stu-id="bd1d7-127">The **ConfigurationName** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="bd1d7-128">MOF-konfigurationsfilen på hämtnings servern måste namnges `<ConfigurationName>.mof` , i det här fallet "ClientConfig. MOF".</span><span class="sxs-lookup"><span data-stu-id="bd1d7-128">The configuration MOF file on the pull server must be named `<ConfigurationName>.mof`, in this case, "ClientConfig.mof".</span></span> <span data-ttu-id="bd1d7-129">Mer information finns i [publicera konfigurationer till en pull-server (v4/V5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="bd1d7-129">For more information, see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="bd1d7-130">Konfigurera en pull-klient för att hämta konfigurationer</span><span class="sxs-lookup"><span data-stu-id="bd1d7-130">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="bd1d7-131">Varje klient måste konfigureras i **pull** -läge och tilldelas URL-adressen till pull-servern där konfigurationen lagras.</span><span class="sxs-lookup"><span data-stu-id="bd1d7-131">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="bd1d7-132">Om du vill göra detta måste du konfigurera den lokala Configuration Manager (LCM) med nödvändig information.</span><span class="sxs-lookup"><span data-stu-id="bd1d7-132">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="bd1d7-133">Om du vill konfigurera LCM skapar du en särskild typ av konfiguration, dekorerat med attributet **DSCLocalConfigurationManager** .</span><span class="sxs-lookup"><span data-stu-id="bd1d7-133">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="bd1d7-134">Mer information om hur du konfigurerar LCM finns i [Konfigurera den lokala Configuration Manager](../managing-nodes/metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="bd1d7-134">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

<span data-ttu-id="bd1d7-135">Följande skript konfigurerar LCM att hämta konfigurationer från en server med namnet CONTOSO-PullSrv.</span><span class="sxs-lookup"><span data-stu-id="bd1d7-135">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

- <span data-ttu-id="bd1d7-136">I skriptet definierar **ConfigurationRepositoryWeb** -blocket hämtnings servern.</span><span class="sxs-lookup"><span data-stu-id="bd1d7-136">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="bd1d7-137">Egenskapen **ServerURL** anger slut punkten för hämtnings servern.</span><span class="sxs-lookup"><span data-stu-id="bd1d7-137">The **ServerURL** property specifies the endpoint for the pull server.</span></span>

- <span data-ttu-id="bd1d7-138">Egenskapen **RegistrationKey** är en delad nyckel mellan alla klient-noder för en pull-server och den hämtnings servern.</span><span class="sxs-lookup"><span data-stu-id="bd1d7-138">The **RegistrationKey** property is a shared key between all client nodes for a pull server and that pull server.</span></span> <span data-ttu-id="bd1d7-139">Samma värde lagras i en fil på hämtnings servern.</span><span class="sxs-lookup"><span data-stu-id="bd1d7-139">The same value is stored in a file on the pull server.</span></span><span data-ttu-id="bd1d7-140"> > [!NOTE] > registrerings nycklar fungerar endast med **webb** hämtnings servrar.</span><span class="sxs-lookup"><span data-stu-id="bd1d7-140"> > [!NOTE] > Registration keys work only with **web** pull servers.</span></span> <span data-ttu-id="bd1d7-141">Du måste fortfarande använda **ConfigurationID** med en **SMB** -pull-server.</span><span class="sxs-lookup"><span data-stu-id="bd1d7-141">You must still use **ConfigurationID** with an **SMB** pull server.</span></span> <span data-ttu-id="bd1d7-142">> information om hur du konfigurerar en pull-server med hjälp av **ConfigurationID** finns i [Konfigurera en pull-klient med konfigurations-ID](pullClientConfigId.md)</span><span class="sxs-lookup"><span data-stu-id="bd1d7-142">> For information about configuring a pull server by using **ConfigurationID** , see [Setting up a pull client using configuration ID](pullClientConfigId.md)</span></span>

- <span data-ttu-id="bd1d7-143">Egenskapen **ConfigurationNames** är en matris som anger namnen på de konfigurationer som är avsedda för-klient-noden.</span><span class="sxs-lookup"><span data-stu-id="bd1d7-143">The **ConfigurationNames** property is an array that specifies the names of the configurations intended for the client node.</span></span><span data-ttu-id="bd1d7-144"> >**Obs:** Om du anger fler än ett värde i **ConfigurationNames** måste du också ange **PartialConfiguration** -block i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="bd1d7-144"> >**Note:** If you specify more than one value in the **ConfigurationNames** , you must also specify **PartialConfiguration** blocks in your configuration.</span></span> <span data-ttu-id="bd1d7-145">>information om ofullständiga konfigurationer finns i [PowerShell Desired State Configuration del konfigurationer](partialConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="bd1d7-145">>For information about partial configurations, see [PowerShell Desired State Configuration partial configurations](partialConfigs.md).</span></span>

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

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="bd1d7-146">Konfigurera en pull-klient för att ladda ned resurser</span><span class="sxs-lookup"><span data-stu-id="bd1d7-146">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="bd1d7-147">Om du bara anger ett **ConfigurationRepositoryWeb** -eller **ConfigurationRepositoryShare** -block i LCM-konfigurationen (som i föregående exempel) hämtar pull-klienten resurser från samma plats där dina ". MOF"-filer lagras.</span><span class="sxs-lookup"><span data-stu-id="bd1d7-147">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from same location where your ".mof" files are stored.</span></span> <span data-ttu-id="bd1d7-148">Du kan också ange olika platser där klienter kan ladda ned resurser.</span><span class="sxs-lookup"><span data-stu-id="bd1d7-148">You can also specify different locations where clients can download resources.</span></span> <span data-ttu-id="bd1d7-149">Om du vill ange en resurs Server använder du antingen en **ResourceRepositoryWeb** (för en webb hämtnings Server) eller ett **ResourceRepositoryShare** -block (för en SMB-pull-server).</span><span class="sxs-lookup"><span data-stu-id="bd1d7-149">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>

<span data-ttu-id="bd1d7-150">I följande exempel visas en metaconfiguration som konfigurerar en-klient för att hämta konfigurationer från en pull-server och resurser från en SMB-resurs.</span><span class="sxs-lookup"><span data-stu-id="bd1d7-150">The following example shows a metaconfiguration that sets up a client to download configurations from a Pull Server, and resources from an SMB share.</span></span>

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

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="bd1d7-151">Konfigurera en pull-klient för att rapportera status</span><span class="sxs-lookup"><span data-stu-id="bd1d7-151">Set up a Pull Client to report status</span></span>

<span data-ttu-id="bd1d7-152">Du kan använda en enda hämtnings Server för konfigurationer, resurser och rapportering.</span><span class="sxs-lookup"><span data-stu-id="bd1d7-152">You can use a single pull server for configurations, resources, and reporting.</span></span> <span data-ttu-id="bd1d7-153">Rapportering är inte konfigurerat för klienter som standard.</span><span class="sxs-lookup"><span data-stu-id="bd1d7-153">Reporting is not configured for clients by default.</span></span> <span data-ttu-id="bd1d7-154">Om du vill konfigurera en klient så att den rapporterar status måste du skapa ett **ReportRepositoryWeb** -block.</span><span class="sxs-lookup"><span data-stu-id="bd1d7-154">To configure a client to report status, you have to create a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="bd1d7-155">I följande exempel visas en metaconfiguration som konfigurerar en klient för att hämta konfigurationer och resurser och skicka rapporterings data till en enda pull-server.</span><span class="sxs-lookup"><span data-stu-id="bd1d7-155">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

> [!NOTE]
> <span data-ttu-id="bd1d7-156">En rapport Server kan inte vara en SMB-resurs.</span><span class="sxs-lookup"><span data-stu-id="bd1d7-156">A report server cannot be an SMB share.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="bd1d7-157">Se även</span><span class="sxs-lookup"><span data-stu-id="bd1d7-157">See Also</span></span>

- [<span data-ttu-id="bd1d7-158">Konfigurera en pull-klient med konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="bd1d7-158">Setting up a pull client with configuration ID</span></span>](PullClientConfigNames.md)
- [<span data-ttu-id="bd1d7-159">Konfigurera en DSC-webb hämtnings Server</span><span class="sxs-lookup"><span data-stu-id="bd1d7-159">Setting up a DSC web pull server</span></span>](pullServer.md)
