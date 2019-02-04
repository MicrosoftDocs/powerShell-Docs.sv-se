---
ms.date: 08/27/2018
keywords: PowerShell cmdlet
title: Använd bekanta kommandonamn
ms.assetid: 021e2424-c64e-4fa5-aa98-aa6405758d5d
ms.openlocfilehash: 3d2c681623086e061e237f08603d65150d2b1947
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688926"
---
# <a name="using-familiar-command-names"></a><span data-ttu-id="62919-103">Använd bekanta kommandonamn</span><span class="sxs-lookup"><span data-stu-id="62919-103">Using familiar command names</span></span>

<span data-ttu-id="62919-104">PowerShell stöder alias att referera till kommandon med alternativa namn.</span><span class="sxs-lookup"><span data-stu-id="62919-104">PowerShell supports aliases to refer to commands by alternate names.</span></span> <span data-ttu-id="62919-105">Alias kan användare med upplevelsen i andra gränssnitt för att använda vanliga kommandonamn som de redan känner för liknande åtgärder i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="62919-105">Aliasing allows users with experience in other shells to use common command names that they already know for similar operations in PowerShell.</span></span>

<span data-ttu-id="62919-106">Alias associerar ett nytt namn med ett annat kommando.</span><span class="sxs-lookup"><span data-stu-id="62919-106">Aliasing associates a new name with another command.</span></span> <span data-ttu-id="62919-107">Till exempel PowerShell har en intern funktion med namnet `Clear-Host` som rensar utdatafönstret.</span><span class="sxs-lookup"><span data-stu-id="62919-107">For example, PowerShell has an internal function named `Clear-Host` that clears the output window.</span></span> <span data-ttu-id="62919-108">Du kan ange antingen den `cls` eller `clear` alias i Kommandotolken.</span><span class="sxs-lookup"><span data-stu-id="62919-108">You can type either the `cls` or `clear` alias at a command prompt.</span></span> <span data-ttu-id="62919-109">PowerShell tolkar dessa alias och kör den `Clear-Host` funktion.</span><span class="sxs-lookup"><span data-stu-id="62919-109">PowerShell interprets these aliases and runs the `Clear-Host` function.</span></span>

<span data-ttu-id="62919-110">Den här funktionen hjälper användare att lära dig PowerShell.</span><span class="sxs-lookup"><span data-stu-id="62919-110">This feature helps users to learn PowerShell.</span></span> <span data-ttu-id="62919-111">Första, de flesta **cmd.exe** och Unix-användare har en stor kan representeras av kommandon som användarna redan känner till namnet.</span><span class="sxs-lookup"><span data-stu-id="62919-111">First, most **cmd.exe** and Unix users have a large repertoire of commands that users already know by name.</span></span> <span data-ttu-id="62919-112">PowerShell-motsvarigheter kanske inte ger samma resultat.</span><span class="sxs-lookup"><span data-stu-id="62919-112">The PowerShell equivalents may not produce identical results.</span></span> <span data-ttu-id="62919-113">Resultatet är dock Stäng tillräckligt som användare kan fungerar utan att känna till namnet för PowerShell-kommando.</span><span class="sxs-lookup"><span data-stu-id="62919-113">However, the results are close enough that users can do work without knowing the PowerShell command name.</span></span> <span data-ttu-id="62919-114">”Finger minne” är en annan större orsaken frustrationen när learning en ny kommandotolk.</span><span class="sxs-lookup"><span data-stu-id="62919-114">"Finger memory" is another major source of frustration when learning a new command shell.</span></span> <span data-ttu-id="62919-115">Om du har använt **cmd.exe** i flera år, kan du reflexively skriver den `cls` kommando för att rensa skärmen.</span><span class="sxs-lookup"><span data-stu-id="62919-115">If you have used **cmd.exe** for years, you might reflexively type the `cls` command to clear the screen.</span></span> <span data-ttu-id="62919-116">Utan alias för `Clear-Host`, du får ett felmeddelande och inte vet vad du gör för att ta bort utdata.</span><span class="sxs-lookup"><span data-stu-id="62919-116">Without the alias for `Clear-Host`, you receive an error message and won't know what to do to clear the output.</span></span>

