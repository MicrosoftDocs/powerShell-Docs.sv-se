---
description: Beskriver ett språk kommando som du kan använda för att köra instruktions listor baserat på resultatet av en eller flera villkorliga tester.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_if?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_If
ms.openlocfilehash: 33c0050cb5f8c3dfa623213b288ef3a84d10099d
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270182"
---
# <a name="about-if"></a><span data-ttu-id="6b29c-104">Om</span><span class="sxs-lookup"><span data-stu-id="6b29c-104">About If</span></span>

## <a name="short-description"></a><span data-ttu-id="6b29c-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="6b29c-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="6b29c-106">Beskriver ett språk kommando som du kan använda för att köra instruktions listor baserat på resultatet av en eller flera villkorliga tester.</span><span class="sxs-lookup"><span data-stu-id="6b29c-106">Describes a language command you can use to run statement lists based on the results of one or more conditional tests.</span></span>

## <a name="long-description"></a><span data-ttu-id="6b29c-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="6b29c-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="6b29c-108">Du kan använda `If` instruktionen för att köra kodblock om ett angivet villkorligt test utvärderas till sant.</span><span class="sxs-lookup"><span data-stu-id="6b29c-108">You can use the `If` statement to run code blocks if a specified conditional test evaluates to true.</span></span> <span data-ttu-id="6b29c-109">Du kan också ange en eller flera ytterligare villkorliga tester som ska köras om alla tidigare tester utvärderas till false.</span><span class="sxs-lookup"><span data-stu-id="6b29c-109">You can also specify one or more additional conditional tests to run if all the prior tests evaluate to false.</span></span> <span data-ttu-id="6b29c-110">Slutligen kan du ange ytterligare ett kodblock som körs om inga andra tidigare villkorliga test utvärderas som sant.</span><span class="sxs-lookup"><span data-stu-id="6b29c-110">Finally, you can specify an additional code block that is run if no other prior conditional test evaluates to true.</span></span>

### <a name="syntax"></a><span data-ttu-id="6b29c-111">Syntax</span><span class="sxs-lookup"><span data-stu-id="6b29c-111">Syntax</span></span>

<span data-ttu-id="6b29c-112">I följande exempel visas `If` syntaxen för uttrycket:</span><span class="sxs-lookup"><span data-stu-id="6b29c-112">The following example shows the `If` statement syntax:</span></span>

```powershell
if (<test1>)
    {<statement list 1>}
[elseif (<test2>)
    {<statement list 2>}]
[else
    {<statement list 3>}]
```

<span data-ttu-id="6b29c-113">När du kör en `If` instruktion utvärderar PowerShell `<test1>` villkors uttrycket som sant eller falskt.</span><span class="sxs-lookup"><span data-stu-id="6b29c-113">When you run an `If` statement, PowerShell evaluates the `<test1>` conditional expression as true or false.</span></span> <span data-ttu-id="6b29c-114">Om `<test1>` är true, `<statement list 1>` körs och PowerShell avslutar `If` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="6b29c-114">If `<test1>` is true, `<statement list 1>` runs, and PowerShell exits the `If` statement.</span></span> <span data-ttu-id="6b29c-115">Om `<test1>` är falskt utvärderar PowerShell det villkor som anges av `<test2>` villkors instruktionen.</span><span class="sxs-lookup"><span data-stu-id="6b29c-115">If `<test1>` is false, PowerShell evaluates the condition specified by the `<test2>` conditional statement.</span></span>

<span data-ttu-id="6b29c-116">Om `<test2>` är true, `<statement list 2>` körs och PowerShell avslutar `If` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="6b29c-116">If `<test2>` is true, `<statement list 2>` runs, and PowerShell exits the `If` statement.</span></span> <span data-ttu-id="6b29c-117">Om både `<test1>` och `<test2>` utvärderas till false `<statement list 3` körs det> kod blocket och PowerShell avslutar IF-instruktionen.</span><span class="sxs-lookup"><span data-stu-id="6b29c-117">If both `<test1>` and `<test2>` evaluate to false, the `<statement list 3`> code block runs, and PowerShell exits the If statement.</span></span>

<span data-ttu-id="6b29c-118">Du kan använda flera ElseIf-instruktioner för att kedja samman en serie villkorliga tester.</span><span class="sxs-lookup"><span data-stu-id="6b29c-118">You can use multiple Elseif statements to chain a series of conditional tests.</span></span> <span data-ttu-id="6b29c-119">Så att varje test bara körs om alla tidigare tester är falska.</span><span class="sxs-lookup"><span data-stu-id="6b29c-119">So, that each test is run only if all the previous tests are false.</span></span>
<span data-ttu-id="6b29c-120">Om du behöver skapa en `If` instruktion som innehåller många ElseIf-instruktioner bör du använda en switch-instruktion i stället.</span><span class="sxs-lookup"><span data-stu-id="6b29c-120">If you need to create an `If` statement that contains many Elseif statements, consider using a Switch statement instead.</span></span>

<span data-ttu-id="6b29c-121">Exempel:</span><span class="sxs-lookup"><span data-stu-id="6b29c-121">Examples:</span></span>

