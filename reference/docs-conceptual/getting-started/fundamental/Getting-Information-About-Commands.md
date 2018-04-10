---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Få information om kommandon
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
ms.openlocfilehash: 1426c171d74afc87751f7d31d46571b9c98fa47e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="getting-information-about-commands"></a>Få information om kommandon
Windows PowerShell **Get-Command** cmdlet hämtar alla kommandon som är tillgängliga i den aktuella sessionen. När du skriver **Get-Command** i Windows PowerShell-kommandotolken visas utdata som liknar följande:

```
PS> Get-Command
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
Cmdlet          Add-Member                      Add-Member [-MemberType] <PS...
...
```

Detta utdata mycket ser ut som hjälp utdata från Cmd.exe: en tabell sammanfattning av interna kommandon. I utdrag ur den **Get-Command** kommandot utdata visas alla kommandon som visas ovan, har en CommandType Cmdlet. En cmdlet är Windows PowerShell inre kommandotypen - en typ som motsvarar ungefär till den **dir** och **cd** kommandon cmd.exe och built-ins i UNIX-gränssnitt, till exempel BASH.

I utdata från den **Get-Command** kommandot alla definitioner avslutas med ellipserna (...) för att indikera att PowerShell inte kan visa allt innehåll i det tillgängliga utrymmet. När Windows PowerShell visar utdata, formaterar resultatet som text och ordnar det som gör att data korrekt passar i fönstret. Vi ska tala om det senare i avsnittet på formaterare.

Den **Get-Command** cmdlet har en **Syntax** parameter som hämtar syntaxen för varje cmdlet. För att få syntaxen för cmdleten Get-Help, använder du följande kommando:

**Get-kommandot Get-Help-Syntax**

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

### <a name="displaying-available-command-types"></a>Visa tillgängliga kommandon
Den **Get-Command** kommando inte innehåller alla kommandon som är tillgängliga i Windows PowerShell. I stället den **Get-Command** kommando visar bara cmdletarna i den aktuella sessionen. Windows PowerShell verkligen har stöd för flera typer av kommandon. Alias, funktioner och skript är också Windows PowerShell-kommandon, även om de inte beskrivs i detalj i Windows PowerShell användarhandboken. Externa filer som är körbara eller har en registrerad typ hanterare också klassificeras som kommandon.

Om du vill hämta alla kommandon i sessionen, skriver du:

```
Get-Command *
```

Eftersom den här listan innehåller de externa filerna i sökvägen, kan den innehålla tusentals objekt. Det är bättre att titta på en uppsättning kommandon.

Inbyggda kommandon av andra typer får använda den **CommandType** parameter för den **Get-Command** cmdlet.

> [!NOTE]
> En asterisk (\*) används för matchning i Windows PowerShell kommandoargumenten med jokertecken. Den \* ”matchar en eller flera tecken”. Du kan skriva **Get-Command en\&#42;** att hitta alla kommandon som börjar med bokstaven ”a”. Till skillnad från matchning med jokertecken i Cmd.exe, kommer Windows PowerShell med jokertecken också under en period.

Om du vill ha kommandot alias som är tilldelade smeknamn kommandon, skriver du:

```
Get-Command -CommandType Alias
```

För att få funktionerna i den aktuella sessionen, skriver du:

```
Get-Command -CommandType Function
```

Om du vill visa skript i Windows PowerShell-sökvägen, skriver du:

```
Get-Command -CommandType Script
```