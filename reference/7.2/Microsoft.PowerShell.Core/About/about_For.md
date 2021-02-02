---
description: Beskriver ett språk kommando som du kan använda för att köra instruktioner som baseras på ett villkorligt test.
Locale: en-US
ms.date: 03/04/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_for?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_For
ms.openlocfilehash: 3f86505d60837e8e5fa4938092a48eeb10833560
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709283"
---
# <a name="about-for"></a><span data-ttu-id="63e6e-103">Om för</span><span class="sxs-lookup"><span data-stu-id="63e6e-103">About For</span></span>

## <a name="short-description"></a><span data-ttu-id="63e6e-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="63e6e-104">Short description</span></span>
<span data-ttu-id="63e6e-105">Beskriver ett språk kommando som du kan använda för att köra instruktioner som baseras på ett villkorligt test.</span><span class="sxs-lookup"><span data-stu-id="63e6e-105">Describes a language command you can use to run statements based on a conditional test.</span></span>

## <a name="long-description"></a><span data-ttu-id="63e6e-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="63e6e-106">Long description</span></span>

<span data-ttu-id="63e6e-107">`For`Instruktionen (kallas även en `For` loop) är en språk konstruktion som du kan använda för att skapa en loop som kör kommandon i ett kommando block medan ett angivet villkor utvärderas till `$true` .</span><span class="sxs-lookup"><span data-stu-id="63e6e-107">The `For` statement (also known as a `For` loop) is a language construct you can use to create a loop that runs commands in a command block while a specified condition evaluates to `$true`.</span></span>

<span data-ttu-id="63e6e-108">En typisk användning av `For` slingan är att iterera en matris med värden och att använda en delmängd av dessa värden.</span><span class="sxs-lookup"><span data-stu-id="63e6e-108">A typical use of the `For` loop is to iterate an array of values and to operate on a subset of these values.</span></span> <span data-ttu-id="63e6e-109">I de flesta fall bör du överväga att använda en instruktion om du vill iterera alla värden i en matris `Foreach` .</span><span class="sxs-lookup"><span data-stu-id="63e6e-109">In most cases, if you want to iterate all the values in an array, consider using a `Foreach` statement.</span></span>

### <a name="syntax"></a><span data-ttu-id="63e6e-110">Syntax</span><span class="sxs-lookup"><span data-stu-id="63e6e-110">Syntax</span></span>

<span data-ttu-id="63e6e-111">Följande visar `For` syntaxen för uttrycket.</span><span class="sxs-lookup"><span data-stu-id="63e6e-111">The following shows the `For` statement syntax.</span></span>

```
for (<Init>; <Condition>; <Repeat>)
{
    <Statement list>
}
```

<span data-ttu-id="63e6e-112">Plats hållaren **init** representerar ett eller flera kommandon som körs innan loopen börjar.</span><span class="sxs-lookup"><span data-stu-id="63e6e-112">The **Init** placeholder represents one or more commands that are run before the loop begins.</span></span> <span data-ttu-id="63e6e-113">Du använder vanligt vis **init** -delen av instruktionen för att skapa och initiera en variabel med ett start värde.</span><span class="sxs-lookup"><span data-stu-id="63e6e-113">You typically use the **Init** portion of the statement to create and initialize a variable with a starting value.</span></span>

<span data-ttu-id="63e6e-114">Den här variabeln kommer sedan att ligga till grund för villkoret som ska testas i nästa del av `For` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="63e6e-114">This variable will then be the basis for the condition to be tested in the next portion of the `For` statement.</span></span>

