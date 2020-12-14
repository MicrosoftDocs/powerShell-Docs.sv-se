---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-custom?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Custom
ms.openlocfilehash: ff4b2dda3f12fa34fc518c6a180f3213ba873d90
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708677"
---
# Format-Custom

## SAMMANFATTNING
Använder en anpassad vy för att formatera utdata.

## SYNTAX

```
Format-Custom [[-Property] <Object[]>] [-Depth <Int32>] [-GroupBy <Object>] [-View <String>]
 [-ShowError] [-DisplayError] [-Force] [-Expand <String>] [-InputObject <PSObject>]
 [<CommonParameters>]
```

## BESKRIVNING

`Format-Custom`Cmdleten formaterar utdata från ett kommando som definieras i en annan vy.
`Format-Custom` är utformat för att Visa vyer som inte är bara tabeller eller bara listor. Du kan använda de vyer som definierats i PowerShell, eller så kan du skapa egna vyer i en ny `format.ps1xml` fil och använda `Update-FormatData` cmdleten för att lägga till dem i PowerShell.

## EXEMPEL

### Exempel 1: formatera utdata med en anpassad vy

```powershell
Get-Command Start-Transcript | Format-Custom -View MyView
```

Det här kommandot formaterar information om `Start-Transcript` cmdleten i det format som definieras av vyn visnings alternativ, en anpassad vy som skapats av användaren. För att kunna köra det här kommandot måste du först skapa en ny PS1XML-fil, **definiera vyn vy** och sedan använda `Update-FormatData` kommandot för att lägga till PS1XML-filen till PowerShell.

### Exempel 2: formatera utdata med standardvyn

```powershell
Get-Process Winlogon | Format-Custom
```

Det här kommandot formaterar information om **Winlogon** -processen i en alternativ anpassad vy.
Eftersom kommandot inte använder parametern **View** `Format-Custom` används en anpassad standardvy för att formatera data.

### Exempel 3: Felsöka format fel

I följande exempel visas resultatet av att lägga till **DisplayError** -eller **ShowError** -parametrarna med ett uttryck.

```powershell
PC /> Get-Date | Format-Custom DayOfWeek,{ $_ / $null } -DisplayError

class DateTime
{
  DayOfWeek = Friday
   $_ / $null  = #ERR
}


PC /> Get-Date | Format-Custom DayOfWeek,{ $_ / $null } -ShowError

class DateTime
{
  DayOfWeek = Friday
   $_ / $null  =
}

Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 8:01:04 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## PARAMETRAR

### -Djup

Anger antalet kolumner i visningen.

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

Visar fel på kommando raden. Den här parametern används sällan, men kan användas som ett fel söknings stöd när du formaterar uttryck i ett `Format-Custom` kommando, och uttrycken verkar inte fungera.

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

Formaterar samlings objekt och objekt i samlingen. Den här parametern är utformad för att formatera objekt som har stöd för **system. Collections. ICollection** -gränssnittet. Standardvärdet är **EnumOnly**.

Giltiga värden är:

- EnumOnly: visar egenskaperna för objekten i samlingen.
- CoreOnly: visar egenskaperna för objektet samling.
- Båda: visar egenskaperna för samlingsobjektet och objekten i samlingen.

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

Instruerar cmdleten att visa all information om felet. Används med parametrarna **DisplayError** eller **ShowError** . Som standard visas endast en del fel information när ett fel objekt skrivs till fel-eller visnings strömmar.

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

Om du utelämnar den här parametern beror egenskaperna som visas i vyn på det objekt som visas. **Egenskapen** parameter namn är valfri. Du kan inte använda **egenskapen** och **Visa** parametrar i samma kommando.

Värdet för **egenskaps** parametern kan vara en ny beräknad egenskap. Den beräknade egenskapen kan vara ett skript block eller en hash-tabell. Giltiga nyckel/värde-par är:

- Uttryck- `<string>` eller `<script block>`
- Djuplodande `<int32>`

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

Skickar fel via pipelinen. Den här parametern används sällan, men kan användas som ett fel söknings stöd när du formaterar uttryck i ett `Format-Custom` kommando, och uttrycken verkar inte fungera.

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

Anger namnet på ett alternativt format eller en annan vy. Om du utelämnar den här parametern `Format-Custom` används en anpassad standardvy. Du kan inte använda **egenskapen** och **Visa** parametrar i samma kommando.

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

Du kan skicka vidare alla objekt till `Format-Custom` .

## UTDATA

### Microsoft. PowerShell. commands. Internal. format

`Format-Custom` Returnerar de format objekt som representerar visningen.

## ANTECKNINGAR

`Format-Custom` är utformat för att Visa vyer som inte är bara tabeller eller bara listor. Om du vill visa en alternativ tabellvy använder du `Format-Table` . Om du vill visa en annan listvy använder du `Format-List` .

Du kan också referera till `Format-Custom` med dess inbyggda alias `fc` . Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).

Parametern **groupby** förutsätter att objekten sorteras. `Format-Custom`Använd för att sortera objekten innan du använder dem för att gruppera objekten `Sort-Object` .

## RELATERADE LÄNKAR

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[Format-Hex](Format-Hex.md)

[Format-List](Format-List.md)

[Format-Table](Format-Table.md)

[Format-Wide](Format-Wide.md)

[Hämta process](../Microsoft.PowerShell.Management/Get-Process.md)
