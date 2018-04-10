---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Felsöka DSC-resurser
ms.openlocfilehash: 6a1f4b04a11185c2cfe9be26324bd66ed13ca7dd
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="debugging-dsc-resources"></a><span data-ttu-id="be552-103">Felsöka DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="be552-103">Debugging DSC resources</span></span>

> <span data-ttu-id="be552-104">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="be552-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="be552-105">I PowerShell 5.0 introducerades en ny funktion i önskad tillstånd serverns konfiguration DSC () som hjälper dig att felsöka en DSC-resurs som en konfiguration som används.</span><span class="sxs-lookup"><span data-stu-id="be552-105">In PowerShell 5.0, a new feature was introduced in Desired State Configuraiton (DSC) that allows you to debug a DSC resource as a configuration is being applied.</span></span>

## <a name="enabling-dsc-debugging"></a><span data-ttu-id="be552-106">Aktivera felsökning av DSC</span><span class="sxs-lookup"><span data-stu-id="be552-106">Enabling DSC debugging</span></span>
<span data-ttu-id="be552-107">Innan du kan felsöka en resurs måste du aktivera felsökning genom att anropa den [aktivera DscDebug](https://technet.microsoft.com/library/mt517870.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="be552-107">Before you can debug a resource, you have to enable debugging by calling the [Enable-DscDebug](https://technet.microsoft.com/library/mt517870.aspx) cmdlet.</span></span>
<span data-ttu-id="be552-108">Den här cmdleten tar en obligatorisk parameter **BreakAll**.</span><span class="sxs-lookup"><span data-stu-id="be552-108">This cmdlet takes a mandatory parameter, **BreakAll**.</span></span>

<span data-ttu-id="be552-109">Du kan verifiera att felsökning har aktiverats genom att titta på resultatet av ett anrop till [Get-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn407378.aspx).</span><span class="sxs-lookup"><span data-stu-id="be552-109">You can verify that debugging has been enabled by looking at the result of a call to [Get-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn407378.aspx).</span></span>

<span data-ttu-id="be552-110">Följande PowerShell-utdata visar resultatet av att aktivera felsökning:</span><span class="sxs-lookup"><span data-stu-id="be552-110">The following PowerShell output shows the result of enabling debugging:</span></span>


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


## <a name="starting-a-configuration-with-debug-enabled"></a><span data-ttu-id="be552-111">Starta en konfiguration med felsökning aktiverat</span><span class="sxs-lookup"><span data-stu-id="be552-111">Starting a configuration with debug enabled</span></span>
<span data-ttu-id="be552-112">Om du vill felsöka en DSC-resurs, kan du starta en konfiguration som anropar den här resursen.</span><span class="sxs-lookup"><span data-stu-id="be552-112">To debug a DSC resource, you start a configuration that calls that resource.</span></span>
<span data-ttu-id="be552-113">I det här exemplet ska vi titta på en enkel konfiguration som anropar den [WindowsFeature](windowsfeatureResource.md) resurs för att kontrollera att funktionen ”WindowsPowerShellWebAccess” är installerad:</span><span class="sxs-lookup"><span data-stu-id="be552-113">For this example, we'll look at a simple configuration that calls the [WindowsFeature](windowsfeatureResource.md) resource to ensure that the "WindowsPowerShellWebAccess" feature is installed:</span></span>

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
<span data-ttu-id="be552-114">Efter att kompilera konfigurationen, starta den genom att anropa [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx).</span><span class="sxs-lookup"><span data-stu-id="be552-114">After compiling the configuration, start it by calling [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx).</span></span>
<span data-ttu-id="be552-115">Konfigurationen stoppas när den lokala Configuration Manager (MGM)-anrop till den första resursen i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="be552-115">The configuration will stop when the Local Configuration Manager (LCM) calls into the first resource in the configuration.</span></span>
<span data-ttu-id="be552-116">Om du använder den `-Verbose` och `-Wait` parametrar, utdata visar rader måste du ange om du vill starta felsökningen.</span><span class="sxs-lookup"><span data-stu-id="be552-116">If you use the `-Verbose` and `-Wait` parameters, the output displays the lines you need to enter to start debugging.</span></span>

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
<span data-ttu-id="be552-117">Nu har MGM kallas resursen och gå till den första punkten break.</span><span class="sxs-lookup"><span data-stu-id="be552-117">At this point, the LCM has called the resource, and come to the first break point.</span></span>
<span data-ttu-id="be552-118">De tre sista raderna i utdata visar hur du ansluta till processen och starta felsökning av resurs-skript.</span><span class="sxs-lookup"><span data-stu-id="be552-118">The last three lines in the output show you how to attach to the process and start debugging the resource script.</span></span>

## <a name="debugging-the-resource-script"></a><span data-ttu-id="be552-119">Felsökning av resurs-skript</span><span class="sxs-lookup"><span data-stu-id="be552-119">Debugging the resource script</span></span>

<span data-ttu-id="be552-120">Starta en ny instans av PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="be552-120">Start a new instance of the PowerShell ISE.</span></span>
<span data-ttu-id="be552-121">I konsolfönstret, anger du de sista tre raderna i utdata från den `Start-DscConfiguration` som kommandon, ersätter `<credentials>` med giltiga autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="be552-121">In the console pane, enter the last three lines of output from the `Start-DscConfiguration` output as commands, replacing `<credentials>` with valid user credentials.</span></span>
<span data-ttu-id="be552-122">Du bör nu se ett meddelande som liknar:</span><span class="sxs-lookup"><span data-stu-id="be552-122">You should now see a prompt that looks similar to:</span></span>

```powershell
[TEST-SRV]: [DBG]: [Process:9000]: [RemoteHost]: PS C:\DebugTest>>
```

<span data-ttu-id="be552-123">Skriptet resurs öppnas i skriptfönstret och felsökningsprogrammet har stoppats på den första raden i det **Test TargetResource** funktionen (den **Test()** metod för en klass-baserade resurs).</span><span class="sxs-lookup"><span data-stu-id="be552-123">The resource script will open in the script pane, and the debugger is stopped at the first line of the **Test-TargetResource** function (the **Test()** method of a class-based resource).</span></span>
<span data-ttu-id="be552-124">Du kan nu använda debug-kommandon i ISE för att gå igenom skriptet resurs, titta på variabelvärden, visa anropsstacken och så vidare.</span><span class="sxs-lookup"><span data-stu-id="be552-124">Now you can use the debug commands in the ISE to step through the resource script, look at variable values, view the call stack, and so on.</span></span>
<span data-ttu-id="be552-125">Information om felsökning i PowerShell ISE finns [hur du felsöker skript i Windows PowerShell ISE](https://technet.microsoft.com/en-us/library/dd819480.aspx).</span><span class="sxs-lookup"><span data-stu-id="be552-125">For information about debugging in the PowerShell ISE, see [How to Debug Scripts in Windows PowerShell ISE](https://technet.microsoft.com/en-us/library/dd819480.aspx).</span></span>
<span data-ttu-id="be552-126">Kom ihåg att varje rad i skriptet resurs (eller klassen) har angetts som brytpunkt.</span><span class="sxs-lookup"><span data-stu-id="be552-126">Remember that every line in the resource script (or class) is set as a break point.</span></span>

## <a name="disabling-dsc-debugging"></a><span data-ttu-id="be552-127">Inaktivera DSC-felsökning</span><span class="sxs-lookup"><span data-stu-id="be552-127">Disabling DSC debugging</span></span>

<span data-ttu-id="be552-128">Efter att [aktivera DscDebug](https://technet.microsoft.com/library/mt517870.aspx), alla anrop till [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) leder till att konfigurationen bryta in i felsökaren.</span><span class="sxs-lookup"><span data-stu-id="be552-128">After calling [Enable-DscDebug](https://technet.microsoft.com/library/mt517870.aspx), all calls to [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) will result in the configuration breaking into the debugger.</span></span> <span data-ttu-id="be552-129">Om du vill tillåta konfigurationer normalt, måste du inaktivera felsökning genom att anropa den [inaktivera DscDebug](https://technet.microsoft.com/en-us/library/mt517872.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="be552-129">To allow configurations to run normally, you must disable debugging by calling the [Disable-DscDebug](https://technet.microsoft.com/en-us/library/mt517872.aspx) cmdlet.</span></span>

><span data-ttu-id="be552-130">**Obs:** omstart ändras inte MGM debug-tillstånd.</span><span class="sxs-lookup"><span data-stu-id="be552-130">**Note:** Rebooting does not change the debug state of the LCM.</span></span> <span data-ttu-id="be552-131">Om felsökning är aktiverad kommer startar en konfiguration fortfarande bryta in i felsökaren efter en omstart.</span><span class="sxs-lookup"><span data-stu-id="be552-131">If debugging is enabled, starting a configuration will still break into the debugger after a reboot.</span></span>


## <a name="see-also"></a><span data-ttu-id="be552-132">Se även</span><span class="sxs-lookup"><span data-stu-id="be552-132">See Also</span></span>
- [<span data-ttu-id="be552-133">Skriva en anpassad DSC-resurs med MOF</span><span class="sxs-lookup"><span data-stu-id="be552-133">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
- [<span data-ttu-id="be552-134">Skriva en anpassad DSC-resurs med PowerShell-klasser</span><span class="sxs-lookup"><span data-stu-id="be552-134">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)