<span data-ttu-id="62919-117">I följande lista visas några vanliga **cmd.exe** och Unix-kommandon som du kan använda i PowerShell:</span><span class="sxs-lookup"><span data-stu-id="62919-117">The following list shows a few of the common **cmd.exe** and Unix commands that you can use in PowerShell:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="62919-118">cat</span><span class="sxs-lookup"><span data-stu-id="62919-118">cat</span></span>|<span data-ttu-id="62919-119">dir</span><span class="sxs-lookup"><span data-stu-id="62919-119">dir</span></span>|<span data-ttu-id="62919-120">Montera</span><span class="sxs-lookup"><span data-stu-id="62919-120">mount</span></span>|<span data-ttu-id="62919-121">rm</span><span class="sxs-lookup"><span data-stu-id="62919-121">rm</span></span>|
|<span data-ttu-id="62919-122">cd</span><span class="sxs-lookup"><span data-stu-id="62919-122">cd</span></span>|<span data-ttu-id="62919-123">echo</span><span class="sxs-lookup"><span data-stu-id="62919-123">echo</span></span>|<span data-ttu-id="62919-124">Flytta</span><span class="sxs-lookup"><span data-stu-id="62919-124">move</span></span>|<span data-ttu-id="62919-125">rmdir</span><span class="sxs-lookup"><span data-stu-id="62919-125">rmdir</span></span>|
|<span data-ttu-id="62919-126">chdir</span><span class="sxs-lookup"><span data-stu-id="62919-126">chdir</span></span>|<span data-ttu-id="62919-127">Radera</span><span class="sxs-lookup"><span data-stu-id="62919-127">erase</span></span>|<span data-ttu-id="62919-128">popd</span><span class="sxs-lookup"><span data-stu-id="62919-128">popd</span></span>|<span data-ttu-id="62919-129">strömsparläge</span><span class="sxs-lookup"><span data-stu-id="62919-129">sleep</span></span>|
|<span data-ttu-id="62919-130">Rensa</span><span class="sxs-lookup"><span data-stu-id="62919-130">clear</span></span>|<span data-ttu-id="62919-131">h</span><span class="sxs-lookup"><span data-stu-id="62919-131">h</span></span>|<span data-ttu-id="62919-132">ps</span><span class="sxs-lookup"><span data-stu-id="62919-132">ps</span></span>|<span data-ttu-id="62919-133">Sortera</span><span class="sxs-lookup"><span data-stu-id="62919-133">sort</span></span>|
|<span data-ttu-id="62919-134">CLS</span><span class="sxs-lookup"><span data-stu-id="62919-134">cls</span></span>|<span data-ttu-id="62919-135">Historik</span><span class="sxs-lookup"><span data-stu-id="62919-135">history</span></span>|<span data-ttu-id="62919-136">pushd</span><span class="sxs-lookup"><span data-stu-id="62919-136">pushd</span></span>|<span data-ttu-id="62919-137">Tee</span><span class="sxs-lookup"><span data-stu-id="62919-137">tee</span></span>|
|<span data-ttu-id="62919-138">Kopiera</span><span class="sxs-lookup"><span data-stu-id="62919-138">copy</span></span>|<span data-ttu-id="62919-139">Avsluta</span><span class="sxs-lookup"><span data-stu-id="62919-139">kill</span></span>|<span data-ttu-id="62919-140">pwd</span><span class="sxs-lookup"><span data-stu-id="62919-140">pwd</span></span>|<span data-ttu-id="62919-141">typ</span><span class="sxs-lookup"><span data-stu-id="62919-141">type</span></span>|
|<span data-ttu-id="62919-142">del</span><span class="sxs-lookup"><span data-stu-id="62919-142">del</span></span>|<span data-ttu-id="62919-143">LP</span><span class="sxs-lookup"><span data-stu-id="62919-143">lp</span></span>|<span data-ttu-id="62919-144">r</span><span class="sxs-lookup"><span data-stu-id="62919-144">r</span></span>|<span data-ttu-id="62919-145">skriva</span><span class="sxs-lookup"><span data-stu-id="62919-145">write</span></span>|
|<span data-ttu-id="62919-146">diff</span><span class="sxs-lookup"><span data-stu-id="62919-146">diff</span></span>|<span data-ttu-id="62919-147">ls</span><span class="sxs-lookup"><span data-stu-id="62919-147">ls</span></span>|<span data-ttu-id="62919-148">ren</span><span class="sxs-lookup"><span data-stu-id="62919-148">ren</span></span>||

