---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Snabbstart – skapa en webbplats med DSC
ms.openlocfilehash: d98607939ccd3cc5e660936d8c0a6d54fce7d65f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079131"
---
> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="quickstart---create-a-website-with-dsc"></a>Snabbstart – skapa en webbplats med DSC

Den här övningen visar hur du skapar och tillämpar en konfiguration med Desired State Configuration (DSC) från början till slut.
Exemplet använder vi ser till att en server har den `Web-Server` (IIS)-funktionen aktiverad och som innehållet för en enkel ”Hello World”-webbplats finns i den `inetpub\wwwroot` katalogen i den här servern.

En översikt över vad DSC är och hur det fungerar, se [Desired State Configuration-översikt för beslutsfattare](../overview/decisionMaker.md).

## <a name="requirements"></a>Krav

Om du vill köra det här exemplet behöver du en dator som kör Windows Server 2012 eller senare och PowerShell 4.0 eller senare.

## <a name="write-and-place-the-indexhtm-file"></a>Skriva och placera filen index.htm

Först ska vi skapa HTML-fil som ska användas som webbplatsens innehåll.

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

En [DSC-konfiguration](../configurations/configurations.md) är en särskild PowerShell-funktion som definierar hur du vill konfigurera en eller flera datorer (noder).

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

Du kan se att det ser ut som en PowerShell-funktion med hjälp av nyckelordet **Configuration** använde före namnet på funktionen.

Den **nod** block anger målnoden som ska konfigureras i det här fallet `localhost`.

Konfigurationen anropar två [resurser](../resources/resources.md), **WindowsFeature** och **filen**.
Resurser som utför arbete för att säkerställa en som Målnoden är i tillståndet som definieras av konfigurationen.

## <a name="compile-the-configuration"></a>Kompilera konfigurationen

För en DSC-konfiguration som ska tillämpas på en nod måste du först kompilera den till en MOF-fil.
Om du vill göra detta måste köra du konfigurationen som en funktion.
Navigera till mappen där du sparade din konfiguration och kör följande kommandon för att kompilera konfigurationen till en MOF-fil i en PowerShell-konsol:

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

Den första raden gör configuration-funktionen som är tillgängliga i konsolen.
Den andra raden kör konfigurationen.
Resultatet är att en ny mapp med namnet `WebsiteTest` skapas som en undermapp i den aktuella mappen.
Den `WebsiteTest` mappen innehåller en fil med namnet `localhost.mof`.
Det är den här filen som sedan kan tillämpas på målnoden.

## <a name="apply-the-configuration"></a>Tillämpa konfigurationen

Nu när du har den kompilerade MOF, du kan tillämpa konfigurationen på målnoden (i det här fallet den lokala datorn) genom att anropa den [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.

Den `Start-DscConfiguration` cmdlet visar den [lokala Configuration Manager (LCM)](../managing-nodes/metaConfig.md), vilket är motorn i DSC att tillämpa konfigurationen.
LCM fungerar för att anropa DSC-resurser för att tillämpa konfigurationen.

I PowerShell-konsolen, gå till mappen där du sparade din konfiguration och kör följande kommando:

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a>Testa konfigurationen

Du kan anropa den [Get-DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) cmdlet för att se om konfigurationen har slutförts.

Du kan också testa resultaten direkt, i det här fallet genom att bläddra till `http://localhost/` i en webbläsare.
Du bör se ”Hello World” HTML-sidan som du skapade som ett första steg i det här exemplet.

## <a name="next-steps"></a>Nästa steg

- Lär dig mer om DSC-konfigurationer på [DSC-konfigurationer](../configurations/configurations.md).
- Se vilka DSC-resurser är tillgängliga och hur du skapar anpassade DSC-resurser på [DSC-resurser](../resources/resources.md).
- Hitta DSC-konfigurationer och resurser i den [PowerShell-galleriet](https://www.powershellgallery.com/).
