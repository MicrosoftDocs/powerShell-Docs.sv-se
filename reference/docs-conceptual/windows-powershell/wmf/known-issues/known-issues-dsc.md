---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Kända problem och begränsningar för Desired State Configuration (DSC)
ms.openlocfilehash: a76c5bb336804c5b384e6b6ba6a705c6049ef7fb
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810206"
---
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a><span data-ttu-id="95125-103">Kända problem och begränsningar för Desired State Configuration (DSC)</span><span class="sxs-lookup"><span data-stu-id="95125-103">Desired State Configuration (DSC) Known Issues and Limitations</span></span>

## <a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a><span data-ttu-id="95125-104">Bryta ändring: certifikat som används för att kryptera/dekryptera lösen ord i DSC-konfigurationer fungerar kanske inte efter installation av WMF 5,0 RTM</span><span class="sxs-lookup"><span data-stu-id="95125-104">Breaking Change: Certificates used to encrypt/decrypt passwords in DSC configurations may not work after installing WMF 5.0 RTM</span></span>

<span data-ttu-id="95125-105">I WMF 4,0-och WMF 5,0 Preview-versioner tillåter DSC inte att lösen ord i konfigurationen är längre än 121 tecken.</span><span class="sxs-lookup"><span data-stu-id="95125-105">In WMF 4.0 and WMF 5.0 Preview releases, DSC would not allow passwords in the configuration to be of length more than 121 characters.</span></span> <span data-ttu-id="95125-106">DSC tvingade sig använda korta lösen ord även om längd och starkt lösen ord önskas.</span><span class="sxs-lookup"><span data-stu-id="95125-106">DSC was forcing to use short passwords even if lengthy and strong password was desired.</span></span> <span data-ttu-id="95125-107">Den här avbrytande ändringen innebär att lösen ord kan vara av godtycklig längd i DSC-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="95125-107">This breaking change allows passwords to be of arbitrary length in the DSC configuration.</span></span>

<span data-ttu-id="95125-108">**Lösning:** Återskapa certifikatet med användning av data kryptering eller nyckel kryptering och förbättrad nyckel användning för dokument kryptering (1.3.6.1.4.1.311.80.1).</span><span class="sxs-lookup"><span data-stu-id="95125-108">**Resolution:** Re-create the certificate with Data Encipherment or Key Encipherment Key usage, and Document Encryption Enhanced Key usage (1.3.6.1.4.1.311.80.1).</span></span> <span data-ttu-id="95125-109">Mer information finns i [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage).</span><span class="sxs-lookup"><span data-stu-id="95125-109">For more information, see [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage).</span></span>

## <a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a><span data-ttu-id="95125-110">DSC-cmdletar kan Miss lyckas efter installation av WMF 5,0 RTM</span><span class="sxs-lookup"><span data-stu-id="95125-110">DSC cmdlets may fail after installing WMF 5.0 RTM</span></span>

<span data-ttu-id="95125-111">`Start-DscConfiguration`och andra DSC-cmdletar kan Miss lyckas efter installation av WMF 5,0 RTM med följande fel:</span><span class="sxs-lookup"><span data-stu-id="95125-111">`Start-DscConfiguration` and other DSC cmdlets may fail after installing WMF 5.0 RTM with the following error:</span></span>

```Output
LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
+ CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
+ FullyQualifiedErrorId : MI RESULT 6
+ PSComputerName : localhost
```

