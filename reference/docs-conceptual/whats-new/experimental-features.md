---
ms.date: 04/28/2020
title: Använda experimentella funktioner i PowerShell
description: Visar en lista över tillgängliga experimentella funktioner och hur du använder dem.
ms.openlocfilehash: e2c9f30cb1d4ec7b89596cebd1e5df27968626cc
ms.sourcegitcommit: a5e945e0889d0635b7af767d80d6a13bc5526269
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/29/2020
ms.locfileid: "82587395"
---
# <a name="using-experimental-features-in-powershell"></a><span data-ttu-id="52b21-103">Använda experimentella funktioner i PowerShell</span><span class="sxs-lookup"><span data-stu-id="52b21-103">Using Experimental Features in PowerShell</span></span>

<span data-ttu-id="52b21-104">Stöd för experimentella funktioner i PowerShell är en mekanism för experimentella funktioner som kan användas tillsammans med befintliga stabila funktioner i PowerShell-eller PowerShell-moduler.</span><span class="sxs-lookup"><span data-stu-id="52b21-104">The Experimental Features support in PowerShell provides a mechanism for experimental features to coexist with existing stable features in PowerShell or PowerShell modules.</span></span>

<span data-ttu-id="52b21-105">Den här artikeln beskriver de experimentella funktioner som är tillgängliga och hur du använder funktionen.</span><span class="sxs-lookup"><span data-stu-id="52b21-105">This article describes the experimental features that are available and how to use the feature.</span></span> <span data-ttu-id="52b21-106">Mer information om hur du aktiverar eller inaktiverar dessa funktioner finns [about_Experimental_Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features).</span><span class="sxs-lookup"><span data-stu-id="52b21-106">For more information about enabling or disabling these features, see [about_Experimental_Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features).</span></span>

## <a name="available-features"></a><span data-ttu-id="52b21-107">Tillgängliga funktioner</span><span class="sxs-lookup"><span data-stu-id="52b21-107">Available features</span></span>

<span data-ttu-id="52b21-108">I följande tabell visas en lista över de funktioner som är tillgängliga i olika versioner av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="52b21-108">The following table lists the feature that are available in various versions of PowerShell.</span></span>

|                            <span data-ttu-id="52b21-109">Name</span><span class="sxs-lookup"><span data-stu-id="52b21-109">Name</span></span>                            |   <span data-ttu-id="52b21-110">6.2</span><span class="sxs-lookup"><span data-stu-id="52b21-110">6.2</span></span>   |   <span data-ttu-id="52b21-111">7.0</span><span class="sxs-lookup"><span data-stu-id="52b21-111">7.0</span></span>   | <span data-ttu-id="52b21-112">7,1 (för hands version)</span><span class="sxs-lookup"><span data-stu-id="52b21-112">7.1 (preview)</span></span> |
| ---------------------------------------------------------- | :-----: | :-----: | :-----------: |
| <span data-ttu-id="52b21-113">PSTempDrive (vanlig i PS 7.0 +)</span><span class="sxs-lookup"><span data-stu-id="52b21-113">PSTempDrive (mainstream in PS 7.0+)</span></span>                        | &check; |         |               |
| <span data-ttu-id="52b21-114">PSUseAbbreviationExpansion (vanlig i PS 7.0 +)</span><span class="sxs-lookup"><span data-stu-id="52b21-114">PSUseAbbreviationExpansion (mainstream in PS 7.0+)</span></span>         | &check; |         |               |
| <span data-ttu-id="52b21-115">PSCommandNotFoundSuggestion</span><span class="sxs-lookup"><span data-stu-id="52b21-115">PSCommandNotFoundSuggestion</span></span>                                | &check; | &check; |    &check;    |
| <span data-ttu-id="52b21-116">PSImplicitRemotingBatching</span><span class="sxs-lookup"><span data-stu-id="52b21-116">PSImplicitRemotingBatching</span></span>                                 | &check; | &check; |    &check;    |
| <span data-ttu-id="52b21-117">Microsoft. PowerShell. Utility. PSManageBreakpointsInRunspace</span><span class="sxs-lookup"><span data-stu-id="52b21-117">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span></span> |         | &check; |    &check;    |
| <span data-ttu-id="52b21-118">PSDesiredStateConfiguration.InvokeDscResource</span><span class="sxs-lookup"><span data-stu-id="52b21-118">PSDesiredStateConfiguration.InvokeDscResource</span></span>              |         | &check; |    &check;    |
| <span data-ttu-id="52b21-119">PSNullConditionalOperators</span><span class="sxs-lookup"><span data-stu-id="52b21-119">PSNullConditionalOperators</span></span>                                 |         | &check; |    &check;    |
| <span data-ttu-id="52b21-120">PSUnixFileStat (endast Windows)</span><span class="sxs-lookup"><span data-stu-id="52b21-120">PSUnixFileStat (non-Windows only)</span></span>                          |         | &check; |    &check;    |
| <span data-ttu-id="52b21-121">PSNativePSPathResolution</span><span class="sxs-lookup"><span data-stu-id="52b21-121">PSNativePSPathResolution</span></span>                                   |         |         |    &check;    |
| <span data-ttu-id="52b21-122">PSCultureInvariantReplaceOperator</span><span class="sxs-lookup"><span data-stu-id="52b21-122">PSCultureInvariantReplaceOperator</span></span>                          |         |         |    &check;    |

