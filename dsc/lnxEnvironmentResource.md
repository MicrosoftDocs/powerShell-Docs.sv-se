---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "DSC för Linux nxEnvironment resurs"
ms.openlocfilehash: 3d09c9642f35627e939460c9c13dfe48d14030c3
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-for-linux-nxenvironment-resource"></a><span data-ttu-id="f38f1-103">DSC för Linux nxEnvironment resurs</span><span class="sxs-lookup"><span data-stu-id="f38f1-103">DSC for Linux nxEnvironment Resource</span></span>

<span data-ttu-id="f38f1-104">Den **nxEnvironment** resurs i PowerShell önskad tillstånd Configuration (DSC) ger möjlighet till att hantera systemmiljövariabler på en Linux-nod.</span><span class="sxs-lookup"><span data-stu-id="f38f1-104">The **nxEnvironment** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage system environment variables on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="f38f1-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f38f1-105">Syntax</span></span>

```
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Path = <bool> }
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="f38f1-106">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="f38f1-106">Properties</span></span>

|  <span data-ttu-id="f38f1-107">Egenskap</span><span class="sxs-lookup"><span data-stu-id="f38f1-107">Property</span></span> |  <span data-ttu-id="f38f1-108">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f38f1-108">Description</span></span> | 
|---|---|
| <span data-ttu-id="f38f1-109">Namn</span><span class="sxs-lookup"><span data-stu-id="f38f1-109">Name</span></span>| <span data-ttu-id="f38f1-110">Anger namnet på den miljövariabel som du vill se till att ett visst tillstånd.</span><span class="sxs-lookup"><span data-stu-id="f38f1-110">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="f38f1-111">Värde</span><span class="sxs-lookup"><span data-stu-id="f38f1-111">Value</span></span>| <span data-ttu-id="f38f1-112">Värdet som tilldelas miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="f38f1-112">The value to assign to the environment variable.</span></span>| 
| <span data-ttu-id="f38f1-113">Se till att</span><span class="sxs-lookup"><span data-stu-id="f38f1-113">Ensure</span></span>| <span data-ttu-id="f38f1-114">Anger om du vill kontrollera om det finns variabeln.</span><span class="sxs-lookup"><span data-stu-id="f38f1-114">Determines whether to check if the variable exists.</span></span> <span data-ttu-id="f38f1-115">Ange egenskapen ”aktuella” så variabeln finns.</span><span class="sxs-lookup"><span data-stu-id="f38f1-115">Set this property to "Present" to ensure the variable exists.</span></span> <span data-ttu-id="f38f1-116">Ange den till ”saknas” så variabeln inte finns.</span><span class="sxs-lookup"><span data-stu-id="f38f1-116">Set it to "Absent" to ensure the variable does not exist.</span></span> <span data-ttu-id="f38f1-117">Standardvärdet är ”saknas”.</span><span class="sxs-lookup"><span data-stu-id="f38f1-117">The default value is "Present".</span></span>| 
| <span data-ttu-id="f38f1-118">Sökväg</span><span class="sxs-lookup"><span data-stu-id="f38f1-118">Path</span></span>| <span data-ttu-id="f38f1-119">Definierar miljövariabeln som konfigureras.</span><span class="sxs-lookup"><span data-stu-id="f38f1-119">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="f38f1-120">Den här egenskapen **$true** om variabeln är den **sökväg** variabeln, annars inställd på **$false**.</span><span class="sxs-lookup"><span data-stu-id="f38f1-120">Set this property to **$true** if the variable is the **Path** variable; otherwise, set it to **$false**.</span></span> <span data-ttu-id="f38f1-121">Standardvärdet är **$false**.</span><span class="sxs-lookup"><span data-stu-id="f38f1-121">The default is **$false**.</span></span> <span data-ttu-id="f38f1-122">Om variabeln som konfigureras är den **sökväg** variabel, värdet tillhandahålls via den **värdet** egenskap läggs till det befintliga värdet.</span><span class="sxs-lookup"><span data-stu-id="f38f1-122">If the variable being configured is the **Path** variable, the value provided through the **Value** property will be appended to the existing value.</span></span>| 
| <span data-ttu-id="f38f1-123">dependsOn</span><span class="sxs-lookup"><span data-stu-id="f38f1-123">DependsOn</span></span> | <span data-ttu-id="f38f1-124">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="f38f1-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f38f1-125">Till exempel om den **ID** resursens configuration skriptblock som du vill köra först är **ResourceName** och dess typ är **ResourceType**, syntaxen för detta Egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="f38f1-125">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="additional-information"></a><span data-ttu-id="f38f1-126">Ytterligare information</span><span class="sxs-lookup"><span data-stu-id="f38f1-126">Additional Information</span></span>

* <span data-ttu-id="f38f1-127">Om **sökväg** saknas eller är inställd på **$false**, miljövariabler hanteras i `/etc/environment`.</span><span class="sxs-lookup"><span data-stu-id="f38f1-127">If **Path** is absent or set to **$false**, environment variables are managed in `/etc/environment`.</span></span> <span data-ttu-id="f38f1-128">Ditt program eller skript som kan kräva konfiguration till källa den `/etc/environment` filen åtkomst till hanterade miljövariablerna.</span><span class="sxs-lookup"><span data-stu-id="f38f1-128">Your programs or scripts may require configuration to source the `/etc/environment` file to access the managed environment variables.</span></span>
* <span data-ttu-id="f38f1-129">Om **sökväg** är inställd på **$true**, miljövariabeln hanteras i filen `/etc/profile.d/DSCenvironment.sh`.</span><span class="sxs-lookup"><span data-stu-id="f38f1-129">If **Path** is set to **$true**, the environment variable is managed in the file `/etc/profile.d/DSCenvironment.sh`.</span></span> <span data-ttu-id="f38f1-130">Den här filen kommer att skapas om den inte finns.</span><span class="sxs-lookup"><span data-stu-id="f38f1-130">This file will be created if it does not exist.</span></span> <span data-ttu-id="f38f1-131">Om **Kontrollera** anges till ”saknas” och **sökväg** är inställd på **$true**, en befintlig miljövariabel endast tas bort från `/etc/profile.d/DSCenvironment.sh` och inte från andra filer.</span><span class="sxs-lookup"><span data-stu-id="f38f1-131">If **Ensure** is set to "Absent" and **Path** is set to **$true**, an existing environment variable will only be removed from `/etc/profile.d/DSCenvironment.sh` and not from other files.</span></span>

## <a name="example"></a><span data-ttu-id="f38f1-132">Exempel</span><span class="sxs-lookup"><span data-stu-id="f38f1-132">Example</span></span>

<span data-ttu-id="f38f1-133">I följande exempel visas hur du använder den **nxEnvironment** resurs så att **TestEnvironmentVariable** finns och har värdet ”Test-värde”.</span><span class="sxs-lookup"><span data-stu-id="f38f1-133">The following example shows how to use the **nxEnvironment** resource to ensure that **TestEnvironmentVariable** is present and has the value "Test-Value".</span></span> <span data-ttu-id="f38f1-134">Om **TestEnvironmentVariable** är inte finns, skapas den.</span><span class="sxs-lookup"><span data-stu-id="f38f1-134">If **TestEnvironmentVariable** is not present, it will be created.</span></span>

```
Import-DSCResource -Module nx 


nxEnvironment EnvironmentExample
{
    Ensure = “Present”
    Name = “TestEnvironmentVariable”
    Value = “TestValue”
}
```


