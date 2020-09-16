---
ms.date: 08/31/2020
title: Använda experimentella funktioner i PowerShell
description: Visar en lista över tillgängliga experimentella funktioner och hur du använder dem.
ms.openlocfilehash: f6bd17b0a3bb70d0b538dd6615b905082c87f800
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/01/2020
ms.locfileid: "89236279"
---
# <a name="using-experimental-features-in-powershell"></a><span data-ttu-id="72d4a-103">Använda experimentella funktioner i PowerShell</span><span class="sxs-lookup"><span data-stu-id="72d4a-103">Using Experimental Features in PowerShell</span></span>

<span data-ttu-id="72d4a-104">Stöd för experimentella funktioner i PowerShell är en mekanism för experimentella funktioner som kan användas tillsammans med befintliga stabila funktioner i PowerShell-eller PowerShell-moduler.</span><span class="sxs-lookup"><span data-stu-id="72d4a-104">The Experimental Features support in PowerShell provides a mechanism for experimental features to coexist with existing stable features in PowerShell or PowerShell modules.</span></span>

<span data-ttu-id="72d4a-105">En experimentell funktion är en där designen inte har slutförts.</span><span class="sxs-lookup"><span data-stu-id="72d4a-105">An experimental feature is one where the design is not finalized.</span></span> <span data-ttu-id="72d4a-106">Funktionen är tillgänglig för användare att testa och ge feedback.</span><span class="sxs-lookup"><span data-stu-id="72d4a-106">The feature is available for users to test and provide feedback.</span></span> <span data-ttu-id="72d4a-107">När en experimentell funktion har slutförts blir design ändringarna ändringar.</span><span class="sxs-lookup"><span data-stu-id="72d4a-107">Once an experimental feature is finalized, the design changes become breaking changes.</span></span>

> [!CAUTION]
> <span data-ttu-id="72d4a-108">Experimentella funktioner är inte avsedda att användas i produktion eftersom ändringarna kan avbrytas.</span><span class="sxs-lookup"><span data-stu-id="72d4a-108">Experimental features aren't intended to be used in production since the changes are allowed to be breaking.</span></span> <span data-ttu-id="72d4a-109">Experimentella funktioner stöds inte officiellt.</span><span class="sxs-lookup"><span data-stu-id="72d4a-109">Experimental features are not officially supported.</span></span> <span data-ttu-id="72d4a-110">Vi uppskattar dock alla synpunkter och fel rapporter.</span><span class="sxs-lookup"><span data-stu-id="72d4a-110">However, we appreciate any feedback and bug reports.</span></span> <span data-ttu-id="72d4a-111">Du kan fil problem i [GitHub-käll databasen](https://github.com/PowerShell/PowerShell/issues/new/choose).</span><span class="sxs-lookup"><span data-stu-id="72d4a-111">You can file issues in the [GitHub source repository](https://github.com/PowerShell/PowerShell/issues/new/choose).</span></span>

<span data-ttu-id="72d4a-112">Mer information om hur du aktiverar eller inaktiverar dessa funktioner finns [about_Experimental_Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features).</span><span class="sxs-lookup"><span data-stu-id="72d4a-112">For more information about enabling or disabling these features, see [about_Experimental_Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features).</span></span>

## <a name="available-features"></a><span data-ttu-id="72d4a-113">Tillgängliga funktioner</span><span class="sxs-lookup"><span data-stu-id="72d4a-113">Available features</span></span>

<span data-ttu-id="72d4a-114">Den här artikeln beskriver de experimentella funktioner som är tillgängliga och hur du använder funktionen.</span><span class="sxs-lookup"><span data-stu-id="72d4a-114">This article describes the experimental features that are available and how to use the feature.</span></span>

