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
# <a name="about-throw"></a><span data-ttu-id="cb362-103">Om Throw</span><span class="sxs-lookup"><span data-stu-id="cb362-103">About Throw</span></span>

## <a name="short-description"></a><span data-ttu-id="cb362-104">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="cb362-104">SHORT DESCRIPTION</span></span>

<span data-ttu-id="cb362-105">Beskriver nyckelordet Throw, som genererar ett avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="cb362-105">Describes the Throw keyword, which generates a terminating error.</span></span>

## <a name="long-description"></a><span data-ttu-id="cb362-106">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="cb362-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="cb362-107">Nyckelordet Throw orsakar ett avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="cb362-107">The Throw keyword causes a terminating error.</span></span> <span data-ttu-id="cb362-108">Du kan använda nyckelordet Throw för att stoppa bearbetningen av ett kommando, en funktion eller ett skript.</span><span class="sxs-lookup"><span data-stu-id="cb362-108">You can use the Throw keyword to stop the processing of a command, function, or script.</span></span>

<span data-ttu-id="cb362-109">Du kan t. ex. använda nyckelordet Throw i skript blocket i en If-instruktion för att svara på ett villkor eller i det catch-blocket för en try-catch-finally-instruktion.</span><span class="sxs-lookup"><span data-stu-id="cb362-109">For example, you can use the Throw keyword in the script block of an If statement to respond to a condition or in the Catch block of a Try-Catch-Finally statement.</span></span> <span data-ttu-id="cb362-110">Du kan också använda nyckelordet Throw i en parameter deklaration för att göra en funktions parameter obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="cb362-110">You can also use the Throw keyword in a parameter declaration to make a function parameter mandatory.</span></span>

<span data-ttu-id="cb362-111">Nyckelordet Throw kan utlösa alla objekt, t. ex. en användar meddelande sträng eller det objekt som orsakade felet.</span><span class="sxs-lookup"><span data-stu-id="cb362-111">The Throw keyword can throw any object, such as a user message string or the object that caused the error.</span></span>

## <a name="syntax"></a><span data-ttu-id="cb362-112">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cb362-112">SYNTAX</span></span>

<span data-ttu-id="cb362-113">Syntaxen för nyckelordet Throw är följande:</span><span class="sxs-lookup"><span data-stu-id="cb362-113">The syntax of the Throw keyword is as follows:</span></span>

```powershell
throw [<expression>]
```

<span data-ttu-id="cb362-114">Uttrycket i Throw-syntaxen är valfritt.</span><span class="sxs-lookup"><span data-stu-id="cb362-114">The expression in the Throw syntax is optional.</span></span> <span data-ttu-id="cb362-115">När Throw-instruktionen inte visas i ett catch-block och den inte innehåller något uttryck, genererar det ett ScriptHalted-fel.</span><span class="sxs-lookup"><span data-stu-id="cb362-115">When the Throw statement does not appear in a Catch block, and it does not include an expression, it generates a ScriptHalted error.</span></span>

```powershell
C:\PS> throw

ScriptHalted
At line:1 char:6
+ throw <<<<
+ CategoryInfo          : OperationStopped: (:) [], RuntimeException
+ FullyQualifiedErrorId : ScriptHalted
```

<span data-ttu-id="cb362-116">Om nyckelordet Throw används i ett catch-block utan ett uttryck, utlöses den aktuella RuntimeException igen.</span><span class="sxs-lookup"><span data-stu-id="cb362-116">If the Throw keyword is used in a Catch block without an expression, it throws the current RuntimeException again.</span></span> <span data-ttu-id="cb362-117">Mer information finns i about_Try_Catch_Finally.</span><span class="sxs-lookup"><span data-stu-id="cb362-117">For more information, see about_Try_Catch_Finally.</span></span>

## <a name="throwing-a-string"></a><span data-ttu-id="cb362-118">UTLÖSER EN STRÄNG</span><span class="sxs-lookup"><span data-stu-id="cb362-118">THROWING A STRING</span></span>

<span data-ttu-id="cb362-119">Det valfria uttrycket i en throw-instruktion kan vara en sträng, som du ser i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="cb362-119">The optional expression in a Throw statement can be a string, as shown in the following example:</span></span>

```powershell
C:\PS> throw "This is an error."

This is an error.
At line:1 char:6
+ throw <<<<  "This is an error."
+ CategoryInfo          : OperationStopped: (This is an error.:String) [], R
untimeException
+ FullyQualifiedErrorId : This is an error.
```

## <a name="throwing-other-objects"></a><span data-ttu-id="cb362-120">ANDRA OBJEKT UTLÖSES</span><span class="sxs-lookup"><span data-stu-id="cb362-120">THROWING OTHER OBJECTS</span></span>

<span data-ttu-id="cb362-121">Uttrycket kan också vara ett objekt som utlöser objektet som representerar PowerShell-processen, vilket visas i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="cb362-121">The expression can also be an object that throws the object that represents the PowerShell process, as shown in the following example:</span></span>

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

<span data-ttu-id="cb362-122">Du kan använda egenskapen TargetObject för objektet ErrorRecord i $error automatisk variabel för att undersöka felet.</span><span class="sxs-lookup"><span data-stu-id="cb362-122">You can use the TargetObject property of the ErrorRecord object in the $error automatic variable to examine the error.</span></span>

