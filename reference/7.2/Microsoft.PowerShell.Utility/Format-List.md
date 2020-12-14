---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/19/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-list?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-List
ms.openlocfilehash: d8410fbc2d3f29f0726f84ab151993a60ce95434
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709792"
---
# Format-List

## SAMMANFATTNING
Formaterar utdata som en lista med egenskaper där varje egenskap visas på en ny rad.

## SYNTAX

```
Format-List [[-Property] <Object[]>] [-GroupBy <Object>] [-View <string>] [-ShowError]
[-DisplayError] [-Force] [-Expand <string>] [-InputObject <psobject>] [<CommonParameters>]
```

## BESKRIVNING

`Format-List`Cmdleten formaterar utdata från ett kommando som en lista med egenskaper där varje egenskap visas på en separat rad. Du kan använda `Format-List` för att formatera och Visa alla eller valda egenskaper för ett objekt som en lista (format-List *).

Eftersom det finns mer utrymme för varje objekt i en lista än i en tabell, visar PowerShell fler egenskaper för objektet i listan, och egenskapsvärdena är mindre troligt vis trunkerade.

## EXEMPEL

### Exempel 1: formatera dator tjänster

```powershell
Get-Service | Format-List
```

Det här kommandot formaterar information om tjänster på datorn som en lista. Som standard är tjänsterna formaterade som en tabell. `Get-Service`Cmdleten hämtar objekt som representerar tjänsterna på datorn. Pipeline-operatorn (|) skickar resultaten via pipelinen till `Format-List` .
Sedan `Format-List` formaterar kommandot tjänst informationen i en lista och skickar den till standardutdata-cmdleten för visning.

### Exempel 2: formatera PS1XML-filer

De här kommandona visar information om PS1XML-filerna i PowerShell-katalogen som en lista.

```powershell
$A = Get-ChildItem $pshome\*.ps1xml
Format-List -InputObject $A
```

Det första kommandot hämtar objekten som representerar filerna och lagrar dem i `$A` variabeln.

Det andra kommandot använder `Format-List` för att formatera information om objekt som lagras i `$A` . Det här kommandot använder parametern **InputObject** för att skicka variabeln till `Format-List` , som sedan skickar det formaterade resultatet till standardutdata-cmdleten för visning.

### Exempel 3: formatera process egenskaper efter namn

Det här kommandot visar namnet, bas prioriteten och prioritets klassen för varje process på datorn.

```powershell
Get-Process | Format-List -Property name, basepriority, priorityclass
```

Den använder `Get-Process` cmdleten för att hämta ett objekt som representerar varje process. Pipeline-operatorn (|) skickar process objekt via pipelinen till `Format-List` . `Format-List` formaterar processerna som en lista med de angivna egenskaperna. *Egenskaps* parameter namnet är valfritt, så du kan utelämna det.

### Exempel 4: formatera alla egenskaper för en process

Det här kommandot visar alla egenskaper för Winlogon-processen.

```powershell
Get-Process winlogon | Format-List -Property *
```

Den använder Get-Process-cmdlet för att hämta ett objekt som representerar Winlogon-processen. Pipeline-operatorn (|) skickar objektet Winlogon-process via pipeline till `Format-List` . Kommandot använder *egenskaps* parametern för att ange egenskaperna och \* för att ange alla egenskaper.
Eftersom namnet på *egenskaps* parametern är valfritt kan du utelämna det och skriva kommandot som `Format-List *` . `Format-List` skickar automatiskt resultaten till standard-utdata-cmdleten för visning.

### Exempel 5: fel sökning av format fel

I följande exempel visas resultatet av att lägga till **DisplayError** -eller **ShowError** -parametrarna med ett uttryck.

