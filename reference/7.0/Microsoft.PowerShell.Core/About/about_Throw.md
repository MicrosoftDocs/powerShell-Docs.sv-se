---
description: Beskriver nyckelordet Throw, som genererar ett avslutande fel.
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_throw?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Throw
ms.openlocfilehash: 2984e0a9e5f470594dd1e5987b69b92f91ce4913
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2021
ms.locfileid: "103193954"
---
# <a name="about-throw"></a>Om Throw

## <a name="short-description"></a>Kort beskrivning
Beskriver nyckelordet Throw, som genererar ett avslutande fel.

## <a name="long-description"></a>Lång beskrivning

Nyckelordet Throw orsakar ett avslutande fel. Du kan använda nyckelordet Throw för att stoppa bearbetningen av ett kommando, en funktion eller ett skript.

Du kan t. ex. använda nyckelordet Throw i skript blocket i en If-instruktion för att svara på ett villkor eller i det catch-blocket för en try-catch-finally-instruktion. Du kan också använda nyckelordet Throw i en parameter deklaration för att göra en funktions parameter obligatorisk.

Nyckelordet Throw kan utlösa alla objekt, t. ex. en användar meddelande sträng eller det objekt som orsakade felet.

## <a name="syntax"></a>Syntax

Syntaxen för nyckelordet Throw är följande:

```powershell
throw [<expression>]
```

Uttrycket i Throw-syntaxen är valfritt. När Throw-instruktionen inte visas i ett catch-block och den inte innehåller något uttryck, genererar det ett ScriptHalted-fel.

```powershell
C:\PS> throw

Exception: ScriptHalted
```

Om nyckelordet Throw används i ett catch-block utan ett uttryck, utlöses den aktuella RuntimeException igen. Mer information finns i about_Try_Catch_Finally.

## <a name="throwing-a-string"></a>Utlöser en sträng

Det valfria uttrycket i en throw-instruktion kan vara en sträng, som du ser i följande exempel:

```powershell
C:\PS> throw "This is an error."

Exception: This is an error.
```

## <a name="throwing-other-objects"></a>Andra objekt utlöses

Uttrycket kan också vara ett objekt som utlöser objektet som representerar PowerShell-processen, vilket visas i följande exempel:

```powershell
C:\PS> throw (get-process Pwsh)

Exception: System.Diagnostics.Process (pwsh) System.Diagnostics.Process (pwsh) System.Diagnostics.Process (pwsh)
```

Du kan använda egenskapen TargetObject för objektet ErrorRecord i $error automatisk variabel för att undersöka felet.

```powershell
C:\PS> $error[0].targetobject

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    125   174.44     229.57      23.61    1548   2 pwsh
     63    44.07      81.95       1.75    1732   2 pwsh
     63    43.32      77.65       1.48    9092   2 pwsh
```

Du kan också utlösa ett ErrorRecord-objekt eller ett .NET-undantag. I följande exempel används nyckelordet Throw för att utlösa ett system. FormatException-objekt.

```powershell
C:\PS> $formatError = new-object system.formatexception

C:\PS> throw $formatError

OperationStopped: One of the identified items was in an invalid format.
```

## <a name="the-resulting-error"></a>Det resulterande felet

Med nyckelordet Throw kan du generera ett ErrorRecord-objekt. Egenskapen Exception för ErrorRecord-objektet innehåller ett RuntimeException-objekt. Resten av ErrorRecord-objektet och RuntimeException-objektet varierar beroende på vilket objekt som nyckelordet Throw genererar.

RunTimeException-objektet är omslutet i ett ErrorRecord-objekt, och ErrorRecord-objektet sparas automatiskt i $Error automatiska variabeln.

## <a name="using-throw-to-create-a-mandatory-parameter"></a>Använda Throw för att skapa en obligatorisk parameter

Till skillnad från tidigare versioner av PowerShell ska du inte använda nyckelordet Throw för parameter validering. Se [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md) för korrekt sätt.

## <a name="see-also"></a>Se även

- [about_Break](about_Break.md)
- [about_Continue](about_Continue.md)
- [about_Scopes](about_Scopes.md)
- [about_Trap](about_Trap.md)
- [about_Try_Catch_Finally](about_Try_Catch_Finally.md)