<span data-ttu-id="63e6e-115">Plats hållaren för **villkor** representerar den del av `For` instruktionen som matchar ett `$true` eller `$false` **booleskt** värde.</span><span class="sxs-lookup"><span data-stu-id="63e6e-115">The **Condition** placeholder represents the portion of the `For` statement that resolves to a `$true` or `$false` **Boolean** value.</span></span> <span data-ttu-id="63e6e-116">PowerShell utvärderar villkoret varje gången `For` slingen körs.</span><span class="sxs-lookup"><span data-stu-id="63e6e-116">PowerShell evaluates the condition each time the `For` loop runs.</span></span> <span data-ttu-id="63e6e-117">Om instruktionen är körs `$true` kommandona i kommando blocket och instruktionen utvärderas igen.</span><span class="sxs-lookup"><span data-stu-id="63e6e-117">If the statement is `$true`, the commands in the command block run, and the statement is evaluated again.</span></span> <span data-ttu-id="63e6e-118">Om villkoret fortfarande är `$true` fallet körs kommandona i **instruktions listan** igen.</span><span class="sxs-lookup"><span data-stu-id="63e6e-118">If the condition is still `$true`, the commands in the **Statement list** run again.</span></span> <span data-ttu-id="63e6e-119">Loopen upprepas tills villkoret blir `$false` .</span><span class="sxs-lookup"><span data-stu-id="63e6e-119">The loop is repeated until the condition becomes `$false`.</span></span>

<span data-ttu-id="63e6e-120">Plats hållaren för **upprepning** representerar ett eller flera kommandon, avgränsade med kommatecken, som körs varje gången upprepningen upprepas.</span><span class="sxs-lookup"><span data-stu-id="63e6e-120">The **Repeat** placeholder represents one or more commands, separated by commas, that are executed each time the loop repeats.</span></span> <span data-ttu-id="63e6e-121">Detta används vanligt vis för att ändra en variabel som testas inuti **villkors** delen i instruktionen.</span><span class="sxs-lookup"><span data-stu-id="63e6e-121">Typically, this is used to modify a variable that is tested inside the **Condition** part of the statement.</span></span>

<span data-ttu-id="63e6e-122">Plats hållaren för **instruktions listan** representerar en uppsättning av ett eller flera kommandon som körs varje gången loopen anges eller upprepas.</span><span class="sxs-lookup"><span data-stu-id="63e6e-122">The **Statement list** placeholder represents a set of one or more commands that are run each time the loop is entered or repeated.</span></span> <span data-ttu-id="63e6e-123">Innehållet i **instruktions listan** omges av klammerparenteser.</span><span class="sxs-lookup"><span data-stu-id="63e6e-123">The contents of the **Statement list** are surrounded by braces.</span></span>

### <a name="support-for-multiple-operations"></a><span data-ttu-id="63e6e-124">Stöd för flera åtgärder</span><span class="sxs-lookup"><span data-stu-id="63e6e-124">Support for multiple operations</span></span>

<span data-ttu-id="63e6e-125">Följande syntax stöds för flera tilldelnings åtgärder i **init** -instruktionen:</span><span class="sxs-lookup"><span data-stu-id="63e6e-125">The following syntaxes are supported for multiple assignment operations in the **Init** statement:</span></span>

```powershell
# Comma separated assignment expressions enclosed in parenthesis.
for (($i = 0), ($j = 0); $i -lt 10; $i++)
{
    "`$i:$i"
    "`$j:$j"
}

# Sub-expression using the semicolon to separate statements.
for ($($i = 0;$j = 0); $i -lt 10; $i++)
{
    "`$i:$i"
    "`$j:$j"
}
```

<span data-ttu-id="63e6e-126">Följande syntax stöds för flera tilldelnings åtgärder i instruktionen **REPEAT** :</span><span class="sxs-lookup"><span data-stu-id="63e6e-126">The following syntaxes are supported for multiple assignment operations in the **Repeat** statement:</span></span>

```powershell
# Comma separated assignment expressions.
for (($i = 0), ($j = 0); $i -lt 10; $i++)
{
    "`$i:$i"
    "`$j:$j"
}

# Comma separated assignment expressions enclosed in parenthesis.
for (($i = 0), ($j = 0); $i -lt 10; ($i++), ($j++))
{
    "`$i:$i"
    "`$j:$j"
}

