---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-runspace?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Runspace
ms.openlocfilehash: 7d2dc7ce170d3f5de15fe5ad289e664e9f11847b
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262682"
---
# Get-Runspace

## SAMMANFATTNING
Hämtar aktiva körnings utrymmen i en PowerShell-värd process.

## SYNTAX

### NameParameterSet (standard)

```
Get-Runspace [[-Name] <String[]>] [<CommonParameters>]
```

### IdParameterSet

```
Get-Runspace [-Id] <Int32[]> [<CommonParameters>]
```

### InstanceIdParameterSet

```
Get-Runspace [-InstanceId] <Guid[]> [<CommonParameters>]
```

## BESKRIVNING

`Get-Runspace`Cmdleten hämtar aktiva körnings utrymmen i en PowerShell-värd process.

## EXEMPEL

### Exempel 1: Hämta körnings utrymmen

```powershell
Get-Runspace
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  1 Runspace1       localhost       Local         Opened        Busy
  2 Runspace2       localhost       Local         Opened        Available
  3 Runspace3       localhost       Local         Opened        Available
```

### Exempel 2: Hämta körnings utrymme efter ID

```powershell
Get-Runspace -Id 2
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  2 Runspace2       localhost       Local         Opened        Available
```

### Exempel 3: Hämta körnings utrymme efter namn

```powershell
Get-Runspace -Name Runspace1
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  1 Runspace1       localhost       Local         Opened        Busy
```

### Exempel 4: Hämta körnings utrymme av InstanceId

I det här exemplet identifierar vi en tillgänglig körnings utrymme med `Name` parametern och lagrar returvärdet till variabeln `$activeRunspace` . På så sätt kan du använda egenskaperna för **körnings utrymme** i efterföljande körningar av `Get-Runspace` .

```powershell
$activeRunspace = Get-Runspace -Name Runspace1
Get-Runspace -InstanceId $activeRunspace.InstanceId
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  1 Runspace1       localhost       Local         Opened        Busy
```

## PARAMETRAR

### -ID

Anger ID för en körnings utrymme

```yaml
Type: System.Int32[]
Parameter Sets: IdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InstanceId

Anger instans-ID-GUID för ett jobb som körs.

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Anger namnet på en körnings utrymme

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

## UTDATA

### System. Management. Automation. körnings utrymmen. körnings utrymme

Du kan skicka vidare resultatet av ett `Get-Runspace` kommando till `Debug-Runspace` .

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Felsök – körnings utrymme](Debug-Runspace.md)