```powershell
PC /> Get-Date | Format-List DayOfWeek,{ $_ / $null } -DisplayError

DayOfWeek    : Friday
 $_ / $null  : #ERR

PC /> Get-Date | Format-List DayOfWeek,{ $_ / $null } -ShowError

DayOfWeek    : Friday
 $_ / $null  :

Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 7:59:23 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## PARAMETRAR

### – DisplayError

Anger att denna cmdlet visar fel på kommando raden. Den här parametern används sällan, men kan användas som ett fel söknings stöd när du formaterar uttryck i ett `Format-List` kommando, och uttrycken verkar inte fungera.

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

### – Expandera

Anger det formaterade samlings objektet, samt objekt i samlingen. Den här parametern är utformad för att formatera objekt som har stöd för ICollection-gränssnittet (system. Collection). Standardvärdet är EnumOnly. De acceptabla värdena för den här parametern är:

- EnumOnly. Visar egenskaperna för objekten i samlingen.
- CoreOnly. Visar egenskaperna för objektet samling.
- Dubbelrikta. Visar egenskaperna för samlings objekt och egenskaper för objekt i samlingen.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Anger att denna cmdlet visar all fel information. Används med parametern **DisplayError** eller **ShowError** . Som standard visas endast en del fel information när ett fel objekt skrivs till fel-eller visnings strömmar.

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

### – GroupBy

Anger utdata i grupper baserat på en delad egenskap eller ett värde. Ange ett uttryck eller en egenskap för utdata.

Värdet för **groupby** -parametern kan vara en ny beräknad egenskap. Den beräknade egenskapen kan vara ett skript block eller en hash-tabell. Giltiga nyckel/värde-par är:

- Namn (eller etikett)- `<string>`
- Uttryck- `<string>` eller `<script block>`
- FormatString `<string>`

Mer information finns i [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject

Anger de objekt som ska formateras. Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.

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

### – Egenskap

Anger objekt egenskaperna som visas i visningen och i vilken ordning de visas.
Jokertecken är tillåtna.

Om du utelämnar den här parametern beror egenskaperna som visas i vyn på det objekt som visas. Parameter namnet "Property" är valfritt. Du kan inte använda **egenskapen** och **Visa** parametrar i samma kommando.

Värdet för **egenskaps** parametern kan vara en ny beräknad egenskap. Den beräknade egenskapen kan vara ett skript block eller en hash-tabell. Giltiga nyckel/värde-par är:

- Namn (eller etikett)- `<string>`
- Uttryck- `<string>` eller `<script block>`
- FormatString `<string>`

Mer information finns i [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### – ShowError

Anger att cmdleten skickar fel via pipelinen. Den här parametern används sällan, men kan användas som ett fel söknings stöd när du formaterar uttryck i ett `Format-List` kommando, och uttrycken verkar inte fungera.

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

### – Visa

Anger namnet på ett alternativt List format eller en vy. Du kan inte använda **egenskapen** och **Visa** parametrar i samma kommando.

```yaml
Type: System.String
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

### System. Management. Automation. PSObject

Du kan skicka vidare alla objekt till `Format-List` .

## UTDATA

### Microsoft. PowerShell. commands. Internal. format

`Format-List` Returnerar de format objekt som representerar listan.

## ANTECKNINGAR

Du kan också referera till Format-List med det inbyggda aliaset, FL. Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).

Format-cmdletarna, till exempel `Format-List` , ordnar de data som ska visas men inte visar dem.
Data visas i utmatnings funktionerna i PowerShell och av de cmdletar som innehåller verbet (out-cmdletarna), till exempel `Out-Host` eller `Out-File` .

Om du inte använder en format-cmdlet, använder PowerShell standardformat för varje objekt som visas.

Parametern **groupby** förutsätter att objekten sorteras. Använd Sort-Object innan `Format-List` du använder för att gruppera objekten.

Med parametern **Visa** kan du ange ett alternativt format för tabellen. Du kan använda de vyer som definierats i `*.format.PS1XML` filerna i PowerShell-katalogen, eller så kan du skapa egna vyer i nya PS1XML-filer och använda cmdleten Update-FormatData för att inkludera dem i PowerShell.

Den alternativa vyn för parametern **View** måste använda List formatet, annars Miss lyckas kommandot. Om den alternativa vyn är en tabell använder du `Format-Table` . Om den alternativa vyn inte är en lista eller en tabell använder du `Format-Custom` .

## RELATERADE LÄNKAR

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[Format-Custom](Format-Custom.md)

[Format-Hex](Format-Hex.md)

[Format-Table](Format-Table.md)

[Format-Wide](Format-Wide.md)
