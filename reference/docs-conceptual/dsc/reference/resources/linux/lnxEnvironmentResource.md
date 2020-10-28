---
ms.date: 07/17/2020
ms.topic: reference
title: DSC för Linux nxEnvironment-resurs
description: DSC för Linux nxEnvironment-resurs
ms.openlocfilehash: 86ed538732254967cb4a3bb55af4f6b179947e52
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644681"
---
# <a name="dsc-for-linux-nxenvironment-resource"></a><span data-ttu-id="b6906-103">DSC för Linux nxEnvironment-resurs</span><span class="sxs-lookup"><span data-stu-id="b6906-103">DSC for Linux nxEnvironment Resource</span></span>

<span data-ttu-id="b6906-104">**NxEnvironment** -resursen i PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera systemmiljövariabler på en Linux-nod.</span><span class="sxs-lookup"><span data-stu-id="b6906-104">The **nxEnvironment** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="b6906-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b6906-105">Syntax</span></span>

```Syntax
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Path = <bool> }
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="b6906-106">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="b6906-106">Properties</span></span>

|<span data-ttu-id="b6906-107">Egenskap</span><span class="sxs-lookup"><span data-stu-id="b6906-107">Property</span></span> |<span data-ttu-id="b6906-108">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b6906-108">Description</span></span> |
|---|---|
|<span data-ttu-id="b6906-109">Namn</span><span class="sxs-lookup"><span data-stu-id="b6906-109">Name</span></span> |<span data-ttu-id="b6906-110">Anger namnet på den miljö variabel som du vill säkerställa ett speciellt tillstånd för.</span><span class="sxs-lookup"><span data-stu-id="b6906-110">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="b6906-111">Värde</span><span class="sxs-lookup"><span data-stu-id="b6906-111">Value</span></span> |<span data-ttu-id="b6906-112">Värdet som ska tilldelas miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="b6906-112">The value to assign to the environment variable.</span></span> |
|<span data-ttu-id="b6906-113">Sökväg</span><span class="sxs-lookup"><span data-stu-id="b6906-113">Path</span></span> |<span data-ttu-id="b6906-114">Definierar den miljö variabel som konfigureras.</span><span class="sxs-lookup"><span data-stu-id="b6906-114">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="b6906-115">Ange den här egenskapen till `$true` om variabeln är **sökvägsvariabeln** . annars anger du den som `$false` .</span><span class="sxs-lookup"><span data-stu-id="b6906-115">Set this property to `$true` if the variable is the **Path** variable; otherwise, set it to `$false`.</span></span> <span data-ttu-id="b6906-116">Standardvärdet är `$false`.</span><span class="sxs-lookup"><span data-stu-id="b6906-116">The default is `$false`.</span></span> <span data-ttu-id="b6906-117">Om variabeln som konfigureras är **sökvägsvariabeln,** läggs värdet som anges via egenskapen **Value** till i det befintliga värdet.</span><span class="sxs-lookup"><span data-stu-id="b6906-117">If the variable being configured is the **Path** variable, the value provided through the **Value** property will be appended to the existing value.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="b6906-118">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="b6906-118">Common properties</span></span>

|<span data-ttu-id="b6906-119">Egenskap</span><span class="sxs-lookup"><span data-stu-id="b6906-119">Property</span></span> |<span data-ttu-id="b6906-120">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b6906-120">Description</span></span> |
|---|---|
|<span data-ttu-id="b6906-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="b6906-121">DependsOn</span></span> |<span data-ttu-id="b6906-122">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="b6906-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="b6906-123">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="b6906-123">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="b6906-124">Kontrol</span><span class="sxs-lookup"><span data-stu-id="b6906-124">Ensure</span></span> |<span data-ttu-id="b6906-125">Anger om variabeln finns eller inte.</span><span class="sxs-lookup"><span data-stu-id="b6906-125">Determines whether to check if the variable exists.</span></span> <span data-ttu-id="b6906-126">Ange att den här egenskapen ska **användas** för att se till att variabeln finns.</span><span class="sxs-lookup"><span data-stu-id="b6906-126">Set this property to **Present** to ensure the variable exists.</span></span> <span data-ttu-id="b6906-127">Ange det som **frånvarande** för att se till att variabeln inte finns.</span><span class="sxs-lookup"><span data-stu-id="b6906-127">Set it to **Absent** to ensure the variable does not exist.</span></span> <span data-ttu-id="b6906-128">Standardvärdet finns **.**</span><span class="sxs-lookup"><span data-stu-id="b6906-128">The default value is **Present** .</span></span> |

## <a name="additional-information"></a><span data-ttu-id="b6906-129">Ytterligare information</span><span class="sxs-lookup"><span data-stu-id="b6906-129">Additional Information</span></span>

- <span data-ttu-id="b6906-130">Om **sökvägen** saknas eller anges till `$false` hanteras miljövariabler i `/etc/environment` .</span><span class="sxs-lookup"><span data-stu-id="b6906-130">If **Path** is absent or set to `$false`, environment variables are managed in `/etc/environment`.</span></span>
  <span data-ttu-id="b6906-131">Dina program eller skript kan behöva konfigureras för att käll `/etc/environment` filen ska kunna komma åt de hanterade miljövariablerna.</span><span class="sxs-lookup"><span data-stu-id="b6906-131">Your programs or scripts may require configuration to source the `/etc/environment` file to access the managed environment variables.</span></span>
- <span data-ttu-id="b6906-132">Om **sökväg** är inställd på `$true` hanteras miljövariabeln i filen `/etc/profile.d/DSCenvironment.sh` .</span><span class="sxs-lookup"><span data-stu-id="b6906-132">If **Path** is set to `$true`, the environment variable is managed in the file `/etc/profile.d/DSCenvironment.sh`.</span></span> <span data-ttu-id="b6906-133">Den här filen kommer att skapas om den inte finns.</span><span class="sxs-lookup"><span data-stu-id="b6906-133">This file will be created if it does not exist.</span></span> <span data-ttu-id="b6906-134">Om alternativet för **att se** till att värdet **saknas** och **sökvägen** är inställt på `$true` , tas en befintlig miljö variabel bara bort från `/etc/profile.d/DSCenvironment.sh` och inte från andra filer.</span><span class="sxs-lookup"><span data-stu-id="b6906-134">If **Ensure** is set to **Absent** and **Path** is set to `$true`, an existing environment variable will only be removed from `/etc/profile.d/DSCenvironment.sh` and not from other files.</span></span>

## <a name="example"></a><span data-ttu-id="b6906-135">Exempel</span><span class="sxs-lookup"><span data-stu-id="b6906-135">Example</span></span>

<span data-ttu-id="b6906-136">I följande exempel visas hur du använder **nxEnvironment** -resursen för att se till att **TestEnvironmentVariable** finns och har värdet "test-Value".</span><span class="sxs-lookup"><span data-stu-id="b6906-136">The following example shows how to use the **nxEnvironment** resource to ensure that **TestEnvironmentVariable** is present and has the value "Test-Value".</span></span> <span data-ttu-id="b6906-137">Om **TestEnvironmentVariable** inte finns kommer den att skapas.</span><span class="sxs-lookup"><span data-stu-id="b6906-137">If **TestEnvironmentVariable** is not present, it will be created.</span></span>

```powershell
Import-DSCResource -Module nx

nxEnvironment EnvironmentExample
{
    Ensure = "Present"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```
