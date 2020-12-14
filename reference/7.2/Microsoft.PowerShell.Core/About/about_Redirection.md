---
description: Förklarar hur du omdirigerar utdata från PowerShell till textfiler.
Locale: en-US
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_redirection?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Redirection
ms.openlocfilehash: fe8da80c6aa0aae3d8d175920283bc31de0c3386
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710555"
---
# <a name="about-redirection"></a><span data-ttu-id="bda70-103">Om omdirigering</span><span class="sxs-lookup"><span data-stu-id="bda70-103">About Redirection</span></span>

## <a name="short-description"></a><span data-ttu-id="bda70-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="bda70-104">Short description</span></span>
<span data-ttu-id="bda70-105">Förklarar hur du omdirigerar utdata från PowerShell till textfiler.</span><span class="sxs-lookup"><span data-stu-id="bda70-105">Explains how to redirect output from PowerShell to text files.</span></span>

## <a name="long-description"></a><span data-ttu-id="bda70-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="bda70-106">Long description</span></span>

<span data-ttu-id="bda70-107">Som standard skickar PowerShell utdata till PowerShell-värden.</span><span class="sxs-lookup"><span data-stu-id="bda70-107">By default, PowerShell sends output to the PowerShell host.</span></span> <span data-ttu-id="bda70-108">Detta är vanligt vis konsol programmet.</span><span class="sxs-lookup"><span data-stu-id="bda70-108">Usually this is the console application.</span></span> <span data-ttu-id="bda70-109">Du kan dock dirigera utdata till en textfil och du kan omdirigera fel utdata till den vanliga utdataströmmen.</span><span class="sxs-lookup"><span data-stu-id="bda70-109">However, you can direct the output to a text file, and you can redirect error output to the regular output stream.</span></span>

<span data-ttu-id="bda70-110">Du kan använda följande metoder för att omdirigera utdata:</span><span class="sxs-lookup"><span data-stu-id="bda70-110">You can use the following methods to redirect output:</span></span>

- <span data-ttu-id="bda70-111">Använd `Out-File` cmdleten som skickar kommandoutdata till en textfil.</span><span class="sxs-lookup"><span data-stu-id="bda70-111">Use the `Out-File` cmdlet, which sends command output to a text file.</span></span>
  <span data-ttu-id="bda70-112">Normalt använder du `Out-File` cmdleten när du behöver använda dess parametrar, till exempel `Encoding` parametrarna,, `Force` `Width` eller `NoClobber` .</span><span class="sxs-lookup"><span data-stu-id="bda70-112">Typically, you use the `Out-File` cmdlet when you need to use its parameters, such as the `Encoding`, `Force`, `Width`, or `NoClobber` parameters.</span></span>

- <span data-ttu-id="bda70-113">Använd `Tee-Object` cmdleten, som skickar kommandoutdata till en textfil och sedan skickar den till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="bda70-113">Use the `Tee-Object` cmdlet, which sends command output to a text file and then sends it to the pipeline.</span></span>

- <span data-ttu-id="bda70-114">Använd operatorerna för PowerShell-omdirigering.</span><span class="sxs-lookup"><span data-stu-id="bda70-114">Use the PowerShell redirection operators.</span></span> <span data-ttu-id="bda70-115">Att använda operatorn för omdirigering med ett fil mål är detsamma som att dirigera till utan `Out-File` extra parametrar.</span><span class="sxs-lookup"><span data-stu-id="bda70-115">Using the redirection operator with a file target is functionally equivalent to piping to `Out-File` with no extra parameters.</span></span>

<span data-ttu-id="bda70-116">Mer information om strömmar finns [about_Output_Streams](about_Output_Streams.md).</span><span class="sxs-lookup"><span data-stu-id="bda70-116">For more information about streams, see [about_Output_Streams](about_Output_Streams.md).</span></span>

