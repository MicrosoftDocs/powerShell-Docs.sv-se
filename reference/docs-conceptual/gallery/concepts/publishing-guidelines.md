---
ms.date: 06/12/2017
contributor: JKeithB, SydneyhSmith
keywords: Galleri, PowerShell, cmdlet, psgallery
description: Rikt linjer för utgivare
title: PowerShell-galleriet publicerings rikt linjer och metod tips
ms.openlocfilehash: 5ee33ba12475f9d3e5ceb3b31f37d9f2acc19d9e
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500608"
---
# <a name="powershellgallery-publishing-guidelines-and-best-practices"></a>PowerShellGallery publicerings rikt linjer och metod tips

I den här artikeln beskrivs rekommenderade steg som används av Microsoft-team för att säkerställa att de paket som publiceras till PowerShell-galleriet är allmänt tagna och ger användarna ett högt värde, baserat på hur PowerShell-galleriet hanterar manifest data och om feedback från stor antalet PowerShell-galleriet användare. Paket som publiceras enligt dessa rikt linjer kommer att bli mer sannolika att installeras, vara betrodda och locka fler användare.

Nedan följer rikt linjer för vad som gör ett bra PowerShell-galleriet-paket, vilka valfria manifest inställningar som är viktigast, vilket förbättrar din kod med feedback från inledande granskare och [PowerShell script Analyzer](https://aka.ms/psscriptanalyzer), version av modulen, dokumentation, tester och exempel för hur du kan använda det du har delat. Mycket av den här dokumentationen följer rikt linjerna för att publicera [moduler för hög kvalitet DSC-resurs](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md).

Mechanics för att publicera ett paket till PowerShell-galleriet finns i [skapa och publicera ett paket](../how-to/publishing-packages/publishing-a-package.md).

Feedback om dessa rikt linjer är välkomna. Om du har feedback kan du öppna problem i vår [dokumentations databas för GitHub](https://github.com/powershell/powershell-docs/issues).

## <a name="best-practices-for-publishing-packages"></a>Metod tips för publicering av paket

Följande metod tips är vad användare av PowerShell-galleriet objekt säger är viktigt och visas i den nominella prioritets ordningen. Paket som följer dessa rikt linjer är mycket mer sannolika att laddas ned och antas av andra.

- Använd PSScriptAnalyzer
- Ta med dokumentation och exempel
- Svara på feedback
- Tillhandahålla moduler i stället för skript
- Ange länkar till en projekt webbplats
- Tagga ditt paket med de kompatibla PSEdition och plattformarna
- Ta med tester med dina moduler
- Inkludera och/eller länka till licens villkoren
- Signera din kod
- Följ [SemVer](https://semver.org/) -rikt linjerna för versions hantering
- Använd vanliga taggar, enligt beskrivningen i vanliga PowerShell-galleriet-Taggar
- Testa publiceringen med hjälp av en lokal lagrings plats
- Använda PowerShellGet för att publicera

Var och en av dessa omfattas kortfattat i avsnitten nedan.

## <a name="use-psscriptanalyzer"></a>Använd PSScriptAnalyzer

[PSScriptAnalyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer) är ett kostnads fritt statiskt kod analys verktyg som fungerar med PowerShell-kod. **PSScriptAnalyzer** kommer att identifiera de vanligaste problemen som visas i PowerShell-koden och ofta en rekommendation för hur du kan åtgärda problemet. Verktyget är enkelt att använda och kategoriserar problemen som fel (allvarligt, måste åtgärdas), varning (måste granskas och bör åtgärdas) och information (värt att kolla för bästa praxis). Alla paket som publiceras till PowerShell-galleriet genomsöks med hjälp av **PSScriptAnalyzer**och eventuella fel rapporteras tillbaka till ägaren och måste åtgärdas.

Det bästa sättet är att köra `Invoke-ScriptAnalyzer` med `-Recurse` och `-Severity` varning.

Granska resultaten och se till att:

- Alla fel korrigeras eller åtgärdas i dokumentationen.
- Alla varningar granskas och åtgärdas där det är tillämpligt.

Användare som laddar ned paket från PowerShell-galleriet är starkt uppmanade att köra **PSScriptAnalyzer** och utvärdera alla fel och varningar. Användare kan förmodligen kontakta paket ägare om de ser att det finns ett fel rapporterat av **PSScriptAnalyzer**. Om det finns en övertygande anledning för ditt paket att behålla kod som flaggats som ett fel, lägger du till den informationen i dokumentationen för att undvika att behöva besvara samma fråga flera gånger.

## <a name="include-documentation-and-examples"></a>Ta med dokumentation och exempel

Dokumentation och exempel är det bästa sättet att se till att användarna kan dra nytta av all delad kod.

Dokumentation är det som är mest användbart att inkludera i paket som publiceras till PowerShell-galleriet.
Användarna kommer normalt att kringgå paket utan dokumentation, eftersom alternativet är att läsa koden för att förstå vad paketet är och hur det används. Det finns flera artiklar om hur du tillhandahåller dokumentation med PowerShell-paket, inklusive:

- Rikt linjer för att tillhandahålla hjälp finns i [så här skriver du cmdlet-hjälpen](https://go.microsoft.com/fwlink/?LinkID=123415).
- Skapa cmdlet-hjälpen, som är den bästa metoden för PowerShell-skript,-funktioner eller-cmdlet.
  Om du vill ha mer information om hur du skapar cmdlet-hjälpen börjar [du med hur du skriver cmdlet-hjälpen](https://go.microsoft.com/fwlink/?LinkID=123415).
  Information om hur du lägger till hjälp i ett skript finns i [om Kommentering baserad hjälp](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).
- Många moduler innehåller också dokumentation i text format, till exempel MarkDown-filer. Detta kan vara särskilt användbart när det finns en projekt webbplats i GitHub, där markdown är ett mycket använt format. Det bästa sättet är att använda [GitHub markdown](https://help.github.com/categories/writing-on-github/).

Exempel visar användare hur paketet är avsett att användas. Många utvecklare säger att de tittar på exempel före dokumentationen för att förstå hur man använder något. De bästa typerna av exempel visar grundläggande användning, plus ett simulerat realistiskt användnings fall och koden är väl kommenterad. Exempel på moduler som publiceras till PowerShell-galleriet ska finnas i mappen exempel under modul roten.

Ett utmärkt mönster för exempel finns i [PSDscResource-modulen](https://www.powershellgallery.com/packages/PSDscResources) under mappen `Examples\RegistryResource`. Det finns fyra exempel på användnings fall med en kort beskrivning längst upp i varje fil som dokumenten visas.

## <a name="manage-dependencies"></a>Hantera beroenden

Det är viktigt att ange moduler som modulen är beroende av i manifestet för modulen. Detta gör det möjligt för slutanvändaren att inte behöva oroa sig för att installera rätt versioner av moduler som ditt tar ett beroende på. Om du vill ange beroende moduler ska du använda fältet obligatorisk modul i manifestet för modulen. Detta läser in moduler som visas i den globala miljön innan du importerar modulen om de inte redan har lästs in. Till exempel kanske vissa moduler redan har lästs in av en annan modul. Det är också möjligt att ange en angiven version som ska läsas in med fältet **RequiredVersion** i stället för fältet **ModuleVersion** . När du använder **ModuleVersion**kommer den att läsa in den senaste versionen som är tillgänglig med minst den angivna versionen. Om du inte använder fältet **RequiredVersion** för att ange en speciell version är det viktigt att övervaka versions uppdateringar till modulen som krävs. Det är särskilt viktigt att vara medveten om eventuella större ändringar som kan påverka användar upplevelsen med modulen.

```powershell
Example: RequiredModules = @(@{ModuleName="myDependentModule"; ModuleVersion="2.0"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})

Example: RequiredModules = @(@{ModuleName="myDependentModule"; RequiredVersion="1.5"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})
```

## <a name="respond-to-feedback"></a>Svara på feedback

Paket ägare som svarar korrekt på feedback är mycket värdefulla för communityn. Användare som tillhandahåller informell feedback är viktiga att svara på eftersom de är tillräckligt intressanta i paketet för att försöka hjälpa till att förbättra det.

Det finns två återkopplings metoder som är tillgängliga i PowerShell-galleriet:

- Kontakt ägare: det gör att en användare kan skicka ett e-postmeddelande till paketets ägare. Som paket ägare är det viktigt att övervaka den e-postadress som används med PowerShell-galleriet-paket och svara på problem som aktive ras. Den enda nack delen med den här metoden är att endast användaren och ägaren kommer att se kommunikationen, så att ägaren kan behöva besvara samma fråga flera gånger.
- Kommentarer: längst ned på sidan paket finns ett **kommentars** fält. Fördelen med det här systemet är att andra användare kan se kommentarer och svar, vilket minskar antalet gånger som en enskild fråga måste besvaras. Som paket ägare rekommenderar vi starkt att du följer de kommentarer som gjorts för varje paket. Mer information om hur du gör detta finns i [ge feedback via sociala medier eller kommentarer](../how-to/working-with-packages/social-media-feedback.md) .

Ägare som svarar på feedback informellt uppskattas av communityn. Använd affärs möjligheten i rapporten för att begära mer information. Om det behövs kan du ange en lösning eller identifiera om en uppdatering åtgärdar ett problem.

Om det är olämpligt beteende som observerats från någon av dessa kommunikations kanaler kan du kontakta Galleri administratörerna genom att använda funktionen rapport missbruk i PowerShell-galleriet.

## <a name="modules-versus-scripts"></a>Moduler jämfört med skript

Att dela ett skript med andra användare är bra och ger andra exempel på hur de kan lösa problem. Problemet är att skript i PowerShell-galleriet är enstaka filer utan separat dokumentation, exempel och test.

PowerShell-moduler har en mappstruktur som tillåter att flera mappar och filer tas med i paketet. Modul strukturen gör det möjligt att inkludera andra paket som vi listar som bästa praxis: cmdlet-hjälp, dokumentation, exempel och test. Den största nack delen är att ett skript i en modul måste exponeras och användas som en funktion. Information om hur du skapar en modul finns i [skriva en Windows PowerShell-modul](/powershell/scripting/developer/module/writing-a-windows-powershell-module).

Det finns situationer där ett skript ger en bättre upplevelse för användaren, särskilt med DSC-konfigurationer. Den bästa metoden för DSC-konfigurationer är att publicera konfigurationen som ett skript med en tillhör ande modul som innehåller dokument, exempel och test. Skriptet listar den tillhör ande modulen med hjälp av `RequiredModules = @(Name of the Module)`. Den här metoden kan användas med alla skript.

Fristående skript som följer de andra bästa metoderna ger användare ett verkligt värde. Det rekommenderas att tillhandahålla kommenterad dokumentation och en länk till en projekt webbplats när du publicerar ett skript till PowerShell-galleriet.

## <a name="provide-a-link-to-a-project-site"></a>Ange en länk till en projekt webbplats

En projekt webbplats är den plats där en utgivare kan interagera direkt med användare av sina PowerShell-galleriet-paket. Användare föredrar paket som tillhandahåller detta, eftersom det gör det möjligt för dem att få information om paketet enklare. Många paket i PowerShell-galleriet utvecklas i GitHub, andra tillhandahålls av organisationer med en särskild webb närvaro. Var och en av dessa kan betraktas som en projekt webbplats.

Att lägga till en länk görs genom att inkludera ProjectURI i PSData-avsnittet i manifestet på följande sätt:

```
  # A URL to the main website for this project.
  ProjectUri = 'https://github.com/powershell/powershell'
```

När en ProjectURI anges kommer PowerShell-galleriet att innehålla en länk till projekt webbplatsen till vänster på paket sidan.

## <a name="tag-your-package-with-the-compatible-pseditions-and-platforms"></a>Tagga ditt paket med de kompatibla PSEdition och plattformarna

Använd följande taggar för att demonstrera användare vars paket fungerar bra med deras miljö:

- PSEdition_Desktop: paket som är kompatibla med Windows PowerShell
- PSEdition_Core: paket som är kompatibla med PowerShell Core
- Windows: paket som är kompatibla med operativ systemet Windows
- Linux: paket som är kompatibla med Linux-operativsystem
- MacOS: paket som är kompatibla med Mac-operativsystemet

Genom att tagga ditt paket med de kompatibla plattformarna kommer det att tas med i Galleri Sök filter i det vänstra fönstret i Sök resultatet. Om du är värd för ditt paket på GitHub kan du, när du taggar ditt paket, också dra nytta av vår [PowerShell-galleriet Compatibility sköld](https://img.shields.io/powershellgallery/p/:packageName.svg)
![compatibility sköld](media/publishing-guidelines/CosmosDB.svg).

## <a name="include-tests"></a>Ta med tester

Att inkludera tester med kod med öppen källkod är viktigt för användarna, eftersom det ger dem garantier för vad du validerar och ger information om hur koden fungerar. Det gör det också möjligt för användarna att se till att de inte bryter dina ursprungliga funktioner om de ändrar koden så att den passar deras miljö.

Vi rekommenderar starkt att testerna skrivs för att dra nytta av pester test Framework, som har utformats specifikt för PowerShell. Pester finns i [GitHub](https://github.com/Pester/Pester), [PowerShell-galleriet](https://www.powershellgallery.com/packages/Pester/)och fartyg i Windows 10, Windows Server 2016, WMF 5,0 och WMF 5,1.

[Projekt webbplatsen pester i GitHub](https://github.com/Pester/Pester) innehåller bra dokumentation om hur du skriver pester-tester, från komma igång till bästa praxis.

Målen för test täckningen anropas i dokumentationen för [resurs modulen med hög kvalitet](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md), med 70% enhets test kod täckning rekommenderas.

## <a name="include-andor-link-to-license-terms"></a>Inkludera och/eller länka till licens villkoren

Alla paket som har publicerats till PowerShell-galleriet måste ange licens villkoren eller vara kopplade till den licens som ingår i [användnings villkoren](https://www.powershellgallery.com/policies/Terms) . Den bästa metoden för att ange en annan licens är att tillhandahålla en länk till licensen med hjälp av **LicenseURI** i **PSData**. Mer information finns i avsnittet om [paket manifest-och Galleri gränssnitt](package-manifest-affecting-ui.md).

```powershell
PrivateData = @{
    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        Tags = @('.net','acl','active-directory')

        # A URL to the license for this module.
        LicenseUri = 'http://www.apache.org/licenses/LICENSE-2.0'
```

## <a name="sign-your-code"></a>Signera din kod

Kod signering ger användare den högsta garanti nivån för vem som har publicerat paketet och att kopian av den kod de får är exakt vad utgivaren har publicerat. Mer information om kod signering finns i [Introduktion till kod signering](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537361(v=vs.85)).
PowerShell stöder validering av kod signering genom två primära metoder:

- Signera skriptfiler
- Katalog som signerar en modul

Signering av PowerShell-filer är en väl etablerad metod för att säkerställa att den kod som körs har producerats av en tillförlitlig källa och att den inte har ändrats. Information om hur du signerar PowerShell-skriptfiler beskrivs i artikeln [om signering](/powershell/module/microsoft.powershell.core/about/about_signing) . I Översikt kan en signatur läggas till i alla `.PS1`-filer som PowerShell validerar när skriptet läses in. PowerShell kan begränsas med hjälp av cmdletar för [körnings principer](/powershell/module/microsoft.powershell.core/about/about_execution_policies) för att säkerställa att signerade skript används.

Moduler för katalog signering är en funktion som har lagts till i PowerShell i version 5,1. Hur du signerar en modul beskrivs i artikeln [katalog-cmdletar](/powershell/scripting/wmf/whats-new/new-updated-cmdlets#catalog-cmdlets) .
I översikten görs en katalog signering genom att skapa en katalog fil som innehåller ett hash-värde för varje fil i modulen och sedan signera filen.

**PowerShellGet** `Publish-Module`, `Install-Module`och `Update-Module`-cmdlets kontrollerar signaturen för att kontrol lera att den är giltig och bekräftar sedan att hash-värdet för varje paket matchar vad som finns i katalogen. `Save-Module` validerar inte en signatur. Om en tidigare version av modulen är installerad på systemet bekräftar `Install-Module` att signerings utfärdaren för den nya versionen överensstämmer med vad som tidigare har installerats. `Install-Module` och `Update-Module` använder signaturen på en `.PSD1`-fil om paketet inte är en katalog som är signerad. Katalog signering fungerar med, men ersätter inte signerings skript filer. PowerShell validerar inte katalog-signaturer vid inläsning av modul.

## <a name="follow-semver-guidelines-for-versioning"></a>Följ SemVer-rikt linjerna för versions hantering

[SemVer](https://semver.org/) är en offentlig konvention som beskriver hur du strukturerar och ändrar en version för att möjliggöra enkel tolkning av ändringar. Versionen för paketet måste ingå i manifest data.

- Versionen ska struktureras som tre numeriska block åtskilda med punkter, som i `0.1.1` eller `4.11.192`.
- Versioner som börjar med `0` visar att paketet ännu inte är färdigt och att det första talet bara börjar med `0` om det är det enda antal som används.
- Ändringar i det första talet (`1.9.9999` till `2.0.0`) visar viktiga och avbrytande ändringar mellan versionerna.
- Ändringar av det andra talet (`1.1` till `1.2`) visar ändringar på funktions nivå, till exempel att lägga till nya cmdlets i en modul.
- Ändringar i det tredje talet indikerar icke-brytande ändringar, till exempel nya parametrar, uppdaterade exempel eller nya tester.
- När du visar versioner sorterar PowerShell versionerna som strängar, så `1.01.0` behandlas som större än `1.001.0`.

PowerShell skapades innan SemVer publicerades, vilket ger stöd för de flesta men inte alla element i SemVer, särskilt:

- Den har inte stöd för för hands versions strängar i versions nummer. Detta är användbart när en utgivare vill leverera en för hands version av en ny huvud version när du har angett en version `1.0.0`. Detta kommer att stödjas i en framtida version av PowerShell-galleriet-och **PowerShellGet** -cmdletar.
- PowerShell och PowerShell-galleriet tillåta versions strängar med 1, 2 och 4 segment. Många tidiga moduler följer inte rikt linjerna och produkt utgåvorna från Microsoft inkluderar build-information som ett fjärde block med nummer (till exempel `5.1.14393.1066`). Dessa skillnader ignoreras från en versions synpunkt.

## <a name="test-using-a-local-repository"></a>Testa med en lokal lagrings plats

PowerShell-galleriet är inte avsedd att vara ett mål för att testa publicerings processen. Det bästa sättet att testa processen från slut punkt till slut punkt för att publicera till PowerShell-galleriet är att konfigurera och använda din egen lokala lagrings plats. Detta kan göras på några sätt, t. ex.:

- Konfigurera en lokal PowerShell-galleriet instans med hjälp av [projektet PS, privat Galleri](https://github.com/PowerShell/PSPrivateGallery) i GitHub. I det här för hands versionen av projektet får du hjälp att skapa en instans av PowerShell-galleriet som du kan styra och använda för dina tester.
- Konfigurera en [intern NuGet-lagringsplats](https://blogs.msdn.microsoft.com/powershell/2014/05/20/setting-up-an-internal-powershellget-repository/).
  Detta kräver mer arbete för att konfigureras, men har fördelen att du verifierar några av kraven, särskilt att validera användningen av en API-nyckel och om beroenden finns i målet när du publicerar.
- Konfigurera en fil resurs som test **lagrings plats**. Detta är enkelt att konfigurera, men eftersom det är en fil resurs kommer de verifieringar som anges ovan inte att äga rum. En möjlig fördel i detta fall är att fil resursen inte kontrollerar den nödvändiga API-nyckeln, så du kan använda samma nyckel som du skulle använda för att publicera till PowerShell-galleriet.

Med någon av dessa lösningar använder du `Register-PSRepository` för att definiera en ny **lagrings plats**, som du använder i `-Repository`-parametern för `Publish-Module`.

En ytterligare punkt om test publicering: alla paket som du publicerar till PowerShell-galleriet kan inte tas bort utan hjälp från Operations-teamet, som bekräftar att inget är beroende av det paket som du vill publicera. Därför stöder vi inte PowerShell-galleriet som ett test mål och kommer att kontakta alla utgivare som gör det.

## <a name="use-powershellget-to-publish"></a>Använda PowerShellGet för att publicera

Vi rekommenderar starkt att utgivare använder `Publish-Module`-och `Publish-Script`-cmdletar när du arbetar med PowerShell-galleriet. **PowerShellGet** har skapats för att hjälpa dig att undvika att komma ihåg viktig information om hur du installerar från och publicerar till PowerShell-galleriet. Ibland har utgivare valt att hoppa över **PowerShellGet** och använda **NuGet** -klienten, eller **PackageManagement** -cmdlet: ar, i stället för `Publish-Module`. Det finns ett antal information som är lätt att missa, vilket resulterar i en rad olika support förfrågningar.

Om det finns en anledning till att du inte kan använda `Publish-Module` eller `Publish-Script`, kan du kontakta oss.
Skriv ett problem i **PowerShellGet** GitHub-lagrings platsen och ange information som gör det möjligt att välja **NuGet** eller **PackageManagement**.

## <a name="recommended-workflow"></a>Rekommenderat arbets flöde

Den mest fungerande metoden vi har hittat för paket som publicerats till PowerShell-galleriet är följande:

- Gör den inledande utvecklingen på en Project-webbplats med öppen källkod. PowerShell-teamet använder GitHub.
- Använd feedback från granskare och [PowerShell script Analyzer](https://aka.ms/psscriptanalyzer) för att få koden att vara stabil.
- Ta med dokumentation, så att andra vet hur man använder ditt arbete.
- Testa publicerings åtgärden med hjälp av en lokal lagrings plats.
- Publicera en stabil eller alfa version till PowerShell-galleriet och se till att ta med dokumentationen och länka till projekt webbplatsen.
- Samla in feedback och iterera på koden i din projekt webbplats och publicera sedan stabila uppdateringar till PowerShell-galleriet.
- Lägg till exempel och pester-tester i projektet och modulen.
- Bestäm om du vill koda signera ditt paket.
- När du tycker att projektet är klart att användas i en produktions miljö, publicerar du en `1.0.0`-version till PowerShell-galleriet.
- Fortsätt att samla in feedback och iterera på din kod baserat på användarindata.
