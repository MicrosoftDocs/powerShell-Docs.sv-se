---
description: Beskriver det attribut som gör att en funktion fungerar som en kompilerad cmdlet.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_CmdletBindingAttribute
ms.openlocfilehash: c76d08fd318ca4c46a745904d8f6e13f08aef9e2
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272139"
---
# <a name="about-functions-cmdletbindingattribute"></a><span data-ttu-id="be289-104">Om functions-CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="be289-104">About Functions CmdletBindingAttribute</span></span>

## <a name="short-description"></a><span data-ttu-id="be289-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="be289-105">Short description</span></span>
<span data-ttu-id="be289-106">Beskriver det attribut som gör att en funktion fungerar som en kompilerad cmdlet.</span><span class="sxs-lookup"><span data-stu-id="be289-106">Describes the attribute that makes a function work like a compiled cmdlet.</span></span>

## <a name="long-description"></a><span data-ttu-id="be289-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="be289-107">Long description</span></span>

<span data-ttu-id="be289-108">`CmdletBinding`Attributet är ett attribut med funktioner som gör att de fungerar som kompilerade cmdlets skrivna i C#.</span><span class="sxs-lookup"><span data-stu-id="be289-108">The `CmdletBinding` attribute is an attribute of functions that makes them operate like compiled cmdlets written in C#.</span></span> <span data-ttu-id="be289-109">Den ger åtkomst till funktionerna i-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="be289-109">It provides access to the features of cmdlets.</span></span>

<span data-ttu-id="be289-110">PowerShell binder parametrarna för funktioner som har `CmdletBinding` attributet på samma sätt som de binder parametrarna för kompilerade cmdlets.</span><span class="sxs-lookup"><span data-stu-id="be289-110">PowerShell binds the parameters of functions that have the `CmdletBinding` attribute in the same way that it binds the parameters of compiled cmdlets.</span></span> <span data-ttu-id="be289-111">Den `$PSCmdlet` automatiska variabeln är tillgänglig för functions med `CmdletBinding` attributet, men `$Args` variabeln är inte tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="be289-111">The `$PSCmdlet` automatic variable is available to functions with the `CmdletBinding` attribute, but the `$Args` variable is not available.</span></span>

<span data-ttu-id="be289-112">I funktioner som har `CmdletBinding` attributet, okända parametrar och positions argument som inte har några matchande positions parametrar, orsakar parameter bindningen fel.</span><span class="sxs-lookup"><span data-stu-id="be289-112">In functions that have the `CmdletBinding` attribute, unknown parameters and positional arguments that have no matching positional parameters cause parameter binding to fail.</span></span>

> [!NOTE]
> <span data-ttu-id="be289-113">Kompilerade cmdletar använder `Cmdlet` attributet som krävs, vilket liknar det `CmdletBinding` attribut som beskrivs i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="be289-113">Compiled cmdlets use the required `Cmdlet` attribute, which is similar to the `CmdletBinding` attribute that is described in this topic.</span></span>

## <a name="syntax"></a><span data-ttu-id="be289-114">Syntax</span><span class="sxs-lookup"><span data-stu-id="be289-114">Syntax</span></span>

<span data-ttu-id="be289-115">I följande exempel visas formatet för en funktion som anger alla valfria argument för `CmdletBinding` attributet.</span><span class="sxs-lookup"><span data-stu-id="be289-115">The following example shows the format of a function that specifies all the optional arguments of the `CmdletBinding` attribute.</span></span> <span data-ttu-id="be289-116">En kort beskrivning av varje argument följer det här exemplet.</span><span class="sxs-lookup"><span data-stu-id="be289-116">A brief description of each argument follows this example.</span></span>

```powershell
{
    [CmdletBinding(ConfirmImpact=<String>,
    DefaultParameterSetName=<String>,
    HelpURI=<URI>,
    SupportsPaging=<Boolean>,
    SupportsShouldProcess=<Boolean>,
    PositionalBinding=<Boolean>)]

    Param ($Parameter1)
    Begin{}
    Process{}
    End{}
}
```

## <a name="confirmimpact"></a><span data-ttu-id="be289-117">ConfirmImpact</span><span class="sxs-lookup"><span data-stu-id="be289-117">ConfirmImpact</span></span>

