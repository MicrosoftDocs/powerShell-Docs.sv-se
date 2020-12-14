---
description: Beskriver PowerShell-sessioner (PSSessions) och förklarar hur du upprättar en permanent anslutning till en fjärrdator.
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssessions?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSSessions
ms.openlocfilehash: edc7109f3f79376ac1d348d3c3cd65e3a8d3e69c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708471"
---
# <a name="about-pssessions"></a>Om PSSessions

## <a name="short-description"></a>Kort beskrivning
Beskriver PowerShell-sessioner (PSSessions) och förklarar hur du upprättar en permanent anslutning till en fjärrdator.

## <a name="long-description"></a>Lång beskrivning

Om du vill köra PowerShell-kommandon på en fjärrdator kan du använda parametern **computername** för en cmdlet, eller så kan du skapa en PowerShell-session (PSSession) och köra kommandon i PSSession.

När du skapar en PSSession upprättar PowerShell en permanent anslutning till fjärrdatorn. Använd en PSSession för att köra en serie relaterade kommandon på en fjärrdator. Kommandon som körs i samma PSSession kan dela data, till exempel värden för variabler, alias och funktioner.

Du kan också skapa en PSSession på den lokala datorn och köra kommandon i den.
En lokal PSSession använder PowerShell-infrastrukturen för fjärr kommunikation för att skapa och underhålla PSSession.

Från och med Windows PowerShell 3,0 är PSSessions oberoende av de sessioner som de skapas i. Aktiva PSSessions underhålls på fjärrdatorn (eller datorn på fjärrplatsen eller "Server sidan" i anslutningen). Därför kan du koppla från PSSession och återansluta till den vid ett senare tillfälle från samma dator eller från en annan dator.

I det här avsnittet beskrivs hur du skapar, använder, hämtar och tar bort PSSessions. Mer avancerad information finns i [about_PSSession_Details](about_PSSession_Details.md).

Obs: PSSessions använder PowerShell-fjärrinfrastrukturen. För att kunna använda PSSessions måste lokala och fjärranslutna datorer konfigureras för fjärr kommunikation.
Mer information finns i [about_Remote_Requirements](about_Remote_Requirements.md).

I Windows Vista och senare versioner av Windows måste du starta PowerShell med alternativet "kör som administratör" för att kunna skapa en PSSession på en lokal dator.

## <a name="what-is-a-session"></a>Vad är en session?

En session är en miljö där PowerShell körs.

Varje gången du startar PowerShell skapas en session åt dig, och du kan köra kommandon i sessionen. Du kan också lägga till objekt i din session, till exempel moduler och snapin-moduler, och du kan skapa objekt, till exempel variabler, funktioner och alias. Dessa objekt finns bara i sessionen och tas bort när sessionen avslutas.

Du kan också skapa användar hanterade sessioner som kallas "PowerShell-sessioner" eller "PSSessions" på den lokala datorn eller på en fjärrdator. Precis som Standardsessionen kan du köra kommandon i en PSSession och lägga till och skapa objekt. Men till skillnad från den session som startar automatiskt kan du kontrol lera de PSSessions som du skapar. Du kan hämta, skapa, konfigurera och ta bort dem, koppla från och återansluta till dem och köra flera kommandon i samma PSSession. PSSession förblir tillgänglig tills du tar bort den eller tids gränsen uppnåddes.

Normalt skapar du en PSSession för att köra en serie relaterade kommandon på en fjärrdator. När du skapar en PSSession på en fjärrdator upprättar PowerShell en permanent anslutning till fjärrdatorn för att stödja sessionen.

Om du använder parametern **computername** för `Invoke-Command` `Enter-PSSession` cmdleten eller för att köra ett fjärrkommando, eller om du vill starta en interaktiv session, skapar PowerShell en tillfällig session på fjärrdatorn och stänger sessionen så snart kommandot är slutfört eller så snart den interaktiva sessionen avslutas. Du kan inte kontrol lera dessa tillfälliga sessioner och du kan inte använda dem för mer än ett enda kommando eller en enkel interaktiv session.

