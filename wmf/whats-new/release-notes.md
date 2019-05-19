---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
title: WMF 5.x viktig information
ms.openlocfilehash: 8bdc423234cf0b104b72b1bee1de35e50783d8a4
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856401"
---
# <a name="windows-management-framework-wmf-5x-release-notes"></a>Windows Management Framework (WMF) 5.x viktig information

## <a name="wmf-50-changes"></a>Ändringar av WMF 5.0

- PowerShell 5.0 lägger till en ny strukturerade **Information** stream
- Förbättringar av DSC, inklusive fyra nya DSC-resurser:
  - WindowsFeatureSet
  - WindowsOptionalFeatureSet
  - ServiceSet
  - ProcessSet
- Har lagts till Just Enough Administration att aktivera rollbaserad administration via PowerShell-fjärrkommunikation
- PowerShell 5.0 utökar språk med användardefinierade klasser och uppräkningar
- Förbättrade felsökningsfunktioner i PowerShell ISE och har lagts till fjärrfelsökning
- Lagt till PowerShellGet och PackageManagement-moduler
- Utökad loggning för PowerShell-skript och betyg
- Lägga till syntaxen Cryptographic Message Syntax-cmdlets
- WMF 5.0 innehåller NetworkSwitchManager-modulen för Windows
- Lagt till modulen Microsoft.PowerShell.ODataUtils
- Stöd har lagts till för Software Inventory Logging (SIL)
- Ny server eller uppdatera cmdletar som svar på frågor och problem

## <a name="wmf-51-changes"></a>WMF 5.1 ändras

WMF 5.1 innehåller PowerShell, WMI, WinRM och Software Inventory Logging (SIL) komponenterna som släpptes med Windows Server 2016. WMF 5.1 kan installeras på Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 och 2012 R2, och tillhandahåller flera förbättringar över WMF 5.0, inklusive:

- Nya cmdletar
- PowerShellGet-förbättringarna omfattar att framtvinga signerade moduler och installera JEA-moduler
- PackageManagement har lagt till stöd för containrar, CBS-installation, EXE-baserad installation, CAB-paket
- Felsökningsförbättringar för DSC- och PowerShell-klasser
- Säkerhetsförbättringar, inklusive framtvingning av katalogsignerade moduler som kommer från Pull-servern och när du använder PowerShellGet-cmdletar
- Svar på ett antal förfrågningar och problem från användare

## <a name="powershell-editions"></a>PowerShell-utgåvor

Från och med version 5.1 finns finns PowerShell i olika utgåvor som anger olika funktionsuppsättningar och plattformskompatibilitet.

- **Desktop Edition:** Bygger på .NET Framework och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på fullständiga utgåvor av Windows, till exempel Server Core och Windows-skrivbordet.
- **Core Edition:** Bygger på .NET Core och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på begränsade utgåvor av Windows som Nano Server och Windows IoT.

### <a name="learn-more-about-using-powershell-editions"></a>Läs mer om hur du använder PowerShell-utgåvor

- [Fastställa utgåva av PowerShell med hjälp av $PSVersionTable](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [Filtrera resultatet för Get-Module av CompatiblePSEditions med hjälp av parametern PSEdition](/powershell/module/microsoft.powershell.core/get-module)
- [Förhindra körning av skript, såvida inte köras på en kompatibel version av PowerShell](/powershell/gallery/concepts/script-psedition-support)
- [Deklarera en modul kompatibilitet med specifika versioner av PowerShell](/powershell/gallery/concepts/module-psedition-support)

## <a name="module-analysis-cache"></a>Module Analysis Cache

Från och med WMF 5.1 finns ger PowerShell kontroll över den fil som används för att cachelagra data om en modul, till exempel kommandon som du exporterar.

Det här cacheminnet lagras som standard i filen `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`. Cachen läses vanligtvis vid start vid sökning efter ett kommando och skrivs i en bakgrundstråd någon gång när en modul har importerats.

Du kan ändra standardplatsen för cachen, ange den `$env:PSModuleAnalysisCachePath` miljövariabeln innan du startar PowerShell. Ändringar i den här miljövariabeln påverkar endast underordnade processer. Värdet ska namnge en fullständig sökväg (inklusive filnamnet) som PowerShell har behörighet att skapa och skriva filer. Om du vill inaktivera filcachen det här värdet till en ogiltig plats, till exempel:

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

Detta anger sökvägen till en ogiltig enhet. Om PowerShell inte kan skrivas till sökvägen, inget fel returneras, men du kan se Felrapportering med hjälp av en spårning:

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

När du skriver ut cacheminnet, kontrollerar PowerShell för moduler som inte längre finns för att undvika ett onödigt stort cache. Ibland är kontrollerna inte önskvärt, då du kan inaktivera dem genom att ange:

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

Versionen av Pester som levereras med PowerShell har blivit uppdaterad från 3.3.5 i WMF 5.1 till 3.4.0.
Den här uppdateringen kan bättre beteende för Pester på Nano Server.

Du kan granska ändringarna i beskrivet genom att granska den [ändringsloggen](https://github.com/pester/Pester/blob/master/CHANGELOG.md) i GitHub-lagringsplatsen.
