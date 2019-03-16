---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
description: Riktlinjer för utgivare
title: PowerShell-galleriet publicera riktlinjer och metodtips
ms.openlocfilehash: 25c359c7acbe7430762a275d8cc4a28f527ec57a
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056506"
---
# <a name="powershellgallery-publishing-guidelines-and-best-practices"></a>PowerShellGallery publicera riktlinjer och metodtips

Det här avsnittet beskriver rekommenderade steg som används av Microsoft-team så att de paket som publicerats i PowerShell-galleriet kommer användas brett och ge användarna, baserat på hur PowerShell-galleriet hanterar manifest data och på feedback från stora högt värde antal användare för PowerShell-galleriet.
Paket som har publicerats till att följa dessa riktlinjer ska troligare att de kan installeras, betrodda, och attrahera fler användare.

Nedan följer riktlinjer för vad som är ett bra PowerShell Gallery-paket, vilka valfria Manifest inställningar som är viktigast, förbättra din kod med feedback från första granskare och [Powershell-skript Analyzer](https://aka.ms/psscriptanalyzer), versionshantering din modul, dokumentation, tester och exempel på hur du använder vad du har delat.
Mycket av den här dokumentationen följer riktlinjerna för publicering [hög kvalitet DSC-resurs moduler](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md).

Säkerhetsnivån publicering av ett paket till PowerShell-galleriet, se [skapa och publicera ett paket](/powershell/gallery/how-to/publishing-packages/publishing-a-package).

Feedback om dessa riktlinjer välkomnade. Om du har feedback, öppna problem i vår [Github-dokumentationslagringsplatsen](https://github.com/powershell/powershell-docs/issues).

## <a name="best-practices-for-publishing-packages"></a>Metodtips för att publicera paket

Följande metodtips är vad användare med PowerShell-galleriet objekt säger är viktigt och visas i nominell prioritetsordning.
Paket som följer dessa riktlinjer är mycket mer troligt att hämtas och användas av andra.

- Använda PSScriptAnalyzer
- Inkludera dokumentation och exempel
- Responsiva gentemot feedback
- Ange moduler i stället för skript
- Innehåller länkar till en projektwebbplats
- Tagga ditt paket med kompatibla PSEdition(s) och plattformar
- Inkludera tester med dina moduler
- Inkludera och/eller länka till licensvillkoren
- Registrera din kod
- Följ [SemVer](http://semver.org/) riktlinjer för versionshantering
- Använd vanliga taggar, enligt beskrivningen i vanliga PowerShell-galleriet taggar
- Testa publicering med en lokal databas
- Använda PowerShellGet för att publicera

Var och en av dessa beskrivs kortfattat i avsnitten nedan.

## <a name="use-psscriptanalyzer"></a>Använda PSScriptAnalyzer

[PSScriptAnalyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer) är ett analysverktyg för statisk kod som fungerar på PowerShell-kod.
PSScriptAnalyzer identifierar de vanligaste problemen som visas i PowerShell-kod och ofta en rekommendation för hur du löser problemet.
Verktyget är enkel att använda och kategoriserar problem som fel (allvarligt, måste åtgärdas), varning (behöver granskas och bör åtgärdas) och Information (värt att checka ut Metodtips för).
Alla paket som publicerats i PowerShell-galleriet ska genomsökas med PSScriptAnalyzer och eventuella fel rapporteras tillbaka till ägare och måste åtgärdas.

Det bästa sättet är att köra `Invoke-ScriptAnalyzer` med `-Recurse` och `-Severity` varning.

Granska resultaten och se till att:

- Alla fel har korrigerats eller åtgärdas i dokumentationen
- Alla varningar granskas och åtgärdas om tillämpligt

Användare som skaffar paket från PowerShell-galleriet rekommenderas att köra PSScriptAnalyzer och utvärdera alla fel och varningar.
Användare är mycket troligt att kontakta paketets ägare om de ser att det finns ett fel som rapporterats av PSScriptAnalyzer.
Om det finns en bra anledning för ditt paket att hålla kod som flaggas som ett fel, kan du lägga till informationen i dokumentationen för att förhindra att svara på samma fråga många gånger.

## <a name="include-documentation-and-examples"></a>Inkludera dokumentation och exempel

Dokumentation och exempel är det bästa sättet att se till att användare kan dra nytta av någon delad kod.

Dokumentation är det mest användbara som ska ingå i paket som publicerats i PowerShell-galleriet.
Användarna kringgå Allmänt paket utan dokumentation, eftersom alternativet är att läsa kod för att förstå vad paketet är och hur du använder den.
Det finns flera artiklar om hur du ger dokumentation med PowerShell-paket, inklusive:

- Riktlinjer för att tillhandahålla hjälp finns i [hur du skriver hjälp för cmdleten](https://go.microsoft.com/fwlink/?LinkID=123415)
- Skapar cmdlet-hjälpen, vilket är den bästa metoden för PowerShell-skript, funktion eller cmdlet.
  Information om hur du skapar cmdlet-hjälpen börjar du med [hur du skriver hjälp för cmdleten](https://go.microsoft.com/fwlink/?LinkID=123415).
  Om du vill lägga till hjälp i ett skript, se [om kommentar baserat hjälpa](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).
- Många moduler kan du även innehålla dokumentation i textformat, till exempel MarkDown-filer.
  Detta kan vara särskilt användbart när det finns en projektwebbplats i Github, där Markdown är ett hårt belastat format.
  Det bästa sättet är att använda [Markdown i Github](https://help.github.com/categories/writing-on-github/)

Exemplen visar användare hur paketet är avsedd att användas.
Många utvecklare står det att de titta på exempel innan dokumentationen för att förstå hur du använder något.
Den bästa typen av exempel visa grundläggande användning, plus en simulerad realistisk användningsfall och koden är väl kommenterade.
Exempel på moduler som publicerats i PowerShell-galleriet ska vara i en exempel-mapp under roten för modulen.

Ett bra mönster exempel finns i den [PSDscResource modulen](https://www.powershellgallery.com/packages/PSDscResources) under mappen Examples\RegistryResource.
Det finns fyra exempel användningsfall med en kort beskrivning överst i varje fil som dokument vad som visas.

## <a name="respond-to-feedback"></a>Svara på feedback

Paketet ägare som ska svarar på feedback värderas mycket av communityn.
Användare som ger informell feedback är viktigt att svara på, eftersom de är intresserad av i paketet för att testa för att förbättra den.

Det finns två metoder för feedback i PowerShell-galleriet:

- Kontakta ägaren: Detta gör det möjligt att skicka ett e-postmeddelande till paketet ägarna. Som ägare paketet är viktigt att övervaka e-postadressen används med PowerShell-galleriet paketen och svara på problem som har skapats. En nackdel till den här metoden är att endast användare och ägare någonsin ser kommunikation, så ägare kan behöva och svara på samma fråga många gånger.
- Kommentarer: Sidan är en kommentarsfält längst ned i paketet.
  Fördelen med att det här systemet är att andra användare kan se kommentarer och svar, vilket minskar antalet gånger varje enskild fråga måste besvaras.
  Som paket ägare rekommenderar vi starkt att du följer alla kommentarer för varje paket.
Se [att tillhandahålla Feedback via sociala medier eller kommentarer](../how-to/working-with-packages/social-media-feedback.md) mer information om hur du gör.

Ägare som svarar på feedback på konstruktiva sätt uppskattas av communityn.
Använda möjligheten i rapporten för att begära mer information om det behövs, tillhandahålla en lösning eller identifiera om en uppdatering korrigerar ett problem.

Om det finns olämplig beteende som observerats från någon av dessa kommunikationskanaler, använder du funktionen Rapportera missbruk i PowerShell-galleriet för att kontakta galleri-administratörer.

## <a name="modules-versus-scripts"></a>Moduler jämfört med skript

Dela ett skript med andra användare är bra och ger andra exempel på hur du löser problem som de kan ha.
Problemet är att skript i PowerShell-galleriet är enkel filer utan separat dokumentation, exempel och tester.

PowerShell-moduler har en mappstruktur som gör att flera mappar och filer som ska ingå i paketet.
Modulstrukturen gör, inklusive de andra paketen som vi lista som bästa praxis: cmdleten hjälp, dokumentation, exempel och tester.
Den största nackdelen är att ett skript i en modul måste visas och används som en funktion.
Information om hur du skapar en modul finns i [skriva en Windows PowerShell-modul](http://go.microsoft.com/fwlink/?LinkId=144916).

Det finns situationer där ett skript ger en bättre upplevelse för användaren, särskilt med DSC-konfigurationer.
Det är bra för DSC-konfigurationer att publicera konfigurationen som ett skript med en medföljande modul som innehåller den docs, exempel och tester.
Skriptet innehåller tillhörande modulen med RequiredModules = @(namnet på modulen).
Den här metoden kan användas med alla skript.

Fristående skript som följer de rekommenderade metoderna ger verkliga värdet till andra användare.
Tillhandahåller kommentarbaserad dokumentation och en länk till en plats för projektet rekommenderas starkt när du publicerar ett skript i PowerShell-galleriet.

## <a name="provide-a-link-to-a-project-site"></a>Ange en länk till en projektwebbplats

En plats för projektet är där en utgivare kan interagera direkt med användarna av sina PowerShell-galleriet-paket.
Användare föredrar paket som tillhandahåller detta, eftersom den låter dem att få information om paketet enklare.
Många paket i PowerShell-galleriet har utvecklats i GitHub, tillhandahålls andra av organisationer med en dedikerad webbnärvaro.
Var och en av dessa kan betraktas som en projektwebbplats.

Lägga till en länk görs genom att inkludera ProjectURI i avsnittet PSData i manifestet på följande sätt:

        # A URL to the main website for this project.
        ProjectUri = 'https://github.com/powershell/powershell'

När en ProjectURI tillhandahålls innehåller i PowerShell-galleriet en länk till webbplatsen projekt till vänster på sidan för paketet.

## <a name="tag-your-package-with-the-compatible-pseditions-and-platforms"></a>Tagga ditt paket med kompatibla PSEdition(s) och plattformar

Använd följande taggar för att visa för användarna som paket ska fungera bra med sin miljö:

- PSEdition_Desktop : Paket som är kompatibla med Windows PowerShell
- PSEdition_Core: Paket som är kompatibla med PowerShell Core
- Windows: Paket som är kompatibla med Windows operativsystem
- Linux: Paket som är kompatibla med Linux-operativsystem
- MacOS: Paket som är kompatibla med Mac-operativsystemet

## <a name="include-tests"></a>Inkludera tester

Inklusive tester med öppen källkod är viktigt att användare, eftersom det ger dem assurance om vad du validera och innehåller information om hur din kod fungerar. Tillåter även användare att se till att de inte skadar din ursprungliga funktioner om de ändrar koden så att de passar deras miljö.

Vi rekommenderar starkt att testerna ska skrivas till att dra nytta av Testramverk Pester som har utformats speciellt för PowerShell.
Lära finns i [GitHub](https://github.com/Pester/Pester), [PowerShell-galleriet](https://www.powershellgallery.com/packages/Pester/), och levereras i Windows 10, Windows Server 2016, WMF 5.0 och WMF 5.1.

Den [Pester projektwebbplatsen i GitHub](https://github.com/Pester/Pester) innehåller bra dokumentation om hur du skriver Pester tester från att komma igång med bästa praxis.

Mål för testtäckning framhävs den [hög kvalitet Resource modulen dokumentation](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md), testa koden täckning rekommenderas med 70%-enhet.

## <a name="include-andor-link-to-license-terms"></a>Inkludera och/eller länka till licensvillkoren

Alla paket som publicerats i PowerShell-galleriet måste ange licensvillkoren eller vara bunden av licensen som ingår i den [användningsvillkor](https://www.powershellgallery.com/policies/Terms) under ”bilaga A”.
Det bästa sättet att ange en annan licens är att tillhandahålla en länk till licensen med hjälp av LicenseURI i PSData.
Du hittar ett exempel i avsnittet om rekommenderade Manifest fält.

```powershell
PrivateData = @{
    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        Tags = @('.net','acl','active-directory')

        # A URL to the license for this module.
        LicenseUri = 'http://www.apache.org/licenses/LICENSE-2.0'
```

## <a name="sign-your-code"></a>Registrera din kod

Kodsignering förser användare med den högsta säkerhetsnivån för vem som publicerade paketet och att kopian av koden de förvärva är exakt vad utgivaren är.
Läs mer om kodsignering Allmänt i [introduktion till Code Signing](http://go.microsoft.com/fwlink/?LinkId=106296).
PowerShell har stöd för verifiering av kodsignering via två primära sätt:

- Signering skriptfiler
- Katalogen som registrerar en modul

Det är ett välkänt tillvägagångssätt till att säkerställa att koden som körs har skapats av en pålitlig källa och har inte ändrats för att registrera PowerShell-filer.
Information om hur du registrerar PowerShell-skriptfiler beskrivs i den [om signering](/powershell/module/microsoft.powershell.core/about/about_signing) avsnittet.
Översikt, kan en signatur läggas till någon. Ps1-fil som PowerShell kontrollerar när skriptet har lästs in.
PowerShell kan begränsas med hjälp av den [körningsprincipen](/powershell/module/microsoft.powershell.core/about/about_execution_policies) cmdletar för att kontrollera användningen av signerade skript.

Catalog signering moduler är en funktion som introducerades i PowerShell i version 5.1.
Hur du registrerar en modul beskrivs i den [katalog-cmdletar](/powershell/wmf/5.1/catalog-cmdlets) avsnittet.
I Översikt görs catalog signering genom att skapa en katalogfil som innehåller ett hash-värde för varje fil i modulen, och sedan registrera filen.
PowerShellGet-publicera modulen, install-module, save-module och update-module-cmdletar ska kontrollera signaturen för att säkerställa att den är giltig och bekräfta sedan att hash-värde för varje paket matchar vad som finns i katalogen.
Om en tidigare version av modulen är installerad på systemet, bekräftar install-module att signering utfärdaren av den nya versionen matchar den tidigare installerade.
Katalogen signering fungerar med, men ersätter inte signering skriptfiler. PowerShell validerar inte katalogen signaturer på modulen inläsningstid.

## <a name="follow-semver-guidelines-for-versioning"></a>Följ SemVer riktlinjer för versionshantering

[SemVer](http://semver.org/) är en offentlig konvention som beskriver hur du strukturerar och ändra en version för att tillåta enkel tolkning av ändringar.
Version för ditt paket måste inkluderas i manifestet data.

- Versionen ska vara strukturerade som 3 numeriska block avgränsade med punkter, som i 0.1.1 eller 4.11.192
- Versioner som börjar med ”0” tyda på att paketet är ännu inte klara för produktion och den första siffran endast ska börja med ”0” om det är bara tal används
- Ändringar i den första siffran (1.9.9999 2.0.0) anger högre och den icke-bakåtkompatibel ändringarna mellan versionerna
- Ändringar i den andra siffran (1.1 1.2) visar funktionen på servernivå ändringar, till exempel att lägga till nya cmdlet: ar till en modul
- Ändringar i det tredje talet anger bakåtkompatibla ändringar, till exempel nya parametrar, uppdaterade exempel eller nya test
- När versioner, PowerShell om du vill sortera versionerna som strängar, så 1.01.0 behandlas som är större än 1.001.0

PowerShell skapades innan SemVer publicerades, så den ger stöd för de flesta men inte alla element i SemVer, särskilt:

- Det stöder inte förhandsversioner strängar i versionsnummer. Detta är användbart när en utgivare önskar att leverera en förhandsversionen av en ny huvudversion när du har angett en version 1.0.0. Detta kommer att stödjas i en framtida version av PowerShell-galleriet och PowerShellGet-cmdletar.
- PowerShell och PowerShell-galleriet kan du version strängar med 1, 2 och 4 segment. Riktlinjerna följde inte de många tidig moduler och produktversioner från Microsoft innehåller versionsinformation eftersom en 4 blockera tal (till exempel 5.1.14393.1066). Baserat på en versionshantering av ignoreras dessa skillnader.

## <a name="test-using-a-local-repository"></a>Testa med en lokal databas

PowerShell-galleriet är inte avsedd att vara målet för att testa publiceringsprocessen.
Det bästa sättet att testa slutpunkt till slutpunkt-processen för publicering till PowerShell-galleriet är att installera och använda en egen lokal databas.
Detta kan göras på flera sätt, inklusive:

- Konfigurera en lokal PowerShell-galleriet-instans med hjälp av den [PS privat galleri projekt](https://github.com/PowerShell/PSPrivateGallery) i Github. Det här preview-projektet kan du ställa in en instans av PowerShell-galleriet som du kan styra och användning för dina tester.
- Konfigurera en [interna Nuget databas](https://blogs.msdn.microsoft.com/powershell/2014/05/20/setting-up-an-internal-powershellget-repository/). Detta kräver mer arbete att ställa in, men har fördelen med att verifiera några fler krav, särskilt verifiera användning av en API-nyckel och om beroenden finns i målet när du publicerar.
- Konfigurera en filresurs som test ”databas”. Är det enkelt att ställa in, men eftersom det är en filresurs verifieringar som anges ovan inte kommer att äga rum. En potentiella fördelar är i det här fallet att filresursen kontrollerar inte (obligatoriskt) API-nyckel, så du kan använda samma nyckel sätt för att publicera i PowerShell-galleriet.

Med någon av dessa lösningar, använder du Register-PSRepository för att definiera en ny ”databas”, som du använder i egenskapen - lagringsplatsen för Publish-Module.

Ytterligare en punkt om test-publicering: alla paket som du publicerar till PowerShell-galleriet kan inte tas bort utan hjälp från operations-teamet som bekräftar att ingenting är beroende av det paket som du vill publicera.
Därför vi har inte stöd för PowerShell-galleriet som testar mål och kommer att kontakta alla utgivare som sker.

## <a name="use-powershellget-to-publish"></a>Använda PowerShellGet för att publicera

Vi rekommenderar starkt att utgivare kan använda Publish-Module och Publish-Script-cmdlets när du arbetar med PowerShell-galleriet.
PowerShellGet har skapats för att undvika att komma ihåg viktig information om att installera från och publicering till PowerShell-galleriet.
Ibland har utgivare valt att hoppa över PowerShellGet och använda NuGet-klienten eller PackageManagement-cmdletar i stället för Publish-Module.
Det finns ett antal information som är enkelt att missade, vilket resulterar i en mängd olika supportärenden.

Om det finns en orsak till att du inte kan använda Publish-Module eller Publish-Script, låt oss veta.
Ett problem i PowerShellGet GitHub-lagringsplatsen och ange information som gör att du kan välja NuGet eller PackageManagement.

## <a name="recommended-workflow"></a>Rekommenderat arbetsflöde

Den mest framgångsrika metoden som vi har hittat för paket som publicerats i PowerShell-galleriet är detta:

- Inledande utveckling i en plats för ett projekt med öppen källkod. PowerShell-teamet använder Github.
- Använd feedback från granskare och [Powershell-skript Analyzer](https://aka.ms/psscriptanalyzer) att hämta koden för att stabilt läge
- Inkludera dokumentation, så att andra vet hur du använder ditt arbete
- Testa publishing åtgärden med en lokal databas.
- Publicera en stabil eller Alpha-versionen till PowerShell-galleriet, se till att inkludera den dokumentation och en länk till projektwebbplatsen
- Samla in feedback och iterera om koden i din projektwebbplats och sedan publicera stabil uppdateringar till PowerShell-galleriet
- Lägg till exempel och Pester tester i ditt projekt och din modul
- Bestäm om du vill kod logga ditt paket
- När du anser att projektet är klart att användas i en produktionsmiljö, publicera en 1.0.0 version PowerShell-galleriet
- Fortsätta att samla in feedback och iterera din kod baserat på indata från användaren