## <a name="microsoftpowershellutilitypsmanagebreakpointsinrunspace"></a><span data-ttu-id="52b21-123">Microsoft. PowerShell. Utility. PSManageBreakpointsInRunspace</span><span class="sxs-lookup"><span data-stu-id="52b21-123">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span></span>

<span data-ttu-id="52b21-124">Aktiverar parametern **BreakAll** i cmdletarna `Debug-Runspace` och `Debug-Job` för att tillåta att användarna bestämmer om de vill att PowerShell ska brytas direkt på den aktuella platsen när de bifogar en fel sökare.</span><span class="sxs-lookup"><span data-stu-id="52b21-124">Enables the **BreakAll** parameter on the `Debug-Runspace` and `Debug-Job` cmdlets to allow users to decide if they want PowerShell to break immediately in the current location when they attach a debugger.</span></span>

## <a name="pscommandnotfoundsuggestion"></a><span data-ttu-id="52b21-125">PSCommandNotFoundSuggestion</span><span class="sxs-lookup"><span data-stu-id="52b21-125">PSCommandNotFoundSuggestion</span></span>

<span data-ttu-id="52b21-126">Rekommenderar möjliga kommandon baserade på fuzzy-matchande sökning efter en **CommandNotFoundException**.</span><span class="sxs-lookup"><span data-stu-id="52b21-126">Recommends potential commands based on fuzzy matching search after a **CommandNotFoundException**.</span></span>

```powershell
PS> get
```

```Output
get: The term 'get' is not recognized as the name of a cmdlet, function, script file, or operable
program. Check the spelling of the name, or if a path was included, verify that the path is correct
and try again.

Suggestion [4,General]: The most similar commands are: set, del, ft, gal, gbp, gc, gci, gcm, gdr,
gcs.
```

## <a name="pscultureinvariantreplaceoperator"></a><span data-ttu-id="52b21-127">PSCultureInvariantReplaceOperator</span><span class="sxs-lookup"><span data-stu-id="52b21-127">PSCultureInvariantReplaceOperator</span></span>

<span data-ttu-id="52b21-128">När den vänstra operanden i en `-replace` operator-instruktion inte är en sträng, konverteras den operanden till en sträng.</span><span class="sxs-lookup"><span data-stu-id="52b21-128">When the left-hand operand in a `-replace` operator statement is not a string, that operand is converted to a string.</span></span>

<span data-ttu-id="52b21-129">När den här funktionen är inaktive rad gör `-replace` operatorn en kultur känslig sträng konvertering.</span><span class="sxs-lookup"><span data-stu-id="52b21-129">When this feature is disabled, the `-replace` operator does a culture-sensitive string conversion.</span></span>
<span data-ttu-id="52b21-130">Om kulturen till exempel är inställt på franska (FR) konverteras värdet `1.2` till strängen `1,2`.</span><span class="sxs-lookup"><span data-stu-id="52b21-130">For example, if your culture is set to French (fr), the value `1.2` is converted to the string `1,2`.</span></span>

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
12
PS> [cultureinfo]::CurrentCulture = 'en'
PS> 1.2 -replace ','
1.2
```

<span data-ttu-id="52b21-131">Med funktionen aktive rad:</span><span class="sxs-lookup"><span data-stu-id="52b21-131">With the feature enabled:</span></span>

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
1.2
```

## <a name="psdesiredstateconfigurationinvokedscresource"></a><span data-ttu-id="52b21-132">PSDesiredStateConfiguration.InvokeDscResource</span><span class="sxs-lookup"><span data-stu-id="52b21-132">PSDesiredStateConfiguration.InvokeDscResource</span></span>

