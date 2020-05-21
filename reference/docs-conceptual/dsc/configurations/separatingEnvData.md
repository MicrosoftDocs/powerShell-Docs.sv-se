---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Avgränsa konfigurations- och miljödata
ms.openlocfilehash: 076e17054cfa20fad5ca925df126e239a77268db
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692434"
---
# <a name="separating-configuration-and-environment-data"></a><span data-ttu-id="b6a20-103">Avgränsa konfigurations- och miljödata</span><span class="sxs-lookup"><span data-stu-id="b6a20-103">Separating configuration and environment data</span></span>

><span data-ttu-id="b6a20-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="b6a20-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="b6a20-105">Det kan vara praktiskt att separera de data som används i en DSC-konfiguration från själva konfigurationen med hjälp av konfigurations data.</span><span class="sxs-lookup"><span data-stu-id="b6a20-105">It can be useful to separate the data used in a DSC configuration from the configuration itself by using configuration data.</span></span>
<span data-ttu-id="b6a20-106">Genom att göra detta kan du använda en enda konfiguration för flera miljöer.</span><span class="sxs-lookup"><span data-stu-id="b6a20-106">By doing this, you can use a single configuration for multiple environments.</span></span>

<span data-ttu-id="b6a20-107">Om du till exempel utvecklar ett program kan du använda en konfiguration för både utvecklings-och produktions miljöer och använda konfigurations data för att ange data för varje miljö.</span><span class="sxs-lookup"><span data-stu-id="b6a20-107">For example, if you are developing an application, you can use one configuration for both development and production environments, and use configuration data to specify data for each environment.</span></span>

## <a name="what-is-configuration-data"></a><span data-ttu-id="b6a20-108">Vad är konfigurations data?</span><span class="sxs-lookup"><span data-stu-id="b6a20-108">What is configuration data?</span></span>

<span data-ttu-id="b6a20-109">Konfigurations data är data som definieras i en hash-hash och skickas till en DSC-konfiguration när du kompilerar den konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="b6a20-109">Configuration data is data that is defined in a hashtable and passed to a DSC configuration when you compile that configuration.</span></span>

<span data-ttu-id="b6a20-110">En detaljerad beskrivning av **ConfigurationData** -hash-tabellen finns i [använda konfigurations data](configData.md).</span><span class="sxs-lookup"><span data-stu-id="b6a20-110">For a detailed description of the **ConfigurationData** hashtable, see [Using configuration data](configData.md).</span></span>

## <a name="a-simple-example"></a><span data-ttu-id="b6a20-111">Ett enkelt exempel</span><span class="sxs-lookup"><span data-stu-id="b6a20-111">A simple example</span></span>

<span data-ttu-id="b6a20-112">Nu ska vi titta på ett mycket enkelt exempel för att se hur det fungerar.</span><span class="sxs-lookup"><span data-stu-id="b6a20-112">Let's look at a very simple example to see how this works.</span></span>
<span data-ttu-id="b6a20-113">Vi ska skapa en enda konfiguration som garanterar att **IIS** finns på vissa noder och att **Hyper-V** finns på andra:</span><span class="sxs-lookup"><span data-stu-id="b6a20-113">We'll create a single configuration that ensures that **IIS** is present on some nodes, and that **Hyper-V** is present on others:</span></span>

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

<span data-ttu-id="b6a20-114">Den sista raden i det här skriptet kompilerar konfigurationen och skickar den `$MyData` som **ConfigurationData** -parameter.</span><span class="sxs-lookup"><span data-stu-id="b6a20-114">The last line in this script compiles the configuration, passing `$MyData` as the value **ConfigurationData** parameter.</span></span>

<span data-ttu-id="b6a20-115">Resultatet är att två MOF-filer skapas:</span><span class="sxs-lookup"><span data-stu-id="b6a20-115">The result is that two MOF files are created:</span></span>

```
    Directory: C:\DscTests\MyDscConfiguration


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:09 PM           1968 VM-1.mof
-a----        3/31/2017   5:09 PM           1970 VM-2.mof
```

<span data-ttu-id="b6a20-116">`$MyData`anger två olika noder, var och en med sin egen `NodeName` och `Role` .</span><span class="sxs-lookup"><span data-stu-id="b6a20-116">`$MyData` specifies two different nodes, each with its own `NodeName` and `Role`.</span></span> <span data-ttu-id="b6a20-117">Konfigurationen skapar automatiskt **Node** -block genom att ta med noderna från `$MyData` (särskilt, `$AllNodes` ) och filter som insamlingen mot `Role` egenskapen.</span><span class="sxs-lookup"><span data-stu-id="b6a20-117">The configuration dynamically creates **Node** blocks by taking the collection of nodes it gets from `$MyData` (specifically, `$AllNodes`) and filters that collection against the `Role` property..</span></span>

