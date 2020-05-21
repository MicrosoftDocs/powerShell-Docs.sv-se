---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Felsöka DSC-resurser
ms.openlocfilehash: 53ee9ea5652ffb577f0c7fba2f240f63816281db
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/20/2020
ms.locfileid: "83691967"
---
# <a name="debugging-dsc-resources"></a>Felsöka DSC-resurser

> Gäller för: Windows PowerShell 5,0

I PowerShell 5,0 introducerades en ny funktion i önskad tillstånds konfiguration (DSC) som gör att du kan felsöka en DSC-resurs när en konfiguration tillämpas.

## <a name="enabling-dsc-debugging"></a>Aktivera DSC-felsökning
Innan du kan felsöka en resurs måste du aktivera fel sökning genom att anropa cmdleten [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug) .
Denna cmdlet använder en obligatorisk parameter, **BreakAll**.

Du kan kontrol lera att fel sökning har Aktiver ATS genom att titta på resultatet av ett anrop till [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager).

Följande PowerShell-utdata visar resultatet av att aktivera fel sökning:

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

## <a name="starting-a-configuration-with-debug-enabled"></a>Starta en konfiguration med fel sökning aktiverat
Om du vill felsöka en DSC-resurs startar du en konfiguration som anropar resursen.
I det här exemplet ska vi titta på en enkel konfiguration som anropar **WindowsFeature** -resursen för att se till att funktionen "WindowsPowerShellWebAccess" är installerad:

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

När du har kompilerat konfigurationen startar du den genom att anropa [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).
Konfigurationen stoppas när den lokala Configuration Manager (LCM) anropar den första resursen i konfigurationen.
Om du använder `-Verbose` -och `-Wait` -parametrarna visar utdata de rader du behöver ange för att starta fel sökningen.

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

I det här läget har LCM anropat resursen och kommer till den första Bryt punkten.
De sista tre raderna i utdata visar hur du ansluter till processen och startar fel sökning av resurs skriptet.

## <a name="debugging-the-resource-script"></a>Fel sökning av resurs skriptet

Starta en ny instans av PowerShell ISE.
I konsol fönstret anger du de tre sista raderna i utdata från `Start-DscConfiguration` utdata som-kommandon, och ersätter `<credentials>` med giltiga användarautentiseringsuppgifter.
Nu bör du se en prompt som ser ut ungefär så här:

```powershell
[TEST-SRV]: [DBG]: [Process:9000]: [RemoteHost]: PS C:\DebugTest>>
```

Resurs skriptet öppnas i skript fönstret och fel söknings programmet stoppas på den första raden i **test-TargetResource** -funktionen (metoden **test ()** i en klass-baserad resurs).
Nu kan du använda fel söknings kommandona i ISE för att gå igenom resurs skriptet, titta på variabla värden, Visa anrops stacken och så vidare. Kom ihåg att varje rad i resurs skriptet (eller klassen) anges som en Bryt punkt.

## <a name="disabling-dsc-debugging"></a>Inaktiverar DSC-felsökning

När du har anropat [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)kommer alla anrop till [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) att resultera i att konfigurationen delas in i fel söknings programmet. Om du vill tillåta konfigurationer att köras normalt måste du inaktivera fel sökning genom att anropa cmdleten [disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug) .

>**Obs:** Vid omstart ändras inte fel söknings läget för LCM. Om fel sökning har Aktiver ATS avbryts start konfigurationen fortfarande till fel söknings programmet efter en omstart.

## <a name="see-also"></a>Se även

- [Skriva en anpassad DSC-resurs med MOF](../resources/authoringResourceMOF.md)
- [Skriva en anpassad DSC-resurs med PowerShell-klasser](../resources/authoringResourceClass.md)
