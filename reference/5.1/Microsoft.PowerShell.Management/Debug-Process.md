---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/debug-process?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Process
ms.openlocfilehash: 98bd72901339d040748fc0d99b14bc1404ea1465
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388322"
---
# Debug-Process

## SAMMANFATTNING
Avbuggar en eller flera processer som körs på den lokala datorn.

## SYNTAX

### Namn (standard)

```
Debug-Process [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Id

```
Debug-Process [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InputObject

```
Debug-Process -InputObject <Process[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Debug-Process`Cmdleten kopplar en fel sökare till en eller flera processer som körs på en lokal dator.
Du kan ange processer efter process namn eller process-ID (PID), eller så kan du skicka vidare process objekt till denna cmdlet.

Den här cmdleten kopplar den fel sökare som för närvarande är registrerad för processen. Innan du använder denna cmdlet måste du kontrol lera att en fel sökare har laddats ned och kon figurer ATS korrekt.

## EXEMPEL

### Exempel 1: koppla en fel sökare till en process på datorn

```
PS C:\> Debug-Process -Name "Windows Powershell"
```

Det här kommandot kopplar en fel sökare till PowerShell-processen på datorn.

### Exempel 2: koppla en fel sökare till alla processer som börjar med den angivna strängen

```
PS C:\> Debug-Process -Name "SQL*"
```

Det här kommandot kopplar en fel sökare till alla processer som har namn som börjar med SQL.

### Exempel 3: koppla en fel sökare till flera processer

```
PS C:\> Debug-Process "Winlogon", "Explorer", "Outlook"
```

Det här kommandot kopplar en fel sökare till Winlogon-, Utforskare-och Outlook-processerna.

### Exempel 4: koppla en fel sökare till flera process-ID: n

```
PS C:\> Debug-Process -Id 1132, 2028
```

Det här kommandot kopplar en fel sökare till de processer som har process-ID 1132 och 2028.

### Exempel 5: Använd Get-Process för att få en process och koppla sedan en fel sökare till den

```
PS C:\> Get-Process "Windows PowerShell" | Debug-Process
```

Det här kommandot kopplar en fel sökare till PowerShell-processerna på datorn. Den använder `Get-Process` cmdleten för att hämta PowerShell-processer på datorn och använder en pipeline-operator ( `|` ) för att skicka processerna till `Debug-Process` cmdlet: en.

Om du vill ange en viss PowerShell-process använder du ID-parametern för `Get-Process` .

### Exempel 6: koppla en fel sökare till en aktuell process på den lokala datorn

```
PS C:\> $PID | Debug-Process
```

Det här kommandot kopplar en fel sökare till de aktuella PowerShell-processerna på datorn.

Kommandot använder den `$PID` automatiska variabeln, som innehåller process-ID: t för den aktuella PowerShell-processen. Sedan använder den en pipeline-operator ( `|` ) för att skicka process-ID: t till `Debug-Process` cmdleten.

Mer information om den `$PID` automatiska variabeln finns i about_Automatic_Variables.

### Exempel 7: koppla en fel sökare till den angivna processen på flera datorer

```
PS C:\> Get-Process -ComputerName "Server01", "Server02" -Name "MyApp" | Debug-Process
```

Det här kommandot kopplar en fel sökare till MyApp-processerna på Server01-och Server02-datorerna.

Kommandot använder `Get-Process` cmdleten för att hämta MyApp-processerna på Server01-och Server02-datorerna. Den använder en pipeline-operator för att skicka processerna till `Debug-Process` cmdleten, som kopplar fel sökningarna.

### Exempel 8: koppla en fel sökare till en process som använder parametern InputObject

```
PS C:\> $P = Get-Process "Windows PowerShell"
PS C:\> Debug-Process -InputObject $P
```

Det här kommandot kopplar en fel sökare till PowerShell-processerna på den lokala datorn.

Det första kommandot använder `Get-Process` cmdleten för att hämta PowerShell-processer på datorn. Det sparar det resulterande processobjektet i variabeln med namnet `$P` .

Det andra kommandot använder **InputObject** -parametern för `Debug-Process` cmdleten för att skicka processobjektet i `$P` variabeln.

## PARAMETRAR

### -ID

Anger process-ID: n för de processer som ska felsökas. **ID-** parameterns namn är valfritt.

Om du vill hitta process-ID för en process skriver du `Get-Process` .

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases: PID, ProcessId

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – InputObject

Anger de process objekt som representerar processer som ska felsökas. Ange en variabel som innehåller process objekt eller ett kommando som hämtar process objekt, t `Get-Process` . ex. cmdleten. Du kan också skicka process objekt till denna cmdlet.

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

Anger namnen på de processer som ska felsökas. Om det finns fler än en process med samma namn, kopplar denna cmdlet en fel sökare till alla processer med det namnet. Parametern **Name** är valfri.

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases: ProcessName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
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

### System. Int32, system. Diagnostics. process, system. String

Du kan skicka vidare ett process-ID (Int32), ett process objekt (system. Diagnostics. process) eller ett process namn (sträng) till denna cmdlet.

## UTDATA

### Inget

Denna cmdlet genererar inga utdata.

## ANTECKNINGAR

Denna cmdlet använder metoden AttachDebugger i Win32_Process-klassen Windows Management Instrumentation (WMI). Mer information om den här metoden finns i [AttachDebugger-metoden](https://go.microsoft.com/fwlink/?LinkId=143640) i MSDN-biblioteket.

## RELATERADE LÄNKAR

[Fel sökning – process](Debug-Process.md)

[Hämta process](Get-Process.md)

[Start process](Start-Process.md)

[Stoppa – process](Stop-Process.md)

[Vänta-process](Wait-Process.md)
