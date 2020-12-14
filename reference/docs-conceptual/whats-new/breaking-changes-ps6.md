---
ms.date: 02/03/2020
keywords: PowerShell, Core
title: Bryta ändringar för PowerShell 6,0
description: Den här artikeln sammanfattar skillnaderna mellan Windows PowerShell 5,1 och PowerShell 6,0.
ms.openlocfilehash: b53365ee72e6a6e85faa56125a8aa7961d3ecc7f
ms.sourcegitcommit: f9d855dd73b916559a22e337672dea3fbb11c634
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/07/2020
ms.locfileid: "96840139"
---
# <a name="breaking-changes-for-powershell-6x"></a><span data-ttu-id="f8628-104">Bryta ändringar för PowerShell 6. x</span><span class="sxs-lookup"><span data-stu-id="f8628-104">Breaking Changes for PowerShell 6.x</span></span>

## <a name="features-no-longer-available-in-powershell-core"></a><span data-ttu-id="f8628-105">Funktioner som inte längre är tillgängliga i PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="f8628-105">Features no longer available in PowerShell Core</span></span>

### <a name="modules-not-shipped-for-powershell-6x"></a><span data-ttu-id="f8628-106">Moduler som inte levererats för PowerShell 6. x</span><span class="sxs-lookup"><span data-stu-id="f8628-106">Modules not shipped for PowerShell 6.x</span></span>

<span data-ttu-id="f8628-107">För olika kompatibilitetsproblem ingår inte följande moduler i PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="f8628-107">For various compatibility reasons, the following modules are not included in PowerShell 6.</span></span>

- <span data-ttu-id="f8628-108">ISE</span><span class="sxs-lookup"><span data-stu-id="f8628-108">ISE</span></span>
- <span data-ttu-id="f8628-109">Microsoft. PowerShell. LocalAccounts</span><span class="sxs-lookup"><span data-stu-id="f8628-109">Microsoft.PowerShell.LocalAccounts</span></span>
- <span data-ttu-id="f8628-110">Microsoft. PowerShell. ODataUtils</span><span class="sxs-lookup"><span data-stu-id="f8628-110">Microsoft.PowerShell.ODataUtils</span></span>
- <span data-ttu-id="f8628-111">Microsoft. PowerShell. operation. Validation</span><span class="sxs-lookup"><span data-stu-id="f8628-111">Microsoft.PowerShell.Operation.Validation</span></span>
- <span data-ttu-id="f8628-112">PSScheduledJob</span><span class="sxs-lookup"><span data-stu-id="f8628-112">PSScheduledJob</span></span>
- <span data-ttu-id="f8628-113">PSWorkflow</span><span class="sxs-lookup"><span data-stu-id="f8628-113">PSWorkflow</span></span>
- <span data-ttu-id="f8628-114">PSWorkflowUtility</span><span class="sxs-lookup"><span data-stu-id="f8628-114">PSWorkflowUtility</span></span>

### <a name="powershell-workflow"></a><span data-ttu-id="f8628-115">PowerShell-arbetsflöde</span><span class="sxs-lookup"><span data-stu-id="f8628-115">PowerShell Workflow</span></span>

<span data-ttu-id="f8628-116">[PowerShell-arbetsflöde][workflow] är en funktion i Windows PowerShell som bygger ovanpå [Windows Workflow Foundation (WF)][workflow-foundation] som gör det möjligt att skapa robusta Runbooks för långvariga eller parallella uppgifter.</span><span class="sxs-lookup"><span data-stu-id="f8628-116">[PowerShell Workflow][workflow] is a feature in Windows PowerShell that builds on top of [Windows Workflow Foundation (WF)][workflow-foundation] that enables the creation of robust runbooks for long-running or parallelized tasks.</span></span>

<span data-ttu-id="f8628-117">På grund av brist på stöd för Windows Workflow Foundation i .NET Core stöder vi inte PowerShell-arbetsflöde i PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="f8628-117">Due to the lack of support for Windows Workflow Foundation in .NET Core, we are not supporting PowerShell Workflow in PowerShell Core.</span></span>

<span data-ttu-id="f8628-118">I framtiden skulle vi vilja aktivera inbyggd parallellitet/samtidighet i PowerShell-språket utan att behöva använda PowerShell-arbetsflöde.</span><span class="sxs-lookup"><span data-stu-id="f8628-118">In the future, we would like to enable native parallelism/concurrency in the PowerShell language without the need for PowerShell Workflow.</span></span>

<span data-ttu-id="f8628-119">Om du behöver använda kontroll punkter för att återuppta ett skript efter det att operativ systemet har startats om, rekommenderar vi att du använder Schemaläggaren för att köra ett skript på Start av operativ systemet, men skriptet måste ha ett eget tillstånd (som att spara det i en fil).</span><span class="sxs-lookup"><span data-stu-id="f8628-119">If there is a need to use checkpoints to resume a script after the OS restarts, we recommend using Task Scheduler to run a script on OS startup, but the script would need to maintain its own state (like persisting it to a file).</span></span>

[workflow]: /previous-versions/powershell/scripting/components/workflows-guide
[workflow-foundation]: /dotnet/framework/windows-workflow-foundation/

### <a name="custom-snap-ins"></a><span data-ttu-id="f8628-120">Anpassade snapin-moduler</span><span class="sxs-lookup"><span data-stu-id="f8628-120">Custom snap-ins</span></span>

<span data-ttu-id="f8628-121">[PowerShell-snapin-moduler][snapin] är en föregående aktivitet till PowerShell-moduler som inte har omfattande antagande i PowerShell-communityn.</span><span class="sxs-lookup"><span data-stu-id="f8628-121">[PowerShell snap-ins][snapin] are a predecessor to PowerShell modules that do not have widespread adoption in the PowerShell community.</span></span>

<span data-ttu-id="f8628-122">På grund av komplexiteten vid stöd för snapin-moduler och deras brist på användning i communityn stöder vi inte längre anpassade snapin-moduler i PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="f8628-122">Due to the complexity of supporting snap-ins and their lack of usage in the community, we no longer support custom snap-ins in PowerShell Core.</span></span>

<span data-ttu-id="f8628-123">Idag tar detta upp `ActiveDirectory` och `DnsClient` moduler i Windows och Windows Server.</span><span class="sxs-lookup"><span data-stu-id="f8628-123">Today, this breaks the `ActiveDirectory` and `DnsClient` modules in Windows and Windows Server.</span></span>

[snapin]: /powershell/module/microsoft.powershell.core/about/about_pssnapins

### <a name="wmi-v1-cmdlets"></a><span data-ttu-id="f8628-124">WMI v1-cmdletar</span><span class="sxs-lookup"><span data-stu-id="f8628-124">WMI v1 cmdlets</span></span>

<span data-ttu-id="f8628-125">På grund av komplexiteten med stöd för två uppsättningar WMI-baserade moduler tog vi bort WMI v1-cmdletar från PowerShell Core:</span><span class="sxs-lookup"><span data-stu-id="f8628-125">Due to the complexity of supporting two sets of WMI-based modules, we removed the WMI v1 cmdlets from PowerShell Core:</span></span>

- `Register-WmiEvent`
- `Set-WmiInstance`
- `Invoke-WmiMethod`
- `Get-WmiObject`
- `Remove-WmiObject`

<span data-ttu-id="f8628-126">I stället rekommenderar vi att du använder CIM-cmdletarna (aka WMI v2) som tillhandahåller samma funktioner med nya funktioner och en omdesignad syntax:</span><span class="sxs-lookup"><span data-stu-id="f8628-126">Instead, we recommend that you the use the CIM (aka WMI v2) cmdlets which provide the same functionality with new functionality and a redesigned syntax:</span></span>

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

### <a name="microsoftpowershelllocalaccounts"></a><span data-ttu-id="f8628-127">Microsoft. PowerShell. LocalAccounts</span><span class="sxs-lookup"><span data-stu-id="f8628-127">Microsoft.PowerShell.LocalAccounts</span></span>

