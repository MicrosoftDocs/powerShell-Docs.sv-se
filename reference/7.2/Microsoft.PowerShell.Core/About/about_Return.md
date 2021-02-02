---
description: Avslutar det aktuella omfånget, som kan vara en funktion, ett skript eller ett skript block.
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_return?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Return
ms.openlocfilehash: 032f3c694096e11e2800be941eb76b1f442b5088
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710975"
---
# <a name="about-return"></a><span data-ttu-id="5ed18-103">Om retur</span><span class="sxs-lookup"><span data-stu-id="5ed18-103">About Return</span></span>

## <a name="short-description"></a><span data-ttu-id="5ed18-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="5ed18-104">Short description</span></span>

<span data-ttu-id="5ed18-105">Avslutar det aktuella omfånget, som kan vara en funktion, ett skript eller ett skript block.</span><span class="sxs-lookup"><span data-stu-id="5ed18-105">Exits the current scope, which can be a function, script, or script block.</span></span>

## <a name="long-description"></a><span data-ttu-id="5ed18-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="5ed18-106">Long description</span></span>

<span data-ttu-id="5ed18-107">`return`Nyckelordet avslutar en funktion, ett skript eller ett skript block.</span><span class="sxs-lookup"><span data-stu-id="5ed18-107">The `return` keyword exits a function, script, or script block.</span></span> <span data-ttu-id="5ed18-108">Den kan användas för att avsluta ett omfång vid en viss punkt, för att returnera ett värde, eller för att ange att slutet på omfattningen har uppnåtts.</span><span class="sxs-lookup"><span data-stu-id="5ed18-108">It can be used to exit a scope at a specific point, to return a value, or to indicate that the end of the scope has been reached.</span></span>

<span data-ttu-id="5ed18-109">Användare som är bekanta med språk som C eller C \# kan vilja använda `return` nyckelordet för att göra logiken att lämna ett explicit område.</span><span class="sxs-lookup"><span data-stu-id="5ed18-109">Users who are familiar with languages like C or C\# might want to use the `return` keyword to make the logic of leaving a scope explicit.</span></span>

<span data-ttu-id="5ed18-110">I PowerShell returneras resultatet av varje instruktion som utdata, även om det inte finns någon instruktion som innehåller nyckelordet Return.</span><span class="sxs-lookup"><span data-stu-id="5ed18-110">In PowerShell, the results of each statement are returned as output, even without a statement that contains the Return keyword.</span></span> <span data-ttu-id="5ed18-111">Språk som C eller C \# returnerar bara de värden eller värden som anges av `return` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="5ed18-111">Languages like C or C\# return only the value or values that are specified by the `return` keyword.</span></span>

> [!NOTE]
> <span data-ttu-id="5ed18-112">Från och med PowerShell 5,0 har PowerShell använt språk för att definiera klasser med hjälp av formell syntax.</span><span class="sxs-lookup"><span data-stu-id="5ed18-112">Beginning in PowerShell 5.0, PowerShell added language for defining classes, by using formal syntax.</span></span>  <span data-ttu-id="5ed18-113">I kontexten för en PowerShell-klass är inget utdata från en metod, förutom vad du anger med hjälp av en `return` instruktion.</span><span class="sxs-lookup"><span data-stu-id="5ed18-113">In the context of a PowerShell class, nothing is output from a method except what you specify using a `return` statement.</span></span> <span data-ttu-id="5ed18-114">Du kan läsa mer om PowerShell-klasser i [about_Classes](about_Classes.md).</span><span class="sxs-lookup"><span data-stu-id="5ed18-114">You can read more about PowerShell classes in [about_Classes](about_Classes.md).</span></span>

### <a name="syntax"></a><span data-ttu-id="5ed18-115">Syntax</span><span class="sxs-lookup"><span data-stu-id="5ed18-115">Syntax</span></span>

<span data-ttu-id="5ed18-116">Syntaxen för `return` nyckelordet ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="5ed18-116">The syntax for the `return` keyword is as follows:</span></span>

```
return [<expression>]
```

<span data-ttu-id="5ed18-117">`return`Nyckelordet får endast visas eller följas av ett värde eller uttryck, enligt följande:</span><span class="sxs-lookup"><span data-stu-id="5ed18-117">The `return` keyword can appear alone, or it can be followed by a value or expression, as follows:</span></span>

