---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Desired State Configuration (DSC) kända problem och begränsningar
ms.openlocfilehash: 6faf24795d14a93f265943029d9f6f1388f32263
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856198"
---
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a><span data-ttu-id="5526e-103">Desired State Configuration (DSC) kända problem och begränsningar</span><span class="sxs-lookup"><span data-stu-id="5526e-103">Desired State Configuration (DSC) Known Issues and Limitations</span></span>

## <a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a><span data-ttu-id="5526e-104">Icke-bakåtkompatibel ändring: Certifikat som används för att kryptera/dekryptera lösenord i DSC-konfigurationer kanske inte fungerar när du har installerat WMF 5.0 RTM</span><span class="sxs-lookup"><span data-stu-id="5526e-104">Breaking Change: Certificates used to encrypt/decrypt passwords in DSC configurations may not work after installing WMF 5.0 RTM</span></span>

<span data-ttu-id="5526e-105">I utgåvor av WMF 4.0 och WMF 5.0 Preview DSC inte tillåter lösenord i konfigurationen med längden mer än 121 tecken.</span><span class="sxs-lookup"><span data-stu-id="5526e-105">In WMF 4.0 and WMF 5.0 Preview releases, DSC would not allow passwords in the configuration to be of length more than 121 characters.</span></span> <span data-ttu-id="5526e-106">DSC tvingande använda korta lösenord, även om långvariga och starka lösenord har önskad.</span><span class="sxs-lookup"><span data-stu-id="5526e-106">DSC was forcing to use short passwords even if lengthy and strong password was desired.</span></span> <span data-ttu-id="5526e-107">Den här stor förändring kan lösenord ska vara av godtycklig längd i DSC-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="5526e-107">This breaking change allows passwords to be of arbitrary length in the DSC configuration.</span></span>

<span data-ttu-id="5526e-108">**Lösning:** Återskapa certifikatet med Datachiffrering eller chiffrering nyckeln användnings- och dokumentet kryptering förbättrad nyckelanvändning (1.3.6.1.4.1.311.80.1).</span><span class="sxs-lookup"><span data-stu-id="5526e-108">**Resolution:** Re-create the certificate with Data Encipherment or Key Encipherment Key usage, and Document Encryption Enhanced Key usage (1.3.6.1.4.1.311.80.1).</span></span> <span data-ttu-id="5526e-109">Mer information finns i [skydda CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage).</span><span class="sxs-lookup"><span data-stu-id="5526e-109">For more information, see [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage).</span></span>

## <a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a><span data-ttu-id="5526e-110">DSC-cmdletar misslyckas när du har installerat WMF 5.0 RTM</span><span class="sxs-lookup"><span data-stu-id="5526e-110">DSC cmdlets may fail after installing WMF 5.0 RTM</span></span>

<span data-ttu-id="5526e-111">`Start-DscConfiguration` och andra DSC-cmdletar misslyckas när du har installerat WMF 5.0 RTM med följande fel:</span><span class="sxs-lookup"><span data-stu-id="5526e-111">`Start-DscConfiguration` and other DSC cmdlets may fail after installing WMF 5.0 RTM with the following error:</span></span>

```Output
LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
+ CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
+ FullyQualifiedErrorId : MI RESULT 6
+ PSComputerName : localhost
```

