---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pshostprocess?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSHostProcess
ms.openlocfilehash: 381d7d9cb32ed4682729ad304e82bb994a21190d
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/02/2020
ms.locfileid: "93261634"
---
# Exit-PSHostProcess

## SAMMANFATTNING
Stänger en interaktiv session med en lokal process.

## SYNTAX

```
Exit-PSHostProcess [<CommonParameters>]
```

## BESKRIVNING

Cmdleten **exit-PSHostProcess** stänger en interaktiv session med en lokal process som du har öppnat genom att köra cmdleten Enter-PSHostProcess. Du kör cmdleten **exit-PSHostProcess** inifrån processen när du är färdig med fel sökning eller fel sökning av skript som körs i en process.

## EXEMPEL

### Exempel 1: avsluta en process

```
[Process:1520]: PS>  Exit-PSHostProcess
PS>
```

I det här exemplet har du arbetat i en aktiv process för att felsöka ett skript som körs i en körnings utrymme i processen, enligt beskrivningen i Ange-PSHostProcess. När du har angett kommandot **Avsluta** för att avsluta fel söknings programmet, kör cmdleten **exit-PSHostProcess** för att stänga den interaktiva sessionen med processen.
Cmdleten stänger sessionen i processen och återgår till PS C: \\ \> prompten.

## PARAMETRAR

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

## UTDATA

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Retur-PSHostProcess](Enter-PSHostProcess.md)