<span data-ttu-id="f8628-128">På grund av användning av API: er som inte stöds, `Microsoft.PowerShell.LocalAccounts` har tagits bort från PowerShell Core tills en bättre lösning har hittats.</span><span class="sxs-lookup"><span data-stu-id="f8628-128">Due to the use of unsupported APIs, `Microsoft.PowerShell.LocalAccounts` has been removed from PowerShell Core until a better solution is found.</span></span>

### <a name="new-webserviceproxy-cmdlet-removed"></a><span data-ttu-id="f8628-129">`New-WebServiceProxy` cmdlet borttagen</span><span class="sxs-lookup"><span data-stu-id="f8628-129">`New-WebServiceProxy` cmdlet removed</span></span>

<span data-ttu-id="f8628-130">.NET Core har inte stöd för Windows Communication Framework, som tillhandahåller tjänster för att använda SOAP-protokollet.</span><span class="sxs-lookup"><span data-stu-id="f8628-130">.NET Core does not support the Windows Communication Framework, which provide services for using the SOAP protocol.</span></span> <span data-ttu-id="f8628-131">Den här cmdleten togs bort eftersom den kräver SOAP.</span><span class="sxs-lookup"><span data-stu-id="f8628-131">This cmdlet was removed because it requires SOAP.</span></span>

### <a name="-transaction-cmdlets-removed"></a><span data-ttu-id="f8628-132">`*-Transaction` cmdletar har tagits bort</span><span class="sxs-lookup"><span data-stu-id="f8628-132">`*-Transaction` cmdlets removed</span></span>

<span data-ttu-id="f8628-133">Dessa cmdletar hade mycket begränsad användning.</span><span class="sxs-lookup"><span data-stu-id="f8628-133">These cmdlets had very limited usage.</span></span> <span data-ttu-id="f8628-134">Beslutet har fattats för att avbryta stödet för dem.</span><span class="sxs-lookup"><span data-stu-id="f8628-134">The decision was made to discontinue support for them.</span></span>

- `Complete-Transaction`
- `Get-Transaction`
- `Start-Transaction`
- `Undo-Transaction`
- `Use-Transaction`

### <a name="security-cmdlets-not-available-on-non-windows-platforms"></a><span data-ttu-id="f8628-135">Säkerhets-cmdletar är inte tillgängliga på plattformar som inte är Windows-plattformar</span><span class="sxs-lookup"><span data-stu-id="f8628-135">Security cmdlets not available on non-Windows platforms</span></span>

- `Get-Acl`
- `Set-Acl`
- `Get-AuthenticodeSignature`
- `Set-AuthenticodeSignature`
- `Get-CmsMessage`
- `Protect-CmsMessage`
- `Unprotect-CmsMessage`
- `New-FileCatalog`
- `Test-FileCatalog`

### <a name="-computerand-other-windows-specific-cmdlets"></a><span data-ttu-id="f8628-136">`*-Computer`och andra Windows-Specific-cmdletar</span><span class="sxs-lookup"><span data-stu-id="f8628-136">`*-Computer`and other Windows-specific cmdlets</span></span>

<span data-ttu-id="f8628-137">På grund av användning av API: er som inte stöds har följande cmdlets tagits bort från PowerShell Core tills en bättre lösning har hittats.</span><span class="sxs-lookup"><span data-stu-id="f8628-137">Due to the use of unsupported APIs, the following cmdlets have been removed from PowerShell Core until a better solution is found.</span></span>

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

### <a name="-counter-cmdlets"></a><span data-ttu-id="f8628-138">`*-Counter` cmdletar</span><span class="sxs-lookup"><span data-stu-id="f8628-138">`*-Counter` cmdlets</span></span>

<span data-ttu-id="f8628-139">På grund av användning av API: er som inte stöds, `*-Counter` har tagits bort från PowerShell Core tills en bättre lösning har hittats.</span><span class="sxs-lookup"><span data-stu-id="f8628-139">Due to the use of unsupported APIs, the `*-Counter` has been removed from PowerShell Core until a better solution is found.</span></span>

### <a name="-eventlog-cmdlets"></a><span data-ttu-id="f8628-140">`*-EventLog` cmdletar</span><span class="sxs-lookup"><span data-stu-id="f8628-140">`*-EventLog` cmdlets</span></span>

<span data-ttu-id="f8628-141">På grund av användning av API: er som inte stöds, `*-EventLog` har tagits bort från PowerShell-kärnan.</span><span class="sxs-lookup"><span data-stu-id="f8628-141">Due to the use of unsupported APIs, the `*-EventLog` has been removed from PowerShell Core.</span></span> <span data-ttu-id="f8628-142">tills en bättre lösning har hittats.</span><span class="sxs-lookup"><span data-stu-id="f8628-142">until a better solution is found.</span></span> <span data-ttu-id="f8628-143">`Get-WinEvent` och `New-WinEvent` är tillgängliga för att hämta och skapa händelser i Windows.</span><span class="sxs-lookup"><span data-stu-id="f8628-143">`Get-WinEvent` and `New-WinEvent` are available to get and create events on Windows.</span></span>

### <a name="cmdlets-that-use-wpf-removed"></a><span data-ttu-id="f8628-144">Cmdletar som använder WPF borttagna</span><span class="sxs-lookup"><span data-stu-id="f8628-144">Cmdlets that use WPF removed</span></span>

<span data-ttu-id="f8628-145">Windows Presentation Framework stöds inte på CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="f8628-145">The Windows Presentation Framework is not supported on CoreCLR.</span></span> <span data-ttu-id="f8628-146">Följande cmdletar påverkas:</span><span class="sxs-lookup"><span data-stu-id="f8628-146">The following cmdlets are affected:</span></span>

- `Show-Command`
- `Out-GridView`
- <span data-ttu-id="f8628-147">Parametern **ShowWindow** för `Get-Help`</span><span class="sxs-lookup"><span data-stu-id="f8628-147">The **showwindow** parameter of `Get-Help`</span></span>

### <a name="some-dsc-cmdlets-removed"></a><span data-ttu-id="f8628-148">Vissa DSC-cmdletar har tagits bort</span><span class="sxs-lookup"><span data-stu-id="f8628-148">Some DSC cmdlets removed</span></span>

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

## <a name="enginelanguage-changes"></a><span data-ttu-id="f8628-149">Motor/språk ändringar</span><span class="sxs-lookup"><span data-stu-id="f8628-149">Engine/language changes</span></span>

### <a name="rename-powershellexe-to-pwshexe-5101"></a><span data-ttu-id="f8628-150">Byt namn `powershell.exe` till `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)</span><span class="sxs-lookup"><span data-stu-id="f8628-150">Rename `powershell.exe` to `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)</span></span>

<span data-ttu-id="f8628-151">För att ge användarna ett deterministiskt sätt att anropa PowerShell Core på Windows (till skillnad från Windows PowerShell) ändrades binärfilen för PowerShell-kärnan till `pwsh.exe` i Windows och `pwsh` på andra plattformar än Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="f8628-151">In order to give users a deterministic way to call PowerShell Core on Windows (as opposed to Windows PowerShell), the PowerShell Core binary was changed to `pwsh.exe` on Windows and `pwsh` on non-Windows platforms.</span></span>

<span data-ttu-id="f8628-152">Det förkortade namnet är också konsekvent med namngivning av gränssnitt på andra plattformar än Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="f8628-152">The shortened name is also consistent with naming of shells on non-Windows platforms.</span></span>

### <a name="dont-insert-line-breaks-to-output-except-for-tables-5193"></a><span data-ttu-id="f8628-153">Infoga inte rad brytningar i utdata (förutom tabeller) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)</span><span class="sxs-lookup"><span data-stu-id="f8628-153">Don't insert line breaks to output (except for tables) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)</span></span>

<span data-ttu-id="f8628-154">Tidigare var utdata justerade till bredden på konsolen och rad brytningarna lades till i konsolens slut punkt, vilket innebär att resultatet inte blev omformaterat som förväntat om terminalfönstret ändrades.</span><span class="sxs-lookup"><span data-stu-id="f8628-154">Previously, output was aligned to the width of the console and line breaks were added at the end width of the console, meaning the output didn't get reformatted as expected if the terminal was resized.</span></span> <span data-ttu-id="f8628-155">Den här ändringen tillämpades inte i tabeller eftersom rad brytningar krävs för att hålla kolumnerna justerade.</span><span class="sxs-lookup"><span data-stu-id="f8628-155">This change was not applied to tables, as the line breaks are necessary to keep the columns aligned.</span></span>

