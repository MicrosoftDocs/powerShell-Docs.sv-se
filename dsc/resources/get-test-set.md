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
# <a name="get-test-set"></a><span data-ttu-id="c7f49-103">Get-Test-Set</span><span class="sxs-lookup"><span data-stu-id="c7f49-103">Get-Test-Set</span></span>

><span data-ttu-id="c7f49-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c7f49-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

![Hämta, testa och tillämpa](/media/get-test-set.png)

<span data-ttu-id="c7f49-106">PowerShell Desired State Configuration är uppbyggd kring ett **hämta**, **Test**, och **ange** processen.</span><span class="sxs-lookup"><span data-stu-id="c7f49-106">PowerShell Desired State Configuration is constructed around a **Get**, **Test**, and **Set** process.</span></span> <span data-ttu-id="c7f49-107">DSC [resurser](resources.md) var och en innehåller metoder för att slutföra var och en av dessa åtgärder.</span><span class="sxs-lookup"><span data-stu-id="c7f49-107">DSC [resources](resources.md) each contains methods to complete each of these operations.</span></span> <span data-ttu-id="c7f49-108">I en [Configuration](../configurations/configurations.md), definierar du resursen förutsättningarna för att fylla i nycklar som blivit parametrar för en resurs **hämta**, **Test**, och **ange** metoder.</span><span class="sxs-lookup"><span data-stu-id="c7f49-108">In a [Configuration](../configurations/configurations.md), you define resource blocks to fill in keys that become parameters for a resource's **Get**, **Test**, and **Set** methods.</span></span>

<span data-ttu-id="c7f49-109">Det här är syntaxen för en **Service** resource block.</span><span class="sxs-lookup"><span data-stu-id="c7f49-109">This is the syntax for a **Service** resource block.</span></span> <span data-ttu-id="c7f49-110">Den **Service** resource konfigurerar Windows-tjänster.</span><span class="sxs-lookup"><span data-stu-id="c7f49-110">The **Service** resource configures Windows services.</span></span>

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

<span data-ttu-id="c7f49-111">Den **hämta**, **Test**, och **ange** metoderna i den **Service** resursen måste parameterblock som har stöd för dessa värden.</span><span class="sxs-lookup"><span data-stu-id="c7f49-111">The **Get**, **Test**, and **Set** methods of the **Service** resource will have parameter blocks that accept these values.</span></span>

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
> <span data-ttu-id="c7f49-112">Det språk och den metod som används för att definiera resursen avgör hur **hämta**, **Test**, och **ange** metoder definieras.</span><span class="sxs-lookup"><span data-stu-id="c7f49-112">The language and method used to define the resource determines how the **Get**, **Test**, and **Set** methods will be defined.</span></span>

<span data-ttu-id="c7f49-113">Eftersom den **Service** resursen har endast en nödvändig nyckel (`Name`), ett **Service** block resurs kan vara så enkla som detta:</span><span class="sxs-lookup"><span data-stu-id="c7f49-113">Because the **Service** resource only has one required key (`Name`), a **Service** block resource could be as simple as this:</span></span>

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

