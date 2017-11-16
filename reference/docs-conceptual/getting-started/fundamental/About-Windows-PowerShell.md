---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Om Windows PowerShell
ms.assetid: 979654ae-7994-47f8-be43-d79e7a140143
ms.openlocfilehash: 5e6d1bb4d8915ba3c83ba0020b959e444b5211cd
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2017
---
# <a name="about-windows-powershell"></a>Om Windows PowerShell
Windows PowerShell är utformade för att förbättra kommandoradsverktyg och skript miljö genom att sedan problem och lägga till nya funktioner.

## <a name="discoverability"></a>Synlighet
Windows PowerShell gör det lätt att identifiera dess funktioner. Du hittar en lista över cmdlets som Visa och ändra Windows-tjänster, exempelvis:

```
Get-Command *-Service
```

Efter att identifiera vilka cmdlet uppnår en aktivitet läsa du mer om cmdlet med hjälp av cmdleten Get-Help. Till exempel för att visa hjälp om cmdlet Get-Service, skriver du:

```
Get-Help Get-Service
```
De flesta cmdlets genererar objekt som kan ändras och sedan återges i text som ska visas. För att förstå resultatet av denna cmdlet, pipe-utdata för cmdleten Get-medlem. Följande kommando visar information om medlemmarna i objektutdata av cmdleten Get-Service.

```
Get-Service | Get-Member
```

## <a name="consistency"></a>Konsekvens
Hantera system kan vara en komplex åtagande och verktyg som har ett konsekvent gränssnitt som hjälper för att styra inbyggd komplexitet. Varken kommandoradsverktyg eller skriptbara COM-objekt har tyvärr rapporterats för sina konsekvent.

Konsekvenskontroll av Windows PowerShell är en av dess primära tillgångar. Om du lär dig hur du använder Sort-Object cmdlet använda du den kunskapen för att sortera utdata från varje cmdlet. Du har inte Läs olika sortering rutiner för varje cmdlet.

Dessutom har inte cmdlet utvecklare att utforma sorterings-funktioner för deras cmdlets. Windows PowerShell ger dem ett ramverk som tillhandahåller grundläggande funktioner och tvingar dem att vara konsekvent många aspekter av gränssnittet. Ramen eliminerar några av de alternativ som vanligtvis kvar att utvecklaren, men i RETUR gör det utvecklingen av robust och enkla att använda cmdlets mycket enklare.

## <a name="interactive-and-scripting-environments"></a>Interaktiva och Scripting miljöer
Windows PowerShell är en kombinerad miljö interaktiva och skript som ger dig tillgång till kommandoradsverktyg och COM-objekt och också kan du använda power av .NET Framework Class Library (FCL).

Den här miljön förbättrar vid Windows kommandotolk, vilket ger en interaktiv miljö med flera kommandoradsverktyg. Förbättrar också på Windows Script Host (WSH) skript, vilket gör att du kan använda flera kommandoradsverktyg och COM automation-objekt, men inte ger en interaktiv miljö.

Windows PowerShell genom att kombinera åtkomst till alla dessa funktioner, utökar möjligheten för en interaktiv användare och skript skrivaren och gör systemadministration mer användarvänlig.

## <a name="object-orientation"></a>Objektorientering
Även om du interagerar med Windows PowerShell genom att skriva kommandon i texten är Windows PowerShell baserad på objekt, inte text. Utdata från ett kommando är ett objekt. Du kan skicka utdata-objekt till ett annat kommando som indata. Windows PowerShell innehåller därför välbekanta gränssnittet till personer som har erfarenhet av andra tankar när introduktion till en ny och kraftfull kommandoradsverktyget paradigmet. Det utökar begreppet skicka data mellan kommandon genom att skicka objekt i stället för text.

## <a name="easy-transition-to-scripting"></a>Lätt att skript
Windows PowerShell gör det enkelt att övergången från att skriva kommandon interaktivt till skapa och köra skript. Du kan skriva kommandon i Kommandotolken för Windows PowerShell att identifiera de kommandon som kan utför en uppgift. Sedan kan du spara dessa kommandon i ett betyg eller en historik innan du kopierar dem till en fil för användning som ett skript.