## <a name="using-configuration-data-to-define-development-and-production-environments"></a><span data-ttu-id="b6a20-118">Använda konfigurations data för att definiera utvecklings-och produktions miljöer</span><span class="sxs-lookup"><span data-stu-id="b6a20-118">Using configuration data to define development and production environments</span></span>

<span data-ttu-id="b6a20-119">Nu ska vi titta på ett komplett exempel som använder en enda konfiguration för att konfigurera både utvecklings-och produktions miljöer för en webbplats.</span><span class="sxs-lookup"><span data-stu-id="b6a20-119">Let's look at a complete example that uses a single configuration to set up both development and production environments of a website.</span></span> <span data-ttu-id="b6a20-120">I utvecklings miljön är både IIS och SQL Server installerade på en enda nod.</span><span class="sxs-lookup"><span data-stu-id="b6a20-120">In the development environment, both IIS and SQL Server are installed on a single nodes.</span></span> <span data-ttu-id="b6a20-121">I produktions miljön är IIS och SQL Server installerade på separata noder.</span><span class="sxs-lookup"><span data-stu-id="b6a20-121">In the production environment, IIS and SQL Server are installed on separate nodes.</span></span> <span data-ttu-id="b6a20-122">Vi använder en konfigurations data. psd1-fil för att ange data för de två olika miljöerna.</span><span class="sxs-lookup"><span data-stu-id="b6a20-122">We'll use a configuration data .psd1 file to specify the data for the two different environments.</span></span>

### <a name="configuration-data-file"></a><span data-ttu-id="b6a20-123">Konfigurations data fil</span><span class="sxs-lookup"><span data-stu-id="b6a20-123">Configuration data file</span></span>

<span data-ttu-id="b6a20-124">Vi definierar utvecklings-och produktions miljö data i en fil med namnet `DevProdEnvData.psd1` enligt följande:</span><span class="sxs-lookup"><span data-stu-id="b6a20-124">We'll define the development and production environment data in a file named `DevProdEnvData.psd1` as follows:</span></span>

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

### <a name="configuration-script-file"></a><span data-ttu-id="b6a20-125">Konfigurations skript fil</span><span class="sxs-lookup"><span data-stu-id="b6a20-125">Configuration script file</span></span>

<span data-ttu-id="b6a20-126">I-konfigurationen, som definieras i en `.ps1` fil, filtrerar vi sedan de noder som vi definierade i `DevProdEnvData.psd1` av deras roll ( `MSSQL` , `Dev` eller båda) och konfigurerar dem därefter.</span><span class="sxs-lookup"><span data-stu-id="b6a20-126">Now, in the configuration, which is defined in a `.ps1` file, we filter the nodes we defined in `DevProdEnvData.psd1` by their role (`MSSQL`, `Dev`, or both), and configure them accordingly.</span></span>
<span data-ttu-id="b6a20-127">Utvecklings miljön har både SQL Server och IIS på en nod, medan produktions miljön har dem på två olika noder.</span><span class="sxs-lookup"><span data-stu-id="b6a20-127">The development environment has both the SQL Server and IIS on one node, while the production environment has them on two different nodes.</span></span>
<span data-ttu-id="b6a20-128">Webbplatsens innehåll är också olika, som anges av `SiteContents` egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="b6a20-128">The site contents is also different, as specified by the `SiteContents` properties.</span></span>

<span data-ttu-id="b6a20-129">I slutet av konfigurations skriptet anropar vi konfigurationen (kompilera den till ett MOF-dokument) och skickar den `DevProdEnvData.psd1` som `$ConfigurationData` parameter.</span><span class="sxs-lookup"><span data-stu-id="b6a20-129">At the end of the configuration script, we call the configuration (compile it into a MOF document), passing `DevProdEnvData.psd1` as the `$ConfigurationData` parameter.</span></span>

><span data-ttu-id="b6a20-130">**Obs:** Den här konfigurationen kräver att modulerna `xSqlPs` och `xWebAdministration` installeras på målnoden.</span><span class="sxs-lookup"><span data-stu-id="b6a20-130">**Note:** This configuration requires the modules `xSqlPs` and `xWebAdministration` to be installed on the target node.</span></span>

<span data-ttu-id="b6a20-131">Vi definierar konfigurationen i en fil med namnet `MyWebApp.ps1` :</span><span class="sxs-lookup"><span data-stu-id="b6a20-131">Let's define the configuration in a file named `MyWebApp.ps1`:</span></span>

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

