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
# <a name="get-test-set"></a><span data-ttu-id="55899-104">Get-test-set</span><span class="sxs-lookup"><span data-stu-id="55899-104">Get-Test-Set</span></span>

><span data-ttu-id="55899-105">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="55899-105">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="55899-106">PowerShell Desired State Configuration är konstruerad runt en **Get** -, **test** -och **set** -process.</span><span class="sxs-lookup"><span data-stu-id="55899-106">PowerShell Desired State Configuration is constructed around a **Get** , **Test** , and **Set** process.</span></span> <span data-ttu-id="55899-107">DSC- [resurser](resources.md) innehåller båda metoder för att slutföra var och en av dessa åtgärder.</span><span class="sxs-lookup"><span data-stu-id="55899-107">DSC [resources](resources.md) each contains methods to complete each of these operations.</span></span>
<span data-ttu-id="55899-108">I en [konfiguration](../configurations/configurations.md)definierar du resurs block för att fylla i nycklar som blir parametrar för en resurs **Get** -, **test** -och **set** -metoder.</span><span class="sxs-lookup"><span data-stu-id="55899-108">In a [Configuration](../configurations/configurations.md), you define resource blocks to fill in keys that become parameters for a resource's **Get** , **Test** , and **Set** methods.</span></span>

<span data-ttu-id="55899-109">Detta är syntaxen för ett **tjänst** resurs block.</span><span class="sxs-lookup"><span data-stu-id="55899-109">This is the syntax for a **Service** resource block.</span></span> <span data-ttu-id="55899-110">**Tjänst** resursen konfigurerar Windows-tjänster.</span><span class="sxs-lookup"><span data-stu-id="55899-110">The **Service** resource configures Windows services.</span></span>

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

<span data-ttu-id="55899-111">Metoderna **Get** , **test** och **set** för **tjänst** resursen kommer att ha parameter block som accepterar dessa värden.</span><span class="sxs-lookup"><span data-stu-id="55899-111">The **Get** , **Test** , and **Set** methods of the **Service** resource will have parameter blocks that accept these values.</span></span>

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
> <span data-ttu-id="55899-112">Språket och metoden som används för att definiera resursen bestämmer hur metoderna **Get** , **test** och **set** ska definieras.</span><span class="sxs-lookup"><span data-stu-id="55899-112">The language and method used to define the resource determines how the **Get** , **Test** , and **Set** methods will be defined.</span></span>

<span data-ttu-id="55899-113">Eftersom **tjänst** resursen bara har en nödvändig nyckel ( `Name` ) kan en **tjänst** block resurs vara så enkel som detta:</span><span class="sxs-lookup"><span data-stu-id="55899-113">Because the **Service** resource only has one required key (`Name`), a **Service** block resource could be as simple as this:</span></span>

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

