---
description: Beskriver `Prompt` funktionen och visar hur du skapar en anpassad `Prompt` funktion.
Locale: en-US
ms.date: 04/15/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_prompts?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Prompts
ms.openlocfilehash: 3887df636c3ad486a4dbe72fffdc8acd92d2b3e9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708447"
---
# <a name="about-prompts"></a><span data-ttu-id="a4702-103">Om prompter</span><span class="sxs-lookup"><span data-stu-id="a4702-103">About Prompts</span></span>

## <a name="short-description"></a><span data-ttu-id="a4702-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="a4702-104">Short description</span></span>
<span data-ttu-id="a4702-105">Beskriver `Prompt` funktionen och visar hur du skapar en anpassad `Prompt` funktion.</span><span class="sxs-lookup"><span data-stu-id="a4702-105">Describes the `Prompt` function and demonstrates how to create a custom `Prompt` function.</span></span>

## <a name="long-description"></a><span data-ttu-id="a4702-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="a4702-106">Long description</span></span>

<span data-ttu-id="a4702-107">PowerShell-Kommandotolken visar att PowerShell är redo att köra ett kommando:</span><span class="sxs-lookup"><span data-stu-id="a4702-107">The PowerShell command prompt indicates that PowerShell is ready to run a command:</span></span>

```
PS C:\>
```

<span data-ttu-id="a4702-108">PowerShell-prompten bestäms av den inbyggda `Prompt` funktionen.</span><span class="sxs-lookup"><span data-stu-id="a4702-108">The PowerShell prompt is determined by the built-in `Prompt` function.</span></span> <span data-ttu-id="a4702-109">Du kan anpassa prompten genom att skapa en egen `Prompt` funktion och spara den i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="a4702-109">You can customize the prompt by creating your own `Prompt` function and saving it in your PowerShell profile.</span></span>

## <a name="about-the-prompt-function"></a><span data-ttu-id="a4702-110">Om funktionen prompt</span><span class="sxs-lookup"><span data-stu-id="a4702-110">About the Prompt function</span></span>

<span data-ttu-id="a4702-111">`Prompt`Funktionen bestämmer utseendet på PowerShell-prompten.</span><span class="sxs-lookup"><span data-stu-id="a4702-111">The `Prompt` function determines the appearance of the PowerShell prompt.</span></span>
<span data-ttu-id="a4702-112">PowerShell innehåller en inbyggd `Prompt` funktion, men du kan åsidosätta den genom att definiera en egen `Prompt` funktion.</span><span class="sxs-lookup"><span data-stu-id="a4702-112">PowerShell comes with a built-in `Prompt` function, but you can override it by defining your own `Prompt` function.</span></span>

<span data-ttu-id="a4702-113">`Prompt`Funktionen har följande syntax:</span><span class="sxs-lookup"><span data-stu-id="a4702-113">The `Prompt` function has the following syntax:</span></span>

```powershell
function Prompt { <function-body> }
```

<span data-ttu-id="a4702-114">`Prompt`Funktionen måste returnera ett objekt.</span><span class="sxs-lookup"><span data-stu-id="a4702-114">The `Prompt` function must return an object.</span></span> <span data-ttu-id="a4702-115">Vi rekommenderar att du returnerar en sträng eller ett objekt som är formaterat som en sträng.</span><span class="sxs-lookup"><span data-stu-id="a4702-115">As a best practice, return a string or an object that is formatted as a string.</span></span> <span data-ttu-id="a4702-116">Den högsta rekommenderade längden är 80 tecken.</span><span class="sxs-lookup"><span data-stu-id="a4702-116">The maximum recommended length is 80 characters.</span></span>

<span data-ttu-id="a4702-117">Följande funktion returnerar till exempel `Prompt` en "Hello, World"-sträng följt av en höger vinkel paren tes ( `>` ).</span><span class="sxs-lookup"><span data-stu-id="a4702-117">For example, the following `Prompt` function returns a "Hello, World" string followed by a  right angle bracket (`>`).</span></span>

```powershell
PS C:\> function prompt {"Hello, World > "}
Hello, World >
```

