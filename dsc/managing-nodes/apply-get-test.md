---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguration, installation
title: Tillämpa, hämta och testa konfigurationer på en nod
ms.openlocfilehash: 41f8d2d75d3dd9621de615e7999c2690cb8ce44a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684341"
---
# <a name="apply-get-and-test-configurations-on-a-node"></a><span data-ttu-id="b1b12-103">Tillämpa, hämta och testa konfigurationer på en nod</span><span class="sxs-lookup"><span data-stu-id="b1b12-103">Apply, Get, and Test Configurations on a Node</span></span>

<span data-ttu-id="b1b12-104">Den här guiden visar hur du arbetar med konfigurationer på ett mål noden.</span><span class="sxs-lookup"><span data-stu-id="b1b12-104">This guide will show you how to work with Configurations on a target Node.</span></span> <span data-ttu-id="b1b12-105">Den här guiden har delats upp i följande steg:</span><span class="sxs-lookup"><span data-stu-id="b1b12-105">This guide is broken up into the following steps:</span></span>

## <a name="apply-a-configuration"></a><span data-ttu-id="b1b12-106">Tillämpa en konfiguration</span><span class="sxs-lookup"><span data-stu-id="b1b12-106">Apply a Configuration</span></span>

<span data-ttu-id="b1b12-107">Vill använda och hantera en konfiguration, måste vi du generera en ”.mof”-fil.</span><span class="sxs-lookup"><span data-stu-id="b1b12-107">In order to apply and manage a Configuration, we need to generate a ".mof" file.</span></span> <span data-ttu-id="b1b12-108">Följande kod representerar en enkel konfiguration som ska användas i den här guiden.</span><span class="sxs-lookup"><span data-stu-id="b1b12-108">The following code will represent a simple Configuration that will be used throughout this guide.</span></span>

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

<span data-ttu-id="b1b12-109">Kompilera den här konfigurationen ger två MOF-filerna.</span><span class="sxs-lookup"><span data-stu-id="b1b12-109">Compiling this configuration will yield two ".mof" files.</span></span>

```output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

<span data-ttu-id="b1b12-110">Tillämpa en konfiguration genom att använda den [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b1b12-110">To apply a Configuration, use the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="b1b12-111">Den `-Path` parametern anger en katalog som där MOF-filerna finns.</span><span class="sxs-lookup"><span data-stu-id="b1b12-111">The `-Path` parameter specifies a directory where ".mof" files reside.</span></span> <span data-ttu-id="b1b12-112">Om ingen `-Computername` anges `Start-DSCConfiguration` försöker gäller varje konfiguration för datornamnet som anges av namnet på 'MOF-filen (\<computername\>.mof).</span><span class="sxs-lookup"><span data-stu-id="b1b12-112">If no `-Computername` is specified, `Start-DSCConfiguration` will attempt to apply each Configuration to the computer name specified by the name of the '.mof' file (\<computername\>.mof).</span></span> <span data-ttu-id="b1b12-113">Ange `-Verbose` till `Start-DSCConfiguration` att se mer utförliga utdata.</span><span class="sxs-lookup"><span data-stu-id="b1b12-113">Specify `-Verbose` to `Start-DSCConfiguration` to see more verbose output.</span></span>

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

<span data-ttu-id="b1b12-114">Om `-Wait` inte anges visas ett jobb som skapats.</span><span class="sxs-lookup"><span data-stu-id="b1b12-114">If `-Wait` is not specified, you see one job created.</span></span> <span data-ttu-id="b1b12-115">Ett jobb som skapats ska ha en **ChildJob** för varje ”.mof” fil bearbetas av `Start-DSCConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="b1b12-115">The job created will have one **ChildJob** for each ".mof" file processed by `Start-DSCConfiguration`.</span></span>

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

<span data-ttu-id="b1b12-116">Om en konfiguration tar lång tid och du vill stoppa den kan du använda [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) att stoppa programmet på den lokala noden.</span><span class="sxs-lookup"><span data-stu-id="b1b12-116">If a Configuration is taking a long time and you want to stop it, you can use [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) to stop application on the local Node.</span></span>

```powershell
Stop-DSCConfiguration -Force
```

<span data-ttu-id="b1b12-117">När du är klar kan du visa status för jobb via jobbobjektet som returnerades av [Get-Job](/powershell/module/microsoft.powershell.core/get-job).</span><span class="sxs-lookup"><span data-stu-id="b1b12-117">Once complete, you can view the status of the jobs through the job object returned by [Get-Job](/powershell/module/microsoft.powershell.core/get-job).</span></span>

```powershell
$job = Get-Job
$job.ChildJobs
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
49     Job49           Configuratio... Completed     True            localhost            Start-DSCConfiguration...
50     Job50           Configuratio... Completed     True            server02             Start-DSCConfiguration...
```

