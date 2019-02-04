---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC för Linux nxPackage-resurs
ms.openlocfilehash: 64bb89a95bd6cbaea4e74b8a9979de52428fef3f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685685"
---
# <a name="dsc-for-linux-nxpackage-resource"></a><span data-ttu-id="74c80-103">DSC för Linux nxPackage-resurs</span><span class="sxs-lookup"><span data-stu-id="74c80-103">DSC for Linux nxPackage Resource</span></span>

<span data-ttu-id="74c80-104">Den **nxPackage** resursen i PowerShell Desired State Configuration (DSC) ger dig möjlighet att hantera paket på en Linux-nod.</span><span class="sxs-lookup"><span data-stu-id="74c80-104">The **nxPackage** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage packages on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="74c80-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="74c80-105">Syntax</span></span>

```
nxPackage <string> #ResourceName
{
    Name = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ LogPath = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="74c80-106">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="74c80-106">Properties</span></span>

|  <span data-ttu-id="74c80-107">Egenskap</span><span class="sxs-lookup"><span data-stu-id="74c80-107">Property</span></span> |  <span data-ttu-id="74c80-108">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="74c80-108">Description</span></span> |
|---|---|
| <span data-ttu-id="74c80-109">Namn</span><span class="sxs-lookup"><span data-stu-id="74c80-109">Name</span></span>| <span data-ttu-id="74c80-110">Namnet på paketet som du vill se till att ett visst tillstånd.</span><span class="sxs-lookup"><span data-stu-id="74c80-110">The name of the package for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="74c80-111">Se till att</span><span class="sxs-lookup"><span data-stu-id="74c80-111">Ensure</span></span>| <span data-ttu-id="74c80-112">Anger om du vill kontrollera om paketet.</span><span class="sxs-lookup"><span data-stu-id="74c80-112">Determines whether to check if the package exists.</span></span> <span data-ttu-id="74c80-113">Ange egenskapen ”aktuella” för att se till att paketet finns.</span><span class="sxs-lookup"><span data-stu-id="74c80-113">Set this property to "Present" to ensure the package exists.</span></span> <span data-ttu-id="74c80-114">Ange den till ”inte” för att se till att paketet inte finns.</span><span class="sxs-lookup"><span data-stu-id="74c80-114">Set it to "Absent" to ensure the package does not exist.</span></span> <span data-ttu-id="74c80-115">Standardvärdet är ”tillgänglig”.</span><span class="sxs-lookup"><span data-stu-id="74c80-115">The default value is "Present".</span></span>|
| <span data-ttu-id="74c80-116">PackageManager</span><span class="sxs-lookup"><span data-stu-id="74c80-116">PackageManager</span></span>| <span data-ttu-id="74c80-117">Värden som stöds är ”yum”, ”apt” och ”zypper”.</span><span class="sxs-lookup"><span data-stu-id="74c80-117">Supported values are "yum", "apt", and "zypper".</span></span> <span data-ttu-id="74c80-118">Anger package manager att använda när du installerar paket.</span><span class="sxs-lookup"><span data-stu-id="74c80-118">Specifies the package manager to use when installing packages.</span></span> <span data-ttu-id="74c80-119">Om **FilePath** anges, används den angivna sökvägen för att installera paketet.</span><span class="sxs-lookup"><span data-stu-id="74c80-119">If **FilePath** is specified, the provided path will be used to install the package.</span></span> <span data-ttu-id="74c80-120">I annat fall används en pakethanterare att installera paketet från en förkonfigurerad lagringsplats.</span><span class="sxs-lookup"><span data-stu-id="74c80-120">Otherwise, a Package Manager will be used to install the package from a pre-configured repository.</span></span> <span data-ttu-id="74c80-121">Om varken **PackageManager** eller **FilePath** har angetts, standard-Pakethanteraren för systemet används.</span><span class="sxs-lookup"><span data-stu-id="74c80-121">If neither **PackageManager** nor **FilePath** are provided, the default package manager for the system will be used.</span></span>|
| <span data-ttu-id="74c80-122">FilePath</span><span class="sxs-lookup"><span data-stu-id="74c80-122">FilePath</span></span>| <span data-ttu-id="74c80-123">Sökvägen där paketet finns</span><span class="sxs-lookup"><span data-stu-id="74c80-123">The file path where the package resides</span></span>|
| <span data-ttu-id="74c80-124">PackageGroup</span><span class="sxs-lookup"><span data-stu-id="74c80-124">PackageGroup</span></span>| <span data-ttu-id="74c80-125">Om **$true**, **namn** förväntas vara namnet på en paketeringsgrupp för användning med en **PackageManager**.</span><span class="sxs-lookup"><span data-stu-id="74c80-125">If **$true**, the **Name** is expected to be the name of a package group for use with a **PackageManager**.</span></span> <span data-ttu-id="74c80-126">**PacakgeGroup** är inte giltig när du anger en **FilePath**.</span><span class="sxs-lookup"><span data-stu-id="74c80-126">**PacakgeGroup** is not valid when providing a **FilePath**.</span></span>|
| <span data-ttu-id="74c80-127">Argument</span><span class="sxs-lookup"><span data-stu-id="74c80-127">Arguments</span></span>| <span data-ttu-id="74c80-128">En sträng med argument som exakt så som kommer att skickas till paketet.</span><span class="sxs-lookup"><span data-stu-id="74c80-128">A string of arguments that will be passed to the package exactly as provided.</span></span>|
| <span data-ttu-id="74c80-129">Returkod</span><span class="sxs-lookup"><span data-stu-id="74c80-129">ReturnCode</span></span>| <span data-ttu-id="74c80-130">Den förväntade returkod.</span><span class="sxs-lookup"><span data-stu-id="74c80-130">The expected return code.</span></span> <span data-ttu-id="74c80-131">Om den faktiska returkod matchar inte det förväntade värdet som anges här kan ett fel returneras i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="74c80-131">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span>|
| <span data-ttu-id="74c80-132">DependsOn</span><span class="sxs-lookup"><span data-stu-id="74c80-132">DependsOn</span></span> | <span data-ttu-id="74c80-133">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="74c80-133">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="74c80-134">Till exempel om den **ID** för resursen configuration-skriptblock som du vill köra först är **ResourceName** och är av typen **ResourceType**, syntaxen för detta Egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="74c80-134">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="74c80-135">Exempel</span><span class="sxs-lookup"><span data-stu-id="74c80-135">Example</span></span>

<span data-ttu-id="74c80-136">I följande exempel ser till att paket med namnet ”httpd” är installerad på en Linux-dator med ”Yum”-Pakethanteraren.</span><span class="sxs-lookup"><span data-stu-id="74c80-136">The following example ensures that the package named "httpd" is installed on a Linux computer, using the “Yum” package manager.</span></span>

```
Import-DSCResource -Module nx

Node $node {
nxPackage httpd
{
    Name = "httpd"
    Ensure = "Present"
    PackageManager = "Yum"
}
}
```