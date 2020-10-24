---
ms.date: 06/11/2020
keywords: powershell,cmdlet
title: PowerShell-ordlista
description: En ord lista med PowerShell-relaterad terminologi.
ms.openlocfilehash: 75b1ed69df7547474687361a9ad3a15e1d677cdc
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92499900"
---
# <a name="powershell-glossary"></a>PowerShell-ordlista

|            Period             | Definition |
| --------------------------- | ---------- |
| binär modul               | En PowerShell-modul vars rotnod är en binär modul (. dll). En binär modul kan eventuellt innehålla ett modul manifest. |
| gemensam parameter            | En parameter som läggs till i alla cmdletar, avancerade funktioner och arbets flöden av PowerShell-motorn. |
| punkt källa                  | Starta ett kommando genom att skriva en punkt och ett blank steg före kommandot i PowerShell. Kommandon som är punktbaserade körs i det aktuella omfånget i stället för i ett nytt omfång. Variabler, alias, funktioner eller enheter som skapas av kommandot skapas i det aktuella omfånget och är tillgängliga för användarna när kommandot har slutförts. |
| dynamisk modul              | En modul som bara finns i minnet. New-Module-och Import-PSSession-cmdletarna skapar dynamiska moduler. |
| dynamisk parameter           | En parameter som läggs till i en PowerShell-cmdlet, funktion eller skript under vissa förhållanden. Cmdlets, functions, providers och scripts kan lägga till dynamiska parametrar. |
| formaterar fil             | En PowerShell XML-fil som har `.format.ps1xml` tillägget och som definierar hur PowerShell visar ett objekt baserat på dess .NET Framework typ. |
| tillstånd för global session        | Sessionstillståndet som innehåller de data som är tillgängliga för användaren av en PowerShell-session. |
| värd                        | Gränssnittet som PowerShell-motorn använder för att kommunicera med användaren. Värden anger till exempel hur prompter hanteras mellan PowerShell och användaren. |
| värd program            | Ett program som läser in PowerShell-motorn i sin process och använder den för att utföra åtgärder. |
| metod för bearbetning av indata     | En metod som en cmdlet kan använda för att bearbeta de poster som tas emot som inmatade. Metoderna för bearbetning av indata omfattar metoden BeginProcessing, metoden ProcessRecord, metoden EndProcessing och metoden StopProcessing. |
| manifest modul             | En PowerShell-modul som har ett manifest och vars RootModule-nyckel är tom. |
| modulen                      | En fristående åter användnings enhet som gör att du kan partitionera, organisera och abstrakta din PowerShell-kod. En modul kan innehålla cmdlets, providrar, funktioner, variabler och andra typer av resurser som kan importeras som en enda enhet. |
| modul manifest             | En PowerShell-datafil ( `.psd1` ) som beskriver innehållet i en modul och som styr hur en modul bearbetas. |
| sessionstillstånd för modul        | Sessionstillståndet som innehåller offentliga och privata data för en PowerShell-modul. Den privata informationen i det här sessionstillståndet är inte tillgänglig för användaren av en PowerShell-session. |
| icke-avslutande fel       | Ett fel som inte hindrar PowerShell från att fortsätta bearbeta kommandot. |
| Substantiv                        | Ordet som följer bindestrecket i ett PowerShell-cmdlet-namn. I substantivet beskrivs resurserna som cmdleten fungerar på. |
| parameter uppsättning               | En grupp parametrar som kan användas i samma kommando för att utföra en speciell åtgärd. |
| pipe                        | I PowerShell skickar du resultatet från föregående kommando som inmatat till nästa kommando i pipelinen. |
| pipeline                    | En serie kommandon som är anslutna av pipeline-operatörer (&#124;) (ASCII 124). Varje pipeline-operator skickar resultatet från föregående kommando som inmatat till nästa kommando. |
| PowerShell-cmdlet           | Ett enda kommando som ingår i pipeline-semantiken för PowerShell. Detta inkluderar binära (C#) cmdlets, avancerade skript funktioner, CDXLM och arbets flöden. |
| PowerShell-kommando          | De element i en pipeline som gör att en åtgärd utförs. PowerShell-kommandon skrivs antingen på tangent bordet eller anropas program mässigt. |
| PowerShell-datafil        | En textfil med `.psd1` fil namns tillägget. PowerShell använder datafiler för olika ändamål, till exempel lagring av modulens manifest data och för att lagra översatta strängar för skript internationalisering. |
| PowerShell-enhet            | En virtuell enhet som ger direkt åtkomst till ett data lager. Den kan definieras av en PowerShell-provider eller skapas på kommando raden. Enheter som skapas på kommando raden är sessionsbaserade enheter och går förlorade när sessionen stängs. |
| CSP                    | Ett Microsoft .NET Framework-baserat program som gör data i ett specialiserat data lager tillgängligt i PowerShell så att du kan visa och hantera dem. |
| PSSession                   | En typ av PowerShell-session som skapas, hanteras och stängs av användaren. |
| modul för rot                 | Modulen som anges i RootModule-nyckeln i ett modul manifest. |
| körnings utrymme                    | I PowerShell körs den drifts miljö där varje kommando i en pipeline körs. |
| skript block                | I PowerShell-programmeringsspråket kan du använda en samling uttryck eller uttryck som kan användas som en enda enhet. Ett skript block kan acceptera argument och returnerade värden. |
| skript fil                 | En fil som har `.ps1` tillägget och som innehåller ett skript som är skrivet på PowerShell-språket. |
| skriptbaserad modul               | En PowerShell-modul vars rotnod är en skript-modul ( `.psm1` ). En skript-modul kan inte innehålla ett modul manifest. |
| modul för skript fil          | En fil som innehåller ett PowerShell-skript. Skriptet definierar de medlemmar som script module exporterar. Filer för skriptfiler har `.psm1` fil namns tillägget. |
| kal                       | Kommando tolken som används för att skicka kommandon till operativ systemet. |
| växlings parameter            | En parameter som inte tar ett argument. |
| avslutar fel           | Ett fel som hindrar PowerShell från att bearbeta kommandot. |
| transaktionen                 | En atomisk arbets enhet. Arbetet i en transaktion måste slutföras i helheten. om någon del av transaktionen Miss lyckas, Miss lyckas hela transaktionen. |
| typ fil                  | En PowerShell XML-fil som har `.ps1xml` tillägget och som utökar egenskaperna för Microsoft .NET Framework-typer i PowerShell. |
| verb                        | Ordet som föregår bindestrecket i ett PowerShell-cmdlet-namn. Verbet beskriver den åtgärd som cmdleten utför. |
| Windows PowerShell ISE      | Den integrerade skript miljön – ett Windows PowerShell-värdprogram som gör att du kan köra kommandon och skriva, testa och felsöka skript i en egen, syntax, Unicode-kompatibel miljö. |
| Windows PowerShell-snapin-modul  | En resurs som definierar en uppsättning cmdlets, providers och Microsoft .NET Framework-typer som kan läggas till i Windows PowerShell-miljön. |
| Windows PowerShell-arbetsflöde | Ett arbetsflöde är en sekvens med programmerade, nätverksanslutna steg som utför tidskrävande uppgifter eller kräver samordning av flera steg i flera enheter eller hanterade noder. Med Windows PowerShell-arbetsflöde kan IT-proffs och utvecklare skapa sekvenser av hanterings aktiviteter för flera enheter, eller enstaka aktiviteter i ett arbets flöde, som arbets flöden. Med Windows PowerShell-arbetsflöde kan du anpassa och köra både PowerShell-skript och XAML-filer som arbets flöden. |
