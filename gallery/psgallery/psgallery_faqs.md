---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: galleriet, powershell, cmdlet, psgallery
title: psgallery_faqs
ms.openlocfilehash: f00372d75b3e73bdc1499c3a2c8895bffb0902f9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="frequently-asked-questions"></a>Vanliga frågor och svar

## <a name="what-is-a-powershell-module"></a>Vad är en PowerShell-modul?

En PowerShell-modul är en återanvändbara paket som innehåller alla funktioner i PowerShell. Allt innehåll i PowerShell (funktion, variabler, DSC-resurser, etc.) kan paketeras i moduler. Moduler normalt mapparna som innehåller vissa typer av filer som lagras på en angiven sökväg. Det finns några olika typer av PowerShell-moduler där.

## <a name="what-is-a-powershell-script"></a>Vad är ett PowerShell-skript?

Ett PowerShell-skript är en serie kommandon som lagras i en .ps1-fil för att aktivera återanvändning och delning. PowerShell-arbetsflöden är också PowerShell-skript som beskriver en uppsättning uppgifter och ange ordningsföljd för dessa aktiviteter. Mer information finns [komma igång med PowerShell-arbetsflöde](https://technet.microsoft.com/library/jj134242.aspx).

## <a name="how-are-powershell-scripts-different-from-powershell-modules"></a>Vad är PowerShell-skript från PowerShell-moduler?

Moduler är vanligtvis bättre för att dela, men vi aktiverar delning av skriptet att göra det enklare att bidra med arbetsflöden och skript till gruppen. Mer information finns i följande bloggar:

- [Skriv inte skript, Skriv PowerShell-moduler](https://blogs.technet.microsoft.com/heyscriptingguy/2011/06/27/dont-write-scripts-write-powershell-modules/)
- [Förstå PowerShell-moduler](https://blogs.technet.microsoft.com/heyscriptingguy/2015/07/10/understanding-powershell-modules/)

## <a name="how-can-i-publish-to-the-powershell-gallery"></a>Hur kan publicera till PowerShell-galleriet?

Du måste registrera ett konto i PowerShell-galleriet innan du kan publicera objekt i galleriet. Det beror på att publicera objekt kräver en NuGetApiKey som tillhandahålls vid registreringen. Om du vill registrera, använder din personliga arbete eller skolkonto för att logga in i PowerShell-galleriet. En enstaka registreringsprocessen krävs när du loggar in för första gången. Därefter kan är din NuGetApiKey tillgänglig på din profilsida.

När du har registrerat i galleriet, använda den [publicera modulen](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) eller [publicera skriptet](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) -cmdletar för att publicera dina objekt i galleriet. Gå till fliken Publicera mer information om hur du kör dessa cmdletar, eller läsa den [publicera modulen](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) och [publicera skript](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) dokumentation.

**Du behöver inte registrera dig eller logga in i galleriet så att installera eller spara objekt.**

## <a name="i-received-failed-to-process-request-the-specified-api-key-is-invalid-or-does-not-have-permission-to-access-the-specified-package-the-remote-server-returned-an-error-403-forbidden-error-when-i-tried-to-publish-an-item-to-the-powershell-gallery-what-does-that-mean"></a>Jag har fått ”kunde inte bearbeta begäran. ”Den angivna API-nyckeln är ogiltig eller har inte behörighet att komma åt det angivna paketet”. Fjärrservern returnerade ett fel: (403) nekad ”. fel när jag försöker publicera ett objekt till PowerShell-galleriet. Vad betyder det?

Det här felet kan inträffa av följande skäl:

- **Den angivna API-nyckeln är ogiltig.**
     Se till att du har angett giltiga API-nyckeln från ditt konto. Visa din profilsida för att få din API-nyckel.
- **Det angivna objektnamnet är inte ägs av dig.**
     Om du har bekräftat att din API-nyckel är korrekt och kanske redan finns ett objekt med samma namn som du vill använda. Objektet kan ha varit olistade som ägare, i så fall visas den inte i någon sökresultat. För att fastställa om det redan finns ett objekt med samma namn, öppna en webbläsare och gå till objektets informationssidan: `https://www.powershellgallery.com/packages/<itemName>`. Till exempel gå direkt till `https://www.powershellgallery.com/packages/pester` tar dig vidare till modulen Pester informationssidan om det inte visas eller inte. Om ett objekt med ett motstridiga namn finns redan och är inte finns i listan, kan du:
    - Välj ett annat namn för objektet.
    - Kontakta ägarna av det befintliga objektet.

## <a name="why-cant-i-sign-in-with-my-personal-account-but-i-could-sign-in-yesterday"></a>Varför inte kan jag logga in med Mina personliga konto men jag kan inte logga in igår?

Tänk på att ditt konto i galleriet inte hantera ändringar i din primära e-postalias. Mer information finns i [Microsoft e-post-alias](https://windows.microsoft.com/windows/outlook/add-alias-account).

## <a name="why-dont-i-see-all-the-gallery-items-when-i-select-all-the-category-checkboxes-on-the-items-tab"></a>Varför visas inte alla galleriobjekt när du markerar alla kryssrutor för kategori på fliken objekt?

Genom att välja en kategori kryssruta, du anger ”jag skulle vilja se alla objekt i den här kategorin”. Endast objekt i valda kategorier som ska visas. Så på samma sätt genom att markera alla kryssrutor för kategori kan du om ”jag skulle vilja se alla objekt i en kategori”. Men vissa objekt i galleriet tillhör inte någon av de kategorier som finns i listan så att de inte att visas i resultaten. Avmarkera alla kategorier för att se alla objekt i galleriet, eller välj fliken objekt igen.

## <a name="what-are-the-requirements-to-publish-a-module-to-the-powershell-gallery"></a>Vilka är kraven för att publicera en modul till PowerShell-galleriet?

Alla typer av PowerShell-modulen (skriptmoduler, binära moduler eller manifestet moduler) kan publiceras i galleriet. Om du vill publicera en modul PowerShellGet måste veta några saker om den - version, beskrivning, författare och hur den är licensierad. Den här informationen läsas som en del av publiceringsprocessen från den *modulmanifestet* (.psd1)-fil, eller från värdet för den [ **publicera modulen** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet **LicenseUri** parameter. Alla moduler som har publicerats i galleriet måste ha modulmanifest. En modul som innehåller följande information i manifestet kan publiceras i galleriet:

- Version
- Beskrivning
- författare
- En URI för licensvillkoren för modulen, antingen som en del av den **PrivateData** avsnittet manifest eller i den **LicenseUri** parameter för den [ **publicera-Module** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.

## <a name="how-do-i-create-a-correctly-formatted-module-manifest"></a>Hur skapar jag en korrekt formaterad modulmanifestet?

Det enklaste sättet att skapa ett modulmanifest är att köra den [ **ny ModuleManifest** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet. I PowerShell 5.0 eller senare, ny ModuleManifest genererar en korrekt formaterad modulmanifestet med tomma fält för användbar metadata som **ProjectUri**, **LicenseUri**, och **taggar**. Bara fylls i automatiskt, eller Använd genererade manifestet är ett exempel på rätt format.

Kontrollera att alla obligatoriska metadatafält har fyllts i korrekt genom att använda den [ **Test ModuleManifest** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.

Uppdatera fälten modulen manifestfilen med den [ **uppdatering ModuleManifest** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.

## <a name="what-are-the-requirements-to-publish-a-script-to-the-gallery"></a>Vilka är kraven för att publicera ett skript i galleriet?

Alla typer av PowerShell-skript (skript eller arbetsflöden) kan publiceras i galleriet. Om du vill publicera ett skript PowerShellGet måste veta några saker om den - version, beskrivning, författare och hur den är licensierad. Läsa den här information som en del av publiceringsprocessen från skriptfilen *PSScriptInfo* avsnitt, eller från värdet för den [ **publicera skriptet** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet  **LicenseUri** parameter. Alla skript som publiceras i galleriet måste ha metadata-information. Alla skript som innehåller följande information i avsnittet dess PSScriptInfo kan publiceras i galleriet:

- Version
- Beskrivning
- författare
- En URI för licensvillkoren av skript, antingen som en del av den **PSScriptInfo** avsnitt av skriptet, eller i den **LicenseUri** parameter för den [ **publicera-skriptet** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.

## <a name="how-do-i-search"></a>Hur gör jag söka?

Skriv vad du söker efter i textrutan. Till exempel om du vill söka efter moduler som är relaterade till Azure SQL skriver du ”azure sql”. Vår sökmotor söker efter dessa nyckelord i alla publicerade artiklar, inklusive titlar, beskrivningar och över metadata. Sedan, baserat på ett viktat kvalitet resultat visas närmaste matchar. Du kan också söka efter specifika fält med fältet: ”värde” syntax i frågan för följande fält:

- Taggar
- Funktioner
- Cmdletar
- DscResources
- PowerShellVersion

I så fall till exempel när du söker efter PowerShellVersion: ”2.0” endast resultat som är kompatibla med PowerShellVersion 2.0 (baserat på deras skriptet och module-manifest) visas.

## <a name="how-do-i-create-a-correctly-formatted-script-file"></a>Hur skapar jag en korrekt formaterad skriptfil?

Det enklaste sättet att skapa en korrekt formaterad skriptfil är att köra den [ **ny ScriptFileInfo** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet. I PowerShell 5.0 ny ScriptFileInfo genererar en korrekt formaterad skriptfil med tomma fält för användbar metadata som **ProjectUri**, **LicenseUri**, och **taggar** . Bara fylls i automatiskt eller använda den genererade skriptfilen som ett exempel på rätt format.

Kontrollera att alla obligatoriska metadatafält har fyllts i korrekt genom att använda den [ **Test ScriptFileInfo** ](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.

Uppdatera metadatafält skript med den [ **uppdatering ScriptFileInfo** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.

## <a name="what-other-types-of-powershell-modules-exist"></a>Det finns andra typer av PowerShell-moduler?

PowerShell-modulen termen refererar även till de filer som implementerar faktiska funktioner. Modulen skriptfiler (.psm1) innehåller PowerShell-kod. Binär modulen filer (.dll) innehåller kompilerad kod.

Här är ett sätt att göra det: mappen som innehåller modulen är modulen mapp. Modulen mapp kan innehålla ett modulmanifest (.psd1) som beskriver innehållet i mappen. De filer som gör jobbet är modulen skriptfiler (.psm1) och binära modul-filer (.dll). DSC-resurser finns i en viss undermapp och implementeras som skriptet modul eller binära modul-filer.

Alla moduler i galleriet innehålla modulmanifest och de flesta av dessa moduler innehålla skript modul eller binära modul-filer. Modulen har löpt ut kan vara förvirrande på grund av dessa olika betydelse. Om inget annat uttryckligen anges finns all användning av word-modulen på den här sidan i mappen modulen som innehåller filerna.

## <a name="how-does-packagemanagement-relate-to-powershellget-high-level-answer"></a>Hur relaterar PackageManagement till PowerShellGet? (Svar på hög nivå)

PackageManagement är ett gemensamt gränssnitt för att arbeta med alla Pakethanteraren. Slutligen, om du behandlar PowerShell-moduler, MSI: er, Ruby gems, NuGet-paket eller Perl moduler ska du kunna använda Packagemanagements kommandon (Sök-paketet och Install-Package) för att hitta och installera dem. PackageManagement gör detta genom att låta en paket-provider för varje Pakethanteraren som ansluts till PackageManagement. Leverantörer gör det faktiska arbetet; de hämta innehåll från databaser och installera innehållet lokalt. Ofta omsluta paketet providers bara befintliga package manager-verktyg för en viss paket.

PowerShellGet är package manager för PowerShell-objekt. Det finns en provider för PSModule paket som innehåller PowerShellGet funktioner via PackageManagement. Därför kan du antingen köra [installera modulen](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) eller Install-Package-providern PSModule att installera en modul från PowerShell-galleriet. Vissa PowerShellGet funktioner, inklusive [uppdatering modulen](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) och [publicera modulen](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), kan inte nås via PackageManagement kommandon.

Sammanfattningsvis fokuserar PowerShellGet endast på att ha en premium-paket hanteringsupplevelse för PowerShell-innehåll. PackageManagement fokuserar på att exponera hanteringsupplevelser för alla paket via en allmän uppsättning verktyg. Om du hittar det här svaret unsatisfying, det finns ett långt svar längst ned i det här dokumentet i den **hur relaterar faktiskt PackageManagement till PowerShellGet?** avsnitt.

Mer information finns i [PackageManagement projekt sidan](https://oneget.org/).

## <a name="how-does-nuget-relate-to-powershellget"></a>Hur relaterar NuGet till PowerShellGet?

PowerShell-galleriet är en modifierad version av den [NuGet-galleriet](https://www.nuget.org/). PowerShellGet använder NuGet-providern för att arbeta med NuGet baserat databaserna som PowerShell-galleriet.

Du kan använda PowerShellGet mot någon giltig NuGet databasen eller filresurs. Du behöver bara lägga till databasen genom att köra den [ **registrera PSRepository** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.

## <a name="does-that-mean-i-can-use-nugetexe-to-work-with-the-gallery"></a>Innebär som jag kan använda NuGet.exe för att arbeta med galleriet?

Ja.

## <a name="how-does-packagemanagement-actually-relate-to-powershellget-technical-details"></a>Hur relaterar faktiskt PackageManagement till PowerShellGet? (Teknisk information)

Under huven utnyttjar PowerShellGet kraftigt PackageManagement infrastruktur.

I PowerShell-cmdlet-lagret [installera modulen](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) är faktiskt en tunn wrapper runt Install-Package-providern PSModule.

I provider-lagret PackageManagement paketet anropar PSModule paketets leverantör egentligen till andra leverantörer av PackageManagement paketet. Till exempel när du arbetar med NuGet-baserade gallerier (till exempel PowerShell-galleriet) PSModule paketet providern använder NuGet-paketet providern för att arbeta med databasen.

![PowerShellGet arkitektur](Images/powershellgetArchitecture.png)

Bild 1: PowerShellGet arkitektur

## <a name="what-is-required-to-run-powershellget"></a>Vad är krävs för att köra PowerShellGet?

I allmänhet rekommenderar vi väljer den senaste versionen av PowerShellGet modul (Observera att den kräver .NET 4.5).

Den **PowerShellGet** module kräver **PowerShell 3.0 eller senare**.

Därför **PowerShellGet** kräver en av följande operativsystem:

- Windows 10
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows 7 SP1
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 SP1

**PowerShellGet** kräver .NET Framework 4.5 eller senare. Du kan installera .NET Framework 4.5 eller senare från [här](https://msdn.microsoft.com/library/5a4x27ek.aspx).

## <a name="is-it-possible-to-reserve-names-for-items-that-will-be-published-in-future"></a>Är det möjligt att reservera namnen på objekten som kommer att publiceras i framtiden?

Det går inte att låg objektnamn. Om du anser att en befintlig artikel har vidtagit namn som passar ditt objekt fler försök [att kontakta ägaren till objektet](psgallery_contacting_item_owners.md). Om du inte har fått svar inom några veckor, kan du kontakta support och PowerShell-galleriet-teamet kommer att se den.

## <a name="how-do-i-claim-ownership-for-items-"></a>Hur gör jag anspråk på äganderätt för objekt?

Checka ut [hantera ägare för objektet på PowerShellGallery.com](Managing-Item-Owners.md) mer information.

## <a name="how-do-i-deal-with-an-item-owner-who-is-violating-my-item-license"></a>Hur hanterar med en ägare för objektet som bryter mot min objektet licens?

Vi rekommenderar att PowerShell-gemenskapen kan samarbeta för att lösa tvister som kan uppstå mellan objekt ägare och ägare av andra objekt.  Vi har särskild en [tvist lösningsprocessen](psgallery_dispute_resolution.md) som ber vi dig följa innan PowerShellGallery.com administratörer intercede.