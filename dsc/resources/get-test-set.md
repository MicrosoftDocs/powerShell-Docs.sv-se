---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguration, installation
title: Get-Test-Set
ms.openlocfilehash: e4aa7770bb5fc8b916b0c0a6488b1ccc0ef0ade9
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229511"
---
# <a name="get-test-set"></a>Get-Test-Set

>Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

![Hämta, testa och tillämpa](/media/get-test-set.png)

PowerShell Desired State Configuration är uppbyggd kring ett **hämta**, **Test**, och **ange** processen. DSC [resurser](resources.md) var och en innehåller metoder för att slutföra var och en av dessa åtgärder. I en [Configuration](../configurations/configurations.md), definierar du resursen förutsättningarna för att fylla i nycklar som blivit parametrar för en resurs **hämta**, **Test**, och **ange** metoder.

Det här är syntaxen för en **Service** resource block. Den **Service** resource konfigurerar Windows-tjänster.

```syntax
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

Den **hämta**, **Test**, och **ange** metoderna i den **Service** resursen måste parameterblock som har stöd för dessa värden.

```powershell
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [System.String]
        $Name,

        [System.String]
        [ValidateSet("Automatic", "Manual", "Disabled")]
        $StartupType,

        [System.String]
        [ValidateSet("LocalSystem", "LocalService", "NetworkService")]
        $BuiltInAccount,

        [System.Management.Automation.PSCredential]
        [ValidateNotNull()]
        $Credential,

        [System.String]
        [ValidateSet("Running", "Stopped")]
        $State="Running",

        [System.String]
        [ValidateNotNullOrEmpty()]
        $DisplayName,

        [System.String]
        [ValidateNotNullOrEmpty()]
        $Description,

        [System.String]
        [ValidateNotNullOrEmpty()]
        $Path,

        [System.String[]]
        [ValidateNotNullOrEmpty()]
        $Dependencies,

        [System.String]
        [ValidateSet("Present", "Absent")]
        $Ensure="Present"
    )
```

> [!NOTE]
> Det språk och den metod som används för att definiera resursen avgör hur **hämta**, **Test**, och **ange** metoder definieras.

Eftersom den **Service** resursen har endast en nödvändig nyckel (`Name`), ett **Service** block resurs kan vara så enkla som detta:

```powershell
Configuration TestConfig
{
    Import-DSCResource -Name Service
    Node localhost
    {
        Service "MyService"
        {
            Name = "Spooler"
        }
    }
}
```

När du kompilera konfigurationen ovan, lagras de värden som du anger för en nyckel i filen ”.mof” som genereras. Mer information finns i [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).

```
instance of MSFT_ServiceResource as $MSFT_ServiceResource1ref
{
SourceInfo = "::5::1::Service";
 ModuleName = "PsDesiredStateConfiguration";
 ResourceID = "[Service]MyService";
 Name = "Spooler";

ModuleVersion = "1.0";

 ConfigurationName = "Test";

};
```

Vid tillämpningen den [lokal konfigurationshanterare](../managing-nodes/metaConfig.md) (LCM) kommer att läsa värdet ”utskriftshanterarens” från ”.mof”-fil och skicka det till den `-Name` -parametern för den **hämta**, **Test**, och **ange** metoder för ”Mintjänst”-instansen av den **Service** resurs.

## <a name="get"></a>Get

Den **hämta** -metoden för en resurs, hämtar tillståndet för resursen eftersom den är konfigurerad på mål-nod. Det här tillståndet returneras som en [hash-tabell](/powershell/module/microsoft.powershell.core/about/about_hash_tables). Nycklarna för den **hash-tabell** ska vara konfigurerbara värden eller parametrar, resursen accepterar.

Den **hämta** metoden mappar direkt till den [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet. När du anropar `Get-DSCConfiguration`, MGM körningar den **hämta** -metoden för varje resurs i konfigurationen som används. LCM använder de viktiga värden som lagras i filen ”.mof” som parametrar för varje motsvarande resursinstans.

Det här är exempel på utdata från en **Service** resurs som konfigurerar ”Utskriftshanteraren”.

```output
ConfigurationName    : Test
DependsOn            :
ModuleName           : PsDesiredStateConfiguration
ModuleVersion        : 1.1
PsDscRunAsCredential :
ResourceId           : [Service]Spooler
SourceInfo           :
BuiltInAccount       : LocalSystem
Credential           :
Dependencies         : {RPCSS, http}
Description          : This service spools print jobs and handles interaction with the printer.  If you turn off
                       this service, you won’t be able to print or see your printers.
