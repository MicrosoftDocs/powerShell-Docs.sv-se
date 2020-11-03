---
description: Beskriver hur funktioner som anger `CmdletBinding` attributet kan använda de metoder och egenskaper som är tillgängliga för kompilerade cmdlets.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced_methods?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced_Methods
ms.openlocfilehash: 862c57d326049096ada28353b74485f8519f46da
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272565"
---
# <a name="about-functions-advanced-methods"></a><span data-ttu-id="3cf99-104">Om functions avancerade metoder</span><span class="sxs-lookup"><span data-stu-id="3cf99-104">About Functions Advanced Methods</span></span>

## <a name="short-description"></a><span data-ttu-id="3cf99-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="3cf99-105">Short description</span></span>

<span data-ttu-id="3cf99-106">Beskriver hur funktioner som anger `CmdletBinding` attributet kan använda de metoder och egenskaper som är tillgängliga för kompilerade cmdlets.</span><span class="sxs-lookup"><span data-stu-id="3cf99-106">Describes how functions that specify the `CmdletBinding` attribute can use the methods and properties that are available to compiled cmdlets.</span></span>

## <a name="long-description"></a><span data-ttu-id="3cf99-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="3cf99-107">Long description</span></span>

<span data-ttu-id="3cf99-108">Funktioner som anger `CmdletBinding` attributet kan komma åt ett antal metoder och egenskaper via `$PSCmdlet` variabeln.</span><span class="sxs-lookup"><span data-stu-id="3cf99-108">Functions that specify the `CmdletBinding` attribute can access a number of methods and properties through the `$PSCmdlet` variable.</span></span> <span data-ttu-id="3cf99-109">Dessa metoder omfattar följande metoder:</span><span class="sxs-lookup"><span data-stu-id="3cf99-109">These methods include the following methods:</span></span>

- <span data-ttu-id="3cf99-110">Ingångs bearbetnings metoder som kompilerade cmdlets använder för att utföra sitt arbete.</span><span class="sxs-lookup"><span data-stu-id="3cf99-110">Input-processing methods that compiled cmdlets use to do their work.</span></span>
- <span data-ttu-id="3cf99-111">`ShouldProcess`Metoderna och `ShouldContinue` som används för att få feedback från användaren innan en åtgärd utförs.</span><span class="sxs-lookup"><span data-stu-id="3cf99-111">The `ShouldProcess` and `ShouldContinue` methods that are used to get user feedback before an action is performed.</span></span>
- <span data-ttu-id="3cf99-112">`ThrowTerminatingError`Metoden för att generera fel poster.</span><span class="sxs-lookup"><span data-stu-id="3cf99-112">The `ThrowTerminatingError` method for generating error records.</span></span>
- <span data-ttu-id="3cf99-113">Flera `Write` metoder som returnerar olika typer av utdata.</span><span class="sxs-lookup"><span data-stu-id="3cf99-113">Several `Write` methods that return different types of output.</span></span>

<span data-ttu-id="3cf99-114">Alla metoder och egenskaper för **PSCmdlet** -klassen är tillgängliga för avancerade funktioner.</span><span class="sxs-lookup"><span data-stu-id="3cf99-114">All the methods and properties of the **PSCmdlet** class are available to advanced functions.</span></span> <span data-ttu-id="3cf99-115">Mer information finns i [system. Management. Automation. PSCmdlet](/dotnet/api/system.management.automation.pscmdlet).</span><span class="sxs-lookup"><span data-stu-id="3cf99-115">For more information, see [System.Management.Automation.PSCmdlet](/dotnet/api/system.management.automation.pscmdlet).</span></span>

<span data-ttu-id="3cf99-116">Mer information om `CmdletBinding` attributet finns i [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md).</span><span class="sxs-lookup"><span data-stu-id="3cf99-116">For more information about the `CmdletBinding` attribute, see [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md).</span></span>
<span data-ttu-id="3cf99-117">**CmdletBindingAttribute** -klassen finns i [system. Management. Automation. cmdlet. CmdletBindingAttribute](/dotnet/api/system.management.automation.cmdletbindingattribute).</span><span class="sxs-lookup"><span data-stu-id="3cf99-117">For the **CmdletBindingAttribute** class, see [System.Management.Automation.Cmdlet.CmdletBindingAttribute](/dotnet/api/system.management.automation.cmdletbindingattribute).</span></span>

