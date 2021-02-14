---
ms.date: 12/14/2020
title: Använda experimentella funktioner i PowerShell
description: Visar en lista över tillgängliga experimentella funktioner och hur du använder dem.
ms.openlocfilehash: 556ae8d877b670b119b7b5b958a52488aad16241
ms.sourcegitcommit: 77f6225ab0c8ea9faa1fe46b2ea15c178ec170e3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100500131"
---
# <a name="using-experimental-features-in-powershell"></a><span data-ttu-id="f5b34-103">Använda experimentella funktioner i PowerShell</span><span class="sxs-lookup"><span data-stu-id="f5b34-103">Using Experimental Features in PowerShell</span></span>

<span data-ttu-id="f5b34-104">Stöd för experimentella funktioner i PowerShell är en mekanism för experimentella funktioner som kan användas tillsammans med befintliga stabila funktioner i PowerShell-eller PowerShell-moduler.</span><span class="sxs-lookup"><span data-stu-id="f5b34-104">The Experimental Features support in PowerShell provides a mechanism for experimental features to coexist with existing stable features in PowerShell or PowerShell modules.</span></span>

<span data-ttu-id="f5b34-105">En experimentell funktion är en där designen inte har slutförts.</span><span class="sxs-lookup"><span data-stu-id="f5b34-105">An experimental feature is one where the design is not finalized.</span></span> <span data-ttu-id="f5b34-106">Funktionen är tillgänglig för användare att testa och ge feedback.</span><span class="sxs-lookup"><span data-stu-id="f5b34-106">The feature is available for users to test and provide feedback.</span></span> <span data-ttu-id="f5b34-107">När en experimentell funktion har slutförts blir design ändringarna ändringar.</span><span class="sxs-lookup"><span data-stu-id="f5b34-107">Once an experimental feature is finalized, the design changes become breaking changes.</span></span>

> [!CAUTION]
> <span data-ttu-id="f5b34-108">Experimentella funktioner är inte avsedda att användas i produktion eftersom ändringarna kan avbrytas.</span><span class="sxs-lookup"><span data-stu-id="f5b34-108">Experimental features aren't intended to be used in production since the changes are allowed to be breaking.</span></span> <span data-ttu-id="f5b34-109">Experimentella funktioner stöds inte officiellt.</span><span class="sxs-lookup"><span data-stu-id="f5b34-109">Experimental features are not officially supported.</span></span> <span data-ttu-id="f5b34-110">Vi uppskattar dock alla synpunkter och fel rapporter.</span><span class="sxs-lookup"><span data-stu-id="f5b34-110">However, we appreciate any feedback and bug reports.</span></span> <span data-ttu-id="f5b34-111">Du kan fil problem i [GitHub-käll databasen](https://github.com/PowerShell/PowerShell/issues/new/choose).</span><span class="sxs-lookup"><span data-stu-id="f5b34-111">You can file issues in the [GitHub source repository](https://github.com/PowerShell/PowerShell/issues/new/choose).</span></span>

<span data-ttu-id="f5b34-112">Mer information om hur du aktiverar eller inaktiverar dessa funktioner finns [about_Experimental_Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features).</span><span class="sxs-lookup"><span data-stu-id="f5b34-112">For more information about enabling or disabling these features, see [about_Experimental_Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features).</span></span>

## <a name="available-features"></a><span data-ttu-id="f5b34-113">Tillgängliga funktioner</span><span class="sxs-lookup"><span data-stu-id="f5b34-113">Available features</span></span>

<span data-ttu-id="f5b34-114">Den här artikeln beskriver de experimentella funktioner som är tillgängliga och hur du använder funktionen.</span><span class="sxs-lookup"><span data-stu-id="f5b34-114">This article describes the experimental features that are available and how to use the feature.</span></span>

