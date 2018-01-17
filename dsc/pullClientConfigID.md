---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "Installera en pull-klient med hjälp av konfigurations-ID"
ms.openlocfilehash: 6e3dda1de0bfbf52fb876fdcd2dd2e99da4583dd
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="setting-up-a-pull-client-using-configuration-id"></a><span data-ttu-id="d7990-103">Installera en pull-klient med hjälp av konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="d7990-103">Setting up a pull client using configuration ID</span></span>

> <span data-ttu-id="d7990-104">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d7990-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="d7990-105">Varje målnoden måste vara ett meddelande om att använda pull-läge och de angivna URL: en där den kontaktar pull-servern för att hämta konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="d7990-105">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span> <span data-ttu-id="d7990-106">Du måste konfigurera lokala Configuration Manager (MGM) med informationen som behövs för att göra detta.</span><span class="sxs-lookup"><span data-stu-id="d7990-106">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="d7990-107">Om du vill konfigurera MGM om du skapar en särskild typ av konfiguration, med den **DSCLocalConfigurationManager** attribut.</span><span class="sxs-lookup"><span data-stu-id="d7990-107">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="d7990-108">Mer information om hur du konfigurerar MGM finns [konfigurera den lokala Configuration Manager](metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="d7990-108">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

> <span data-ttu-id="d7990-109">**Obs**: det här avsnittet gäller PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="d7990-109">**Note**: This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="d7990-110">Information om hur du skapar en pull-klient i PowerShell 4.0 finns [installera en pull-klient med hjälp av konfigurations-ID i PowerShell 4.0](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="d7990-110">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

<span data-ttu-id="d7990-111">Följande skript konfigurerar MGM pull konfigurationer från en server med namnet ”CONTOSO-PullSrv”.</span><span class="sxs-lookup"><span data-stu-id="d7990-111">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

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

<span data-ttu-id="d7990-112">I skriptet på **ConfigurationRepositoryWeb** block definierar pull-servern.</span><span class="sxs-lookup"><span data-stu-id="d7990-112">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="d7990-113">Den **ServerURL**</span><span class="sxs-lookup"><span data-stu-id="d7990-113">The **ServerURL**</span></span>

<span data-ttu-id="d7990-114">När skriptet körs, skapas en ny utdatamapp med namnet **PullClientConfigID** och det placerar en metakonfigurationen MOF-fil.</span><span class="sxs-lookup"><span data-stu-id="d7990-114">After this script runs, it creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="d7990-115">I det här fallet metakonfigurationen MOF-filen får namnet `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="d7990-115">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="d7990-116">Om du vill tillämpa konfigurationen genom att anropa den **Set DscLocalConfigurationManager** cmdlet, med den **sökväg** inställd på platsen för metakonfigurationen MOF-filen.</span><span class="sxs-lookup"><span data-stu-id="d7990-116">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="d7990-117">Exempelvis: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`</span><span class="sxs-lookup"><span data-stu-id="d7990-117">For example: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`</span></span>

## <a name="configuration-id"></a><span data-ttu-id="d7990-118">Konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="d7990-118">Configuration ID</span></span>

<span data-ttu-id="d7990-119">Script-anger den **ConfigurationID** -egenskapen för MGM till ett GUID som tidigare hade skapats för detta ändamål (du kan skapa ett GUID med hjälp av den **ny Guid** cmdlet).</span><span class="sxs-lookup"><span data-stu-id="d7990-119">The script sets the **ConfigurationID** property of LCM to a GUID that had been previously created for this purpose (you can create a GUID by using the **New-Guid** cmdlet).</span></span> <span data-ttu-id="d7990-120">Den **ConfigurationID** är vad MGM om du använder för att hitta rätt konfiguration på hämtningsservern.</span><span class="sxs-lookup"><span data-stu-id="d7990-120">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="d7990-121">Konfigurationen MOF-filen på hämtningsservern måste ha namnet _ConfigurationID_MOF, där _ConfigurationID_ är värdet för den **ConfigurationID** -egenskapen för målet nodens MGM.</span><span class="sxs-lookup"><span data-stu-id="d7990-121">The configuration MOF file on the pull server must be named _ConfigurationID_.mof, where _ConfigurationID_ is the value of the **ConfigurationID** property of the target node's LCM.</span></span>

## <a name="smb-pull-server"></a><span data-ttu-id="d7990-122">SMB pull-servern</span><span class="sxs-lookup"><span data-stu-id="d7990-122">SMB pull server</span></span>

<span data-ttu-id="d7990-123">Om du vill konfigurera en klient till pull konfigurationer från en SMB-server, använder en **ConfigurationRepositoryShare** block.</span><span class="sxs-lookup"><span data-stu-id="d7990-123">To set up a client to pull configurations from an SMB server, use a **ConfigurationRepositoryShare** block.</span></span> <span data-ttu-id="d7990-124">I en **ConfigurationRepositoryShare** block du ange sökvägen till servern genom att ange den **SourcePath** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="d7990-124">In a **ConfigurationRepositoryShare** block, you specify the path to the server by setting the **SourcePath** property.</span></span> <span data-ttu-id="d7990-125">Följande metakonfigurationen konfigurerar målnoden ska ta emot från en SMB-pull-server med namnet **SMBPullServer**.</span><span class="sxs-lookup"><span data-stu-id="d7990-125">The following metaconfiguration configures the target node to pull from an SMB pull server named **SMBPullServer**.</span></span>

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
            SourcePath = '\\SMBPullServer\PullSource'
            
        }     
    }
}
PullClientConfigID
```

## <a name="resource-and-report-servers"></a><span data-ttu-id="d7990-126">Resurs- och -servrar</span><span class="sxs-lookup"><span data-stu-id="d7990-126">Resource and report servers</span></span>

<span data-ttu-id="d7990-127">Om du bara anger en **ConfigurationRepositoryWeb** eller **ConfigurationRepositoryShare** blockera i konfigurationen MGM (som i föregående exempel), pull-klienten hämtar resurser från den angiven server, men det kommer inte skicka rapporter till den.</span><span class="sxs-lookup"><span data-stu-id="d7990-127">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from the specified server, but it will not send reports to it.</span></span> <span data-ttu-id="d7990-128">Du kan använda en enda hämtningsservern för konfigurationer, resurser och rapportering, men du måste skapa en **ReportRepositoryWeb** block att konfigurera rapportering.</span><span class="sxs-lookup"><span data-stu-id="d7990-128">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span> 

<span data-ttu-id="d7990-129">I följande exempel visas en metakonfigurationen som ställer in en klient till pull konfigurationer och resurser och skicka rapportdata till en enda pull-server.</span><span class="sxs-lookup"><span data-stu-id="d7990-129">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

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

<span data-ttu-id="d7990-130">Du kan också ange olika pull-servrar för resurser och rapportering.</span><span class="sxs-lookup"><span data-stu-id="d7990-130">You can also specify different pull servers for resources and reporting.</span></span> <span data-ttu-id="d7990-131">Om du vill ange en resurs-server du använder antingen en **ResourceRepositoryWeb** (för en webbserver pull) eller en **ResourceRepositoryShare** block (för en SMB-pull-server).</span><span class="sxs-lookup"><span data-stu-id="d7990-131">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>
<span data-ttu-id="d7990-132">Om du vill ange en rapportserver som du använder en **ReportRepositoryWeb** block.</span><span class="sxs-lookup"><span data-stu-id="d7990-132">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="d7990-133">En rapportserver får inte vara en SMB-server.</span><span class="sxs-lookup"><span data-stu-id="d7990-133">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="d7990-134">Följande metakonfigurationen konfigurerar en pull-klient för att få sina konfigurationer från **CONTOSO PullSrv** och dess resurser från **CONTOSO ResourceSrv**, och för att skicka statusrapporter till  **CONTOSO-ReportSrv**:</span><span class="sxs-lookup"><span data-stu-id="d7990-134">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d7990-135">Se även</span><span class="sxs-lookup"><span data-stu-id="d7990-135">See Also</span></span>

* [<span data-ttu-id="d7990-136">Installera en pull-klient med konfigurationsnamn</span><span class="sxs-lookup"><span data-stu-id="d7990-136">Setting up a pull client with configuration names</span></span>](pullClientConfigNames.md)