<span data-ttu-id="c7f49-114">När du kompilera konfigurationen ovan, lagras de värden som du anger för en nyckel i filen ”.mof” som genereras.</span><span class="sxs-lookup"><span data-stu-id="c7f49-114">When you compile the Configuration above, the values you specify for a key are stored in the ".mof" file that is generated.</span></span> <span data-ttu-id="c7f49-115">Mer information finns i [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="c7f49-115">For more information, see [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>

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

<span data-ttu-id="c7f49-116">Vid tillämpningen den [lokal konfigurationshanterare](../managing-nodes/metaConfig.md) (LCM) kommer att läsa värdet ”utskriftshanterarens” från ”.mof”-fil och skicka det till den `-Name` -parametern för den **hämta**, **Test**, och **ange** metoder för ”Mintjänst”-instansen av den **Service** resurs.</span><span class="sxs-lookup"><span data-stu-id="c7f49-116">When applied, the [Local Configuration Manager](../managing-nodes/metaConfig.md) (LCM) will read the value "Spooler" from the ".mof" file, and pass it to the `-Name` parameter of the **Get**, **Test**, and **Set** methods for the "MyService" instance of the **Service** resource.</span></span>

## <a name="get"></a><span data-ttu-id="c7f49-117">Get</span><span class="sxs-lookup"><span data-stu-id="c7f49-117">Get</span></span>

<span data-ttu-id="c7f49-118">Den **hämta** -metoden för en resurs, hämtar tillståndet för resursen eftersom den är konfigurerad på mål-nod.</span><span class="sxs-lookup"><span data-stu-id="c7f49-118">The **Get** method of a resource, retrieves the state of the resource as it is configured on the target Node.</span></span> <span data-ttu-id="c7f49-119">Det här tillståndet returneras som en [hash-tabell](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span><span class="sxs-lookup"><span data-stu-id="c7f49-119">This state is returned as a [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span> <span data-ttu-id="c7f49-120">Nycklarna för den **hash-tabell** ska vara konfigurerbara värden eller parametrar, resursen accepterar.</span><span class="sxs-lookup"><span data-stu-id="c7f49-120">The keys of the **hashtable** will be the configurable values, or parameters, the resource accepts.</span></span>

<span data-ttu-id="c7f49-121">Den **hämta** metoden mappar direkt till den [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c7f49-121">The **Get** method maps directly to the [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="c7f49-122">När du anropar `Get-DSCConfiguration`, MGM körningar den **hämta** -metoden för varje resurs i konfigurationen som används.</span><span class="sxs-lookup"><span data-stu-id="c7f49-122">When you call `Get-DSCConfiguration`, the LCM runs the **Get** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="c7f49-123">LCM använder de viktiga värden som lagras i filen ”.mof” som parametrar för varje motsvarande resursinstans.</span><span class="sxs-lookup"><span data-stu-id="c7f49-123">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="c7f49-124">Det här är exempel på utdata från en **Service** resurs som konfigurerar ”Utskriftshanteraren”.</span><span class="sxs-lookup"><span data-stu-id="c7f49-124">This is sample output from a **Service** resource that configures the "Spooler" service.</span></span>

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

<span data-ttu-id="c7f49-125">Utdata visar de aktuella värdet egenskaperna kan konfigureras genom att den **Service** resurs.</span><span class="sxs-lookup"><span data-stu-id="c7f49-125">The output shows the current value properties configurable by the **Service** resource.</span></span>

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

## <a name="test"></a><span data-ttu-id="c7f49-126">Testa</span><span class="sxs-lookup"><span data-stu-id="c7f49-126">Test</span></span>

<span data-ttu-id="c7f49-127">Den **Test** -metoden för en resurs avgör om Målnoden är för närvarande är kompatibel med resursens *önskade tillstånd*.</span><span class="sxs-lookup"><span data-stu-id="c7f49-127">The **Test** method of a resource determines if the target node is currently compliant with the resource's *desired state*.</span></span> <span data-ttu-id="c7f49-128">Den **Test** metoden returnerar `$True` eller `$False` endast för att indikera om noden är kompatibel.</span><span class="sxs-lookup"><span data-stu-id="c7f49-128">The **Test** method returns `$True` or `$False` only to indicate whether the Node is compliant.</span></span>
<span data-ttu-id="c7f49-129">När du anropar [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), LCM-anrop i **Test** metod för varje resurs i konfigurationen som används.</span><span class="sxs-lookup"><span data-stu-id="c7f49-129">When you call [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), the LCM calls the **Test** method of each resource in the currently applied configuration.</span></span> <span data-ttu-id="c7f49-130">LCM använder de viktiga värden som lagras i filen ”.mof” som parametrar för varje motsvarande resursinstans.</span><span class="sxs-lookup"><span data-stu-id="c7f49-130">The LCM uses the key values stored in the ".mof" file as parameters to each corresponding resource instance.</span></span>

<span data-ttu-id="c7f49-131">Om resultatet av en enskild resurs **Test** är `$False`, `Test-DSCConfiguration` returnerar `$False` som anger att noden inte är kompatibla.</span><span class="sxs-lookup"><span data-stu-id="c7f49-131">If the result of any individual resource's **Test** is `$False`, `Test-DSCConfiguration` returns `$False` indicating that the Node is not compliant.</span></span> <span data-ttu-id="c7f49-132">Om alla resursens **Test** metoder returnerar `$True`, `Test-DSCConfiguration` returnerar `$True` som visar att noden är kompatibla.</span><span class="sxs-lookup"><span data-stu-id="c7f49-132">If all resource's **Test** methods return `$True`, `Test-DSCConfiguration` returns `$True` to indicate that the Node is compliant.</span></span>

```powershell
Test-DSCConfiguration
```

```output
True
```

<span data-ttu-id="c7f49-133">Från och med PowerShell 5.0 på `-Detailed` parameter har lagts till.</span><span class="sxs-lookup"><span data-stu-id="c7f49-133">Beginning in PowerShell 5.0, the `-Detailed` parameter was added.</span></span> <span data-ttu-id="c7f49-134">Ange `-Detailed` orsakar `Test-DSCConfiguration` att returnera ett objekt som innehåller samlingar av resultat för kompatibla och icke-kompatibla resurser.</span><span class="sxs-lookup"><span data-stu-id="c7f49-134">Specifying `-Detailed` causes `Test-DSCConfiguration` to return an object containing collections of results for compliant, and non-compliant resources.</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

<span data-ttu-id="c7f49-135">Mer information finns i [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)</span><span class="sxs-lookup"><span data-stu-id="c7f49-135">For more information, see [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)</span></span>

## <a name="set"></a><span data-ttu-id="c7f49-136">Ange</span><span class="sxs-lookup"><span data-stu-id="c7f49-136">Set</span></span>

<span data-ttu-id="c7f49-137">Den **ange** -metoden för en resurs försöker tvinga noden ska bli kompatibla med resursens *önskade tillstånd*.</span><span class="sxs-lookup"><span data-stu-id="c7f49-137">The **Set** method of a resource attempts to force the Node to become compliant with the resource's *desired state*.</span></span> <span data-ttu-id="c7f49-138">Den **ange** metoden är avsedd att vara **idempotenta**, vilket innebär att **ange** kan köra flera gånger och alltid få samma resultat utan fel.</span><span class="sxs-lookup"><span data-stu-id="c7f49-138">The **Set** method is meant to be **idempotent**, which means that **Set** could be run multiple times and always get the same result without errors.</span></span>  <span data-ttu-id="c7f49-139">När du kör [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), MGM växlar mellan varje resurs i konfigurationen som används.</span><span class="sxs-lookup"><span data-stu-id="c7f49-139">When you run [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), the LCM cycles through each resource in the currently applied configuration.</span></span> <span data-ttu-id="c7f49-140">LCM hämtar nyckelvärden för den aktuella resursinstansen från filen ”.mof” och använder dem som parametrar för den **Test** metod.</span><span class="sxs-lookup"><span data-stu-id="c7f49-140">The LCM retrieves key values for the current resource instance from the ".mof" file and uses them as parameters for the **Test** method.</span></span> <span data-ttu-id="c7f49-141">Om den **Test** metoden returnerar `$True`, noden är kompatibel med den aktuella resursen och **ange** metoden hoppas över.</span><span class="sxs-lookup"><span data-stu-id="c7f49-141">If the **Test** method returns `$True`, the Node is compliant with the current resource, and the **Set** method is skipped.</span></span> <span data-ttu-id="c7f49-142">Om den **Test** returnerar `$False`, noden inte är kompatibel.</span><span class="sxs-lookup"><span data-stu-id="c7f49-142">If the **Test** returns `$False`, the Node is non-compliant.</span></span>  <span data-ttu-id="c7f49-143">LCM skickar resursen instansens nyckelvärden som parametrar till resursens **ange** metod, återställa noden för efterlevnad.</span><span class="sxs-lookup"><span data-stu-id="c7f49-143">The LCM passes the resource instance's key values as parameters to the resource's **Set** method, restoring the Node to compliance.</span></span>

<span data-ttu-id="c7f49-144">Genom att ange den `-Verbose` och `-Wait` parametrar, som du kan se förloppet för den `Start-DSCConfiguration` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c7f49-144">By specifying the `-Verbose` and `-Wait` parameters, you can watch the progress of the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="c7f49-145">I det här exemplet är noden redan kompatibel.</span><span class="sxs-lookup"><span data-stu-id="c7f49-145">In this example, the Node is already compliant.</span></span> <span data-ttu-id="c7f49-146">Den `Verbose` utdata indikerar att den **ange** metoden hoppades över.</span><span class="sxs-lookup"><span data-stu-id="c7f49-146">The `Verbose` output indicates that the **Set** method was skipped.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c7f49-147">Se även</span><span class="sxs-lookup"><span data-stu-id="c7f49-147">See also</span></span>

- [<span data-ttu-id="c7f49-148">Översikt över Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="c7f49-148">Azure Automation DSC Overview</span></span>](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="c7f49-149">Konfigurera en SMB-pullserver</span><span class="sxs-lookup"><span data-stu-id="c7f49-149">Setting up an SMB pull server</span></span>](../pull-server/pullServerSMB.md)
- [<span data-ttu-id="c7f49-150">Konfigurera en pullklient</span><span class="sxs-lookup"><span data-stu-id="c7f49-150">Configuring a pull client</span></span>](../pull-server/pullClientConfigID.md)