### <a name="redirectable-output-streams"></a><span data-ttu-id="bda70-117">Omdirigerade utgående strömmar</span><span class="sxs-lookup"><span data-stu-id="bda70-117">Redirectable output streams</span></span>

<span data-ttu-id="bda70-118">PowerShell stöder omdirigering av följande utdata-strömmar.</span><span class="sxs-lookup"><span data-stu-id="bda70-118">PowerShell supports redirection of the following output streams.</span></span>

| <span data-ttu-id="bda70-119">Skicka #</span><span class="sxs-lookup"><span data-stu-id="bda70-119">Stream #</span></span> |      <span data-ttu-id="bda70-120">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="bda70-120">Description</span></span>       | <span data-ttu-id="bda70-121">Infört i</span><span class="sxs-lookup"><span data-stu-id="bda70-121">Introduced in</span></span>  |    <span data-ttu-id="bda70-122">Skriv cmdlet</span><span class="sxs-lookup"><span data-stu-id="bda70-122">Write Cmdlet</span></span>     |
| -------- | ---------------------- | -------------- | ------------------- |
| <span data-ttu-id="bda70-123">1</span><span class="sxs-lookup"><span data-stu-id="bda70-123">1</span></span>        | <span data-ttu-id="bda70-124">**Lyckades** Skicka</span><span class="sxs-lookup"><span data-stu-id="bda70-124">**Success** Stream</span></span>     | <span data-ttu-id="bda70-125">PowerShell 2,0</span><span class="sxs-lookup"><span data-stu-id="bda70-125">PowerShell 2.0</span></span> | `Write-Output`      |
| <span data-ttu-id="bda70-126">2</span><span class="sxs-lookup"><span data-stu-id="bda70-126">2</span></span>        | <span data-ttu-id="bda70-127">**Fel** Skicka</span><span class="sxs-lookup"><span data-stu-id="bda70-127">**Error** Stream</span></span>       | <span data-ttu-id="bda70-128">PowerShell 2,0</span><span class="sxs-lookup"><span data-stu-id="bda70-128">PowerShell 2.0</span></span> | `Write-Error`       |
| <span data-ttu-id="bda70-129">3</span><span class="sxs-lookup"><span data-stu-id="bda70-129">3</span></span>        | <span data-ttu-id="bda70-130">**Varning** Skicka</span><span class="sxs-lookup"><span data-stu-id="bda70-130">**Warning** Stream</span></span>     | <span data-ttu-id="bda70-131">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="bda70-131">PowerShell 3.0</span></span> | `Write-Warning`     |
| <span data-ttu-id="bda70-132">4</span><span class="sxs-lookup"><span data-stu-id="bda70-132">4</span></span>        | <span data-ttu-id="bda70-133">**Utförlig** Skicka</span><span class="sxs-lookup"><span data-stu-id="bda70-133">**Verbose** Stream</span></span>     | <span data-ttu-id="bda70-134">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="bda70-134">PowerShell 3.0</span></span> | `Write-Verbose`     |
| <span data-ttu-id="bda70-135">5</span><span class="sxs-lookup"><span data-stu-id="bda70-135">5</span></span>        | <span data-ttu-id="bda70-136">**Felsök** Skicka</span><span class="sxs-lookup"><span data-stu-id="bda70-136">**Debug** Stream</span></span>       | <span data-ttu-id="bda70-137">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="bda70-137">PowerShell 3.0</span></span> | `Write-Debug`       |
| <span data-ttu-id="bda70-138">6</span><span class="sxs-lookup"><span data-stu-id="bda70-138">6</span></span>        | <span data-ttu-id="bda70-139">**Information** Skicka</span><span class="sxs-lookup"><span data-stu-id="bda70-139">**Information** Stream</span></span> | <span data-ttu-id="bda70-140">PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="bda70-140">PowerShell 5.0</span></span> | `Write-Information` |
| *        | <span data-ttu-id="bda70-141">Alla strömmar</span><span class="sxs-lookup"><span data-stu-id="bda70-141">All Streams</span></span>            | <span data-ttu-id="bda70-142">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="bda70-142">PowerShell 3.0</span></span> |                     |

