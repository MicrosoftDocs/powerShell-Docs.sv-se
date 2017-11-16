---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "Ställa in en pull-klient som använder konfigurationsnamn"
ms.openlocfilehash: 9bfcac87300d30a59b66e60ed24add32e2420e21
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="setting-up-a-pull-client-using-configuration-names"></a><span data-ttu-id="47d16-103">Ställa in en pull-klient som använder konfigurationsnamn</span><span class="sxs-lookup"><span data-stu-id="47d16-103">Setting up a pull client using configuration names</span></span>

> <span data-ttu-id="47d16-104">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="47d16-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="47d16-105">Varje målnoden måste vara ett meddelande om att använda pull-läge och de angivna URL: en där den kontaktar pull-servern för att hämta konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="47d16-105">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span>
<span data-ttu-id="47d16-106">Du måste konfigurera lokala Configuration Manager (MGM) med informationen som behövs för att göra detta.</span><span class="sxs-lookup"><span data-stu-id="47d16-106">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span>
<span data-ttu-id="47d16-107">Om du vill konfigurera MGM om du skapar en särskild typ av konfiguration, med den **DSCLocalConfigurationManager** attribut.</span><span class="sxs-lookup"><span data-stu-id="47d16-107">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span>
<span data-ttu-id="47d16-108">Mer information om hur du konfigurerar MGM finns [konfigurera den lokala Configuration Manager](metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="47d16-108">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

> <span data-ttu-id="47d16-109">**Obs**: det här avsnittet gäller PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="47d16-109">**Note**: This topic applies to PowerShell 5.0.</span></span>
<span data-ttu-id="47d16-110">Information om hur du skapar en pull-klient i PowerShell 4.0 finns [installera en pull-klient med hjälp av konfigurations-ID i PowerShell 4.0](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="47d16-110">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

<span data-ttu-id="47d16-111">Följande skript konfigurerar MGM pull konfigurationer från en server med namnet ”CONTOSO-PullSrv”:</span><span class="sxs-lookup"><span data-stu-id="47d16-111">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv":</span></span>

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

<span data-ttu-id="47d16-112">I skriptet på **ConfigurationRepositoryWeb** block definierar pull-servern.</span><span class="sxs-lookup"><span data-stu-id="47d16-112">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span>
<span data-ttu-id="47d16-113">Den **ServerURL** egenskapen anger slutpunkten för pull-servern.</span><span class="sxs-lookup"><span data-stu-id="47d16-113">The **ServerURL** property specifies the endpoint for the pull server.</span></span>

<span data-ttu-id="47d16-114">Den **RegistrationKey** -egenskapen är en delad nyckel mellan alla klientnoder för en pull-server och den pull-servern.</span><span class="sxs-lookup"><span data-stu-id="47d16-114">The **RegistrationKey** property is a shared key between all client nodes for a pull server and that pull server.</span></span>
<span data-ttu-id="47d16-115">Samma värde lagras i en fil på hämtningsservern.</span><span class="sxs-lookup"><span data-stu-id="47d16-115">The same value is stored in a file on the pull server.</span></span>

<span data-ttu-id="47d16-116">Den **ConfigurationNames** är en matris som anger namnen på de konfigurationer som är avsedda för klientnod.</span><span class="sxs-lookup"><span data-stu-id="47d16-116">The **ConfigurationNames** property is an array that specifies the names of the configurations intended for the client node.</span></span>
<span data-ttu-id="47d16-117">På hämtningsservern i MOF konfigurationsfilen för den här klientnoden måste ha namnet *ConfigurationNames*MOF, där *ConfigurationNames* överensstämmer med värdet för den **ConfigurationNames**  egenskapsuppsättningen i den här metakonfigurationen.</span><span class="sxs-lookup"><span data-stu-id="47d16-117">On the pull server, the configuration MOF file for this client node must be named *ConfigurationNames*.mof, where *ConfigurationNames* matches the value of the **ConfigurationNames** property you set in this metaconfiguration.</span></span>

><span data-ttu-id="47d16-118">**Obs:** om du anger fler än ett värde i den **ConfigurationNames**, måste du också ange **PartialConfiguration** blockerar i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="47d16-118">**Note:** If you specify more than one value in the **ConfigurationNames**, you must also specify **PartialConfiguration** blocks in your configuration.</span></span>
<span data-ttu-id="47d16-119">Information om konfigurationer som delvis finns [PowerShell Desired State Configuration partiella konfigurationer](partialConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="47d16-119">For information about partial configurations, see [PowerShell Desired State Configuration partial configurations](partialConfigs.md).</span></span>

<span data-ttu-id="47d16-120">När skriptet körs, skapas en ny utdatamapp med namnet **PullClientConfigNames** och det placerar en metakonfigurationen MOF-fil.</span><span class="sxs-lookup"><span data-stu-id="47d16-120">After this script runs, it creates a new output folder named **PullClientConfigNames** and puts a metaconfiguration MOF file there.</span></span>
<span data-ttu-id="47d16-121">I det här fallet metakonfigurationen MOF-filen får namnet `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="47d16-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="47d16-122">Om du vill tillämpa konfigurationen genom att anropa den **Set DscLocalConfigurationManager** cmdlet, med den **sökväg** inställd på platsen för metakonfigurationen MOF-filen.</span><span class="sxs-lookup"><span data-stu-id="47d16-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span>

```powershell
Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigNames –Verbose.
```

> <span data-ttu-id="47d16-123">**Obs**: registreringsnycklar fungerar bara med pull-webbservrar.</span><span class="sxs-lookup"><span data-stu-id="47d16-123">**Note**: Registration keys work only with web pull servers.</span></span>
<span data-ttu-id="47d16-124">Du måste använda **ConfigurationID** med en SMB-pull-server.</span><span class="sxs-lookup"><span data-stu-id="47d16-124">You must still use **ConfigurationID** with an SMB pull server.</span></span>
<span data-ttu-id="47d16-125">Information om hur du konfigurerar en pull-server med hjälp av **ConfigurationID**, se [installera en pull-klient med hjälp av konfigurations-ID](PullClientConfigNames.md)</span><span class="sxs-lookup"><span data-stu-id="47d16-125">For information about configuring a pull server by using **ConfigurationID**, see [Setting up a pull client using configuration ID](PullClientConfigNames.md)</span></span>

## <a name="resource-and-report-servers"></a><span data-ttu-id="47d16-126">Resurs- och -servrar</span><span class="sxs-lookup"><span data-stu-id="47d16-126">Resource and report servers</span></span>

<span data-ttu-id="47d16-127">Om du bara anger en **ConfigurationRepositoryWeb** eller **ConfigurationRepositoryShare** blockera i konfigurationen MGM (som i föregående exempel), pull-klienten hämtar resurser från den angiven server, men det kommer inte skicka rapporter till den.</span><span class="sxs-lookup"><span data-stu-id="47d16-127">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from the specified server, but it will not send reports to it.</span></span>
<span data-ttu-id="47d16-128">Du kan använda en enda hämtningsservern för konfigurationer, resurser och rapportering, men du måste skapa en **ReportRepositoryWeb** block att konfigurera rapportering.</span><span class="sxs-lookup"><span data-stu-id="47d16-128">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>
<span data-ttu-id="47d16-129">I följande exempel visas en metakonfigurationen som ställer in en klient till pull konfigurationer och resurser och skicka rapportdata till en enda pull-server.</span><span class="sxs-lookup"><span data-stu-id="47d16-129">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

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
        }
    }
}
PullClientConfigNames
```

<span data-ttu-id="47d16-130">Du kan också ange olika pull-servrar för resurser och rapportering.</span><span class="sxs-lookup"><span data-stu-id="47d16-130">You can also specify different pull servers for resources and reporting.</span></span>
<span data-ttu-id="47d16-131">Om du vill ange en resurs-server du använder antingen en **ResourceRepositoryWeb** (för en webbserver pull) eller en **ResourceRepositoryShare** block (för en SMB-pull-server).</span><span class="sxs-lookup"><span data-stu-id="47d16-131">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>
<span data-ttu-id="47d16-132">Om du vill ange en rapportserver som du använder en **ReportRepositoryWeb** block.</span><span class="sxs-lookup"><span data-stu-id="47d16-132">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span>
<span data-ttu-id="47d16-133">En rapportserver får inte vara en SMB-server.</span><span class="sxs-lookup"><span data-stu-id="47d16-133">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="47d16-134">Följande metakonfigurationen konfigurerar en pull-klient för att få sina konfigurationer från **CONTOSO PullSrv** och dess resurser från **CONTOSO ResourceSrv**, och för att skicka statusrapporter till  **CONTOSO-ReportSrv**:</span><span class="sxs-lookup"><span data-stu-id="47d16-134">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

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

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-ResourceSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '30ef9bd8-9acf-4e01-8374-4dc35710fc90'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-ReportSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '6b392c6a-818c-4b24-bf38-47124f1e2f14'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a><span data-ttu-id="47d16-135">Se även</span><span class="sxs-lookup"><span data-stu-id="47d16-135">See Also</span></span>

* [<span data-ttu-id="47d16-136">Installera en pull-klient med konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="47d16-136">Setting up a pull client with configuration ID</span></span>](PullClientConfigNames.md)
* [<span data-ttu-id="47d16-137">Ställer in en pull webbserver DSC</span><span class="sxs-lookup"><span data-stu-id="47d16-137">Setting up a DSC web pull server</span></span>](pullServer.md)

