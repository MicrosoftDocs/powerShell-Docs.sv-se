---
description: Beskriver nyckelordet Throw, som genererar ett avslutande fel.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_throw?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Throw
ms.openlocfilehash: d4bf0ea00145c03522d4db952be201c877c9d50c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271677"
---
# <a name="about-throw"></a><span data-ttu-id="1ed07-104">Om Throw</span><span class="sxs-lookup"><span data-stu-id="1ed07-104">About Throw</span></span>

## <a name="short-description"></a><span data-ttu-id="1ed07-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="1ed07-105">Short description</span></span>
<span data-ttu-id="1ed07-106">Beskriver nyckelordet Throw, som genererar ett avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="1ed07-106">Describes the Throw keyword, which generates a terminating error.</span></span>

## <a name="long-description"></a><span data-ttu-id="1ed07-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="1ed07-107">Long description</span></span>

<span data-ttu-id="1ed07-108">Nyckelordet Throw orsakar ett avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="1ed07-108">The Throw keyword causes a terminating error.</span></span> <span data-ttu-id="1ed07-109">Du kan använda nyckelordet Throw för att stoppa bearbetningen av ett kommando, en funktion eller ett skript.</span><span class="sxs-lookup"><span data-stu-id="1ed07-109">You can use the Throw keyword to stop the processing of a command, function, or script.</span></span>

<span data-ttu-id="1ed07-110">Du kan t. ex. använda nyckelordet Throw i skript blocket i en If-instruktion för att svara på ett villkor eller i det catch-blocket för en try-catch-finally-instruktion.</span><span class="sxs-lookup"><span data-stu-id="1ed07-110">For example, you can use the Throw keyword in the script block of an If statement to respond to a condition or in the Catch block of a Try-Catch-Finally statement.</span></span> <span data-ttu-id="1ed07-111">Du kan också använda nyckelordet Throw i en parameter deklaration för att göra en funktions parameter obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="1ed07-111">You can also use the Throw keyword in a parameter declaration to make a function parameter mandatory.</span></span>

<span data-ttu-id="1ed07-112">Nyckelordet Throw kan utlösa alla objekt, t. ex. en användar meddelande sträng eller det objekt som orsakade felet.</span><span class="sxs-lookup"><span data-stu-id="1ed07-112">The Throw keyword can throw any object, such as a user message string or the object that caused the error.</span></span>

## <a name="syntax"></a><span data-ttu-id="1ed07-113">Syntax</span><span class="sxs-lookup"><span data-stu-id="1ed07-113">Syntax</span></span>

<span data-ttu-id="1ed07-114">Syntaxen för nyckelordet Throw är följande:</span><span class="sxs-lookup"><span data-stu-id="1ed07-114">The syntax of the Throw keyword is as follows:</span></span>

```powershell
throw [<expression>]
```

<span data-ttu-id="1ed07-115">Uttrycket i Throw-syntaxen är valfritt.</span><span class="sxs-lookup"><span data-stu-id="1ed07-115">The expression in the Throw syntax is optional.</span></span> <span data-ttu-id="1ed07-116">När Throw-instruktionen inte visas i ett catch-block och den inte innehåller något uttryck, genererar det ett ScriptHalted-fel.</span><span class="sxs-lookup"><span data-stu-id="1ed07-116">When the Throw statement does not appear in a Catch block, and it does not include an expression, it generates a ScriptHalted error.</span></span>

```powershell
C:\PS> throw

Exception: ScriptHalted
```

<span data-ttu-id="1ed07-117">Om nyckelordet Throw används i ett catch-block utan ett uttryck, utlöses den aktuella RuntimeException igen.</span><span class="sxs-lookup"><span data-stu-id="1ed07-117">If the Throw keyword is used in a Catch block without an expression, it throws the current RuntimeException again.</span></span> <span data-ttu-id="1ed07-118">Mer information finns i about_Try_Catch_Finally.</span><span class="sxs-lookup"><span data-stu-id="1ed07-118">For more information, see about_Try_Catch_Finally.</span></span>

## <a name="throwing-a-string"></a><span data-ttu-id="1ed07-119">Utlöser en sträng</span><span class="sxs-lookup"><span data-stu-id="1ed07-119">Throwing a string</span></span>

<span data-ttu-id="1ed07-120">Det valfria uttrycket i en throw-instruktion kan vara en sträng, som du ser i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="1ed07-120">The optional expression in a Throw statement can be a string, as shown in the following example:</span></span>

```powershell
C:\PS> throw "This is an error."

Exception: This is an error.
```

## <a name="throwing-other-objects"></a><span data-ttu-id="1ed07-121">Andra objekt utlöses</span><span class="sxs-lookup"><span data-stu-id="1ed07-121">Throwing other objects</span></span>

