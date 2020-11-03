---
description: Beskriver nyckelordet Throw, som genererar ett avslutande fel.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_throw?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Throw
ms.openlocfilehash: dce019e9dc77d24843f254f978224cf5820d31aa
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270351"
---
# <a name="about-throw"></a><span data-ttu-id="634ab-104">Om Throw</span><span class="sxs-lookup"><span data-stu-id="634ab-104">About Throw</span></span>

## <a name="short-description"></a><span data-ttu-id="634ab-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="634ab-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="634ab-106">Beskriver nyckelordet Throw, som genererar ett avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="634ab-106">Describes the Throw keyword, which generates a terminating error.</span></span>

## <a name="long-description"></a><span data-ttu-id="634ab-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="634ab-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="634ab-108">Nyckelordet Throw orsakar ett avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="634ab-108">The Throw keyword causes a terminating error.</span></span> <span data-ttu-id="634ab-109">Du kan använda nyckelordet Throw för att stoppa bearbetningen av ett kommando, en funktion eller ett skript.</span><span class="sxs-lookup"><span data-stu-id="634ab-109">You can use the Throw keyword to stop the processing of a command, function, or script.</span></span>

<span data-ttu-id="634ab-110">Du kan t. ex. använda nyckelordet Throw i skript blocket i en If-instruktion för att svara på ett villkor eller i det catch-blocket för en try-catch-finally-instruktion.</span><span class="sxs-lookup"><span data-stu-id="634ab-110">For example, you can use the Throw keyword in the script block of an If statement to respond to a condition or in the Catch block of a Try-Catch-Finally statement.</span></span> <span data-ttu-id="634ab-111">Du kan också använda nyckelordet Throw i en parameter deklaration för att göra en funktions parameter obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="634ab-111">You can also use the Throw keyword in a parameter declaration to make a function parameter mandatory.</span></span>

<span data-ttu-id="634ab-112">Nyckelordet Throw kan utlösa alla objekt, t. ex. en användar meddelande sträng eller det objekt som orsakade felet.</span><span class="sxs-lookup"><span data-stu-id="634ab-112">The Throw keyword can throw any object, such as a user message string or the object that caused the error.</span></span>

## <a name="syntax"></a><span data-ttu-id="634ab-113">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="634ab-113">SYNTAX</span></span>

<span data-ttu-id="634ab-114">Syntaxen för nyckelordet Throw är följande:</span><span class="sxs-lookup"><span data-stu-id="634ab-114">The syntax of the Throw keyword is as follows:</span></span>

```powershell
throw [<expression>]
```

<span data-ttu-id="634ab-115">Uttrycket i Throw-syntaxen är valfritt.</span><span class="sxs-lookup"><span data-stu-id="634ab-115">The expression in the Throw syntax is optional.</span></span> <span data-ttu-id="634ab-116">När Throw-instruktionen inte visas i ett catch-block och den inte innehåller något uttryck, genererar det ett ScriptHalted-fel.</span><span class="sxs-lookup"><span data-stu-id="634ab-116">When the Throw statement does not appear in a Catch block, and it does not include an expression, it generates a ScriptHalted error.</span></span>

```powershell
C:\PS> throw

ScriptHalted
At line:1 char:6
+ throw <<<<
+ CategoryInfo          : OperationStopped: (:) [], RuntimeException
+ FullyQualifiedErrorId : ScriptHalted
```

<span data-ttu-id="634ab-117">Om nyckelordet Throw används i ett catch-block utan ett uttryck, utlöses den aktuella RuntimeException igen.</span><span class="sxs-lookup"><span data-stu-id="634ab-117">If the Throw keyword is used in a Catch block without an expression, it throws the current RuntimeException again.</span></span> <span data-ttu-id="634ab-118">Mer information finns i about_Try_Catch_Finally.</span><span class="sxs-lookup"><span data-stu-id="634ab-118">For more information, see about_Try_Catch_Finally.</span></span>

## <a name="throwing-a-string"></a><span data-ttu-id="634ab-119">UTLÖSER EN STRÄNG</span><span class="sxs-lookup"><span data-stu-id="634ab-119">THROWING A STRING</span></span>

<span data-ttu-id="634ab-120">Det valfria uttrycket i en throw-instruktion kan vara en sträng, som du ser i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="634ab-120">The optional expression in a Throw statement can be a string, as shown in the following example:</span></span>

```powershell
C:\PS> throw "This is an error."

This is an error.
At line:1 char:6
+ throw <<<<  "This is an error."
+ CategoryInfo          : OperationStopped: (This is an error.:String) [], R
untimeException
+ FullyQualifiedErrorId : This is an error.
```

## <a name="throwing-other-objects"></a><span data-ttu-id="634ab-121">ANDRA OBJEKT UTLÖSES</span><span class="sxs-lookup"><span data-stu-id="634ab-121">THROWING OTHER OBJECTS</span></span>

<span data-ttu-id="634ab-122">Uttrycket kan också vara ett objekt som utlöser objektet som representerar PowerShell-processen, vilket visas i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="634ab-122">The expression can also be an object that throws the object that represents the PowerShell process, as shown in the following example:</span></span>

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

<span data-ttu-id="634ab-123">Du kan använda egenskapen TargetObject för objektet ErrorRecord i $error automatisk variabel för att undersöka felet.</span><span class="sxs-lookup"><span data-stu-id="634ab-123">You can use the TargetObject property of the ErrorRecord object in the $error automatic variable to examine the error.</span></span>

