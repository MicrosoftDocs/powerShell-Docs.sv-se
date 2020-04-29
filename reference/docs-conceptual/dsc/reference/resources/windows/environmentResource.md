---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC-miljö-resurs
ms.openlocfilehash: d6d3b4a2086be28fbfa2bf200acef9b13b7b7825
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71942484"
---
# <a name="dsc-environment-resource"></a><span data-ttu-id="b5483-103">DSC-miljö-resurs</span><span class="sxs-lookup"><span data-stu-id="b5483-103">DSC Environment Resource</span></span>

> <span data-ttu-id="b5483-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5. x</span><span class="sxs-lookup"><span data-stu-id="b5483-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="b5483-105">**Miljö** resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera systemmiljövariabler.</span><span class="sxs-lookup"><span data-stu-id="b5483-105">The **Environment** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="b5483-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="b5483-106">Syntax</span></span>

```Syntax
Environment [string] #ResourceName
{
    Name = [string]
    [ Path = [bool] ]
    [ Value = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="b5483-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="b5483-107">Properties</span></span>

|<span data-ttu-id="b5483-108">Egenskap</span><span class="sxs-lookup"><span data-stu-id="b5483-108">Property</span></span> |<span data-ttu-id="b5483-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b5483-109">Description</span></span> |
|---|---|
|<span data-ttu-id="b5483-110">Name</span><span class="sxs-lookup"><span data-stu-id="b5483-110">Name</span></span> |<span data-ttu-id="b5483-111">Anger namnet på den miljö variabel som du vill säkerställa ett speciellt tillstånd för.</span><span class="sxs-lookup"><span data-stu-id="b5483-111">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="b5483-112">Sökväg</span><span class="sxs-lookup"><span data-stu-id="b5483-112">Path</span></span> |<span data-ttu-id="b5483-113">Definierar den miljö variabel som konfigureras.</span><span class="sxs-lookup"><span data-stu-id="b5483-113">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="b5483-114">Ställ in den här `$true` egenskapen till om variabeln **är sökvägsvariabeln;** annars ställer du in den `$false`på.</span><span class="sxs-lookup"><span data-stu-id="b5483-114">Set this property to `$true` if the variable is the **Path** variable; otherwise, set it to `$false`.</span></span> <span data-ttu-id="b5483-115">Standardvärdet är `$false`.</span><span class="sxs-lookup"><span data-stu-id="b5483-115">The default is `$false`.</span></span> <span data-ttu-id="b5483-116">Om variabeln som konfigureras är **sökvägsvariabeln,** läggs värdet som anges via egenskapen **Value** till i det befintliga värdet.</span><span class="sxs-lookup"><span data-stu-id="b5483-116">If the variable being configured is the **Path** variable, the value provided through the **Value** property will be appended to the existing value.</span></span> |
|<span data-ttu-id="b5483-117">Värde</span><span class="sxs-lookup"><span data-stu-id="b5483-117">Value</span></span> |<span data-ttu-id="b5483-118">Värdet som ska tilldelas miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="b5483-118">The value to assign to the environment variable.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="b5483-119">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="b5483-119">Common properties</span></span>

|<span data-ttu-id="b5483-120">Egenskap</span><span class="sxs-lookup"><span data-stu-id="b5483-120">Property</span></span> |<span data-ttu-id="b5483-121">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b5483-121">Description</span></span> |
|---|---|
|<span data-ttu-id="b5483-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="b5483-122">DependsOn</span></span> |<span data-ttu-id="b5483-123">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="b5483-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="b5483-124">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är `DependsOn = "[ResourceType]ResourceName"`syntaxen för att använda den här egenskapen.</span><span class="sxs-lookup"><span data-stu-id="b5483-124">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="b5483-125">Kontrol</span><span class="sxs-lookup"><span data-stu-id="b5483-125">Ensure</span></span> |<span data-ttu-id="b5483-126">Anger om en variabel finns.</span><span class="sxs-lookup"><span data-stu-id="b5483-126">Indicates if a variable exists.</span></span> <span data-ttu-id="b5483-127">Ange att den här egenskapen ska **användas** för att skapa miljövariabeln om den inte finns eller för att säkerställa att dess värde matchar det som tillhandahålls via egenskapen **Value** om variabeln redan finns.</span><span class="sxs-lookup"><span data-stu-id="b5483-127">Set this property to **Present** to create the environment variable if it does not exist or to ensure that its value matches what is provided through the **Value** property if the variable already exists.</span></span> <span data-ttu-id="b5483-128">Ange det som **frånvarande** för att ta bort variabeln om den finns.</span><span class="sxs-lookup"><span data-stu-id="b5483-128">Set it to **Absent** to delete the variable if it exists.</span></span> |
|<span data-ttu-id="b5483-129">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="b5483-129">PsDscRunAsCredential</span></span> |<span data-ttu-id="b5483-130">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="b5483-130">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="b5483-131">Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="b5483-131">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="b5483-132">Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="b5483-132">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="b5483-133">Exempel</span><span class="sxs-lookup"><span data-stu-id="b5483-133">Example</span></span>

<span data-ttu-id="b5483-134">I följande exempel ser du att TestEnvironmentVariable finns och att det har värdet _TestValue_.</span><span class="sxs-lookup"><span data-stu-id="b5483-134">The following example ensures that TestEnvironmentVariable is present and it has the value _TestValue_.</span></span> <span data-ttu-id="b5483-135">Om den inte finns skapas den av.</span><span class="sxs-lookup"><span data-stu-id="b5483-135">If it is not present, it creates it.</span></span>

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```