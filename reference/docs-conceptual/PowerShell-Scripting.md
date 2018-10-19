---
ms.date: 08/27/2018
keywords: PowerShell cmdlet
title: PowerShell-skript
ms.openlocfilehash: 07925ce8dcafd33970a703c9b241bf6f76f88d10
ms.sourcegitcommit: 47becf2823ece251a7264db2387bb503cf3abaa9
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/19/2018
ms.locfileid: "49451038"
---
# <a name="powershell"></a>PowerShell

PowerShell är ett uppgiftsbaserat kommandoradsgränssnitt och skriptspråk som bygger på .NET.
PowerShell hjälper administratörer och Privilegierade användare automatisera snabbt uppgifter som hanterar operativsystem (Linux, macOS och Windows) och processer.

PowerShell-kommandon kan du hantera datorer från kommandoraden. PowerShell-providers kan du få åtkomst till datalager, till exempel registret och certifikatarkivet, lika enkelt som du har åtkomst till filsystemet. PowerShell innehåller en omfattande uttrycksparser och ett fullständigt utvecklat skriptspråk.

## <a name="powershell-is-open-source"></a>PowerShell är öppen källkod

PowerShell grundläggande källkoden är nu tillgängligt i GitHub och öppna community-bidrag.
Se [PowerShell källkod på GitHub](https://github.com/powershell/powershell).

Du kan börja med bits på [hämta PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).
Eller kanske, med en snabb genomgång på [komma igång](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).

## <a name="powershell-design-goals"></a>PowerShell-designmålen

PowerShell har utformats för att förbättra miljön kommandorad och skript genom att långsiktigt problem och lägga till nya funktioner.

### <a name="discoverability"></a>För att göra

PowerShell gör det enkelt att identifiera dess funktioner. Till exempel för att hitta en lista över cmdlets som Visa och ändra Windows-tjänster, skriver du:

```powershell
Get-Command *-Service
```

Efter identifiering av vilka cmdlet uppnår en uppgift, kan du läsa mer om cmdlet: en med hjälp av den `Get-Help` cmdlet. Till exempel vill visa hjälp om den `Get-Service` cmdlet, typ:

```powershell
Get-Help Get-Service
```

De flesta cmdletar returnerar objekt som kan ändras och sedan renderas som text som ska visas. För att helt förstå resultatet av en cmdlet, skicka utdata till den `Get-Member` cmdlet. Till exempel följande kommando visar information om medlemmarna i objektutdata av den `Get-Service` cmdlet.

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a>Konsekvens

Hantera system kan vara en komplicerad uppgift. Verktyg som har ett konsekvent gränssnitt hjälpa till att styra den inbyggda komplexiteten. Tyvärr är inte kommandoradsverktyg och skriptbara COM-objekt känt för sin konsekvens.

Konsekvenskontroll av PowerShell är en av dess primära tillgångar. Exempel: Om du lära dig hur du använder den `Sort-Object` cmdlet, du kan använda denna kunskap för att ordna resultatet av en cmdlet. Du behöver att lära dig de olika sortering rutinerna för varje cmdlet.

Dessutom inte cmdlet-utvecklare att utforma sortering funktioner för deras cmdlets. PowerShell ger ett ramverk med grundläggande funktioner som tvingar konsekvens. Ramverket eliminerar vissa alternativ som är kvar att utvecklaren. Men, i utbyte kan det gör utvecklingen av cmdlet: ar mycket enklare.

### <a name="interactive-and-scripting-environments"></a>Interaktiva och skript miljöer

Windows-kommandotolk innehåller ett interaktivt gränssnitt med åtkomst till kommandoradsverktyg och basic-skript. Windows Script Host (WSH) har skriptbara kommandoradsverktyg och COM automation-objekt, men tillhandahåller inte ett interaktivt gränssnitt.

PowerShell kombinerar ett interaktivt gränssnitt och en skriptmiljö. PowerShell kan komma åt kommandoradsverktyg, COM-objekt och .NET-klassbibliotek. Kombinationen av funktioner utökar funktionerna i den interaktiva användaren skrivar-skript och systemadministratören.

### <a name="object-orientation"></a>Objektorientering

PowerShell är baserad på objekt inte text. Utdata från ett kommando är ett objekt. Du kan skicka objektet, genom pipelinen och till ett annat kommando som indata.

Denna pipeline finns det ett välbekanta gränssnitt för personer med andra gränssnitt. PowerShell utvidgar detta begrepp genom att skicka objekt i stället för text.

### <a name="easy-transition-to-scripting"></a>Lätt att skript

PowerShell-kommando för att göra blir det enkelt att övergången från att skriva in kommandon interaktivt till skapa och köra skript. PowerShell betyg och historik gör det enkelt att kopiera kommandon till en fil för användning som ett skript.