> [!NOTE]
> <span data-ttu-id="bda70-143">Det finns också en **förlopps** ström i PowerShell, men den stöder inte omdirigering.</span><span class="sxs-lookup"><span data-stu-id="bda70-143">There is also a **Progress** stream in PowerShell, but it does not support redirection.</span></span>

### <a name="powershell-redirection-operators"></a><span data-ttu-id="bda70-144">Operatorer för PowerShell-omdirigering</span><span class="sxs-lookup"><span data-stu-id="bda70-144">PowerShell redirection operators</span></span>

<span data-ttu-id="bda70-145">Operatorerna för PowerShell-omdirigering är följande, där `n` representerar Stream-numret.</span><span class="sxs-lookup"><span data-stu-id="bda70-145">The PowerShell redirection operators are as follows, where `n` represents the stream number.</span></span> <span data-ttu-id="bda70-146">**Framgångs** strömmen ( `1` ) är standard om ingen ström anges.</span><span class="sxs-lookup"><span data-stu-id="bda70-146">The **Success** stream ( `1` ) is the default if no stream is specified.</span></span>

| <span data-ttu-id="bda70-147">Operator</span><span class="sxs-lookup"><span data-stu-id="bda70-147">Operator</span></span> |                         <span data-ttu-id="bda70-148">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="bda70-148">Description</span></span>                         | <span data-ttu-id="bda70-149">Syntax</span><span class="sxs-lookup"><span data-stu-id="bda70-149">Syntax</span></span> |
| -------- | ----------------------------------------------------------- | ------ |
| `>`      | <span data-ttu-id="bda70-150">Skicka angiven data ström till en fil.</span><span class="sxs-lookup"><span data-stu-id="bda70-150">Send specified stream to a file.</span></span>                            | `n>`   |
| `>>`     | <span data-ttu-id="bda70-151">**Lägg till** angiven data ström i en fil.</span><span class="sxs-lookup"><span data-stu-id="bda70-151">**Append** specified stream to a file.</span></span>                      | `n>>`  |
| `>&1`    | <span data-ttu-id="bda70-152">_Omdirigerar_ den angivna data strömmen till den **framgångs rik** data strömmen.</span><span class="sxs-lookup"><span data-stu-id="bda70-152">_Redirects_ the specified stream to the **Success** stream.</span></span> | `n>&1` |

> [!NOTE]
> <span data-ttu-id="bda70-153">Till skillnad från vissa UNIX-gränssnitt kan du bara omdirigera andra strömmar till strömmen som **lyckats** .</span><span class="sxs-lookup"><span data-stu-id="bda70-153">Unlike some Unix shells, you can only redirect other streams to the **Success** stream.</span></span>

## <a name="examples"></a><span data-ttu-id="bda70-154">Exempel</span><span class="sxs-lookup"><span data-stu-id="bda70-154">Examples</span></span>

### <a name="example-1-redirect-errors-and-output-to-a-file"></a><span data-ttu-id="bda70-155">Exempel 1: omdirigera fel och utdata till en fil</span><span class="sxs-lookup"><span data-stu-id="bda70-155">Example 1: Redirect errors and output to a file</span></span>

<span data-ttu-id="bda70-156">Det här exemplet körs `dir` på ett objekt som kommer att lyckas, och ett som kommer att vara fel.</span><span class="sxs-lookup"><span data-stu-id="bda70-156">This example runs `dir` on one item that will succeed, and one that will error.</span></span>

```powershell
dir 'C:\', 'fakepath' 2>&1 > .\dir.log
```

