---
ms.date: 09/06/2019
keywords: powershell,cmdlet
title: What's New in the PowerShell 5.0 ISE
ms.openlocfilehash: 8f15e99c5a6ae33aeae9bd33eb0cf58fb27e3b90
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416642"
---
# <a name="whats-new-in-the-windows-powershell-50-ise"></a><span data-ttu-id="00246-103">What's New in the Windows PowerShell 5.0 ISE</span><span class="sxs-lookup"><span data-stu-id="00246-103">What's New in the Windows PowerShell 5.0 ISE</span></span>

<span data-ttu-id="00246-104">This topic explains the new and updated features that have been introduced in version 5.0 of the Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="00246-104">This topic explains the new and updated features that have been introduced in version 5.0 of the Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

> [!NOTE]
> <span data-ttu-id="00246-105">The PowerShell ISE is no longer in active feature development.</span><span class="sxs-lookup"><span data-stu-id="00246-105">The PowerShell ISE is no longer in active feature development.</span></span> <span data-ttu-id="00246-106">As a shipping component of Windows, it continues to be officially supported for security and high-priority servicing fixes.</span><span class="sxs-lookup"><span data-stu-id="00246-106">As a shipping component of Windows, it continues to be officially supported for security and high-priority servicing fixes.</span></span>
> <span data-ttu-id="00246-107">We currently have no plans to remove the ISE from Windows.</span><span class="sxs-lookup"><span data-stu-id="00246-107">We currently have no plans to remove the ISE from Windows.</span></span>
>
> <span data-ttu-id="00246-108">There is no support for the ISE in PowerShell v6 and beyond.</span><span class="sxs-lookup"><span data-stu-id="00246-108">There is no support for the ISE in PowerShell v6 and beyond.</span></span> <span data-ttu-id="00246-109">Users looking for replacement for the ISE should use [Visual Studio Code](https://code.visualstudio.com/) with the [PowerShell Extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell).</span><span class="sxs-lookup"><span data-stu-id="00246-109">Users looking for replacement for the ISE should use [Visual Studio Code](https://code.visualstudio.com/) with the [PowerShell Extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell).</span></span>

## <a name="feature-description"></a><span data-ttu-id="00246-110">Funktionsbeskrivning</span><span class="sxs-lookup"><span data-stu-id="00246-110">Feature description</span></span>

<span data-ttu-id="00246-111">The Windows PowerShell ISE is a host application that enables you to write, run, and test scripts and modules in a graphical and intuitive environment.</span><span class="sxs-lookup"><span data-stu-id="00246-111">The Windows PowerShell ISE is a host application that enables you to write, run, and test scripts and modules in a graphical and intuitive environment.</span></span> <span data-ttu-id="00246-112">Key features such as syntax-coloring, tab completion, visual debugging, Unicode compliance, and context-sensitive Help provide a rich scripting experience.</span><span class="sxs-lookup"><span data-stu-id="00246-112">Key features such as syntax-coloring, tab completion, visual debugging, Unicode compliance, and context-sensitive Help provide a rich scripting experience.</span></span>

<span data-ttu-id="00246-113">For more information, see [Introducing the Windows PowerShell ISE](../components/ise/Introducing-the-Windows-PowerShell-ISE.md).</span><span class="sxs-lookup"><span data-stu-id="00246-113">For more information, see [Introducing the Windows PowerShell ISE](../components/ise/Introducing-the-Windows-PowerShell-ISE.md).</span></span>

<span data-ttu-id="00246-114">The following table lists the new and changed features for this release of Windows PowerShell ISE in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="00246-114">The following table lists the new and changed features for this release of Windows PowerShell ISE in Windows PowerShell.</span></span>

## <a name="intellisense"></a><span data-ttu-id="00246-115">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="00246-115">IntelliSense</span></span>

> <span data-ttu-id="00246-116">Added in ISE 3.0</span><span class="sxs-lookup"><span data-stu-id="00246-116">Added in ISE 3.0</span></span>

<span data-ttu-id="00246-117">IntelliSense is an automatic-completion assistance feature that is part of Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="00246-117">IntelliSense is an automatic-completion assistance feature that is part of Windows PowerShell ISE.</span></span>
<span data-ttu-id="00246-118">IntelliSense displays clickable menus of potentially matching cmdlets, parameters, parameter values, files, or folders as you type.</span><span class="sxs-lookup"><span data-stu-id="00246-118">IntelliSense displays clickable menus of potentially matching cmdlets, parameters, parameter values, files, or folders as you type.</span></span>

<span data-ttu-id="00246-119">**What value does this change add?**</span><span class="sxs-lookup"><span data-stu-id="00246-119">**What value does this change add?**</span></span>

<span data-ttu-id="00246-120">With the addition of IntelliSense, it's easier to discover cmdlets and syntax when you use Windows PowerShell ISE to create scripts.</span><span class="sxs-lookup"><span data-stu-id="00246-120">With the addition of IntelliSense, it's easier to discover cmdlets and syntax when you use Windows PowerShell ISE to create scripts.</span></span> <span data-ttu-id="00246-121">You can also use Windows PowerShell ISE to learn Windows PowerShell while you create new scripts.</span><span class="sxs-lookup"><span data-stu-id="00246-121">You can also use Windows PowerShell ISE to learn Windows PowerShell while you create new scripts.</span></span>

<span data-ttu-id="00246-122">**What works differently?**</span><span class="sxs-lookup"><span data-stu-id="00246-122">**What works differently?**</span></span>

<span data-ttu-id="00246-123">When you type cmdlets in the Windows PowerShell ISE, a scrollable and clickable menu displays, allowing you to browse and select the appropriate commands.</span><span class="sxs-lookup"><span data-stu-id="00246-123">When you type cmdlets in the Windows PowerShell ISE, a scrollable and clickable menu displays, allowing you to browse and select the appropriate commands.</span></span>

## <a name="snippets"></a><span data-ttu-id="00246-124">Snippets</span><span class="sxs-lookup"><span data-stu-id="00246-124">Snippets</span></span>

> <span data-ttu-id="00246-125">Added in ISE 3.0</span><span class="sxs-lookup"><span data-stu-id="00246-125">Added in ISE 3.0</span></span>

<span data-ttu-id="00246-126">*Snippets* are short sections of Windows PowerShell code that you can insert into the scripts you create in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="00246-126">*Snippets* are short sections of Windows PowerShell code that you can insert into the scripts you create in Windows PowerShell ISE.</span></span> <span data-ttu-id="00246-127">Windows PowerShell ISE comes with a default set of snippets.</span><span class="sxs-lookup"><span data-stu-id="00246-127">Windows PowerShell ISE comes with a default set of snippets.</span></span> <span data-ttu-id="00246-128">You can add snippets by using the `New-Snippet` cmdlet while working in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="00246-128">You can add snippets by using the `New-Snippet` cmdlet while working in Windows PowerShell ISE.</span></span>

<span data-ttu-id="00246-129">**What value does this change add?**</span><span class="sxs-lookup"><span data-stu-id="00246-129">**What value does this change add?**</span></span>

<span data-ttu-id="00246-130">By using snippets, you can quickly assemble and create scripts to automate your environment.</span><span class="sxs-lookup"><span data-stu-id="00246-130">By using snippets, you can quickly assemble and create scripts to automate your environment.</span></span>

<span data-ttu-id="00246-131">**What works differently?**</span><span class="sxs-lookup"><span data-stu-id="00246-131">**What works differently?**</span></span>

<span data-ttu-id="00246-132">To use snippets in Windows PowerShell 3.0 or later, on the **Edit** menu, click **Start Snippets**, or press <kbd>Ctrl</kbd>+<kbd>J</kbd>.</span><span class="sxs-lookup"><span data-stu-id="00246-132">To use snippets in Windows PowerShell 3.0 or later, on the **Edit** menu, click **Start Snippets**, or press <kbd>Ctrl</kbd>+<kbd>J</kbd>.</span></span>

## <a name="add-on-tools"></a><span data-ttu-id="00246-133">Add-on tools</span><span class="sxs-lookup"><span data-stu-id="00246-133">Add-on tools</span></span>

> <span data-ttu-id="00246-134">Added in PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="00246-134">Added in PowerShell 3.0</span></span>

<span data-ttu-id="00246-135">Windows PowerShell ISE now supports add-on tools using the object model.</span><span class="sxs-lookup"><span data-stu-id="00246-135">Windows PowerShell ISE now supports add-on tools using the object model.</span></span> <span data-ttu-id="00246-136">These add-ons are Windows Presentation Foundation (WPF) controls that are displayed as a vertical or horizontal pane in the console.</span><span class="sxs-lookup"><span data-stu-id="00246-136">These add-ons are Windows Presentation Foundation (WPF) controls that are displayed as a vertical or horizontal pane in the console.</span></span> <span data-ttu-id="00246-137">Multiple add-on tools in a pane are displayed as a tabbed control.</span><span class="sxs-lookup"><span data-stu-id="00246-137">Multiple add-on tools in a pane are displayed as a tabbed control.</span></span> <span data-ttu-id="00246-138">You can also add or remove add-on tools that are produced by non-Microsoft parties.</span><span class="sxs-lookup"><span data-stu-id="00246-138">You can also add or remove add-on tools that are produced by non-Microsoft parties.</span></span> <span data-ttu-id="00246-139">For more information, see [The Purpose of the Windows PowerShell ISE Scripting Object Model](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md).</span><span class="sxs-lookup"><span data-stu-id="00246-139">For more information, see [The Purpose of the Windows PowerShell ISE Scripting Object Model](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md).</span></span>

<span data-ttu-id="00246-140">**What value does this change add?**</span><span class="sxs-lookup"><span data-stu-id="00246-140">**What value does this change add?**</span></span>

<span data-ttu-id="00246-141">Add-ons allow you to extend and customize Windows PowerShell ISE with tools that add functionality and enhance your scripting experience.</span><span class="sxs-lookup"><span data-stu-id="00246-141">Add-ons allow you to extend and customize Windows PowerShell ISE with tools that add functionality and enhance your scripting experience.</span></span>

<span data-ttu-id="00246-142">**What works differently?**</span><span class="sxs-lookup"><span data-stu-id="00246-142">**What works differently?**</span></span>

<span data-ttu-id="00246-143">Windows PowerShell ISE 3.0 and later come with the **Commands** add-on.</span><span class="sxs-lookup"><span data-stu-id="00246-143">Windows PowerShell ISE 3.0 and later come with the **Commands** add-on.</span></span> <span data-ttu-id="00246-144">The **Commands** add-on allows you to browse cmdlets, and access help about the cmdlets side-by-side with the **Script** and **Console** Panes.</span><span class="sxs-lookup"><span data-stu-id="00246-144">The **Commands** add-on allows you to browse cmdlets, and access help about the cmdlets side-by-side with the **Script** and **Console** Panes.</span></span>

<span data-ttu-id="00246-145">Additional add-ons can be found by using the **Open Add-on Tools Website** command on the **Add-ons** menu.</span><span class="sxs-lookup"><span data-stu-id="00246-145">Additional add-ons can be found by using the **Open Add-on Tools Website** command on the **Add-ons** menu.</span></span>

## <a name="restart-manager-and-auto-save"></a><span data-ttu-id="00246-146">Restart manager and auto-save</span><span class="sxs-lookup"><span data-stu-id="00246-146">Restart manager and auto-save</span></span>

> <span data-ttu-id="00246-147">Added in PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="00246-147">Added in PowerShell 3.0</span></span>

<span data-ttu-id="00246-148">Windows PowerShell ISE now automatically saves your open scripts every two minutes, in a separate location.</span><span class="sxs-lookup"><span data-stu-id="00246-148">Windows PowerShell ISE now automatically saves your open scripts every two minutes, in a separate location.</span></span> <span data-ttu-id="00246-149">When Windows PowerShell ISE restarts after an unexpected crash or reboot, it recovers scripts that were open in the last session, even if the scripts weren't saved.</span><span class="sxs-lookup"><span data-stu-id="00246-149">When Windows PowerShell ISE restarts after an unexpected crash or reboot, it recovers scripts that were open in the last session, even if the scripts weren't saved.</span></span>

<span data-ttu-id="00246-150">To change the automatic saving interval, run the following command in the Console pane: `$psise.Options.AutoSaveMinuteInterval`.</span><span class="sxs-lookup"><span data-stu-id="00246-150">To change the automatic saving interval, run the following command in the Console pane: `$psise.Options.AutoSaveMinuteInterval`.</span></span>

<span data-ttu-id="00246-151">**What value does this change add?**</span><span class="sxs-lookup"><span data-stu-id="00246-151">**What value does this change add?**</span></span>

<span data-ttu-id="00246-152">You can now work within Windows PowerShell ISE knowing that your open scripts are automatically saved.</span><span class="sxs-lookup"><span data-stu-id="00246-152">You can now work within Windows PowerShell ISE knowing that your open scripts are automatically saved.</span></span>

<span data-ttu-id="00246-153">**What works differently?**</span><span class="sxs-lookup"><span data-stu-id="00246-153">**What works differently?**</span></span>

<span data-ttu-id="00246-154">Windows PowerShell ISE 2.0 doesn't save the scripts automatically.</span><span class="sxs-lookup"><span data-stu-id="00246-154">Windows PowerShell ISE 2.0 doesn't save the scripts automatically.</span></span>

## <a name="most-recently-used-list"></a><span data-ttu-id="00246-155">Most-recently used list</span><span class="sxs-lookup"><span data-stu-id="00246-155">Most-recently used list</span></span>

> <span data-ttu-id="00246-156">Added in PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="00246-156">Added in PowerShell 3.0</span></span>

<span data-ttu-id="00246-157">Windows PowerShell ISE now has a most-recently used list for files.</span><span class="sxs-lookup"><span data-stu-id="00246-157">Windows PowerShell ISE now has a most-recently used list for files.</span></span> <span data-ttu-id="00246-158">When you open a file in Windows PowerShell ISE, the file is added to the most-recently used list on the **File** menu.</span><span class="sxs-lookup"><span data-stu-id="00246-158">When you open a file in Windows PowerShell ISE, the file is added to the most-recently used list on the **File** menu.</span></span>

<span data-ttu-id="00246-159">To change the default number of files in the most-recently used list, run the following command in the Console Pane: `$psise.Options.MruCount`.</span><span class="sxs-lookup"><span data-stu-id="00246-159">To change the default number of files in the most-recently used list, run the following command in the Console Pane: `$psise.Options.MruCount`.</span></span>

<span data-ttu-id="00246-160">**What value does this change add?**</span><span class="sxs-lookup"><span data-stu-id="00246-160">**What value does this change add?**</span></span>

<span data-ttu-id="00246-161">You can now use the most-recently used list to easily access your frequently used files.</span><span class="sxs-lookup"><span data-stu-id="00246-161">You can now use the most-recently used list to easily access your frequently used files.</span></span>

<span data-ttu-id="00246-162">**What works differently?**</span><span class="sxs-lookup"><span data-stu-id="00246-162">**What works differently?**</span></span>

<span data-ttu-id="00246-163">Windows PowerShell ISE 2.0 doesn't have a most-recently used list.</span><span class="sxs-lookup"><span data-stu-id="00246-163">Windows PowerShell ISE 2.0 doesn't have a most-recently used list.</span></span>

## <a name="console-pane"></a><span data-ttu-id="00246-164">Console Pane</span><span class="sxs-lookup"><span data-stu-id="00246-164">Console Pane</span></span>

> <span data-ttu-id="00246-165">Added in PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="00246-165">Added in PowerShell 3.0</span></span>

<span data-ttu-id="00246-166">The separate Command and Output Panes that were available in the first release of Windows PowerShell ISE have been combined into a single Console Pane.</span><span class="sxs-lookup"><span data-stu-id="00246-166">The separate Command and Output Panes that were available in the first release of Windows PowerShell ISE have been combined into a single Console Pane.</span></span> <span data-ttu-id="00246-167">The Console Pane is similar in function and appearance to a typical Windows PowerShell console, but it includes the following enhancements:</span><span class="sxs-lookup"><span data-stu-id="00246-167">The Console Pane is similar in function and appearance to a typical Windows PowerShell console, but it includes the following enhancements:</span></span>

- <span data-ttu-id="00246-168">Syntax coloring for input text (not output text), including XML syntax</span><span class="sxs-lookup"><span data-stu-id="00246-168">Syntax coloring for input text (not output text), including XML syntax</span></span>
- <span data-ttu-id="00246-169">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="00246-169">IntelliSense</span></span>
- <span data-ttu-id="00246-170">Brace matching</span><span class="sxs-lookup"><span data-stu-id="00246-170">Brace matching</span></span>
- <span data-ttu-id="00246-171">Error indication</span><span class="sxs-lookup"><span data-stu-id="00246-171">Error indication</span></span>
- <span data-ttu-id="00246-172">Full Unicode support</span><span class="sxs-lookup"><span data-stu-id="00246-172">Full Unicode support</span></span>
- <span data-ttu-id="00246-173"><kbd>F1</kbd> context-sensitive help</span><span class="sxs-lookup"><span data-stu-id="00246-173"><kbd>F1</kbd> context-sensitive help</span></span>
- <span data-ttu-id="00246-174"><kbd>Ctrl</kbd>+<kbd>F1</kbd> context-sensitive Show-Command</span><span class="sxs-lookup"><span data-stu-id="00246-174"><kbd>Ctrl</kbd>+<kbd>F1</kbd> context-sensitive Show-Command</span></span>
- <span data-ttu-id="00246-175">Complex script and right-to-left support</span><span class="sxs-lookup"><span data-stu-id="00246-175">Complex script and right-to-left support</span></span>
- <span data-ttu-id="00246-176">Font support</span><span class="sxs-lookup"><span data-stu-id="00246-176">Font support</span></span>
- <span data-ttu-id="00246-177">Zoom</span><span class="sxs-lookup"><span data-stu-id="00246-177">Zoom</span></span>
- <span data-ttu-id="00246-178">Line-select and block-select modes</span><span class="sxs-lookup"><span data-stu-id="00246-178">Line-select and block-select modes</span></span>
- <span data-ttu-id="00246-179">Preservation of typed content at the command line when you press the <kbd>UpArrow</kbd> to view history in the console</span><span class="sxs-lookup"><span data-stu-id="00246-179">Preservation of typed content at the command line when you press the <kbd>UpArrow</kbd> to view history in the console</span></span>

<span data-ttu-id="00246-180">**What value does this change add?**</span><span class="sxs-lookup"><span data-stu-id="00246-180">**What value does this change add?**</span></span>

<span data-ttu-id="00246-181">The addition of these Console Pane changes provides a scripting experience that is more consistent with the console interface.</span><span class="sxs-lookup"><span data-stu-id="00246-181">The addition of these Console Pane changes provides a scripting experience that is more consistent with the console interface.</span></span>

<span data-ttu-id="00246-182">**What works differently?**</span><span class="sxs-lookup"><span data-stu-id="00246-182">**What works differently?**</span></span>

<span data-ttu-id="00246-183">Windows PowerShell ISE 2.0 has separate Command and Output Panes.</span><span class="sxs-lookup"><span data-stu-id="00246-183">Windows PowerShell ISE 2.0 has separate Command and Output Panes.</span></span>

## <a name="command-line-switches"></a><span data-ttu-id="00246-184">Command-line switches</span><span class="sxs-lookup"><span data-stu-id="00246-184">Command-line switches</span></span>

> <span data-ttu-id="00246-185">Added in PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="00246-185">Added in PowerShell 3.0</span></span>

<span data-ttu-id="00246-186">If you start Windows PowerShell ISE from the command line (by typing **powershell_ise.exe**), you can add the following new command-line switches.</span><span class="sxs-lookup"><span data-stu-id="00246-186">If you start Windows PowerShell ISE from the command line (by typing **powershell_ise.exe**), you can add the following new command-line switches.</span></span>

- <span data-ttu-id="00246-187">`-NoProfile`: Starts Windows PowerShell ISE without running `$profile`</span><span class="sxs-lookup"><span data-stu-id="00246-187">`-NoProfile`: Starts Windows PowerShell ISE without running `$profile`</span></span>
- <span data-ttu-id="00246-188">`-Help`: Displays a Help window</span><span class="sxs-lookup"><span data-stu-id="00246-188">`-Help`: Displays a Help window</span></span>
- <span data-ttu-id="00246-189">`-mta`: Starts Windows PowerShell ISE in multithreaded apartment mode.</span><span class="sxs-lookup"><span data-stu-id="00246-189">`-mta`: Starts Windows PowerShell ISE in multithreaded apartment mode.</span></span> <span data-ttu-id="00246-190">The default operation mode for Windows PowerShell ISE is single-threaded apartment mode, or `-sta`.</span><span class="sxs-lookup"><span data-stu-id="00246-190">The default operation mode for Windows PowerShell ISE is single-threaded apartment mode, or `-sta`.</span></span>

<span data-ttu-id="00246-191">**What value does this change add?**</span><span class="sxs-lookup"><span data-stu-id="00246-191">**What value does this change add?**</span></span>

<span data-ttu-id="00246-192">The addition of these command-line switches allows you to control the environment in which the Windows PowerShell ISE runs.</span><span class="sxs-lookup"><span data-stu-id="00246-192">The addition of these command-line switches allows you to control the environment in which the Windows PowerShell ISE runs.</span></span>

<span data-ttu-id="00246-193">**What works differently?**</span><span class="sxs-lookup"><span data-stu-id="00246-193">**What works differently?**</span></span>

<span data-ttu-id="00246-194">Windows PowerShell ISE 2.0 doesn't recognize these command-line switches.</span><span class="sxs-lookup"><span data-stu-id="00246-194">Windows PowerShell ISE 2.0 doesn't recognize these command-line switches.</span></span>

## <a name="new-editor-features"></a><span data-ttu-id="00246-195">New editor features</span><span class="sxs-lookup"><span data-stu-id="00246-195">New editor features</span></span>

> <span data-ttu-id="00246-196">Added in PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="00246-196">Added in PowerShell 3.0</span></span>

<span data-ttu-id="00246-197">Other Windows PowerShell ISE editing features include:</span><span class="sxs-lookup"><span data-stu-id="00246-197">Other Windows PowerShell ISE editing features include:</span></span>

- <span data-ttu-id="00246-198">**XML syntax coloring** - Windows PowerShell ISE now colors XML syntax in the same way as it colors Windows PowerShell syntax.</span><span class="sxs-lookup"><span data-stu-id="00246-198">**XML syntax coloring** - Windows PowerShell ISE now colors XML syntax in the same way as it colors Windows PowerShell syntax.</span></span>
- <span data-ttu-id="00246-199">**Brace matching** - Windows PowerShell ISE includes brace matching and highlighting, and can be used in the following ways: (for example, using the **Go to Match** command or <kbd>Ctrl</kbd>+<kbd>]</kbd> locates the closing brace, if you have an opening brace selected).</span><span class="sxs-lookup"><span data-stu-id="00246-199">**Brace matching** - Windows PowerShell ISE includes brace matching and highlighting, and can be used in the following ways: (for example, using the **Go to Match** command or <kbd>Ctrl</kbd>+<kbd>]</kbd> locates the closing brace, if you have an opening brace selected).</span></span>
- <span data-ttu-id="00246-200">**Outline view** The Script Pane supports outlining, which allows collapsing or expanding sections of code by clicking plus or minus signs in the left margin.</span><span class="sxs-lookup"><span data-stu-id="00246-200">**Outline view** The Script Pane supports outlining, which allows collapsing or expanding sections of code by clicking plus or minus signs in the left margin.</span></span> <span data-ttu-id="00246-201">You can use braces or the `#region` and `#endregion` tags to mark the beginning or end of a collapsible section.</span><span class="sxs-lookup"><span data-stu-id="00246-201">You can use braces or the `#region` and `#endregion` tags to mark the beginning or end of a collapsible section.</span></span> <span data-ttu-id="00246-202">To expand or collapse all regions, press <kbd>Ctrl</kbd>+<kbd>M</kbd>.</span><span class="sxs-lookup"><span data-stu-id="00246-202">To expand or collapse all regions, press <kbd>Ctrl</kbd>+<kbd>M</kbd>.</span></span>
- <span data-ttu-id="00246-203">**Drag and drop text editing** - Windows PowerShell ISE now supports drag and drop text editing.</span><span class="sxs-lookup"><span data-stu-id="00246-203">**Drag and drop text editing** - Windows PowerShell ISE now supports drag and drop text editing.</span></span> <span data-ttu-id="00246-204">You can select any block of text and drag that text to another location in the editor or the console to move the text.</span><span class="sxs-lookup"><span data-stu-id="00246-204">You can select any block of text and drag that text to another location in the editor or the console to move the text.</span></span> <span data-ttu-id="00246-205">If you hold down the <kbd>Ctrl</kbd> key while you drag the selected text, when you release the mouse button the text is copied to the new location.</span><span class="sxs-lookup"><span data-stu-id="00246-205">If you hold down the <kbd>Ctrl</kbd> key while you drag the selected text, when you release the mouse button the text is copied to the new location.</span></span> <span data-ttu-id="00246-206">In this version of Windows PowerShell ISE, when you drag and drop files onto Windows PowerShell ISE, Windows PowerShell ISE opens the file.</span><span class="sxs-lookup"><span data-stu-id="00246-206">In this version of Windows PowerShell ISE, when you drag and drop files onto Windows PowerShell ISE, Windows PowerShell ISE opens the file.</span></span>
- <span data-ttu-id="00246-207">**Parse error display** - Parse errors are indicated with red underlines.</span><span class="sxs-lookup"><span data-stu-id="00246-207">**Parse error display** - Parse errors are indicated with red underlines.</span></span> <span data-ttu-id="00246-208">When you hover over an indicated error, tooltip text displays the problem that was found in the code.</span><span class="sxs-lookup"><span data-stu-id="00246-208">When you hover over an indicated error, tooltip text displays the problem that was found in the code.</span></span>
- <span data-ttu-id="00246-209">**Zoom** - The zoom percentage of the console's content can be set by using the zoom slider (in the lower right corner of Windows PowerShell ISE window), or by entering the command `$psise.options.Zoom` in the Console Pane.</span><span class="sxs-lookup"><span data-stu-id="00246-209">**Zoom** - The zoom percentage of the console's content can be set by using the zoom slider (in the lower right corner of Windows PowerShell ISE window), or by entering the command `$psise.options.Zoom` in the Console Pane.</span></span>
- <span data-ttu-id="00246-210">**Rich text copy and paste** - Copying to the clipboard in Windows PowerShell ISE preserves the font, size, and color information of the original selection.</span><span class="sxs-lookup"><span data-stu-id="00246-210">**Rich text copy and paste** - Copying to the clipboard in Windows PowerShell ISE preserves the font, size, and color information of the original selection.</span></span>
- <span data-ttu-id="00246-211">**Block selection** - You can select a block of text by holding down the <kbd>ALT</kbd> key while selecting text in the Script Pane with your mouse, or by pressing <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>Arrow</kbd>.</span><span class="sxs-lookup"><span data-stu-id="00246-211">**Block selection** - You can select a block of text by holding down the <kbd>ALT</kbd> key while selecting text in the Script Pane with your mouse, or by pressing <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>Arrow</kbd>.</span></span>

