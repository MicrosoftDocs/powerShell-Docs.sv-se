---
ms.date: 08/27/2018
keywords: PowerShell, cmdlet
title: Använd bekanta kommandonamn
ms.openlocfilehash: 30b33bc8739975c1a40e51c04a3ee4e426c199e7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030891"
---
# <a name="using-familiar-command-names"></a><span data-ttu-id="71e99-103">Använd bekanta kommandonamn</span><span class="sxs-lookup"><span data-stu-id="71e99-103">Using familiar command names</span></span>

<span data-ttu-id="71e99-104">PowerShell stöder alias för att referera till kommandon med alternativa namn.</span><span class="sxs-lookup"><span data-stu-id="71e99-104">PowerShell supports aliases to refer to commands by alternate names.</span></span> <span data-ttu-id="71e99-105">Med aliasering kan användare i andra gränssnitt använda vanliga kommando namn som de redan känner till för liknande åtgärder i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="71e99-105">Aliasing allows users with experience in other shells to use common command names that they already know for similar operations in PowerShell.</span></span>

<span data-ttu-id="71e99-106">Alias associerar ett nytt namn med ett annat kommando.</span><span class="sxs-lookup"><span data-stu-id="71e99-106">Aliasing associates a new name with another command.</span></span> <span data-ttu-id="71e99-107">PowerShell har till exempel en intern funktion med namnet `Clear-Host` som rensar utdatafönstret.</span><span class="sxs-lookup"><span data-stu-id="71e99-107">For example, PowerShell has an internal function named `Clear-Host` that clears the output window.</span></span> <span data-ttu-id="71e99-108">Du kan ange antingen `cls` eller `clear` alias i en kommando tolk.</span><span class="sxs-lookup"><span data-stu-id="71e99-108">You can type either the `cls` or `clear` alias at a command prompt.</span></span> <span data-ttu-id="71e99-109">PowerShell tolkar dessa alias och kör funktionen `Clear-Host`.</span><span class="sxs-lookup"><span data-stu-id="71e99-109">PowerShell interprets these aliases and runs the `Clear-Host` function.</span></span>

<span data-ttu-id="71e99-110">Den här funktionen hjälper användare att lära sig PowerShell.</span><span class="sxs-lookup"><span data-stu-id="71e99-110">This feature helps users to learn PowerShell.</span></span> <span data-ttu-id="71e99-111">Först har de flesta **cmd. exe** -och UNIX-användare en stor repertoaren av kommandon som användarna redan känner till med namn.</span><span class="sxs-lookup"><span data-stu-id="71e99-111">First, most **cmd.exe** and Unix users have a large repertoire of commands that users already know by name.</span></span> <span data-ttu-id="71e99-112">PowerShell-motsvarigheterna kanske inte genererar identiska resultat.</span><span class="sxs-lookup"><span data-stu-id="71e99-112">The PowerShell equivalents may not produce identical results.</span></span> <span data-ttu-id="71e99-113">Resultaten är dock tillräckligt nära att användarna kan arbeta utan att känna till PowerShell-kommando namnet.</span><span class="sxs-lookup"><span data-stu-id="71e99-113">However, the results are close enough that users can do work without knowing the PowerShell command name.</span></span> <span data-ttu-id="71e99-114">"Finger minne" är en annan stor källa för att lära sig ett nytt kommando gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="71e99-114">"Finger memory" is another major source of frustration when learning a new command shell.</span></span> <span data-ttu-id="71e99-115">Om du har använt **cmd. exe** för år kan du ange `cls` kommandot för att rensa skärmen.</span><span class="sxs-lookup"><span data-stu-id="71e99-115">If you have used **cmd.exe** for years, you might reflexively type the `cls` command to clear the screen.</span></span> <span data-ttu-id="71e99-116">Utan alias för `Clear-Host`får du ett fel meddelande och vet inte vad du ska göra för att rensa utdata.</span><span class="sxs-lookup"><span data-stu-id="71e99-116">Without the alias for `Clear-Host`, you receive an error message and won't know what to do to clear the output.</span></span>