<span data-ttu-id="62919-149">Den `Get-Alias` cmdlet visar det verkliga namnet på den interna PowerShell-kommando som är associerade med ett alias.</span><span class="sxs-lookup"><span data-stu-id="62919-149">The `Get-Alias` cmdlet shows you the real name of the native PowerShell command associated with an alias.</span></span>

```powershell
PS> Get-Alias cls
```

```Output
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Alias           cls -> Clear-Host
```

## <a name="interpreting-standard-aliases"></a><span data-ttu-id="62919-150">Tolka standard alias</span><span class="sxs-lookup"><span data-stu-id="62919-150">Interpreting standard aliases</span></span>

<span data-ttu-id="62919-151">Alias vi beskrivits utformades för namn-kompatibilitet med andra kommandogränssnitt.</span><span class="sxs-lookup"><span data-stu-id="62919-151">The aliases we described previously were designed for name-compatibility with other command shells.</span></span>
<span data-ttu-id="62919-152">De flesta alias som är inbyggda i PowerShell är utformade för kortfattat.</span><span class="sxs-lookup"><span data-stu-id="62919-152">Most aliases built into PowerShell are designed for brevity.</span></span> <span data-ttu-id="62919-153">Kortare namn är lättare att typ, men är svåra att läsa om du inte vet vad de refererar till.</span><span class="sxs-lookup"><span data-stu-id="62919-153">Shorter names are easier to type, but are difficult to read if you don't know what they refer to.</span></span>

<span data-ttu-id="62919-154">PowerShell-alias försöker angripa mellan tydlighet och kortfattat.</span><span class="sxs-lookup"><span data-stu-id="62919-154">PowerShell aliases try to compromise between clarity and brevity.</span></span> <span data-ttu-id="62919-155">PowerShell använder en standarduppsättning med alias för vanliga substantiv och verb.</span><span class="sxs-lookup"><span data-stu-id="62919-155">PowerShell uses a standard set of aliases for common nouns and verbs.</span></span>

<span data-ttu-id="62919-156">Exempel förkortningar:</span><span class="sxs-lookup"><span data-stu-id="62919-156">Example abbreviations:</span></span>

| <span data-ttu-id="62919-157">Substantiv eller Verb</span><span class="sxs-lookup"><span data-stu-id="62919-157">Noun or Verb</span></span> | <span data-ttu-id="62919-158">Förkortning</span><span class="sxs-lookup"><span data-stu-id="62919-158">Abbreviation</span></span> |
|--------------|--------------|
| <span data-ttu-id="62919-159">Get</span><span class="sxs-lookup"><span data-stu-id="62919-159">Get</span></span>          | <span data-ttu-id="62919-160">g</span><span class="sxs-lookup"><span data-stu-id="62919-160">g</span></span>            |
| <span data-ttu-id="62919-161">Ange</span><span class="sxs-lookup"><span data-stu-id="62919-161">Set</span></span>          | <span data-ttu-id="62919-162">s</span><span class="sxs-lookup"><span data-stu-id="62919-162">s</span></span>            |
| <span data-ttu-id="62919-163">Artikel</span><span class="sxs-lookup"><span data-stu-id="62919-163">Item</span></span>         | <span data-ttu-id="62919-164">i</span><span class="sxs-lookup"><span data-stu-id="62919-164">i</span></span>            |
| <span data-ttu-id="62919-165">Position</span><span class="sxs-lookup"><span data-stu-id="62919-165">Location</span></span>     | <span data-ttu-id="62919-166">l</span><span class="sxs-lookup"><span data-stu-id="62919-166">l</span></span>            |
| <span data-ttu-id="62919-167">Kommando</span><span class="sxs-lookup"><span data-stu-id="62919-167">Command</span></span>      | <span data-ttu-id="62919-168">cm</span><span class="sxs-lookup"><span data-stu-id="62919-168">cm</span></span>           |
| <span data-ttu-id="62919-169">Alias</span><span class="sxs-lookup"><span data-stu-id="62919-169">Alias</span></span>        | <span data-ttu-id="62919-170">AL</span><span class="sxs-lookup"><span data-stu-id="62919-170">al</span></span>           |

