---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
title: Nya scenarier och funktioner i WMF 5.1
ms.openlocfilehash: b00069aad7422f86d1462a62a6c4bc8a91e46705
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687001"
---
# <a name="new-scenarios-and-features-in-wmf-51"></a>Nya scenarier och funktioner i WMF 5.1

> Anm Den här informationen är preliminär och kan komma att ändras.

## <a name="powershell-editions"></a>PowerShell-utgåvor

Från och med version 5.1 finns PowerShell i olika utgåvor som anger olika funktionsuppsättningar och plattformskompatibilitet.

- **Desktop Edition:** Bygger på .NET Framework och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på fullständiga utgåvor av Windows, till exempel Server Core och Windows-skrivbordet.
- **Core Edition:** Bygger på .NET Core och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på begränsade utgåvor av Windows som Nano Server och Windows IoT.

**Läs mer om hur du använder PowerShell-utgåvor**

- [Fastställa utgåva av PowerShell med hjälp av $PSVersionTable](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [Filtrera resultatet för Get-Module av CompatiblePSEditions med hjälp av parametern PSEdition](/powershell/module/microsoft.powershell.core/get-module)
- [Förhindra körning av skript, såvida inte köras på en kompatibel version av PowerShell](/powershell/gallery/concepts/script-psedition-support)
- [Deklarera en modul kompatibilitet med specifika versioner av PowerShell](/powershell/gallery/concepts/module-psedition-support)

## <a name="catalog-cmdlets"></a>Katalog-cmdletar

Två nya cmdletar har lagts till i den [Microsoft.PowerShell.Security](/powershell/module/microsoft.powershell.security) modul; dessa generera och verifiera filerna för Windows-katalogen.

### <a name="new-filecatalog"></a>Ny FileCatalog
--------------------------------

Ny FileCatalog katalogfil en Windows för mappar och filer.
Den här katalogfilen innehåller hashvärden för alla filer i angiven sökväg.
Användare kan distribuera mapparna tillsammans med motsvarande katalogfil som representerar dessa mappar.
Den här informationen är användbar för att kontrollera om några ändringar har gjorts till mapparna sedan tiden för skapandet av katalogen.

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

Katalogen version 1 och 2 stöds.
Version 1 använder SHA1-hash-algoritm för att skapa värden; version 2 använder SHA256.
Katalogversion 2 stöds inte på *Windows Server 2008 R2* eller *Windows 7*.
Du bör använda katalogversion 2 på *Windows 8*, *Windows Server 2012*, och senare operativsystem.

![](../images/NewFileCatalog.jpg)

Detta skapar katalogfilen.

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

Att kontrollera integriteten för katalogfil (Pester.cat i ovanstående exempel), registrera den med hjälp av [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) cmdlet.

### <a name="test-filecatalog"></a>Test-FileCatalog
--------------------------------

Test-FileCatalog verifierar katalogen som representerar en uppsättning mappar.

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

Denna cmdlet Jämför alla filer hash-värden och deras relativa sökvägar i *catalog* med ettor på *disk*.
Om den identifierar eventuella matchningsfel mellan värden och sökvägar returnerar den status som *ValidationFailed*.
Användare kan hämta den här informationen med hjälp av den *-detaljerad* parametern.
Den visar även signering status för katalogen i *signatur* egenskap som motsvarar att anropa [Get-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Get-AuthenticodeSignature) cmdleten på katalogfilen.
Användare kan även hoppa över alla filer under verifieringen genom att använda den *- FilesToSkip* parametern.

## <a name="module-analysis-cache"></a>Module Analysis Cache

Från och med WMF 5.1 finns ger PowerShell kontroll över den fil som används för att cachelagra data om en modul, till exempel kommandon som du exporterar.

Det här cacheminnet lagras som standard i filen `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
Cachen läses vanligtvis vid start vid sökning efter ett kommando och skrivs i en bakgrundstråd någon gång när en modul har importerats.

Du kan ändra standardplatsen för cachen, ange den `$env:PSModuleAnalysisCachePath` miljövariabeln innan du startar PowerShell.
Ändringar i den här miljövariabeln påverkar endast underordnade processer.
Värdet ska namnge en fullständig sökväg (inklusive filnamnet) som PowerShell har behörighet att skapa och skriva filer.
Om du vill inaktivera filcachen det här värdet till en ogiltig plats, till exempel:

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

Detta anger sökvägen till en ogiltig enhet.
Om PowerShell inte kan skrivas till sökvägen, inget fel returneras, men du kan se Felrapportering med hjälp av en spårning:

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

När du skriver ut cacheminnet, kontrollerar PowerShell för moduler som inte längre finns för att undvika ett onödigt stort cache.
Ibland är kontrollerna inte önskvärt, då du kan inaktivera dem genom att ange:

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

Ange den här miljövariabeln börjar gälla omedelbart i den aktuella processen.

## <a name="specifying-module-version"></a>Ange Modulversion

I WMF 5.1 `using module` fungerar på samma sätt som andra modul-relaterade konstruktioner i PowerShell.
Tidigare fick du inte vill ange en viss modul-version. Om det finns flera versioner finns, resulterade detta i ett fel.

I WMF 5.1:

- Du kan använda [ModuleSpecification-konstruktor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).
Den här hashtabellen har samma format som `Get-Module -FullyQualifiedName`.

**Exempel:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

- Om det finns flera versioner av modulen, PowerShell använder den **samma lösning logik** som `Import-Module` och inte returneras ett fel – på samma sätt som när `Import-Module` och `Import-DscResource`.

## <a name="improvements-to-pester"></a>Förbättringar av lära

I WMF 5.1, versionen av Pester som levereras med PowerShell har uppdaterats från 3.3.5 till 3.4.0 med hjälp av commit https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e, vilket förbättrar beteende för Pester på Nano Server.

Du kan granska ändringarna i versionerna 3.3.5 3.4.0 genom att granska filen ChangeLog.md vid: https://github.com/pester/Pester/blob/master/CHANGELOG.md