<span data-ttu-id="52b21-133">Möjliggör kompilering till MOF på icke-Windows-system och möjliggör användning av `Invoke-DSCResource` utan LCM.</span><span class="sxs-lookup"><span data-stu-id="52b21-133">Enables compilation to MOF on non-Windows systems and enables the use of `Invoke-DSCResource` without an LCM.</span></span>

## <a name="psimplicitremotingbatching"></a><span data-ttu-id="52b21-134">PSImplicitRemotingBatching</span><span class="sxs-lookup"><span data-stu-id="52b21-134">PSImplicitRemotingBatching</span></span>

<span data-ttu-id="52b21-135">Den här funktionen undersöker kommandot som anges i gränssnittet och om alla kommandon är implicita proxy-kommandon för fjärr kommunikation som utgör en enkel pipeline, grupperas kommandona tillsammans och anropas som en enda fjärrpipeline.</span><span class="sxs-lookup"><span data-stu-id="52b21-135">This feature examines the command typed in the shell, and if all the commands are implicit remoting proxy commands that form a simple pipeline, then the commands are batched together and invoked as a single remote pipeline.</span></span>

<span data-ttu-id="52b21-136">Exempel:</span><span class="sxs-lookup"><span data-stu-id="52b21-136">Example:</span></span>

```powershell
# Create remote session and import TestIMod module
$s = nsn -host remoteMachine
icm $s { ipmo 'C:\Users\user\Documents\WindowsPowerShell\Modules\TestIMod\TestIMod.psd1' }
Import-PSSession $s -mod testimod

$maxProcs = 1000
$filter = 'pwsh','powershell*','wmi*'

# Without batching, this pipeline takes approximately 12 seconds to run
Measure-Command { Get-AllProcesses -MaxCount $maxProcs | Select-Custom $filter | Group-Stuff $filter }
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 12
Milliseconds      : 463

# But with the batching experimental feature enabled, it takes approximately 0.20 seconds
Measure-Command { Get-AllProcesses -MaxCount $maxProcs | Select-Custom $filter | Group-Stuff $filter }
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 0
Milliseconds      : 209
```

<span data-ttu-id="52b21-137">Som det sågs ovan, med funktionen för batchbearbetning, är alla tre implicita proxy- `Get-AllProcesses`kommandon `Select-Custom`för `Group-Stuff`fjärr kommunikation,,,, som körs i fjärrsessionen och resultatet från pipelinen de enda data som returneras till klienten.</span><span class="sxs-lookup"><span data-stu-id="52b21-137">As seen above, with the batching feature enabled, all three implicit remoting proxy commands, `Get-AllProcesses`, `Select-Custom`, `Group-Stuff`, run in the remote session and the result from the pipeline is the only data returned to the client.</span></span> <span data-ttu-id="52b21-138">Detta minskar mängden data som skickas fram och tillbaka mellan klienten och fjärrsessionen och minskar också mängden objekt serialisering och avserialisering.</span><span class="sxs-lookup"><span data-stu-id="52b21-138">This decreases the amount of data sent back and forth between client and remote session, and also reduces the amount of object serialization and de-serialization.</span></span>

## <a name="psnativepspathresolution"></a><span data-ttu-id="52b21-139">PSNativePSPathResolution</span><span class="sxs-lookup"><span data-stu-id="52b21-139">PSNativePSPathResolution</span></span>

<span data-ttu-id="52b21-140">Om en PSDrive-sökväg som använder fil Systems leverantören skickas till ett ursprungligt kommando skickas den matchade fil Sök vägen till det ursprungliga kommandot.</span><span class="sxs-lookup"><span data-stu-id="52b21-140">If a PSDrive path that uses the FileSystem provider is passed to a native command, the resolved file path is passed to the native command.</span></span> <span data-ttu-id="52b21-141">Det innebär att ett kommando `code temp:/test.txt` som nu fungerar som förväntat.</span><span class="sxs-lookup"><span data-stu-id="52b21-141">This means a command like `code temp:/test.txt` now works as expected.</span></span>

<span data-ttu-id="52b21-142">I Windows, om sökvägen börjar med `~`, är det också som matchas med den fullständiga sökvägen och skickas till det inbyggda kommandot.</span><span class="sxs-lookup"><span data-stu-id="52b21-142">Also, on Windows, if the path starts with `~`, that is resolved to the full path and passed to the native command.</span></span> <span data-ttu-id="52b21-143">I båda fallen normaliseras sökvägen till katalog avgränsarna för det aktuella operativ systemet.</span><span class="sxs-lookup"><span data-stu-id="52b21-143">In both cases, the path is normalized to the directory separators for the relevant operating system.</span></span>

