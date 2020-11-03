---
description: Förklarar hur du använder lokala och fjärrvariabler i fjärrkommandon.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_variables?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Variables
ms.openlocfilehash: 813b961d6e59dd85e09a461f8b5743924fecc673
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270459"
---
# <a name="about-remote-variables"></a>Om fjärrvariabler

## <a name="short-description"></a>Kort beskrivning

Förklarar hur du använder lokala och fjärrvariabler i fjärrkommandon.

## <a name="long-description"></a>Lång beskrivning

Du kan använda variabler i kommandon som du kör på fjärrdatorer. Tilldela ett värde till variabeln och Använd sedan variabeln i stället för värdet.

Som standard antas variablerna i fjärrkommandona att definieras i sessionen som kör kommandot. Variabler som definieras i en lokal session måste identifieras som lokala variabler i kommandot.

## <a name="using-remote-variables"></a>Använda fjärrvariabler

PowerShell förutsätter att variablerna som används i fjärrkommandon definieras i sessionen där kommandot körs.

I det här exemplet `$ps` definieras variabeln i den tillfälliga sessionen där `Get-WinEvent` kommandot körs.

```powershell
Invoke-Command -ComputerName S1 -ScriptBlock {
  $ps = "*PowerShell*"; Get-WinEvent -LogName $ps
}
```

När kommandot körs i en beständig session, **PSSession** , måste fjärrvariabeln definieras i den sessionen.

```powershell
$s = New-PSSession -ComputerName S1
Invoke-Command -Session $s -ScriptBlock {$ps = "*PowerShell*"}
Invoke-Command -Session $s -ScriptBlock {Get-WinEvent -LogName $ps}
```

## <a name="using-local-variables"></a>Använda lokala variabler

Du kan använda lokala variabler i fjärrkommandon, men variabeln måste definieras i den lokala sessionen.

Från och med PowerShell 3,0 kan du använda `Using` omfångs modifieraren för att identifiera en lokal variabel i ett fjärran slutet kommando.

Syntaxen för `Using` är följande:

```
$Using:<VariableName>
```

I följande exempel `$ps` skapas variabeln i den lokala sessionen, men används i den session där kommandot körs. `Using`Omfångs modifieraren identifieras `$ps` som en lokal variabel.

```powershell
$ps = "*PowerShell*"
Invoke-Command -ComputerName S1 -ScriptBlock {
  Get-WinEvent -LogName $Using:ps
}
```

`Using`Omfångs modifieraren kan användas i en **PSSession**.

```powershell
$s = New-PSSession -ComputerName S1
$ps = "*PowerShell*"
Invoke-Command -Session $s -ScriptBlock {Get-WinEvent -LogName $Using:ps}
```

En variabel referens, till exempel `$using:var` expanderar värdet variabeln `$var` från anroparens kontext. Du får inte åtkomst till anroparens variabel objekt.
`Using`Omfångs modifieraren kan inte användas för att ändra en lokal variabel i **PSSession**. Följande kod fungerar exempelvis inte:

```powershell
$s = New-PSSession -ComputerName S1
$ps = "*PowerShell*"
Invoke-Command -Session $s -ScriptBlock {$Using:ps = 'Cannot assign new value'}
```

Mer information om `Using` finns i [about_Scopes](./about_Scopes.md)

### <a name="using-splatting"></a>Använda ihopbuntning

PowerShell-ihopbuntning skickar en samling parameter namn och värden till ett kommando. Mer information finns i [about_Splatting](about_Splatting.md).

I det här exemplet är ihopbuntning-variabeln `$Splat` en hash-tabell som har kon figurer ATS på den lokala datorn. `Invoke-Command`Ansluter till en fjärrdator-session. **Script block** använder `Using` omfångs modifieraren med symbolen at ( `@` ) för att representera splatted-variabeln.

```powershell
$Splat = @{ Name = "Win*"; Include = "WinRM" }
Invoke-Command -Session $s -ScriptBlock { Get-Service @Using:Splat }
```

### <a name="other-situations-where-the-using-scope-modifier-is-needed"></a>Andra situationer där omfångs modifieraren "använder" krävs

För alla skript eller kommandon som körs utanför sessionen behöver du `Using` omfångs modifieraren för att bädda in variabel värden från scopet för den anropande sessionen, så att det går att komma åt dem. `Using`Omfångs modifieraren stöds i följande kontexter:

- Fjärrkörning av kommandon, startade med `Invoke-Command` användning **av ComputerName** , **hostname** , **SSHConnection** eller **sessionstillstånd** (fjärrsession)
- Bakgrunds jobb, startade med `Start-Job` (out-of-process-session)
- Tråd jobb som startades via `Start-ThreadJob` (separat trådad session)

Beroende på sammanhanget är inbäddade variabel värden antingen oberoende kopior av data i anroparens omfång eller referenser till den. I fjärranslutna och inaktiva sessioner är de alltid oberoende kopior. De skickas som referens i Thread-sessioner.

## <a name="serialization-of-variable-values"></a>Serialisering av variabel värden

Fjärrkörning av kommandon och bakgrunds jobb körs utanför processen.
Sessioner utanför processen använder XML-baserad serialisering och deserialisering för att göra värdena för variabler tillgängliga över process gränserna. Serialiserings processen konverterar objekt till en **PSObject** som innehåller de ursprungliga objekt egenskaperna, men inte dess metoder.

För en begränsad uppsättning typer, deserialiserar objekt tillbaka till den ursprungliga typen. Det dehydratiserade objektet är en kopia av den ursprungliga objekt instansen.
Den har typ egenskaper och metoder. För enkla typer, till exempel **system. version** , är kopian exakt. För komplexa typer är kopian perfekt. Till exempel innehåller inte rehydratiserade certifikat objekt den privata nyckeln.

Instanser av alla andra typer är **PSObject** -instanser. Egenskapen **PSTypeNames** innehåller det ursprungliga typ namnet som föregås av **deserialiserad** , till exempel **Deserialized.System. Data. DataTable**

## <a name="using-local-variables-with-argumentlist-parameter"></a>Använda lokala variabler med **argument List** -parametern

Du kan använda lokala variabler i ett fjärran slutet kommando genom att definiera parametrar för fjärrkommandot och använda parametern **argument List** för `Invoke-Command` cmdleten för att ange den lokala variabeln som parametervärdet.

- Använd `param` nyckelordet för att definiera parametrar för fjärrkommandot. Parameter namnen är plats hållare som inte behöver matcha den lokala variabelns namn.

- Använd de parametrar som definieras av `param` nyckelordet i kommandot.

- Använd parametern **argument List** för `Invoke-Command` cmdleten för att ange den lokala variabeln som parameter värde.

Följande kommandon definierar till exempel `$ps` variabeln i den lokala sessionen och använder den sedan i ett fjärrkommando. Kommandot använder `$log` som parameter namn och den lokala variabeln, `$ps` som värde.

```powershell
$ps = "*PowerShell*"
Invoke-Command -ComputerName S1 -ScriptBlock {
  param($log)
  Get-WinEvent -LogName $log
} -ArgumentList $ps
```

## <a name="see-also"></a>Se även

[about_PSSessions](about_PSSessions.md)

[about_Remote](about_Remote.md)

[about_Scopes](about_Scopes.md)

[about_Splatting](about_Splatting.md)

[about_Variables](about_Variables.md)

[Retur-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[Invoke-kommando](xref:Microsoft.PowerShell.Core.Invoke-Command)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[Start-ThreadJob](xref:ThreadJob.Start-ThreadJob)
