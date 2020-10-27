---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguration, installation
title: Tillämpa, hämta och testa konfigurationer på en nod
description: I den här guiden får du lära dig hur du arbetar med konfigurationer på en målnod.
ms.openlocfilehash: 6bc9262bc0e2ce8eea7b85bd46ecc0c0a691276d
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651017"
---
# <a name="apply-get-and-test-configurations-on-a-node"></a><span data-ttu-id="bb7a6-104">Tillämpa, hämta och testa konfigurationer på en nod</span><span class="sxs-lookup"><span data-stu-id="bb7a6-104">Apply, Get, and Test Configurations on a Node</span></span>

<span data-ttu-id="bb7a6-105">I den här guiden får du lära dig hur du arbetar med konfigurationer på en målnod.</span><span class="sxs-lookup"><span data-stu-id="bb7a6-105">This guide will show you how to work with Configurations on a target Node.</span></span> <span data-ttu-id="bb7a6-106">Den här guiden är uppdelad i följande steg:</span><span class="sxs-lookup"><span data-stu-id="bb7a6-106">This guide is broken up into the following steps:</span></span>

## <a name="apply-a-configuration"></a><span data-ttu-id="bb7a6-107">Använd en konfiguration</span><span class="sxs-lookup"><span data-stu-id="bb7a6-107">Apply a Configuration</span></span>

<span data-ttu-id="bb7a6-108">Vi måste generera en ". MOF"-fil för att kunna tillämpa och hantera en konfiguration.</span><span class="sxs-lookup"><span data-stu-id="bb7a6-108">In order to apply and manage a Configuration, we need to generate a ".mof" file.</span></span> <span data-ttu-id="bb7a6-109">Följande kod visar en enkel konfiguration som kommer att användas i den här guiden.</span><span class="sxs-lookup"><span data-stu-id="bb7a6-109">The following code will represent a simple Configuration that will be used throughout this guide.</span></span>

```powershell
Configuration Sample
{
    # This will generate two .mof files, a localhost.mof, and a server02.mof
    Node localhost, server02
    {
        File SampleFile
        {
            DestinationPath = 'C:\Temp\temp.txt'
            Contents = 'This is a simple resource to show Configuration functionality on a Node.'
        }
    }
}

# The -OutputPath parameter is built into every Configuration automatically.
# The value of -OutputPath determines where the .mof file should be stored, once compiled.
Sample -OutputPath "C:\Temp\"
```

<span data-ttu-id="bb7a6-110">Om du kompilerar den här konfigurationen skickas två ". MOF"-filer.</span><span class="sxs-lookup"><span data-stu-id="bb7a6-110">Compiling this configuration will yield two ".mof" files.</span></span>

```Output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

<span data-ttu-id="bb7a6-111">Använd cmdleten [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) för att tillämpa en konfiguration.</span><span class="sxs-lookup"><span data-stu-id="bb7a6-111">To apply a Configuration, use the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="bb7a6-112">`-Path`Parametern anger en katalog där ". MOF"-filer finns.</span><span class="sxs-lookup"><span data-stu-id="bb7a6-112">The `-Path` parameter specifies a directory where ".mof" files reside.</span></span> <span data-ttu-id="bb7a6-113">Om inget `-Computername` anges `Start-DSCConfiguration` försöker att tillämpa varje konfiguration till dator namnet som anges av namnet på. MOF-filen ( `<computername>.mof` ).</span><span class="sxs-lookup"><span data-stu-id="bb7a6-113">If no `-Computername` is specified, `Start-DSCConfiguration` will attempt to apply each Configuration to the computer name specified by the name of the '.mof' file (`<computername>.mof`).</span></span> <span data-ttu-id="bb7a6-114">Ange `-Verbose` om du vill `Start-DSCConfiguration` Visa mer utförlig utdata.</span><span class="sxs-lookup"><span data-stu-id="bb7a6-114">Specify `-Verbose` to `Start-DSCConfiguration` to see more verbose output.</span></span>

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

<span data-ttu-id="bb7a6-115">Om `-Wait` inte anges visas ett jobb som skapats.</span><span class="sxs-lookup"><span data-stu-id="bb7a6-115">If `-Wait` is not specified, you see one job created.</span></span> <span data-ttu-id="bb7a6-116">Jobbet som skapas kommer att ha en **ChildJob** för varje ". MOF"-fil som bearbetas av `Start-DSCConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="bb7a6-116">The job created will have one **ChildJob** for each ".mof" file processed by `Start-DSCConfiguration`.</span></span>

