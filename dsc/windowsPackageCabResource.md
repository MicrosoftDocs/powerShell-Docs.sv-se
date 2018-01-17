---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC WindowsPackageCab resurs
ms.openlocfilehash: 1d7c8d9bf45d2eda8734daa8877315d219662c75
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-windowspackagecab-resource"></a><span data-ttu-id="84c8c-103">DSC WindowsPackageCab resurs</span><span class="sxs-lookup"><span data-stu-id="84c8c-103">DSC WindowsPackageCab Resource</span></span>

> <span data-ttu-id="84c8c-104">Gäller för: Windows PowerShell 5.1 och senare</span><span class="sxs-lookup"><span data-stu-id="84c8c-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="84c8c-105">Den **WindowsPackageCab** resurs i Windows PowerShell önskad tillstånd Configuration (DSC) ger dig möjlighet att installera eller avinstallera Windows CAB-paket på målnoden.</span><span class="sxs-lookup"><span data-stu-id="84c8c-105">The **WindowsPackageCab** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Windows cabinet (.cab) packages on a target node.</span></span>

<span data-ttu-id="84c8c-106">Målnoden måste ha installerat PowerShell DISM-modulen.</span><span class="sxs-lookup"><span data-stu-id="84c8c-106">The target node must have the DISM PowerShell module installed.</span></span> <span data-ttu-id="84c8c-107">Mer information finns i [Använd DISM i Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span><span class="sxs-lookup"><span data-stu-id="84c8c-107">For information, see [Use DISM in Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span></span> 


## <a name="syntax"></a><span data-ttu-id="84c8c-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="84c8c-108">Syntax</span></span>

```
{
    Name = [string]
    Ensure = [string] { Absent | Present }
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="84c8c-109">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="84c8c-109">Properties</span></span>

|  <span data-ttu-id="84c8c-110">Egenskap</span><span class="sxs-lookup"><span data-stu-id="84c8c-110">Property</span></span>  |  <span data-ttu-id="84c8c-111">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="84c8c-111">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="84c8c-112">Namn</span><span class="sxs-lookup"><span data-stu-id="84c8c-112">Name</span></span>| <span data-ttu-id="84c8c-113">Anger namnet på paketet för du vill se till att ett visst tillstånd.</span><span class="sxs-lookup"><span data-stu-id="84c8c-113">Indicates the name of the package for you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="84c8c-114">Se till att</span><span class="sxs-lookup"><span data-stu-id="84c8c-114">Ensure</span></span>| <span data-ttu-id="84c8c-115">Anger om paketet har installerats.</span><span class="sxs-lookup"><span data-stu-id="84c8c-115">Indicates if the package is installed.</span></span> <span data-ttu-id="84c8c-116">Ange den här egenskapen till ”saknas” för att se till att paketet inte är installerat (eller avinstallera paketet om det är installerat).</span><span class="sxs-lookup"><span data-stu-id="84c8c-116">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="84c8c-117">Ange att ”finns” (standardvärdet) för att säkerställa att paketet har installerats.</span><span class="sxs-lookup"><span data-stu-id="84c8c-117">Set it to "Present" (the default value) to ensure the package is installed.</span></span>|
| <span data-ttu-id="84c8c-118">Sökväg</span><span class="sxs-lookup"><span data-stu-id="84c8c-118">Path</span></span>| <span data-ttu-id="84c8c-119">Anger sökvägen där paketet finns.</span><span class="sxs-lookup"><span data-stu-id="84c8c-119">Indicates the path where the package resides.</span></span>| 
| <span data-ttu-id="84c8c-120">LogPath</span><span class="sxs-lookup"><span data-stu-id="84c8c-120">LogPath</span></span>| <span data-ttu-id="84c8c-121">Anger den fullständiga sökvägen där du vill att providern ska spara en loggfil för att installera eller avinstallera paketet.</span><span class="sxs-lookup"><span data-stu-id="84c8c-121">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>| 
| <span data-ttu-id="84c8c-122">dependsOn</span><span class="sxs-lookup"><span data-stu-id="84c8c-122">DependsOn</span></span> | <span data-ttu-id="84c8c-123">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="84c8c-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="84c8c-124">Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis **ResourceName** och dess typ är **ResourceType**, syntaxen för den här egenskapen är ”DependsOn =” [ResourceType] ResourceName ”''.</span><span class="sxs-lookup"><span data-stu-id="84c8c-124">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>| 

## <a name="example"></a><span data-ttu-id="84c8c-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="84c8c-125">Example</span></span>

<span data-ttu-id="84c8c-126">Följande exempelkonfiguration tar indataparametrar och säkerställer att CAB-filen som anges av den `$Name` parameter är installerad.</span><span class="sxs-lookup"><span data-stu-id="84c8c-126">The following example configuration takes input parameters, and ensures that the .cab file specified by the `$Name` parameter is installed.</span></span>

```powershell
Configuration Sample_WindowsPackageCab
{
    param
    (
        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $Name,

        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $SourcePath,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $LogPath
    )

    Import-DscResource -ModuleName 'PSDscResources'

    WindowsPackageCab WindowsPackageCab1
    {
        Name = $Name
        Ensure = 'Present'
        SourcePath = $SourcePath
        LogPath = $LogPath
    }
}
```

