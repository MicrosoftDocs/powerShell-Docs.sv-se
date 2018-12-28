---
ms.date: 04/11/2018
keywords: DSC, powershell, konfiguration, installation
title: DSC-hämtningstjänsten
ms.openlocfilehash: 659a8f8b2ce7d34058e789c5de336dc1f1f2abb2
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404991"
---
# <a name="desired-state-configuration-pull-service"></a><span data-ttu-id="04071-103">Desired State Configuration-hämtningstjänsten</span><span class="sxs-lookup"><span data-stu-id="04071-103">Desired State Configuration Pull Service</span></span>

> <span data-ttu-id="04071-104">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="04071-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="04071-105">Pull-servern (Windows-funktionen *DSC-tjänst*) är en stöds komponent i Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner.</span><span class="sxs-lookup"><span data-stu-id="04071-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="04071-106">Rekommenderar vi att du påbörjar övergången hanterade klienter [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inklusive funktioner utöver Pull-servern på Windows Server) eller en av community-lösningar visas [här](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="04071-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="04071-107">Lokal konfigurationshanterare kan hanteras centralt av en Pull-tjänst-lösning.</span><span class="sxs-lookup"><span data-stu-id="04071-107">Local Configuration Manager can be centrally managed by a Pull Service solution.</span></span>
<span data-ttu-id="04071-108">När du använder den här metoden, är den nod som hanteras registrerat med en tjänst och tilldelad en konfiguration i LCM inställningar.</span><span class="sxs-lookup"><span data-stu-id="04071-108">When using this approach, the node that is being managed is registered with a service and assigned a configuration in LCM settings.</span></span>
<span data-ttu-id="04071-109">Konfigurationen och alla DSC-resurser som behövs som beroenden för konfigurationen hämtas till datorn och används av LCM för att hantera konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="04071-109">The configuration and all DSC resources needed as dependencies for the configuration are downloaded to the machine and used by LCM to manage the configuration.</span></span>
<span data-ttu-id="04071-110">Information om tillståndet för den datorn hanteras har överförts till tjänsten för rapportering.</span><span class="sxs-lookup"><span data-stu-id="04071-110">Information about the state of the machine being managed is uploaded to the service for reporting.</span></span>
<span data-ttu-id="04071-111">Detta kallas för ”hämtningstjänsten”.</span><span class="sxs-lookup"><span data-stu-id="04071-111">This concept is referred to as "pull service."</span></span>

<span data-ttu-id="04071-112">De aktuella alternativ för pull-tjänsten är:</span><span class="sxs-lookup"><span data-stu-id="04071-112">The current options for pull service include:</span></span>

- <span data-ttu-id="04071-113">Azure Automation Desired State Configuration-tjänsten</span><span class="sxs-lookup"><span data-stu-id="04071-113">Azure Automation Desired State Configuration service</span></span>
- <span data-ttu-id="04071-114">En pull-tjänst som körs på Windows Server</span><span class="sxs-lookup"><span data-stu-id="04071-114">A pull service running on Windows Server</span></span>
- <span data-ttu-id="04071-115">Community underhålls lösningar med öppen källkod</span><span class="sxs-lookup"><span data-stu-id="04071-115">Community maintained open-source solutions</span></span>
- <span data-ttu-id="04071-116">En SMB-resurs</span><span class="sxs-lookup"><span data-stu-id="04071-116">An SMB share</span></span>

<span data-ttu-id="04071-117">**Den rekommenderade lösningen**, och alternativet med de funktioner som är tillgänglig, är [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="04071-117">**The recommended solution**, and the option with the most features available, is [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

<span data-ttu-id="04071-118">Azure-tjänsten kan hantera noder på plats i privat Datacenter eller i offentliga moln, till exempel Azure och AWS.</span><span class="sxs-lookup"><span data-stu-id="04071-118">The Azure service can manage nodes on-premises in private datacenters, or in public clouds such as Azure and AWS.</span></span>
<span data-ttu-id="04071-119">Överväg att begränsa utgående trafik till endast publicerade Azure IP-intervall för privata miljöer där servrarna inte kan ansluta direkt till Internet, (se [Azure Datacenter IP-intervall](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span><span class="sxs-lookup"><span data-stu-id="04071-119">For private environments where servers cannot directly connect to the Internet, consider limiting outbound traffic to only the published Azure IP range (see [Azure Datacenter IP Ranges](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span></span>

<span data-ttu-id="04071-120">Funktioner i tjänsten online som inte är för närvarande tillgängliga i pull-tjänsten på Windows Server:</span><span class="sxs-lookup"><span data-stu-id="04071-120">Features of the online service that are not currently available in the pull service on Windows Server include:</span></span>
- <span data-ttu-id="04071-121">Alla data krypteras vid överföring och i vila</span><span class="sxs-lookup"><span data-stu-id="04071-121">All data is encrypted in transit and at rest</span></span>
- <span data-ttu-id="04071-122">Klientcertifikat skapas och hanteras automatiskt</span><span class="sxs-lookup"><span data-stu-id="04071-122">Client certificates are created and managed automatically</span></span>
- <span data-ttu-id="04071-123">Hemligheter lagra för att centralt hantera [lösenord/autentiseringsuppgifterna](/azure/automation/automation-credentials), eller [variabler](/azure/automation/automation-variables) , till exempel servernamn eller anslutningssträngar</span><span class="sxs-lookup"><span data-stu-id="04071-123">Secrets store for centrally managing [passwords/credentials](/azure/automation/automation-credentials), or [variables](/azure/automation/automation-variables) such as server names or connection strings</span></span>
- <span data-ttu-id="04071-124">Centralt hantera nod [LCM konfiguration](../managing-nodes/metaConfig.md#basic-settings)</span><span class="sxs-lookup"><span data-stu-id="04071-124">Centrally manage node [LCM configuration](../managing-nodes/metaConfig.md#basic-settings)</span></span>
- <span data-ttu-id="04071-125">Tilldela centralt konfigurationer till klientnoder</span><span class="sxs-lookup"><span data-stu-id="04071-125">Centrally assign configurations to client nodes</span></span>
- <span data-ttu-id="04071-126">Versionen konfigurationen ändras till ”kontrollvärde grupper” för att testa innan de når produktionen</span><span class="sxs-lookup"><span data-stu-id="04071-126">Release configuration changes to "canary groups" for testing before reaching production</span></span>
- <span data-ttu-id="04071-127">Grafisk rapportering</span><span class="sxs-lookup"><span data-stu-id="04071-127">Graphical reporting</span></span>
  - <span data-ttu-id="04071-128">Statusinformation om på DSC-resurs granularitetsnivån</span><span class="sxs-lookup"><span data-stu-id="04071-128">Status detail at the DSC resource level of granularity</span></span>
  - <span data-ttu-id="04071-129">Utförlig felmeddelanden från klientdatorer för felsökning</span><span class="sxs-lookup"><span data-stu-id="04071-129">Verbose error messages from client machines for troubleshooting</span></span>
- <span data-ttu-id="04071-130">[Integrering med Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) för avisering, automatiserade uppgifter Android/iOS-app för rapportering och aviseringar</span><span class="sxs-lookup"><span data-stu-id="04071-130">[Integration with Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) for alerting, automated tasks, Android/iOS app for reporting and alerting</span></span>

## <a name="dsc-pull-service-in-windows-server"></a><span data-ttu-id="04071-131">DSC-hämtningstjänsten i Windows Server</span><span class="sxs-lookup"><span data-stu-id="04071-131">DSC pull service in Windows Server</span></span>

<span data-ttu-id="04071-132">Det är möjligt att konfigurera en pull-tjänsten ska köras på Windows Server.</span><span class="sxs-lookup"><span data-stu-id="04071-132">It is possible to configuring a pull service to run on Windows Server.</span></span>
<span data-ttu-id="04071-133">Vara bäst att pull-tjänst-lösning som ingår i Windows Server innehåller endast funktioner för att lagra konfigurationer och moduler för att ladda ned och samla in rapportdata i databasen.</span><span class="sxs-lookup"><span data-stu-id="04071-133">Be advised that the pull service solution included in Windows Server includes only capabilities of storing configurations/modules for download and capturing report data in to database.</span></span>
<span data-ttu-id="04071-134">Den innehåller inte alla funktioner som erbjuds av tjänsten i Azure och därför är inte ett bra verktyg för att utvärdera hur tjänsten används.</span><span class="sxs-lookup"><span data-stu-id="04071-134">It does not include many of the capabilities offered by the service in Azure and so is not a good tool for evaluating how the service would be used.</span></span>

<span data-ttu-id="04071-135">Pull-tjänsten som erbjuds i Windows Server är en webbtjänst i IIS som använder ett OData-gränssnitt för att tillgängliggöra DSC-konfigurationsfilerna till målnoder när de noderna som ber om.</span><span class="sxs-lookup"><span data-stu-id="04071-135">The pull service offered in Windows Server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="04071-136">Krav för att använda en pull-server:</span><span class="sxs-lookup"><span data-stu-id="04071-136">Requirements for using a pull server:</span></span>

- <span data-ttu-id="04071-137">En server som kör:</span><span class="sxs-lookup"><span data-stu-id="04071-137">A server running:</span></span>
  - <span data-ttu-id="04071-138">WMF/PowerShell 5.0 eller senare</span><span class="sxs-lookup"><span data-stu-id="04071-138">WMF/PowerShell 5.0 or greater</span></span>
  - <span data-ttu-id="04071-139">IIS-serverrollen</span><span class="sxs-lookup"><span data-stu-id="04071-139">IIS server role</span></span>
  - <span data-ttu-id="04071-140">DSC-tjänsten</span><span class="sxs-lookup"><span data-stu-id="04071-140">DSC Service</span></span>
- <span data-ttu-id="04071-141">Vi rekommenderar några innebär att generera ett certifikat att skydda autentiseringsuppgifterna som skickas till den lokala Configuration Manager (LCM) på målnoder</span><span class="sxs-lookup"><span data-stu-id="04071-141">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="04071-142">Det bästa sättet att konfigurera Windows Server till pull värdtjänsten är att använda en DSC-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="04071-142">The best way to configure Windows Server to host pull service is to use a DSC configuration.</span></span>
<span data-ttu-id="04071-143">Ett exempelskript finns nedan.</span><span class="sxs-lookup"><span data-stu-id="04071-143">An example script is provided below.</span></span>

### <a name="supported-database-systems"></a><span data-ttu-id="04071-144">Stöds databassystem</span><span class="sxs-lookup"><span data-stu-id="04071-144">Supported database systems</span></span>

|<span data-ttu-id="04071-145">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="04071-145">WMF 4.0</span></span>   |<span data-ttu-id="04071-146">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="04071-146">WMF 5.0</span></span>  |<span data-ttu-id="04071-147">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="04071-147">WMF 5.1</span></span> |<span data-ttu-id="04071-148">WMF 5.1 (Windows Server Insider Preview 17090)</span><span class="sxs-lookup"><span data-stu-id="04071-148">WMF 5.1 (Windows Server Insider Preview 17090)</span></span>|
|---------|---------|---------|---------|
|<span data-ttu-id="04071-149">MDB</span><span class="sxs-lookup"><span data-stu-id="04071-149">MDB</span></span>     |<span data-ttu-id="04071-150">ESENT (standard), MDB</span><span class="sxs-lookup"><span data-stu-id="04071-150">ESENT (Default), MDB</span></span> |<span data-ttu-id="04071-151">ESENT (standard), MDB</span><span class="sxs-lookup"><span data-stu-id="04071-151">ESENT (Default), MDB</span></span>|<span data-ttu-id="04071-152">ESENT (standard), SQLServer, MDB</span><span class="sxs-lookup"><span data-stu-id="04071-152">ESENT (Default), SQL Server, MDB</span></span>

<span data-ttu-id="04071-153">Från och med versionen 17090 av [Windows Server, Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), SQL Server är ett alternativ som stöds för Pull-tjänsten (Windows-funktionen *DSC-tjänst*).</span><span class="sxs-lookup"><span data-stu-id="04071-153">Starting in release 17090 of [Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), SQL Server is a supported option for the Pull Service (Windows Feature *DSC-Service*).</span></span>  <span data-ttu-id="04071-154">Detta ger ett nytt alternativ för att skala stora DSC-miljöer som inte har migrerat till [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="04071-154">This provides a new option for scaling large DSC environments that have not migrated to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

> <span data-ttu-id="04071-155">**Obs**: Stöd för SQL Server kommer inte att lägga till tidigare versioner av WMF 5.1 (eller tidigare) och är endast tillgängligt på Windows Server-versioner som är större än eller lika med 17090.</span><span class="sxs-lookup"><span data-stu-id="04071-155">**Note**: SQL Server support will not be added to previous versions of WMF 5.1 (or earlier) and will only be available on Windows Server versions greater than or equal to 17090.</span></span>

<span data-ttu-id="04071-156">Om du vill konfigurera pull-servern för att använda SQL Server, ange **SqlProvider** till `$true` och **SqlConnectionString** till en giltig anslutningssträng i SQL Server.</span><span class="sxs-lookup"><span data-stu-id="04071-156">To configure the pull server to use SQL Server, set **SqlProvider** to `$true` and **SqlConnectionString** to a valid SQL Server Connection String.</span></span>  <span data-ttu-id="04071-157">Mer information finns i [SqlClient anslutningssträngar](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span><span class="sxs-lookup"><span data-stu-id="04071-157">For more information, see [SqlClient Connection Strings](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span></span>
<span data-ttu-id="04071-158">Ett exempel på konfiguration av SQL Server med **xDscWebService**, läsa [använder resursen som xDscWebService](#using-the-xdscwebservice-resource) och granska [Sample_xDscWebServiceRegistration_ UseSQLProvider.ps1 på GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span><span class="sxs-lookup"><span data-stu-id="04071-158">For an example of SQL Server configuration with **xDscWebService**, first read [Using the xDscWebService resource](#using-the-xdscwebservice-resource) and then review [Sample_xDscWebServiceRegistration_UseSQLProvider.ps1 on GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span></span>

### <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="04071-159">Med hjälp av xDscWebService-resurs</span><span class="sxs-lookup"><span data-stu-id="04071-159">Using the xDscWebService resource</span></span>

<span data-ttu-id="04071-160">Det enklaste sättet att konfigurera en webbpullserver är att använda den **xDscWebService** resursmängd som ingår i den **xPSDesiredStateConfiguration** modulen.</span><span class="sxs-lookup"><span data-stu-id="04071-160">The easiest way to set up a web pull server is to use the **xDscWebService** resource, included in the **xPSDesiredStateConfiguration** module.</span></span>
<span data-ttu-id="04071-161">Följande steg beskriver hur du använder resursen i en konfiguration som konfigurerar webbtjänsten.</span><span class="sxs-lookup"><span data-stu-id="04071-161">The following steps explain how to use the resource in a configuration that sets up the web service.</span></span>

1. <span data-ttu-id="04071-162">Anropa den [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet för att installera den **xPSDesiredStateConfiguration** modulen.</span><span class="sxs-lookup"><span data-stu-id="04071-162">Call the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span> <span data-ttu-id="04071-163">**Obs**: **Install-Module** ingår i den **PowerShellGet** modulen, som ingår i PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="04071-163">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="04071-164">Du kan ladda ned den **PowerShellGet** -modulen för PowerShell 3.0 och 4.0 på [PackageManagement PowerShell-moduler förhandsversion](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="04071-164">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>
1. <span data-ttu-id="04071-165">Hämta ett SSL-certifikat för DSC-hämtningsservern från en betrodd certifikatutfärdare, antingen inom din organisation eller en offentlig myndighet.</span><span class="sxs-lookup"><span data-stu-id="04071-165">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="04071-166">Certifikatet som togs emot från utfärdaren är vanligtvis i PFX-format.</span><span class="sxs-lookup"><span data-stu-id="04071-166">The certificate received from the authority is usually in the PFX format.</span></span> <span data-ttu-id="04071-167">Installera certifikatet på den nod som blir DSC-hämtningsservern på standardplatsen, vilket ska vara CERT: \LocalMachine\My.</span><span class="sxs-lookup"><span data-stu-id="04071-167">Install the certificate on the node that will become the DSC Pull server in the default location, which should be CERT:\LocalMachine\My.</span></span> <span data-ttu-id="04071-168">Anteckna tumavtrycket för certifikatet.</span><span class="sxs-lookup"><span data-stu-id="04071-168">Make a note of the certificate thumbprint.</span></span>
1. <span data-ttu-id="04071-169">Välj ett GUID som ska användas som nyckel för tjänstregistrering.</span><span class="sxs-lookup"><span data-stu-id="04071-169">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="04071-170">För att generera en med hjälp av PowerShell anger du följande i PS-Kommandotolken och tryck på RETUR: '``` [guid]::newGuid()```'eller'```New-Guid```'.</span><span class="sxs-lookup"><span data-stu-id="04071-170">To generate one using PowerShell enter the following at the PS prompt and press enter: '``` [guid]::newGuid()```' or '```New-Guid```'.</span></span> <span data-ttu-id="04071-171">Den här nyckeln används av klientnoder som en delad nyckel för autentisering under registreringen.</span><span class="sxs-lookup"><span data-stu-id="04071-171">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="04071-172">Mer information finns i avsnittet registreringsnyckel nedan.</span><span class="sxs-lookup"><span data-stu-id="04071-172">For more information, see the Registration Key section below.</span></span>
1. <span data-ttu-id="04071-173">I PowerShell ISE starta (F5) följande konfigurationsskript (ingår i exempel-mappen på den **xPSDesiredStateConfiguration** modulen som Sample_xDscWebServiceRegistration.ps1).</span><span class="sxs-lookup"><span data-stu-id="04071-173">In the PowerShell ISE, start (F5) the following configuration script (included in the Examples folder of the  **xPSDesiredStateConfiguration** module as Sample_xDscWebServiceRegistration.ps1).</span></span> <span data-ttu-id="04071-174">Det här skriptet ställer in hämtningsservern.</span><span class="sxs-lookup"><span data-stu-id="04071-174">This script sets up the pull server.</span></span>

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

1. <span data-ttu-id="04071-175">Kör sedan konfigurationen skicka tumavtrycket för SSL-certifikat som den **certificateThumbPrint** parameter och en GUID-registrering nyckel som den **RegistrationKey** parameter:</span><span class="sxs-lookup"><span data-stu-id="04071-175">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDscWebServiceRegistration -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

#### <a name="registration-key"></a><span data-ttu-id="04071-176">Nyckel för tjänstregistrering</span><span class="sxs-lookup"><span data-stu-id="04071-176">Registration Key</span></span>

<span data-ttu-id="04071-177">För att tillåta noder som ska registreras på servern så att de kan använda namnen i stället för ett ID, en registreringsnyckel som har skapats av ovanstående konfiguration sparas i en fil med namnet `RegistrationKeys.txt` i `C:\Program Files\WindowsPowerShell\DscService`.</span><span class="sxs-lookup"><span data-stu-id="04071-177">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key that was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="04071-178">Nyckel för tjänstregistrering fungerar som en delad hemlighet som används under den första registreringen av klienten med pull-servern.</span><span class="sxs-lookup"><span data-stu-id="04071-178">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="04071-179">Klienten genererar ett självsignerat certifikat som används för att autentisera till hämtningsservern unikt när registreringen är slutförd.</span><span class="sxs-lookup"><span data-stu-id="04071-179">The client will generate a self-signed certificate that is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="04071-180">Tumavtrycket för certifikatet lagras lokalt och som är associerade med pull-serverns URL.</span><span class="sxs-lookup"><span data-stu-id="04071-180">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>
> <span data-ttu-id="04071-181">**Obs**: Registreringsnycklar stöds inte i PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="04071-181">**Note**: Registration keys are not supported in PowerShell 4.0.</span></span>

<span data-ttu-id="04071-182">Nyckel för tjänstregistrering måste finnas i metaconfiguration för alla målnoden som ska registreras med den här pull-servern för att kunna konfigurera en nod för autentisering med pull-servern.</span><span class="sxs-lookup"><span data-stu-id="04071-182">In order to configure a node to authenticate with the pull server, the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="04071-183">Observera att den **RegistrationKey** i metaconfiguration nedan tas bort när måldatorn har registrerats och som värdet '140a952b-b9d6-406b-b416-e0f759c9c0e4' måste matcha det värde som lagras i den RegistrationKeys.txt fil på hämtningsservern.</span><span class="sxs-lookup"><span data-stu-id="04071-183">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value '140a952b-b9d6-406b-b416-e0f759c9c0e4' must match the value stored in the RegistrationKeys.txt file on the pull server.</span></span> <span data-ttu-id="04071-184">Behandla alltid registrering nyckelvärdet på ett säkert sätt, eftersom att känna till det tillåter alla måldatorn för att registreras på pull-servern.</span><span class="sxs-lookup"><span data-stu-id="04071-184">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

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

> <span data-ttu-id="04071-185">**Obs**: Den **ReportServerWeb** avsnittet kan rapporterar data som ska skickas till den pull-servern.</span><span class="sxs-lookup"><span data-stu-id="04071-185">**Note**: The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span>

<span data-ttu-id="04071-186">Bristen på den **ConfigurationID** egenskap i filen metaconfiguration innebär den pull-servern stöder version 2 av protokollet för pull-server så att en inledande registrering krävs.</span><span class="sxs-lookup"><span data-stu-id="04071-186">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span>
<span data-ttu-id="04071-187">Däremot förekomsten av en **ConfigurationID** innebär att V1-version av protokollet för pull-server ska användas och det finns ingen registrering-bearbetning.</span><span class="sxs-lookup"><span data-stu-id="04071-187">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

><span data-ttu-id="04071-188">**Obs**: I ett pushscenario finns en bugg i den aktuella versionen som gör det nödvändigt att definiera en ConfigurationID-egenskap i filen metaconfiguration för noder som aldrig har registrerat med en pull-server.</span><span class="sxs-lookup"><span data-stu-id="04071-188">**Note**: In a PUSH scenario, a bug exists in the current release that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="04071-189">Detta tvinga V1-Hämtningsserver-protokollet och undvika felmeddelanden för registrering.</span><span class="sxs-lookup"><span data-stu-id="04071-189">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="04071-190">Placera konfigurationer och resurser</span><span class="sxs-lookup"><span data-stu-id="04071-190">Placing configurations and resources</span></span>

<span data-ttu-id="04071-191">Efter pull serverinstallationen är klar måste de mappar som definieras av den **ConfigurationPath** och **ModulePath** egenskaper i pull-serverkonfiguration är där du placerar moduler och konfigurationer som ska vara tillgängliga för målnoder att hämta.</span><span class="sxs-lookup"><span data-stu-id="04071-191">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span>
<span data-ttu-id="04071-192">De här filerna måste vara i ett visst format i för pull-servern ska kunna bearbetas korrekt.</span><span class="sxs-lookup"><span data-stu-id="04071-192">These files need to be in a specific format in order for the pull server to correctly process them.</span></span>

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="04071-193">DSC resursformatet modulen paket</span><span class="sxs-lookup"><span data-stu-id="04071-193">DSC resource module package format</span></span>

<span data-ttu-id="04071-194">Varje Resursmodul måste zippade och med namnet enligt följande mönster `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="04071-194">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span>
<span data-ttu-id="04071-195">Till exempel namnet en modul med namnet xWebAdminstration med en Modulversion av 3.1.2.0 ”xWebAdministration_3.2.1.0.zip”.</span><span class="sxs-lookup"><span data-stu-id="04071-195">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span>
<span data-ttu-id="04071-196">Varje version av en modul måste finnas i en enda zip-fil.</span><span class="sxs-lookup"><span data-stu-id="04071-196">Each version of a module must be contained in a single zip file.</span></span>
<span data-ttu-id="04071-197">Eftersom det finns endast en version av en resurs i varje zip-filen, stöds inte formatet modulen har lagts till i WMF 5.0 med stöd för flera modulversionerna i en enskild katalog.</span><span class="sxs-lookup"><span data-stu-id="04071-197">Since there is only a single version of a resource in each zip file, the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span>
<span data-ttu-id="04071-198">Det innebär att innan du packa upp DSC-resurs-moduler för användning med hämtningsservern du måste göra små ändringar i katalogstrukturen.</span><span class="sxs-lookup"><span data-stu-id="04071-198">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span>
<span data-ttu-id="04071-199">Moduler som innehåller DSC-resurs i WMF 5.0 standardformatet är ' {modulmappen}\{Modulversion} \DscResources\{DSC resursmapp}\'.</span><span class="sxs-lookup"><span data-stu-id="04071-199">The default format of modules containing DSC resource in WMF 5.0 is '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.</span></span>
<span data-ttu-id="04071-200">Innan du paketering för hämtningsservern, ta bort den **{Modulversion}** mapp så blir sökvägen ' {modulmappen} \DscResources\{DSC resursmapp}\'.</span><span class="sxs-lookup"><span data-stu-id="04071-200">Before packaging up for the pull server, remove the **{Module version}** folder so the path becomes '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span></span>
<span data-ttu-id="04071-201">Med den här ändringen zip-mappen som beskrivs ovan och placera dessa zip-filer i den **ModulePath** mapp.</span><span class="sxs-lookup"><span data-stu-id="04071-201">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="04071-202">Använd `New-DscChecksum {module zip file}` att skapa en kontrollsumma-fil för den nya modulen.</span><span class="sxs-lookup"><span data-stu-id="04071-202">Use `New-DscChecksum {module zip file}` to create a checksum file for the newly added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="04071-203">Konfigurationen MOF-format</span><span class="sxs-lookup"><span data-stu-id="04071-203">Configuration MOF format</span></span>

<span data-ttu-id="04071-204">En MOF-konfigurationsfilen måste kopplas till en kontrollsumma-fil så att en LCM på målnoden verifiera konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="04071-204">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="04071-205">Om du vill skapa en kontrollsumma, anropa den [New DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="04071-205">To create a checksum, call the [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) cmdlet.</span></span>
<span data-ttu-id="04071-206">Cmdlet: en tar en **sökväg** parameter som anger den mapp där konfigurationen MOF finns.</span><span class="sxs-lookup"><span data-stu-id="04071-206">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span>
<span data-ttu-id="04071-207">Cmdleten skapar en kontrollsumma-fil med namnet `ConfigurationMOFName.mof.checksum`, där `ConfigurationMOFName` är namnet på mof-konfigurationsfilen.</span><span class="sxs-lookup"><span data-stu-id="04071-207">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="04071-208">Om det finns flera olika konfigurationer MOF-filer i en angiven mapp, skapas en kontrollsumma för varje konfiguration i mappen.</span><span class="sxs-lookup"><span data-stu-id="04071-208">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>
<span data-ttu-id="04071-209">Placera MOF-filer och deras associerade kontrollsumma filer i den **ConfigurationPath** mapp.</span><span class="sxs-lookup"><span data-stu-id="04071-209">Place the MOF files and their associated checksum files in the **ConfigurationPath** folder.</span></span>

><span data-ttu-id="04071-210">**Obs**: Om du ändrar MOF-konfigurationsfilen på något sätt, måste du också återskapa filen kontrollsumma.</span><span class="sxs-lookup"><span data-stu-id="04071-210">**Note**: If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

### <a name="tooling"></a><span data-ttu-id="04071-211">Verktyg</span><span class="sxs-lookup"><span data-stu-id="04071-211">Tooling</span></span>

<span data-ttu-id="04071-212">För att kunna utgör inställningen verifiera och hantera hämtningsservern enklare, följande verktyg ingår som exempel i den senaste versionen av modulen xPSDesiredStateConfiguration:</span><span class="sxs-lookup"><span data-stu-id="04071-212">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>

1. <span data-ttu-id="04071-213">En modul som hjälper med paketering moduler för DSC-resurs och konfigurationsfiler för användning på hämtningsservern.</span><span class="sxs-lookup"><span data-stu-id="04071-213">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span> <span data-ttu-id="04071-214">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span><span class="sxs-lookup"><span data-stu-id="04071-214">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span></span> <span data-ttu-id="04071-215">Exemplen nedan:</span><span class="sxs-lookup"><span data-stu-id="04071-215">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="04071-216">Ett skript som kontrollerar pull-servern är korrekt konfigurerad.</span><span class="sxs-lookup"><span data-stu-id="04071-216">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="04071-217">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span><span class="sxs-lookup"><span data-stu-id="04071-217">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span></span>

## <a name="community-solutions-for-pull-service"></a><span data-ttu-id="04071-218">Community-lösningar för Pull-tjänsten</span><span class="sxs-lookup"><span data-stu-id="04071-218">Community Solutions for Pull Service</span></span>

<span data-ttu-id="04071-219">DSC-communityn har skapat flera lösningar för att implementera protokollet pull-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="04071-219">The DSC community has authored multiple solutions to implement the pull service protocol.</span></span>
<span data-ttu-id="04071-220">För lokala miljöer erbjuder dessa pull service-funktionerna och en möjlighet att bidra till community med inkrementell förbättringar.</span><span class="sxs-lookup"><span data-stu-id="04071-220">For on-premises environments, these offer pull service capabilities and an opportunity to contribute back to the community with incremental enhancements.</span></span>

- [<span data-ttu-id="04071-221">Tug</span><span class="sxs-lookup"><span data-stu-id="04071-221">Tug</span></span>](https://github.com/powershellorg/tug)
- [<span data-ttu-id="04071-222">DSC-TRÆK</span><span class="sxs-lookup"><span data-stu-id="04071-222">DSC-TRÆK</span></span>](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a><span data-ttu-id="04071-223">Pull-klientkonfiguration</span><span class="sxs-lookup"><span data-stu-id="04071-223">Pull client configuration</span></span>

<span data-ttu-id="04071-224">I följande avsnitt beskrivs hur du konfigurerar pull-klienter i detalj:</span><span class="sxs-lookup"><span data-stu-id="04071-224">The following topics describe setting up pull clients in detail:</span></span>

- [<span data-ttu-id="04071-225">Konfigurera en DSC-pullklient med konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="04071-225">Set up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
- [<span data-ttu-id="04071-226">Konfigurera en DSC-hämtningsklient med konfigurationsnamn</span><span class="sxs-lookup"><span data-stu-id="04071-226">Set up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
- [<span data-ttu-id="04071-227">Partiella konfigurationer</span><span class="sxs-lookup"><span data-stu-id="04071-227">Partial configurations</span></span>](partialConfigs.md)

## <a name="see-also"></a><span data-ttu-id="04071-228">Se även</span><span class="sxs-lookup"><span data-stu-id="04071-228">See also</span></span>

- [<span data-ttu-id="04071-229">Windows PowerShell Desired State Configuration-översikt</span><span class="sxs-lookup"><span data-stu-id="04071-229">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)
- [<span data-ttu-id="04071-230">Tillämpa konfigurationer</span><span class="sxs-lookup"><span data-stu-id="04071-230">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="04071-231">Använd en DSC-rapportserver</span><span class="sxs-lookup"><span data-stu-id="04071-231">Using a DSC report server</span></span>](reportServer.md)
- <span data-ttu-id="04071-232">[[MS-DSCPM]: Desired State Configuration protokollet för Pull-modell](https://msdn.microsoft.com/library/dn393548.aspx)</span><span class="sxs-lookup"><span data-stu-id="04071-232">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol](https://msdn.microsoft.com/library/dn393548.aspx)</span></span>
- <span data-ttu-id="04071-233">[[MS-DSCPM]: Desired State Configuration Pull-modellen protokollet rättelser](https://msdn.microsoft.com/library/mt612824.aspx)</span><span class="sxs-lookup"><span data-stu-id="04071-233">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol Errata](https://msdn.microsoft.com/library/mt612824.aspx)</span></span>
