---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: PowerShell-skript
ms.openlocfilehash: c6ba3abc2544834e2cbec16a524f79399a1d2599
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094059"
---
# <a name="powershell"></a>PowerShell

Bygger på .NET Framework och är PowerShell ett uppgiftsbaserat kommandoradsgränssnitt och skriptspråk; Det är utformat särskilt för administratörer och Privilegierade användare, att automatisera snabbt administrationen av flera operativsystem (Linux, macOS, Unix- och Windows) och processer som är relaterade till de program som körs på dessa operativsystem.

## <a name="powershell-is-open-source"></a>PowerShell är öppen källkod

PowerShell grundläggande källkoden är nu tillgängligt i GitHub och öppna community-bidrag.
Se [PowerShell källkod på GitHub](https://github.com/powershell/powershell).

Du kan börja med bits på [hämta PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).
Eller kanske, med en snabb genomgång på [komma igång](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)

## <a name="powershell-design-goals"></a>PowerShell-designmålen
PowerShell har utformats för att förbättra miljön kommandorad och skript genom att långsiktigt problem och lägga till nya funktioner.

### <a name="discoverability"></a>För att göra
PowerShell gör det enkelt att identifiera dess funktioner. Till exempel för att hitta en lista över cmdlets som Visa och ändra Windows-tjänster, skriver du:

```powershell
Get-Command *-Service
```

Efter identifiering av vilka cmdlet uppnår en uppgift, kan du läsa mer om cmdlet: en med hjälp av den `Get-Help` cmdlet.
Till exempel vill visa hjälp om den `Get-Service` cmdlet, typ:

```powershell
Get-Help Get-Service
```
De flesta cmdletar sända objekt som kan ändras och sedan återges i text som ska visas.
För att helt förstå utdata från denna cmdlet kan skicka utdata till den `Get-Member` cmdlet.
Till exempel följande kommando visar information om medlemmarna i objektutdata av den `Get-Service` cmdlet.

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a>Konsekvens
Hantera system kan vara en komplex åtagande och verktyg som har ett konsekvent gränssnitt bidra till att styra den inbyggda komplexiteten.
Varken kommandoradsverktyg eller skriptbara COM-objekt har tyvärr rapporterats för sina konsekvens.

Konsekvenskontroll av PowerShell är en av dess primära tillgångar.
Exempel: Om du lära dig hur du använder den `Sort-Object` cmdlet, du kan använda denna kunskap för att ordna resultatet av en cmdlet.
Du behöver inte lära dig de olika sortering rutinerna för varje cmdlet.

Dessutom behöver inte cmdlet-utvecklare utforma sortering funktioner för deras cmdlets.
PowerShell ger dem ett ramverk som tillhandahåller grundläggande funktioner och tvingar dem att vara konsekvent många aspekter av gränssnittet.
Ramverket eliminerar några av de alternativ som vanligtvis lämnas till utvecklaren, men i utbyte blir utvecklingen av robust och enkel att använda cmdlet: ar mycket enklare.

### <a name="interactive-and-scripting-environments"></a>Interaktiva och skript miljöer
PowerShell är en kombinerad interaktiva och skript som ger dig tillgång till kommandoradsverktyg och COM-objekt och även aktiverar du kan använda kraften i .NET Framework Class Library (FCL).

Den här miljön förbättrar vid Windows Kommandotolken, vilket ger en interaktiv miljö med flera kommandoradsverktyg.
Det förbättrar också vid skript för Windows Script Host (WSH), som gör att du använder flera kommandoradsverktyg och COM automation-objekt, men inte anger en interaktiv miljö.

Genom att kombinera åtkomst till alla dessa funktioner kan PowerShell utökar möjligheten för den interaktiva användaren och skrivar-skriptet och gör systemadministration mer hanterbara.

### <a name="object-orientation"></a>Objektorientering
Även om du interagerar med PowerShell genom att skriva kommandon i texten, är PowerShell baserad på objekt, inte text.
Utdata från ett kommando är ett objekt.
Du kan skicka objektet till ett annat kommando som indata.
Därför innehåller PowerShell en välbekanta gränssnittet till personer som har erfarenhet av andra gränssnitt, samtidigt som introducerar nya, kraftfulla kommandoradsverktyget paradigm.
Det är en utökad variant för att skicka data mellan kommandon genom att skicka objekt i stället för text.

### <a name="easy-transition-to-scripting"></a>Lätt att skript
PowerShell gör det enkelt att övergången från att skriva in kommandon interaktivt till skapa och köra skript.
Du kan skriva kommandon i Kommandotolken för PowerShell för att identifiera de kommandon som utför en uppgift.
Sedan kan du spara dessa kommandon i en avskrift eller en historik innan kopiera dem till en fil för användning som ett skript.
