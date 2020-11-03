---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/18/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-timezone?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-TimeZone
ms.openlocfilehash: 9f442e4423eb9695776733e7938cc2cf861e2fae
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263780"
---
# Set-TimeZone

## SAMMANFATTNING
Ställer in system tids zonen till en angiven tidszon.

## SYNTAX

### Namn (standard)

```
Set-TimeZone [-Name] <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Id

```
Set-TimeZone -Id <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InputObject

```
Set-TimeZone [-InputObject] <TimeZoneInfo> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Set-TimeZone`Cmdleten anger system tids zonen till en angiven tidszon.

## EXEMPEL

### Exempel 1: Ange tids zonen efter ID

I det här exemplet anges tids zonen på den lokala datorn till ryska, normal tid.

```powershell
Set-TimeZone -Id "Russian Standard Time" -PassThru
```

```Output
Id                         : Russian Standard Time
DisplayName                : (UTC+03:00) Moscow, St. Petersburg
StandardName               : Russia TZ 2 Standard Time
DaylightName               : Russia TZ 2 Daylight Time
BaseUtcOffset              : 03:00:00
SupportsDaylightSavingTime : True
```

### Exempel 2: Ange tids zonen efter namn

I det här exemplet anges tids zonen på den lokala datorn till ryska, normal tid.

```powershell
Set-TimeZone -Name "Russia TZ 2 Standard Time"
```

Som vi såg i föregående exempel stämmer inte alltid med **ID** och **namnet** för tids zonen.
Parametern **Name** måste matcha **StandardName** -eller **DaylightName** -egenskaperna för **TimeZoneInfo** -objektet.

## PARAMETRAR

### -ID

Anger ID för den tidszon som denna cmdlet anger. En fullständig lista över tids zons-ID: n kan erhållas genom att köra följande kommando: `Get-TimeZone -ListAvailable` .

```yaml
Type: System.String
Parameter Sets: Id
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – InputObject

Anger ett **TimeZoneInfo** -objekt som ska användas som indatamängd.

```yaml
Type: System.TimeZoneInfo
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

Anger namnet på den tidszon som denna cmdlet anger. En fullständig lista över tids zons namn kan hämtas genom att köra följande kommando: `Get-TimeZone -ListAvailable` .

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – PassThru

Returnerar ett objekt som representerar det objekt som du arbetar med. Som standard genererar denna cmdlet inga utdata.

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

Visar vad som skulle hända om cmdleten kördes. Cmdleten körs inte.

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

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String, system. TimeZoneInfo, system. String

## UTDATA

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Get-TimeZone](Get-TimeZone.md)
