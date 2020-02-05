---
ms.date: 02/03/2020
keywords: PowerShell, Core
title: Bryta ändringar för PowerShell 6,0
ms.openlocfilehash: 47ed14cceed86e4dd04a8e0079af00f6a98988ea
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995452"
---
# <a name="breaking-changes-for-powershell-6x"></a><span data-ttu-id="39724-103">Bryta ändringar för PowerShell 6. x</span><span class="sxs-lookup"><span data-stu-id="39724-103">Breaking Changes for PowerShell 6.x</span></span>

## <a name="features-no-longer-available-in-powershell-core"></a><span data-ttu-id="39724-104">Funktioner som inte längre är tillgängliga i PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="39724-104">Features no longer available in PowerShell Core</span></span>

### <a name="modules-not-shipped-for-powershell-6x"></a><span data-ttu-id="39724-105">Moduler som inte levererats för PowerShell 6. x</span><span class="sxs-lookup"><span data-stu-id="39724-105">Modules not shipped for PowerShell 6.x</span></span>

<span data-ttu-id="39724-106">För olika kompatibilitetsproblem ingår inte följande moduler i PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="39724-106">For various compatibility reasons, the following modules are not included in PowerShell 6.</span></span>

- <span data-ttu-id="39724-107">ISE</span><span class="sxs-lookup"><span data-stu-id="39724-107">ISE</span></span>
- <span data-ttu-id="39724-108">Microsoft. PowerShell. LocalAccounts</span><span class="sxs-lookup"><span data-stu-id="39724-108">Microsoft.PowerShell.LocalAccounts</span></span>
- <span data-ttu-id="39724-109">Microsoft. PowerShell. ODataUtils</span><span class="sxs-lookup"><span data-stu-id="39724-109">Microsoft.PowerShell.ODataUtils</span></span>
- <span data-ttu-id="39724-110">Microsoft. PowerShell. operation. Validation</span><span class="sxs-lookup"><span data-stu-id="39724-110">Microsoft.PowerShell.Operation.Validation</span></span>
- <span data-ttu-id="39724-111">PSScheduledJob</span><span class="sxs-lookup"><span data-stu-id="39724-111">PSScheduledJob</span></span>
- <span data-ttu-id="39724-112">PSWorkflow</span><span class="sxs-lookup"><span data-stu-id="39724-112">PSWorkflow</span></span>
- <span data-ttu-id="39724-113">PSWorkflowUtility</span><span class="sxs-lookup"><span data-stu-id="39724-113">PSWorkflowUtility</span></span>

### <a name="powershell-workflow"></a><span data-ttu-id="39724-114">PowerShell-arbetsflöde</span><span class="sxs-lookup"><span data-stu-id="39724-114">PowerShell Workflow</span></span>

<span data-ttu-id="39724-115">[PowerShell-arbetsflöde][workflow] är en funktion i Windows PowerShell som bygger ovanpå [Windows Workflow Foundation (WF)][workflow-foundation] som gör det möjligt att skapa robusta Runbooks för långvariga eller parallella uppgifter.</span><span class="sxs-lookup"><span data-stu-id="39724-115">[PowerShell Workflow][workflow] is a feature in Windows PowerShell that builds on top of [Windows Workflow Foundation (WF)][workflow-foundation] that enables the creation of robust runbooks for long-running or parallelized tasks.</span></span>

<span data-ttu-id="39724-116">På grund av brist på stöd för Windows Workflow Foundation i .NET Core stöder vi inte PowerShell-arbetsflöde i PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="39724-116">Due to the lack of support for Windows Workflow Foundation in .NET Core, we are not supporting PowerShell Workflow in PowerShell Core.</span></span>

<span data-ttu-id="39724-117">I framtiden skulle vi vilja aktivera inbyggd parallellitet/samtidighet i PowerShell-språket utan att behöva använda PowerShell-arbetsflöde.</span><span class="sxs-lookup"><span data-stu-id="39724-117">In the future, we would like to enable native parallelism/concurrency in the PowerShell language without the need for PowerShell Workflow.</span></span>

<span data-ttu-id="39724-118">Om du behöver använda kontroll punkter för att återuppta ett skript efter det att operativ systemet har startats om, rekommenderar vi att du använder Schemaläggaren för att köra ett skript på Start av operativ systemet, men skriptet måste ha ett eget tillstånd (som att spara det i en fil).</span><span class="sxs-lookup"><span data-stu-id="39724-118">If there is a need to use checkpoints to resume a script after the OS restarts, we recommend using Task Scheduler to run a script on OS startup, but the script would need to maintain its own state (like persisting it to a file).</span></span>

[workflow]: /powershell/scripting/components/workflows-guide
[workflow-foundation]: https://docs.microsoft.com/dotnet/framework/windows-workflow-foundation/

### <a name="custom-snap-ins"></a><span data-ttu-id="39724-119">Anpassade snapin-moduler</span><span class="sxs-lookup"><span data-stu-id="39724-119">Custom snap-ins</span></span>

<span data-ttu-id="39724-120">[PowerShell-snapin-moduler][snapin] är en föregående aktivitet till PowerShell-moduler som inte har omfattande antagande i PowerShell-communityn.</span><span class="sxs-lookup"><span data-stu-id="39724-120">[PowerShell snap-ins][snapin] are a predecessor to PowerShell modules that do not have widespread adoption in the PowerShell community.</span></span>

<span data-ttu-id="39724-121">På grund av komplexiteten vid stöd för snapin-moduler och deras brist på användning i communityn stöder vi inte längre anpassade snapin-moduler i PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="39724-121">Due to the complexity of supporting snap-ins and their lack of usage in the community, we no longer support custom snap-ins in PowerShell Core.</span></span>

<span data-ttu-id="39724-122">Idag tar detta upp `ActiveDirectory` och `DnsClient` modulerna i Windows och Windows Server.</span><span class="sxs-lookup"><span data-stu-id="39724-122">Today, this breaks the `ActiveDirectory` and `DnsClient` modules in Windows and Windows Server.</span></span>

[snapin]: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins

### <a name="wmi-v1-cmdlets"></a><span data-ttu-id="39724-123">WMI v1-cmdletar</span><span class="sxs-lookup"><span data-stu-id="39724-123">WMI v1 cmdlets</span></span>

<span data-ttu-id="39724-124">På grund av komplexiteten med stöd för två uppsättningar WMI-baserade moduler tog vi bort WMI v1-cmdletar från PowerShell Core:</span><span class="sxs-lookup"><span data-stu-id="39724-124">Due to the complexity of supporting two sets of WMI-based modules, we removed the WMI v1 cmdlets from PowerShell Core:</span></span>

- `Register-WmiEvent`
- `Set-WmiInstance`
- `Invoke-WmiMethod`
- `Get-WmiObject`
- `Remove-WmiObject`

<span data-ttu-id="39724-125">I stället rekommenderar vi att du använder CIM-cmdletarna (aka WMI v2) som tillhandahåller samma funktioner med nya funktioner och en omdesignad syntax:</span><span class="sxs-lookup"><span data-stu-id="39724-125">Instead, we recommend that you the use the CIM (aka WMI v2) cmdlets which provide the same functionality with new functionality and a redesigned syntax:</span></span>

- `Get-CimAssociatedInstance`
- `Get-CimClass`
- `Get-CimInstance`
- `Get-CimSession`
- `Invoke-CimMethod`
- `New-CimInstance`
- `New-CimSession`
- `New-CimSessionOption`
- `Register-CimIndicationEvent`
- `Remove-CimInstance`
- `Remove-CimSession`
- `Set-CimInstance`

### <a name="microsoftpowershelllocalaccounts"></a><span data-ttu-id="39724-126">Microsoft. PowerShell. LocalAccounts</span><span class="sxs-lookup"><span data-stu-id="39724-126">Microsoft.PowerShell.LocalAccounts</span></span>

<span data-ttu-id="39724-127">På grund av användning av API: er som inte stöds har `Microsoft.PowerShell.LocalAccounts` tagits bort från PowerShell Core tills en bättre lösning har hittats.</span><span class="sxs-lookup"><span data-stu-id="39724-127">Due to the use of unsupported APIs, `Microsoft.PowerShell.LocalAccounts` has been removed from PowerShell Core until a better solution is found.</span></span>

### <a name="new-webserviceproxy-cmdlet-removed"></a><span data-ttu-id="39724-128">`New-WebServiceProxy` cmdlet har tagits bort</span><span class="sxs-lookup"><span data-stu-id="39724-128">`New-WebServiceProxy` cmdlet removed</span></span>