<span data-ttu-id="be289-118">Argumentet **ConfirmImpact** anger när funktions åtgärden ska bekräftas av ett anrop till **ShouldProcess** -metoden.</span><span class="sxs-lookup"><span data-stu-id="be289-118">The **ConfirmImpact** argument specifies when the action of the function should be confirmed by a call to the **ShouldProcess** method.</span></span> <span data-ttu-id="be289-119">Anropet till **ShouldProcess** -metoden visar bara en bekräftelse när argumentet **ConfirmImpact** är lika med eller större än värdet för `$ConfirmPreference` variabeln Preference.</span><span class="sxs-lookup"><span data-stu-id="be289-119">The call to the **ShouldProcess** method displays a confirmation prompt only when the **ConfirmImpact** argument is equal to or greater than the value of the `$ConfirmPreference` preference variable.</span></span> <span data-ttu-id="be289-120">(Standardvärdet för argumentet är **medium**.) Ange bara det här argumentet om argumentet **SupportsShouldProcess** också anges.</span><span class="sxs-lookup"><span data-stu-id="be289-120">(The default value of the argument is **Medium**.) Specify this argument only when the **SupportsShouldProcess** argument is also specified.</span></span>

<span data-ttu-id="be289-121">Mer information om bekräftelse begär Anden finns i [begära bekräftelse](/powershell/scripting/developer/cmdlet/requesting-confirmation).</span><span class="sxs-lookup"><span data-stu-id="be289-121">For more information about confirmation requests, see [Requesting Confirmation](/powershell/scripting/developer/cmdlet/requesting-confirmation).</span></span>

## <a name="defaultparametersetname"></a><span data-ttu-id="be289-122">DefaultParameterSetName</span><span class="sxs-lookup"><span data-stu-id="be289-122">DefaultParameterSetName</span></span>

<span data-ttu-id="be289-123">Argumentet **DefaultParameterSetName** anger namnet på den parameter uppsättning som PowerShell ska försöka använda när det inte går att avgöra vilken parameter som ska användas.</span><span class="sxs-lookup"><span data-stu-id="be289-123">The **DefaultParameterSetName** argument specifies the name of the parameter set that PowerShell will attempt to use when it cannot determine which parameter set to use.</span></span> <span data-ttu-id="be289-124">Du kan undvika det här problemet genom att göra den unika parametern för varje parameter inställd på en obligatorisk parameter.</span><span class="sxs-lookup"><span data-stu-id="be289-124">You can avoid this issue by making the unique parameter of each parameter set a mandatory parameter.</span></span>

## <a name="helpuri"></a><span data-ttu-id="be289-125">HelpURI</span><span class="sxs-lookup"><span data-stu-id="be289-125">HelpURI</span></span>

<span data-ttu-id="be289-126">Argumentet **HelpURI** anger Internet adressen till onlineversionen av hjälp avsnittet som beskriver funktionen.</span><span class="sxs-lookup"><span data-stu-id="be289-126">The **HelpURI** argument specifies the internet address of the online version of the help topic that describes the function.</span></span> <span data-ttu-id="be289-127">Värdet för argumentet **HelpURI** måste börja med http eller https.</span><span class="sxs-lookup"><span data-stu-id="be289-127">The value of the **HelpURI** argument must begin with "http" or "https".</span></span>

<span data-ttu-id="be289-128">Värdet för argumentet **HelpURI** används för värdet för egenskapen **HelpURI** för **CommandInfo** -objektet som `Get-Command` returneras för funktionen.</span><span class="sxs-lookup"><span data-stu-id="be289-128">The **HelpURI** argument value is used for the value of the **HelpURI** property of the **CommandInfo** object that `Get-Command` returns for the function.</span></span>

<span data-ttu-id="be289-129">Men när hjälpfiler installeras på datorn och värdet för den första länken i **RelatedLinks** -avsnittet i Hjälp filen är en URI, eller värdet för det första `.Link` direktivet i den kommenterade hjälpen är en URI, används URI: n i Hjälp filen som värde för egenskapen **HelpUri** för funktionen.</span><span class="sxs-lookup"><span data-stu-id="be289-129">However, when help files are installed on the computer and the value of the first link in the **RelatedLinks** section of the help file is a URI, or the value of the first `.Link` directive in comment-based help is a URI, the URI in the help file is used as the value of the **HelpUri** property of the function.</span></span>

<span data-ttu-id="be289-130">`Get-Help`Cmdlet: en använder värdet för egenskapen **HelpURI** för att hitta online-versionen av funktions hjälp avsnittet när du har angett en **online** -parameter `Get-Help` i ett kommando.</span><span class="sxs-lookup"><span data-stu-id="be289-130">The `Get-Help` cmdlet uses the value of the **HelpURI** property to locate the online version of the function help topic when the **Online** parameter of `Get-Help` is specified in a command.</span></span>

## <a name="supportspaging"></a><span data-ttu-id="be289-131">SupportsPaging</span><span class="sxs-lookup"><span data-stu-id="be289-131">SupportsPaging</span></span>

