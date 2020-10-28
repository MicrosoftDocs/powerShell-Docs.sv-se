---
ms.date: 07/08/2020
keywords: DSC, PowerShell, konfiguration, installation
title: Get-test-set
description: Den här artikeln beskriver hur du implementerar metoderna get, test och set i en DSC-konfiguration.
ms.openlocfilehash: e0da1452a1237c550f52a4a4f9e4400f801ed7cd
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646795"
---
# <a name="get-test-set"></a>Get-test-set

>Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0

PowerShell Desired State Configuration är konstruerad runt en **Get** -, **test** -och **set** -process. DSC- [resurser](resources.md) innehåller båda metoder för att slutföra var och en av dessa åtgärder.
I en [konfiguration](../configurations/configurations.md)definierar du resurs block för att fylla i nycklar som blir parametrar för en resurs **Get** -, **test** -och **set** -metoder.

Detta är syntaxen för ett **tjänst** resurs block. **Tjänst** resursen konfigurerar Windows-tjänster.

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

Metoderna **Get** , **test** och **set** för **tjänst** resursen kommer att ha parameter block som accepterar dessa värden.

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
> Språket och metoden som används för att definiera resursen bestämmer hur metoderna **Get** , **test** och **set** ska definieras.

Eftersom **tjänst** resursen bara har en nödvändig nyckel ( `Name` ) kan en **tjänst** block resurs vara så enkel som detta:

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

När du kompilerar konfigurationen ovan lagras de värden som du anger för en nyckel i den `.mof` fil som genereras. Mer information finns i [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).

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

När den används, kommer den [lokala Configuration Manager](../managing-nodes/metaConfig.md) (LCM) att läsa värdet "Spooler" från `.mof` filen och skicka den till **Name** -parametern för **Get** -, **test** -och **set** -instansen för **tjänst** resursen.

## <a name="get"></a>Hämta

**Get** -metoden för en resurs, hämtar resursens tillstånd som den är konfigurerad på målnoden. Det här status returneras som en [hash-hash](/powershell/module/microsoft.powershell.core/about/about_hash_tables). Nycklarna i **hash** -tabellen är de konfigurerbara värden eller parametrarna som resursen accepterar.

**Get** -metoden mappar direkt till [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) -cmdlet: en.
När du anropar `Get-DSCConfiguration` Kör LCM **Get** -metoden för varje resurs i den aktuella konfigurationen. LCM använder de nyckel värden som lagras i `.mof` filen som parametrar för varje motsvarande resurs instans.

Detta är exempel på utdata från en **tjänst** resurs som konfigurerar "Spooler"-tjänsten.

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
                       this service, you won't be able to print or see your printers.
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

Utdata visar aktuella värde egenskaper som kan konfigureras av **tjänst** resursen.

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

**Test** metoden för en resurs bestämmer om målnoden för närvarande är kompatibel med resursens _önskade tillstånd_ . **Test** metoden returnerar `$true` eller `$false` visar om noden är kompatibel. När du anropar [test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)anropar LCM **test** metoden för varje resurs i den aktuella konfigurationen. LCM använder nyckel värden som lagras i filen ". MOF" som parametrar för varje motsvarande resurs instans.

Om resultatet av en enskild resurs **test** är `$false` `Test-DSCConfiguration` returneras `$false` anger att noden inte är kompatibel. Om alla **test** metoder `$true` för resursen returnerar, `Test-DSCConfiguration` returneras `$true` för att indikera att noden är kompatibel.

```powershell
Test-DSCConfiguration
```

```output
True
```

Från och med PowerShell 5,0 lades den **detaljerade** parametern till. Ange **detaljerade** orsaker `Test-DSCConfiguration` till att returnera ett objekt som innehåller samlings resultat för kompatibla och icke-kompatibla resurser.

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

Mer information finns i [test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).

## <a name="set"></a>Ange

**Set** -metoden för en resurs försöker tvinga noden att bli kompatibel med resursens *önskade tillstånd* . **Set** -metoden är avsedd att vara **idempotenta** , vilket innebär att **uppsättningen** kan köras flera gånger och alltid får samma resultat utan fel. När du kör [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration)växlar LCM genom varje resurs i den aktuella konfigurationen. LCM hämtar nyckel värden för den aktuella resurs instansen från filen ". MOF" och använder dem som parametrar för **test** metoden. Om **test** metoden returnerar `$true` , är noden kompatibel med den aktuella resursen och **set** -metoden hoppas över. Om **testet** returnerar `$false` är noden icke-kompatibel. LCM skickar resurs instansens nyckel värden som parametrar till resursens **set** -Metod och återställer noden till efterlevnad.

Genom att ange **utförlig** och **wait** -parametrarna kan du se förloppet för `Start-DSCConfiguration` cmdleten. I det här exemplet är noden redan kompatibel. `Verbose`Utdata anger att **set** -metoden hoppades över.

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

- [Översikt över Azure Automation DSC](/azure/automation/automation-dsc-overview)
- [Konfigurera en SMB-pull-server](../pull-server/pullServerSMB.md)
- [Konfigurera en pull-klient](../pull-server/pullClientConfigID.md)
