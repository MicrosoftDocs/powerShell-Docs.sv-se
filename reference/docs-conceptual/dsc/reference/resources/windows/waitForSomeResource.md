---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC WaitForSome-resurs
ms.openlocfilehash: 91589c84518a2bd0f4816d11aa011dec1d5305e1
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71941266"
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="cd0c5-103">DSC WaitForSome-resurs</span><span class="sxs-lookup"><span data-stu-id="cd0c5-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="cd0c5-104">Gäller för: Windows PowerShell 5. x</span><span class="sxs-lookup"><span data-stu-id="cd0c5-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="cd0c5-105">Du kan använda den **WAITFORSOME** DSC-resursen (Desired State Configuration) i ett Node-block i en [DSC-konfiguration](../../../configurations/configurations.md) för att ange beroenden för konfigurationer på andra noder.</span><span class="sxs-lookup"><span data-stu-id="cd0c5-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="cd0c5-106">Den här resursen slutförs om resursen som anges av egenskapen **resourceName** har önskat tillstånd på ett minsta antal noder (anges av **NodeCount**) som definieras av egenskapen **nodnamn** .</span><span class="sxs-lookup"><span data-stu-id="cd0c5-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

> [!NOTE]
> <span data-ttu-id="cd0c5-107">**WaitForSome** -resursen använder Windows Remote Management för att kontrol lera status för andra noder.</span><span class="sxs-lookup"><span data-stu-id="cd0c5-107">**WaitForSome** resource uses Windows Remote Management to check the state of other Nodes.</span></span> <span data-ttu-id="cd0c5-108">Mer information om port-och säkerhets krav för WinRM finns i [säkerhets överväganden för PowerShell-fjärrkommunikation](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="cd0c5-108">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="syntax"></a><span data-ttu-id="cd0c5-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="cd0c5-109">Syntax</span></span>

```Syntax
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [ RetryCount = [UInt32] ]
    [ RetryIntervalSec = [UInt64] ]
    [ ThrottleLimit = [UInt32] ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="cd0c5-110">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="cd0c5-110">Properties</span></span>

|<span data-ttu-id="cd0c5-111">Egenskap</span><span class="sxs-lookup"><span data-stu-id="cd0c5-111">Property</span></span> |<span data-ttu-id="cd0c5-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="cd0c5-112">Description</span></span> |
|---|---|
|<span data-ttu-id="cd0c5-113">NodeCount</span><span class="sxs-lookup"><span data-stu-id="cd0c5-113">NodeCount</span></span> |<span data-ttu-id="cd0c5-114">Det minsta antalet noder som måste ha önskat tillstånd för att resursen ska lyckas.</span><span class="sxs-lookup"><span data-stu-id="cd0c5-114">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span> |
|<span data-ttu-id="cd0c5-115">NodeName</span><span class="sxs-lookup"><span data-stu-id="cd0c5-115">NodeName</span></span> |<span data-ttu-id="cd0c5-116">Målvärdena för resursen som är beroende av.</span><span class="sxs-lookup"><span data-stu-id="cd0c5-116">The target nodes of the resource to depend on.</span></span> |
|<span data-ttu-id="cd0c5-117">ResourceName</span><span class="sxs-lookup"><span data-stu-id="cd0c5-117">ResourceName</span></span> |<span data-ttu-id="cd0c5-118">Resurs namnet som är beroende av.</span><span class="sxs-lookup"><span data-stu-id="cd0c5-118">The resource name to depend on.</span></span> <span data-ttu-id="cd0c5-119">Om den här resursen tillhör en annan konfiguration formaterar du namnet som `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`.</span><span class="sxs-lookup"><span data-stu-id="cd0c5-119">If this resource belongs to a different configuration, format the name as `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`.</span></span> |
|<span data-ttu-id="cd0c5-120">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="cd0c5-120">RetryIntervalSec</span></span> |<span data-ttu-id="cd0c5-121">Antalet sekunder innan nytt försök.</span><span class="sxs-lookup"><span data-stu-id="cd0c5-121">The number of seconds before retrying.</span></span> <span data-ttu-id="cd0c5-122">Minimivärdet är 1.</span><span class="sxs-lookup"><span data-stu-id="cd0c5-122">Minimum is 1.</span></span> |
|<span data-ttu-id="cd0c5-123">RetryCount</span><span class="sxs-lookup"><span data-stu-id="cd0c5-123">RetryCount</span></span> |<span data-ttu-id="cd0c5-124">Det maximala antalet försök att försöka igen.</span><span class="sxs-lookup"><span data-stu-id="cd0c5-124">The maximum number of times to retry.</span></span> |
|<span data-ttu-id="cd0c5-125">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="cd0c5-125">ThrottleLimit</span></span> |<span data-ttu-id="cd0c5-126">Antal datorer som ska anslutas samtidigt.</span><span class="sxs-lookup"><span data-stu-id="cd0c5-126">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="cd0c5-127">Standardvärdet är `New-CimSession` standard.</span><span class="sxs-lookup"><span data-stu-id="cd0c5-127">Default is `New-CimSession` default.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="cd0c5-128">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="cd0c5-128">Common properties</span></span>

|<span data-ttu-id="cd0c5-129">Egenskap</span><span class="sxs-lookup"><span data-stu-id="cd0c5-129">Property</span></span> |<span data-ttu-id="cd0c5-130">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="cd0c5-130">Description</span></span> |
|---|---|
|<span data-ttu-id="cd0c5-131">DependsOn</span><span class="sxs-lookup"><span data-stu-id="cd0c5-131">DependsOn</span></span> |<span data-ttu-id="cd0c5-132">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="cd0c5-132">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="cd0c5-133">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är `DependsOn = "[ResourceType]ResourceName"`syntaxen för att använda den här egenskapen.</span><span class="sxs-lookup"><span data-stu-id="cd0c5-133">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="cd0c5-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="cd0c5-134">PsDscRunAsCredential</span></span> |<span data-ttu-id="cd0c5-135">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="cd0c5-135">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="cd0c5-136">Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="cd0c5-136">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="cd0c5-137">Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="cd0c5-137">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="cd0c5-138">Exempel</span><span class="sxs-lookup"><span data-stu-id="cd0c5-138">Example</span></span>

<span data-ttu-id="cd0c5-139">Ett exempel på hur du använder den här resursen finns i [ange beroenden mellan noder](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="cd0c5-139">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>