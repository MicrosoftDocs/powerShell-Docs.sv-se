---
description: Beskriver hur du använder ihopbuntning för att skicka parametrar till kommandon i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_splatting?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Splatting
ms.openlocfilehash: 0cf9702adcc7d19a19d9aaa9673fb42e3af715fa
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271953"
---
# <a name="about-splatting"></a>Om Ihopbuntning

## <a name="short-description"></a>Kort beskrivning

Beskriver hur du använder ihopbuntning för att skicka parametrar till kommandon i PowerShell.

## <a name="long-description"></a>Lång beskrivning

Ihopbuntning är en metod för att skicka en samling parameter värden till ett kommando som en enhet. PowerShell kopplar varje värde i samlingen med en kommando parameter. Splatted parameter värden lagras i namngivna ihopbuntning-variabler, som ser ut som standardvariabler, men börjar med en symbol ( `@` ) i stället för ett dollar tecken ( `$` ). Vid-symbolen visas PowerShell att du skickar en samling värden i stället för ett enda värde.

Ihopbuntning gör kommandona kortare och lättare att läsa. Du kan återanvända ihopbuntning-värden i olika kommando anrop och använda ihopbuntning för att skicka parameter värden från den `$PSBoundParameters` automatiska variabeln till andra skript och funktioner.

Från och med Windows PowerShell 3,0 kan du också använda ihopbuntning för att representera alla parametrar för ett kommando.

## <a name="syntax"></a>Syntax

```
<CommandName> <optional parameters> @<HashTable> <optional parameters>
<CommandName> <optional parameters> @<Array> <optional parameters>
```

Använd mat ris syntaxen för att ange parameter värden för positions parametrar, där parameter namn inte krävs. Använd syntaxen för hash-tabellen för att ange parameter namn och värdepar. Splatted-värdet kan finnas var som helst i parameter listan.

När ihopbuntning inte behöver använda en hash-tabell eller en matris för att skicka alla parametrar. Du kan skicka vissa parametrar genom att använda ihopbuntning och skicka andra efter position eller parameter namn. Du kan också splat flera objekt i ett enda kommando så att du inte skickar fler än ett värde för varje parameter.

## <a name="splatting-with-hash-tables"></a>Ihopbuntning med hash-tabeller

Använd en hash-tabell för att splat parameter namn och värdepar. Du kan använda det här formatet för alla parameter typer, inklusive parametrar för position och växling.
Positions parametrar måste tilldelas med namn.

I följande exempel jämförs två `Copy-Item` kommandon som kopierar Test.txt-filen till Test2.txt-filen i samma katalog.

I det första exemplet används det traditionella formatet där parameter namn ingår.

```powershell
Copy-Item -Path "test.txt" -Destination "test2.txt" -WhatIf
```

I det andra exemplet används hash-tabellens ihopbuntning. Det första kommandot skapar en hash-tabell med parameter namn och parameter-värdepar och lagrar den i `$HashArguments` variabeln. Det andra kommandot använder `$HashArguments` variabeln i ett kommando med ihopbuntning. Symbolen vid ( `@HashArguments` ) ersätter dollar tecknet ( `$HashArguments` ) i kommandot.

Använd eller om du vill ange **WhatIf** ett värde för parametern whatIf `$True` switch `$False` .

```powershell
$HashArguments = @{
  Path = "test.txt"
  Destination = "test2.txt"
  WhatIf = $true
}
Copy-Item @HashArguments
```

> [!NOTE]
> I det första kommandot indikerar symbolen ( `@` ) en hash-tabell, inte ett splatted-värde. Syntaxen för hash-tabeller i PowerShell är: `@{<name>=<value>; <name>=<value>; ...}`

## <a name="splatting-with-arrays"></a>Ihopbuntning med matriser

Använd en matris för att splat värden för positions parametrar, vilket inte kräver parameter namn. Värdena måste vara i positions nummer ordningen i matrisen.

I följande exempel jämförs två `Copy-Item` kommandon som kopierar Test.txt-filen till Test2.txt-filen i samma katalog.

