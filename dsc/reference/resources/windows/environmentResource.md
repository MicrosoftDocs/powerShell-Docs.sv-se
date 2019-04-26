---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC-Miljöresurs
ms.openlocfilehash: 2bc1600a9df32538d59efa712569b12fa9e3beee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077542"
---
# <a name="dsc-environment-resource"></a><span data-ttu-id="4c8de-103">DSC-Miljöresurs</span><span class="sxs-lookup"><span data-stu-id="4c8de-103">DSC Environment Resource</span></span>

> <span data-ttu-id="4c8de-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4c8de-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="4c8de-105">Den __miljö__ resursen i Windows PowerShell Desired State Configuration (DSC) ger dig möjlighet att hantera systemets miljövariabler.</span><span class="sxs-lookup"><span data-stu-id="4c8de-105">The __Environment__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="4c8de-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="4c8de-106">Syntax</span></span>
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

## <a name="properties"></a><span data-ttu-id="4c8de-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="4c8de-107">Properties</span></span>

|  <span data-ttu-id="4c8de-108">Egenskap</span><span class="sxs-lookup"><span data-stu-id="4c8de-108">Property</span></span>  |  <span data-ttu-id="4c8de-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4c8de-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="4c8de-110">Namn</span><span class="sxs-lookup"><span data-stu-id="4c8de-110">Name</span></span>| <span data-ttu-id="4c8de-111">Anger namnet på den miljövariabel som du vill se till att ett visst tillstånd.</span><span class="sxs-lookup"><span data-stu-id="4c8de-111">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="4c8de-112">Se till att</span><span class="sxs-lookup"><span data-stu-id="4c8de-112">Ensure</span></span>| <span data-ttu-id="4c8de-113">Anger om det finns en variabel.</span><span class="sxs-lookup"><span data-stu-id="4c8de-113">Indicates if a variable exists.</span></span> <span data-ttu-id="4c8de-114">Den här egenskapen __finns__ att skapa miljövariabeln om det inte finns eller se till att värdet matchar vad som är tillgängligt via den __värdet__ egenskapen om variabeln redan finns.</span><span class="sxs-lookup"><span data-stu-id="4c8de-114">Set this property to __Present__ to create the environment variable if it does not exist or to ensure that its value matches what is provided through the __Value__ property if the variable already exists.</span></span> <span data-ttu-id="4c8de-115">Ange den till __frånvarande__ att ta bort variabeln om den finns.</span><span class="sxs-lookup"><span data-stu-id="4c8de-115">Set it to __Absent__ to delete the variable if it exists.</span></span>|
| <span data-ttu-id="4c8de-116">Sökväg</span><span class="sxs-lookup"><span data-stu-id="4c8de-116">Path</span></span>| <span data-ttu-id="4c8de-117">Definierar miljövariabeln som konfigureras.</span><span class="sxs-lookup"><span data-stu-id="4c8de-117">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="4c8de-118">Den här egenskapen __$true__ om variabeln är den __sökväg__ variabeln, i annat fall väljer __$false__.</span><span class="sxs-lookup"><span data-stu-id="4c8de-118">Set this property to __$true__ if the variable is the __Path__ variable; otherwise, set it to __$false__.</span></span> <span data-ttu-id="4c8de-119">Standardvärdet är __$false__.</span><span class="sxs-lookup"><span data-stu-id="4c8de-119">The default is __$false__.</span></span> <span data-ttu-id="4c8de-120">Om variabeln som konfigureras är den __sökväg__ variabeln, värdet tillhandahålls via de __värdet__ egenskapen kommer att läggas till det befintliga värdet.</span><span class="sxs-lookup"><span data-stu-id="4c8de-120">If the variable being configured is the __Path__ variable, the value provided through the __Value__ property will be appended to the existing value.</span></span>|
| <span data-ttu-id="4c8de-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="4c8de-121">DependsOn</span></span> | <span data-ttu-id="4c8de-122">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="4c8de-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="4c8de-123">Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är __ResourceName__ och är av typen __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="4c8de-123">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="4c8de-124">Värde</span><span class="sxs-lookup"><span data-stu-id="4c8de-124">Value</span></span>| <span data-ttu-id="4c8de-125">Värdet som tilldelas miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="4c8de-125">The value to assign to the environment variable.</span></span>|

## <a name="example"></a><span data-ttu-id="4c8de-126">Exempel</span><span class="sxs-lookup"><span data-stu-id="4c8de-126">Example</span></span>

<span data-ttu-id="4c8de-127">I följande exempel ser till att __TestEnvironmentVariable__ finns och har värdet __Provvärde__.</span><span class="sxs-lookup"><span data-stu-id="4c8de-127">The following example ensures that __TestEnvironmentVariable__ is present and it has the value __TestValue__.</span></span> <span data-ttu-id="4c8de-128">Om det inte finns skapas den.</span><span class="sxs-lookup"><span data-stu-id="4c8de-128">If it is not present, it creates it.</span></span>

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```