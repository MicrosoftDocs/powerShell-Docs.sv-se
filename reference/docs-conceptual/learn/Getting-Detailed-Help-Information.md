---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: Få detaljerad hjälpinformation
ms.openlocfilehash: e722eb8a0ca13e3d2de864314775a0a9fa578390
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417656"
---
# <a name="getting-detailed-help-information"></a><span data-ttu-id="0cfe8-103">Få detaljerad hjälpinformation</span><span class="sxs-lookup"><span data-stu-id="0cfe8-103">Getting detailed help information</span></span>

<span data-ttu-id="0cfe8-104">PowerShell includes detailed Help articles that explain PowerShell concepts and the PowerShell language.</span><span class="sxs-lookup"><span data-stu-id="0cfe8-104">PowerShell includes detailed Help articles that explain PowerShell concepts and the PowerShell language.</span></span> <span data-ttu-id="0cfe8-105">There are also Help articles for each cmdlet and provider and for many functions and scripts.</span><span class="sxs-lookup"><span data-stu-id="0cfe8-105">There are also Help articles for each cmdlet and provider and for many functions and scripts.</span></span>

<span data-ttu-id="0cfe8-106">You can display these Help articles at the command prompt or view the most recently updated versions of these articles in the [PowerShell](/powershell/scripting/overview) documentation online.</span><span class="sxs-lookup"><span data-stu-id="0cfe8-106">You can display these Help articles at the command prompt or view the most recently updated versions of these articles in the [PowerShell](/powershell/scripting/overview) documentation online.</span></span>

## <a name="getting-help-for-cmdlets"></a><span data-ttu-id="0cfe8-107">Getting help for cmdlets</span><span class="sxs-lookup"><span data-stu-id="0cfe8-107">Getting help for cmdlets</span></span>

