---
description: Beskriver `Prompt` funktionen och visar hur du skapar en anpassad `Prompt` funktion.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/15/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_prompts?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Prompts
ms.openlocfilehash: 3e1496c84fa528b4673a770b5b2777fc3d31dc34
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270021"
---
# <a name="about-prompts"></a><span data-ttu-id="822b2-104">Om prompter</span><span class="sxs-lookup"><span data-stu-id="822b2-104">About Prompts</span></span>

## <a name="short-description"></a><span data-ttu-id="822b2-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="822b2-105">Short description</span></span>
<span data-ttu-id="822b2-106">Beskriver `Prompt` funktionen och visar hur du skapar en anpassad `Prompt` funktion.</span><span class="sxs-lookup"><span data-stu-id="822b2-106">Describes the `Prompt` function and demonstrates how to create a custom `Prompt` function.</span></span>

## <a name="long-description"></a><span data-ttu-id="822b2-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="822b2-107">Long description</span></span>

<span data-ttu-id="822b2-108">PowerShell-Kommandotolken visar att PowerShell är redo att köra ett kommando:</span><span class="sxs-lookup"><span data-stu-id="822b2-108">The PowerShell command prompt indicates that PowerShell is ready to run a command:</span></span>

```
PS C:\>
```

<span data-ttu-id="822b2-109">PowerShell-prompten bestäms av den inbyggda `Prompt` funktionen.</span><span class="sxs-lookup"><span data-stu-id="822b2-109">The PowerShell prompt is determined by the built-in `Prompt` function.</span></span> <span data-ttu-id="822b2-110">Du kan anpassa prompten genom att skapa en egen `Prompt` funktion och spara den i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="822b2-110">You can customize the prompt by creating your own `Prompt` function and saving it in your PowerShell profile.</span></span>

## <a name="about-the-prompt-function"></a><span data-ttu-id="822b2-111">Om funktionen prompt</span><span class="sxs-lookup"><span data-stu-id="822b2-111">About the Prompt function</span></span>

<span data-ttu-id="822b2-112">`Prompt`Funktionen bestämmer utseendet på PowerShell-prompten.</span><span class="sxs-lookup"><span data-stu-id="822b2-112">The `Prompt` function determines the appearance of the PowerShell prompt.</span></span>
<span data-ttu-id="822b2-113">PowerShell innehåller en inbyggd `Prompt` funktion, men du kan åsidosätta den genom att definiera en egen `Prompt` funktion.</span><span class="sxs-lookup"><span data-stu-id="822b2-113">PowerShell comes with a built-in `Prompt` function, but you can override it by defining your own `Prompt` function.</span></span>

<span data-ttu-id="822b2-114">`Prompt`Funktionen har följande syntax:</span><span class="sxs-lookup"><span data-stu-id="822b2-114">The `Prompt` function has the following syntax:</span></span>

```powershell
function Prompt { <function-body> }
```

<span data-ttu-id="822b2-115">`Prompt`Funktionen måste returnera ett objekt.</span><span class="sxs-lookup"><span data-stu-id="822b2-115">The `Prompt` function must return an object.</span></span> <span data-ttu-id="822b2-116">Vi rekommenderar att du returnerar en sträng eller ett objekt som är formaterat som en sträng.</span><span class="sxs-lookup"><span data-stu-id="822b2-116">As a best practice, return a string or an object that is formatted as a string.</span></span> <span data-ttu-id="822b2-117">Den högsta rekommenderade längden är 80 tecken.</span><span class="sxs-lookup"><span data-stu-id="822b2-117">The maximum recommended length is 80 characters.</span></span>

<span data-ttu-id="822b2-118">Följande funktion returnerar till exempel `Prompt` en "Hello, World"-sträng följt av en höger vinkel paren tes ( `>` ).</span><span class="sxs-lookup"><span data-stu-id="822b2-118">For example, the following `Prompt` function returns a "Hello, World" string followed by a  right angle bracket (`>`).</span></span>

```powershell
PS C:\> function prompt {"Hello, World > "}
Hello, World >
```

### <a name="getting-the-prompt-function"></a><span data-ttu-id="822b2-119">Hämtar prompt-funktionen</span><span class="sxs-lookup"><span data-stu-id="822b2-119">Getting the Prompt function</span></span>

