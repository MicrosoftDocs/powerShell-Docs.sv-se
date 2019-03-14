---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Avgränsa konfigurations- och miljödata
ms.openlocfilehash: 305a766fec81d4ea4afce187756188b067a2048b
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794934"
---
# <a name="separating-configuration-and-environment-data"></a><span data-ttu-id="bd69e-103">Avgränsa konfigurations- och miljödata</span><span class="sxs-lookup"><span data-stu-id="bd69e-103">Separating configuration and environment data</span></span>

><span data-ttu-id="bd69e-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="bd69e-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="bd69e-105">Det kan vara praktiskt att dela de data som används i en DSC-konfiguration från själva-konfigurationen med hjälp av konfigurationsdata.</span><span class="sxs-lookup"><span data-stu-id="bd69e-105">It can be useful to separate the data used in a DSC configuration from the configuration itself by using configuration data.</span></span>
<span data-ttu-id="bd69e-106">Du kan använda en enda konfiguration för flera miljöer genom att göra detta.</span><span class="sxs-lookup"><span data-stu-id="bd69e-106">By doing this, you can use a single configuration for multiple environments.</span></span>

<span data-ttu-id="bd69e-107">Exempelvis om du utvecklar ett program, kan du använda en konfiguration för utvecklings-och produktionsmiljöer och Använd konfigurationsdata för att ange data för varje miljö.</span><span class="sxs-lookup"><span data-stu-id="bd69e-107">For example, if you are developing an application, you can use one configuration for both development and production environments, and use configuration data to specify data for each environment.</span></span>

## <a name="what-is-configuration-data"></a><span data-ttu-id="bd69e-108">Vad är konfigurationsdata?</span><span class="sxs-lookup"><span data-stu-id="bd69e-108">What is configuration data?</span></span>

<span data-ttu-id="bd69e-109">Konfigurationsdata är data som definieras i en hash-tabell och skickas till en DSC-konfiguration när du kompilerar den konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="bd69e-109">Configuration data is data that is defined in a hashtable and passed to a DSC configuration when you compile that configuration.</span></span>

<span data-ttu-id="bd69e-110">En detaljerad beskrivning av den **ConfigurationData** hash-tabell, se [med konfigurationsdata](configData.md).</span><span class="sxs-lookup"><span data-stu-id="bd69e-110">For a detailed description of the **ConfigurationData** hashtable, see [Using configuration data](configData.md).</span></span>

## <a name="a-simple-example"></a><span data-ttu-id="bd69e-111">Ett enkelt exempel</span><span class="sxs-lookup"><span data-stu-id="bd69e-111">A simple example</span></span>

<span data-ttu-id="bd69e-112">Nu ska vi titta på ett väldigt enkelt exempel och se hur det fungerar.</span><span class="sxs-lookup"><span data-stu-id="bd69e-112">Let's look at a very simple example to see how this works.</span></span>
<span data-ttu-id="bd69e-113">Vi skapar en enda konfiguration som säkerställer att **IIS** finns på vissa noder och att **Hyper-V** finns på andra:</span><span class="sxs-lookup"><span data-stu-id="bd69e-113">We'll create a single configuration that ensures that **IIS** is present on some nodes, and that **Hyper-V** is present on others:</span></span>

```powershell
Configuration MyDscConfiguration {

    Node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
        WindowsFeature IISInstall {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }

    }
    Node $AllNodes.Where{$_.Role -eq "VMHost"}.NodeName
    {
        WindowsFeature HyperVInstall {
            Ensure = 'Present'
            Name   = 'Hyper-V'
        }
    }
}

$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            Role = 'WebServer'
        },

        @{
            NodeName    = 'VM-2'
            Role = 'VMHost'
        }
    )
}

MyDscConfiguration -ConfigurationData $MyData
```

<span data-ttu-id="bd69e-114">Den sista raden i det här skriptet kompilerar konfigurationen, skicka `$MyData` som värde **ConfigurationData** parametern.</span><span class="sxs-lookup"><span data-stu-id="bd69e-114">The last line in this script compiles the configuration, passing `$MyData` as the value **ConfigurationData** parameter.</span></span>

<span data-ttu-id="bd69e-115">Resultatet är att två MOF-filer skapas:</span><span class="sxs-lookup"><span data-stu-id="bd69e-115">The result is that two MOF files are created:</span></span>