<span data-ttu-id="62919-171">Dessa alias är att förstå när du vet vilka snabbformat.</span><span class="sxs-lookup"><span data-stu-id="62919-171">These aliases are understandable when you know the shorthand names.</span></span>

| <span data-ttu-id="62919-172">Cmdlet-namn</span><span class="sxs-lookup"><span data-stu-id="62919-172">Cmdlet name</span></span>    | <span data-ttu-id="62919-173">Alias</span><span class="sxs-lookup"><span data-stu-id="62919-173">Alias</span></span> |
|----------------|-------|
| `Get-Item `    | <span data-ttu-id="62919-174">gi</span><span class="sxs-lookup"><span data-stu-id="62919-174">gi</span></span>    |
| `Set-Item`     | <span data-ttu-id="62919-175">si</span><span class="sxs-lookup"><span data-stu-id="62919-175">si</span></span>    |
| `Get-Location` | <span data-ttu-id="62919-176">gl</span><span class="sxs-lookup"><span data-stu-id="62919-176">gl</span></span>    |
| `Set-Location` | <span data-ttu-id="62919-177">sl</span><span class="sxs-lookup"><span data-stu-id="62919-177">sl</span></span>    |
| `Get-Command`  | <span data-ttu-id="62919-178">gcm</span><span class="sxs-lookup"><span data-stu-id="62919-178">gcm</span></span>   |
| `Get-Alias`    | <span data-ttu-id="62919-179">GAL</span><span class="sxs-lookup"><span data-stu-id="62919-179">gal</span></span>   |

<span data-ttu-id="62919-180">När du är bekant med PowerShell-alias är det enkelt att gissa som den **sal** alias refererar till `Set-Alias`.</span><span class="sxs-lookup"><span data-stu-id="62919-180">Once you're familiar with PowerShell aliasing, it's easy to guess that the **sal** alias refers to `Set-Alias`.</span></span>

## <a name="creating-new-aliases"></a><span data-ttu-id="62919-181">Skapa nytt alias</span><span class="sxs-lookup"><span data-stu-id="62919-181">Creating new aliases</span></span>

<span data-ttu-id="62919-182">Du kan skapa egna alias med hjälp av den `Set-Alias` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="62919-182">You can create your own aliases using the `Set-Alias` cmdlet.</span></span> <span data-ttu-id="62919-183">Till exempel skapa följande instruktioner standard cmdlet-alias som beskrivits tidigare:</span><span class="sxs-lookup"><span data-stu-id="62919-183">For example, the following statements create the standard cmdlet aliases previously discussed:</span></span>

```powershell
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

<span data-ttu-id="62919-184">Internt PowerShell använder liknande kommandon under starten, men dessa alias är inte kan ändras.</span><span class="sxs-lookup"><span data-stu-id="62919-184">Internally, PowerShell uses similar commands during startup, but these aliases are not changeable.</span></span>
<span data-ttu-id="62919-185">Om du försöker köra något av följande kommandon, får du ett felmeddelande om att aliaset som inte kan ändras.</span><span class="sxs-lookup"><span data-stu-id="62919-185">If you try to execute one of these commands, you get an error explaining that the alias can't be modified.</span></span> <span data-ttu-id="62919-186">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="62919-186">For example:</span></span>

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```