|                            <span data-ttu-id="72d4a-115">Name</span><span class="sxs-lookup"><span data-stu-id="72d4a-115">Name</span></span>                            |   <span data-ttu-id="72d4a-116">6,2</span><span class="sxs-lookup"><span data-stu-id="72d4a-116">6.2</span></span>   |   <span data-ttu-id="72d4a-117">7,0</span><span class="sxs-lookup"><span data-stu-id="72d4a-117">7.0</span></span>   | <span data-ttu-id="72d4a-118">7,1 (för hands version)</span><span class="sxs-lookup"><span data-stu-id="72d4a-118">7.1 (preview)</span></span> |
| ---------------------------------------------------------- | :-----: | :-----: | :-----------: |
| <span data-ttu-id="72d4a-119">PSTempDrive (vanlig i PS 7.0 +)</span><span class="sxs-lookup"><span data-stu-id="72d4a-119">PSTempDrive (mainstream in PS 7.0+)</span></span>                        | &check; |         |               |
| <span data-ttu-id="72d4a-120">PSUseAbbreviationExpansion (vanlig i PS 7.0 +)</span><span class="sxs-lookup"><span data-stu-id="72d4a-120">PSUseAbbreviationExpansion (mainstream in PS 7.0+)</span></span>         | &check; |         |               |
| <span data-ttu-id="72d4a-121">PSCommandNotFoundSuggestion</span><span class="sxs-lookup"><span data-stu-id="72d4a-121">PSCommandNotFoundSuggestion</span></span>                                | &check; | &check; |    &check;    |
| <span data-ttu-id="72d4a-122">PSImplicitRemotingBatching</span><span class="sxs-lookup"><span data-stu-id="72d4a-122">PSImplicitRemotingBatching</span></span>                                 | &check; | &check; |    &check;    |
| <span data-ttu-id="72d4a-123">Microsoft. PowerShell. Utility. PSManageBreakpointsInRunspace</span><span class="sxs-lookup"><span data-stu-id="72d4a-123">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span></span> |         | &check; |    &check;    |
| <span data-ttu-id="72d4a-124">PSDesiredStateConfiguration.InvokeDscResource</span><span class="sxs-lookup"><span data-stu-id="72d4a-124">PSDesiredStateConfiguration.InvokeDscResource</span></span>              |         | &check; |    &check;    |
| <span data-ttu-id="72d4a-125">PSNullConditionalOperators</span><span class="sxs-lookup"><span data-stu-id="72d4a-125">PSNullConditionalOperators</span></span>                                 |         | &check; |    &check;    |
| <span data-ttu-id="72d4a-126">PSUnixFileStat (endast Windows)</span><span class="sxs-lookup"><span data-stu-id="72d4a-126">PSUnixFileStat (non-Windows only)</span></span>                          |         | &check; |    &check;    |
| <span data-ttu-id="72d4a-127">PSNativePSPathResolution (vanlig i PS 7.1 +)</span><span class="sxs-lookup"><span data-stu-id="72d4a-127">PSNativePSPathResolution (mainstream in PS 7.1+)</span></span>           |         |         |    &check;    |
| <span data-ttu-id="72d4a-128">PSCultureInvariantReplaceOperator</span><span class="sxs-lookup"><span data-stu-id="72d4a-128">PSCultureInvariantReplaceOperator</span></span>                          |         |         |    &check;    |
| <span data-ttu-id="72d4a-129">PSNotApplyErrorActionToStderr</span><span class="sxs-lookup"><span data-stu-id="72d4a-129">PSNotApplyErrorActionToStderr</span></span>                              |         |         |    &check;    |

## <a name="microsoftpowershellutilitypsmanagebreakpointsinrunspace"></a><span data-ttu-id="72d4a-130">Microsoft. PowerShell. Utility. PSManageBreakpointsInRunspace</span><span class="sxs-lookup"><span data-stu-id="72d4a-130">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span></span>