```
    Directory: C:\DscTests\MyDscConfiguration


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:09 PM           1968 VM-1.mof
-a----        3/31/2017   5:09 PM           1970 VM-2.mof
```

<span data-ttu-id="bd69e-116">`$MyData` Anger två olika noder, var och en med sin egen `NodeName` och `Role`.</span><span class="sxs-lookup"><span data-stu-id="bd69e-116">`$MyData` specifies two different nodes, each with its own `NodeName` and `Role`.</span></span> <span data-ttu-id="bd69e-117">Konfigurationen skapas dynamiskt **nod** block genom att utföra uppsättningen noder får från `$MyData` (mer specifikt `$AllNodes`) och filtrerar samlingen mot den `Role` egenskap...</span><span class="sxs-lookup"><span data-stu-id="bd69e-117">The configuration dynamically creates **Node** blocks by taking the collection of nodes it gets from `$MyData` (specifically, `$AllNodes`) and filters that collection against the `Role` property..</span></span>

## <a name="using-configuration-data-to-define-development-and-production-environments"></a><span data-ttu-id="bd69e-118">Med konfigurationsdata för att definiera miljöer för utveckling och produktion</span><span class="sxs-lookup"><span data-stu-id="bd69e-118">Using configuration data to define development and production environments</span></span>

<span data-ttu-id="bd69e-119">Nu ska vi titta på ett komplett exempel som använder en enkel konfiguration för att konfigurera både utveckling och produktion miljöer till en webbplats.</span><span class="sxs-lookup"><span data-stu-id="bd69e-119">Let's look at a complete example that uses a single configuration to set up both development and production environments of a website.</span></span> <span data-ttu-id="bd69e-120">I utvecklingsmiljön installeras både IIS och SQL Server på en enstaka noder.</span><span class="sxs-lookup"><span data-stu-id="bd69e-120">In the development environment, both IIS and SQL Server are installed on a single nodes.</span></span> <span data-ttu-id="bd69e-121">I produktionsmiljön, är IIS och SQL Server installerade på olika noder.</span><span class="sxs-lookup"><span data-stu-id="bd69e-121">In the production environment, IIS and SQL Server are installed on separate nodes.</span></span> <span data-ttu-id="bd69e-122">Vi använder konfigurationsdatafilen .psd1 för att ange data för två olika miljöer.</span><span class="sxs-lookup"><span data-stu-id="bd69e-122">We'll use a configuration data .psd1 file to specify the data for the two different environments.</span></span>

### <a name="configuration-data-file"></a><span data-ttu-id="bd69e-123">Konfigurationsdatafilen</span><span class="sxs-lookup"><span data-stu-id="bd69e-123">Configuration data file</span></span>

<span data-ttu-id="bd69e-124">Ska vi definiera miljödata utveckling och produktion i en fil med namnet `DevProdEnvData.psd1` på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="bd69e-124">We'll define the development and production environment data in a file named `DevProdEnvData.psd1` as follows:</span></span>

```powershell
@{

    AllNodes = @(

        @{
            NodeName        = "*"
            SQLServerName   = "MySQLServer"
            SqlSource       = "C:\Software\Sql"
            DotNetSrc       = "C:\Software\sxs"
        WebSiteName     = "New website"
        },

        @{
            NodeName        = "Prod-SQL"
            Role            = "MSSQL"
        },

        @{
            NodeName        = "Prod-IIS"
            Role            = "Web"
            SiteContents    = "C:\Website\Prod\SiteContents\"
            SitePath        = "\\Prod-IIS\Website\"
        },

        @{
            NodeName         = "Dev"
            Role             = "MSSQL", "Web"
            SiteContents     = "C:\Website\Dev\SiteContents\"
            SitePath         = "\\Dev\Website\"
        }
    )
}
```

### <a name="configuration-script-file"></a><span data-ttu-id="bd69e-125">Konfigurationsfilen för skript</span><span class="sxs-lookup"><span data-stu-id="bd69e-125">Configuration script file</span></span>