<span data-ttu-id="39724-129">.NET Core har inte stöd för Windows Communication Framework, som tillhandahåller tjänster för att använda SOAP-protokollet.</span><span class="sxs-lookup"><span data-stu-id="39724-129">.NET Core does not support the Windows Communication Framework, which provide services for using the SOAP protocol.</span></span> <span data-ttu-id="39724-130">Den här cmdleten togs bort eftersom den kräver SOAP.</span><span class="sxs-lookup"><span data-stu-id="39724-130">This cmdlet was removed because it requires SOAP.</span></span>

### <a name="-transaction-cmdlets-removed"></a><span data-ttu-id="39724-131">`*-Transaction` cmdlets tas bort</span><span class="sxs-lookup"><span data-stu-id="39724-131">`*-Transaction` cmdlets removed</span></span>

<span data-ttu-id="39724-132">Dessa cmdletar hade mycket begränsad användning.</span><span class="sxs-lookup"><span data-stu-id="39724-132">These cmdlets had very limited usage.</span></span> <span data-ttu-id="39724-133">Beslutet har fattats för att avbryta stödet för dem.</span><span class="sxs-lookup"><span data-stu-id="39724-133">The decision was made to discontinue support for them.</span></span>

- `Complete-Transaction`
- `Get-Transaction`
- `Start-Transaction`
- `Undo-Transaction`
- `Use-Transaction`

### <a name="security-cmdlets-not-available-on-non-windows-platforms"></a><span data-ttu-id="39724-134">Säkerhets-cmdletar är inte tillgängliga på plattformar som inte är Windows-plattformar</span><span class="sxs-lookup"><span data-stu-id="39724-134">Security cmdlets not available on non-Windows platforms</span></span>

- `Get-Acl`
- `Set-Acl`
- `Get-AuthenticodeSignature`
- `Set-AuthenticodeSignature`
- `Get-CmsMessage`
- `Protect-CmsMessage`
- `Unprotect-CmsMessage`
- `New-FileCatalog`
- `Test-FileCatalog`

### <a name="-computerand-other-windows-specific-cmdlets"></a><span data-ttu-id="39724-135">`*-Computer`och andra Windows-/regionsspecifika cmdlets</span><span class="sxs-lookup"><span data-stu-id="39724-135">`*-Computer`and other Windows-specific cmdlets</span></span>

<span data-ttu-id="39724-136">På grund av användning av API: er som inte stöds har följande cmdlets tagits bort från PowerShell Core tills en bättre lösning har hittats.</span><span class="sxs-lookup"><span data-stu-id="39724-136">Due to the use of unsupported APIs, the following cmdlets have been removed from PowerShell Core until a better solution is found.</span></span>

- `Get-Clipboard`
- `Set-Clipboard`
- `Add-Computer`
- `Checkpoint-Computer`
- `Remove-Computer`
- `Restore-Computer`
- `Reset-ComputerMachinePassword`
- `Disable-ComputerRestore`
- `Enable-ComputerRestore`
- `Get-ComputerRestorePoint`
- `Test-ComputerSecureChannel`
- `Get-ControlPanelItem`
- `Show-ControlPanelItem`
- `Get-HotFix`
- `Clear-RecycleBin`
- `Update-List`
- `Out-Printer`
- `ConvertFrom-String`
- `Convert-String`

### <a name="-counter-cmdlets"></a><span data-ttu-id="39724-137">`*-Counter`-cmdletar</span><span class="sxs-lookup"><span data-stu-id="39724-137">`*-Counter` cmdlets</span></span>

<span data-ttu-id="39724-138">På grund av användning av API: er som inte stöds har `*-Counter` tagits bort från PowerShell Core tills en bättre lösning har hittats.</span><span class="sxs-lookup"><span data-stu-id="39724-138">Due to the use of unsupported APIs, the `*-Counter` has been removed from PowerShell Core until a better solution is found.</span></span>

### <a name="-eventlog-cmdlets"></a><span data-ttu-id="39724-139">`*-EventLog`-cmdletar</span><span class="sxs-lookup"><span data-stu-id="39724-139">`*-EventLog` cmdlets</span></span>

<span data-ttu-id="39724-140">På grund av användning av API: er som inte stöds har `*-EventLog` tagits bort från PowerShell-kärnan.</span><span class="sxs-lookup"><span data-stu-id="39724-140">Due to the use of unsupported APIs, the `*-EventLog` has been removed from PowerShell Core.</span></span> <span data-ttu-id="39724-141">tills en bättre lösning har hittats.</span><span class="sxs-lookup"><span data-stu-id="39724-141">until a better solution is found.</span></span> <span data-ttu-id="39724-142">`Get-WinEvent` och `Create-WinEvent` är tillgängliga för att hämta och skapa händelser i Windows.</span><span class="sxs-lookup"><span data-stu-id="39724-142">`Get-WinEvent` and `Create-WinEvent` are available to get and create events on Windows.</span></span>

### <a name="cmdlets-that-use-wpf-removed"></a><span data-ttu-id="39724-143">Cmdletar som använder WPF borttagna</span><span class="sxs-lookup"><span data-stu-id="39724-143">Cmdlets that use WPF removed</span></span>

<span data-ttu-id="39724-144">Windows Presentation Framework stöds inte på CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="39724-144">The Windows Presentation Framework is not supported on CoreCLR.</span></span> <span data-ttu-id="39724-145">Följande cmdletar påverkas:</span><span class="sxs-lookup"><span data-stu-id="39724-145">The following cmdlets are affected:</span></span>

- `Show-Command`
- `Out-GridView`
- <span data-ttu-id="39724-146">**ShowWindow** -parametern för `Get-Help`</span><span class="sxs-lookup"><span data-stu-id="39724-146">The **showwindow** parameter of `Get-Help`</span></span>

### <a name="some-dsc-cmdlets-removed"></a><span data-ttu-id="39724-147">Vissa DSC-cmdletar har tagits bort</span><span class="sxs-lookup"><span data-stu-id="39724-147">Some DSC cmdlets removed</span></span>

- `Get-DscConfiguration`
- `Publish-DscConfiguration`
- `Restore-DscConfiguration`
- `Start-DscConfiguration`
- `Stop-DscConfiguration`
- `Test-DscConfiguration`
- `Update-DscConfiguration`
- `Remove-DscConfigurationDocument`
- `Get-DscConfigurationStatus`
- `Disable-DscDebug`
- `Enable-DscDebug`
- `Get-DscLocalConfigurationManager`
- `Set-DscLocalConfigurationManager`
- `Invoke-DscResource`

## <a name="enginelanguage-changes"></a><span data-ttu-id="39724-148">Motor/språk ändringar</span><span class="sxs-lookup"><span data-stu-id="39724-148">Engine/language changes</span></span>

### <a name="rename-powershellexe-to-pwshexe-5101httpsgithubcompowershellpowershellissues5101"></a><span data-ttu-id="39724-149">Byt namn på `powershell.exe` till `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)</span><span class="sxs-lookup"><span data-stu-id="39724-149">Rename `powershell.exe` to `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)</span></span>

<span data-ttu-id="39724-150">För att ge användarna ett deterministiskt sätt att anropa PowerShell Core på Windows (till skillnad från Windows PowerShell) ändrades binärfilen för PowerShell-kärnan till `pwsh.exe` i Windows och `pwsh` på andra plattformar än Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="39724-150">In order to give users a deterministic way to call PowerShell Core on Windows (as opposed to Windows PowerShell), the PowerShell Core binary was changed to `pwsh.exe` on Windows and `pwsh` on non-Windows platforms.</span></span>

<span data-ttu-id="39724-151">Det förkortade namnet är också konsekvent med namngivning av gränssnitt på andra plattformar än Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="39724-151">The shortened name is also consistent with naming of shells on non-Windows platforms.</span></span>

### <a name="dont-insert-line-breaks-to-output-except-for-tables-5193httpsgithubcompowershellpowershellissues5193"></a><span data-ttu-id="39724-152">Infoga inte rad brytningar i utdata (förutom tabeller) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)</span><span class="sxs-lookup"><span data-stu-id="39724-152">Don't insert line breaks to output (except for tables) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)</span></span>

