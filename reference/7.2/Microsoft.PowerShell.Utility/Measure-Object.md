---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/measure-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Measure-Object
ms.openlocfilehash: 594837b2f85f4d5d5d4125d3f7c63ad2c8a16153
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710374"
---
# Measure-Object

## SAMMANFATTNING
Beräknar numeriska egenskaper för objekt, samt tecken, ord och rader i sträng objekt, till exempel filer för text.

## SYNTAX

### GenericMeasure (standard)

```
Measure-Object [[-Property] <PSPropertyExpression[]>] [-InputObject <PSObject>] [-StandardDeviation]
 [-Sum] [-AllStats] [-Average] [-Maximum] [-Minimum] [<CommonParameters>]
```

### TextMeasure

```
Measure-Object [[-Property] <PSPropertyExpression[]>] [-InputObject <PSObject>] [-Line] [-Word]
 [-Character] [-IgnoreWhiteSpace] [<CommonParameters>]
```

## BESKRIVNING

`Measure-Object`Cmdleten beräknar egenskaps värden för vissa typer av objekt.
`Measure-Object` utför tre typer av mätningar, beroende på parametrarna i kommandot.

`Measure-Object`Cmdlet: en utför beräkningar på objektets egenskaps värden. Du kan använda `Measure-Object` för att räkna objekt eller räkna objekt med en angiven **egenskap**. Du kan också använda `Measure-Object` för att beräkna **lägsta**, **högsta**, **Sum**, **StandardDeviation** och **medelvärde** för numeriska värden. För **sträng** objekt kan du också använda `Measure-Object` för att räkna antalet rader, ord och tecken.

## EXEMPEL

### Exempel 1: räkna filerna och mapparna i en katalog

Det här kommandot räknar filerna och mapparna i den aktuella katalogen.

```powershell
Get-ChildItem | Measure-Object
```

### Exempel 2: mäta filerna i en katalog

Det här kommandot visar det **lägsta**, **högsta** och **summan** av storlekarna för alla filer i den aktuella katalogen och den genomsnittliga storleken på en fil i katalogen.

```powershell
Get-ChildItem | Measure-Object -Property length -Minimum -Maximum -Average
```

### Exempel 3: mäta text i en textfil

Det här kommandot visar antalet tecken, ord och rader i Text.txts filen.
Utan den **obehandlade** parametern, `Get-Content` matas filen ut som en matris med rader.

Det första kommandot använder `Set-Content` för att lägga till viss standard text i en fil.

```powershell
"One", "Two", "Three", "Four" | Set-Content -Path C:\Temp\tmp.txt
Get-Content C:\Temp\tmp.txt | Measure-Object -Character -Line -Word
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    4     4         15
```

### Exempel 4: Mät objekt som innehåller en angiven egenskap

Det här exemplet räknar antalet objekt som har egenskapen **DisplayName** . De två första kommandona hämtar alla tjänster och processer på den lokala datorn. Det tredje kommandot räknar det sammanlagda antalet tjänster och processer. Det sista kommandot kombinerar de två samlingarna och slår resultatet till `Measure-Object` .

Objektet **system. Diagnostics. process** har ingen **DisplayName** -egenskap och lämnas utanför det slutliga antalet.

```powershell
$services = Get-Service
$processes = Get-Process
$services + $processes | Measure-Object
$services + $processes | Measure-Object -Property DisplayName
```

```Output
Count    : 682
Average  :
Sum      :
Maximum  :
Minimum  :
Property :

Count    : 290
Average  :
Sum      :
Maximum  :
Minimum  :
Property : DisplayName
```

### Exempel 5: mäta innehållet i en CSV-fil

Det här kommandot beräknar det genomsnittliga året för de anställda i ett företag.

`ServiceYrs.csv`Filen är en CSV-fil som innehåller anställnings numret och varje anställds års tjänst. Den första raden i tabellen är en rubrik rad av **EmpNo**, **år**.

När du använder `Import-Csv` för att importera filen är resultatet en **PSCustomObject** med antecknings egenskaper för **EmpNo** och **år**.
Du kan använda `Measure-Object` för att beräkna värdena för dessa egenskaper, precis som andra egenskaper för ett objekt.

```powershell
Import-Csv d:\test\serviceyrs.csv | Measure-Object -Property years -Minimum -Maximum -Average
```

### Exempel 6: Mät booleska värden

Det här exemplet visar hur `Measure-Object` kan mäta booleska värden.
I det här fallet använder den **Boolean** -egenskapen **PSIsContainer** för att mäta antalet mappar (vs. files) i den aktuella katalogen.

```powershell
Get-ChildItem | Measure-Object -Property psiscontainer -Maximum -Sum -Minimum -Average
```

```Output
Count             : 126
Average           : 0.0634920634920635
Sum               : 8
Maximum           : 1
Minimum           : 0
StandardDeviation :
Property          : PSIsContainer
```

### Exempel 7: Mät strängar

I följande exempel mäter antalet rader, först en sträng och sedan över flera strängar. Tecknet för ny rad <code>`n</code> avgränsar strängar till flera rader.

```powershell
# The newline character `n separates the string into separate lines, as shown in the output.
"One`nTwo`nThree"
"One`nTwo`nThree" | Measure-Object -Line
```

```Output
One
Two
Three


Lines Words Characters Property
----- ----- ---------- --------
    3