<span data-ttu-id="00246-212">**What value does this change add?**</span><span class="sxs-lookup"><span data-stu-id="00246-212">**What value does this change add?**</span></span>

<span data-ttu-id="00246-213">The additional editing features provide a more consistent and powerful editing environment.</span><span class="sxs-lookup"><span data-stu-id="00246-213">The additional editing features provide a more consistent and powerful editing environment.</span></span>

<span data-ttu-id="00246-214">**What works differently?**</span><span class="sxs-lookup"><span data-stu-id="00246-214">**What works differently?**</span></span>

<span data-ttu-id="00246-215">These editing enhancements weren't present in Windows PowerShell ISE 2.0.</span><span class="sxs-lookup"><span data-stu-id="00246-215">These editing enhancements weren't present in Windows PowerShell ISE 2.0.</span></span>

## <a name="new-help-viewer-window"></a><span data-ttu-id="00246-216">New Help viewer window</span><span class="sxs-lookup"><span data-stu-id="00246-216">New Help viewer window</span></span>

> <span data-ttu-id="00246-217">Added in PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="00246-217">Added in PowerShell 3.0</span></span>

<span data-ttu-id="00246-218">If you press <kbd>F1</kbd> when your cursor is in a cmdlet, or you have part of a cmdlet highlighted, the new Help viewer opens context-sensitive Help about the highlighted cmdlet.</span><span class="sxs-lookup"><span data-stu-id="00246-218">If you press <kbd>F1</kbd> when your cursor is in a cmdlet, or you have part of a cmdlet highlighted, the new Help viewer opens context-sensitive Help about the highlighted cmdlet.</span></span> <span data-ttu-id="00246-219">To display Windows PowerShell **About** help, type `operators` in the console pane, and then press <kbd>F1</kbd>.</span><span class="sxs-lookup"><span data-stu-id="00246-219">To display Windows PowerShell **About** help, type `operators` in the console pane, and then press <kbd>F1</kbd>.</span></span>