<span data-ttu-id="bda70-157">Den använder `2>&1` för att dirigera om **fel** strömmen till  strömmen och `>` skicka den resulterande **framgångs** strömmen till en fil med namnet`dir.log`</span><span class="sxs-lookup"><span data-stu-id="bda70-157">It uses `2>&1` to redirect the **Error** stream to the **Success** stream, and `>` to send the resultant **Success** stream to a file called `dir.log`</span></span>

### <a name="example-2-send-all-success-stream-data-to-a-file"></a><span data-ttu-id="bda70-158">Exempel 2: skicka alla lyckade Ströms data till en fil</span><span class="sxs-lookup"><span data-stu-id="bda70-158">Example 2: Send all Success stream data to a file</span></span>

<span data-ttu-id="bda70-159">I det här exemplet skickas alla **lyckade** data ström data till en fil med namnet `script.log` .</span><span class="sxs-lookup"><span data-stu-id="bda70-159">This example sends all **Success** stream data to a file called `script.log`.</span></span>

```powershell
.\script.ps1 > script.log
```

### <a name="example-3-send-success-warning-and-error-streams-to-a-file"></a><span data-ttu-id="bda70-160">Exempel 3: skicka lyckade, varnings-och fel strömmar till en fil</span><span class="sxs-lookup"><span data-stu-id="bda70-160">Example 3: Send Success, Warning, and Error streams to a file</span></span>

<span data-ttu-id="bda70-161">Det här exemplet visar hur du kan kombinera omdirigerings operatörer för att uppnå önskat resultat.</span><span class="sxs-lookup"><span data-stu-id="bda70-161">This example shows how you can combine redirection operators to achieve a desired result.</span></span>

```powershell
&{
   Write-Warning "hello"
   Write-Error "hello"
   Write-Output "hi"
} 3>&1 2>&1 > P:\Temp\redirection.log
```

- <span data-ttu-id="bda70-162">`3>&1` omdirigerar **varnings** strömmen till den **framgångs rik** data strömmen.</span><span class="sxs-lookup"><span data-stu-id="bda70-162">`3>&1` redirects the **Warning** stream to the **Success** stream.</span></span>
- <span data-ttu-id="bda70-163">`2>&1` omdirigerar **fel** strömmen till den **framgångs rik** strömmen (som även innehåller alla **varnings** data från data)</span><span class="sxs-lookup"><span data-stu-id="bda70-163">`2>&1` redirects the **Error** stream to the **Success** stream (which also now includes all **Warning** stream data)</span></span>
- <span data-ttu-id="bda70-164">`>` omdirigerar den **framgångs rik** data strömmen (som nu innehåller både **varnings** -och **fel** strömmar) till en fil `C:\temp\redirection.log` med namnet.</span><span class="sxs-lookup"><span data-stu-id="bda70-164">`>` redirects the **Success** stream (which now contains both **Warning** and **Error** streams) to a file called `C:\temp\redirection.log`)</span></span>

### <a name="example-4-redirect-all-streams-to-a-file"></a><span data-ttu-id="bda70-165">Exempel 4: omdirigera alla strömmar till en fil</span><span class="sxs-lookup"><span data-stu-id="bda70-165">Example 4: Redirect all streams to a file</span></span>

<span data-ttu-id="bda70-166">Det här exemplet skickar alla strömmar utdata från ett skript `script.ps1` som kallas för en fil med namnet `script.log`</span><span class="sxs-lookup"><span data-stu-id="bda70-166">This example sends all streams output from a script called `script.ps1` to a file called `script.log`</span></span>

```powershell
.\script.ps1 *> script.log
```

### <a name="example-5-suppress-all-write-host-and-information-stream-data"></a><span data-ttu-id="bda70-167">Exempel 5: utelämna alla Write-Host och informations data strömmar</span><span class="sxs-lookup"><span data-stu-id="bda70-167">Example 5: Suppress all Write-Host and Information stream data</span></span>