```

```powershell
# The first string counts as a single line.
# The second string is separated into two lines by the newline character.
"One", "Two`nThree" | Measure-Object -Line
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    3
```

```powershell
# The Word switch counts the number of words in each InputObject
# Each InputObject is treated as a single line.
"One, Two", "Three", "Four Five" | Measure-Object -Word -Line
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    3     5
```

### Exempel 8: mäta alla värden

Från och med PowerShell 6  `Measure-Object` kan du mäta all statistik tillsammans med AllStats-parametern.

```powershell
1..5 | Measure-Object -AllStats
```

```output
Count             : 5
Average           : 3
Sum               : 15
Maximum           : 5
Minimum           : 1
StandardDeviation : 1.58113883008419
Property          :
```

### Exempel 9: mått med script block-egenskaper

Från och med PowerShell 6 `Measure-Object` stöder **script block** -egenskaper. Följande exempel visar hur du använder en **script block** -egenskap för att fastställa storleken, i megabyte, för alla filer i en katalog.

```powershell
Get-ChildItem | Measure-Object -Sum {$_.Length/1MB}
```

### Exempel 10: mått hash

Från och med PowerShell 6 `Measure-Object` stöder mätning av **datahash** -ingångar. I följande exempel bestäms det största värdet för `num` nyckeln för 3 **hash** -objekt.

```powershell
@{num=3}, @{num=4}, @{num=5} | Measure-Object -Maximum Num
```

```output
Count             : 3
Average           :
Sum               :
Maximum           : 5
Minimum           :
StandardDeviation :
Property          : num
```

### Exempel 11: Mät standard avvikelsen

Från och med PowerShell 6 `Measure-Object` stöder `-StandardDeviation` parametern. I följande exempel bestäms *standard avvikelsen* för den CPU som används av alla processer. En stor avvikelse indikerar ett litet antal processer som förbrukar mest processor kraft.

```powershell
Get-Process | Measure-Object -Average -StandardDeviation CPU
```

```output
Count             : 303
Average           : 163.032384488449
Sum               :
Maximum           :
Minimum           :
StandardDeviation : 859.444048419069
Property          : CPU
```

### Exempel 12: mäta med jokertecken

Från och med PowerShell 6 `Measure-Object` stöder mätning av objekt med jokertecken i egenskaps namn. I följande exempel bestäms det högsta av alla typer av växlings Bart minne mellan en uppsättning processer.

```powershell
Get-Process | Measure-Object -Maximum *paged*memory*size
```

```output
Count             : 303
Average           :
Sum               :
Maximum           : 735784
Minimum           :
StandardDeviation :
Property          : NonpagedSystemMemorySize

Count             : 303
Average           :
Sum               :
Maximum           : 352104448
Minimum           :
StandardDeviation :
Property          : PagedMemorySize

Count             : 303
Average           :
Sum               :
Maximum           : 2201968
Minimum           :
StandardDeviation :
Property          : PagedSystemMemorySize

Count             : 303
Average           :
Sum               :
Maximum           : 719032320
Minimum           :
StandardDeviation :
Property          : PeakPagedMemorySize
```

## PARAMETRAR

### – Genomsnittlig

Anger att cmdleten visar genomsnitts värdet för de angivna egenskaperna.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Character

Anger att cmdleten räknar antalet tecken i objekten.

> [!NOTE]
> **Ord**, **char** och **linje** växlar räknas *i* varje inobjekt, samt *över* inobjekt. Se exempel 7.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IgnoreWhiteSpace

Anger att cmdleten ignorerar blank steg i antal tecken.
Som standard ignoreras inte blank steg.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject

Anger de objekt som ska mätas.
Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.

När du använder parametern **InputObject** i `Measure-Object` , i stället för Skicka kommando resultat till `Measure-Object` , behandlas **InputObject** -värdet som ett enskilt objekt.

Vi rekommenderar att du använder `Measure-Object` i pipelinen om du vill mäta en samling objekt baserat på om objekten har angivna värden i definierade egenskaper.

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

### -Rad

Anger att cmdleten räknar antalet rader i objekten.

> [!NOTE]
> **Ord**, **char** och **linje** växlar räknas *i* varje inobjekt, samt *över* inobjekt. Se exempel 7.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Maximalt

Anger att cmdleten visar det maximala värdet för de angivna egenskaperna.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Minst

Anger att cmdleten visar det minsta värdet för de angivna egenskaperna.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Egenskap

Anger en eller flera egenskaper som ska mätas. Om du inte anger några andra mått `Measure-Object` räknar de objekt som har de egenskaper som du anger.

Värdet för **egenskaps** parametern kan vara en ny beräknad egenskap. Den beräknade egenskapen måste vara ett skript block. Mer information finns i [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).

```yaml
Type: Microsoft.PowerShell.Commands.PSPropertyExpression[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -StandardDeviation

Anger att cmdleten visar standard avvikelsen för värdena för de angivna egenskaperna.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Sum

Anger att cmdleten visar summan av värdena för de angivna egenskaperna.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllStats

Anger att cmdleten visar all statistik för de angivna egenskaperna.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Ord

Anger att cmdleten räknar antalet ord i objekten.

> [!NOTE]
> **Ord**, **char** och **linje** växlar räknas *i* varje inobjekt, samt *över* inobjekt. Se exempel 7.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
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

Du kan skicka pipe-objekt till `Measure-Object` .

## UTDATA

### Microsoft. PowerShell. commands. GenericMeasureInfo

### Microsoft. PowerShell. commands. TextMeasureInfo

Om du använder parametern **Word** `Measure-Object` returnerar ett **TextMeasureInfo** -objekt.
Annars returnerar den ett **GenericMeasureInfo** -objekt.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[Jämför objekt](Compare-Object.md)

[-Objekt](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Gruppera objekt](Group-Object.md)

[Nytt – objekt](New-Object.md)

[Select-Object](Select-Object.md)

[Sortera objekt](Sort-Object.md)

[Tee – objekt](Tee-Object.md)

[Where-objekt](../Microsoft.PowerShell.Core/Where-Object.md)
