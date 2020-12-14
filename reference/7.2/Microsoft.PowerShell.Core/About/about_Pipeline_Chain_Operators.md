---
description: Beskriver länkning av pipelines med `&&` `||` operatorerna och i PowerShell.
Locale: en-US
ms.date: 09/30/2019
schema: 2.0.0
title: about_Pipeline_Chain_Operators
ms.openlocfilehash: ece84ec061126401e53bf58112cd79a07a816e8d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710986"
---
# <a name="about-pipeline-chain-operators"></a><span data-ttu-id="4dab2-103">Om operatorer för pipeline-kedjan</span><span class="sxs-lookup"><span data-stu-id="4dab2-103">About Pipeline Chain Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="4dab2-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="4dab2-104">Short description</span></span>

<span data-ttu-id="4dab2-105">Beskriver länkning av pipelines med `&&` `||` operatorerna och i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4dab2-105">Describes chaining pipelines with the `&&` and `||` operators in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="4dab2-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="4dab2-106">Long description</span></span>

<span data-ttu-id="4dab2-107">Från och med PowerShell 7 implementerar PowerShell `&&` `||` operatorerna och för att villkorligt kedja pipelines.</span><span class="sxs-lookup"><span data-stu-id="4dab2-107">Beginning in PowerShell 7, PowerShell implements the `&&` and `||` operators to conditionally chain pipelines.</span></span> <span data-ttu-id="4dab2-108">Dessa operatörer är kända i PowerShell som *operatorer för pipeline-kedjan* och liknar dem [och-eller-listor](https://pubs.opengroup.org/onlinepubs/009695399/utilities/xcu_chap02.html#tag_02_09_03) i POSIX-gränssnitt som bash, zsh och sh, samt [villkorsstyrda bearbetnings symboler](/previous-versions/windows/it-pro/windows-xp/bb490954(v=technet.10)#using-multiple-commands-and-conditional-processing-symbols) i Windows Command Shell (cmd.exe).</span><span class="sxs-lookup"><span data-stu-id="4dab2-108">These operators are known in PowerShell as *pipeline chain operators*, and are similar to [AND-OR lists](https://pubs.opengroup.org/onlinepubs/009695399/utilities/xcu_chap02.html#tag_02_09_03) in POSIX shells like bash, zsh and sh, as well as [conditional processing symbols](/previous-versions/windows/it-pro/windows-xp/bb490954(v=technet.10)#using-multiple-commands-and-conditional-processing-symbols) in the Windows Command Shell (cmd.exe).</span></span>

<span data-ttu-id="4dab2-109">`&&`Operatören kör den högra pipelinen om den vänstra pipelinen lyckades.</span><span class="sxs-lookup"><span data-stu-id="4dab2-109">The `&&` operator executes the right-hand pipeline, if the left-hand pipeline succeeded.</span></span> <span data-ttu-id="4dab2-110">I motsatt `||` Kör operatören den högra pipelinen om den vänstra pipelinen misslyckades.</span><span class="sxs-lookup"><span data-stu-id="4dab2-110">Conversely, the `||` operator executes the right-hand pipeline if the left-hand pipeline failed.</span></span>

<span data-ttu-id="4dab2-111">Dessa operatörer använder `$?` `$LASTEXITCODE` variablerna och för att avgöra om en pipeline misslyckades.</span><span class="sxs-lookup"><span data-stu-id="4dab2-111">These operators use the `$?` and `$LASTEXITCODE` variables to determine if a pipeline failed.</span></span> <span data-ttu-id="4dab2-112">På så sätt kan du använda dem med inbyggda kommandon och inte bara med cmdlets eller functions.</span><span class="sxs-lookup"><span data-stu-id="4dab2-112">This allows you to use them with native commands and not just with cmdlets or functions.</span></span> <span data-ttu-id="4dab2-113">Exempel:</span><span class="sxs-lookup"><span data-stu-id="4dab2-113">For example:</span></span>

```powershell
# Create an SSH key pair - if successful copy the public key to clipboard
ssh-keygen -t rsa -b 2048 && Get-Content -Raw ~\.ssh\id_rsa.pub | clip
```

### <a name="examples"></a><span data-ttu-id="4dab2-114">Exempel</span><span class="sxs-lookup"><span data-stu-id="4dab2-114">Examples</span></span>

#### <a name="two-successful-commands"></a><span data-ttu-id="4dab2-115">Två lyckade kommandon</span><span class="sxs-lookup"><span data-stu-id="4dab2-115">Two successful commands</span></span>

```powershell
Write-Output 'First' && Write-Output 'Second'
```

```Output
First
Second
```

#### <a name="first-command-fails-causing-second-not-to-be-executed"></a><span data-ttu-id="4dab2-116">Det första kommandot Miss lyckas, vilket orsakar att den andra inte körs</span><span class="sxs-lookup"><span data-stu-id="4dab2-116">First command fails, causing second not to be executed</span></span>

```powershell
Write-Error 'Bad' && Write-Output 'Second'
```

```Output
Write-Error: Bad
```

#### <a name="first-command-succeeds-so-the-second-command-is-not-executed"></a><span data-ttu-id="4dab2-117">Det första kommandot slutförs, så det andra kommandot körs inte</span><span class="sxs-lookup"><span data-stu-id="4dab2-117">First command succeeds, so the second command is not executed</span></span>

```powershell
Write-Output 'First' || Write-Output 'Second'
```

```Output
First
```

#### <a name="first-command-fails-so-the-second-command-is-executed"></a><span data-ttu-id="4dab2-118">Det första kommandot Miss lyckas, så det andra kommandot körs</span><span class="sxs-lookup"><span data-stu-id="4dab2-118">First command fails, so the second command is executed</span></span>

```powershell
Write-Error 'Bad' || Write-Output 'Second'
```

```Output
Write-Error: Bad
Second
```

<span data-ttu-id="4dab2-119">Pipelinen lyckades definieras av värdet för `$?` variabeln, som PowerShell anger automatiskt efter att en pipeline har körts baserat på dess körnings status.</span><span class="sxs-lookup"><span data-stu-id="4dab2-119">Pipeline success is defined by the value of the `$?` variable, which PowerShell automatically sets after executing a pipeline based on its execution status.</span></span>
<span data-ttu-id="4dab2-120">Det innebär att operatörer i pipeline-kedjan har följande likvärdighet:</span><span class="sxs-lookup"><span data-stu-id="4dab2-120">This means that pipeline chain operators have the following equivalence:</span></span>

```powershell
Test-Command '1' && Test-Command '2'
```

<span data-ttu-id="4dab2-121">fungerar på samma sätt som</span><span class="sxs-lookup"><span data-stu-id="4dab2-121">works the same as</span></span>

```powershell
Test-Command '1'; if ($?) { Test-Command '2' }
```

<span data-ttu-id="4dab2-122">och</span><span class="sxs-lookup"><span data-stu-id="4dab2-122">and</span></span>

```powershell
Test-Command '1' || Test-Command '2'
```

<span data-ttu-id="4dab2-123">fungerar på samma sätt som</span><span class="sxs-lookup"><span data-stu-id="4dab2-123">works the same as</span></span>

```powershell
Test-Command '1'; if (-not $?) { Test-Command '2' }
```

### <a name="assignment-from-pipeline-chains"></a><span data-ttu-id="4dab2-124">Tilldelning från pipeline-kedjor</span><span class="sxs-lookup"><span data-stu-id="4dab2-124">Assignment from pipeline chains</span></span>

<span data-ttu-id="4dab2-125">Genom att tilldela en variabel från en pipeline-kedja tas sammanfogningen av alla pipeliner i kedjan:</span><span class="sxs-lookup"><span data-stu-id="4dab2-125">Assigning a variable from a pipeline chain takes the concatenation of all the pipelines in the chain:</span></span>

```powershell
$result = Write-Output '1' && Write-Output '2'
$result
```

```Output
1
2
```

<span data-ttu-id="4dab2-126">Om ett skript avslutas fel uppstår under tilldelningen från en pipeline-kedja, lyckas inte tilldelningen:</span><span class="sxs-lookup"><span data-stu-id="4dab2-126">If a script-terminating error occurs during assignment from a pipeline chain, the assignment does not succeed:</span></span>

```powershell
try
{
    $result = Write-Output 'Value' && $(throw 'Bad')
}
catch
{
    # Do nothing, just squash the error
}

"Result: $result"
```

```Output
Result:
```

### <a name="operator-syntax-and-precedence"></a><span data-ttu-id="4dab2-127">Operator-syntax och prioritet</span><span class="sxs-lookup"><span data-stu-id="4dab2-127">Operator syntax and precedence</span></span>

<span data-ttu-id="4dab2-128">Till skillnad från andra operatörer `&&` och `||` drift på pipelines i stället för uttryck som `+` eller `-and` , till exempel.</span><span class="sxs-lookup"><span data-stu-id="4dab2-128">Unlike other operators, `&&` and `||` operate on pipelines, rather than on expressions like `+` or `-and`, for example.</span></span>

<span data-ttu-id="4dab2-129">`&&` och `||` har lägre prioritet än rörledning ( `|` ) eller omdirigering ( `>` ), men en högre prioritet än jobb operatörer ( `&` ), tilldelning ( `=` ) eller semikolon ( `;` ).</span><span class="sxs-lookup"><span data-stu-id="4dab2-129">`&&` and `||` have a lower precedence than piping (`|`) or redirection (`>`), but a higher precedence than job operators (`&`), assignment (`=`) or semicolons (`;`).</span></span> <span data-ttu-id="4dab2-130">Det innebär att pipeliner i en pipeline-kedja kan omdirigeras individuellt och att hela pipelinen kan vara bakgrunds, tilldelas variabler eller åtskiljas som instruktioner.</span><span class="sxs-lookup"><span data-stu-id="4dab2-130">This means that pipelines within a pipeline chain can be individually redirected, and that entire pipeline chains can be backgrounded, assigned to variables, or separated as statements.</span></span>

<span data-ttu-id="4dab2-131">Om du vill använda en syntax med lägre prioritet i en pipeline-kedja kan du överväga att använda parenteser `(...)` .</span><span class="sxs-lookup"><span data-stu-id="4dab2-131">To use lower precedence syntax within a pipeline chain, consider the use of parentheses `(...)`.</span></span>
<span data-ttu-id="4dab2-132">Om du vill bädda in en instruktion i en pipeline-kedja kan du på samma sätt använda ett under uttryck `$(...)` .</span><span class="sxs-lookup"><span data-stu-id="4dab2-132">Similarly, to embed a statement within a pipeline chain, a subexpression `$(...)` can be used.</span></span>
<span data-ttu-id="4dab2-133">Detta kan vara användbart för att kombinera inbyggda kommandon med kontroll flöde:</span><span class="sxs-lookup"><span data-stu-id="4dab2-133">This can be useful for combining native commands with control flow:</span></span>

```powershell
foreach ($file in 'file1','file2','file3')
{
    # When find succeeds, the loop breaks
    find $file && Write-Output "Found $file" && $(break)
}
```

```Output
find: file1: No such file or directory
file2
Found file2
```

<span data-ttu-id="4dab2-134">Från och med PowerShell 7 har beteendet för dessa syntax ändrats så att `$?` ställs in som förväntat när ett kommando lyckas eller Miss lyckas inom parenteser eller under uttryck.</span><span class="sxs-lookup"><span data-stu-id="4dab2-134">As of PowerShell 7, the behaviour of these syntaxes has been changed so that `$?` is set as expected when a command succeeds or fails within parentheses or a subexpression.</span></span>

<span data-ttu-id="4dab2-135">Precis som de flesta andra operatorer i PowerShell, `&&` och `||` är också *kvar att associera*, vilket innebär att de är grupperade från vänster.</span><span class="sxs-lookup"><span data-stu-id="4dab2-135">Like most other operators in PowerShell, `&&` and `||` are also *left-associative*, meaning they group from the left.</span></span> <span data-ttu-id="4dab2-136">Exempel:</span><span class="sxs-lookup"><span data-stu-id="4dab2-136">For example:</span></span>

```powershell
Get-ChildItem -Path ./file.txt || Write-Error "file.txt does not exist" && Get-Content -Raw ./file.txt
```

<span data-ttu-id="4dab2-137">kommer att grupperas som:</span><span class="sxs-lookup"><span data-stu-id="4dab2-137">will group as:</span></span>

```
[Get-ChildItem -Path ./file.txt || Write-Error "file.txt does not exist"] && Get-Content -Raw ./file.txt
```

<span data-ttu-id="4dab2-138">motsvarar:</span><span class="sxs-lookup"><span data-stu-id="4dab2-138">being equivalent to:</span></span>

```powershell
Get-ChildItem -Path ./file.txt

if (-not $?) { Write-Error "file.txt does not exist" }

if ($?) { Get-Content -Raw ./file.txt }
```

### <a name="error-interaction"></a><span data-ttu-id="4dab2-139">Fel interaktion</span><span class="sxs-lookup"><span data-stu-id="4dab2-139">Error interaction</span></span>

<span data-ttu-id="4dab2-140">Pipelines kedje operatorer absorberar inte fel.</span><span class="sxs-lookup"><span data-stu-id="4dab2-140">Pipeline chain operators do not absorb errors.</span></span> <span data-ttu-id="4dab2-141">När en instruktion i en pipeline-kedja genererar ett skript-avslutande fel, avslutas pipelin kedjan.</span><span class="sxs-lookup"><span data-stu-id="4dab2-141">When a statement in a pipeline chain throws a script-terminating error, the pipeline chain is terminated.</span></span>

<span data-ttu-id="4dab2-142">Exempel:</span><span class="sxs-lookup"><span data-stu-id="4dab2-142">For example:</span></span>

```powershell
$(throw 'Bad') || Write-Output '2'
```

```Output
Exception: Bad
```

<span data-ttu-id="4dab2-143">Även om felet fångas, avslutas pipelinen fortfarande:</span><span class="sxs-lookup"><span data-stu-id="4dab2-143">Even when the error is caught, the pipeline chain is still terminated:</span></span>

```powershell
try
{
    $(throw 'Bad') || Write-Output '2'
}
catch
{
    Write-Output "Caught: $_"
}
Write-Output 'Done'
```

```Output
Caught: Bad
Done
```

<span data-ttu-id="4dab2-144">Om ett fel inte är avslutat eller bara avslutar en pipeline, fortsätter pipelinen att uppfylla värdet för `$?` :</span><span class="sxs-lookup"><span data-stu-id="4dab2-144">If an error is non-terminating, or only terminates a pipeline, the pipeline chain continues, respecting the value of `$?`:</span></span>

```powershell
function Test-NonTerminatingError
{
    [CmdletBinding()]
    param()

    $exception = [System.Exception]::new('BAD')
    $errorId = 'BAD'
    $errorCategory = 'NotSpecified'

    $errorRecord = [System.Management.Automation.ErrorRecord]::new($exception, $errorId, $errorCategory, $null)

    $PSCmdlet.WriteError($errorRecord)
}

Test-NonTerminatingError || Write-Output 'Second'
```

```Output
Test-NonTerminatingError: BAD
Second
```

### <a name="chaining-pipelines-rather-than-commands"></a><span data-ttu-id="4dab2-145">Länka pipeliner i stället för kommandon</span><span class="sxs-lookup"><span data-stu-id="4dab2-145">Chaining pipelines rather than commands</span></span>

<span data-ttu-id="4dab2-146">Operatorer för pipeline-kedjan, efter namn, kan användas för att kedje pipelines, i stället för bara kommandon.</span><span class="sxs-lookup"><span data-stu-id="4dab2-146">Pipeline chain operators, by their name, can be used to chain pipelines, rather than just commands.</span></span> <span data-ttu-id="4dab2-147">Detta matchar beteendet för andra gränssnitt, men kan göra det *svårare att* fastställa:</span><span class="sxs-lookup"><span data-stu-id="4dab2-147">This matches the behavior of other shells, but can make *success* harder to determine:</span></span>

```powershell
function Test-NotTwo
{
    [CmdletBinding()]
    param(
      [Parameter(ValueFromPipeline)]
      $Input
    )

    process
    {
        if ($Input -ne 2)
        {
            return $Input
        }

        $exception = [System.Exception]::new('Input is 2')
        $errorId = 'InputTwo'
        $errorCategory = 'InvalidData'

        $errorRecord = [System.Management.Automation.ErrorRecord]::new($exception, $errorId, $errorCategory, $null)

        $PSCmdlet.WriteError($errorRecord)
    }
}

1,2,3 | Test-NotTwo && Write-Output 'All done!'
```

```Output
1
Test-NotTwo : Input is 2
3
```

<span data-ttu-id="4dab2-148">Observera att `Write-Output 'All done!'` inte körs eftersom det anses vara fel `Test-NotTwo` när du har genererat ett icke-avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="4dab2-148">Note that `Write-Output 'All done!'` is not executed, since `Test-NotTwo` is deemed to have failed after generating the non-terminating error.</span></span>

## <a name="see-also"></a><span data-ttu-id="4dab2-149">Se även</span><span class="sxs-lookup"><span data-stu-id="4dab2-149">See also</span></span>

- [<span data-ttu-id="4dab2-150">about_Operators</span><span class="sxs-lookup"><span data-stu-id="4dab2-150">about_Operators</span></span>](about_Operators.md)
- [<span data-ttu-id="4dab2-151">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="4dab2-151">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)
- [<span data-ttu-id="4dab2-152">about_pipelines</span><span class="sxs-lookup"><span data-stu-id="4dab2-152">about_pipelines</span></span>](about_pipelines.md)