<span data-ttu-id="00246-220">Before you use this feature, download the most current version of Windows PowerShell Help topics from the Microsoft website.</span><span class="sxs-lookup"><span data-stu-id="00246-220">Before you use this feature, download the most current version of Windows PowerShell Help topics from the Microsoft website.</span></span> <span data-ttu-id="00246-221">The simplest method for downloading the Help topics is to run the `Update-Help` cmdlet in the Console Pane when running Windows PowerShell ISE as administrator.</span><span class="sxs-lookup"><span data-stu-id="00246-221">The simplest method for downloading the Help topics is to run the `Update-Help` cmdlet in the Console Pane when running Windows PowerShell ISE as administrator.</span></span>

<span data-ttu-id="00246-222">You can alter where the <kbd>F1</kbd> key looks for Help.</span><span class="sxs-lookup"><span data-stu-id="00246-222">You can alter where the <kbd>F1</kbd> key looks for Help.</span></span> <span data-ttu-id="00246-223">In the **Tools**/**Options** menu, on the **General Settings** tab, under **Other Settings**, you can set or clear the checkbox **Use local help content instead of online content**.</span><span class="sxs-lookup"><span data-stu-id="00246-223">In the **Tools**/**Options** menu, on the **General Settings** tab, under **Other Settings**, you can set or clear the checkbox **Use local help content instead of online content**.</span></span> <span data-ttu-id="00246-224">When checked, the client looks for the cmdlet Help in the downloaded Help found in the modules folder.</span><span class="sxs-lookup"><span data-stu-id="00246-224">When checked, the client looks for the cmdlet Help in the downloaded Help found in the modules folder.</span></span> <span data-ttu-id="00246-225">If the checkbox is cleared, the client looks for help online.</span><span class="sxs-lookup"><span data-stu-id="00246-225">If the checkbox is cleared, the client looks for help online.</span></span>

