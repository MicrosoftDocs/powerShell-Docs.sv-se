---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Avgränsa konfigurations- och miljödata
ms.openlocfilehash: 305a766fec81d4ea4afce187756188b067a2048b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080041"
---
# <a name="separating-configuration-and-environment-data"></a>Avgränsa konfigurations- och miljödata

>Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

Det kan vara praktiskt att dela de data som används i en DSC-konfiguration från själva-konfigurationen med hjälp av konfigurationsdata.
Du kan använda en enda konfiguration för flera miljöer genom att göra detta.

Exempelvis om du utvecklar ett program, kan du använda en konfiguration för utvecklings-och produktionsmiljöer och Använd konfigurationsdata för att ange data för varje miljö.

## <a name="what-is-configuration-data"></a>Vad är konfigurationsdata?

Konfigurationsdata är data som definieras i en hash-tabell och skickas till en DSC-konfiguration när du kompilerar den konfigurationen.

En detaljerad beskrivning av den **ConfigurationData** hash-tabell, se [med konfigurationsdata](configData.md).

## <a name="a-simple-example"></a>Ett enkelt exempel

Nu ska vi titta på ett väldigt enkelt exempel och se hur det fungerar.
Vi skapar en enda konfiguration som säkerställer att **IIS** finns på vissa noder och att **Hyper-V** finns på andra:

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

Den sista raden i det här skriptet kompilerar konfigurationen, skicka `$MyData` som värde **ConfigurationData** parametern.

Resultatet är att två MOF-filer skapas:

```
    Directory: C:\DscTests\MyDscConfiguration


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:09 PM           1968 VM-1.mof
-a----        3/31/2017   5:09 PM           1970 VM-2.mof
```

`$MyData` Anger två olika noder, var och en med sin egen `NodeName` och `Role`. Konfigurationen skapas dynamiskt **nod** block genom att utföra uppsättningen noder får från `$MyData` (mer specifikt `$AllNodes`) och filtrerar samlingen mot den `Role` egenskap...

## <a name="using-configuration-data-to-define-development-and-production-environments"></a>Med konfigurationsdata för att definiera miljöer för utveckling och produktion

Nu ska vi titta på ett komplett exempel som använder en enkel konfiguration för att konfigurera både utveckling och produktion miljöer till en webbplats. I utvecklingsmiljön installeras både IIS och SQL Server på en enstaka noder. I produktionsmiljön, är IIS och SQL Server installerade på olika noder. Vi använder konfigurationsdatafilen .psd1 för att ange data för två olika miljöer.

### <a name="configuration-data-file"></a>Konfigurationsdatafilen

Ska vi definiera miljödata utveckling och produktion i en fil med namnet `DevProdEnvData.psd1` på följande sätt:

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

### <a name="configuration-script-file"></a>Konfigurationsfilen för skript

Nu, i konfigurationen, som definieras i en `.ps1` filen, filtrerar vi de noder som vi definierade i `DevProdEnvData.psd1` efter deras roll (`MSSQL`, `Dev`, eller båda), och konfigurera dem enlighet med detta.
Utvecklingsmiljön har både SQL Server och IIS på en nod, medan produktionsmiljön har dem på två olika noder.
Innehållet på webbplatsen är också olika, enligt den `SiteContents` egenskaper.

I slutet av konfigurationsskriptet som vi kallar konfigurationen (kompilera den till en MOF-dokument), skicka `DevProdEnvData.psd1` som den `$ConfigurationData` parametern.

>**Obs:** Den här konfigurationen kräver modulerna `xSqlPs` och `xWebAdministration` installeras på målnoden.

Nu ska vi definiera konfigurationen i en fil med namnet `MyWebApp.ps1`:

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

När du kör den här konfigurationen skapas tre MOF-filer (en för var och en med namnet post i den **AllNodes** matris):

```
    Directory: C:\DscTests\MyWebApp


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:47 PM           2944 Prod-SQL.mof
-a----        3/31/2017   5:47 PM           6994 Dev.mof
-a----        3/31/2017   5:47 PM           5338 Prod-IIS.mof
```

## <a name="using-non-node-data"></a>Använda icke-nod-data

Du kan lägga till ytterligare nycklar till den **ConfigurationData** hash-tabell för data som inte är specifika för en nod.
Följande konfiguration garanterar att finns två webbplatser.
Data för varje webbplats har definierats i den **AllNodes** matris.
Filen `Config.xml` används för båda webbplatserna, så vi definiera den i en ytterligare nyckel med namnet `NonNodeData`.
Observera att du kan ha så många ytterligare knappar som du vill ha och du kan kalla dem vad du vill.
`NonNodeData` inte är ett reserverat ord, det är precis vad vi valt att namnge den extra nyckeln.

Du har åtkomst till ytterligare nycklar med hjälp av en särskild variabel **$ConfigurationData**.
I det här exemplet `ConfigFileContents` nås med rad:
```powershell
 Contents = $ConfigurationData.NonNodeData.ConfigFileContents
 ```
 i den `File` resource block.


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


## <a name="see-also"></a>Se även
- [Med hjälp av konfigurationsdata](configData.md)
- [Alternativ för autentiseringsuppgifter i konfigurationsdata](configDataCredentials.md)
- [DSC-konfigurationer](configurations.md)