<span data-ttu-id="72d4a-131">I PowerShell 7,0 aktiverar experimentet **BreakAll** -parametern i `Debug-Runspace` `Debug-Job` cmdletarna och gör att användarna kan välja om de vill att PowerShell ska brytas direkt på den aktuella platsen när de bifogar en fel sökare.</span><span class="sxs-lookup"><span data-stu-id="72d4a-131">In PowerShell 7.0, the experiment enables the **BreakAll** parameter on the `Debug-Runspace` and `Debug-Job` cmdlets to allow users to decide if they want PowerShell to break immediately in the current location when they attach a debugger.</span></span>

<span data-ttu-id="72d4a-132">I PowerShell 7,1 lägger detta experiment till att även lägga till parametern **körnings utrymme** i `*-PSBreakpoint` cmdletarna.</span><span class="sxs-lookup"><span data-stu-id="72d4a-132">In PowerShell 7.1, this experiment also adds the **Runspace** parameter to the `*-PSBreakpoint` cmdlets.</span></span>

- `Disable-PSBreakpoint`
- `Enable-PSBreakpoint`
- `Get-PSBreakpoint`
- `Remove-PSBreakpoint`
- `Set-PSBreakpoint`

<span data-ttu-id="72d4a-133">Parametern **körnings utrymme** anger ett **körnings utrymme** -objekt som interagerar med Bryt punkter i den angivna körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="72d4a-133">The **Runspace** parameter specifies a **Runspace** object to interact with breakpoints in the specified runspace.</span></span>

```powershell
Start-Job -ScriptBlock {
    Set-PSBreakpoint -Command Start-Sleep
    Start-Sleep -Seconds 10
}

$runspace = Get-Runspace -Id 1

$breakpoint = Get-PSBreakPoint -Runspace $runspace
```

<span data-ttu-id="72d4a-134">I det här exemplet startas ett jobb och en Bryt punkt anges som Bryt när körs `Set-PSBreakPoint` .</span><span class="sxs-lookup"><span data-stu-id="72d4a-134">In this example, a job is started and a breakpoint is set to break when the `Set-PSBreakPoint` is run.</span></span> <span data-ttu-id="72d4a-135">Körnings utrymme lagras i en variabel och skickas till `Get-PSBreakPoint` kommandot med parametern **körnings utrymme** .</span><span class="sxs-lookup"><span data-stu-id="72d4a-135">The runspace is stored in a variable and passed to the `Get-PSBreakPoint` command with the **Runspace** parameter.</span></span> <span data-ttu-id="72d4a-136">Sedan kan du kontrol lera Bryt punkten i `$breakpoint` variabeln.</span><span class="sxs-lookup"><span data-stu-id="72d4a-136">You can then inspect the breakpoint in the `$breakpoint` variable.</span></span>

## <a name="pscommandnotfoundsuggestion"></a><span data-ttu-id="72d4a-137">PSCommandNotFoundSuggestion</span><span class="sxs-lookup"><span data-stu-id="72d4a-137">PSCommandNotFoundSuggestion</span></span>

<span data-ttu-id="72d4a-138">Rekommenderar möjliga kommandon baserade på fuzzy-matchande sökning efter en **CommandNotFoundException**.</span><span class="sxs-lookup"><span data-stu-id="72d4a-138">Recommends potential commands based on fuzzy matching search after a **CommandNotFoundException**.</span></span>

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

## <a name="pscultureinvariantreplaceoperator"></a><span data-ttu-id="72d4a-139">PSCultureInvariantReplaceOperator</span><span class="sxs-lookup"><span data-stu-id="72d4a-139">PSCultureInvariantReplaceOperator</span></span>

<span data-ttu-id="72d4a-140">När den vänstra operanden i en `-replace` operator-instruktion inte är en sträng, konverteras den operanden till en sträng.</span><span class="sxs-lookup"><span data-stu-id="72d4a-140">When the left-hand operand in a `-replace` operator statement is not a string, that operand is converted to a string.</span></span>

