---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Felsöka DSC-resurser
ms.openlocfilehash: 30d49768fc2301b5306d0001e157d60e2e991883
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219114"
---
# <a name="debugging-dsc-resources"></a>Felsöka DSC-resurser

> Gäller för: Windows PowerShell 5.0

I PowerShell 5.0 introducerades en ny funktion i önskad tillstånd serverns konfiguration DSC () som hjälper dig att felsöka en DSC-resurs som en konfiguration som används.

## <a name="enabling-dsc-debugging"></a>Aktivera felsökning av DSC
Innan du kan felsöka en resurs måste du aktivera felsökning genom att anropa den [aktivera DscDebug](https://technet.microsoft.com/library/mt517870.aspx) cmdlet.
Den här cmdleten tar en obligatorisk parameter **BreakAll**.

Du kan verifiera att felsökning har aktiverats genom att titta på resultatet av ett anrop till [Get-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn407378.aspx).

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


## <a name="starting-a-configuration-with-debug-enabled"></a>Starta en konfiguration med felsökning aktiverat
Om du vill felsöka en DSC-resurs, kan du starta en konfiguration som anropar den här resursen.
I det här exemplet ska vi titta på en enkel konfiguration som anropar den [WindowsFeature](windowsfeatureResource.md) resurs för att kontrollera att funktionen ”WindowsPowerShellWebAccess” är installerad:

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
Efter att kompilera konfigurationen, starta den genom att anropa [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx).
Konfigurationen stoppas när den lokala Configuration Manager (MGM)-anrop till den första resursen i konfigurationen.
Om du använder den `-Verbose` och `-Wait` parametrar, utdata visar rader måste du ange om du vill starta felsökningen.

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
Nu har MGM kallas resursen och gå till den första punkten break.
De tre sista raderna i utdata visar hur du ansluta till processen och starta felsökning av resurs-skript.

## <a name="debugging-the-resource-script"></a>Felsökning av resurs-skript

Starta en ny instans av PowerShell ISE.
I konsolfönstret, anger du de sista tre raderna i utdata från den `Start-DscConfiguration` som kommandon, ersätter `<credentials>` med giltiga autentiseringsuppgifter.
Du bör nu se ett meddelande som liknar:

```powershell
[TEST-SRV]: [DBG]: [Process:9000]: [RemoteHost]: PS C:\DebugTest>>
```

Skriptet resurs öppnas i skriptfönstret och felsökningsprogrammet har stoppats på den första raden i det **Test TargetResource** funktionen (den **Test()** metod för en klass-baserade resurs).
Du kan nu använda debug-kommandon i ISE för att gå igenom skriptet resurs, titta på variabelvärden, visa anropsstacken och så vidare.
Information om felsökning i PowerShell ISE finns [hur du felsöker skript i Windows PowerShell ISE](https://technet.microsoft.com/en-us/library/dd819480.aspx).
Kom ihåg att varje rad i skriptet resurs (eller klassen) har angetts som brytpunkt.

## <a name="disabling-dsc-debugging"></a>Inaktivera DSC-felsökning

Efter att [aktivera DscDebug](https://technet.microsoft.com/library/mt517870.aspx), alla anrop till [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) leder till att konfigurationen bryta in i felsökaren. Om du vill tillåta konfigurationer normalt, måste du inaktivera felsökning genom att anropa den [inaktivera DscDebug](https://technet.microsoft.com/en-us/library/mt517872.aspx) cmdlet.

>**Obs:** omstart ändras inte MGM debug-tillstånd. Om felsökning är aktiverad kommer startar en konfiguration fortfarande bryta in i felsökaren efter en omstart.


## <a name="see-also"></a>Se även
- [Skriva en anpassad DSC-resurs med MOF](authoringResourceMOF.md)
- [Skriva en anpassad DSC-resurs med PowerShell-klasser](authoringResourceClass.md)