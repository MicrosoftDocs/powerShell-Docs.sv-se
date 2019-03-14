---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 883f80a5c8c99f2ab9886558a7aebfe1204f3be6
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795155"
---
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a><span data-ttu-id="f202d-102">Desired State Configuration (DSC) kända problem och begränsningar</span><span class="sxs-lookup"><span data-stu-id="f202d-102">Desired State Configuration (DSC) Known Issues and Limitations</span></span>

## <a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a><span data-ttu-id="f202d-103">Icke-bakåtkompatibel ändring: Certifikat som används för att kryptera/dekryptera lösenord i DSC-konfigurationer kanske inte fungerar när du har installerat WMF 5.0 RTM</span><span class="sxs-lookup"><span data-stu-id="f202d-103">Breaking Change: Certificates used to encrypt/decrypt passwords in DSC configurations may not work after installing WMF 5.0 RTM</span></span>

<span data-ttu-id="f202d-104">I utgåvor av WMF 4.0 och WMF 5.0 Preview DSC inte tillåter lösenord i konfigurationen med längden mer än 121 tecken.</span><span class="sxs-lookup"><span data-stu-id="f202d-104">In WMF 4.0 and WMF 5.0 Preview releases, DSC would not allow passwords in the configuration to be of length more than 121 characters.</span></span> <span data-ttu-id="f202d-105">DSC tvingande använda korta lösenord, även om långvariga och starka lösenord har önskad.</span><span class="sxs-lookup"><span data-stu-id="f202d-105">DSC was forcing to use short passwords even if lengthy and strong password was desired.</span></span> <span data-ttu-id="f202d-106">Den här stor förändring kan lösenord ska vara av godtycklig längd i DSC-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="f202d-106">This breaking change allows passwords to be of arbitrary length in the DSC configuration.</span></span>

<span data-ttu-id="f202d-107">**Lösning:** Återskapa certifikatet med Datachiffrering eller chiffrering nyckeln användnings- och dokumentet kryptering förbättrad nyckelanvändning (1.3.6.1.4.1.311.80.1).</span><span class="sxs-lookup"><span data-stu-id="f202d-107">**Resolution:** Re-create the certificate with Data Encipherment or Key Encipherment Key usage, and Document Encryption Enhanced Key usage (1.3.6.1.4.1.311.80.1).</span></span> <span data-ttu-id="f202d-108">TechNet-artikeln <https://technet.microsoft.com/library/dn807171.aspx> innehåller mer information.</span><span class="sxs-lookup"><span data-stu-id="f202d-108">Technet article <https://technet.microsoft.com/library/dn807171.aspx> has more information.</span></span>

## <a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a><span data-ttu-id="f202d-109">DSC-cmdletar misslyckas när du har installerat WMF 5.0 RTM</span><span class="sxs-lookup"><span data-stu-id="f202d-109">DSC cmdlets may fail after installing WMF 5.0 RTM</span></span>

<span data-ttu-id="f202d-110">Start-DscConfiguration och andra DSC-cmdletar misslyckas när du har installerat WMF 5.0 RTM med följande fel:</span><span class="sxs-lookup"><span data-stu-id="f202d-110">Start-DscConfiguration and other DSC cmdlets may fail after installing WMF 5.0 RTM with the following error:</span></span>
```powershell
    LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
    + CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
    + FullyQualifiedErrorId : MI RESULT 6
    + PSComputerName : localhost
```

