---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "Installera en pull-klient med hjälp av konfigurations-ID i PowerShell 4.0"
ms.openlocfilehash: 19328018d276cddd0877869b0ec69c14c51e4b85
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="setting-up-a-pull-client-using-configuration-id-in-powershell-40"></a><span data-ttu-id="b0cdb-103">Installera en pull-klient med hjälp av konfigurations-ID i PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="b0cdb-103">Setting up a pull client using configuration ID in PowerShell 4.0</span></span>

><span data-ttu-id="b0cdb-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b0cdb-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="b0cdb-105">Varje målnoden måste vara ett meddelande om att använda pull-läge och de angivna URL: en där den kontaktar pull-servern för att hämta konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="b0cdb-105">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span> <span data-ttu-id="b0cdb-106">Du måste konfigurera lokala Configuration Manager (MGM) med informationen som behövs för att göra detta.</span><span class="sxs-lookup"><span data-stu-id="b0cdb-106">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="b0cdb-107">Om du vill konfigurera MGM om skapar du en särskild typ av konfiguration som kallas ”metakonfigurationen”.</span><span class="sxs-lookup"><span data-stu-id="b0cdb-107">To configure the LCM, you create a special type of configuration known as a "metaconfiguration".</span></span> <span data-ttu-id="b0cdb-108">Mer information om hur du konfigurerar MGM finns [Windows PowerShell 4.0 önskad tillstånd Configuration Local Configuration Manager](metaConfig4.md)</span><span class="sxs-lookup"><span data-stu-id="b0cdb-108">For more information about configuring the LCM, see [Windows PowerShell 4.0 Desired State Configuration Local Configuration Manager](metaConfig4.md)</span></span>

<span data-ttu-id="b0cdb-109">Följande skript konfigurerar MGM pull konfigurationer från en server med namnet ”PullServer”:</span><span class="sxs-lookup"><span data-stu-id="b0cdb-109">The following script configures the LCM to pull configurations from a server named "PullServer":</span></span>

```powershell
Configuration SimpleMetaConfigurationForPull 
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
SimpleMetaConfigurationForPull -Output "."
```

<span data-ttu-id="b0cdb-110">I skriptet **DownloadManagerCustomData** överför Webbadressen för pull-servern och (för det här exemplet) kan en osäker anslutning.</span><span class="sxs-lookup"><span data-stu-id="b0cdb-110">In the script, **DownloadManagerCustomData** passes the URL of the pull server and (for this example) allows an unsecured connection.</span></span> 

<span data-ttu-id="b0cdb-111">När skriptet körs, skapas en ny utdatamapp kallas **SimpleMetaConfigurationForPull** och det placerar en metakonfigurationen MOF-fil.</span><span class="sxs-lookup"><span data-stu-id="b0cdb-111">After this script runs, it creates a new output folder called **SimpleMetaConfigurationForPull** and puts a metaconfiguration MOF file there.</span></span>

<span data-ttu-id="b0cdb-112">Om du vill tillämpa konfigurationen genom att använda **Set DscLocalConfigurationManager** med parametrar för **ComputerName** (använda ”localhost”) och **sökväg** (sökvägen till platsen för den rikta nodens localhost.meta.mof-fil).</span><span class="sxs-lookup"><span data-stu-id="b0cdb-112">To apply the configuration, use **Set-DscLocalConfigurationManager** with parameters for **ComputerName** (use “localhost”) and **Path** (the path to the location of the target node’s localhost.meta.mof file).</span></span> <span data-ttu-id="b0cdb-113">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="b0cdb-113">For example:</span></span> 
```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path . –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="b0cdb-114">Konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="b0cdb-114">Configuration ID</span></span>
<span data-ttu-id="b0cdb-115">Script-anger den **ConfigurationID** -egenskapen för MGM till ett GUID som tidigare hade skapats för detta ändamål (du kan skapa ett GUID med hjälp av den **ny Guid** cmdlet).</span><span class="sxs-lookup"><span data-stu-id="b0cdb-115">The script sets the **ConfigurationID** property of the LCM to a GUID that had been previously created for this purpose (you can create a GUID by using the **New-Guid** cmdlet).</span></span> <span data-ttu-id="b0cdb-116">Den **ConfigurationID** är vad MGM om du använder för att hitta rätt konfiguration på hämtningsservern.</span><span class="sxs-lookup"><span data-stu-id="b0cdb-116">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="b0cdb-117">Konfigurationen MOF-filen på hämtningsservern måste ha namnet `ConfigurationID.mof`, där *ConfigurationID* är värdet för den **ConfigurationID** -egenskapen för nodens target MGM.</span><span class="sxs-lookup"><span data-stu-id="b0cdb-117">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span>

## <a name="pulling-from-an-smb-server"></a><span data-ttu-id="b0cdb-118">Dra från en SMB-server</span><span class="sxs-lookup"><span data-stu-id="b0cdb-118">Pulling from an SMB server</span></span>

<span data-ttu-id="b0cdb-119">Om den pull-servern har konfigurerats som en SMB-filresursen i stället för en webbtjänst, anger du den **DscFileDownloadManager** snarare än den **WebDownLoadManager**.</span><span class="sxs-lookup"><span data-stu-id="b0cdb-119">If the pull server is set up as an SMB file share, rather than a web service, you specify the **DscFileDownloadManager** rather than the **WebDownLoadManager**.</span></span>
<span data-ttu-id="b0cdb-120">Den **DscFileDownloadManager** tar en **SourcePath** egenskapen i stället för **ServerUrl**.</span><span class="sxs-lookup"><span data-stu-id="b0cdb-120">The **DscFileDownloadManager** takes a **SourcePath** property instead of **ServerUrl**.</span></span> <span data-ttu-id="b0cdb-121">Följande skript konfigurerar MGM om du vill dra konfigurationer från en SMB-resurs med namnet ”SmbDscShare” på en server med namnet ”CONTOSO-SERVER”:</span><span class="sxs-lookup"><span data-stu-id="b0cdb-121">The following script configures the LCM to pull configurations from an SMB share named "SmbDscShare" on a server named "CONTOSO-SERVER":</span></span>

```powershell
Configuration SimpleMetaConfigurationForPull 
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
SimpleMetaConfigurationForPull -Output "."
```

## <a name="see-also"></a><span data-ttu-id="b0cdb-122">Se även</span><span class="sxs-lookup"><span data-stu-id="b0cdb-122">See Also</span></span>

- [<span data-ttu-id="b0cdb-123">Ställer in en pull webbserver DSC</span><span class="sxs-lookup"><span data-stu-id="b0cdb-123">Setting up a DSC web pull server</span></span>](pullServer.md)
- [<span data-ttu-id="b0cdb-124">Ställer in en DSC SMB pull-server</span><span class="sxs-lookup"><span data-stu-id="b0cdb-124">Setting up a DSC SMB pull server</span></span>](pullServerSMB.md)