I PowerShell är den aktuella sessionen den session som du arbetar i. Den aktuella sessionen kan referera till en session, inklusive en tillfällig session eller en PSSession.

## <a name="why-use-a-pssession"></a>Varför ska jag använda en PSSession?

Använd en PSSession när du behöver en permanent anslutning till en fjärrdator.
Med en PSSession kan du köra en serie kommandon som delar data, till exempel värdet för variabler, innehållet i en funktion eller definitionen av ett alias.

Du kan köra fjärrkommandon utan att skapa en PSSession. Använd parametern **computername** för fjärraktiverade cmdlet: ar för att köra ett enskilt kommando eller en serie orelaterade kommandon på en eller flera datorer.

När du använder parametern **computername** för `Invoke-Command` eller `Enter-PSSession` , upprättar PowerShell en tillfällig anslutning till fjärrdatorn och stänger sedan anslutningen så snart kommandot har slutförts. Alla data element som du skapar försvinner när anslutningen stängs.

Andra cmdletar som har en **computername** -parameter, till exempel `Get-Eventlog` och `Get-WmiObject` , använder olika fjärr kommunikations tekniker för att samla in data. Ingen skapar en permanent anslutning som en PSSession.

## <a name="how-to-create-a-pssession"></a>Så här skapar du en PSSession

Använd cmdleten för att skapa en PSSession `New-PSSession` . Om du vill skapa PSSession på en fjärrdator använder du parametern **computername** för `New-PSSession` cmdleten.

Följande kommando skapar till exempel en ny PSSession på Server01-datorn.

```powershell
New-PSSession -ComputerName Server01
```

När du skickar kommandot `New-PSSession` skapar PSSession och returnerar ett objekt som representerar PSSession. Du kan spara objektet i en variabel när du skapar PSSession, eller så kan du använda ett `Get-PSSession` kommando för att hämta PSSession vid ett senare tillfälle.

Följande kommando skapar till exempel en ny PSSession på Server01-datorn och sparar det resulterande objektet i variabeln $ps.

```powershell
$ps = New-PSSession -ComputerName Server01
```

## <a name="how-to-create-pssessions-on-multiple-computers"></a>Så här skapar du PSSessions på flera datorer

Om du vill skapa PSSessions på flera datorer använder du parametern **computername** för `New-PSSession` cmdleten. Ange namnen på fjärrdatorerna i en kommaavgränsad lista.

Om du till exempel vill skapa PSSessions på Server01-, Server02-och Server03-datorerna skriver du:

```powershell
New-PSSession -ComputerName Server01, Server02, Server03
```

`New-PSSession` skapar en PSSession på varje fjärran sluten dator.

## <a name="how-to-get-pssessions"></a>Så här hämtar du PSSessions

Om du vill hämta PSSessions som har skapats i den aktuella sessionen använder du `Get-PSSession` cmdleten utan parametern **computername** . `Get-PSSession` returnerar samma typ av objekt som `New-PSSession` returneras.

Följande kommando hämtar alla PSSessions som skapades i den aktuella sessionen.

```powershell
Get-PSSession
```

Standard visningen av PSSessions visar deras ID och standard visnings namn. Du kan tilldela ett alternativt visnings namn när du skapar sessionen.

```output
Id   Name       ComputerName    State    ConfigurationName
---  ----       ------------    -----    ---------------------
1    Session1   Server01        Opened   Microsoft.PowerShell
2    Session2   Server02        Opened   Microsoft.PowerShell
3    Session3   Server03        Opened   Microsoft.PowerShell
```

Du kan också spara PSSessions i en variabel. Följande kommando hämtar PSSessions och sparar dem i \$ ps123-variabeln.

```powershell
$ps123 = Get-PSSession
```

När du använder PSSession-cmdlet: arna kan du referera till en PSSession med hjälp av dess ID, efter dess namn eller med dess instans-ID (GUID). Följande kommando hämtar ett PSSession efter dess ID och sparar det i ps01- \$ variabeln.