<span data-ttu-id="bd69e-126">Nu, i konfigurationen, som definieras i en `.ps1` filen, filtrerar vi de noder som vi definierade i `DevProdEnvData.psd1` efter deras roll (`MSSQL`, `Dev`, eller båda), och konfigurera dem enlighet med detta.</span><span class="sxs-lookup"><span data-stu-id="bd69e-126">Now, in the configuration, which is defined in a `.ps1` file, we filter the nodes we defined in `DevProdEnvData.psd1` by their role (`MSSQL`, `Dev`, or both), and configure them accordingly.</span></span>
<span data-ttu-id="bd69e-127">Utvecklingsmiljön har både SQL Server och IIS på en nod, medan produktionsmiljön har dem på två olika noder.</span><span class="sxs-lookup"><span data-stu-id="bd69e-127">The development environment has both the SQL Server and IIS on one node, while the production environment has them on two different nodes.</span></span>
<span data-ttu-id="bd69e-128">Innehållet på webbplatsen är också olika, enligt den `SiteContents` egenskaper.</span><span class="sxs-lookup"><span data-stu-id="bd69e-128">The site contents is also different, as specified by the `SiteContents` properties.</span></span>

<span data-ttu-id="bd69e-129">I slutet av konfigurationsskriptet som vi kallar konfigurationen (kompilera den till en MOF-dokument), skicka `DevProdEnvData.psd1` som den `$ConfigurationData` parametern.</span><span class="sxs-lookup"><span data-stu-id="bd69e-129">At the end of the configuration script, we call the configuration (compile it into a MOF document), passing `DevProdEnvData.psd1` as the `$ConfigurationData` parameter.</span></span>

><span data-ttu-id="bd69e-130">**Obs:** Den här konfigurationen kräver modulerna `xSqlPs` och `xWebAdministration` installeras på målnoden.</span><span class="sxs-lookup"><span data-stu-id="bd69e-130">**Note:** This configuration requires the modules `xSqlPs` and `xWebAdministration` to be installed on the target node.</span></span>

<span data-ttu-id="bd69e-131">Nu ska vi definiera konfigurationen i en fil med namnet `MyWebApp.ps1`:</span><span class="sxs-lookup"><span data-stu-id="bd69e-131">Let's define the configuration in a file named `MyWebApp.ps1`:</span></span>

```powershell
Configuration MyWebApp
{
    Import-DscResource -Module PSDesiredStateConfiguration
    Import-DscResource -Module xSqlPs
    Import-DscResource -Module xWebAdministration

    Node $AllNodes.Where{$_.Role -contains "MSSQL"}.NodeName
   {
        # Install prerequisites
        WindowsFeature installdotNet35
        {
            Ensure      = "Present"
            Name        = "Net-Framework-Core"
            Source      = "c:\software\sxs"
        }

        # Install SQL Server
        xSqlServerInstall InstallSqlServer
        {
            InstanceName = $Node.SQLServerName
            SourcePath   = $Node.SqlSource
            Features     = "SQLEngine,SSMS"
            DependsOn    = "[WindowsFeature]installdotNet35"

        }
   }

   Node $AllNodes.Where{$_.Role -contains "Web"}.NodeName
   {
        # Install the IIS role
        WindowsFeature IIS
        {
            Ensure       = 'Present'
            Name         = 'Web-Server'
        }

        # Install the ASP .NET 4.5 role
        WindowsFeature AspNet45
        {
            Ensure       = 'Present'
            Name         = 'Web-Asp-Net45'

        }

        # Stop the default website
        xWebsite DefaultSite
        {
            Ensure       = 'Present'
            Name         = 'Default Web Site'
            State        = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn    = '[WindowsFeature]IIS'

        }

        # Copy the website content
        File WebContent

        {
            Ensure          = 'Present'
            SourcePath      = $Node.SiteContents
            DestinationPath = $Node.SitePath
            Recurse         = $true
            Type            = 'Directory'
            DependsOn       = '[WindowsFeature]AspNet45'

        }


        # Create the new Website

        xWebsite NewWebsite

        {

            Ensure          = 'Present'
            Name            = $Node.WebSiteName
            State           = 'Started'
            PhysicalPath    = $Node.SitePath
            DependsOn       = '[File]WebContent'
        }

    }

}

MyWebApp -ConfigurationData DevProdEnvData.psd1
```

<span data-ttu-id="bd69e-132">När du kör den här konfigurationen skapas tre MOF-filer (en för var och en med namnet post i den **AllNodes** matris):</span><span class="sxs-lookup"><span data-stu-id="bd69e-132">When you run this configuration, three MOF files are created (one for each named entry in the **AllNodes** array):</span></span>

```
    Directory: C:\DscTests\MyWebApp


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:47 PM           2944 Prod-SQL.mof
-a----        3/31/2017   5:47 PM           6994 Dev.mof
-a----        3/31/2017   5:47 PM           5338 Prod-IIS.mof
```

