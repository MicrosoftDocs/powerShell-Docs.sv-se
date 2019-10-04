---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC-skript resurs
ms.openlocfilehash: e09e86011fa7dbb2a4d7f28b5032b4328b6f6ec2
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941329"
---
# <a name="dsc-script-resource"></a><span data-ttu-id="8422e-103">DSC-skript resurs</span><span class="sxs-lookup"><span data-stu-id="8422e-103">DSC Script Resource</span></span>

> <span data-ttu-id="8422e-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5. x</span><span class="sxs-lookup"><span data-stu-id="8422e-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="8422e-105">**Skript** resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att köra Windows PowerShell-skript block på målnoden.</span><span class="sxs-lookup"><span data-stu-id="8422e-105">The **Script** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to run Windows PowerShell script blocks on target nodes.</span></span> <span data-ttu-id="8422e-106">**Skript** resursen använder **GetScript**-, **SetScript**-och **TestScript** -egenskaper som innehåller skript block som du definierar för att utföra motsvarande DSC-tillstånds åtgärder.</span><span class="sxs-lookup"><span data-stu-id="8422e-106">The **Script** resource uses **GetScript**, **SetScript**, and **TestScript** properties that contain script blocks you define to perform the corresponding DSC state operations.</span></span>

## <a name="syntax"></a><span data-ttu-id="8422e-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="8422e-107">Syntax</span></span>

