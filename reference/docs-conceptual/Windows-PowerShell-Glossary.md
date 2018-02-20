---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: "Ordlista för Windows PowerShell"
ms.assetid: b0f88cbe-cb83-4912-a301-184534cb35c7
ms.openlocfilehash: 872ceb342cc72477c5142ce28a9b3b66e32bb84f
ms.sourcegitcommit: 05d576cf107780fa52b2db4a042816be40b00fbc
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/19/2018
---
# <a name="windows-powershell-glossary"></a>Ordlista för Windows PowerShell


|Begrepp|Definition|
|--------|--------------|
|binär modul|Windows PowerShell-modulen vars rotmodul är en binär modulfilen (.dll). En binär modul kan eller kan inte innehålla ett modulmanifest.|
|vanliga parametern|En parameter som läggs till i alla cmdlets avancerade funktioner och arbetsflöden av Windows PowerShell-motorn.|
|dot-källa|I Windows PowerShell, starta ett kommando genom att skriva en punkt eller ett blanksteg före kommandot. Kommandon som är punkt källkod körs i det aktuella omfånget i stället för i ett nytt scope. Alla variabler, alias, funktioner eller enheter som skapas med kommandot skapas i den aktuella omfattningen och är tillgängliga för användare när kommandot har slutförts.|
|dynamisk modul|En modul som endast finns i minnet. Ny modul och importera-PSSession cmdletar skapar dynamiska moduler.|
|Dynamic-parametern|En parameter som läggs till i en Windows PowerShell-cmdleten, en funktion eller ett skript under vissa förhållanden. Cmdlet: ar, funktioner, leverantörer och skript kan lägga till dynamiska parametrar.|
|formatering fil|En Windows PowerShell-XML-fil som har det. format.ps1xml tillägget och som definierar hur Windows PowerShell visar ett objekt baserat på dess typ för .NET Framework.|
|globala sessionstillstånd|Sessionstillståndet som innehåller de data som är tillgänglig för användare av Windows PowerShell-sessionen.|
|värden|Gränssnittet i Windows PowerShell-motorn använder för att kommunicera med användaren. Till exempel anger värden hur frågor hanteras mellan Windows PowerShell och användaren.|
|värdprogrammet|Ett program som läser in Windows PowerShell-motorn i dess process och används för att utföra åtgärder.|
|indata som bearbetar metod|En metod som en cmdlet kan använda för att bearbeta de poster som tas emot som indata. Behandling av inkommande sätt är metoden BeginProcessing, metoden ProcessRecord, metoden EndProcessing och StopProcessing-metoden.|
|manifestmodulen|En Windows PowerShell-modul som har ett manifest och vars RootModule nyckel är tom.|
|modulmanifestet|Windows PowerShell datafil (.psd1) som beskriver innehållet i en modul och som styr hur en modul har bearbetats.|
|modulen sessionstillstånd|Sessionstillståndet som innehåller de offentliga och privata data i en Windows PowerShell-modul. Privata data i den här sessionens tillstånd är inte tillgängliga för användare av Windows PowerShell-sessionen.|
|ej avslutande fel|Ett fel som inte att stoppa Windows PowerShell inte kan fortsätta att bearbeta kommandot.|
|substantiv|Det ord som följer bindestreck i ett Windows PowerShell-cmdlet-namn. Substantivet beskriver de resurser som cmdlet fungerar.|
|Parameteruppsättningen|En grupp av parametrar som kan användas i samma kommando för att utföra en specifik åtgärd.|
|pipe|I Windows PowerShell att skicka resultatet av föregående kommando som indata till nästa kommando i pipelinen.|
|pipeline|En serie kommandon som är anslutna med pipelineoperatorer (&#124;) (ASCII 124). Varje pipelineoperator skickar resultaten från föregående kommando som indata till nästa kommando.|
|PSSession|En typ av Windows PowerShell-session som har skapats, hanteras och stängas av användaren.|
|rotmodul|Modulen som angetts i nyckeln RootModule i ett modulmanifest.|
|Runspace|I Windows PowerShell, den driftsmiljö som varje kommando i en pipeline körs.|
|skriptblock|Programmera språk, en samling med-uttryck eller uttryck som kan användas som en enhet i Windows PowerShell. Ett skriptblock kan ta emot argument och returvärden.|
|skriptmodul|Windows PowerShell-modulen vars rotmodul är en modul-skriptfil (.psm1). En skriptmodul kan eller kan inte innehålla ett modulmanifest.|
|skript-filen för modulen|En fil som innehåller en Windows PowerShell-skript. Skriptet definierar medlemmarna som exporterar skriptet modulen. Modulen skriptfiler har filnamnstillägget .psm1.|
|Shell|Kommandotolken som används för att skicka kommandon till operativsystemet.|
|växeln-parameter|En parameter som inte har ett argument.|
|avslutande felet|Ett fel som förhindrar att Windows PowerShell kommandot bearbetades.|
|Transaktionen|En atomisk arbetsenheten. Resurser i en transaktion måste slutföras som helhet. Om någon del av transaktionen misslyckas, misslyckas hela transaktionen.|
|typer fil|En Windows PowerShell-XML-fil som har filnamnstillägget .ps1xml och som utökar egenskaper för Microsoft .NET Framework-typer i Windows PowerShell.|
|verb|Det ord som föregår bindestreck i ett Windows PowerShell-cmdlet-namn. Verbet som beskriver den åtgärd som utförs av cmdleten.|
|Windows PowerShell|Ett kommandoradsgränssnitt och uppgiftsbaserad skriptteknik som ger omfattande kontroll för IT-administratörer och automatisering av administrationsuppgifter.|
|Windows PowerShell-kommando|Elementen i en pipeline som orsakar en åtgärd som ska utföras. Windows PowerShell-kommandon är angett på tangentbordet eller anropas via programmering.|
|Datafil för Windows PowerShell|En textfil som har filnamnstillägget .psd1. Windows PowerShell använder datafiler för olika ändamål, till exempel modulen manifestet data lagras och lagra översatta strängar för skript internationella.|
|Windows PowerShell-enhet|En virtuell enhet som ger direktåtkomst till ett datalager. Det kan definieras av en Windows PowerShell-provider eller skapats på kommandoraden. Enheter som skapats på kommandoraden är session-specifika enheter och försvinner när sessionen är stängd.|
|Windows PowerShell® Integrated Scripting Environment (ISE)|En Windows PowerShell-värdprogrammet som gör att du kör kommandon att skriva, testa och felsöka skript i ett eget, syntax färg, Unicode-kompatibel miljö.|
|Windows PowerShell-modulen|En egen återanvändbara enhet som hjälper dig att partitionera, ordna och abstrakt Windows PowerShell-koden. En modul kan innehålla cmdlets, providers, funktioner, variabler och andra typer av resurser som kan importeras som en enda enhet.|
|Windows PowerShell-provider|Ett Microsoft .NET Framework-baserade program som tillhandahåller data i en särskild datalagring i Windows PowerShell så att du kan visa och hantera den.|
|Windows PowerShell-skript|Ett skript som skrivits i Windows PowerShell-språk.|
|Windows PowerShell-skriptfil|En fil som har filnamnstillägget .ps1 och som innehåller ett skript som skrivits i Windows PowerShell-språk.|
|Snapin-modulen för Windows PowerShell|En resurs som definierar en uppsättning cmdlets och providers Microsoft .NET Framework-typer som kan läggas till Windows PowerShell-miljö.|
|Windows PowerShell-arbetsflöde|Ett arbetsflöde är en sekvens med programmerade, nätverksanslutna steg som utför tidskrävande uppgifter eller kräver samordning av flera steg i flera enheter eller hanterade noder. Windows PowerShell-arbetsflöde gör att IT-experter och utvecklare kan skriva sekvenser av hantering av flera enheter aktiviteter eller enstaka aktiviteter i ett arbetsflöde, som arbetsflöden. Windows PowerShell-arbetsflöde kan du anpassa och köra både Windows PowerShell-skript och XAML-filer som arbetsflöden.|