<span data-ttu-id="822b2-120">Hämta `Prompt` funktionen genom att använda `Get-Command` cmdleten eller använda `Get-Item` cmdleten i funktions enheten.</span><span class="sxs-lookup"><span data-stu-id="822b2-120">To get the `Prompt` function, use the `Get-Command` cmdlet or use the `Get-Item` cmdlet in the Function drive.</span></span>

<span data-ttu-id="822b2-121">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="822b2-121">For example:</span></span>

```powershell
PS C:\> Get-Command Prompt

CommandType     Name      ModuleName
-----------     ----      ----------
Function        prompt
```

<span data-ttu-id="822b2-122">Om du vill hämta skriptet som anger värdet för prompten använder du punkt metoden för att hämta egenskapen **script block** för `Prompt` funktionen.</span><span class="sxs-lookup"><span data-stu-id="822b2-122">To get the script that sets the value of the prompt, use the dot method to get the **ScriptBlock** property of the `Prompt` function.</span></span>

<span data-ttu-id="822b2-123">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="822b2-123">For example:</span></span>

```powershell
(Get-Command Prompt).ScriptBlock
```

```Output
"PS $($executionContext.SessionState.Path.CurrentLocation)$('>' * ($nestedPromptLevel + 1)) "
# .Link
# https://go.microsoft.com/fwlink/?LinkID=225750
# .ExternalHelp System.Management.Automation.dll-help.xml
```

<span data-ttu-id="822b2-124">Precis som alla funktioner `Prompt` lagras funktionen i `Function:` enheten.</span><span class="sxs-lookup"><span data-stu-id="822b2-124">Like all functions, the `Prompt` function is stored in the `Function:` drive.</span></span>
<span data-ttu-id="822b2-125">Om du vill visa skriptet som skapar den aktuella `Prompt` funktionen skriver du:</span><span class="sxs-lookup"><span data-stu-id="822b2-125">To display the script that creates the current `Prompt` function, type:</span></span>

```powershell
(Get-Item function:prompt).ScriptBlock
```

### <a name="the-default-prompt"></a><span data-ttu-id="822b2-126">Standard frågan</span><span class="sxs-lookup"><span data-stu-id="822b2-126">The default prompt</span></span>

<span data-ttu-id="822b2-127">Standard frågan visas bara när `Prompt` funktionen genererar ett fel eller inte returnerar något objekt.</span><span class="sxs-lookup"><span data-stu-id="822b2-127">The default prompt appears only when the `Prompt` function generates an error or does not return an object.</span></span>

<span data-ttu-id="822b2-128">Standard frågan om PowerShell är:</span><span class="sxs-lookup"><span data-stu-id="822b2-128">The default PowerShell prompt is:</span></span>

```
PS>
```

<span data-ttu-id="822b2-129">Följande kommando anger till exempel `Prompt` funktionen till `$null` , som är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="822b2-129">For example, the following command sets the `Prompt` function to `$null`, which is invalid.</span></span> <span data-ttu-id="822b2-130">Därför visas standard meddelandet.</span><span class="sxs-lookup"><span data-stu-id="822b2-130">As a result, the default prompt appears.</span></span>

```powershell
PS C:\> function prompt {$null}
PS>
```

<span data-ttu-id="822b2-131">Eftersom PowerShell innehåller en inbyggd prompt visas normalt inte standard meddelandet.</span><span class="sxs-lookup"><span data-stu-id="822b2-131">Because PowerShell comes with a built-in prompt, you usually do not see the default prompt.</span></span>

### <a name="built-in-prompt"></a><span data-ttu-id="822b2-132">Inbyggd prompt</span><span class="sxs-lookup"><span data-stu-id="822b2-132">Built-in prompt</span></span>

<span data-ttu-id="822b2-133">PowerShell innehåller en inbyggd `Prompt` funktion.</span><span class="sxs-lookup"><span data-stu-id="822b2-133">PowerShell includes a built-in `Prompt` function.</span></span>

```powershell
function prompt {
    $(if (Test-Path variable:/PSDebugContext) { '[DBG]: ' }
      else { '' }) + 'PS ' + $(Get-Location) +
        $(if ($NestedPromptLevel -ge 1) { '>>' }) + '> '
}
```