<span data-ttu-id="71e99-117">I följande lista visas några av de vanliga **cmd. exe** -och UNIX-kommandon som du kan använda i PowerShell:</span><span class="sxs-lookup"><span data-stu-id="71e99-117">The following list shows a few of the common **cmd.exe** and Unix commands that you can use in PowerShell:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="71e99-118">lat</span><span class="sxs-lookup"><span data-stu-id="71e99-118">cat</span></span>|<span data-ttu-id="71e99-119">tillämpning</span><span class="sxs-lookup"><span data-stu-id="71e99-119">dir</span></span>|<span data-ttu-id="71e99-120">insättning</span><span class="sxs-lookup"><span data-stu-id="71e99-120">mount</span></span>|<span data-ttu-id="71e99-121">RM</span><span class="sxs-lookup"><span data-stu-id="71e99-121">rm</span></span>|
|<span data-ttu-id="71e99-122">cd</span><span class="sxs-lookup"><span data-stu-id="71e99-122">cd</span></span>|<span data-ttu-id="71e99-123">echo</span><span class="sxs-lookup"><span data-stu-id="71e99-123">echo</span></span>|<span data-ttu-id="71e99-124">flytta</span><span class="sxs-lookup"><span data-stu-id="71e99-124">move</span></span>|<span data-ttu-id="71e99-125">rmdir</span><span class="sxs-lookup"><span data-stu-id="71e99-125">rmdir</span></span>|
|<span data-ttu-id="71e99-126">chdir</span><span class="sxs-lookup"><span data-stu-id="71e99-126">chdir</span></span>|<span data-ttu-id="71e99-127">radera</span><span class="sxs-lookup"><span data-stu-id="71e99-127">erase</span></span>|<span data-ttu-id="71e99-128">POPD</span><span class="sxs-lookup"><span data-stu-id="71e99-128">popd</span></span>|<span data-ttu-id="71e99-129">Spar</span><span class="sxs-lookup"><span data-stu-id="71e99-129">sleep</span></span>|
|<span data-ttu-id="71e99-130">Rensa</span><span class="sxs-lookup"><span data-stu-id="71e99-130">clear</span></span>|<span data-ttu-id="71e99-131">h</span><span class="sxs-lookup"><span data-stu-id="71e99-131">h</span></span>|<span data-ttu-id="71e99-132">PS</span><span class="sxs-lookup"><span data-stu-id="71e99-132">ps</span></span>|<span data-ttu-id="71e99-133">sortera</span><span class="sxs-lookup"><span data-stu-id="71e99-133">sort</span></span>|
|<span data-ttu-id="71e99-134">CLS</span><span class="sxs-lookup"><span data-stu-id="71e99-134">cls</span></span>|<span data-ttu-id="71e99-135">Historik</span><span class="sxs-lookup"><span data-stu-id="71e99-135">history</span></span>|<span data-ttu-id="71e99-136">PUSHD</span><span class="sxs-lookup"><span data-stu-id="71e99-136">pushd</span></span>|<span data-ttu-id="71e99-137">tee</span><span class="sxs-lookup"><span data-stu-id="71e99-137">tee</span></span>|
|<span data-ttu-id="71e99-138">exemplar</span><span class="sxs-lookup"><span data-stu-id="71e99-138">copy</span></span>|<span data-ttu-id="71e99-139">döda</span><span class="sxs-lookup"><span data-stu-id="71e99-139">kill</span></span>|<span data-ttu-id="71e99-140">PWD</span><span class="sxs-lookup"><span data-stu-id="71e99-140">pwd</span></span>|<span data-ttu-id="71e99-141">typ</span><span class="sxs-lookup"><span data-stu-id="71e99-141">type</span></span>|
|<span data-ttu-id="71e99-142">Backsteg</span><span class="sxs-lookup"><span data-stu-id="71e99-142">del</span></span>|<span data-ttu-id="71e99-143">LP</span><span class="sxs-lookup"><span data-stu-id="71e99-143">lp</span></span>|<span data-ttu-id="71e99-144">R</span><span class="sxs-lookup"><span data-stu-id="71e99-144">r</span></span>|<span data-ttu-id="71e99-145">skriva</span><span class="sxs-lookup"><span data-stu-id="71e99-145">write</span></span>|
|<span data-ttu-id="71e99-146">differensområden</span><span class="sxs-lookup"><span data-stu-id="71e99-146">diff</span></span>|<span data-ttu-id="71e99-147">LS</span><span class="sxs-lookup"><span data-stu-id="71e99-147">ls</span></span>|<span data-ttu-id="71e99-148">Outlook</span><span class="sxs-lookup"><span data-stu-id="71e99-148">ren</span></span>||

