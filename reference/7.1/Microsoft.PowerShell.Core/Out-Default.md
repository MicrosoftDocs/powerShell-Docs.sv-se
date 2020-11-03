---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-default?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Default
ms.openlocfilehash: c1293b93079fed439c42d6ba41747cbe6a0c33fe
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267620"
---
# Out-Default

## SAMMANFATTNING
Skickar utdata till standard-formateraren och till standardutdata-cmdleten.

## SYNTAX

```
Out-Default [-Transcript] [-InputObject <PSObject>] [<CommonParameters>]
```

## BESKRIVNING

PowerShell lägger automatiskt `Out-Default` till i slutet av varje pipeline. `Out-Default` bestämmer hur objekt strömmen ska formateras och matas ut. Om objekt strömmen är en data ström med strängar, `Out-Default` rör dessa direkt som `Out-Host` anropar lämpliga API: er som tillhandahålls av värden. Om objekt strömmen inte innehåller strängar `Out-Default` kontrollerar objektet objektet för att avgöra vad som ska göras.
Först ser det ut som objekt typ och avgör om det finns en registrerad _vy_ för den här objekt typen.

PowerShell definierar XML-schemat och en mekanism ( `Update-FormatData` cmdleten) där vem som helst kan registrera vyer för en objekt typ. Du kan ange **breda** , **lista** , **tabell** eller **anpassade** vyer för valfri objekt typ. Vyerna anger vilka egenskaper som ska visas och hur de ska visas. Om en vy är registrerad definierar den vilken formatering som ska användas. Så om den registrerade vyn är en **tabellvy** , `Out-Default` strömmas objekten till `Format-Table | Out-Host` . `Format-Table` transformerar objekten till en strömmande av formaterings poster (som styrs av data i vydefinitionen) och `Out-Host` transformerar de formaterade posterna till anrop i värd gränssnittet.

## EXEMPEL

### Exempel 1

Även om denna cmdlet inte är avsedd att köras direkt av slutanvändaren kan det vara.

```powershell
Get-Process | Select-Object -First 5 | Out-Default
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     12     2.56       5.20       0.00    7376   0 aesm_service
     48    34.32      18.10      26.64    9320  13 AlertusDesktopAlert
     24    13.97      12.74       0.77   12656  13 ApplicationFrameHost
      8     1.79       4.41       0.00    8180   0 AppVShNotify
      9     1.99       5.07       0.19   19320  13 AppVShNotify
```

## PARAMETRAR

### – InputObject

Accepterar ininformation till cmdleten.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Avskrift

Anger om utdata ska skickas till PowerShell: s avskrifts tjänster.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

## UTDATA

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Format-Custom](../Microsoft.PowerShell.Utility/Format-Custom.md)

[Format-List](../Microsoft.PowerShell.Utility/Format-List.md)

[Format-Table](../Microsoft.PowerShell.Utility/Format-Table.md)

[Format-Wide](../Microsoft.PowerShell.Utility/Format-Wide.md)

[about_Format.ps1XML](About/about_Format.ps1xml.md)

[Hur PowerShell-formatering och utmatning fungerar](https://devblogs.microsoft.com/powershell/how-powershell-formatting-and-outputting-really-works/)