<span data-ttu-id="55899-114">När du kompilerar konfigurationen ovan lagras de värden som du anger för en nyckel i den `.mof` fil som genereras.</span><span class="sxs-lookup"><span data-stu-id="55899-114">When you compile the Configuration above, the values you specify for a key are stored in the `.mof` file that is generated.</span></span> <span data-ttu-id="55899-115">Mer information finns i [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="55899-115">For more information, see [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>

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

<span data-ttu-id="55899-116">När den används, kommer den [lokala Configuration Manager](../managing-nodes/metaConfig.md) (LCM) att läsa värdet "Spooler" från `.mof` filen och skicka den till **Name** -parametern för **Get** -, **test** -och **set** -instansen för **tjänst** resursen.</span><span class="sxs-lookup"><span data-stu-id="55899-116">When applied, the [Local Configuration Manager](../managing-nodes/metaConfig.md) (LCM) will read the value "Spooler" from the `.mof` file, and pass it to the **Name** parameter of the **Get** , **Test** , and **Set** methods for the "MyService" instance of the **Service** resource.</span></span>

## <a name="get"></a><span data-ttu-id="55899-117">Hämta</span><span class="sxs-lookup"><span data-stu-id="55899-117">Get</span></span>

<span data-ttu-id="55899-118">**Get** -metoden för en resurs, hämtar resursens tillstånd som den är konfigurerad på målnoden.</span><span class="sxs-lookup"><span data-stu-id="55899-118">The **Get** method of a resource, retrieves the state of the resource as it is configured on the target Node.</span></span> <span data-ttu-id="55899-119">Det här status returneras som en [hash-hash](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span><span class="sxs-lookup"><span data-stu-id="55899-119">This state is returned as a [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span> <span data-ttu-id="55899-120">Nycklarna i **hash** -tabellen är de konfigurerbara värden eller parametrarna som resursen accepterar.</span><span class="sxs-lookup"><span data-stu-id="55899-120">The keys of the **hashtable** will be the configurable values, or parameters, the resource accepts.</span></span>

<span data-ttu-id="55899-121">**Get** -metoden mappar direkt till [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) -cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="55899-121">The **Get** method maps directly to the [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet.</span></span>
<span data-ttu-id="55899-122">När du anropar `Get-DSCConfiguration` Kör LCM **Get** -metoden för varje resurs i den aktuella konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="55899-122">When you call `Get-DSCConfiguration`, the LCM runs the **Get** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="55899-123">LCM använder de nyckel värden som lagras i `.mof` filen som parametrar för varje motsvarande resurs instans.</span><span class="sxs-lookup"><span data-stu-id="55899-123">The LCM uses the key values stored in the `.mof` file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="55899-124">Detta är exempel på utdata från en **tjänst** resurs som konfigurerar "Spooler"-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="55899-124">This is sample output from a **Service** resource that configures the "Spooler" service.</span></span>

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

<span data-ttu-id="55899-125">Utdata visar aktuella värde egenskaper som kan konfigureras av **tjänst** resursen.</span><span class="sxs-lookup"><span data-stu-id="55899-125">The output shows the current value properties configurable by the **Service** resource.</span></span>

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

## <a name="test"></a><span data-ttu-id="55899-126">Testa</span><span class="sxs-lookup"><span data-stu-id="55899-126">Test</span></span>

<span data-ttu-id="55899-127">**Test** metoden för en resurs bestämmer om målnoden för närvarande är kompatibel med resursens _önskade tillstånd_ .</span><span class="sxs-lookup"><span data-stu-id="55899-127">The **Test** method of a resource determines if the target node is currently compliant with the resource's _desired state_ .</span></span> <span data-ttu-id="55899-128">**Test** metoden returnerar `$true` eller `$false` visar om noden är kompatibel.</span><span class="sxs-lookup"><span data-stu-id="55899-128">The **Test** method returns `$true` or `$false` only to indicate whether the Node is compliant.</span></span> <span data-ttu-id="55899-129">När du anropar [test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)anropar LCM **test** metoden för varje resurs i den aktuella konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="55899-129">When you call [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), the LCM calls the **Test** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="55899-130">LCM använder nyckel värden som lagras i filen ". MOF" som parametrar för varje motsvarande resurs instans.</span><span class="sxs-lookup"><span data-stu-id="55899-130">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="55899-131">Om resultatet av en enskild resurs **test** är `$false` `Test-DSCConfiguration` returneras `$false` anger att noden inte är kompatibel.</span><span class="sxs-lookup"><span data-stu-id="55899-131">If the result of any individual resource's **Test** is `$false`, `Test-DSCConfiguration` returns `$false` indicating that the Node is not compliant.</span></span> <span data-ttu-id="55899-132">Om alla **test** metoder `$true` för resursen returnerar, `Test-DSCConfiguration` returneras `$true` för att indikera att noden är kompatibel.</span><span class="sxs-lookup"><span data-stu-id="55899-132">If all resource's **Test** methods return `$true`, `Test-DSCConfiguration` returns `$true` to indicate that the Node is compliant.</span></span>

```powershell
Test-DSCConfiguration
```

```output
True
```

<span data-ttu-id="55899-133">Från och med PowerShell 5,0 lades den **detaljerade** parametern till.</span><span class="sxs-lookup"><span data-stu-id="55899-133">Beginning in PowerShell 5.0, the **Detailed** parameter was added.</span></span> <span data-ttu-id="55899-134">Ange **detaljerade** orsaker `Test-DSCConfiguration` till att returnera ett objekt som innehåller samlings resultat för kompatibla och icke-kompatibla resurser.</span><span class="sxs-lookup"><span data-stu-id="55899-134">Specifying **Detailed** causes `Test-DSCConfiguration` to return an object containing collections of results for compliant, and non-compliant resources.</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

<span data-ttu-id="55899-135">Mer information finns i [test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span><span class="sxs-lookup"><span data-stu-id="55899-135">For more information, see [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span>

## <a name="set"></a><span data-ttu-id="55899-136">Ange</span><span class="sxs-lookup"><span data-stu-id="55899-136">Set</span></span>

<span data-ttu-id="55899-137">**Set** -metoden för en resurs försöker tvinga noden att bli kompatibel med resursens *önskade tillstånd* .</span><span class="sxs-lookup"><span data-stu-id="55899-137">The **Set** method of a resource attempts to force the Node to become compliant with the resource's *desired state* .</span></span> <span data-ttu-id="55899-138">**Set** -metoden är avsedd att vara **idempotenta** , vilket innebär att **uppsättningen** kan köras flera gånger och alltid får samma resultat utan fel.</span><span class="sxs-lookup"><span data-stu-id="55899-138">The **Set** method is meant to be **idempotent** , which means that **Set** could be run multiple times and always get the same result without errors.</span></span> <span data-ttu-id="55899-139">När du kör [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration)växlar LCM genom varje resurs i den aktuella konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="55899-139">When you run [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), the LCM cycles through each resource in the currently applied configuration.</span></span> <span data-ttu-id="55899-140">LCM hämtar nyckel värden för den aktuella resurs instansen från filen ". MOF" och använder dem som parametrar för **test** metoden.</span><span class="sxs-lookup"><span data-stu-id="55899-140">The LCM retrieves key values for the current resource instance from the ".mof" file and uses them as parameters for the **Test** method.</span></span> <span data-ttu-id="55899-141">Om **test** metoden returnerar `$true` , är noden kompatibel med den aktuella resursen och **set** -metoden hoppas över.</span><span class="sxs-lookup"><span data-stu-id="55899-141">If the **Test** method returns `$true`, the Node is compliant with the current resource, and the **Set** method is skipped.</span></span> <span data-ttu-id="55899-142">Om **testet** returnerar `$false` är noden icke-kompatibel.</span><span class="sxs-lookup"><span data-stu-id="55899-142">If the **Test** returns `$false`, the Node is non-compliant.</span></span> <span data-ttu-id="55899-143">LCM skickar resurs instansens nyckel värden som parametrar till resursens **set** -Metod och återställer noden till efterlevnad.</span><span class="sxs-lookup"><span data-stu-id="55899-143">The LCM passes the resource instance's key values as parameters to the resource's **Set** method, restoring the Node to compliance.</span></span>

<span data-ttu-id="55899-144">Genom att ange **utförlig** och **wait** -parametrarna kan du se förloppet för `Start-DSCConfiguration` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="55899-144">By specifying the **Verbose** and **Wait** parameters, you can watch the progress of the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="55899-145">I det här exemplet är noden redan kompatibel.</span><span class="sxs-lookup"><span data-stu-id="55899-145">In this example, the Node is already compliant.</span></span> <span data-ttu-id="55899-146">`Verbose`Utdata anger att **set** -metoden hoppades över.</span><span class="sxs-lookup"><span data-stu-id="55899-146">The `Verbose` output indicates that the **Set** method was skipped.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="55899-147">Se även</span><span class="sxs-lookup"><span data-stu-id="55899-147">See also</span></span>

- [<span data-ttu-id="55899-148">Översikt över Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="55899-148">Azure Automation DSC Overview</span></span>](/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="55899-149">Konfigurera en SMB-pull-server</span><span class="sxs-lookup"><span data-stu-id="55899-149">Setting up an SMB pull server</span></span>](../pull-server/pullServerSMB.md)
- [<span data-ttu-id="55899-150">Konfigurera en pull-klient</span><span class="sxs-lookup"><span data-stu-id="55899-150">Configuring a pull client</span></span>](../pull-server/pullClientConfigID.md)