<span data-ttu-id="f202d-111">**Lösning:** Ta bort DSCEngineCache.mof genom att köra följande kommando i en upphöjd PowerShell-session (Kör som administratör):</span><span class="sxs-lookup"><span data-stu-id="f202d-111">**Resolution:** Delete DSCEngineCache.mof by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```

## <a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a><span data-ttu-id="f202d-112">DSC-cmdlets fungerar inte om WMF 5.0 RTM installeras ovanpå WMF 5.0 produktion förhandsversion</span><span class="sxs-lookup"><span data-stu-id="f202d-112">DSC cmdlets may not work if WMF 5.0 RTM is installed on top of WMF 5.0 Production Preview</span></span>

<span data-ttu-id="f202d-113">**Lösning:** Kör följande kommando i en upphöjd PowerShell-session (Kör som administratör):</span><span class="sxs-lookup"><span data-stu-id="f202d-113">**Resolution:** Run the following command in an elevated PowerShell session (run as administrator):</span></span>
```powershell
    mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```

## <a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a><span data-ttu-id="f202d-114">LCM går i ett instabilt tillstånd och Använd Get-DscConfiguration DebugMode</span><span class="sxs-lookup"><span data-stu-id="f202d-114">LCM can go into an unstable state while using Get-DscConfiguration in DebugMode</span></span>

<span data-ttu-id="f202d-115">Om LCM finns i DebugMode, att trycka på CTRL + C för att stoppa bearbetningen av Get-DscConfiguration kan orsaka MGM om du vill gå till ett instabilt tillstånd sådana som merparten av DSC-cmdlets fungerar inte.</span><span class="sxs-lookup"><span data-stu-id="f202d-115">If LCM is in DebugMode, pressing CTRL+C to stop the processing of Get-DscConfiguration can cause LCM to go into an unstable state such that majority of DSC cmdlets won’t work.</span></span>

<span data-ttu-id="f202d-116">**Lösning:** Inte på CTRL + C när du felsöker Get-DscConfiguration-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f202d-116">**Resolution:** Don’t press CTRL+C while debugging Get-DscConfiguration cmdlet.</span></span>

## <a name="stop-dscconfiguration-may-not-respond-in-debugmode"></a><span data-ttu-id="f202d-117">Stop-DscConfiguration svarar inte i DebugMode</span><span class="sxs-lookup"><span data-stu-id="f202d-117">Stop-DscConfiguration may not respond in DebugMode</span></span>

<span data-ttu-id="f202d-118">Om LCM finns i DebugMode, kanske Stop-DscConfiguration inte svarar när försök att stoppa en åtgärd startas av Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="f202d-118">If LCM is in DebugMode, Stop-DscConfiguration may not respond while trying to stop an operation started by Get-DscConfiguration</span></span>

<span data-ttu-id="f202d-119">**Lösning:** Slutför felsökning av åtgärden startas av Get-DscConfiguration som beskrivs i avsnittet ”[felsökning DSC-resurser](https://msdn.microsoft.com/powershell/dsc/debugresource)'.</span><span class="sxs-lookup"><span data-stu-id="f202d-119">**Resolution:** Finish the debugging of the operation started by Get-DscConfiguration as outlined in section ‘[Debugging DSC resources](https://msdn.microsoft.com/powershell/dsc/debugresource)’.</span></span>

## <a name="no-verbose-error-messages-are-shown-in-debugmode"></a><span data-ttu-id="f202d-120">Inga utförlig felmeddelanden visas i DebugMode</span><span class="sxs-lookup"><span data-stu-id="f202d-120">No Verbose Error Messages are shown in DebugMode</span></span>

<span data-ttu-id="f202d-121">Om LCM finns i DebugMode, visas inga utförlig felmeddelanden från DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="f202d-121">If LCM is in DebugMode, no verbose error messages are displayed from DSC Resources.</span></span>

<span data-ttu-id="f202d-122">**Lösning:** Inaktivera *DebugMode* att visa utförliga meddelanden från resursen</span><span class="sxs-lookup"><span data-stu-id="f202d-122">**Resolution:** Disable *DebugMode* to see verbose messages from the resource</span></span>

## <a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="f202d-123">Anropa DscResource åtgärder kan inte hämtas med cmdleten Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="f202d-123">Invoke-DscResource operations cannot be retrieved by Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="f202d-124">När du använder cmdleten Invoke-DscResource direkt anropa metoder för en resurs, går inte poster i en sådan åtgärd att hämta via Get-DscConfigurationStatus vid ett senare tillfälle.</span><span class="sxs-lookup"><span data-stu-id="f202d-124">After using Invoke-DscResource cmdlet to directly invoke any resource’s methods, the records of such operation cannot be retrieved through Get-DscConfigurationStatus at a later time.</span></span>

<span data-ttu-id="f202d-125">**Lösning:** Ingen.</span><span class="sxs-lookup"><span data-stu-id="f202d-125">**Resolution:** None.</span></span>

## <a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a><span data-ttu-id="f202d-126">Get-DscConfigurationStatus returnerar pull cykel åtgärder som typen *konsekvens*</span><span class="sxs-lookup"><span data-stu-id="f202d-126">Get-DscConfigurationStatus returns pull cycle operations as type *Consistency*</span></span>

<span data-ttu-id="f202d-127">När en nod har angetts till PULL uppdatera läge för varje pull-åtgärder som utförs, Get-DscConfigurationStatus cmdlet rapporterar åtgärdstypen som *konsekvens* i stället för *inledande*</span><span class="sxs-lookup"><span data-stu-id="f202d-127">When a node is set to PULL refresh mode, for each pull operation performed, Get-DscConfigurationStatus cmdlet reports the operation type as *Consistency* instead of *Initial*</span></span>

<span data-ttu-id="f202d-128">**Lösning:** Ingen.</span><span class="sxs-lookup"><span data-stu-id="f202d-128">**Resolution:** None.</span></span>

## <a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a><span data-ttu-id="f202d-129">Anropa DscResource cmdlet returnerar inte meddelandet i den ordning som de skapas</span><span class="sxs-lookup"><span data-stu-id="f202d-129">Invoke-DscResource cmdlet does not return message in the order they were produced</span></span>

<span data-ttu-id="f202d-130">Cmdleten Invoke-DscResource returnerar inte utförlig, varning, och felmeddelanden i den ordning som de har producerats av LCM eller DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="f202d-130">The Invoke-DscResource cmdlet does not return verbose, warning, and error messages in the order they were produced by LCM or the DSC resource.</span></span>

<span data-ttu-id="f202d-131">**Lösning:** Ingen.</span><span class="sxs-lookup"><span data-stu-id="f202d-131">**Resolution:** None.</span></span>

## <a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a><span data-ttu-id="f202d-132">DSC-resurser kan inte felsökas enkelt när det används med Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="f202d-132">DSC Resources cannot be debugged easily when used with Invoke-DscResource</span></span>

<span data-ttu-id="f202d-133">När LCM körs i felsökningsläge (se [felsökning DSC-resurser](https://msdn.microsoft.com/powershell/dsc/debugresource) för mer information), Invoke-DscResource cmdlet ger inte information om körningsutrymme att ansluta till för felsökning.</span><span class="sxs-lookup"><span data-stu-id="f202d-133">When LCM is running in debug mode (see [Debugging DSC resources](https://msdn.microsoft.com/powershell/dsc/debugresource) for more details), Invoke-DscResource cmdlet does not give information about runspace to connect to for debugging.</span></span>
<span data-ttu-id="f202d-134">**Lösning:** Identifiera och ansluta till körningsutrymme med hjälp av cmdlet: ar **Get-PSHostProcessInfo**, **RETUR PSHostProcess** , **Get-Körningsutrymme** och **Debug-Körningsutrymme** felsöka DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="f202d-134">**Resolution:** Discover and attach to the runspace using cmdlets **Get-PSHostProcessInfo**, **Enter-PSHostProcess** , **Get-Runspace** and **Debug-Runspace** to debug the DSC resource.</span></span>

```powershell
# Find all the processes hosting PowerShell
Get-PSHostProcessInfo

