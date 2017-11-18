---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "Avgränsa konfiguration och miljö data"
ms.openlocfilehash: 861a4cecc28b2d93b2cfa2743d47ee0e5025e1f4
ms.sourcegitcommit: 60c6f9d8cf316e6d5b285854e6e5641ac7648f3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2017
---
# <a name="separating-configuration-and-environment-data"></a>Avgränsa konfiguration och miljö data

>Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

Det kan vara praktiskt att dela de data som används i en DSC-konfiguration från konfigurationen sig själv med hjälp av konfigurationsdata.
Du kan använda en enda konfiguration för miljöer med flera genom att göra.

Till exempel om du utvecklar ett program, kan du använda en konfiguration för både utveckling och produktionsmiljöer och Använd konfigurationsdata för att ange data för varje miljö.

## <a name="what-is-configuration-data"></a>Vad är konfigurationsdata?

Konfigurationsdata är data som har definierats i en hash-tabell och skickats till DSC-konfigurationen när du kompilerar den konfigurationen.

En detaljerad beskrivning av den **ConfigurationData** hash-tabell, se [med konfigurationsdata](configData.md).

## <a name="a-simple-example"></a>Ett enkelt exempel

Nu ska vi titta på ett väldigt enkelt exempel för att se hur det fungerar. Skapar vi en enkel konfiguration som säkerställer att **IIS** finns på vissa noder och att **Hyper-V** finns på andra: 

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

Den sista raden i det här skriptet kompilerar konfigurationen, skicka `$MyData` som värdet **ConfigurationData** parameter.

Resultatet är att två MOF-filer skapas:

```
    Directory: C:\DscTests\MyDscConfiguration


Mode                LastWriteTime         Length Name                                                                                                                    
----                -------------         ------ ----                                                                                                                    
-a----        3/31/2017   5:09 PM           1968 VM-1.mof                                                                                                                
-a----        3/31/2017   5:09 PM           1970 VM-2.mof  
```
 
`$MyData`Anger två olika noder, med egna `NodeName` och `Role`. Konfigurationen skapas dynamiskt **nod** block med samling med noder som får från `$MyData` (särskilt `$AllNodes`) och filtrerar samlingen mot den `Role` egenskapen...

## <a name="using-configuration-data-to-define-development-and-production-environments"></a>Med hjälp av konfigurationsdata för att definiera utveckling och produktionsmiljöer

Nu ska vi titta på en komplett exempel som använder en enda konfiguration för att ställa in både utveckling och produktionsmiljöer till en webbplats. I utvecklingsmiljön installeras både IIS och SQL Server på en enda noder. I produktionsmiljön, är IIS och SQL Server installerade på olika noder. Vi använder en konfigurationsfil data .psd1 för att ange data för två olika miljöer.

 ### <a name="configuration-data-file"></a>Konfigurationsfilen för data

Ska vi definiera miljödata utveckling och produktion i en fil namd `DevProdEnvData.psd1` på följande sätt:

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

Nu i konfigurationen som har definierats i en `.ps1` fil, vi filtrera de noder som vi har definierat i `DevProdEnvData.psd1` med deras roll (`MSSQL`, `Dev`, eller båda), och konfigurera dem i enlighet med detta. Utvecklingsmiljön har både SQL Server och IIS på en nod, medan produktionsmiljön har dem på två olika noder. Plats-innehållet är också olika som anges av den `SiteContents` egenskaper.

I slutet av konfigurationsskript som vi kallar konfigurationen (kompilera den till en MOF-dokument), skicka `DevProdEnvData.psd1` som den `$ConfigurationData` parameter.

>**Obs:** den här konfigurationen krävs moduler `xSqlPs` och `xWebAdministration` installeras på målnoden.

Definiera konfigurationen i en fil med namnet `MyWebApp.ps1`:

```powershell
Configuration MyWebApp
{
    Import-DscResource -Module PSDesiredStateConfiguration
    Import-DscResource -Module xSqlPs
    Import-DscResource -Module xWebAdministration

    Node $AllNodes.Where{$_.Role -contains "MSSQL"}.Nodename
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

När du kör den här konfigurationen skapas tre MOF-filer (en för varje med namnet post i den **AllNodes** array):

```
    Directory: C:\DscTests\MyWebApp


Mode                LastWriteTime         Length Name                                                                                                                    
----                -------------         ------ ----                                                                                                                    
-a----        3/31/2017   5:47 PM           2944 Prod-SQL.mof                                                                                                            
-a----        3/31/2017   5:47 PM           6994 Dev.mof                                                                                                                 
-a----        3/31/2017   5:47 PM           5338 Prod-IIS.mof
```

## <a name="using-non-node-data"></a>Med hjälp av data-nod

Du kan lägga till ytterligare nycklar till den **ConfigurationData** hash-tabell för data som inte är specifika för en nod.
Följande konfiguration gör finns två webbplatser.
Data för varje webbplats har definierats i den **AllNodes** matris.
Filen `Config.xml` används för både webbplatser, så vi definiera den i nyckeln med namnet `NonNodeData`.
Observera att du kan ha valfritt antal ytterligare nycklar som du vill och ge dem vad du vill.
`NonNodeData`är inte ett reserverat ord, det är bara vad vi beslutat att ytterligare nyckeln namnet.

Du har åtkomst till ytterligare nycklar med hjälp av en särskild variabel **$ConfigurationData**.
I det här exemplet `ConfigFileContents` används med rad:
```powershell
 Contents = $ConfigurationData.NonNodeData.ConfigFileContents
 ```
 i den `File` resursen block.


```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName           = “*”
            LogPath            = “C:\Logs”
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
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = “Present”
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
- [Med konfigurationsdata](configData.md)
- [Alternativ för autentiseringsuppgifter i konfigurationsdata](configDataCredentials.md)
- [DSC-konfigurationer](configurations.md)