### <a name="input-processing-methods"></a><span data-ttu-id="3cf99-118">Metoder för bearbetning av indata</span><span class="sxs-lookup"><span data-stu-id="3cf99-118">Input processing methods</span></span>

<span data-ttu-id="3cf99-119">De metoder som beskrivs i det här avsnittet kallas för metoder för bearbetning av indata.</span><span class="sxs-lookup"><span data-stu-id="3cf99-119">The methods described in this section are referred to as the input processing methods.</span></span> <span data-ttu-id="3cf99-120">För functions representeras dessa tre metoder av `Begin` `Process` funktionens,-och- `End` block.</span><span class="sxs-lookup"><span data-stu-id="3cf99-120">For functions, these three methods are represented by the `Begin`, `Process`, and `End` blocks of the function.</span></span> <span data-ttu-id="3cf99-121">Du behöver inte använda något av dessa block i funktionerna.</span><span class="sxs-lookup"><span data-stu-id="3cf99-121">You aren't required to use any of these blocks in your functions.</span></span>

> [!NOTE]
> <span data-ttu-id="3cf99-122">Dessa block är också tillgängliga för funktioner som inte använder- `CmdletBinding` attributet.</span><span class="sxs-lookup"><span data-stu-id="3cf99-122">These blocks are also available to functions that don't use the `CmdletBinding` attribute.</span></span>

#### <a name="begin"></a><span data-ttu-id="3cf99-123">Börja</span><span class="sxs-lookup"><span data-stu-id="3cf99-123">Begin</span></span>

<span data-ttu-id="3cf99-124">Det här blocket används för att tillhandahålla valfri för bearbetning av en gång för funktionen.</span><span class="sxs-lookup"><span data-stu-id="3cf99-124">This block is used to provide optional one-time preprocessing for the function.</span></span>
<span data-ttu-id="3cf99-125">PowerShell-körningen använder koden i det här blocket en gång för varje instans av funktionen i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="3cf99-125">The PowerShell runtime uses the code in this block once for each instance of the function in the pipeline.</span></span>

#### <a name="process"></a><span data-ttu-id="3cf99-126">Process</span><span class="sxs-lookup"><span data-stu-id="3cf99-126">Process</span></span>

<span data-ttu-id="3cf99-127">Det här blocket används för att tillhandahålla post-för-post-bearbetning för funktionen.</span><span class="sxs-lookup"><span data-stu-id="3cf99-127">This block is used to provide record-by-record processing for the function.</span></span> <span data-ttu-id="3cf99-128">Du kan använda ett `Process` block utan att definiera de andra blocken.</span><span class="sxs-lookup"><span data-stu-id="3cf99-128">You can use a `Process` block without defining the other blocks.</span></span> <span data-ttu-id="3cf99-129">Antalet `Process` block körningar beror på hur du använder funktionen och vilka indatatyper funktionen tar emot.</span><span class="sxs-lookup"><span data-stu-id="3cf99-129">The number of `Process` block executions depends on how you use the function and what input the function receives.</span></span>