### <a name="skip-null-element-check-for-collections-with-a-value-type-element-type-5432"></a><span data-ttu-id="f8628-156">Hoppa över null-Elements kontroll för samlingar med en värde typs element typ [#5432](https://github.com/PowerShell/PowerShell/issues/5432)</span><span class="sxs-lookup"><span data-stu-id="f8628-156">Skip null-element check for collections with a value-type element type [#5432](https://github.com/PowerShell/PowerShell/issues/5432)</span></span>

<span data-ttu-id="f8628-157">`Mandatory` `ValidateNotNull` `ValidateNotNullOrEmpty` Hoppa över null-elementet för parametern och attributen om samlingens element typ är värdetyp.</span><span class="sxs-lookup"><span data-stu-id="f8628-157">For the `Mandatory` parameter and `ValidateNotNull` and `ValidateNotNullOrEmpty` attributes, skip the null-element check if the collection's element type is value type.</span></span>

### <a name="change-outputencoding-to-use-utf-8-nobom-encoding-rather-than-ascii-5369"></a><span data-ttu-id="f8628-158">Ändra `$OutputEncoding` till att använda `UTF-8 NoBOM` encoding i stället för ASCII [#5369](https://github.com/PowerShell/PowerShell/issues/5369)</span><span class="sxs-lookup"><span data-stu-id="f8628-158">Change `$OutputEncoding` to use `UTF-8 NoBOM` encoding rather than ASCII [#5369](https://github.com/PowerShell/PowerShell/issues/5369)</span></span>

<span data-ttu-id="f8628-159">Föregående kodning, ASCII (7-bitars), resulterar i en felaktig ändring av utdata i vissa fall.</span><span class="sxs-lookup"><span data-stu-id="f8628-159">The previous encoding, ASCII (7-bit), would result in incorrect alteration of the output in some cases.</span></span> <span data-ttu-id="f8628-160">Den här ändringen är att göra `UTF-8 NoBOM` standardvärdet, vilket bevarar Unicode-utdata med en kodning som stöds av de flesta verktyg och operativ system.</span><span class="sxs-lookup"><span data-stu-id="f8628-160">This change is to make `UTF-8 NoBOM` default, which preserves Unicode output with an encoding supported by most tools and operating systems.</span></span>

### <a name="remove-allscope-from-most-default-aliases-5268"></a><span data-ttu-id="f8628-161">Ta bort `AllScope` från de flesta Standardalias [#5268](https://github.com/PowerShell/PowerShell/issues/5268)</span><span class="sxs-lookup"><span data-stu-id="f8628-161">Remove `AllScope` from most default aliases [#5268](https://github.com/PowerShell/PowerShell/issues/5268)</span></span>

<span data-ttu-id="f8628-162">För att påskynda skapandet av omfattningar, `AllScope` har tagits bort från de flesta Standardalias.</span><span class="sxs-lookup"><span data-stu-id="f8628-162">To speed up scope creation, `AllScope` was removed from most default aliases.</span></span> <span data-ttu-id="f8628-163">`AllScope` har lämnats för några ofta använda alias där sökningen var snabbare.</span><span class="sxs-lookup"><span data-stu-id="f8628-163">`AllScope` was left for a few frequently used aliases where the lookup was faster.</span></span>

### <a name="-verbose-and--debug-no-longer-overrides-erroractionpreference-5113"></a><span data-ttu-id="f8628-164">`-Verbose` och `-Debug` åsidosätter inte längre `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)</span><span class="sxs-lookup"><span data-stu-id="f8628-164">`-Verbose` and `-Debug` no longer overrides `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)</span></span>

<span data-ttu-id="f8628-165">Tidigare, om `-Verbose` eller `-Debug` har angetts, overrode beteendet `$ErrorActionPreference` .</span><span class="sxs-lookup"><span data-stu-id="f8628-165">Previously, if `-Verbose` or `-Debug` were specified, it overrode the behavior of `$ErrorActionPreference`.</span></span> <span data-ttu-id="f8628-166">Med den här ändringen `-Verbose` och `-Debug` påverkar inte längre beteendet för `$ErrorActionPreference` .</span><span class="sxs-lookup"><span data-stu-id="f8628-166">With this change, `-Verbose` and `-Debug` no longer affect the behavior of `$ErrorActionPreference`.</span></span>

## <a name="cmdlet-changes"></a><span data-ttu-id="f8628-167">Cmdlet-ändringar</span><span class="sxs-lookup"><span data-stu-id="f8628-167">Cmdlet changes</span></span>

### <a name="invoke-restmethod-doesnt-return-useful-info-when-no-data-is-returned-5320"></a><span data-ttu-id="f8628-168">Invoke-RestMethod returnerar inte värdefull information när inga data returneras.</span><span class="sxs-lookup"><span data-stu-id="f8628-168">Invoke-RestMethod doesn't return useful info when no data is returned.</span></span> [<span data-ttu-id="f8628-169">#5320</span><span class="sxs-lookup"><span data-stu-id="f8628-169">#5320</span></span>](https://github.com/PowerShell/PowerShell/issues/5320)

<span data-ttu-id="f8628-170">När ett API returnerar bara `null` , serialiserade Invoke-RestMethod detta som sträng i `"null"` stället för `$null` .</span><span class="sxs-lookup"><span data-stu-id="f8628-170">When an API returns just `null`, Invoke-RestMethod was serializing this as the string `"null"` instead of `$null`.</span></span> <span data-ttu-id="f8628-171">Den här ändringen korrigerar logiken i `Invoke-RestMethod` för korrekt serialisering av ett giltigt JSON-värde för enkel värde `null` som `$null` .</span><span class="sxs-lookup"><span data-stu-id="f8628-171">This change fixes the logic in `Invoke-RestMethod` to properly serialize a valid single value JSON `null` literal as `$null`.</span></span>

### <a name="remove--protocol-from--computer-cmdlets-5277"></a><span data-ttu-id="f8628-172">Ta bort `-Protocol` från `*-Computer` cmdlets [#5277](https://github.com/PowerShell/PowerShell/issues/5277)</span><span class="sxs-lookup"><span data-stu-id="f8628-172">Remove `-Protocol` from `*-Computer` cmdlets [#5277](https://github.com/PowerShell/PowerShell/issues/5277)</span></span>

<span data-ttu-id="f8628-173">På grund av problem med RPC-fjärrkommunikation i CoreFX (särskilt på plattformar som inte är Windows) och säkerställer en konsekvent fjärrhantering i PowerShell, `-Protocol` har parametern tagits bort från `\*-Computer` cmdletarna.</span><span class="sxs-lookup"><span data-stu-id="f8628-173">Due to issues with RPC remoting in CoreFX (particularly on non-Windows platforms) and ensuring a consistent remoting experience in PowerShell, the `-Protocol` parameter was removed from the `\*-Computer` cmdlets.</span></span> <span data-ttu-id="f8628-174">DCOM stöds inte längre för fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="f8628-174">DCOM is no longer supported for remoting.</span></span> <span data-ttu-id="f8628-175">Följande cmdletar stöder bara WSMAN-fjärr kommunikation:</span><span class="sxs-lookup"><span data-stu-id="f8628-175">The following cmdlets only support WSMAN remoting:</span></span>

- <span data-ttu-id="f8628-176">Rename-Computer</span><span class="sxs-lookup"><span data-stu-id="f8628-176">Rename-Computer</span></span>
- <span data-ttu-id="f8628-177">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="f8628-177">Restart-Computer</span></span>
- <span data-ttu-id="f8628-178">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="f8628-178">Stop-Computer</span></span>

### <a name="remove--computername-from--service-cmdlets-5090"></a><span data-ttu-id="f8628-179">Ta bort `-ComputerName` från `*-Service` cmdlets [#5090](https://github.com/PowerShell/PowerShell/issues/5094)</span><span class="sxs-lookup"><span data-stu-id="f8628-179">Remove `-ComputerName` from `*-Service` cmdlets [#5090](https://github.com/PowerShell/PowerShell/issues/5094)</span></span>