- <span data-ttu-id="52b21-144">Om sökvägen inte är en PSDrive eller `~` (i Windows) sker inte Sök vägs normalisering</span><span class="sxs-lookup"><span data-stu-id="52b21-144">If the path is not a PSDrive or `~` (on Windows), then path normalization doesn't occur</span></span>
- <span data-ttu-id="52b21-145">Om sökvägen är i enkla citat tecken matchas den inte och behandlas som literal</span><span class="sxs-lookup"><span data-stu-id="52b21-145">If the path is in single quotes, then it's not resolved and treated as literal</span></span>

## <a name="psnullconditionaloperators"></a><span data-ttu-id="52b21-146">PSNullConditionalOperators</span><span class="sxs-lookup"><span data-stu-id="52b21-146">PSNullConditionalOperators</span></span>

<span data-ttu-id="52b21-147">Introducerar nya operatörer för null-ansvariga för villkorlig `?.` medlem `?[]`-och.</span><span class="sxs-lookup"><span data-stu-id="52b21-147">Introduces new operators for Null conditional member access operators - `?.` and `?[]`.</span></span> <span data-ttu-id="52b21-148">Null-ansvariga för medlems åtkomst kan användas för skalära typer och mat ris typer.</span><span class="sxs-lookup"><span data-stu-id="52b21-148">Null member access operators can used on scalar types and array types.</span></span> <span data-ttu-id="52b21-149">Returnera värdet för den använda medlemmen om variabeln inte är null.</span><span class="sxs-lookup"><span data-stu-id="52b21-149">Return the value of the accessed member if the variable is not null.</span></span> <span data-ttu-id="52b21-150">Om värdet för variabeln är null returnerar du null.</span><span class="sxs-lookup"><span data-stu-id="52b21-150">If the value of the variable is null, then return null.</span></span>

```powershell
$x = $null
${x}?.propname
${x?}?.propname

${x}?[0]
${x?}?[0]

${x}?.MyMethod()
```

<span data-ttu-id="52b21-151">Egenskapen `propname` används och värdet returneras endast om `$x` inte är null.</span><span class="sxs-lookup"><span data-stu-id="52b21-151">The property `propname` is accessed and it's value is returned only if `$x` is not null.</span></span> <span data-ttu-id="52b21-152">På samma sätt används indexeraren endast om `$x` inte är null.</span><span class="sxs-lookup"><span data-stu-id="52b21-152">Similarly, the indexer is used only if `$x` is not null.</span></span> <span data-ttu-id="52b21-153">Om `$x` är null returneras null.</span><span class="sxs-lookup"><span data-stu-id="52b21-153">If `$x` is null, then null is returned.</span></span>

<span data-ttu-id="52b21-154">`?.` Operatorerna `?[]` och är medlemmar i operatorn och ger inte ett blank steg mellan variabel namnet och operatorn.</span><span class="sxs-lookup"><span data-stu-id="52b21-154">The `?.` and `?[]` operators are member access operators and do not allow a space in between the variable name and the operator.</span></span>

<span data-ttu-id="52b21-155">Eftersom PowerShell tillåter `?` som en del av variabel namnet, krävs avtvetydighet när operatorerna används utan blank steg mellan variabelns namn och operatorn.</span><span class="sxs-lookup"><span data-stu-id="52b21-155">Since PowerShell allows `?` as part of the variable name, disambiguation is required when the operators are used without a space between the variable name and the operator.</span></span> <span data-ttu-id="52b21-156">För att disambiguate ska variablerna använda `{}` runt variabel namnet som: `${x?}?.propertyName` eller. `${y}?[0]`</span><span class="sxs-lookup"><span data-stu-id="52b21-156">To disambiguate, the variables must use `{}` around the variable name like: `${x?}?.propertyName` or `${y}?[0]`.</span></span>

## <a name="pstempdrive"></a><span data-ttu-id="52b21-157">PSTempDrive</span><span class="sxs-lookup"><span data-stu-id="52b21-157">PSTempDrive</span></span>