```powershell
$ps01 = Get-PSSession -Id 1
```

Från och med Windows PowerShell 3,0 underhålls PSSessions på fjärrdatorn. Om du vill hämta PSSessions som du har skapat på vissa fjärrdatorer använder du parametern **computername** för `Get-PSSession` cmdleten. Följande kommando hämtar PSSessions som du skapade på Server01-fjärrdatorn. Detta inkluderar PSSessions som skapats i den aktuella sessionen och i andra sessioner på den lokala datorn eller andra datorer.

```powershell
Get-PSSession -ComputerName Server01
```

I Windows PowerShell 2,0 `Get-PSSession` hämtar endast de PSSessions som skapades i den aktuella sessionen. Den hämtar inte PSSessions som har skapats i andra sessioner eller på andra datorer, även om sessionerna är anslutna till och kör kommandon på den lokala datorn.

## <a name="how-to-run-commands-in-a-pssession"></a>Köra kommandon i en PSSession

Använd cmdleten om du vill köra ett kommando i en eller flera PSSessions `Invoke-Command` .
Använd parametern session för att ange PSSessions och parametern **script block** för att ange kommandot.

Om du till exempel vill köra ett `Get-ChildItem` kommando ("dir") i vart och ett av de tre PSSessions som sparas i variabeln $ps 123, skriver du:

```powershell
Invoke-Command -Session $ps123 -ScriptBlock { Get-ChildItem }
```

## <a name="how-to-delete-pssessions"></a>Ta bort PSSessions

När du är färdig med PSSession använder du `Remove-PSSession` cmdleten för att ta bort PSSession och för att frigöra de resurser som används.

```powershell
Remove-PSSession -Session $ps
```

eller

```powershell
Remove-PSSession -Id 1
```

Om du vill ta bort en PSSession från en fjärrdator använder du parametern **computername** för `Remove-PSSession` cmdleten.

```powershell
Remove-PSSession -ComputerName Server01 -Id 1
```

Om du inte tar bort PSSession är PSSession fortfarande tillgängligt för användning tills tids gränsen uppnåddes.

Du kan också använda **idleTimeout** -parametern för `New-PSSessionOption` cmdlet: en för att ange en förfallo tid för en inaktiv PSSession. Mer information finns i [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).

## <a name="the-pssession-cmdlets"></a>PSSession-cmdletar

Om du vill ha en lista över PSSession-cmdletar skriver du:

```powershell
Get-Help *-PSSession
```

- Connect-PSSession: ansluter en PSSession till den aktuella sessionen
- Koppla från-PSSession: kopplar från en PSSession från den aktuella sessionen
- Retur-PSSession: startar en interaktiv session
- Exit-PSSession: avslutar en interaktiv session
- Get-PSSession: hämtar PSSessions i den aktuella sessionen
- New-PSSession: skapar en ny PSSession på en lokal eller fjärran sluten dator
- Receive-PSSession: hämtar resultatet från kommandon som kördes i en frånkopplad session
- Remove-PSSession: tar bort PSSessions i den aktuella sessionen

## <a name="for-more-information"></a>Mer information

Mer information om PSSessions finns i [about_PSSession_Details](about_PSSession_Details.md).

## <a name="see-also"></a>Se även

[about_Remote](about_Remote.md)

[about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md)

[about_Remote_Requirements](about_Remote_Requirements.md)

[Anslut – PSSession](xref:Microsoft.PowerShell.Core.Connect-PSSession)

[Koppla från-PSSession](xref:Microsoft.PowerShell.Core.Disconnect-PSSession)

[Retur-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[Avsluta-PSSession](xref:Microsoft.PowerShell.Core.Exit-PSSession)

[Get-PSSession](xref:Microsoft.PowerShell.Core.Get-PSSession)

[Invoke-kommando](xref:Microsoft.PowerShell.Core.Invoke-Command)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[Remove-PSSession](xref:Microsoft.PowerShell.Core.Remove-PSSession)

