---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguration, tjänst, inställning
title: Skriva, kompilera och tillämpa en konfiguration
ms.openlocfilehash: fa4d98fd12202439ba7025fd8af3fa398653ca05
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404793"
---
> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="write-compile-and-apply-a-configuration"></a>Skriva, kompilera och tillämpa en konfiguration

Den här övningen visar hur du skapar och tillämpar en konfiguration med Desired State Configuration (DSC) från början till slut.
I följande exempel lära du dig att skriva och tillämpa en väldigt enkel konfiguration. Konfigurationen garanterar en ”HelloWorld.txt”-fil finns på den lokala datorn. Om du tar bort filen DSC kommer att återskapa den nästa gång den uppdaterar.

En översikt över vad DSC är och hur det fungerar, se [Desired State Configuration-översikt för utvecklare](../overview/overview.md).

## <a name="requirements"></a>Krav

Om du vill köra det här exemplet behöver du en dator med PowerShell 4.0 eller senare.

## <a name="write-the-configuration"></a>Skriva konfigurationen

En DSC [Configuration](configurations.md) är en särskild PowerShell-funktion som definierar hur du vill konfigurera en eller flera datorer (noder).

I PowerShell ISE eller andra PowerShell-redigerare, skriver du följande:

```powershell
Configuration HelloWorld {

    # Import the module that contains the File resource.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets to compile MOF files for, when this configuration is executed.
    Node 'localhost' {

        # The File resource can ensure the state of files, or copy them from a source to a destination with persistent updates.
        File HelloWorld {
            DestinationPath = "C:\Temp\HelloWorld.txt"
            Ensure = "Present"
            Contents   = "Hello World from DSC!"
        }
    }
}
```

Spara filen som ”HelloWorld.ps1”.

Definiera en konfiguration är som definierar en funktion. Den **nod** block anger målnoden som ska konfigureras i det här fallet `localhost`.

Konfigurationen anropar en [resurser](../resources/resources.md), `File` resurs. Resurser som utför arbete för att säkerställa en som Målnoden är i tillståndet som definieras av konfigurationen.

## <a name="compile-the-configuration"></a>Kompilera konfigurationen

För en DSC-konfiguration som ska tillämpas på en nod måste du först kompilera den till en MOF-fil.
Kör konfiguration, som en funktion ska kompilera en ”.mof”-fil för varje nod som definieras av den `Node` block.
För att köra konfigurationen, måste du *dot-källa* ”HelloWorld.ps1” skriptet i den aktuella omfattningen.
Mer information finns i [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).

*Dot-källa* ”HelloWorld.ps1” skriptet genom att skriva in sökvägen där du sparade den, efter den `. ` (punkt, utrymme). Du kan sedan köra konfigurationen genom att anropa den som en funktion.

```powershell
. C:\Scripts\WebsiteTest.ps1
HelloWolrd
```

Detta genererar följande utdata:

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a>Tillämpa konfigurationen

Nu när du har den kompilerade MOF, du kan tillämpa konfigurationen på målnoden (i det här fallet den lokala datorn) genom att anropa den [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.

Den `Start-DscConfiguration` cmdlet visar den [lokala Configuration Manager (LCM)](../managing-nodes/metaConfig.md), motorn i DSC att tillämpa konfigurationen.
LCM fungerar för att anropa DSC-resurser för att tillämpa konfigurationen.

Använda koden nedan för att köra den `Start-DSCConfiguration` cmdlet. Ange sökvägen till katalogen där din ”localhost.mof” lagras till det `-Path` parametern. Den `Start-DSCConfiguration` cmdlet genomsöks den katalog som anges för alla ”\<computername\>.mof” filer. Den `Start-DSCConfiguration` cmdlet försöker tillämpa varje ”.mof”-fil som hittas på datornamnet som anges av filnamnet (”localhost”, ”server01”, ”dc-02” osv.).

> [!NOTE]
> Om den `-Wait` parametern inte anges `Start-DSCConfiguration` skapar ett bakgrundsjobb för att utföra åtgärden. Anger den `-Verbose` parametern kan du titta på den **utförlig** resultatet av åtgärden. `-Wait`, och `-Verbose` är båda valfria parametrar.

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a>Testa konfigurationen

När den `Start-DSCConfiguration` cmdleten har slutförts, visas en ”HelloWorld.txt”-fil på den plats du angav. Du kan kontrollera innehållet med den [Get-innehåll](/powershell/module/microsoft.powershell.management/get-content) cmdlet.

Du kan också *testa* aktuell status med [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).

Utdata ska vara ”True” om noden är för närvarande är kompatibel med tillämpade konfigurationen.

```powershell
Test-DSCConfiguration
```

```output
True
```

```powershell
Get-Content -Path C:\Temp\HelloWorld.txt
```

```output
Hello World from DSC!
```

## <a name="re-applying-the-configuration"></a>Återanvänder konfigurationen

Du kan ta bort textfilen som skapats av din konfiguration om du vill se din konfiguration tillämpas igen. Användning de `Start-DSCConfiguration` cmdlet med den `-UseExisting` parametern. Den `-UseExisting` parametern instruerar `Start-DSCConfiguration` för att tillämpa igen filen ”current.mof”, som representerar de nyligen har tillämpat konfigurationen.

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a>Nästa steg

- Lär dig mer om DSC-konfigurationer på [DSC-konfigurationer](configurations.md).
- Se vilka DSC-resurser är tillgängliga och hur du skapar anpassade DSC-resurser på [DSC-resurser](../resources/resources.md).
- Hitta DSC-konfigurationer och resurser i den [PowerShell-galleriet](https://www.powershellgallery.com/).