<span data-ttu-id="52b21-158">Skapar den `TEMP:` PSDrive som är mappad till användarens tillfälliga katalog Sök väg.</span><span class="sxs-lookup"><span data-stu-id="52b21-158">Creates the `TEMP:` PSDrive mapped to user's temporary directory path.</span></span>

> [!NOTE]
> <span data-ttu-id="52b21-159">Den här funktionen har flyttat från experiment fasen och är en vanlig funktion i PowerShell 7 och högre.</span><span class="sxs-lookup"><span data-stu-id="52b21-159">This feature has moved out of the experimental phase and is a mainstream feature in PowerShell 7 and higher.</span></span>

## <a name="psunixfilestat"></a><span data-ttu-id="52b21-160">PSUnixFileStat</span><span class="sxs-lookup"><span data-stu-id="52b21-160">PSUnixFileStat</span></span>

<span data-ttu-id="52b21-161">Den här funktionen ger nya beteenden för att inkludera data från UNIX **stat** -API i utdatan från fil system leverantören för att under lätta en mer UNIX-liknande fil lista.</span><span class="sxs-lookup"><span data-stu-id="52b21-161">This feature provides new behavior to include data from the Unix **stat** API in the output of the file system provider to facilitate a more Unix-like file listing.</span></span> <span data-ttu-id="52b21-162">Den lägger till en ny antecknings egenskap i fil namns leverantören med namnet **UnixStat** som innehåller `stat(2)` ett gemensamt uttryck för API: et från det underliggande UNIX-typ systemet.</span><span class="sxs-lookup"><span data-stu-id="52b21-162">It adds a new note property in the filesystem provider named **UnixStat** that includes a common expression of the `stat(2)` API from the underlying Unix type system.</span></span>

<span data-ttu-id="52b21-163">Utdata från `Get-ChildItem` bör se ut ungefär så här:</span><span class="sxs-lookup"><span data-stu-id="52b21-163">The output from `Get-ChildItem` should look something like this:</span></span>

```powershell
PS> dir | select -first 4 -skip 5


    Directory: /Users/jimtru/src/github/forks/JamesWTruher/PowerShell-1

UnixMode   User      Group           LastWriteTime        Size Name
--------   ----      -----           -------------        ---- ----
drwxr-xr-x jimtru    staff        10/23/2019 13:16         416 test
drwxr-xr-x jimtru    staff         11/8/2019 10:37         896 tools
-rw-r--r-- jimtru    staff         11/8/2019 10:37      112858 build.psm1
-rw-r--r-- jimtru    staff         11/8/2019 10:37      201297 CHANGELOG.md
```

## <a name="psuseabbreviationexpansion"></a><span data-ttu-id="52b21-164">PSUseAbbreviationExpansion</span><span class="sxs-lookup"><span data-stu-id="52b21-164">PSUseAbbreviationExpansion</span></span>

<span data-ttu-id="52b21-165">Den här funktionen gör det möjligt att slutföra nedtvingade cmdlets och funktioner:</span><span class="sxs-lookup"><span data-stu-id="52b21-165">This feature enables tab-completion of abbreviated cmdlets and functions:</span></span>

<span data-ttu-id="52b21-166">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="52b21-166">For example:</span></span>

- <span data-ttu-id="52b21-167">`i-psdf<tab>`Returnerar `Import-PowerShellDataFile`.</span><span class="sxs-lookup"><span data-stu-id="52b21-167">`i-psdf<tab>` returns `Import-PowerShellDataFile`.</span></span>
- <span data-ttu-id="52b21-168">`u-akvmssdr<tab>`avkastning`Undo-AzKeyVaultManagedStorageSasDefinitionRemoval`</span><span class="sxs-lookup"><span data-stu-id="52b21-168">`u-akvmssdr<tab>` returns `Undo-AzKeyVaultManagedStorageSasDefinitionRemoval`</span></span>

<span data-ttu-id="52b21-169">Detta fungerar bara för slut för ande av flikar (interaktiv användning `i-psdf` ), så det är inte ett giltigt cmdlet-namn i ett skript.</span><span class="sxs-lookup"><span data-stu-id="52b21-169">This only works for tab completion (interactive use), so `i-psdf` is not a valid cmdlet name in a script.</span></span>

> [!NOTE]
> <span data-ttu-id="52b21-170">Den här funktionen har flyttat från experiment fasen och är en vanlig funktion i PowerShell 7 och högre.</span><span class="sxs-lookup"><span data-stu-id="52b21-170">This feature has moved out of the experimental phase and is a mainstream feature in PowerShell 7 and higher.</span></span>
