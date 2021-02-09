---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 02/08/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSSession
ms.openlocfilehash: b1827929c53560cb261cd7b3ba1e5bd407c25700
ms.sourcegitcommit: 3a1d80e27438976101f216b8c3d623c61b868db8
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/09/2021
ms.locfileid: "99975098"
---
# Exit-PSSession

## Sammanfattning
Avslutar en interaktiv session med en fjärran sluten dator.

## SYNTAX

```
Exit-PSSession [<CommonParameters>]
```

## Description

`Exit-PSSession`Cmdleten avslutar interaktiva sessioner som du startade med `Enter-PSSession` cmdleten.

Du kan också använda `exit` nyckelordet för att avsluta en interaktiv session. Detta är detsamma som att använda `Exit-PSSession` .

## Exempel

### Exempel 1: starta och stoppa en interaktiv session

```powershell
PS> Enter-PSSession -ComputerName Server01
Server01\PS> Exit-PSSession
PS>
```

Kommandona startar och stoppar sedan en interaktiv session med Server01-fjärrdatorn.

### Exempel 2: starta och stoppa en interaktiv session med hjälp av ett PSSession-objekt

```powershell
PS> $s = New-PSSession -ComputerName Server01
PS> Enter-PSSession -Session $s
Server01\PS> Exit-PSSession
PS> $s
Id Name            ComputerName    State    ConfigurationName
-- ----            ------------    -----    -----------------
1  Session1        Server01        Opened   Microsoft.PowerShell
```

Kommandona startar och stoppar en interaktiv session med Server01-datorn som använder en PowerShell-session (**PSSession**).

Eftersom den interaktiva sessionen startades med hjälp av en PowerShell-session är **PSSession** fortfarande tillgängligt när den interaktiva sessionen avslutas. Om du använder parametern _computername_ `Enter-PSSession` skapas en tillfällig session som stängs när den interaktiva sessionen avslutas.

Det första kommandot använder `New-PSSession` cmdleten för att skapa en **PSSession** på Server01-datorn. Kommandot sparar **PSSession** i `$s` variabeln.

Det andra kommandot använder `Enter-PSSession` för att starta en interaktiv session med hjälp av **PSSession** i `$s` .

Det tredje kommandot använder `Exit-PSSession` för att stoppa den interaktiva sessionen.

Det sista kommandot visar **PSSession** i `$s` variabeln. Egenskapen **State** visar att **PSSession** fortfarande är öppen och tillgänglig för användning.

### Exempel 3: Använd nyckelordet Exit för att stoppa en session

```powershell
PS> Enter-PSSession -ComputerName Server01
Server01\PS> exit
PS>
```

I det här exemplet används `exit` nyckelordet för att stoppa en interaktiv session som har startats med hjälp av `Enter-PSSession` . `exit`Nyckelordet har samma resultat som när du använder `Exit-PSSession` .

## Parametrar

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## Indata

### Inget

Det går inte att skicka pipe-objekt till denna cmdlet.

## Utdata

### Inget

Denna cmdlet returnerar inga utdata.

## Kommentarer

Denna cmdlet tar bara med de gemensamma parametrarna.

## RELATERADE LÄNKAR

[Anslut – PSSession](Connect-PSSession.md)

[Koppla från-PSSession](Disconnect-PSSession.md)

[Retur-PSSession](Enter-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-kommando](Invoke-Command.md)

[New-PSSession](New-PSSession.md)

[Ta emot – PSSession](Receive-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)