|                            <span data-ttu-id="f5b34-115">Namn</span><span class="sxs-lookup"><span data-stu-id="f5b34-115">Name</span></span>                            |   <span data-ttu-id="f5b34-116">6,2</span><span class="sxs-lookup"><span data-stu-id="f5b34-116">6.2</span></span>   |   <span data-ttu-id="f5b34-117">7.0</span><span class="sxs-lookup"><span data-stu-id="f5b34-117">7.0</span></span>   |   <span data-ttu-id="f5b34-118">7.1</span><span class="sxs-lookup"><span data-stu-id="f5b34-118">7.1</span></span>   |   <span data-ttu-id="f5b34-119">7.2</span><span class="sxs-lookup"><span data-stu-id="f5b34-119">7.2</span></span>   |
| ---------------------------------------------------------- | :-----: | :-----: | :-----: | :-----: |
| <span data-ttu-id="f5b34-120">PSTempDrive (vanlig i PS 7.0 +)</span><span class="sxs-lookup"><span data-stu-id="f5b34-120">PSTempDrive (mainstream in PS 7.0+)</span></span>                        | &check; |         |         |         |
| <span data-ttu-id="f5b34-121">PSUseAbbreviationExpansion (vanlig i PS 7.0 +)</span><span class="sxs-lookup"><span data-stu-id="f5b34-121">PSUseAbbreviationExpansion (mainstream in PS 7.0+)</span></span>         | &check; |         |         |         |
| <span data-ttu-id="f5b34-122">PSNullConditionalOperators (vanlig i PS 7.1 +)</span><span class="sxs-lookup"><span data-stu-id="f5b34-122">PSNullConditionalOperators (mainstream in PS 7.1+)</span></span>         |         | &check; |         |         |
| <span data-ttu-id="f5b34-123">PSUnixFileStat (endast Windows-konventionellt i PS 7.1 +)</span><span class="sxs-lookup"><span data-stu-id="f5b34-123">PSUnixFileStat (non-Windows only - mainstream in PS 7.1+)</span></span>  |         | &check; |         |         |
| <span data-ttu-id="f5b34-124">PSCommandNotFoundSuggestion</span><span class="sxs-lookup"><span data-stu-id="f5b34-124">PSCommandNotFoundSuggestion</span></span>                                | &check; | &check; | &check; | &check; |
| <span data-ttu-id="f5b34-125">PSImplicitRemotingBatching</span><span class="sxs-lookup"><span data-stu-id="f5b34-125">PSImplicitRemotingBatching</span></span>                                 | &check; | &check; | &check; | &check; |
| <span data-ttu-id="f5b34-126">Microsoft. PowerShell. Utility. PSManageBreakpointsInRunspace</span><span class="sxs-lookup"><span data-stu-id="f5b34-126">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span></span> |         | &check; | &check; | &check; |
| <span data-ttu-id="f5b34-127">PSDesiredStateConfiguration.InvokeDscResource</span><span class="sxs-lookup"><span data-stu-id="f5b34-127">PSDesiredStateConfiguration.InvokeDscResource</span></span>              |         | &check; | &check; | &check; |
| <span data-ttu-id="f5b34-128">PSNativePSPathResolution</span><span class="sxs-lookup"><span data-stu-id="f5b34-128">PSNativePSPathResolution</span></span>                                   |         |         | &check; | &check; |
| <span data-ttu-id="f5b34-129">PSCultureInvariantReplaceOperator</span><span class="sxs-lookup"><span data-stu-id="f5b34-129">PSCultureInvariantReplaceOperator</span></span>                          |         |         | &check; | &check; |
| <span data-ttu-id="f5b34-130">PSNotApplyErrorActionToStderr</span><span class="sxs-lookup"><span data-stu-id="f5b34-130">PSNotApplyErrorActionToStderr</span></span>                              |         |         | &check; | &check; |
| <span data-ttu-id="f5b34-131">PSSubsystemPluginModel</span><span class="sxs-lookup"><span data-stu-id="f5b34-131">PSSubsystemPluginModel</span></span>                                     |         |         | &check; | &check; |
| <span data-ttu-id="f5b34-132">PSAnsiProgress</span><span class="sxs-lookup"><span data-stu-id="f5b34-132">PSAnsiProgress</span></span>                                             |         |         |         | &check; |
| <span data-ttu-id="f5b34-133">PSAnsiRendering</span><span class="sxs-lookup"><span data-stu-id="f5b34-133">PSAnsiRendering</span></span>                                            |         |         |         | &check; |

## <a name="microsoftpowershellutilitypsmanagebreakpointsinrunspace"></a><span data-ttu-id="f5b34-134">Microsoft. PowerShell. Utility. PSManageBreakpointsInRunspace</span><span class="sxs-lookup"><span data-stu-id="f5b34-134">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span></span>

<span data-ttu-id="f5b34-135">I PowerShell 7,0 aktiverar experimentet **BreakAll** -parametern i `Debug-Runspace` `Debug-Job` cmdletarna och gör att användarna kan välja om de vill att PowerShell ska brytas direkt på den aktuella platsen när de bifogar en fel sökare.</span><span class="sxs-lookup"><span data-stu-id="f5b34-135">In PowerShell 7.0, the experiment enables the **BreakAll** parameter on the `Debug-Runspace` and `Debug-Job` cmdlets to allow users to decide if they want PowerShell to break immediately in the current location when they attach a debugger.</span></span>

<span data-ttu-id="f5b34-136">I PowerShell 7,1 lägger detta experiment till att även lägga till parametern **körnings utrymme** i `*-PSBreakpoint` cmdletarna.</span><span class="sxs-lookup"><span data-stu-id="f5b34-136">In PowerShell 7.1, this experiment also adds the **Runspace** parameter to the `*-PSBreakpoint` cmdlets.</span></span>

- `Disable-PSBreakpoint`
- `Enable-PSBreakpoint`
- `Get-PSBreakpoint`
- `Remove-PSBreakpoint`
- `Set-PSBreakpoint`

<span data-ttu-id="f5b34-137">Parametern **körnings utrymme** anger ett **körnings utrymme** -objekt som interagerar med Bryt punkter i den angivna körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="f5b34-137">The **Runspace** parameter specifies a **Runspace** object to interact with breakpoints in the specified runspace.</span></span>

```powershell
Start-Job -ScriptBlock {
    Set-PSBreakpoint -Command Start-Sleep
    Start-Sleep -Seconds 10
}

$runspace = Get-Runspace -Id 1

$breakpoint = Get-PSBreakPoint -Runspace $runspace
```

