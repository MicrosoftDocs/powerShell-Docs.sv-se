---
description: Beskriver nya funktioner som ingår i Windows PowerShell 5,1.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/17/2018
online version: https://docs.microsoft.com/powershell/module/?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_PowerShell_5.1
ms.openlocfilehash: 567af048dd137c0287c6eba4ccc42a77055c0c92
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/21/2020
ms.locfileid: "93273206"
---
# <a name="about_windows_powershell_51"></a>about_Windows_PowerShell_5.1

## <a name="short-description"></a>KORT BESKRIVNING

Beskriver nya funktioner som ingår i Windows PowerShell 5,1.

## <a name="long-description"></a>LÅNG BESKRIVNING

Windows PowerShell 5,1 innehåller viktiga nya funktioner som utökar användningen, förbättrar dess användbarhet och gör att du kan styra och hantera Windows-baserade miljöer enklare och mer omfattande.

Windows PowerShell 5,1 är bakåtkompatibelt. Cmdlets, providers, moduler, snapin-moduler, skript, funktioner och profiler som har utformats för Windows PowerShell 4,0, Windows PowerShell 3,0 och Windows PowerShell 2,0 fungerar vanligt vis i Windows PowerShell 5,1 utan ändringar.

- Nya cmdlet:ar: lokala användare och grupper, Get-ComputerInfo
- PowerShellGet-förbättringarna omfattar att framtvinga signerade moduler och installera JEA-moduler
- PackageManagement har lagt till stöd för containrar, CBS-installation, EXE-baserad installation, CAB-paket
- Felsökningsförbättringar för DSC- och PowerShell-klasser
- Säkerhetsförbättringar, inklusive framtvingning av katalogsignerade moduler som kommer från Pull-servern och när du använder PowerShellGet-cmdletar
- Svar på ett antal förfrågningar och problem från användare

Windows PowerShell 5,1 installeras som standard på Windows Server 2016 och Windows 10. Om du vill installera Windows PowerShell 5,1 på Windows Server 2012 R2, Windows 8,1 Enterprise eller Windows 8,1 Pro, se [Installera och konfigurera WMF 5,1](/powershell/scripting/wmf/setup/install-configure).
Se till att läsa informationen om hämtningen och uppfyller alla system krav innan du installerar Windows Management Framework 5,1.

Du kan också läsa om ändringar i Windows PowerShell 5,1 i [Vad är nytt i Windows PowerShell](/powershell/scripting/windows-powershell/whats-new/what-s-new-in-windows-powershell-50).

## <a name="new-scenarios-and-features-in-wmf-51"></a>Nya scenarier och funktioner i WMF 5,1

> OBS! den här informationen är preliminär och kan komma att ändras.

### <a name="powershell-editions"></a>PowerShell-utgåvor
Från och med version 5.1 finns PowerShell i olika utgåvor som anger olika funktionsuppsättningar och plattformskompatibilitet.

- **Desktop Edition:** bygger på .NET Framework och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på fullständiga utgåvor av Windows, till exempel Server Core och Windows Desktop.
- **Core Edition:** bygger på .NET Core och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på begränsade utgåvor av Windows som Nano Server och Windows IoT.

**Lär dig mer om att använda PowerShell-versioner**