<span data-ttu-id="39724-153">Tidigare var utdata justerade till bredden på konsolen och rad brytningarna lades till i konsolens slut punkt, vilket innebär att resultatet inte blev omformaterat som förväntat om terminalfönstret ändrades.</span><span class="sxs-lookup"><span data-stu-id="39724-153">Previously, output was aligned to the width of the console and line breaks were added at the end width of the console, meaning the output didn't get reformatted as expected if the terminal was resized.</span></span> <span data-ttu-id="39724-154">Den här ändringen tillämpades inte i tabeller eftersom rad brytningar krävs för att hålla kolumnerna justerade.</span><span class="sxs-lookup"><span data-stu-id="39724-154">This change was not applied to tables, as the line breaks are necessary to keep the columns aligned.</span></span>

### <a name="skip-null-element-check-for-collections-with-a-value-type-element-type-5432httpsgithubcompowershellpowershellissues5432"></a><span data-ttu-id="39724-155">Hoppa över null-Elements kontroll för samlingar med en värde typs element typ [#5432](https://github.com/PowerShell/PowerShell/issues/5432)</span><span class="sxs-lookup"><span data-stu-id="39724-155">Skip null-element check for collections with a value-type element type [#5432](https://github.com/PowerShell/PowerShell/issues/5432)</span></span>

<span data-ttu-id="39724-156">För parametern `Mandatory` och `ValidateNotNull` och `ValidateNotNullOrEmpty` attribut, hoppar du över värdet null-element om samlingens element typ är värdetyp.</span><span class="sxs-lookup"><span data-stu-id="39724-156">For the `Mandatory` parameter and `ValidateNotNull` and `ValidateNotNullOrEmpty` attributes, skip the null-element check if the collection's element type is value type.</span></span>

### <a name="change-outputencoding-to-use-utf-8-nobom-encoding-rather-than-ascii-5369httpsgithubcompowershellpowershellissues5369"></a><span data-ttu-id="39724-157">Ändra `$OutputEncoding` att använda `UTF-8 NoBOM` encoding i stället för ASCII [#5369](https://github.com/PowerShell/PowerShell/issues/5369)</span><span class="sxs-lookup"><span data-stu-id="39724-157">Change `$OutputEncoding` to use `UTF-8 NoBOM` encoding rather than ASCII [#5369](https://github.com/PowerShell/PowerShell/issues/5369)</span></span>

<span data-ttu-id="39724-158">Föregående kodning, ASCII (7-bitars), resulterar i en felaktig ändring av utdata i vissa fall.</span><span class="sxs-lookup"><span data-stu-id="39724-158">The previous encoding, ASCII (7-bit), would result in incorrect alteration of the output in some cases.</span></span> <span data-ttu-id="39724-159">Den här ändringen är att göra `UTF-8 NoBOM` standard, vilket bevarar Unicode-utdata med en kodning som stöds av de flesta verktyg och operativ system.</span><span class="sxs-lookup"><span data-stu-id="39724-159">This change is to make `UTF-8 NoBOM` default, which preserves Unicode output with an encoding supported by most tools and operating systems.</span></span>

### <a name="remove-allscope-from-most-default-aliases-5268httpsgithubcompowershellpowershellissues5268"></a><span data-ttu-id="39724-160">Ta bort `AllScope` från de flesta Standardalias [#5268](https://github.com/PowerShell/PowerShell/issues/5268)</span><span class="sxs-lookup"><span data-stu-id="39724-160">Remove `AllScope` from most default aliases [#5268](https://github.com/PowerShell/PowerShell/issues/5268)</span></span>

<span data-ttu-id="39724-161">För att påskynda skapandet av ett område, har `AllScope` tagits bort från de flesta Standardalias.</span><span class="sxs-lookup"><span data-stu-id="39724-161">To speed up scope creation, `AllScope` was removed from most default aliases.</span></span> <span data-ttu-id="39724-162">`AllScope` lämnades för några vanliga alias där sökningen var snabbare.</span><span class="sxs-lookup"><span data-stu-id="39724-162">`AllScope` was left for a few frequently used aliases where the lookup was faster.</span></span>

### <a name="-verbose-and--debug-no-longer-overrides-erroractionpreference-5113httpsgithubcompowershellpowershellissues5113"></a><span data-ttu-id="39724-163">`-Verbose` och `-Debug` inte längre åsidosätter `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)</span><span class="sxs-lookup"><span data-stu-id="39724-163">`-Verbose` and `-Debug` no longer overrides `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)</span></span>

<span data-ttu-id="39724-164">Tidigare, om `-Verbose` eller `-Debug` har angetts, overrode funktionen för `$ErrorActionPreference`.</span><span class="sxs-lookup"><span data-stu-id="39724-164">Previously, if `-Verbose` or `-Debug` were specified, it overrode the behavior of `$ErrorActionPreference`.</span></span> <span data-ttu-id="39724-165">Med den här ändringen påverkar `-Verbose` och `-Debug` inte längre `$ErrorActionPreference`ens beteende.</span><span class="sxs-lookup"><span data-stu-id="39724-165">With this change, `-Verbose` and `-Debug` no longer affect the behavior of `$ErrorActionPreference`.</span></span>

## <a name="cmdlet-changes"></a><span data-ttu-id="39724-166">Cmdlet-ändringar</span><span class="sxs-lookup"><span data-stu-id="39724-166">Cmdlet changes</span></span>

### <a name="invoke-restmethod-doesnt-return-useful-info-when-no-data-is-returned-5320httpsgithubcompowershellpowershellissues5320"></a><span data-ttu-id="39724-167">Invoke-RestMethod returnerar inte värdefull information när inga data returneras.</span><span class="sxs-lookup"><span data-stu-id="39724-167">Invoke-RestMethod doesn't return useful info when no data is returned.</span></span> [<span data-ttu-id="39724-168">#5320</span><span class="sxs-lookup"><span data-stu-id="39724-168">#5320</span></span>](https://github.com/PowerShell/PowerShell/issues/5320)

<span data-ttu-id="39724-169">När ett API returnerar bara `null`, serialiserade Invoke-RestMethod detta som strängen `"null"` i stället för `$null`.</span><span class="sxs-lookup"><span data-stu-id="39724-169">When an API returns just `null`, Invoke-RestMethod was serializing this as the string `"null"` instead of `$null`.</span></span> <span data-ttu-id="39724-170">Med den här ändringen åtgärdas logiken i `Invoke-RestMethod` för korrekt serialisering av ett giltigt JSON-`null` literalt värde som `$null`.</span><span class="sxs-lookup"><span data-stu-id="39724-170">This change fixes the logic in `Invoke-RestMethod` to properly serialize a valid single value JSON `null` literal as `$null`.</span></span>

### <a name="remove--protocol-from--computer-cmdlets-5277httpsgithubcompowershellpowershellissues5277"></a><span data-ttu-id="39724-171">Ta bort `-Protocol` från `*-Computer`-cmdletar [#5277](https://github.com/PowerShell/PowerShell/issues/5277)</span><span class="sxs-lookup"><span data-stu-id="39724-171">Remove `-Protocol` from `*-Computer` cmdlets [#5277](https://github.com/PowerShell/PowerShell/issues/5277)</span></span>

<span data-ttu-id="39724-172">På grund av problem med RPC-fjärrkommunikation i CoreFX (särskilt på plattformar som inte är Windows) och säkerställer en konsekvent fjärrhantering i PowerShell, har parametern `-Protocol` tagits bort från `\*-Computer`-cmdlet: arna.</span><span class="sxs-lookup"><span data-stu-id="39724-172">Due to issues with RPC remoting in CoreFX (particularly on non-Windows platforms) and ensuring a consistent remoting experience in PowerShell, the `-Protocol` parameter was removed from the `\*-Computer` cmdlets.</span></span> <span data-ttu-id="39724-173">DCOM stöds inte längre för fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="39724-173">DCOM is no longer supported for remoting.</span></span> <span data-ttu-id="39724-174">Följande cmdletar stöder bara WSMAN-fjärr kommunikation:</span><span class="sxs-lookup"><span data-stu-id="39724-174">The following cmdlets only support WSMAN remoting:</span></span>

- <span data-ttu-id="39724-175">Byt namn – dator</span><span class="sxs-lookup"><span data-stu-id="39724-175">Rename-Computer</span></span>
- <span data-ttu-id="39724-176">Starta om datorn</span><span class="sxs-lookup"><span data-stu-id="39724-176">Restart-Computer</span></span>
- <span data-ttu-id="39724-177">Stoppa – dator</span><span class="sxs-lookup"><span data-stu-id="39724-177">Stop-Computer</span></span>