<span data-ttu-id="be289-132">Argumentet **SupportsPaging** lägger till de **första** , **Skip** -och **IncludeTotalCount** -parametrarna i funktionen.</span><span class="sxs-lookup"><span data-stu-id="be289-132">The **SupportsPaging** argument adds the **First** , **Skip** , and **IncludeTotalCount** parameters to the function.</span></span> <span data-ttu-id="be289-133">Med de här parametrarna kan användarna välja utdata från en mycket stor resultat uppsättning.</span><span class="sxs-lookup"><span data-stu-id="be289-133">These parameters allow users to select output from a very large result set.</span></span> <span data-ttu-id="be289-134">Det här argumentet är utformat för cmdlets och Functions som returnerar data från stora data lager som har stöd för data urval, till exempel en SQL-databas.</span><span class="sxs-lookup"><span data-stu-id="be289-134">This argument is designed for cmdlets and functions that return data from large data stores that support data selection, such as an SQL database.</span></span>

<span data-ttu-id="be289-135">Det här argumentet introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="be289-135">This argument was introduced in Windows PowerShell 3.0.</span></span>

- <span data-ttu-id="be289-136">**Första** : endast de första n-objekten hämtas.</span><span class="sxs-lookup"><span data-stu-id="be289-136">**First** : Gets only the first 'n' objects.</span></span>
- <span data-ttu-id="be289-137">**Skip** : ignorerar de första n-objekten och hämtar sedan de återstående objekten.</span><span class="sxs-lookup"><span data-stu-id="be289-137">**Skip** :  Ignores the first 'n' objects and then gets the remaining objects.</span></span>
- <span data-ttu-id="be289-138">**IncludeTotalCount** : rapporterar antalet objekt i data uppsättningen (ett heltal) följt av objekten.</span><span class="sxs-lookup"><span data-stu-id="be289-138">**IncludeTotalCount** : Reports the number of objects in the data set (an integer) followed by the objects.</span></span> <span data-ttu-id="be289-139">Om cmdleten inte kan avgöra det totala antalet returneras "okänt antal".</span><span class="sxs-lookup"><span data-stu-id="be289-139">If the cmdlet cannot determine the total count, it returns "Unknown total count".</span></span>

<span data-ttu-id="be289-140">PowerShell innehåller **NewTotalCount** , en hjälp metod som hämtar det totala Count-värdet för att returnera och innehåller en uppskattning av precisionen för det totala Count-värdet.</span><span class="sxs-lookup"><span data-stu-id="be289-140">PowerShell includes **NewTotalCount** , a helper method that gets the total count value to return and includes an estimate of the accuracy of the total count value.</span></span>

<span data-ttu-id="be289-141">Följande exempel funktion visar hur du lägger till stöd för växlings parametrarna i en avancerad funktion.</span><span class="sxs-lookup"><span data-stu-id="be289-141">The following sample function shows how to add support for the paging parameters to an advanced function.</span></span>

```powershell
function Get-Numbers {
    [CmdletBinding(SupportsPaging = $true)]
    param()

    $FirstNumber = [Math]::Min($PSCmdlet.PagingParameters.Skip, 100)
    $LastNumber = [Math]::Min($PSCmdlet.PagingParameters.First +
      $FirstNumber - 1, 100)

    if ($PSCmdlet.PagingParameters.IncludeTotalCount) {
        $TotalCountAccuracy = 1.0
        $TotalCount = $PSCmdlet.PagingParameters.NewTotalCount(100,
          $TotalCountAccuracy)
        Write-Output $TotalCount
    }
    $FirstNumber .. $LastNumber | Write-Output
}
```

## <a name="supportsshouldprocess"></a><span data-ttu-id="be289-142">SupportsShouldProcess</span><span class="sxs-lookup"><span data-stu-id="be289-142">SupportsShouldProcess</span></span>

<span data-ttu-id="be289-143">Argumentet **SupportsShouldProcess** lägger till **Confirm** -och **whatIf** -parametrar i funktionen.</span><span class="sxs-lookup"><span data-stu-id="be289-143">The **SupportsShouldProcess** argument adds **Confirm** and **WhatIf** parameters to the function.</span></span> <span data-ttu-id="be289-144">Parametern **Confirm** efterfrågar användaren innan kommandot körs på varje objekt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="be289-144">The **Confirm** parameter prompts the user before it runs the command on each object in the pipeline.</span></span> <span data-ttu-id="be289-145">Parametern **whatIf** listar de ändringar som kommandot gör, i stället för att köra kommandot.</span><span class="sxs-lookup"><span data-stu-id="be289-145">The **WhatIf** parameter lists the changes that the command would make, instead of running the command.</span></span>

## <a name="positionalbinding"></a><span data-ttu-id="be289-146">PositionalBinding</span><span class="sxs-lookup"><span data-stu-id="be289-146">PositionalBinding</span></span>

