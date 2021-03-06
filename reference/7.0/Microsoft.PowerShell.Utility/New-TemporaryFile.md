---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-temporaryfile?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-TemporaryFile
ms.openlocfilehash: c4bfe6b4ed04ae638421c18f5095403057dc03c9
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262377"
---
# New-TemporaryFile

## SAMMANFATTNING
Skapar en temporär fil.

## SYNTAX

```
New-TemporaryFile [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

Denna cmdlet skapar temporära filer som du kan använda i skript.

`New-TemporaryFile`Cmdleten skapar en tom fil som har `.tmp` fil namns tillägget.
Denna cmdlet namnger filen `tmp<NNNN>.tmp` , där `<NNNN>` är ett slumpmässigt hexadecimalt tal.
Cmdleten skapar filen i **Temp** -mappen.

Denna cmdlet använder metoden [Path. GetTempPath ()](/dotnet/api/system.io.path.gettemppath) för att hitta **Temp** -mappen. Den här metoden kontrollerar om det finns miljövariabler i följande ordning och använder den första sökvägen som hittades:

- På Windows-plattformar:

  1. Sökvägen som anges av TMP-miljövariabeln.
  1. Sökvägen som anges av miljövariabeln TEMP.
  1. Den sökväg som anges av miljövariabeln USERPROFILE.
  1. Windows-katalogen.

- På andra plattformar än Windows: använder sökvägen som anges av miljövariabeln TMPDIR.

## EXEMPEL

### Exempel 1: skapa en temporär fil

```powershell
$TempFile = New-TemporaryFile
```

Det här kommandot skapar en `.tmp` fil i den tillfälliga mappen och lagrar sedan en referens till filen i `$TempFile` variabeln. Du kan använda den här filen senare i skriptet.

## PARAMETRAR

### -Confirm

Uppmanar dig att bekräfta innan du kör cmdleten.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Visar vad som skulle hända om cmdleten kördes.
Cmdleten körs inte.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

## UTDATA

### System. IO. FileInfo

Denna cmdlet returnerar ett **fileinfo** -objekt som representerar den temporära filen.

## ANTECKNINGAR

## RELATERADE LÄNKAR