### <a name="getting-the-prompt-function"></a><span data-ttu-id="a4702-118">Hämtar prompt-funktionen</span><span class="sxs-lookup"><span data-stu-id="a4702-118">Getting the Prompt function</span></span>

<span data-ttu-id="a4702-119">Hämta `Prompt` funktionen genom att använda `Get-Command` cmdleten eller använda `Get-Item` cmdleten i funktions enheten.</span><span class="sxs-lookup"><span data-stu-id="a4702-119">To get the `Prompt` function, use the `Get-Command` cmdlet or use the `Get-Item` cmdlet in the Function drive.</span></span>

<span data-ttu-id="a4702-120">Exempel:</span><span class="sxs-lookup"><span data-stu-id="a4702-120">For example:</span></span>

```powershell
PS C:\> Get-Command Prompt

CommandType     Name      ModuleName
-----------     ----      ----------
Function        prompt
```

<span data-ttu-id="a4702-121">Om du vill hämta skriptet som anger värdet för prompten använder du punkt metoden för att hämta egenskapen **script block** för `Prompt` funktionen.</span><span class="sxs-lookup"><span data-stu-id="a4702-121">To get the script that sets the value of the prompt, use the dot method to get the **ScriptBlock** property of the `Prompt` function.</span></span>

<span data-ttu-id="a4702-122">Exempel:</span><span class="sxs-lookup"><span data-stu-id="a4702-122">For example:</span></span>

```powershell
(Get-Command Prompt).ScriptBlock
```

```Output
"PS $($executionContext.SessionState.Path.CurrentLocation)$('>' * ($nestedPromptLevel + 1)) "
# .Link
# https://go.microsoft.com/fwlink/?LinkID=225750
# .ExternalHelp System.Management.Automation.dll-help.xml
```

<span data-ttu-id="a4702-123">Precis som alla funktioner `Prompt` lagras funktionen i `Function:` enheten.</span><span class="sxs-lookup"><span data-stu-id="a4702-123">Like all functions, the `Prompt` function is stored in the `Function:` drive.</span></span>
<span data-ttu-id="a4702-124">Om du vill visa skriptet som skapar den aktuella `Prompt` funktionen skriver du:</span><span class="sxs-lookup"><span data-stu-id="a4702-124">To display the script that creates the current `Prompt` function, type:</span></span>

```powershell
(Get-Item function:prompt).ScriptBlock
```

### <a name="the-default-prompt"></a><span data-ttu-id="a4702-125">Standard frågan</span><span class="sxs-lookup"><span data-stu-id="a4702-125">The default prompt</span></span>

<span data-ttu-id="a4702-126">Standard frågan visas bara när `Prompt` funktionen genererar ett fel eller inte returnerar något objekt.</span><span class="sxs-lookup"><span data-stu-id="a4702-126">The default prompt appears only when the `Prompt` function generates an error or does not return an object.</span></span>

<span data-ttu-id="a4702-127">Standard frågan om PowerShell är:</span><span class="sxs-lookup"><span data-stu-id="a4702-127">The default PowerShell prompt is:</span></span>

```
PS>
```

<span data-ttu-id="a4702-128">Följande kommando anger till exempel `Prompt` funktionen till `$null` , som är ogiltig.</span><span class="sxs-lookup"><span data-stu-id="a4702-128">For example, the following command sets the `Prompt` function to `$null`, which is invalid.</span></span> <span data-ttu-id="a4702-129">Därför visas standard meddelandet.</span><span class="sxs-lookup"><span data-stu-id="a4702-129">As a result, the default prompt appears.</span></span>

```powershell
PS C:\> function prompt {$null}
PS>
```

<span data-ttu-id="a4702-130">Eftersom PowerShell innehåller en inbyggd prompt visas normalt inte standard meddelandet.</span><span class="sxs-lookup"><span data-stu-id="a4702-130">Because PowerShell comes with a built-in prompt, you usually do not see the default prompt.</span></span>

### <a name="built-in-prompt"></a><span data-ttu-id="a4702-131">Inbyggd prompt</span><span class="sxs-lookup"><span data-stu-id="a4702-131">Built-in prompt</span></span>

