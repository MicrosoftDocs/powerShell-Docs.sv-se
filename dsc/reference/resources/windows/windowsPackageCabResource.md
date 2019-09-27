---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC WindowsPackageCab-resurs
ms.openlocfilehash: ec465b2c3b1d180ba46ee24a61f2be1129148962
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71323824"
---
# <a name="dsc-windowspackagecab-resource"></a><span data-ttu-id="0d763-103">DSC WindowsPackageCab-resurs</span><span class="sxs-lookup"><span data-stu-id="0d763-103">DSC WindowsPackageCab Resource</span></span>

> <span data-ttu-id="0d763-104">Gäller för: Windows PowerShell 5,1</span><span class="sxs-lookup"><span data-stu-id="0d763-104">Applies To: Windows PowerShell 5.1</span></span>

<span data-ttu-id="0d763-105">**WindowsPackageCab** -resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att installera eller avinstallera Windows kabinett paket (. cab) på en målnod.</span><span class="sxs-lookup"><span data-stu-id="0d763-105">The **WindowsPackageCab** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Windows cabinet (.cab) packages on a target node.</span></span>

<span data-ttu-id="0d763-106">Målnod måste ha DISM PowerShell-modulen installerad.</span><span class="sxs-lookup"><span data-stu-id="0d763-106">The target node must have the DISM PowerShell module installed.</span></span> <span data-ttu-id="0d763-107">Mer information finns i [använda DISM i Windows PowerShell](/windows-hardware/manufacture/desktop/use-dism-in-windows-powershell-s14).</span><span class="sxs-lookup"><span data-stu-id="0d763-107">For information, see [Use DISM in Windows PowerShell](/windows-hardware/manufacture/desktop/use-dism-in-windows-powershell-s14).</span></span>

## <a name="syntax"></a><span data-ttu-id="0d763-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="0d763-108">Syntax</span></span>

```Syntax
{
    Name = [string]
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    Ensure = [string] { Absent | Present }
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="0d763-109">properties</span><span class="sxs-lookup"><span data-stu-id="0d763-109">Properties</span></span>

|<span data-ttu-id="0d763-110">Egenskap</span><span class="sxs-lookup"><span data-stu-id="0d763-110">Property</span></span> |<span data-ttu-id="0d763-111">Description</span><span class="sxs-lookup"><span data-stu-id="0d763-111">Description</span></span> |
|---|---|
|<span data-ttu-id="0d763-112">Name</span><span class="sxs-lookup"><span data-stu-id="0d763-112">Name</span></span> |<span data-ttu-id="0d763-113">Anger namnet på det paket som du vill säkerställa ett speciellt tillstånd för.</span><span class="sxs-lookup"><span data-stu-id="0d763-113">Indicates the name of the package for you want to ensure a specific state.</span></span> |
|<span data-ttu-id="0d763-114">Sök</span><span class="sxs-lookup"><span data-stu-id="0d763-114">SourcePath</span></span> |<span data-ttu-id="0d763-115">Anger sökvägen dit paketet finns.</span><span class="sxs-lookup"><span data-stu-id="0d763-115">Indicates the path where the package resides.</span></span> |
|<span data-ttu-id="0d763-116">LogPath</span><span class="sxs-lookup"><span data-stu-id="0d763-116">LogPath</span></span> |<span data-ttu-id="0d763-117">Anger den fullständiga sökvägen dit du vill att providern ska spara en loggfil för att installera eller avinstallera paketet.</span><span class="sxs-lookup"><span data-stu-id="0d763-117">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="0d763-118">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="0d763-118">Common properties</span></span>

|<span data-ttu-id="0d763-119">Egenskap</span><span class="sxs-lookup"><span data-stu-id="0d763-119">Property</span></span> |<span data-ttu-id="0d763-120">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0d763-120">Description</span></span> |
|---|---|
|<span data-ttu-id="0d763-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="0d763-121">DependsOn</span></span> |<span data-ttu-id="0d763-122">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="0d763-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="0d763-123">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är `DependsOn = "[ResourceType]ResourceName"`syntaxen för att använda den här egenskapen.</span><span class="sxs-lookup"><span data-stu-id="0d763-123">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="0d763-124">Kontrol</span><span class="sxs-lookup"><span data-stu-id="0d763-124">Ensure</span></span> |<span data-ttu-id="0d763-125">Anger om paketet är installerat.</span><span class="sxs-lookup"><span data-stu-id="0d763-125">Indicates if the package is installed.</span></span> <span data-ttu-id="0d763-126">Ange den här egenskapen som **saknas** för att se till att paketet inte är installerat (eller avinstallera paketet om det är installerat).</span><span class="sxs-lookup"><span data-stu-id="0d763-126">Set this property to **Absent** to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="0d763-127">Ange att det är **tillgängligt** för att se till att paketet är installerat.</span><span class="sxs-lookup"><span data-stu-id="0d763-127">Set it to **Present** to ensure the package is installed.</span></span> <span data-ttu-id="0d763-128">**Se till att** det finns en obligatorisk egenskap för **WindowsPackageCab** -resursen.</span><span class="sxs-lookup"><span data-stu-id="0d763-128">**Ensure** is a required property on the **WindowsPackageCab** resource.</span></span> |
|<span data-ttu-id="0d763-129">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="0d763-129">PsDscRunAsCredential</span></span> |<span data-ttu-id="0d763-130">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="0d763-130">Sets the credential for running the entire resource as.</span></span> |

## <a name="example"></a><span data-ttu-id="0d763-131">Exempel</span><span class="sxs-lookup"><span data-stu-id="0d763-131">Example</span></span>

<span data-ttu-id="0d763-132">Följande exempel konfiguration använder indataparametrar och säkerställer att CAB-filen som anges av `$Name` parametern är installerad.</span><span class="sxs-lookup"><span data-stu-id="0d763-132">The following example configuration takes input parameters, and ensures that the .cab file specified by the `$Name` parameter is installed.</span></span>

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