```Syntax
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

> [!NOTE]
> <span data-ttu-id="8422e-108">**GetScript**-, **TestScript**-och **SetScript** -block lagras som strängar.</span><span class="sxs-lookup"><span data-stu-id="8422e-108">**GetScript**, **TestScript**, and **SetScript** blocks are stored as strings.</span></span>

## <a name="properties"></a><span data-ttu-id="8422e-109">properties</span><span class="sxs-lookup"><span data-stu-id="8422e-109">Properties</span></span>

|<span data-ttu-id="8422e-110">Egenskap</span><span class="sxs-lookup"><span data-stu-id="8422e-110">Property</span></span> |<span data-ttu-id="8422e-111">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8422e-111">Description</span></span> |
|---|---|
|<span data-ttu-id="8422e-112">GetScript</span><span class="sxs-lookup"><span data-stu-id="8422e-112">GetScript</span></span> |<span data-ttu-id="8422e-113">Ett skript block som returnerar nodens aktuella tillstånd.</span><span class="sxs-lookup"><span data-stu-id="8422e-113">A script block that returns the current state of the Node.</span></span> |
|<span data-ttu-id="8422e-114">SetScript</span><span class="sxs-lookup"><span data-stu-id="8422e-114">SetScript</span></span> |<span data-ttu-id="8422e-115">Ett skript block som DSC använder för att genomdriva efterlevnad om noden inte har önskat tillstånd.</span><span class="sxs-lookup"><span data-stu-id="8422e-115">A script block that DSC uses to enforce compliance when the Node is not in the desired state.</span></span> |
|<span data-ttu-id="8422e-116">TestScript</span><span class="sxs-lookup"><span data-stu-id="8422e-116">TestScript</span></span> |<span data-ttu-id="8422e-117">Ett skript block som avgör om noden har önskat tillstånd.</span><span class="sxs-lookup"><span data-stu-id="8422e-117">A script block that determines if the Node is in the desired state.</span></span> |
|<span data-ttu-id="8422e-118">Certifiering</span><span class="sxs-lookup"><span data-stu-id="8422e-118">Credential</span></span> |<span data-ttu-id="8422e-119">Anger de autentiseringsuppgifter som ska användas för att köra det här skriptet, om autentiseringsuppgifter krävs.</span><span class="sxs-lookup"><span data-stu-id="8422e-119">Indicates the credentials to use for running this script, if credentials are required.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="8422e-120">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="8422e-120">Common properties</span></span>

|<span data-ttu-id="8422e-121">Egenskap</span><span class="sxs-lookup"><span data-stu-id="8422e-121">Property</span></span> |<span data-ttu-id="8422e-122">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8422e-122">Description</span></span> |
|---|---|
|<span data-ttu-id="8422e-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="8422e-123">DependsOn</span></span> |<span data-ttu-id="8422e-124">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="8422e-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="8422e-125">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är `DependsOn = "[ResourceType]ResourceName"`syntaxen för att använda den här egenskapen.</span><span class="sxs-lookup"><span data-stu-id="8422e-125">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="8422e-126">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="8422e-126">PsDscRunAsCredential</span></span> |<span data-ttu-id="8422e-127">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="8422e-127">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="8422e-128">Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="8422e-128">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="8422e-129">Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="8422e-129">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

### <a name="additional-information"></a><span data-ttu-id="8422e-130">Ytterligare information</span><span class="sxs-lookup"><span data-stu-id="8422e-130">Additional information</span></span>

#### <a name="getscript"></a><span data-ttu-id="8422e-131">GetScript</span><span class="sxs-lookup"><span data-stu-id="8422e-131">GetScript</span></span>

<span data-ttu-id="8422e-132">DSC använder inte utdata från **GetScript**.</span><span class="sxs-lookup"><span data-stu-id="8422e-132">DSC does not use the output from **GetScript**.</span></span> <span data-ttu-id="8422e-133">Cmdlet: en [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) kör **GetScript** för att hämta en nods aktuella status.</span><span class="sxs-lookup"><span data-stu-id="8422e-133">The [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet executes **GetScript** to retrieve a node's current state.</span></span> <span data-ttu-id="8422e-134">Ett retur värde krävs inte från **GetScript**.</span><span class="sxs-lookup"><span data-stu-id="8422e-134">A return value is not required from **GetScript**.</span></span> <span data-ttu-id="8422e-135">Om du anger ett retur värde måste det vara en hash som innehåller en **resultat** nyckel vars värde är en sträng.</span><span class="sxs-lookup"><span data-stu-id="8422e-135">If you specify a return value, it must be a hashtable containing a **Result** key whose value is a String.</span></span>

#### <a name="testscript"></a><span data-ttu-id="8422e-136">TestScript</span><span class="sxs-lookup"><span data-stu-id="8422e-136">TestScript</span></span>

<span data-ttu-id="8422e-137">**TestScript** körs av DSC för att avgöra om **SetScript** ska köras.</span><span class="sxs-lookup"><span data-stu-id="8422e-137">**TestScript** is executed by DSC to determine if **SetScript** should be run.</span></span> <span data-ttu-id="8422e-138">Om **TestScript** returnerar `$false`kör DSC **SetScript** för att återställa noden till önskat tillstånd.</span><span class="sxs-lookup"><span data-stu-id="8422e-138">If **TestScript** returns `$false`, DSC executes **SetScript** to bring the node back to the desired state.</span></span> <span data-ttu-id="8422e-139">Det måste returnera ett booleskt värde.</span><span class="sxs-lookup"><span data-stu-id="8422e-139">It must return a boolean value.</span></span> <span data-ttu-id="8422e-140">Resultatet av `$true` indikerar att noden är kompatibel och att **SetScript** inte ska köras.</span><span class="sxs-lookup"><span data-stu-id="8422e-140">A result of `$true` indicates that the node is compliant and **SetScript** should not executed.</span></span>

<span data-ttu-id="8422e-141">Cmdleten [test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) kör **TestScript** för att hämta nodernas kompatibilitet med **skript** resurserna.</span><span class="sxs-lookup"><span data-stu-id="8422e-141">The [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet, executes **TestScript** to retrieve the nodes compliance with the **Script** resources.</span></span>
<span data-ttu-id="8422e-142">I det här fallet körs dock inte **SetScript** , oavsett vilket **TestScript** -block som returneras.</span><span class="sxs-lookup"><span data-stu-id="8422e-142">However, in this case, **SetScript** does not run, no matter what **TestScript** block returns.</span></span>

> [!NOTE]
> <span data-ttu-id="8422e-143">Alla utdata från din **TestScript** är en del av dess retur värde.</span><span class="sxs-lookup"><span data-stu-id="8422e-143">All output from your **TestScript** is part of its return value.</span></span> <span data-ttu-id="8422e-144">PowerShell tolkar ignorerade utdata som icke-noll, vilket innebär att din **TestScript** returneras `$true` oavsett nodens tillstånd.</span><span class="sxs-lookup"><span data-stu-id="8422e-144">PowerShell interprets unsuppressed output as non-zero, which means that your **TestScript** will return `$true` regardless of your node's state.</span></span> <span data-ttu-id="8422e-145">Detta resulterar i oförutsägbara resultat, falska positiva identifieringar och orsakar problem under fel sökningen.</span><span class="sxs-lookup"><span data-stu-id="8422e-145">This results in unpredictable results, false positives, and causes difficulty during troubleshooting.</span></span>

#### <a name="setscript"></a><span data-ttu-id="8422e-146">SetScript</span><span class="sxs-lookup"><span data-stu-id="8422e-146">SetScript</span></span>

<span data-ttu-id="8422e-147">**SetScript** ändrar noden för att framtvinga det önskade läget.</span><span class="sxs-lookup"><span data-stu-id="8422e-147">**SetScript** modifies the node to enforce the desired state.</span></span> <span data-ttu-id="8422e-148">Den anropas av DSC om **TestScript** -skript blocket `$false`returnerar.</span><span class="sxs-lookup"><span data-stu-id="8422e-148">It is called by DSC if the **TestScript** script block returns `$false`.</span></span> <span data-ttu-id="8422e-149">**SetScript** får inte ha något retur värde.</span><span class="sxs-lookup"><span data-stu-id="8422e-149">The **SetScript** should have no return value.</span></span>

## <a name="examples"></a><span data-ttu-id="8422e-150">Exempel</span><span class="sxs-lookup"><span data-stu-id="8422e-150">Examples</span></span>

### <a name="example-1-write-sample-text-using-a-script-resource"></a><span data-ttu-id="8422e-151">Exempel 1: Skriv exempel text med hjälp av en skript resurs</span><span class="sxs-lookup"><span data-stu-id="8422e-151">Example 1: Write sample text using a Script resource</span></span>

<span data-ttu-id="8422e-152">`C:\TempFolder\TestFile.txt` I det här exemplet testas om det finns på varje nod.</span><span class="sxs-lookup"><span data-stu-id="8422e-152">This example tests for the existence of `C:\TempFolder\TestFile.txt` on each node.</span></span> <span data-ttu-id="8422e-153">Om den inte finns skapas den med hjälp `SetScript`av.</span><span class="sxs-lookup"><span data-stu-id="8422e-153">If it does not exist, it creates it using the `SetScript`.</span></span> <span data-ttu-id="8422e-154">`GetScript` Returnerar filens innehåll och dess retur värde används inte.</span><span class="sxs-lookup"><span data-stu-id="8422e-154">The `GetScript` returns the contents of the file, and its return value is not used.</span></span>

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

### <a name="example-2-compare-version-information-using-a-script-resource"></a><span data-ttu-id="8422e-155">Exempel 2: Jämför versions information med hjälp av en skript resurs</span><span class="sxs-lookup"><span data-stu-id="8422e-155">Example 2: Compare version information using a Script resource</span></span>

<span data-ttu-id="8422e-156">I det här exemplet hämtas den *kompatibla* versions informationen från en textfil på den redigerings datorn och lagras i `$version` variabeln.</span><span class="sxs-lookup"><span data-stu-id="8422e-156">This example retrieves the *compliant* version information from a text file on the authoring computer and stores it in the `$version` variable.</span></span> <span data-ttu-id="8422e-157">När du genererar nodens MOF-fil ersätter `$using:version` DSC variablerna i varje skript block med värdet `$version` för variabeln.</span><span class="sxs-lookup"><span data-stu-id="8422e-157">When generating the node's MOF file, DSC replaces the `$using:version` variables in each script block with the value of the `$version` variable.</span></span>
<span data-ttu-id="8422e-158">Under körningen lagras den *kompatibla* versionen i en textfil på varje nod och jämförs och uppdateras vid efterföljande körningar.</span><span class="sxs-lookup"><span data-stu-id="8422e-158">During execution, the *compliant* version is stored in a text file on each Node and compared and updated on subsequent executions.</span></span>

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