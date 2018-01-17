---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "Ställer in en pull webbserver DSC"
ms.openlocfilehash: 9a09804ef0efe3e4c92923910884710187d44ac5
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="setting-up-a-dsc-web-pull-server"></a><span data-ttu-id="83562-103">Ställer in en pull webbserver DSC</span><span class="sxs-lookup"><span data-stu-id="83562-103">Setting up a DSC web pull server</span></span>

> <span data-ttu-id="83562-104">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="83562-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="83562-105">En pull-DSC webbserver är en webbtjänst i IIS som använder ett OData-gränssnitt för att tillhandahålla DSC konfigurationsfiler målnoder när de noderna som ber om.</span><span class="sxs-lookup"><span data-stu-id="83562-105">A DSC web pull server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="83562-106">Krav för att använda en pull-server:</span><span class="sxs-lookup"><span data-stu-id="83562-106">Requirements for using a pull server:</span></span>

* <span data-ttu-id="83562-107">En server som kör:</span><span class="sxs-lookup"><span data-stu-id="83562-107">A server running:</span></span>
  - <span data-ttu-id="83562-108">WMF/PowerShell 5.0 eller senare</span><span class="sxs-lookup"><span data-stu-id="83562-108">WMF/PowerShell 5.0 or greater</span></span>
  - <span data-ttu-id="83562-109">IIS-serverrollen</span><span class="sxs-lookup"><span data-stu-id="83562-109">IIS server role</span></span>
  - <span data-ttu-id="83562-110">DSC Service</span><span class="sxs-lookup"><span data-stu-id="83562-110">DSC Service</span></span>
* <span data-ttu-id="83562-111">Vi rekommenderar vissa innebär genererar ett certifikat för säker autentiseringsuppgifter som angavs till den lokala Configuration Manager (MGM) på målnoder</span><span class="sxs-lookup"><span data-stu-id="83562-111">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="83562-112">Du kan lägga till IIS-serverrollen och DSC-tjänsten med guiden Lägg till roller och funktioner i Serverhanteraren eller med hjälp av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="83562-112">You can add the IIS server role and DSC Service with the Add Roles and Features wizard in Server Manager, or by using PowerShell.</span></span> <span data-ttu-id="83562-113">Exempelskript som ingår i det här avsnittet kommer att hantera dessa steg du också.</span><span class="sxs-lookup"><span data-stu-id="83562-113">The sample scripts included in this topic will handle both of these steps for you as well.</span></span>

## <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="83562-114">Resursnamnet xDSCWebService</span><span class="sxs-lookup"><span data-stu-id="83562-114">Using the xDSCWebService resource</span></span>
<span data-ttu-id="83562-115">Det enklaste sättet att konfigurera en pull-webbserver är att använda resursen xWebService ingår i modulen xPSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="83562-115">The easiest way to set up a web pull server is to use the xWebService resource, included in the xPSDesiredStateConfiguration module.</span></span> <span data-ttu-id="83562-116">Följande steg förklarar hur du använder resursen i en konfiguration som ställer in webbtjänsten.</span><span class="sxs-lookup"><span data-stu-id="83562-116">The following steps explain how to use the resource in a configuration that sets up the web service.</span></span>

