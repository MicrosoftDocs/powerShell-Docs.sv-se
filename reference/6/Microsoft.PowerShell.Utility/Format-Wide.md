---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-wide?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Wide
ms.openlocfilehash: 820835065e73cdabb07e47b238041d0b8e375d2f
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/10/2020
ms.locfileid: "93269049"
---
# Format-Wide

## SAMMANFATTNING
Formaterar objekt som en bred tabell som endast visar en egenskap för varje objekt.

## SYNTAX

```
Format-Wide [[-Property] <Object>] [-AutoSize] [-Column <int>] [-GroupBy <Object>] [-View <string>]
  [-ShowError] [-DisplayError] [-Force] [-Expand <string>] [-InputObject <psobject>]
  [<CommonParameters>]
```

## BESKRIVNING

`Format-Wide`Cmdleten formaterar objekt som en bred tabell som endast visar en egenskap för varje objekt. Du kan använda **egenskaps** parametern för att avgöra vilken egenskap som visas.

## EXEMPEL

### Exempel 1: formatera namn på filer i den aktuella katalogen

Det här kommandot visar namnen på filer i den aktuella katalogen i tre kolumner på skärmen.

```powershell
Get-ChildItem | Format-Wide -Column 3
```

Get-ChildItem-cmdlet: en hämtar objekt som representerar varje fil i katalogen. Pipeline-operatorn (|) skickar fil objekt via pipelinen till `Format-Wide` , som formaterar dem för utdata. **Kolumn** parametern anger antalet kolumner.

### Exempel 2: formatera namn på register nycklar

Det här kommandot visar namnen på register nycklar i HKEY_CURRENT_USER\Software\Microsoft nyckeln.

```powershell
Get-ChildItem HKCU:\software\microsoft | Format-Wide -Property pschildname -AutoSize
```

Get-ChildItem cmdleten hämtar objekt som representerar nycklarna. Sökvägen anges som HKCU:, en av de enheter som exponeras av PowerShell-registernyckeln, följt av nyckel Sök vägen. Pipeline-operatorn (|) skickar register nyckel objekt via pipelinen till `Format-Wide` , som formaterar dem för utdata. **Egenskaps** parametern anger namnet på egenskapen och parametern **AutoSize** justerar kolumnerna för läsbarhet.

### Exempel 3: Felsöka format fel

I följande exempel visas resultatet av att lägga till **DisplayError** -eller **ShowError** -parametrarna med ett uttryck.

```powershell
PS /> Get-Date | Format-Wide { $_ / $null } -DisplayError


#ERR

PS /> Get-Date | Format-Wide { $_ / $null } -ShowError


Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 8:18:01 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## PARAMETRAR

### -AutoSize

Justerar kolumn storlek och antal kolumner baserat på data bredden. Som standard bestäms kolumn storleken och antalet av vyn. Du kan inte använda **AutoSize** -och **Column** -parametrarna i samma kommando.

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

### -Kolumn

Anger antalet kolumner i visningen. Du kan inte använda **AutoSize** -och **Column** -parametrarna i samma kommando.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – DisplayError

Visar fel på kommando raden. Den här parametern används sällan, men kan användas som ett fel söknings stöd när du formaterar uttryck i ett `Format-Wide` kommando, och uttrycken verkar inte fungera.

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

Formaterar samlings objekt och objekt i samlingen. Den här parametern är utformad för att formatera objekt som har stöd för ICollection-gränssnittet (system. Collection). Standardvärdet är **EnumOnly**.

Giltiga värden är:

- EnumOnly: visar egenskaperna för objekten i samlingen.
- CoreOnly: visar egenskaperna för objektet samling.
- Båda: visar egenskaperna för Collection-objektet och egenskaperna för objekt i samlingen.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: EnumOnly
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Anger att denna cmdlet åsidosätter begränsningar som hindrar kommandot från att lyckas, bara för att ändringarna inte äventyrar säkerheten. **Tvinga** åsidosätter till exempel det skrivskyddade attributet eller skapa kataloger för att slutföra en fil Sök väg, men kommer inte att försöka ändra fil behörigheter.

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

Formaterar utdata i grupper baserat på en delad egenskap eller ett värde. Ange ett uttryck eller en egenskap för utdata.

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

- Uttryck- `<string>` eller `<script block>`
- FormatString `<string>`

Mer information finns i [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### – ShowError

Skickar fel via pipelinen. Den här parametern används sällan, men kan användas som ett fel söknings stöd när du formaterar uttryck i ett `Format-Wide` kommando, och uttrycken verkar inte fungera.

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

Anger namnet på ett alternativt tabell format eller en vy. Du kan inte använda **egenskapen** och **Visa** parametrar i samma kommando.

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

Du kan skicka vidare alla objekt till `Format-Wide` .

## UTDATA

### Microsoft. PowerShell. commands. Internal. format

`Format-Wide` Returnerar format objekt som representerar tabellen.

## ANTECKNINGAR

Du kan också referera till `Format-Wide` med dess inbyggda alias `fw` . Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).

Parametern **groupby** förutsätter att objekten sorteras. Använd `Sort-Object` innan `Format-Custom` du använder för att gruppera objekten.

Med parametern **Visa** kan du ange ett alternativt format för tabellen. Du kan använda de vyer som definierats i `*.format.PS1XML` filerna i PowerShell-katalogen, eller så kan du skapa egna vyer i nya PS1XML-filer och använda `Update-FormatData` cmdleten för att inkludera dem i PowerShell.

Den alternativa vyn för parametern **View** måste använda tabell format; annars Miss lyckas kommandot. Om den alternativa vyn är en lista använder du `Format-List` . Om den alternativa vyn varken är en lista eller en tabell använder du format-Custom.

## RELATERADE LÄNKAR

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[Format-Custom](Format-Custom.md)

[Format-Hex](Format-Hex.md)

[Format-List](Format-List.md)

[Format-Table](Format-Table.md)