<span data-ttu-id="72d4a-141">När den här funktionen är inaktive rad `-replace` gör operatorn en kultur känslig sträng konvertering.</span><span class="sxs-lookup"><span data-stu-id="72d4a-141">When this feature is disabled, the `-replace` operator does a culture-sensitive string conversion.</span></span>
<span data-ttu-id="72d4a-142">Om kulturen till exempel är inställt på franska (FR) `1.2` konverteras värdet till strängen `1,2` .</span><span class="sxs-lookup"><span data-stu-id="72d4a-142">For example, if your culture is set to French (fr), the value `1.2` is converted to the string `1,2`.</span></span>

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
12
PS> [cultureinfo]::CurrentCulture = 'en'
PS> 1.2 -replace ','
1.2
```

<span data-ttu-id="72d4a-143">Med funktionen aktive rad:</span><span class="sxs-lookup"><span data-stu-id="72d4a-143">With the feature enabled:</span></span>

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
1.2
```

## <a name="psdesiredstateconfigurationinvokedscresource"></a><span data-ttu-id="72d4a-144">PSDesiredStateConfiguration.InvokeDscResource</span><span class="sxs-lookup"><span data-stu-id="72d4a-144">PSDesiredStateConfiguration.InvokeDscResource</span></span>

<span data-ttu-id="72d4a-145">Möjliggör kompilering till MOF på icke-Windows-system och möjliggör användning av `Invoke-DSCResource` utan LCM.</span><span class="sxs-lookup"><span data-stu-id="72d4a-145">Enables compilation to MOF on non-Windows systems and enables the use of `Invoke-DSCResource` without an LCM.</span></span>

## <a name="psimplicitremotingbatching"></a><span data-ttu-id="72d4a-146">PSImplicitRemotingBatching</span><span class="sxs-lookup"><span data-stu-id="72d4a-146">PSImplicitRemotingBatching</span></span>

<span data-ttu-id="72d4a-147">Den här funktionen undersöker kommandot som anges i gränssnittet och om alla kommandon är implicita proxy-kommandon för fjärr kommunikation som utgör en enkel pipeline, grupperas kommandona tillsammans och anropas som en enda fjärrpipeline.</span><span class="sxs-lookup"><span data-stu-id="72d4a-147">This feature examines the command typed in the shell, and if all the commands are implicit remoting proxy commands that form a simple pipeline, then the commands are batched together and invoked as a single remote pipeline.</span></span>

<span data-ttu-id="72d4a-148">Exempel:</span><span class="sxs-lookup"><span data-stu-id="72d4a-148">Example:</span></span>

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

<span data-ttu-id="72d4a-149">Som det sågs ovan, med funktionen för batchbearbetning, är alla tre implicita proxy-kommandon för fjärr kommunikation,,,, `Get-AllProcesses` `Select-Custom` `Group-Stuff` som körs i fjärrsessionen och resultatet från pipelinen de enda data som returneras till klienten.</span><span class="sxs-lookup"><span data-stu-id="72d4a-149">As seen above, with the batching feature enabled, all three implicit remoting proxy commands, `Get-AllProcesses`, `Select-Custom`, `Group-Stuff`, run in the remote session and the result from the pipeline is the only data returned to the client.</span></span> <span data-ttu-id="72d4a-150">Detta minskar mängden data som skickas fram och tillbaka mellan klienten och fjärrsessionen och minskar också mängden objekt serialisering och avserialisering.</span><span class="sxs-lookup"><span data-stu-id="72d4a-150">This decreases the amount of data sent back and forth between client and remote session, and also reduces the amount of object serialization and de-serialization.</span></span>

## <a name="psnativepspathresolution"></a><span data-ttu-id="72d4a-151">PSNativePSPathResolution</span><span class="sxs-lookup"><span data-stu-id="72d4a-151">PSNativePSPathResolution</span></span>

