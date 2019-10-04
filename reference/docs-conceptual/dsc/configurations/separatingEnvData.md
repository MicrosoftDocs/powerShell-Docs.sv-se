---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Avgränsa konfigurations- och miljödata
ms.openlocfilehash: b16243fc9096f786a25ed20868e94a3aa85e403e
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942288"
---
# <a name="separating-configuration-and-environment-data"></a>Avgränsa konfigurations- och miljödata

>Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0

Det kan vara praktiskt att separera de data som används i en DSC-konfiguration från själva konfigurationen med hjälp av konfigurations data.
Genom att göra detta kan du använda en enda konfiguration för flera miljöer.

Om du till exempel utvecklar ett program kan du använda en konfiguration för både utvecklings-och produktions miljöer och använda konfigurations data för att ange data för varje miljö.

## <a name="what-is-configuration-data"></a>Vad är konfigurations data?

Konfigurations data är data som definieras i en hash-hash och skickas till en DSC-konfiguration när du kompilerar den konfigurationen.

En detaljerad beskrivning av **ConfigurationData** -hash-tabellen finns i [använda konfigurations data](configData.md).

## <a name="a-simple-example"></a>Ett enkelt exempel

Nu ska vi titta på ett mycket enkelt exempel för att se hur det fungerar.
Vi ska skapa en enda konfiguration som garanterar att **IIS** finns på vissa noder och att **Hyper-V** finns på andra:

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

Den sista raden i det här skriptet kompilerar konfigurationen och skickar `$MyData` den som **ConfigurationData** -parameter.

Resultatet är att två MOF-filer skapas:

```
    Directory: C:\DscTests\MyDscConfiguration


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:09 PM           1968 VM-1.mof
-a----        3/31/2017   5:09 PM           1970 VM-2.mof
```

`$MyData`anger två olika noder, var och en med `NodeName` sin `Role`egen och. Konfigurationen skapar automatiskt **Node** -block genom att ta med noderna från `$MyData` (särskilt, `$AllNodes` `Role` ) och filter som insamlingen mot egenskapen.

## <a name="using-configuration-data-to-define-development-and-production-environments"></a>Använda konfigurations data för att definiera utvecklings-och produktions miljöer

Nu ska vi titta på ett komplett exempel som använder en enda konfiguration för att konfigurera både utvecklings-och produktions miljöer för en webbplats. I utvecklings miljön är både IIS och SQL Server installerade på en enda nod. I produktions miljön är IIS och SQL Server installerade på separata noder. Vi använder en konfigurations data. psd1-fil för att ange data för de två olika miljöerna.

### <a name="configuration-data-file"></a>Konfigurations data fil

Vi definierar utvecklings-och produktions miljö data i en fil med namnet `DevProdEnvData.psd1` enligt följande:

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

### <a name="configuration-script-file"></a>Konfigurations skript fil

I-konfigurationen, som `.ps1` definieras i en fil, filtrerar vi sedan de noder som vi definierade i `DevProdEnvData.psd1` av deras roll (`MSSQL`, `Dev`eller båda) och konfigurerar dem därefter.
Utvecklings miljön har både SQL Server och IIS på en nod, medan produktions miljön har dem på två olika noder.
Webbplatsens innehåll är också olika, som anges av `SiteContents` egenskaperna.

I slutet av konfigurations skriptet anropar vi konfigurationen (kompilera den till ett MOF-dokument) och skickar `DevProdEnvData.psd1` den `$ConfigurationData` som parameter.

>**Obs:** Den här konfigurationen kräver att `xSqlPs` modulerna och `xWebAdministration` installeras på målnoden.

Vi definierar konfigurationen i en fil med namnet `MyWebApp.ps1`:

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

När du kör den här konfigurationen skapas tre MOF-filer (en för varje namngiven post i **AllNodes** -matrisen):

```
    Directory: C:\DscTests\MyWebApp


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:47 PM           2944 Prod-SQL.mof
-a----        3/31/2017   5:47 PM           6994 Dev.mof
-a----        3/31/2017   5:47 PM           5338 Prod-IIS.mof
```

## <a name="using-non-node-data"></a>Använda data som inte är noder

Du kan lägga till ytterligare nycklar i **ConfigurationData** -hashen för data som inte är en del av en nod.
Följande konfiguration säkerställer förekomsten av två webbplatser.
Data för varje webbplats definieras i **AllNodes** -matrisen.
Filen `Config.xml` används för båda webbplatserna, så vi definierar den i ytterligare en nyckel med namnet `NonNodeData`.
Observera att du kan ha så många ytterligare nycklar som du vill, och du kan ge dem ett namn som du vill.
`NonNodeData`är inte ett reserverat ord, det är bara det vi valde att ge den nya nyckeln.

Du får åtkomst till ytterligare nycklar med hjälp av den särskilda variabeln **$ConfigurationData**.
I det här exemplet `ConfigFileContents` kan du komma åt raden:
```powershell
 Contents = $ConfigurationData.NonNodeData.ConfigFileContents
 ```
 `File` i resurs blocket.


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


## <a name="see-also"></a>Se även
- [Använda konfigurations data](configData.md)
- [Alternativ för autentiseringsuppgifter i konfigurations data](configDataCredentials.md)
- [DSC-konfigurationer](configurations.md)
