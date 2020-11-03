---
description: Beskriver de operatorer som fungerar med Microsoft .NET typer.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/15/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_type_operators?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Type_Operators
ms.openlocfilehash: 807b99175463b930177f293eaf6c2fd8cc5bc224
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2020
ms.locfileid: "93272853"
---
# <a name="about-type-operators"></a>Om typ operatorer

## <a name="short-description"></a>KORT BESKRIVNING
Beskriver de operatorer som fungerar med Microsoft .NET typer.

## <a name="long-description"></a>LÅNG BESKRIVNING

Operatorerna boolesk typ ( `-is` och `-isNot` ) avgör om ett objekt är en instans av en angiven .net-typ. `-is`Operatorn returnerar värdet **True** om typen matchar och värdet **false** annars. `-isNot`Operatorn returnerar värdet **false** om typen matchar och värdet **True** annars.

`-as`Operatorn försöker konvertera indatamängden till den angivna .net-typen. Om det lyckas returneras det konverterade objektet. Om det Miss lyckas returneras `$null` . Det returnerar inget fel.

I följande tabell visas typ operatorerna i PowerShell.

|Operator|Beskrivning                |Exempel                          |
|--------|---------------------------|---------------------------------|
|`-is`   |Returnerar sant när indatamängden|`(get-date) -is [DateTime]`      |
|        |är en instans av      |`True`                           |
|        |angiven .NET-typ.       |                                 |
|`-isNot`|Returnerar sant när indatamängden|`(get-date) -isNot [DateTime]`   |
|        |inte en instans av     |`False`                          |
|        |specified.NET-typ.        |                                 |
|`-as`   |Konverterar indatamängden till  |`"5/7/07" -as [DateTime]`        |
|        |angiven .NET-typ.       |`Monday, May 7, 2007 12:00:00 AM`|

Syntaxen för typ operatörerna är följande:

```powershell
<input> <operator> [.NET type]
```

Du kan också använda följande syntax:

```powershell
<input> <operator> ".NET type"
```

.NET-typen kan skrivas som ett typnamn inom hakparenteser eller en sträng, till exempel `[DateTime]` eller `"DateTime"` för **system. DateTime**. Om typen inte finns i roten för system namn området anger du det fullständiga namnet på objekt typen. Du kan utelämna "system.". Om du till exempel vill ange **system. Diagnostics. process** , anger du, `[System.Diagnostics.Process]` `[Diagnostics.Process]` eller `"Diagnostics.Process"` .

Typ operatörerna används alltid som indatamängds objekt som helhet. Det vill säga om inobjektet är en samling, är det den _samlings_ typ som testas, inte typerna för samlingens _element_.

### <a name="-isisnot-operators"></a>– är/isNot-ansvariga

Operatorerna **boolesk** typ ( `-is` och `-isNot` ) returnerar alltid ett **booleskt** värde, även om indatatypen är en samling objekt.

Om `<input>` är en typ som är samma som eller _härleds_ från .net-typen `-is` returneras operatorn `$True` .

Till exempel härleds **DirectoryInfo** -typen från **FileSystemInfo** -typen. Därför returnerar båda dessa exempel **Sant**.

```powershell
PS> (Get-Item /) -is [System.IO.DirectoryInfo]
True
PS> (Get-Item /) -is [System.IO.FileSystemInfo]
True
```

`-is`Operatören kan också matcha gränssnitt om det `<input>` implementerar gränssnittet i jämförelsen. I det här exemplet är indatamängden en matris. Matriser implementerar gränssnittet **system. Collections. ilist** .

```powershell
PS> 1, 2 -is [System.Collections.IList]
True
```

### <a name="-as-operator"></a>-as-operator

`-as`Operatorn försöker konvertera indatamängden till den angivna .net-typen. Om det lyckas returneras det konverterade objektet. Om det Miss lyckas returneras det `$null` . Det returnerar inget fel.

Om `<input>` är en typ som _härleds_ från .net-typen `-as` _skickas genom_ returnerat indatamängds objekt oförändrad. Till exempel härleds **DirectoryInfo** -typen från **FileSystemInfo** -typen. Objekt typen är därför oförändrad i följande exempel:

```powershell
PS> $fsroot = (Get-Item /) -as [System.IO.FileSystemInfo]
PS> $fsroot.GetType().FullName
System.IO.DirectoryInfo
```

#### <a name="converting-the-datetime-type-is-culture-sensitive"></a>Konvertering av DateTime-typen är kultur känslig

Till skillnad från typ data typs byte fungerar konverteringen till `[DateTime]` typ med `-as` operatorn endast med strängar som är formaterade enligt reglerna för den aktuella kulturen.

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr-FR'
PS> '13/5/20' -as [datetime]

mercredi 13 mai 2020 00:00:00

PS> '05/13/20' -as [datetime]
PS> [datetime]'05/13/20'

mercredi 13 mai 2020 00:00:00

PS> [datetime]'13/05/20'
InvalidArgument: Cannot convert value "13/05/20" to type "System.DateTime".
Error: "String '13/05/20' was not recognized as a valid DateTime."
```

Använd cmdleten för att hitta .NET-typen för ett objekt `Get-Member` . Du kan också använda **gettype** -metoden för alla objekt tillsammans med egenskapen **FullName** för den här metoden. Följande uttryck hämtar t. ex. typen av retur värde för ett `Get-Culture` kommando:

```powershell
PS> (Get-Culture).GetType().FullName
System.Globalization.CultureInfo
```

## <a name="examples"></a>EXEMPEL

I följande exempel visas några användnings områden av typen operatorer:

```powershell
PS> 32 -is [Float]
False

PS> 32 -is "int"
True

PS> (get-date) -is [DateTime]
True

PS> "12/31/2007" -is [DateTime]
False

PS> "12/31/2007" -is [String]
True

PS> (get-process PowerShell)[0] -is [System.Diagnostics.Process]
True

PS> (get-command get-member) -is [System.Management.Automation.CmdletInfo]
True
```

I följande exempel visas att när indatatypen är en samling objekt, är den matchande typen .NET-typen för samlingen, inte typen för de enskilda objekten i samlingen.

I det här exemplet, även om `Get-Culture` både `Get-UICulture` cmdletarna och returnerar **system. globalisering. CultureInfo** -objekt, är en samling av dessa objekt en system. Object-matris.

```powershell
PS> (get-culture) -is [System.Globalization.CultureInfo]
True

PS> (get-uiculture) -is [System.Globalization.CultureInfo]
True

PS> (get-culture), (get-uiculture) -is [System.Globalization.CultureInfo]
False

PS> (get-culture), (get-uiculture) -is [Array]
True

PS> (get-culture), (get-uiculture) | foreach {
  $_ -is [System.Globalization.CultureInfo])
}
True
True

PS> (get-culture), (get-uiculture) -is [Object]
True
```

I följande exempel visas hur du använder `-as` operatorn.

```powershell
PS> "12/31/07" -is [DateTime]
False

PS> "12/31/07" -as [DateTime]
Monday, December 31, 2007 12:00:00 AM

PS> $date = "12/31/07" -as [DateTime]

C:\PS>$a -is [DateTime]
True

PS> 1031 -as [System.Globalization.CultureInfo]

LCID      Name      DisplayName
----      ----      -----------
1031      de-DE     German (Germany)
```

Följande exempel visar att när `-as` operatorn inte kan konvertera inobjektet till .net-typen returneras `$null` .

```powershell
PS> 1031 -as [System.Diagnostics.Process]
PS>
```

## <a name="see-also"></a>SE ÄVEN

[about_Operators](about_Operators.md)