### <a name="remove--computername-from--service-cmdlets-5090httpsgithubcompowershellpowershellissues5094"></a><span data-ttu-id="39724-178">Ta bort `-ComputerName` från `*-Service`-cmdletar [#5090](https://github.com/PowerShell/PowerShell/issues/5094)</span><span class="sxs-lookup"><span data-stu-id="39724-178">Remove `-ComputerName` from `*-Service` cmdlets [#5090](https://github.com/PowerShell/PowerShell/issues/5094)</span></span>

<span data-ttu-id="39724-179">För att uppmuntra en konsekvent användning av PSRP har parametern `-ComputerName` tagits bort från `*-Service`-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="39724-179">In order to encourage the consistent use of PSRP, the `-ComputerName` parameter was removed from `*-Service` cmdlets.</span></span>

### <a name="fix-get-item--literalpath-ab-if-ab-doesnt-actually-exist-to-return-error-5197httpsgithubcompowershellpowershellissues5197"></a><span data-ttu-id="39724-180">Korrigera `Get-Item -LiteralPath a*b` om `a*b` faktiskt inte finns för att returnera fel [#5197](https://github.com/PowerShell/PowerShell/issues/5197)</span><span class="sxs-lookup"><span data-stu-id="39724-180">Fix `Get-Item -LiteralPath a*b` if `a*b` doesn't actually exist to return error [#5197](https://github.com/PowerShell/PowerShell/issues/5197)</span></span>

<span data-ttu-id="39724-181">Tidigare skulle `-LiteralPath` med ett jokertecken behandla det på samma sätt som `-Path` och om jokertecken inte hittas skulle det leda till tyst slut.</span><span class="sxs-lookup"><span data-stu-id="39724-181">Previously, `-LiteralPath` given a wildcard would treat it the same as `-Path` and if the wildcard found no files, it would silently exit.</span></span> <span data-ttu-id="39724-182">Korrekt beteende bör vara att `-LiteralPath` är Literal så om filen inte finns, bör den innehålla fel.</span><span class="sxs-lookup"><span data-stu-id="39724-182">Correct behavior should be that `-LiteralPath` is literal so if the file doesn't exist, it should error.</span></span> <span data-ttu-id="39724-183">Ändra är att hantera jokertecken som används med `-Literal` som literal.</span><span class="sxs-lookup"><span data-stu-id="39724-183">Change is to treat wildcards used with `-Literal` as literal.</span></span>

### <a name="import-csv-should-apply-pstypenames-upon-import-when-type-information-is-present-in-the-csv-5134httpsgithubcompowershellpowershellissues5134"></a><span data-ttu-id="39724-184">`Import-Csv` bör gälla `PSTypeNames` vid import när typ information finns i CSV- [#5134](https://github.com/PowerShell/PowerShell/issues/5134)</span><span class="sxs-lookup"><span data-stu-id="39724-184">`Import-Csv` should apply `PSTypeNames` upon import when type information is present in the CSV [#5134](https://github.com/PowerShell/PowerShell/issues/5134)</span></span>

<span data-ttu-id="39724-185">Tidigare har objekt som exporter ATS med `Export-CSV` med `TypeInformation` som importer ATS med `ConvertFrom-Csv` inte bevaras av typ informationen.</span><span class="sxs-lookup"><span data-stu-id="39724-185">Previously, objects exported using `Export-CSV` with `TypeInformation` imported with `ConvertFrom-Csv` were not retaining the type information.</span></span> <span data-ttu-id="39724-186">Den här ändringen lägger till typ informationen till `PSTypeNames` medlem om den är tillgänglig från CSV-filen.</span><span class="sxs-lookup"><span data-stu-id="39724-186">This change adds the type information to `PSTypeNames` member if available from the CSV file.</span></span>

### <a name="-notypeinformation-should-be-default-on-export-csv-5131httpsgithubcompowershellpowershellissues5131"></a><span data-ttu-id="39724-187">`-NoTypeInformation` ska vara standard på `Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131)</span><span class="sxs-lookup"><span data-stu-id="39724-187">`-NoTypeInformation` should be default on `Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131)</span></span>

<span data-ttu-id="39724-188">Den här ändringen gjordes för att lösa kundfeedback om standard beteendet för `Export-CSV` att inkludera typ information.</span><span class="sxs-lookup"><span data-stu-id="39724-188">This change was made to address customer feedback on the default behavior of `Export-CSV` to include type information.</span></span>

<span data-ttu-id="39724-189">Tidigare skulle cmdleten skriva en kommentar som den första raden som innehåller objektets typnamn.</span><span class="sxs-lookup"><span data-stu-id="39724-189">Previously, the cmdlet would output a comment as the first line containing the type name of the object.</span></span> <span data-ttu-id="39724-190">Ändringen är att ignorera detta som standard eftersom det inte tolkas av de flesta verktyg.</span><span class="sxs-lookup"><span data-stu-id="39724-190">The change is to suppress this by default as it's not understood by most tools.</span></span> <span data-ttu-id="39724-191">Använd `-IncludeTypeInformation` för att behålla det tidigare beteendet.</span><span class="sxs-lookup"><span data-stu-id="39724-191">Use `-IncludeTypeInformation` to retain the previous behavior.</span></span>

### <a name="web-cmdlets-should-warn-when--credential-is-sent-over-unencrypted-connections-5112httpsgithubcompowershellpowershellissues5112"></a><span data-ttu-id="39724-192">Webb-cmdletar ska varna när `-Credential` skickas via okrypterade anslutningar [#5112](https://github.com/PowerShell/PowerShell/issues/5112)</span><span class="sxs-lookup"><span data-stu-id="39724-192">Web Cmdlets should warn when `-Credential` is sent over unencrypted connections [#5112](https://github.com/PowerShell/PowerShell/issues/5112)</span></span>

<span data-ttu-id="39724-193">När du använder HTTP skickas innehåll inklusive lösen ord som klartext.</span><span class="sxs-lookup"><span data-stu-id="39724-193">When using HTTP, content including passwords are sent as clear-text.</span></span> <span data-ttu-id="39724-194">Den här ändringen är att inte tillåta detta som standard och returnera ett fel om autentiseringsuppgifterna skickas på ett osäkert sätt.</span><span class="sxs-lookup"><span data-stu-id="39724-194">This change is to not allow this by default and return an error if credentials are being passed in an insecure manner.</span></span> <span data-ttu-id="39724-195">Användare kan kringgå detta genom att använda `-AllowUnencryptedAuthentication` växeln.</span><span class="sxs-lookup"><span data-stu-id="39724-195">Users can bypass this by using the `-AllowUnencryptedAuthentication` switch.</span></span>

## <a name="api-changes"></a><span data-ttu-id="39724-196">API-ändringar</span><span class="sxs-lookup"><span data-stu-id="39724-196">API changes</span></span>

### <a name="remove-addtypecommandbase-class-5407httpsgithubcompowershellpowershellissues5407"></a><span data-ttu-id="39724-197">Ta bort `AddTypeCommandBase` klass [#5407](https://github.com/PowerShell/PowerShell/issues/5407)</span><span class="sxs-lookup"><span data-stu-id="39724-197">Remove `AddTypeCommandBase` class [#5407](https://github.com/PowerShell/PowerShell/issues/5407)</span></span>

<span data-ttu-id="39724-198">`AddTypeCommandBase`-klassen togs bort från `Add-Type` för att förbättra prestandan.</span><span class="sxs-lookup"><span data-stu-id="39724-198">The `AddTypeCommandBase` class was removed from `Add-Type` to improve performance.</span></span> <span data-ttu-id="39724-199">Den här klassen används endast av cmdleten Add-Type och bör inte påverka användare.</span><span class="sxs-lookup"><span data-stu-id="39724-199">This class is only used by the Add-Type cmdlet and should not impact users.</span></span>

### <a name="unify-cmdlets-with-parameter--encoding-to-be-of-type-systemtextencoding-5080httpsgithubcompowershellpowershellissues5080"></a><span data-ttu-id="39724-200">Förena cmdlets med parameter `-Encoding` att vara av typen `System.Text.Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)</span><span class="sxs-lookup"><span data-stu-id="39724-200">Unify cmdlets with parameter `-Encoding` to be of type `System.Text.Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)</span></span>

<span data-ttu-id="39724-201">`-Encoding` värde `Byte` har tagits bort från cmdletarna för fil Systems Provider.</span><span class="sxs-lookup"><span data-stu-id="39724-201">The `-Encoding` value `Byte` has been removed from the filesystem provider cmdlets.</span></span> <span data-ttu-id="39724-202">En ny parameter, `-AsByteStream`, används nu för att ange att en byte-dataström krävs som indata eller att utdata är en data ström i byte.</span><span class="sxs-lookup"><span data-stu-id="39724-202">A new parameter, `-AsByteStream`, is now used to specify that a byte stream is required as input or that the output is a stream of bytes.</span></span>

