---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "Resurs för DSC-WindowsFeature"
ms.openlocfilehash: b4f50cb9ee172600b1811175e9cf67f6a7ed2d55
ms.sourcegitcommit: cd5a1f054cbf9eb95c5242a995f9741e031ddb24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/28/2017
---
# <a name="dsc-windowsfeature-resource"></a><span data-ttu-id="0ba93-103">Resurs för DSC-WindowsFeature</span><span class="sxs-lookup"><span data-stu-id="0ba93-103">DSC WindowsFeature Resource</span></span>

> <span data-ttu-id="0ba93-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0ba93-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="0ba93-105">Den **WindowsFeature** resurs i Windows PowerShell önskad tillstånd Configuration (DSC) tillhandahåller en mekanism för att säkerställa att roller och funktioner läggs till eller tas bort på målnoden.</span><span class="sxs-lookup"><span data-stu-id="0ba93-105">The **WindowsFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="0ba93-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="0ba93-106">Syntax</span></span>

```
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Source = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="0ba93-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="0ba93-107">Properties</span></span>

|  <span data-ttu-id="0ba93-108">Egenskap</span><span class="sxs-lookup"><span data-stu-id="0ba93-108">Property</span></span>  |  <span data-ttu-id="0ba93-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0ba93-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="0ba93-110">Namn</span><span class="sxs-lookup"><span data-stu-id="0ba93-110">Name</span></span>| <span data-ttu-id="0ba93-111">Anger namnet på rollen eller funktionen som du vill kontrollera läggs till eller tas bort.</span><span class="sxs-lookup"><span data-stu-id="0ba93-111">Indicates the name of the role or feature that you want to ensure is added or removed.</span></span> <span data-ttu-id="0ba93-112">Det här är samma som den __namn__ egenskap från den [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet, och inte visningsnamnet för rollen eller funktionen.</span><span class="sxs-lookup"><span data-stu-id="0ba93-112">This is the same as the __Name__ property from the [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet, and not the display name of the role or feature.</span></span>| 
| <span data-ttu-id="0ba93-113">autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="0ba93-113">Credential</span></span>| <span data-ttu-id="0ba93-114">Anger autentiseringsuppgifter som ska användas för att lägga till eller ta bort roll eller funktion.</span><span class="sxs-lookup"><span data-stu-id="0ba93-114">Indicates the credentials to use to add or remove the role or feature.</span></span>| 
| <span data-ttu-id="0ba93-115">Se till att</span><span class="sxs-lookup"><span data-stu-id="0ba93-115">Ensure</span></span>| <span data-ttu-id="0ba93-116">Anger om rollen eller funktionen har lagts till.</span><span class="sxs-lookup"><span data-stu-id="0ba93-116">Indicates if the role or feature is added.</span></span> <span data-ttu-id="0ba93-117">Se till att rollen eller funktionen lagts till, Ställ in den här egenskapen till ”finns” för att se till att rollen eller funktionen bort, egenskapen till ”saknas”.</span><span class="sxs-lookup"><span data-stu-id="0ba93-117">To ensure that the role or feature is added, set this property to "Present" To ensure that the role or feature is removed, set the property to "Absent".</span></span>| 
| <span data-ttu-id="0ba93-118">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="0ba93-118">IncludeAllSubFeature</span></span>| <span data-ttu-id="0ba93-119">Den här egenskapen __$true__ att kontrollera tillståndet för alla obligatoriska underfunktioner med tillståndet för funktionen som anges med den __namn__ egenskapen.</span><span class="sxs-lookup"><span data-stu-id="0ba93-119">Set this property to __$true__ to ensure the state of all required subfeatures with the state of the feature you specify with the __Name__ property.</span></span>| 
| <span data-ttu-id="0ba93-120">LogPath</span><span class="sxs-lookup"><span data-stu-id="0ba93-120">LogPath</span></span>| <span data-ttu-id="0ba93-121">Anger sökvägen till en loggfil där du vill att resursprovidern att logga in igen.</span><span class="sxs-lookup"><span data-stu-id="0ba93-121">Indicates the path to a log file where you want the resource provider to log the operation.</span></span>| 
| <span data-ttu-id="0ba93-122">dependsOn</span><span class="sxs-lookup"><span data-stu-id="0ba93-122">DependsOn</span></span>| <span data-ttu-id="0ba93-123">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="0ba93-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="0ba93-124">Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis __ResourceName__ och dess typ är __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="0ba93-124">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
| <span data-ttu-id="0ba93-125">Källa</span><span class="sxs-lookup"><span data-stu-id="0ba93-125">Source</span></span>| <span data-ttu-id="0ba93-126">Anger platsen för källfilen för installationen, om det behövs.</span><span class="sxs-lookup"><span data-stu-id="0ba93-126">Indicates the location of the source file to use for installation, if necessary.</span></span>| 

## <a name="example"></a><span data-ttu-id="0ba93-127">Exempel</span><span class="sxs-lookup"><span data-stu-id="0ba93-127">Example</span></span>
```powershell
WindowsFeature RoleExample
{
    Ensure = "Present" 
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature  
}
```