```powershell
C:\PS> $error[0].targetobject

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
319      26    61016      70864   568     3.28   5548 PowerShell
```

<span data-ttu-id="634ab-124">Du kan också utlösa ett ErrorRecord-objekt eller ett undantag för Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="634ab-124">You can also throw an ErrorRecord object or a Microsoft .NET Framework exception.</span></span> <span data-ttu-id="634ab-125">I följande exempel används nyckelordet Throw för att utlösa ett system. FormatException-objekt.</span><span class="sxs-lookup"><span data-stu-id="634ab-125">The following example uses the Throw keyword to throw a System.FormatException object.</span></span>

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

## <a name="resulting-error"></a><span data-ttu-id="634ab-126">RESULTERANDE FEL</span><span class="sxs-lookup"><span data-stu-id="634ab-126">RESULTING ERROR</span></span>

<span data-ttu-id="634ab-127">Med nyckelordet Throw kan du generera ett ErrorRecord-objekt.</span><span class="sxs-lookup"><span data-stu-id="634ab-127">The Throw keyword can generate an ErrorRecord object.</span></span> <span data-ttu-id="634ab-128">Egenskapen Exception för ErrorRecord-objektet innehåller ett RuntimeException-objekt.</span><span class="sxs-lookup"><span data-stu-id="634ab-128">The Exception property of the ErrorRecord object contains a RuntimeException object.</span></span> <span data-ttu-id="634ab-129">Resten av ErrorRecord-objektet och RuntimeException-objektet varierar beroende på vilket objekt som nyckelordet Throw genererar.</span><span class="sxs-lookup"><span data-stu-id="634ab-129">The remainder of the ErrorRecord object and the RuntimeException object vary with the object that the Throw keyword throws.</span></span>

<span data-ttu-id="634ab-130">RunTimeException-objektet är omslutet i ett ErrorRecord-objekt, och ErrorRecord-objektet sparas automatiskt i $Error automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="634ab-130">The RunTimeException object is wrapped in an ErrorRecord object, and the ErrorRecord object is automatically saved in the $Error automatic variable.</span></span>

## <a name="using-throw-to-create-a-mandatory-parameter"></a><span data-ttu-id="634ab-131">ANVÄNDA THROW FÖR ATT SKAPA EN OBLIGATORISK PARAMETER</span><span class="sxs-lookup"><span data-stu-id="634ab-131">USING THROW TO CREATE A MANDATORY PARAMETER</span></span>

<span data-ttu-id="634ab-132">Du kan använda nyckelordet Throw för att göra en funktions parameter obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="634ab-132">You can use the Throw keyword to make a function parameter mandatory.</span></span>

<span data-ttu-id="634ab-133">Detta är ett alternativ till att använda den obligatoriska parametern för parameterns nyckelord.</span><span class="sxs-lookup"><span data-stu-id="634ab-133">This is an alternative to using the Mandatory parameter of the Parameter keyword.</span></span> <span data-ttu-id="634ab-134">När du använder den obligatoriska parametern, uppmanas användaren att ange det obligatoriska parametervärdet.</span><span class="sxs-lookup"><span data-stu-id="634ab-134">When you use the Mandatory parameter, the system prompts the user for the required parameter value.</span></span> <span data-ttu-id="634ab-135">När du använder nyckelordet Throw, stannar kommandot och felposten visas.</span><span class="sxs-lookup"><span data-stu-id="634ab-135">When you use the Throw keyword, the command stops and displays the error record.</span></span>

<span data-ttu-id="634ab-136">Till exempel gör nyckelordet Throw i parametern-under uttryck Sök vägs parametern till en obligatorisk parameter i funktionen.</span><span class="sxs-lookup"><span data-stu-id="634ab-136">For example, the Throw keyword in the parameter subexpression makes the Path parameter a required parameter in the function.</span></span>

<span data-ttu-id="634ab-137">I det här fallet genererar nyckelordet Throw en meddelande sträng, men det är förekomsten av nyckelordet Throw som genererar det avslutande felet om parametern Path inte anges.</span><span class="sxs-lookup"><span data-stu-id="634ab-137">In this case, the Throw keyword throws a message string, but it is the presence of the Throw keyword that generates the terminating error if the Path parameter is not specified.</span></span> <span data-ttu-id="634ab-138">Det uttryck som följer efter Throw är valfritt.</span><span class="sxs-lookup"><span data-stu-id="634ab-138">The expression that follows Throw is optional.</span></span>

```powershell
function Get-XMLFiles
{
  param ($path = $(throw "The Path parameter is required."))
  dir -path $path\*.xml -recurse |
    sort lastwritetime |
      ft lastwritetime, attributes, name  -auto
}
```

## <a name="see-also"></a><span data-ttu-id="634ab-139">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="634ab-139">SEE ALSO</span></span>

[<span data-ttu-id="634ab-140">about_Break</span><span class="sxs-lookup"><span data-stu-id="634ab-140">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="634ab-141">about_Continue</span><span class="sxs-lookup"><span data-stu-id="634ab-141">about_Continue</span></span>](about_Continue.md)

[<span data-ttu-id="634ab-142">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="634ab-142">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="634ab-143">about_Trap</span><span class="sxs-lookup"><span data-stu-id="634ab-143">about_Trap</span></span>](about_Trap.md)

[<span data-ttu-id="634ab-144">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="634ab-144">about_Try_Catch_Finally</span></span>](about_Try_Catch_Finally.md)
