---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Resursen DSC-skript
ms.openlocfilehash: d65a89ceba0b641ccb0ac3dfcc6d5ec1a48dc92a
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/15/2018
---
# <a name="dsc-script-resource"></a><span data-ttu-id="a8b85-103">Resursen DSC-skript</span><span class="sxs-lookup"><span data-stu-id="a8b85-103">DSC Script Resource</span></span>

 
> <span data-ttu-id="a8b85-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a8b85-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="a8b85-105">Den **skriptet** resurs i Windows PowerShell önskad tillstånd Configuration (DSC) tillhandahåller en mekanism för att köra Windows PowerShell-skriptblock på målnoder.</span><span class="sxs-lookup"><span data-stu-id="a8b85-105">The **Script** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to run Windows PowerShell script blocks on target nodes.</span></span> <span data-ttu-id="a8b85-106">Den `Script` resursen har `GetScript`, `SetScript`, och `TestScript` egenskaper.</span><span class="sxs-lookup"><span data-stu-id="a8b85-106">The `Script` resource has `GetScript`, `SetScript`, and `TestScript` properties.</span></span> <span data-ttu-id="a8b85-107">De här egenskaperna ska anges till skriptblock som ska köras på varje målnoden.</span><span class="sxs-lookup"><span data-stu-id="a8b85-107">These properties should be set to script blocks that will run on each target node.</span></span> 

<span data-ttu-id="a8b85-108">Den `GetScript` skriptblock ska returnera en hash-tabell som representerar tillståndet för den aktuella noden.</span><span class="sxs-lookup"><span data-stu-id="a8b85-108">The `GetScript` script block should return a hashtable representing the state of the current node.</span></span> <span data-ttu-id="a8b85-109">Hash-tabellen får bara innehålla en nyckel `Result` och värdet måste vara av typen `String`.</span><span class="sxs-lookup"><span data-stu-id="a8b85-109">The hashtable must only contain one key `Result` and the value must be of type `String`.</span></span> <span data-ttu-id="a8b85-110">Det krävs inte returnerar något.</span><span class="sxs-lookup"><span data-stu-id="a8b85-110">It is not required to return anything.</span></span> <span data-ttu-id="a8b85-111">DSC göra inte något med utdata från den här skriptblock.</span><span class="sxs-lookup"><span data-stu-id="a8b85-111">DSC doesn't do anything with the output of this script block.</span></span>

<span data-ttu-id="a8b85-112">Den `TestScript` skriptblock bestämmer om den aktuella noden ska ändras.</span><span class="sxs-lookup"><span data-stu-id="a8b85-112">The `TestScript` script block should determine if the current node needs to be modified.</span></span> <span data-ttu-id="a8b85-113">Det ska returnera `$true` om noden är uppdaterad.</span><span class="sxs-lookup"><span data-stu-id="a8b85-113">It should return `$true` if the node is up-to-date.</span></span> <span data-ttu-id="a8b85-114">Det ska returnera `$false` om nodens konfiguration är inaktuell och bör uppdateras av den `SetScript` skriptblock.</span><span class="sxs-lookup"><span data-stu-id="a8b85-114">It should return `$false` if the node's configuration is out-of-date and should be updated by the `SetScript` script block.</span></span> <span data-ttu-id="a8b85-115">Den `TestScript` skriptblock anropas av DSC.</span><span class="sxs-lookup"><span data-stu-id="a8b85-115">The `TestScript` script block is called by DSC.</span></span>

<span data-ttu-id="a8b85-116">Den `SetScript` skriptblock bör ändra noden.</span><span class="sxs-lookup"><span data-stu-id="a8b85-116">The `SetScript` script block should modify the node.</span></span> <span data-ttu-id="a8b85-117">Den anropas av DSC om den `TestScript` blockera returnera `$false`.</span><span class="sxs-lookup"><span data-stu-id="a8b85-117">It is called by DSC if the `TestScript` block return `$false`.</span></span>