<span data-ttu-id="a4702-132">PowerShell innehåller en inbyggd `Prompt` funktion.</span><span class="sxs-lookup"><span data-stu-id="a4702-132">PowerShell includes a built-in `Prompt` function.</span></span>

```powershell
function prompt {
    $(if (Test-Path variable:/PSDebugContext) { '[DBG]: ' }
      else { '' }) + 'PS ' + $(Get-Location) +
        $(if ($NestedPromptLevel -ge 1) { '>>' }) + '> '
}
```

<span data-ttu-id="a4702-133">Funktionen använder `Test-Path` cmdleten för att avgöra om den `$PSDebugContext` automatiska variabeln är ifylld.</span><span class="sxs-lookup"><span data-stu-id="a4702-133">The function uses the `Test-Path` cmdlet to determine whether the `$PSDebugContext` automatic variable is populated.</span></span> <span data-ttu-id="a4702-134">Om `$PSDebugContext` är ifylld är du i fel söknings läge och `[DBG]:` läggs till i prompten enligt följande:</span><span class="sxs-lookup"><span data-stu-id="a4702-134">If `$PSDebugContext` is populated, you are in debugging mode, and `[DBG]:` is added to the prompt, as follows:</span></span>

```Output
[DBG]: PS C:\ps-test>
```

<span data-ttu-id="a4702-135">Om `$PSDebugContext` inte har fyllts i, läggs funktionen `PS` till i prompten.</span><span class="sxs-lookup"><span data-stu-id="a4702-135">If `$PSDebugContext` is not populated, the function adds `PS` to the prompt.</span></span>
<span data-ttu-id="a4702-136">Och funktionen använder `Get-Location` cmdleten för att hämta aktuell katalog plats för fil systemet.</span><span class="sxs-lookup"><span data-stu-id="a4702-136">And, the function uses the `Get-Location` cmdlet to get the current file system directory location.</span></span> <span data-ttu-id="a4702-137">Sedan lägger den till en höger vinkel paren tes ( `>` ).</span><span class="sxs-lookup"><span data-stu-id="a4702-137">Then, it adds a right angle bracket (`>`).</span></span>

<span data-ttu-id="a4702-138">Exempel:</span><span class="sxs-lookup"><span data-stu-id="a4702-138">For example:</span></span>

```Output
PS C:\ps-test>
```

<span data-ttu-id="a4702-139">Om du är i en kapslad prompt lägger funktionen till två vinkelparenteser ( `>>` ) i prompten.</span><span class="sxs-lookup"><span data-stu-id="a4702-139">If you are in a nested prompt, the function adds two angle brackets (`>>`) to the prompt.</span></span> <span data-ttu-id="a4702-140">(Du är i en kapslad prompt om värdet för den `$NestedPromptLevel` automatiska variabeln är större än 1.)</span><span class="sxs-lookup"><span data-stu-id="a4702-140">(You are in a nested prompt if the value of the `$NestedPromptLevel` automatic variable is greater than 1.)</span></span>

<span data-ttu-id="a4702-141">Om du till exempel felsöker i en kapslad prompt liknar prompten följande fråga:</span><span class="sxs-lookup"><span data-stu-id="a4702-141">For example, when you are debugging in a nested prompt, the prompt resembles the following prompt:</span></span>

```Output
[DBG] PS C:\ps-test>>>
```

### <a name="changes-to-the-prompt"></a><span data-ttu-id="a4702-142">Ändringar i prompten</span><span class="sxs-lookup"><span data-stu-id="a4702-142">Changes to the prompt</span></span>

<span data-ttu-id="a4702-143">`Enter-PSSession`Cmdleten prepends namnet på fjärrdatorn till den aktuella `Prompt` funktionen.</span><span class="sxs-lookup"><span data-stu-id="a4702-143">The `Enter-PSSession` cmdlet prepends the name of the remote computer to the current `Prompt` function.</span></span> <span data-ttu-id="a4702-144">När du använder `Enter-PSSession` cmdleten för att starta en session med en fjärrdator, ändras kommando tolken så att den innehåller namnet på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="a4702-144">When you use the `Enter-PSSession` cmdlet to start a session with a remote computer, the command prompt changes to include the name of the remote computer.</span></span> <span data-ttu-id="a4702-145">Exempel:</span><span class="sxs-lookup"><span data-stu-id="a4702-145">For example:</span></span>