<span data-ttu-id="72d4a-152">Om en PSDrive-sökväg som använder fil Systems leverantören skickas till ett ursprungligt kommando skickas den matchade fil Sök vägen till det ursprungliga kommandot.</span><span class="sxs-lookup"><span data-stu-id="72d4a-152">If a PSDrive path that uses the FileSystem provider is passed to a native command, the resolved file path is passed to the native command.</span></span> <span data-ttu-id="72d4a-153">Det innebär att ett kommando som `code temp:/test.txt` nu fungerar som förväntat.</span><span class="sxs-lookup"><span data-stu-id="72d4a-153">This means a command like `code temp:/test.txt` now works as expected.</span></span>

<span data-ttu-id="72d4a-154">I Windows, om sökvägen börjar med `~` , är det också som matchas med den fullständiga sökvägen och skickas till det inbyggda kommandot.</span><span class="sxs-lookup"><span data-stu-id="72d4a-154">Also, on Windows, if the path starts with `~`, that is resolved to the full path and passed to the native command.</span></span> <span data-ttu-id="72d4a-155">I båda fallen normaliseras sökvägen till katalog avgränsarna för det aktuella operativ systemet.</span><span class="sxs-lookup"><span data-stu-id="72d4a-155">In both cases, the path is normalized to the directory separators for the relevant operating system.</span></span>

- <span data-ttu-id="72d4a-156">Om sökvägen inte är en PSDrive eller `~` (i Windows) sker inte Sök vägs normalisering</span><span class="sxs-lookup"><span data-stu-id="72d4a-156">If the path is not a PSDrive or `~` (on Windows), then path normalization doesn't occur</span></span>
- <span data-ttu-id="72d4a-157">Om sökvägen är i enkla citat tecken matchas den inte och behandlas som literal</span><span class="sxs-lookup"><span data-stu-id="72d4a-157">If the path is in single quotes, then it's not resolved and treated as literal</span></span>

> [!NOTE]
> <span data-ttu-id="72d4a-158">Den här funktionen har flyttat från experiment fasen och är en vanlig funktion i PowerShell 7,1 och högre.</span><span class="sxs-lookup"><span data-stu-id="72d4a-158">This feature has moved out of the experimental phase and is a mainstream feature in PowerShell 7.1 and higher.</span></span>

## <a name="psnotapplyerroractiontostderr"></a><span data-ttu-id="72d4a-159">PSNotApplyErrorActionToStderr</span><span class="sxs-lookup"><span data-stu-id="72d4a-159">PSNotApplyErrorActionToStderr</span></span>

<span data-ttu-id="72d4a-160">När den här experimentella funktionen är aktive rad skrivs fel poster som omdirigeras från interna kommandon, t. ex. När du använder omdirigerings operatorer ( `2>&1` ), inte till `$Error` variabeln och Preference-variabeln `$ErrorActionPreference` påverkar inte de omdirigerade utdata.</span><span class="sxs-lookup"><span data-stu-id="72d4a-160">When this experimental feature is enabled, error records redirected from native commands, like when using redirection operators (`2>&1`), are not written to the `$Error` variable and the preference variable `$ErrorActionPreference` does not affect the redirected output.</span></span>

<span data-ttu-id="72d4a-161">Många interna kommandon skriver till `stderr` som en alternativ ström för ytterligare information.</span><span class="sxs-lookup"><span data-stu-id="72d4a-161">Many native commands write to `stderr` as an alternative stream for additional information.</span></span> <span data-ttu-id="72d4a-162">Det här beteendet kan orsaka förvirring vid fel sökning. Du kan också förlora ytterligare utdata om `$ErrorActionPreference` är inställt på ett tillstånd som stänger av utdata.</span><span class="sxs-lookup"><span data-stu-id="72d4a-162">This behavior can cause confusion when looking through errors; or the additional output information can be lost to the user if `$ErrorActionPreference` is set to a state that mutes the output.</span></span>

## <a name="psnullconditionaloperators"></a><span data-ttu-id="72d4a-163">PSNullConditionalOperators</span><span class="sxs-lookup"><span data-stu-id="72d4a-163">PSNullConditionalOperators</span></span>