### <a name="add-better-error-message-for-empty-and-null--uformat-parameter-5055httpsgithubcompowershellpowershellissues5055"></a><span data-ttu-id="39724-203">Lägg till bättre fel meddelande för Tom och null `-UFormat` parameter [#5055](https://github.com/PowerShell/PowerShell/issues/5055)</span><span class="sxs-lookup"><span data-stu-id="39724-203">Add better error message for empty and null `-UFormat` parameter [#5055](https://github.com/PowerShell/PowerShell/issues/5055)</span></span>

<span data-ttu-id="39724-204">När en tom format sträng skulle skickas till `-UFormat`visas ett fel meddelande om att ett fel meddelande visas.</span><span class="sxs-lookup"><span data-stu-id="39724-204">Previously, when passing an empty format string to `-UFormat`, an unhelpful error message would appear.</span></span> <span data-ttu-id="39724-205">Ett mer beskrivande fel har lagts till.</span><span class="sxs-lookup"><span data-stu-id="39724-205">A more descriptive error has been added.</span></span>

### <a name="clean-up-console-code-4995httpsgithubcompowershellpowershellissues4995"></a><span data-ttu-id="39724-206">Rensa konsol kod [#4995](https://github.com/PowerShell/PowerShell/issues/4995)</span><span class="sxs-lookup"><span data-stu-id="39724-206">Clean up console code [#4995](https://github.com/PowerShell/PowerShell/issues/4995)</span></span>

<span data-ttu-id="39724-207">Följande funktioner har tagits bort eftersom de inte stöds i PowerShell Core, och det finns inga planer på att lägga till stöd som de finns för äldre skäl för Windows PowerShell: `-psconsolefile` växel och kod, `-importsystemmodules` växlar och kod och kod för teckensnitts ändring.</span><span class="sxs-lookup"><span data-stu-id="39724-207">The following features were removed as they are not supported in PowerShell Core, and there are no plans to add support as they exist for legacy reasons for Windows PowerShell: `-psconsolefile` switch and code, `-importsystemmodules` switch and code, and font changing code.</span></span>

### <a name="removed-runspaceconfiguration-support-4942httpsgithubcompowershellpowershellissues4942"></a><span data-ttu-id="39724-208">Har tagits bort `RunspaceConfiguration`-support [#4942](https://github.com/PowerShell/PowerShell/issues/4942)</span><span class="sxs-lookup"><span data-stu-id="39724-208">Removed `RunspaceConfiguration` support [#4942](https://github.com/PowerShell/PowerShell/issues/4942)</span></span>

<span data-ttu-id="39724-209">När du tidigare skapade en PowerShell-körnings utrymme via programmering med hjälp av API: et kan du använda den äldre [`RunspaceConfiguration`][runspaceconfig] eller den nyare [`InitialSessionState`][iss].</span><span class="sxs-lookup"><span data-stu-id="39724-209">Previously, when creating a PowerShell runspace programmatically using the API you could use the legacy [`RunspaceConfiguration`][runspaceconfig] or the newer [`InitialSessionState`][iss].</span></span> <span data-ttu-id="39724-210">Den här ändringen tog bort stöd för `RunspaceConfiguration` och stöder bara `InitialSessionState`.</span><span class="sxs-lookup"><span data-stu-id="39724-210">This change removed support for `RunspaceConfiguration` and only supports `InitialSessionState`.</span></span>

[runspaceconfig]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.runspaceconfiguration
[iss]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.initialsessionstate

### <a name="commandinvocationintrinsicsinvokescript-bind-arguments-to-input-instead-of-args-4923httpsgithubcompowershellpowershellissues4923"></a><span data-ttu-id="39724-211">`CommandInvocationIntrinsics.InvokeScript` binda argument till `$input` i stället för `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)</span><span class="sxs-lookup"><span data-stu-id="39724-211">`CommandInvocationIntrinsics.InvokeScript` bind arguments to `$input` instead of `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)</span></span>

<span data-ttu-id="39724-212">En felaktig position av en parameter resulterade i argumenten som angavs som indatamängd i stället för som argument.</span><span class="sxs-lookup"><span data-stu-id="39724-212">An incorrect position of a parameter resulted in the args passed as input instead of as args.</span></span>

### <a name="remove-unsupported--showwindow-switch-from-get-help-4903httpsgithubcompowershellpowershellissues4903"></a><span data-ttu-id="39724-213">Ta bort `-showwindow` växel från `Get-Help` som inte stöds [#4903](https://github.com/PowerShell/PowerShell/issues/4903)</span><span class="sxs-lookup"><span data-stu-id="39724-213">Remove unsupported `-showwindow` switch from `Get-Help` [#4903](https://github.com/PowerShell/PowerShell/issues/4903)</span></span>

<span data-ttu-id="39724-214">`-showwindow` är beroende av WPF, vilket inte stöds på CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="39724-214">`-showwindow` relies on WPF, which is not supported on CoreCLR.</span></span>

### <a name="allow--to-be-used-in-registry-path-for-remove-item-4866httpsgithubcompowershellpowershellissues4866"></a><span data-ttu-id="39724-215">Tillåt att \* används i register Sök väg för `Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866)</span><span class="sxs-lookup"><span data-stu-id="39724-215">Allow \* to be used in registry path for `Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866)</span></span>

<span data-ttu-id="39724-216">Tidigare skulle `-LiteralPath` med ett jokertecken behandla det på samma sätt som `-Path` och om jokertecken inte hittas skulle det leda till tyst slut.</span><span class="sxs-lookup"><span data-stu-id="39724-216">Previously, `-LiteralPath` given a wildcard would treat it the same as `-Path` and if the wildcard found no files, it would silently exit.</span></span> <span data-ttu-id="39724-217">Korrekt beteende bör vara att `-LiteralPath` är Literal så om filen inte finns, bör den innehålla fel.</span><span class="sxs-lookup"><span data-stu-id="39724-217">Correct behavior should be that `-LiteralPath` is literal so if the file doesn't exist, it should error.</span></span> <span data-ttu-id="39724-218">Ändra är att hantera jokertecken som används med `-Literal` som literal.</span><span class="sxs-lookup"><span data-stu-id="39724-218">Change is to treat wildcards used with `-Literal` as literal.</span></span>

### <a name="fix-set-service-failing-test-4802httpsgithubcompowershellpowershellissues4802"></a><span data-ttu-id="39724-219">Korrigera `Set-Service` att testet inte fungerar [#4802](https://github.com/PowerShell/PowerShell/issues/4802)</span><span class="sxs-lookup"><span data-stu-id="39724-219">Fix `Set-Service` failing test [#4802](https://github.com/PowerShell/PowerShell/issues/4802)</span></span>

<span data-ttu-id="39724-220">Tidigare, om `New-Service -StartupType foo` användes, ignorerades `foo` och tjänsten skapades med en typ av standard starttyp.</span><span class="sxs-lookup"><span data-stu-id="39724-220">Previously, if `New-Service -StartupType foo` was used, `foo` was ignored and the service was created with some default startup type.</span></span> <span data-ttu-id="39724-221">Den här ändringen är att explicit utlösa ett fel för en ogiltig starttyp.</span><span class="sxs-lookup"><span data-stu-id="39724-221">This change is to explicitly throw an error for an invalid startup type.</span></span>

### <a name="rename-isosx-to-ismacos-4700httpsgithubcompowershellpowershellissues4700"></a><span data-ttu-id="39724-222">Byt namn på `$IsOSX` till `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)</span><span class="sxs-lookup"><span data-stu-id="39724-222">Rename `$IsOSX` to `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)</span></span>

<span data-ttu-id="39724-223">Namngivningen i PowerShell bör vara konsekvent med vår namn och överensstämmer med Apples användning av macOS i stället för OSX.</span><span class="sxs-lookup"><span data-stu-id="39724-223">The naming in PowerShell should be consistent with our naming and conform to Apple's use of macOS instead of OSX.</span></span> <span data-ttu-id="39724-224">Men för att kunna läsa och ständigt kan vi hålla sig till Pascal-höljet.</span><span class="sxs-lookup"><span data-stu-id="39724-224">However, for readability and consistently we are staying with Pascal casing.</span></span>

