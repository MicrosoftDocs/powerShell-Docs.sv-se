---
description: Beskriver nyckelordet Throw, som genererar ett avslutande fel.
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_throw?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Throw
ms.openlocfilehash: e573722154fff99363b26806064ec17c8903bfd8
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194183"
---
# <a name="about-throw"></a>Om Throw

## <a name="short-description"></a>KORT BESKRIVNING

Beskriver nyckelordet Throw, som genererar ett avslutande fel.

## <a name="long-description"></a>LÅNG BESKRIVNING

Nyckelordet Throw orsakar ett avslutande fel. Du kan använda nyckelordet Throw för att stoppa bearbetningen av ett kommando, en funktion eller ett skript.

Du kan t. ex. använda nyckelordet Throw i skript blocket i en If-instruktion för att svara på ett villkor eller i det catch-blocket för en try-catch-finally-instruktion. Du kan också använda nyckelordet Throw i en parameter deklaration för att göra en funktions parameter obligatorisk.

Nyckelordet Throw kan utlösa alla objekt, t. ex. en användar meddelande sträng eller det objekt som orsakade felet.

## <a name="syntax"></a>SYNTAX

Syntaxen för nyckelordet Throw är följande:

```powershell
throw [<expression>]
```

Uttrycket i Throw-syntaxen är valfritt. När Throw-instruktionen inte visas i ett catch-block och den inte innehåller något uttryck, genererar det ett ScriptHalted-fel.

```powershell
C:\PS> throw

ScriptHalted
At line:1 char:6
+ throw <<<<
+ CategoryInfo          : OperationStopped: (:) [], RuntimeException
+ FullyQualifiedErrorId : ScriptHalted
```

Om nyckelordet Throw används i ett catch-block utan ett uttryck, utlöses den aktuella RuntimeException igen. Mer information finns i about_Try_Catch_Finally.

## <a name="throwing-a-string"></a>UTLÖSER EN STRÄNG

Det valfria uttrycket i en throw-instruktion kan vara en sträng, som du ser i följande exempel:

```powershell
C:\PS> throw "This is an error."

This is an error.
At line:1 char:6
+ throw <<<<  "This is an error."
+ CategoryInfo          : OperationStopped: (This is an error.:String) [], R
untimeException
+ FullyQualifiedErrorId : This is an error.
```

## <a name="throwing-other-objects"></a>ANDRA OBJEKT UTLÖSES

Uttrycket kan också vara ett objekt som utlöser objektet som representerar PowerShell-processen, vilket visas i följande exempel:

```powershell
C:\PS> throw (get-process PowerShell)

System.Diagnostics.Process (PowerShell)
At line:1 char:6
+ throw <<<<  (get-process PowerShell)
+ CategoryInfo          : OperationStopped: (System.Diagnostics.Process (Pow
erShell):Process) [],
RuntimeException
+ FullyQualifiedErrorId : System.Diagnostics.Process (PowerShell)
```

Du kan använda egenskapen TargetObject för objektet ErrorRecord i $error automatisk variabel för att undersöka felet.

```powershell
C:\PS> $error[0].targetobject

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
319      26    61016      70864   568     3.28   5548 PowerShell
```

Du kan också utlösa ett ErrorRecord-objekt eller ett undantag för Microsoft .NET Framework. I följande exempel används nyckelordet Throw för att utlösa ett system. FormatException-objekt.

```powershell
C:\PS> $formatError = new-object system.formatexception

C:\PS> throw $formatError

One of the identified items was in an invalid format.
At line:1 char:6
+ throw <<<<  $formatError
+ CategoryInfo          : OperationStopped: (:) [], FormatException
+ FullyQualifiedErrorId : One of the identified items was in an invalid
format.
```

## <a name="resulting-error"></a>RESULTERANDE FEL

Med nyckelordet Throw kan du generera ett ErrorRecord-objekt. Egenskapen Exception för ErrorRecord-objektet innehåller ett RuntimeException-objekt. Resten av ErrorRecord-objektet och RuntimeException-objektet varierar beroende på vilket objekt som nyckelordet Throw genererar.

RunTimeException-objektet är omslutet i ett ErrorRecord-objekt, och ErrorRecord-objektet sparas automatiskt i $Error automatiska variabeln.

## <a name="using-throw-to-create-a-mandatory-parameter"></a>ANVÄNDA THROW FÖR ATT SKAPA EN OBLIGATORISK PARAMETER

Du kan använda nyckelordet Throw för att göra en funktions parameter obligatorisk.

Detta är ett alternativ till att använda den obligatoriska parametern för parameterns nyckelord. När du använder den obligatoriska parametern, uppmanas användaren att ange det obligatoriska parametervärdet. När du använder nyckelordet Throw, stannar kommandot och felposten visas.

Till exempel gör nyckelordet Throw i parametern-under uttryck Sök vägs parametern till en obligatorisk parameter i funktionen.

I det här fallet genererar nyckelordet Throw en meddelande sträng, men det är förekomsten av nyckelordet Throw som genererar det avslutande felet om parametern Path inte anges. Det uttryck som följer efter Throw är valfritt.

```powershell
function Get-XMLFiles
{
  param ($path = $(throw "The Path parameter is required."))
  dir -path $path\*.xml -recurse |
    sort lastwritetime |
      ft lastwritetime, attributes, name  -auto
}
```

## <a name="see-also"></a>SE ÄVEN

[about_Break](about_Break.md)

[about_Continue](about_Continue.md)

[about_Scopes](about_Scopes.md)

[about_Trap](about_Trap.md)

[about_Try_Catch_Finally](about_Try_Catch_Finally.md)