<span data-ttu-id="f8628-180">`-ComputerName`Parametern har tagits bort från cmdlets för att uppmuntra en konsekvent användning av PSRP `*-Service` .</span><span class="sxs-lookup"><span data-stu-id="f8628-180">In order to encourage the consistent use of PSRP, the `-ComputerName` parameter was removed from `*-Service` cmdlets.</span></span>

### <a name="fix-get-item--literalpath-ab-if-ab-doesnt-actually-exist-to-return-error-5197"></a><span data-ttu-id="f8628-181">Korrigera `Get-Item -LiteralPath a*b` om den `a*b` inte redan finns för att returnera fel [#5197](https://github.com/PowerShell/PowerShell/issues/5197)</span><span class="sxs-lookup"><span data-stu-id="f8628-181">Fix `Get-Item -LiteralPath a*b` if `a*b` doesn't actually exist to return error [#5197](https://github.com/PowerShell/PowerShell/issues/5197)</span></span>

<span data-ttu-id="f8628-182">Tidigare `-LiteralPath` skulle ett jokertecken behandla det på samma sätt som `-Path` och om jokertecken inte hittade några filer, stängs det tyst.</span><span class="sxs-lookup"><span data-stu-id="f8628-182">Previously, `-LiteralPath` given a wildcard would treat it the same as `-Path` and if the wildcard found no files, it would silently exit.</span></span> <span data-ttu-id="f8628-183">Rätt beteende bör vara det `-LiteralPath` exakta värdet, så om filen inte finns, bör den innehålla fel.</span><span class="sxs-lookup"><span data-stu-id="f8628-183">Correct behavior should be that `-LiteralPath` is literal so if the file doesn't exist, it should error.</span></span> <span data-ttu-id="f8628-184">Ändra är att hantera jokertecken som används med `-Literal` literal.</span><span class="sxs-lookup"><span data-stu-id="f8628-184">Change is to treat wildcards used with `-Literal` as literal.</span></span>

### <a name="import-csv-should-apply-pstypenames-upon-import-when-type-information-is-present-in-the-csv-5134"></a><span data-ttu-id="f8628-185">`Import-Csv` bör gälla `PSTypeNames` vid import när typ information finns i CSV- [#5134](https://github.com/PowerShell/PowerShell/issues/5134)</span><span class="sxs-lookup"><span data-stu-id="f8628-185">`Import-Csv` should apply `PSTypeNames` upon import when type information is present in the CSV [#5134](https://github.com/PowerShell/PowerShell/issues/5134)</span></span>

<span data-ttu-id="f8628-186">Tidigare bevarade objekt som exporter ATS med `Export-CSV` med `TypeInformation` importerad med `ConvertFrom-Csv` inte typ informationen.</span><span class="sxs-lookup"><span data-stu-id="f8628-186">Previously, objects exported using `Export-CSV` with `TypeInformation` imported with `ConvertFrom-Csv` were not retaining the type information.</span></span> <span data-ttu-id="f8628-187">Den här ändringen lägger till typ informationen till `PSTypeNames` medlemmen om den är tillgänglig från CSV-filen.</span><span class="sxs-lookup"><span data-stu-id="f8628-187">This change adds the type information to `PSTypeNames` member if available from the CSV file.</span></span>

### <a name="-notypeinformation-should-be-default-on-export-csv-5131"></a><span data-ttu-id="f8628-188">`-NoTypeInformation` ska vara standard `Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131)</span><span class="sxs-lookup"><span data-stu-id="f8628-188">`-NoTypeInformation` should be default on `Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131)</span></span>

<span data-ttu-id="f8628-189">Den här ändringen gjordes för att lösa kundfeedback om standard beteendet för `Export-CSV` att inkludera typ information.</span><span class="sxs-lookup"><span data-stu-id="f8628-189">This change was made to address customer feedback on the default behavior of `Export-CSV` to include type information.</span></span>

<span data-ttu-id="f8628-190">Tidigare skulle cmdleten skriva en kommentar som den första raden som innehåller objektets typnamn.</span><span class="sxs-lookup"><span data-stu-id="f8628-190">Previously, the cmdlet would output a comment as the first line containing the type name of the object.</span></span> <span data-ttu-id="f8628-191">Ändringen är att ignorera detta som standard eftersom det inte tolkas av de flesta verktyg.</span><span class="sxs-lookup"><span data-stu-id="f8628-191">The change is to suppress this by default as it's not understood by most tools.</span></span> <span data-ttu-id="f8628-192">Används `-IncludeTypeInformation` för att behålla det tidigare beteendet.</span><span class="sxs-lookup"><span data-stu-id="f8628-192">Use `-IncludeTypeInformation` to retain the previous behavior.</span></span>

### <a name="web-cmdlets-should-warn-when--credential-is-sent-over-unencrypted-connections-5112"></a><span data-ttu-id="f8628-193">Webb-cmdlets bör varna när `-Credential` skickas via okrypterade anslutningar [#5112](https://github.com/PowerShell/PowerShell/issues/5112)</span><span class="sxs-lookup"><span data-stu-id="f8628-193">Web Cmdlets should warn when `-Credential` is sent over unencrypted connections [#5112](https://github.com/PowerShell/PowerShell/issues/5112)</span></span>

<span data-ttu-id="f8628-194">När du använder HTTP skickas innehåll inklusive lösen ord som klartext.</span><span class="sxs-lookup"><span data-stu-id="f8628-194">When using HTTP, content including passwords are sent as clear-text.</span></span> <span data-ttu-id="f8628-195">Den här ändringen är att inte tillåta detta som standard och returnera ett fel om autentiseringsuppgifterna skickas på ett osäkert sätt.</span><span class="sxs-lookup"><span data-stu-id="f8628-195">This change is to not allow this by default and return an error if credentials are being passed in an insecure manner.</span></span> <span data-ttu-id="f8628-196">Användare kan kringgå detta genom att använda `-AllowUnencryptedAuthentication` växeln.</span><span class="sxs-lookup"><span data-stu-id="f8628-196">Users can bypass this by using the `-AllowUnencryptedAuthentication` switch.</span></span>

## <a name="api-changes"></a><span data-ttu-id="f8628-197">API-ändringar</span><span class="sxs-lookup"><span data-stu-id="f8628-197">API changes</span></span>

### <a name="remove-addtypecommandbase-class-5407"></a><span data-ttu-id="f8628-198">Ta bort `AddTypeCommandBase` klass [#5407](https://github.com/PowerShell/PowerShell/issues/5407)</span><span class="sxs-lookup"><span data-stu-id="f8628-198">Remove `AddTypeCommandBase` class [#5407](https://github.com/PowerShell/PowerShell/issues/5407)</span></span>

<span data-ttu-id="f8628-199">`AddTypeCommandBase`Klassen har tagits bort från `Add-Type` för att förbättra prestandan.</span><span class="sxs-lookup"><span data-stu-id="f8628-199">The `AddTypeCommandBase` class was removed from `Add-Type` to improve performance.</span></span> <span data-ttu-id="f8628-200">Den här klassen används endast av Add-Type-cmdleten och bör inte påverka användare.</span><span class="sxs-lookup"><span data-stu-id="f8628-200">This class is only used by the Add-Type cmdlet and should not impact users.</span></span>

### <a name="unify-cmdlets-with-parameter--encoding-to-be-of-type-systemtextencoding-5080"></a><span data-ttu-id="f8628-201">Förena cmdletar med parametern `-Encoding` som typ `System.Text.Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)</span><span class="sxs-lookup"><span data-stu-id="f8628-201">Unify cmdlets with parameter `-Encoding` to be of type `System.Text.Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)</span></span>

<span data-ttu-id="f8628-202">`-Encoding`Värdet `Byte` har tagits bort från cmdletarna för fil Systems Provider.</span><span class="sxs-lookup"><span data-stu-id="f8628-202">The `-Encoding` value `Byte` has been removed from the filesystem provider cmdlets.</span></span> <span data-ttu-id="f8628-203">En ny parameter `-AsByteStream` används nu för att ange att en byte-dataström krävs som indata eller att utdata är en data ström i byte.</span><span class="sxs-lookup"><span data-stu-id="f8628-203">A new parameter, `-AsByteStream`, is now used to specify that a byte stream is required as input or that the output is a stream of bytes.</span></span>