<span data-ttu-id="822b2-134">Funktionen använder `Test-Path` cmdleten för att avgöra om den `$PSDebugContext` automatiska variabeln är ifylld.</span><span class="sxs-lookup"><span data-stu-id="822b2-134">The function uses the `Test-Path` cmdlet to determine whether the `$PSDebugContext` automatic variable is populated.</span></span> <span data-ttu-id="822b2-135">Om `$PSDebugContext` är ifylld är du i fel söknings läge och `[DBG]:` läggs till i prompten enligt följande:</span><span class="sxs-lookup"><span data-stu-id="822b2-135">If `$PSDebugContext` is populated, you are in debugging mode, and `[DBG]:` is added to the prompt, as follows:</span></span>

```Output
[DBG]: PS C:\ps-test>
```

<span data-ttu-id="822b2-136">Om `$PSDebugContext` inte har fyllts i, läggs funktionen `PS` till i prompten.</span><span class="sxs-lookup"><span data-stu-id="822b2-136">If `$PSDebugContext` is not populated, the function adds `PS` to the prompt.</span></span>
<span data-ttu-id="822b2-137">Och funktionen använder `Get-Location` cmdleten för att hämta aktuell katalog plats för fil systemet.</span><span class="sxs-lookup"><span data-stu-id="822b2-137">And, the function uses the `Get-Location` cmdlet to get the current file system directory location.</span></span> <span data-ttu-id="822b2-138">Sedan lägger den till en höger vinkel paren tes ( `>` ).</span><span class="sxs-lookup"><span data-stu-id="822b2-138">Then, it adds a right angle bracket (`>`).</span></span>

<span data-ttu-id="822b2-139">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="822b2-139">For example:</span></span>

```Output
PS C:\ps-test>
```

<span data-ttu-id="822b2-140">Om du är i en kapslad prompt lägger funktionen till två vinkelparenteser ( `>>` ) i prompten.</span><span class="sxs-lookup"><span data-stu-id="822b2-140">If you are in a nested prompt, the function adds two angle brackets (`>>`) to the prompt.</span></span> <span data-ttu-id="822b2-141">(Du är i en kapslad prompt om värdet för den `$NestedPromptLevel` automatiska variabeln är större än 1.)</span><span class="sxs-lookup"><span data-stu-id="822b2-141">(You are in a nested prompt if the value of the `$NestedPromptLevel` automatic variable is greater than 1.)</span></span>

<span data-ttu-id="822b2-142">Om du till exempel felsöker i en kapslad prompt liknar prompten följande fråga:</span><span class="sxs-lookup"><span data-stu-id="822b2-142">For example, when you are debugging in a nested prompt, the prompt resembles the following prompt:</span></span>

```Output
[DBG] PS C:\ps-test>>>
```

### <a name="changes-to-the-prompt"></a><span data-ttu-id="822b2-143">Ändringar i prompten</span><span class="sxs-lookup"><span data-stu-id="822b2-143">Changes to the prompt</span></span>

<span data-ttu-id="822b2-144">`Enter-PSSession`Cmdleten prepends namnet på fjärrdatorn till den aktuella `Prompt` funktionen.</span><span class="sxs-lookup"><span data-stu-id="822b2-144">The `Enter-PSSession` cmdlet prepends the name of the remote computer to the current `Prompt` function.</span></span> <span data-ttu-id="822b2-145">När du använder `Enter-PSSession` cmdleten för att starta en session med en fjärrdator, ändras kommando tolken så att den innehåller namnet på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="822b2-145">When you use the `Enter-PSSession` cmdlet to start a session with a remote computer, the command prompt changes to include the name of the remote computer.</span></span> <span data-ttu-id="822b2-146">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="822b2-146">For example:</span></span>

```Output
PS Hello, World> Enter-PSSession Server01
[Server01]: PS Hello, World>
```

<span data-ttu-id="822b2-147">Andra PowerShell-värdprogram och alternativa gränssnitt kan ha sina egna anpassade kommando tolkar.</span><span class="sxs-lookup"><span data-stu-id="822b2-147">Other PowerShell host applications and alternate shells might have their own custom command prompts.</span></span>