ProcessName ProcessId AppDomainName
----------- --------- -------------
powershell 3932 DefaultAppDomain
powershell_ise 2304 DefaultAppDomain
WmiPrvSE 3396 DscPsPluginWkr_AppDomain

# Enter the process that is hosting DSC engine (WMI process with DscPsPluginWkr_Appdomain)
Enter-PSHostProcess -Id 3396 -AppDomainName DscPsPluginWkr_AppDomain

# Find all the available rusnspaces in that process
Get-Runspace

Id Name ComputerName Type State Availability
-- ---- ------------ ---- ----- ------------
2 Runspace2 localhost Local Opened InBreakpoint
5 RemoteHost localhost Local Opened Busy

# Debug the runspace that is in **InBreakpoint** availability state
Debug-Runspace -Id 2
```

## <a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a><span data-ttu-id="f202d-135">Olika partiell konfiguration dokumenten för samma nod kan inte ha identiska resursnamn</span><span class="sxs-lookup"><span data-stu-id="f202d-135">Various Partial Configuration documents for same node cannot have identical resource names</span></span>

<span data-ttu-id="f202d-136">För flera partiella konfigurationer som har distribuerats till en enda nod, kör identiska namn för resurser orsak fel.</span><span class="sxs-lookup"><span data-stu-id="f202d-136">For several partial configurations that are deployed onto a single node, identical names of resources cause run time error.</span></span>

<span data-ttu-id="f202d-137">**Lösning:** Använda olika namn för även samma resurser i olika partiella konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="f202d-137">**Resolution:** Use different names for even same resources in different partial configurations.</span></span>

## <a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a><span data-ttu-id="f202d-138">Start-DscConfiguration – UseExisting fungerar inte med - autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="f202d-138">Start-DscConfiguration –UseExisting does not work with -Credential</span></span>

<span data-ttu-id="f202d-139">När du använder Start-DscConfiguration med parametern – UseExisting – Credential parametern ignoreras.</span><span class="sxs-lookup"><span data-stu-id="f202d-139">When using Start-DscConfiguration with –UseExisting parameter, the –Credential parameter is ignored.</span></span> <span data-ttu-id="f202d-140">DSC använder standard-ID för att fortsätta åtgärden.</span><span class="sxs-lookup"><span data-stu-id="f202d-140">DSC uses default process identity to proceed the operation.</span></span> <span data-ttu-id="f202d-141">Detta orsakar fel när andra autentiseringsuppgifter krävs för att fortsätta på fjärrnoden.</span><span class="sxs-lookup"><span data-stu-id="f202d-141">This causes error when a different credential is needed to proceed on remote node.</span></span>

<span data-ttu-id="f202d-142">**Lösning:** Använda CIM-session för DSC-fjärråtgärder:</span><span class="sxs-lookup"><span data-stu-id="f202d-142">**Resolution:** Use CIM session for remote DSC operations:</span></span>
```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```

## <a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a><span data-ttu-id="f202d-143">IPv6-adresser som nodnamn i DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="f202d-143">IPv6 Addresses as Node Names in DSC configurations</span></span>

<span data-ttu-id="f202d-144">IPv6-adresser som noden i DSC-konfigurationsskript stöds inte i den här versionen.</span><span class="sxs-lookup"><span data-stu-id="f202d-144">IPv6 addresses as node names in DSC configuration scripts are not supported in this release.</span></span>

<span data-ttu-id="f202d-145">**Lösning:** Ingen.</span><span class="sxs-lookup"><span data-stu-id="f202d-145">**Resolution:** None.</span></span>

## <a name="debugging-of-class-based-dsc-resources"></a><span data-ttu-id="f202d-146">Felsökning av klassbaserade DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="f202d-146">Debugging of Class-Based DSC Resources</span></span>

<span data-ttu-id="f202d-147">Felsökning av klassbaserade DSC-resurser stöds inte i den här versionen.</span><span class="sxs-lookup"><span data-stu-id="f202d-147">Debugging of class-based DSC Resources is not supported in this release.</span></span>

<span data-ttu-id="f202d-148">**Lösning:** Ingen.</span><span class="sxs-lookup"><span data-stu-id="f202d-148">**Resolution:** None.</span></span>

## <a name="variables--functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a><span data-ttu-id="f202d-149">Variabler & funktioner som definierats i $script omfånget i DSC MOF-baserade Resource bevaras inte mellan flera anrop till en DSC-resurs</span><span class="sxs-lookup"><span data-stu-id="f202d-149">Variables & Functions defined in $script scope in DSC Class-Based Resource are not preserved across multiple calls to a DSC Resource</span></span>

<span data-ttu-id="f202d-150">Flera på varandra följande anrop till Start-DSCConfiguration misslyckas om konfigurationen använder en MOF-baserade resurs som har variabler eller funktioner som definierats i $script omfånget.</span><span class="sxs-lookup"><span data-stu-id="f202d-150">Multiple consecutive calls to Start-DSCConfiguration will fail if configuration is using any class-based resource which has variables or functions defined in $script scope.</span></span>

<span data-ttu-id="f202d-151">**Lösning:** Definiera alla variabler och funktioner i DSC resursklass själva.</span><span class="sxs-lookup"><span data-stu-id="f202d-151">**Resolution:** Define all variables and functions in DSC Resource class itself.</span></span> <span data-ttu-id="f202d-152">No $script omfång variabler/funktioner.</span><span class="sxs-lookup"><span data-stu-id="f202d-152">No $script scope variables/functions.</span></span>

## <a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a><span data-ttu-id="f202d-153">DSC-resurs felsökning när en resurs använder PSDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="f202d-153">DSC Resource Debugging when a resource is using PSDscRunAsCredential</span></span>

<span data-ttu-id="f202d-154">DSC-resurs felsökning när en resurs använder den *PSDscRunAsCredential* -egenskapen i konfigurationen stöds inte i den här versionen.</span><span class="sxs-lookup"><span data-stu-id="f202d-154">DSC Resource debugging when a resource is using the *PSDscRunAsCredential* property in the configuration is not suported in this release.</span></span>

<span data-ttu-id="f202d-155">**Lösning:** Ingen.</span><span class="sxs-lookup"><span data-stu-id="f202d-155">**Resolution:** None.</span></span>

## <a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a><span data-ttu-id="f202d-156">PsDscRunAsCredential stöds inte för DSC sammansatta resurser</span><span class="sxs-lookup"><span data-stu-id="f202d-156">PsDscRunAsCredential is not supported for DSC Composite Resources</span></span>

<span data-ttu-id="f202d-157">**Lösning:** Använda Credential-egenskapen om det är tillgängligt.</span><span class="sxs-lookup"><span data-stu-id="f202d-157">**Resolution:** Use Credential property if available.</span></span> <span data-ttu-id="f202d-158">Exempel ServiceSet och WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="f202d-158">Example ServiceSet and WindowsFeatureSet</span></span>

## <a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a><span data-ttu-id="f202d-159">*Get-DscResource-Syntax* PsDscRunAsCredential avspeglar inte korrekt</span><span class="sxs-lookup"><span data-stu-id="f202d-159">*Get-DscResource -Syntax* does not reflect PsDscRunAsCredential correctly</span></span>

<span data-ttu-id="f202d-160">Get-DscResource-Syntax avspeglar inte PsDscRunAsCredential korrekt när resursen markeras som obligatoriska eller har inte stöd för den.</span><span class="sxs-lookup"><span data-stu-id="f202d-160">Get-DscResource -Syntax does not reflect PsDscRunAsCredential correctly when resource marks it as mandatory or does not support it.</span></span>

<span data-ttu-id="f202d-161">**Lösning:** Ingen.</span><span class="sxs-lookup"><span data-stu-id="f202d-161">**Resolution:** None.</span></span> <span data-ttu-id="f202d-162">Dock visar redigera konfigurationen i ISE rätt metadata om PsDscRunAsCredential egenskapen när du använder IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="f202d-162">However, authoring configuration in ISE reflects correct metadata about PsDscRunAsCredential property when using IntelliSense.</span></span>

## <a name="windowsoptionalfeature-is-not-available-in-windows-7"></a><span data-ttu-id="f202d-163">WindowsOptionalFeature är inte tillgänglig i Windows 7</span><span class="sxs-lookup"><span data-stu-id="f202d-163">WindowsOptionalFeature is not available in Windows 7</span></span>

<span data-ttu-id="f202d-164">WindowsOptionalFeature DSC-resursen är inte tillgänglig i Windows 7.</span><span class="sxs-lookup"><span data-stu-id="f202d-164">The WindowsOptionalFeature DSC resource is not available in Windows 7.</span></span> <span data-ttu-id="f202d-165">Den här resursen kräver DISM-modulen och DISM-cmdletar som är tillgängliga från och med Windows 8 och senare versioner av Windows-operativsystemet.</span><span class="sxs-lookup"><span data-stu-id="f202d-165">This resource requires the DISM module, and DISM cmdlets that are available starting in Windows 8 and newer releases of the Windows operating system.</span></span>

## <a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a><span data-ttu-id="f202d-166">Klassbaserade DSC-resurser, kanske Import-DscResource - ModuleVersion inte fungerar som förväntat</span><span class="sxs-lookup"><span data-stu-id="f202d-166">For Class-based DSC resources, Import-DscResource -ModuleVersion may not work as expected</span></span>

<span data-ttu-id="f202d-167">Om noden kompilering har flera version av en klassbaserade DSC-Resursmodul, `Import-DscResource -ModuleVersion` inte hämtar den angivna versionen och resulterar i följande kompileringsfel.</span><span class="sxs-lookup"><span data-stu-id="f202d-167">If the compilation node has multiple version of a class-based DSC resource module, `Import-DscResource -ModuleVersion` does not pick the specified version and results in following compilation error.</span></span>

```
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s): "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