<span data-ttu-id="f5b34-138">I det här exemplet startas ett jobb och en Bryt punkt anges som Bryt när körs `Set-PSBreakPoint` .</span><span class="sxs-lookup"><span data-stu-id="f5b34-138">In this example, a job is started and a breakpoint is set to break when the `Set-PSBreakPoint` is run.</span></span> <span data-ttu-id="f5b34-139">Körnings utrymme lagras i en variabel och skickas till `Get-PSBreakPoint` kommandot med parametern **körnings utrymme** .</span><span class="sxs-lookup"><span data-stu-id="f5b34-139">The runspace is stored in a variable and passed to the `Get-PSBreakPoint` command with the **Runspace** parameter.</span></span> <span data-ttu-id="f5b34-140">Sedan kan du kontrol lera Bryt punkten i `$breakpoint` variabeln.</span><span class="sxs-lookup"><span data-stu-id="f5b34-140">You can then inspect the breakpoint in the `$breakpoint` variable.</span></span>

## <a name="psansirendering"></a><span data-ttu-id="f5b34-141">PSAnsiRendering</span><span class="sxs-lookup"><span data-stu-id="f5b34-141">PSAnsiRendering</span></span>

<span data-ttu-id="f5b34-142">Det här experimentet lades till i PowerShell 7,2.</span><span class="sxs-lookup"><span data-stu-id="f5b34-142">This experiment was added in PowerShell 7.2.</span></span> <span data-ttu-id="f5b34-143">Funktionen gör det möjligt att ändra hur PowerShell-motorn matar ut text och lägger till den `$PSStyle` automatiska variabeln för att styra ANSI-åter givning av sträng utdata.</span><span class="sxs-lookup"><span data-stu-id="f5b34-143">The feature enables changes how the PowerShell engine outputs text and add the `$PSStyle` automatic variable to control ANSI rendering of string output.</span></span>

```powershell
PS> $PSStyle

Name            MemberType Definition
----            ---------- ----------
Reset           Property   string AttributesOff {get;set;}
Background      Property   System.Management.Automation.PSStyle+BackgroundColor Background {get;set;}
Blink           Property   string Blink {get;set;}
BlinkOff        Property   string BlinkOff {get;set;}
Bold            Property   string Bold {get;set;}
BoldOff         Property   string BoldOff {get;set;}
Foreground      Property   System.Management.Automation.PSStyle+ForegroundColor Foreground {get;set;}
Formatting      Property   System.Management.Automation.PSStyle+FormattingData Formatting {get;set;}
Hidden          Property   string Hidden {get;set;}
HiddenOff       Property   string HiddenOff {get;set;}
OutputRendering Property   System.Management.Automation.OutputRendering OutputRendering {get;set;}
Reverse         Property   string Reverse {get;set;}
ReverseOff      Property   string ReverseOff {get;set;}
Italic          Property   string Standout {get;set;}
ItalicOff       Property   string StandoutOff {get;set;}
Underline       Property   string Underlined {get;set;}
Underline Off   Property   string UnderlinedOff {get;set;}
```

<span data-ttu-id="f5b34-144">Bas medlemmarna returnerar strängar av ANSI escape-sekvenser som är mappade till deras namn.</span><span class="sxs-lookup"><span data-stu-id="f5b34-144">The base members return strings of ANSI escape sequences mapped to their names.</span></span> <span data-ttu-id="f5b34-145">Värdena kan anges för att tillåta anpassning.</span><span class="sxs-lookup"><span data-stu-id="f5b34-145">The values are settable to allow customization.</span></span>

<span data-ttu-id="f5b34-146">Mer information finns i [about_Automatic_Variables](/reference/7.2/Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)</span><span class="sxs-lookup"><span data-stu-id="f5b34-146">For more information, see [about_Automatic_Variables](/reference/7.2/Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)</span></span>

> [!NOTE]
> <span data-ttu-id="f5b34-147">För C#-utvecklare kan du komma åt `PSStyle` som en singleton.</span><span class="sxs-lookup"><span data-stu-id="f5b34-147">For C# developers, you can access `PSStyle` as a singleton.</span></span> <span data-ttu-id="f5b34-148">Användningen kommer att se ut så här:</span><span class="sxs-lookup"><span data-stu-id="f5b34-148">Usage will look like this:</span></span>
>
> ```csharp
> string output = $"{PSStyle.Instance.Foreground.Red}{PSStyle.Instance.Bold}Hello{PSStyle.Instance.Reset}";
> ```
>
> <span data-ttu-id="f5b34-149">`PSStyle` finns i namn området system. Management. Automation.</span><span class="sxs-lookup"><span data-stu-id="f5b34-149">`PSStyle` exists in the System.Management.Automation namespace.</span></span>

<span data-ttu-id="f5b34-150">Tillsammans med åtkomst till `$PSStyle` , introducerar detta ändringar i PowerShell-motorn.</span><span class="sxs-lookup"><span data-stu-id="f5b34-150">Along with access to `$PSStyle`, this introduces changes to the PowerShell engine.</span></span> <span data-ttu-id="f5b34-151">PowerShell-formatsystemet uppdateras för att respektera `$PSStyle.OutputRendering` .</span><span class="sxs-lookup"><span data-stu-id="f5b34-151">The PowerShell formatting system is updated to respect `$PSStyle.OutputRendering`.</span></span>

