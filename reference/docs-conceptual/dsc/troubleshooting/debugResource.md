---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Felsöka DSC-resurser
ms.openlocfilehash: c088e13a25ba31ceebaf52b2d24b5d32b96ae2fc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71942162"
---
# <a name="debugging-dsc-resources"></a><span data-ttu-id="8d0b0-103">Felsöka DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="8d0b0-103">Debugging DSC resources</span></span>

> <span data-ttu-id="8d0b0-104">Gäller för: Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="8d0b0-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="8d0b0-105">I PowerShell 5,0 introducerades en ny funktion i önskad tillstånds konfiguration (DSC) som gör att du kan felsöka en DSC-resurs när en konfiguration tillämpas.</span><span class="sxs-lookup"><span data-stu-id="8d0b0-105">In PowerShell 5.0, a new feature was introduced in Desired State Configuration (DSC) that allows you to debug a DSC resource as a configuration is being applied.</span></span>

## <a name="enabling-dsc-debugging"></a><span data-ttu-id="8d0b0-106">Aktivera DSC-felsökning</span><span class="sxs-lookup"><span data-stu-id="8d0b0-106">Enabling DSC debugging</span></span>
<span data-ttu-id="8d0b0-107">Innan du kan felsöka en resurs måste du aktivera fel sökning genom att anropa cmdleten [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug) .</span><span class="sxs-lookup"><span data-stu-id="8d0b0-107">Before you can debug a resource, you have to enable debugging by calling the [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug) cmdlet.</span></span>
<span data-ttu-id="8d0b0-108">Denna cmdlet använder en obligatorisk parameter, **BreakAll**.</span><span class="sxs-lookup"><span data-stu-id="8d0b0-108">This cmdlet takes a mandatory parameter, **BreakAll**.</span></span>

<span data-ttu-id="8d0b0-109">Du kan kontrol lera att fel sökning har Aktiver ATS genom att titta på resultatet av ett anrop till [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager).</span><span class="sxs-lookup"><span data-stu-id="8d0b0-109">You can verify that debugging has been enabled by looking at the result of a call to [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager).</span></span>

<span data-ttu-id="8d0b0-110">Följande PowerShell-utdata visar resultatet av att aktivera fel sökning:</span><span class="sxs-lookup"><span data-stu-id="8d0b0-110">The following PowerShell output shows the result of enabling debugging:</span></span>


```powershell
PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
NONE

PS C:\DebugTest> Enable-DscDebug -BreakAll

PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
ForceModuleImport
ResourceScriptBreakAll

PS C:\DebugTest>
```


## <a name="starting-a-configuration-with-debug-enabled"></a><span data-ttu-id="8d0b0-111">Starta en konfiguration med fel sökning aktiverat</span><span class="sxs-lookup"><span data-stu-id="8d0b0-111">Starting a configuration with debug enabled</span></span>
<span data-ttu-id="8d0b0-112">Om du vill felsöka en DSC-resurs startar du en konfiguration som anropar resursen.</span><span class="sxs-lookup"><span data-stu-id="8d0b0-112">To debug a DSC resource, you start a configuration that calls that resource.</span></span>
<span data-ttu-id="8d0b0-113">I det här exemplet ska vi titta på en enkel konfiguration som anropar **WindowsFeature** -resursen för att se till att funktionen "WindowsPowerShellWebAccess" är installerad:</span><span class="sxs-lookup"><span data-stu-id="8d0b0-113">For this example, we'll look at a simple configuration that calls the **WindowsFeature** resource to ensure that the "WindowsPowerShellWebAccess" feature is installed:</span></span>