<span data-ttu-id="0cfe8-108">To get Help about PowerShell cmdlets, use the [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0cfe8-108">To get Help about PowerShell cmdlets, use the [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) cmdlet.</span></span> <span data-ttu-id="0cfe8-109">For example, to get Help for the `Get-ChildItem` cmdlet, type:</span><span class="sxs-lookup"><span data-stu-id="0cfe8-109">For example, to get Help for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem
```

<span data-ttu-id="0cfe8-110">eller</span><span class="sxs-lookup"><span data-stu-id="0cfe8-110">or</span></span>

```powershell
Get-ChildItem -?
```

<span data-ttu-id="0cfe8-111">You can even get Help about the Get-Help cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0cfe8-111">You can even get Help about the Get-Help cmdlet.</span></span> <span data-ttu-id="0cfe8-112">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="0cfe8-112">For example:</span></span>

```powershell
Get-Help Get-Help
```

<span data-ttu-id="0cfe8-113">To get a list of all the cmdlet Help articles in your session, type:</span><span class="sxs-lookup"><span data-stu-id="0cfe8-113">To get a list of all the cmdlet Help articles in your session, type:</span></span>

```powershell
Get-Help -Category Cmdlet
```

<span data-ttu-id="0cfe8-114">To display one page of each Help article at a time, use the `help` function or its alias `man`.</span><span class="sxs-lookup"><span data-stu-id="0cfe8-114">To display one page of each Help article at a time, use the `help` function or its alias `man`.</span></span>
<span data-ttu-id="0cfe8-115">For example, to display Help for the `Get-ChildItem` cmdlet, type</span><span class="sxs-lookup"><span data-stu-id="0cfe8-115">For example, to display Help for the `Get-ChildItem` cmdlet, type</span></span>

```powershell
man Get-ChildItem
```

<span data-ttu-id="0cfe8-116">eller</span><span class="sxs-lookup"><span data-stu-id="0cfe8-116">or</span></span>

```powershell
help Get-ChildItem
```

<span data-ttu-id="0cfe8-117">To display detailed information, use the **Detailed** parameter of the `Get-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0cfe8-117">To display detailed information, use the **Detailed** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="0cfe8-118">For example, to get detailed information about the `Get-ChildItem` cmdlet, type:</span><span class="sxs-lookup"><span data-stu-id="0cfe8-118">For example, to get detailed information about the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Detailed
```

<span data-ttu-id="0cfe8-119">To display all content in the Help article, use the **Full** parameter of the `Get-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0cfe8-119">To display all content in the Help article, use the **Full** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="0cfe8-120">For example, to display all content in the Help article for the `Get-ChildItem` cmdlet, type:</span><span class="sxs-lookup"><span data-stu-id="0cfe8-120">For example, to display all content in the Help article for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Full
```

<span data-ttu-id="0cfe8-121">To get detailed Help about the parameters of a cmdlet, use the **Parameter** parameter of the `Get-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0cfe8-121">To get detailed Help about the parameters of a cmdlet, use the **Parameter** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="0cfe8-122">For example, to get detailed Help for all of the parameters of the `Get-ChildItem` cmdlet, type:</span><span class="sxs-lookup"><span data-stu-id="0cfe8-122">For example, to get detailed Help for all of the parameters of the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Parameter *
```

<span data-ttu-id="0cfe8-123">To display only the examples in a Help article, use the **Examples** parameter of the `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="0cfe8-123">To display only the examples in a Help article, use the **Examples** parameter of the `Get-Help`.</span></span>
<span data-ttu-id="0cfe8-124">For example, to display only the examples in the Help article for the `Get-ChildItem` cmdlet, type:</span><span class="sxs-lookup"><span data-stu-id="0cfe8-124">For example, to display only the examples in the Help article for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Examples
```

<span data-ttu-id="0cfe8-125">For information about how to write Help articles for the cmdlets that you write, see [How to Write Cmdlet Help](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).</span><span class="sxs-lookup"><span data-stu-id="0cfe8-125">For information about how to write Help articles for the cmdlets that you write, see [How to Write Cmdlet Help](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

## <a name="getting-conceptual-help"></a><span data-ttu-id="0cfe8-126">Getting conceptual help</span><span class="sxs-lookup"><span data-stu-id="0cfe8-126">Getting conceptual help</span></span>

<span data-ttu-id="0cfe8-127">The `Get-Help` cmdlet also displays information about conceptual articles in PowerShell, including articles about the PowerShell language.</span><span class="sxs-lookup"><span data-stu-id="0cfe8-127">The `Get-Help` cmdlet also displays information about conceptual articles in PowerShell, including articles about the PowerShell language.</span></span> <span data-ttu-id="0cfe8-128">Conceptual Help articles begin with the "about_" prefix, such as about_line_editing.</span><span class="sxs-lookup"><span data-stu-id="0cfe8-128">Conceptual Help articles begin with the "about_" prefix, such as about_line_editing.</span></span> <span data-ttu-id="0cfe8-129">(The name of the conceptual article must be entered in English even on non-English versions of PowerShell.)</span><span class="sxs-lookup"><span data-stu-id="0cfe8-129">(The name of the conceptual article must be entered in English even on non-English versions of PowerShell.)</span></span>

<span data-ttu-id="0cfe8-130">To display a list of conceptual articles, type:</span><span class="sxs-lookup"><span data-stu-id="0cfe8-130">To display a list of conceptual articles, type:</span></span>

```powershell
Get-Help about_*
```

<span data-ttu-id="0cfe8-131">To display a particular Help article, type the article name, for example:</span><span class="sxs-lookup"><span data-stu-id="0cfe8-131">To display a particular Help article, type the article name, for example:</span></span>

```powershell
Get-Help about_command_syntax
```

<span data-ttu-id="0cfe8-132">The parameters of `Get-Help`, such as **Detailed**, **Parameter**, and **Examples**, have no effect on the display of conceptual Help articles.</span><span class="sxs-lookup"><span data-stu-id="0cfe8-132">The parameters of `Get-Help`, such as **Detailed**, **Parameter**, and **Examples**, have no effect on the display of conceptual Help articles.</span></span>

## <a name="getting-help-about-providers"></a><span data-ttu-id="0cfe8-133">Getting help about providers</span><span class="sxs-lookup"><span data-stu-id="0cfe8-133">Getting help about providers</span></span>

<span data-ttu-id="0cfe8-134">The `Get-Help` cmdlet displays information about PowerShell providers.</span><span class="sxs-lookup"><span data-stu-id="0cfe8-134">The `Get-Help` cmdlet displays information about PowerShell providers.</span></span> <span data-ttu-id="0cfe8-135">To get Help for a provider, type `Get-Help` followed by the provider name.</span><span class="sxs-lookup"><span data-stu-id="0cfe8-135">To get Help for a provider, type `Get-Help` followed by the provider name.</span></span> <span data-ttu-id="0cfe8-136">For example, to get Help for the Registry provider, type:</span><span class="sxs-lookup"><span data-stu-id="0cfe8-136">For example, to get Help for the Registry provider, type:</span></span>

```powershell
Get-Help registry
```

<span data-ttu-id="0cfe8-137">To get a list of all the provider Help articles in your session, type</span><span class="sxs-lookup"><span data-stu-id="0cfe8-137">To get a list of all the provider Help articles in your session, type</span></span>

```powershell
Get-Help -Category provider
```

<span data-ttu-id="0cfe8-138">The parameters of `Get-Help`, such as **Detailed**, **Parameter**, and **Examples**, have no effect on the display of provider Help articles.</span><span class="sxs-lookup"><span data-stu-id="0cfe8-138">The parameters of `Get-Help`, such as **Detailed**, **Parameter**, and **Examples**, have no effect on the display of provider Help articles.</span></span>

## <a name="getting-help-about-scripts-and-functions"></a><span data-ttu-id="0cfe8-139">Getting help about scripts and functions</span><span class="sxs-lookup"><span data-stu-id="0cfe8-139">Getting help about scripts and functions</span></span>

<span data-ttu-id="0cfe8-140">Many scripts and functions in PowerShell have Help articles.</span><span class="sxs-lookup"><span data-stu-id="0cfe8-140">Many scripts and functions in PowerShell have Help articles.</span></span> <span data-ttu-id="0cfe8-141">Use the `Get-Help` cmdlet to display the Help articles for scripts and functions.</span><span class="sxs-lookup"><span data-stu-id="0cfe8-141">Use the `Get-Help` cmdlet to display the Help articles for scripts and functions.</span></span>

<span data-ttu-id="0cfe8-142">To display the Help for a function, type `Get-Help` followed by the function name.</span><span class="sxs-lookup"><span data-stu-id="0cfe8-142">To display the Help for a function, type `Get-Help` followed by the function name.</span></span> <span data-ttu-id="0cfe8-143">For example, to get Help for the `Disable-PSRemoting` function, type:</span><span class="sxs-lookup"><span data-stu-id="0cfe8-143">For example, to get Help for the `Disable-PSRemoting` function, type:</span></span>

```powershell
Get-Help Disable-PSRemoting
```

<span data-ttu-id="0cfe8-144">To display the Help for a script, type the path to the script file.</span><span class="sxs-lookup"><span data-stu-id="0cfe8-144">To display the Help for a script, type the path to the script file.</span></span> <span data-ttu-id="0cfe8-145">If the script is not in a path listed in the Path environment variable, you must use the fully qualified path.</span><span class="sxs-lookup"><span data-stu-id="0cfe8-145">If the script is not in a path listed in the Path environment variable, you must use the fully qualified path.</span></span>

<span data-ttu-id="0cfe8-146">For example, if you have a script called "TestScript.ps1" in your C:\\PS-Test directory, to display the Help article for the script, type:</span><span class="sxs-lookup"><span data-stu-id="0cfe8-146">For example, if you have a script called "TestScript.ps1" in your C:\\PS-Test directory, to display the Help article for the script, type:</span></span>

```powershell
Get-Help c:\ps-test\TestScript.ps1
```

<span data-ttu-id="0cfe8-147">The parameters that are designed for displaying cmdlet Help work for script and function Help, too.</span><span class="sxs-lookup"><span data-stu-id="0cfe8-147">The parameters that are designed for displaying cmdlet Help work for script and function Help, too.</span></span> <span data-ttu-id="0cfe8-148">However, help for functions and scripts is not shown when you run `Get-Help *`.</span><span class="sxs-lookup"><span data-stu-id="0cfe8-148">However, help for functions and scripts is not shown when you run `Get-Help *`.</span></span>

<span data-ttu-id="0cfe8-149">For information about writing Help articles for your functions and scripts, see the following articles:</span><span class="sxs-lookup"><span data-stu-id="0cfe8-149">For information about writing Help articles for your functions and scripts, see the following articles:</span></span>

- [<span data-ttu-id="0cfe8-150">about_Functions</span><span class="sxs-lookup"><span data-stu-id="0cfe8-150">about_Functions</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions)
- [<span data-ttu-id="0cfe8-151">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="0cfe8-151">about_Scripts</span></span>](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [<span data-ttu-id="0cfe8-152">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="0cfe8-152">about_Comment_Based_Help</span></span>](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)

## <a name="getting-help-online"></a><span data-ttu-id="0cfe8-153">Getting help online</span><span class="sxs-lookup"><span data-stu-id="0cfe8-153">Getting help online</span></span>

<span data-ttu-id="0cfe8-154">Viewing the Help articles online is one of the best ways to get help.</span><span class="sxs-lookup"><span data-stu-id="0cfe8-154">Viewing the Help articles online is one of the best ways to get help.</span></span> <span data-ttu-id="0cfe8-155">Online articles are easier to update and provide the most current content.</span><span class="sxs-lookup"><span data-stu-id="0cfe8-155">Online articles are easier to update and provide the most current content.</span></span>

<span data-ttu-id="0cfe8-156">To get Help online, use the **Online** parameter of the `Get-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0cfe8-156">To get Help online, use the **Online** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="0cfe8-157">All the Help articles that come with PowerShell, including provider Help and conceptual (About) Help articles, are available online in the [PowerShell](/powershell/scripting/powershell-scripting) documentation.</span><span class="sxs-lookup"><span data-stu-id="0cfe8-157">All the Help articles that come with PowerShell, including provider Help and conceptual (About) Help articles, are available online in the [PowerShell](/powershell/scripting/powershell-scripting) documentation.</span></span>

> [!NOTE]
> <span data-ttu-id="0cfe8-158">You can't use the **Online** parameter with conceptual (about_\*) or provider Help articles.</span><span class="sxs-lookup"><span data-stu-id="0cfe8-158">You can't use the **Online** parameter with conceptual (about_\*) or provider Help articles.</span></span>
> <span data-ttu-id="0cfe8-159">Online help is optional, so it does not work for every cmdlet, function, or script.</span><span class="sxs-lookup"><span data-stu-id="0cfe8-159">Online help is optional, so it does not work for every cmdlet, function, or script.</span></span>

<span data-ttu-id="0cfe8-160">For example, to get the online version of the Help article about the `Get-ChildItem` cmdlet, type:</span><span class="sxs-lookup"><span data-stu-id="0cfe8-160">For example, to get the online version of the Help article about the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Online
```

<span data-ttu-id="0cfe8-161">PowerShell opens the article in your default browser.</span><span class="sxs-lookup"><span data-stu-id="0cfe8-161">PowerShell opens the article in your default browser.</span></span> <span data-ttu-id="0cfe8-162">If online Help is supported for a Help article, you can also view the URL of the Help article.</span><span class="sxs-lookup"><span data-stu-id="0cfe8-162">If online Help is supported for a Help article, you can also view the URL of the Help article.</span></span> <span data-ttu-id="0cfe8-163">The URL appears in the Related Links section of a Help article.</span><span class="sxs-lookup"><span data-stu-id="0cfe8-163">The URL appears in the Related Links section of a Help article.</span></span>

<span data-ttu-id="0cfe8-164">For example, to see the URL for the online version of the Add-Computer cmdlet, type:</span><span class="sxs-lookup"><span data-stu-id="0cfe8-164">For example, to see the URL for the online version of the Add-Computer cmdlet, type:</span></span>

```powershell
Get-Help Add-Computer
```

<span data-ttu-id="0cfe8-165">The first line in the Related Links section of the article is shown below.</span><span class="sxs-lookup"><span data-stu-id="0cfe8-165">The first line in the Related Links section of the article is shown below.</span></span>

```Output
Online version: https://go.microsoft.com/fwlink/?LinkId=821564
```

<span data-ttu-id="0cfe8-166">For information about how to provide online support for your Help articles, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span><span class="sxs-lookup"><span data-stu-id="0cfe8-166">For information about how to provide online support for your Help articles, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

## <a name="see-also"></a><span data-ttu-id="0cfe8-167">Se även</span><span class="sxs-lookup"><span data-stu-id="0cfe8-167">See also</span></span>

- [<span data-ttu-id="0cfe8-168">about_Functions</span><span class="sxs-lookup"><span data-stu-id="0cfe8-168">about_Functions</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions)
- [<span data-ttu-id="0cfe8-169">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="0cfe8-169">about_Scripts</span></span>](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [<span data-ttu-id="0cfe8-170">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="0cfe8-170">about_Comment_Based_Help</span></span>](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)
- [<span data-ttu-id="0cfe8-171">Get-Help</span><span class="sxs-lookup"><span data-stu-id="0cfe8-171">Get-Help</span></span>](/powershell/module/microsoft.powershell.core/get-help)