```powershell
return
return $a
return (2 + $a)
```

### <a name="examples"></a><span data-ttu-id="5ed18-118">Exempel</span><span class="sxs-lookup"><span data-stu-id="5ed18-118">Examples</span></span>

<span data-ttu-id="5ed18-119">I följande exempel används `return` nyckelordet för att avsluta en funktion vid en viss punkt om ett villkor är uppfyllt.</span><span class="sxs-lookup"><span data-stu-id="5ed18-119">The following example uses the `return` keyword to exit a function at a specific point if a conditional is met.</span></span> <span data-ttu-id="5ed18-120">Udda tal multipliceras inte eftersom Return-instruktionen avslutas innan instruktionen kan köras.</span><span class="sxs-lookup"><span data-stu-id="5ed18-120">Odd numbers are not multiplied because the return statement exits before that statement can execute.</span></span>

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

<span data-ttu-id="5ed18-121">I PowerShell kan värden returneras även om `return` nyckelordet inte används.</span><span class="sxs-lookup"><span data-stu-id="5ed18-121">In PowerShell, values can be returned even if the `return` keyword is not used.</span></span>
<span data-ttu-id="5ed18-122">Resultaten av varje instruktion returneras.</span><span class="sxs-lookup"><span data-stu-id="5ed18-122">The results of each statement are returned.</span></span> <span data-ttu-id="5ed18-123">Följande uttryck returnerar till exempel värdet för `$a` variabeln:</span><span class="sxs-lookup"><span data-stu-id="5ed18-123">For example, the following statements return the value of the `$a` variable:</span></span>

```powershell
$a
return
```

<span data-ttu-id="5ed18-124">Följande instruktion returnerar även värdet för `$a` :</span><span class="sxs-lookup"><span data-stu-id="5ed18-124">The following statement also returns the value of `$a`:</span></span>

```powershell
return $a
```

<span data-ttu-id="5ed18-125">I följande exempel finns en instruktion som är avsedd att ge användaren veta att funktionen utför en beräkning:</span><span class="sxs-lookup"><span data-stu-id="5ed18-125">The following example includes a statement intended to let the user know that the function is performing a calculation:</span></span>

```powershell
function calculation {
    param ($value)

    "Please wait. Working on calculation..."
    $value += 73
    return $value
}

$a = calculation 14
```

<span data-ttu-id="5ed18-126">"Vänta.</span><span class="sxs-lookup"><span data-stu-id="5ed18-126">The "Please wait.</span></span> <span data-ttu-id="5ed18-127">Arbetar med beräkning... " strängen visas inte.</span><span class="sxs-lookup"><span data-stu-id="5ed18-127">Working on calculation..." string is not displayed.</span></span> <span data-ttu-id="5ed18-128">I stället tilldelas den `$a` variabeln, som i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="5ed18-128">Instead, it is assigned to the `$a` variable, as in the following example:</span></span>

```
PS> $a
Please wait. Working on calculation...
87
```

<span data-ttu-id="5ed18-129">Både den informations sträng och resultatet av beräkningen returneras av funktionen och tilldelas till `$a` variabeln.</span><span class="sxs-lookup"><span data-stu-id="5ed18-129">Both the informational string and the result of the calculation are returned by the function and assigned to the `$a` variable.</span></span>

<span data-ttu-id="5ed18-130">Om du vill visa ett meddelande i din funktion, från och med PowerShell 5,0, kan du använda `Information` data strömmen.</span><span class="sxs-lookup"><span data-stu-id="5ed18-130">If you would like to display a message within your function, beginning in PowerShell 5.0, you can use the `Information` stream.</span></span> <span data-ttu-id="5ed18-131">I koden nedan korrigeras exemplet ovan med hjälp av `Write-Information` cmdleten med en `InformationAction` av **Continue**.</span><span class="sxs-lookup"><span data-stu-id="5ed18-131">The code below corrects the above example using the `Write-Information` cmdlet with a `InformationAction` of **Continue**.</span></span>

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

### <a name="return-values-and-the-pipeline"></a><span data-ttu-id="5ed18-132">Retur värden och pipelinen</span><span class="sxs-lookup"><span data-stu-id="5ed18-132">Return values and the Pipeline</span></span>

