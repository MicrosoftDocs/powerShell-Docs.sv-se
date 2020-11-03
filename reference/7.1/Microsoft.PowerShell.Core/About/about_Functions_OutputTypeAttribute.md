---
description: Beskriver ett attribut som rapporterar den typ av objekt som funktionen returnerar.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_outputtypeattribute?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_OutputTypeAttribute
ms.openlocfilehash: 7cd7f04941077d823bb15d0fa393ca241f38ae3b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93269876"
---
# <a name="about-functions-outputtypeattribute"></a>Om functions-OutputTypeAttribute

## <a name="short-description"></a>KORT BESKRIVNING
Beskriver ett attribut som rapporterar den typ av objekt som funktionen returnerar.

## <a name="long-description"></a>LÅNG BESKRIVNING

Attributet OutputType visar de .NET-typer av objekt som funktionerna returnerar. Du kan använda en valfri ParameterSetName-parameter för att lista olika utdatatyper för varje parameter uppsättning.

Attributet OutputType stöds i enkla och avancerade funktioner. Den är oberoende av CmdletBinding-attributet.

Attributet OutputType tillhandahåller värdet för egenskapen OutputType för objektet **system. Management. Automation. FunctionInfo** som `Get-Command` cmdleten returnerar.

Värdet för OutputType-attributet är bara en dokumentations anteckning. Den härleds inte från funktions koden eller jämförs med den faktiska funktionens utdata. Därför kan värdet vara felaktigt.

## <a name="syntax"></a>SYNTAX

Attributet OutputType för functions har följande syntax:

```
[OutputType([<TypeLiteral>], ParameterSetName="<Name>")]
[OutputType("<TypeNameString>", ParameterSetName="<Name>")]
```

Parametern **ParameterSetName** är valfri.

Du kan visa flera typer i attributet OutputType.

```
[OutputType([<Type1>],[<Type2>],[<Type3>])]
```

Du kan använda parametern **ParameterSetName** för att ange att olika parameter uppsättningar returnerar olika typer.

```
[OutputType([<Type1>], ParameterSetName=("<Set1>","<Set2>"))]
[OutputType([<Type2>], ParameterSetName="<Set3>")]
```

Placera instruktionerna för OutputType-attribut i listan attribut som föregår `Param` instruktionen.

I följande exempel visas placeringen av OutputType-attributet i en enkel funktion.

```powershell
function SimpleFunction2
{
  [OutputType([<Type>])]
  Param ($Parameter1)

  <function body>
}
```

I följande exempel visas placeringen av attributet OutputType i avancerade funktioner.

```powershell
function AdvancedFunction1
{
  [OutputType([<Type>])]
  Param (
    [parameter(Mandatory=$true)]
    [String[]]
    $Parameter1
  )

  <function body>
}

function AdvancedFunction2
{
  [CmdletBinding(SupportsShouldProcess=<Boolean>)]
  [OutputType([<Type>])]
  Param (
    [parameter(Mandatory=$true)]
    [String[]]
    $Parameter1
  )

  <function body>
}
```

## <a name="examples"></a>EXEMPEL

### <a name="example-1-create-a-function-that-has-the-outputtype-of-string"></a>Exempel 1: skapa en funktion som har en strängs OutputType

```powershell
function Send-Greeting
{
  [OutputType([String])]
  Param ($Name)

  "Hello, $Name"
}
```

Använd cmdleten om du vill se den resulterande utdatatyps egenskapen `Get-Command` .

```powershell
(Get-Command Send-Greeting).OutputType
```

```Output
Name                                               Type
----                                               ----
System.String                                      System.String
```

### <a name="example-2-use-the-output-attribute-to-indicate-dynamic-output-types"></a>Exempel 2: Använd attributet output för att ange dynamiska typer av utdata

Följande avancerade funktion använder attributet OutputType för att indikera att funktionen returnerar olika typer beroende på den parameter uppsättning som används i kommandot funktion.

```powershell
function Get-User
{
  [CmdletBinding(DefaultParameterSetName="ID")]

  [OutputType("System.Int32", ParameterSetName="ID")]
  [OutputType([String], ParameterSetName="Name")]

  Param (
    [parameter(Mandatory=$true, ParameterSetName="ID")]
    [Int[]]
    $UserID,

    [parameter(Mandatory=$true, ParameterSetName="Name")]
    [String[]]
    $UserName
  )

  <function body>
}
```

### <a name="example-3-shows-when-an-actual-output-differs-from-the-outputtype"></a>Exempel 3: visar när en faktisk utmatning skiljer sig från OutputType

Följande exempel visar att värdet för egenskapen OutputType visas i värdet för egenskapen OutputType, även om det är felaktigt.

`Get-Time`Funktionen returnerar en sträng som innehåller kort formen av tiden i alla DateTime-objekt. Men attributet OutputType rapporterar att det returnerar ett **system. DateTime** -objekt.

```powershell
function Get-Time
{
  [OutputType([DateTime])]
  Param (
    [parameter(Mandatory=$true)]
    [Datetime]$DateTime
  )

  $DateTime.ToShortTimeString()
}
```

`GetType()`Metoden bekräftar att funktionen returnerar en sträng.

```powershell
(Get-Time -DateTime (Get-Date)).GetType().FullName
```

```Output
System.String
```

Men egenskapen OutputType, som hämtar värdet från attributet OutputType, rapporterar att funktionen returnerar ett **datetime** -objekt.

```powershell
(Get-Command Get-Time).OutputType
```

```Output
Name                                      Type
----                                      ----
System.DateTime                           System.DateTime
```

### <a name="example-4-a-function--that-shouldnt-have-output"></a>Exempel 4: en funktion som inte har utdata

I följande exempel visas en anpassad funktion som ska utföras och åtgärdas, men som inte returnerar något.

```powershell
function Invoke-Notepad
{
  [OutputType([System.Void])]
  Param ()
  & notepad.exe | Out-Null
}
```

## <a name="notes"></a>ANTECKNINGAR

Värdet för egenskapen OutputType för ett **FunctionInfo** -objekt är en matris med **system. Management. Automation. PSTypeName** -objekt, som var och en har namn och typ egenskaper.

Om du bara vill hämta namnet på varje Utdatatyp använder du kommandot med följande format.

```powershell
(Get-Command Get-Time).OutputType | ForEach {$_.Name}
```

Värdet för egenskapen OutputType kan vara null. Använd ett null-värde när utdata inte är en .NET-typ, till exempel ett **WMI-** objekt eller en formaterad vy av ett objekt.

## <a name="see-also"></a>SE ÄVEN

[about_Functions](about_Functions.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

