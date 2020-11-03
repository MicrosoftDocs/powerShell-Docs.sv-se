---
description: Variabler som anpassar PowerShell-beteendet.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_preference_variables?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Preference_Variables
ms.openlocfilehash: 2f290020a66b2db15c41cc9581ae3582dda8c96d
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270038"
---
# <a name="about-preference-variables"></a><span data-ttu-id="ed9e1-104">Om Preferences-variabler</span><span class="sxs-lookup"><span data-stu-id="ed9e1-104">About Preference Variables</span></span>

## <a name="short-description"></a><span data-ttu-id="ed9e1-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="ed9e1-105">Short description</span></span>

<span data-ttu-id="ed9e1-106">Variabler som anpassar PowerShell-beteendet.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-106">Variables that customize the behavior of PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="ed9e1-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="ed9e1-107">Long description</span></span>

<span data-ttu-id="ed9e1-108">PowerShell innehåller en uppsättning variabler som gör att du kan anpassa dess beteende.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-108">PowerShell includes a set of variables that enable you to customize its behavior.</span></span> <span data-ttu-id="ed9e1-109">Dessa inställningar fungerar som alternativ i GUI-baserade system.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-109">These preference variables work like the options in GUI-based systems.</span></span>

<span data-ttu-id="ed9e1-110">Inställningarna för variabler påverkar PowerShell-operativsystemet och alla kommandon som körs i miljön.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-110">The preference variables affect the PowerShell operating environment and all commands run in the environment.</span></span> <span data-ttu-id="ed9e1-111">I många fall har cmdletarna parametrar som du kan använda för att åsidosätta inställnings beteendet för ett särskilt kommando.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-111">In many cases, the cmdlets have parameters that you can use to override the preference behavior for a specific command.</span></span>

<span data-ttu-id="ed9e1-112">I följande tabell visas inställningarna för variabler och standardvärden.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-112">The following table lists the preference variables and their default values.</span></span>