### <a name="add-better-error-message-for-empty-and-null--uformat-parameter-5055"></a><span data-ttu-id="f8628-204">Lägg till bättre fel meddelande för Tom och null- `-UFormat` parameter [#5055](https://github.com/PowerShell/PowerShell/issues/5055)</span><span class="sxs-lookup"><span data-stu-id="f8628-204">Add better error message for empty and null `-UFormat` parameter [#5055](https://github.com/PowerShell/PowerShell/issues/5055)</span></span>

<span data-ttu-id="f8628-205">Tidigare visas ett fel meddelande om att en tom format sträng skickades till `-UFormat` .</span><span class="sxs-lookup"><span data-stu-id="f8628-205">Previously, when passing an empty format string to `-UFormat`, an unhelpful error message would appear.</span></span> <span data-ttu-id="f8628-206">Ett mer beskrivande fel har lagts till.</span><span class="sxs-lookup"><span data-stu-id="f8628-206">A more descriptive error has been added.</span></span>

### <a name="clean-up-console-code-4995"></a><span data-ttu-id="f8628-207">Rensa konsol kod [#4995](https://github.com/PowerShell/PowerShell/issues/4995)</span><span class="sxs-lookup"><span data-stu-id="f8628-207">Clean up console code [#4995](https://github.com/PowerShell/PowerShell/issues/4995)</span></span>

<span data-ttu-id="f8628-208">Följande funktioner har tagits bort eftersom de inte stöds i PowerShell Core, och det finns inga planer på att lägga till stöd som de finns för äldre skäl för Windows PowerShell: `-psconsolefile` switch och kod, `-importsystemmodules` växel och kod och kod för ändring av teckensnitt.</span><span class="sxs-lookup"><span data-stu-id="f8628-208">The following features were removed as they are not supported in PowerShell Core, and there are no plans to add support as they exist for legacy reasons for Windows PowerShell: `-psconsolefile` switch and code, `-importsystemmodules` switch and code, and font changing code.</span></span>

### <a name="removed-runspaceconfiguration-support-4942"></a><span data-ttu-id="f8628-209">`RunspaceConfiguration`Stöd [#4942](https://github.com/PowerShell/PowerShell/issues/4942) har tagits bort</span><span class="sxs-lookup"><span data-stu-id="f8628-209">Removed `RunspaceConfiguration` support [#4942](https://github.com/PowerShell/PowerShell/issues/4942)</span></span>

<span data-ttu-id="f8628-210">När du tidigare skapade en PowerShell-körnings utrymme via programmering med hjälp av API: et kan du använda det äldre [`RunspaceConfiguration`][runspaceconfig] eller senare [`InitialSessionState`][iss] .</span><span class="sxs-lookup"><span data-stu-id="f8628-210">Previously, when creating a PowerShell runspace programmatically using the API you could use the legacy [`RunspaceConfiguration`][runspaceconfig] or the newer [`InitialSessionState`][iss].</span></span> <span data-ttu-id="f8628-211">Den här ändringen har tagit bort stöd för `RunspaceConfiguration` och stöder bara `InitialSessionState` .</span><span class="sxs-lookup"><span data-stu-id="f8628-211">This change removed support for `RunspaceConfiguration` and only supports `InitialSessionState`.</span></span>

[runspaceconfig]: /dotnet/api/system.management.automation.runspaces.runspaceconfiguration
[iss]: /dotnet/api/system.management.automation.runspaces.initialsessionstate

### <a name="commandinvocationintrinsicsinvokescript-bind-arguments-to-input-instead-of-args-4923"></a><span data-ttu-id="f8628-212">`CommandInvocationIntrinsics.InvokeScript` bind argument till `$input` i stället för `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)</span><span class="sxs-lookup"><span data-stu-id="f8628-212">`CommandInvocationIntrinsics.InvokeScript` bind arguments to `$input` instead of `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)</span></span>

<span data-ttu-id="f8628-213">En felaktig position av en parameter resulterade i argumenten som angavs som indatamängd i stället för som argument.</span><span class="sxs-lookup"><span data-stu-id="f8628-213">An incorrect position of a parameter resulted in the args passed as input instead of as args.</span></span>

### <a name="remove-unsupported--showwindow-switch-from-get-help-4903"></a><span data-ttu-id="f8628-214">Ta bort växeln som inte stöds `-showwindow` från `Get-Help` [#4903](https://github.com/PowerShell/PowerShell/issues/4903)</span><span class="sxs-lookup"><span data-stu-id="f8628-214">Remove unsupported `-showwindow` switch from `Get-Help` [#4903](https://github.com/PowerShell/PowerShell/issues/4903)</span></span>

<span data-ttu-id="f8628-215">`-showwindow` är beroende av WPF, vilket inte stöds på CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="f8628-215">`-showwindow` relies on WPF, which is not supported on CoreCLR.</span></span>

### <a name="allow--to-be-used-in-registry-path-for-remove-item-4866"></a><span data-ttu-id="f8628-216">Tillåt att \* används i register Sök vägen för `Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866)</span><span class="sxs-lookup"><span data-stu-id="f8628-216">Allow \* to be used in registry path for `Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866)</span></span>

<span data-ttu-id="f8628-217">Tidigare `-LiteralPath` skulle ett jokertecken behandla det på samma sätt som `-Path` och om jokertecken inte hittade några filer, stängs det tyst.</span><span class="sxs-lookup"><span data-stu-id="f8628-217">Previously, `-LiteralPath` given a wildcard would treat it the same as `-Path` and if the wildcard found no files, it would silently exit.</span></span> <span data-ttu-id="f8628-218">Rätt beteende bör vara det `-LiteralPath` exakta värdet, så om filen inte finns, bör den innehålla fel.</span><span class="sxs-lookup"><span data-stu-id="f8628-218">Correct behavior should be that `-LiteralPath` is literal so if the file doesn't exist, it should error.</span></span> <span data-ttu-id="f8628-219">Ändra är att hantera jokertecken som används med `-Literal` literal.</span><span class="sxs-lookup"><span data-stu-id="f8628-219">Change is to treat wildcards used with `-Literal` as literal.</span></span>

### <a name="fix-set-service-failing-test-4802"></a><span data-ttu-id="f8628-220">Korrigera `Set-Service` misslyckad test [#4802](https://github.com/PowerShell/PowerShell/issues/4802)</span><span class="sxs-lookup"><span data-stu-id="f8628-220">Fix `Set-Service` failing test [#4802](https://github.com/PowerShell/PowerShell/issues/4802)</span></span>

<span data-ttu-id="f8628-221">Om användes tidigare `New-Service -StartupType foo` `foo` ignorerades och tjänsten skapades med en typ av standard starttyp.</span><span class="sxs-lookup"><span data-stu-id="f8628-221">Previously, if `New-Service -StartupType foo` was used, `foo` was ignored and the service was created with some default startup type.</span></span> <span data-ttu-id="f8628-222">Den här ändringen är att explicit utlösa ett fel för en ogiltig starttyp.</span><span class="sxs-lookup"><span data-stu-id="f8628-222">This change is to explicitly throw an error for an invalid startup type.</span></span>

### <a name="rename-isosx-to-ismacos-4700"></a><span data-ttu-id="f8628-223">Byt namn `$IsOSX` till `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)</span><span class="sxs-lookup"><span data-stu-id="f8628-223">Rename `$IsOSX` to `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)</span></span>

<span data-ttu-id="f8628-224">Namngivningen i PowerShell bör vara konsekvent med vår namn och överensstämmer med Apples användning av macOS i stället för OSX.</span><span class="sxs-lookup"><span data-stu-id="f8628-224">The naming in PowerShell should be consistent with our naming and conform to Apple's use of macOS instead of OSX.</span></span> <span data-ttu-id="f8628-225">Men för att kunna läsa och ständigt kan vi hålla sig till Pascal-höljet.</span><span class="sxs-lookup"><span data-stu-id="f8628-225">However, for readability and consistently we are staying with Pascal casing.</span></span>