<span data-ttu-id="5526e-112">**Lösning:** Ta bort DSCEngineCache.mof genom att köra följande kommando i en upphöjd PowerShell-session (Kör som administratör):</span><span class="sxs-lookup"><span data-stu-id="5526e-112">**Resolution:** Delete DSCEngineCache.mof by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```

## <a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a><span data-ttu-id="5526e-113">DSC-cmdlets fungerar inte om WMF 5.0 RTM installeras ovanpå WMF 5.0 produktion förhandsversion</span><span class="sxs-lookup"><span data-stu-id="5526e-113">DSC cmdlets may not work if WMF 5.0 RTM is installed on top of WMF 5.0 Production Preview</span></span>

<span data-ttu-id="5526e-114">**Lösning:** Kör följande kommando i en upphöjd PowerShell-session (Kör som administratör):</span><span class="sxs-lookup"><span data-stu-id="5526e-114">**Resolution:** Run the following command in an elevated PowerShell session (run as administrator):</span></span>

```powershell
mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```

## <a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a><span data-ttu-id="5526e-115">LCM går i ett instabilt tillstånd och Använd Get-DscConfiguration DebugMode</span><span class="sxs-lookup"><span data-stu-id="5526e-115">LCM can go into an unstable state while using Get-DscConfiguration in DebugMode</span></span>

<span data-ttu-id="5526e-116">Om LCM finns i DebugMode, att trycka på CTRL + C för att stoppa bearbetningen av `Get-DscConfiguration` kan orsaka MGM om du vill gå till ett instabilt tillstånd sådana som merparten av DSC-cmdlets fungerar inte.</span><span class="sxs-lookup"><span data-stu-id="5526e-116">If LCM is in DebugMode, pressing CTRL+C to stop the processing of `Get-DscConfiguration` can cause LCM to go into an unstable state such that majority of DSC cmdlets won’t work.</span></span>

<span data-ttu-id="5526e-117">**Lösning:** Inte på CTRL + C när du felsöker `Get-DscConfiguration` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5526e-117">**Resolution:** Don’t press CTRL+C while debugging `Get-DscConfiguration` cmdlet.</span></span>

## <a name="stop-dscconfiguration-may-not-respond-in-debugmode"></a><span data-ttu-id="5526e-118">Stop-DscConfiguration svarar inte i DebugMode</span><span class="sxs-lookup"><span data-stu-id="5526e-118">Stop-DscConfiguration may not respond in DebugMode</span></span>

<span data-ttu-id="5526e-119">Om LCM i DebugMode, `Stop-DscConfiguration` svarar inte när försök att stoppa en åtgärd igång genom att `Get-DscConfiguration`</span><span class="sxs-lookup"><span data-stu-id="5526e-119">If LCM is in DebugMode, `Stop-DscConfiguration` may not respond while trying to stop an operation started by `Get-DscConfiguration`</span></span>

<span data-ttu-id="5526e-120">**Lösning:** Slutför felsökning av åtgärden startas av `Get-DscConfiguration` som beskrivs i [felsökning DSC-resurser](/powershell/dsc/troubleshooting/debugResource).</span><span class="sxs-lookup"><span data-stu-id="5526e-120">**Resolution:** Finish the debugging of the operation started by `Get-DscConfiguration` as outlined in [Debugging DSC resources](/powershell/dsc/troubleshooting/debugResource).</span></span>

## <a name="no-verbose-error-messages-are-shown-in-debugmode"></a><span data-ttu-id="5526e-121">Inga utförlig felmeddelanden visas i DebugMode</span><span class="sxs-lookup"><span data-stu-id="5526e-121">No Verbose Error Messages are shown in DebugMode</span></span>

<span data-ttu-id="5526e-122">Om LCM i **DebugMode**, inga utförlig felmeddelanden visas från DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="5526e-122">If LCM is in **DebugMode**, no verbose error messages are displayed from DSC Resources.</span></span>

<span data-ttu-id="5526e-123">**Lösning:** Inaktivera **DebugMode** att visa utförliga meddelanden från resursen</span><span class="sxs-lookup"><span data-stu-id="5526e-123">**Resolution:** Disable **DebugMode** to see verbose messages from the resource</span></span>

## <a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="5526e-124">Anropa DscResource åtgärder kan inte hämtas med cmdleten Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="5526e-124">Invoke-DscResource operations cannot be retrieved by Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="5526e-125">När du har använt `Invoke-DscResource` cmdlet för att anropa direkt alla resurser metoder, posterna i detta går inte att hämta via `Get-DscConfigurationStatus`.</span><span class="sxs-lookup"><span data-stu-id="5526e-125">After using `Invoke-DscResource` cmdlet to directly invoke any resource’s methods, the records of such operation cannot be retrieved through `Get-DscConfigurationStatus`.</span></span>

<span data-ttu-id="5526e-126">**Lösning:** Ingen.</span><span class="sxs-lookup"><span data-stu-id="5526e-126">**Resolution:** None.</span></span>

## <a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a><span data-ttu-id="5526e-127">Get-DscConfigurationStatus returnerar pull cykel åtgärder som typen **konsekvens**</span><span class="sxs-lookup"><span data-stu-id="5526e-127">Get-DscConfigurationStatus returns pull cycle operations as type **Consistency**</span></span>

<span data-ttu-id="5526e-128">När en nod har angetts till PULL uppdatera läge för varje pull-åtgärder som utförs, `Get-DscConfigurationStatus` cmdlet rapporterar åtgärdstypen som **konsekvens** i stället för *inledande*</span><span class="sxs-lookup"><span data-stu-id="5526e-128">When a node is set to PULL refresh mode, for each pull operation performed, `Get-DscConfigurationStatus` cmdlet reports the operation type as **Consistency** instead of *Initial*</span></span>

<span data-ttu-id="5526e-129">**Lösning:** Ingen.</span><span class="sxs-lookup"><span data-stu-id="5526e-129">**Resolution:** None.</span></span>

## <a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a><span data-ttu-id="5526e-130">Anropa DscResource cmdlet returnerar inte meddelandet i den ordning som de skapas</span><span class="sxs-lookup"><span data-stu-id="5526e-130">Invoke-DscResource cmdlet does not return message in the order they were produced</span></span>

<span data-ttu-id="5526e-131">Den `Invoke-DscResource` cmdlet inte returnerar verbose, varning, och felmeddelanden i den ordning som de har producerats av LCM eller DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="5526e-131">The `Invoke-DscResource` cmdlet does not return verbose, warning, and error messages in the order they were produced by LCM or the DSC resource.</span></span>

<span data-ttu-id="5526e-132">**Lösning:** Ingen.</span><span class="sxs-lookup"><span data-stu-id="5526e-132">**Resolution:** None.</span></span>

## <a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a><span data-ttu-id="5526e-133">DSC-resurser kan inte felsökas enkelt när det används med Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="5526e-133">DSC Resources cannot be debugged easily when used with Invoke-DscResource</span></span>

<span data-ttu-id="5526e-134">När du kör i felsökningsläge och LCM `Invoke-DscResource` cmdlet ger inte information om körningsutrymme att ansluta till för felsökning.</span><span class="sxs-lookup"><span data-stu-id="5526e-134">When LCM is running in debug mode, `Invoke-DscResource` cmdlet does not give information about runspace to connect to for debugging.</span></span> <span data-ttu-id="5526e-135">Mer information finns i [felsökning DSC-resurser](/powershell/dsc/troubleshooting/debugResource).</span><span class="sxs-lookup"><span data-stu-id="5526e-135">For more information, see [Debugging DSC resources](/powershell/dsc/troubleshooting/debugResource).</span></span>

<span data-ttu-id="5526e-136">**Lösning:** Identifiera och ansluta till körningsutrymme med hjälp av cmdlet: ar `Get-PSHostProcessInfo`, `Enter-PSHostProcess` , `Get-Runspace` och `Debug-Runspace` felsöka DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="5526e-136">**Resolution:** Discover and attach to the runspace using cmdlets `Get-PSHostProcessInfo`, `Enter-PSHostProcess` , `Get-Runspace` and `Debug-Runspace` to debug the DSC resource.</span></span>

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

## <a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a><span data-ttu-id="5526e-137">Olika partiell konfiguration dokumenten för samma nod kan inte ha identiska resursnamn</span><span class="sxs-lookup"><span data-stu-id="5526e-137">Various Partial Configuration documents for same node cannot have identical resource names</span></span>

<span data-ttu-id="5526e-138">För flera partiella konfigurationer som har distribuerats till en enda nod, kör identiska namn för resurser orsak fel.</span><span class="sxs-lookup"><span data-stu-id="5526e-138">For several partial configurations that are deployed onto a single node, identical names of resources cause run time error.</span></span>

<span data-ttu-id="5526e-139">**Lösning:** Använda olika namn för även samma resurser i olika partiella konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="5526e-139">**Resolution:** Use different names for even same resources in different partial configurations.</span></span>

## <a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a><span data-ttu-id="5526e-140">Start-DscConfiguration – UseExisting fungerar inte med - autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="5526e-140">Start-DscConfiguration –UseExisting does not work with -Credential</span></span>

<span data-ttu-id="5526e-141">När du använder `Start-DscConfiguration` med **UseExisting** parameter, den **Credential** parametern ignoreras.</span><span class="sxs-lookup"><span data-stu-id="5526e-141">When using `Start-DscConfiguration` with **UseExisting** parameter, the **Credential** parameter is ignored.</span></span> <span data-ttu-id="5526e-142">DSC använder standard-ID för att fortsätta åtgärden.</span><span class="sxs-lookup"><span data-stu-id="5526e-142">DSC uses default process identity to proceed the operation.</span></span> <span data-ttu-id="5526e-143">Detta orsakar fel när andra autentiseringsuppgifter krävs för att fortsätta på fjärrnoden.</span><span class="sxs-lookup"><span data-stu-id="5526e-143">This causes error when a different credential is needed to proceed on remote node.</span></span>

<span data-ttu-id="5526e-144">**Lösning:** Använda CIM-session för DSC-fjärråtgärder:</span><span class="sxs-lookup"><span data-stu-id="5526e-144">**Resolution:** Use CIM session for remote DSC operations:</span></span>

```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```

## <a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a><span data-ttu-id="5526e-145">IPv6-adresser som nodnamn i DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="5526e-145">IPv6 Addresses as Node Names in DSC configurations</span></span>

<span data-ttu-id="5526e-146">IPv6-adresser som noden i DSC-konfigurationsskript stöds inte i den här versionen.</span><span class="sxs-lookup"><span data-stu-id="5526e-146">IPv6 addresses as node names in DSC configuration scripts are not supported in this release.</span></span>

<span data-ttu-id="5526e-147">**Lösning:** Ingen.</span><span class="sxs-lookup"><span data-stu-id="5526e-147">**Resolution:** None.</span></span>

## <a name="debugging-of-class-based-dsc-resources"></a><span data-ttu-id="5526e-148">Felsökning av `Class-Based` DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="5526e-148">Debugging of `Class-Based` DSC Resources</span></span>

<span data-ttu-id="5526e-149">Felsökning av klassbaserade DSC-resurser stöds inte i den här versionen.</span><span class="sxs-lookup"><span data-stu-id="5526e-149">Debugging of class-based DSC Resources is not supported in this release.</span></span>

<span data-ttu-id="5526e-150">**Lösning:** Ingen.</span><span class="sxs-lookup"><span data-stu-id="5526e-150">**Resolution:** None.</span></span>

## <a name="variables-and-functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a><span data-ttu-id="5526e-151">Variabler och funktioner som definierats i $script omfånget i DSC MOF-baserade Resource bevaras inte mellan flera anrop till en DSC-resurs</span><span class="sxs-lookup"><span data-stu-id="5526e-151">Variables and functions defined in $script scope in DSC Class-Based Resource are not preserved across multiple calls to a DSC Resource</span></span>

<span data-ttu-id="5526e-152">Flera på varandra följande anrop till `Start-DSCConfiguration` misslyckas om konfigurationen använder en MOF-baserade resurs som har variabler eller funktioner som definierats i `$script` omfång.</span><span class="sxs-lookup"><span data-stu-id="5526e-152">Multiple consecutive calls to `Start-DSCConfiguration` fails if the configuration is using any class-based resource which has variables or functions defined in `$script` scope.</span></span>

<span data-ttu-id="5526e-153">**Lösning:** Definiera alla variabler och funktioner i DSC resursklass själva.</span><span class="sxs-lookup"><span data-stu-id="5526e-153">**Resolution:** Define all variables and functions in DSC Resource class itself.</span></span> <span data-ttu-id="5526e-154">Inte `$script` omfång för variabler/funktioner.</span><span class="sxs-lookup"><span data-stu-id="5526e-154">No `$script` scope variables/functions.</span></span>

## <a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a><span data-ttu-id="5526e-155">DSC-resurs felsökning när en resurs använder PSDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="5526e-155">DSC Resource Debugging when a resource is using PSDscRunAsCredential</span></span>

<span data-ttu-id="5526e-156">DSC-resurs felsökning när en resurs använder den **PSDscRunAsCredential** egenskapen i konfigurationen stöds inte i den här versionen.</span><span class="sxs-lookup"><span data-stu-id="5526e-156">DSC Resource debugging when a resource is using the **PSDscRunAsCredential** property in the configuration is not supported in this release.</span></span>

<span data-ttu-id="5526e-157">**Lösning:** Ingen.</span><span class="sxs-lookup"><span data-stu-id="5526e-157">**Resolution:** None.</span></span>

## <a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a><span data-ttu-id="5526e-158">PsDscRunAsCredential stöds inte för DSC sammansatta resurser</span><span class="sxs-lookup"><span data-stu-id="5526e-158">PsDscRunAsCredential is not supported for DSC Composite Resources</span></span>

<span data-ttu-id="5526e-159">**Lösning:** Använda Credential-egenskapen om det är tillgängligt.</span><span class="sxs-lookup"><span data-stu-id="5526e-159">**Resolution:** Use Credential property if available.</span></span> <span data-ttu-id="5526e-160">Exempel ServiceSet och WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="5526e-160">Example ServiceSet and WindowsFeatureSet</span></span>

## <a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a><span data-ttu-id="5526e-161">Get-DscResource-Syntax avspeglar inte PsDscRunAsCredential korrekt</span><span class="sxs-lookup"><span data-stu-id="5526e-161">Get-DscResource -Syntax does not reflect PsDscRunAsCredential correctly</span></span>

<span data-ttu-id="5526e-162">Den **Syntax** parametern avspeglar inte **PsDscRunAsCredential** korrekt när resursen markeras som obligatoriska eller har inte stöd för den.</span><span class="sxs-lookup"><span data-stu-id="5526e-162">The **Syntax** parameter does not reflect **PsDscRunAsCredential** correctly when resource marks it as mandatory or does not support it.</span></span>

<span data-ttu-id="5526e-163">**Lösning:** Ingen.</span><span class="sxs-lookup"><span data-stu-id="5526e-163">**Resolution:** None.</span></span> <span data-ttu-id="5526e-164">Dock redigera konfigurationen i ISE visar rätt metadata om **PsDscRunAsCredential** egenskapen när du använder IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="5526e-164">However, authoring configuration in ISE reflects correct metadata about **PsDscRunAsCredential** property when using IntelliSense.</span></span>

## <a name="windowsoptionalfeature-is-not-available-in-windows-7"></a><span data-ttu-id="5526e-165">WindowsOptionalFeature är inte tillgänglig i Windows 7</span><span class="sxs-lookup"><span data-stu-id="5526e-165">WindowsOptionalFeature is not available in Windows 7</span></span>

<span data-ttu-id="5526e-166">Den **WindowsOptionalFeature** DSC-resursen är inte tillgänglig i Windows 7.</span><span class="sxs-lookup"><span data-stu-id="5526e-166">The **WindowsOptionalFeature** DSC resource is not available in Windows 7.</span></span> <span data-ttu-id="5526e-167">Den här resursen kräver DISM-modulen och DISM-cmdletar som är tillgängliga från och med Windows 8 och senare versioner av Windows-operativsystemet.</span><span class="sxs-lookup"><span data-stu-id="5526e-167">This resource requires the DISM module, and DISM cmdlets that are available starting in Windows 8 and newer releases of the Windows operating system.</span></span>

## <a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a><span data-ttu-id="5526e-168">Klassbaserade DSC-resurser, kanske Import-DscResource - ModuleVersion inte fungerar som förväntat</span><span class="sxs-lookup"><span data-stu-id="5526e-168">For Class-based DSC resources, Import-DscResource -ModuleVersion may not work as expected</span></span>

<span data-ttu-id="5526e-169">Om noden kompilering har flera versioner av en klassbaserade DSC-resurs-modul, `Import-DscResource -ModuleVersion` inte hämtar den angivna versionen och resulterar i följande kompileringsfel.</span><span class="sxs-lookup"><span data-stu-id="5526e-169">If the compilation node has multiple versions of a class-based DSC resource module, `Import-DscResource -ModuleVersion` does not pick the specified version and results in following compilation error.</span></span>

```Output
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s):
 "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