- <span data-ttu-id="f5b34-152">`StringDecorated` typen läggs till för att hantera ANSI-undantagna strängar.</span><span class="sxs-lookup"><span data-stu-id="f5b34-152">`StringDecorated` type is added to handle ANSI escaped strings.</span></span>
- <span data-ttu-id="f5b34-153">`string IsDecorated` boolesk egenskap läggs till för att returnera om strängen innehåller ANSI escape-sekvenser baserat på om strängen innehåller ESC eller C1 CSI.</span><span class="sxs-lookup"><span data-stu-id="f5b34-153">`string IsDecorated` boolean property is added to return if the string contains ANSI escape sequences based on if the string contains ESC or C1 CSI.</span></span>
- <span data-ttu-id="f5b34-154">`Length`Egenskapen returnerar _bara_ längden för texten utan ANSI escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="f5b34-154">The `Length` property returns _only_ the length for the text without the ANSI escape sequences.</span></span>
- <span data-ttu-id="f5b34-155">`StringDecorated Substring(int contentLength)` Metoden returnerar en under sträng som börjar vid indexet 0 upp till innehålls längden som inte är en del av ANSI escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="f5b34-155">`StringDecorated Substring(int contentLength)` method returns a substring starting at index 0 up to the content length that is not a part of ANSI escape sequences.</span></span> <span data-ttu-id="f5b34-156">Detta krävs för tabellformatering för att trunkera strängar och bevara ANSI escape-sekvenser som inte tar upp ett utskrivbart tecken utrymme.</span><span class="sxs-lookup"><span data-stu-id="f5b34-156">This is needed for table formatting to truncate strings and preserve ANSI escape sequences that don't take up printable character space.</span></span>
- <span data-ttu-id="f5b34-157">`string ToString()` metoden förblir densamma och returnerar strängens klartext-version.</span><span class="sxs-lookup"><span data-stu-id="f5b34-157">`string ToString()` method stays the same and returns the plaintext version of the string.</span></span>
- <span data-ttu-id="f5b34-158">`string ToString(bool Ansi)` Metoden returnerar rå ANSI Embedded-sträng om `Ansi` parametern är true.</span><span class="sxs-lookup"><span data-stu-id="f5b34-158">`string ToString(bool Ansi)` method returns the raw ANSI embedded string if the `Ansi` parameter is true.</span></span> <span data-ttu-id="f5b34-159">Annars returneras en klar text version med ANSI escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="f5b34-159">Otherwise, a plaintext version with ANSI escape sequences removed is returned.</span></span>

## <a name="psansiprogress"></a><span data-ttu-id="f5b34-160">PSAnsiProgress</span><span class="sxs-lookup"><span data-stu-id="f5b34-160">PSAnsiProgress</span></span>

<span data-ttu-id="f5b34-161">Det här experimentet lades till i PowerShell 7,2.</span><span class="sxs-lookup"><span data-stu-id="f5b34-161">This experiment was added in PowerShell 7.2.</span></span> <span data-ttu-id="f5b34-162">Funktionen lägger till `$PSStyle.Progress` medlemmen och gör att du kan kontrol lera visningen av förlopps visaren.</span><span class="sxs-lookup"><span data-stu-id="f5b34-162">The feature adds the `$PSStyle.Progress` member and allows you to control progress view bar rendering.</span></span>

- <span data-ttu-id="f5b34-163">`$PSStyle.Progress.Style` – En ANSI-sträng anger åter givnings formatet.</span><span class="sxs-lookup"><span data-stu-id="f5b34-163">`$PSStyle.Progress.Style` - An ANSI string setting the rendering style.</span></span>
- <span data-ttu-id="f5b34-164">`$PSStyle.Progress.MaxWidth` -Anger Max bredden för vyn.</span><span class="sxs-lookup"><span data-stu-id="f5b34-164">`$PSStyle.Progress.MaxWidth` - Sets the max width of the view.</span></span> <span data-ttu-id="f5b34-165">Ange som `0` konsol bredd.</span><span class="sxs-lookup"><span data-stu-id="f5b34-165">Set to `0` for console width.</span></span>
  <span data-ttu-id="f5b34-166">Standardvärdet `120`</span><span class="sxs-lookup"><span data-stu-id="f5b34-166">Defaults to `120`</span></span>
- <span data-ttu-id="f5b34-167">`$PSStyle.Progress.View` – En Enum med värden `Minimal` och `Classic` .</span><span class="sxs-lookup"><span data-stu-id="f5b34-167">`$PSStyle.Progress.View` - An enum with values, `Minimal` and `Classic`.</span></span> <span data-ttu-id="f5b34-168">`Classic` är den befintliga renderingen utan ändringar.</span><span class="sxs-lookup"><span data-stu-id="f5b34-168">`Classic` is the existing rendering with no changes.</span></span> <span data-ttu-id="f5b34-169">`Minimal` är en enskild linje som är minimal åter givning.</span><span class="sxs-lookup"><span data-stu-id="f5b34-169">`Minimal` is a single line minimal rendering.</span></span> <span data-ttu-id="f5b34-170">`Minimal` används som standard.</span><span class="sxs-lookup"><span data-stu-id="f5b34-170">`Minimal` is the default.</span></span>

<span data-ttu-id="f5b34-171">I följande exempel uppdateras åter givnings formatet till en minimal förlopps indikator.</span><span class="sxs-lookup"><span data-stu-id="f5b34-171">The following example updates the rendering style to a minimal progress bar.</span></span>

