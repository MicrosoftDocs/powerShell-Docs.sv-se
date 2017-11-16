---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "DSC för Linux nxPackage resurs"
ms.openlocfilehash: 11019b1cd12f23b0b498b7cb9a06e02c46c3c279
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-for-linux-nxpackage-resource"></a><span data-ttu-id="4a53c-103">DSC för Linux nxPackage resurs</span><span class="sxs-lookup"><span data-stu-id="4a53c-103">DSC for Linux nxPackage Resource</span></span>

<span data-ttu-id="4a53c-104">Den **nxPackage** resurs i PowerShell önskad tillstånd Configuration (DSC) ger dig möjlighet att hantera paket på en Linux-nod.</span><span class="sxs-lookup"><span data-stu-id="4a53c-104">The **nxPackage** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage packages on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="4a53c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4a53c-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="4a53c-106">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="4a53c-106">Properties</span></span>

|  <span data-ttu-id="4a53c-107">Egenskap</span><span class="sxs-lookup"><span data-stu-id="4a53c-107">Property</span></span> |  <span data-ttu-id="4a53c-108">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4a53c-108">Description</span></span> | 
|---|---|
| <span data-ttu-id="4a53c-109">Namn</span><span class="sxs-lookup"><span data-stu-id="4a53c-109">Name</span></span>| <span data-ttu-id="4a53c-110">Namnet på paketet som du vill se till att ett visst tillstånd.</span><span class="sxs-lookup"><span data-stu-id="4a53c-110">The name of the package for which you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="4a53c-111">Se till att</span><span class="sxs-lookup"><span data-stu-id="4a53c-111">Ensure</span></span>| <span data-ttu-id="4a53c-112">Anger om du vill kontrollera att paketet finns.</span><span class="sxs-lookup"><span data-stu-id="4a53c-112">Determines whether to check if the package exists.</span></span> <span data-ttu-id="4a53c-113">Ange egenskapen ”aktuella” för att säkerställa att paketet finns.</span><span class="sxs-lookup"><span data-stu-id="4a53c-113">Set this property to "Present" to ensure the package exists.</span></span> <span data-ttu-id="4a53c-114">Ange den till ”saknas” så paketet inte finns.</span><span class="sxs-lookup"><span data-stu-id="4a53c-114">Set it to "Absent" to ensure the package does not exist.</span></span> <span data-ttu-id="4a53c-115">Standardvärdet är ”saknas”.</span><span class="sxs-lookup"><span data-stu-id="4a53c-115">The default value is "Present".</span></span>|  
| <span data-ttu-id="4a53c-116">PackageManager</span><span class="sxs-lookup"><span data-stu-id="4a53c-116">PackageManager</span></span>| <span data-ttu-id="4a53c-117">Värden som stöds är ”yum”, ”lgh” och ”zypper”.</span><span class="sxs-lookup"><span data-stu-id="4a53c-117">Supported values are "yum", "apt", and "zypper".</span></span> <span data-ttu-id="4a53c-118">Anger package manager att använda vid installation av paket.</span><span class="sxs-lookup"><span data-stu-id="4a53c-118">Specifies the package manager to use when installing packages.</span></span> <span data-ttu-id="4a53c-119">Om **FilePath** anges den angivna sökvägen används för att installera paketet.</span><span class="sxs-lookup"><span data-stu-id="4a53c-119">If **FilePath** is specified, the provided path will be used to install the package.</span></span> <span data-ttu-id="4a53c-120">Annars används en Package Manager för att installera paketet från en förkonfigurerad databas.</span><span class="sxs-lookup"><span data-stu-id="4a53c-120">Otherwise, a Package Manager will be used to install the package from a pre-configured repository.</span></span> <span data-ttu-id="4a53c-121">Om varken **PackageManager** eller **FilePath** tillhandahålls standard package manager för systemet används.</span><span class="sxs-lookup"><span data-stu-id="4a53c-121">If neither **PackageManager** nor **FilePath** are provided, the default package manager for the system will be used.</span></span>| 
| <span data-ttu-id="4a53c-122">filePath</span><span class="sxs-lookup"><span data-stu-id="4a53c-122">FilePath</span></span>| <span data-ttu-id="4a53c-123">Sökvägen till filen där paketet finns</span><span class="sxs-lookup"><span data-stu-id="4a53c-123">The file path where the package resides</span></span>| 
| <span data-ttu-id="4a53c-124">PackageGroup</span><span class="sxs-lookup"><span data-stu-id="4a53c-124">PackageGroup</span></span>| <span data-ttu-id="4a53c-125">Om **$true**, **namn** förväntas vara namnet på en paketeringsgrupp för användning med en **PackageManager**.</span><span class="sxs-lookup"><span data-stu-id="4a53c-125">If **$true**, the **Name** is expected to be the name of a package group for use with a **PackageManager**.</span></span> <span data-ttu-id="4a53c-126">**PacakgeGroup** är inte giltig när de tillhandahåller en **FilePath**.</span><span class="sxs-lookup"><span data-stu-id="4a53c-126">**PacakgeGroup** is not valid when providing a **FilePath**.</span></span>| 
| <span data-ttu-id="4a53c-127">Argument</span><span class="sxs-lookup"><span data-stu-id="4a53c-127">Arguments</span></span>| <span data-ttu-id="4a53c-128">En sträng med argument som exakt så som kommer att skickas till paketet.</span><span class="sxs-lookup"><span data-stu-id="4a53c-128">A string of arguments that will be passed to the package exactly as provided.</span></span>| 
| <span data-ttu-id="4a53c-129">Returkod</span><span class="sxs-lookup"><span data-stu-id="4a53c-129">ReturnCode</span></span>| <span data-ttu-id="4a53c-130">Förväntade returkoden.</span><span class="sxs-lookup"><span data-stu-id="4a53c-130">The expected return code.</span></span> <span data-ttu-id="4a53c-131">Om den faktiska returkod matchar inte det förväntade värdet som anges här, konfigurationen returneras ett fel.</span><span class="sxs-lookup"><span data-stu-id="4a53c-131">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span>| 
| <span data-ttu-id="4a53c-132">dependsOn</span><span class="sxs-lookup"><span data-stu-id="4a53c-132">DependsOn</span></span> | <span data-ttu-id="4a53c-133">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="4a53c-133">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="4a53c-134">Till exempel om den **ID** resursens configuration skriptblock som du vill köra först är **ResourceName** och dess typ är **ResourceType**, syntaxen för detta Egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="4a53c-134">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="example"></a><span data-ttu-id="4a53c-135">Exempel</span><span class="sxs-lookup"><span data-stu-id="4a53c-135">Example</span></span>

<span data-ttu-id="4a53c-136">I följande exempel säkerställer att paketet med namnet ”httpd” är installerad på en Linux-dator med hjälp av ”Yum” package manager.</span><span class="sxs-lookup"><span data-stu-id="4a53c-136">The following example ensures that the package named "httpd" is installed on a Linux computer, using the “Yum” package manager.</span></span>

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