<span data-ttu-id="6b29c-122">Den enklaste `If` instruktionen innehåller ett enda kommando och innehåller inte några ElseIf-instruktioner eller andra instruktioner.</span><span class="sxs-lookup"><span data-stu-id="6b29c-122">The simplest `If` statement contains a single command and does not contain any Elseif statements or any Else statements.</span></span> <span data-ttu-id="6b29c-123">I följande exempel visas den enklaste formen av `If` instruktionen:</span><span class="sxs-lookup"><span data-stu-id="6b29c-123">The following example shows the simplest form of the `If` statement:</span></span>

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
```

<span data-ttu-id="6b29c-124">I det här exemplet, om variabeln $a är större än 2, utvärderas villkoret till sant och instruktions listan körs.</span><span class="sxs-lookup"><span data-stu-id="6b29c-124">In this example, if the $a variable is greater than 2, the condition evaluates to true, and the statement list runs.</span></span> <span data-ttu-id="6b29c-125">Men om $a är mindre än eller lika med 2 eller inte är en befintlig variabel `If` visas inget meddelande i instruktionen.</span><span class="sxs-lookup"><span data-stu-id="6b29c-125">However, if $a is less than or equal to 2 or is not an existing variable, the `If` statement does not display a message.</span></span>

<span data-ttu-id="6b29c-126">Genom att lägga till en Else-instruktion visas ett meddelande när $a är mindre än eller lika med 2.</span><span class="sxs-lookup"><span data-stu-id="6b29c-126">By adding an Else statement, a message is displayed when $a is less than or equal to 2.</span></span> <span data-ttu-id="6b29c-127">Som nästa exempel visar:</span><span class="sxs-lookup"><span data-stu-id="6b29c-127">As the next example shows:</span></span>

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
else {
    Write-Host ("The value $a is less than or equal to 2," +
        " is not created or is not initialized.")
}
```

<span data-ttu-id="6b29c-128">För att ytterligare förfina det här exemplet kan du använda ElseIf-instruktionen för att visa ett meddelande när värdet för $a är lika med 2.</span><span class="sxs-lookup"><span data-stu-id="6b29c-128">To further refine this example, you can use the Elseif statement to display a message when the value of $a is equal to 2.</span></span> <span data-ttu-id="6b29c-129">Som nästa exempel visar:</span><span class="sxs-lookup"><span data-stu-id="6b29c-129">As the next example shows:</span></span>

```powershell
if ($a -gt 2) {
    Write-Host "The value $a is greater than 2."
}
elseif ($a -eq 2) {
    Write-Host "The value $a is equal to 2."
}
else {
    Write-Host ("The value $a is less than 2 or" +
        " was not created or initialized.")
}
```

### <a name="using-the-ternary-operator-syntax"></a><span data-ttu-id="6b29c-130">Använda syntaxen för ternär operator</span><span class="sxs-lookup"><span data-stu-id="6b29c-130">Using the ternary operator syntax</span></span>

<span data-ttu-id="6b29c-131">PowerShell 7,0 introducerade en ny syntax med ternär operatorn.</span><span class="sxs-lookup"><span data-stu-id="6b29c-131">PowerShell 7.0 introduced a new syntax using the ternary operator.</span></span> <span data-ttu-id="6b29c-132">Det följer syntaxen för C# ternär operator:</span><span class="sxs-lookup"><span data-stu-id="6b29c-132">It follows the C# ternary operator syntax:</span></span>

```Syntax
<condition> ? <if-true> : <if-false>
```

<span data-ttu-id="6b29c-133">Ternär operatorn beter sig som den förenklade `if-else` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="6b29c-133">The ternary operator behaves like the simplified `if-else` statement.</span></span> <span data-ttu-id="6b29c-134">`<condition>`Uttrycket utvärderas och resultatet konverteras till ett booleskt värde för att avgöra vilken gren som ska utvärderas härnäst:</span><span class="sxs-lookup"><span data-stu-id="6b29c-134">The `<condition>` expression is evaluated and the result is converted to a boolean to determine which branch should be evaluated next:</span></span>

- <span data-ttu-id="6b29c-135">`<if-true>`Uttrycket körs om `<condition>` uttrycket är sant</span><span class="sxs-lookup"><span data-stu-id="6b29c-135">The `<if-true>` expression is executed if the `<condition>` expression is true</span></span>
- <span data-ttu-id="6b29c-136">`<if-false>`Uttrycket körs om `<condition>` uttrycket är falskt</span><span class="sxs-lookup"><span data-stu-id="6b29c-136">The `<if-false>` expression is executed if the `<condition>` expression is false</span></span>

<span data-ttu-id="6b29c-137">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="6b29c-137">For example:</span></span>

```powershell
$message = (Test-Path $path) ? "Path exists" : "Path not found"
```

<span data-ttu-id="6b29c-138">I det här exemplet `$message` finns värdet "sökväg finns" när `Test-Path` returnerar `$true` .</span><span class="sxs-lookup"><span data-stu-id="6b29c-138">In this example, the value of `$message` is "Path exists" when `Test-Path` returns `$true`.</span></span> <span data-ttu-id="6b29c-139">När `Test-Path` returnerar returneras `$false` `$message` "sökvägen hittades inte".</span><span class="sxs-lookup"><span data-stu-id="6b29c-139">When `Test-Path` returns `$false`, the value of `$message` is "Path not found".</span></span>

```powershell
$service = Get-Service BITS
$service.Status -eq 'Running' ? (Stop-Service $service) : (Start-Service $service)
```

<span data-ttu-id="6b29c-140">I det här exemplet, om tjänsten körs, stoppas den, och om dess **status inte är igång startas** den.</span><span class="sxs-lookup"><span data-stu-id="6b29c-140">In this example, if the service is running, it is stopped, and if its status is not **Running** , it is started.</span></span>

## <a name="see-also"></a><span data-ttu-id="6b29c-141">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="6b29c-141">SEE ALSO</span></span>

[<span data-ttu-id="6b29c-142">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="6b29c-142">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="6b29c-143">about_Switch</span><span class="sxs-lookup"><span data-stu-id="6b29c-143">about_Switch</span></span>](about_Switch.md)