I det första exemplet används det traditionella formatet där parameter namn utelämnas. Parameter värden visas i positions ordning i kommandot.

```powershell
Copy-Item "test.txt" "test2.txt" -WhatIf
```

I det andra exemplet används matrisen ihopbuntning. Det första kommandot skapar en matris med parameter värden och lagrar den i `$ArrayArguments` variabeln. Värdena är i positions ordning i matrisen. Det andra kommandot använder `$ArrayArguments` variabeln i ett kommando i ihopbuntning. Symbolen vid ( `@ArrayArguments` ) ersätter dollar tecknet ( `$ArrayArguments` ) i kommandot.

```powershell
$ArrayArguments = "test.txt", "test2.txt"
Copy-Item @ArrayArguments -WhatIf
```

### <a name="using-the-argumentlist-parameter"></a>Använda parametern argument List

Flera cmdlets har en **argument List** -parameter som används för att skicka parameter värden till ett skript block som körs av cmdleten. Parametern **argument List** tar en matris med värden som skickas till-skript blocket. PowerShell använder i själva verket matris-ihopbuntning för att binda värdena till parametrarna i skript blocket. Om du behöver skicka en matris som ett enda objekt som är kopplat till en enskild parameter när du använder **argument List** måste du figursätta matrisen som det enda elementet i en annan matris.

I följande exempel finns ett skript block som använder en enda parameter som är en sträng mat ris.

```powershell
$array = 'Hello', 'World!'
Invoke-Command -ScriptBlock {
  param([string[]]$words) $words -join ' '
  } -ArgumentList $array
```

I det här exemplet skickas endast det första objektet i `$array` till-skript blocket.
```Output
Hello
```

```powershell
$array = 'Hello', 'World!'
Invoke-Command -ScriptBlock {
  param([string[]]$words) $words -join ' '
  } -ArgumentList (,$array)
```

I det här exemplet `$array` är omslutna i en matris så att hela matrisen skickas till-skript blocket som ett enda objekt.

```Output
Hello World!
```

## <a name="examples"></a>Exempel

Det här exemplet visar hur du återanvänder splatted-värden i olika kommandon. Kommandona i det här exemplet använder `Write-Host` cmdleten för att skriva meddelanden till värd program konsolen. Den använder ihopbuntning för att ange förgrunds-och bakgrunds färger.

Ändra värdet för variabeln om du vill ändra färgerna på alla kommandon `$Colors` .

Det första kommandot skapar en hash-tabell med parameter namn och värden och lagrar hash-tabellen i `$Colors` variabeln.

```powershell
$Colors = @{ForegroundColor = "black"; BackgroundColor = "white"}
```

Det andra och tredje kommandot använder `$Colors` variabeln för ihopbuntning i ett `Write-Host` kommando. Om du vill använda `$Colors variable` ersätter du dollar tecknet ( `$Colors` ) med en symbol ( `@Colors` ).

```powershell
#Write a message with the colors in $Colors
Write-Host "This is a test." @Colors

#Write second message with same colors. The position of splatted
#hash table does not matter.
Write-Host @Colors "This is another test."
```

Det här exemplet visar hur du vidarebefordrar sina parametrar till andra kommandon med hjälp av ihopbuntning och den `$PSBoundParameters` automatiska variabeln.

Den `$PSBoundParameters` automatiska variabeln är ett Dictionary-objekt (system. Collections. Generic. Dictionary) som innehåller alla parameter namn och värden som används när ett skript eller en funktion körs.

I följande exempel använder vi `$PSBoundParameters` variabeln för att vidarebefordra parameter värden som skickas till ett skript eller en funktion från `Test2` funktion till `Test1` funktionen. Båda anropen till `Test1` funktionen från `Test2` använder ihopbuntning.

```powershell
function Test1
{
    param($a, $b, $c)

    $a
    $b
    $c
}

function Test2
{
    param($a, $b, $c)

    #Call the Test1 function with $a, $b, and $c.
    Test1 @PsBoundParameters

    #Call the Test1 function with $b and $c, but not with $a
    $LimitedParameters = $PSBoundParameters
    $LimitedParameters.Remove("a") | Out-Null
    Test1 @LimitedParameters
}
```