```powershell
$PSStyle.Progress.View.Minimal
```

> [!NOTE]
> <span data-ttu-id="f5b34-172">Du måste ha **PSAnsiRendering** experimentell funktion aktive rad för att använda den här funktionen.</span><span class="sxs-lookup"><span data-stu-id="f5b34-172">You must have the **PSAnsiRendering** experimental feature enabled to use this feature.</span></span>

## <a name="pscommandnotfoundsuggestion"></a><span data-ttu-id="f5b34-173">PSCommandNotFoundSuggestion</span><span class="sxs-lookup"><span data-stu-id="f5b34-173">PSCommandNotFoundSuggestion</span></span>

<span data-ttu-id="f5b34-174">Rekommenderar möjliga kommandon baserade på fuzzy-matchande sökning efter en **CommandNotFoundException**.</span><span class="sxs-lookup"><span data-stu-id="f5b34-174">Recommends potential commands based on fuzzy matching search after a **CommandNotFoundException**.</span></span>

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

## <a name="pscultureinvariantreplaceoperator"></a><span data-ttu-id="f5b34-175">PSCultureInvariantReplaceOperator</span><span class="sxs-lookup"><span data-stu-id="f5b34-175">PSCultureInvariantReplaceOperator</span></span>

<span data-ttu-id="f5b34-176">När den vänstra operanden i en `-replace` operator-instruktion inte är en sträng, konverteras den operanden till en sträng.</span><span class="sxs-lookup"><span data-stu-id="f5b34-176">When the left-hand operand in a `-replace` operator statement is not a string, that operand is converted to a string.</span></span>

<span data-ttu-id="f5b34-177">När den här funktionen är inaktive rad `-replace` gör operatorn en kultur känslig sträng konvertering.</span><span class="sxs-lookup"><span data-stu-id="f5b34-177">When this feature is disabled, the `-replace` operator does a culture-sensitive string conversion.</span></span>
<span data-ttu-id="f5b34-178">Om kulturen till exempel är inställt på franska (FR) `1.2` konverteras värdet till strängen `1,2` .</span><span class="sxs-lookup"><span data-stu-id="f5b34-178">For example, if your culture is set to French (fr), the value `1.2` is converted to the string `1,2`.</span></span>

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
12
PS> [cultureinfo]::CurrentCulture = 'en'
PS> 1.2 -replace ','
1.2
```

<span data-ttu-id="f5b34-179">Med funktionen aktive rad:</span><span class="sxs-lookup"><span data-stu-id="f5b34-179">With the feature enabled:</span></span>

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
1.2
```

## <a name="psdesiredstateconfigurationinvokedscresource"></a><span data-ttu-id="f5b34-180">PSDesiredStateConfiguration.InvokeDscResource</span><span class="sxs-lookup"><span data-stu-id="f5b34-180">PSDesiredStateConfiguration.InvokeDscResource</span></span>

<span data-ttu-id="f5b34-181">Möjliggör kompilering till MOF på icke-Windows-system och möjliggör användning av `Invoke-DSCResource` utan LCM.</span><span class="sxs-lookup"><span data-stu-id="f5b34-181">Enables compilation to MOF on non-Windows systems and enables the use of `Invoke-DSCResource` without an LCM.</span></span>

## <a name="psimplicitremotingbatching"></a><span data-ttu-id="f5b34-182">PSImplicitRemotingBatching</span><span class="sxs-lookup"><span data-stu-id="f5b34-182">PSImplicitRemotingBatching</span></span>

<span data-ttu-id="f5b34-183">Den här funktionen undersöker kommandot som anges i gränssnittet och om alla kommandon är implicita proxy-kommandon för fjärr kommunikation som utgör en enkel pipeline, grupperas kommandona tillsammans och anropas som en enda fjärrpipeline.</span><span class="sxs-lookup"><span data-stu-id="f5b34-183">This feature examines the command typed in the shell, and if all the commands are implicit remoting proxy commands that form a simple pipeline, then the commands are batched together and invoked as a single remote pipeline.</span></span>

<span data-ttu-id="f5b34-184">Exempel:</span><span class="sxs-lookup"><span data-stu-id="f5b34-184">Example:</span></span>

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

<span data-ttu-id="f5b34-185">Som det sågs ovan, med funktionen för batchbearbetning, är alla tre implicita proxy-kommandon för fjärr kommunikation,,,, `Get-AllProcesses` `Select-Custom` `Group-Stuff` som körs i fjärrsessionen och resultatet från pipelinen de enda data som returneras till klienten.</span><span class="sxs-lookup"><span data-stu-id="f5b34-185">As seen above, with the batching feature enabled, all three implicit remoting proxy commands, `Get-AllProcesses`, `Select-Custom`, `Group-Stuff`, run in the remote session and the result from the pipeline is the only data returned to the client.</span></span> <span data-ttu-id="f5b34-186">Detta minskar mängden data som skickas fram och tillbaka mellan klienten och fjärrsessionen och minskar också mängden objekt serialisering och avserialisering.</span><span class="sxs-lookup"><span data-stu-id="f5b34-186">This decreases the amount of data sent back and forth between client and remote session, and also reduces the amount of object serialization and de-serialization.</span></span>

