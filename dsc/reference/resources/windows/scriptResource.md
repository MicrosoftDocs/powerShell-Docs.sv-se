---
ms.date: 08/24/2018
keywords: DSC, powershell, konfiguration, installation
title: DSC-skriptresurs
ms.openlocfilehash: 4eee5625add4d96ade7ababf7f534f597a26712d
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984297"
---
# <a name="dsc-script-resource"></a><span data-ttu-id="2dc16-103">DSC-skriptresurs</span><span class="sxs-lookup"><span data-stu-id="2dc16-103">DSC Script Resource</span></span>

> <span data-ttu-id="2dc16-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="2dc16-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="2dc16-105">Den **skriptet** resursen i Windows PowerShell Desired State Configuration (DSC) är en mekanism för att köra Windows PowerShell-skriptblock på målnoder.</span><span class="sxs-lookup"><span data-stu-id="2dc16-105">The **Script** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to run Windows PowerShell script blocks on target nodes.</span></span> <span data-ttu-id="2dc16-106">Den **skriptet** resource använder `GetScript`, `SetScript`, och `TestScript` egenskaper som innehåller skriptblock som du definierar för att utföra motsvarande DSC tillstånd åtgärder.</span><span class="sxs-lookup"><span data-stu-id="2dc16-106">The **Script** resource uses `GetScript`, `SetScript`, and `TestScript` properties that contain script blocks you define to perform the corresponding DSC state operations.</span></span>

## <a name="syntax"></a><span data-ttu-id="2dc16-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="2dc16-107">Syntax</span></span>