```Output
Test2 -a 1 -b 2 -c 3
1
2
3
2
3
```

## <a name="splatting-command-parameters"></a>Ihopbuntning kommando parametrar

Du kan använda ihopbuntning för att representera parametrarna för ett kommando. Den här metoden är användbar när du skapar en proxy-funktion, det vill säga en funktion som anropar ett annat kommando. Den här funktionen introduceras i Windows PowerShell 3,0.

Om du vill splat parametrar för ett kommando använder `@Args` du för att representera kommando parametrarna. Den här metoden är enklare än att räkna upp kommando parametrar och det fungerar utan att göra ändringar även om parametrarna för den anropade kommando ändringen.

Funktionen använder den `$Args` automatiska variabeln som innehåller alla otilldelade parameter värden.

Följande funktion anropar exempelvis `Get-Process` cmdleten. I den här funktionen `@Args` representerar alla parametrar för `Get-Process` cmdleten.

```powershell
function Get-MyProcess { Get-Process @Args }
```

När du använder `Get-MyProcess` funktionen skickas alla otilldelade parametrar och parameter värden till `@Args` , som du ser i följande kommandon.

```powershell
Get-MyProcess -Name PowerShell
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    463      46   225484     237196   719    15.86   3228 powershell
```

```powershell
Get-MyProcess -Name PowerShell_Ise -FileVersionInfo
```

```Output
ProductVersion   FileVersion      FileName
--------------   -----------      --------
6.2.9200.16384   6.2.9200.1638... C:\Windows\system32\WindowsPowerShell\...
```

Du kan använda `@Args` i en funktion som har explicit deklarerade parametrar. Du kan använda det mer än en gång i en funktion, men alla parametrar som du anger skickas till alla instanser av `@Args` , som du ser i följande exempel.

```powershell
function Get-MyCommand
{
    Param ([switch]$P, [switch]$C)
    if ($P) { Get-Process @Args }
    if ($C) { Get-Command @Args }
}

Get-MyCommand -P -C -Name PowerShell
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
408      28    75568      83176   620     1.33   1692 powershell

Path               : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.e
Extension          : .exe
Definition         : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.e
Visibility         : Public
OutputType         : {System.String}
Name               : powershell.exe
CommandType        : Application
ModuleName         :
Module             :
RemotingCapability : PowerShell
Parameters         :
ParameterSets      :
HelpUri            :
FileVersionInfo    : File:             C:\Windows\System32\WindowsPowerShell
                     \v1.0\powershell.exe
                     InternalName:     POWERSHELL
                     OriginalFilename: PowerShell.EXE.MUI
                     FileVersion:      10.0.14393.0 (rs1_release.160715-1616
                     FileDescription:  Windows PowerShell
                     Product:          Microsoft Windows Operating System
                     ProductVersion:   10.0.14393.0
                     Debug:            False
                     Patched:          False
                     PreRelease:       False
                     PrivateBuild:     False
                     SpecialBuild:     False
                     Language:         English (United States)
```

## <a name="notes"></a>Kommentarer

Om du gör en funktion i en avancerad funktion med antingen **CmdletBinding** -eller- **parametervärdena** är den `$args` automatiska variabeln inte längre tillgänglig i funktionen. Avancerade funktioner kräver explicit parameter definition.

PowerShell Desired State Configuration (DSC) har inte utformats för att använda ihopbuntning.
Du kan inte använda ihopbuntning för att skicka värden till en DSC-resurs. Mer information finns i artikeln [pseudo-IHOPBUNTNING DSC-resurser](https://gaelcolas.com/2017/11/05/pseudo-splatting-dsc-resources/)för Gael-Colas.

## <a name="see-also"></a>Se även

[about_Arrays](about_Arrays.md)

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Hash_Tables](about_Hash_Tables.md)

[about_Parameters](about_Parameters.md)
