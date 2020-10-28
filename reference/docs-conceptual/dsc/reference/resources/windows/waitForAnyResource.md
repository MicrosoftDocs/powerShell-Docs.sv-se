---
ms.date: 07/16/2020
ms.topic: reference
title: DSC WaitForAny-resurs
description: DSC WaitForAny-resurs
ms.openlocfilehash: dde54d8169a66012ad3b5be967b981eaa486b2bd
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656683"
---
# <a name="dsc-waitforany-resource"></a><span data-ttu-id="ee343-103">DSC WaitForAny-resurs</span><span class="sxs-lookup"><span data-stu-id="ee343-103">DSC WaitForAny Resource</span></span>

> <span data-ttu-id="ee343-104">Gäller för: Windows PowerShell 5,1</span><span class="sxs-lookup"><span data-stu-id="ee343-104">Applies To: Windows PowerShell 5.1</span></span>

<span data-ttu-id="ee343-105">Du kan använda den **WAITFORANY** DSC-resursen (Desired State Configuration) i ett Node-block i en [DSC-konfiguration](../../../configurations/configurations.md) för att ange beroenden för konfigurationer på andra noder.</span><span class="sxs-lookup"><span data-stu-id="ee343-105">The **WaitForAny** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="ee343-106">Den här resursen slutförs om resursen som anges av egenskapen **resourceName** är i önskat tillstånd på alla målnod som definierats i egenskapen **nodnamn** .</span><span class="sxs-lookup"><span data-stu-id="ee343-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on any target nodes defined in the **NodeName** property.</span></span>

> [!NOTE]
> <span data-ttu-id="ee343-107">**WaitForAny** -resursen använder Windows Remote Management för att kontrol lera status för andra noder.</span><span class="sxs-lookup"><span data-stu-id="ee343-107">**WaitForAny** resource uses Windows Remote Management to check the state of other Nodes.</span></span> <span data-ttu-id="ee343-108">Mer information om port-och säkerhets krav för WinRM finns i [säkerhets överväganden för PowerShell-fjärrkommunikation](/powershell/scripting/learn/remoting/winrmsecurity).</span><span class="sxs-lookup"><span data-stu-id="ee343-108">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity).</span></span>

## <a name="syntax"></a><span data-ttu-id="ee343-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="ee343-109">Syntax</span></span>

```Syntax
WaitForAny [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string[]]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ]
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="ee343-110">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="ee343-110">Properties</span></span>

|<span data-ttu-id="ee343-111">Egenskap</span><span class="sxs-lookup"><span data-stu-id="ee343-111">Property</span></span> |<span data-ttu-id="ee343-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ee343-112">Description</span></span> |
|---|---|
|<span data-ttu-id="ee343-113">ResourceName</span><span class="sxs-lookup"><span data-stu-id="ee343-113">ResourceName</span></span> |<span data-ttu-id="ee343-114">Resurs namnet som är beroende av.</span><span class="sxs-lookup"><span data-stu-id="ee343-114">The resource name to depend on.</span></span> <span data-ttu-id="ee343-115">Om den här resursen tillhör en annan konfiguration formaterar du namnet som `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]` .</span><span class="sxs-lookup"><span data-stu-id="ee343-115">If this resource belongs to a different configuration, format the name as `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`.</span></span> |
|<span data-ttu-id="ee343-116">NodeName</span><span class="sxs-lookup"><span data-stu-id="ee343-116">NodeName</span></span> |<span data-ttu-id="ee343-117">Målvärdena för resursen som är beroende av.</span><span class="sxs-lookup"><span data-stu-id="ee343-117">The target nodes of the resource to depend on.</span></span> |
|<span data-ttu-id="ee343-118">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="ee343-118">RetryIntervalSec</span></span> |<span data-ttu-id="ee343-119">Antalet sekunder innan nytt försök.</span><span class="sxs-lookup"><span data-stu-id="ee343-119">The number of seconds before retrying.</span></span> <span data-ttu-id="ee343-120">Minimivärdet är 1.</span><span class="sxs-lookup"><span data-stu-id="ee343-120">Minimum is 1.</span></span> |
|<span data-ttu-id="ee343-121">RetryCount</span><span class="sxs-lookup"><span data-stu-id="ee343-121">RetryCount</span></span> |<span data-ttu-id="ee343-122">Det maximala antalet försök att försöka igen.</span><span class="sxs-lookup"><span data-stu-id="ee343-122">The maximum number of times to retry.</span></span> |
|<span data-ttu-id="ee343-123">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="ee343-123">ThrottleLimit</span></span> |<span data-ttu-id="ee343-124">Antal datorer som ska anslutas samtidigt.</span><span class="sxs-lookup"><span data-stu-id="ee343-124">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="ee343-125">Standardvärdet är `New-CimSession` standard.</span><span class="sxs-lookup"><span data-stu-id="ee343-125">Default is `New-CimSession` default.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="ee343-126">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="ee343-126">Common properties</span></span>

|<span data-ttu-id="ee343-127">Egenskap</span><span class="sxs-lookup"><span data-stu-id="ee343-127">Property</span></span> |<span data-ttu-id="ee343-128">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ee343-128">Description</span></span> |
|---|---|
|<span data-ttu-id="ee343-129">DependsOn</span><span class="sxs-lookup"><span data-stu-id="ee343-129">DependsOn</span></span> |<span data-ttu-id="ee343-130">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="ee343-130">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="ee343-131">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="ee343-131">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="ee343-132">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="ee343-132">PsDscRunAsCredential</span></span> |<span data-ttu-id="ee343-133">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="ee343-133">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="ee343-134">Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="ee343-134">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="ee343-135">Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="ee343-135">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="ee343-136">Exempel</span><span class="sxs-lookup"><span data-stu-id="ee343-136">Example</span></span>

<span data-ttu-id="ee343-137">Ett exempel på hur du använder den här resursen finns i [ange beroenden mellan noder](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="ee343-137">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