<span data-ttu-id="b6a20-132">När du kör den här konfigurationen skapas tre MOF-filer (en för varje namngiven post i **AllNodes** -matrisen):</span><span class="sxs-lookup"><span data-stu-id="b6a20-132">When you run this configuration, three MOF files are created (one for each named entry in the **AllNodes** array):</span></span>

```
    Directory: C:\DscTests\MyWebApp


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:47 PM           2944 Prod-SQL.mof
-a----        3/31/2017   5:47 PM           6994 Dev.mof
-a----        3/31/2017   5:47 PM           5338 Prod-IIS.mof
```

## <a name="using-non-node-data"></a><span data-ttu-id="b6a20-133">Använda data som inte är noder</span><span class="sxs-lookup"><span data-stu-id="b6a20-133">Using non-node data</span></span>

<span data-ttu-id="b6a20-134">Du kan lägga till ytterligare nycklar i **ConfigurationData** -hashen för data som inte är en del av en nod.</span><span class="sxs-lookup"><span data-stu-id="b6a20-134">You can add additional keys to the **ConfigurationData** hashtable for data that is not specific to a node.</span></span>
<span data-ttu-id="b6a20-135">Följande konfiguration säkerställer förekomsten av två webbplatser.</span><span class="sxs-lookup"><span data-stu-id="b6a20-135">The following configuration ensures the presence of two websites.</span></span>
<span data-ttu-id="b6a20-136">Data för varje webbplats definieras i **AllNodes** -matrisen.</span><span class="sxs-lookup"><span data-stu-id="b6a20-136">Data for each website are defined in the **AllNodes** array.</span></span>
<span data-ttu-id="b6a20-137">Filen `Config.xml` används för båda webbplatserna, så vi definierar den i ytterligare en nyckel med namnet `NonNodeData` .</span><span class="sxs-lookup"><span data-stu-id="b6a20-137">The file `Config.xml` is used for both websites, so we define it in an additional key with the name `NonNodeData`.</span></span>
<span data-ttu-id="b6a20-138">Observera att du kan ha så många ytterligare nycklar som du vill, och du kan ge dem ett namn som du vill.</span><span class="sxs-lookup"><span data-stu-id="b6a20-138">Note that you can have as many additional keys as you want, and you can name them anything you want.</span></span>
<span data-ttu-id="b6a20-139">`NonNodeData`är inte ett reserverat ord, det är bara det vi valde att ge den nya nyckeln.</span><span class="sxs-lookup"><span data-stu-id="b6a20-139">`NonNodeData` is not a reserved word, it is just what we decided to name the additional key.</span></span>

<span data-ttu-id="b6a20-140">Du får åtkomst till ytterligare nycklar med hjälp av den särskilda variabeln **$ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="b6a20-140">You access additional keys by using the special variable **$ConfigurationData**.</span></span>
<span data-ttu-id="b6a20-141">I det här exemplet kan `ConfigFileContents` du komma åt raden:</span><span class="sxs-lookup"><span data-stu-id="b6a20-141">In this example, `ConfigFileContents` is accessed with the line:</span></span>

```powershell
 Contents = $ConfigurationData.NonNodeData.ConfigFileContents
 ```

 <span data-ttu-id="b6a20-142">i `File` resurs blocket.</span><span class="sxs-lookup"><span data-stu-id="b6a20-142">in the `File` resource block.</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName           = "*"
            LogPath            = "C:\Logs"
        },

        @{
            NodeName = "VM-1"
            SiteContents = "C:\Site1"
            SiteName = "Website1"
        },


        @{
            NodeName = "VM-2"
            SiteContents = "C:\Site2"
            SiteName = "Website2"
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
            Ensure       = "Present"
        }

        File ConfigFile
        {
            DestinationPath = $Node.SiteContents + "\\config.xml"
            Contents = $ConfigurationData.NonNodeData.ConfigFileContents
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="b6a20-143">Se även</span><span class="sxs-lookup"><span data-stu-id="b6a20-143">See Also</span></span>

- [<span data-ttu-id="b6a20-144">Använda konfigurations data</span><span class="sxs-lookup"><span data-stu-id="b6a20-144">Using configuration data</span></span>](configData.md)
- [<span data-ttu-id="b6a20-145">Alternativ för autentiseringsuppgifter i konfigurations data</span><span class="sxs-lookup"><span data-stu-id="b6a20-145">Credentials Options in Configuration Data</span></span>](configDataCredentials.md)
- [<span data-ttu-id="b6a20-146">DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="b6a20-146">DSC Configurations</span></span>](configurations.md)