### <a name="make-error-message-consistent-when-invalid-script-is-passed-to--file-better-error-when-passed-ambiguous-argument-4573httpsgithubcompowershellpowershellissues4573"></a><span data-ttu-id="39724-225">Gör fel meddelandet konsekvent när ogiltigt skript skickas till fil, vilket är ett bättre fel när ett tvetydigt argument har skickats [#4573](https://github.com/PowerShell/PowerShell/issues/4573)</span><span class="sxs-lookup"><span data-stu-id="39724-225">Make error message consistent when invalid script is passed to -File, better error when passed ambiguous argument [#4573](https://github.com/PowerShell/PowerShell/issues/4573)</span></span>

<span data-ttu-id="39724-226">Ändra avslutnings koderna för `pwsh.exe` så att de överensstämmer med UNIX-konventioner</span><span class="sxs-lookup"><span data-stu-id="39724-226">Change the exit codes of `pwsh.exe` to align with Unix conventions</span></span>

### <a name="removal-of-localaccount-and-cmdlets-from--diagnostics-modules-4302httpsgithubcompowershellpowershellissues4302-4303httpsgithubcompowershellpowershellissues4303"></a><span data-ttu-id="39724-227">Borttagning av `LocalAccount` och cmdlets från `Diagnostics` moduler.</span><span class="sxs-lookup"><span data-stu-id="39724-227">Removal of `LocalAccount` and cmdlets from  `Diagnostics` modules.</span></span> <span data-ttu-id="39724-228">[#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)</span><span class="sxs-lookup"><span data-stu-id="39724-228">[#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)</span></span>

<span data-ttu-id="39724-229">På grund av API: er som inte stöds har `LocalAccounts`-modulen och `Counter`-cmdletar i modulen `Diagnostics` tagits bort tills en bättre lösning har hittats.</span><span class="sxs-lookup"><span data-stu-id="39724-229">Due to unsupported APIs, the `LocalAccounts` module and the `Counter` cmdlets in the `Diagnostics` module were removed until a better solution is found.</span></span>

### <a name="executing-powershell-script-with-bool-parameter-does-not-work-4036httpsgithubcompowershellpowershellissues4036"></a><span data-ttu-id="39724-230">Det går inte att köra PowerShell-skriptet med bool-parametern [#4036](https://github.com/PowerShell/PowerShell/issues/4036)</span><span class="sxs-lookup"><span data-stu-id="39724-230">Executing PowerShell script with bool parameter does not work [#4036](https://github.com/PowerShell/PowerShell/issues/4036)</span></span>

<span data-ttu-id="39724-231">Tidigare använde **PowerShell. exe** (nu **pwsh. exe**) för att köra ett powershell-skript med `-File` angav inget sätt att skicka `$true`/`$false` som parameter värden.</span><span class="sxs-lookup"><span data-stu-id="39724-231">Previously, using **powershell.exe** (now **pwsh.exe**) to execute a PowerShell script using `-File` provided no way to pass `$true`/`$false` as parameter values.</span></span> <span data-ttu-id="39724-232">Stöd för `$true`/`$false` som parsade värden till parametrar har lagts till.</span><span class="sxs-lookup"><span data-stu-id="39724-232">Support for `$true`/`$false` as parsed values to parameters was added.</span></span> <span data-ttu-id="39724-233">Växlings värden stöds också som för närvarande dokumenterad syntax fungerar inte.</span><span class="sxs-lookup"><span data-stu-id="39724-233">Switch values are also supported as currently documented syntax doesn't work.</span></span>

### <a name="remove-clrversion-property-from-psversiontable-4027httpsgithubcompowershellpowershellissues4027"></a><span data-ttu-id="39724-234">Ta bort `ClrVersion` egenskap från `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)</span><span class="sxs-lookup"><span data-stu-id="39724-234">Remove `ClrVersion` property from `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)</span></span>

<span data-ttu-id="39724-235">Egenskapen `ClrVersion` för `$PSVersionTable` är inte användbar med CoreCLR, slutanvändare ska inte använda det värdet för att fastställa kompatibiliteten.</span><span class="sxs-lookup"><span data-stu-id="39724-235">The `ClrVersion` property of `$PSVersionTable` is not useful with CoreCLR, end users should not be using that value to determine compatibility.</span></span>

### <a name="change-positional-parameter-for-powershellexe-from--command-to--file-4019httpsgithubcompowershellpowershellissues4019"></a><span data-ttu-id="39724-236">Ändra positions parameter för `powershell.exe` från `-Command` till `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)</span><span class="sxs-lookup"><span data-stu-id="39724-236">Change positional parameter for `powershell.exe` from `-Command` to `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)</span></span>

<span data-ttu-id="39724-237">Aktivera Shebang användning av PowerShell på andra plattformar än Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="39724-237">Enable shebang use of PowerShell on non-Windows platforms.</span></span> <span data-ttu-id="39724-238">Det innebär att du kan göra en körbar skript fil som anropar PowerShell automatiskt i stället för att explicit anropa `pwsh`när du använder UNIX-baserade system.</span><span class="sxs-lookup"><span data-stu-id="39724-238">This means on Unix based systems, you can make a script executable that would invoke PowerShell automatically rather than explicitly invoking `pwsh`.</span></span> <span data-ttu-id="39724-239">Det innebär också att du nu kan göra saker som `powershell foo.ps1` eller `powershell fooScript` utan att ange `-File`.</span><span class="sxs-lookup"><span data-stu-id="39724-239">This also means that you can now do things like `powershell foo.ps1` or `powershell fooScript` without specifying `-File`.</span></span> <span data-ttu-id="39724-240">Den här ändringen kräver dock att du uttryckligen anger `-c` eller `-Command` när du försöker göra saker som `powershell.exe Get-Command`.</span><span class="sxs-lookup"><span data-stu-id="39724-240">However, this change now requires that you explicitly specify `-c` or `-Command` when trying to do things like `powershell.exe Get-Command`.</span></span>

### <a name="implement-unicode-escape-parsing-3958httpsgithubcompowershellpowershellissues3958"></a><span data-ttu-id="39724-241">Implementera tolkning av Unicode-Escape [#3958](https://github.com/PowerShell/PowerShell/issues/3958)</span><span class="sxs-lookup"><span data-stu-id="39724-241">Implement Unicode escape parsing [#3958](https://github.com/PowerShell/PowerShell/issues/3958)</span></span>