## <a name="psnativepspathresolution"></a><span data-ttu-id="f5b34-187">PSNativePSPathResolution</span><span class="sxs-lookup"><span data-stu-id="f5b34-187">PSNativePSPathResolution</span></span>

<span data-ttu-id="f5b34-188">Om en PSDrive-sökväg som använder fil Systems leverantören skickas till ett ursprungligt kommando skickas den matchade fil Sök vägen till det ursprungliga kommandot.</span><span class="sxs-lookup"><span data-stu-id="f5b34-188">If a PSDrive path that uses the FileSystem provider is passed to a native command, the resolved file path is passed to the native command.</span></span> <span data-ttu-id="f5b34-189">Det innebär att ett kommando som `code temp:/test.txt` nu fungerar som förväntat.</span><span class="sxs-lookup"><span data-stu-id="f5b34-189">This means a command like `code temp:/test.txt` now works as expected.</span></span>

<span data-ttu-id="f5b34-190">I Windows, om sökvägen börjar med `~` , är det också som matchas med den fullständiga sökvägen och skickas till det inbyggda kommandot.</span><span class="sxs-lookup"><span data-stu-id="f5b34-190">Also, on Windows, if the path starts with `~`, that is resolved to the full path and passed to the native command.</span></span> <span data-ttu-id="f5b34-191">I båda fallen normaliseras sökvägen till katalog avgränsarna för det aktuella operativ systemet.</span><span class="sxs-lookup"><span data-stu-id="f5b34-191">In both cases, the path is normalized to the directory separators for the relevant operating system.</span></span>

- <span data-ttu-id="f5b34-192">Om sökvägen inte är en PSDrive eller `~` (i Windows) sker inte Sök vägs normalisering</span><span class="sxs-lookup"><span data-stu-id="f5b34-192">If the path is not a PSDrive or `~` (on Windows), then path normalization doesn't occur</span></span>
- <span data-ttu-id="f5b34-193">Om sökvägen är i enkla citat tecken matchas den inte och behandlas som literal</span><span class="sxs-lookup"><span data-stu-id="f5b34-193">If the path is in single quotes, then it's not resolved and treated as literal</span></span>

## <a name="psnotapplyerroractiontostderr"></a><span data-ttu-id="f5b34-194">PSNotApplyErrorActionToStderr</span><span class="sxs-lookup"><span data-stu-id="f5b34-194">PSNotApplyErrorActionToStderr</span></span>

<span data-ttu-id="f5b34-195">När den här experimentella funktionen är aktive rad skrivs fel poster som omdirigeras från interna kommandon, t. ex. När du använder omdirigerings operatorer ( `2>&1` ), inte till `$Error` variabeln och Preference-variabeln `$ErrorActionPreference` påverkar inte de omdirigerade utdata.</span><span class="sxs-lookup"><span data-stu-id="f5b34-195">When this experimental feature is enabled, error records redirected from native commands, like when using redirection operators (`2>&1`), are not written to the `$Error` variable and the preference variable `$ErrorActionPreference` does not affect the redirected output.</span></span>

<span data-ttu-id="f5b34-196">Många interna kommandon skriver till `stderr` som en alternativ ström för ytterligare information.</span><span class="sxs-lookup"><span data-stu-id="f5b34-196">Many native commands write to `stderr` as an alternative stream for additional information.</span></span> <span data-ttu-id="f5b34-197">Det här beteendet kan orsaka förvirring när du tittar på fel eller ytterligare utdata kan gå förlorade till användaren om `$ErrorActionPreference` har angetts till ett tillstånd som inaktive ras av utdata.</span><span class="sxs-lookup"><span data-stu-id="f5b34-197">This behavior can cause confusion when looking through errors or the additional output information can be lost to the user if `$ErrorActionPreference` is set to a state that mutes the output.</span></span>

<span data-ttu-id="f5b34-198">Om ett ursprungligt kommando har en slutkod som inte är noll `$?` är inställt på `$false` .</span><span class="sxs-lookup"><span data-stu-id="f5b34-198">When a native command has a non-zero exit code, `$?` is set to `$false`.</span></span> <span data-ttu-id="f5b34-199">Om slut koden är noll `$?` anges till `$true` .</span><span class="sxs-lookup"><span data-stu-id="f5b34-199">If the exit code is zero, `$?` is set to `$true`.</span></span>

## <a name="psnullconditionaloperators"></a><span data-ttu-id="f5b34-200">PSNullConditionalOperators</span><span class="sxs-lookup"><span data-stu-id="f5b34-200">PSNullConditionalOperators</span></span>

<span data-ttu-id="f5b34-201">Introducerar nya operatörer för null-ansvariga för villkorlig medlem- `?.` och `?[]` .</span><span class="sxs-lookup"><span data-stu-id="f5b34-201">Introduces new operators for Null conditional member access operators - `?.` and `?[]`.</span></span> <span data-ttu-id="f5b34-202">Null-ansvariga för medlems åtkomst kan användas för skalära typer och mat ris typer.</span><span class="sxs-lookup"><span data-stu-id="f5b34-202">Null member access operators can be used on scalar types and array types.</span></span> <span data-ttu-id="f5b34-203">Returnera värdet för den använda medlemmen om variabeln inte är null.</span><span class="sxs-lookup"><span data-stu-id="f5b34-203">Return the value of the accessed member if the variable is not null.</span></span> <span data-ttu-id="f5b34-204">Om värdet för variabeln är null returnerar du null.</span><span class="sxs-lookup"><span data-stu-id="f5b34-204">If the value of the variable is null, then return null.</span></span>

