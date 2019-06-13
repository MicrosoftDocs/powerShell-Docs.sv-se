---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Windows PowerShell-ordlista
ms.openlocfilehash: 0827ec771b1744b87a8c0f0ddf48438f9ba484b2
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030350"
---
# <a name="windows-powershell-glossary"></a>Windows PowerShell-ordlista


|Begrepp|Definition|
|--------|--------------|
|binär-modulen|En Windows PowerShell-modul som vars rotmodul är en binär modul-fil (.dll). En binär modul kan eller nödvändigtvis inte ett modulmanifest.|
|vanliga parametern|En parameter som läggs till i alla cmdlets, avancerade funktioner och arbetsflöden med Windows PowerShell-motorn.|
|dot-källa|I Windows PowerShell, för att starta ett kommando genom att skriva en punkt eller ett blanksteg före kommandot. Kommandon som är punkt källkod körs i den aktuella omfattningen i stället för i ett nytt scope. Alla variabler, alias, funktioner eller enheter som kommandot skapar skapas i den aktuella omfattningen och är tillgängliga för användare när kommandot har slutförts.|
|dynamisk modul|En modul som endast finns i minnet. Cmdlet: New-modulen och Import-PSSession skapa dynamiska moduler.|
|dynamisk parameter|En parameter som läggs till i en Windows PowerShell-cmdleten, funktion eller skript på vissa villkor. Cmdlet: ar, funktioner, leverantörer och skript kan lägga till dynamiska parametrar.|
|formatering fil|En Windows PowerShell-XML-fil som har det. format.ps1xml tillägget och som definierar hur Windows PowerShell visar ett objekt baserat på dess typ för .NET Framework.|
|Global sessionstillstånd|Sessionstillstånd som innehåller de data som är tillgänglig för användare av en Windows PowerShell-session.|
|host|Det gränssnitt som Windows PowerShell-motorn använder för att kommunicera med användaren. Till exempel anger värden hur anvisningarna hanteras mellan Windows PowerShell och användaren.|
|värdprogrammet|Ett program som läser in Windows PowerShell-motorn i processen och används för att utföra åtgärder.|
|indata metoden bearbetades|En metod som en cmdlet kan använda för att bearbeta posterna som tas emot som indata. Inkommande bearbetning-sätt är att metoden BeginProcessing, metoden ProcessRecord, metoden EndProcessing och StopProcessing-metoden.|
|manifest-modulen|En Windows PowerShell-modul som har ett manifest och vars RootModule-nyckel är tom.|
|modulmanifestet|Windows PowerShell datafil (.psd1) som beskriver innehållet i en modul och som styr hur en modul har bearbetats.|
|modulen sessionstillstånd|Sessionstillstånd med de offentliga och privata data på en Windows PowerShell-modulen. Privata data i den här sessionstillstånd är inte tillgänglig för användare av en Windows PowerShell-session.|
|icke-avslutande fel|Ett fel som inte hindrar Windows PowerShell inte kan fortsätta att bearbeta kommandot.|
|substantiv|Ord som följer bindestreck i en Windows PowerShell cmdlet-namn. Substantivet beskriver de resurser som cmdlet: en fungerar.|
|Parameteruppsättning|En grupp med parametrar som kan användas i samma kommando för att utföra en viss åtgärd.|
|pipe|I Windows PowerShell, för att skicka resultaten från föregående kommando som indata till nästa kommando i pipelinen.|
|pipeline|En serie kommandon som är anslutna via pipeline-operatorer (&#124;) (ASCII 124). Varje pipelineoperatorn skickar resultaten från föregående kommando som indata till nästa kommando.|
|PSSession|En typ av Windows PowerShell-session som har skapats kan hanteras och avslutades av användaren.|
|rotmodul|Modulen som anges i nyckeln RootModule i ett modulmanifest.|
|körningsutrymme|I Windows PowerShell, driftmiljön där varje kommando i en pipeline körs.|
|skriptblocket|Programmera språk, en samling med uttryck eller uttryck som kan användas som en enhet i Windows PowerShell. Ett skriptblock kan acceptera argument och returnerar värden.|
|modul skriptu powershellu|En Windows PowerShell-modul som vars rotmodul är en modul-skriptfil (.psm1). En skriptmodul kan eller nödvändigtvis inte ett modulmanifest.|
|skript-filen för modulen|En fil som innehåller ett Windows PowerShell-skript. Skriptet definierar de medlemmar som modulen skriptet exporterar. Modulen skriptfiler har .psm1-filnamnstillägg.|
|Shell|Kommandotolken som används för att skicka kommandon till operativsystemet.|
|växlingsparametern|En parameter som inte har ett argument.|
|avslutande fel|Ett fel som förhindrar att Windows PowerShell kommandot bearbetades.|
|Transaktionen|En atomisk enhet för arbete. Arbete i en transaktion måste slutföras som helhet. Om någon del av transaktionen misslyckas, inte hela transaktionen.|
|typer av fil|En Windows PowerShell-XML-fil som har tillägget .ps1xml och som utökar egenskaperna för Microsoft .NET Framework-typer i Windows PowerShell.|
|verb|Ord som föregår bindestreck i en Windows PowerShell cmdlet-namn. Verbet beskriver den åtgärd som utförs av cmdlet: en.|
|Windows PowerShell|Ett kommandoradsgränssnitt och uppgiftsbaserad skriptteknik som tillhandahåller omfattande kontroll för IT-administratörer och automatisering av administrationsuppgifter.|
|Windows PowerShell-kommando|Element i en pipeline som orsakar en åtgärd som ska utföras. Windows PowerShell-kommandon är antingen angett på tangentbordet eller anropas via programmering.|
|Datafil för Windows PowerShell|En textfil med filnamnstillägget .psd1. Windows PowerShell använder filer för olika ändamål, till exempel lagra modulen manifest data och lagra översatta strängar för skriptet nationella inställningar.|
|Windows PowerShell-enhet|En virtuell enhet som ger direktåtkomst till ett datalager. Det kan definieras av en Windows PowerShell-providern eller skapas på kommandoraden. Enheter som skapats på kommandoraden är session-specifika enheter och försvinner när sessionen är stängd.|
|Windows PowerShell ISE (Integrated Scripting Environment)|Ett värdprogram för Windows PowerShell som gör det möjligt att köra kommandon och att skriva, testa och felsöka skript i ett eget, syntax färg, Unicode-kompatibel miljö.|
|Windows PowerShell-modulen|En självständig återanvändbara enhet där du kan partitionera, ordna och abstrahera dina Windows PowerShell-kod. En modul kan innehålla cmdlets, providers, funktioner, variabler och andra typer av resurser som kan importeras som en enda enhet.|
|Windows PowerShell-providern|Ett Microsoft .NET Framework-baserade program som tillhandahåller data i ett specialiserade datalager i Windows PowerShell så att du kan visa och hantera den.|
|Windows PowerShell-skript|Ett skript som är skriven i Windows PowerShell-språket.|
|Windows PowerShell-skriptfil|En fil med tillägget .ps1 och som innehåller ett skript som är skriven i Windows PowerShell-språket.|
|Snapin-modulen för Windows PowerShell|En resurs som definierar en uppsättning cmdlets och leverantörer av Microsoft .NET Framework-typer som kan läggas till i Windows PowerShell-miljö.|
|Windows PowerShell-arbetsflöde|Ett arbetsflöde är en sekvens med programmerade, nätverksanslutna steg som utför tidskrävande uppgifter eller kräver samordning av flera steg i flera enheter eller hanterade noder. Windows PowerShell-arbetsflöde kan IT-proffs och utvecklare kan skriva sekvenser av hantering av flera enheter aktiviteter eller enstaka aktiviteter i ett arbetsflöde, som arbetsflöden. Windows PowerShell-arbetsflöde kan du anpassa och kör både Windows PowerShell-skript och XAML-filer som arbetsflöden.|
