---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 11/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pshostprocess?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSHostProcess
ms.openlocfilehash: 1734758d34e89020f579fffa217cef58eb222736
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344056"
---
# Exit-PSHostProcess

## SAMMANFATTNING
Stänger en interaktiv session med en lokal process.

## SYNTAX

```
Exit-PSHostProcess [<CommonParameters>]
```

## BESKRIVNING

`Exit-PSHostProcess`Cmdleten stänger en interaktiv session med en lokal process som du har öppnat genom att köra `Enter-PSHostProcess` cmdleten. Du kör `Exit-PSHostProcess` cmdleten inifrån processen när du är färdig med fel sökningen eller fel sökning av ett skript som körs i en process. Från och med PowerShell 6,2 stöds denna cmdlet på plattformar som inte är Windows-plattformar.

## EXEMPEL

### Exempel 1: avsluta en process

```
[Process:1520]: PS>  Exit-PSHostProcess
PS>
```

I det här exemplet har du arbetat i en aktiv process för att felsöka ett skript som körs i en körnings utrymme i processen, enligt beskrivningen i `Enter-PSHostProcess` . När du har angett `exit` kommandot för att avsluta fel söknings programmet, kör du `Exit-PSHostProcess` cmdleten för att stänga den interaktiva sessionen med processen.
Cmdleten stänger sessionen i processen och återgår till `PS C:\>` prompten.

## PARAMETRAR

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

## UTDATA

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Retur-PSHostProcess](Enter-PSHostProcess.md)
