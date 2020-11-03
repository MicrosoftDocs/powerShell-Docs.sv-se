---
description: Avslutar det aktuella omfånget, som kan vara en funktion, ett skript eller ett skript block.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_return?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Return
ms.openlocfilehash: c0c5b60163870e9352f0c3aa750d5603f29a81b1
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272457"
---
# <a name="about-return"></a>Om retur

## <a name="short-description"></a>Kort beskrivning

Avslutar det aktuella omfånget, som kan vara en funktion, ett skript eller ett skript block.

## <a name="long-description"></a>Lång beskrivning

`return`Nyckelordet avslutar en funktion, ett skript eller ett skript block. Den kan användas för att avsluta ett omfång vid en viss punkt, för att returnera ett värde, eller för att ange att slutet på omfattningen har uppnåtts.

Användare som är bekanta med språk som C eller C \# kan vilja använda `return` nyckelordet för att göra logiken att lämna ett explicit område.

I PowerShell returneras resultatet av varje instruktion som utdata, även om det inte finns någon instruktion som innehåller nyckelordet Return. Språk som C eller C \# returnerar bara de värden eller värden som anges av `return` nyckelordet.

> [!NOTE]
> Från och med PowerShell 5,0 har PowerShell använt språk för att definiera klasser med hjälp av formell syntax.  I kontexten för en PowerShell-klass är inget utdata från en metod, förutom vad du anger med hjälp av en `return` instruktion. Du kan läsa mer om PowerShell-klasser i [about_Classes](about_Classes.md).

### <a name="syntax"></a>Syntax

Syntaxen för `return` nyckelordet ser ut så här:

```
return [<expression>]
```

`return`Nyckelordet får endast visas eller följas av ett värde eller uttryck, enligt följande:

```powershell
return
return $a
return (2 + $a)
```

### <a name="examples"></a>Exempel

I följande exempel används `return` nyckelordet för att avsluta en funktion vid en viss punkt om ett villkor är uppfyllt. Udda tal multipliceras inte eftersom Return-instruktionen avslutas innan instruktionen kan köras.

```powershell
function MultiplyEven
{
    param($number)

    if ($number % 2) { return "$number is not even" }
    $number * 2
}

1..10 | ForEach-Object {MultiplyEven -Number $_}
```

```output
1 is not even
4
3 is not even
8
5 is not even
12
7 is not even
16
9 is not even
20
```

I PowerShell kan värden returneras även om `return` nyckelordet inte används.
Resultaten av varje instruktion returneras. Följande uttryck returnerar till exempel värdet för `$a` variabeln:

```powershell
$a
return
```

Följande instruktion returnerar även värdet för `$a` :

```powershell
return $a
```

I följande exempel finns en instruktion som är avsedd att ge användaren veta att funktionen utför en beräkning:

```powershell
function calculation {
    param ($value)

    "Please wait. Working on calculation..."
    $value += 73
    return $value
}

$a = calculation 14
```

"Vänta. Arbetar med beräkning... " strängen visas inte. I stället tilldelas den `$a` variabeln, som i följande exempel:

```
PS> $a
Please wait. Working on calculation...
87
```

Både den informations sträng och resultatet av beräkningen returneras av funktionen och tilldelas till `$a` variabeln.

Om du vill visa ett meddelande i din funktion, från och med PowerShell 5,0, kan du använda `Information` data strömmen. I koden nedan korrigeras exemplet ovan med hjälp av `Write-Information` cmdleten med en `InformationAction` av **Continue**.

```powershell
function calculation {
    param ($value)

    Write-Information "Please wait. Working on calculation..." -InformationAction Continue
    $value += 73
    return $value
}

$a = calculation 14
```

```output
Please wait. Working on calculation...
C:\PS> $a
87
```

### <a name="return-values-and-the-pipeline"></a>Retur värden och pipelinen

När du returnerar en samling från skript blocket eller funktionen, avregistrerar PowerShell automatiskt medlemmarna och skickar dem en i taget via pipelinen. Detta beror på PowerShell: s en-vid-tidpunkt-bearbetning. Mer information finns i [about_pipelines](about_pipelines.md).

Det här konceptet illustreras med följande exempel funktion som returnerar en matris med tal. Utdata från funktionen är skickas till `Measure-Object` cmdleten som räknar antalet objekt i pipelinen.

```powershell
function Test-Return
{
    $array = 1,2,3
    return $array
}
Test-Return | Measure-Object
```

```Output
Count    : 3
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```

Använd någon av följande två metoder om du vill tvinga ett skript block eller en funktion att returnera samling som ett enda objekt till pipelinen:

- Uttryck för unär mat ris

  Genom att använda ett enställt uttryck kan du skicka ditt retur värde nedåt i pipeline som ett enda objekt som illustreras i följande exempel.

  ```powershell
  function Test-Return
  {
      $array = 1,2,3
      return (, $array)
  }
  Test-Return | Measure-Object
  ```

  ```Output
  Count    : 1
  Average  :
  Sum      :
  Maximum  :
  Minimum  :
  Property :
  ```

- `Write-Output` med **noenumeration** parameter.

  Du kan också använda `Write-Output` cmdlet: en med **noenumeration** -parametern. Exemplet nedan använder `Measure-Object` cmdleten för att räkna de objekt som skickas till pipelinen från exempel funktionen med hjälp av `return` nyckelordet.

  ```powershell
  function Test-Return
  {
      $array = 1, 2, 3
      return Write-Output -NoEnumerate $array
  }

  Test-Return | Measure-Object
  ```

  ```Output
  Count    : 1
  Average  :
  Sum      :
  Maximum  :
  Minimum  :
  Property :
  ```

## <a name="see-also"></a>Se även

[about_Language_Keywords](about_Language_Keywords.md)

[about_Functions](about_Functions.md)

[about_Scopes](about_Scopes.md)

[about_Classes](about_Classes.md)

[Skriv information](xref:Microsoft.PowerShell.Utility.Write-Information)

[about_Script_Blocks](about_Script_Blocks.md)