```powershell
C:\PS> $error[0].targetobject

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
319      26    61016      70864   568     3.28   5548 PowerShell
```

<span data-ttu-id="cb362-123">Du kan också utlösa ett ErrorRecord-objekt eller ett undantag för Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cb362-123">You can also throw an ErrorRecord object or a Microsoft .NET Framework exception.</span></span> <span data-ttu-id="cb362-124">I följande exempel används nyckelordet Throw för att utlösa ett system. FormatException-objekt.</span><span class="sxs-lookup"><span data-stu-id="cb362-124">The following example uses the Throw keyword to throw a System.FormatException object.</span></span>

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

## <a name="resulting-error"></a><span data-ttu-id="cb362-125">RESULTERANDE FEL</span><span class="sxs-lookup"><span data-stu-id="cb362-125">RESULTING ERROR</span></span>

<span data-ttu-id="cb362-126">Med nyckelordet Throw kan du generera ett ErrorRecord-objekt.</span><span class="sxs-lookup"><span data-stu-id="cb362-126">The Throw keyword can generate an ErrorRecord object.</span></span> <span data-ttu-id="cb362-127">Egenskapen Exception för ErrorRecord-objektet innehåller ett RuntimeException-objekt.</span><span class="sxs-lookup"><span data-stu-id="cb362-127">The Exception property of the ErrorRecord object contains a RuntimeException object.</span></span> <span data-ttu-id="cb362-128">Resten av ErrorRecord-objektet och RuntimeException-objektet varierar beroende på vilket objekt som nyckelordet Throw genererar.</span><span class="sxs-lookup"><span data-stu-id="cb362-128">The remainder of the ErrorRecord object and the RuntimeException object vary with the object that the Throw keyword throws.</span></span>

<span data-ttu-id="cb362-129">RunTimeException-objektet är omslutet i ett ErrorRecord-objekt, och ErrorRecord-objektet sparas automatiskt i $Error automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="cb362-129">The RunTimeException object is wrapped in an ErrorRecord object, and the ErrorRecord object is automatically saved in the $Error automatic variable.</span></span>

## <a name="using-throw-to-create-a-mandatory-parameter"></a><span data-ttu-id="cb362-130">ANVÄNDA THROW FÖR ATT SKAPA EN OBLIGATORISK PARAMETER</span><span class="sxs-lookup"><span data-stu-id="cb362-130">USING THROW TO CREATE A MANDATORY PARAMETER</span></span>

<span data-ttu-id="cb362-131">Du kan använda nyckelordet Throw för att göra en funktions parameter obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="cb362-131">You can use the Throw keyword to make a function parameter mandatory.</span></span>

<span data-ttu-id="cb362-132">Detta är ett alternativ till att använda den obligatoriska parametern för parameterns nyckelord.</span><span class="sxs-lookup"><span data-stu-id="cb362-132">This is an alternative to using the Mandatory parameter of the Parameter keyword.</span></span> <span data-ttu-id="cb362-133">När du använder den obligatoriska parametern, uppmanas användaren att ange det obligatoriska parametervärdet.</span><span class="sxs-lookup"><span data-stu-id="cb362-133">When you use the Mandatory parameter, the system prompts the user for the required parameter value.</span></span> <span data-ttu-id="cb362-134">När du använder nyckelordet Throw, stannar kommandot och felposten visas.</span><span class="sxs-lookup"><span data-stu-id="cb362-134">When you use the Throw keyword, the command stops and displays the error record.</span></span>

<span data-ttu-id="cb362-135">Till exempel gör nyckelordet Throw i parametern-under uttryck Sök vägs parametern till en obligatorisk parameter i funktionen.</span><span class="sxs-lookup"><span data-stu-id="cb362-135">For example, the Throw keyword in the parameter subexpression makes the Path parameter a required parameter in the function.</span></span>

<span data-ttu-id="cb362-136">I det här fallet genererar nyckelordet Throw en meddelande sträng, men det är förekomsten av nyckelordet Throw som genererar det avslutande felet om parametern Path inte anges.</span><span class="sxs-lookup"><span data-stu-id="cb362-136">In this case, the Throw keyword throws a message string, but it is the presence of the Throw keyword that generates the terminating error if the Path parameter is not specified.</span></span> <span data-ttu-id="cb362-137">Det uttryck som följer efter Throw är valfritt.</span><span class="sxs-lookup"><span data-stu-id="cb362-137">The expression that follows Throw is optional.</span></span>

```powershell
function Get-XMLFiles
{
  param ($path = $(throw "The Path parameter is required."))
  dir -path $path\*.xml -recurse |
    sort lastwritetime |
      ft lastwritetime, attributes, name  -auto
}
```

## <a name="see-also"></a><span data-ttu-id="cb362-138">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="cb362-138">SEE ALSO</span></span>

[<span data-ttu-id="cb362-139">about_Break</span><span class="sxs-lookup"><span data-stu-id="cb362-139">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="cb362-140">about_Continue</span><span class="sxs-lookup"><span data-stu-id="cb362-140">about_Continue</span></span>](about_Continue.md)

[<span data-ttu-id="cb362-141">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="cb362-141">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="cb362-142">about_Trap</span><span class="sxs-lookup"><span data-stu-id="cb362-142">about_Trap</span></span>](about_Trap.md)

[<span data-ttu-id="cb362-143">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="cb362-143">about_Try_Catch_Finally</span></span>](about_Try_Catch_Finally.md)