<span data-ttu-id="f202d-168">**Lösning:** Importera versionen som krävs genom att definiera den *ModuleSpecification* objekt till den `-ModuleName` med `RequiredVersion` nyckeln som anges på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="f202d-168">**Resolution:** Import the required version by defining the *ModuleSpecification* object to the `-ModuleName` with `RequiredVersion` key specified as follows:</span></span>

``` PowerShell
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}
```

## <a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a><span data-ttu-id="f202d-169">Vissa DSC-resurser som Registerresurser kan börja ta lång tid att bearbeta begäran.</span><span class="sxs-lookup"><span data-stu-id="f202d-169">Some DSC resources like registry resource may start to take a long time to process the request.</span></span>

<span data-ttu-id="f202d-170">**Resolution1:** Skapa en schemalagd aktivitet som rensar upp följande mapp med jämna mellanrum.</span><span class="sxs-lookup"><span data-stu-id="f202d-170">**Resolution1:** Create a schedule task that cleans up the following folder periodically.</span></span>

``` PowerShell
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis
```

<span data-ttu-id="f202d-171">**Resolution2:** Ändra DSC-konfiguration för att rensa den *CommandAnalysis* mappen i slutet av konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="f202d-171">**Resolution2:** Change the DSC configuration to clean up the *CommandAnalysis* folder at the end of the configuration.</span></span>

``` PowerShell
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
        DependsOn="[Registry]SetRegisteredOwner"
        getscript="@{}"
        testscript = 'Remove-Item -Path $env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis -Force -Recurse -ErrorAction SilentlyContinue -ErrorVariable ev | out-null;$true'
        setscript = '$true'
    }
}
```
