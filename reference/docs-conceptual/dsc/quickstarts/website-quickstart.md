---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Snabb start – skapa en webbplats med DSC
ms.openlocfilehash: d98607939ccd3cc5e660936d8c0a6d54fce7d65f
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942729"
---
> Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0

# <a name="quickstart---create-a-website-with-dsc"></a>Snabb start – skapa en webbplats med DSC

Den här övningen beskriver hur du skapar och tillämpar en Desired State Configuration (DSC)-konfiguration från början till slut.
Exemplet som vi ska använda ser till att en server har aktiverat funktionen `Web-Server` (IIS) och att innehållet för en enkel "Hello World"-webbplats finns i katalogen `inetpub\wwwroot` på den servern.

En översikt över vad DSC är och hur det fungerar finns i [Översikt över önskad tillstånds konfiguration för besluts fattare](../overview/decisionMaker.md).

## <a name="requirements"></a>Krav

Om du vill köra det här exemplet behöver du en dator som kör Windows Server 2012 eller senare och PowerShell 4,0 eller senare.

## <a name="write-and-place-the-indexhtm-file"></a>Skriv och placera filen index. htm

Först skapar vi HTML-filen som vi ska använda som webbplats innehåll.

I rotmappen skapar du en mapp med namnet `test`.

Skriv följande text i en text redigerare:

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

Spara detta som `index.htm` i mappen `test` som du skapade tidigare.

## <a name="write-the-configuration"></a>Skriv konfigurationen

En [DSC-konfiguration](../configurations/configurations.md) är en särskild PowerShell-funktion som definierar hur du vill konfigurera en eller flera mål datorer (noder).

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

Du kan se att det ser ut som en PowerShell-funktion, med tillägg av den nyckelords **konfiguration** som används före namnet på funktionen.

**Node** -blocket anger den målnod som ska konfigureras i det här `localhost`fallet.

Konfigurationen anropar två [resurser](../resources/resources.md), **WindowsFeature** och **fil**.
Resurser gör jobbet för att säkerställa att målnoden är i det tillstånd som definieras av konfigurationen.

## <a name="compile-the-configuration"></a>Kompilera konfigurationen

För att en DSC-konfiguration ska tillämpas på en nod måste den först kompileras till en MOF-fil.
Det gör du genom att köra konfigurationen som en funktion.
I en PowerShell-konsol navigerar du till samma mapp där du sparade konfigurationen och kör följande kommandon för att kompilera konfigurationen till en MOF-fil:

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

Den första raden gör konfigurations funktionen tillgänglig i-konsolen.
Den andra raden kör-konfigurationen.
Resultatet är att en ny mapp med namnet `WebsiteTest` skapas som en undermapp till den aktuella mappen.
Mappen `WebsiteTest` innehåller en fil med namnet `localhost.mof`.
Det är den här filen som sedan kan användas på målnoden.

## <a name="apply-the-configuration"></a>Tillämpa konfigurationen

Nu när du har kompilerat MOF kan du tillämpa konfigurationen på målnoden (i det här fallet den lokala datorn) genom att anropa cmdleten [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) .

@No__t-0-cmdleten anger den [lokala Configuration Manager (LCM)](../managing-nodes/metaConfig.md), som är en motor för DSC, för att tillämpa konfigurationen.
LCM fungerar som att anropa DSC-resurserna för att tillämpa konfigurationen.

I en PowerShell-konsol navigerar du till samma mapp där du sparade konfigurationen och kör följande kommando:

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a>Testa konfigurationen

Du kan anropa cmdleten [Get-DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) för att se om konfigurationen har slutförts.

Du kan också testa resultaten direkt, i det här fallet genom att bläddra till `http://localhost/` i en webbläsare.
Du bör se HTML-sidan Hello World som du skapade som första steg i det här exemplet.

## <a name="next-steps"></a>Nästa steg

- Lär dig mer om DSC-konfigurationer på [DSC-konfigurationer](../configurations/configurations.md).
- Se vilka DSC-resurser som är tillgängliga och hur du skapar anpassade DSC-resurser på [DSC-resurser](../resources/resources.md).
- Hitta DSC-konfigurationer och-resurser i [PowerShell-galleriet](https://www.powershellgallery.com/).