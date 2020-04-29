---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Windows PowerShell-ordlista
ms.openlocfilehash: 0827ec771b1744b87a8c0f0ddf48438f9ba484b2
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030350"
---
# <a name="windows-powershell-glossary"></a>Windows PowerShell-ordlista


|Period|Definition|
|--------|--------------|
|binär modul|En Windows PowerShell-modul vars modul är en binärfil (. dll). En binär modul kan eventuellt innehålla ett modul manifest.|
|gemensam parameter|En parameter som läggs till i alla cmdletar, avancerade funktioner och arbets flöden med Windows PowerShell-motorn.|
|punkt källa|Starta ett kommando genom att skriva en punkt och ett blank steg före kommandot i Windows PowerShell. Kommandon som är punktbaserade körs i det aktuella omfånget i stället för i ett nytt omfång. Variabler, alias, funktioner eller enheter som skapas av kommandot skapas i det aktuella omfånget och är tillgängliga för användarna när kommandot har slutförts.|
|dynamisk modul|En modul som bara finns i minnet. Cmdletarna New-module och import-PSSession skapar dynamiska moduler.|
|dynamisk parameter|En parameter som läggs till i en Windows PowerShell-cmdlet, funktion eller skript under vissa förhållanden. Cmdlets, functions, providers och scripts kan lägga till dynamiska parametrar.|
|formaterar fil|En Windows PowerShell XML-fil med tillägget. format. ps1xml och som definierar hur Windows PowerShell visar ett objekt baserat på dess .NET Framework typ.|
|tillstånd för global session|Sessionstillståndet som innehåller de data som är tillgängliga för användaren av en Windows PowerShell-session.|
|värd|Gränssnittet som Windows PowerShell-motorn använder för att kommunicera med användaren. Värden anger till exempel hur prompter ska hanteras mellan Windows PowerShell och användaren.|
|värd program|Ett program som läser in Windows PowerShell-motorn i sin process och använder den för att utföra åtgärder.|
|metod för bearbetning av indata|En metod som en cmdlet kan använda för att bearbeta de poster som tas emot som inmatade. Metoderna för bearbetning av indata omfattar metoden BeginProcessing, metoden ProcessRecord, metoden EndProcessing och metoden StopProcessing.|
|manifest modul|En Windows PowerShell-modul som har ett manifest och vars RootModule-nyckel är tom.|
|modul manifest|En Windows PowerShell-datafil (. psd1) som beskriver innehållet i en modul och som styr hur en modul bearbetas.|
|sessionstillstånd för modul|Sessionstillståndet som innehåller offentliga och privata data för en Windows PowerShell-modul. Status för privata data i det här sessionstillståndet är inte tillgänglig för användaren av en Windows PowerShell-session.|
|icke-avslutande fel|Ett fel som inte stoppar Windows PowerShell från att fortsätta bearbeta kommandot.|
|Substantiv|Ordet som följer bindestrecket i ett namn för Windows PowerShell-cmdleten. I substantivet beskrivs resurserna som cmdleten fungerar på.|
|parameter uppsättning|En grupp parametrar som kan användas i samma kommando för att utföra en speciell åtgärd.|
|pipe|I Windows PowerShell skickar du resultatet från föregående kommando som inmatade till nästa kommando i pipelinen.|
|pipeline|En serie kommandon som är anslutna av pipeline-operatörer (&#124;) (ASCII 124). Varje pipeline-operator skickar resultatet från föregående kommando som inmatat till nästa kommando.|
|PSSession|En typ av Windows PowerShell-session som skapas, hanteras och stängs av användaren.|
|modul för rot|Modulen som anges i RootModule-nyckeln i ett modul manifest.|
|körnings utrymme|I Windows PowerShell körs den drifts miljö där varje kommando i en pipeline körs.|
|skript block|I programmeringsspråk för Windows PowerShell, en samling med instruktioner eller uttryck som kan användas som en enda enhet. Ett skript block kan acceptera argument och returnerade värden.|
|skriptbaserad modul|En Windows PowerShell-modul vars rotnod är en skript-modul (. psm1). En skript-modul kan inte innehålla ett modul manifest.|
|modul för skript fil|En fil som innehåller ett Windows PowerShell-skript. Skriptet definierar de medlemmar som script module exporterar. Filer i skriptfiler har fil namns tillägget. psm1.|
|kal|Kommando tolken som används för att skicka kommandon till operativ systemet.|
|växlings parameter|En parameter som inte tar ett argument.|
|avslutar fel|Ett fel som förhindrar att Windows PowerShell bearbetar kommandot.|
|transaktionen|En atomisk arbets enhet. Arbetet i en transaktion måste slutföras i helheten. om någon del av transaktionen Miss lyckas, Miss lyckas hela transaktionen.|
|typ fil|En Windows PowerShell XML-fil som har fil namns tillägget. ps1xml och som utökar egenskaperna för Microsoft .NET Framework-typer i Windows PowerShell.|
|verb|Ordet som föregår bindestrecket i ett Windows PowerShell-cmdlet-namn. Verbet beskriver den åtgärd som cmdleten utför.|
|Windows PowerShell|En kommando rads gränssnitt och uppgiftsbaserade skript teknik som ger IT-administratörer heltäckande kontroll och automatisering av system administrations uppgifter.|
|Windows PowerShell-kommando|De element i en pipeline som gör att en åtgärd utförs. Windows PowerShell-kommandon skrivs antingen på tangent bordet eller anropas program mässigt.|
|Windows PowerShell-datafil|En textfil med fil namns tillägget. psd1. Windows PowerShell använder datafiler för olika ändamål, till exempel lagring av modulens manifest data och lagring av översatta strängar för skript internationalisering.|
|Windows PowerShell-enhet|En virtuell enhet som ger direkt åtkomst till ett data lager. Den kan definieras av en Windows PowerShell-provider eller skapas på kommando raden. Enheter som skapas på kommando raden är sessionsbaserade enheter och går förlorade när sessionen stängs.|
|Windows PowerShell ISE (Integrated Scripting Environment)|Ett Windows PowerShell-värdprogram som gör att du kan köra kommandon och skriva, testa och felsöka skript i en egen, syntax, Unicode-kompatibel miljö.|
|Windows PowerShell-modul|En fristående åter användnings enhet som gör att du kan partitionera, organisera och abstrakta din Windows PowerShell-kod. En modul kan innehålla cmdlets, providrar, funktioner, variabler och andra typer av resurser som kan importeras som en enda enhet.|
|Windows PowerShell-Provider|Ett Microsoft .NET Framework-baserat program som gör data i ett specialiserat data lager tillgängligt i Windows PowerShell så att du kan visa och hantera dem.|
|Windows PowerShell-skript|Ett skript som är skrivet på Windows PowerShell-språket.|
|Skript fil för Windows PowerShell|En fil som har fil namns tillägget. ps1 och som innehåller ett skript som är skrivet på Windows PowerShell-språket.|
|Windows PowerShell-snapin-modul|En resurs som definierar en uppsättning cmdlets, providers och Microsoft .NET Framework-typer som kan läggas till i Windows PowerShell-miljön.|
|Windows PowerShell-arbetsflöde|Ett arbetsflöde är en sekvens med programmerade, nätverksanslutna steg som utför tidskrävande uppgifter eller kräver samordning av flera steg i flera enheter eller hanterade noder. Med Windows PowerShell-arbetsflöde kan IT-proffs och utvecklare skapa sekvenser av hanterings aktiviteter för flera enheter, eller enstaka aktiviteter i ett arbets flöde, som arbets flöden. Med Windows PowerShell-arbetsflöde kan du anpassa och köra både Windows PowerShell-skript och XAML-filer som arbets flöden.|