```
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> <span data-ttu-id="2dc16-108">Den `GetScript`, `TestScript`, och `SetScript` block lagras som strängar.</span><span class="sxs-lookup"><span data-stu-id="2dc16-108">The `GetScript`, `TestScript`, and `SetScript` blocks are stored as strings.</span></span>

## <a name="properties"></a><span data-ttu-id="2dc16-109">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="2dc16-109">Properties</span></span>

|<span data-ttu-id="2dc16-110">Egenskap</span><span class="sxs-lookup"><span data-stu-id="2dc16-110">Property</span></span>|<span data-ttu-id="2dc16-111">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2dc16-111">Description</span></span>|
|--------|-----------|
|<span data-ttu-id="2dc16-112">GetScript</span><span class="sxs-lookup"><span data-stu-id="2dc16-112">GetScript</span></span>|<span data-ttu-id="2dc16-113">Ett skriptblock som returnerar det aktuella tillståndet för noden.</span><span class="sxs-lookup"><span data-stu-id="2dc16-113">A script block that returns the current state of the Node.</span></span>|
|<span data-ttu-id="2dc16-114">SetScript</span><span class="sxs-lookup"><span data-stu-id="2dc16-114">SetScript</span></span>|<span data-ttu-id="2dc16-115">Ett skriptblock som DSC använder för att tvinga kompatibilitet när noden inte är i önskat läge.</span><span class="sxs-lookup"><span data-stu-id="2dc16-115">A script block that DSC uses to enforce compliance when the Node is not in the desired state.</span></span>|
|<span data-ttu-id="2dc16-116">TestScript</span><span class="sxs-lookup"><span data-stu-id="2dc16-116">TestScript</span></span>|<span data-ttu-id="2dc16-117">Ett skriptblock som avgör om noden är statusen som önskas.</span><span class="sxs-lookup"><span data-stu-id="2dc16-117">A script block that determines if the Node is in the desired state.</span></span>|
|<span data-ttu-id="2dc16-118">Autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="2dc16-118">Credential</span></span>| <span data-ttu-id="2dc16-119">Anger autentiseringsuppgifterna som används för att köra det här skriptet om autentiseringsuppgifter krävs.</span><span class="sxs-lookup"><span data-stu-id="2dc16-119">Indicates the credentials to use for running this script, if credentials are required.</span></span>|
|<span data-ttu-id="2dc16-120">DependsOn</span><span class="sxs-lookup"><span data-stu-id="2dc16-120">DependsOn</span></span>| <span data-ttu-id="2dc16-121">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="2dc16-121">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="2dc16-122">Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är **ResourceName** och är av typen **ResourceType**, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="2dc16-122">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>

### <a name="getscript"></a><span data-ttu-id="2dc16-123">GetScript</span><span class="sxs-lookup"><span data-stu-id="2dc16-123">GetScript</span></span>

<span data-ttu-id="2dc16-124">DSC inte använder utdata från `GetScript`.</span><span class="sxs-lookup"><span data-stu-id="2dc16-124">DSC does not use the output from `GetScript`.</span></span> <span data-ttu-id="2dc16-125">Den [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet körs den `GetScript` att hämta aktuell status för en nod.</span><span class="sxs-lookup"><span data-stu-id="2dc16-125">The [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet executes the `GetScript` to retrieve a node's current state.</span></span> <span data-ttu-id="2dc16-126">Det krävs inte ett returvärde från `GetScript`.</span><span class="sxs-lookup"><span data-stu-id="2dc16-126">A return value is not required from `GetScript`.</span></span> <span data-ttu-id="2dc16-127">Om du anger ett returvärde, det måste vara en `hashtable` som innehåller en **resultatet** nyckel vars värde är en `String`.</span><span class="sxs-lookup"><span data-stu-id="2dc16-127">If you specify a return value, it must be a `hashtable` containing a **Result** key whose value is a `String`.</span></span>

### <a name="testscript"></a><span data-ttu-id="2dc16-128">TestScript</span><span class="sxs-lookup"><span data-stu-id="2dc16-128">TestScript</span></span>

<span data-ttu-id="2dc16-129">Den `TestScript` körs av DSC för att avgöra om den `SetScript` ska köras.</span><span class="sxs-lookup"><span data-stu-id="2dc16-129">The `TestScript` is executed by DSC to determine if the `SetScript` should be run.</span></span> <span data-ttu-id="2dc16-130">Om den `TestScript` returnerar `$false`, DSC körs den `SetScript` att ge önskat tillstånd för noden.</span><span class="sxs-lookup"><span data-stu-id="2dc16-130">If the `TestScript` returns `$false`, DSC executes the `SetScript` to bring the node back to the desired state.</span></span> <span data-ttu-id="2dc16-131">Det måste returnera ett `boolean` värde.</span><span class="sxs-lookup"><span data-stu-id="2dc16-131">It must return a `boolean` value.</span></span> <span data-ttu-id="2dc16-132">Ett resultat av `$true` anger att noden är kompatibel och `SetScript` bör utförs inte.</span><span class="sxs-lookup"><span data-stu-id="2dc16-132">A result of `$true` indicates that the node is compliant and `SetScript` should not executed.</span></span>

<span data-ttu-id="2dc16-133">Den [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet, körs den `TestScript` att hämta noder kompatibiliteten med den **skriptet** resurser.</span><span class="sxs-lookup"><span data-stu-id="2dc16-133">The [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet, executes the `TestScript` to retrieve the nodes compliance with the  **Script** resources.</span></span> <span data-ttu-id="2dc16-134">Men i det här fallet den `SetScript` inte körs, oavsett vad de `TestScript` blockera returnerar.</span><span class="sxs-lookup"><span data-stu-id="2dc16-134">However, in this case, the `SetScript` does not run, no matter what the `TestScript` block returns.</span></span>

> [!NOTE]
> <span data-ttu-id="2dc16-135">Alla utdata från din `TestScript` är en del av dess returvärde.</span><span class="sxs-lookup"><span data-stu-id="2dc16-135">All output from your `TestScript` is part of its return value.</span></span> <span data-ttu-id="2dc16-136">PowerShell tolkar unsuppressed utdata som inte är noll, vilket innebär att din `TestScript` returnerar `$true` oavsett dina nodens tillstånd.</span><span class="sxs-lookup"><span data-stu-id="2dc16-136">PowerShell interprets unsuppressed output as non-zero, which means that your `TestScript` will return `$true` regardless of your node's state.</span></span>
> <span data-ttu-id="2dc16-137">Detta leder till oväntade resultat, falska positiva identifieringar, och orsakar problem vid felsökning.</span><span class="sxs-lookup"><span data-stu-id="2dc16-137">This results in unpredictable results, false positives, and causes difficulty during troubleshooting.</span></span>

### <a name="setscript"></a><span data-ttu-id="2dc16-138">SetScript</span><span class="sxs-lookup"><span data-stu-id="2dc16-138">SetScript</span></span>

<span data-ttu-id="2dc16-139">Den `SetScript` ändrar noden om du vill framtvinga önskat läge.</span><span class="sxs-lookup"><span data-stu-id="2dc16-139">The `SetScript` modifies the node to enforce the desired state.</span></span> <span data-ttu-id="2dc16-140">Den kommer att anropas av DSC om den `TestScript` skript block returnerar `$false`.</span><span class="sxs-lookup"><span data-stu-id="2dc16-140">It is called by DSC if the `TestScript` script block returns `$false`.</span></span> <span data-ttu-id="2dc16-141">Den `SetScript` bör har inget returvärde.</span><span class="sxs-lookup"><span data-stu-id="2dc16-141">The `SetScript` should have no return value.</span></span>

## <a name="examples"></a><span data-ttu-id="2dc16-142">Exempel</span><span class="sxs-lookup"><span data-stu-id="2dc16-142">Examples</span></span>

### <a name="example-1-write-sample-text-using-a-script-resource"></a><span data-ttu-id="2dc16-143">Exempel 1: Skriva exempeltext med hjälp av en skriptresurs</span><span class="sxs-lookup"><span data-stu-id="2dc16-143">Example 1: Write sample text using a Script resource</span></span>

<span data-ttu-id="2dc16-144">Det här exemplet testar förekomsten av `C:\TempFolder\TestFile.txt` på varje nod.</span><span class="sxs-lookup"><span data-stu-id="2dc16-144">This example tests for the existence of `C:\TempFolder\TestFile.txt` on each node.</span></span> <span data-ttu-id="2dc16-145">Om den inte finns skapas den med hjälp av den `SetScript`.</span><span class="sxs-lookup"><span data-stu-id="2dc16-145">If it does not exist, it creates it using the `SetScript`.</span></span> <span data-ttu-id="2dc16-146">Den `GetScript` returnerar innehållet i filen och dess returnerade värdet inte används.</span><span class="sxs-lookup"><span data-stu-id="2dc16-146">The `GetScript` returns the contents of the file, and its return value is not used.</span></span>

```powershell
Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script ScriptExample
        {
            SetScript = {
                $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
                $sw.WriteLine("Some sample string")
                $sw.Close()
            }
            TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
            GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }
        }
    }
}
```

### <a name="example-2-compare-version-information-using-a-script-resource"></a><span data-ttu-id="2dc16-147">Exempel 2: Jämför versionsinformation med hjälp av en skriptresurs</span><span class="sxs-lookup"><span data-stu-id="2dc16-147">Example 2: Compare version information using a Script resource</span></span>

<span data-ttu-id="2dc16-148">Det här exemplet hämtar den *kompatibla* versionsinformation från en textfil på den redigering datorn och lagrar den i den `$version` variabeln.</span><span class="sxs-lookup"><span data-stu-id="2dc16-148">This example retrieves the *compliant* version information from a text file on the authoring computer and stores it in the `$version` variable.</span></span> <span data-ttu-id="2dc16-149">När du genererar nodens MOF-filen, DSC ersätter den `$using:version` variabler i varje skript blockera med värdet för den `$version` variabeln.</span><span class="sxs-lookup"><span data-stu-id="2dc16-149">When generating the node's MOF file, DSC replaces the `$using:version` variables in each script block with the value of the `$version` variable.</span></span> <span data-ttu-id="2dc16-150">Under körningen på *kompatibla* version lagras i en textfil på varje nod och jämfört med och uppdateras vid efterföljande körningar.</span><span class="sxs-lookup"><span data-stu-id="2dc16-150">During execution, the *compliant* version is stored in a text file on each Node and compared and updated on subsequent executions.</span></span>

```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script UpdateConfigurationVersion
        {
            GetScript = {
                $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
                return @{ 'Result' = "$currentVersion" }
            }
            TestScript = {
                # Create and invoke a scriptblock using the $GetScript automatic variable, which contains a string representation of the GetScript.
                $state = [scriptblock]::Create($GetScript).Invoke()

                if( $state['Result'] -eq $using:version )
                {
                    Write-Verbose -Message ('{0} -eq {1}' -f $state['Result'],$using:version)
                    return $true
                }
                Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
                return $false
            }
            SetScript = {
                $using:version | Set-Content -Path (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
            }
        }
    }
}
```
