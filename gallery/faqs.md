---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: PowerShell-galleriet vanliga frågor och svar
ms.openlocfilehash: bcbb36a9ec60d88d1ef56fd270f0ae1862d5ca6b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084632"
---
# <a name="frequently-asked-questions"></a>Vanliga frågor och svar

## <a name="what-is-a-powershell-module"></a>Vad är en PowerShell-modul?

En PowerShell-modul är en återanvändbara paket som innehåller vissa PowerShell-funktioner. Allt innehåll i PowerShell (functions, variabler, DSC-resurser, osv.) kan paketeras i moduler. Moduler är oftast mappar som innehåller vissa typer av filer som lagras på en specifik sökväg. Det finns några olika typer av PowerShell-moduler där.

## <a name="what-is-a-powershell-script"></a>Vad är ett PowerShell-skript?

Ett PowerShell-skript är en serie kommandon som lagras i en .ps1-fil för att aktivera återanvändning och delning. PowerShell-arbetsflöden finns även PowerShell-skript som beskriver en uppsättning aktiviteter och ger sekvensering för aktiviteterna. Mer information finns på [komma igång med PowerShell-arbetsflöde](https://technet.microsoft.com/library/jj134242.aspx).

## <a name="how-are-powershell-scripts-different-from-powershell-modules"></a>Hur skiljer sig PowerShell-skript från PowerShell-moduler?

Moduler är vanligtvis bättre för att dela, men vi möjliggör delning av skriptet att göra det enklare för dig att bidra arbetsflöden och skript till diskussionsgruppen. Mer information finns i följande bloggar:

- [Skriv inte skript, skriva PowerShell-moduler](https://blogs.technet.microsoft.com/heyscriptingguy/2011/06/27/dont-write-scripts-write-powershell-modules/)
- [Förstå PowerShell-moduler](https://blogs.technet.microsoft.com/heyscriptingguy/2015/07/10/understanding-powershell-modules/)

## <a name="how-can-i-publish-to-the-powershell-gallery"></a>Hur kan jag publicera PowerShell-galleriet?

Du måste registrera ett konto i PowerShell-galleriet innan du kan publicera paket i galleriet. Det beror på att publicera paket kräver en NuGetApiKey som anges vid registreringen. Om du vill registrera, använder din personliga, arbets eller skolkonto för att logga in på PowerShell-galleriet. En process för registrering krävs när du loggar in för första gången. Därefter är din NuGetApiKey tillgänglig på din profilsida.

När du har registrerat i galleriet, använda den [Publicera modul][] eller [Publish-Script][] cmdletar för att publicera ditt paket i galleriet.
Gå till fliken Publish för mer information om hur du kör dessa cmdlet: ar, eller läsa den [Publicera modul][] och [Publish-Script][] dokumentation.

**Du behöver inte registrera eller logga in i galleriet för att installera eller spara paket.**

## <a name="i-received-failed-to-process-request-the-specified-api-key-is-invalid-or-does-not-have-permission-to-access-the-specified-package-the-remote-server-returned-an-error-403-forbidden-error-when-i-tried-to-publish-a-package-to-the-powershell-gallery-what-does-that-mean"></a>Jag har fått ”det gick inte att bearbeta begäran. ”Den angivna API-nyckeln är ogiltig eller har inte behörighet att få åtkomst till det angivna paketet”. Fjärrservern returnerade ett fel: (403) Forbidden." fel när jag försökte publicera ett paket till PowerShell-galleriet. Vad betyder det?

Det här felet kan inträffa av följande skäl:

- **Den angivna API-nyckeln är ogiltig.**
     Se till att du har angett en giltig API-nyckel från ditt konto. Visa din profilsida för att få din API-nyckel.
- **Det angivna paketnamnet äger som du inte.**
     Om du har bekräftat att din API-nyckel är korrekt, så det finns redan ett paket med samma namn som du vill använda. Paketet har inte finns i listan som ägare, i så fall den visas inte i alla sökresultat. För att avgöra om ett paket med samma namn redan finns, öppna en webbläsare och navigera till paketets informationssidan: `https://www.powershellgallery.com/packages/<packageName>`. Exempelvis kan gå direkt till `https://www.powershellgallery.com/packages/pester` tar dig till modulen Pester informationssida, oavsett om det inte finns i listan eller inte. Om ett paket med en motstridig namn finns redan och är inte finns i listan, kan du:
    - Välj ett annat namn för ditt paket.
    - Kontakta ägarna av det befintliga paketet.

## <a name="why-cant-i-sign-in-with-my-personal-account-but-i-could-sign-in-yesterday"></a>Varför inte kan jag logga in med mitt personliga konto, men jag kan logga in igår?

Tänk på att ditt konto i galleriet inte hantera ändringar till din primära e-postalias. Mer information finns i [Microsoft e-post-alias](https://windows.microsoft.com/windows/outlook/add-alias-account).

## <a name="why-dont-i-see-all-the-gallery-packages-when-i-select-all-the-category-checkboxes-on-the-packages-tab"></a>Varför ser jag gallery-paket när jag väljer kategorin kryssrutorna på fliken paket?

Genom att välja en kategori kryssruta, du anger ”jag skulle vilja se alla paket i den här kategorin”. Endast paket i valda kategorier visas. Så på samma sätt genom att välja alla kryssrutor för kategori, du om ”jag skulle vilja se alla paket i valfri kategori”. Men vissa paket i galleriet hör inte till någon av kategorierna, så att de inte att visas i resultaten. Avmarkera alla kategorier för att se alla paket i galleriet, eller välj fliken paket igen.

## <a name="what-are-the-requirements-to-publish-a-module-to-the-powershell-gallery"></a>Vilka är kraven för att publicera en modul till PowerShell-galleriet?

Alla typer av PowerShell-modulen (skriptmoduler, binära moduler eller manifest moduler) kan publiceras i galleriet.
Om du vill publicera en modul PowerShellGet behöver veta om ett par saker om den - version, beskrivning, författare och hur den är licensierad.
Den här informationen ska läsas som en del av publiceringsprocessen från den *modulmanifestet* (.psd1)-fil eller från värdet för den [Publicera modul][] cmdletens **LicenseUri** parameter.
Alla moduler som publicerats i galleriet måste ha modulmanifest.
Alla moduler som innehåller följande information i manifestet kan publiceras i galleriet:

- Version
- Beskrivning
- Författare
- En URI till licensvillkor av modulen, antingen som en del av den **PrivateData** avsnittet av manifestet eller i den **LicenseUri** -parametern för den [Publicera modul][] cmdlet.

## <a name="how-do-i-create-a-correctly-formatted-module-manifest"></a>Hur skapar jag en korrekt formaterad modulmanifestet?

Det enklaste sättet att skapa ett modulmanifest är att köra den [New-ModuleManifest][] cmdlet. I PowerShell 5.0 eller senare, New-ModuleManifest genererar en korrekt formaterad modulmanifestet med tomma fält för användbara metadata som **ProjectUri**, **LicenseUri**, och **taggar**. Helt enkelt fylls i automatiskt, eller Använd genererat manifest som ett exempel på rätt format.

Kontrollera att alla nödvändiga metadatafält har fyllts i korrekt genom att använda den [Test-ModuleManifest][] cmdlet.

Uppdatera modulen manifestfilen fälten med den [Update-ModuleManifest][] cmdlet.

## <a name="what-are-the-requirements-to-publish-a-script-to-the-gallery"></a>Vilka är kraven för att publicera ett skript i galleriet?

Alla typer av PowerShell-skript (skript eller arbetsflöden) kan publiceras i galleriet.
För att publicera ett skript, PowerShellGet behöver veta om ett par saker om den - version, beskrivning, författare och hur den är licensierad.
Den här informationen ska läsas som en del av publiceringsprocessen från skriptfilen *PSScriptInfo* avsnittet eller från värdet för den [Publish-Script][] cmdletens **LicenseUri**parametern.
Alla skript som publiceras i galleriet måste ha metadatainformation.
Alla skript som innehåller följande information under dess PSScriptInfo kan publiceras i galleriet:

- Version
- Beskrivning
- Författare
- En URI till licensvillkor av skript, antingen som en del av den **PSScriptInfo** avsnittet av skriptet eller i den **LicenseUri** -parametern för den [Publish-Script][] cmdlet.

## <a name="how-do-i-search"></a>Hur söker jag?

Ange vad du letar efter i textrutan. Till exempel om du vill hitta moduler som är relaterade till Azure SQL, skriver du ”azure sql”. Vår sökmotor söker efter dessa nyckelord i alla publicerade paket, inklusive rubriker, beskrivningar och i metadata. Sedan, baserat på en viktad kvalitet poäng, visas de närmaste matchningarna. Du kan också söka efter specifika fält med fält: ”värde”-syntax i sökfrågan för följande fält:

- Taggar
- Funktioner
- Cmdletar
- DscResources
- PowerShellVersion

I så fall till exempel när du söker efter PowerShellVersion: ”2.0” endast resultat som är kompatibla med PowerShellVersion 2.0 (baserat på deras modulen/skript-manifest) visas.

## <a name="how-do-i-create-a-correctly-formatted-script-file"></a>Hur skapar jag en korrekt formaterad skriptfil?

Det enklaste sättet att skapa en korrekt formaterad skriptfil är att köra den [New-ScriptFileInfo][] cmdlet. I PowerShell 5.0, New-ScriptFileInfo genererar en korrekt formaterad skriptfil med tomma fält för användbara metadata som **ProjectUri**, **LicenseUri**, och **taggar** . Helt enkelt fylls i automatiskt, eller använder du filen genererade skriptet som ett exempel på rätt format.

Kontrollera att alla nödvändiga metadatafält har fyllts i korrekt genom att använda den [Test-ScriptFileInfo][] cmdlet.

Uppdatera metadatafält skript med den [Update-ScriptFileInfo][] cmdlet.

## <a name="what-other-types-of-powershell-modules-exist"></a>Vad andra typer av PowerShell-moduler finns?

PowerShell-modulen termen avser även de filer som implementerar faktiska funktioner. Modulen skriptfiler (.psm1) innehåller PowerShell-kod. Modulen binära filer (.dll) innehåller kompilerad kod.

Här är ett sätt att göra det: mappen som innehåller modulen är modulmappen. Modulmappen kan innehålla ett modulmanifest (.psd1) som beskriver innehållet i mappen. De filer som gör jobbet är modulen skriptfiler (.psm1) och binära modul-filer (.dll). DSC-resurser finns i en viss undermapp och implementeras som modulen skriptfiler eller binär modulen filer.

Alla moduler i galleriet innehålla modulmanifest och de flesta av dessa moduler innehåller modulen skriptfiler eller binär modulen filer. Modulen termen kan vara förvirrande på grund av dessa olika funktioner. Om inget annat uttryckligen anges avser all användning av word-modulen på den här sidan modulmappen som innehåller filerna.

## <a name="how-does-packagemanagement-relate-to-powershellget-high-level-answer"></a>Hur relaterar PackageManagement till PowerShellGet? (Svar på hög nivå)

PackageManagement är ett gemensamt gränssnitt för att arbeta med valfri Pakethanteraren. Slutligen om du hanterar PowerShell-moduler, MSI: er, Ruby gems, NuGet-paket eller Perl moduler får ska du kunna använda Packagemanagements kommandon (Sök-Package och Install-Package) för att hitta och installera den. PackageManagement gör detta genom att låta en paket-provider för varje Pakethanteraren som ansluts till PackageManagement. Leverantörer göra allt det faktiska arbetet; de hämta innehåll från databaser och installera innehållet lokalt. Paketet providers omsluta ofta bara runt befintliga package manager-verktyg för en viss pakettyp.

PowerShellGet är Pakethanteraren för PowerShell-paket.
Det finns en provider för PSModule paket som innehåller PowerShellGet funktioner via PackageManagement.
Därför kan du antingen kör [Install-Module][] eller Install-Package-Provider PSModule installera en modul från PowerShell-galleriet.
Vissa PowerShellGet-funktioner, inklusive [Update-Module][] och [Publicera modul][], inte kan nås via PackageManagement-kommandon.

Sammanfattningsvis fokuserar PowerShellGet endast på att ha en hanteringsupplevelse för premium-paketet för PowerShell-innehåll. PackageManagement fokuserar på att exponera alla paket-hanteringsupplevelser via en allmän uppsättning verktyg. Om du hittar det här svaret unsatisfying, det finns ett långt svar längst ned i det här dokumentet i den **hur relaterar faktiskt PackageManagement till PowerShellGet?** avsnittet.

Mer information finns på den [PackageManagement projektsida](https://oneget.org/).

## <a name="how-does-nuget-relate-to-powershellget"></a>Hur relaterar NuGet till PowerShellGet?

PowerShell-galleriet är en modifierad version av den [NuGet-galleriet](https://www.nuget.org/). PowerShellGet använder NuGet-providern för att arbeta med NuGet baserat databaserna som PowerShell-galleriet.

Du kan använda PowerShellGet mot någon giltig NuGet lagringsplats eller filresurs. Du behöver bara lägga till databasen genom att köra den [Register-PSRepository][] cmdlet.

## <a name="does-that-mean-i-can-use-nugetexe-to-work-with-the-gallery"></a>Betyder det att jag kan använda NuGet.exe för att arbeta med galleriet?

Ja.

## <a name="how-does-packagemanagement-actually-relate-to-powershellget-technical-details"></a>Hur relaterar faktiskt PackageManagement till PowerShellGet? (Teknisk information)

Under huven utnyttjar PowerShellGet kraftigt PackageManagement infrastruktur.

I PowerShell-cmdlet-lagret [Install-Module][] är faktiskt en tunn adapter Install-Package-providern PSModule.

I provider-lagret PackageManagement paketet anrop PSModule paketets leverantör faktiskt till andra leverantörer av PackageManagement-paketet. När du arbetar med NuGet-baserade gallerier (till exempel PowerShell-galleriet) använder PSModule paketet providern exempelvis NuGet-paketet providern för att arbeta med databasen.

![PowerShellGet-arkitektur](Images/powershellgetArchitecture.png)

Bild 1: PowerShellGet-arkitektur

## <a name="what-is-required-to-run-powershellget"></a>Vad krävs för att köra PowerShellGet?

I allmänhet rekommenderar vi väljer den senaste versionen av modulen PowerShellGet (Observera att det kräver .NET 4.5).

Den **PowerShellGet** modulen kräver **PowerShell version 3.0 eller senare**.

Därför **PowerShellGet** kräver något av följande operativsystem:

- Windows 10
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows 7 SP1
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 SP1

**PowerShellGet** även kräver .NET Framework 4.5 eller senare. Du kan installera .NET Framework 4.5 eller senare från [här](https://msdn.microsoft.com/library/5a4x27ek.aspx).

## <a name="is-it-possible-to-reserve-names-for-packages-that-will-be-published-in-future"></a>Är det möjligt att reservera namn för paket som kommer att publiceras i framtiden?

Det går inte att låg paketnamn. Om du anser att ett befintligt paket har vidtagit de namn som passar ditt paket mer, försök [att kontakta ägaren av paketet](./how-to/working-with-packages/contacting-package-owners.md). Om du inte fått svar inom ett par veckor, kan du kontakta supporten och PowerShell-galleriet-teamet kommer att se den.

## <a name="how-do-i-claim-ownership-for-packages"></a>Hur gör jag anspråk på äganderätt för paket?

Kolla in [hantera paket ägare av PowerShellGallery.com](./how-to/publishing-packages/managing-package-owners.md) mer information.

## <a name="how-do-i-deal-with-a-package-owner-who-is-violating-my-package-license"></a>Hur jag jobbar med en paket-ägare som bryter mot min paketlicensen?

Vi rekommenderar att PowerShell-communityn kan samverka för att lösa eventuella tvister som uppstår mellan paketet ägare och ägare av andra paket.  Vi har särskild en [tvist lösningsprocessen](./how-to/getting-support/dispute-resolution.md) som vi be dig att följa innan PowerShellGallery.com administratörer intercede.

[New-ModuleManifest]: /powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest
[Test-ModuleManifest]: /powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest
[Update-ModuleManifest]: /powershell/module/Microsoft.PowerShell.Core/Update-ModuleManifest

[Install-Module]: /powershell/module/PowershellGet/Install-Module
[New-ScriptFileInfo]: /powershell/module/PowershellGet/New-ScriptFileInfo
[Publicera modul]: /powershell/module/PowershellGet/Publish-Module
[Publish-Script]: /powershell/module/PowershellGet/Publish-Script
[Register-PSRepository]: /powershell/module/PowershellGet/Register-PSRepository
[Test-ScriptFileInfo]: /powershell/module/PowershellGet/Test-ScriptFileInfo
[Update-Module]: /powershell/module/PowershellGet/Update-Module
[Update-ScriptFileInfo]: /powershell/module/PowershellGet/Update-ScriptFileInfo