<span data-ttu-id="3cf99-130">Den automatiska variabeln `$_` eller `$PSItem` innehåller det aktuella objektet i pipelinen för användning i `Process` blocket.</span><span class="sxs-lookup"><span data-stu-id="3cf99-130">The automatic variable `$_` or `$PSItem` contains the current object in the pipeline for use in the `Process` block.</span></span> <span data-ttu-id="3cf99-131">Den `$input` automatiska variabeln innehåller en uppräknare som endast är tillgänglig för funktioner och skript block.</span><span class="sxs-lookup"><span data-stu-id="3cf99-131">The `$input` automatic variable contains an enumerator that's only available to functions and script blocks.</span></span>
<span data-ttu-id="3cf99-132">Mer information finns i [about_Automatic_Variables](about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="3cf99-132">For more information, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

- <span data-ttu-id="3cf99-133">Genom att anropa funktionen i början eller utanför en pipeline körs `Process` blocket en gång.</span><span class="sxs-lookup"><span data-stu-id="3cf99-133">Calling the function at the beginning, or outside of a pipeline, executes the `Process` block once.</span></span>
- <span data-ttu-id="3cf99-134">I en pipeline `Process` körs blocket en gång för varje indatamängd som når funktionen.</span><span class="sxs-lookup"><span data-stu-id="3cf99-134">Within a pipeline, the `Process` block executes once for each input object that reaches the function.</span></span>
- <span data-ttu-id="3cf99-135">Om pipeline-inflödet som når funktionen är tom `Process` körs **inte** blocket.</span><span class="sxs-lookup"><span data-stu-id="3cf99-135">If the pipeline input that reaches the function is empty, the `Process` block **does not** execute.</span></span>
  - <span data-ttu-id="3cf99-136">`Begin`Och- `End` blocken körs fortfarande.</span><span class="sxs-lookup"><span data-stu-id="3cf99-136">The `Begin` and `End` blocks still execute.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3cf99-137">Om en funktions parameter är inställd på att acceptera pipeline-indata och ett `Process` block inte har definierats, kommer post by post-bearbetningen inte att fungera.</span><span class="sxs-lookup"><span data-stu-id="3cf99-137">If a function parameter is set to accept pipeline input, and a `Process` block isn't defined, record-by-record processing will fail.</span></span> <span data-ttu-id="3cf99-138">I det här fallet körs bara en gång, oavsett inaktuella inuppgifter.</span><span class="sxs-lookup"><span data-stu-id="3cf99-138">In this case, your function will only execute once, regardless of the input.</span></span>

#### <a name="end"></a><span data-ttu-id="3cf99-139">Slut</span><span class="sxs-lookup"><span data-stu-id="3cf99-139">End</span></span>

<span data-ttu-id="3cf99-140">Det här blocket används för att ge en valfri efter bearbetning för funktionen.</span><span class="sxs-lookup"><span data-stu-id="3cf99-140">This block is used to provide optional one-time post-processing for the function.</span></span>

<span data-ttu-id="3cf99-141">I följande exempel visas dispositionen för en funktion som innehåller ett `Begin` block för för bearbetning av en gång, ett `Process` block för bearbetning av flera poster och ett `End` block för bearbetning efter bearbetning i taget.</span><span class="sxs-lookup"><span data-stu-id="3cf99-141">The following example shows the outline of a function that contains a `Begin` block for one-time preprocessing, a `Process` block for multiple record processing, and an `End` block for one-time post-processing.</span></span>

```powershell
Function Test-ScriptCmdlet
{
[CmdletBinding(SupportsShouldProcess=$True)]
    Param ($Parameter1)
    Begin{}
    Process{}
    End{}
}
```

> [!NOTE]
> <span data-ttu-id="3cf99-142">Om du använder antingen ett- `Begin` eller- `End` block måste du definiera alla tre blocken.</span><span class="sxs-lookup"><span data-stu-id="3cf99-142">Using either a `Begin` or `End` block requires that you define all three blocks.</span></span> <span data-ttu-id="3cf99-143">När du använder alla tre blocken måste all PowerShell-kod finnas i ett av blocken.</span><span class="sxs-lookup"><span data-stu-id="3cf99-143">When using all three blocks, all PowerShell code must be inside one of the blocks.</span></span>

### <a name="confirmation-methods"></a><span data-ttu-id="3cf99-144">Bekräftelse metoder</span><span class="sxs-lookup"><span data-stu-id="3cf99-144">Confirmation methods</span></span>

#### <a name="shouldprocess"></a><span data-ttu-id="3cf99-145">ShouldProcess</span><span class="sxs-lookup"><span data-stu-id="3cf99-145">ShouldProcess</span></span>

<span data-ttu-id="3cf99-146">Den här metoden anropas för att begära bekräftelse från användaren innan funktionen utför en åtgärd som skulle ändra systemet.</span><span class="sxs-lookup"><span data-stu-id="3cf99-146">This method is called to request confirmation from the user before the function performs an action that would change the system.</span></span> <span data-ttu-id="3cf99-147">Funktionen kan fortsätta baserat på det booleska värde som returnerades av metoden.</span><span class="sxs-lookup"><span data-stu-id="3cf99-147">The function can continue based on the Boolean value returned by the method.</span></span> <span data-ttu-id="3cf99-148">Den här metoden kan endast anropas från `Process{}` blocket för funktionen.</span><span class="sxs-lookup"><span data-stu-id="3cf99-148">This method can only be called only from within the `Process{}` block of the function.</span></span> <span data-ttu-id="3cf99-149">`CmdletBinding`Attributet måste också deklarera att funktionen stöder `ShouldProcess` (som visas i föregående exempel).</span><span class="sxs-lookup"><span data-stu-id="3cf99-149">The `CmdletBinding` attribute must also declare that the function supports `ShouldProcess` (as shown in the previous example).</span></span>

<span data-ttu-id="3cf99-150">Mer information om den här metoden finns i [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess).</span><span class="sxs-lookup"><span data-stu-id="3cf99-150">For more information about this method, see [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess).</span></span>

<span data-ttu-id="3cf99-151">Mer information om hur du begär en bekräftelse finns i [be om bekräftelse](/powershell/scripting/developer/cmdlet/requesting-confirmation).</span><span class="sxs-lookup"><span data-stu-id="3cf99-151">For more information about how to request confirmation, see [Requesting Confirmation](/powershell/scripting/developer/cmdlet/requesting-confirmation).</span></span>

#### <a name="shouldcontinue"></a><span data-ttu-id="3cf99-152">ShouldContinue</span><span class="sxs-lookup"><span data-stu-id="3cf99-152">ShouldContinue</span></span>

<span data-ttu-id="3cf99-153">Den här metoden anropas för att begära ett andra bekräftelse meddelande.</span><span class="sxs-lookup"><span data-stu-id="3cf99-153">This method is called to request a second confirmation message.</span></span> <span data-ttu-id="3cf99-154">Den ska anropas när `ShouldProcess` metoden returnerar `$true` .</span><span class="sxs-lookup"><span data-stu-id="3cf99-154">It should be called when the `ShouldProcess` method returns `$true`.</span></span> <span data-ttu-id="3cf99-155">Mer information om den här metoden finns i [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue).</span><span class="sxs-lookup"><span data-stu-id="3cf99-155">For more information about this method, see [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue).</span></span>

### <a name="error-methods"></a><span data-ttu-id="3cf99-156">Fel metoder</span><span class="sxs-lookup"><span data-stu-id="3cf99-156">Error methods</span></span>

<span data-ttu-id="3cf99-157">Funktioner kan anropa två olika metoder när fel inträffar.</span><span class="sxs-lookup"><span data-stu-id="3cf99-157">Functions can call two different methods when errors occur.</span></span> <span data-ttu-id="3cf99-158">När ett icke-avslutande fel inträffar ska funktionen anropa `WriteError` metoden, som beskrivs i `Write` avsnittet metoder.</span><span class="sxs-lookup"><span data-stu-id="3cf99-158">When a non-terminating error occurs, the function should call the `WriteError` method, which is described in the `Write` methods section.</span></span> <span data-ttu-id="3cf99-159">När ett avslutande fel inträffar och funktionen inte kan fortsätta bör den anropa- `ThrowTerminatingError` metoden.</span><span class="sxs-lookup"><span data-stu-id="3cf99-159">When a terminating error occurs and the function can't continue, it should call the `ThrowTerminatingError` method.</span></span> <span data-ttu-id="3cf99-160">Du kan också använda `Throw` instruktionen för att avsluta fel och cmdleten [Write-Error](xref:Microsoft.PowerShell.Utility.Write-Error) för icke-avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="3cf99-160">You can also use the `Throw` statement for terminating errors and the [Write-Error](xref:Microsoft.PowerShell.Utility.Write-Error) cmdlet for non-terminating errors.</span></span>

<span data-ttu-id="3cf99-161">Mer information finns i [system. Management. Automation. cmdlet. ThrowTerminatingError](/dotnet/api/system.management.automation.cmdlet.throwterminatingerror).</span><span class="sxs-lookup"><span data-stu-id="3cf99-161">For more information, see [System.Management.Automation.Cmdlet.ThrowTerminatingError](/dotnet/api/system.management.automation.cmdlet.throwterminatingerror).</span></span>

### <a name="write-methods"></a><span data-ttu-id="3cf99-162">Skriv metoder</span><span class="sxs-lookup"><span data-stu-id="3cf99-162">Write methods</span></span>

<span data-ttu-id="3cf99-163">En funktion kan anropa följande metoder för att returnera olika typer av utdata.</span><span class="sxs-lookup"><span data-stu-id="3cf99-163">A function can call the following methods to return different types of output.</span></span>
<span data-ttu-id="3cf99-164">Observera att inte alla utdata går till nästa-kommando i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="3cf99-164">Notice that not all the output goes to the next command in the pipeline.</span></span> <span data-ttu-id="3cf99-165">Du kan också använda olika `Write` cmdlets, till exempel `Write-Error` .</span><span class="sxs-lookup"><span data-stu-id="3cf99-165">You can also use the various `Write` cmdlets, such as `Write-Error`.</span></span>

#### <a name="writecommanddetail"></a><span data-ttu-id="3cf99-166">WriteCommandDetail</span><span class="sxs-lookup"><span data-stu-id="3cf99-166">WriteCommandDetail</span></span>

<span data-ttu-id="3cf99-167">Information om `WriteCommandDetails` -metoden finns i [system. Management. Automation. cmdlet. WriteCommandDetail](/dotnet/api/system.management.automation.cmdlet.writecommanddetail).</span><span class="sxs-lookup"><span data-stu-id="3cf99-167">For information about the `WriteCommandDetails` method, see [System.Management.Automation.Cmdlet.WriteCommandDetail](/dotnet/api/system.management.automation.cmdlet.writecommanddetail).</span></span>

#### <a name="writedebug"></a><span data-ttu-id="3cf99-168">WriteDebug</span><span class="sxs-lookup"><span data-stu-id="3cf99-168">WriteDebug</span></span>

<span data-ttu-id="3cf99-169">Om du vill ange information som kan användas för att felsöka en funktion kan du anropa-funktionen anropa `WriteDebug` metoden.</span><span class="sxs-lookup"><span data-stu-id="3cf99-169">To provide information that can be used to troubleshoot a function, make the function call the `WriteDebug` method.</span></span> <span data-ttu-id="3cf99-170">`WriteDebug`Metoden visar fel söknings meddelanden för användaren.</span><span class="sxs-lookup"><span data-stu-id="3cf99-170">The `WriteDebug` method displays debug messages to the user.</span></span> <span data-ttu-id="3cf99-171">Mer information finns i [system. Management. Automation. cmdlet. WriteDebug](/dotnet/api/system.management.automation.cmdlet.writedebug).</span><span class="sxs-lookup"><span data-stu-id="3cf99-171">For more information, see [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/system.management.automation.cmdlet.writedebug).</span></span>

#### <a name="writeerror"></a><span data-ttu-id="3cf99-172">WriteError</span><span class="sxs-lookup"><span data-stu-id="3cf99-172">WriteError</span></span>

<span data-ttu-id="3cf99-173">Funktioner ska anropa den här metoden när icke-avslutande fel inträffar och funktionen är utformad för att fortsätta bearbeta poster.</span><span class="sxs-lookup"><span data-stu-id="3cf99-173">Functions should call this method when non-terminating errors occur and the function is designed to continue processing records.</span></span> <span data-ttu-id="3cf99-174">Mer information finns i [system. Management. Automation. cmdlet. WriteError](/dotnet/api/system.management.automation.cmdlet.writeerror).</span><span class="sxs-lookup"><span data-stu-id="3cf99-174">For more information, see [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/system.management.automation.cmdlet.writeerror).</span></span>

> [!NOTE]
> <span data-ttu-id="3cf99-175">Om ett avslutande fel inträffar ska funktionen anropa [ThrowTerminatingError](/dotnet/api/system.management.automation.cmdlet.throwterminatingerror) -metoden.</span><span class="sxs-lookup"><span data-stu-id="3cf99-175">If a terminating error occurs, the function should call the [ThrowTerminatingError](/dotnet/api/system.management.automation.cmdlet.throwterminatingerror) method.</span></span>

#### <a name="writeobject"></a><span data-ttu-id="3cf99-176">WriteObject</span><span class="sxs-lookup"><span data-stu-id="3cf99-176">WriteObject</span></span>

<span data-ttu-id="3cf99-177">`WriteObject`Metoden gör att funktionen kan skicka ett objekt till nästa-kommando i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="3cf99-177">The `WriteObject` method allows the function to send an object to the next command in the pipeline.</span></span> <span data-ttu-id="3cf99-178">I de flesta fall `WriteObject` är metoden som ska användas när funktionen returnerar data.</span><span class="sxs-lookup"><span data-stu-id="3cf99-178">In most cases, `WriteObject` is the method to use when the function returns data.</span></span> <span data-ttu-id="3cf99-179">Mer information finns i [system. Management. Automation. PSCmdlet. WriteObject](/dotnet/api/system.management.automation.cmdlet.writeobject).</span><span class="sxs-lookup"><span data-stu-id="3cf99-179">For more information, see [System.Management.Automation.PSCmdlet.WriteObject](/dotnet/api/system.management.automation.cmdlet.writeobject).</span></span>

#### <a name="writeprogress"></a><span data-ttu-id="3cf99-180">WriteProgress</span><span class="sxs-lookup"><span data-stu-id="3cf99-180">WriteProgress</span></span>

<span data-ttu-id="3cf99-181">För funktioner med åtgärder som tar lång tid att slutföra, tillåter den här metoden att funktionen anropar `WriteProgress` metoden så att information om förloppet visas.</span><span class="sxs-lookup"><span data-stu-id="3cf99-181">For functions with actions that take a long time to complete, this method allows the function to call the `WriteProgress` method so that progress information is displayed.</span></span> <span data-ttu-id="3cf99-182">Du kan till exempel Visa procent andelen som slutförts.</span><span class="sxs-lookup"><span data-stu-id="3cf99-182">For example, you can display the percent completed.</span></span>
<span data-ttu-id="3cf99-183">Mer information finns i [system. Management. Automation. PSCmdlet. WriteProgress](/dotnet/api/system.management.automation.cmdlet.writeprogress).</span><span class="sxs-lookup"><span data-stu-id="3cf99-183">For more information, see [System.Management.Automation.PSCmdlet.WriteProgress](/dotnet/api/system.management.automation.cmdlet.writeprogress).</span></span>

#### <a name="writeverbose"></a><span data-ttu-id="3cf99-184">WriteVerbose</span><span class="sxs-lookup"><span data-stu-id="3cf99-184">WriteVerbose</span></span>

<span data-ttu-id="3cf99-185">Om du vill ha detaljerad information om vad funktionen gör kan du göra så att funktionen anropar `WriteVerbose` metoden för att Visa utförliga meddelanden för användaren.</span><span class="sxs-lookup"><span data-stu-id="3cf99-185">To provide detailed information about what the function is doing, make the function call the `WriteVerbose` method to display verbose messages to the user.</span></span> <span data-ttu-id="3cf99-186">Som standard visas inte utförliga meddelanden.</span><span class="sxs-lookup"><span data-stu-id="3cf99-186">By default, verbose messages aren't displayed.</span></span> <span data-ttu-id="3cf99-187">Mer information finns i [system. Management. Automation. PSCmdlet. WriteVerbose](/dotnet/api/system.management.automation.cmdlet.writeverbose).</span><span class="sxs-lookup"><span data-stu-id="3cf99-187">For more information, see [System.Management.Automation.PSCmdlet.WriteVerbose](/dotnet/api/system.management.automation.cmdlet.writeverbose).</span></span>

#### <a name="writewarning"></a><span data-ttu-id="3cf99-188">WriteWarning</span><span class="sxs-lookup"><span data-stu-id="3cf99-188">WriteWarning</span></span>

<span data-ttu-id="3cf99-189">Om du vill ange information om villkor som kan orsaka oväntade resultat kan du använda funktionen anropa WriteWarning-metoden för att Visa varnings meddelanden för användaren.</span><span class="sxs-lookup"><span data-stu-id="3cf99-189">To provide information about conditions that may cause unexpected results, make the function call the WriteWarning method to display warning messages to the user.</span></span> <span data-ttu-id="3cf99-190">Varnings meddelanden visas som standard.</span><span class="sxs-lookup"><span data-stu-id="3cf99-190">By default, warning messages are displayed.</span></span> <span data-ttu-id="3cf99-191">Mer information finns i [system. Management. Automation. PSCmdlet. WriteWarning](/dotnet/api/system.management.automation.cmdlet.writewarning).</span><span class="sxs-lookup"><span data-stu-id="3cf99-191">For more information, see [System.Management.Automation.PSCmdlet.WriteWarning](/dotnet/api/system.management.automation.cmdlet.writewarning).</span></span>

> [!NOTE]
> <span data-ttu-id="3cf99-192">Du kan också Visa varnings meddelanden genom `$WarningPreference` att konfigurera variabeln eller genom att använda `Verbose` `Debug` kommando rads alternativen och.</span><span class="sxs-lookup"><span data-stu-id="3cf99-192">You can also display warning messages by configuring the `$WarningPreference` variable or by using the `Verbose` and `Debug` command-line options.</span></span> <span data-ttu-id="3cf99-193">Mer information om `$WarningPreference` variabeln finns i [about_Preference_Variables](about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="3cf99-193">for more information about the `$WarningPreference` variable, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

### <a name="other-methods-and-properties"></a><span data-ttu-id="3cf99-194">Andra metoder och egenskaper</span><span class="sxs-lookup"><span data-stu-id="3cf99-194">Other methods and properties</span></span>

<span data-ttu-id="3cf99-195">Information om andra metoder och egenskaper som kan nås via `$PSCmdlet` variabeln finns i [system. Management. Automation. PSCmdlet](/dotnet/api/system.management.automation.pscmdlet).</span><span class="sxs-lookup"><span data-stu-id="3cf99-195">For information about the other methods and properties that can be accessed through the `$PSCmdlet` variable, see [System.Management.Automation.PSCmdlet](/dotnet/api/system.management.automation.pscmdlet).</span></span>

<span data-ttu-id="3cf99-196">Egenskapen [ParameterSetName](/dotnet/api/system.management.automation.pscmdlet.parametersetname) låter dig till exempel se den parameter uppsättning som används.</span><span class="sxs-lookup"><span data-stu-id="3cf99-196">For example, the [ParameterSetName](/dotnet/api/system.management.automation.pscmdlet.parametersetname) property allows you to see the parameter set that is being used.</span></span> <span data-ttu-id="3cf99-197">Med parameter uppsättningar kan du skapa en funktion som utför olika uppgifter baserat på de parametrar som anges när funktionen körs.</span><span class="sxs-lookup"><span data-stu-id="3cf99-197">Parameter sets allow you to create a function that performs different tasks based on the parameters that are specified when the function is run.</span></span>

## <a name="see-also"></a><span data-ttu-id="3cf99-198">Se även</span><span class="sxs-lookup"><span data-stu-id="3cf99-198">See also</span></span>

[<span data-ttu-id="3cf99-199">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="3cf99-199">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="3cf99-200">about_Functions</span><span class="sxs-lookup"><span data-stu-id="3cf99-200">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="3cf99-201">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="3cf99-201">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="3cf99-202">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="3cf99-202">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="3cf99-203">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="3cf99-203">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="3cf99-204">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="3cf99-204">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)

[<span data-ttu-id="3cf99-205">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="3cf99-205">about_Preference_Variables</span></span>](about_Preference_Variables.md)