```Output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

<span data-ttu-id="bb7a6-117">Om en konfiguration tar lång tid och du vill stoppa den, kan du använda [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) för att stoppa programmet på den lokala noden.</span><span class="sxs-lookup"><span data-stu-id="bb7a6-117">If a Configuration is taking a long time and you want to stop it, you can use [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) to stop application on the local Node.</span></span>

```powershell
Stop-DSCConfiguration -Force
```

<span data-ttu-id="bb7a6-118">När du är klar kan du Visa jobbets status genom det jobb objekt som returneras av [Get-Job](/powershell/module/microsoft.powershell.core/get-job).</span><span class="sxs-lookup"><span data-stu-id="bb7a6-118">Once complete, you can view the status of the jobs through the job object returned by [Get-Job](/powershell/module/microsoft.powershell.core/get-job).</span></span>

```powershell
$job = Get-Job
$job.ChildJobs
```

```Output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
49     Job49           Configuratio... Completed     True            localhost            Start-DSCConfiguration...
50     Job50           Configuratio... Completed     True            server02             Start-DSCConfiguration...
```

<span data-ttu-id="bb7a6-119">Om du vill se **utförliga** utdata använder du följande kommandon för att visa **utförlig** data ström för varje **ChildJob** .</span><span class="sxs-lookup"><span data-stu-id="bb7a6-119">To see the **Verbose** output, use the following commands to view the **Verbose** stream for each **ChildJob** .</span></span> <span data-ttu-id="bb7a6-120">Mer information om PowerShell-jobb finns [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span><span class="sxs-lookup"><span data-stu-id="bb7a6-120">For more about PowerShell jobs, see [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span></span>

```powershell
# View the verbose output of the localhost job using array indexing.
$job.ChildJobs[0].Verbose
```

```Output
Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,
'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
An LCM method call arrived from computer SERVER01 with user sid S-1-5-21-124525095-708259637-1543119021-1282804.
[SERVER01]: LCM:  [ Start  Set      ]
[SERVER01]: LCM:  [ Start  Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ Start  Test     ]  [[File]SampleFile]
[SERVER01]:                            [[File]SampleFile] The destination object was found and no action is required.
[SERVER01]: LCM:  [ End    Test     ]  [[File]SampleFile]  in 0.0370 seconds.
[SERVER01]: LCM:  [ Skip   Set      ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Set      ]
[SERVER01]: LCM:  [ End    Set      ]    in  0.2400 seconds.
Operation 'Invoke CimMethod' complete.
```

<span data-ttu-id="bb7a6-121">Från och med PowerShell 5,0 `-UseExisting` lades parametern till i `Start-DSCConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="bb7a6-121">Beginning in PowerShell 5.0, the `-UseExisting` parameter was added to `Start-DSCConfiguration`.</span></span> <span data-ttu-id="bb7a6-122">Genom `-UseExisting` att ange instruerar du cmdleten att använda den befintliga tillämpade konfigurationen i stället för en som anges av `-Path` parametern.</span><span class="sxs-lookup"><span data-stu-id="bb7a6-122">By specifying `-UseExisting`, you instruct the cmdlet to use the existing applied Configuration instead of one specified by the `-Path` parameter.</span></span>

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a><span data-ttu-id="bb7a6-123">Testa en konfiguration</span><span class="sxs-lookup"><span data-stu-id="bb7a6-123">Test a Configuration</span></span>