<span data-ttu-id="b1b12-118">Se den **utförlig** utdata, Använd följande kommandon för att visa den **utförlig** stream för varje **ChildJob**.</span><span class="sxs-lookup"><span data-stu-id="b1b12-118">To see the **Verbose** output, use the following commands to view the **Verbose** stream for each **ChildJob**.</span></span> <span data-ttu-id="b1b12-119">Mer information om PowerShell-jobb finns i [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span><span class="sxs-lookup"><span data-stu-id="b1b12-119">For more about PowerShell jobs, see [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span></span>

```powershell
# View the verbose output of the localhost job using array indexing.
$job.ChildJobs[0].Verbose
```

```output
Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
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

<span data-ttu-id="b1b12-120">Från och med PowerShell 5.0, den `-UseExisting` parameter har lagts till i `Start-DSCConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="b1b12-120">Beginning in PowerShell 5.0, the `-UseExisting` parameter was added to `Start-DSCConfiguration`.</span></span> <span data-ttu-id="b1b12-121">Genom att ange `-UseExisting`, du instruera cmdlet för att använda den befintliga konfigurationen som används i stället för som anges av den `-Path` parametern.</span><span class="sxs-lookup"><span data-stu-id="b1b12-121">By specifying `-UseExisting`, you instruct the cmdlet to use the existing applied Configuration instead of one specified by the `-Path` parameter.</span></span>

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a><span data-ttu-id="b1b12-122">Testa en konfiguration</span><span class="sxs-lookup"><span data-stu-id="b1b12-122">Test a Configuration</span></span>

<span data-ttu-id="b1b12-123">Du kan testa en som används konfiguration med hjälp av [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span><span class="sxs-lookup"><span data-stu-id="b1b12-123">You can test a currently applied Configuration using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span> <span data-ttu-id="b1b12-124">`Test-DSCConfiguration` Returnerar `True` om noden inte är kompatibelt, och `False` om den inte.</span><span class="sxs-lookup"><span data-stu-id="b1b12-124">`Test-DSCConfiguration` will return `True` if the Node is compliant, and `False` if it is not.</span></span>

```powershell
Test-DSCConfiguration
```

<span data-ttu-id="b1b12-125">Från och med PowerShell 5.0, den `-Detailed` parameter har lagts till som returnerar ett objekt med samlingar för **ResourcesInDesiredState** och **ResourcesNotInDesiredState**</span><span class="sxs-lookup"><span data-stu-id="b1b12-125">Beginning in PowerShell 5.0, the `-Detailed` parameter was added which returns an object with collections for **ResourcesInDesiredState** and **ResourcesNotInDesiredState**</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

<span data-ttu-id="b1b12-126">Från och med PowerShell 5.0 du kan testa en konfiguration utan att använda den.</span><span class="sxs-lookup"><span data-stu-id="b1b12-126">Beginning in PowerShell 5.0 you can test a Configuration without applying it.</span></span> <span data-ttu-id="b1b12-127">Den `-ReferenceConfiguration` parametern accepterar sökvägen för filsegment ”.mof” att testa noden mot.</span><span class="sxs-lookup"><span data-stu-id="b1b12-127">The `-ReferenceConfiguration` parameter accepts the path of a ".mof" file to test the Node against.</span></span> <span data-ttu-id="b1b12-128">Inte **ange** åtgärder utförs i noden.</span><span class="sxs-lookup"><span data-stu-id="b1b12-128">No **Set** actions are taken against the Node.</span></span> <span data-ttu-id="b1b12-129">Det finns lösningar för att testa en konfiguration utan att använda det i PowerShell 4.0, men de beskrivs inte här.</span><span class="sxs-lookup"><span data-stu-id="b1b12-129">In PowerShell 4.0, there are workarounds to test a Configuration without applying it, but they are not discussed here.</span></span>

## <a name="get-configuration-values"></a><span data-ttu-id="b1b12-130">Få konfigurationsvärden</span><span class="sxs-lookup"><span data-stu-id="b1b12-130">Get Configuration Values</span></span>

<span data-ttu-id="b1b12-131">Den [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet returnerar de aktuella värdena för alla resurser som är konfigurerade i konfigurationen som används.</span><span class="sxs-lookup"><span data-stu-id="b1b12-131">The [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet returns the current values for any configured resources in the currently applied Configuration.</span></span>

```powershell
Get-DSCConfiguration
```

<span data-ttu-id="b1b12-132">Utdata från vårt exempel konfigurationen skulle se ut så här om du har tillämpats.</span><span class="sxs-lookup"><span data-stu-id="b1b12-132">Output from our sample Configuration would look like this if applied successfully.</span></span>

```output
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

## <a name="get-configuration-status"></a><span data-ttu-id="b1b12-133">Hämta Konfigurationsstatus</span><span class="sxs-lookup"><span data-stu-id="b1b12-133">Get Configuration Status</span></span>

<span data-ttu-id="b1b12-134">Från och med PowerShell 5.0 den [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet: en kan du se historiken för tillämpade konfigurationer till noden.</span><span class="sxs-lookup"><span data-stu-id="b1b12-134">Beginning in PowerShell 5.0 the [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet allows you to see the history of applied Configurations to the node.</span></span> <span data-ttu-id="b1b12-135">PowerShell DSC håller reda på de senaste {{N}} konfigurationer som används i **Push** eller **hämta** läge.</span><span class="sxs-lookup"><span data-stu-id="b1b12-135">PowerShell DSC keeps track of the last {{N}} Configurations applied in **Push** or **Pull** mode.</span></span> <span data-ttu-id="b1b12-136">Detta inkluderar alla *konsekvens* kontroller som utförs av LCM.</span><span class="sxs-lookup"><span data-stu-id="b1b12-136">This includes any *consistency* checks executed by the LCM.</span></span> <span data-ttu-id="b1b12-137">Som standard `Get-DSCConfigurationStatus` visar den senaste historikpost endast.</span><span class="sxs-lookup"><span data-stu-id="b1b12-137">By default, `Get-DSCConfigurationStatus` shows you the last history entry only.</span></span>

```powershell
Get-DSCConfigurationStatus
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

<span data-ttu-id="b1b12-138">Använd den `-All` parametern för att se all Konfigurationsstatus historik.</span><span class="sxs-lookup"><span data-stu-id="b1b12-138">Use the `-All` parameter to see all Configuration Status history.</span></span>

> [!NOTE]
> <span data-ttu-id="b1b12-139">Utdata trunkeras av utrymmesskäl.</span><span class="sxs-lookup"><span data-stu-id="b1b12-139">Output is truncated for brevity.</span></span>

```powershell
Get-DSCConfigurationStatus -All
```

```output
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

## <a name="manage-configuration-documents"></a><span data-ttu-id="b1b12-140">Hantera Configuration dokument</span><span class="sxs-lookup"><span data-stu-id="b1b12-140">Manage Configuration Documents</span></span>

<span data-ttu-id="b1b12-141">LCM hanterar konfigurationen av noden genom att arbeta med **Configuration dokument**.</span><span class="sxs-lookup"><span data-stu-id="b1b12-141">The LCM manages the Configuration of the Node by working with **Configuration Documents**.</span></span> <span data-ttu-id="b1b12-142">De här MOF-filerna finns i katalogen ”C:\Windows\System32\Configuration”.</span><span class="sxs-lookup"><span data-stu-id="b1b12-142">These ".mof" files reside in the "C:\Windows\System32\Configuration" directory.</span></span>

<span data-ttu-id="b1b12-143">Från och med PowerShell 5.0 den [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) kan du ta bort de MOF-filerna för att stoppa framtida konsekvenskontroller eller ta bort en konfiguration som innehåller fel vid tillämpning.</span><span class="sxs-lookup"><span data-stu-id="b1b12-143">Beginning in PowerShell 5.0 the [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) allows you to remove the ".mof" files to stop future consistency checks or remove a Configuration that has errors when applied.</span></span> <span data-ttu-id="b1b12-144">Den `-Stage` parametern kan du ange vilken ”.mof”-fil som du vill ta bort.</span><span class="sxs-lookup"><span data-stu-id="b1b12-144">The `-Stage` parameter allows you to specify which ".mof" file you want to remove.</span></span>

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> <span data-ttu-id="b1b12-145">I PowerShell 4.0 kan du fortfarande ta bort dessa MOF-filerna direkt med hjälp av [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).</span><span class="sxs-lookup"><span data-stu-id="b1b12-145">In PowerShell 4.0, you can still remove these ".mof" files directly using [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).</span></span>

## <a name="publish-configurations"></a><span data-ttu-id="b1b12-146">Publicera konfigurationer</span><span class="sxs-lookup"><span data-stu-id="b1b12-146">Publish Configurations</span></span>

<span data-ttu-id="b1b12-147">Från och med PowerShell 5.0, den [publicera-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet har lagts till.</span><span class="sxs-lookup"><span data-stu-id="b1b12-147">Beginning in PowerShell 5.0, the [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet was added.</span></span> <span data-ttu-id="b1b12-148">Denna cmdlet kan du publicera en ”.mof”-fil till fjärrdatorer, utan att använda den.</span><span class="sxs-lookup"><span data-stu-id="b1b12-148">This cmdlet allows you to publish a ".mof" file to remote computers, without applying it.</span></span>

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a><span data-ttu-id="b1b12-149">Se även</span><span class="sxs-lookup"><span data-stu-id="b1b12-149">See also</span></span>

- [<span data-ttu-id="b1b12-150">Hämta, Test, och ange</span><span class="sxs-lookup"><span data-stu-id="b1b12-150">Get, Test, and Set</span></span>](../resources/get-test-set.md)