<span data-ttu-id="95125-112">**Lösning:** Ta bort DSCEngineCache. MOF genom att köra följande kommando i en upphöjd PowerShell-session (kör som administratör):</span><span class="sxs-lookup"><span data-stu-id="95125-112">**Resolution:** Delete DSCEngineCache.mof by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```

## <a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a><span data-ttu-id="95125-113">DSC-cmdletar fungerar kanske inte om WMF 5,0 RTM installeras ovanpå WMF 5,0 Product Preview</span><span class="sxs-lookup"><span data-stu-id="95125-113">DSC cmdlets may not work if WMF 5.0 RTM is installed on top of WMF 5.0 Production Preview</span></span>

<span data-ttu-id="95125-114">**Lösning:** Kör följande kommando i en upphöjd PowerShell-session (kör som administratör):</span><span class="sxs-lookup"><span data-stu-id="95125-114">**Resolution:** Run the following command in an elevated PowerShell session (run as administrator):</span></span>

```powershell
mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```

## <a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a><span data-ttu-id="95125-115">LCM kan hamna i ett instabilt tillstånd när du använder Get-DscConfiguration i DebugMode</span><span class="sxs-lookup"><span data-stu-id="95125-115">LCM can go into an unstable state while using Get-DscConfiguration in DebugMode</span></span>

<span data-ttu-id="95125-116">Om LCM finns i DebugMode, trycker du på CTRL + C för att stoppa bearbetningen av `Get-DscConfiguration` kan orsaka att LCM går in i ett instabilt tillstånd så att majoriteten av DSC-cmdlets inte fungerar.</span><span class="sxs-lookup"><span data-stu-id="95125-116">If LCM is in DebugMode, pressing CTRL+C to stop the processing of `Get-DscConfiguration` can cause LCM to go into an unstable state such that majority of DSC cmdlets won’t work.</span></span>

<span data-ttu-id="95125-117">**Lösning:** Tryck inte på CTRL + C vid fel sökning av `Get-DscConfiguration` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="95125-117">**Resolution:** Don’t press CTRL+C while debugging `Get-DscConfiguration` cmdlet.</span></span>

## <a name="stop-dscconfiguration-may-not-respond-in-debugmode"></a><span data-ttu-id="95125-118">Stop-DscConfiguration får inte svara i DebugMode</span><span class="sxs-lookup"><span data-stu-id="95125-118">Stop-DscConfiguration may not respond in DebugMode</span></span>

<span data-ttu-id="95125-119">Om LCM finns i DebugMode, `Stop-DscConfiguration` kan inte svara vid försök att stoppa en åtgärd som startats av`Get-DscConfiguration`</span><span class="sxs-lookup"><span data-stu-id="95125-119">If LCM is in DebugMode, `Stop-DscConfiguration` may not respond while trying to stop an operation started by `Get-DscConfiguration`</span></span>

<span data-ttu-id="95125-120">**Lösning:** Slutför fel sökningen av åtgärden som startades av `Get-DscConfiguration` som beskrivs i [Felsöka DSC-resurser](/powershell/scripting/dsc/troubleshooting/debugResource).</span><span class="sxs-lookup"><span data-stu-id="95125-120">**Resolution:** Finish the debugging of the operation started by `Get-DscConfiguration` as outlined in [Debugging DSC resources](/powershell/scripting/dsc/troubleshooting/debugResource).</span></span>

## <a name="no-verbose-error-messages-are-shown-in-debugmode"></a><span data-ttu-id="95125-121">Inga utförliga fel meddelanden visas i DebugMode</span><span class="sxs-lookup"><span data-stu-id="95125-121">No Verbose Error Messages are shown in DebugMode</span></span>

<span data-ttu-id="95125-122">Om LCM finns i **DebugMode**, visas inga utförliga fel meddelanden från DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="95125-122">If LCM is in **DebugMode**, no verbose error messages are displayed from DSC Resources.</span></span>

<span data-ttu-id="95125-123">**Lösning:** Inaktivera **DebugMode** för att se utförliga meddelanden från resursen</span><span class="sxs-lookup"><span data-stu-id="95125-123">**Resolution:** Disable **DebugMode** to see verbose messages from the resource</span></span>

## <a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="95125-124">Invoke-Dscresource Keyword Supports-åtgärder kan inte hämtas av Get-DscConfigurationStatus-cmdleten</span><span class="sxs-lookup"><span data-stu-id="95125-124">Invoke-DscResource operations cannot be retrieved by Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="95125-125">När `Invoke-DscResource` du har använt cmdlet för att direkt anropa alla resurs metoder går det inte att hämta posterna för sådan åtgärd via `Get-DscConfigurationStatus` .</span><span class="sxs-lookup"><span data-stu-id="95125-125">After using `Invoke-DscResource` cmdlet to directly invoke any resource’s methods, the records of such operation cannot be retrieved through `Get-DscConfigurationStatus`.</span></span>

<span data-ttu-id="95125-126">**Lösning:** Alternativet.</span><span class="sxs-lookup"><span data-stu-id="95125-126">**Resolution:** None.</span></span>

## <a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a><span data-ttu-id="95125-127">Get-DscConfigurationStatus returnerar pull-cykel åtgärder som typ **konsekvens**</span><span class="sxs-lookup"><span data-stu-id="95125-127">Get-DscConfigurationStatus returns pull cycle operations as type **Consistency**</span></span>

<span data-ttu-id="95125-128">När en nod ställs in på Hämta uppdaterings läge, `Get-DscConfigurationStatus` rapporterar cmdleten åtgärds typen som **konsekvens** i stället för *initialt* för varje pull-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="95125-128">When a node is set to PULL refresh mode, for each pull operation performed, `Get-DscConfigurationStatus` cmdlet reports the operation type as **Consistency** instead of *Initial*</span></span>

<span data-ttu-id="95125-129">**Lösning:** Alternativet.</span><span class="sxs-lookup"><span data-stu-id="95125-129">**Resolution:** None.</span></span>

## <a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a><span data-ttu-id="95125-130">Invoke-Dscresource Keyword Supports-cmdlet returnerar inte meddelandet i den ordning som de producerade</span><span class="sxs-lookup"><span data-stu-id="95125-130">Invoke-DscResource cmdlet does not return message in the order they were produced</span></span>

<span data-ttu-id="95125-131">`Invoke-DscResource`Cmdleten returnerar inte utförliga, varnings-och fel meddelanden i den ordning som de producerade av LCM eller DSC-resursen.</span><span class="sxs-lookup"><span data-stu-id="95125-131">The `Invoke-DscResource` cmdlet does not return verbose, warning, and error messages in the order they were produced by LCM or the DSC resource.</span></span>

<span data-ttu-id="95125-132">**Lösning:** Alternativet.</span><span class="sxs-lookup"><span data-stu-id="95125-132">**Resolution:** None.</span></span>

## <a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a><span data-ttu-id="95125-133">DSC-resurser kan inte felsökas enkelt när de används med Invoke-Dscresource Keyword Supports</span><span class="sxs-lookup"><span data-stu-id="95125-133">DSC Resources cannot be debugged easily when used with Invoke-DscResource</span></span>

<span data-ttu-id="95125-134">När LCM körs i fel söknings läge `Invoke-DscResource` ger cmdleten inte information om körnings utrymme för att ansluta till för fel sökning.</span><span class="sxs-lookup"><span data-stu-id="95125-134">When LCM is running in debug mode, `Invoke-DscResource` cmdlet does not give information about runspace to connect to for debugging.</span></span> <span data-ttu-id="95125-135">Mer information finns i [fel sökning av DSC-resurser](/powershell/scripting/dsc/troubleshooting/debugResource).</span><span class="sxs-lookup"><span data-stu-id="95125-135">For more information, see [Debugging DSC resources](/powershell/scripting/dsc/troubleshooting/debugResource).</span></span>

<span data-ttu-id="95125-136">**Lösning:** Identifiera och Anslut till körnings utrymme med cmdlet: ar `Get-PSHostProcessInfo` , `Enter-PSHostProcess` `Get-Runspace` och `Debug-Runspace` för att felsöka DSC-resursen.</span><span class="sxs-lookup"><span data-stu-id="95125-136">**Resolution:** Discover and attach to the runspace using cmdlets `Get-PSHostProcessInfo`, `Enter-PSHostProcess` , `Get-Runspace` and `Debug-Runspace` to debug the DSC resource.</span></span>

```powershell
# Find all the processes hosting PowerShell
Get-PSHostProcessInfo

