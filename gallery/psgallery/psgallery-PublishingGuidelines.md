---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: galleriet, powershell, cmdlet, psgallery
description: "Riktlinjer för utgivare"
title: "PowerShell-galleriet publicering riktlinjer och bästa praxis"
ms.openlocfilehash: 882a33c00cc024ad2bbb05a3283e058a61035e3a
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2017
---
# <a name="powershellgallery-publishing-guidelines-and-best-practices"></a>PowerShellGallery publicering riktlinjer och bästa praxis

Det här avsnittet beskrivs rekommenderade steg som används av Microsoft team för att se till att objekt som publicerats i PowerShell-galleriet kommer användas brett och tillhandahålla högt värde för användare, baserat på hur manifestet data hanteras i PowerShell-galleriet och feedback från stora tal PowerShell-galleriet användare.
Objekt som är publicerade följa dessa riktlinjer tas mer troligt att installeras, betrodd, och ger dig fler användare.

Nedan följer riktlinjer för vad som gör ett bra PowerShell galleriobjekt, vilka valfria inställningar för manifestet är viktigast, förbättra din kod med feedback från första granskare och [Powershell-skript Analyzer](https://aka.ms/psscriptanalyzer), versionshantering din modul, dokumentation, tester och exempel på hur du använder du har delat.
En stor del av den här dokumentationen följer riktlinjerna för publicering [hög kvalitet DSC resurs moduler](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md).

Publicera ett objekt i PowerShell-galleriet säkerhetsnivån finns [skapa och publicera en artikel](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/creating-and-publishing-an-item).

Feedback om dessa riktlinjer välkomnade. Om du har feedback, öppnar du problem i våra [Github dokumentationen databasen](https://github.com/powershell/powershell-docs/).

## <a name="best-practices-for-publishing-items"></a>Metodtips för publicering av objekt

Följande säkerhetsmetoder är vad användarna av PowerShell galleriobjekt säga är viktigt och visas i nominell prioritetsordning.
Objekt som följer dessa riktlinjer är mycket troligt att hämtas och antas av andra.

* Använd PSScriptAnalyzer
* Innehåller dokumentation och exempel
* Att svara på feedback
* Ange moduler i stället för skript
* Innehåller länkar till en projektwebbplats
* Inkludera tester med din moduler
* Inkludera och/eller länka till licensvillkoren
* Registrera din kod
* Följ [SemVer](http://semver.org/) riktlinjer för versionshantering
* Använd vanliga taggar, enligt beskrivningen i vanliga PowerShell-galleriet taggar
* Testa publicering med en lokal databas

Var och en av dessa beskrivs kortfattat i avsnitten nedan.

## <a name="use-psscriptanalyzer"></a>Använd PSScriptAnalyzer

[PSScriptAnalyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer) är ett analysverktyg för statisk kod som fungerar på PowerShell-koden.
PSScriptAnalyzer identifierar de vanligaste problem som visas i PowerShell-koden och ofta en rekommendation för hur du löser problemet.
Verktyget är enkel att använda och kategoriserar problem som fel (allvarligt, måste åtgärdas), varning (måste granskas och bör åtgärdas) och Information (värt att checka ut metodtips).
Alla objekt-objektet som publicerats till PowerShell-galleriet genomsöks med PSScriptAnalyzer och eventuella problem rapporteras tillbaka till ägaren och måste åtgärdas.

Det bästa sättet är att köra `Invoke-ScriptAnalyzer` med `-Recurse` och `-Severity` varning.

Granska resultaten och se till att:

* Alla fel korrigeras eller beskrivs i dokumentationen till
* Alla varningar granskas och åtgärdas tillämpliga

Användare som skaffar objekt från PowerShell-galleriet rekommenderas att köra PSScriptAnalyzer och utvärdera alla fel och varningar.
Användare är mycket troligt att kontakta objektet ägare om de kan se att det finns ett fel rapporterat av PSScriptAnalyzer.
Lägg till denna information i dokumentationen för att undvika att svara många gånger för samma fråga om starka skäl för din artikel för att hålla kod som har flaggats som ett fel.

## <a name="include-documentation-and-examples"></a>Innehåller dokumentation och exempel

Dokumentation och exempel är det bästa sättet att se till att användare kan dra nytta av någon delad kod.

Dokumentation är det mest användbara som ska ingå i objekt som publicerats i PowerShell-galleriet.
Användare kommer vanligtvis att kringgå objekt utan dokumentation, när alternativet är att läsa koden för att förstå artikeln är och hur du använder den.
Det finns flera artiklar i MSDN om hur du skapar dokumentation med PowerShell-artiklar, inklusive:

* Riktlinjer för att tillhandahålla hjälp finns i [så att skriva Cmdlet](https://go.microsoft.com/fwlink/?LinkID=123415)
* Skapa cmdlet-hjälpen, vilket är det bästa sättet för PowerShell-skript, funktion eller cmdlet.
  Information om hur du skapar cmdlet-hjälpen börjar du med [så att skriva Cmdlet](https://go.microsoft.com/fwlink/?LinkID=123415) i MSDN library.
  Om du vill lägga till hjälp i ett skript, se [om kommentar baserat hjälpa](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_comment_based_help).
* Många moduler kan du också inkludera dokumentationen i textformat, till exempel MarkDown-filer.
  Det kan vara särskilt användbart när det finns en projektwebbplats i Github, där Markdown är hårt belastat format.
  Det bästa sättet är att använda [Markdown i Github](https://help.github.com/categories/writing-on-github/)

Exemplen visar användare hur artikeln är avsedd att användas.
Många utvecklare säger att de letar på exempel innan dokumentation för att förstå hur du använder något.
Bästa är exemplen visar grundläggande användning, plus en simulerad realistiska användningsfall och koden korrekt kommenterad.
Exempel på moduler som har publicerats till PowerShell-galleriet måste vara i en exempel-mapp under roten för modulen.

Ett bra mönster exempel finns i den [PSDscResource modulen](https://www.powershellgallery.com/packages/PSDscResources) under mappen Examples\RegistryResource.
Det finns fyra exempel användningsområden med en kort beskrivning längst upp i varje fil som dokument vad som visas.

## <a name="respond-to-feedback"></a>Svara på feedback

Ägare av objekt som ska svara på feedback värderas hög gemenskapen.
Användare som anger informell feedback är viktigt att svara på, som de är intresserad av i objektet att förbättra den.

Det finns två metoder för feedback i PowerShell-galleriet:

* Kontakta ägaren: Detta gör det möjligt att skicka ett e-postmeddelande till dess ägare för objektet. Är viktigt att övervaka e-postadressen används med PowerShell-galleriet artiklar och svara på problem som aktiveras som en artikel ägare. En nackdel till den här metoden är att endast användare och ägare kommer någonsin se kommunikation, så ägaren kan svara på samma fråga många gånger.
* Kommentarer: Längst ned på sidan objektet är ett kommentarer.
  Fördelen med att systemet är att andra användare kan se kommentarer och svar, vilket minskar antalet gånger som en enskild fråga som måste besvaras.
  Som en artikel ägare rekommenderar vi att du följer kommentarer för varje objekt.
Se [ger Feedback via sociala medier eller kommentarer](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery-SocialMediaFeedback) information om hur du gör.

Ägare som svara på feedback på konstruktiva sätt uppskattas av gruppen.
Använda möjlighet i rapporten för att begära mer information om det behövs, tillhandahålla en lösning eller identifiera om en uppdatering för att rätta till problemet.

Om det är olämpligt observerats från någon av dessa kommunikationskanaler, använder du funktionen Rapportera missbruk av PowerShell-galleriet för att kontakta Gallery-administratörer.

## <a name="modules-versus-scripts"></a>Moduler jämfört med skript

Dela ett skript med andra användare är bra och ger andra exempel på hur du löser problem som de kan ha.
Problemet är att skript i PowerShell-galleriet enskilda filer utan separat dokumentation, exempel och tester.

PowerShell-moduler har en mappstruktur som gör att flera mappar och filer som ska ingå i paketet.
Modulstrukturen kan även andra objekt som vi listan som bästa praxis: cmdlet hjälp, dokumentation, exempel och tester.
Den största nackdelen är att ett skript i en modul måste exponeras och användas som en funktion.
Information om hur du skapar en modul finns [skriva en Windows PowerShell-modulen](http://go.microsoft.com/fwlink/?LinkId=144916).

Det finns situationer där ett skript som ger en bättre upplevelse för användare, särskilt med DSC-konfigurationer.
Bästa praxis för DSC-konfigurationer är att publicera konfigurationen som ett skript med en tillhörande modul som innehåller dokument, exempel och tester.
Skriptet innehåller medföljande modulen med RequiredModules = @(namnet på modulen).
Den här metoden kan användas med alla skript.

Fristående skript som följer bästa praxis ange verkliga värde till andra användare.
Ange kommentarbaserad dokumentation och en länk till en plats för projektet rekommenderas när du publicerar ett skript i PowerShell-galleriet.

## <a name="provide-a-link-to-a-project-site"></a>Ange en länk till en projektwebbplats

En plats för projektet är där en utgivare kan interagera direkt med användare av deras PowerShell galleriobjekt.
Användare föredrar artiklar som innehåller det som den kan användas för att få information om objektet enklare.
Många element i PowerShell-galleriet utvecklas i GitHub, tillhandahålls andra av organisationer med en dedikerad webben.
Var och en av dessa kan betraktas som en projektwebbplats.

En ny länk görs genom att inkludera ProjectURI i avsnittet PSData i manifestet på följande sätt:

        # A URL to the main website for this project.
        ProjectUri = 'https://github.com/powershell/powershell'

När en ProjectURI tillhandahålls innehåller PowerShell-galleriet en länk till webbplatsen projekt till vänster på sidan för objektet.

## <a name="include-tests"></a>Inkludera tester

Inklusive tester med öppen källkod är viktigt att användare, eftersom den ger försäkran om vad du validera och innehåller information om hur koden fungerar. Det gör också användarna för att säkerställa att de inte dela din ursprungliga funktionen om de ändra din kod så att den passar deras miljö.

Du rekommenderas att testerna skrivas till dra nytta av Pester test framework, som har utformats speciellt för PowerShell.
Lära finns i [GitHub](https://github.com/Pester/Pester), [PowerShell-galleriet](https://www.powershellgallery.com/packages/Pester/), och levereras i Windows 10, Windows Server 2016, WMF 5.0 och WMF 5.1.

Den [Pester project-webbplats i GitHub](https://github.com/Pester/Pester) innehåller bra dokumentationen om hur du skriver Pester tester från att komma igång med bästa praxis.

Mål för test täckning påpekas i den [hög kvalitet Resursmodul dokumentationen](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md), testa koden täckning bör med 70% enhet.

## <a name="include-andor-link-to-license-terms"></a>Inkludera och/eller länka till licensvillkoren

Alla objekt som har publicerats i PowerShell-galleriet måste ange licensvillkoren eller vara bunden av licensen ingår i den [användningsvillkoren](https://www.powershellgallery.com/policies/Terms) under ”bilaga A”.
Den bästa metoden för att ange en annan licens är att tillhandahålla en länk till licensen med LicenseURI i PSData.
Du hittar ett exempel i avsnittet rekommenderas Manifest fält.

```powershell
PrivateData = @{
    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        Tags = @('.net','acl','active-directory')

        # A URL to the license for this module.
        LicenseUri = 'http://www.apache.org/licenses/LICENSE-2.0'
```

## <a name="sign-your-code"></a>Registrera din kod

Kodsignering förser användare med den högsta säkerhetsnivån för vem som publicerade artikeln och att kopian av koden de skaffar är exakt utgivaren släpps.
Mer information om kodsignering vanligtvis finns [introduktion till kodsignering](http://go.microsoft.com/fwlink/?LinkId=106296).
PowerShell stöder validering av kodsignering via två primära sätt:

* Signering skriptfiler
* Katalogen som registrerar en modul

Signering av PowerShell-filer är en väletablerade metod för att säkerställa som koden utförs tillhandahålls av en pålitlig källa och inte har ändrats.
Information om hur du anmäler PowerShell skriptfiler ingår i den [om signering](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_signing) avsnittet.
En signatur kan läggas till någon i Översikt. Ps1-fil som PowerShell validerar när skriptet har lästs in.
PowerShell kan begränsas med hjälp av den [körningsprincipen](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_execution_policies) -cmdletar för att kontrollera användningen av signerade skript.

Katalogen signering moduler är en funktion som lagts till PowerShell i version 5.1.
Hur du registrerar en modul beskrivs i den [katalog Cmdlets](https://msdn.microsoft.com/en-us/powershell/wmf/5.1/catalog-cmdlets) avsnittet.
I Översikt görs katalog signering genom att skapa en katalogfil som innehåller ett hash-värde för varje fil i modulen, och sedan signera filen.
PowerShellGet publicera modul, installera modulen, spara modulen och update-module cmdlets ska kontrollera signaturen för att säkerställa att det är giltigt och bekräfta sedan att hash-värdet för varje objekt matchar vad som finns i katalogen.
Om en tidigare version av modulen är installerad på datorn, bekräftar installera modulen att signering behörighet för den nya versionen matchar den tidigare installerade.
Katalogen signering fungerar med, men ersätter inte skriptfiler för signering. PowerShell validerar inte katalogen signaturer på modulen inläsningstid.

## <a name="follow-semver-guidelines-for-versioning"></a>Följ SemVer riktlinjer för versionshantering

[SemVer](http://semver.org/) är en offentlig konvention som beskriver hur du struktur och ändra en version för att tillåta enkel intepretation av ändringar.
Versionen för objektet måste tas med i manifestet data.

* Versionen ska vara strukturerad som 3 numeriska block avgränsade med punkter som 0.1.1 eller 4.11.192
* Versioner som börjar med ”0” anger att objektet är ännu inte klar produktion och den första siffran bara ska börja med ”0” om det är det enda nummer som används
* Ändringar i den första siffran (1.9.9999 2.0.0) ange högre och gör ändringar mellan versioner
* Ändringar i det andra talet (1.01 1,02) Ange funktionsnivå ändringar, till exempel att lägga till nya cmdlet: ar i en modul
* Ändringar i det tredje talet anger hårt ändringar, till exempel nya parametrar, uppdaterade exempel eller nya tester
* När du visar en lista över versioner, PowerShell om du vill sortera versionerna som strängar, så 1.01.0 behandlas som är större än 1.001.0

PowerShell skapades innan SemVer publicerades så att den har stöd för de flesta, men inte alla element i SemVer, speciellt:

* Det stöder inte förhandsversionen strängar i versionsnummer. Detta är användbart när en utgivare önskar att leverera en förhandsversionen av en ny högre version när du har angett en version 1.0.0. Detta kommer att stödjas i en framtida version av PowerShell-galleriet och PowerShellGet-cmdlets.
* Tillåt version strängar med 1, 2 och 4 segment PowerShell och PowerShell-galleriet. Många tidig moduler följer inte riktlinjerna och produktversioner från Microsoft build information som en 4 blockera med tal (till exempel 5.1.14393.1066). Från en versionshantering synvinkel ignoreras dessa skillnader.

## <a name="test-using-a-local-repository"></a>Testa med en lokal databas

PowerShell-galleriet är inte avsedd att vara målet för att testa publiceringsprocessen.
Det bästa sättet att testa slutpunkt till slutpunkt-processen för publicering till PowerShell-galleriet är att ställa in och använda lokala databasen.
Detta kan göras på flera sätt, inklusive:

* Konfigurera en lokal instans i PowerShell-galleriet med hjälp av den [PS privata galleriet projektet](https://github.com/PowerShell/PSPrivateGallery) i Github. Förhandsgranska projektet hjälper dig att konfigurera en instans av PowerShell-galleriet som du kan styra och användning för dina tester.
* Konfigurera en [interna Nuget databasen](https://blogs.msdn.microsoft.com/powershell/2014/05/20/setting-up-an-internal-powershellget-repository/). Detta kräver mer arbete att ställa in, men har fördelen med att verifiera några fler krav, särskilt verifiera användning av en API-nyckel, och om beroenden finns i mål när du publicerar.
* Skapa en filresurs som test ”databas”. Det är enkelt att ställa in, men eftersom det är en filresurs verifieringar som nämns ovan sker inte. En potentiella fördelar är i det här fallet att filresursen kontrollerar inte (obligatoriskt) API-nyckeln, så du kan använda samma nyckel sätt för att publicera till PowerShell-galleriet.

Med någon av dessa lösningar, använder du registrera PSRepository för att definiera en ny ”databas”, som du använder i egenskapen - databasen för publicera-modulen.

Ytterligare en punkt om test publicering: ett objekt som du publicerar till PowerShell-galleriet kan inte tas bort utan hjälp från operations-teamet som bekräftar att inget är beroende av objektet du vill publicera.
Därför vi har inte stöd för PowerShell-galleriet som tester mål och kommer att kontakta alla utgivare som sker.

## <a name="recommended-workflow"></a>Rekommenderat arbetsflöde

Det effektivaste sättet som vi har hittat för objekt som publicerats i PowerShell-galleriet är:

* Inledande utveckling i en en öppen källkod projektwebbplats. PowerShell-teamets använder Github.
* Använd feedback från granskare och [Powershell-skript Analyzer](https://aka.ms/psscriptanalyzer) att hämta koden för att stabilt tillstånd
* Innehåller dokumentation, så att andra känna till hur du använder ditt arbete
* Testa publishing åtgärden med hjälp av en lokal databas.
* Publicera en stabil eller alfanumeriska versionen till PowerShell-galleriet, se till att inkludera dokumentation och länk till projektwebbplatsen
* Samla in feedback och iterera koden på din projektwebbplats och sedan publicera stabil uppdateringar till PowerShell-galleriet
* Lägg till exempel och Pester test i ditt projekt och din modul
* Bestäm om du vill kod logga objektet
* När du anser att projektet är redo att användas i en produktionsmiljö, publicera en 1.0.0 version i PowerShell-galleriet
* Fortsätta att samla in feedback och iterera din kod baserat på indata från användaren