<span data-ttu-id="00246-226">**What value does this change add?**</span><span class="sxs-lookup"><span data-stu-id="00246-226">**What value does this change add?**</span></span>

<span data-ttu-id="00246-227">Context-sensitive Help without leaving your current cmdlet or script provides an integrated learning experience.</span><span class="sxs-lookup"><span data-stu-id="00246-227">Context-sensitive Help without leaving your current cmdlet or script provides an integrated learning experience.</span></span>

<span data-ttu-id="00246-228">**What works differently?**</span><span class="sxs-lookup"><span data-stu-id="00246-228">**What works differently?**</span></span>

<span data-ttu-id="00246-229">Pressing <kbd>F1</kbd> in previous versions of Windows PowerShell ISE opened the help file on the local computer.</span><span class="sxs-lookup"><span data-stu-id="00246-229">Pressing <kbd>F1</kbd> in previous versions of Windows PowerShell ISE opened the help file on the local computer.</span></span> <span data-ttu-id="00246-230">In Windows PowerShell ISE 3.0 and later, a window opens that contains the help for the cmdlet that is searchable and configurable.</span><span class="sxs-lookup"><span data-stu-id="00246-230">In Windows PowerShell ISE 3.0 and later, a window opens that contains the help for the cmdlet that is searchable and configurable.</span></span> <span data-ttu-id="00246-231">This Help experience is new for Windows PowerShell ISE 3.0, and Updatable Help is new for Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="00246-231">This Help experience is new for Windows PowerShell ISE 3.0, and Updatable Help is new for Windows PowerShell 3.0.</span></span>