1. <span data-ttu-id="83562-117">Anropa den [installera modulen](https://technet.microsoft.com/en-us/library/dn807162.aspx) för att installera den **xPSDesiredStateConfiguration** modul.</span><span class="sxs-lookup"><span data-stu-id="83562-117">Call the [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span> <span data-ttu-id="83562-118">**Obs**: **installera modulen** ingår i den **PowerShellGet** module, som ingår i PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="83562-118">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="83562-119">Du kan hämta den **PowerShellGet** -modul för PowerShell 3.0 och 4.0 på [PackageManagement PowerShell-moduler Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="83562-119">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span> 
1. <span data-ttu-id="83562-120">Hämta ett SSL-certifikat för DSC Pull-server från en betrodd certifikatutfärdare, antingen inom din organisation eller en offentlig myndighet.</span><span class="sxs-lookup"><span data-stu-id="83562-120">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="83562-121">Certifikatet som togs emot från myndigheten är vanligtvis i PFX-format.</span><span class="sxs-lookup"><span data-stu-id="83562-121">The certificate received from the authority is usually in the PFX format.</span></span> <span data-ttu-id="83562-122">Installera certifikatet på den nod som blir DSC Pull-servern i standardplatsen som ska vara CERT: \LocalMachine\My.</span><span class="sxs-lookup"><span data-stu-id="83562-122">Install the certificate on the node that will become the DSC Pull server in the default location which should be CERT:\LocalMachine\My.</span></span> <span data-ttu-id="83562-123">Anteckna tumavtrycket för certifikatet.</span><span class="sxs-lookup"><span data-stu-id="83562-123">Make a note of the certificate thumbprint.</span></span>
1. <span data-ttu-id="83562-124">Välj ett GUID som ska användas som nyckel för tjänstregistrering.</span><span class="sxs-lookup"><span data-stu-id="83562-124">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="83562-125">Skapa ett med hjälp av PowerShell Skriv följande i PS-Kommandotolken och tryck på RETUR: '``` [guid]::newGuid()```'eller'```New-Guid```'.</span><span class="sxs-lookup"><span data-stu-id="83562-125">To generate one using PowerShell enter the following at the PS prompt and press enter: '``` [guid]::newGuid()```' or '```New-Guid```'.</span></span> <span data-ttu-id="83562-126">Den här nyckeln används av klientnoder som en delad nyckel för autentisering under registreringen.</span><span class="sxs-lookup"><span data-stu-id="83562-126">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="83562-127">Mer information finns i avsnittet registreringsnyckel nedan.</span><span class="sxs-lookup"><span data-stu-id="83562-127">For more information see the Registration Key section below.</span></span>
1. <span data-ttu-id="83562-128">I PowerShell ISE start (F5) följande konfigurationsskript (ingår i mappen exempel i den **xPSDesiredStateConfiguration** modulen som Sample_xDscWebService.ps1).</span><span class="sxs-lookup"><span data-stu-id="83562-128">In the PowerShell ISE, start (F5) the following configuration script (included in the Example folder of the  **xPSDesiredStateConfiguration** module as Sample_xDscWebService.ps1).</span></span> <span data-ttu-id="83562-129">Det här skriptet konfigurerar pull-server.</span><span class="sxs-lookup"><span data-stu-id="83562-129">This script sets up the pull server.</span></span>
  
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

1. <span data-ttu-id="83562-130">Kör sedan konfigurationen skicka tumavtrycket för SSL-certifikat som den **certificateThumbPrint** parameter och en GUID-registrering nyckel som den **RegistrationKey** parameter:</span><span class="sxs-lookup"><span data-stu-id="83562-130">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store 
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDSCPullServer -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

## <a name="registration-key"></a><span data-ttu-id="83562-131">Nyckel för tjänstregistrering</span><span class="sxs-lookup"><span data-stu-id="83562-131">Registration Key</span></span>
<span data-ttu-id="83562-132">Så att klienten noder som ska registreras på servern så att de kan använda konfigurationsnamn i stället för ett konfigurations-ID, en registreringsnyckel som skapats av ovanstående konfiguration sparas i en fil med namnet `RegistrationKeys.txt` i `C:\Program Files\WindowsPowerShell\DscService`.</span><span class="sxs-lookup"><span data-stu-id="83562-132">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key which was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="83562-133">Registreringsnyckeln som fungerar som en delad hemlighet som används under registreringen av klienten med pull-servern.</span><span class="sxs-lookup"><span data-stu-id="83562-133">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="83562-134">Klienten genererar ett självsignerat certifikat som används för att autentisera unikt till den pull-servern när registreringen är slutförd.</span><span class="sxs-lookup"><span data-stu-id="83562-134">The client will generate a self-signed certificate which is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="83562-135">Tumavtrycket för certifikatet lagras lokalt och som är kopplade till URL-Adressen till den pull-servern.</span><span class="sxs-lookup"><span data-stu-id="83562-135">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>
> <span data-ttu-id="83562-136">**Obs**: registreringsnycklar stöds inte i PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="83562-136">**Note**: Registration keys are not supported in PowerShell 4.0.</span></span> 

<span data-ttu-id="83562-137">Nyckeln måste vara i metakonfigurationen för varje målnod i som ska registreras med den här pull-servern för att kunna konfigurera en nod för att autentisera med hämtningsservern i registreringen.</span><span class="sxs-lookup"><span data-stu-id="83562-137">In order to configure a node to authenticate with the pull server the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="83562-138">Observera att den **RegistrationKey** i metakonfigurationen nedan tas bort när måldatorn har registrerats och att värdet '140a952b-b9d6-406b-b416-e0f759c9c0e4' måste matcha det värde som lagras i den RegistrationKeys.txt fil på hämtningsservern.</span><span class="sxs-lookup"><span data-stu-id="83562-138">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value '140a952b-b9d6-406b-b416-e0f759c9c0e4' must match the value stored in the RegistrationKeys.txt file on the pull server.</span></span> <span data-ttu-id="83562-139">Behandla alltid nyckelvärdet registrering på ett säkert sätt, eftersom att känna till det tillåter alla måldatorn registreras på pull-servern.</span><span class="sxs-lookup"><span data-stu-id="83562-139">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

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
> <span data-ttu-id="83562-140">**Obs**: den **ReportServerWeb** avsnittet kan rapportera data skickas till den pull-servern.</span><span class="sxs-lookup"><span data-stu-id="83562-140">**Note**: The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span> 

<span data-ttu-id="83562-141">Bristen på den **ConfigurationID** egenskapen i filen metakonfigurationen innebär att hämtningsservern stöder version 2 av protokollet för pull-server så att en inledande registrering krävs.</span><span class="sxs-lookup"><span data-stu-id="83562-141">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span> <span data-ttu-id="83562-142">Däremot förekomsten av en **ConfigurationID** innebär att V1-version av protokollet för pull-server används och det finns ingen registrering bearbetning.</span><span class="sxs-lookup"><span data-stu-id="83562-142">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

><span data-ttu-id="83562-143">**Obs**: I en PUSH-scenariot ett programfel finns i den aktuella slutgiltiga som gör det nödvändigt att definiera en ConfigurationID-egenskap i filen metakonfigurationen för noder som aldrig har registrerats med en pull-server.</span><span class="sxs-lookup"><span data-stu-id="83562-143">**Note**: In a PUSH scenario, a bug exists in the current relase that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="83562-144">Detta tvingar protokollet V1 Pull-Server och undvika fel registreringsmeddelanden.</span><span class="sxs-lookup"><span data-stu-id="83562-144">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="83562-145">Placera konfigurationer och resurser</span><span class="sxs-lookup"><span data-stu-id="83562-145">Placing configurations and resources</span></span>

<span data-ttu-id="83562-146">När pull serverinstallationen är klar måste de mappar som definieras av den **ConfigurationPath** och **ModulePath** egenskaper i pull-serverkonfiguration är där du kan placera moduler och konfigurationer som ska vara tillgängliga för målnoder och hämtar.</span><span class="sxs-lookup"><span data-stu-id="83562-146">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span> <span data-ttu-id="83562-147">Filerna måste vara i ett specifikt format för pull-servern att bearbeta dem korrekt.</span><span class="sxs-lookup"><span data-stu-id="83562-147">These files need to be in a specific format in order for the pull server to correctly process them.</span></span> 

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="83562-148">DSC resursformatet modulen paketet</span><span class="sxs-lookup"><span data-stu-id="83562-148">DSC resource module package format</span></span>

<span data-ttu-id="83562-149">Varje Resursmodul behöver zippade och namnet enligt följande mönster `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="83562-149">Each resource module needs to be zipped and named according the following pattern `{Module Name}_{Module Version}.zip`.</span></span> <span data-ttu-id="83562-150">Till exempel namnet en modul med namnet xWebAdminstration med en Modulversion av 3.1.2.0 'xWebAdministration_3.2.1.0.zip'.</span><span class="sxs-lookup"><span data-stu-id="83562-150">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span> <span data-ttu-id="83562-151">Varje version av en modul måste finnas i en enda zip-fil.</span><span class="sxs-lookup"><span data-stu-id="83562-151">Each version of a module must be contained in a single zip file.</span></span> <span data-ttu-id="83562-152">Eftersom det finns endast en version av en resurs i formatet modulen lades till i WMF 5.0 med varje zip-filen stöds inte stöd för flera modulversioner i en katalog.</span><span class="sxs-lookup"><span data-stu-id="83562-152">Since there is only a single version of a resource in each zip file the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span> <span data-ttu-id="83562-153">Detta innebär att innan paketering in DSC resurs moduler för användning med pull-server behöver du göra en mindre ändring i katalogstrukturen.</span><span class="sxs-lookup"><span data-stu-id="83562-153">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span> <span data-ttu-id="83562-154">Moduler som innehåller DSC-resurs i WMF 5.0 standardformatet är ' {modulen mappen}\{Modulversion} \DscResources\{DSC resursmapp}\'.</span><span class="sxs-lookup"><span data-stu-id="83562-154">The default format of modules containing DSC resource in WMF 5.0 is '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.</span></span> <span data-ttu-id="83562-155">Innan paketering för pull-server bara ta bort den **{Modulversion}** mapp så blir sökvägen ' {modulen mappen} \DscResources\{DSC resursmapp}\'.</span><span class="sxs-lookup"><span data-stu-id="83562-155">Before packaging up for the pull server simply remove the **{Module version}** folder so the path becomes '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span></span> <span data-ttu-id="83562-156">Med den här ändringen zip-mappen som beskrivs ovan och placera dessa zip-filer i den **ModulePath** mapp.</span><span class="sxs-lookup"><span data-stu-id="83562-156">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="83562-157">Använd `new-dscchecksum {module zip file}` att skapa en kontrollsumma fil för modulen nyligen tillagda.</span><span class="sxs-lookup"><span data-stu-id="83562-157">Use `new-dscchecksum {module zip file}` to create a checksum file for the newly-added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="83562-158">Konfigurationen MOF-format</span><span class="sxs-lookup"><span data-stu-id="83562-158">Configuration MOF format</span></span> 
<span data-ttu-id="83562-159">En konfiguration MOF-fil måste kombineras med en fil kontrollsummor så att en MGM på målnoden kan validera konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="83562-159">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span> <span data-ttu-id="83562-160">Om du vill skapa en kontrollsumma anropa den [ny DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="83562-160">To create a checksum, call the [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet.</span></span> <span data-ttu-id="83562-161">Cmdlet tar en **sökväg** parameter som anger den mapp där konfigurationen MOF finns.</span><span class="sxs-lookup"><span data-stu-id="83562-161">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="83562-162">Cmdleten skapar en kontrollsumma-fil med namnet `ConfigurationMOFName.mof.checksum`, där `ConfigurationMOFName` är namnet på konfigurationens mof-fil.</span><span class="sxs-lookup"><span data-stu-id="83562-162">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span> <span data-ttu-id="83562-163">Om det finns mer än en konfiguration MOF-filer i den angivna mappen, skapas en kontrollsumma för varje konfiguration i mappen.</span><span class="sxs-lookup"><span data-stu-id="83562-163">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span> <span data-ttu-id="83562-164">Placera MOF-filer och deras associerade kontrollsumma filer i den den **ConfigurationPath** mapp.</span><span class="sxs-lookup"><span data-stu-id="83562-164">Place the MOF files and their associated checksum files in the the **ConfigurationPath** folder.</span></span>

><span data-ttu-id="83562-165">**Obs**: Om du ändrar konfigurationen MOF-filen på något sätt, måste du också återskapa filen kontrollsumma.</span><span class="sxs-lookup"><span data-stu-id="83562-165">**Note**: If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

## <a name="tooling"></a><span data-ttu-id="83562-166">Tooling</span><span class="sxs-lookup"><span data-stu-id="83562-166">Tooling</span></span>
<span data-ttu-id="83562-167">För att kunna utgör inställningen verifiera och hantera den pull-servern som är enklare, följande verktyg ingår som exemplen i den senaste versionen av modulen xPSDesiredStateConfiguration:</span><span class="sxs-lookup"><span data-stu-id="83562-167">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>
1. <span data-ttu-id="83562-168">En modul som kan hjälpa dig i Paketera DSC resurs moduler och konfigurationsfilerna för användning på pull-server.</span><span class="sxs-lookup"><span data-stu-id="83562-168">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span> <span data-ttu-id="83562-169">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span><span class="sxs-lookup"><span data-stu-id="83562-169">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span></span> <span data-ttu-id="83562-170">Exemplen nedan:</span><span class="sxs-lookup"><span data-stu-id="83562-170">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @("xWebAdministration", "xPhp") 
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList 

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="83562-171">Ett skript som kontrollerar pull-servern är korrekt konfigurerad.</span><span class="sxs-lookup"><span data-stu-id="83562-171">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="83562-172">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span><span class="sxs-lookup"><span data-stu-id="83562-172">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span></span>


## <a name="pull-client-configuration"></a><span data-ttu-id="83562-173">Pull-klientkonfiguration</span><span class="sxs-lookup"><span data-stu-id="83562-173">Pull client configuration</span></span> 
<span data-ttu-id="83562-174">I följande avsnitt beskrivs hur du konfigurerar pull-klienter i detalj:</span><span class="sxs-lookup"><span data-stu-id="83562-174">The following topics describe setting up pull clients in detail:</span></span>

* [<span data-ttu-id="83562-175">Ställa in en DSC pull-klient som använder ett konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="83562-175">Setting up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
* [<span data-ttu-id="83562-176">Ställa in en DSC pull-klient med konfigurationsnamn</span><span class="sxs-lookup"><span data-stu-id="83562-176">Setting up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="83562-177">Partiell konfigurationer</span><span class="sxs-lookup"><span data-stu-id="83562-177">Partial configurations</span></span>](partialConfigs.md)


## <a name="see-also"></a><span data-ttu-id="83562-178">Se även</span><span class="sxs-lookup"><span data-stu-id="83562-178">See also</span></span>
* [<span data-ttu-id="83562-179">Windows PowerShell Desired State Configuration-översikt</span><span class="sxs-lookup"><span data-stu-id="83562-179">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
* [<span data-ttu-id="83562-180">Tillämpa konfigurationer</span><span class="sxs-lookup"><span data-stu-id="83562-180">Enacting configurations</span></span>](enactingConfigurations.md)
* [<span data-ttu-id="83562-181">Använd en DSC-rapportserver</span><span class="sxs-lookup"><span data-stu-id="83562-181">Using a DSC report server</span></span>](reportServer.md)