# Sub-expression using the semicolon to separate statements.
for ($($i = 0;$j = 0); $i -lt 10; $($i++;$j++))
{
    "`$i:$i"
    "`$j:$j"
}
```

> [!NOTE]
> <span data-ttu-id="63e6e-127">Andra åtgärder än före eller efter-steg kanske inte fungerar med alla syntaxer.</span><span class="sxs-lookup"><span data-stu-id="63e6e-127">Operations other than pre or post increment may not work with all syntaxes.</span></span>

<span data-ttu-id="63e6e-128">För flera **villkor** använder logiska operatorer som de visas i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="63e6e-128">For multiple **Conditions** use logical operators as demonstrated by the following example.</span></span>

```powershell
for (($i = 0), ($j = 0); $i -lt 10 -and $j -lt 10; $i++,$j++)
{
    "`$i:$i"
    "`$j:$j"
}
```

<span data-ttu-id="63e6e-129">Mer information finns i [about_Logical_Operators](about_Logical_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="63e6e-129">For more information, see [about_Logical_Operators](about_Logical_Operators.md).</span></span>

### <a name="examples"></a><span data-ttu-id="63e6e-130">Exempel</span><span class="sxs-lookup"><span data-stu-id="63e6e-130">Examples</span></span>

<span data-ttu-id="63e6e-131">En instruktion kräver minst en `For` parentes som omger kommandot **init**, **condition** och **REPEAT** i instruktionen och ett kommando omgiven av klamrar i **instruktions List** delen av instruktionen.</span><span class="sxs-lookup"><span data-stu-id="63e6e-131">At a minimum, a `For` statement requires the parenthesis surrounding the **Init**, **Condition**, and **Repeat** part of the statement and a command surrounded by braces in the **Statement list** part of the statement.</span></span>

<span data-ttu-id="63e6e-132">Observera att de kommande exemplen avsiktligt visar kod utanför `For` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="63e6e-132">Note that the upcoming examples intentionally show code outside the `For` statement.</span></span> <span data-ttu-id="63e6e-133">I senare exempel integreras kod i `For` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="63e6e-133">In later examples, code is integrated into the `For` statement.</span></span>

<span data-ttu-id="63e6e-134">Till exempel `For` visar följande instruktion hela tiden värdet för `$i` variabeln tills du avbryter kommandot manuellt genom att trycka på CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="63e6e-134">For example, the following `For` statement continually displays the value of the `$i` variable until you manually break out of the command by pressing CTRL+C.</span></span>

```powershell
$i = 1
for (;;)
{
    Write-Host $i
}
```

<span data-ttu-id="63e6e-135">Du kan lägga till ytterligare kommandon i instruktions listan så att värdet i `$i` ökas med 1 varje gången loopen körs, som i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="63e6e-135">You can add additional commands to the statement list so that the value of `$i` is incremented by 1 each time the loop is run, as the following example shows.</span></span>

```powershell
for (;;)
{
    $i++; Write-Host $i
}
```

<span data-ttu-id="63e6e-136">Tills du har slut på kommandot genom att trycka på CTRL + C visar den här instruktionen hela tiden värdet för `$i` variabeln som ökas med 1 varje gång slingan körs.</span><span class="sxs-lookup"><span data-stu-id="63e6e-136">Until you break out of the command by pressing CTRL+C, this statement will continually display the value of the `$i` variable as it is incremented by 1 each time the loop is run.</span></span>

<span data-ttu-id="63e6e-137">I stället för att ändra värdet för variabeln i instruktions List delen av `For` instruktionen kan du använda den **upprepande** delen av `For` instruktionen i stället, enligt följande.</span><span class="sxs-lookup"><span data-stu-id="63e6e-137">Rather than change the value of the variable in the statement list part of the `For` statement, you can use the **Repeat** portion of the `For` statement instead, as follows.</span></span>

```powershell
$i=1
for (;;$i++)
{
    Write-Host $i
}
```

<span data-ttu-id="63e6e-138">Den här instruktionen upprepas fortfarande oändligt tills du delar ut kommandot genom att trycka på CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="63e6e-138">This statement will still repeat indefinitely until you break out of the command by pressing CTRL+C.</span></span>

<span data-ttu-id="63e6e-139">Du kan avsluta `For` loopen med ett *villkor*.</span><span class="sxs-lookup"><span data-stu-id="63e6e-139">You can terminate the `For` loop using a *condition*.</span></span> <span data-ttu-id="63e6e-140">Du kan placera ett villkor med hjälp av **villkors** delen i `For` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="63e6e-140">You can place a condition using the **Condition** portion of the `For` statement.</span></span> <span data-ttu-id="63e6e-141">`For`Loopen avslutas när villkoret utvärderas till `$false` .</span><span class="sxs-lookup"><span data-stu-id="63e6e-141">The `For` loop terminates when the condition evaluates to `$false`.</span></span>

<span data-ttu-id="63e6e-142">I följande exempel `For` körs loopen medan värdet `$i` är mindre än eller lika med 10.</span><span class="sxs-lookup"><span data-stu-id="63e6e-142">In the following example, the `For` loop runs while the value of `$i` is less than or equal to 10.</span></span>

```powershell
$i=1
for(;$i -le 10;$i++)
{
    Write-Host $i
}
```

<span data-ttu-id="63e6e-143">I stället för att skapa och initiera variabeln utanför `For` instruktionen kan du utföra den här uppgiften i `For` loopen med hjälp av instruktionens **init** -del `For` .</span><span class="sxs-lookup"><span data-stu-id="63e6e-143">Instead of creating and initializing the variable outside the `For` statement, you can perform this task inside the `For` loop by using the **Init** portion of the `For` statement.</span></span>

```powershell
for($i=1; $i -le 10; $i++){Write-Host $i}
```

<span data-ttu-id="63e6e-144">Du kan använda vagn returer i stället för semikolon för att avgränsa delarna **init**, **condition** och **REPEAT** i `For` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="63e6e-144">You can use carriage returns instead of semicolons to delimit the **Init**, **Condition**, and **Repeat** portions of the `For` statement.</span></span> <span data-ttu-id="63e6e-145">I följande exempel visas en `For` som använder den här alternativa syntaxen.</span><span class="sxs-lookup"><span data-stu-id="63e6e-145">The following example shows a `For` that uses this alternative syntax.</span></span>

```powershell
for ($i = 0
  $i -lt 10
  $i++){
  $i
}
```

<span data-ttu-id="63e6e-146">Den här alternativa formen av `For` instruktionen fungerar i PowerShell-skriptfiler och i PowerShell-Kommandotolken.</span><span class="sxs-lookup"><span data-stu-id="63e6e-146">This alternative form of the `For` statement works in PowerShell script files and at the PowerShell command prompt.</span></span> <span data-ttu-id="63e6e-147">Men det är enklare att använda kommandot `For` Statement med semikolon när du anger interaktiva kommandon i kommando tolken.</span><span class="sxs-lookup"><span data-stu-id="63e6e-147">However, it is easier to use the `For` statement syntax with semicolons when you enter interactive commands at the command prompt.</span></span>

<span data-ttu-id="63e6e-148">`For`Loopen är mer flexibel än `Foreach` loopen eftersom du kan öka värdena i en matris eller samling med hjälp av mönster.</span><span class="sxs-lookup"><span data-stu-id="63e6e-148">The `For` loop is more flexible than the `Foreach` loop because it allows you to increment values in an array or collection by using patterns.</span></span> <span data-ttu-id="63e6e-149">I följande exempel `$i` ökas variabeln med 2 i **upprepnings** delen av `For` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="63e6e-149">In the following example, the `$i` variable is incremented by 2 in the **Repeat** portion of the `For` statement.</span></span>

```powershell
for ($i = 0; $i -le 20; $i += 2)
{
    Write-Host $i
}
```

<span data-ttu-id="63e6e-150">`For`Slingan kan också skrivas på en rad som i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="63e6e-150">The `For` loop can also be written on one line as in the following example.</span></span>

```powershell
for ($i = 0; $i -lt 10; $i++) { Write-Host $i }
```

## <a name="see-also"></a><span data-ttu-id="63e6e-151">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="63e6e-151">SEE ALSO</span></span>

[<span data-ttu-id="63e6e-152">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="63e6e-152">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="63e6e-153">about_Foreach</span><span class="sxs-lookup"><span data-stu-id="63e6e-153">about_Foreach</span></span>](about_Foreach.md)