<span data-ttu-id="71e99-149">`Get-Alias`-cmdleten visar det verkliga namnet på det ursprungliga PowerShell-kommandot som är associerat med ett alias.</span><span class="sxs-lookup"><span data-stu-id="71e99-149">The `Get-Alias` cmdlet shows you the real name of the native PowerShell command associated with an alias.</span></span>

```powershell
PS> Get-Alias cls
```

```Output
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Alias           cls -> Clear-Host
```

## <a name="interpreting-standard-aliases"></a><span data-ttu-id="71e99-150">Tolka Standardalias</span><span class="sxs-lookup"><span data-stu-id="71e99-150">Interpreting standard aliases</span></span>

<span data-ttu-id="71e99-151">De alias som vi beskrivit tidigare har utformats för namn-kompatibilitet med andra kommando gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="71e99-151">The aliases we described previously were designed for name-compatibility with other command shells.</span></span>
<span data-ttu-id="71e99-152">De flesta alias som är inbyggda i PowerShell är utformade för det kortfattat.</span><span class="sxs-lookup"><span data-stu-id="71e99-152">Most aliases built into PowerShell are designed for brevity.</span></span> <span data-ttu-id="71e99-153">Kortare namn är enklare att skriva, men det är svårt att läsa om du inte vet vad de refererar till.</span><span class="sxs-lookup"><span data-stu-id="71e99-153">Shorter names are easier to type, but are difficult to read if you don't know what they refer to.</span></span>

<span data-ttu-id="71e99-154">PowerShell-alias försöker kompromissa mellan klarhet och det kortfattat.</span><span class="sxs-lookup"><span data-stu-id="71e99-154">PowerShell aliases try to compromise between clarity and brevity.</span></span> <span data-ttu-id="71e99-155">PowerShell använder en standard uppsättning alias för vanliga Substantiv och verb.</span><span class="sxs-lookup"><span data-stu-id="71e99-155">PowerShell uses a standard set of aliases for common nouns and verbs.</span></span>

<span data-ttu-id="71e99-156">Exempel förkortningar:</span><span class="sxs-lookup"><span data-stu-id="71e99-156">Example abbreviations:</span></span>

| <span data-ttu-id="71e99-157">Substantiv eller verb</span><span class="sxs-lookup"><span data-stu-id="71e99-157">Noun or Verb</span></span> | <span data-ttu-id="71e99-158">Förkortning</span><span class="sxs-lookup"><span data-stu-id="71e99-158">Abbreviation</span></span> |
|--------------|--------------|
| <span data-ttu-id="71e99-159">Get</span><span class="sxs-lookup"><span data-stu-id="71e99-159">Get</span></span>          | <span data-ttu-id="71e99-160">g</span><span class="sxs-lookup"><span data-stu-id="71e99-160">g</span></span>            |
| <span data-ttu-id="71e99-161">Ange</span><span class="sxs-lookup"><span data-stu-id="71e99-161">Set</span></span>          | <span data-ttu-id="71e99-162">s</span><span class="sxs-lookup"><span data-stu-id="71e99-162">s</span></span>            |
| <span data-ttu-id="71e99-163">Artikel</span><span class="sxs-lookup"><span data-stu-id="71e99-163">Item</span></span>         | <span data-ttu-id="71e99-164">Jag</span><span class="sxs-lookup"><span data-stu-id="71e99-164">i</span></span>            |
| <span data-ttu-id="71e99-165">Position</span><span class="sxs-lookup"><span data-stu-id="71e99-165">Location</span></span>     | <span data-ttu-id="71e99-166">L</span><span class="sxs-lookup"><span data-stu-id="71e99-166">l</span></span>            |
| <span data-ttu-id="71e99-167">Kommando</span><span class="sxs-lookup"><span data-stu-id="71e99-167">Command</span></span>      | <span data-ttu-id="71e99-168">210</span><span class="sxs-lookup"><span data-stu-id="71e99-168">cm</span></span>           |
| <span data-ttu-id="71e99-169">Alias</span><span class="sxs-lookup"><span data-stu-id="71e99-169">Alias</span></span>        | <span data-ttu-id="71e99-170">Al</span><span class="sxs-lookup"><span data-stu-id="71e99-170">al</span></span>           |