<span data-ttu-id="a8b85-118">Om du behöver använda variabler i konfigurationen skriptet i den `GetScript`, `TestScript`, eller `SetScript` skriptblock som använder den `$using:` omfång (se nedan ett exempel).</span><span class="sxs-lookup"><span data-stu-id="a8b85-118">If you need to use variables from your configuration script in the `GetScript`, `TestScript`, or `SetScript` script blocks, use the `$using:` scope (see below for an example).</span></span>


## <a name="syntax"></a><span data-ttu-id="a8b85-119">Syntax</span><span class="sxs-lookup"><span data-stu-id="a8b85-119">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="a8b85-120">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="a8b85-120">Properties</span></span>

|  <span data-ttu-id="a8b85-121">Egenskap</span><span class="sxs-lookup"><span data-stu-id="a8b85-121">Property</span></span>  |  <span data-ttu-id="a8b85-122">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a8b85-122">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="a8b85-123">GetScript</span><span class="sxs-lookup"><span data-stu-id="a8b85-123">GetScript</span></span>| <span data-ttu-id="a8b85-124">Ger ett block med Windows PowerShell-skript som körs när du anropar den [Get-DscConfiguration](https://technet.microsoft.com/library/dn407379.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a8b85-124">Provides a block of Windows PowerShell script that runs when you invoke the [Get-DscConfiguration](https://technet.microsoft.com/library/dn407379.aspx) cmdlet.</span></span> <span data-ttu-id="a8b85-125">Det här blocket måste returnera en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="a8b85-125">This block must return a hashtable.</span></span> <span data-ttu-id="a8b85-126">Hash-tabellen får bara innehålla en nyckel **resultatet** och värdet måste vara av typen **sträng**.</span><span class="sxs-lookup"><span data-stu-id="a8b85-126">The hashtable must only contain one key **Result** and the value must be of type **String**.</span></span>| 
| <span data-ttu-id="a8b85-127">SetScript</span><span class="sxs-lookup"><span data-stu-id="a8b85-127">SetScript</span></span>| <span data-ttu-id="a8b85-128">Innehåller ett block med Windows PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="a8b85-128">Provides a block of Windows PowerShell script.</span></span> <span data-ttu-id="a8b85-129">När du anropar den [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet, den **TestScript** block körs första.</span><span class="sxs-lookup"><span data-stu-id="a8b85-129">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet, the **TestScript** block runs first.</span></span> <span data-ttu-id="a8b85-130">Om den **TestScript** blockera returnerar **$false**, **SetScript** block körs.</span><span class="sxs-lookup"><span data-stu-id="a8b85-130">If the **TestScript** block returns **$false**, the **SetScript** block will run.</span></span> <span data-ttu-id="a8b85-131">Om den **TestScript** blockera returnerar **$true**, **SetScript** block körs inte.</span><span class="sxs-lookup"><span data-stu-id="a8b85-131">If the **TestScript** block returns **$true**, the **SetScript** block will not run.</span></span>| 
| <span data-ttu-id="a8b85-132">TestScript</span><span class="sxs-lookup"><span data-stu-id="a8b85-132">TestScript</span></span>| <span data-ttu-id="a8b85-133">Innehåller ett block med Windows PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="a8b85-133">Provides a block of Windows PowerShell script.</span></span> <span data-ttu-id="a8b85-134">När du anropar den [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet, det här blocket körs.</span><span class="sxs-lookup"><span data-stu-id="a8b85-134">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet, this block runs.</span></span> <span data-ttu-id="a8b85-135">Om den returnerar **$false**, SetScript blocket körs.</span><span class="sxs-lookup"><span data-stu-id="a8b85-135">If it returns **$false**, the SetScript block will run.</span></span> <span data-ttu-id="a8b85-136">Om den returnerar **$true**, SetScript som block kommer inte att köra.</span><span class="sxs-lookup"><span data-stu-id="a8b85-136">If it returns **$true**, the SetScript block will not run.</span></span> <span data-ttu-id="a8b85-137">Den **TestScript** block körs även när du anropar den [Test DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a8b85-137">The **TestScript** block also runs when you invoke the [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet.</span></span> <span data-ttu-id="a8b85-138">Men i det här fallet den **SetScript** block inte körs, oavsett vilket värde som TestScript blockera returnerar.</span><span class="sxs-lookup"><span data-stu-id="a8b85-138">However, in this case, the **SetScript** block will not run, no matter what value the TestScript block returns.</span></span> <span data-ttu-id="a8b85-139">Den **TestScript** block måste returnera True om den faktiska konfigurationen matchar aktuella önskad tillståndskonfiguration och FALSKT om den inte matchar.</span><span class="sxs-lookup"><span data-stu-id="a8b85-139">The **TestScript** block must return True if the actual configuration matches the current desired state configuration, and False if it does not match.</span></span> <span data-ttu-id="a8b85-140">(Den aktuella tillståndskonfigurationen är den senaste konfigurationen trätt i kraft på den nod som använder DSC.)</span><span class="sxs-lookup"><span data-stu-id="a8b85-140">(The current desired state configuration is the last configuration enacted on the node that is using DSC.)</span></span>| 
| <span data-ttu-id="a8b85-141">autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="a8b85-141">Credential</span></span>| <span data-ttu-id="a8b85-142">Anger autentiseringsuppgifter som ska användas för att köra detta skript om autentiseringsuppgifter krävs.</span><span class="sxs-lookup"><span data-stu-id="a8b85-142">Indicates the credentials to use for running this script, if credentials are required.</span></span>| 
| <span data-ttu-id="a8b85-143">dependsOn</span><span class="sxs-lookup"><span data-stu-id="a8b85-143">DependsOn</span></span>| <span data-ttu-id="a8b85-144">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="a8b85-144">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a8b85-145">Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis **ResourceName** och dess typ är **ResourceType**, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="a8b85-145">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>

## <a name="example-1"></a><span data-ttu-id="a8b85-146">Exempel 1</span><span class="sxs-lookup"><span data-stu-id="a8b85-146">Example 1</span></span>
```powershell
Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script ScriptExample
    {
        SetScript = 
        { 
            $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
            $sw.WriteLine("Some sample string")
            $sw.Close()
        }
        TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
        GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }          
    }
}
```

## <a name="example-2"></a><span data-ttu-id="a8b85-147">Exempel 2</span><span class="sxs-lookup"><span data-stu-id="a8b85-147">Example 2</span></span>
```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script UpdateConfigurationVersion
    {
        GetScript = { 
            $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
            return @{ 'Result' = "$currentVersion" }
        }          
        TestScript = { 
            $state = $GetScript
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
```

<span data-ttu-id="a8b85-148">Den här resursen skriver konfigurationens version till en textfil.</span><span class="sxs-lookup"><span data-stu-id="a8b85-148">This resource is writing the configuration's version to a text file.</span></span> <span data-ttu-id="a8b85-149">Den här versionen finns på klientdatorn, men inte på någon av noderna, så att den har ska skickas till var och en av de `Script` resursens skriptblock med PowerShells `using` omfång.</span><span class="sxs-lookup"><span data-stu-id="a8b85-149">This version is available on the client computer, but isn't on any of the nodes, so it has to be passed to each of the `Script` resource's script blocks with PowerShell's `using` scope.</span></span> <span data-ttu-id="a8b85-150">När genererar nodens MOF-fil, värdet för den `$version` variabeln läses från en textfil på klientdatorn.</span><span class="sxs-lookup"><span data-stu-id="a8b85-150">When generating the node's MOF file, the value of the `$version` variable is read from a text file on the client computer.</span></span> <span data-ttu-id="a8b85-151">DSC-ersätter den `$using:version` variabler i varje skript blockera med värdet för den `$version` variabeln.</span><span class="sxs-lookup"><span data-stu-id="a8b85-151">DSC replaces the `$using:version` variables in each script block with the value of the `$version` variable.</span></span>