## <a name="show-command-cmdlet"></a><span data-ttu-id="00246-232">Show-Command cmdlet</span><span class="sxs-lookup"><span data-stu-id="00246-232">Show-Command cmdlet</span></span>

> <span data-ttu-id="00246-233">Added in PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="00246-233">Added in PowerShell 3.0</span></span>

<span data-ttu-id="00246-234">The `Show-Command` cmdlet enables you to compose or run a cmdlet or function by filling in a graphical form.</span><span class="sxs-lookup"><span data-stu-id="00246-234">The `Show-Command` cmdlet enables you to compose or run a cmdlet or function by filling in a graphical form.</span></span> <span data-ttu-id="00246-235">The form lets users work with Windows PowerShell in a graphical environment.</span><span class="sxs-lookup"><span data-stu-id="00246-235">The form lets users work with Windows PowerShell in a graphical environment.</span></span>
<span data-ttu-id="00246-236">`Show-Command` also enables advanced scripters to create a quick Windows PowerShell-based GUI.</span><span class="sxs-lookup"><span data-stu-id="00246-236">`Show-Command` also enables advanced scripters to create a quick Windows PowerShell-based GUI.</span></span>

<span data-ttu-id="00246-237">**What value does this change add?**</span><span class="sxs-lookup"><span data-stu-id="00246-237">**What value does this change add?**</span></span>