<span data-ttu-id="71e99-171">Dessa alias är begripliga när du känner till stenografiska namn.</span><span class="sxs-lookup"><span data-stu-id="71e99-171">These aliases are understandable when you know the shorthand names.</span></span>

| <span data-ttu-id="71e99-172">Cmdlet-namn</span><span class="sxs-lookup"><span data-stu-id="71e99-172">Cmdlet name</span></span>    | <span data-ttu-id="71e99-173">Alias</span><span class="sxs-lookup"><span data-stu-id="71e99-173">Alias</span></span> |
|----------------|-------|
| `Get-Item`     | <span data-ttu-id="71e99-174">eter</span><span class="sxs-lookup"><span data-stu-id="71e99-174">gi</span></span>    |
| `Set-Item`     | <span data-ttu-id="71e99-175">Si</span><span class="sxs-lookup"><span data-stu-id="71e99-175">si</span></span>    |
| `Get-Location` | <span data-ttu-id="71e99-176">huvud</span><span class="sxs-lookup"><span data-stu-id="71e99-176">gl</span></span>    |
| `Set-Location` | <span data-ttu-id="71e99-177">SL</span><span class="sxs-lookup"><span data-stu-id="71e99-177">sl</span></span>    |
| `Get-Command`  | <span data-ttu-id="71e99-178">GCM</span><span class="sxs-lookup"><span data-stu-id="71e99-178">gcm</span></span>   |
| `Get-Alias`    | <span data-ttu-id="71e99-179">gal</span><span class="sxs-lookup"><span data-stu-id="71e99-179">gal</span></span>   |

<span data-ttu-id="71e99-180">När du är bekant med PowerShell-alias är det enkelt att gissa att **sal** -aliaset refererar till `Set-Alias`.</span><span class="sxs-lookup"><span data-stu-id="71e99-180">Once you're familiar with PowerShell aliasing, it's easy to guess that the **sal** alias refers to `Set-Alias`.</span></span>

## <a name="creating-new-aliases"></a><span data-ttu-id="71e99-181">Skapa nya alias</span><span class="sxs-lookup"><span data-stu-id="71e99-181">Creating new aliases</span></span>

<span data-ttu-id="71e99-182">Du kan skapa egna alias med hjälp av `Set-Alias`-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="71e99-182">You can create your own aliases using the `Set-Alias` cmdlet.</span></span> <span data-ttu-id="71e99-183">Följande uttryck skapar till exempel standard-cmdlet-alias som tidigare diskuterats:</span><span class="sxs-lookup"><span data-stu-id="71e99-183">For example, the following statements create the standard cmdlet aliases previously discussed:</span></span>

```powershell
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

<span data-ttu-id="71e99-184">Internt använder PowerShell liknande kommandon vid start, men dessa alias kan inte ändras.</span><span class="sxs-lookup"><span data-stu-id="71e99-184">Internally, PowerShell uses similar commands during startup, but these aliases are not changeable.</span></span>
<span data-ttu-id="71e99-185">Om du försöker köra ett av dessa kommandon får du ett fel som förklarar att aliaset inte kan ändras.</span><span class="sxs-lookup"><span data-stu-id="71e99-185">If you try to execute one of these commands, you get an error explaining that the alias can't be modified.</span></span> <span data-ttu-id="71e99-186">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="71e99-186">For example:</span></span>

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```
