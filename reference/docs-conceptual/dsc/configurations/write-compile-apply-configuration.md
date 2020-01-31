---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguration, tjänst, installation
title: Skriva, kompilera och tillämpa en konfiguration
ms.openlocfilehash: eb61e518762b9f13e617ecd4711bfef7a86814ec
ms.sourcegitcommit: ea7d87a7a56f368e3175219686dfa2870053c644
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/29/2020
ms.locfileid: "76818166"
---
> Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0

# <a name="write-compile-and-apply-a-configuration"></a>Skriva, kompilera och tillämpa en konfiguration

Den här övningen beskriver hur du skapar och tillämpar en Desired State Configuration (DSC)-konfiguration från början till slut.
I följande exempel får du lära dig hur du skriver och använder en mycket enkel konfiguration. Konfigurationen ser till att filen "HelloWorld. txt" finns på den lokala datorn. Om du tar bort filen kommer DSC att återskapa den nästa gången den uppdateras.

En översikt över vad DSC är och hur det fungerar finns i [Översikt över önskad tillstånds konfiguration för utvecklare](../overview/overview.md).

## <a name="requirements"></a>Krav

Om du vill köra det här exemplet behöver du en dator som kör PowerShell 4,0 eller senare.

## <a name="write-the-configuration"></a>Skriv konfigurationen

En DSC- [konfiguration](configurations.md) är en särskild PowerShell-funktion som definierar hur du vill konfigurera en eller flera mål datorer (noder).

I PowerShell ISE eller andra PowerShell-redigerare skriver du följande:

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

> ! Viktiga i mer avancerade scenarier där flera moduler måste importeras så att du kan arbeta med många DSC-resurser i samma konfiguration, se till att varje modul placeras på en separat rad med hjälp av `Import-DscResource`.
> Detta är enklare att underhålla i käll kontroll och krävs när du arbetar med DSC i Azure-tillstånds konfiguration.
>
> ```powershell
>  Configuration HelloWorld {
>
>   # Import the module that contains the File resource.
>   Import-DscResource -ModuleName PsDesiredStateConfiguration
>   Import-DscResource -ModuleName xWebAdministration
>
> ```

Spara filen som "HelloWorld. ps1".

Att definiera en konfiguration är som att definiera en funktion. **Node** -blocket anger den målnod som ska konfigureras i det här fallet `localhost`.

Konfigurationen anropar en [resurs](../resources/resources.md), `File` resursen. Resurser gör jobbet för att säkerställa att målnoden är i det tillstånd som definieras av konfigurationen.

## <a name="compile-the-configuration"></a>Kompilera konfigurationen

För att en DSC-konfiguration ska tillämpas på en nod måste den först kompileras till en MOF-fil.
Genom att köra konfigurationen, som en funktion, kompileras en ". MOF"-fil för varje nod som definieras av `Node` blocket.
För att kunna köra konfigurationen måste du *dot* -skriptet "HelloWorld. ps1" i det aktuella omfånget.
Mer information finns i [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).

<!-- markdownlint-disable MD038 -->
*Dot-källa* ditt "HelloWorld. ps1"-skript genom att skriva in sökvägen där du sparade den, efter `. ` (punkt, blank steg). Sedan kan du köra konfigurationen genom att anropa den som en funktion.
<!-- markdownlint-enable MD038 -->

```powershell
. C:\Scripts\HelloWorld.ps1
HelloWorld
```

Detta genererar följande utdata:

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a>Tillämpa konfigurationen

Nu när du har kompilerat MOF kan du tillämpa konfigurationen på målnoden (i det här fallet den lokala datorn) genom att anropa cmdleten [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) .

`Start-DscConfiguration`-cmdleten anger att den [lokala Configuration Manager (LCM)](../managing-nodes/metaConfig.md), motorn för DSC, ska tillämpa konfigurationen.
LCM fungerar som att anropa DSC-resurserna för att tillämpa konfigurationen.

Använd koden nedan för att köra `Start-DSCConfiguration`-cmdleten. Ange sökvägen till katalogen där din "localhost. MOF" lagras i `-Path`-parametern. `Start-DSCConfiguration` cmdleten söker igenom katalogen som anges för filerna "\<ComputerName\>. MOF". `Start-DSCConfiguration`-cmdleten försöker tillämpa varje ". MOF"-fil som den hittar till det ComputerName som anges av fil namnet ("localhost", "Server01", "DC-02" osv.).

> [!NOTE]
> Om parametern `-Wait` inte anges skapar `Start-DSCConfiguration` ett bakgrunds jobb för att utföra åtgärden. Genom att ange parametern `-Verbose` kan du se **utförlig** utdata för åtgärden. `-Wait`och `-Verbose` är båda valfria parametrar.

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a>Testa konfigurationen

När `Start-DSCConfiguration` cmdlet har slutförts bör du se filen "HelloWorld. txt" på den plats som du har angett. Du kan kontrol lera innehållet med cmdleten [Get-Content](/powershell/module/microsoft.powershell.management/get-content) .

Du kan också *testa* den aktuella statusen med hjälp av [test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).

Utdata ska vara "true" om noden för närvarande är kompatibel med den tillämpade konfigurationen.

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

## <a name="re-applying-the-configuration"></a>Tillämpar konfigurationen igen

Om du vill se hur konfigurationen tillämpas igen kan du ta bort text filen som skapats av din konfiguration. Använd `Start-DSCConfiguration`-cmdlet: en med parametern `-UseExisting`. Parametern `-UseExisting` instruerar `Start-DSCConfiguration` att tillämpa den aktuella. MOF-filen igen som representerar den senast tillämpade konfigurationen.

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a>Nästa steg

- Lär dig mer om DSC-konfigurationer på [DSC-konfigurationer](configurations.md).
- Se vilka DSC-resurser som är tillgängliga och hur du skapar anpassade DSC-resurser på [DSC-resurser](../resources/resources.md).
- Hitta DSC-konfigurationer och-resurser i [PowerShell-galleriet](https://www.powershellgallery.com/).