```powershell
Configuration PSWebAccess
    {
    Import-DscResource -ModuleName 'PsDesiredStateConfiguration'
    Node localhost
        {
        WindowsFeature PSWA
            {
            Name = 'WindowsPowerShellWebAccess'
            Ensure = 'Present'
            }
        }
    }
PSWebAccess
```
<span data-ttu-id="8d0b0-114">När du har kompilerat konfigurationen startar du den genom att anropa [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span><span class="sxs-lookup"><span data-stu-id="8d0b0-114">After compiling the configuration, start it by calling [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span></span>
<span data-ttu-id="8d0b0-115">Konfigurationen stoppas när den lokala Configuration Manager (LCM) anropar den första resursen i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="8d0b0-115">The configuration will stop when the Local Configuration Manager (LCM) calls into the first resource in the configuration.</span></span>
<span data-ttu-id="8d0b0-116">Om du använder parametrarna `-Verbose` och `-Wait`, visar utdata de rader som du måste ange för att starta fel sökningen.</span><span class="sxs-lookup"><span data-stu-id="8d0b0-116">If you use the `-Verbose` and `-Wait` parameters, the output displays the lines you need to enter to start debugging.</span></span>

```powershell
Start-DscConfiguration .\PSWebAccess -Wait -Verbose
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfiguration
Manager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Set      ]
WARNING: [TEST-SRV]:                            [DSCEngine] Warning LCM is in Debug 'ResourceScriptBreakAll' mode.  Resource script processing will
be stopped to wait for PowerShell script debugger to attach.
VERBOSE: [TEST-SRV]:                            [DSCEngine] Importing the module C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateCo
nfiguration\DscResources\MSFT_RoleResource\MSFT_RoleResource.psm1 in force mode.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Resource ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]: LCM:  [ Start  Test     ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]:                            [[WindowsFeature]PSWA] Importing the module MSFT_RoleResource in force mode.
WARNING: [TEST-SRV]:                            [[WindowsFeature]PSWA] Resource is waiting for PowerShell script debugger to attach.
Use the following commands to begin debugging this resource script:
Enter-PSSession -ComputerName TEST-SRV -Credential <credentials>
Enter-PSHostProcess -Id 9000 -AppDomainName DscPsPluginWkr_AppDomain
Debug-Runspace -Id 9
```
<span data-ttu-id="8d0b0-117">I det här läget har LCM anropat resursen och kommer till den första Bryt punkten.</span><span class="sxs-lookup"><span data-stu-id="8d0b0-117">At this point, the LCM has called the resource, and come to the first break point.</span></span>
<span data-ttu-id="8d0b0-118">De sista tre raderna i utdata visar hur du ansluter till processen och startar fel sökning av resurs skriptet.</span><span class="sxs-lookup"><span data-stu-id="8d0b0-118">The last three lines in the output show you how to attach to the process and start debugging the resource script.</span></span>

## <a name="debugging-the-resource-script"></a><span data-ttu-id="8d0b0-119">Fel sökning av resurs skriptet</span><span class="sxs-lookup"><span data-stu-id="8d0b0-119">Debugging the resource script</span></span>

<span data-ttu-id="8d0b0-120">Starta en ny instans av PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="8d0b0-120">Start a new instance of the PowerShell ISE.</span></span>
<span data-ttu-id="8d0b0-121">I konsol fönstret anger du de tre sista raderna i utdata från `Start-DscConfiguration` utdata som kommandon, och ersätter `<credentials>` med giltiga användarautentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="8d0b0-121">In the console pane, enter the last three lines of output from the `Start-DscConfiguration` output as commands, replacing `<credentials>` with valid user credentials.</span></span>
<span data-ttu-id="8d0b0-122">Nu bör du se en prompt som ser ut ungefär så här:</span><span class="sxs-lookup"><span data-stu-id="8d0b0-122">You should now see a prompt that looks similar to:</span></span>

```powershell
[TEST-SRV]: [DBG]: [Process:9000]: [RemoteHost]: PS C:\DebugTest>>
```

<span data-ttu-id="8d0b0-123">Resurs skriptet öppnas i skript fönstret och fel söknings programmet stoppas på den första raden i **test-TargetResource** -funktionen (metoden **test ()** i en klass-baserad resurs).</span><span class="sxs-lookup"><span data-stu-id="8d0b0-123">The resource script will open in the script pane, and the debugger is stopped at the first line of the **Test-TargetResource** function (the **Test()** method of a class-based resource).</span></span>
<span data-ttu-id="8d0b0-124">Nu kan du använda fel söknings kommandona i ISE för att gå igenom resurs skriptet, titta på variabla värden, Visa anrops stacken och så vidare.</span><span class="sxs-lookup"><span data-stu-id="8d0b0-124">Now you can use the debug commands in the ISE to step through the resource script, look at variable values, view the call stack, and so on.</span></span> <span data-ttu-id="8d0b0-125">Kom ihåg att varje rad i resurs skriptet (eller klassen) anges som en Bryt punkt.</span><span class="sxs-lookup"><span data-stu-id="8d0b0-125">Remember that every line in the resource script (or class) is set as a break point.</span></span>

## <a name="disabling-dsc-debugging"></a><span data-ttu-id="8d0b0-126">Inaktiverar DSC-felsökning</span><span class="sxs-lookup"><span data-stu-id="8d0b0-126">Disabling DSC debugging</span></span>

<span data-ttu-id="8d0b0-127">När du har anropat [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)kommer alla anrop till [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) att resultera i att konfigurationen delas in i fel söknings programmet.</span><span class="sxs-lookup"><span data-stu-id="8d0b0-127">After calling [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug), all calls to [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) will result in the configuration breaking into the debugger.</span></span> <span data-ttu-id="8d0b0-128">Om du vill tillåta konfigurationer att köras normalt måste du inaktivera fel sökning genom att anropa cmdleten [disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug) .</span><span class="sxs-lookup"><span data-stu-id="8d0b0-128">To allow configurations to run normally, you must disable debugging by calling the [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug) cmdlet.</span></span>

><span data-ttu-id="8d0b0-129">**Obs:** Vid omstart ändras inte fel söknings läget för LCM.</span><span class="sxs-lookup"><span data-stu-id="8d0b0-129">**Note:** Rebooting does not change the debug state of the LCM.</span></span> <span data-ttu-id="8d0b0-130">Om fel sökning har Aktiver ATS avbryts start konfigurationen fortfarande till fel söknings programmet efter en omstart.</span><span class="sxs-lookup"><span data-stu-id="8d0b0-130">If debugging is enabled, starting a configuration will still break into the debugger after a reboot.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d0b0-131">Se även</span><span class="sxs-lookup"><span data-stu-id="8d0b0-131">See Also</span></span>

- [<span data-ttu-id="8d0b0-132">Skriva en anpassad DSC-resurs med MOF</span><span class="sxs-lookup"><span data-stu-id="8d0b0-132">Writing a custom DSC resource with MOF</span></span>](../resources/authoringResourceMOF.md)
- [<span data-ttu-id="8d0b0-133">Skriva en anpassad DSC-resurs med PowerShell-klasser</span><span class="sxs-lookup"><span data-stu-id="8d0b0-133">Writing a custom DSC resource with PowerShell classes</span></span>](../resources/authoringResourceClass.md)
