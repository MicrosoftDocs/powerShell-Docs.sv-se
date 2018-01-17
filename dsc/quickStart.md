---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Desired State Configuration-Snabbstart
ms.openlocfilehash: e21017f24db8c90229063895c1a7e4c6f0546d0c
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="desired-state-configuration-quick-start"></a>Desired State Configuration-Snabbstart

Den här övningen går igenom hur du skapar och använda en önskad tillstånd Configuration DSC ()-konfiguration från början till slut.
Exemplet använder vi garanterar att en server har den `Web-Server` (IIS)-funktionen aktiverad och att innehållet för en enkel ”Hello World”-webbplats finns i den `intepub\wwwroot` på servern.

En översikt över DSC är och hur det fungerar, se [Desired Configuration översikt över för beslutsfattare](decisionMaker.md).

## <a name="requirements"></a>Krav

Om du vill köra det här exemplet behöver du en dator som kör Windows Server 2012 eller senare och PowerShell 4.0 eller senare.

## <a name="write-and-place-the-indexhtm-file"></a>Skriva och placera filen index.htm

Först ska vi skapa HTML-fil som vi ska använda som webbplatsens innehåll.

Skapa en mapp med namnet i din rotmapp `test`.

Skriv följande text i en textredigerare:

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

Spara den som `index.htm` i den `test` mappen som du skapade tidigare. 

## <a name="write-the-configuration"></a>Skriva konfigurationen

En [DSC-konfigurationen](configurations.md) är en särskild funktion i PowerShell som definierar hur du vill konfigurera en eller flera datorer (noder).

Skriv följande i PowerShell ISE:

```powershell
Configuration WebsiteTest {

    # Import the module that contains the resources we're using.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets this configuration will be applied to.
    Node 'localhost' {

        # The first resource block ensures that the Web-Server (IIS) feature is enabled.
        WindowsFeature WebServer {
            Ensure = "Present"
            Name   = "Web-Server"
        }

        # The second resource block ensures that the website content copied to the website root folder.
        File WebsiteContent {
            Ensure = 'Present'
            SourcePath = 'c:\test\index.htm'
            DestinationPath = 'c:\inetpub\wwwroot'
        }
    }
}
```

Spara filen som `WebsiteTest.ps1`.

Du kan se att det ser ut som en PowerShell-funktionen med nyckelordet **Configuration** använde före namnet på funktionen.

Den **nod** block anger målnoden som ska konfigureras i det här fallet `localhost`.

Konfigurationen anropar två [resurser](resources.md), [WindowsFeature](windowsFeatureResource.md) och [filen](fileResource.md).
Resurser som arbetar för att säkerställa som Målnoden är i tillståndet enligt konfigurationen.

## <a name="compile-the-configuration"></a>Kompilera konfiguration

För en DSC-konfiguration som ska tillämpas på en nod måste du först kompilera den till en MOF-fil.
Om du vill göra detta måste köra du konfigurationen som en funktion.
Navigera till samma mapp där du sparade konfigurationen i PowerShell-konsolen och kör följande kommandon för att kompilera konfiguration till en MOF-fil:

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

Detta genererar följande utdata:

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

Den första raden gör configuration-funktionen i konsolen.
Den andra raden körs konfigurationen.
Resultatet är att en ny mapp med namnet `WebsiteTest` skapas en undermapp i den aktuella mappen.
Den `WebsiteTest` mappen innehåller en fil med namnet `localhost.mof`.
Det är den här filen som sedan kan tillämpas på målnoden.

## <a name="apply-the-configuration"></a>Tillämpa konfigurationen

Nu när du har den kompilerade MOF kan du tillämpa konfigurationen till målnoden (i det här fallet den lokala datorn) genom att anropa den [Start DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration) cmdlet.

Den `Start-DscConfiguration` cmdlet talar om den [lokala Configuration Manager (MGM)](metaConfig.md), som är motorn för DSC att tillämpa konfigurationen.
MGM är den anropar DSC-resurser för att tillämpa konfigurationen.

Navigera till samma mapp där du sparade konfigurationen i PowerShell-konsolen och kör följande kommando:

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a>Testa konfigurationen

Du kan anropa den [Get-DscConfigurationStatus](/reference/5.1/PSDesiredStateConfiguration/Get-DscConfigurationStatus) för att se om konfigurationen har slutförts. 

Du kan också testa resultaten direkt, i det här fallet genom att bläddra till `http://localhost/` i en webbläsare.
Du bör se ”Hello World” HTML-sidan som du skapade som ett första steg i det här exemplet.

## <a name="next-steps"></a>Nästa steg

- Lär dig mer om DSC-konfigurationer på [DSC-konfigurationer](configurations.md).
- Se vilka DSC-resurser är tillgängliga och hur du skapar anpassade DSC-resurser på [DSC resurser](resources.md).
- Hitta DSC-konfigurationer och resurser i den [PowerShell-galleriet](https://www.powershellgallery.com/).



