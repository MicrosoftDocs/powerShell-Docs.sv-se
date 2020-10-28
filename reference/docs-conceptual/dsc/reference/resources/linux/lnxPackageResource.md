---
ms.date: 07/17/2020
ms.topic: reference
title: DSC för Linux nxPackage-resurs
description: DSC för Linux nxPackage-resurs
ms.openlocfilehash: b84c7963297e8a88e729cd67611245b017c27fb7
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648837"
---
# <a name="dsc-for-linux-nxpackage-resource"></a><span data-ttu-id="0dbfe-103">DSC för Linux nxPackage-resurs</span><span class="sxs-lookup"><span data-stu-id="0dbfe-103">DSC for Linux nxPackage Resource</span></span>

<span data-ttu-id="0dbfe-104">**NxPackage** -resursen i PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera paket på en Linux-nod.</span><span class="sxs-lookup"><span data-stu-id="0dbfe-104">The **nxPackage** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage packages on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="0dbfe-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0dbfe-105">Syntax</span></span>

```Syntax
nxPackage <string> #ResourceName
{
    Name = <string>
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ FilePath = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="0dbfe-106">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="0dbfe-106">Properties</span></span>

|<span data-ttu-id="0dbfe-107">Egenskap</span><span class="sxs-lookup"><span data-stu-id="0dbfe-107">Property</span></span> |<span data-ttu-id="0dbfe-108">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0dbfe-108">Description</span></span> |
|---|---|
|<span data-ttu-id="0dbfe-109">Namn</span><span class="sxs-lookup"><span data-stu-id="0dbfe-109">Name</span></span> |<span data-ttu-id="0dbfe-110">Namnet på det paket som du vill säkerställa ett speciellt tillstånd för.</span><span class="sxs-lookup"><span data-stu-id="0dbfe-110">The name of the package for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="0dbfe-111">PackageManager</span><span class="sxs-lookup"><span data-stu-id="0dbfe-111">PackageManager</span></span> |<span data-ttu-id="0dbfe-112">De värden som stöds är **yum** , **apt** och **zypper** .</span><span class="sxs-lookup"><span data-stu-id="0dbfe-112">Supported values are **yum** , **apt** , and **zypper** .</span></span> <span data-ttu-id="0dbfe-113">Anger vilken paket hanterare som ska användas för att installera paket.</span><span class="sxs-lookup"><span data-stu-id="0dbfe-113">Specifies the package manager to use when installing packages.</span></span> <span data-ttu-id="0dbfe-114">Om **sökväg anges används** den angivna sökvägen för att installera paketet.</span><span class="sxs-lookup"><span data-stu-id="0dbfe-114">If **FilePath** is specified, the provided path will be used to install the package.</span></span> <span data-ttu-id="0dbfe-115">Annars kommer en paket hanterare att användas för att installera paketet från en förkonfigurerad lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="0dbfe-115">Otherwise, a Package Manager will be used to install the package from a pre-configured repository.</span></span> <span data-ttu-id="0dbfe-116">Om varken **PackageManager** eller **sökväg** anges används standard paket hanteraren för systemet.</span><span class="sxs-lookup"><span data-stu-id="0dbfe-116">If neither **PackageManager** nor **FilePath** are provided, the default package manager for the system will be used.</span></span> |
|<span data-ttu-id="0dbfe-117">PackageGroup</span><span class="sxs-lookup"><span data-stu-id="0dbfe-117">PackageGroup</span></span> |<span data-ttu-id="0dbfe-118">Om `$true` **namnet** förväntas vara namnet på en paket grupp som ska användas med en **PackageManager** .</span><span class="sxs-lookup"><span data-stu-id="0dbfe-118">If `$true`, the **Name** is expected to be the name of a package group for use with a **PackageManager** .</span></span> <span data-ttu-id="0dbfe-119">**PackageGroup** är inte giltig vid en **fil Sök väg** .</span><span class="sxs-lookup"><span data-stu-id="0dbfe-119">**PackageGroup** is not valid when providing a **FilePath** .</span></span> |
|<span data-ttu-id="0dbfe-120">Argument</span><span class="sxs-lookup"><span data-stu-id="0dbfe-120">Arguments</span></span> |<span data-ttu-id="0dbfe-121">En sträng med argument som skickas till paketet exakt som det anges.</span><span class="sxs-lookup"><span data-stu-id="0dbfe-121">A string of arguments that will be passed to the package exactly as provided.</span></span> |
|<span data-ttu-id="0dbfe-122">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="0dbfe-122">ReturnCode</span></span> |<span data-ttu-id="0dbfe-123">Den förväntade retur koden.</span><span class="sxs-lookup"><span data-stu-id="0dbfe-123">The expected return code.</span></span> <span data-ttu-id="0dbfe-124">Om den faktiska retur koden inte matchar det förväntade värdet här, returnerar konfigurationen ett fel.</span><span class="sxs-lookup"><span data-stu-id="0dbfe-124">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span> |
|<span data-ttu-id="0dbfe-125">FilePath</span><span class="sxs-lookup"><span data-stu-id="0dbfe-125">FilePath</span></span> |<span data-ttu-id="0dbfe-126">Sökvägen till filen där paketet finns.</span><span class="sxs-lookup"><span data-stu-id="0dbfe-126">The file path where the package resides.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="0dbfe-127">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="0dbfe-127">Common properties</span></span>

|<span data-ttu-id="0dbfe-128">Egenskap</span><span class="sxs-lookup"><span data-stu-id="0dbfe-128">Property</span></span> |<span data-ttu-id="0dbfe-129">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0dbfe-129">Description</span></span> |
|---|---|
|<span data-ttu-id="0dbfe-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="0dbfe-130">DependsOn</span></span> |<span data-ttu-id="0dbfe-131">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="0dbfe-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="0dbfe-132">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="0dbfe-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="0dbfe-133">Kontrol</span><span class="sxs-lookup"><span data-stu-id="0dbfe-133">Ensure</span></span> |<span data-ttu-id="0dbfe-134">Avgör om det finns ett paket som ska kontrol leras.</span><span class="sxs-lookup"><span data-stu-id="0dbfe-134">Determines whether to check if the package exists.</span></span> <span data-ttu-id="0dbfe-135">Ange att den här egenskapen **finns** för att se till att paketet finns.</span><span class="sxs-lookup"><span data-stu-id="0dbfe-135">Set this property to **Present** to ensure the package exists.</span></span> <span data-ttu-id="0dbfe-136">Ange det som **frånvarande** för att säkerställa att paketet inte finns.</span><span class="sxs-lookup"><span data-stu-id="0dbfe-136">Set it to **Absent** to ensure the package does not exist.</span></span> <span data-ttu-id="0dbfe-137">Standardvärdet finns **.**</span><span class="sxs-lookup"><span data-stu-id="0dbfe-137">The default value is **Present** .</span></span> |

## <a name="example"></a><span data-ttu-id="0dbfe-138">Exempel</span><span class="sxs-lookup"><span data-stu-id="0dbfe-138">Example</span></span>

<span data-ttu-id="0dbfe-139">I följande exempel ser du till att paketet med namnet "httpd" är installerat på en Linux-dator med hjälp av paket hanteraren "yum".</span><span class="sxs-lookup"><span data-stu-id="0dbfe-139">The following example ensures that the package named "httpd" is installed on a Linux computer, using the "Yum" package manager.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxPackage httpd
    {
        Name = "httpd"
        Ensure = "Present"
        PackageManager = "Yum"
    }
}
```