ProcessName    ProcessId AppDomainName
-----------    --------- -------------
powershell          3932 DefaultAppDomain
powershell_ise      2304 DefaultAppDomain
WmiPrvSE            3396 DscPsPluginWkr_AppDomain

# Enter the process that is hosting DSC engine (WMI process with DscPsPluginWkr_Appdomain)
Enter-PSHostProcess -Id 3396 -AppDomainName DscPsPluginWkr_AppDomain

# Find all the available rusnspaces in that process
Get-Runspace

Id Name       ComputerName Type  State  Availability
-- ----       ------------ ----  -----  ------------
 2 Runspace2  localhost    Local Opened InBreakpoint
 5 RemoteHost localhost    Local Opened Busy

# Debug the runspace that is in **InBreakpoint** availability state
Debug-Runspace -Id 2
```

## <a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a><span data-ttu-id="95125-137">Olika konfigurations dokument för samma nod får inte ha identiska resurs namn</span><span class="sxs-lookup"><span data-stu-id="95125-137">Various Partial Configuration documents for same node cannot have identical resource names</span></span>

<span data-ttu-id="95125-138">För flera delar av konfigurationer som distribueras till en enda nod kan identiska namn på resurser orsaka körnings tids fel.</span><span class="sxs-lookup"><span data-stu-id="95125-138">For several partial configurations that are deployed onto a single node, identical names of resources cause run time error.</span></span>

<span data-ttu-id="95125-139">**Lösning:** Använd olika namn för även samma resurser i olika delar av konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="95125-139">**Resolution:** Use different names for even same resources in different partial configurations.</span></span>

## <a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a><span data-ttu-id="95125-140">Start-DscConfiguration – UseExisting fungerar inte med-Credential</span><span class="sxs-lookup"><span data-stu-id="95125-140">Start-DscConfiguration –UseExisting does not work with -Credential</span></span>

<span data-ttu-id="95125-141">När `Start-DscConfiguration` du använder med parametern **UseExisting** ignoreras parametern **Credential** .</span><span class="sxs-lookup"><span data-stu-id="95125-141">When using `Start-DscConfiguration` with **UseExisting** parameter, the **Credential** parameter is ignored.</span></span> <span data-ttu-id="95125-142">DSC använder standard process identitet för att fortsätta åtgärden.</span><span class="sxs-lookup"><span data-stu-id="95125-142">DSC uses default process identity to proceed the operation.</span></span> <span data-ttu-id="95125-143">Detta orsakar fel när en annan autentiseringsuppgift krävs för att fortsätta till fjärrnoden.</span><span class="sxs-lookup"><span data-stu-id="95125-143">This causes error when a different credential is needed to proceed on remote node.</span></span>

<span data-ttu-id="95125-144">**Lösning:** Använd CIM-session för fjärran sluten DSC-åtgärder:</span><span class="sxs-lookup"><span data-stu-id="95125-144">**Resolution:** Use CIM session for remote DSC operations:</span></span>

```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```

## <a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a><span data-ttu-id="95125-145">IPv6-adresser som nodnamn i DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="95125-145">IPv6 Addresses as Node Names in DSC configurations</span></span>

<span data-ttu-id="95125-146">IPv6-adresser som nodnamn i DSC-konfigurations skript stöds inte i den här versionen.</span><span class="sxs-lookup"><span data-stu-id="95125-146">IPv6 addresses as node names in DSC configuration scripts are not supported in this release.</span></span>

<span data-ttu-id="95125-147">**Lösning:** Alternativet.</span><span class="sxs-lookup"><span data-stu-id="95125-147">**Resolution:** None.</span></span>

## <a name="debugging-of-class-based-dsc-resources"></a><span data-ttu-id="95125-148">Fel sökning av `Class-Based` DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="95125-148">Debugging of `Class-Based` DSC Resources</span></span>

<span data-ttu-id="95125-149">Fel sökning av klassbaserade DSC-resurser stöds inte i den här versionen.</span><span class="sxs-lookup"><span data-stu-id="95125-149">Debugging of class-based DSC Resources is not supported in this release.</span></span>

<span data-ttu-id="95125-150">**Lösning:** Alternativet.</span><span class="sxs-lookup"><span data-stu-id="95125-150">**Resolution:** None.</span></span>

## <a name="variables-and-functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a><span data-ttu-id="95125-151">Variabler och funktioner som definieras i $script omfång i en klass baserad DSC-resurs bevaras inte över flera anrop till en DSC-resurs</span><span class="sxs-lookup"><span data-stu-id="95125-151">Variables and functions defined in $script scope in DSC Class-Based Resource are not preserved across multiple calls to a DSC Resource</span></span>

<span data-ttu-id="95125-152">Flera anrop i följd `Start-DSCConfiguration` Miss lyckas om konfigurationen använder en klassbaserade resurs som har variabler eller funktioner definierade i `$script` området.</span><span class="sxs-lookup"><span data-stu-id="95125-152">Multiple consecutive calls to `Start-DSCConfiguration` fails if the configuration is using any class-based resource which has variables or functions defined in `$script` scope.</span></span>

<span data-ttu-id="95125-153">**Lösning:** Definiera alla variabler och funktioner i själva DSC-resurs klassen.</span><span class="sxs-lookup"><span data-stu-id="95125-153">**Resolution:** Define all variables and functions in DSC Resource class itself.</span></span> <span data-ttu-id="95125-154">Inga `$script` omfångs-variabler/-funktioner.</span><span class="sxs-lookup"><span data-stu-id="95125-154">No `$script` scope variables/functions.</span></span>

## <a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a><span data-ttu-id="95125-155">Fel sökning av DSC-resurs när en resurs använder PSDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="95125-155">DSC Resource Debugging when a resource is using PSDscRunAsCredential</span></span>

<span data-ttu-id="95125-156">DSC-resurs fel sökning när en resurs använder egenskapen **PSDscRunAsCredential** i konfigurationen stöds inte i den här versionen.</span><span class="sxs-lookup"><span data-stu-id="95125-156">DSC Resource debugging when a resource is using the **PSDscRunAsCredential** property in the configuration is not supported in this release.</span></span>

<span data-ttu-id="95125-157">**Lösning:** Alternativet.</span><span class="sxs-lookup"><span data-stu-id="95125-157">**Resolution:** None.</span></span>

## <a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a><span data-ttu-id="95125-158">PsDscRunAsCredential stöds inte för sammansatta DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="95125-158">PsDscRunAsCredential is not supported for DSC Composite Resources</span></span>

<span data-ttu-id="95125-159">**Lösning:** Använd egenskapen autentiseringsuppgifter om den är tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="95125-159">**Resolution:** Use Credential property if available.</span></span> <span data-ttu-id="95125-160">Exempel på ServiceSet och WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="95125-160">Example ServiceSet and WindowsFeatureSet</span></span>

## <a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a><span data-ttu-id="95125-161">Get-Dscresource Keyword Supports-syntaxen visar inte PsDscRunAsCredential korrekt</span><span class="sxs-lookup"><span data-stu-id="95125-161">Get-DscResource -Syntax does not reflect PsDscRunAsCredential correctly</span></span>

<span data-ttu-id="95125-162">Parametern **syntax** reflekterar inte **PsDscRunAsCredential** korrekt när resursen markerar den som obligatorisk eller inte stöder den.</span><span class="sxs-lookup"><span data-stu-id="95125-162">The **Syntax** parameter does not reflect **PsDscRunAsCredential** correctly when resource marks it as mandatory or does not support it.</span></span>

<span data-ttu-id="95125-163">**Lösning:** Alternativet.</span><span class="sxs-lookup"><span data-stu-id="95125-163">**Resolution:** None.</span></span> <span data-ttu-id="95125-164">Redigering av konfiguration i ISE visar dock korrekta metadata om **PsDscRunAsCredential** -egenskapen när du använder IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="95125-164">However, authoring configuration in ISE reflects correct metadata about **PsDscRunAsCredential** property when using IntelliSense.</span></span>

## <a name="windowsoptionalfeature-is-not-available-in-windows-7"></a><span data-ttu-id="95125-165">WindowsOptionalFeature är inte tillgängligt i Windows 7</span><span class="sxs-lookup"><span data-stu-id="95125-165">WindowsOptionalFeature is not available in Windows 7</span></span>

<span data-ttu-id="95125-166">**WindowsOptionalFeature** DSC-resursen är inte tillgänglig i Windows 7.</span><span class="sxs-lookup"><span data-stu-id="95125-166">The **WindowsOptionalFeature** DSC resource is not available in Windows 7.</span></span> <span data-ttu-id="95125-167">Den här resursen kräver DISM-modulen och DISM-cmdletar som är tillgängliga från och med Windows 8 och nyare versioner av Windows operativ system.</span><span class="sxs-lookup"><span data-stu-id="95125-167">This resource requires the DISM module, and DISM cmdlets that are available starting in Windows 8 and newer releases of the Windows operating system.</span></span>

## <a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a><span data-ttu-id="95125-168">Import-Dscresource Keyword Supports-ModuleVersion kanske inte fungerar som förväntat för klassbaserade DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="95125-168">For Class-based DSC resources, Import-DscResource -ModuleVersion may not work as expected</span></span>

<span data-ttu-id="95125-169">Om noden kompilering har flera versioner av en klass-baserad DSC-resurs, `Import-DscResource -ModuleVersion` väljer inte den angivna versionen och resulterar i följande kompileringsfel.</span><span class="sxs-lookup"><span data-stu-id="95125-169">If the compilation node has multiple versions of a class-based DSC resource module, `Import-DscResource -ModuleVersion` does not pick the specified version and results in following compilation error.</span></span>

```Output
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s):
 "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