<span data-ttu-id="5ed18-133">När du returnerar en samling från skript blocket eller funktionen, avregistrerar PowerShell automatiskt medlemmarna och skickar dem en i taget via pipelinen.</span><span class="sxs-lookup"><span data-stu-id="5ed18-133">When you return a collection from your script block or function, PowerShell automatically unrolls the members and passes them one at a time through the pipeline.</span></span> <span data-ttu-id="5ed18-134">Detta beror på PowerShell: s en-vid-tidpunkt-bearbetning.</span><span class="sxs-lookup"><span data-stu-id="5ed18-134">This is due to PowerShell's one-at-a-time processing.</span></span> <span data-ttu-id="5ed18-135">Mer information finns i [about_pipelines](about_pipelines.md).</span><span class="sxs-lookup"><span data-stu-id="5ed18-135">For more information, see [about_pipelines](about_pipelines.md).</span></span>

<span data-ttu-id="5ed18-136">Det här konceptet illustreras med följande exempel funktion som returnerar en matris med tal.</span><span class="sxs-lookup"><span data-stu-id="5ed18-136">This concept is illustrated by the following sample function that returns an array of numbers.</span></span> <span data-ttu-id="5ed18-137">Utdata från funktionen är skickas till `Measure-Object` cmdleten som räknar antalet objekt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="5ed18-137">The output from the function is piped to the `Measure-Object` cmdlet which counts the number of objects in the pipeline.</span></span>

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

<span data-ttu-id="5ed18-138">Använd någon av följande två metoder om du vill tvinga ett skript block eller en funktion att returnera samling som ett enda objekt till pipelinen:</span><span class="sxs-lookup"><span data-stu-id="5ed18-138">To force a script block or function to return collection as a single object to the pipeline, use one of the following two methods:</span></span>

- <span data-ttu-id="5ed18-139">Uttryck för unär mat ris</span><span class="sxs-lookup"><span data-stu-id="5ed18-139">Unary array expression</span></span>

  <span data-ttu-id="5ed18-140">Genom att använda ett enställt uttryck kan du skicka ditt retur värde nedåt i pipeline som ett enda objekt som illustreras i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="5ed18-140">Utilizing a unary expression you can send your return value down the pipeline as a single object as illustrated by the following example.</span></span>

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

- <span data-ttu-id="5ed18-141">`Write-Output` med **noenumeration** parameter.</span><span class="sxs-lookup"><span data-stu-id="5ed18-141">`Write-Output` with **NoEnumerate** parameter.</span></span>

  <span data-ttu-id="5ed18-142">Du kan också använda `Write-Output` cmdlet: en med **noenumeration** -parametern.</span><span class="sxs-lookup"><span data-stu-id="5ed18-142">You can also use the `Write-Output` cmdlet with the **NoEnumerate** parameter.</span></span> <span data-ttu-id="5ed18-143">Exemplet nedan använder `Measure-Object` cmdleten för att räkna de objekt som skickas till pipelinen från exempel funktionen med hjälp av `return` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="5ed18-143">The example below uses the `Measure-Object` cmdlet to count the objects sent to the pipeline from the sample function by the `return` keyword.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5ed18-144">Se även</span><span class="sxs-lookup"><span data-stu-id="5ed18-144">See also</span></span>

[<span data-ttu-id="5ed18-145">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="5ed18-145">about_Language_Keywords</span></span>](about_Language_Keywords.md)

[<span data-ttu-id="5ed18-146">about_Functions</span><span class="sxs-lookup"><span data-stu-id="5ed18-146">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="5ed18-147">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="5ed18-147">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="5ed18-148">about_Classes</span><span class="sxs-lookup"><span data-stu-id="5ed18-148">about_Classes</span></span>](about_Classes.md)

[<span data-ttu-id="5ed18-149">Skriv information</span><span class="sxs-lookup"><span data-stu-id="5ed18-149">Write-Information</span></span>](xref:Microsoft.PowerShell.Utility.Write-Information)

[<span data-ttu-id="5ed18-150">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="5ed18-150">about_Script_Blocks</span></span>](about_Script_Blocks.md)