<span data-ttu-id="39724-242">`` `u####`` eller `` `u{####}`` konverteras till motsvarande Unicode-tecken.</span><span class="sxs-lookup"><span data-stu-id="39724-242">`` `u####`` or `` `u{####}`` is converted to the corresponding Unicode character.</span></span> <span data-ttu-id="39724-243">Om du vill mata ut en literal `` `u``kan du undanta bakticket: ``` ``u```.</span><span class="sxs-lookup"><span data-stu-id="39724-243">To output a literal `` `u``, escape the backtick: ``` ``u```.</span></span>

### <a name="change-new-modulemanifest-encoding-to-utf8nobom-on-non-windows-platforms-3940httpsgithubcompowershellpowershellissues3940"></a><span data-ttu-id="39724-244">Ändra `New-ModuleManifest` encoding till `UTF8NoBOM` på andra plattformar än Windows-plattformar [#3940](https://github.com/PowerShell/PowerShell/issues/3940)</span><span class="sxs-lookup"><span data-stu-id="39724-244">Change `New-ModuleManifest` encoding to `UTF8NoBOM` on non-Windows platforms [#3940](https://github.com/PowerShell/PowerShell/issues/3940)</span></span>

<span data-ttu-id="39724-245">Tidigare skapade `New-ModuleManifest` psd1-manifest i UTF-16 med BOM, vilket skapar ett problem för Linux-verktyg.</span><span class="sxs-lookup"><span data-stu-id="39724-245">Previously, `New-ModuleManifest` creates psd1 manifests in UTF-16 with BOM, creating a problem for Linux tools.</span></span> <span data-ttu-id="39724-246">Den här avbrytande ändringen ändrar kodningen för `New-ModuleManifest` till UTF (ingen BOM) på andra plattformar än Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="39724-246">This breaking change changes the encoding of `New-ModuleManifest` to be UTF (no BOM) in non-Windows platforms.</span></span>

### <a name="prevent-get-childitem-from-recursing-into-symlinks-1875-3780httpsgithubcompowershellpowershellissues3780"></a><span data-ttu-id="39724-247">Förhindra att `Get-ChildItem` återkommer till symlinks (#1875).</span><span class="sxs-lookup"><span data-stu-id="39724-247">Prevent `Get-ChildItem` from recursing into symlinks (#1875).</span></span> [<span data-ttu-id="39724-248">#3780</span><span class="sxs-lookup"><span data-stu-id="39724-248">#3780</span></span>](https://github.com/PowerShell/PowerShell/issues/3780)

<span data-ttu-id="39724-249">Den här ändringen ger `Get-ChildItem` mer i rad med UNIX-`ls -r` och inbyggda Windows `dir /s`-kommandon.</span><span class="sxs-lookup"><span data-stu-id="39724-249">This change brings `Get-ChildItem` more in line with the Unix `ls -r` and the Windows `dir /s` native commands.</span></span> <span data-ttu-id="39724-250">Precis som de nämnda kommandona visar cmdleten symboliska länkar till kataloger som hittades under rekursion, men rekursivt inte in dem.</span><span class="sxs-lookup"><span data-stu-id="39724-250">Like the mentioned commands, the cmdlet displays symbolic links to directories found during recursion, but does not recurse into them.</span></span>

### <a name="fix-get-content--delimiter-to-not-include-the-delimiter-in-the-returned-lines-3706httpsgithubcompowershellpowershellissues3706"></a><span data-ttu-id="39724-251">Korrigera `Get-Content -Delimiter` att inte inkludera avgränsaren i de returnerade raderna [#3706](https://github.com/PowerShell/PowerShell/issues/3706)</span><span class="sxs-lookup"><span data-stu-id="39724-251">Fix `Get-Content -Delimiter` to not include the delimiter in the returned lines [#3706](https://github.com/PowerShell/PowerShell/issues/3706)</span></span>

<span data-ttu-id="39724-252">Tidigare var de utdata som användes när du använde `Get-Content -Delimiter` inkonsekventa och praktiska eftersom det krävde ytterligare bearbetning av data för att ta bort avgränsaren.</span><span class="sxs-lookup"><span data-stu-id="39724-252">Previously, the output while using `Get-Content -Delimiter` was inconsistent and inconvenient as it required further processing of the data to remove the delimiter.</span></span> <span data-ttu-id="39724-253">Den här ändringen tar bort avgränsaren i returnerade rader.</span><span class="sxs-lookup"><span data-stu-id="39724-253">This change removes the delimiter in returned lines.</span></span>

### <a name="implement-format-hex-in-c-3320httpsgithubcompowershellpowershellissues3320"></a><span data-ttu-id="39724-254">Implementera format-hex i C# [#3320](https://github.com/PowerShell/PowerShell/issues/3320)</span><span class="sxs-lookup"><span data-stu-id="39724-254">Implement Format-Hex in C# [#3320](https://github.com/PowerShell/PowerShell/issues/3320)</span></span>

<span data-ttu-id="39724-255">Parametern `-Raw` är nu "No-OP" (i så fall inget).</span><span class="sxs-lookup"><span data-stu-id="39724-255">The `-Raw` parameter is now a "no-op" (in that it does nothing).</span></span> <span data-ttu-id="39724-256">Om du fortsätter kommer alla utdata att visas med en sann representation av siffror som innehåller alla byte för dess typ (vilken `-Raw` parameter utfördes innan ändringen).</span><span class="sxs-lookup"><span data-stu-id="39724-256">Going forward all of the output will be displayed with a true representation of numbers that includes all of the bytes for its type (what the `-Raw` parameter was formally doing prior to this change).</span></span>

### <a name="powershell-as-a-default-shell-doesnt-work-with-script-command-3319httpsgithubcompowershellpowershellissues3319"></a><span data-ttu-id="39724-257">PowerShell som standard gränssnitt fungerar inte med skript kommandot [#3319](https://github.com/PowerShell/PowerShell/issues/3319)</span><span class="sxs-lookup"><span data-stu-id="39724-257">PowerShell as a default shell doesn't work with script command [#3319](https://github.com/PowerShell/PowerShell/issues/3319)</span></span>

<span data-ttu-id="39724-258">I UNIX är det en konvention för gränssnitt att acceptera `-i` för ett interaktivt gränssnitt och många verktyg förväntar sig detta beteende (`script` till exempel och när du ställer in PowerShell som standard gränssnitt) och anropar gränssnittet med `-i`-växeln.</span><span class="sxs-lookup"><span data-stu-id="39724-258">On Unix, it is a convention for shells to accept `-i` for an interactive shell and many tools expect this behavior (`script` for example, and when setting PowerShell as the default shell) and calls the shell with the `-i` switch.</span></span> <span data-ttu-id="39724-259">Den här ändringen delas upp i `-i` tidigare kunde användas som kort hand för att matcha `-inputformat`som nu måste vara `-in`.</span><span class="sxs-lookup"><span data-stu-id="39724-259">This change is breaking in that `-i` previously could be used as short hand to match `-inputformat`, which now needs to be `-in`.</span></span>

### <a name="typo-fix-in-get-computerinfo-property-name-3167httpsgithubcompowershellpowershellissues3167"></a><span data-ttu-id="39724-260">Skriv åtgärd i get-ComputerInfo egenskaps namn [#3167](https://github.com/PowerShell/PowerShell/issues/3167)</span><span class="sxs-lookup"><span data-stu-id="39724-260">Typo fix in Get-ComputerInfo property name [#3167](https://github.com/PowerShell/PowerShell/issues/3167)</span></span>

<span data-ttu-id="39724-261">`BiosSerialNumber` skrevs felstavat som `BiosSeralNumber` och har ändrats till rätt stavning.</span><span class="sxs-lookup"><span data-stu-id="39724-261">`BiosSerialNumber` was misspelled as `BiosSeralNumber` and has been changed to the correct spelling.</span></span>

### <a name="add-get-stringhash-and-get-filehash-cmdlets-3024httpsgithubcompowershellpowershellissues3024"></a><span data-ttu-id="39724-262">Lägg till `Get-StringHash`-och `Get-FileHash`-cmdletar [#3024](https://github.com/PowerShell/PowerShell/issues/3024)</span><span class="sxs-lookup"><span data-stu-id="39724-262">Add `Get-StringHash` and `Get-FileHash` cmdlets [#3024](https://github.com/PowerShell/PowerShell/issues/3024)</span></span>

<span data-ttu-id="39724-263">Den här ändringen är att vissa hash-algoritmer inte stöds av CoreFX, vilket innebär att de inte längre är tillgängliga:</span><span class="sxs-lookup"><span data-stu-id="39724-263">This change is that some hash algorithms are not supported by CoreFX, therefore they are no longer available:</span></span>

- `MACTripleDES`
- `RIPEMD160`

### <a name="add-validation-on-get--cmdlets-where-passing-null-returns-all-objects-instead-of-error-2672httpsgithubcompowershellpowershellissues2672"></a><span data-ttu-id="39724-264">Lägg till verifiering på `Get-*`-cmdletar där skicka $null returnerar alla objekt i stället för fel [#2672](https://github.com/PowerShell/PowerShell/issues/2672)</span><span class="sxs-lookup"><span data-stu-id="39724-264">Add validation on `Get-*` cmdlets where passing $null returns all objects instead of error [#2672](https://github.com/PowerShell/PowerShell/issues/2672)</span></span>

<span data-ttu-id="39724-265">Att skicka `$null` till något av följande genererar nu ett fel:</span><span class="sxs-lookup"><span data-stu-id="39724-265">Passing `$null` to any of the following now throws an error:</span></span>

- `Get-Credential -UserName`
- `Get-Event -SourceIdentifier`
- `Get-EventSubscriber -SourceIdentifier`
- `Get-Help -Name`
- `Get-PSBreakpoint -Script`
- `Get-PSProvider -PSProvider`
- `Get-PSSessionConfiguration -Name`
- `Get-PSSnapin -Name`
- `Get-Runspace -Name`
- `Get-RunspaceDebug -RunspaceName`
- `Get-Service -Name`
- `Get-TraceSource -Name`
- `Get-Variable -Name`
- `Get-WmiObject -Class`
- `Get-WmiObject -Property`

### <a name="add-support-w3c-extended-log-file-format-in-import-csv-2482httpsgithubcompowershellpowershellissues2482"></a><span data-ttu-id="39724-266">Lägg till stöd för utökat logg fils format för W3C i `Import-Csv` [#2482](https://github.com/PowerShell/PowerShell/issues/2482)</span><span class="sxs-lookup"><span data-stu-id="39724-266">Add support W3C Extended Log File Format in `Import-Csv` [#2482](https://github.com/PowerShell/PowerShell/issues/2482)</span></span>

<span data-ttu-id="39724-267">Tidigare kan `Import-Csv`-cmdleten inte användas för att importera loggfilerna direkt i utökat logg format för W3C och ytterligare åtgärder krävs.</span><span class="sxs-lookup"><span data-stu-id="39724-267">Previously, the `Import-Csv` cmdlet cannot be used to directly import the log files in W3C extended log format and additional action would be required.</span></span> <span data-ttu-id="39724-268">Med den här ändringen stöds W3C Extended Log-formatet.</span><span class="sxs-lookup"><span data-stu-id="39724-268">With this change, W3C extended log format is supported.</span></span>

### <a name="parameter-binding-problem-with-valuefromremainingarguments-in-ps-functions-2035httpsgithubcompowershellpowershellissues2035"></a><span data-ttu-id="39724-269">Parameter bindnings problem med `ValueFromRemainingArguments` i PS-funktioner [#2035](https://github.com/PowerShell/PowerShell/issues/2035)</span><span class="sxs-lookup"><span data-stu-id="39724-269">Parameter binding problem with `ValueFromRemainingArguments` in PS functions [#2035](https://github.com/PowerShell/PowerShell/issues/2035)</span></span>

<span data-ttu-id="39724-270">`ValueFromRemainingArguments` returnerar nu värdena som en matris i stället för ett enda värde som är en matris.</span><span class="sxs-lookup"><span data-stu-id="39724-270">`ValueFromRemainingArguments` now returns the values as an array instead of a single value which itself is an array.</span></span>

### <a name="buildversion-is-removed-from-psversiontable-1415httpsgithubcompowershellpowershellissues1415"></a><span data-ttu-id="39724-271">`BuildVersion` tas bort från `$PSVersionTable` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)</span><span class="sxs-lookup"><span data-stu-id="39724-271">`BuildVersion` is removed from `$PSVersionTable` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)</span></span>

<span data-ttu-id="39724-272">Ta bort egenskapen `BuildVersion` från `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="39724-272">Remove the `BuildVersion` property from `$PSVersionTable`.</span></span> <span data-ttu-id="39724-273">Den här egenskapen är kopplad till Windows build-versionen.</span><span class="sxs-lookup"><span data-stu-id="39724-273">This property was tied to the Windows build version.</span></span> <span data-ttu-id="39724-274">I stället rekommenderar vi att du använder `GitCommitId` för att hämta den exakta versionen av PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="39724-274">Instead, we recommend that you use `GitCommitId` to retrieve the exact build version of PowerShell Core.</span></span>

### <a name="changes-to-web-cmdlets"></a><span data-ttu-id="39724-275">Ändringar av webb-cmdletar</span><span class="sxs-lookup"><span data-stu-id="39724-275">Changes to Web Cmdlets</span></span>

<span data-ttu-id="39724-276">De underliggande .NET API: erna för webb-cmdletar har ändrats till `System.Net.Http.HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="39724-276">The underlying .NET API of the Web Cmdlets has been changed to `System.Net.Http.HttpClient`.</span></span> <span data-ttu-id="39724-277">Den här ändringen ger många fördelar.</span><span class="sxs-lookup"><span data-stu-id="39724-277">This change provides many benefits.</span></span> <span data-ttu-id="39724-278">Men den här ändringen tillsammans med en brist på interoperabilitet med Internet Explorer har resulterat i flera större ändringar i `Invoke-WebRequest` och `Invoke-RestMethod`.</span><span class="sxs-lookup"><span data-stu-id="39724-278">However, this change along with a lack of interoperability with Internet Explorer have resulted in several breaking changes within `Invoke-WebRequest` and `Invoke-RestMethod`.</span></span>

- <span data-ttu-id="39724-279">`Invoke-WebRequest` stöder nu endast grundläggande HTML-parsning.</span><span class="sxs-lookup"><span data-stu-id="39724-279">`Invoke-WebRequest` now supports basic HTML Parsing only.</span></span> <span data-ttu-id="39724-280">`Invoke-WebRequest` returnerar alltid ett `BasicHtmlWebResponseObject`-objekt.</span><span class="sxs-lookup"><span data-stu-id="39724-280">`Invoke-WebRequest` always returns a `BasicHtmlWebResponseObject` object.</span></span> <span data-ttu-id="39724-281">Egenskaperna för `ParsedHtml` och `Forms` har tagits bort.</span><span class="sxs-lookup"><span data-stu-id="39724-281">The `ParsedHtml` and `Forms` properties have been removed.</span></span>
- <span data-ttu-id="39724-282">`BasicHtmlWebResponseObject.Headers` värden är nu `String[]` i stället för `String`.</span><span class="sxs-lookup"><span data-stu-id="39724-282">`BasicHtmlWebResponseObject.Headers` values are now `String[]` instead of `String`.</span></span>
- <span data-ttu-id="39724-283">`BasicHtmlWebResponseObject.BaseResponse` är nu ett `System.Net.Http.HttpResponseMessage`-objekt.</span><span class="sxs-lookup"><span data-stu-id="39724-283">`BasicHtmlWebResponseObject.BaseResponse` is now a `System.Net.Http.HttpResponseMessage` object.</span></span>
- <span data-ttu-id="39724-284">Egenskapen `Response` i Web cmdlet-undantag är nu ett `System.Net.Http.HttpResponseMessage` objekt.</span><span class="sxs-lookup"><span data-stu-id="39724-284">The `Response` property on Web Cmdlet exceptions is now a `System.Net.Http.HttpResponseMessage` object.</span></span>
- <span data-ttu-id="39724-285">Strikt rubrik tolkning för RFC är nu standard för `-Headers` och `-UserAgent` parameter.</span><span class="sxs-lookup"><span data-stu-id="39724-285">Strict RFC header parsing is now default for the `-Headers` and `-UserAgent` parameter.</span></span> <span data-ttu-id="39724-286">Detta kan kringgås med `-SkipHeaderValidation`.</span><span class="sxs-lookup"><span data-stu-id="39724-286">This can be bypassed with `-SkipHeaderValidation`.</span></span>
- <span data-ttu-id="39724-287">`file://`-och `ftp://`-URI-scheman stöds inte längre.</span><span class="sxs-lookup"><span data-stu-id="39724-287">`file://` and `ftp://` URI schemes are no longer supported.</span></span>
- <span data-ttu-id="39724-288">`System.Net.ServicePointManager` inställningar inte längre används.</span><span class="sxs-lookup"><span data-stu-id="39724-288">`System.Net.ServicePointManager` settings are no longer honored.</span></span>
- <span data-ttu-id="39724-289">Det finns för närvarande ingen certifikatbaserad autentisering tillgänglig på macOS.</span><span class="sxs-lookup"><span data-stu-id="39724-289">There is currently no certificate based authentication available on macOS.</span></span>
- <span data-ttu-id="39724-290">Om du använder `-Credential` över en `http://` URI resulterar det i ett fel.</span><span class="sxs-lookup"><span data-stu-id="39724-290">Use of `-Credential` over an `http://` URI will result in an error.</span></span> <span data-ttu-id="39724-291">Använd en `https://`-URI eller ange parametern `-AllowUnencryptedAuthentication` för att ignorera felet.</span><span class="sxs-lookup"><span data-stu-id="39724-291">Use an `https://` URI or supply the `-AllowUnencryptedAuthentication` parameter to suppress the error.</span></span>
- <span data-ttu-id="39724-292">`-MaximumRedirection` skapar nu ett avslutande fel när omdirigerings försöken överskrider den angivna gränsen i stället för att returnera resultatet av den senaste omdirigeringen.</span><span class="sxs-lookup"><span data-stu-id="39724-292">`-MaximumRedirection` now produces a terminating error when redirection attempts exceed the provided limit instead of returning the results of the last redirection.</span></span>
- <span data-ttu-id="39724-293">I PowerShell 6,2 gjordes en ändring som standard till UTF-8-kodning för JSON-svar.</span><span class="sxs-lookup"><span data-stu-id="39724-293">In PowerShell 6.2, a change was made to default to UTF-8 encoding for JSON responses.</span></span> <span data-ttu-id="39724-294">Om ingen teckenuppsättning anges för ett JSON-svar ska standard kodningen vara UTF-8 per RFC 8259.</span><span class="sxs-lookup"><span data-stu-id="39724-294">When a charset is not supplied for a JSON response, the default encoding should be UTF-8 per RFC 8259.</span></span>