```powershell
$x = $null
${x}?.propname
${x?}?.propname

${x}?[0]
${x?}?[0]

${x}?.MyMethod()
```

<span data-ttu-id="f5b34-205">Egenskapen `propname` används och värdet returneras endast om `$x` inte är null.</span><span class="sxs-lookup"><span data-stu-id="f5b34-205">The property `propname` is accessed and it's value is returned only if `$x` is not null.</span></span> <span data-ttu-id="f5b34-206">På samma sätt används indexeraren endast om `$x` inte är null.</span><span class="sxs-lookup"><span data-stu-id="f5b34-206">Similarly, the indexer is used only if `$x` is not null.</span></span> <span data-ttu-id="f5b34-207">Om `$x` är null returneras null.</span><span class="sxs-lookup"><span data-stu-id="f5b34-207">If `$x` is null, then null is returned.</span></span>

<span data-ttu-id="f5b34-208">`?.` `?[]` Operatorerna och är medlemmar i operatorn och ger inte ett blank steg mellan variabel namnet och operatorn.</span><span class="sxs-lookup"><span data-stu-id="f5b34-208">The `?.` and `?[]` operators are member access operators and do not allow a space in between the variable name and the operator.</span></span>

<span data-ttu-id="f5b34-209">Eftersom PowerShell tillåter `?` som en del av variabel namnet, krävs avtvetydighet när operatorerna används utan blank steg mellan variabelns namn och operatorn.</span><span class="sxs-lookup"><span data-stu-id="f5b34-209">Since PowerShell allows `?` as part of the variable name, disambiguation is required when the operators are used without a space between the variable name and the operator.</span></span> <span data-ttu-id="f5b34-210">För att disambiguate ska variablerna använda `{}` runt variabel namnet som: `${x?}?.propertyName` eller `${y}?[0]` .</span><span class="sxs-lookup"><span data-stu-id="f5b34-210">To disambiguate, the variables must use `{}` around the variable name like: `${x?}?.propertyName` or `${y}?[0]`.</span></span>

> [!NOTE]
> <span data-ttu-id="f5b34-211">Den här funktionen har flyttat från experiment fasen och är en vanlig funktion i PowerShell 7,1 och högre.</span><span class="sxs-lookup"><span data-stu-id="f5b34-211">This feature has moved out of the experimental phase and is a mainstream feature in PowerShell 7.1 and higher.</span></span>

## <a name="pstempdrive"></a><span data-ttu-id="f5b34-212">PSTempDrive</span><span class="sxs-lookup"><span data-stu-id="f5b34-212">PSTempDrive</span></span>

<span data-ttu-id="f5b34-213">Skapar den `TEMP:` PSDrive som är mappad till användarens tillfälliga katalog Sök väg.</span><span class="sxs-lookup"><span data-stu-id="f5b34-213">Creates the `TEMP:` PSDrive mapped to user's temporary directory path.</span></span>

> [!NOTE]
> <span data-ttu-id="f5b34-214">Den här funktionen har flyttat från experiment fasen och är en vanlig funktion i PowerShell 7 och högre.</span><span class="sxs-lookup"><span data-stu-id="f5b34-214">This feature has moved out of the experimental phase and is a mainstream feature in PowerShell 7 and higher.</span></span>

## <a name="psunixfilestat"></a><span data-ttu-id="f5b34-215">PSUnixFileStat</span><span class="sxs-lookup"><span data-stu-id="f5b34-215">PSUnixFileStat</span></span>

<span data-ttu-id="f5b34-216">Den här funktionen ger nya beteenden för att inkludera data från UNIX **stat** -API i utdatan från fil system leverantören för att under lätta en mer UNIX-liknande fil lista.</span><span class="sxs-lookup"><span data-stu-id="f5b34-216">This feature provides new behavior to include data from the Unix **stat** API in the output of the file system provider to facilitate a more Unix-like file listing.</span></span> <span data-ttu-id="f5b34-217">Den lägger till en ny antecknings egenskap i fil namns leverantören med namnet **UnixStat** som innehåller ett gemensamt uttryck för `stat(2)` API: et från det underliggande UNIX-typ systemet.</span><span class="sxs-lookup"><span data-stu-id="f5b34-217">It adds a new note property in the filesystem provider named **UnixStat** that includes a common expression of the `stat(2)` API from the underlying Unix type system.</span></span>

<span data-ttu-id="f5b34-218">Utdata från `Get-ChildItem` bör se ut ungefär så här:</span><span class="sxs-lookup"><span data-stu-id="f5b34-218">The output from `Get-ChildItem` should look something like this:</span></span>

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

> [!NOTE]
> <span data-ttu-id="f5b34-219">Den här funktionen har flyttat från experiment fasen och är en vanlig funktion i PowerShell 7,1 och högre.</span><span class="sxs-lookup"><span data-stu-id="f5b34-219">This feature has moved out of the experimental phase and is a mainstream feature in PowerShell 7.1 and higher.</span></span>

