---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/20/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/export-binarymilog?WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-BinaryMiLog
ms.openlocfilehash: cf03ad884121c6cf8cf65cdb791cbdc4e587c3b9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263931"
---
# Export-BinaryMiLog

## SAMMANFATTNING
Skapar en binär kodad representation av ett objekt eller objekt och lagrar det i en fil.

## SYNTAX

```
Export-BinaryMiLog [-InputObject <CimInstance>] [-Path] <String> [<CommonParameters>]
```

## BESKRIVNING

`Export-BinaryMILog`Cmdleten skapar en binär-baserad representation av ett objekt eller objekt och lagrar det i en fil. Du kan sedan använda `Import-BinaryMiLog` cmdleten för att återskapa det sparade objektet baserat på innehållet i filen.

Denna cmdlet liknar `Import-Clixml` , förutom att `Export-BinaryMILog` lagrar det resulterande objektet i en binär kodad fil.

## EXEMPEL

### Exempel 1 – Skapa en binär representation av CimInstances

```powershell
Get-CimInstance Win32_Process | Export-BinaryMiLog -Path "Processes.bmil"
```

Detta kommando exporterar **CimInstances** till en binär mi-loggfil som anges av parametern Path. Se exemplet för Import-BinaryMiLog för att se hur du återskapar **CimInstances** genom att importera den här filen.

## PARAMETRAR

### – InputObject

Anger indatamängden för denna cmdlet. Du kan använda den här parametern, eller så kan du skicka en pipe till denna cmdlet.

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Path

Anger sökvägen till filen där den binära representationen av objektet ska lagras. Parametern **Path** stöder jokertecken och relativa sökvägar. Denna cmdlet genererar ett fel om sökvägen matchar fler än en fil.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Microsoft. Management. Infrastructure. CimInstance

## UTDATA

### System. Object

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Get-CimInstance](get-ciminstance.md)

[Importera – BinaryMiLog](import-binarymilog.md)

[Importera – CliXml](../microsoft.powershell.utility/import-clixml.md)