<span data-ttu-id="be289-147">Argumentet **PositionalBinding** avgör om parametrar i funktionen är placerade som standard.</span><span class="sxs-lookup"><span data-stu-id="be289-147">The **PositionalBinding** argument determines whether parameters in the function are positional by default.</span></span> <span data-ttu-id="be289-148">Standardvärdet är `$True`.</span><span class="sxs-lookup"><span data-stu-id="be289-148">The default value is `$True`.</span></span> <span data-ttu-id="be289-149">Du kan använda argumentet **PositionalBinding** med värdet för `$False` att inaktivera positions bindning.</span><span class="sxs-lookup"><span data-stu-id="be289-149">You can use the **PositionalBinding** argument with a value of `$False` to disable positional binding.</span></span>

<span data-ttu-id="be289-150">**PositionalBinding** -argumentet introduceras i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="be289-150">The **PositionalBinding** argument is introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="be289-151">Parameter namnet är valfritt när parametrarna är placerade.</span><span class="sxs-lookup"><span data-stu-id="be289-151">When parameters are positional, the parameter name is optional.</span></span>
<span data-ttu-id="be289-152">PowerShell associerar parameter värden utan namn med funktions parametrarna enligt ordningen eller positionen för de värden som inte är namngivna i funktions kommandot.</span><span class="sxs-lookup"><span data-stu-id="be289-152">PowerShell associates unnamed parameter values with the function parameters according to the order or position of the unnamed parameter values in the function command.</span></span>

<span data-ttu-id="be289-153">När parametrar inte är positionerade (de är "namngivna"), krävs parameter namnet (eller en förkortning eller ett alias för namnet) i kommandot.</span><span class="sxs-lookup"><span data-stu-id="be289-153">When parameters are not positional (they are "named"), the parameter name (or an abbreviation or alias of the name) is required in the command.</span></span>

<span data-ttu-id="be289-154">När **PositionalBinding** är är `$True` funktions parametrarna placerade som standard.</span><span class="sxs-lookup"><span data-stu-id="be289-154">When **PositionalBinding** is `$True`, function parameters are positional by default.</span></span> <span data-ttu-id="be289-155">PowerShell tilldelar parametrarna positions nummer till parametrarna i den ordning som de deklareras i funktionen.</span><span class="sxs-lookup"><span data-stu-id="be289-155">PowerShell assigns position number to the parameters in the order in which they are declared in the function.</span></span>

<span data-ttu-id="be289-156">När **PositionalBinding** är `$False` funktions parametrar placeras de inte som standard.</span><span class="sxs-lookup"><span data-stu-id="be289-156">When **PositionalBinding** is `$False`, function parameters are not positional by default.</span></span> <span data-ttu-id="be289-157">Om inte **positions** argumentet för attributet **parameter** deklareras i parametern, måste parameter namnet (eller ett alias eller en förkortning) inkluderas när parametern används i en funktion.</span><span class="sxs-lookup"><span data-stu-id="be289-157">Unless the **Position** argument of the **Parameter** attribute is declared on the parameter, the parameter name (or an alias or abbreviation) must be included when the parameter is used in a function.</span></span>

<span data-ttu-id="be289-158">**Positions** argumentet för attributet **parameter** har företräde framför **PositionalBinding** -standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="be289-158">The **Position** argument of the **Parameter** attribute takes precedence over the **PositionalBinding** default value.</span></span> <span data-ttu-id="be289-159">Du kan använda argumentet **position** för att ange ett positions värde för en parameter.</span><span class="sxs-lookup"><span data-stu-id="be289-159">You can use the **Position** argument to specify a position value for a parameter.</span></span> <span data-ttu-id="be289-160">Mer information om **positions** argumentet finns [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span><span class="sxs-lookup"><span data-stu-id="be289-160">For more information about the **Position** argument, see [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

## <a name="notes"></a><span data-ttu-id="be289-161">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="be289-161">Notes</span></span>

<span data-ttu-id="be289-162">**SupportsTransactions** -argumentet stöds inte i avancerade funktioner.</span><span class="sxs-lookup"><span data-stu-id="be289-162">The **SupportsTransactions** argument is not supported in advanced functions.</span></span>

## <a name="keywords"></a><span data-ttu-id="be289-163">Nyckelord</span><span class="sxs-lookup"><span data-stu-id="be289-163">Keywords</span></span>

<span data-ttu-id="be289-164">about_Functions_CmdletBinding_Attribute</span><span class="sxs-lookup"><span data-stu-id="be289-164">about_Functions_CmdletBinding_Attribute</span></span>

## <a name="see-also"></a><span data-ttu-id="be289-165">Se även</span><span class="sxs-lookup"><span data-stu-id="be289-165">See also</span></span>

[<span data-ttu-id="be289-166">about_Functions</span><span class="sxs-lookup"><span data-stu-id="be289-166">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="be289-167">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="be289-167">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="be289-168">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="be289-168">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="be289-169">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="be289-169">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="be289-170">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="be289-170">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)
