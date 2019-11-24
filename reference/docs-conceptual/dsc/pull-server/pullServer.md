---
ms.date: 03/04/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC-hämtningstjänsten
ms.openlocfilehash: 865eae5813e0c7b656a4158f0b1350e60f1e3291
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942771"
---
# <a name="desired-state-configuration-pull-service"></a><span data-ttu-id="326c9-103">Mottagar tjänst för önskad tillstånds konfiguration</span><span class="sxs-lookup"><span data-stu-id="326c9-103">Desired State Configuration Pull Service</span></span>

> [!IMPORTANT]
> <span data-ttu-id="326c9-104">Hämtnings servern (Windows Feature *DSC-tjänst*) är en komponent som stöds av Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner.</span><span class="sxs-lookup"><span data-stu-id="326c9-104">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="326c9-105">Vi rekommenderar att du börjar överföra hanterade klienter till [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inklusive funktioner utöver hämtnings servern på Windows Server) eller någon av de community-lösningar som anges [här](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="326c9-105">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="326c9-106">Lokala Configuration Manager kan hanteras centralt av en pull service-lösning.</span><span class="sxs-lookup"><span data-stu-id="326c9-106">Local Configuration Manager can be centrally managed by a Pull Service solution.</span></span>
<span data-ttu-id="326c9-107">När du använder den här metoden registreras noden som hanteras med en tjänst och tilldelas en konfiguration i LCM-inställningar.</span><span class="sxs-lookup"><span data-stu-id="326c9-107">When using this approach, the node that is being managed is registered with a service and assigned a configuration in LCM settings.</span></span>
<span data-ttu-id="326c9-108">Konfigurationen och alla DSC-resurser som krävs som beroenden för konfigurationen laddas ned till datorn och används av LCM för att hantera konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="326c9-108">The configuration and all DSC resources needed as dependencies for the configuration are downloaded to the machine and used by LCM to manage the configuration.</span></span>
<span data-ttu-id="326c9-109">Information om statusen för den dator som hanteras överförs till tjänsten för rapportering.</span><span class="sxs-lookup"><span data-stu-id="326c9-109">Information about the state of the machine being managed is uploaded to the service for reporting.</span></span>
<span data-ttu-id="326c9-110">Det här begreppet kallas för pull-tjänst.</span><span class="sxs-lookup"><span data-stu-id="326c9-110">This concept is referred to as "pull service."</span></span>

<span data-ttu-id="326c9-111">De aktuella alternativen för pull service är:</span><span class="sxs-lookup"><span data-stu-id="326c9-111">The current options for pull service include:</span></span>

- <span data-ttu-id="326c9-112">Azure Automation tjänst för önskad tillstånds konfiguration</span><span class="sxs-lookup"><span data-stu-id="326c9-112">Azure Automation Desired State Configuration service</span></span>
- <span data-ttu-id="326c9-113">En pull-tjänst som körs på Windows Server</span><span class="sxs-lookup"><span data-stu-id="326c9-113">A pull service running on Windows Server</span></span>
- <span data-ttu-id="326c9-114">Community-underhållna lösningar med öppen källkod</span><span class="sxs-lookup"><span data-stu-id="326c9-114">Community maintained open-source solutions</span></span>
- <span data-ttu-id="326c9-115">En SMB-resurs</span><span class="sxs-lookup"><span data-stu-id="326c9-115">An SMB share</span></span>

<span data-ttu-id="326c9-116">**Den rekommenderade lösningen**och alternativet med de mest tillgängliga funktionerna är [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="326c9-116">**The recommended solution**, and the option with the most features available, is [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

<span data-ttu-id="326c9-117">Azure-tjänsten kan hantera noder lokalt i privata data Center eller i offentliga moln, till exempel Azure och AWS.</span><span class="sxs-lookup"><span data-stu-id="326c9-117">The Azure service can manage nodes on-premises in private datacenters, or in public clouds such as Azure and AWS.</span></span>
<span data-ttu-id="326c9-118">För privata miljöer där servrar inte kan ansluta direkt till Internet bör du överväga att begränsa utgående trafik till endast det publicerade Azure IP-intervallet (se [Azure datacenter IP-intervall](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span><span class="sxs-lookup"><span data-stu-id="326c9-118">For private environments where servers cannot directly connect to the Internet, consider limiting outbound traffic to only the published Azure IP range (see [Azure Datacenter IP Ranges](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span></span>

<span data-ttu-id="326c9-119">Funktioner i online tjänsten som inte är tillgängliga i pull-tjänsten på Windows Server inkluderar:</span><span class="sxs-lookup"><span data-stu-id="326c9-119">Features of the online service that are not currently available in the pull service on Windows Server include:</span></span>

- <span data-ttu-id="326c9-120">Alla data krypteras under överföring och i vila</span><span class="sxs-lookup"><span data-stu-id="326c9-120">All data is encrypted in transit and at rest</span></span>
- <span data-ttu-id="326c9-121">Klient certifikat skapas och hanteras automatiskt</span><span class="sxs-lookup"><span data-stu-id="326c9-121">Client certificates are created and managed automatically</span></span>
- <span data-ttu-id="326c9-122">Hemligheter för central hantering av [lösen ord/autentiseringsuppgifter](/azure/automation/automation-credentials), eller [variabler](/azure/automation/automation-variables) som server namn eller anslutnings strängar</span><span class="sxs-lookup"><span data-stu-id="326c9-122">Secrets store for centrally managing [passwords/credentials](/azure/automation/automation-credentials), or [variables](/azure/automation/automation-variables) such as server names or connection strings</span></span>
- <span data-ttu-id="326c9-123">Centralt hantera [konfiguration av LCM](../managing-nodes/metaConfig.md#basic-settings) -noden</span><span class="sxs-lookup"><span data-stu-id="326c9-123">Centrally manage node [LCM configuration](../managing-nodes/metaConfig.md#basic-settings)</span></span>
- <span data-ttu-id="326c9-124">Centralt tilldela konfigurationer till klient-noder</span><span class="sxs-lookup"><span data-stu-id="326c9-124">Centrally assign configurations to client nodes</span></span>
- <span data-ttu-id="326c9-125">Frisläpp konfigurations ändringar till "Kanarie Groups" för testning innan du når produktion</span><span class="sxs-lookup"><span data-stu-id="326c9-125">Release configuration changes to "canary groups" for testing before reaching production</span></span>
- <span data-ttu-id="326c9-126">Grafisk rapportering</span><span class="sxs-lookup"><span data-stu-id="326c9-126">Graphical reporting</span></span>
  - <span data-ttu-id="326c9-127">Statusinformation på DSC-resursens nivå för granularitet</span><span class="sxs-lookup"><span data-stu-id="326c9-127">Status detail at the DSC resource level of granularity</span></span>
  - <span data-ttu-id="326c9-128">Utförliga fel meddelanden från klient datorer för fel sökning</span><span class="sxs-lookup"><span data-stu-id="326c9-128">Verbose error messages from client machines for troubleshooting</span></span>
- <span data-ttu-id="326c9-129">[Integrering med Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) för aviseringar, automatiserade uppgifter, Android/iOS-app för rapportering och aviseringar</span><span class="sxs-lookup"><span data-stu-id="326c9-129">[Integration with Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) for alerting, automated tasks, Android/iOS app for reporting and alerting</span></span>

## <a name="dsc-pull-service-in-windows-server"></a><span data-ttu-id="326c9-130">DSC-pull-tjänst i Windows Server</span><span class="sxs-lookup"><span data-stu-id="326c9-130">DSC pull service in Windows Server</span></span>

<span data-ttu-id="326c9-131">Det är möjligt att konfigurera en pull-tjänst för att köras på Windows Server.</span><span class="sxs-lookup"><span data-stu-id="326c9-131">It is possible to configure a pull service to run on Windows Server.</span></span>
<span data-ttu-id="326c9-132">Vi rekommenderar att lösningen för pull-tjänster som ingår i Windows Server bara innehåller funktioner för att lagra konfigurationer/moduler för att hämta och samla in rapport data i till-databasen.</span><span class="sxs-lookup"><span data-stu-id="326c9-132">Be advised that the pull service solution included in Windows Server includes only capabilities of storing configurations/modules for download and capturing report data in to database.</span></span>
<span data-ttu-id="326c9-133">Det innehåller inte många av de funktioner som erbjuds av tjänsten i Azure och det är inte ett användbart verktyg för att utvärdera hur tjänsten används.</span><span class="sxs-lookup"><span data-stu-id="326c9-133">It does not include many of the capabilities offered by the service in Azure and so is not a good tool for evaluating how the service would be used.</span></span>

<span data-ttu-id="326c9-134">Pull-tjänsten som erbjuds i Windows Server är en webb tjänst i IIS som använder ett OData-gränssnitt för att göra DSC-konfigurationsfiler tillgängliga för mål noder när noderna begär det.</span><span class="sxs-lookup"><span data-stu-id="326c9-134">The pull service offered in Windows Server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="326c9-135">Krav för att använda en hämtnings Server:</span><span class="sxs-lookup"><span data-stu-id="326c9-135">Requirements for using a pull server:</span></span>

- <span data-ttu-id="326c9-136">En server som kör:</span><span class="sxs-lookup"><span data-stu-id="326c9-136">A server running:</span></span>
  - <span data-ttu-id="326c9-137">WMF/PowerShell 4,0 eller senare</span><span class="sxs-lookup"><span data-stu-id="326c9-137">WMF/PowerShell 4.0 or greater</span></span>
  - <span data-ttu-id="326c9-138">IIS-serverrollen</span><span class="sxs-lookup"><span data-stu-id="326c9-138">IIS server role</span></span>
  - <span data-ttu-id="326c9-139">DSC-tjänst</span><span class="sxs-lookup"><span data-stu-id="326c9-139">DSC Service</span></span>
- <span data-ttu-id="326c9-140">Det bästa är att skapa ett certifikat för att skydda autentiseringsuppgifter som skickas till den lokala Configuration Manager (LCM) på målnoden</span><span class="sxs-lookup"><span data-stu-id="326c9-140">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="326c9-141">Det bästa sättet att konfigurera Windows Server som värd för pull-tjänst är att använda en DSC-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="326c9-141">The best way to configure Windows Server to host pull service is to use a DSC configuration.</span></span>
<span data-ttu-id="326c9-142">Ett exempel skript anges nedan.</span><span class="sxs-lookup"><span data-stu-id="326c9-142">An example script is provided below.</span></span>

### <a name="supported-database-systems"></a><span data-ttu-id="326c9-143">Databas system som stöds</span><span class="sxs-lookup"><span data-stu-id="326c9-143">Supported database systems</span></span>

|<span data-ttu-id="326c9-144">WMF 4,0</span><span class="sxs-lookup"><span data-stu-id="326c9-144">WMF 4.0</span></span>   |<span data-ttu-id="326c9-145">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="326c9-145">WMF 5.0</span></span>  |<span data-ttu-id="326c9-146">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="326c9-146">WMF 5.1</span></span> |<span data-ttu-id="326c9-147">WMF 5,1 (Windows Server Insider Preview 17090)</span><span class="sxs-lookup"><span data-stu-id="326c9-147">WMF 5.1 (Windows Server Insider Preview 17090)</span></span>|
|---------|---------|---------|---------|
|<span data-ttu-id="326c9-148">MDB</span><span class="sxs-lookup"><span data-stu-id="326c9-148">MDB</span></span>     |<span data-ttu-id="326c9-149">ESENT (standard), MDB</span><span class="sxs-lookup"><span data-stu-id="326c9-149">ESENT (Default), MDB</span></span> |<span data-ttu-id="326c9-150">ESENT (standard), MDB</span><span class="sxs-lookup"><span data-stu-id="326c9-150">ESENT (Default), MDB</span></span>|<span data-ttu-id="326c9-151">ESENT (standard), SQL Server, MDB</span><span class="sxs-lookup"><span data-stu-id="326c9-151">ESENT (Default), SQL Server, MDB</span></span>

<span data-ttu-id="326c9-152">Från och med version 17090 av [Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver)är SQL Server ett alternativ som stöds för pull-tjänsten (Windows Feature *DSC-service*).</span><span class="sxs-lookup"><span data-stu-id="326c9-152">Starting in release 17090 of [Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), SQL Server is a supported option for the Pull Service (Windows Feature *DSC-Service*).</span></span> <span data-ttu-id="326c9-153">Detta ger ett nytt alternativ för skalning av stora DSC-miljöer som inte har migrerats till [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="326c9-153">This provides a new option for scaling large DSC environments that have not migrated to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

> [!NOTE]
> <span data-ttu-id="326c9-154">SQL Server-stöd kommer inte att läggas till i tidigare versioner av WMF 5,1 (eller tidigare) och är bara tillgängliga på Windows Server-versioner som är större än eller lika med 17090.</span><span class="sxs-lookup"><span data-stu-id="326c9-154">SQL Server support will not be added to previous versions of WMF 5.1 (or earlier) and will only be available on Windows Server versions greater than or equal to 17090.</span></span>

<span data-ttu-id="326c9-155">Konfigurera hämtnings servern för att använda SQL Server genom att ange **SqlProvider** till `$true` och **SQLConnectionString** till en giltig SQL Server anslutnings sträng.</span><span class="sxs-lookup"><span data-stu-id="326c9-155">To configure the pull server to use SQL Server, set **SqlProvider** to `$true` and **SqlConnectionString** to a valid SQL Server Connection String.</span></span> <span data-ttu-id="326c9-156">Mer information finns i [anslutnings strängar för SqlClient](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span><span class="sxs-lookup"><span data-stu-id="326c9-156">For more information, see [SqlClient Connection Strings](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span></span>
<span data-ttu-id="326c9-157">Ett exempel på SQL Server konfiguration med **xDscWebService**får du först läsa [med xDscWebService-resursen](#using-the-xdscwebservice-resource) och sedan granska [Sample_xDscWebServiceRegistration_UseSQLProvider. ps1 på GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span><span class="sxs-lookup"><span data-stu-id="326c9-157">For an example of SQL Server configuration with **xDscWebService**, first read [Using the xDscWebService resource](#using-the-xdscwebservice-resource) and then review [Sample_xDscWebServiceRegistration_UseSQLProvider.ps1 on GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span></span>

### <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="326c9-158">Använda xDscWebService-resursen</span><span class="sxs-lookup"><span data-stu-id="326c9-158">Using the xDscWebService resource</span></span>

<span data-ttu-id="326c9-159">Det enklaste sättet att konfigurera en webb hämtnings Server är att använda **xDscWebService** -resursen, som ingår i **xPSDesiredStateConfiguration** -modulen.</span><span class="sxs-lookup"><span data-stu-id="326c9-159">The easiest way to set up a web pull server is to use the **xDscWebService** resource, included in the **xPSDesiredStateConfiguration** module.</span></span>
<span data-ttu-id="326c9-160">Följande steg beskriver hur du använder resursen i en konfiguration som konfigurerar webb tjänsten.</span><span class="sxs-lookup"><span data-stu-id="326c9-160">The following steps explain how to use the resource in a configuration that sets up the web service.</span></span>

1. <span data-ttu-id="326c9-161">Anropa cmdleten [install-module](/powershell/module/PowershellGet/Install-Module) för att installera **xPSDesiredStateConfiguration** -modulen.</span><span class="sxs-lookup"><span data-stu-id="326c9-161">Call the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span>
   > [!NOTE]
   > <span data-ttu-id="326c9-162">**Install-module** ingår i **PowerShellGet** -modulen, som ingår i PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="326c9-162">**Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="326c9-163">Du kan hämta **PowerShellGet** -modulen för för hands versionen av PowerShell 3,0 och 4,0 i [PackageManagement PowerShell-moduler](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="326c9-163">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>
2. <span data-ttu-id="326c9-164">Hämta ett SSL-certifikat för DSC-pull-servern från en betrodd certifikat utfärdare, antingen inom organisationen eller en offentlig myndighet.</span><span class="sxs-lookup"><span data-stu-id="326c9-164">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="326c9-165">Certifikatet som togs emot från utfärdaren är vanligt vis i PFX-format.</span><span class="sxs-lookup"><span data-stu-id="326c9-165">The certificate received from the authority is usually in the PFX format.</span></span>
3. <span data-ttu-id="326c9-166">Installera certifikatet på den nod som ska bli DSC-pull-server på standard platsen, vilket ska vara `CERT:\LocalMachine\My`.</span><span class="sxs-lookup"><span data-stu-id="326c9-166">Install the certificate on the node that will become the DSC Pull server in the default location, which should be `CERT:\LocalMachine\My`.</span></span>
   - <span data-ttu-id="326c9-167">Anteckna tumavtryck för certifikatet.</span><span class="sxs-lookup"><span data-stu-id="326c9-167">Make a note of the certificate thumbprint.</span></span>
4. <span data-ttu-id="326c9-168">Välj en GUID som ska användas som registrerings nyckel.</span><span class="sxs-lookup"><span data-stu-id="326c9-168">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="326c9-169">Om du vill generera en med PowerShell anger du följande vid PS-prompten och trycker på RETUR: `[guid]::newGuid()` eller `New-Guid`.</span><span class="sxs-lookup"><span data-stu-id="326c9-169">To generate one using PowerShell enter the following at the PS prompt and press enter: `[guid]::newGuid()` or `New-Guid`.</span></span> <span data-ttu-id="326c9-170">Den här nyckeln används av-klient noder som en delad nyckel för att autentisera vid registreringen.</span><span class="sxs-lookup"><span data-stu-id="326c9-170">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="326c9-171">Mer information finns i avsnittet registrerings nyckel nedan.</span><span class="sxs-lookup"><span data-stu-id="326c9-171">For more information, see the Registration Key section below.</span></span>
5. <span data-ttu-id="326c9-172">Starta (F5) följande konfigurations skript i PowerShell ISE (ingår i mappen exempel i **xPSDesiredStateConfiguration** -modulen som `Sample_xDscWebServiceRegistration.ps1`).</span><span class="sxs-lookup"><span data-stu-id="326c9-172">In the PowerShell ISE, start (F5) the following configuration script (included in the Examples folder of the **xPSDesiredStateConfiguration** module as `Sample_xDscWebServiceRegistration.ps1`).</span></span> <span data-ttu-id="326c9-173">Det här skriptet konfigurerar hämtnings servern.</span><span class="sxs-lookup"><span data-stu-id="326c9-173">This script sets up the pull server.</span></span>

    ```powershell
    configuration Sample_xDscWebServiceRegistration
    {
        param
        (
            [string[]]$NodeName = 'localhost',

            [ValidateNotNullOrEmpty()]
            [string] $certificateThumbPrint,

            [Parameter(HelpMessage='This should be a string with enough entropy (randomness) to protect the registration of clients to the pull server.  We will use new GUID by default.')]
            [ValidateNotNullOrEmpty()]
            [string] $RegistrationKey   # A guid that clients use to initiate conversation with pull server
        )

        Import-DSCResource -ModuleName PSDesiredStateConfiguration
        Import-DSCResource -ModuleName xPSDesiredStateConfiguration

        Node $NodeName
        {
            WindowsFeature DSCServiceFeature
            {
                Ensure = "Present"
                Name   = "DSC-Service"
            }

            xDscWebService PSDSCPullServer
            {
                Ensure                  = "Present"
                EndpointName            = "PSDSCPullServer"
                Port                    = 8080
                PhysicalPath            = "$env:SystemDrive\inetpub\PSDSCPullServer"
                CertificateThumbPrint   = $certificateThumbPrint
                ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
                ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
                State                   = "Started"
                DependsOn               = "[WindowsFeature]DSCServiceFeature"
                RegistrationKeyPath     = "$env:PROGRAMFILES\WindowsPowerShell\DscService"
                AcceptSelfSignedCertificates = $true
                UseSecurityBestPractices     = $true
                Enable32BitAppOnWin64   = $false
            }

            File RegistrationKeyFile
            {
                Ensure          = 'Present'
                Type            = 'File'
                DestinationPath = "$env:ProgramFiles\WindowsPowerShell\DscService\RegistrationKeys.txt"
                Contents        = $RegistrationKey
            }
        }
    }
    ```

6. <span data-ttu-id="326c9-174">Kör konfigurationen och skicka tumavtrycket för SSL-certifikatet som parametern **certificateThumbPrint** och en GUID-registrerings nyckel som parametern **RegistrationKey** :</span><span class="sxs-lookup"><span data-stu-id="326c9-174">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDscWebServiceRegistration -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

#### <a name="registration-key"></a><span data-ttu-id="326c9-175">Registrerings nyckel</span><span class="sxs-lookup"><span data-stu-id="326c9-175">Registration Key</span></span>

<span data-ttu-id="326c9-176">Om du vill tillåta att klusternoder registreras på servern så att de kan använda konfigurations namn i stället för ett konfigurations-ID, sparas en registrerings nyckel som skapades av konfigurationen ovan i en fil med namnet `RegistrationKeys.txt` i `C:\Program Files\WindowsPowerShell\DscService`.</span><span class="sxs-lookup"><span data-stu-id="326c9-176">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key that was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="326c9-177">Registrerings nyckeln fungerar som en delad hemlighet som används under den inledande registreringen av klienten med hämtnings servern.</span><span class="sxs-lookup"><span data-stu-id="326c9-177">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="326c9-178">Klienten genererar ett självsignerat certifikat som används för att autentisera till pull-servern när registreringen är slutförd.</span><span class="sxs-lookup"><span data-stu-id="326c9-178">The client will generate a self-signed certificate that is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="326c9-179">Tumavtrycket för det här certifikatet lagras lokalt och associeras med URL: en för pull-servern.</span><span class="sxs-lookup"><span data-stu-id="326c9-179">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>

> [!NOTE]
> <span data-ttu-id="326c9-180">Registrerings nycklar stöds inte i PowerShell 4,0.</span><span class="sxs-lookup"><span data-stu-id="326c9-180">Registration keys are not supported in PowerShell 4.0.</span></span>

<span data-ttu-id="326c9-181">För att du ska kunna konfigurera en nod att autentisera med hämtnings servern måste registrerings nyckeln finnas i metaconfiguration för alla målnod som ska registreras med den här hämtnings servern.</span><span class="sxs-lookup"><span data-stu-id="326c9-181">In order to configure a node to authenticate with the pull server, the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="326c9-182">Observera att **RegistrationKey** i metaconfiguration nedan tas bort när mål datorn har registrerats och att värdet måste matcha det värde som lagras i `RegistrationKeys.txt`-filen på hämtnings servern (' 140a952b-b9d6-406b-b416-e0f759c9c0e4 ' för det här exemplet).</span><span class="sxs-lookup"><span data-stu-id="326c9-182">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value must match the value stored in the `RegistrationKeys.txt` file on the pull server ('140a952b-b9d6-406b-b416-e0f759c9c0e4' for this example).</span></span> <span data-ttu-id="326c9-183">Behandla alltid registrerings nyckel svärdet på ett säkert sätt, eftersom du vet att alla mål datorer kan registreras på hämtnings servern.</span><span class="sxs-lookup"><span data-stu-id="326c9-183">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration Sample_MetaConfigurationToRegisterWithLessSecurePullServer
{
    param
    (
        [ValidateNotNullOrEmpty()]
        [string] $NodeName = 'localhost',

        [ValidateNotNullOrEmpty()]
        [string] $RegistrationKey, #same as the one used to set up pull server in previous configuration

        [ValidateNotNullOrEmpty()]
        [string] $ServerName = 'localhost' #node name of the pull server, same as $NodeName used in previous configuration
    )

    Node $NodeName
    {
        Settings
        {
            RefreshMode        = 'Pull'
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey    = $RegistrationKey
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL       = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey = $RegistrationKey
        }
    }
}

Sample_MetaConfigurationToRegisterWithLessSecurePullServer -RegistrationKey $RegistrationKey -OutputPath c:\Configs\TargetNodes
```

> [!NOTE]
> <span data-ttu-id="326c9-184">I avsnittet **ReportServerWeb** kan du skicka rapporterings data till hämtnings servern.</span><span class="sxs-lookup"><span data-stu-id="326c9-184">The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span>

<span data-ttu-id="326c9-185">Avsaknad av egenskapen **ConfigurationID** i metaconfiguration-filen innebär implicit att hämtnings servern har stöd för v2-versionen av protokollet för pull-server, så att en inledande registrering krävs.</span><span class="sxs-lookup"><span data-stu-id="326c9-185">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span>
<span data-ttu-id="326c9-186">Förekomsten av en **ConfigurationID** innebär däremot att v1-versionen av pull server-protokollet används och att det inte finns någon registrerings bearbetning.</span><span class="sxs-lookup"><span data-stu-id="326c9-186">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

> [!NOTE]
> <span data-ttu-id="326c9-187">I ett PUSH-scenario finns en bugg i den aktuella versionen som gör det nödvändigt att definiera en ConfigurationID-egenskap i metaconfiguration-filen för noder som aldrig har registrerats med en pull-server.</span><span class="sxs-lookup"><span data-stu-id="326c9-187">In a PUSH scenario, a bug exists in the current release that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="326c9-188">Detta tvingar v1 pull server-protokollet och undvika meddelanden om registrerings fel.</span><span class="sxs-lookup"><span data-stu-id="326c9-188">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="326c9-189">Placera konfigurationer och resurser</span><span class="sxs-lookup"><span data-stu-id="326c9-189">Placing configurations and resources</span></span>

<span data-ttu-id="326c9-190">När installationen av hämtnings servern är klar är mapparna som definieras av egenskaperna **ConfigurationPath** och **ModulePath** i hämtnings Server konfigurationen där du kommer att placera moduler och konfigurationer som är tillgängliga för målnoden att hämta.</span><span class="sxs-lookup"><span data-stu-id="326c9-190">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span>
<span data-ttu-id="326c9-191">Filerna måste vara i ett särskilt format för att hämtnings servern ska kunna bearbeta dem på rätt sätt.</span><span class="sxs-lookup"><span data-stu-id="326c9-191">These files need to be in a specific format in order for the pull server to correctly process them.</span></span>

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="326c9-192">Paket format för DSC-resurs</span><span class="sxs-lookup"><span data-stu-id="326c9-192">DSC resource module package format</span></span>

<span data-ttu-id="326c9-193">Varje resurs-modul måste vara zippad och namngiven enligt följande mönster `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="326c9-193">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span>

<span data-ttu-id="326c9-194">Till exempel skulle en modul med namnet xWebAdminstration med en modul version av 3.1.2.0 heta `xWebAdministration_3.1.2.0.zip`.</span><span class="sxs-lookup"><span data-stu-id="326c9-194">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named `xWebAdministration_3.1.2.0.zip`.</span></span>
<span data-ttu-id="326c9-195">Varje version av en modul måste finnas i en enda zip-fil.</span><span class="sxs-lookup"><span data-stu-id="326c9-195">Each version of a module must be contained in a single zip file.</span></span>
<span data-ttu-id="326c9-196">Eftersom det bara finns en enda version av en resurs i varje zip-fil stöds inte modulfönstret som lagts till i WMF 5,0 med stöd för flera versioner i en enda katalog.</span><span class="sxs-lookup"><span data-stu-id="326c9-196">Since there is only a single version of a resource in each zip file, the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span>
<span data-ttu-id="326c9-197">Det innebär att innan du packar upp DSC-resurspooler för användning med pull-server måste du göra en liten ändring i katalog strukturen.</span><span class="sxs-lookup"><span data-stu-id="326c9-197">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span>
<span data-ttu-id="326c9-198">Standardformat för moduler som innehåller DSC-resurs i WMF 5,0 är `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="326c9-198">The default format of modules containing DSC resource in WMF 5.0 is `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span></span>
<span data-ttu-id="326c9-199">Innan du packar upp för hämtnings servern tar du bort mappen **{module version}** så att sökvägen blir `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="326c9-199">Before packaging up for the pull server, remove the **{Module version}** folder so the path becomes `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span></span>
<span data-ttu-id="326c9-200">Med den här ändringen zip-mappen enligt beskrivningen ovan och placera dessa zip-filer i mappen **ModulePath** .</span><span class="sxs-lookup"><span data-stu-id="326c9-200">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="326c9-201">Använd `New-DscChecksum {module zip file}` för att skapa en kontroll Summa fil för den nyligen tillagda modulen.</span><span class="sxs-lookup"><span data-stu-id="326c9-201">Use `New-DscChecksum {module zip file}` to create a checksum file for the newly added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="326c9-202">MOF-format för konfiguration</span><span class="sxs-lookup"><span data-stu-id="326c9-202">Configuration MOF format</span></span>

<span data-ttu-id="326c9-203">En konfigurations-MOF-fil måste kombineras med en kontroll Summa fil så att en LCM på en målnod kan verifiera konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="326c9-203">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="326c9-204">Om du vill skapa en kontroll Summa anropar du cmdleten [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) .</span><span class="sxs-lookup"><span data-stu-id="326c9-204">To create a checksum, call the [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) cmdlet.</span></span>
<span data-ttu-id="326c9-205">Cmdlet: en använder en **Sök vägs** parameter som anger den mapp där MOF-konfigurationsfilen finns.</span><span class="sxs-lookup"><span data-stu-id="326c9-205">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span>
<span data-ttu-id="326c9-206">Cmdleten skapar en kontroll Summa fil med namnet `ConfigurationMOFName.mof.checksum`, där `ConfigurationMOFName` är namnet på MOF-konfigurationsfilen.</span><span class="sxs-lookup"><span data-stu-id="326c9-206">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="326c9-207">Om det finns fler än en konfigurations-MOF-fil i den angivna mappen skapas en kontroll summa för varje konfiguration i mappen.</span><span class="sxs-lookup"><span data-stu-id="326c9-207">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>
<span data-ttu-id="326c9-208">Placera MOF-filerna och deras associerade kontroll Summa filer i mappen **ConfigurationPath** .</span><span class="sxs-lookup"><span data-stu-id="326c9-208">Place the MOF files and their associated checksum files in the **ConfigurationPath** folder.</span></span>

> [!NOTE]
> <span data-ttu-id="326c9-209">Om du ändrar konfigurations-MOF-filen på valfritt sätt måste du också återskapa kontroll Summa filen.</span><span class="sxs-lookup"><span data-stu-id="326c9-209">If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

### <a name="tooling"></a><span data-ttu-id="326c9-210">Verktyg</span><span class="sxs-lookup"><span data-stu-id="326c9-210">Tooling</span></span>

<span data-ttu-id="326c9-211">Följande verktyg ingår som exempel i den senaste versionen av xPSDesiredStateConfiguration-modulen för att göra det enklare att konfigurera, verifiera och hantera hämtnings servern:</span><span class="sxs-lookup"><span data-stu-id="326c9-211">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>

1. <span data-ttu-id="326c9-212">En modul som hjälper till att paketera DSC-resurspooler och konfigurationsfiler för användning på hämtnings servern.</span><span class="sxs-lookup"><span data-stu-id="326c9-212">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span>
   <span data-ttu-id="326c9-213">[PublishModulesAndMofsToPullServer. psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span><span class="sxs-lookup"><span data-stu-id="326c9-213">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span></span>
   <span data-ttu-id="326c9-214">Exempel nedan:</span><span class="sxs-lookup"><span data-stu-id="326c9-214">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="326c9-215">Ett skript som verifierar hämtnings servern är korrekt konfigurerat.</span><span class="sxs-lookup"><span data-stu-id="326c9-215">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="326c9-216">[PullServerSetupTests. ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span><span class="sxs-lookup"><span data-stu-id="326c9-216">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span></span>

## <a name="community-solutions-for-pull-service"></a><span data-ttu-id="326c9-217">Community-lösningar för pull-tjänst</span><span class="sxs-lookup"><span data-stu-id="326c9-217">Community Solutions for Pull Service</span></span>

<span data-ttu-id="326c9-218">DSC-communityn har skapat flera lösningar för att implementera protokollet för pull-protokollet.</span><span class="sxs-lookup"><span data-stu-id="326c9-218">The DSC community has authored multiple solutions to implement the pull service protocol.</span></span>
<span data-ttu-id="326c9-219">För lokala miljöer erbjuder dessa funktioner för pull-tjänster och en möjlighet att bidra tillbaka till communityn med stegvisa förbättringar.</span><span class="sxs-lookup"><span data-stu-id="326c9-219">For on-premises environments, these offer pull service capabilities and an opportunity to contribute back to the community with incremental enhancements.</span></span>

- [<span data-ttu-id="326c9-220">Tug</span><span class="sxs-lookup"><span data-stu-id="326c9-220">Tug</span></span>](https://github.com/powershellorg/tug)
- [<span data-ttu-id="326c9-221">DSC – TRÆK</span><span class="sxs-lookup"><span data-stu-id="326c9-221">DSC-TRÆK</span></span>](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a><span data-ttu-id="326c9-222">Hämta klient konfiguration</span><span class="sxs-lookup"><span data-stu-id="326c9-222">Pull client configuration</span></span>

<span data-ttu-id="326c9-223">I följande avsnitt beskrivs hur du konfigurerar pull-klienter i detalj:</span><span class="sxs-lookup"><span data-stu-id="326c9-223">The following topics describe setting up pull clients in detail:</span></span>

- [<span data-ttu-id="326c9-224">Konfigurera en DSC-pull-klient med ett konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="326c9-224">Set up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
- [<span data-ttu-id="326c9-225">Konfigurera en DSC-pull-klient med hjälp av konfigurations namn</span><span class="sxs-lookup"><span data-stu-id="326c9-225">Set up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
- [<span data-ttu-id="326c9-226">Partiella konfigurationer</span><span class="sxs-lookup"><span data-stu-id="326c9-226">Partial configurations</span></span>](partialConfigs.md)

## <a name="see-also"></a><span data-ttu-id="326c9-227">Se också</span><span class="sxs-lookup"><span data-stu-id="326c9-227">See also</span></span>

- [<span data-ttu-id="326c9-228">Översikt över önskad tillstånds konfiguration i Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="326c9-228">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)
- [<span data-ttu-id="326c9-229">Tillämpa konfigurationer</span><span class="sxs-lookup"><span data-stu-id="326c9-229">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="326c9-230">Använd en DSC-rapportserver</span><span class="sxs-lookup"><span data-stu-id="326c9-230">Using a DSC report server</span></span>](reportServer.md)
- <span data-ttu-id="326c9-231">[[MS-DSCP]: protokoll för Desired State Configuration pull-modell](https://msdn.microsoft.com/library/dn393548.aspx)</span><span class="sxs-lookup"><span data-stu-id="326c9-231">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol](https://msdn.microsoft.com/library/dn393548.aspx)</span></span>
- <span data-ttu-id="326c9-232">[[MS-DSCP]: protokoll för önskad tillstånds konfiguration pull-errata](https://msdn.microsoft.com/library/mt612824.aspx)</span><span class="sxs-lookup"><span data-stu-id="326c9-232">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol Errata](https://msdn.microsoft.com/library/mt612824.aspx)</span></span>
