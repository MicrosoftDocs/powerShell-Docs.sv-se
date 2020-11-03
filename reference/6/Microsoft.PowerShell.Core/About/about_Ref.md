---
description: Beskriver hur du skapar och använder en variabel av typen referens. Du kan använda variabler för referens typ för att tillåta en funktion att ändra värdet för en variabel som skickas till den.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/24/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_ref?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Ref
ms.openlocfilehash: fefc0f002db0b9591b2d23e148db381f7413871f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270518"
---
# <a name="about-ref"></a>Om Ref

## <a name="short-description"></a>Kort beskrivning
Beskriver hur du skapar och använder en variabel av typen referens. Du kan använda variabler för referens typ för att tillåta en funktion att ändra värdet för en variabel som skickas till den.

## <a name="long-description"></a>Lång beskrivning

Du kan skicka variabler till funktioner *efter referens* eller *värde*.

När du skickar en variabel *efter värde* skickar du en kopia av data.

I följande exempel ändrar funktionen värdet för variabeln som skickas till den. I PowerShell är heltal värde typer, så de skickas med värdet.
Värdet för `$var` är därför oförändrat utanför omfånget för funktionen.

```powershell
Function Test($data)
{
    $data = 3
}

$var = 10
Test -data $var
$var
```

```output
10
```

I följande exempel skickas en variabel som innehåller en `Hashtable` funktion till en funktion. `Hashtable` är en objekt typ som standard skickas den till funktionen *efter referens*.

När en variabel skickas *efter referens* kan funktionen ändra data och ändringen fortsätter när funktionen har körts.

```powershell
Function Test($data)
{
    $data.Test = "New Text"
}

$var = @{}
Test -data $var
$var
```

```output
Name                           Value
----                           -----
Test                           New Text
```

Funktionen lägger till ett nytt nyckel/värde-par som finns kvar utanför funktionens omfång.

### <a name="writing-functions-to-accept-reference-parameters"></a>Skriva funktioner för att acceptera referens parametrar

Du kan koda dina funktioner för att ta en parameter som en referens, oavsett vilken typ av data som skickas. Detta kräver att du anger parametrarna typ som `System.Management.Automation.PSReference` eller `[ref]` .

När du använder referenser måste du använda `Value` egenskap av `System.Management.Automation.PSReference` typ för att komma åt dina data.

```powershell
Function Test([ref]$data)
{
    $data.Value = 3
}
```

Om du vill skicka en variabel till en parameter som förväntar sig en referens måste du skriva omvandla variabeln som en referens.

> [!NOTE]
> Hakparenteser och parenteser är båda obligatoriska.

```powershell
$var = 10
Test -data ([ref]$var)
$var
```

```output
3
```

### <a name="passing-references-to-net-methods"></a>Skicka referenser till .NET-metoder

Vissa .NET-metoder kan kräva att du skickar en variabel som referens. När metodens definition använder nyckelorden `in` , `out` eller `ref` på en parameter, förväntas en referens.

```powershell
[int] | Get-Member -Static -Name TryParse
```

```output
Name     MemberType Definition
----     ---------- ----------
TryParse Method     static bool TryParse(string s, [ref] int result)
```

`TryParse`Metoden försöker parsa en sträng som ett heltal. Om metoden lyckas returneras `$true` och resultatet lagras i variabeln som du skickade **med referens**.

```
PS> $number = 0
PS> [int]::TryParse("15", ([ref]$number))
True
PS> $number
15
```

### <a name="references-and-scopes"></a>Referenser och omfattningar

Referenser tillåter att värdet för en variabel i det överordnade omfånget ändras inom ett underordnat omfång.

```powershell
# Create a value type variable.
$i = 0
# Create a reference type variable.
$iRef = [ref]0
# Invoke a scriptblock to attempt to change both values.
&{$i++;$iRef.Value++}
# Output the results.
"`$i = $i;`$iRef = $($iRef.Value)"
```

```output
$i = 0;$iRef = 1
```

Endast variabeln av referens typen ändrades.

## <a name="see-also"></a>Se även

[about_Variables](about_Variables.md)

[about_Environment_Variables](about_Environment_Variables.md)

[about_Functions](about_Functions.md)

[about_Script_Blocks](about_Script_Blocks.md)

[about_Scopes](about_scopes.md)