- [Bestämma vilken version av PowerShell som körs med hjälp av $PSVersionTable](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [Filtrera Get-Module resultat efter CompatiblePSEditions med parametern PSEdition](/powershell/module/microsoft.powershell.core/get-module)
- [Förhindra skript körning om den inte körs på en kompatibel version av PowerShell](/powershell/scripting/gallery/concepts/script-psedition-support)
- [Deklarera en moduls kompatibilitet för vissa PowerShell-versioner](/powershell/scripting/gallery/concepts/module-psedition-support)

### <a name="catalog-cmdlets"></a>Katalog-cmdletar

Två nya cmdletar har lagts till i [Microsoft. PowerShell. Security](/previous-versions/windows/powershell-scripting/hh847877(v=wps.640)) -modulen. dessa genererar och validerar Windows Catalog-filer.

#### <a name="new-filecatalog"></a>New-FileCatalog

New-FileCatalog skapar en Windows Catalog-fil för en uppsättning mappar och filer.
Den här katalog filen innehåller hash-värden för alla filer i angivna sökvägar. Användare kan distribuera en uppsättning mappar tillsammans med motsvarande katalog fil som representerar dessa mappar. Den här informationen är användbar för att verifiera om några ändringar har gjorts i mapparna sedan katalogen skapades.

```
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>]
 [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

Katalog version 1 och 2 stöds. Version 1 använder SHA1-hash-algoritmen för att skapa filhash-filer. version 2 använder SHA256. Katalog version 2 stöds inte i *Windows Server 2008 R2* eller *Windows 7*. Du bör använda katalog version 2 på *Windows 8* , *Windows Server 2012* och senare operativ system.

För att kontrol lera integriteten för katalog filen (Pester.cat i exemplet ovan), signera den med cmdleten [set-AuthenticodeSignature](/powershell/module/microsoft.powershell.security/set-authenticodesignature) .

#### <a name="test-filecatalog"></a>Test-FileCatalog

Test-FileCatalog verifierar katalogen som representerar en uppsättning mappar.

```
Test-FileCatalog [-Detailed] [-FilesToSkip <String[]>]
 [-CatalogFilePath] <String> [[-Path] <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

Denna cmdlet jämför alla filers hashar och deras relativa sökvägar som finns i *katalogen* med dem på *disk*. Om det upptäcks matchnings fel mellan filhashar och sökvägar returneras statusen som *ValidationFailed*. Användare kan hämta all den här informationen med hjälp av parametern *-detaljerad* . Den visar också signerings status för katalogen i egenskapen *signatur* som motsvarar anropet [Get-AuthenticodeSignature](/powershell/module/microsoft.powershell.security/get-authenticodesignature) -cmdlet i katalog filen. Användare kan även hoppa över alla filer under valideringen med hjälp av parametern *-FilesToSkip* .

### <a name="module-analysis-cache"></a>Modul analys-cache

Från och med WMF 5,1 ger PowerShell kontroll över filen som används för att cachelagra data om en modul, till exempel de kommandon som exporteras.

Som standard lagras cacheminnet i filen `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache` . Cachen läses normalt vid start vid sökning efter ett kommando och skrivs i en bakgrunds tråd någon gång efter att en modul har importer ATS.

Om du vill ändra standard platsen för cacheminnet anger du `$env:PSModuleAnalysisCachePath` miljövariabeln innan du startar PowerShell. Ändringar i denna miljö variabel påverkar bara underordnade processer. Värdet bör ge en fullständig sökväg (inklusive fil namnet) som PowerShell har behörighet att skapa och skriva filer. Om du vill inaktivera filcachen ställer du in det här värdet på en ogiltig plats, till exempel:

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

Detta anger sökvägen till en ogiltig enhet. Om PowerShell inte kan skriva till sökvägen returneras inget fel, men du kan se fel rapportering med hjälp av en spårning:

```powershell
Trace-Command -PSHost -Name Modules -Expression {
  Import-Module Microsoft.PowerShell.Management -Force
}
```

När du skriver ut cacheminnet söker PowerShell efter moduler som inte längre finns för att undvika en onödigt stor cache. Ibland är de här kontrollerna inte önskvärda, i så fall kan du inaktivera dem genom att ställa in:

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

Att ställa in den här miljövariabeln börjar gälla direkt i den aktuella processen.

### <a name="specifying-module-version"></a>Anger modul version

I WMF 5,1 `using module` fungerar samma sätt som för andra modulbaserade konstruktioner i PowerShell. Tidigare hade du inget sätt att ange en viss version av modulen. om det finns flera versioner, resulterade det i ett fel.

I WMF 5,1:

* Du kan använda [ModuleSpecification-konstruktorn (hash)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor).
  Den här hash-tabellen har samma format som `Get-Module -FullyQualifiedName` .

  **Exempel:**`using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

* Om det finns flera versioner av modulen använder PowerShell **samma lösnings logik** som `Import-Module` och returnerar inte ett fel – samma beteende som `Import-Module` och `Import-DscResource` .

### <a name="improvements-to-pester"></a>Förbättringar av pester

I WMF 5,1 har den version av pester som medföljer PowerShell uppdaterats från 3.3.5 till 3.4.0, med tillägget GitHub [PR # 484](https://github.com/pester/Pester/pull/484), vilket ger bättre beteende för pester på Nano Server.

Du kan granska ändringarna i versionerna 3.3.5 till 3.4.0 genom att granska ChangeLog.md-filen på: https://github.com/pester/Pester/blob/master/CHANGELOG.md

## <a name="keywords"></a>RESERVERADE

Vad är nytt i Windows PowerShell 5,1