<span data-ttu-id="1ed07-122">Uttrycket kan också vara ett objekt som utlöser objektet som representerar PowerShell-processen, vilket visas i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="1ed07-122">The expression can also be an object that throws the object that represents the PowerShell process, as shown in the following example:</span></span>

```powershell
C:\PS> throw (get-process Pwsh)

Exception: System.Diagnostics.Process (pwsh) System.Diagnostics.Process (pwsh) System.Diagnostics.Process (pwsh)
```

<span data-ttu-id="1ed07-123">Du kan använda egenskapen TargetObject för objektet ErrorRecord i $error automatisk variabel för att undersöka felet.</span><span class="sxs-lookup"><span data-stu-id="1ed07-123">You can use the TargetObject property of the ErrorRecord object in the $error automatic variable to examine the error.</span></span>

```powershell
C:\PS> $error[0].targetobject

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    125   174.44     229.57      23.61    1548   2 pwsh
     63    44.07      81.95       1.75    1732   2 pwsh
     63    43.32      77.65       1.48    9092   2 pwsh
```

<span data-ttu-id="1ed07-124">Du kan också utlösa ett ErrorRecord-objekt eller ett .NET-undantag.</span><span class="sxs-lookup"><span data-stu-id="1ed07-124">You can also throw an ErrorRecord object or a .NET exception.</span></span> <span data-ttu-id="1ed07-125">I följande exempel används nyckelordet Throw för att utlösa ett system. FormatException-objekt.</span><span class="sxs-lookup"><span data-stu-id="1ed07-125">The following example uses the Throw keyword to throw a System.FormatException object.</span></span>

```powershell
C:\PS> $formatError = new-object system.formatexception

C:\PS> throw $formatError

OperationStopped: One of the identified items was in an invalid format.
```

## <a name="the-resulting-error"></a><span data-ttu-id="1ed07-126">Det resulterande felet</span><span class="sxs-lookup"><span data-stu-id="1ed07-126">The resulting error</span></span>

<span data-ttu-id="1ed07-127">Med nyckelordet Throw kan du generera ett ErrorRecord-objekt.</span><span class="sxs-lookup"><span data-stu-id="1ed07-127">The Throw keyword can generate an ErrorRecord object.</span></span> <span data-ttu-id="1ed07-128">Egenskapen Exception för ErrorRecord-objektet innehåller ett RuntimeException-objekt.</span><span class="sxs-lookup"><span data-stu-id="1ed07-128">The Exception property of the ErrorRecord object contains a RuntimeException object.</span></span> <span data-ttu-id="1ed07-129">Resten av ErrorRecord-objektet och RuntimeException-objektet varierar beroende på vilket objekt som nyckelordet Throw genererar.</span><span class="sxs-lookup"><span data-stu-id="1ed07-129">The remainder of the ErrorRecord object and the RuntimeException object vary with the object that the Throw keyword throws.</span></span>

<span data-ttu-id="1ed07-130">RunTimeException-objektet är omslutet i ett ErrorRecord-objekt, och ErrorRecord-objektet sparas automatiskt i $Error automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="1ed07-130">The RunTimeException object is wrapped in an ErrorRecord object, and the ErrorRecord object is automatically saved in the $Error automatic variable.</span></span>

## <a name="using-throw-to-create-a-mandatory-parameter"></a><span data-ttu-id="1ed07-131">Använda Throw för att skapa en obligatorisk parameter</span><span class="sxs-lookup"><span data-stu-id="1ed07-131">Using Throw to create a mandatory parameter</span></span>

<span data-ttu-id="1ed07-132">Till skillnad från tidigare versioner av PowerShell ska du inte använda nyckelordet Throw för parameter validering.</span><span class="sxs-lookup"><span data-stu-id="1ed07-132">Unlike past versions of PowerShell, do not use the Throw keyword for parameter validation.</span></span> <span data-ttu-id="1ed07-133">Se [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md) för korrekt sätt.</span><span class="sxs-lookup"><span data-stu-id="1ed07-133">See [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md) for the correct way.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ed07-134">Se även</span><span class="sxs-lookup"><span data-stu-id="1ed07-134">See also</span></span>

- [<span data-ttu-id="1ed07-135">about_Break</span><span class="sxs-lookup"><span data-stu-id="1ed07-135">about_Break</span></span>](about_Break.md)
- [<span data-ttu-id="1ed07-136">about_Continue</span><span class="sxs-lookup"><span data-stu-id="1ed07-136">about_Continue</span></span>](about_Continue.md)
- [<span data-ttu-id="1ed07-137">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="1ed07-137">about_Scopes</span></span>](about_Scopes.md)
- [<span data-ttu-id="1ed07-138">about_Trap</span><span class="sxs-lookup"><span data-stu-id="1ed07-138">about_Trap</span></span>](about_Trap.md)
- [<span data-ttu-id="1ed07-139">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="1ed07-139">about_Try_Catch_Finally</span></span>](about_Try_Catch_Finally.md)