### <a name="make-error-message-consistent-when-invalid-script-is-passed-to--file-better-error-when-passed-ambiguous-argument-4573"></a><span data-ttu-id="f8628-226">Gör fel meddelandet konsekvent när ogiltigt skript skickas till fil, vilket är ett bättre fel när ett tvetydigt argument har skickats [#4573](https://github.com/PowerShell/PowerShell/issues/4573)</span><span class="sxs-lookup"><span data-stu-id="f8628-226">Make error message consistent when invalid script is passed to -File, better error when passed ambiguous argument [#4573](https://github.com/PowerShell/PowerShell/issues/4573)</span></span>

<span data-ttu-id="f8628-227">Ändra avslutnings koderna för `pwsh.exe` att anpassas efter UNIX-konventioner</span><span class="sxs-lookup"><span data-stu-id="f8628-227">Change the exit codes of `pwsh.exe` to align with Unix conventions</span></span>

### <a name="removal-of-localaccount-and-cmdlets-from--diagnostics-modules-4302-4303"></a><span data-ttu-id="f8628-228">Borttagning av `LocalAccount` och cmdlets från  `Diagnostics` moduler.</span><span class="sxs-lookup"><span data-stu-id="f8628-228">Removal of `LocalAccount` and cmdlets from  `Diagnostics` modules.</span></span> <span data-ttu-id="f8628-229">[#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)</span><span class="sxs-lookup"><span data-stu-id="f8628-229">[#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)</span></span>

<span data-ttu-id="f8628-230">På grund av API: er som inte stöds `LocalAccounts` har modulen och `Counter` cmdletarna i `Diagnostics` modulen tagits bort tills en bättre lösning har hittats.</span><span class="sxs-lookup"><span data-stu-id="f8628-230">Due to unsupported APIs, the `LocalAccounts` module and the `Counter` cmdlets in the `Diagnostics` module were removed until a better solution is found.</span></span>

### <a name="executing-powershell-script-with-bool-parameter-does-not-work-4036"></a><span data-ttu-id="f8628-231">Det går inte att köra PowerShell-skriptet med bool-parametern [#4036](https://github.com/PowerShell/PowerShell/issues/4036)</span><span class="sxs-lookup"><span data-stu-id="f8628-231">Executing PowerShell script with bool parameter does not work [#4036](https://github.com/PowerShell/PowerShell/issues/4036)</span></span>

<span data-ttu-id="f8628-232">Tidigare använde **powershell.exe** (nu **pwsh.exe**) för att köra ett PowerShell-skript som `-File` inte har tillhandahållit något sätt att skicka `$true` / `$false` som parameter värden.</span><span class="sxs-lookup"><span data-stu-id="f8628-232">Previously, using **powershell.exe** (now **pwsh.exe**) to execute a PowerShell script using `-File` provided no way to pass `$true`/`$false` as parameter values.</span></span> <span data-ttu-id="f8628-233">Stöd för `$true` / `$false` som parsade värden till parametrar har lagts till.</span><span class="sxs-lookup"><span data-stu-id="f8628-233">Support for `$true`/`$false` as parsed values to parameters was added.</span></span> <span data-ttu-id="f8628-234">Växlings värden stöds också som för närvarande dokumenterad syntax fungerar inte.</span><span class="sxs-lookup"><span data-stu-id="f8628-234">Switch values are also supported as currently documented syntax doesn't work.</span></span>

### <a name="remove-clrversion-property-from-psversiontable-4027"></a><span data-ttu-id="f8628-235">Ta bort `ClrVersion` egenskap från `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)</span><span class="sxs-lookup"><span data-stu-id="f8628-235">Remove `ClrVersion` property from `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)</span></span>

<span data-ttu-id="f8628-236">`ClrVersion`Egenskapen i `$PSVersionTable` är inte användbar med CoreCLR, slutanvändare ska inte använda det värdet för att fastställa kompatibiliteten.</span><span class="sxs-lookup"><span data-stu-id="f8628-236">The `ClrVersion` property of `$PSVersionTable` is not useful with CoreCLR, end users should not be using that value to determine compatibility.</span></span>

### <a name="change-positional-parameter-for-powershellexe-from--command-to--file-4019"></a><span data-ttu-id="f8628-237">Ändra positions parameter för `powershell.exe` från `-Command` till `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)</span><span class="sxs-lookup"><span data-stu-id="f8628-237">Change positional parameter for `powershell.exe` from `-Command` to `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)</span></span>

<span data-ttu-id="f8628-238">Aktivera Shebang användning av PowerShell på andra plattformar än Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="f8628-238">Enable shebang use of PowerShell on non-Windows platforms.</span></span> <span data-ttu-id="f8628-239">Det innebär att du kan skapa en skript-körbar fil som anropar PowerShell automatiskt i stället för att uttryckligen anropa det på UNIX-baserade system `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="f8628-239">This means on Unix based systems, you can make a script executable that would invoke PowerShell automatically rather than explicitly invoking `pwsh`.</span></span> <span data-ttu-id="f8628-240">Det innebär också att du nu kan göra saker som `powershell foo.ps1` eller `powershell fooScript` utan att ange `-File` .</span><span class="sxs-lookup"><span data-stu-id="f8628-240">This also means that you can now do things like `powershell foo.ps1` or `powershell fooScript` without specifying `-File`.</span></span> <span data-ttu-id="f8628-241">Den här ändringen kräver dock att du uttryckligen anger `-c` eller `-Command` när du försöker göra saker som `powershell.exe Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="f8628-241">However, this change now requires that you explicitly specify `-c` or `-Command` when trying to do things like `powershell.exe Get-Command`.</span></span>

### <a name="implement-unicode-escape-parsing-3958"></a><span data-ttu-id="f8628-242">Implementera tolkning av Unicode-Escape [#3958](https://github.com/PowerShell/PowerShell/issues/3958)</span><span class="sxs-lookup"><span data-stu-id="f8628-242">Implement Unicode escape parsing [#3958](https://github.com/PowerShell/PowerShell/issues/3958)</span></span>