<span data-ttu-id="72d4a-164">Introducerar nya operatörer för null-ansvariga för villkorlig medlem- `?.` och `?[]` .</span><span class="sxs-lookup"><span data-stu-id="72d4a-164">Introduces new operators for Null conditional member access operators - `?.` and `?[]`.</span></span> <span data-ttu-id="72d4a-165">Null-ansvariga för medlems åtkomst kan användas för skalära typer och mat ris typer.</span><span class="sxs-lookup"><span data-stu-id="72d4a-165">Null member access operators can used on scalar types and array types.</span></span> <span data-ttu-id="72d4a-166">Returnera värdet för den använda medlemmen om variabeln inte är null.</span><span class="sxs-lookup"><span data-stu-id="72d4a-166">Return the value of the accessed member if the variable is not null.</span></span> <span data-ttu-id="72d4a-167">Om värdet för variabeln är null returnerar du null.</span><span class="sxs-lookup"><span data-stu-id="72d4a-167">If the value of the variable is null, then return null.</span></span>

```powershell
$x = $null
${x}?.propname
${x?}?.propname

${x}?[0]
${x?}?[0]

${x}?.MyMethod()
```

<span data-ttu-id="72d4a-168">Egenskapen `propname` används och värdet returneras endast om `$x` inte är null.</span><span class="sxs-lookup"><span data-stu-id="72d4a-168">The property `propname` is accessed and it's value is returned only if `$x` is not null.</span></span> <span data-ttu-id="72d4a-169">På samma sätt används indexeraren endast om `$x` inte är null.</span><span class="sxs-lookup"><span data-stu-id="72d4a-169">Similarly, the indexer is used only if `$x` is not null.</span></span> <span data-ttu-id="72d4a-170">Om `$x` är null returneras null.</span><span class="sxs-lookup"><span data-stu-id="72d4a-170">If `$x` is null, then null is returned.</span></span>

<span data-ttu-id="72d4a-171">`?.` `?[]` Operatorerna och är medlemmar i operatorn och ger inte ett blank steg mellan variabel namnet och operatorn.</span><span class="sxs-lookup"><span data-stu-id="72d4a-171">The `?.` and `?[]` operators are member access operators and do not allow a space in between the variable name and the operator.</span></span>

<span data-ttu-id="72d4a-172">Eftersom PowerShell tillåter `?` som en del av variabel namnet, krävs avtvetydighet när operatorerna används utan blank steg mellan variabelns namn och operatorn.</span><span class="sxs-lookup"><span data-stu-id="72d4a-172">Since PowerShell allows `?` as part of the variable name, disambiguation is required when the operators are used without a space between the variable name and the operator.</span></span> <span data-ttu-id="72d4a-173">För att disambiguate ska variablerna använda `{}` runt variabel namnet som: `${x?}?.propertyName` eller `${y}?[0]` .</span><span class="sxs-lookup"><span data-stu-id="72d4a-173">To disambiguate, the variables must use `{}` around the variable name like: `${x?}?.propertyName` or `${y}?[0]`.</span></span>

## <a name="pstempdrive"></a><span data-ttu-id="72d4a-174">PSTempDrive</span><span class="sxs-lookup"><span data-stu-id="72d4a-174">PSTempDrive</span></span>

<span data-ttu-id="72d4a-175">Skapar den `TEMP:` PSDrive som är mappad till användarens tillfälliga katalog Sök väg.</span><span class="sxs-lookup"><span data-stu-id="72d4a-175">Creates the `TEMP:` PSDrive mapped to user's temporary directory path.</span></span>

> [!NOTE]
> <span data-ttu-id="72d4a-176">Den här funktionen har flyttat från experiment fasen och är en vanlig funktion i PowerShell 7 och högre.</span><span class="sxs-lookup"><span data-stu-id="72d4a-176">This feature has moved out of the experimental phase and is a mainstream feature in PowerShell 7 and higher.</span></span>

## <a name="psunixfilestat"></a><span data-ttu-id="72d4a-177">PSUnixFileStat</span><span class="sxs-lookup"><span data-stu-id="72d4a-177">PSUnixFileStat</span></span>