```Output
PS Hello, World> Enter-PSSession Server01
[Server01]: PS Hello, World>
```

<span data-ttu-id="a4702-146">Andra PowerShell-värdprogram och alternativa gränssnitt kan ha sina egna anpassade kommando tolkar.</span><span class="sxs-lookup"><span data-stu-id="a4702-146">Other PowerShell host applications and alternate shells might have their own custom command prompts.</span></span>

<span data-ttu-id="a4702-147">Mer information om de `$PSDebugContext` `$NestedPromptLevel` automatiska variablerna och finns i [about_Automatic_Variables](about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="a4702-147">For more information about the `$PSDebugContext` and `$NestedPromptLevel` automatic variables, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

### <a name="how-to-customize-the-prompt"></a><span data-ttu-id="a4702-148">Anpassa prompten</span><span class="sxs-lookup"><span data-stu-id="a4702-148">How to customize the prompt</span></span>

<span data-ttu-id="a4702-149">Om du vill anpassa prompten skriver du en ny `Prompt` funktion.</span><span class="sxs-lookup"><span data-stu-id="a4702-149">To customize the prompt, write a new `Prompt` function.</span></span> <span data-ttu-id="a4702-150">Funktionen är inte skyddad, så du kan skriva över den.</span><span class="sxs-lookup"><span data-stu-id="a4702-150">The function is not protected, so you can overwrite it.</span></span>

<span data-ttu-id="a4702-151">Skriv följande om du vill skriva en `Prompt` funktion:</span><span class="sxs-lookup"><span data-stu-id="a4702-151">To write a `Prompt` function, type the following:</span></span>

```powershell
function prompt { }
```

<span data-ttu-id="a4702-152">Ange sedan de kommandon eller den sträng som skapar din prompt mellan klammerparenteserna.</span><span class="sxs-lookup"><span data-stu-id="a4702-152">Then, between the braces, enter the commands or the string that creates your prompt.</span></span>

<span data-ttu-id="a4702-153">Följande prompt innehåller till exempel ditt dator namn:</span><span class="sxs-lookup"><span data-stu-id="a4702-153">For example, the following prompt includes your computer name:</span></span>

```powershell
function prompt {"PS [$env:COMPUTERNAME]> "}
```

<span data-ttu-id="a4702-154">På Server01-datorn liknar prompten följande prompt:</span><span class="sxs-lookup"><span data-stu-id="a4702-154">On the Server01 computer, the prompt resembles the following prompt:</span></span>

```Output
PS [Server01] >
```

<span data-ttu-id="a4702-155">Följande `Prompt` funktion innehåller aktuellt datum och tid:</span><span class="sxs-lookup"><span data-stu-id="a4702-155">The following `Prompt` function includes the current date and time:</span></span>

```powershell
function prompt {"$(Get-Date)> "}
```

<span data-ttu-id="a4702-156">Prompten liknar följande prompt:</span><span class="sxs-lookup"><span data-stu-id="a4702-156">The prompt resembles the following prompt:</span></span>

```Output
03/15/2012 17:49:47>
```

<span data-ttu-id="a4702-157">Du kan också ändra standard `Prompt` funktionen:</span><span class="sxs-lookup"><span data-stu-id="a4702-157">You can also change the default `Prompt` function:</span></span>

<span data-ttu-id="a4702-158">Till exempel läggs följande ändrade `Prompt` funktion till i `[ADMIN]:` den inbyggda PowerShell-prompten när PowerShell öppnas med alternativet **Kör som administratör** :</span><span class="sxs-lookup"><span data-stu-id="a4702-158">For example, the following modified `Prompt` function adds `[ADMIN]:` to the built-in PowerShell prompt when PowerShell is opened by using the **Run as administrator** option:</span></span>

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

<span data-ttu-id="a4702-159">När du startar PowerShell med alternativet **Kör som administratör** visas ett meddelande som liknar följande meddelande:</span><span class="sxs-lookup"><span data-stu-id="a4702-159">When you start PowerShell by using the **Run as administrator** option, a prompt that resembles the following prompt appears:</span></span>

```Output
[ADMIN]: PS C:\ps-test>
```

<span data-ttu-id="a4702-160">Följande `Prompt` funktion visar historik-ID för nästa kommando.</span><span class="sxs-lookup"><span data-stu-id="a4702-160">The following `Prompt` function displays the history ID of the next command.</span></span> <span data-ttu-id="a4702-161">Om du vill visa kommando historiken använder du `Get-History` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a4702-161">To view the command history, use the `Get-History` cmdlet.</span></span>

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

<span data-ttu-id="a4702-162">Följande prompt använder `Write-Host` `Get-Random` cmdletarna och för att skapa en prompt som ändrar färg slumpmässigt.</span><span class="sxs-lookup"><span data-stu-id="a4702-162">The following prompt uses the `Write-Host` and `Get-Random` cmdlets to create a prompt that changes color randomly.</span></span> <span data-ttu-id="a4702-163">Eftersom `Write-Host` skrivningar till det aktuella värd programmet, men inte returnerar ett objekt, innehåller den här funktionen en `Return` instruktion.</span><span class="sxs-lookup"><span data-stu-id="a4702-163">Because `Write-Host` writes to the current host application but does not return an object, this function includes a `Return` statement.</span></span> <span data-ttu-id="a4702-164">Utan den, använder PowerShell standard frågan `PS>` .</span><span class="sxs-lookup"><span data-stu-id="a4702-164">Without it, PowerShell uses the default prompt, `PS>`.</span></span>

```powershell
function prompt {
    $color = Get-Random -Min 1 -Max 16
    Write-Host ("PS " + $(Get-Location) +">") -NoNewLine `
     -ForegroundColor $Color
    return " "
}
```

### <a name="saving-the-prompt-function"></a><span data-ttu-id="a4702-165">Spara prompt-funktionen</span><span class="sxs-lookup"><span data-stu-id="a4702-165">Saving the Prompt function</span></span>

<span data-ttu-id="a4702-166">Precis som vilken funktion som helst `Prompt` finns funktionen bara i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="a4702-166">Like any function, the `Prompt` function exists only in the current session.</span></span> <span data-ttu-id="a4702-167">Om du vill spara `Prompt` funktionen i framtida sessioner lägger du till den i dina PowerShell-profiler.</span><span class="sxs-lookup"><span data-stu-id="a4702-167">To save the `Prompt` function for future sessions, add it to your PowerShell profiles.</span></span> <span data-ttu-id="a4702-168">Mer information om profiler finns [about_Profiles](about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="a4702-168">For more information about profiles, see [about_Profiles](about_Profiles.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a4702-169">Se även</span><span class="sxs-lookup"><span data-stu-id="a4702-169">See also</span></span>

[<span data-ttu-id="a4702-170">Get-location</span><span class="sxs-lookup"><span data-stu-id="a4702-170">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)

[<span data-ttu-id="a4702-171">Retur-PSSession</span><span class="sxs-lookup"><span data-stu-id="a4702-171">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="a4702-172">Hämta historik</span><span class="sxs-lookup"><span data-stu-id="a4702-172">Get-History</span></span>](xref:Microsoft.PowerShell.Core.Get-History)

[<span data-ttu-id="a4702-173">Hämta slumpmässiga</span><span class="sxs-lookup"><span data-stu-id="a4702-173">Get-Random</span></span>](xref:Microsoft.PowerShell.Utility.Get-Random)

[<span data-ttu-id="a4702-174">Skriv värd</span><span class="sxs-lookup"><span data-stu-id="a4702-174">Write-Host</span></span>](xref:Microsoft.PowerShell.Utility.Write-Host)

[<span data-ttu-id="a4702-175">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="a4702-175">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="a4702-176">about_Functions</span><span class="sxs-lookup"><span data-stu-id="a4702-176">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="a4702-177">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="a4702-177">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="a4702-178">about_Debuggers</span><span class="sxs-lookup"><span data-stu-id="a4702-178">about_Debuggers</span></span>](about_Debuggers.md)

[<span data-ttu-id="a4702-179">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="a4702-179">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

