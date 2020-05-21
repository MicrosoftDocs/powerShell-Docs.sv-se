---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC WindowsFeature-resurs
ms.openlocfilehash: 7f9b200b4d10aef6c8a3f76c497f4d60e8062cb5
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557405"
---
# <a name="dsc-windowsfeature-resource"></a><span data-ttu-id="3bd61-103">DSC WindowsFeature-resurs</span><span class="sxs-lookup"><span data-stu-id="3bd61-103">DSC WindowsFeature Resource</span></span>

> <span data-ttu-id="3bd61-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5. x</span><span class="sxs-lookup"><span data-stu-id="3bd61-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="3bd61-105">**WindowsFeature** -resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att se till att roller och funktioner läggs till eller tas bort på en målnod.</span><span class="sxs-lookup"><span data-stu-id="3bd61-105">The **WindowsFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="3bd61-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="3bd61-106">Syntax</span></span>

```Syntax
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ Source = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="3bd61-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="3bd61-107">Properties</span></span>

|<span data-ttu-id="3bd61-108">Egenskap</span><span class="sxs-lookup"><span data-stu-id="3bd61-108">Property</span></span> |<span data-ttu-id="3bd61-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3bd61-109">Description</span></span> |
|---|---|
|<span data-ttu-id="3bd61-110">Name</span><span class="sxs-lookup"><span data-stu-id="3bd61-110">Name</span></span> |<span data-ttu-id="3bd61-111">Anger namnet på den roll eller funktion som du vill se till att den läggs till eller tas bort.</span><span class="sxs-lookup"><span data-stu-id="3bd61-111">Indicates the name of the role or feature that you want to ensure is added or removed.</span></span> <span data-ttu-id="3bd61-112">Detta är samma som egenskapen **Name** från cmdleten [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) och inte visnings namnet för rollen eller funktionen.</span><span class="sxs-lookup"><span data-stu-id="3bd61-112">This is the same as the **Name** property from the [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet, and not the display name of the role or feature.</span></span> |
|<span data-ttu-id="3bd61-113">Autentiseringsuppgift</span><span class="sxs-lookup"><span data-stu-id="3bd61-113">Credential</span></span> |<span data-ttu-id="3bd61-114">Anger de autentiseringsuppgifter som ska användas för att lägga till eller ta bort rollen eller funktionen.</span><span class="sxs-lookup"><span data-stu-id="3bd61-114">Indicates the credentials to use to add or remove the role or feature.</span></span> |
|<span data-ttu-id="3bd61-115">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="3bd61-115">IncludeAllSubFeature</span></span> |<span data-ttu-id="3bd61-116">Ange den här egenskapen till för att se till att `$true` alla nödvändiga underfunktioner har statusen för den funktion som du anger med egenskapen **Name** .</span><span class="sxs-lookup"><span data-stu-id="3bd61-116">Set this property to `$true` to ensure the state of all required subfeatures with the state of the feature you specify with the **Name** property.</span></span> |
|<span data-ttu-id="3bd61-117">LogPath</span><span class="sxs-lookup"><span data-stu-id="3bd61-117">LogPath</span></span> |<span data-ttu-id="3bd61-118">Anger sökvägen till en loggfil där du vill att resurs leverantören ska logga åtgärden.</span><span class="sxs-lookup"><span data-stu-id="3bd61-118">Indicates the path to a log file where you want the resource provider to log the operation.</span></span> |
|<span data-ttu-id="3bd61-119">Källa</span><span class="sxs-lookup"><span data-stu-id="3bd61-119">Source</span></span> |<span data-ttu-id="3bd61-120">Anger platsen för den käll fil som ska användas för installation, om det behövs.</span><span class="sxs-lookup"><span data-stu-id="3bd61-120">Indicates the location of the source file to use for installation, if necessary.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="3bd61-121">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="3bd61-121">Common properties</span></span>

|<span data-ttu-id="3bd61-122">Egenskap</span><span class="sxs-lookup"><span data-stu-id="3bd61-122">Property</span></span> |<span data-ttu-id="3bd61-123">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3bd61-123">Description</span></span> |
|---|---|
|<span data-ttu-id="3bd61-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="3bd61-124">DependsOn</span></span> |<span data-ttu-id="3bd61-125">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="3bd61-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="3bd61-126">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="3bd61-126">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="3bd61-127">Kontrol</span><span class="sxs-lookup"><span data-stu-id="3bd61-127">Ensure</span></span> |<span data-ttu-id="3bd61-128">Anger om rollen eller funktionen har lagts till.</span><span class="sxs-lookup"><span data-stu-id="3bd61-128">Indicates if the role or feature is added.</span></span> <span data-ttu-id="3bd61-129">Om du vill se till att rollen eller funktionen har lagts till ställer du in den här egenskapen som **tillgänglig**.</span><span class="sxs-lookup"><span data-stu-id="3bd61-129">To ensure that the role or feature is added, set this property to **Present**.</span></span> <span data-ttu-id="3bd61-130">För att säkerställa att rollen eller funktionen tas bort ställer du in egenskapen på **saknas**.</span><span class="sxs-lookup"><span data-stu-id="3bd61-130">To ensure that the role or feature is removed, set the property to **Absent**.</span></span> <span data-ttu-id="3bd61-131">Standardvärdet finns **.**</span><span class="sxs-lookup"><span data-stu-id="3bd61-131">The default value is **Present**.</span></span> |
|<span data-ttu-id="3bd61-132">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="3bd61-132">PsDscRunAsCredential</span></span> |<span data-ttu-id="3bd61-133">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="3bd61-133">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="3bd61-134">Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="3bd61-134">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="3bd61-135">Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="3bd61-135">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="3bd61-136">Exempel</span><span class="sxs-lookup"><span data-stu-id="3bd61-136">Example</span></span>

```powershell
WindowsFeature RoleExample
{
    Ensure = "Present"
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature
}
```
