---
ms.date: 08/27/2018
keywords: PowerShell, cmdlet
title: Få information om kommandon
ms.openlocfilehash: eb918c6f89d8369db775258263a8f7a7902a6cc7
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030941"
---
# <a name="getting-information-about-commands"></a>Få information om kommandon

PowerShell `Get-Command` visar kommandon som är tillgängliga i den aktuella sessionen.
När du kör `Get-Command` cmdleten ser du något som liknar följande utdata:

```output
CommandType     Name                    Version    Source
-----------     ----                    -------    ------
Cmdlet          Add-Computer            3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-Content             3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-History             3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-JobTrigger          1.1.0.0    PSScheduledJob
Cmdlet          Add-LocalGroupMember    1.0.0.0    Microsoft.PowerShell.LocalAccounts
Cmdlet          Add-Member              3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Add-PSSnapin            3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-Type                3.1.0.0    Microsoft.PowerShell.Utility
...
```

Det här resultatet ser ut ungefär som hjälp resultatet av **cmd. exe**: en tabell Sammanfattning av interna kommandon. I utdraget av `Get-Command` kommandoutdata som visas ovan har alla kommandon som visas en cmdlet. En cmdlet är PowerShell: s inbyggda kommando typ. Den här typen motsvarar ungefär samma som för `dir` kommandon `cd` som och i **cmd. exe** eller inbyggda kommandon i UNIX-gränssnitt som bash.

`Get-Command` Cmdleten har en **syntax** -parameter som returnerar syntaxen för varje cmdlet. I följande exempel visas hur du hämtar syntaxen för `Get-Help` cmdleten:

```powershell
Get-Command Get-Help -Syntax
```

```output
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

## <a name="displaying-available-command-by-type"></a>Visar tillgängligt kommando efter typ

`Get-Command` Kommandot visar bara cmdletarna i den aktuella sessionen. PowerShell stöder faktiskt flera andra typer av kommandon:

- Alias
- Functions
- Skript

Externa körbara filer eller filer som har en registrerad fil typs hanterare klassificeras också som kommandon.

Om du vill hämta alla kommandon i sessionen skriver du:

```powershell
Get-Command *
```

Den här listan innehåller externa kommandon i din Sök väg så att den kan innehålla tusentals objekt.
Det är mer användbart att titta på en reducerad uppsättning kommandon.

> [!NOTE]
> Asterisken (\*) används för matchning av jokertecken i PowerShell-kommandon. Betyder \* att "matcha ett eller flera tecken". Du kan skriva `Get-Command a*` för att hitta alla kommandon som börjar med bokstaven "a". Till skillnad från matchning av jokertecken i **cmd. exe**kommer PowerShell-jokertecknet också att matcha en punkt.

Använd parametern **CommandType** för `Get-Command` för att hämta interna kommandon av andra typer.
kommandon.

Om du vill hämta kommando Ali Aset, som är tilldelade smek namn för kommandon, skriver du:

```powershell
Get-Command -CommandType Alias
```

Om du vill hämta funktionerna i den aktuella sessionen skriver du:

```powershell
Get-Command -CommandType Function
```

Om du vill visa skript i PowerShell: s Sök väg skriver du:

```powershell
Get-Command -CommandType Script
```