## <a name="using-non-node-data"></a><span data-ttu-id="bd69e-133">Använda icke-nod-data</span><span class="sxs-lookup"><span data-stu-id="bd69e-133">Using non-node data</span></span>

<span data-ttu-id="bd69e-134">Du kan lägga till ytterligare nycklar till den **ConfigurationData** hash-tabell för data som inte är specifika för en nod.</span><span class="sxs-lookup"><span data-stu-id="bd69e-134">You can add additional keys to the **ConfigurationData** hashtable for data that is not specific to a node.</span></span>
<span data-ttu-id="bd69e-135">Följande konfiguration garanterar att finns två webbplatser.</span><span class="sxs-lookup"><span data-stu-id="bd69e-135">The following configuration ensures the presence of two websites.</span></span>
<span data-ttu-id="bd69e-136">Data för varje webbplats har definierats i den **AllNodes** matris.</span><span class="sxs-lookup"><span data-stu-id="bd69e-136">Data for each website are defined in the **AllNodes** array.</span></span>
<span data-ttu-id="bd69e-137">Filen `Config.xml` används för båda webbplatserna, så vi definiera den i en ytterligare nyckel med namnet `NonNodeData`.</span><span class="sxs-lookup"><span data-stu-id="bd69e-137">The file `Config.xml` is used for both websites, so we define it in an additional key with the name `NonNodeData`.</span></span>
<span data-ttu-id="bd69e-138">Observera att du kan ha så många ytterligare knappar som du vill ha och du kan kalla dem vad du vill.</span><span class="sxs-lookup"><span data-stu-id="bd69e-138">Note that you can have as many additional keys as you want, and you can name them anything you want.</span></span>
<span data-ttu-id="bd69e-139">`NonNodeData` inte är ett reserverat ord, det är precis vad vi valt att namnge den extra nyckeln.</span><span class="sxs-lookup"><span data-stu-id="bd69e-139">`NonNodeData` is not a reserved word, it is just what we decided to name the additional key.</span></span>

<span data-ttu-id="bd69e-140">Du har åtkomst till ytterligare nycklar med hjälp av en särskild variabel **$ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="bd69e-140">You access additional keys by using the special variable **$ConfigurationData**.</span></span>
<span data-ttu-id="bd69e-141">I det här exemplet `ConfigFileContents` nås med rad:</span><span class="sxs-lookup"><span data-stu-id="bd69e-141">In this example, `ConfigFileContents` is accessed with the line:</span></span>
```powershell
 Contents = $ConfigurationData.NonNodeData.ConfigFileContents
 ```
 <span data-ttu-id="bd69e-142">i den `File` resource block.</span><span class="sxs-lookup"><span data-stu-id="bd69e-142">in the `File` resource block.</span></span>


```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName           = “*”
            LogPath            = “C:\Logs”
        },

        @{
            NodeName = “VM-1”
            SiteContents = “C:\Site1”
            SiteName = “Website1”
        },


        @{
            NodeName = “VM-2”;
            SiteContents = “C:\Site2”
            SiteName = “Website2”
        }
    );

    NonNodeData =
    @{
        ConfigFileContents = (Get-Content C:\Template\Config.xml)
     }
}

configuration WebsiteConfig
{
    Import-DscResource -ModuleName xWebAdministration -Name MSFT_xWebsite

    node $AllNodes.NodeName
    {
        xWebsite Site
        {
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = “Present”
        }

        File ConfigFile
        {
            DestinationPath = $Node.SiteContents + “\\config.xml”
            Contents = $ConfigurationData.NonNodeData.ConfigFileContents
        }
    }
}
```


## <a name="see-also"></a><span data-ttu-id="bd69e-143">Se även</span><span class="sxs-lookup"><span data-stu-id="bd69e-143">See Also</span></span>
- [<span data-ttu-id="bd69e-144">Med hjälp av konfigurationsdata</span><span class="sxs-lookup"><span data-stu-id="bd69e-144">Using configuration data</span></span>](configData.md)
- [<span data-ttu-id="bd69e-145">Alternativ för autentiseringsuppgifter i konfigurationsdata</span><span class="sxs-lookup"><span data-stu-id="bd69e-145">Credentials Options in Configuration Data</span></span>](configDataCredentials.md)
- [<span data-ttu-id="bd69e-146">DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="bd69e-146">DSC Configurations</span></span>](configurations.md)