|             <span data-ttu-id="ed9e1-113">Variabel</span><span class="sxs-lookup"><span data-stu-id="ed9e1-113">Variable</span></span>             |       <span data-ttu-id="ed9e1-114">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="ed9e1-114">Default Value</span></span>       |
| -------------------------------- | ------------------------- |
| `$ConfirmPreference`             | <span data-ttu-id="ed9e1-115">Hög</span><span class="sxs-lookup"><span data-stu-id="ed9e1-115">High</span></span>                      |
| `$DebugPreference`               | <span data-ttu-id="ed9e1-116">SilentlyContinue</span><span class="sxs-lookup"><span data-stu-id="ed9e1-116">SilentlyContinue</span></span>          |
| `$ErrorActionPreference`         | <span data-ttu-id="ed9e1-117">Fortsätt</span><span class="sxs-lookup"><span data-stu-id="ed9e1-117">Continue</span></span>                  |
| `$ErrorView`                     | <span data-ttu-id="ed9e1-118">ConciseView</span><span class="sxs-lookup"><span data-stu-id="ed9e1-118">ConciseView</span></span>               |
| `$FormatEnumerationLimit`        | <span data-ttu-id="ed9e1-119">4</span><span class="sxs-lookup"><span data-stu-id="ed9e1-119">4</span></span>                         |
| `$InformationPreference`         | <span data-ttu-id="ed9e1-120">SilentlyContinue</span><span class="sxs-lookup"><span data-stu-id="ed9e1-120">SilentlyContinue</span></span>          |
| `$LogCommandHealthEvent`         | <span data-ttu-id="ed9e1-121">Falskt (ej loggad)</span><span class="sxs-lookup"><span data-stu-id="ed9e1-121">False (not logged)</span></span>        |
| `$LogCommandLifecycleEvent`      | <span data-ttu-id="ed9e1-122">Falskt (ej loggad)</span><span class="sxs-lookup"><span data-stu-id="ed9e1-122">False (not logged)</span></span>        |
| `$LogEngineHealthEvent`          | <span data-ttu-id="ed9e1-123">Sant (loggad)</span><span class="sxs-lookup"><span data-stu-id="ed9e1-123">True (logged)</span></span>             |
| `$LogEngineLifecycleEvent`       | <span data-ttu-id="ed9e1-124">Sant (loggad)</span><span class="sxs-lookup"><span data-stu-id="ed9e1-124">True (logged)</span></span>             |
| `$LogProviderLifecycleEvent`     | <span data-ttu-id="ed9e1-125">Sant (loggad)</span><span class="sxs-lookup"><span data-stu-id="ed9e1-125">True (logged)</span></span>             |
| `$LogProviderHealthEvent`        | <span data-ttu-id="ed9e1-126">Sant (loggad)</span><span class="sxs-lookup"><span data-stu-id="ed9e1-126">True (logged)</span></span>             |
| `$MaximumHistoryCount`           | <span data-ttu-id="ed9e1-127">4096</span><span class="sxs-lookup"><span data-stu-id="ed9e1-127">4096</span></span>                      |
| `$OFS`                           | <span data-ttu-id="ed9e1-128">(Tecken avstånd ( `" "` ))</span><span class="sxs-lookup"><span data-stu-id="ed9e1-128">(Space character (`" "`))</span></span> |
| `$OutputEncoding`                | <span data-ttu-id="ed9e1-129">UTF8Encoding-objekt</span><span class="sxs-lookup"><span data-stu-id="ed9e1-129">UTF8Encoding object</span></span>       |
| `$ProgressPreference`            | <span data-ttu-id="ed9e1-130">Fortsätt</span><span class="sxs-lookup"><span data-stu-id="ed9e1-130">Continue</span></span>                  |
| `$PSDefaultParameterValues`      | <span data-ttu-id="ed9e1-131">(Ingen-tom hash-tabell)</span><span class="sxs-lookup"><span data-stu-id="ed9e1-131">(None - empty hash table)</span></span> |
| `$PSEmailServer`                 | <span data-ttu-id="ed9e1-132">(Ingen)</span><span class="sxs-lookup"><span data-stu-id="ed9e1-132">(None)</span></span>                    |
| `$PSModuleAutoLoadingPreference` | <span data-ttu-id="ed9e1-133">Alla</span><span class="sxs-lookup"><span data-stu-id="ed9e1-133">All</span></span>                       |
| `$PSSessionApplicationName`      | <span data-ttu-id="ed9e1-134">WSMan</span><span class="sxs-lookup"><span data-stu-id="ed9e1-134">wsman</span></span>                     |
| `$PSSessionConfigurationName`    | `http://schemas.microsoft.com/powershell/Microsoft.PowerShell` |
| `$PSSessionOption`               | <span data-ttu-id="ed9e1-135">Se [$PSSessionOption](#pssessionoption)</span><span class="sxs-lookup"><span data-stu-id="ed9e1-135">See [$PSSessionOption](#pssessionoption)</span></span> |
| `$Transcript`                    | <span data-ttu-id="ed9e1-136">(ingen)</span><span class="sxs-lookup"><span data-stu-id="ed9e1-136">(none)</span></span>                    |
| `$VerbosePreference`             | <span data-ttu-id="ed9e1-137">SilentlyContinue</span><span class="sxs-lookup"><span data-stu-id="ed9e1-137">SilentlyContinue</span></span>          |
| `$WarningPreference`             | <span data-ttu-id="ed9e1-138">Fortsätt</span><span class="sxs-lookup"><span data-stu-id="ed9e1-138">Continue</span></span>                  |
| `$WhatIfPreference`              | <span data-ttu-id="ed9e1-139">Falskt</span><span class="sxs-lookup"><span data-stu-id="ed9e1-139">False</span></span>                     |

<span data-ttu-id="ed9e1-140">PowerShell innehåller följande miljövariabler som lagrar användar inställningar.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-140">PowerShell includes the following environment variables that store user preferences.</span></span> <span data-ttu-id="ed9e1-141">Mer information om de här miljövariablerna finns [about_Environment_Variables](about_Environment_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="ed9e1-141">For more information about these environment variables, see [about_Environment_Variables](about_Environment_Variables.md).</span></span>

- `env:PSExecutionPolicyPreference`
- `$env:PSModulePath`

> [!NOTE]
> <span data-ttu-id="ed9e1-142">Ändringar av preferens variabeln börjar bara gälla i skript och funktioner om dessa skript eller funktioner har definierats i samma omfång som den omfattning i vilken preferensen användes.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-142">Changes to preference variable only take effect in scripts and functions if those scripts or functions are defined in the same scope as the scope in which preference was used.</span></span> <span data-ttu-id="ed9e1-143">Mer information finns i [about_Scopes](about_Scopes.md).</span><span class="sxs-lookup"><span data-stu-id="ed9e1-143">For more information, see [about_Scopes](about_Scopes.md).</span></span>

## <a name="working-with-preference-variables"></a><span data-ttu-id="ed9e1-144">Arbeta med Preferences-variabler</span><span class="sxs-lookup"><span data-stu-id="ed9e1-144">Working with preference variables</span></span>

<span data-ttu-id="ed9e1-145">I det här dokumentet beskrivs var och en av inställningarna för variabler.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-145">This document describes each of the preference variables.</span></span>

<span data-ttu-id="ed9e1-146">Om du vill visa det aktuella värdet för en speciell inställnings variabel skriver du variabelns namn.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-146">To display the current value of a specific preference variable, type the variable's name.</span></span> <span data-ttu-id="ed9e1-147">Till exempel visar följande kommando `$ConfirmPreference` variabelns värde.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-147">For example, the following command displays the `$ConfirmPreference` variable's value.</span></span>

```powershell
 $ConfirmPreference
```

```Output
High
```

<span data-ttu-id="ed9e1-148">Om du vill ändra variabelns värde använder du en tilldelnings instruktion.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-148">To change a variable's value, use an assignment statement.</span></span> <span data-ttu-id="ed9e1-149">Följande uttryck ändrar till exempel `$ConfirmPreference` parameterns värde till **medium**.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-149">For example, the following statement changes the `$ConfirmPreference` parameter's value to **Medium**.</span></span>

```powershell
$ConfirmPreference = "Medium"
```

<span data-ttu-id="ed9e1-150">De värden som du anger är bara för den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-150">The values that you set are specific to the current PowerShell session.</span></span> <span data-ttu-id="ed9e1-151">Om du vill göra variablerna effektiva i alla PowerShell-sessioner lägger du till dem i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-151">To make variables effective in all PowerShell sessions, add them to your PowerShell profile.</span></span> <span data-ttu-id="ed9e1-152">Mer information finns i [about_Profiles](about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="ed9e1-152">For more information, see [about_Profiles](about_Profiles.md).</span></span>

## <a name="working-remotely"></a><span data-ttu-id="ed9e1-153">Arbeta fjärran slutet</span><span class="sxs-lookup"><span data-stu-id="ed9e1-153">Working remotely</span></span>

<span data-ttu-id="ed9e1-154">När du kör kommandon på en fjärrdator, omfattas fjärrkommandona bara av inställningarna som anges i fjärrdatorns PowerShell-klient.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-154">When you run commands on a remote computer, the remote commands are only subject to the preferences set in the remote computer's PowerShell client.</span></span> <span data-ttu-id="ed9e1-155">Om du till exempel kör ett fjärrkommando, avgör värdet för fjärrdatorns `$DebugPreference` variabel hur PowerShell svarar på fel sökning av meddelanden.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-155">For example, when you run a remote command, the value of the remote computer's `$DebugPreference` variable determines how PowerShell responds to debugging messages.</span></span>

<span data-ttu-id="ed9e1-156">Mer information om fjärrkommandon finns i [about_Remote](about_Remote.md).</span><span class="sxs-lookup"><span data-stu-id="ed9e1-156">For more information about remote commands, see [about_Remote](about_Remote.md).</span></span>

### <a name="confirmpreference"></a><span data-ttu-id="ed9e1-157">\$ConfirmPreference</span><span class="sxs-lookup"><span data-stu-id="ed9e1-157">\$ConfirmPreference</span></span>

<span data-ttu-id="ed9e1-158">Anger om PowerShell automatiskt uppmanas att bekräfta innan en cmdlet eller funktion körs.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-158">Determines whether PowerShell automatically prompts you for confirmation before running a cmdlet or function.</span></span>

<span data-ttu-id="ed9e1-159">`$ConfirmPreference`Variabelns giltiga värden är **hög** , **medel** eller **låg**.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-159">The `$ConfirmPreference` variable's valid values are **High** , **Medium** , or **Low**.</span></span> <span data-ttu-id="ed9e1-160">Cmdlets och Functions tilldelas en risk för **hög** , **medel** eller **låg**.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-160">Cmdlets and functions are assigned a risk of **High** , **Medium** , or **Low**.</span></span> <span data-ttu-id="ed9e1-161">När värdet för `$ConfirmPreference` variabeln är mindre än eller lika med den risk som tilldelats till en cmdlet eller funktion, uppmanas du automatiskt att bekräfta innan du kör cmdleten eller funktionen.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-161">When the value of the `$ConfirmPreference` variable is less than or equal to the risk assigned to a cmdlet or function, PowerShell automatically prompts you for confirmation before running the cmdlet or function.</span></span>

<span data-ttu-id="ed9e1-162">Om värdet för `$ConfirmPreference` variabeln är **none** , uppmanar PowerShell aldrig automatiskt innan du kör en cmdlet eller funktion.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-162">If the value of the `$ConfirmPreference` variable is **None** , PowerShell never automatically prompts you before running a cmdlet or function.</span></span>

<span data-ttu-id="ed9e1-163">Ändra variabelns värde om du vill ändra ett bekräftelse beteende för alla cmdletar och funktioner i sessionen `$ConfirmPreference` .</span><span class="sxs-lookup"><span data-stu-id="ed9e1-163">To change the confirming behavior for all cmdlets and functions in the session, change `$ConfirmPreference` variable's value.</span></span>

<span data-ttu-id="ed9e1-164">Om du vill åsidosätta `$ConfirmPreference` för ett enda kommando använder du en cmdlets eller funktions **Confirm** -parameter.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-164">To override the `$ConfirmPreference` for a single command, use a cmdlet's or function's **Confirm** parameter.</span></span> <span data-ttu-id="ed9e1-165">Om du vill begära bekräftelse använder du `-Confirm` .</span><span class="sxs-lookup"><span data-stu-id="ed9e1-165">To request confirmation, use `-Confirm`.</span></span> <span data-ttu-id="ed9e1-166">Använd om du vill ignorera bekräftelsen `-Confirm:$false` .</span><span class="sxs-lookup"><span data-stu-id="ed9e1-166">To suppress confirmation, use `-Confirm:$false`.</span></span>

<span data-ttu-id="ed9e1-167">Giltiga värden för `$ConfirmPreference` :</span><span class="sxs-lookup"><span data-stu-id="ed9e1-167">Valid values of `$ConfirmPreference`:</span></span>

- <span data-ttu-id="ed9e1-168">**Ingen** : PowerShell begär inte automatiskt.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-168">**None** : PowerShell doesn't prompt automatically.</span></span> <span data-ttu-id="ed9e1-169">Om du vill begära bekräftelse av ett visst kommando använder du parametern **Confirm** för cmdleten eller funktionen.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-169">To request confirmation of a particular command, use the **Confirm** parameter of the cmdlet or function.</span></span>
- <span data-ttu-id="ed9e1-170">**Låg** : PowerShell uppmanas att bekräfta innan du kör cmdletar eller Functions med låg, medel eller hög risk.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-170">**Low** : PowerShell prompts for confirmation before running cmdlets or functions with a low, medium, or high risk.</span></span>
- <span data-ttu-id="ed9e1-171">**Medium** : PowerShell upprättar en bekräftelse innan du kör cmdletar eller funktioner med medelhög eller hög risk.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-171">**Medium** : PowerShell prompts for confirmation before running cmdlets or functions with a medium, or high risk.</span></span>
- <span data-ttu-id="ed9e1-172">**Hög** : PowerShell uppmanas att bekräfta innan du kör cmdletar eller funktioner med hög risk.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-172">**High** : PowerShell prompts for confirmation before running cmdlets or functions with a high risk.</span></span>

#### <a name="detailed-explanation"></a><span data-ttu-id="ed9e1-173">Detaljerad förklaring</span><span class="sxs-lookup"><span data-stu-id="ed9e1-173">Detailed explanation</span></span>

<span data-ttu-id="ed9e1-174">PowerShell kan automatiskt uppmana dig att bekräfta innan du vidtar en åtgärd.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-174">PowerShell can automatically prompt you for confirmation before doing an action.</span></span> <span data-ttu-id="ed9e1-175">Till exempel, när cmdlet eller funktion avsevärt påverkar systemet för att ta bort data eller använda en stor mängd system resurser.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-175">For example, when cmdlet or function significantly affects the system to delete data or use a significant amount of system resources.</span></span>

```powershell
Remove-Item -Path C:\file.txt
```

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target "C:\file.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [?] Help (default is "Y"):
```

<span data-ttu-id="ed9e1-176">Uppskattningen av risken är ett attribut för cmdleten eller funktionen som kallas **ConfirmImpact**.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-176">The estimate of the risk is an attribute of the cmdlet or function known as its **ConfirmImpact**.</span></span> <span data-ttu-id="ed9e1-177">Användare kan inte ändra det.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-177">Users can't change it.</span></span>

<span data-ttu-id="ed9e1-178">Cmdlets och Functions som kan utgöra en risk för systemet har en **Confirm** -parameter som du kan använda för att begära eller ignorera bekräftelse för ett enda kommando.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-178">Cmdlets and functions that might pose a risk to the system have a **Confirm** parameter that you can use to request or suppress confirmation for a single command.</span></span>

<span data-ttu-id="ed9e1-179">Eftersom de flesta cmdletar och Functions använder standard risk värde, **ConfirmImpact** , av **medel** , och standardvärdet för `$ConfirmPreference` är **högt** , sker ingen automatisk bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-179">Because most cmdlets and functions use the default risk value, **ConfirmImpact** , of **Medium** , and the default value of `$ConfirmPreference` is **High** , automatic confirmation rarely occurs.</span></span> <span data-ttu-id="ed9e1-180">Du kan dock aktivera automatisk bekräftelse genom att ändra värdet `$ConfirmPreference` till **medel** eller **låg**.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-180">However, you can activate automatic confirmation by changing the value of `$ConfirmPreference` to **Medium** or **Low**.</span></span>

#### <a name="examples"></a><span data-ttu-id="ed9e1-181">Exempel</span><span class="sxs-lookup"><span data-stu-id="ed9e1-181">Examples</span></span>

<span data-ttu-id="ed9e1-182">I det här exemplet visas effekterna av `$ConfirmPreference` variabelns standardvärde, **hög**.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-182">This example shows the effect of the `$ConfirmPreference` variable's default value, **High**.</span></span> <span data-ttu-id="ed9e1-183">Det **höga** värdet bekräftar bara högrisk-cmdlets och functions.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-183">The **High** value only confirms high-risk cmdlets and functions.</span></span> <span data-ttu-id="ed9e1-184">Eftersom de flesta cmdletar och funktioner är medelhög risk bekräftas de inte automatiskt och `Remove-Item` tar bort filen.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-184">Since most cmdlets and functions are medium risk, they aren't automatically confirmed and `Remove-Item` deletes the file.</span></span> <span data-ttu-id="ed9e1-185">Om `-Confirm` du lägger till i kommandot uppmanas användaren att bekräfta.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-185">Adding `-Confirm` to the command prompts the user for confirmation.</span></span>

```powershell
$ConfirmPreference
```

```Output
High
```

```powershell
Remove-Item -Path C:\temp1.txt
```

<span data-ttu-id="ed9e1-186">Använd `-Confirm` för att begära bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-186">Use `-Confirm` to request confirmation.</span></span>

```powershell
Remove-Item -Path C:\temp2.txt -Confirm
```

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target "C:\temp2.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All
[?] Help (default is "Y"):
```

<span data-ttu-id="ed9e1-187">I följande exempel visas effekterna av att ändra värdet för `$ConfirmPreference` till **medium**.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-187">The following example shows the effect of changing the value of `$ConfirmPreference` to **Medium**.</span></span> <span data-ttu-id="ed9e1-188">Eftersom de flesta cmdletar och funktionen är medelhög risk bekräftas de automatiskt.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-188">Because most cmdlets and function are medium risk, they're automatically confirmed.</span></span> <span data-ttu-id="ed9e1-189">Om du inte vill att bekräftelse meddelandet för ett enskilt kommando ska visas använder du **Confirm** -parametern med värdet `$false` .</span><span class="sxs-lookup"><span data-stu-id="ed9e1-189">To suppress the confirmation prompt for a single command, use the **Confirm** parameter with a value of `$false`.</span></span>

```powershell
$ConfirmPreference = "Medium"
Remove-Item -Path C:\temp2.txt
```

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target "C:\temp2.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All
[?] Help (default is "Y"):
```

```powershell
Remove-Item -Path C:\temp3.txt -Confirm:$false
```

### <a name="debugpreference"></a><span data-ttu-id="ed9e1-190">\$DebugPreference</span><span class="sxs-lookup"><span data-stu-id="ed9e1-190">\$DebugPreference</span></span>

<span data-ttu-id="ed9e1-191">Fastställer hur PowerShell svarar på fel sökning av meddelanden som genereras av ett skript, en cmdlet eller en provider eller av ett `Write-Debug` kommando på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-191">Determines how PowerShell responds to debugging messages generated by a script, cmdlet or provider, or by a `Write-Debug` command at the command line.</span></span>

<span data-ttu-id="ed9e1-192">Vissa cmdletar visar fel söknings meddelanden, som vanligt vis är tekniska meddelanden som har utformats för programmerare och teknisk support personal.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-192">Some cmdlets display debugging messages, which are typically technical messages designed for programmers and technical support professionals.</span></span> <span data-ttu-id="ed9e1-193">Fel sökning av meddelanden visas som standard inte, men du kan visa fel söknings meddelanden genom att ändra värdet för `$DebugPreference` .</span><span class="sxs-lookup"><span data-stu-id="ed9e1-193">By default, debugging messages aren't displayed, but you can display debugging messages by changing the value of `$DebugPreference`.</span></span>

<span data-ttu-id="ed9e1-194">Du kan använda den vanliga parametern för **fel sökning** för en cmdlet för att visa eller dölja fel söknings meddelanden för ett speciellt kommando.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-194">You can use the **Debug** common parameter of a cmdlet to display or hide the debugging messages for a specific command.</span></span> <span data-ttu-id="ed9e1-195">Mer information finns i [about_CommonParameters](about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="ed9e1-195">For more information, see [about_CommonParameters](about_CommonParameters.md).</span></span>

<span data-ttu-id="ed9e1-196">Giltiga värden är följande:</span><span class="sxs-lookup"><span data-stu-id="ed9e1-196">The valid values are as follows:</span></span>

- <span data-ttu-id="ed9e1-197">**Stop** : visar fel söknings meddelandet och stoppar körningen.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-197">**Stop** : Displays the debug message and stops executing.</span></span> <span data-ttu-id="ed9e1-198">Skriver ett fel till konsolen.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-198">Writes an error to the console.</span></span>
- <span data-ttu-id="ed9e1-199">**Fråga** : visar fel söknings meddelandet och du tillfrågas om du vill fortsätta.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-199">**Inquire** : Displays the debug message and asks you whether you want to continue.</span></span> <span data-ttu-id="ed9e1-200">Om du lägger till en vanlig **fel söknings** parameter till ett kommando, och om kommandot har kon figurer ATS för att generera ett fel söknings meddelande, ändras värdet för `$DebugPreference` **Inquire** variabeln.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-200">Adding the **Debug** common parameter to a command, when the command is configured to generate a debugging message, changes the value of the `$DebugPreference` variable to **Inquire**.</span></span>
- <span data-ttu-id="ed9e1-201">**Fortsätt** : visar fel söknings meddelandet och fortsätter körningen.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-201">**Continue** : Displays the debug message and continues with execution.</span></span>
- <span data-ttu-id="ed9e1-202">**SilentlyContinue** : (standard) ingen påverkan.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-202">**SilentlyContinue** : (Default) No effect.</span></span> <span data-ttu-id="ed9e1-203">Fel söknings meddelandet visas inte och körningen fortsätter utan avbrott.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-203">The debug message isn't displayed and execution continues without interruption.</span></span>

#### <a name="examples"></a><span data-ttu-id="ed9e1-204">Exempel</span><span class="sxs-lookup"><span data-stu-id="ed9e1-204">Examples</span></span>

<span data-ttu-id="ed9e1-205">I följande exempel visas effekterna av att ändra värdena för `$DebugPreference` när ett `Write-Debug` kommando anges på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-205">The following examples show the effect of changing the values of `$DebugPreference` when a `Write-Debug` command is entered at the command line.</span></span>
<span data-ttu-id="ed9e1-206">Ändringen påverkar alla fel söknings meddelanden, inklusive meddelanden som genereras av cmdlets och skript.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-206">The change affects all debugging messages, including messages generated by cmdlets and scripts.</span></span> <span data-ttu-id="ed9e1-207">I exemplen visas **fel söknings** parametern som visar eller döljer fel söknings meddelanden som är relaterade till ett enda kommando.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-207">The examples show the **Debug** parameter, which displays or hides the debugging messages related to a single command.</span></span>

<span data-ttu-id="ed9e1-208">I det här exemplet visas effekterna av `$DebugPreference` variabelns standardvärde, **SilentlyContinue**.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-208">This example shows the effect of the `$DebugPreference` variable's default value, **SilentlyContinue**.</span></span> <span data-ttu-id="ed9e1-209">Som standard `Write-Debug` visas inte cmdletens fel söknings meddelande och bearbetningen fortsätter.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-209">By default, the `Write-Debug` cmdlet's debug message isn't displayed and processing continues.</span></span> <span data-ttu-id="ed9e1-210">När **fel söknings** parametern används åsidosätts inställningen för ett enda kommando.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-210">When the **Debug** parameter is used, it overrides the preference for a single command.</span></span> <span data-ttu-id="ed9e1-211">Fel söknings meddelandet visas.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-211">The debug message is displayed.</span></span>

```powershell
$DebugPreference
```

```Output
SilentlyContinue
```

```powershell
Write-Debug -Message "Hello, World"
```

```powershell
Write-Debug -Message "Hello, World" -Debug
```

```Output
DEBUG: Hello, World
```

<span data-ttu-id="ed9e1-212">I det här exemplet visas resultatet av `$DebugPreference` värdet **Continue** .</span><span class="sxs-lookup"><span data-stu-id="ed9e1-212">This example shows the effect of `$DebugPreference` with the **Continue** value.</span></span> <span data-ttu-id="ed9e1-213">Fel söknings meddelandet visas och kommandot fortsätter att bearbeta.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-213">The debug message is displayed and the command continues to process.</span></span>

```powershell
$DebugPreference = "Continue"
Write-Debug -Message "Hello, World"
```

```Output
DEBUG: Hello, World
```

<span data-ttu-id="ed9e1-214">I det här exemplet används **fel söknings** parametern med värdet för `$false` att utelämna meddelandet för ett enda kommando.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-214">This example uses the **Debug** parameter with a value of `$false` to suppress the message for a single command.</span></span> <span data-ttu-id="ed9e1-215">Fel söknings meddelandet visas inte.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-215">The debug message isn't displayed.</span></span>

```powershell
Write-Debug -Message "Hello, World" -Debug:$false
```

<span data-ttu-id="ed9e1-216">I det här exemplet visas hur `$DebugPreference` du ställer in till **Stop** -värdet.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-216">This example shows the effect of `$DebugPreference` being set to the **Stop** value.</span></span> <span data-ttu-id="ed9e1-217">Fel söknings meddelandet visas och kommandot stoppas.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-217">The debug message is displayed and the command is stopped.</span></span>

```powershell
$DebugPreference = "Stop"
Write-Debug -Message "Hello, World"
```

```Output
DEBUG: Hello, World
Write-Debug : The running command stopped because the preference variable
 "DebugPreference" or common parameter is set to Stop: Hello, World
At line:1 char:1
+ Write-Debug -Message "Hello, World"
```

<span data-ttu-id="ed9e1-218">I det här exemplet används **fel söknings** parametern med värdet för `$false` att utelämna meddelandet för ett enda kommando.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-218">This example uses the **Debug** parameter with a value of `$false` to suppress the message for a single command.</span></span> <span data-ttu-id="ed9e1-219">Fel söknings meddelandet visas inte och bearbetningen stoppas inte.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-219">The debug message isn't displayed and processing isn't stopped.</span></span>

```powershell
Write-Debug -Message "Hello, World" -Debug:$false
```

<span data-ttu-id="ed9e1-220">I det här exemplet visas en inverkan på `$DebugPreference` värdet för **frågan** .</span><span class="sxs-lookup"><span data-stu-id="ed9e1-220">This example shows the effect of `$DebugPreference` being set to the **Inquire** value.</span></span> <span data-ttu-id="ed9e1-221">Fel söknings meddelandet visas och användaren uppmanas att bekräfta.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-221">The debug message is displayed and the user is prompted for confirmation.</span></span>

```powershell
$DebugPreference = "Inquire"
Write-Debug -Message "Hello, World"
```

```Output
DEBUG: Hello, World

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
```

<span data-ttu-id="ed9e1-222">I det här exemplet används **fel söknings** parametern med värdet för `$false` att utelämna meddelandet för ett enda kommando.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-222">This example uses the **Debug** parameter with a value of `$false` to suppress the message for a single command.</span></span> <span data-ttu-id="ed9e1-223">Fel söknings meddelandet visas inte och bearbetningen fortsätter.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-223">The debug message isn't displayed and processing continues.</span></span>

```powershell
Write-Debug -Message "Hello, World" -Debug:$false
```

### <a name="erroractionpreference"></a><span data-ttu-id="ed9e1-224">\$ErrorActionPreference</span><span class="sxs-lookup"><span data-stu-id="ed9e1-224">\$ErrorActionPreference</span></span>

<span data-ttu-id="ed9e1-225">Fastställer hur PowerShell svarar på ett icke-avslutande fel, ett fel som inte stoppar cmdlet-bearbetningen.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-225">Determines how PowerShell responds to a non-terminating error, an error that doesn't stop the cmdlet processing.</span></span> <span data-ttu-id="ed9e1-226">Till exempel på kommando raden eller i ett skript, en cmdlet eller en provider, till exempel de fel som genereras av `Write-Error` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-226">For example, at the command line or in a script, cmdlet, or provider, such as the errors generated by the `Write-Error` cmdlet.</span></span>

<span data-ttu-id="ed9e1-227">Du kan använda en cmdlets **ErrorAction** gemensamma parameter om du vill åsidosätta inställningen för ett speciellt kommando.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-227">You can use a cmdlet's **ErrorAction** common parameter to override the preference for a specific command.</span></span>

<span data-ttu-id="ed9e1-228">Giltiga värden är följande:</span><span class="sxs-lookup"><span data-stu-id="ed9e1-228">The valid values are as follows:</span></span>

- <span data-ttu-id="ed9e1-229">**Bryt** – ange fel sökaren när ett fel inträffar eller när ett undantag utlöses.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-229">**Break** - Enter the debugger when an error occurs or when an exception is raised.</span></span>
- <span data-ttu-id="ed9e1-230">**Fortsätt** : (standard) visar fel meddelandet och fortsätter att köra.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-230">**Continue** : (Default) Displays the error message and continues executing.</span></span>
- <span data-ttu-id="ed9e1-231">**Ignore: ignorerar** fel meddelandet och fortsätter att köra kommandot.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-231">**Ignore** : Suppresses the error message and continues to execute the command.</span></span> <span data-ttu-id="ed9e1-232">**Ignore** -värdet är avsett för användning per kommando, inte för användning som Sparad inställning.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-232">The **Ignore** value is intended for per-command use, not for use as saved preference.</span></span> <span data-ttu-id="ed9e1-233">**Ignore** är inte ett giltigt värde för `$ErrorActionPreference` variabeln.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-233">**Ignore** isn't a valid value for the `$ErrorActionPreference` variable.</span></span>
- <span data-ttu-id="ed9e1-234">**Fråga** : visar fel meddelandet och du tillfrågas om du vill fortsätta.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-234">**Inquire** : Displays the error message and asks you whether you want to continue.</span></span>
- <span data-ttu-id="ed9e1-235">**SilentlyContinue** : ingen påverkan.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-235">**SilentlyContinue** : No effect.</span></span> <span data-ttu-id="ed9e1-236">Fel meddelandet visas inte och körningen fortsätter utan avbrott.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-236">The error message isn't displayed and execution continues without interruption.</span></span>
- <span data-ttu-id="ed9e1-237">**Stop** : visar fel meddelandet och stoppar körningen.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-237">**Stop** : Displays the error message and stops executing.</span></span> <span data-ttu-id="ed9e1-238">Förutom det fel som genereras genererar **Stop** -värdet ett ActionPreferenceStopException-objekt till fel strömmen.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-238">In addition to the error generated, the **Stop** value generates an ActionPreferenceStopException object to the error stream.</span></span>
  <span data-ttu-id="ed9e1-239">streama</span><span class="sxs-lookup"><span data-stu-id="ed9e1-239">stream</span></span>
- <span data-ttu-id="ed9e1-240">**Suspend** : pausar automatiskt ett arbets flödes jobb för att tillåta ytterligare undersökning.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-240">**Suspend** : Automatically suspends a workflow job to allow for further investigation.</span></span> <span data-ttu-id="ed9e1-241">Efter undersökningen kan arbets flödet återupptas.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-241">After investigation, the workflow can be resumed.</span></span> <span data-ttu-id="ed9e1-242">**Suspend** -värdet är avsett för användning per kommando, inte för användning som Sparad inställning.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-242">The **Suspend** value is intended for per-command use, not for use as saved preference.</span></span> <span data-ttu-id="ed9e1-243">**Suspend** är inte ett giltigt värde för `$ErrorActionPreference` variabeln.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-243">**Suspend** isn't a valid value for the `$ErrorActionPreference` variable.</span></span>

<span data-ttu-id="ed9e1-244">`$ErrorActionPreference` och **ErrorAction** -parametern påverkar inte hur PowerShell svarar på att avsluta fel som stoppar cmdlet-bearbetningen.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-244">`$ErrorActionPreference` and the **ErrorAction** parameter don't affect how PowerShell responds to terminating errors that stop cmdlet processing.</span></span> <span data-ttu-id="ed9e1-245">Mer information om den gemensamma parametern **ErrorAction** finns [about_CommonParameters](about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="ed9e1-245">For more information about the **ErrorAction** common parameter, see [about_CommonParameters](about_CommonParameters.md).</span></span>

#### <a name="examples"></a><span data-ttu-id="ed9e1-246">Exempel</span><span class="sxs-lookup"><span data-stu-id="ed9e1-246">Examples</span></span>

<span data-ttu-id="ed9e1-247">I de här exemplen visas effekterna av de olika värdena i `$ErrorActionPreference` variabeln.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-247">These examples show the effect of the different values of the `$ErrorActionPreference` variable.</span></span> <span data-ttu-id="ed9e1-248">Parametern **ErrorAction** används för att åsidosätta `$ErrorActionPreference` värdet.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-248">The **ErrorAction** parameter is used to override the `$ErrorActionPreference` value.</span></span>

<span data-ttu-id="ed9e1-249">Det här exemplet visar `$ErrorActionPreference` standardvärdet, **Fortsätt**.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-249">This example shows the `$ErrorActionPreference` default value, **Continue**.</span></span> <span data-ttu-id="ed9e1-250">Ett icke-avslutande fel genereras.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-250">A non-terminating error is generated.</span></span> <span data-ttu-id="ed9e1-251">Meddelandet visas och bearbetningen fortsätter.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-251">The message is displayed and processing continues.</span></span>

```powershell
# Change the ErrorActionPreference to 'Continue'
$ErrorActionPreference = 'Continue'
# Generate a non-terminating error and continue processing the script.
Write-Error -Message  'Test Error' ; Write-Host 'Hello World'
```

```Output
Write-Error: Test Error
Hello World
```

<span data-ttu-id="ed9e1-252">Det här exemplet visar `$ErrorActionPreference` standardvärdet, **fråga**.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-252">This example shows the `$ErrorActionPreference` default value, **Inquire**.</span></span> <span data-ttu-id="ed9e1-253">Ett fel genereras och en meddelande instruktion visas.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-253">An error is generated and a prompt for action is shown.</span></span>

```powershell
# Change the ErrorActionPreference to 'Inquire'
$ErrorActionPreference = 'Inquire'
Write-Error -Message 'Test Error' ; Write-Host 'Hello World'
```

```Output
Confirm
Test Error
[Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="ed9e1-254">Det här exemplet visar `$ErrorActionPreference` uppsättningen till **SilentlyContinue**.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-254">This example shows the `$ErrorActionPreference` set to **SilentlyContinue**.</span></span>
<span data-ttu-id="ed9e1-255">Fel meddelandet ignoreras.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-255">The error message is suppressed.</span></span>

```powershell
# Change the ErrorActionPreference to 'SilentlyContinue'
$ErrorActionPreference = 'SilentlyContinue'
# Generate an error message
Write-Error -Message 'Test Error' ; Write-Host 'Hello World'
# Error message is suppressed and script continues processing
```

```Output
Hello World
```

<span data-ttu-id="ed9e1-256">I det här exemplet visas `$ErrorActionPreference` mängden att **stoppa**.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-256">This example shows the `$ErrorActionPreference` set to **Stop**.</span></span> <span data-ttu-id="ed9e1-257">Det visar också det extra objekt som genererats till `$Error` variabeln.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-257">It also shows the extra object generated to the `$Error` variable.</span></span>

```powershell
# Change the ErrorActionPreference to 'Stop'
$ErrorActionPreference = 'Stop'
# Error message is is generated and script stops processing
Write-Error -Message 'Test Error' ; Write-Host 'Hello World'

# Show the ActionPreferenceStopException and the error generated
$Error[0]
$Error[1]
```

```Output
Write-Error: Test Error

ErrorRecord                 : Test Error
WasThrownFromThrowStatement : False
TargetSite                  : System.Collections.ObjectModel.Collection`1[System.Management.Automation.PSObject]
                              Invoke(System.Collections.IEnumerable)
StackTrace                  :    at System.Management.Automation.Runspaces.PipelineBase.Invoke(IEnumerable input)
                                 at Microsoft.PowerShell.Executor.ExecuteCommandHelper(Pipeline tempPipeline,
                              Exception& exceptionThrown, ExecutionOptions options)
Message                     : The running command stopped because the preference variable "ErrorActionPreference" or
                              common parameter is set to Stop: Test Error
Data                        : {System.Management.Automation.Interpreter.InterpretedFrameInfo}
InnerException              :
HelpLink                    :
Source                      : System.Management.Automation
HResult                     : -2146233087

Write-Error: Test Error
```

### <a name="errorview"></a><span data-ttu-id="ed9e1-258">\$ErrorView</span><span class="sxs-lookup"><span data-stu-id="ed9e1-258">\$ErrorView</span></span>

<span data-ttu-id="ed9e1-259">Anger visnings formatet för fel meddelanden i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-259">Determines the display format of error messages in PowerShell.</span></span>

<span data-ttu-id="ed9e1-260">Giltiga värden är följande:</span><span class="sxs-lookup"><span data-stu-id="ed9e1-260">The valid values are as follows:</span></span>

- <span data-ttu-id="ed9e1-261">**ConciseView** : (standard) ger ett koncist fel meddelande och en omfactoring-vy för avancerade modulers byggare.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-261">**ConciseView** : (Default) Provides a concise error message and a refactored view for advanced module builders.</span></span> <span data-ttu-id="ed9e1-262">Om felet är från kommando raden är det ett fel meddelande med en enda rad.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-262">If the error is from command line it's a single line error message.</span></span> <span data-ttu-id="ed9e1-263">Annars får du ett fel meddelande med flera rader som innehåller felet och en pekare till felet som visar var på raden finns.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-263">Otherwise, you receive a multiline error message that contains the error and a pointer to the error showing where it occurs in that line.</span></span> <span data-ttu-id="ed9e1-264">Om terminalen stöder virtuell terminal används ANSI Color-koder för att ange färg accent.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-264">If the terminal supports Virtual Terminal, then ANSI color codes are used to provide color accent.</span></span> <span data-ttu-id="ed9e1-265">Dekor färgen kan ändras på `$Host.PrivateData.ErrorAccentColor` .</span><span class="sxs-lookup"><span data-stu-id="ed9e1-265">The Accent color can be changed at `$Host.PrivateData.ErrorAccentColor`.</span></span> <span data-ttu-id="ed9e1-266">Använd `Get-Error` cmdlet för en utförlig detaljerad vy av det fullständigt kvalificerade felet, inklusive inre undantag.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-266">Use `Get-Error` cmdlet for a comprehensive detailed view of the fully qualified error, including inner exceptions.</span></span>

  <span data-ttu-id="ed9e1-267">**ConciseView** lades till i PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-267">**ConciseView** was added in PowerShell 7.</span></span>

- <span data-ttu-id="ed9e1-268">**NormalView** : en detaljerad vy som är avsedd för de flesta användare.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-268">**NormalView** : A detailed view designed for most users.</span></span> <span data-ttu-id="ed9e1-269">Består av en beskrivning av felet och namnet på objektet som berörs av felet.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-269">Consists of a description of the error and the name of the object involved in the error.</span></span>

- <span data-ttu-id="ed9e1-270">**CategoryView** : en kortfattad, strukturerad vy utformad för produktions miljöer.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-270">**CategoryView** : A succinct, structured view designed for production environments.</span></span> <span data-ttu-id="ed9e1-271">Formatet är följande:</span><span class="sxs-lookup"><span data-stu-id="ed9e1-271">The format is as follows:</span></span>

  <span data-ttu-id="ed9e1-272">{Category}: ({TargetName}: {TargetType}): [{Activity}], {orsak}</span><span class="sxs-lookup"><span data-stu-id="ed9e1-272">{Category}: ({TargetName}:{TargetType}):[{Activity}], {Reason}</span></span>

<span data-ttu-id="ed9e1-273">Mer information om fälten i **CategoryView** finns i [ErrorCategoryInfo](/dotnet/api/system.management.automation.errorcategoryinfo) -klassen.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-273">For more information about the fields in **CategoryView** , see [ErrorCategoryInfo](/dotnet/api/system.management.automation.errorcategoryinfo) class.</span></span>

#### <a name="examples"></a><span data-ttu-id="ed9e1-274">Exempel</span><span class="sxs-lookup"><span data-stu-id="ed9e1-274">Examples</span></span>

<span data-ttu-id="ed9e1-275">Det här exemplet visar hur ett fel visas när värdet för `$ErrorView` är standard, **ConciseView**.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-275">This example shows how an error appears when the value of `$ErrorView` is the default, **ConciseView**.</span></span> <span data-ttu-id="ed9e1-276">`Get-ChildItem` används för att hitta en katalog som inte finns.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-276">`Get-ChildItem` is used to find a non-existent directory.</span></span>

```powershell
Get-ChildItem -path 'C:\NoRealDirectory'
```

```Output
Get-ChildItem: Cannot find path 'C:\NoRealDirectory' because it does not exist.
```

<span data-ttu-id="ed9e1-277">Det här exemplet visar hur ett fel visas när värdet för `$ErrorView` är standard, **ConciseView**.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-277">This example shows how an error appears when the value of `$ErrorView` is the default, **ConciseView**.</span></span> <span data-ttu-id="ed9e1-278">`Script.ps1` körs och genererar ett fel från `Get-Item` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-278">`Script.ps1` is run and throws an error from `Get-Item` statement.</span></span>

```powershell
./Script.ps1
```

```Output
Get-Item: C:\Script.ps1
Line |
  11 | Get-Item -Path .\stuff
     | ^ Cannot find path 'C:\demo\stuff' because it does not exist.
```

<span data-ttu-id="ed9e1-279">Det här exemplet visar hur ett fel visas när värdet för `$ErrorView` ändras till **NormalView**.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-279">This example shows how an error appears when the value of `$ErrorView` is changed to **NormalView**.</span></span> <span data-ttu-id="ed9e1-280">`Get-ChildItem` används för att hitta en fil som inte finns.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-280">`Get-ChildItem` is used to find a non-existent file.</span></span>

```powershell
Get-ChildItem -Path C:\nofile.txt
```

```Output
Get-ChildItem : Cannot find path 'C:\nofile.txt' because it does not exist.
At line:1 char:1
+ Get-ChildItem -Path C:\nofile.txt
```

<span data-ttu-id="ed9e1-281">Det här exemplet visar hur samma fel visas när värdet för `$ErrorView` ändras till **CategoryView**.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-281">This example shows how the same error appears when the value of `$ErrorView` is changed to **CategoryView**.</span></span>

```powershell
$ErrorView = "CategoryView"
Get-ChildItem -Path C:\nofile.txt
```

```Output
ObjectNotFound: (C:\nofile.txt:String) [Get-ChildItem], ItemNotFoundException
```

<span data-ttu-id="ed9e1-282">Det här exemplet visar att värdet för `$ErrorView` endast påverkar fel visningen.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-282">This example demonstrates that the value of `$ErrorView` only affects the error display.</span></span> <span data-ttu-id="ed9e1-283">Den ändrar inte strukturen för det fel objekt som lagras i den `$Error` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-283">It doesn't change the structure of the error object that is stored in the `$Error` automatic variable.</span></span> <span data-ttu-id="ed9e1-284">Information om den `$Error` automatiska variabeln finns i [about_automatic_variables](about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="ed9e1-284">For information about the `$Error` automatic variable, see [about_automatic_variables](about_Automatic_Variables.md).</span></span>

<span data-ttu-id="ed9e1-285">Följande kommando tar objektet **ErrorRecord** associerat med det senaste felet i fel mat ris, **element 0** och formaterar alla fel objekts egenskaper i en lista.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-285">The following command takes the **ErrorRecord** object associated with the most recent error in the error array, **element 0** , and formats all the error object's properties in a list.</span></span>

```powershell
$Error[0] | Format-List -Property * -Force
```

```Output
PSMessageDetails      :
Exception             : System.Management.Automation.ItemNotFoundException:
                          Cannot find path 'C:\nofile.txt' because it does
                          not exist.
                        at System.Management.Automation.SessionStateInternal.
                          GetChildItems(String path, Boolean recurse, UInt32
                          depth, CmdletProviderContext context)
                        at System.Management.Automation.ChildItemCmdlet
                          ProviderIntrinsics.Get(String path, Boolean
                          recurse, UInt32 depth, CmdletProviderContext context)
                        at Microsoft.PowerShell.Commands.GetChildItemCommand.
                          ProcessRecord()
TargetObject          : C:\nofile.txt
CategoryInfo          : ObjectNotFound: (C:\nofile.txt:String) [Get-ChildItem],
                          ItemNotFoundException
FullyQualifiedErrorId : PathNotFound,
                          Microsoft.PowerShell.Commands.GetChildItemCommand
ErrorDetails          :
InvocationInfo        : System.Management.Automation.InvocationInfo
ScriptStackTrace      : at <ScriptBlock>, <No file>: line 1
PipelineIterationInfo : {0, 1}
```

### <a name="formatenumerationlimit"></a><span data-ttu-id="ed9e1-286">\$FormatEnumerationLimit</span><span class="sxs-lookup"><span data-stu-id="ed9e1-286">\$FormatEnumerationLimit</span></span>

<span data-ttu-id="ed9e1-287">Anger hur många räknade objekt som ska ingå i en visning.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-287">Determines how many enumerated items are included in a display.</span></span> <span data-ttu-id="ed9e1-288">Den här variabeln påverkar inte underliggande objekt, bara visningen.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-288">This variable doesn't affect the underlying objects, only the display.</span></span> <span data-ttu-id="ed9e1-289">När värdet för `$FormatEnumerationLimit` är färre än antalet uppräknade objekt lägger PowerShell till en ellips ( `...` ) för att visa objekt som inte visas.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-289">When the value of `$FormatEnumerationLimit` is fewer than the number of enumerated items, PowerShell adds an ellipsis (`...`) to indicate items not shown.</span></span>

<span data-ttu-id="ed9e1-290">**Giltiga värden** : heltal ( `Int32` )</span><span class="sxs-lookup"><span data-stu-id="ed9e1-290">**Valid values** : Integers (`Int32`)</span></span>

<span data-ttu-id="ed9e1-291">**Standardvärde** : 4</span><span class="sxs-lookup"><span data-stu-id="ed9e1-291">**Default value** : 4</span></span>

#### <a name="examples"></a><span data-ttu-id="ed9e1-292">Exempel</span><span class="sxs-lookup"><span data-stu-id="ed9e1-292">Examples</span></span>

<span data-ttu-id="ed9e1-293">Det här exemplet visar hur du använder `$FormatEnumerationLimit` variabeln för att förbättra visningen av räknade objekt.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-293">This example shows how to use the `$FormatEnumerationLimit` variable to improve the display of enumerated items.</span></span>

<span data-ttu-id="ed9e1-294">Kommandot i det här exemplet genererar en tabell som visar alla tjänster som körs på datorn i två grupper: en för att **köra** tjänster och en för **stoppade** tjänster.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-294">The command in this example generates a table that lists all the services running on the computer in two groups: one for **running** services and one for **stopped** services.</span></span> <span data-ttu-id="ed9e1-295">Den använder ett `Get-Service` kommando för att hämta alla tjänster och skickar sedan resultaten via pipelinen till `Group-Object` cmdleten, som grupperar resultaten efter tjänst status.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-295">It uses a `Get-Service` command to get all the services, and then sends the results through the pipeline to the `Group-Object` cmdlet, which groups the results by the service status.</span></span>

<span data-ttu-id="ed9e1-296">Resultatet är en tabell som visar statusen i kolumnen **namn** och processerna i kolumnen **grupp** .</span><span class="sxs-lookup"><span data-stu-id="ed9e1-296">The result is a table that lists the status in the **Name** column, and the processes in the **Group** column.</span></span> <span data-ttu-id="ed9e1-297">Om du vill ändra kolumn etiketterna använder du en hash-tabell, se [about_Hash_Tables](about_Hash_Tables.md).</span><span class="sxs-lookup"><span data-stu-id="ed9e1-297">To change the column labels, use a hash table, see [about_Hash_Tables](about_Hash_Tables.md).</span></span> <span data-ttu-id="ed9e1-298">Mer information finns i exemplen i [Format-Table](xref:Microsoft.PowerShell.Utility.Format-Table).</span><span class="sxs-lookup"><span data-stu-id="ed9e1-298">For more information, see the examples in [Format-Table](xref:Microsoft.PowerShell.Utility.Format-Table).</span></span>

<span data-ttu-id="ed9e1-299">Hitta det aktuella värdet för `$FormatEnumerationLimit` .</span><span class="sxs-lookup"><span data-stu-id="ed9e1-299">Find the current value of `$FormatEnumerationLimit`.</span></span>

```powershell
$FormatEnumerationLimit
```

```Output
4
```

<span data-ttu-id="ed9e1-300">Lista alla tjänster grupperade efter **status**.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-300">List all services grouped by **Status**.</span></span> <span data-ttu-id="ed9e1-301">Det finns högst fyra tjänster som anges i kolumnen **grupp** för varje status `$FormatEnumerationLimit` , eftersom har värdet **4**.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-301">There are a maximum of four services listed in the **Group** column for each status because `$FormatEnumerationLimit` has a value of **4**.</span></span>

```powershell
Get-Service | Group-Object -Property Status
```

```Output
Count  Name       Group
-----  ----       -----
60     Running    {AdtAgent, ALG, Ati HotKey Poller, AudioSrv...}
41     Stopped    {Alerter, AppMgmt, aspnet_state, ATI Smart...}
```

<span data-ttu-id="ed9e1-302">Öka värdet för till 1000 för att öka antalet objekt i listan `$FormatEnumerationLimit` . **1000**</span><span class="sxs-lookup"><span data-stu-id="ed9e1-302">To increase the number of items listed, increase the value of `$FormatEnumerationLimit` to **1000**.</span></span> <span data-ttu-id="ed9e1-303">Använd `Get-Service` och `Group-Object` för att Visa tjänsterna.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-303">Use `Get-Service` and `Group-Object` to display the services.</span></span>

```powershell
$FormatEnumerationLimit = 1000
Get-Service | Group-Object -Property Status
```

```Output
Count  Name       Group
-----  ----       -----
60     Running    {AdtAgent, ALG, Ati HotKey Poller, AudioSrv, BITS, CcmExec...
41     Stopped    {Alerter, AppMgmt, aspnet_state, ATI Smart, Browser, CiSvc...
```

<span data-ttu-id="ed9e1-304">Använd `Format-Table` med parametern **wrap** för att visa listan över tjänster.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-304">Use `Format-Table` with the **Wrap** parameter to display the list of services.</span></span>

```powershell
Get-Service | Group-Object -Property Status | Format-Table -Wrap
```

```Output
Count  Name       Group
-----  ----       -----
60     Running    {AdtAgent, ALG, Ati HotKey Poller, AudioSrv, BITS, CcmExec,
                  Client for NFS, CryptSvc, DcomLaunch, Dhcp, dmserver,
                  Dnscache, ERSvc, Eventlog, EventSystem, FwcAgent, helpsvc,
                  HidServ, IISADMIN, InoRPC, InoRT, InoTask, lanmanserver,
                  lanmanworkstation, LmHosts, MDM, Netlogon, Netman, Nla,
                  NtLmSsp, PlugPlay, PolicyAgent, ProtectedStorage, RasMan,
                  RemoteRegistry, RpcSs, SamSs, Schedule, seclogon, SENS,
                  SharedAccess, ShellHWDetection, SMT PSVC, Spooler,
                  srservice, SSDPSRV, stisvc, TapiSrv, TermService, Themes,
                  TrkWks, UMWdf, W32Time, W3SVC, WebClient, winmgmt, wscsvc,
                  wuauserv, WZCSVC, zzInterix}

41     Stopped    {Alerter, AppMgmt, aspnet_state, ATI Smart, Browser, CiSvc,
                  ClipSrv, clr_optimization_v2.0.50727_32, COMSysApp,
                  CronService, dmadmin, FastUserSwitchingCompatibility,
                  HTTPFilter, ImapiService, Mapsvc, Messenger, mnmsrvc,
                  MSDTC, MSIServer, msvsmon80, NetDDE, NetDDEdsdm, NtmsSvc,
                  NVSvc, ose, RasAuto, RDSessMgr, RemoteAccess, RpcLocator,
                  SCardSvr, SwPrv, SysmonLog, TlntSvr, upnphost, UPS, VSS,
                  WmdmPmSN, Wmi, WmiApSrv, xmlprov}
```

### <a name="informationpreference"></a><span data-ttu-id="ed9e1-305">\$InformationPreference</span><span class="sxs-lookup"><span data-stu-id="ed9e1-305">\$InformationPreference</span></span>

<span data-ttu-id="ed9e1-306">Med `$InformationPreference` variabeln kan du ange inställningar för informations ström som du vill ska visas för användarna.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-306">The `$InformationPreference` variable lets you set information stream preferences that you want displayed to users.</span></span> <span data-ttu-id="ed9e1-307">Mer specifikt, informations meddelanden som du har lagt till i kommandon eller skript genom att lägga till [Write-information-](xref:Microsoft.PowerShell.Utility.Write-Information) cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-307">Specifically, informational messages that you added to commands or scripts by adding the [Write-Information](xref:Microsoft.PowerShell.Utility.Write-Information) cmdlet.</span></span> <span data-ttu-id="ed9e1-308">Om parametern **InformationAction** används åsidosätts värdet för `$InformationPreference` variabeln.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-308">If the **InformationAction** parameter is used, its value overrides the value of the `$InformationPreference` variable.</span></span> <span data-ttu-id="ed9e1-309">`Write-Information` introducerades i PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-309">`Write-Information` was introduced in PowerShell 5.0.</span></span>

<span data-ttu-id="ed9e1-310">Giltiga värden är följande:</span><span class="sxs-lookup"><span data-stu-id="ed9e1-310">The valid values are as follows:</span></span>

- <span data-ttu-id="ed9e1-311">**Stop** : stoppar ett kommando eller skript vid en förekomst av `Write-Information` kommandot.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-311">**Stop** : Stops a command or script at an occurrence of the `Write-Information` command.</span></span>
- <span data-ttu-id="ed9e1-312">**Fråga** : visar det informations meddelande som du anger i ett `Write-Information` kommando och frågar om du vill fortsätta.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-312">**Inquire** : Displays the informational message that you specify in a `Write-Information` command, then asks whether you want to continue.</span></span>
- <span data-ttu-id="ed9e1-313">**Fortsätt** : visar informations meddelandet och fortsätter att köra.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-313">**Continue** : Displays the informational message, and continues running.</span></span>
- <span data-ttu-id="ed9e1-314">**Suspend** är bara tillgängligt för arbets flöden som inte stöds i PowerShell 6 och senare.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-314">**Suspend** is only available for workflows which aren't supported in PowerShell 6 and beyond.</span></span>
- <span data-ttu-id="ed9e1-315">**SilentlyContinue** : (standard) ingen påverkan.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-315">**SilentlyContinue** : (Default) No effect.</span></span> <span data-ttu-id="ed9e1-316">Informations meddelandena visas inte och skriptet fortsätter utan avbrott.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-316">The informational messages aren't displayed, and the script continues without interruption.</span></span>

### <a name="logevent"></a><span data-ttu-id="ed9e1-317">\$Log \*-händelse</span><span class="sxs-lookup"><span data-stu-id="ed9e1-317">\$Log\*Event</span></span>

<span data-ttu-id="ed9e1-318">Variablerna **Log \* Event** Preferences avgör vilka typer av händelser som skrivs till PowerShell-händelseloggen i Loggboken.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-318">The **Log\*Event** preference variables determine which types of events are written to the PowerShell event log in Event Viewer.</span></span> <span data-ttu-id="ed9e1-319">Som standard loggas bara motor-och leverantörs händelser.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-319">By default, only engine and provider events are logged.</span></span> <span data-ttu-id="ed9e1-320">Men du kan använda variablerna **Log \* Event** Preference för att anpassa din logg, till exempel loggnings händelser för kommandon.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-320">But, you can use the **Log\*Event** preference variables to customize your log, such as logging events about commands.</span></span>

<span data-ttu-id="ed9e1-321">Variablerna **Log \* Event** Preferences är följande:</span><span class="sxs-lookup"><span data-stu-id="ed9e1-321">The **Log\*Event** preference variables are as follows:</span></span>

- <span data-ttu-id="ed9e1-322">`$LogCommandHealthEvent`: Loggar fel och undantag vid kommando initiering och bearbetning.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-322">`$LogCommandHealthEvent`: Logs errors and exceptions in command initialization and processing.</span></span> <span data-ttu-id="ed9e1-323">Standardvärdet är `$false` (inte loggat).</span><span class="sxs-lookup"><span data-stu-id="ed9e1-323">The default is `$false` (not logged).</span></span>
- <span data-ttu-id="ed9e1-324">`$LogCommandLifecycleEvent`: Loggar start och stopp av kommandon och kommando pipeliner och säkerhets undantag vid kommando identifiering.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-324">`$LogCommandLifecycleEvent`: Logs the starting and stopping of commands and command pipelines and security exceptions in command discovery.</span></span> <span data-ttu-id="ed9e1-325">Standardvärdet är `$false` (inte loggat).</span><span class="sxs-lookup"><span data-stu-id="ed9e1-325">The default is `$false` (not logged).</span></span>
- <span data-ttu-id="ed9e1-326">`$LogEngineHealthEvent`: Loggar fel och fel i sessioner.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-326">`$LogEngineHealthEvent`: Logs errors and failures of sessions.</span></span> <span data-ttu-id="ed9e1-327">Standardvärdet är `$true` (loggas).</span><span class="sxs-lookup"><span data-stu-id="ed9e1-327">The default is `$true` (logged).</span></span>
- <span data-ttu-id="ed9e1-328">`$LogEngineLifecycleEvent`: Loggar öppnande och stängning av sessioner.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-328">`$LogEngineLifecycleEvent`: Logs the opening and closing of sessions.</span></span> <span data-ttu-id="ed9e1-329">Standardvärdet är `$true` (loggas).</span><span class="sxs-lookup"><span data-stu-id="ed9e1-329">The default is `$true` (logged).</span></span>
- <span data-ttu-id="ed9e1-330">`$LogProviderHealthEvent`: Loggar leverantörs fel, t. ex. läsnings-och skrivfel, fel söknings fel och anrops fel.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-330">`$LogProviderHealthEvent`: Logs provider errors, such as read and write errors, lookup errors, and invocation errors.</span></span> <span data-ttu-id="ed9e1-331">Standardvärdet är `$true` (loggas).</span><span class="sxs-lookup"><span data-stu-id="ed9e1-331">The default is `$true` (logged).</span></span>
- <span data-ttu-id="ed9e1-332">`$LogProviderLifecycleEvent`: Loggar lägger till och tar bort PowerShell-leverantörer.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-332">`$LogProviderLifecycleEvent`: Logs adding and removing of PowerShell providers.</span></span> <span data-ttu-id="ed9e1-333">Standardvärdet är `$true` (loggas).</span><span class="sxs-lookup"><span data-stu-id="ed9e1-333">The default is `$true` (logged).</span></span> <span data-ttu-id="ed9e1-334">Information om PowerShell-leverantörer finns [about_Providers](about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="ed9e1-334">For information about PowerShell providers, see [about_Providers](about_Providers.md).</span></span>

<span data-ttu-id="ed9e1-335">Om du vill aktivera en \**log *-händelse** skriver du variabeln med värdet `$true` , till exempel:</span><span class="sxs-lookup"><span data-stu-id="ed9e1-335">To enable a **Log\*Event** , type the variable with a value of `$true`, for example:</span></span>

```powershell
$LogCommandLifeCycleEvent = $true
```

<span data-ttu-id="ed9e1-336">Om du vill inaktivera en händelse typ skriver du variabeln med värdet `$false` , till exempel:</span><span class="sxs-lookup"><span data-stu-id="ed9e1-336">To disable an event type, type the variable with a value of `$false`, for example:</span></span>

```powershell
$LogCommandLifeCycleEvent = $false
```

<span data-ttu-id="ed9e1-337">De händelser som du aktiverar gäller endast för den aktuella PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-337">The events that you enable are effective only for the current PowerShell console.</span></span> <span data-ttu-id="ed9e1-338">Om du vill tillämpa konfigurationen på alla-konsoler sparar du variabel inställningarna i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-338">To apply the configuration to all consoles, save the variable settings in your PowerShell profile.</span></span> <span data-ttu-id="ed9e1-339">Mer information finns i [about_Profiles](about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="ed9e1-339">For more information, see [about_Profiles](about_Profiles.md).</span></span>

### <a name="maximumhistorycount"></a><span data-ttu-id="ed9e1-340">\$MaximumHistoryCount</span><span class="sxs-lookup"><span data-stu-id="ed9e1-340">\$MaximumHistoryCount</span></span>

<span data-ttu-id="ed9e1-341">Anger hur många kommandon som sparas i kommando historiken för den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-341">Determines how many commands are saved in the command history for the current session.</span></span>

<span data-ttu-id="ed9e1-342">**Giltiga värden** : 1-32768 ( `Int32` )</span><span class="sxs-lookup"><span data-stu-id="ed9e1-342">**Valid values** : 1 - 32768 (`Int32`)</span></span>

<span data-ttu-id="ed9e1-343">**Standard** : 4096</span><span class="sxs-lookup"><span data-stu-id="ed9e1-343">**Default** : 4096</span></span>

<span data-ttu-id="ed9e1-344">Om du vill ta reda på hur många kommandon som har sparats i kommando historiken skriver du:</span><span class="sxs-lookup"><span data-stu-id="ed9e1-344">To determine the number of commands current saved in the command history, type:</span></span>

```powershell
(Get-History).Count
```

<span data-ttu-id="ed9e1-345">Använd cmdleten om du vill se de kommandon som sparats i din tidigare session `Get-History` .</span><span class="sxs-lookup"><span data-stu-id="ed9e1-345">To see the commands saved in your session history, use the `Get-History` cmdlet.</span></span> <span data-ttu-id="ed9e1-346">Mer information finns i [about_History](about_History.md).</span><span class="sxs-lookup"><span data-stu-id="ed9e1-346">For more information, see [about_History](about_History.md).</span></span>

### <a name="ofs"></a><span data-ttu-id="ed9e1-347">\$OFS</span><span class="sxs-lookup"><span data-stu-id="ed9e1-347">\$OFS</span></span>

<span data-ttu-id="ed9e1-348">Utgående fält avgränsare (OFS) anger det tecken som avgränsar elementen i en matris som konverteras till en sträng.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-348">The Output Field Separator (OFS) specifies the character that separates the elements of an array that is converted to a string.</span></span>

<span data-ttu-id="ed9e1-349">**Giltiga värden** : vilken sträng som helst.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-349">**Valid values** : Any string.</span></span>

<span data-ttu-id="ed9e1-350">**Standard** : utrymme</span><span class="sxs-lookup"><span data-stu-id="ed9e1-350">**Default** : Space</span></span>

<span data-ttu-id="ed9e1-351">`$OFS`Variabeln finns inte som standard och utdatafilen avgränsare är ett blank steg, men du kan lägga till den här variabeln och ange den som valfri sträng.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-351">By default, the `$OFS` variable doesn't exist and the output file separator is a space, but you can add this variable and set it to any string.</span></span> <span data-ttu-id="ed9e1-352">Du kan ändra värdet för `$OFS` i sessionen genom att skriva `$OFS="<value>"` .</span><span class="sxs-lookup"><span data-stu-id="ed9e1-352">You can change the value of `$OFS` in your session, by typing `$OFS="<value>"`.</span></span>

> [!NOTE]
> <span data-ttu-id="ed9e1-353">Om du förväntar dig att standardvärdet för ett blank steg ( `" "` ) i ditt skript, modul eller konfigurations utdata är förvarat bör du se till att `$OFS` standardvärdet inte har ändrats någon annan stans i koden.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-353">If you're expecting the default value of a space (`" "`) in your script, module, or configuration output, be careful that the `$OFS` default value hasn't been changed elsewhere in your code.</span></span>

#### <a name="examples"></a><span data-ttu-id="ed9e1-354">Exempel</span><span class="sxs-lookup"><span data-stu-id="ed9e1-354">Examples</span></span>

<span data-ttu-id="ed9e1-355">Det här exemplet visar att ett blank steg används för att avgränsa värdena när en matris konverteras till en sträng.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-355">This example shows that a space is used to separate the values when an array is converted to a string.</span></span> <span data-ttu-id="ed9e1-356">I det här fallet lagras en matris med heltal i en variabel och variabeln omvandlas sedan som en sträng.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-356">In this case, an array of integers is stored in a variable and then the variable is cast as a string.</span></span>

```powershell
$array = 1,2,3,4
[string]$array
```

```Output
1 2 3 4
```

<span data-ttu-id="ed9e1-357">Om du vill ändra avgränsaren lägger du till `$OFS` variabeln genom att tilldela det ett värde.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-357">To change the separator, add the `$OFS` variable by assigning a value to it.</span></span>
<span data-ttu-id="ed9e1-358">Variabeln måste ha namnet `$OFS` .</span><span class="sxs-lookup"><span data-stu-id="ed9e1-358">The variable must be named `$OFS`.</span></span>

```powershell
$OFS = "+"
[string]$array
```

```Output
1+2+3+4
```

<span data-ttu-id="ed9e1-359">För att återställa standard beteendet kan du tilldela ett blank steg ( `" "` ) till värdet för `$OFS` eller ta bort variabeln.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-359">To restore the default behavior, you can assign a space (`" "`) to the value of `$OFS` or delete the variable.</span></span> <span data-ttu-id="ed9e1-360">Följande kommandon tar bort variabeln och kontrollerar att avgränsaren är ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-360">The following commands delete the variable and then verify that the separator is a space.</span></span>

```powershell
Remove-Variable OFS
[string]$array
```

```Output
1 2 3 4
```

### <a name="outputencoding"></a><span data-ttu-id="ed9e1-361">\$OutputEncoding</span><span class="sxs-lookup"><span data-stu-id="ed9e1-361">\$OutputEncoding</span></span>

<span data-ttu-id="ed9e1-362">Anger tecken kodnings metoden som PowerShell använder när den skickar text till andra program.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-362">Determines the character encoding method that PowerShell uses when it sends text to other applications.</span></span>

<span data-ttu-id="ed9e1-363">Om ett program till exempel returnerar Unicode-strängar till PowerShell kan du behöva ändra värdet till **UnicodeEncoding** för att skicka tecknen korrekt.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-363">For example, if an application returns Unicode strings to PowerShell, you might need to change the value to **UnicodeEncoding** to send the characters correctly.</span></span>

<span data-ttu-id="ed9e1-364">Giltiga värden är följande: objekt som härletts från en kodnings klass, till exempel **ASCIIEncoding** , **SBCSCodePageEncoding** , **UTF7Encoding** , **UTF8Encoding** , **UTF32Encoding** och **UnicodeEncoding**.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-364">The valid values are as follows: Objects derived from an Encoding class, such as **ASCIIEncoding** , **SBCSCodePageEncoding** , **UTF7Encoding** , **UTF8Encoding** , **UTF32Encoding** , and **UnicodeEncoding**.</span></span>

<span data-ttu-id="ed9e1-365">**Standard** : UTF8Encoding-objekt (system. text. UTF8Encoding)</span><span class="sxs-lookup"><span data-stu-id="ed9e1-365">**Default** : UTF8Encoding object (System.Text.UTF8Encoding)</span></span>

#### <a name="examples"></a><span data-ttu-id="ed9e1-366">Exempel</span><span class="sxs-lookup"><span data-stu-id="ed9e1-366">Examples</span></span>

<span data-ttu-id="ed9e1-367">Det här exemplet visar hur du gör Windows **findstr.exe** kommandot fungerar i PowerShell på en dator som är lokaliserad för ett språk som använder Unicode-tecken, t. ex. kinesiska.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-367">This example shows how to make the Windows **findstr.exe** command work in PowerShell on a computer that is localized for a language that uses Unicode characters, such as Chinese.</span></span>

<span data-ttu-id="ed9e1-368">Det första kommandot hittar värdet för `$OutputEncoding` .</span><span class="sxs-lookup"><span data-stu-id="ed9e1-368">The first command finds the value of `$OutputEncoding`.</span></span> <span data-ttu-id="ed9e1-369">Eftersom värdet är ett encoding-objekt visas endast dess **EncodingName** -egenskap.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-369">Because the value is an encoding object, display only its **EncodingName** property.</span></span>

```powershell
$OutputEncoding.EncodingName
```

<span data-ttu-id="ed9e1-370">I det här exemplet används ett **findstr.exe** -kommando för att söka efter två kinesiska tecken som finns i `Test.txt` filen.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-370">In this example, a **findstr.exe** command is used to search for two Chinese characters that are present in the `Test.txt` file.</span></span> <span data-ttu-id="ed9e1-371">När den här **findstr.exe** kommandot körs i kommando tolken i Windows ( **cmd.exe** ), hittar **findstr.exe** tecknen i text filen.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-371">When this **findstr.exe** command is run in the Windows Command Prompt ( **cmd.exe** ), **findstr.exe** finds the characters in the text file.</span></span> <span data-ttu-id="ed9e1-372">Men när du kör samma **findstr.exe** kommando i PowerShell, hittas inte tecknen eftersom PowerShell skickar dem till **findstr.exe** i ASCII-text, i stället för i Unicode-text.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-372">However, when you run the same **findstr.exe** command in PowerShell, the characters aren't found because the PowerShell sends them to **findstr.exe** in ASCII text, instead of in Unicode text.</span></span>

```powershell
findstr <Unicode-characters>
```

<span data-ttu-id="ed9e1-373">Om du vill att kommandot ska fungera i PowerShell ställer du in värdet på `$OutputEncoding` värdet för **OutputEncoding** -egenskapen i-konsolen, som baseras på det språk som valts för Windows.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-373">To make the command work in PowerShell, set the value of `$OutputEncoding` to the value of the **OutputEncoding** property of the console, that is based on the locale selected for Windows.</span></span> <span data-ttu-id="ed9e1-374">Eftersom **OutputEncoding** är en statisk egenskap i-konsolen använder du dubbla kolon ( `::` ) i kommandot.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-374">Because **OutputEncoding** is a static property of the console, use double-colons (`::`) in the command.</span></span>

```powershell
$OutputEncoding = [console]::OutputEncoding
$OutputEncoding.EncodingName
```

```Output
OEM United States
```

<span data-ttu-id="ed9e1-375">När kodningen har ändrats hittar **findstr.exe** kommandot Unicode-tecknen.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-375">After the encoding change, the **findstr.exe** command finds the Unicode characters.</span></span>

```powershell
findstr <Unicode-characters>
```

```Output
test.txt:         <Unicode-characters>
```

### <a name="progresspreference"></a><span data-ttu-id="ed9e1-376">\$ProgressPreference</span><span class="sxs-lookup"><span data-stu-id="ed9e1-376">\$ProgressPreference</span></span>

<span data-ttu-id="ed9e1-377">Fastställer hur PowerShell svarar på förlopps uppdateringar som genereras av ett skript, en cmdlet eller en provider, till exempel de förlopps indikatorer som genereras av cmdleten [Write-Progress](xref:Microsoft.PowerShell.Utility.Write-Progress) .</span><span class="sxs-lookup"><span data-stu-id="ed9e1-377">Determines how PowerShell responds to progress updates generated by a script, cmdlet, or provider, such as the progress bars generated by the [Write-Progress](xref:Microsoft.PowerShell.Utility.Write-Progress) cmdlet.</span></span>
<span data-ttu-id="ed9e1-378">`Write-Progress`Cmdleten skapar förlopps indikatorer som visar ett kommandos status.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-378">The `Write-Progress` cmdlet creates progress bars that show a command's status.</span></span>

<span data-ttu-id="ed9e1-379">Giltiga värden är följande:</span><span class="sxs-lookup"><span data-stu-id="ed9e1-379">The valid values are as follows:</span></span>

- <span data-ttu-id="ed9e1-380">**Stop** : visar inte förlopps indikatorn.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-380">**Stop** : Doesn't display the progress bar.</span></span> <span data-ttu-id="ed9e1-381">I stället visas ett fel meddelande och det slutar att köras.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-381">Instead, it displays an error message and stops executing.</span></span>
- <span data-ttu-id="ed9e1-382">**Fråga** : visar inte förlopps indikatorn.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-382">**Inquire** : Doesn't display the progress bar.</span></span> <span data-ttu-id="ed9e1-383">Kräver behörighet att fortsätta.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-383">Prompts for permission to continue.</span></span> <span data-ttu-id="ed9e1-384">Om du svarar med `Y` eller `A` visas förlopps indikatorn.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-384">If you reply with `Y` or `A`, it displays the progress bar.</span></span>
- <span data-ttu-id="ed9e1-385">**Fortsätt** : (standard) visar förlopps indikatorn och fortsätter med körningen.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-385">**Continue** : (Default) Displays the progress bar and continues with execution.</span></span>
- <span data-ttu-id="ed9e1-386">**SilentlyContinue** : kör kommandot, men visar inte förlopps indikatorn.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-386">**SilentlyContinue** : Executes the command, but doesn't display the progress bar.</span></span>

### <a name="psemailserver"></a><span data-ttu-id="ed9e1-387">\$PSEmailServer</span><span class="sxs-lookup"><span data-stu-id="ed9e1-387">\$PSEmailServer</span></span>

<span data-ttu-id="ed9e1-388">Anger standard-e-postservern som används för att skicka e-postmeddelanden.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-388">Specifies the default e-mail server that is used to send email messages.</span></span> <span data-ttu-id="ed9e1-389">Den här preferens variabeln används av cmdletar som skickar e-post, till exempel cmdleten [send-](xref:Microsoft.PowerShell.Utility.Send-MailMessage) mail.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-389">This preference variable is used by cmdlets that send email, such as the [Send-MailMessage](xref:Microsoft.PowerShell.Utility.Send-MailMessage) cmdlet.</span></span>

### <a name="psdefaultparametervalues"></a><span data-ttu-id="ed9e1-390">\$PSDefaultParameterValues</span><span class="sxs-lookup"><span data-stu-id="ed9e1-390">\$PSDefaultParameterValues</span></span>

<span data-ttu-id="ed9e1-391">Anger standardvärden för parametrarna för cmdlets och Advanced functions.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-391">Specifies default values for the parameters of cmdlets and advanced functions.</span></span>
<span data-ttu-id="ed9e1-392">Värdet för `$PSDefaultParameterValues` är en hash-tabell där nyckeln består av cmdlet-namnet och parameter namnet avgränsat med kolon ( `:` ).</span><span class="sxs-lookup"><span data-stu-id="ed9e1-392">The value of `$PSDefaultParameterValues` is a hash table where the key consists of the cmdlet name and parameter name separated by a colon (`:`).</span></span> <span data-ttu-id="ed9e1-393">Värdet är ett anpassat standardvärde som du anger.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-393">The value is a custom default value that you specify.</span></span>

<span data-ttu-id="ed9e1-394">`$PSDefaultParameterValues` introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-394">`$PSDefaultParameterValues` was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="ed9e1-395">Mer information om den här preferens variabeln finns [about_Parameters_Default_Values](about_Parameters_Default_Values.md).</span><span class="sxs-lookup"><span data-stu-id="ed9e1-395">For more information about this preference variable, see [about_Parameters_Default_Values](about_Parameters_Default_Values.md).</span></span>

### <a name="psmoduleautoloadingpreference"></a><span data-ttu-id="ed9e1-396">\$PSModuleAutoloadingPreference</span><span class="sxs-lookup"><span data-stu-id="ed9e1-396">\$PSModuleAutoloadingPreference</span></span>

<span data-ttu-id="ed9e1-397">Aktiverar och inaktiverar automatisk import av moduler i sessionen.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-397">Enables and disables automatic importing of modules in the session.</span></span> <span data-ttu-id="ed9e1-398">**All** är standard.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-398">**All** is the default.</span></span> <span data-ttu-id="ed9e1-399">Oavsett variabelns värde kan du importera en modul med [import-modulen](xref:Microsoft.PowerShell.Core.Import-Module) .</span><span class="sxs-lookup"><span data-stu-id="ed9e1-399">Regardless of the variable's value, you can use [Import-Module](xref:Microsoft.PowerShell.Core.Import-Module) to import a module.</span></span>

<span data-ttu-id="ed9e1-400">Giltiga värden är:</span><span class="sxs-lookup"><span data-stu-id="ed9e1-400">Valid values are:</span></span>

- <span data-ttu-id="ed9e1-401">**Alla** : moduler importeras automatiskt vid första användning.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-401">**All** : Modules are imported automatically on first-use.</span></span> <span data-ttu-id="ed9e1-402">Om du vill importera en modul kan du hämta eller använda valfritt kommando i modulen.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-402">To import a module, get or use any command in the module.</span></span> <span data-ttu-id="ed9e1-403">Använd till exempel `Get-Command`.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-403">For example, use `Get-Command`.</span></span>
- <span data-ttu-id="ed9e1-404">**ModuleQualified** : moduler importeras automatiskt när en användare använder det module-kvalificerade namnet för ett kommando i modulen.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-404">**ModuleQualified** : Modules are imported automatically only when a user uses the module-qualified name of a command in the module.</span></span> <span data-ttu-id="ed9e1-405">Till exempel, om användaren skriver `MyModule\MyCommand` , importerar PowerShell modulen modulen **modul** .</span><span class="sxs-lookup"><span data-stu-id="ed9e1-405">For example, if the user types `MyModule\MyCommand`, PowerShell imports the **MyModule** module.</span></span>
- <span data-ttu-id="ed9e1-406">**Ingen** : automatisk import av moduler är inaktive rad i sessionen.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-406">**None** : Automatic importing of modules is disabled in the session.</span></span> <span data-ttu-id="ed9e1-407">Använd cmdleten om du vill importera en modul `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="ed9e1-407">To import a module, use the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="ed9e1-408">Mer information om automatisk import av moduler finns i [about_Modules](about_Modules.md).</span><span class="sxs-lookup"><span data-stu-id="ed9e1-408">For more information about automatic importing of modules, see [about_Modules](about_Modules.md).</span></span>

### <a name="pssessionapplicationname"></a><span data-ttu-id="ed9e1-409">\$PSSessionApplicationName</span><span class="sxs-lookup"><span data-stu-id="ed9e1-409">\$PSSessionApplicationName</span></span>

<span data-ttu-id="ed9e1-410">Anger standard program namnet för ett fjärrkommando som använder hanterings teknik för webb tjänster (WS-Management).</span><span class="sxs-lookup"><span data-stu-id="ed9e1-410">Specifies the default application name for a remote command that uses Web Services for Management (WS-Management) technology.</span></span> <span data-ttu-id="ed9e1-411">Mer information finns i [om Windows Remote Management](/windows/win32/winrm/about-windows-remote-management).</span><span class="sxs-lookup"><span data-stu-id="ed9e1-411">For more information, see [About Windows Remote Management](/windows/win32/winrm/about-windows-remote-management).</span></span>

<span data-ttu-id="ed9e1-412">Systemets standard program namn är `WSMAN` , men du kan använda den här preferens variabeln för att ändra standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-412">The system default application name is `WSMAN`, but you can use this preference variable to change the default.</span></span>

<span data-ttu-id="ed9e1-413">Program namnet är den sista noden i en anslutnings-URI.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-413">The application name is the last node in a connection URI.</span></span> <span data-ttu-id="ed9e1-414">Till exempel är program namnet i följande exempel-URI `WSMAN` .</span><span class="sxs-lookup"><span data-stu-id="ed9e1-414">For example, the application name in the following sample URI is `WSMAN`.</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="ed9e1-415">Standard program namnet används när fjärrkommandot inte anger en anslutnings-URI eller ett program namn.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-415">The default application name is used when the remote command doesn't specify a connection URI or an application name.</span></span>

<span data-ttu-id="ed9e1-416">**WinRM** -tjänsten använder program namnet för att välja en lyssnare som ska betjäna anslutningsbegäran.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-416">The **WinRM** service uses the application name to select a listener to service the connection request.</span></span> <span data-ttu-id="ed9e1-417">Parameterns värde ska matcha värdet på egenskapen **URLPrefix** för en lyssnare på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-417">The parameter's value should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

<span data-ttu-id="ed9e1-418">Om du vill åsidosätta system standard och värdet för den här variabeln och välja ett annat program namn för en viss session använder du parametrarna **ConnectionURI** eller **ApplicationName** för cmdletarna [New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession), [RETUR-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)eller [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command) .</span><span class="sxs-lookup"><span data-stu-id="ed9e1-418">To override the system default and the value of this variable, and select a different application name for a particular session, use the **ConnectionURI** or **ApplicationName** parameters of the [New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession), [Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession), or [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command) cmdlets.</span></span>

<span data-ttu-id="ed9e1-419">`$PSSessionApplicationName`Variabeln Preference anges på den lokala datorn, men anger en lyssnare på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-419">The `$PSSessionApplicationName` preference variable is set on the local computer, but it specifies a listener on the remote computer.</span></span> <span data-ttu-id="ed9e1-420">Om det program namn som du anger inte finns på fjärrdatorn Miss lyckas kommandot för att upprätta sessionen.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-420">If the application name that you specify doesn't exist on the remote computer, the command to establish the session fails.</span></span>

### <a name="pssessionconfigurationname"></a><span data-ttu-id="ed9e1-421">\$PSSessionConfigurationName</span><span class="sxs-lookup"><span data-stu-id="ed9e1-421">\$PSSessionConfigurationName</span></span>

<span data-ttu-id="ed9e1-422">Anger standard konfigurationen för sessionen som används för **PSSessions** som skapats i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-422">Specifies the default session configuration that is used for **PSSessions** created in the current session.</span></span>

<span data-ttu-id="ed9e1-423">Den här preferens variabeln ställs in på den lokala datorn, men anger en sessionsinformation som finns på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-423">This preference variable is set on the local computer, but it specifies a session configuration that's located on the remote computer.</span></span>

<span data-ttu-id="ed9e1-424">Värdet för `$PSSessionConfigurationName` variabeln är en fullständigt kvalificerad resurs-URI.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-424">The value of the `$PSSessionConfigurationName` variable is a fully qualified resource URI.</span></span>

<span data-ttu-id="ed9e1-425">Standardvärdet `http://schemas.microsoft.com/PowerShell/microsoft.PowerShell` anger konfigurationen av **Microsoft. PowerShell** -sessionen på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-425">The default value `http://schemas.microsoft.com/PowerShell/microsoft.PowerShell` indicates the **Microsoft.PowerShell** session configuration on the remote computer.</span></span>

<span data-ttu-id="ed9e1-426">Om du bara anger ett konfigurations namn är följande schema-URI anpassningsprefix:</span><span class="sxs-lookup"><span data-stu-id="ed9e1-426">If you specify only a configuration name, the following schema URI is prepended:</span></span>

`http://schemas.microsoft.com/PowerShell/`

<span data-ttu-id="ed9e1-427">Du kan åsidosätta standardvärdet och välja en annan sessionsinformation för en viss session med hjälp av parametern **ConfigurationName** i `New-PSSession` `Enter-PSSession` cmdletarna,, eller `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="ed9e1-427">You can override the default and select a different session configuration for a particular session by using the **ConfigurationName** parameter of the `New-PSSession`, `Enter-PSSession`, or `Invoke-Command` cmdlets.</span></span>

<span data-ttu-id="ed9e1-428">Du kan när som helst ändra värdet för den här variabeln.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-428">You can change the value of this variable at any time.</span></span> <span data-ttu-id="ed9e1-429">När du gör det måste du komma ihåg att den konfiguration av sessionen som du väljer måste finnas på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-429">When you do, remember that the session configuration that you select must exist on the remote computer.</span></span> <span data-ttu-id="ed9e1-430">Om den inte gör det Miss lyckas kommandot för att skapa en session som använder konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-430">If it doesn't, the command to create a session that uses the session configuration fails.</span></span>

<span data-ttu-id="ed9e1-431">Den här preferens variabeln avgör inte vilka konfigurationer för lokal session som används när fjärranslutna användare skapar en session som ansluter till den här datorn.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-431">This preference variable doesn't determine which local session configurations are used when remote users create a session that connects to this computer.</span></span>
<span data-ttu-id="ed9e1-432">Du kan dock använda behörigheterna för de lokala session-konfigurationerna för att avgöra vilka användare som kan använda dem.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-432">However, you can use the permissions for the local session configurations to determine which users may use them.</span></span>

### <a name="pssessionoption"></a><span data-ttu-id="ed9e1-433">\$PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="ed9e1-433">\$PSSessionOption</span></span>

<span data-ttu-id="ed9e1-434">Fastställer standardvärden för avancerade användar alternativ i en fjärrsession.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-434">Establishes the default values for advanced user options in a remote session.</span></span>
<span data-ttu-id="ed9e1-435">Dessa alternativ inställningar åsidosätter systemets standardvärden för session-alternativ.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-435">These option preferences override the system default values for session options.</span></span>

<span data-ttu-id="ed9e1-436">`$PSSessionOption`Variabeln innehåller ett **PSSessionOption** -objekt.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-436">The `$PSSessionOption` variable contains a **PSSessionOption** object.</span></span> <span data-ttu-id="ed9e1-437">Mer information finns i [system. Management. Automation. Remoting. PSSessionOption](/dotnet/api/system.management.automation.remoting.pssessionoption).</span><span class="sxs-lookup"><span data-stu-id="ed9e1-437">For more information, see [System.Management.Automation.Remoting.PSSessionOption](/dotnet/api/system.management.automation.remoting.pssessionoption).</span></span>
<span data-ttu-id="ed9e1-438">Varje egenskap för objektet representerar ett session-alternativ.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-438">Each property of the object represents a session option.</span></span> <span data-ttu-id="ed9e1-439">Egenskapen **nocompression** aktiverar till exempel data komprimering under sessionen.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-439">For example, the **NoCompression** property turns of data compression during the session.</span></span>

<span data-ttu-id="ed9e1-440">Som standard `$PSSessionOption` innehåller variabeln ett **PSSessionOption** -objekt med standardvärdena för alla alternativ, som du ser nedan.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-440">By default, the `$PSSessionOption` variable contains a **PSSessionOption** object with the default values for all options, as shown below.</span></span>

```Output
MaximumConnectionRedirectionCount : 5
NoCompression                     : False
NoMachineProfile                  : False
ProxyAccessType                   : None
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
OperationTimeout                  : 00:03:00
NoEncryption                      : False
UseUTF16                          : False
IncludePortInSPN                  : False
OutputBufferingMode               : None
Culture                           :
UICulture                         :
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         : 209715200
ApplicationArguments              :
OpenTimeout                       : 00:03:00
CancelTimeout                     : 00:01:00
IdleTimeout                       : -00:00:00.0010000
```

<span data-ttu-id="ed9e1-441">Beskrivningar av dessa alternativ och mer information finns i [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span><span class="sxs-lookup"><span data-stu-id="ed9e1-441">For descriptions of these options and more information, see [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span></span> <span data-ttu-id="ed9e1-442">Mer information om fjärrkommandon och sessioner finns i [about_Remote](about_Remote.md) och [about_PSSessions](about_PSSessions.md).</span><span class="sxs-lookup"><span data-stu-id="ed9e1-442">For more information about remote commands and sessions, see [about_Remote](about_Remote.md) and [about_PSSessions](about_PSSessions.md).</span></span>

<span data-ttu-id="ed9e1-443">Om du vill ändra värdet på `$PSSessionOption` variabeln Preference använder du `New-PSSessionOption` cmdleten för att skapa ett **PSSessionOption** -objekt med de alternativ värden som du föredrar.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-443">To change the value of the `$PSSessionOption` preference variable, use the `New-PSSessionOption` cmdlet to create a **PSSessionOption** object with the option values you prefer.</span></span> <span data-ttu-id="ed9e1-444">Spara utdata i en variabel som kallas `$PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="ed9e1-444">Save the output in a variable called `$PSSessionOption`.</span></span>

```powershell
$PSSessionOption = New-PSSessionOption -NoCompression
```

<span data-ttu-id="ed9e1-445">Om du vill använda `$PSSessionOption` variabeln Preference i varje PowerShell-session lägger du till ett `New-PSSessionOption` kommando som skapar `$PSSessionOption` variabeln i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-445">To use the `$PSSessionOption` preference variable in every PowerShell session, add a `New-PSSessionOption` command that creates the `$PSSessionOption` variable to your PowerShell profile.</span></span> <span data-ttu-id="ed9e1-446">Mer information finns i [about_Profiles](about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="ed9e1-446">For more information, see [about_Profiles](about_Profiles.md).</span></span>

<span data-ttu-id="ed9e1-447">Du kan ange anpassade alternativ för en viss fjärrsession.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-447">You can set custom options for a particular remote session.</span></span> <span data-ttu-id="ed9e1-448">De alternativ som du anger prioriteras framför systemets standardinställningar och värdet för Preference- `$PSSessionOption` variabeln.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-448">The options that you set take precedence over the system defaults and the value of the `$PSSessionOption` preference variable.</span></span>

<span data-ttu-id="ed9e1-449">Om du vill ange alternativ för anpassade sessioner använder du `New-PSSessionOption` cmdleten för att skapa ett **PSSessionOption** -objekt.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-449">To set custom session options, use the `New-PSSessionOption` cmdlet to create a **PSSessionOption** object.</span></span> <span data-ttu-id="ed9e1-450">Använd sedan **PSSessionOption** -objektet som värdet för parametern **SessionOption** i cmdletar som skapar en session, till exempel, `New-PSSession` `Enter-PSSession` och `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="ed9e1-450">Then, use the **PSSessionOption** object as the value of the **SessionOption** parameter in cmdlets that create a session, such as `New-PSSession`, `Enter-PSSession`, and `Invoke-Command`.</span></span>

### <a name="transcript"></a><span data-ttu-id="ed9e1-451">$Transcript</span><span class="sxs-lookup"><span data-stu-id="ed9e1-451">$Transcript</span></span>

<span data-ttu-id="ed9e1-452">Används av `Start-Transcript` för att ange namn och plats för avskrifts filen.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-452">Used by `Start-Transcript` to specify the name and location of the transcript file.</span></span> <span data-ttu-id="ed9e1-453">Om du inte anger något värde för parametern **Path** `Start-Transcript` använder sökvägen i värdet för den `$Transcript` globala variabeln.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-453">If you do not specify a value for the **Path** parameter, `Start-Transcript` uses the path in the value of the `$Transcript` global variable.</span></span> <span data-ttu-id="ed9e1-454">Om du inte har skapat den här variabeln `Start-Transcript` lagras avskrifterna i `$Home\My Documents` katalogen som `\PowerShell_transcript.<time-stamp>.txt` filer.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-454">If you have not created this variable, `Start-Transcript` stores the transcripts in the `$Home\My Documents` directory as `\PowerShell_transcript.<time-stamp>.txt` files.</span></span>

### <a name="verbosepreference"></a><span data-ttu-id="ed9e1-455">\$VerbosePreference</span><span class="sxs-lookup"><span data-stu-id="ed9e1-455">\$VerbosePreference</span></span>

<span data-ttu-id="ed9e1-456">Fastställer hur PowerShell svarar på utförliga meddelanden som genereras av ett skript, en cmdlet eller en provider, till exempel de meddelanden som genereras av [Write-Verbose-](xref:Microsoft.PowerShell.Utility.Write-Verbose) cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-456">Determines how PowerShell responds to verbose messages generated by a script, cmdlet, or provider, such as the messages generated by the [Write-Verbose](xref:Microsoft.PowerShell.Utility.Write-Verbose) cmdlet.</span></span>
<span data-ttu-id="ed9e1-457">Utförliga meddelanden beskriver de åtgärder som utförs för att köra ett kommando.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-457">Verbose messages describe the actions performed to execute a command.</span></span>

<span data-ttu-id="ed9e1-458">Som standard visas inte utförliga meddelanden, men du kan ändra det här beteendet genom att ändra värdet för `$VerbosePreference` .</span><span class="sxs-lookup"><span data-stu-id="ed9e1-458">By default, verbose messages aren't displayed, but you can change this behavior by changing the value of `$VerbosePreference`.</span></span>

<span data-ttu-id="ed9e1-459">Du kan använda den **utförliga** gemensamma parametern för en cmdlet för att visa eller dölja utförliga meddelanden för ett speciellt kommando.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-459">You can use the **Verbose** common parameter of a cmdlet to display or hide the verbose messages for a specific command.</span></span> <span data-ttu-id="ed9e1-460">Mer information finns i [about_CommonParameters](about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="ed9e1-460">For more information, see [about_CommonParameters](about_CommonParameters.md).</span></span>

<span data-ttu-id="ed9e1-461">Giltiga värden är följande:</span><span class="sxs-lookup"><span data-stu-id="ed9e1-461">The valid values are as follows:</span></span>

- <span data-ttu-id="ed9e1-462">**Stop** : visar utförligt meddelande och ett fel meddelande och sedan slutar att köra.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-462">**Stop** : Displays the verbose message and an error message and then stops executing.</span></span>
- <span data-ttu-id="ed9e1-463">**Fråga** : visar utförligt meddelande och visar en uppmaning som frågar om du vill fortsätta.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-463">**Inquire** : Displays the verbose message and then displays a prompt that asks you whether you want to continue.</span></span>
- <span data-ttu-id="ed9e1-464">**Fortsätt** : visar utförligt meddelande och fortsätter sedan med körningen.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-464">**Continue** : Displays the verbose message and then continues with execution.</span></span>
- <span data-ttu-id="ed9e1-465">**SilentlyContinue** : (standard) visar inte utförligt meddelande.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-465">**SilentlyContinue** : (Default) Doesn't display the verbose message.</span></span> <span data-ttu-id="ed9e1-466">Fortsätter att köra.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-466">Continues executing.</span></span>

#### <a name="examples"></a><span data-ttu-id="ed9e1-467">Exempel</span><span class="sxs-lookup"><span data-stu-id="ed9e1-467">Examples</span></span>

<span data-ttu-id="ed9e1-468">I de här exemplen visas effekterna av de olika värdena i `$VerbosePreference` och **verbose** -parametern för att åsidosätta Preference-värdet.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-468">These examples show the effect of the different values of `$VerbosePreference` and the **Verbose** parameter to override the preference value.</span></span>

<span data-ttu-id="ed9e1-469">Det här exemplet visar resultatet av **SilentlyContinue** -värdet, som är standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-469">This example shows the effect of the **SilentlyContinue** value, that is the default.</span></span> <span data-ttu-id="ed9e1-470">Kommandot använder **meddelande** parametern, men skriver inte ett meddelande till PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-470">The command uses the **Message** parameter, but doesn't write a message to the PowerShell console.</span></span>

```powershell
Write-Verbose -Message "Verbose message test."
```

<span data-ttu-id="ed9e1-471">När den **utförliga** parametern används, skrivs meddelandet.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-471">When the **Verbose** parameter is used, the message is written.</span></span>

```powershell
Write-Verbose -Message "Verbose message test." -Verbose
```

```Output
VERBOSE: Verbose message test.
```

<span data-ttu-id="ed9e1-472">Det här exemplet visar resultatet av värdet **Continue** .</span><span class="sxs-lookup"><span data-stu-id="ed9e1-472">This example shows the effect of the **Continue** value.</span></span> <span data-ttu-id="ed9e1-473">`$VerbosePreference`Variabeln är inställd på att **fortsätta** och meddelandet visas.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-473">The `$VerbosePreference` variable is set to **Continue** and the message is displayed.</span></span>

```powershell
$VerbosePreference = "Continue"
Write-Verbose -Message "Verbose message test."
```

```Output
VERBOSE: Verbose message test.
```

<span data-ttu-id="ed9e1-474">I det här exemplet används **verbose** -parametern med värdet `$false` som åsidosätter **Continue** -värdet.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-474">This example uses the **Verbose** parameter with a value of `$false` that overrides the **Continue** value.</span></span> <span data-ttu-id="ed9e1-475">Meddelandet visas inte.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-475">The message isn't displayed.</span></span>

```powershell
Write-Verbose -Message "Verbose message test." -Verbose:$false
```

<span data-ttu-id="ed9e1-476">Det här exemplet visar resultatet av **stopp** värdet.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-476">This example shows the effect of the **Stop** value.</span></span> <span data-ttu-id="ed9e1-477">`$VerbosePreference`Variabeln har angetts till **stoppa** och meddelandet visas.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-477">The `$VerbosePreference` variable is set to **Stop** and the message is displayed.</span></span> <span data-ttu-id="ed9e1-478">Kommandot har stoppats.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-478">The command is stopped.</span></span>

```powershell
$VerbosePreference = "Stop"
Write-Verbose -Message "Verbose message test."
```

```Output
VERBOSE: Verbose message test.
Write-Verbose : The running command stopped because the preference variable
  "VerbosePreference" or common parameter is set to Stop: Verbose message test.
At line:1 char:1
+ Write-Verbose -Message "Verbose message test."
```

<span data-ttu-id="ed9e1-479">I det här exemplet används **verbose** -parametern med värdet `$false` som åsidosätter **stopp** värdet.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-479">This example uses the **Verbose** parameter with a value of `$false` that overrides the **Stop** value.</span></span> <span data-ttu-id="ed9e1-480">Meddelandet visas inte.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-480">The message isn't displayed.</span></span>

```powershell
Write-Verbose -Message "Verbose message test." -Verbose:$false
```

<span data-ttu-id="ed9e1-481">I det här exemplet visas resultatet av **förfrågning** svärdet.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-481">This example shows the effect of the **Inquire** value.</span></span> <span data-ttu-id="ed9e1-482">`$VerbosePreference`Variabeln är inställd på **fråga**.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-482">The `$VerbosePreference` variable is set to **Inquire**.</span></span> <span data-ttu-id="ed9e1-483">Meddelandet visas och användaren uppmanas att bekräfta.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-483">The message is displayed and the user is prompted for confirmation.</span></span>

```powershell
$VerbosePreference = "Inquire"
Write-Verbose -Message "Verbose message test."
```

```Output
VERBOSE: Verbose message test.

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
```

<span data-ttu-id="ed9e1-484">I det här exemplet används **verbose** -parametern med värdet `$false` som åsidosätter värdet för **förfrågan** .</span><span class="sxs-lookup"><span data-stu-id="ed9e1-484">This example uses the **Verbose** parameter with a value of `$false` that overrides the **Inquire** value.</span></span> <span data-ttu-id="ed9e1-485">Användaren tillfrågas inte och meddelandet visas inte.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-485">The user isn't prompted and the message isn't displayed.</span></span>

```powershell
Write-Verbose -Message "Verbose message test." -Verbose:$false
```

### <a name="warningpreference"></a><span data-ttu-id="ed9e1-486">\$WarningPreference</span><span class="sxs-lookup"><span data-stu-id="ed9e1-486">\$WarningPreference</span></span>

<span data-ttu-id="ed9e1-487">Fastställer hur PowerShell svarar på varnings meddelanden som genereras av ett skript, en cmdlet eller en provider, till exempel de meddelanden som genereras av cmdleten [Write-Warning](xref:Microsoft.PowerShell.Utility.Write-Warning) .</span><span class="sxs-lookup"><span data-stu-id="ed9e1-487">Determines how PowerShell responds to warning messages generated by a script, cmdlet, or provider, such as the messages generated by the [Write-Warning](xref:Microsoft.PowerShell.Utility.Write-Warning) cmdlet.</span></span>

<span data-ttu-id="ed9e1-488">Som standard visas varnings meddelanden och körningen fortsätter, men du kan ändra det här beteendet genom att ändra värdet för `$WarningPreference` .</span><span class="sxs-lookup"><span data-stu-id="ed9e1-488">By default, warning messages are displayed and execution continues, but you can change this behavior by changing the value of `$WarningPreference`.</span></span>

<span data-ttu-id="ed9e1-489">Du kan använda parametern **WarningAction** common för en cmdlet för att avgöra hur PowerShell svarar på varningar från ett visst kommando.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-489">You can use the **WarningAction** common parameter of a cmdlet to determine how PowerShell responds to warnings from a particular command.</span></span> <span data-ttu-id="ed9e1-490">Mer information finns i [about_CommonParameters](about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="ed9e1-490">For more information, see [about_CommonParameters](about_CommonParameters.md).</span></span>

<span data-ttu-id="ed9e1-491">Giltiga värden är följande:</span><span class="sxs-lookup"><span data-stu-id="ed9e1-491">The valid values are as follows:</span></span>

- <span data-ttu-id="ed9e1-492">**Stop** : visar varnings meddelandet och ett fel meddelande och slutar sedan att köra.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-492">**Stop** : Displays the warning message and an error message and then stops executing.</span></span>
- <span data-ttu-id="ed9e1-493">**Fråga** : visar varnings meddelandet och frågar sedan om behörighet att fortsätta.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-493">**Inquire** : Displays the warning message and then prompts for permission to continue.</span></span>
- <span data-ttu-id="ed9e1-494">**Fortsätt** : (standard) visar varnings meddelandet och fortsätter sedan att köra.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-494">**Continue** : (Default) Displays the warning message and then continues executing.</span></span>
- <span data-ttu-id="ed9e1-495">**SilentlyContinue** : visar inte varnings meddelandet.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-495">**SilentlyContinue** : Doesn't display the warning message.</span></span> <span data-ttu-id="ed9e1-496">Fortsätter att köra.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-496">Continues executing.</span></span>

#### <a name="examples"></a><span data-ttu-id="ed9e1-497">Exempel</span><span class="sxs-lookup"><span data-stu-id="ed9e1-497">Examples</span></span>

<span data-ttu-id="ed9e1-498">I de här exemplen visas effekterna av de olika värdena i `$WarningPreference` .</span><span class="sxs-lookup"><span data-stu-id="ed9e1-498">These examples show the effect of the different values of `$WarningPreference`.</span></span>
<span data-ttu-id="ed9e1-499">Parametern **WarningAction** åsidosätter Preference-värdet.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-499">The **WarningAction** parameter overrides the preference value.</span></span>

<span data-ttu-id="ed9e1-500">I det här exemplet visas resultatet av standardvärdet, **Fortsätt**.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-500">This example shows the effect of the default value, **Continue**.</span></span>

```powershell
$m = "This action can delete data."
Write-Warning -Message $m
```

```Output
WARNING: This action can delete data.
```

<span data-ttu-id="ed9e1-501">I det här exemplet används parametern **WarningAction** med värdet **SilentlyContinue** för att förhindra varningen.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-501">This example uses the **WarningAction** parameter with the value **SilentlyContinue** to suppress the warning.</span></span> <span data-ttu-id="ed9e1-502">Meddelandet visas inte.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-502">The message isn't displayed.</span></span>

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction SilentlyContinue
```

<span data-ttu-id="ed9e1-503">I det här exemplet ändras `$WarningPreference` variabeln till **SilentlyContinue** -värdet.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-503">This example changes the `$WarningPreference` variable to the **SilentlyContinue** value.</span></span> <span data-ttu-id="ed9e1-504">Meddelandet visas inte.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-504">The message isn't displayed.</span></span>

```powershell
$WarningPreference = "SilentlyContinue"
$m = "This action can delete data."
Write-Warning -Message $m
```

<span data-ttu-id="ed9e1-505">I det här exemplet används parametern **WarningAction** för att stoppa när en varning genereras.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-505">This example uses the **WarningAction** parameter to stop when a warning is generated.</span></span>

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction Stop
```

```Output
WARNING: This action can delete data.
Write-Warning : The running command stopped because the preference variable
  "WarningPreference" or common parameter is set to Stop:
    This action can delete data.
At line:1 char:1
+ Write-Warning -Message $m -WarningAction Stop
```

<span data-ttu-id="ed9e1-506">Det här exemplet ändrar `$WarningPreference` variabeln till **fråge** värdet.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-506">This example changes the `$WarningPreference` variable to the **Inquire** value.</span></span> <span data-ttu-id="ed9e1-507">Användaren uppmanas att bekräfta.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-507">The user is prompted for confirmation.</span></span>

```powershell
$WarningPreference = "Inquire"
$m = "This action can delete data."
Write-Warning -Message $m
```

```Output
WARNING: This action can delete data.

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
```

<span data-ttu-id="ed9e1-508">I det här exemplet används parametern **WarningAction** med värdet **SilentlyContinue**.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-508">This example uses the **WarningAction** parameter with the value **SilentlyContinue**.</span></span> <span data-ttu-id="ed9e1-509">Kommandot fortsätter att köras och inget meddelande visas.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-509">The command continues to execute and no message is displayed.</span></span>

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction SilentlyContinue
```

<span data-ttu-id="ed9e1-510">Det här exemplet ändrar `$WarningPreference` värdet för att **stoppa**.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-510">This example changes the `$WarningPreference` value to **Stop**.</span></span>

```powershell
$WarningPreference = "Stop"
$m = "This action can delete data."
Write-Warning -Message $m
```

```Output
WARNING: This action can delete data.
Write-Warning : The running command stopped because the preference variable
  "WarningPreference" or common parameter is set to Stop:
    This action can delete data.
At line:1 char:1
+ Write-Warning -Message $m
```

<span data-ttu-id="ed9e1-511">I det här exemplet används **WarningAction** med **frågans** värde.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-511">This example uses the **WarningAction** with the **Inquire** value.</span></span> <span data-ttu-id="ed9e1-512">Användaren tillfrågas när en varning inträffar.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-512">The user is prompted when a warning occurs.</span></span>

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction Inquire
```

```Output
WARNING: This action can delete data.

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
```

### <a name="whatifpreference"></a><span data-ttu-id="ed9e1-513">\$WhatIfPreference</span><span class="sxs-lookup"><span data-stu-id="ed9e1-513">\$WhatIfPreference</span></span>

<span data-ttu-id="ed9e1-514">Bestämmer om **whatIf** automatiskt aktive ras för varje kommando som stöder det.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-514">Determines whether **WhatIf** is automatically enabled for every command that supports it.</span></span> <span data-ttu-id="ed9e1-515">När **whatIf** är aktiverat rapporterar cmdleten den förväntade resultatet av kommandot, men kör inte kommandot.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-515">When **WhatIf** is enabled, the cmdlet reports the expected effect of the command, but doesn't execute the command.</span></span>

<span data-ttu-id="ed9e1-516">Giltiga värden är följande:</span><span class="sxs-lookup"><span data-stu-id="ed9e1-516">The valid values are as follows:</span></span>

- <span data-ttu-id="ed9e1-517">**Falskt** ( **0** , ej aktiverat): (standard) **whatIf** aktive ras inte automatiskt.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-517">**False** ( **0** , not enabled): (Default) **WhatIf** isn't automatically enabled.</span></span> <span data-ttu-id="ed9e1-518">Använd cmdletens **whatIf** -parameter om du vill aktivera det manuellt.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-518">To enable it manually, use the cmdlet's **WhatIf** parameter.</span></span>
- <span data-ttu-id="ed9e1-519">**Sant** ( **1** , aktive rad): **whatIf** aktive ras automatiskt för alla kommandon som stöder det.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-519">**True** ( **1** , enabled): **WhatIf** is automatically enabled on any command that supports it.</span></span> <span data-ttu-id="ed9e1-520">Användare kan använda parametern **whatIf** med värdet **false** för att inaktivera den manuellt, till exempel `-WhatIf:$false` .</span><span class="sxs-lookup"><span data-stu-id="ed9e1-520">Users can use the **WhatIf** parameter with a value of **False** to disable it manually, such as `-WhatIf:$false`.</span></span>

#### <a name="examples"></a><span data-ttu-id="ed9e1-521">Exempel</span><span class="sxs-lookup"><span data-stu-id="ed9e1-521">Examples</span></span>

<span data-ttu-id="ed9e1-522">I de här exemplen visas effekterna av de olika värdena i `$WhatIfPreference` .</span><span class="sxs-lookup"><span data-stu-id="ed9e1-522">These examples show the effect of the different values of `$WhatIfPreference`.</span></span>
<span data-ttu-id="ed9e1-523">De visar hur du använder parametern **whatIf** för att åsidosätta Preference-värdet för ett speciellt kommando.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-523">They show how to use the **WhatIf** parameter to override the preference value for a specific command.</span></span>

<span data-ttu-id="ed9e1-524">Det här exemplet visar resultatet av `$WhatIfPreference` variabeln som angetts till standardvärdet, **false**.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-524">This example shows the effect of the `$WhatIfPreference` variable set to the default value, **False**.</span></span> <span data-ttu-id="ed9e1-525">Används `Get-ChildItem` för att kontrol lera att filen finns.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-525">Use `Get-ChildItem` to verify that the file exists.</span></span>
<span data-ttu-id="ed9e1-526">`Remove-Item` tar bort filen.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-526">`Remove-Item` deletes the file.</span></span> <span data-ttu-id="ed9e1-527">När filen har tagits bort kan du kontrol lera borttagningen med `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="ed9e1-527">After the file is deleted, you can verify the deletion with `Get-ChildItem`.</span></span>

```powershell
Get-ChildItem -Path .\test.txt
Remove-Item -Path ./test.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           9/13/2019    10:53             10 test.txt
```

```powershell
Get-ChildItem -Path .\test.txt
```

```Output
Get-ChildItem : Cannot find path 'C:\Test\test.txt' because it does not exist.
At line:1 char:1
+ Get-ChildItem -File test.txt
```

<span data-ttu-id="ed9e1-528">Det här exemplet visar effekterna av att använda parametern **whatIf** när värdet för `$WhatIfPreference` är **false**.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-528">This example shows the effect of using the **WhatIf** parameter when the value of `$WhatIfPreference` is **False**.</span></span>

<span data-ttu-id="ed9e1-529">Kontrol lera att filen finns.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-529">Verify that the file exists.</span></span>

```powershell
Get-ChildItem -Path .\test2.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/28/2019    17:06             12 test2.txt
```

<span data-ttu-id="ed9e1-530">Använd parametern **whatIf** för att avgöra resultatet av försöket att ta bort filen.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-530">Use the **WhatIf** parameter to determine the result of attempting to delete the file.</span></span>

```powershell
Remove-Item -Path .\test2.txt -WhatIf
```

```Output
What if: Performing the operation "Remove File" on target "C:\Test\test2.txt".
``````

<span data-ttu-id="ed9e1-531">Kontrol lera att filen inte har tagits bort.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-531">Verify that the file wasn't deleted.</span></span>

```powershell
Get-ChildItem -Path .\test2.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/28/2019    17:06             12 test2.txt
```

<span data-ttu-id="ed9e1-532">I det här exemplet visas resultatet av `$WhatIfPreference` variabeln som anges till värdet, **Sant**.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-532">This example shows the effect of the `$WhatIfPreference` variable set to the value, **True**.</span></span> <span data-ttu-id="ed9e1-533">När du använder `Remove-Item` för att ta bort en fil visas filens sökväg, men filen tas inte bort.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-533">When you use `Remove-Item` to delete a file, the file's path is displayed, but the file isn't deleted.</span></span>

<span data-ttu-id="ed9e1-534">Försök att ta bort en fil.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-534">Attempt to delete a file.</span></span> <span data-ttu-id="ed9e1-535">Ett meddelande visas om vad som skulle hända om `Remove-Item` kördes, men filen inte tas bort.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-535">A message is displayed about what would happen if `Remove-Item` was run, but the file isn't deleted.</span></span>

```powershell
$WhatIfPreference = "True"
Remove-Item -Path .\test2.txt
```

```Output
What if: Performing the operation "Remove File" on target "C:\Test\test2.txt".
```

<span data-ttu-id="ed9e1-536">Används `Get-ChildItem` för att kontrol lera att filen inte har tagits bort.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-536">Use `Get-ChildItem` to verify that the file wasn't deleted.</span></span>

```powershell
Get-ChildItem -Path .\test2.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/28/2019    17:06             12 test2.txt
```

<span data-ttu-id="ed9e1-537">I det här exemplet visas hur du tar bort en fil när värdet `$WhatIfPreference` är **True**.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-537">This example shows how to delete a file when the value of `$WhatIfPreference` is **True**.</span></span> <span data-ttu-id="ed9e1-538">Den använder parametern **whatIf** med värdet `$false` .</span><span class="sxs-lookup"><span data-stu-id="ed9e1-538">It uses the **WhatIf** parameter with a value of `$false`.</span></span> <span data-ttu-id="ed9e1-539">Används `Get-ChildItem` för att kontrol lera att filen har tagits bort.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-539">Use `Get-ChildItem` to verify the file was deleted.</span></span>

```powershell
Remove-Item -Path .\test2.txt -WhatIf:$false
Get-ChildItem -Path .\test2.txt
```

```Output
Get-ChildItem : Cannot find path 'C:\Test\test2.txt' because it does not exist.
At line:1 char:1
+ Get-ChildItem -Path .\test2.txt
```

<span data-ttu-id="ed9e1-540">Följande är exempel på den `Get-Process` cmdlet som inte stöder **whatIf** och `Stop-Process` som stöder **whatIf**.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-540">The following are examples of the `Get-Process` cmdlet that doesn't support **WhatIf** and `Stop-Process` that does support **WhatIf**.</span></span> <span data-ttu-id="ed9e1-541">`$WhatIfPreference`Variabelns värde är **Sant**.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-541">The `$WhatIfPreference` variable's value is **True**.</span></span>

<span data-ttu-id="ed9e1-542">`Get-Process` stöder inte **whatIf**.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-542">`Get-Process` doesn't support **WhatIf**.</span></span> <span data-ttu-id="ed9e1-543">När kommandot körs visas **Winword** -processen.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-543">When the command is executed, it displays the **Winword** process.</span></span>

```powershell
Get-Process -Name Winword
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    130   119.84     173.38       8.39   15024   4 WINWORD
```

<span data-ttu-id="ed9e1-544">`Stop-Process` stöder **whatIf**.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-544">`Stop-Process` does support **WhatIf**.</span></span> <span data-ttu-id="ed9e1-545">**Winword** -processen har inte stoppats.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-545">The **Winword** process isn't stopped.</span></span>

```powershell
Stop-Process -Name Winword
```

```Output
What if: Performing the operation "Stop-Process" on target "WINWORD (15024)".
```

<span data-ttu-id="ed9e1-546">Du kan åsidosätta `Stop-Process` **whatIf** -beteendet med hjälp av parametern **whatIf** med värdet `$false` .</span><span class="sxs-lookup"><span data-stu-id="ed9e1-546">You can override the `Stop-Process` **WhatIf** behavior by using the **WhatIf** parameter with a value of `$false`.</span></span> <span data-ttu-id="ed9e1-547">**Winword** -processen har stoppats.</span><span class="sxs-lookup"><span data-stu-id="ed9e1-547">The **Winword** process is stopped.</span></span>

```powershell
Stop-Process -Name Winword -WhatIf:$false
```

<span data-ttu-id="ed9e1-548">Använd om du vill kontrol lera att **Winword** -processen har stoppats `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="ed9e1-548">To verify that the **Winword** process was stopped, use `Get-Process`.</span></span>

```powershell
Get-Process -Name Winword
```

```Output
Get-Process : Cannot find a process with the name "Winword".
  Verify the process name and call the cmdlet again.
At line:1 char:1
+ Get-Process -Name Winword
```

## <a name="see-also"></a><span data-ttu-id="ed9e1-549">Se även</span><span class="sxs-lookup"><span data-stu-id="ed9e1-549">See also</span></span>

[<span data-ttu-id="ed9e1-550">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="ed9e1-550">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="ed9e1-551">about_CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ed9e1-551">about_CommonParameters</span></span>](about_CommonParameters.md)

[<span data-ttu-id="ed9e1-552">about_Environment_Variables</span><span class="sxs-lookup"><span data-stu-id="ed9e1-552">about_Environment_Variables</span></span>](about_Environment_Variables.md)

[<span data-ttu-id="ed9e1-553">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="ed9e1-553">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="ed9e1-554">about_Remote</span><span class="sxs-lookup"><span data-stu-id="ed9e1-554">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="ed9e1-555">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="ed9e1-555">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="ed9e1-556">about_Variables</span><span class="sxs-lookup"><span data-stu-id="ed9e1-556">about_Variables</span></span>](about_Variables.md)
