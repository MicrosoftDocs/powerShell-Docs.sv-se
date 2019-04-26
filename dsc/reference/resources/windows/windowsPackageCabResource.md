---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC WindowsPackageCab-resurs
ms.openlocfilehash: 035944e7ca5c7469250c48a19b79f2f2d5d38e9a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076947"
---
# <a name="dsc-windowspackagecab-resource"></a><span data-ttu-id="f1327-103">DSC WindowsPackageCab-resurs</span><span class="sxs-lookup"><span data-stu-id="f1327-103">DSC WindowsPackageCab Resource</span></span>

> <span data-ttu-id="f1327-104">Gäller för: Windows PowerShell 5.1 och senare</span><span class="sxs-lookup"><span data-stu-id="f1327-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="f1327-105">Den **WindowsPackageCab** resursen i Windows PowerShell Desired State Configuration (DSC) är en mekanism för att installera eller avinstallera Windows CAB-paket på målnoden.</span><span class="sxs-lookup"><span data-stu-id="f1327-105">The **WindowsPackageCab** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Windows cabinet (.cab) packages on a target node.</span></span>

<span data-ttu-id="f1327-106">Målnoden måste ha installerat DISM PowerShell-modulen.</span><span class="sxs-lookup"><span data-stu-id="f1327-106">The target node must have the DISM PowerShell module installed.</span></span> <span data-ttu-id="f1327-107">Mer information finns i [Använd DISM i Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span><span class="sxs-lookup"><span data-stu-id="f1327-107">For information, see [Use DISM in Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span></span>


## <a name="syntax"></a><span data-ttu-id="f1327-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="f1327-108">Syntax</span></span>

```
{
    Name = [string]
    Ensure = [string] { Absent | Present }
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="f1327-109">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="f1327-109">Properties</span></span>

|  <span data-ttu-id="f1327-110">Egenskap</span><span class="sxs-lookup"><span data-stu-id="f1327-110">Property</span></span>  |  <span data-ttu-id="f1327-111">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f1327-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="f1327-112">Namn</span><span class="sxs-lookup"><span data-stu-id="f1327-112">Name</span></span>| <span data-ttu-id="f1327-113">Anger namnet på paketet för du vill se till att ett visst tillstånd.</span><span class="sxs-lookup"><span data-stu-id="f1327-113">Indicates the name of the package for you want to ensure a specific state.</span></span>|
| <span data-ttu-id="f1327-114">Se till att</span><span class="sxs-lookup"><span data-stu-id="f1327-114">Ensure</span></span>| <span data-ttu-id="f1327-115">Anger om paketet har installerats.</span><span class="sxs-lookup"><span data-stu-id="f1327-115">Indicates if the package is installed.</span></span> <span data-ttu-id="f1327-116">Ange den här egenskapen till ”inte” för att kontrollera att paketet inte har installerats (eller avinstallera paketet om det är installerat).</span><span class="sxs-lookup"><span data-stu-id="f1327-116">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="f1327-117">Ange den till ”Visa” (standardvärdet) för att säkerställa att paketet har installerats.</span><span class="sxs-lookup"><span data-stu-id="f1327-117">Set it to "Present" (the default value) to ensure the package is installed.</span></span>|
| <span data-ttu-id="f1327-118">Sökväg</span><span class="sxs-lookup"><span data-stu-id="f1327-118">Path</span></span>| <span data-ttu-id="f1327-119">Anger sökvägen där paketet finns.</span><span class="sxs-lookup"><span data-stu-id="f1327-119">Indicates the path where the package resides.</span></span>|
| <span data-ttu-id="f1327-120">LogPath</span><span class="sxs-lookup"><span data-stu-id="f1327-120">LogPath</span></span>| <span data-ttu-id="f1327-121">Anger den fullständiga sökvägen där du vill att providern ska spara en loggfil för att installera eller avinstallera paketet.</span><span class="sxs-lookup"><span data-stu-id="f1327-121">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>|
| <span data-ttu-id="f1327-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="f1327-122">DependsOn</span></span> | <span data-ttu-id="f1327-123">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="f1327-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f1327-124">Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är **ResourceName** och är av typen **ResourceType**, syntaxen för den här egenskapen är ”DependsOn =” [ ResourceType] ResourceName ”''.</span><span class="sxs-lookup"><span data-stu-id="f1327-124">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example"></a><span data-ttu-id="f1327-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="f1327-125">Example</span></span>

<span data-ttu-id="f1327-126">Följande exempelkonfiguration tar indataparametrar och säkerställer att CAB-filen som anges av den `$Name` parametern är installerad.</span><span class="sxs-lookup"><span data-stu-id="f1327-126">The following example configuration takes input parameters, and ensures that the .cab file specified by the `$Name` parameter is installed.</span></span>

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