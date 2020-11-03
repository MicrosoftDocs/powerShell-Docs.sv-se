---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pssession?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSSession
ms.openlocfilehash: 4e0b79cae4af290c64f579217a3731aaac401d6d
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/02/2020
ms.locfileid: "93261563"
---
# Exit-PSSession

## SAMMANFATTNING
Avslutar en interaktiv session med en fjärran sluten dator.

## SYNTAX

```
Exit-PSSession [<CommonParameters>]
```

## BESKRIVNING

Cmdleten **exit-PSSession** avslutar interaktiva sessioner som du startade med hjälp av Enter-PSSession-cmdleten.

Du kan också använda nyckelordet **exit** för att avsluta en interaktiv session.
Resultatet är detsamma som att använda **exit-PSSession**.

## EXEMPEL

### Exempel 1: starta och stoppa en interaktiv session

```
PS> Enter-PSSession -computername Server01
Server01\PS> Exit-PSSession
PS>
```

Kommandona startar och stoppar sedan en interaktiv session med Server01-fjärrdatorn.

### Exempel 2: starta och stoppa en interaktiv session med hjälp av ett PSSession-objekt

```
PS> $s = New-PSSession -ComputerName Server01
PS> Enter-PSSession -Session $s
Server01\PS> Exit-PSSession
PS> $s
Id Name            ComputerName    State    ConfigurationName
-- ----            ------------    -----    -----------------
1  Session1        Server01        Opened   Microsoft.PowerShell
```

Kommandona startar och stoppar en interaktiv session med Server01-datorn som använder en PowerShell-session ( **PSSession** ).

Eftersom den interaktiva sessionen startades med hjälp av en PowerShell-session är **PSSession** fortfarande tillgängligt när den interaktiva sessionen avslutas.
Om du använder parametern *computername* kan du **Ange-PSSession** för att skapa en tillfällig session som stängs när den interaktiva sessionen avslutas.

Det första kommandot använder cmdleten New-PSSession för att skapa en **PSSession** på Server01-datorn.
Kommandot sparar **PSSession** i variabeln $s.

Det andra kommandot använder **RETUR-PSSession** för att starta en interaktiv session med hjälp av **PSSession** i $s.

Det tredje kommandot använder **exit-PSSession** för att stoppa den interaktiva sessionen.

Det sista kommandot visar **PSSession** i variabeln $s.
Egenskapen **State** visar att **PSSession** fortfarande är öppen och tillgänglig för användning.

### Exempel 3: Använd nyckelordet Exit för att stoppa en session

```
PS> Enter-PSSession -computername Server01
Server01\PS> exit
PS>
```

I det här exemplet används nyckelordet **exit** för att stoppa en interaktiv session som har startats med hjälp av **Enter-PSSession**.
Nyckelordet **exit** har samma resultat som när du använder **exit-PSSession**.

## PARAMETRAR

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Det går inte att skicka pipe-objekt till denna cmdlet.

## UTDATA

### Inget

Denna cmdlet returnerar inga utdata.

## ANTECKNINGAR

* Denna cmdlet tar bara med de gemensamma parametrarna.

*

## RELATERADE LÄNKAR

[Anslut – PSSession](Connect-PSSession.md)

[Koppla från-PSSession](Disconnect-PSSession.md)

[Retur-PSSession](Enter-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-kommando](Invoke-Command.md)

[New-PSSession](New-PSSession.md)

[Ta emot – PSSession](Receive-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)
