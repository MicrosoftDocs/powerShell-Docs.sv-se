---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galleri, PowerShell, cmdlet, psgallery
title: PowerShell-galleriet vanliga frågor
ms.openlocfilehash: 035681e108e1a3e05fe5d659d527ae1ad1c64cf4
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "80500577"
---
# <a name="frequently-asked-questions"></a>Vanliga frågor och svar

## <a name="what-is-a-powershell-module"></a>Vad är en PowerShell-modul?

En PowerShell-modul är ett återanvändbart paket som innehåller vissa PowerShell-funktioner. Allt i PowerShell (functions, variabler, DSC-resurser osv.) kan paketeras i moduler. Moduler är normalt mappar som innehåller vissa typer av filer som lagras på en angiven sökväg. Det finns några olika typer av PowerShell-moduler som finns där.

## <a name="what-is-a-powershell-script"></a>Vad är ett PowerShell-skript?

Ett PowerShell-skript är en serie kommandon som lagras i en. ps1-fil för att aktivera åter användning och delning. PowerShell-arbetsflöden är också PowerShell-skript, som innehåller en uppsättning aktiviteter och som tillhandahåller sekvenseringen för dessa aktiviteter. Mer information finns på [komma igång med PowerShell-arbetsflöde](https://technet.microsoft.com/library/jj134242.aspx).

## <a name="how-are-powershell-scripts-different-from-powershell-modules"></a>Hur skiljer sig PowerShell-skript från PowerShell-moduler?

Moduler är i allmänhet bättre för delning, men vi aktiverar skript delning för att göra det enklare för dig att bidra med arbets flöden och skript till communityn. Mer information finns i följande Bloggar:

- [Skriv inte skript, skriv PowerShell-moduler](https://blogs.technet.microsoft.com/heyscriptingguy/2011/06/27/dont-write-scripts-write-powershell-modules/)
- [Förstå PowerShell-moduler](https://blogs.technet.microsoft.com/heyscriptingguy/2015/07/10/understanding-powershell-modules/)

## <a name="how-can-i-publish-to-the-powershell-gallery"></a>Hur kan jag publicera till PowerShell-galleriet?

Du måste registrera ett konto i PowerShell-galleriet innan du kan publicera paket i galleriet. Detta beror på att publicerings paket kräver en NuGetApiKey, som anges vid registreringen. Registrera dig genom att använda ditt personliga konto, ditt arbets-eller skol konto för att logga in på PowerShell-galleriet. En enstaka registrerings process krävs när du loggar in för första gången.
Därefter är din NuGetApiKey tillgänglig på din profil sida.

När du har registrerat i galleriet använder du cmdletarna [Publish-module][] eller [Publish-script][] för att publicera ditt paket i galleriet. Mer information om hur du kör dessa cmdlets finns på fliken publicera eller läsa dokumentationen för [publicerings-][] och [publicerings skript][] .

**Du behöver inte registrera eller logga in på galleriet för att installera eller Spara paket.**

## <a name="i-received-failed-to-process-request-the-specified-api-key-is-invalid-or-does-not-have-permission-to-access-the-specified-package-the-remote-server-returned-an-error-403-forbidden-error-when-i-tried-to-publish-a-package-to-the-powershell-gallery-what-does-that-mean"></a>Jag fick "Det gick inte att bearbeta begäran. Den angivna API-nyckeln är ogiltig eller har inte behörighet att komma åt det angivna paketet. Fjärrservern returnerade ett fel: (403) tillåts inte. " fel när jag försökte publicera ett paket till PowerShell-galleriet. Vad innebär det?

Det här felet kan inträffa av följande orsaker:

- **Den angivna API-nyckeln är ogiltig.** Se till att du har angett en giltig API-nyckel från ditt konto. Visa din profil sida för att hämta din API-nyckel.
- **Det angivna paket namnet ägs inte av dig.** Om du har bekräftat att din API-nyckel är korrekt, kan det finnas redan ett paket med samma namn som det som du försöker använda. Paketet kan ha avvisats av ägaren, och i så fall visas det inte i några Sök resultat. Du kan kontrol lera om det redan finns ett paket med samma namn genom att öppna en webbläsare och navigera till paketets informations `https://www.powershellgallery.com/packages/<packageName>`sida:. Om du till exempel navigerar direkt `https://www.powershellgallery.com/packages/pester` till går du till pester-modulens informations sida, oavsett om den är listad eller inte. Om det redan finns ett paket med ett namn som är i konflikt och inte finns med i listan kan du:
  - Välj ett annat namn för ditt paket.
  - Kontakta ägare till det befintliga paketet.

## <a name="why-cant-i-sign-in-with-my-personal-account-but-i-could-sign-in-yesterday"></a>Varför kan jag inte logga in med mitt personliga konto, men jag kan logga in i igår?

Tänk på att ditt Galleri konto inte hanterar ändringar i ditt primära e-postalias.
Mer information finns i [Microsoft email alias](https://windows.microsoft.com/windows/outlook/add-alias-account).

## <a name="why-dont-i-see-all-the-gallery-packages-when-i-select-all-the-category-checkboxes-on-the-packages-tab"></a>Varför visas inte alla Galleri paket när jag markerar alla kryss rutor för kategori på fliken paket?

Genom att markera kryss rutan Kategori anger du "Jag vill se alla paket i den här kategorin". Endast paketen i de valda kategorierna kommer att visas. På samma sätt, genom att markera alla kryss rutor för kategori, anger du "Jag vill se alla paket i valfri kategori". Men vissa paket i galleriet tillhör inte någon av kategorierna i listan, så de visas inte i resultaten. Om du vill se alla paket i galleriet avmarkerar du alla kategorier eller väljer fliken paket igen.

## <a name="what-are-the-requirements-to-publish-a-module-to-the-powershell-gallery"></a>Vilka är kraven för att publicera en modul till PowerShell-galleriet?

Alla typer av PowerShell-moduler (skript moduler, binära moduler eller manifest) kan publiceras i galleriet. För att publicera en modul behöver PowerShellGet känna till några saker om den, version, beskrivning, författare och hur den licensieras. Den här informationen läses som en del av publicerings processen från *modul manifest* filen (. psd1), eller från värdet för cmdlet: en **LicenseUri** -parameter för [Publish-modul][] . Alla moduler som publicerats till galleriet måste ha modul manifest. Alla moduler som innehåller följande information i manifestet kan publiceras i galleriet:

- Version
- Beskrivning
- Författare
- En URI till modulens licens villkor, antingen som en del av **PrivateData** -avsnittet i manifestet eller i **LicenseUri** -parametern för cmdleten [Publish-module][] .

## <a name="how-do-i-create-a-correctly-formatted-module-manifest"></a>Hur gör jag för att skapa ett korrekt formaterat modul manifest?

Det enklaste sättet att skapa ett modul manifest är att köra cmdleten [New-ModuleManifest][] . I PowerShell 5,0 eller senare genererar New-ModuleManifest ett korrekt formaterat modul manifest med tomma fält för användbara metadata som **ProjectUri**, **LicenseUri**och **taggar**. Fyll bara i tomma eller Använd det genererade manifestet som ett exempel på korrekt formatering.

Använd cmdleten [test-ModuleManifest][] för att kontrol lera att alla obligatoriska metadatafält har fyllts i korrekt.

Om du vill uppdatera modulens manifest fil fält använder du cmdleten [Update-ModuleManifest][] .

## <a name="what-are-the-requirements-to-publish-a-script-to-the-gallery"></a>Vilka är kraven för att publicera ett skript i galleriet?

Alla typer av PowerShell-skript (skript eller arbets flöden) kan publiceras i galleriet. För att kunna publicera ett skript behöver PowerShellGet känna till några saker om det – version, beskrivning, författare och hur det är licensierat. Den här informationen läses som en del av publicerings processen från skript filens *PSScriptInfo* -avsnitt eller från värdet för cmdlet: en **LicenseUri** i [Publish-script][] . Alla skript som publiceras till galleriet måste ha metadatainformation. Alla skript som innehåller följande information i sitt PSScriptInfo-avsnitt kan publiceras i galleriet:

- Version
- Beskrivning
- Författare
- En URI till skriptets licens villkor, antingen som en del av **PSScriptInfo** -avsnittet i skriptet eller i **LicenseUri** -parametern för cmdleten [Publish-script][] .

## <a name="how-do-i-search"></a>Hur gör jag för att Sök?

Skriv det du söker i text rutan. Om du till exempel vill hitta moduler som är relaterade till Azure SQL skriver du bara "Azure SQL". Vår sökmotor söker efter dessa nyckelord i alla publicerade paket, inklusive titlar, beskrivningar och över metadata. Sedan, baserat på en viktad kvalitets poäng, visas närmaste matchningar. Du kan också söka efter ett särskilt fält med fält: "value"-syntax i Sök frågan för följande fält:

- Taggar
- Functions
- Cmdletar
- DscResources
- PowerShellVersion

Så när du till exempel söker efter PowerShellVersion: "2.0" visas endast resultat som är kompatibla med PowerShellVersion 2,0 (baserat på deras modul/skript manifest).

## <a name="how-do-i-create-a-correctly-formatted-script-file"></a>Hur gör jag för att skapa en korrekt formaterad skript fil?

Det enklaste sättet att skapa en korrekt formaterad skript fil är att köra cmdleten [New-ScriptFileInfo][] . I PowerShell 5,0 genererar New-ScriptFileInfo en korrekt formaterad skript fil med tomma fält för användbara metadata som **ProjectUri**, **LicenseUri**och **taggar**. Fyll bara i tomma eller Använd den genererade skript filen som ett exempel på korrekt formatering.

Använd cmdleten [test-ScriptFileInfo][] för att kontrol lera att alla obligatoriska metadatafält har fyllts i korrekt.

Om du vill uppdatera skriptets metadata-fält använder du cmdleten [Update-ScriptFileInfo][] .

## <a name="what-other-types-of-powershell-modules-exist"></a>Vilka andra typer av PowerShell-moduler finns?

Termen PowerShell-modul avser även de filer som implementerar faktiska funktioner. Filer för skript-modul (. psm1) innehåller PowerShell-kod. Filer för binär modul (. dll) innehåller kompilerad kod.

Här är ett sätt att tänka på detta: mappen som kapslar modulen är module-mappen. Mappen module kan innehålla ett modul manifest (. psd1) som beskriver mappens innehåll. De filer som faktiskt utför arbetet är skriptfiler (. psm1) och binärfiler (. dll). DSC-resurser finns i en speciell undermapp och implementeras som skriptfiler eller filer för binär modul.

Alla moduler i galleriet innehåller modul manifest och de flesta av de här modulerna innehåller skriptfiler eller filer för binär modul. Termen module kan vara förvirrande på grund av dessa olika betydelser. Om inget annat uttryckligen anges kan all användning av Word-modulen på den här sidan referera till mappen modul som innehåller dessa filer.

## <a name="how-does-packagemanagement-relate-to-powershellget-high-level-answer"></a>Hur relaterar PackageManagement till PowerShellGet? (Svar på hög nivå)

PackageManagement är ett gemensamt gränssnitt för att arbeta med alla paket hanterare. Om du arbetar med PowerShell-moduler, MSIs, ruby-Gems, NuGet-paket eller perl-moduler, bör du använda PackageManagement-kommandon (Find-Package och install-Package) för att hitta och installera dem. PackageManagement gör detta genom att ha en paket leverantör för varje paket hanterare som ansluter till PackageManagement. Leverantörer utför allt verkligt arbete; de hämtar innehåll från databaser och installerar innehållet lokalt. Ofta omsluts paket leverantörer runt de befintliga Package Manager-verktygen för en specifik paket typ.

PowerShellGet är paket hanteraren för PowerShell-paket. Det finns en PSModule-paketfil som exponerar PowerShellGet-funktionen via PackageManagement. Därför kan du antingen köra [install-module][] eller install-Package-Provider-PSModule för att installera en modul från PowerShell-galleriet. Vissa PowerShellGet-funktioner, inklusive [Update-module][] och [Publish-module][], kan inte nås via PackageManagement-kommandon.

I sammanfattning fokuserar PowerShellGet bara på att ha en förstklassig paket hanterings upplevelse för PowerShell-innehåll. PackageManagement fokuserar på att exponera alla paket hanterings upplevelser via en allmän uppsättning verktyg. Om du tycker att det här svaret inte uppfyller, finns det ett långt svar längst ned i det här dokumentet, i avsnittet **hur refererar PackageManagement faktiskt till PowerShellGet?** .

Mer information finns på [projekt sidan för PackageManagement](https://oneget.org/).

## <a name="how-does-nuget-relate-to-powershellget"></a>Hur relaterar NuGet till PowerShellGet?

PowerShell-galleriet är en modifierad version av [NuGet-galleriet](https://www.nuget.org/).
PowerShellGet använder NuGet-providern för att arbeta med NuGet-baserade databaser som PowerShell-galleriet.

Du kan använda PowerShellGet mot en giltig NuGet-lagringsplats eller fil resurs. Du behöver bara lägga till lagrings platsen genom att köra cmdleten [register-PSRepository][] .

## <a name="does-that-mean-i-can-use-nugetexe-to-work-with-the-gallery"></a>Innebär det att jag kan använda NuGet. exe för att arbeta med galleriet?

Ja.

## <a name="how-does-packagemanagement-actually-relate-to-powershellget-technical-details"></a>Hur hör PackageManagement faktiskt till PowerShellGet? (Teknisk information)

Under huven utnyttjar PowerShellGet kraftigt PackageManagement-infrastrukturen.

På PowerShell-cmdlet-lagret är [install-module][] faktiskt en tunn omslutning runt `Install-Package -Provider PSModule`.

I PackageManagement Package Provider-skiktet anropar PSModule-paket leverantören andra PackageManagement-paket leverantörer. Om du till exempel arbetar med NuGet-baserade gallerier (t. ex. PowerShell-galleriet) använder PSModule-paket leverantören NuGet-paketfilen för att arbeta med lagrings platsen.

![PowerShellGet-arkitektur](media/faqs/powershellgetArchitecture.png)

Bild 1: PowerShellGet-arkitektur

## <a name="what-is-required-to-run-powershellget"></a>Vad krävs för att köra PowerShellGet?

I allmänhet rekommenderar vi att du väljer den senaste versionen av PowerShellGet-modulen (Observera att .NET 4,5 krävs).

För **PowerShellGet**-modulen krävs **PowerShell version 3.0 eller senare**.

Det innebär att **PowerShellGet** kräver något av följande operativsystem:

- Windows 10
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows 7 SP1
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 SP1

**PowerShellGet** kräver också .NET Framework 4,5 eller senare. Du kan installera .NET Framework 4.5 eller senare [här](https://msdn.microsoft.com/library/5a4x27ek.aspx).

## <a name="is-it-possible-to-reserve-names-for-packages-that-will-be-published-in-future"></a>Är det möjligt att reservera namn för paket som ska publiceras i framtiden?

Det går inte att squat paket namn. Om du tycker att ett befintligt paket har tagit det namn som passar ditt paket, kan du försöka [kontakta ägaren till paketet](./how-to/working-with-packages/contacting-package-owners.md).
Om du inte fick svar inom några veckor kan du kontakta supporten så kommer PowerShell-galleriets teamet att titta på det.

## <a name="how-do-i-claim-ownership-for-packages"></a>Hur gör jag för att anspråk på ägarskapet för paket?

Se [Hantera paket ägare på PowerShellGallery.com](./how-to/publishing-packages/managing-package-owners.md) för mer information.

## <a name="how-do-i-deal-with-a-package-owner-who-is-violating-my-package-license"></a>Hur gör jag för att hantera en paket ägare som bryter mot paket licensen?

Vi uppmuntrar PowerShell-gruppen att samar beta för att lösa eventuella tvister som kan uppstå mellan paket ägare och ägare av andra paket. Vi har utformat en [lösning för tvistlösning](./how-to/getting-support/dispute-resolution.md) som vi ber dig att följa innan PowerShellGallery.com-administratörerna överersätter.

<!-- link references-->
[New-ModuleManifest]: /powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest
[Test-ModuleManifest]: /powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest
[Uppdatera – ModuleManifest]: /powershell/module/PowerShellGet/Update-ModuleManifest
[Installera-modul]: /powershell/module/PowershellGet/Install-Module
[New-ScriptFileInfo]: /powershell/module/PowershellGet/New-ScriptFileInfo
[Publicera-modul]: /powershell/module/PowershellGet/Publish-Module
[Publicera – skript]: /powershell/module/PowershellGet/Publish-Script
[Registrera – PSRepository]: /powershell/module/PowershellGet/Register-PSRepository
[Test-ScriptFileInfo]: /powershell/module/PowershellGet/Test-ScriptFileInfo
[Update-modul]: /powershell/module/PowershellGet/Update-Module
[Update-ScriptFileInfo]: /powershell/module/PowershellGet/Update-ScriptFileInfo