<span data-ttu-id="f8628-243">`` `u####`` eller `` `u{####}`` konverteras till motsvarande Unicode-tecken.</span><span class="sxs-lookup"><span data-stu-id="f8628-243">`` `u####`` or `` `u{####}`` is converted to the corresponding Unicode character.</span></span> <span data-ttu-id="f8628-244">Om du vill mata ut en litteral `` `u`` kan du undanta bakticket: ``` ``u``` .</span><span class="sxs-lookup"><span data-stu-id="f8628-244">To output a literal `` `u``, escape the backtick: ``` ``u```.</span></span>

### <a name="change-new-modulemanifest-encoding-to-utf8nobom-on-non-windows-platforms-3940"></a><span data-ttu-id="f8628-245">Ändra `New-ModuleManifest` kodningen till `UTF8NoBOM` på andra plattformar än Windows-plattformar [#3940](https://github.com/PowerShell/PowerShell/issues/3940)</span><span class="sxs-lookup"><span data-stu-id="f8628-245">Change `New-ModuleManifest` encoding to `UTF8NoBOM` on non-Windows platforms [#3940](https://github.com/PowerShell/PowerShell/issues/3940)</span></span>

<span data-ttu-id="f8628-246">Tidigare `New-ModuleManifest` skapade psd1-manifest i UTF-16 med BOM och skapar ett problem för Linux-verktyg.</span><span class="sxs-lookup"><span data-stu-id="f8628-246">Previously, `New-ModuleManifest` creates psd1 manifests in UTF-16 with BOM, creating a problem for Linux tools.</span></span> <span data-ttu-id="f8628-247">Den här avbrytande ändringen ändrar kodningen `New-ModuleManifest` till UTF (ingen BOM) på andra plattformar än Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="f8628-247">This breaking change changes the encoding of `New-ModuleManifest` to be UTF (no BOM) in non-Windows platforms.</span></span>

### <a name="prevent-get-childitem-from-recursing-into-symlinks-1875-3780"></a><span data-ttu-id="f8628-248">Förhindra att `Get-ChildItem` återkommer till symlinks (#1875).</span><span class="sxs-lookup"><span data-stu-id="f8628-248">Prevent `Get-ChildItem` from recursing into symlinks (#1875).</span></span> [<span data-ttu-id="f8628-249">#3780</span><span class="sxs-lookup"><span data-stu-id="f8628-249">#3780</span></span>](https://github.com/PowerShell/PowerShell/issues/3780)

<span data-ttu-id="f8628-250">Den här ändringen ger `Get-ChildItem` mer i rad med UNIX- `ls -r` och inbyggda Windows- `dir /s` kommandon.</span><span class="sxs-lookup"><span data-stu-id="f8628-250">This change brings `Get-ChildItem` more in line with the Unix `ls -r` and the Windows `dir /s` native commands.</span></span> <span data-ttu-id="f8628-251">Precis som de nämnda kommandona visar cmdleten symboliska länkar till kataloger som hittades under rekursion, men rekursivt inte in dem.</span><span class="sxs-lookup"><span data-stu-id="f8628-251">Like the mentioned commands, the cmdlet displays symbolic links to directories found during recursion, but does not recurse into them.</span></span>

### <a name="fix-get-content--delimiter-to-not-include-the-delimiter-in-the-returned-lines-3706"></a><span data-ttu-id="f8628-252">Korrigera `Get-Content -Delimiter` för att inte inkludera avgränsaren i de returnerade raderna [#3706](https://github.com/PowerShell/PowerShell/issues/3706)</span><span class="sxs-lookup"><span data-stu-id="f8628-252">Fix `Get-Content -Delimiter` to not include the delimiter in the returned lines [#3706](https://github.com/PowerShell/PowerShell/issues/3706)</span></span>

<span data-ttu-id="f8628-253">Tidigare var de utdata `Get-Content -Delimiter` som användes inkonsekventa och olämpliga eftersom det krävde ytterligare bearbetning av data för att ta bort avgränsaren.</span><span class="sxs-lookup"><span data-stu-id="f8628-253">Previously, the output while using `Get-Content -Delimiter` was inconsistent and inconvenient as it required further processing of the data to remove the delimiter.</span></span> <span data-ttu-id="f8628-254">Den här ändringen tar bort avgränsaren i returnerade rader.</span><span class="sxs-lookup"><span data-stu-id="f8628-254">This change removes the delimiter in returned lines.</span></span>

### <a name="implement-format-hex-in-c-3320"></a><span data-ttu-id="f8628-255">Implementera Format-Hex i C# [#3320](https://github.com/PowerShell/PowerShell/issues/3320)</span><span class="sxs-lookup"><span data-stu-id="f8628-255">Implement Format-Hex in C# [#3320](https://github.com/PowerShell/PowerShell/issues/3320)</span></span>

<span data-ttu-id="f8628-256">`-Raw`Parametern är nu en "No-OP" (där det inte gör något).</span><span class="sxs-lookup"><span data-stu-id="f8628-256">The `-Raw` parameter is now a "no-op" (in that it does nothing).</span></span> <span data-ttu-id="f8628-257">Om du fortsätter kommer alla utdata att visas med en sann representation av siffror som innehåller alla byte för dess typ (vad den `-Raw` här ändringen hade innan ändringen).</span><span class="sxs-lookup"><span data-stu-id="f8628-257">Going forward all of the output will be displayed with a true representation of numbers that includes all of the bytes for its type (what the `-Raw` parameter was formally doing prior to this change).</span></span>

### <a name="powershell-as-a-default-shell-doesnt-work-with-script-command-3319"></a><span data-ttu-id="f8628-258">PowerShell som standard gränssnitt fungerar inte med skript kommandot [#3319](https://github.com/PowerShell/PowerShell/issues/3319)</span><span class="sxs-lookup"><span data-stu-id="f8628-258">PowerShell as a default shell doesn't work with script command [#3319](https://github.com/PowerShell/PowerShell/issues/3319)</span></span>

<span data-ttu-id="f8628-259">I UNIX är det en konvention för gränssnitt att acceptera `-i` för ett interaktivt gränssnitt och många verktyg förväntar sig detta beteende ( `script` till exempel och när du ställer in PowerShell som standard gränssnitt) och anropar gränssnittet med `-i` växeln.</span><span class="sxs-lookup"><span data-stu-id="f8628-259">On Unix, it is a convention for shells to accept `-i` for an interactive shell and many tools expect this behavior (`script` for example, and when setting PowerShell as the default shell) and calls the shell with the `-i` switch.</span></span> <span data-ttu-id="f8628-260">Den här ändringen är Sparad i som `-i` tidigare kunde användas som kort för att matcha `-inputformat` , vilket nu måste vara `-in` .</span><span class="sxs-lookup"><span data-stu-id="f8628-260">This change is breaking in that `-i` previously could be used as short hand to match `-inputformat`, which now needs to be `-in`.</span></span>

### <a name="typo-fix-in-get-computerinfo-property-name-3167"></a><span data-ttu-id="f8628-261">Korrigera skrivfel i Get-ComputerInfo egenskaps namn [#3167](https://github.com/PowerShell/PowerShell/issues/3167)</span><span class="sxs-lookup"><span data-stu-id="f8628-261">Typo fix in Get-ComputerInfo property name [#3167](https://github.com/PowerShell/PowerShell/issues/3167)</span></span>

<span data-ttu-id="f8628-262">`BiosSerialNumber` är felstavat `BiosSeralNumber` och har ändrats till rätt stavning.</span><span class="sxs-lookup"><span data-stu-id="f8628-262">`BiosSerialNumber` was misspelled as `BiosSeralNumber` and has been changed to the correct spelling.</span></span>

### <a name="add-get-stringhash-and-get-filehash-cmdlets-3024"></a><span data-ttu-id="f8628-263">Lägg till `Get-StringHash` och `Get-FileHash` cmdlets [#3024](https://github.com/PowerShell/PowerShell/issues/3024)</span><span class="sxs-lookup"><span data-stu-id="f8628-263">Add `Get-StringHash` and `Get-FileHash` cmdlets [#3024](https://github.com/PowerShell/PowerShell/issues/3024)</span></span>

<span data-ttu-id="f8628-264">Den här ändringen är att vissa hash-algoritmer inte stöds av CoreFX, vilket innebär att de inte längre är tillgängliga:</span><span class="sxs-lookup"><span data-stu-id="f8628-264">This change is that some hash algorithms are not supported by CoreFX, therefore they are no longer available:</span></span>

- `MACTripleDES`
- `RIPEMD160`

### <a name="add-validation-on-get--cmdlets-where-passing-null-returns-all-objects-instead-of-error-2672"></a><span data-ttu-id="f8628-265">Lägg till verifiering på `Get-*` cmdletar där överföring av $null returnerar alla objekt i stället för fel [#2672](https://github.com/PowerShell/PowerShell/issues/2672)</span><span class="sxs-lookup"><span data-stu-id="f8628-265">Add validation on `Get-*` cmdlets where passing $null returns all objects instead of error [#2672](https://github.com/PowerShell/PowerShell/issues/2672)</span></span>

<span data-ttu-id="f8628-266">`$null`Att skicka till något av följande genererar nu ett fel:</span><span class="sxs-lookup"><span data-stu-id="f8628-266">Passing `$null` to any of the following now throws an error:</span></span>

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

### <a name="add-support-w3c-extended-log-file-format-in-import-csv-2482"></a><span data-ttu-id="f8628-267">Lägg till stöd för utökat logg fils format för W3C i `Import-Csv` [#2482](https://github.com/PowerShell/PowerShell/issues/2482)</span><span class="sxs-lookup"><span data-stu-id="f8628-267">Add support W3C Extended Log File Format in `Import-Csv` [#2482](https://github.com/PowerShell/PowerShell/issues/2482)</span></span>

<span data-ttu-id="f8628-268">Tidigare `Import-Csv` kan cmdleten inte användas för att importera loggfilerna direkt i utökat logg format för W3C och ytterligare åtgärder krävs.</span><span class="sxs-lookup"><span data-stu-id="f8628-268">Previously, the `Import-Csv` cmdlet cannot be used to directly import the log files in W3C extended log format and additional action would be required.</span></span> <span data-ttu-id="f8628-269">Med den här ändringen stöds W3C Extended Log-formatet.</span><span class="sxs-lookup"><span data-stu-id="f8628-269">With this change, W3C extended log format is supported.</span></span>

### <a name="parameter-binding-problem-with-valuefromremainingarguments-in-ps-functions-2035"></a><span data-ttu-id="f8628-270">Parameter bindnings problem med `ValueFromRemainingArguments` i PS functions [#2035](https://github.com/PowerShell/PowerShell/issues/2035)</span><span class="sxs-lookup"><span data-stu-id="f8628-270">Parameter binding problem with `ValueFromRemainingArguments` in PS functions [#2035](https://github.com/PowerShell/PowerShell/issues/2035)</span></span>

<span data-ttu-id="f8628-271">`ValueFromRemainingArguments` returnerar nu värdena som en matris i stället för ett enda värde som är en matris.</span><span class="sxs-lookup"><span data-stu-id="f8628-271">`ValueFromRemainingArguments` now returns the values as an array instead of a single value which itself is an array.</span></span>

### <a name="buildversion-is-removed-from-psversiontable-1415"></a><span data-ttu-id="f8628-272">`BuildVersion` har tagits bort från `$PSVersionTable` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)</span><span class="sxs-lookup"><span data-stu-id="f8628-272">`BuildVersion` is removed from `$PSVersionTable` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)</span></span>

<span data-ttu-id="f8628-273">Ta bort `BuildVersion` egenskapen från `$PSVersionTable` .</span><span class="sxs-lookup"><span data-stu-id="f8628-273">Remove the `BuildVersion` property from `$PSVersionTable`.</span></span> <span data-ttu-id="f8628-274">Den här egenskapen är kopplad till Windows build-versionen.</span><span class="sxs-lookup"><span data-stu-id="f8628-274">This property was tied to the Windows build version.</span></span> <span data-ttu-id="f8628-275">I stället rekommenderar vi att du använder `GitCommitId` för att hämta den exakta versionen av PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="f8628-275">Instead, we recommend that you use `GitCommitId` to retrieve the exact build version of PowerShell Core.</span></span>

### <a name="changes-to-web-cmdlets"></a><span data-ttu-id="f8628-276">Ändringar av webb-cmdletar</span><span class="sxs-lookup"><span data-stu-id="f8628-276">Changes to Web Cmdlets</span></span>

<span data-ttu-id="f8628-277">De underliggande .NET API: erna för webb-cmdletarna har ändrats till `System.Net.Http.HttpClient` .</span><span class="sxs-lookup"><span data-stu-id="f8628-277">The underlying .NET API of the Web Cmdlets has been changed to `System.Net.Http.HttpClient`.</span></span> <span data-ttu-id="f8628-278">Den här ändringen ger många fördelar.</span><span class="sxs-lookup"><span data-stu-id="f8628-278">This change provides many benefits.</span></span> <span data-ttu-id="f8628-279">Men den här ändringen tillsammans med en brist på interoperabilitet med Internet Explorer har resulterat i flera större ändringar i `Invoke-WebRequest` och `Invoke-RestMethod` .</span><span class="sxs-lookup"><span data-stu-id="f8628-279">However, this change along with a lack of interoperability with Internet Explorer have resulted in several breaking changes within `Invoke-WebRequest` and `Invoke-RestMethod`.</span></span>

- <span data-ttu-id="f8628-280">`Invoke-WebRequest` stöder nu bara grundläggande HTML-parsning.</span><span class="sxs-lookup"><span data-stu-id="f8628-280">`Invoke-WebRequest` now supports basic HTML Parsing only.</span></span> <span data-ttu-id="f8628-281">`Invoke-WebRequest` returnerar alltid ett `BasicHtmlWebResponseObject` objekt.</span><span class="sxs-lookup"><span data-stu-id="f8628-281">`Invoke-WebRequest` always returns a `BasicHtmlWebResponseObject` object.</span></span> <span data-ttu-id="f8628-282">`ParsedHtml`Egenskaperna och `Forms` har tagits bort.</span><span class="sxs-lookup"><span data-stu-id="f8628-282">The `ParsedHtml` and `Forms` properties have been removed.</span></span>
- <span data-ttu-id="f8628-283">`BasicHtmlWebResponseObject.Headers` värdena är nu i `String[]` stället för `String` .</span><span class="sxs-lookup"><span data-stu-id="f8628-283">`BasicHtmlWebResponseObject.Headers` values are now `String[]` instead of `String`.</span></span>
- <span data-ttu-id="f8628-284">`BasicHtmlWebResponseObject.BaseResponse` är nu ett `System.Net.Http.HttpResponseMessage` objekt.</span><span class="sxs-lookup"><span data-stu-id="f8628-284">`BasicHtmlWebResponseObject.BaseResponse` is now a `System.Net.Http.HttpResponseMessage` object.</span></span>
- <span data-ttu-id="f8628-285">`Response`Egenskapen för webb-cmdlet-undantag är nu ett `System.Net.Http.HttpResponseMessage` objekt.</span><span class="sxs-lookup"><span data-stu-id="f8628-285">The `Response` property on Web Cmdlet exceptions is now a `System.Net.Http.HttpResponseMessage` object.</span></span>
- <span data-ttu-id="f8628-286">Strikt rubrik tolkning för RFC är nu standard för `-Headers` parametern och `-UserAgent` .</span><span class="sxs-lookup"><span data-stu-id="f8628-286">Strict RFC header parsing is now default for the `-Headers` and `-UserAgent` parameter.</span></span> <span data-ttu-id="f8628-287">Detta kan kringgås med `-SkipHeaderValidation` .</span><span class="sxs-lookup"><span data-stu-id="f8628-287">This can be bypassed with `-SkipHeaderValidation`.</span></span>
- <span data-ttu-id="f8628-288">`file://` och `ftp://` URI-scheman stöds inte längre.</span><span class="sxs-lookup"><span data-stu-id="f8628-288">`file://` and `ftp://` URI schemes are no longer supported.</span></span>
- <span data-ttu-id="f8628-289">`System.Net.ServicePointManager` inställningarna stöds inte längre.</span><span class="sxs-lookup"><span data-stu-id="f8628-289">`System.Net.ServicePointManager` settings are no longer honored.</span></span>
- <span data-ttu-id="f8628-290">Det finns för närvarande ingen certifikatbaserad autentisering tillgänglig på macOS.</span><span class="sxs-lookup"><span data-stu-id="f8628-290">There is currently no certificate based authentication available on macOS.</span></span>
- <span data-ttu-id="f8628-291">Om du använder `-Credential` över en `http://` URI kommer det att resultera i ett fel.</span><span class="sxs-lookup"><span data-stu-id="f8628-291">Use of `-Credential` over an `http://` URI will result in an error.</span></span> <span data-ttu-id="f8628-292">Använd en `https://` URI eller ange `-AllowUnencryptedAuthentication` parametern för att ignorera felet.</span><span class="sxs-lookup"><span data-stu-id="f8628-292">Use an `https://` URI or supply the `-AllowUnencryptedAuthentication` parameter to suppress the error.</span></span>
- <span data-ttu-id="f8628-293">`-MaximumRedirection` genererar nu ett avslutande fel när omdirigerings försök överskrider den angivna gränsen i stället för att returnera resultaten av den senaste omdirigeringen.</span><span class="sxs-lookup"><span data-stu-id="f8628-293">`-MaximumRedirection` now produces a terminating error when redirection attempts exceed the provided limit instead of returning the results of the last redirection.</span></span>
- <span data-ttu-id="f8628-294">I PowerShell 6,2 gjordes en ändring som standard till UTF-8-kodning för JSON-svar.</span><span class="sxs-lookup"><span data-stu-id="f8628-294">In PowerShell 6.2, a change was made to default to UTF-8 encoding for JSON responses.</span></span> <span data-ttu-id="f8628-295">Om ingen teckenuppsättning anges för ett JSON-svar ska standard kodningen vara UTF-8 per RFC 8259.</span><span class="sxs-lookup"><span data-stu-id="f8628-295">When a charset is not supplied for a JSON response, the default encoding should be UTF-8 per RFC 8259.</span></span>