<span data-ttu-id="00246-238">By using `Show-Command` in your Windows PowerShell scripts, you can provide your users with the graphical environment with which they're familiar.</span><span class="sxs-lookup"><span data-stu-id="00246-238">By using `Show-Command` in your Windows PowerShell scripts, you can provide your users with the graphical environment with which they're familiar.</span></span> <span data-ttu-id="00246-239">`Show-Command` can also help introductory users learn Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="00246-239">`Show-Command` can also help introductory users learn Windows PowerShell.</span></span>

<span data-ttu-id="00246-240">**What works differently?**</span><span class="sxs-lookup"><span data-stu-id="00246-240">**What works differently?**</span></span>

<span data-ttu-id="00246-241">`Show-Command` is new Windows PowerShell ISE 3.0.</span><span class="sxs-lookup"><span data-stu-id="00246-241">`Show-Command` is new Windows PowerShell ISE 3.0.</span></span>

## <a name="see-also"></a><span data-ttu-id="00246-242">Se även</span><span class="sxs-lookup"><span data-stu-id="00246-242">See also</span></span>

<span data-ttu-id="00246-243">For more information about using Windows PowerShell ISE, see [Exploring the Windows PowerShell Integrated Scripting Environment](../components/ise/exploring-the-windows-powershell-ise.md).</span><span class="sxs-lookup"><span data-stu-id="00246-243">For more information about using Windows PowerShell ISE, see [Exploring the Windows PowerShell Integrated Scripting Environment](../components/ise/exploring-the-windows-powershell-ise.md).</span></span>
