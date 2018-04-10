---
ms.date: 02/02/2018
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC-hämtningstjänsten
ms.openlocfilehash: 1547092d5ea6733296bf89f05dd96f70c0a000ac
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="desired-state-configuration-pull-service"></a><span data-ttu-id="ba9f0-103">Desired State Configuration Pull-tjänsten</span><span class="sxs-lookup"><span data-stu-id="ba9f0-103">Desired State Configuration Pull Service</span></span>

> <span data-ttu-id="ba9f0-104">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ba9f0-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="ba9f0-105">Local Configuration Manager kan hanteras centralt av en Pull-tjänst-lösning.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-105">Local Configuration Manager can be centrally managed by a Pull Service solution.</span></span>
<span data-ttu-id="ba9f0-106">När du använder den här metoden är noden som hanteras registrerats med en tjänst och tilldelad en konfiguration i MGM inställningar.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-106">When using this approach, the node that is being managed is registered with a service and assigned a configuration in LCM settings.</span></span>
<span data-ttu-id="ba9f0-107">Konfigurationen och alla DSC-resurser som behövs som beroenden för konfigurationen laddas ned till datorn och används av MGM för att hantera konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-107">The configuration and all DSC resources needed as dependencies for the configuration are downloaded to the machine and used by LCM to manage the configuration.</span></span>
<span data-ttu-id="ba9f0-108">Information om tillståndet för den datorn hanteras har överförts till tjänsten för rapportering.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-108">Information about the state of the machine being managed is uploaded to the service for reporting.</span></span>
<span data-ttu-id="ba9f0-109">Detta kallas ”pull-tjänst”.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-109">This concept is referred to as "pull service".</span></span>

<span data-ttu-id="ba9f0-110">Aktuella alternativ för pull-tjänsten är:</span><span class="sxs-lookup"><span data-stu-id="ba9f0-110">The current options for pull service include:</span></span>

- <span data-ttu-id="ba9f0-111">Azure Automation önskade tillstånd konfigurationstjänsten</span><span class="sxs-lookup"><span data-stu-id="ba9f0-111">Azure Automation Desired State Configuration service</span></span>
- <span data-ttu-id="ba9f0-112">En pull-tjänst som körs på Windows Server</span><span class="sxs-lookup"><span data-stu-id="ba9f0-112">A pull service running on Windows Server</span></span>
- <span data-ttu-id="ba9f0-113">Gemenskapen underhålls öppen källkod</span><span class="sxs-lookup"><span data-stu-id="ba9f0-113">Community maintained open source solutions</span></span>
- <span data-ttu-id="ba9f0-114">En SMB-resurs</span><span class="sxs-lookup"><span data-stu-id="ba9f0-114">An SMB share</span></span>

