---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-uptime?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Uptime
ms.openlocfilehash: df4091609f403a58749a6821044d768089cdc03c
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194569"
---
# Get-Uptime

## SAMMANFATTNING
Hämta **TimeSpan** sedan senaste start.

## SYNTAX

### TimeSpan (standard)

```
Get-Uptime [<CommonParameters>]
```

### Starta

```
Get-Uptime [-Since] [<CommonParameters>]
```

## BESKRIVNING

Den här cmdleten returnerar den tid som gått sedan den senaste starten av operativ systemet.

`Get-Uptime`Cmdleten introducerades i PowerShell 6,0.

## EXEMPEL

### Exempel 1 – Visa tid sedan senaste start

```powershell
Get-Uptime
```

```Output
Days              : 9
Hours             : 0
Minutes           : 9
Seconds           : 45
Milliseconds      : 0
Ticks             : 7781850000000
TotalDays         : 9.00677083333333
TotalHours        : 216.1625
TotalMinutes      : 12969.75
TotalSeconds      : 778185
TotalMilliseconds : 778185000
```

### Exempel 2 – Visa tiden för den senaste starten

```powershell
Get-Uptime -Since
```

```Output
Tuesday, June 18, 2019 2:34:56 PM
```

## PARAMETRAR

### -Sedan

Orsaka att cmdleten returnerar ett **datetime** -objekt som representerar den senaste gången operativ systemet startades.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Since
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

### Inget

## UTDATA

### System. TimeSpan

Det här är standard retur typen när inga parametrar används.

### System. DateTime

Den här typen returneras när parametern **sedan** används.

> [!NOTE]
> Om snabb start av Windows har Aktiver ATS, uppdaterar Windows inte värdet som lagras i **LastBootUpTime**. Om du vill inaktivera snabb start kör du följande kommando: `Powercfg -h off` .
>
> Mer information om snabb start i Windows finns i avsnittet [Skilj snabb starten från Väcknings från vilo läge](/windows-hardware/drivers/kernel/distinguishing-fast-startup-from-wake-from-hibernation).

## ANTECKNINGAR

I Windows är det returnerade värdet detsamma som egenskapen **LastBootUpTime** för klassen **Win32_OperatingSystem** i WMI.

## RELATERADE LÄNKAR

[Win32_OperatingSystem](/windows/win32/cimwin32prov/win32-operatingsystem#properties)