## <a name="psuseabbreviationexpansion"></a><span data-ttu-id="f5b34-220">PSUseAbbreviationExpansion</span><span class="sxs-lookup"><span data-stu-id="f5b34-220">PSUseAbbreviationExpansion</span></span>

<span data-ttu-id="f5b34-221">Den här funktionen gör det möjligt att slutföra nedtvingade cmdlets och funktioner:</span><span class="sxs-lookup"><span data-stu-id="f5b34-221">This feature enables tab-completion of abbreviated cmdlets and functions:</span></span>

<span data-ttu-id="f5b34-222">Exempel:</span><span class="sxs-lookup"><span data-stu-id="f5b34-222">For example:</span></span>

- <span data-ttu-id="f5b34-223">`i-psdf<tab>` Returnerar `Import-PowerShellDataFile` .</span><span class="sxs-lookup"><span data-stu-id="f5b34-223">`i-psdf<tab>` returns `Import-PowerShellDataFile`.</span></span>
- <span data-ttu-id="f5b34-224">`u-akvmssdr<tab>` avkastning `Undo-AzKeyVaultManagedStorageSasDefinitionRemoval`</span><span class="sxs-lookup"><span data-stu-id="f5b34-224">`u-akvmssdr<tab>` returns `Undo-AzKeyVaultManagedStorageSasDefinitionRemoval`</span></span>

<span data-ttu-id="f5b34-225">Detta fungerar bara för slut för ande av flikar (interaktiv användning), så det `i-psdf` är inte ett giltigt cmdlet-namn i ett skript.</span><span class="sxs-lookup"><span data-stu-id="f5b34-225">This only works for tab completion (interactive use), so `i-psdf` is not a valid cmdlet name in a script.</span></span>

> [!NOTE]
> <span data-ttu-id="f5b34-226">Den här funktionen har flyttat från experiment fasen och är en vanlig funktion i PowerShell 7 och högre.</span><span class="sxs-lookup"><span data-stu-id="f5b34-226">This feature has moved out of the experimental phase and is a mainstream feature in PowerShell 7 and higher.</span></span>

## <a name="pssubsystempluginmodel"></a><span data-ttu-id="f5b34-227">PSSubsystemPluginModel</span><span class="sxs-lookup"><span data-stu-id="f5b34-227">PSSubsystemPluginModel</span></span>

<span data-ttu-id="f5b34-228">Den här funktionen aktiverar under Systems-plugin-modellen i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f5b34-228">This feature enables the subsystem plugin model in PowerShell.</span></span> <span data-ttu-id="f5b34-229">Funktionen gör det möjligt att separera komponenter i `System.Management.Automation.dll` enskilda under system som finns i en egen sammansättning.</span><span class="sxs-lookup"><span data-stu-id="f5b34-229">The feature makes it possible to separate components of `System.Management.Automation.dll` into individual subsystems that reside in their own assembly.</span></span> <span data-ttu-id="f5b34-230">Den här separationen minskar den grundläggande PowerShell-motorns disk utrymme och gör att dessa komponenter blir valfria funktioner för en minimal PowerShell-installation.</span><span class="sxs-lookup"><span data-stu-id="f5b34-230">This separation reduces the disk footprint of the core PowerShell engine and allows these components to become optional features for a minimal PowerShell installation.</span></span>

<span data-ttu-id="f5b34-231">För närvarande stöds endast under systemet **CommandPredictor** .</span><span class="sxs-lookup"><span data-stu-id="f5b34-231">Currently, only the **CommandPredictor** subsystem is supported.</span></span> <span data-ttu-id="f5b34-232">Det här del systemet används tillsammans med PSReadLine-modulen för att tillhandahålla anpassade förutsägelse-plugin-program.</span><span class="sxs-lookup"><span data-stu-id="f5b34-232">This subsystem is used along with the PSReadLine module to provide custom prediction plugins.</span></span> <span data-ttu-id="f5b34-233">I framtiden kan **jobb**, **CommandCompleter**, **fjärr kommunikation** och andra komponenter delas upp i del system sammansättningar utanför `System.Management.Automation.dll` .</span><span class="sxs-lookup"><span data-stu-id="f5b34-233">In future, **Job**, **CommandCompleter**, **Remoting** and other components could be separated into subsystem assemblies outside of `System.Management.Automation.dll`.</span></span>

<span data-ttu-id="f5b34-234">Experiment funktionen innehåller en ny cmdlet, [Get-PSSubsystem](xref:Microsoft.PowerShell.Core.Get-PSSubsystem).</span><span class="sxs-lookup"><span data-stu-id="f5b34-234">The experimental feature includes a new cmdlet, [Get-PSSubsystem](xref:Microsoft.PowerShell.Core.Get-PSSubsystem).</span></span> <span data-ttu-id="f5b34-235">Den här cmdleten är endast tillgänglig om funktionen är aktive rad.</span><span class="sxs-lookup"><span data-stu-id="f5b34-235">This cmdlet is only available when the feature is enabled.</span></span> <span data-ttu-id="f5b34-236">Denna cmdlet returnerar information om de del system som är tillgängliga i systemet.</span><span class="sxs-lookup"><span data-stu-id="f5b34-236">This cmdlet returns information about the subsystems that are available on the system.</span></span>