<span data-ttu-id="ba9f0-115">**Den rekommenderade lösningen**, och alternativet med de funktioner som är tillgängliga, är [Azure Automation DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="ba9f0-115">**The recommended solution**, and the option with the most features available, is [Azure Automation DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-getting-started).</span></span>

<span data-ttu-id="ba9f0-116">Azure-tjänsten kan hantera noder lokalt i privat Datacenter eller i offentliga moln, till exempel Azure och AWS.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-116">The Azure service can manage nodes on-premises in private datacenters, or in public clouds such as Azure and AWS.</span></span>
<span data-ttu-id="ba9f0-117">Överväg att begränsa utgående trafik till endast publicerade Azure IP-adressintervall för privata miljöer där servrarna inte kan ansluta direkt till Internet, (se [IP-intervall för Azure-Datacenter](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span><span class="sxs-lookup"><span data-stu-id="ba9f0-117">For private environments where servers cannot directly connect to the Internet, consider limiting outbound traffic to only the published Azure IP range (see [Azure Datacenter IP Ranges](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span></span>

<span data-ttu-id="ba9f0-118">Tjänsten online-funktioner som inte är tillgängliga i pull-tjänsten på Windows Server inkluderar:</span><span class="sxs-lookup"><span data-stu-id="ba9f0-118">Features of the online service that are not currently available in the pull service on Windows Server include:</span></span>
- <span data-ttu-id="ba9f0-119">Krypteras alla data under överföring och i vila</span><span class="sxs-lookup"><span data-stu-id="ba9f0-119">All data is encrypted in transit and at rest</span></span>
- <span data-ttu-id="ba9f0-120">Klientcertifikat skapas och hanteras automatiskt</span><span class="sxs-lookup"><span data-stu-id="ba9f0-120">Client certificates are created and managed automatically</span></span>
- <span data-ttu-id="ba9f0-121">Hemligheter lagra för att centralt hantera [lösenord/autentiseringsuppgifterna](https://docs.microsoft.com/en-us/azure/automation/automation-credentials), eller [variabler](https://docs.microsoft.com/en-us/azure/automation/automation-variables) , till exempel servernamn eller anslutningssträngar</span><span class="sxs-lookup"><span data-stu-id="ba9f0-121">Secrets store for centrally managing [passwords/credentials](https://docs.microsoft.com/en-us/azure/automation/automation-credentials), or [variables](https://docs.microsoft.com/en-us/azure/automation/automation-variables) such as server names or connection strings</span></span>
- <span data-ttu-id="ba9f0-122">Centralt hantera nod [MGM konfiguration](metaConfig.md#basic-settings)</span><span class="sxs-lookup"><span data-stu-id="ba9f0-122">Centrally manage node [LCM configuration](metaConfig.md#basic-settings)</span></span>
- <span data-ttu-id="ba9f0-123">Tilldela centralt konfigurationer till klientnoder</span><span class="sxs-lookup"><span data-stu-id="ba9f0-123">Centrally assign configurations to client nodes</span></span>
- <span data-ttu-id="ba9f0-124">Versionen konfiguration ändras till ”Kanarieöarna grupper” för att testa innan det nådde produktion</span><span class="sxs-lookup"><span data-stu-id="ba9f0-124">Release configuration changes to "canary groups" for testing before reaching production</span></span>
- <span data-ttu-id="ba9f0-125">Grafisk rapportering</span><span class="sxs-lookup"><span data-stu-id="ba9f0-125">Graphical reporting</span></span>
  - <span data-ttu-id="ba9f0-126">Information om status på nivån för DSC-resurs i granularitet</span><span class="sxs-lookup"><span data-stu-id="ba9f0-126">Status detail at the DSC resource level of granularity</span></span>
  - <span data-ttu-id="ba9f0-127">Detaljerade felmeddelanden från klientdatorer för felsökning</span><span class="sxs-lookup"><span data-stu-id="ba9f0-127">Verbose error messages from client machines for troubleshooting</span></span>
- <span data-ttu-id="ba9f0-128">[Integrering med Azure logganalys](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-diagnostics) för aviseringar, automatiserade åtgärder Android/iOS-app för rapportering och aviseringar</span><span class="sxs-lookup"><span data-stu-id="ba9f0-128">[Integration with Azure Log Analytics](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-diagnostics) for alerting, automated tasks, Android/iOS app for reporting and alerting</span></span>

## <a name="dsc-pull-service-in-windows-server"></a><span data-ttu-id="ba9f0-129">DSC pull-tjänsten i Windows Server</span><span class="sxs-lookup"><span data-stu-id="ba9f0-129">DSC pull service in Windows Server</span></span>

<span data-ttu-id="ba9f0-130">Det är möjligt att konfigurera en pull-tjänsten körs på Windows Server.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-130">It is possible to configuring a pull service to run on Windows Server.</span></span>
<span data-ttu-id="ba9f0-131">Du vara medveten om att pull-tjänsten-lösningen som ingår i Windows Server innehåller endast funktioner för lagring av konfigurationer och moduler för att ladda ned och samlar in rapportdata i databasen.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-131">Please be advised that the pull service solution included in Windows Server includes only capabilities of storing configurations/modules for download and capturing report data in to database.</span></span>
<span data-ttu-id="ba9f0-132">Den innehåller inte många av funktionerna som erbjuds av tjänst i Azure och är alltså inte en bra verktyg för att utvärdera hur tjänsten skulle användas.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-132">It does not include many of the capabilities offered by the service in Azure and so is not a good tool for evaluating how the service would be used.</span></span>

<span data-ttu-id="ba9f0-133">Pull-tjänsten erbjuds i Windows Server är en webbtjänst i IIS som använder ett OData-gränssnitt för att tillhandahålla DSC konfigurationsfiler målnoder när de noderna som ber om.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-133">The pull service offered in Windows Server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="ba9f0-134">Krav för att använda en pull-server:</span><span class="sxs-lookup"><span data-stu-id="ba9f0-134">Requirements for using a pull server:</span></span>

- <span data-ttu-id="ba9f0-135">En server som kör:</span><span class="sxs-lookup"><span data-stu-id="ba9f0-135">A server running:</span></span>
  - <span data-ttu-id="ba9f0-136">WMF/PowerShell 5.0 eller senare</span><span class="sxs-lookup"><span data-stu-id="ba9f0-136">WMF/PowerShell 5.0 or greater</span></span>
  - <span data-ttu-id="ba9f0-137">IIS-serverrollen</span><span class="sxs-lookup"><span data-stu-id="ba9f0-137">IIS server role</span></span>
  - <span data-ttu-id="ba9f0-138">DSC Service</span><span class="sxs-lookup"><span data-stu-id="ba9f0-138">DSC Service</span></span>
- <span data-ttu-id="ba9f0-139">Vi rekommenderar vissa innebär genererar ett certifikat för säker autentiseringsuppgifter som angavs till den lokala Configuration Manager (MGM) på målnoder</span><span class="sxs-lookup"><span data-stu-id="ba9f0-139">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="ba9f0-140">Det bästa sättet att konfigurera Windows Server till pull-värdtjänsten är att använda en DSC-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-140">The best way to configure Windows Server to host pull service is to use a DSC configuration.</span></span>
<span data-ttu-id="ba9f0-141">Ett exempelskript finns nedan.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-141">An example script is provided below.</span></span>

### <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="ba9f0-142">Resursnamnet xDSCWebService</span><span class="sxs-lookup"><span data-stu-id="ba9f0-142">Using the xDSCWebService resource</span></span>

<span data-ttu-id="ba9f0-143">Det enklaste sättet att konfigurera en pull-webbserver är att använda resursen xWebService ingår i modulen xPSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-143">The easiest way to set up a web pull server is to use the xWebService resource, included in the xPSDesiredStateConfiguration module.</span></span>
<span data-ttu-id="ba9f0-144">Följande steg förklarar hur du använder resursen i en konfiguration som ställer in webbtjänsten.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-144">The following steps explain how to use the resource in a configuration that sets up the web service.</span></span>

1. <span data-ttu-id="ba9f0-145">Anropa den [installera modulen](https://technet.microsoft.com/en-us/library/dn807162.aspx) för att installera den **xPSDesiredStateConfiguration** modul.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-145">Call the [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span> <span data-ttu-id="ba9f0-146">**Obs**: **installera modulen** ingår i den **PowerShellGet** module, som ingår i PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-146">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="ba9f0-147">Du kan hämta den **PowerShellGet** -modul för PowerShell 3.0 och 4.0 på [PackageManagement PowerShell-moduler Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="ba9f0-147">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>
1. <span data-ttu-id="ba9f0-148">Hämta ett SSL-certifikat för DSC Pull-server från en betrodd certifikatutfärdare, antingen inom din organisation eller en offentlig myndighet.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-148">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="ba9f0-149">Certifikatet som togs emot från myndigheten är vanligtvis i PFX-format.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-149">The certificate received from the authority is usually in the PFX format.</span></span> <span data-ttu-id="ba9f0-150">Installera certifikatet på den nod som blir DSC Pull-servern i standardplatsen som ska vara CERT: \LocalMachine\My.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-150">Install the certificate on the node that will become the DSC Pull server in the default location which should be CERT:\LocalMachine\My.</span></span> <span data-ttu-id="ba9f0-151">Anteckna tumavtrycket för certifikatet.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-151">Make a note of the certificate thumbprint.</span></span>
1. <span data-ttu-id="ba9f0-152">Välj ett GUID som ska användas som nyckel för tjänstregistrering.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-152">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="ba9f0-153">Skapa ett med hjälp av PowerShell Skriv följande i PS-Kommandotolken och tryck på RETUR: '``` [guid]::newGuid()```'eller'```New-Guid```'.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-153">To generate one using PowerShell enter the following at the PS prompt and press enter: '``` [guid]::newGuid()```' or '```New-Guid```'.</span></span> <span data-ttu-id="ba9f0-154">Den här nyckeln används av klientnoder som en delad nyckel för autentisering under registreringen.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-154">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="ba9f0-155">Mer information finns i avsnittet registreringsnyckel nedan.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-155">For more information see the Registration Key section below.</span></span>
1. <span data-ttu-id="ba9f0-156">I PowerShell ISE start (F5) följande konfigurationsskript (ingår i mappen exempel i den **xPSDesiredStateConfiguration** modulen som Sample_xDscWebService.ps1).</span><span class="sxs-lookup"><span data-stu-id="ba9f0-156">In the PowerShell ISE, start (F5) the following configuration script (included in the Example folder of the  **xPSDesiredStateConfiguration** module as Sample_xDscWebService.ps1).</span></span> <span data-ttu-id="ba9f0-157">Det här skriptet konfigurerar pull-server.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-157">This script sets up the pull server.</span></span>

```powershell
    configuration Sample_xDscPullServer
    {
        param
        (
                [string[]]$NodeName = 'localhost',

                [ValidateNotNullOrEmpty()]
                [string] $certificateThumbPrint,

                [Parameter(Mandatory)]
                [ValidateNotNullOrEmpty()]
                [string] $RegistrationKey
         )

         Import-DSCResource -ModuleName xPSDesiredStateConfiguration
         Import-DSCResource –ModuleName PSDesiredStateConfiguration

         Node $NodeName
         {
             WindowsFeature DSCServiceFeature
             {
                 Ensure = 'Present'
                 Name   = 'DSC-Service'
             }

             xDscWebService PSDSCPullServer
             {
                 Ensure                   = 'Present'
                 EndpointName             = 'PSDSCPullServer'
                 Port                     = 8080
                 PhysicalPath             = "$env:SystemDrive\inetpub\PSDSCPullServer"
                 CertificateThumbPrint    = $certificateThumbPrint
                 ModulePath               = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
                 ConfigurationPath        = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
                 State                    = 'Started'
                 DependsOn                = '[WindowsFeature]DSCServiceFeature'
                 UseSecurityBestPractices = $false
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

1. <span data-ttu-id="ba9f0-158">Kör sedan konfigurationen skicka tumavtrycket för SSL-certifikat som den **certificateThumbPrint** parameter och en GUID-registrering nyckel som den **RegistrationKey** parameter:</span><span class="sxs-lookup"><span data-stu-id="ba9f0-158">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDSCPullServer -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose

```

#### <a name="registration-key"></a><span data-ttu-id="ba9f0-159">Nyckel för tjänstregistrering</span><span class="sxs-lookup"><span data-stu-id="ba9f0-159">Registration Key</span></span>

<span data-ttu-id="ba9f0-160">Så att klienten noder som ska registreras på servern så att de kan använda konfigurationsnamn i stället för ett konfigurations-ID, en registreringsnyckel som skapats av ovanstående konfiguration sparas i en fil med namnet `RegistrationKeys.txt` i `C:\Program Files\WindowsPowerShell\DscService`.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-160">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key which was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="ba9f0-161">Registreringsnyckeln som fungerar som en delad hemlighet som används under registreringen av klienten med pull-servern.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-161">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="ba9f0-162">Klienten genererar ett självsignerat certifikat som används för att autentisera unikt till den pull-servern när registreringen är slutförd.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-162">The client will generate a self-signed certificate which is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="ba9f0-163">Tumavtrycket för certifikatet lagras lokalt och som är kopplade till URL-Adressen till den pull-servern.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-163">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>
> <span data-ttu-id="ba9f0-164">**Obs**: registreringsnycklar stöds inte i PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-164">**Note**: Registration keys are not supported in PowerShell 4.0.</span></span>

<span data-ttu-id="ba9f0-165">Nyckeln måste vara i metakonfigurationen för varje målnod i som ska registreras med den här pull-servern för att kunna konfigurera en nod för att autentisera med hämtningsservern i registreringen.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-165">In order to configure a node to authenticate with the pull server the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="ba9f0-166">Observera att den **RegistrationKey** i metakonfigurationen nedan tas bort när måldatorn har registrerats och att värdet '140a952b-b9d6-406b-b416-e0f759c9c0e4' måste matcha det värde som lagras i den RegistrationKeys.txt fil på hämtningsservern.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-166">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value '140a952b-b9d6-406b-b416-e0f759c9c0e4' must match the value stored in the RegistrationKeys.txt file on the pull server.</span></span> <span data-ttu-id="ba9f0-167">Behandla alltid nyckelvärdet registrering på ett säkert sätt, eftersom att känna till det tillåter alla måldatorn registreras på pull-servern.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-167">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode          = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded   = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey    = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
        }
    }
}

PullClientConfigID -OutputPath c:\Configs\TargetNodes


```

> <span data-ttu-id="ba9f0-168">**Obs**: den **ReportServerWeb** avsnittet kan rapportera data skickas till den pull-servern.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-168">**Note**: The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span>

<span data-ttu-id="ba9f0-169">Bristen på den **ConfigurationID** egenskapen i filen metakonfigurationen innebär att hämtningsservern stöder version 2 av protokollet för pull-server så att en inledande registrering krävs.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-169">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span>
<span data-ttu-id="ba9f0-170">Däremot förekomsten av en **ConfigurationID** innebär att V1-version av protokollet för pull-server används och det finns ingen registrering bearbetning.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-170">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

><span data-ttu-id="ba9f0-171">**Obs**: I en PUSH-scenariot ett programfel finns i den aktuella slutgiltiga som gör det nödvändigt att definiera en ConfigurationID-egenskap i filen metakonfigurationen för noder som aldrig har registrerats med en pull-server.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-171">**Note**: In a PUSH scenario, a bug exists in the current relase that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="ba9f0-172">Detta tvingar protokollet V1 Pull-Server och undvika fel registreringsmeddelanden.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-172">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="ba9f0-173">Placera konfigurationer och resurser</span><span class="sxs-lookup"><span data-stu-id="ba9f0-173">Placing configurations and resources</span></span>

<span data-ttu-id="ba9f0-174">När pull serverinstallationen är klar måste de mappar som definieras av den **ConfigurationPath** och **ModulePath** egenskaper i pull-serverkonfiguration är där du kan placera moduler och konfigurationer som ska vara tillgängliga för målnoder och hämtar.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-174">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span>
<span data-ttu-id="ba9f0-175">Filerna måste vara i ett specifikt format för pull-servern att bearbeta dem korrekt.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-175">These files need to be in a specific format in order for the pull server to correctly process them.</span></span>

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="ba9f0-176">DSC resursformatet modulen paketet</span><span class="sxs-lookup"><span data-stu-id="ba9f0-176">DSC resource module package format</span></span>

<span data-ttu-id="ba9f0-177">Varje Resursmodul behöver zippade och namnet enligt följande mönster `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-177">Each resource module needs to be zipped and named according the following pattern `{Module Name}_{Module Version}.zip`.</span></span>
<span data-ttu-id="ba9f0-178">Till exempel namnet en modul med namnet xWebAdminstration med en Modulversion av 3.1.2.0 'xWebAdministration_3.2.1.0.zip'.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-178">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span>
<span data-ttu-id="ba9f0-179">Varje version av en modul måste finnas i en enda zip-fil.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-179">Each version of a module must be contained in a single zip file.</span></span>
<span data-ttu-id="ba9f0-180">Eftersom det finns endast en version av en resurs i formatet modulen lades till i WMF 5.0 med varje zip-filen stöds inte stöd för flera modulversioner i en katalog.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-180">Since there is only a single version of a resource in each zip file the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span>
<span data-ttu-id="ba9f0-181">Detta innebär att innan paketering in DSC resurs moduler för användning med pull-server behöver du göra en mindre ändring i katalogstrukturen.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-181">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span>
<span data-ttu-id="ba9f0-182">Moduler som innehåller DSC-resurs i WMF 5.0 standardformatet är ' {modulen mappen}\{Modulversion} \DscResources\{DSC resursmapp}\'.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-182">The default format of modules containing DSC resource in WMF 5.0 is '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.</span></span>
<span data-ttu-id="ba9f0-183">Innan paketering för pull-server bara ta bort den **{Modulversion}** mapp så blir sökvägen ' {modulen mappen} \DscResources\{DSC resursmapp}\'.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-183">Before packaging up for the pull server simply remove the **{Module version}** folder so the path becomes '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span></span>
<span data-ttu-id="ba9f0-184">Med den här ändringen zip-mappen som beskrivs ovan och placera dessa zip-filer i den **ModulePath** mapp.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-184">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="ba9f0-185">Använd `new-dscchecksum {module zip file}` att skapa en kontrollsumma fil för modulen nyligen tillagda.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-185">Use `new-dscchecksum {module zip file}` to create a checksum file for the newly-added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="ba9f0-186">Konfigurationen MOF-format</span><span class="sxs-lookup"><span data-stu-id="ba9f0-186">Configuration MOF format</span></span>

<span data-ttu-id="ba9f0-187">En konfiguration MOF-fil måste kombineras med en fil kontrollsummor så att en MGM på målnoden kan validera konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-187">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="ba9f0-188">Om du vill skapa en kontrollsumma anropa den [ny DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-188">To create a checksum, call the [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet.</span></span>
<span data-ttu-id="ba9f0-189">Cmdlet tar en **sökväg** parameter som anger den mapp där konfigurationen MOF finns.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-189">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span>
<span data-ttu-id="ba9f0-190">Cmdleten skapar en kontrollsumma-fil med namnet `ConfigurationMOFName.mof.checksum`, där `ConfigurationMOFName` är namnet på konfigurationens mof-fil.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-190">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="ba9f0-191">Om det finns mer än en konfiguration MOF-filer i den angivna mappen, skapas en kontrollsumma för varje konfiguration i mappen.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-191">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>
<span data-ttu-id="ba9f0-192">Placera MOF-filer och deras associerade kontrollsumma filer i den **ConfigurationPath** mapp.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-192">Place the MOF files and their associated checksum files in the **ConfigurationPath** folder.</span></span>

><span data-ttu-id="ba9f0-193">**Obs**: Om du ändrar konfigurationen MOF-filen på något sätt, måste du också återskapa filen kontrollsumma.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-193">**Note**: If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

### <a name="tooling"></a><span data-ttu-id="ba9f0-194">Tooling</span><span class="sxs-lookup"><span data-stu-id="ba9f0-194">Tooling</span></span>

<span data-ttu-id="ba9f0-195">För att kunna utgör inställningen verifiera och hantera den pull-servern som är enklare, följande verktyg ingår som exemplen i den senaste versionen av modulen xPSDesiredStateConfiguration:</span><span class="sxs-lookup"><span data-stu-id="ba9f0-195">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>

1. <span data-ttu-id="ba9f0-196">En modul som kan hjälpa dig i Paketera DSC resurs moduler och konfigurationsfilerna för användning på pull-server.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-196">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span> <span data-ttu-id="ba9f0-197">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span><span class="sxs-lookup"><span data-stu-id="ba9f0-197">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span></span> <span data-ttu-id="ba9f0-198">Exemplen nedan:</span><span class="sxs-lookup"><span data-stu-id="ba9f0-198">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @("xWebAdministration", "xPhp")
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="ba9f0-199">Ett skript som kontrollerar pull-servern är korrekt konfigurerad.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-199">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="ba9f0-200">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span><span class="sxs-lookup"><span data-stu-id="ba9f0-200">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span></span>

## <a name="community-solutions-for-pull-service"></a><span data-ttu-id="ba9f0-201">Community-lösningar för Pull-tjänsten</span><span class="sxs-lookup"><span data-stu-id="ba9f0-201">Community Solutions for Pull Service</span></span>

<span data-ttu-id="ba9f0-202">DSC-gruppen har skapats på flera lösningar för att implementera protokollet pull-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-202">The DSC community has authored multiple solutions to implement the pull service protocol.</span></span>
<span data-ttu-id="ba9f0-203">För lokal tillbaka miljöer dessa erbjuder pull funktioner och möjlighet att bidra till gruppen med inkrementell förbättringar.</span><span class="sxs-lookup"><span data-stu-id="ba9f0-203">For on-premises environments these offer pull service capabilities and an opportunity to contribute back to the community with incremental enhancements.</span></span>

- [<span data-ttu-id="ba9f0-204">Tug</span><span class="sxs-lookup"><span data-stu-id="ba9f0-204">Tug</span></span>](https://github.com/powershellorg/tug)
- [<span data-ttu-id="ba9f0-205">DSC-TRÆK</span><span class="sxs-lookup"><span data-stu-id="ba9f0-205">DSC-TRÆK</span></span>](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a><span data-ttu-id="ba9f0-206">Pull-klientkonfiguration</span><span class="sxs-lookup"><span data-stu-id="ba9f0-206">Pull client configuration</span></span>

<span data-ttu-id="ba9f0-207">I följande avsnitt beskrivs hur du konfigurerar pull-klienter i detalj:</span><span class="sxs-lookup"><span data-stu-id="ba9f0-207">The following topics describe setting up pull clients in detail:</span></span>

- [<span data-ttu-id="ba9f0-208">Ställa in en DSC pull-klient som använder ett konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="ba9f0-208">Setting up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
- [<span data-ttu-id="ba9f0-209">Ställa in en DSC pull-klient med konfigurationsnamn</span><span class="sxs-lookup"><span data-stu-id="ba9f0-209">Setting up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
- [<span data-ttu-id="ba9f0-210">Partiell konfigurationer</span><span class="sxs-lookup"><span data-stu-id="ba9f0-210">Partial configurations</span></span>](partialConfigs.md)

## <a name="see-also"></a><span data-ttu-id="ba9f0-211">Se även</span><span class="sxs-lookup"><span data-stu-id="ba9f0-211">See also</span></span>

- [<span data-ttu-id="ba9f0-212">Windows PowerShell Desired State Configuration-översikt</span><span class="sxs-lookup"><span data-stu-id="ba9f0-212">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
- [<span data-ttu-id="ba9f0-213">Tillämpa konfigurationer</span><span class="sxs-lookup"><span data-stu-id="ba9f0-213">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="ba9f0-214">Använd en DSC-rapportserver</span><span class="sxs-lookup"><span data-stu-id="ba9f0-214">Using a DSC report server</span></span>](reportServer.md)