<span data-ttu-id="bda70-168">I det här exemplet ignoreras alla informations data strömmar.</span><span class="sxs-lookup"><span data-stu-id="bda70-168">This example suppresses all information stream data.</span></span> <span data-ttu-id="bda70-169">Om du vill läsa mer om **information** Stream-cmdletar, se [Write-Host](xref:Microsoft.PowerShell.Utility.Write-Host) och [Write-information](xref:Microsoft.PowerShell.Utility.Write-Information)</span><span class="sxs-lookup"><span data-stu-id="bda70-169">To read more about **Information** stream cmdlets, see [Write-Host](xref:Microsoft.PowerShell.Utility.Write-Host) and [Write-Information](xref:Microsoft.PowerShell.Utility.Write-Information)</span></span>

```powershell
&{
   Write-Host "Hello"
   Write-Information "Hello" -InformationAction Continue
} 6> $null
```

### <a name="example-6-show-the-effect-of-action-preferences"></a><span data-ttu-id="bda70-170">Exempel 6: Visa effekterna av åtgärds inställningar</span><span class="sxs-lookup"><span data-stu-id="bda70-170">Example 6: Show the effect of Action Preferences</span></span>

<span data-ttu-id="bda70-171">Variabler och parametrar för åtgärds inställningar kan ändra vad som skrivs till en viss data ström.</span><span class="sxs-lookup"><span data-stu-id="bda70-171">Action Preference variables and parameters can change what gets written to a particular stream.</span></span> <span data-ttu-id="bda70-172">Skriptet i det här exemplet visar hur värdet för `$ErrorActionPreference` påverkar vad som skrivs till **fel** strömmen.</span><span class="sxs-lookup"><span data-stu-id="bda70-172">The script in this example shows how the value of `$ErrorActionPreference` affects what gets written to the **Error** stream.</span></span>

```powershell
$ErrorActionPreference = 'Continue'
$ErrorActionPreference > log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'SilentlyContinue'
$ErrorActionPreference >> log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'Stop'
$ErrorActionPreference >> log.txt
Try {
    get-item /not-here 2>&1 >> log.txt
}
catch {
    "`tError caught!" >> log.txt
}
$ErrorActionPreference = 'Ignore'
$ErrorActionPreference >> log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'Inquire'
$ErrorActionPreference >> log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'Continue'
```

<span data-ttu-id="bda70-173">När vi kör det här skriptet uppmanas vi att få frågan när det `$ErrorActionPreference` är inställt på `Inquire` .</span><span class="sxs-lookup"><span data-stu-id="bda70-173">When we run this script we get prompted when `$ErrorActionPreference` is set to `Inquire`.</span></span>

```powershell
PS C:\temp> .\test.ps1