<span data-ttu-id="72d4a-178">Den här funktionen ger nya beteenden för att inkludera data från UNIX **stat** -API i utdatan från fil system leverantören för att under lätta en mer UNIX-liknande fil lista.</span><span class="sxs-lookup"><span data-stu-id="72d4a-178">This feature provides new behavior to include data from the Unix **stat** API in the output of the file system provider to facilitate a more Unix-like file listing.</span></span> <span data-ttu-id="72d4a-179">Den lägger till en ny antecknings egenskap i fil namns leverantören med namnet **UnixStat** som innehåller ett gemensamt uttryck för `stat(2)` API: et från det underliggande UNIX-typ systemet.</span><span class="sxs-lookup"><span data-stu-id="72d4a-179">It adds a new note property in the filesystem provider named **UnixStat** that includes a common expression of the `stat(2)` API from the underlying Unix type system.</span></span>

<span data-ttu-id="72d4a-180">Utdata från `Get-ChildItem` bör se ut ungefär så här:</span><span class="sxs-lookup"><span data-stu-id="72d4a-180">The output from `Get-ChildItem` should look something like this:</span></span>

```powershell
dir | select -first 4 -skip 5


    Directory: /Users/jimtru/src/github/forks/JamesWTruher/PowerShell-1

UnixMode   User      Group           LastWriteTime        Size Name
--------   ----      -----           -------------        ---- ----
drwxr-xr-x jimtru    staff        10/23/2019 13:16         416 test
drwxr-xr-x jimtru    staff         11/8/2019 10:37         896 tools
-rw-r--r-- jimtru    staff         11/8/2019 10:37      112858 build.psm1
-rw-r--r-- jimtru    staff         11/8/2019 10:37      201297 CHANGELOG.md
```

## <a name="psuseabbreviationexpansion"></a><span data-ttu-id="72d4a-181">PSUseAbbreviationExpansion</span><span class="sxs-lookup"><span data-stu-id="72d4a-181">PSUseAbbreviationExpansion</span></span>

<span data-ttu-id="72d4a-182">Den här funktionen gör det möjligt att slutföra nedtvingade cmdlets och funktioner:</span><span class="sxs-lookup"><span data-stu-id="72d4a-182">This feature enables tab-completion of abbreviated cmdlets and functions:</span></span>

<span data-ttu-id="72d4a-183">Exempel:</span><span class="sxs-lookup"><span data-stu-id="72d4a-183">For example:</span></span>

- <span data-ttu-id="72d4a-184">`i-psdf<tab>` Returnerar `Import-PowerShellDataFile` .</span><span class="sxs-lookup"><span data-stu-id="72d4a-184">`i-psdf<tab>` returns `Import-PowerShellDataFile`.</span></span>
- <span data-ttu-id="72d4a-185">`u-akvmssdr<tab>` avkastning `Undo-AzKeyVaultManagedStorageSasDefinitionRemoval`</span><span class="sxs-lookup"><span data-stu-id="72d4a-185">`u-akvmssdr<tab>` returns `Undo-AzKeyVaultManagedStorageSasDefinitionRemoval`</span></span>

<span data-ttu-id="72d4a-186">Detta fungerar bara för slut för ande av flikar (interaktiv användning), så det `i-psdf` är inte ett giltigt cmdlet-namn i ett skript.</span><span class="sxs-lookup"><span data-stu-id="72d4a-186">This only works for tab completion (interactive use), so `i-psdf` is not a valid cmdlet name in a script.</span></span>

> [!NOTE]
> <span data-ttu-id="72d4a-187">Den här funktionen har flyttat från experiment fasen och är en vanlig funktion i PowerShell 7 och högre.</span><span class="sxs-lookup"><span data-stu-id="72d4a-187">This feature has moved out of the experimental phase and is a mainstream feature in PowerShell 7 and higher.</span></span>