<span data-ttu-id="822b2-148">Mer information om de `$PSDebugContext` `$NestedPromptLevel` automatiska variablerna och finns i [about_Automatic_Variables](about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="822b2-148">For more information about the `$PSDebugContext` and `$NestedPromptLevel` automatic variables, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

### <a name="how-to-customize-the-prompt"></a><span data-ttu-id="822b2-149">Anpassa prompten</span><span class="sxs-lookup"><span data-stu-id="822b2-149">How to customize the prompt</span></span>

<span data-ttu-id="822b2-150">Om du vill anpassa prompten skriver du en ny `Prompt` funktion.</span><span class="sxs-lookup"><span data-stu-id="822b2-150">To customize the prompt, write a new `Prompt` function.</span></span> <span data-ttu-id="822b2-151">Funktionen är inte skyddad, så du kan skriva över den.</span><span class="sxs-lookup"><span data-stu-id="822b2-151">The function is not protected, so you can overwrite it.</span></span>

<span data-ttu-id="822b2-152">Skriv följande om du vill skriva en `Prompt` funktion:</span><span class="sxs-lookup"><span data-stu-id="822b2-152">To write a `Prompt` function, type the following:</span></span>

```powershell
function prompt { }
```

<span data-ttu-id="822b2-153">Ange sedan de kommandon eller den sträng som skapar din prompt mellan klammerparenteserna.</span><span class="sxs-lookup"><span data-stu-id="822b2-153">Then, between the braces, enter the commands or the string that creates your prompt.</span></span>

<span data-ttu-id="822b2-154">Följande prompt innehåller till exempel ditt dator namn:</span><span class="sxs-lookup"><span data-stu-id="822b2-154">For example, the following prompt includes your computer name:</span></span>

```powershell
function prompt {"PS [$env:COMPUTERNAME]> "}
```

<span data-ttu-id="822b2-155">På Server01-datorn liknar prompten följande prompt:</span><span class="sxs-lookup"><span data-stu-id="822b2-155">On the Server01 computer, the prompt resembles the following prompt:</span></span>

```Output
PS [Server01] >
```

<span data-ttu-id="822b2-156">Följande `Prompt` funktion innehåller aktuellt datum och tid:</span><span class="sxs-lookup"><span data-stu-id="822b2-156">The following `Prompt` function includes the current date and time:</span></span>

```powershell
function prompt {"$(Get-Date)> "}
```

<span data-ttu-id="822b2-157">Prompten liknar följande prompt:</span><span class="sxs-lookup"><span data-stu-id="822b2-157">The prompt resembles the following prompt:</span></span>

```Output
03/15/2012 17:49:47>
```

<span data-ttu-id="822b2-158">Du kan också ändra standard `Prompt` funktionen:</span><span class="sxs-lookup"><span data-stu-id="822b2-158">You can also change the default `Prompt` function:</span></span>

<span data-ttu-id="822b2-159">Till exempel läggs följande ändrade `Prompt` funktion till i `[ADMIN]:` den inbyggda PowerShell-prompten när PowerShell öppnas med alternativet **Kör som administratör** :</span><span class="sxs-lookup"><span data-stu-id="822b2-159">For example, the following modified `Prompt` function adds `[ADMIN]:` to the built-in PowerShell prompt when PowerShell is opened by using the **Run as administrator** option:</span></span>

```powershell
function prompt {
  $identity = [Security.Principal.WindowsIdentity]::GetCurrent()
  $principal = [Security.Principal.WindowsPrincipal] $identity
  $adminRole = [Security.Principal.WindowsBuiltInRole]::Administrator

  $(if (Test-Path variable:/PSDebugContext) { '[DBG]: ' }
    elseif($principal.IsInRole($adminRole)) { "[ADMIN]: " }
    else { '' }
  ) + 'PS ' + $(Get-Location) +
    $(if ($NestedPromptLevel -ge 1) { '>>' }) + '> '
}
```

<span data-ttu-id="822b2-160">När du startar PowerShell med alternativet **Kör som administratör** visas ett meddelande som liknar följande meddelande:</span><span class="sxs-lookup"><span data-stu-id="822b2-160">When you start PowerShell by using the **Run as administrator** option, a prompt that resembles the following prompt appears:</span></span>

```Output
[ADMIN]: PS C:\ps-test>
```

<span data-ttu-id="822b2-161">Följande `Prompt` funktion visar historik-ID för nästa kommando.</span><span class="sxs-lookup"><span data-stu-id="822b2-161">The following `Prompt` function displays the history ID of the next command.</span></span> <span data-ttu-id="822b2-162">Om du vill visa kommando historiken använder du `Get-History` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="822b2-162">To view the command history, use the `Get-History` cmdlet.</span></span>

```powershell
function prompt {
   # The at sign creates an array in case only one history item exists.
   $history = @(Get-History)
   if($history.Count -gt 0)
   {
      $lastItem = $history[$history.Count - 1]
      $lastId = $lastItem.Id
   }

   $nextCommand = $lastId + 1
   $currentDirectory = Get-Location
   "PS: $nextCommand $currentDirectory >"
}
```

<span data-ttu-id="822b2-163">Följande prompt använder `Write-Host` `Get-Random` cmdletarna och för att skapa en prompt som ändrar färg slumpmässigt.</span><span class="sxs-lookup"><span data-stu-id="822b2-163">The following prompt uses the `Write-Host` and `Get-Random` cmdlets to create a prompt that changes color randomly.</span></span> <span data-ttu-id="822b2-164">Eftersom `Write-Host` skrivningar till det aktuella värd programmet, men inte returnerar ett objekt, innehåller den här funktionen en `Return` instruktion.</span><span class="sxs-lookup"><span data-stu-id="822b2-164">Because `Write-Host` writes to the current host application but does not return an object, this function includes a `Return` statement.</span></span> <span data-ttu-id="822b2-165">Utan den, använder PowerShell standard frågan `PS>` .</span><span class="sxs-lookup"><span data-stu-id="822b2-165">Without it, PowerShell uses the default prompt, `PS>`.</span></span>

```powershell
function prompt {
    $color = Get-Random -Min 1 -Max 16
    Write-Host ("PS " + $(Get-Location) +">") -NoNewLine `
     -ForegroundColor $Color
    return " "
}
```

### <a name="saving-the-prompt-function"></a><span data-ttu-id="822b2-166">Spara prompt-funktionen</span><span class="sxs-lookup"><span data-stu-id="822b2-166">Saving the Prompt function</span></span>

<span data-ttu-id="822b2-167">Precis som vilken funktion som helst `Prompt` finns funktionen bara i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="822b2-167">Like any function, the `Prompt` function exists only in the current session.</span></span> <span data-ttu-id="822b2-168">Om du vill spara `Prompt` funktionen i framtida sessioner lägger du till den i dina PowerShell-profiler.</span><span class="sxs-lookup"><span data-stu-id="822b2-168">To save the `Prompt` function for future sessions, add it to your PowerShell profiles.</span></span> <span data-ttu-id="822b2-169">Mer information om profiler finns [about_Profiles](about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="822b2-169">For more information about profiles, see [about_Profiles](about_Profiles.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="822b2-170">Se även</span><span class="sxs-lookup"><span data-stu-id="822b2-170">See also</span></span>

[<span data-ttu-id="822b2-171">Get-location</span><span class="sxs-lookup"><span data-stu-id="822b2-171">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)

[<span data-ttu-id="822b2-172">Retur-PSSession</span><span class="sxs-lookup"><span data-stu-id="822b2-172">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="822b2-173">Hämta historik</span><span class="sxs-lookup"><span data-stu-id="822b2-173">Get-History</span></span>](xref:Microsoft.PowerShell.Core.Get-History)

[<span data-ttu-id="822b2-174">Hämta slumpmässiga</span><span class="sxs-lookup"><span data-stu-id="822b2-174">Get-Random</span></span>](xref:Microsoft.PowerShell.Utility.Get-Random)

[<span data-ttu-id="822b2-175">Skriv värd</span><span class="sxs-lookup"><span data-stu-id="822b2-175">Write-Host</span></span>](xref:Microsoft.PowerShell.Utility.Write-Host)

[<span data-ttu-id="822b2-176">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="822b2-176">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="822b2-177">about_Functions</span><span class="sxs-lookup"><span data-stu-id="822b2-177">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="822b2-178">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="822b2-178">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="822b2-179">about_Debuggers</span><span class="sxs-lookup"><span data-stu-id="822b2-179">about_Debuggers</span></span>](about_Debuggers.md)

[<span data-ttu-id="822b2-180">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="822b2-180">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)
