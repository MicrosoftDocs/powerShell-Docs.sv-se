---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Resurs för DSC-miljö
ms.openlocfilehash: 4f024afe2d70c13e19406745ec7fd69821ab229b
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-environment-resource"></a><span data-ttu-id="42ea0-103">Resurs för DSC-miljö</span><span class="sxs-lookup"><span data-stu-id="42ea0-103">DSC Environment Resource</span></span>

> <span data-ttu-id="42ea0-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="42ea0-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="42ea0-105">Den __miljö__ resurs i Windows PowerShell önskad tillstånd Configuration (DSC) tillhandahåller en mekanism för att hantera systemmiljövariabler.</span><span class="sxs-lookup"><span data-stu-id="42ea0-105">The __Environment__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="42ea0-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="42ea0-106">Syntax</span></span>
``` mof
Environment [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Path = [bool] ]
    [ DependsOn = [string[]] ]
    [ Value = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="42ea0-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="42ea0-107">Properties</span></span>

|  <span data-ttu-id="42ea0-108">Egenskap</span><span class="sxs-lookup"><span data-stu-id="42ea0-108">Property</span></span>  |  <span data-ttu-id="42ea0-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="42ea0-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="42ea0-110">Namn</span><span class="sxs-lookup"><span data-stu-id="42ea0-110">Name</span></span>| <span data-ttu-id="42ea0-111">Anger namnet på den miljövariabel som du vill se till att ett visst tillstånd.</span><span class="sxs-lookup"><span data-stu-id="42ea0-111">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="42ea0-112">Se till att</span><span class="sxs-lookup"><span data-stu-id="42ea0-112">Ensure</span></span>| <span data-ttu-id="42ea0-113">Anger om det finns en variabel.</span><span class="sxs-lookup"><span data-stu-id="42ea0-113">Indicates if a variable exists.</span></span> <span data-ttu-id="42ea0-114">Den här egenskapen __finns__ skapa miljövariabeln om det inte finns eller så att dess värde matchar vad som tillhandahålls via den __värdet__ egenskapen om variabeln redan finns.</span><span class="sxs-lookup"><span data-stu-id="42ea0-114">Set this property to __Present__ to create the environment variable if it does not exist or to ensure that its value matches what is provided through the __Value__ property if the variable already exists.</span></span> <span data-ttu-id="42ea0-115">Ange det till __saknas__ ta bort variabeln om den finns.</span><span class="sxs-lookup"><span data-stu-id="42ea0-115">Set it to __Absent__ to delete the variable if it exists.</span></span>|
| <span data-ttu-id="42ea0-116">Sökväg</span><span class="sxs-lookup"><span data-stu-id="42ea0-116">Path</span></span>| <span data-ttu-id="42ea0-117">Definierar miljövariabeln som konfigureras.</span><span class="sxs-lookup"><span data-stu-id="42ea0-117">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="42ea0-118">Den här egenskapen __$true__ om variabeln är den __sökväg__ variabeln, annars inställd på __$false__.</span><span class="sxs-lookup"><span data-stu-id="42ea0-118">Set this property to __$true__ if the variable is the __Path__ variable; otherwise, set it to __$false__.</span></span> <span data-ttu-id="42ea0-119">Standardvärdet är __$false__.</span><span class="sxs-lookup"><span data-stu-id="42ea0-119">The default is __$false__.</span></span> <span data-ttu-id="42ea0-120">Om variabeln som konfigureras är den __sökväg__ variabel, värdet tillhandahålls via den __värdet__ egenskap läggs till det befintliga värdet.</span><span class="sxs-lookup"><span data-stu-id="42ea0-120">If the variable being configured is the __Path__ variable, the value provided through the __Value__ property will be appended to the existing value.</span></span>|
| <span data-ttu-id="42ea0-121">dependsOn</span><span class="sxs-lookup"><span data-stu-id="42ea0-121">DependsOn</span></span> | <span data-ttu-id="42ea0-122">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="42ea0-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="42ea0-123">Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis __ResourceName__ och dess typ är __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="42ea0-123">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="42ea0-124">Värde</span><span class="sxs-lookup"><span data-stu-id="42ea0-124">Value</span></span>| <span data-ttu-id="42ea0-125">Värdet som tilldelas miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="42ea0-125">The value to assign to the environment variable.</span></span>|

## <a name="example"></a><span data-ttu-id="42ea0-126">Exempel</span><span class="sxs-lookup"><span data-stu-id="42ea0-126">Example</span></span>

<span data-ttu-id="42ea0-127">I följande exempel säkerställer att __TestEnvironmentVariable__ finns och har värdet __Provvärde__.</span><span class="sxs-lookup"><span data-stu-id="42ea0-127">The following example ensures that __TestEnvironmentVariable__ is present and it has the value __TestValue__.</span></span> <span data-ttu-id="42ea0-128">Om det inte finns, skapas den.</span><span class="sxs-lookup"><span data-stu-id="42ea0-128">If it is not present, it creates it.</span></span>

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```