<span data-ttu-id="95125-170">**Lösning:** Importera den version som krävs genom att definiera **ModuleSpecification** -objektet till **Modulnamn** -parametern med **RequiredVersion** -nyckeln angiven enligt följande:</span><span class="sxs-lookup"><span data-stu-id="95125-170">**Resolution:** Import the required version by defining the **ModuleSpecification** object to the **ModuleName** parameter with **RequiredVersion** key specified as follows:</span></span>

```powershell
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}
```

## <a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a><span data-ttu-id="95125-171">Vissa DSC-resurser som register resurser kan ta lång tid att bearbeta begäran.</span><span class="sxs-lookup"><span data-stu-id="95125-171">Some DSC resources like registry resource may start to take a long time to process the request.</span></span>

<span data-ttu-id="95125-172">**Lösning 1:** Skapa en schema aktivitet som rensar upp följande mapp med jämna mellanrum.</span><span class="sxs-lookup"><span data-stu-id="95125-172">**Resolution 1:** Create a schedule task that cleans up the following folder periodically.</span></span>

```powershell
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis
```

<span data-ttu-id="95125-173">**Lösning 2:** Ändra DSC-konfigurationen för att rensa mappen *CommandAnalysis* i slutet av konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="95125-173">**Resolution 2:** Change the DSC configuration to clean up the *CommandAnalysis* folder at the end of the configuration.</span></span>

```powershell
Configuration $configName
{

   # User Data
    Registry SetRegisteredOwner
    {
        Ensure = 'Present'
        Force = $True
        Key = $Node.RegisteredKey
        ValueName = $Node.RegisteredOwnerValue
        ValueType = 'String'
        ValueData = $Node.RegisteredOwnerData
    }
    #
    # Script to delete the config
    #
    script DeleteCommandAnalysisCache
    {
        DependsOn = "[Registry]SetRegisteredOwner"
        getscript = "@{}"
        testscript = 'Remove-Item -Path $env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis -Force -Recurse -ErrorAction SilentlyContinue -ErrorVariable ev | out-null;$true'
        setscript = '$true'
    }
}
```
