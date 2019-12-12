---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
title: Versionsinformation för WMF 5.x
ms.openlocfilehash: 3fc712dbcbe184c60ae248b260c8f6800f111fdd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416498"
---
# <a name="windows-management-framework-wmf-5x-release-notes"></a>Viktig information om Windows Management Framework (WMF) 5. x

## <a name="wmf-50-changes"></a>WMF 5,0-ändringar

- PowerShell 5,0 lägger till en ny strukturerad **informations** ström
- Förbättringar av DSC, inklusive fyra nya DSC-resurser:
  - WindowsFeatureSet
  - WindowsOptionalFeatureSet
  - ServiceSet
  - ProcessSet
- Lade till bara tillräckligt med administration för att aktivera rollbaserad administration via PowerShell-fjärrkommunikation
- PowerShell 5,0 utökar språket till att inkludera användardefinierade klasser och uppräkningar
- Förbättrade fel söknings funktioner i PowerShell ISE och ytterligare fjärrfelsökning
- PowerShellGet-och PackageManagement-modulerna har lagts till
- Förbättrat PowerShell-skript, loggning och avskrifter
- Lägg till cmdletar för kryptografiskt meddelande-syntax
- WMF 5,0 innehåller NetworkSwitchManager-modulen för Windows
- Modulen Microsoft. PowerShell. ODataUtils har lagts till
- Stöd för Software Inventory Logging (SIL) har lagts till
- Sever New eller Update-cmdletar som svar på användar förfrågningar och problem

## <a name="wmf-51-changes"></a>WMF 5,1-ändringar

WMF 5,1 innehåller komponenterna PowerShell, WMI, WinRM och Software Inventory Logging (SIL) som släpptes med Windows Server 2016. WMF 5,1 kan installeras på Windows 7, Windows 8,1, Windows Server 2008 R2, 2012 och 2012 R2, och innehåller flera förbättringar över WMF 5,0, inklusive:

- Nya cmdletar
- PowerShellGet-förbättringarna omfattar att framtvinga signerade moduler och installera JEA-moduler
- PackageManagement har lagt till stöd för containrar, CBS-installation, EXE-baserad installation, CAB-paket
- Felsökningsförbättringar för DSC- och PowerShell-klasser
- Säkerhetsförbättringar, inklusive framtvingning av katalogsignerade moduler som kommer från Pull-servern och när du använder PowerShellGet-cmdletar
- Svar på ett antal förfrågningar och problem från användare

> [!IMPORTANT]
> Innan du installerar WMF 5,1 på Windows Server 2008 eller Windows 7 kontrollerar du att WMF 3,0 inte är installerat. Mer information finns i [WMF 5,1-krav för Windows Server 2008 R2 SP1 och Windows 7 SP1](../setup/install-configure.md#wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1).

## <a name="powershell-editions"></a>PowerShell-utgåvor

Från och med version 5,1 är PowerShell tillgängligt i olika versioner som kännetecknar varierande funktions uppsättningar och plattformens kompatibilitet.

- **Desktop Edition:** bygger på .NET Framework och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på fullständiga utgåvor av Windows, till exempel Server Core och Windows Desktop.
- **Core Edition:** bygger på .NET Core och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på begränsade utgåvor av Windows som Nano Server och Windows IoT.

### <a name="learn-more-about-using-powershell-editions"></a>Lär dig mer om att använda PowerShell-versioner

- [Bestämma vilken version av PowerShell som körs med hjälp av $PSVersionTable](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [Filtrera get-module-resultat efter CompatiblePSEditions med parametern PSEdition](/powershell/module/microsoft.powershell.core/get-module)
- [Förhindra skript körning om den inte körs på en kompatibel version av PowerShell](/powershell/scripting/gallery/concepts/script-psedition-support)
- [Deklarera en moduls kompatibilitet för vissa PowerShell-versioner](/powershell/scripting/gallery/concepts/module-psedition-support)

## <a name="module-analysis-cache"></a>Modul analys-cache

Från och med WMF 5,1 ger PowerShell kontroll över filen som används för att cachelagra data om en modul, till exempel de kommandon som exporteras.

Som standard lagras cacheminnet i filen `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`. Cachen läses normalt vid start vid sökning efter ett kommando och skrivs i en bakgrunds tråd någon gång efter att en modul har importer ATS.

Om du vill ändra standard platsen för cacheminnet anger du `$env:PSModuleAnalysisCachePath`-miljövariabeln innan du startar PowerShell. Ändringar i denna miljö variabel påverkar bara underordnade processer. Värdet bör ge en fullständig sökväg (inklusive fil namnet) som PowerShell har behörighet att skapa och skriva filer. Om du vill inaktivera filcachen ställer du in det här värdet på en ogiltig plats, till exempel:

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

Detta anger sökvägen till en ogiltig enhet. Om PowerShell inte kan skriva till sökvägen returneras inget fel, men du kan se fel rapportering med hjälp av en spårning:

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

När du skriver ut cacheminnet söker PowerShell efter moduler som inte längre finns för att undvika en onödigt stor cache. Ibland är de här kontrollerna inte önskvärda, i så fall kan du inaktivera dem genom att ställa in:

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

Att ställa in den här miljövariabeln börjar gälla direkt i den aktuella processen.

## <a name="specifying-module-version"></a>Anger modul version

I WMF 5,1 fungerar `using module` på samma sätt som andra modulbaserade konstruktioner i PowerShell.
Tidigare hade du inget sätt att ange en viss version av modulen. om det finns flera versioner, resulterade det i ett fel.

I WMF 5,1:

- Du kan använda [ModuleSpecification-konstruktorn (hash)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).

  Den här hash-tabellen har samma format som `Get-Module -FullyQualifiedName`.

  **Exempel:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

- Om det finns flera versioner av modulen använder PowerShell **samma lösnings logik** som `Import-Module` och returnerar inte ett fel – samma beteende som `Import-Module` och `Import-DscResource`.

## <a name="improvements-to-pester"></a>Förbättringar av pester

I WMF 5,1 har den version av pester som medföljer PowerShell uppdaterats från 3.3.5 till 3.4.0.
Den här uppdateringen ger bättre beteende för pester på Nano Server.

Du kan granska ändringar av skadegörare genom att inspektera [ändringsloggen](https://github.com/pester/Pester/blob/master/CHANGELOG.md) i GitHub-lagringsplatsen.
