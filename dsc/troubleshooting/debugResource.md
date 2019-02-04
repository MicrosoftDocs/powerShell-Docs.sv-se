---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Felsöka DSC-resurser
ms.openlocfilehash: 9b2e7dd9b42332b869c4d7fabb21bd4b5a6b8800
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683956"
---
# <a name="debugging-dsc-resources"></a>Felsöka DSC-resurser

> Gäller för: Windows PowerShell 5.0

I PowerShell 5.0 introducerades en ny funktion i önskat tillstånd Anpassningsdelar (DSC) som hjälper dig att felsöka en DSC-resurs som en konfiguration som används.

## <a name="enabling-dsc-debugging"></a>Aktivera felsökning av DSC
Innan du kan felsöka en resurs, måste du aktivera felsökning genom att anropa den [aktivera DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug) cmdlet.
Den här cmdleten tar en obligatorisk parameter **BreakAll**.

Du kan kontrollera att felsökning har aktiverats genom att titta på resultatet av ett anrop till [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager).

Följande PowerShell-utdata visar resultatet av att aktivera felsökning:


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


## <a name="starting-a-configuration-with-debug-enabled"></a>Startar en konfiguration med debug aktiverat
För att felsöka en DSC-resurs, kan du starta en konfiguration som anropar den här resursen.
I det här exemplet ska vi titta på en enkel konfiguration som anropar den **WindowsFeature** resursen för att kontrollera att funktionen ”WindowsPowerShellWebAccess” är installerad:

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
När du kompilera konfigurationen, starta den genom att anropa [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).
Konfigurationen stoppas när den lokala Configuration Manager (LCM) anrop till den första resursen i konfigurationen.
Om du använder den `-Verbose` och `-Wait` parametrar, utdata visar rader som du måste ange för att starta felsökningen.

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
Nu har LCM kallas resursen och gå till den första brytpunkten.
De tre sista raderna i utdata visar hur du ansluter till processen och starta felsökning resurs-skriptet.

## <a name="debugging-the-resource-script"></a>Felsökning av resurs-skript

Starta en ny instans av PowerShell ISE.
I konsolfönstret, anger du de tre sista raderna i utdata från den `Start-DscConfiguration` utdata som kommandon och Ersätt `<credentials>` med giltiga autentiseringsuppgifter.
Du bör nu se en uppmaning som liknar:

```powershell
[TEST-SRV]: [DBG]: [Process:9000]: [RemoteHost]: PS C:\DebugTest>>
```

Resurs-skriptet öppnas i skriptfönstret och felsökningsprogrammet har stoppats på den första raden i **Test-TargetResource** funktion (den **Test()** -metoden för en MOF-baserade resurs).
Du kan nu använda debug-kommandon i ISE för att gå igenom skriptet resurs, titta på variabelvärden, visa anropsstacken och så vidare. Kom ihåg att varje rad i resurs-skript (eller klassen) anges till en brytpunkt.

## <a name="disabling-dsc-debugging"></a>Inaktivering av DSC-felsökning

När du anropar [aktivera DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug), alla anrop till [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) resulterar i konfigurationen bryta in i felsökaren. Om du vill tillåta konfigurationer normalt, måste du inaktivera felsökning genom att anropa den [inaktivera DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug) cmdlet.

>**Obs:** Debug staten LCM ändras inte när du startar om. Om felsökning är aktiverad kommer startar en konfiguration fortfarande bryta in i felsökaren efter en omstart.

## <a name="see-also"></a>Se även

- [Skriva en anpassad DSC-resurs med MOF](../resources/authoringResourceMOF.md)
- [Skriva en anpassad DSC-resurs med PowerShell-klasser](../resources/authoringResourceClass.md)