<span data-ttu-id="bb7a6-124">Du kan testa en aktuell konfiguration med hjälp av [test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span><span class="sxs-lookup"><span data-stu-id="bb7a6-124">You can test a currently applied Configuration using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span>
<span data-ttu-id="bb7a6-125">`Test-DSCConfiguration` kommer att returneras `True` om noden är kompatibel och `False` inte.</span><span class="sxs-lookup"><span data-stu-id="bb7a6-125">`Test-DSCConfiguration` will return `True` if the Node is compliant, and `False` if it is not.</span></span>

```powershell
Test-DSCConfiguration
```

<span data-ttu-id="bb7a6-126">Från och med PowerShell 5,0 `-Detailed` lades parametern till som returnerar ett objekt med samlingar för **ResourcesInDesiredState** och **ResourcesNotInDesiredState**</span><span class="sxs-lookup"><span data-stu-id="bb7a6-126">Beginning in PowerShell 5.0, the `-Detailed` parameter was added which returns an object with collections for **ResourcesInDesiredState** and **ResourcesNotInDesiredState**</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

<span data-ttu-id="bb7a6-127">Från och med PowerShell 5,0 kan du testa en konfiguration utan att använda den.</span><span class="sxs-lookup"><span data-stu-id="bb7a6-127">Beginning in PowerShell 5.0 you can test a Configuration without applying it.</span></span> <span data-ttu-id="bb7a6-128">`-ReferenceConfiguration`Parametern accepterar sökvägen till en ". MOF"-fil för att testa noden mot.</span><span class="sxs-lookup"><span data-stu-id="bb7a6-128">The `-ReferenceConfiguration` parameter accepts the path of a ".mof" file to test the Node against.</span></span> <span data-ttu-id="bb7a6-129">Inga **uppsättnings** åtgärder vidtas mot noden.</span><span class="sxs-lookup"><span data-stu-id="bb7a6-129">No **Set** actions are taken against the Node.</span></span> <span data-ttu-id="bb7a6-130">I PowerShell 4,0 finns det lösningar för att testa en konfiguration utan att använda den, men de beskrivs inte här.</span><span class="sxs-lookup"><span data-stu-id="bb7a6-130">In PowerShell 4.0, there are workarounds to test a Configuration without applying it, but they are not discussed here.</span></span>

## <a name="get-configuration-values"></a><span data-ttu-id="bb7a6-131">Hämta konfigurations värden</span><span class="sxs-lookup"><span data-stu-id="bb7a6-131">Get Configuration Values</span></span>

<span data-ttu-id="bb7a6-132">Cmdlet [: en get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) returnerar de aktuella värdena för alla konfigurerade resurser i den aktuella konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="bb7a6-132">The [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet returns the current values for any configured resources in the currently applied Configuration.</span></span>

```powershell
Get-DSCConfiguration
```

<span data-ttu-id="bb7a6-133">Utdata från vår exempel konfiguration skulle se ut så här om de tillämpas korrekt.</span><span class="sxs-lookup"><span data-stu-id="bb7a6-133">Output from our sample Configuration would look like this if applied successfully.</span></span>

```Output
ConfigurationName    : Sample
DependsOn            :
ModuleName           : PSDesiredStateConfiguration
ModuleVersion        :
PsDscRunAsCredential :
ResourceId           : [File]SampleFile
SourceInfo           :
Attributes           : {archive}
Checksum             :
Contents             :
CreatedDate          : 11/27/2018 7:16:06 AM
Credential           :
DestinationPath      : C:\Temp\temp.txt
Ensure               : present
Force                :
MatchSource          :
ModifiedDate         : 11/27/2018 7:16:06 AM
Recurse              :
Size                 : 75
SourcePath           :
SubItems             :
Type                 : file
PSComputerName       :
CimClassName         : MSFT_FileDirectoryConfiguration
```

## <a name="get-configuration-status"></a><span data-ttu-id="bb7a6-134">Hämta konfigurations status</span><span class="sxs-lookup"><span data-stu-id="bb7a6-134">Get Configuration Status</span></span>

<span data-ttu-id="bb7a6-135">Med början i PowerShell 5,0 cmdleten [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) kan du se historiken över tillämpade konfigurationer på noden.</span><span class="sxs-lookup"><span data-stu-id="bb7a6-135">Beginning in PowerShell 5.0 the [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet allows you to see the history of applied Configurations to the node.</span></span> <span data-ttu-id="bb7a6-136">PowerShell DSC håller koll på de senaste {{N}} konfigurationerna som tillämpas i **push** -eller **pull** -läge.</span><span class="sxs-lookup"><span data-stu-id="bb7a6-136">PowerShell DSC keeps track of the last {{N}} Configurations applied in **Push** or **Pull** mode.</span></span> <span data-ttu-id="bb7a6-137">Detta omfattar alla *konsekvens* kontroller som utförs av LCM.</span><span class="sxs-lookup"><span data-stu-id="bb7a6-137">This includes any *consistency* checks executed by the LCM.</span></span> <span data-ttu-id="bb7a6-138">Som standard `Get-DSCConfigurationStatus` visas endast den sista historik posten.</span><span class="sxs-lookup"><span data-stu-id="bb7a6-138">By default, `Get-DSCConfigurationStatus` shows you the last history entry only.</span></span>

```powershell
Get-DSCConfigurationStatus
```

```Output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

<span data-ttu-id="bb7a6-139">Använd `-All` parametern för att se all konfigurations status historik.</span><span class="sxs-lookup"><span data-stu-id="bb7a6-139">Use the `-All` parameter to see all Configuration Status history.</span></span>

> [!NOTE]
> <span data-ttu-id="bb7a6-140">Utdata trunkeras för det kortfattat.</span><span class="sxs-lookup"><span data-stu-id="bb7a6-140">Output is truncated for brevity.</span></span>

```powershell
Get-DSCConfigurationStatus -All
```

```Output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
Success    11/27/2018 7:16:06 AM     Initial         PUSH  False                1
Success    11/27/2018 7:04:53 AM     Initial         PUSH  False                1
Success    11/27/2018 7:03:45 AM     Consistency     PUSH  False                2
Success    11/27/2018 7:03:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:48:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:44 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:18:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:03:44 AM     Consistency     PUSH  False                2
```

## <a name="manage-configuration-documents"></a><span data-ttu-id="bb7a6-141">Hantera konfigurations dokument</span><span class="sxs-lookup"><span data-stu-id="bb7a6-141">Manage Configuration Documents</span></span>

<span data-ttu-id="bb7a6-142">LCM hanterar nodens konfiguration genom att arbeta med **konfigurations dokument** .</span><span class="sxs-lookup"><span data-stu-id="bb7a6-142">The LCM manages the Configuration of the Node by working with **Configuration Documents** .</span></span> <span data-ttu-id="bb7a6-143">Dessa ". MOF"-filer finns i `C:\Windows\System32\Configuration` katalogen.</span><span class="sxs-lookup"><span data-stu-id="bb7a6-143">These ".mof" files reside in the `C:\Windows\System32\Configuration` directory.</span></span>

<span data-ttu-id="bb7a6-144">Från och med PowerShell 5,0 gör [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) att du kan ta bort filerna ". MOF" för att stoppa framtida konsekvens kontroller eller ta bort en konfiguration som har fel när den tillämpas.</span><span class="sxs-lookup"><span data-stu-id="bb7a6-144">Beginning in PowerShell 5.0 the [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) allows you to remove the ".mof" files to stop future consistency checks or remove a Configuration that has errors when applied.</span></span> <span data-ttu-id="bb7a6-145">`-Stage`Parametern låter dig ange vilken ". MOF"-fil som du vill ta bort.</span><span class="sxs-lookup"><span data-stu-id="bb7a6-145">The `-Stage` parameter allows you to specify which ".mof" file you want to remove.</span></span>

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> <span data-ttu-id="bb7a6-146">I PowerShell 4,0 kan du fortfarande ta bort dessa ". MOF"-filer direkt med [Remove-item](/powershell/module/microsoft.powershell.management/remove-item).</span><span class="sxs-lookup"><span data-stu-id="bb7a6-146">In PowerShell 4.0, you can still remove these ".mof" files directly using [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).</span></span>

## <a name="publish-configurations"></a><span data-ttu-id="bb7a6-147">Publicera konfigurationer</span><span class="sxs-lookup"><span data-stu-id="bb7a6-147">Publish Configurations</span></span>

<span data-ttu-id="bb7a6-148">Från och med PowerShell 5,0 lades cmdleten [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) till.</span><span class="sxs-lookup"><span data-stu-id="bb7a6-148">Beginning in PowerShell 5.0, the [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet was added.</span></span> <span data-ttu-id="bb7a6-149">Med den här cmdleten kan du publicera en ". MOF"-fil på fjärrdatorer utan att använda den.</span><span class="sxs-lookup"><span data-stu-id="bb7a6-149">This cmdlet allows you to publish a ".mof" file to remote computers, without applying it.</span></span>

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a><span data-ttu-id="bb7a6-150">Se även</span><span class="sxs-lookup"><span data-stu-id="bb7a6-150">See also</span></span>

- [<span data-ttu-id="bb7a6-151">Hämta, testa och tillämpa</span><span class="sxs-lookup"><span data-stu-id="bb7a6-151">Get, Test, and Set</span></span>](../resources/get-test-set.md)
