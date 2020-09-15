---
ms.date: 07/16/2020
keywords: DSC, PowerShell, konfiguration, installation
title: DSC WindowsPackageCab-resurs
ms.openlocfilehash: 7205a454d100bb369fd6cf0c5ac419585c8bbe86
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464153"
---
# <a name="dsc-windowspackagecab-resource"></a><span data-ttu-id="c6be8-103">DSC WindowsPackageCab-resurs</span><span class="sxs-lookup"><span data-stu-id="c6be8-103">DSC WindowsPackageCab Resource</span></span>

> <span data-ttu-id="c6be8-104">Gäller för: Windows PowerShell 5,1</span><span class="sxs-lookup"><span data-stu-id="c6be8-104">Applies To: Windows PowerShell 5.1</span></span>

<span data-ttu-id="c6be8-105">**WindowsPackageCab** -resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att installera eller avinstallera Windows kabinett paket (. cab) på en målnod.</span><span class="sxs-lookup"><span data-stu-id="c6be8-105">The **WindowsPackageCab** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Windows cabinet (.cab) packages on a target node.</span></span>

<span data-ttu-id="c6be8-106">Målnod måste ha DISM PowerShell-modulen installerad.</span><span class="sxs-lookup"><span data-stu-id="c6be8-106">The target node must have the DISM PowerShell module installed.</span></span> <span data-ttu-id="c6be8-107">Mer information finns i [använda DISM i Windows PowerShell](/windows-hardware/manufacture/desktop/use-dism-in-windows-powershell-s14).</span><span class="sxs-lookup"><span data-stu-id="c6be8-107">For information, see [Use DISM in Windows PowerShell](/windows-hardware/manufacture/desktop/use-dism-in-windows-powershell-s14).</span></span>

## <a name="syntax"></a><span data-ttu-id="c6be8-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="c6be8-108">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="c6be8-109">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="c6be8-109">Properties</span></span>

|<span data-ttu-id="c6be8-110">Egenskap</span><span class="sxs-lookup"><span data-stu-id="c6be8-110">Property</span></span> |<span data-ttu-id="c6be8-111">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c6be8-111">Description</span></span> |
|---|---|
|<span data-ttu-id="c6be8-112">Name</span><span class="sxs-lookup"><span data-stu-id="c6be8-112">Name</span></span> |<span data-ttu-id="c6be8-113">Anger namnet på det paket som du vill säkerställa ett speciellt tillstånd för.</span><span class="sxs-lookup"><span data-stu-id="c6be8-113">Indicates the name of the package for you want to ensure a specific state.</span></span> |
|<span data-ttu-id="c6be8-114">Sök</span><span class="sxs-lookup"><span data-stu-id="c6be8-114">SourcePath</span></span> |<span data-ttu-id="c6be8-115">Anger sökvägen dit paketet finns.</span><span class="sxs-lookup"><span data-stu-id="c6be8-115">Indicates the path where the package resides.</span></span> |
|<span data-ttu-id="c6be8-116">LogPath</span><span class="sxs-lookup"><span data-stu-id="c6be8-116">LogPath</span></span> |<span data-ttu-id="c6be8-117">Anger den fullständiga sökvägen dit du vill att providern ska spara en loggfil för att installera eller avinstallera paketet.</span><span class="sxs-lookup"><span data-stu-id="c6be8-117">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="c6be8-118">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="c6be8-118">Common properties</span></span>

|<span data-ttu-id="c6be8-119">Egenskap</span><span class="sxs-lookup"><span data-stu-id="c6be8-119">Property</span></span> |<span data-ttu-id="c6be8-120">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c6be8-120">Description</span></span> |
|---|---|
|<span data-ttu-id="c6be8-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="c6be8-121">DependsOn</span></span> |<span data-ttu-id="c6be8-122">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="c6be8-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c6be8-123">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="c6be8-123">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="c6be8-124">Kontrol</span><span class="sxs-lookup"><span data-stu-id="c6be8-124">Ensure</span></span> |<span data-ttu-id="c6be8-125">Anger om paketet är installerat.</span><span class="sxs-lookup"><span data-stu-id="c6be8-125">Indicates if the package is installed.</span></span> <span data-ttu-id="c6be8-126">Ange den här egenskapen som **saknas** för att se till att paketet inte är installerat (eller avinstallera paketet om det är installerat).</span><span class="sxs-lookup"><span data-stu-id="c6be8-126">Set this property to **Absent** to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="c6be8-127">Ange att det är **tillgängligt** för att se till att paketet är installerat.</span><span class="sxs-lookup"><span data-stu-id="c6be8-127">Set it to **Present** to ensure the package is installed.</span></span> <span data-ttu-id="c6be8-128">**Se till att** det finns en obligatorisk egenskap för **WindowsPackageCab** -resursen.</span><span class="sxs-lookup"><span data-stu-id="c6be8-128">**Ensure** is a required property on the **WindowsPackageCab** resource.</span></span> |
|<span data-ttu-id="c6be8-129">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="c6be8-129">PsDscRunAsCredential</span></span> |<span data-ttu-id="c6be8-130">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="c6be8-130">Sets the credential for running the entire resource as.</span></span> |

## <a name="example"></a><span data-ttu-id="c6be8-131">Exempel</span><span class="sxs-lookup"><span data-stu-id="c6be8-131">Example</span></span>

<span data-ttu-id="c6be8-132">Följande exempel konfiguration använder indataparametrar och säkerställer att CAB-filen som anges av `$Name` parametern är installerad.</span><span class="sxs-lookup"><span data-stu-id="c6be8-132">The following example configuration takes input parameters, and ensures that the .cab file specified by the `$Name` parameter is installed.</span></span>

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