Confirm
Cannot find path 'C:\not-here' because it does not exist.
[Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"): H
Get-Item: C:\temp\test.ps1:23
Line |
  23 |  get-item /not-here 2>&1 >> log.txt
     |  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     | The running command stopped because the user selected the Stop option.
```

<span data-ttu-id="bda70-174">När vi undersöker logg filen ser vi följande:</span><span class="sxs-lookup"><span data-stu-id="bda70-174">When we examine the log file we see the following:</span></span>

```
PS C:\temp> Get-Content .\log.txt
Continue

Get-Item: C:\temp\test.ps1:3
Line |
   3 |  get-item /not-here 2>&1 >> log.txt
     |  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     | Cannot find path 'C:\not-here' because it does not exist.

SilentlyContinue
Stop
    Error caught!
Ignore
Inquire
```

## <a name="notes"></a><span data-ttu-id="bda70-175">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="bda70-175">Notes</span></span>

<span data-ttu-id="bda70-176">De omdirigerings operatörer som inte lägger till data ( `>` och `n>` ) skriver över det aktuella innehållet i den angivna filen utan varning.</span><span class="sxs-lookup"><span data-stu-id="bda70-176">The redirection operators that do not append data (`>` and `n>`) overwrite the current contents of the specified file without warning.</span></span>

<span data-ttu-id="bda70-177">Om filen däremot är skrivskyddad, dold eller en system fil, **Miss lyckas** omdirigeringen.</span><span class="sxs-lookup"><span data-stu-id="bda70-177">However, if the file is a read-only, hidden, or system file, the redirection **fails**.</span></span> <span data-ttu-id="bda70-178">Operatorerna Lägg till omdirigering ( `>>` och `n>>` ) skriver inte till en skrivskyddad fil, utan lägger till innehåll i en system fil eller en dold fil.</span><span class="sxs-lookup"><span data-stu-id="bda70-178">The append redirection operators (`>>` and `n>>`) do not write to a read-only file, but they append content to a system or hidden file.</span></span>

<span data-ttu-id="bda70-179">Använd `Out-File` cmdleten med parametern för att tvinga fram en omdirigering av innehåll till en skrivskyddad, dold eller system fil `Force` .</span><span class="sxs-lookup"><span data-stu-id="bda70-179">To force the redirection of content to a read-only, hidden, or system file, use the `Out-File` cmdlet with its `Force` parameter.</span></span>

<span data-ttu-id="bda70-180">När du skriver till filer använder omdirigerings operatörerna `UTF8NoBOM` encoding.</span><span class="sxs-lookup"><span data-stu-id="bda70-180">When you are writing to files, the redirection operators use `UTF8NoBOM` encoding.</span></span> <span data-ttu-id="bda70-181">Om filen har en annan kodning kanske utdata inte är korrekt formaterade.</span><span class="sxs-lookup"><span data-stu-id="bda70-181">If the file has a different encoding, the output might not be formatted correctly.</span></span> <span data-ttu-id="bda70-182">Om du vill skriva till filer med en annan kodning använder du `Out-File` cmdleten med dess `Encoding` parameter.</span><span class="sxs-lookup"><span data-stu-id="bda70-182">To write to files with a different encoding, use the `Out-File` cmdlet with its `Encoding` parameter.</span></span>

### <a name="potential-confusion-with-comparison-operators"></a><span data-ttu-id="bda70-183">Potentiell förvirring med jämförelse operatörer</span><span class="sxs-lookup"><span data-stu-id="bda70-183">Potential confusion with comparison operators</span></span>

<span data-ttu-id="bda70-184">`>`Operatorn är inte att förväxlas med [större än-](about_Comparison_Operators.md#-gt) jämförelse operatorn (ofta betecknad som `>` i andra programmeringsspråk).</span><span class="sxs-lookup"><span data-stu-id="bda70-184">The `>` operator is not to be confused with the [Greater-than](about_Comparison_Operators.md#-gt) comparison operator (often denoted as `>` in other programming languages).</span></span>

<span data-ttu-id="bda70-185">Beroende på vilka objekt som jämförs kan utdata som används `>` vara korrekta (eftersom 36 inte är större än 42).</span><span class="sxs-lookup"><span data-stu-id="bda70-185">Depending on the objects being compared, the output using `>` can appear to be correct (because 36 is not greater than 42).</span></span>

```powershell
PS> if (36 > 42) { "true" } else { "false" }
false
```

<span data-ttu-id="bda70-186">En kontroll av det lokala fil systemet kan dock se att en fil som heter `42` har skrivits, med innehållet `36` .</span><span class="sxs-lookup"><span data-stu-id="bda70-186">However, a check of the local filesystem can see that a file called `42` was written, with the contents `36`.</span></span>

```powershell
PS> dir

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
------          1/02/20  10:10 am              3 42

PS> cat 42
36
```

<span data-ttu-id="bda70-187">Försök att använda omvänd jämförelse `<` (mindre än) ger ett systemfel:</span><span class="sxs-lookup"><span data-stu-id="bda70-187">Attempting to use the reverse comparison `<` (less than), yields a system error:</span></span>

```powershell
PS> if (36 < 42) { "true" } else { "false" }
At line:1 char:8
+ if (36 < 42) { "true" } else { "false" }
+        ~
The '<' operator is reserved for future use.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : RedirectionNotSupported
```

<span data-ttu-id="bda70-188">Om en numerisk jämförelse är den nödvändiga åtgärden `-lt` och `-gt` ska användas.</span><span class="sxs-lookup"><span data-stu-id="bda70-188">If numeric comparison is the required operation, `-lt` and `-gt` should be used.</span></span> <span data-ttu-id="bda70-189">Se: [ `-gt` jämförelse operator](about_Comparison_Operators.md#-gt)</span><span class="sxs-lookup"><span data-stu-id="bda70-189">See: [`-gt` Comparison Operator](about_Comparison_Operators.md#-gt)</span></span>

## <a name="see-also"></a><span data-ttu-id="bda70-190">Se även</span><span class="sxs-lookup"><span data-stu-id="bda70-190">See also</span></span>

- [<span data-ttu-id="bda70-191">Ut-fil</span><span class="sxs-lookup"><span data-stu-id="bda70-191">Out-File</span></span>](xref:Microsoft.PowerShell.Utility.Out-File)
- [<span data-ttu-id="bda70-192">Tee – objekt</span><span class="sxs-lookup"><span data-stu-id="bda70-192">Tee-Object</span></span>](xref:Microsoft.PowerShell.Utility.Tee-Object)
- [<span data-ttu-id="bda70-193">Skriv-debug</span><span class="sxs-lookup"><span data-stu-id="bda70-193">Write-Debug</span></span>](xref:Microsoft.PowerShell.Utility.Write-Debug)
- [<span data-ttu-id="bda70-194">Skriv-fel</span><span class="sxs-lookup"><span data-stu-id="bda70-194">Write-Error</span></span>](xref:Microsoft.PowerShell.Utility.Write-Error)
- [<span data-ttu-id="bda70-195">Skriv värd</span><span class="sxs-lookup"><span data-stu-id="bda70-195">Write-Host</span></span>](xref:Microsoft.PowerShell.Utility.Write-Host)
- [<span data-ttu-id="bda70-196">Skriv information</span><span class="sxs-lookup"><span data-stu-id="bda70-196">Write-Information</span></span>](xref:Microsoft.PowerShell.Utility.Write-Information)
- [<span data-ttu-id="bda70-197">Skriva-utdata</span><span class="sxs-lookup"><span data-stu-id="bda70-197">Write-Output</span></span>](xref:Microsoft.PowerShell.Utility.Write-Output)
- [<span data-ttu-id="bda70-198">Skriv förlopp</span><span class="sxs-lookup"><span data-stu-id="bda70-198">Write-Progress</span></span>](xref:Microsoft.PowerShell.Utility.Write-Progress)
- [<span data-ttu-id="bda70-199">Skriv-verbose</span><span class="sxs-lookup"><span data-stu-id="bda70-199">Write-Verbose</span></span>](xref:Microsoft.PowerShell.Utility.Write-Verbose)
- [<span data-ttu-id="bda70-200">Skriv varning</span><span class="sxs-lookup"><span data-stu-id="bda70-200">Write-Warning</span></span>](xref:Microsoft.PowerShell.Utility.Write-Warning)
- [<span data-ttu-id="bda70-201">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="bda70-201">about_Output_Streams</span></span>](about_Output_Streams.md)
- [<span data-ttu-id="bda70-202">about_Operators</span><span class="sxs-lookup"><span data-stu-id="bda70-202">about_Operators</span></span>](about_Operators.md)
- [<span data-ttu-id="bda70-203">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="bda70-203">about_Command_Syntax</span></span>](about_Command_Syntax.md)
- [<span data-ttu-id="bda70-204">about_Path_Syntax</span><span class="sxs-lookup"><span data-stu-id="bda70-204">about_Path_Syntax</span></span>](about_Path_Syntax.md)