DisplayName          : Print Spooler
Ensure               :
Name                 : Spooler
Path                 : C:\WINDOWS\System32\spoolsv.exe
StartupType          : Automatic
State                : Running
Status               :
PSComputerName       :
CimClassName         : MSFT_ServiceResource
```

Utdata visar de aktuella värdet egenskaperna kan konfigureras genom att den **Service** resurs.

```syntax
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

## <a name="test"></a>Testa

Den **Test** -metoden för en resurs avgör om Målnoden är för närvarande är kompatibel med resursens *önskade tillstånd*. Den **Test** metoden returnerar `$True` eller `$False` endast för att indikera om noden är kompatibel.
När du anropar [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), LCM-anrop i **Test** metod för varje resurs i konfigurationen som används. LCM använder de viktiga värden som lagras i filen ”.mof” som parametrar för varje motsvarande resursinstans.

Om resultatet av en enskild resurs **Test** är `$False`, `Test-DSCConfiguration` returnerar `$False` som anger att noden inte är kompatibla. Om alla resursens **Test** metoder returnerar `$True`, `Test-DSCConfiguration` returnerar `$True` som visar att noden är kompatibla.

```powershell
Test-DSCConfiguration
```

```output
True
```

Från och med PowerShell 5.0 på `-Detailed` parameter har lagts till. Ange `-Detailed` orsakar `Test-DSCConfiguration` att returnera ett objekt som innehåller samlingar av resultat för kompatibla och icke-kompatibla resurser.

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

Mer information finns i [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)

## <a name="set"></a>Ange

Den **ange** -metoden för en resurs försöker tvinga noden ska bli kompatibla med resursens *önskade tillstånd*. Den **ange** metoden är avsedd att vara **idempotenta**, vilket innebär att **ange** kan köra flera gånger och alltid få samma resultat utan fel.  När du kör [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), MGM växlar mellan varje resurs i konfigurationen som används. LCM hämtar nyckelvärden för den aktuella resursinstansen från filen ”.mof” och använder dem som parametrar för den **Test** metod. Om den **Test** metoden returnerar `$True`, noden är kompatibel med den aktuella resursen och **ange** metoden hoppas över. Om den **Test** returnerar `$False`, noden inte är kompatibel.  LCM skickar resursen instansens nyckelvärden som parametrar till resursens **ange** metod, återställa noden för efterlevnad.

Genom att ange den `-Verbose` och `-Wait` parametrar, som du kan se förloppet för den `Start-DSCConfiguration` cmdlet. I det här exemplet är noden redan kompatibel. Den `Verbose` utdata indikerar att den **ange** metoden hoppades över.

```
PS> Start-DSCConfiguration -Verbose -Wait -UseExisting

VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
ApplyConfiguration,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer SERVER01 with user sid
S-1-5-21-124525095-708259637-1543119021-1282804.
VERBOSE: [SERVER01]:                            [] Starting consistency engine.
VERBOSE: [SERVER01]:                            [] Checking consistency for current configuration.
VERBOSE: [SERVER01]:                            [DSCEngine] Importing the module
C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\DscResources\MSFT_ServiceResource\MSFT
_ServiceResource.psm1 in force mode.
VERBOSE: [SERVER01]: LCM:  [ Start  Resource ]  [[Service]Spooler]
VERBOSE: [SERVER01]: LCM:  [ Start  Test     ]  [[Service]Spooler]
VERBOSE: [SERVER01]:                            [[Service]Spooler] Importing the module MSFT_ServiceResource in
force mode.
VERBOSE: [SERVER01]: LCM:  [ End    Test     ]  [[Service]Spooler]  in 0.2540 seconds.
VERBOSE: [SERVER01]: LCM:  [ Skip   Set      ]  [[Service]Spooler]
VERBOSE: [SERVER01]: LCM:  [ End    Resource ]  [[Service]Spooler]
VERBOSE: [SERVER01]:                            [] Consistency check completed.
VERBOSE: Operation 'Invoke CimMethod' complete.
VERBOSE: Time taken for configuration job to complete is 1.379 seconds
```

## <a name="see-also"></a>Se även

- [Översikt över Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [Konfigurera en SMB-pullserver](../pull-server/pullServerSMB.md)
- [Konfigurera en pullklient](../pull-server/pullClientConfigID.md)
