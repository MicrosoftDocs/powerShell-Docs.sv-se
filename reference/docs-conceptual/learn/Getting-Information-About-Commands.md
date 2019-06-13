---
ms.date: 08/27/2018
keywords: PowerShell cmdlet
title: Få information om kommandon
ms.openlocfilehash: eb918c6f89d8369db775258263a8f7a7902a6cc7
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030941"
---
# <a name="getting-information-about-commands"></a>Få information om kommandon

PowerShell `Get-Command` visar kommandon som är tillgängliga i den aktuella sessionen.
När du kör den `Get-Command` cmdlet, visas något som liknar följande utdata:

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

Detta utdata ser ut precis som utdata för hjälp av **cmd.exe**: en tabular sammanfattning av interna kommandon. I utdrag ur den `Get-Command` kommandot utdata som visas ovan, alla kommandon som visas har en CommandType Cmdlet. En cmdlet är PowerShell-inbäddade kommandotypen. Den här typen motsvarar ungefär kommandon som `dir` och `cd` i **cmd.exe** eller inbyggda kommandon på Unix-gränssnitt som bash.

Den `Get-Command` cmdlet har en **Syntax** parameter som returnerar syntaxen för varje cmdlet. I följande exempel visas hur du hämtar syntaxen för den `Get-Help` cmdlet:

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

## <a name="displaying-available-command-by-type"></a>Visar kommandon som är tillgängliga efter typ

Den `Get-Command` kommandot visar bara cmdletarna i den aktuella sessionen. PowerShell stöder faktiskt flera andra typer av kommandon:

- Alias
- Funktioner
- Skript

Externa körbara filer eller filer som har en registrerad typ hanterare också klassificeras som kommandon.

Om du vill hämta alla kommandon i sessionen, skriver du:

```powershell
Get-Command *
```

Den här listan innehåller externa kommandon i sökvägen så att den kan innehålla tusentals objekt.
Det är mer användbart att titta på en reducerad uppsättning kommandon.

> [!NOTE]
> Asterisken (\*) används för matchning i PowerShell kommandoargumenten med jokertecken. Den \* ”matchar en eller flera tecken”. Du kan skriva `Get-Command a*` att hitta alla kommandon som börjar med bokstaven ”a”. Till skillnad från matchning med jokertecken i **cmd.exe**, PowerShell-jokertecken också matchar en punkt.

Använd den **CommandType** -parametern för `Get-Command` att hämta inbyggda kommandon av andra typer.
cmdlet.

Om du vill ha kommando-alias som är tilldelade smeknamn kommandon, skriver du:

```powershell
Get-Command -CommandType Alias
```

För att få funktionerna i den aktuella sessionen, skriver du:

```powershell
Get-Command -CommandType Function
```

Om du vill visa skript i PowerShell-sökvägen, skriver du:

```powershell
Get-Command -CommandType Script
```
