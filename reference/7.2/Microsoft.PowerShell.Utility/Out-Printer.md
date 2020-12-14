---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-printer?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Printer
ms.openlocfilehash: f2b3e20685ee52a7f9ca1bfd23af5fc5bca24001
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710080"
---
# Out-Printer

## SAMMANFATTNING
Skickar utdata till en skrivare.

## SYNTAX

```
Out-Printer [[-Name] <String>] [-InputObject <PSObject>] [<CommonParameters>]
```

## BESKRIVNING

`Out-Printer`Cmdleten skickar utdata till standard skrivaren eller till en alternativ skrivare, om en sådan finns angiven.

> [!NOTE]
> Den här cmdleten introducerades om i PowerShell 7. Den här cmdleten är endast tillgänglig på Windows-system som stöder Windows-skrivbordet.

## EXEMPEL

### Exempel 1 – skicka en fil som ska skrivas ut på standard skrivaren

Det här exemplet visar hur du skriver ut en fil, även om inte `Out-Printer` har en **Sök vägs** parameter.

```powershell
Get-Content -Path ./readme.txt | Out-Printer
```

`Get-Content`hämtar innehållet i `readme.txt` filen i den aktuella katalogen och skickar den till `Out-Printer` , som skickar den till standard skrivaren.

### Exempel 2: skriva ut en sträng till en fjärran sluten skrivare

Det här exemplet skriver ut `Hello, World` till **färg skrivaren PRT-6b** på Server01.

```powershell
"Hello, World" | Out-Printer -Name "\\Server01\Prt-6B Color"
```

Parametern **Name** väljer en speciell skrivare istället för standardvärdet.

### Exempel 3 – Skriv ut ett hjälp avsnitt till standard skrivaren

I det här exemplet skrivs den fullständiga versionen av hjälp avsnittet för `Get-CimInstance` .

```powershell
$H = Get-Help -Full Get-CimInstance
Out-Printer -InputObject $H
```

`Get-Help` hämtar den fullständiga versionen av hjälp avsnittet för `Get-CimInstance` och lagrar den i `$H` variabeln. Parametern **InputObject** skickar värdet `$H` till `Out-Printer` .

## PARAMETRAR

### – InputObject

Anger de objekt som ska skickas till skrivaren. Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.

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

### -Name

Skickar utdata till den angivna skrivaren. Parameter namnets **namn** är valfritt.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PrinterName

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Management. Automation. PSObject

Du kan skicka vidare alla objekt till `Out-Printer` .

## UTDATA

### Inga

`Out-Printer` returnerar inga objekt.

## ANTECKNINGAR

Den här cmdleten är endast tillgänglig på Windows-plattformar.

Cmdletarna som innehåller `Out` verbet formaterar inte objekt. De återger dem bara och skickar dem till det angivna visnings målet. Om du skickar ett oformaterat objekt till en `Out` cmdlet skickar cmdleten den till en formaterings-cmdlet innan du återger den.

`Out-Printer` skickar data till skrivaren, men genererar inga utdata-objekt till pipelinen. Om du skickar utdata från `Out-Printer` till `Get-Member` , rapporterar det `Get-Member` att inga objekt har angetts.

## RELATERADE LÄNKAR

[Ut-fil](Out-File.md)

[Out-sträng](Out-String.md)