<span data-ttu-id="5526e-170">**Lösning:** Importera versionen som krävs genom att definiera den **ModuleSpecification** objekt till den **ModuleName** parameter med **RequiredVersion** nyckeln som anges på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="5526e-170">**Resolution:** Import the required version by defining the **ModuleSpecification** object to the **ModuleName** parameter with **RequiredVersion** key specified as follows:</span></span>

```powershell
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}
```

## <a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a><span data-ttu-id="5526e-171">Vissa DSC-resurser som Registerresurser kan börja ta lång tid att bearbeta begäran.</span><span class="sxs-lookup"><span data-stu-id="5526e-171">Some DSC resources like registry resource may start to take a long time to process the request.</span></span>

<span data-ttu-id="5526e-172">**Lösning 1:** Skapa en schemalagd aktivitet som rensar upp följande mapp med jämna mellanrum.</span><span class="sxs-lookup"><span data-stu-id="5526e-172">**Resolution 1:** Create a schedule task that cleans up the following folder periodically.</span></span>

```powershell
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis
```

<span data-ttu-id="5526e-173">**Lösning 2:** Ändra DSC-konfiguration för att rensa den *CommandAnalysis* mappen i slutet av konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="5526e-173">**Resolution 2:** Change the DSC configuration to clean up the *CommandAnalysis* folder at the end of the configuration.</span></span>

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
