---
ms.date: 07/16/2020
ms.topic: reference
title: DSC-logg resurs
description: DSC-logg resurs
ms.openlocfilehash: 281d1f8aeeb4d075f073419ac02a0f81888ed2b5
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142471"
---
# <a name="dsc-log-resource"></a><span data-ttu-id="aaeb8-103">DSC-logg resurs</span><span class="sxs-lookup"><span data-stu-id="aaeb8-103">DSC Log Resource</span></span>

> <span data-ttu-id="aaeb8-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5. x</span><span class="sxs-lookup"><span data-stu-id="aaeb8-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="aaeb8-105">**Logg** resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att skriva meddelanden till Microsoft-Windows-önskad tillstånds konfiguration/analytisk händelse logg.</span><span class="sxs-lookup"><span data-stu-id="aaeb8-105">The **Log** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a><span data-ttu-id="aaeb8-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="aaeb8-106">Syntax</span></span>

```Syntax
Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

> [!NOTE]
> <span data-ttu-id="aaeb8-107">Som standard är bara drift loggar för DSC aktiverade.</span><span class="sxs-lookup"><span data-stu-id="aaeb8-107">By default only the Operational logs for DSC are enabled.</span></span> <span data-ttu-id="aaeb8-108">Innan den analytiska loggen blir tillgänglig eller synlig måste den vara aktive rad.</span><span class="sxs-lookup"><span data-stu-id="aaeb8-108">Before the Analytic log will be available or visible, it must be enabled.</span></span> <span data-ttu-id="aaeb8-109">Mer information finns i [var är DSC-händelseloggar?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).</span><span class="sxs-lookup"><span data-stu-id="aaeb8-109">For more information, see [Where are DSC Event Logs?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).</span></span>

## <a name="properties"></a><span data-ttu-id="aaeb8-110">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="aaeb8-110">Properties</span></span>

| <span data-ttu-id="aaeb8-111">Egenskap</span><span class="sxs-lookup"><span data-stu-id="aaeb8-111">Property</span></span> |                                                   <span data-ttu-id="aaeb8-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="aaeb8-112">Description</span></span>                                                    |
| -------- | ---------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="aaeb8-113">Meddelande</span><span class="sxs-lookup"><span data-stu-id="aaeb8-113">Message</span></span>  | <span data-ttu-id="aaeb8-114">Anger det meddelande som du vill skriva till Microsoft-Windows-önskad tillstånds konfiguration/analytisk händelse logg.</span><span class="sxs-lookup"><span data-stu-id="aaeb8-114">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="aaeb8-115">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="aaeb8-115">Common properties</span></span>

|       <span data-ttu-id="aaeb8-116">Egenskap</span><span class="sxs-lookup"><span data-stu-id="aaeb8-116">Property</span></span>       |                                                                                                                                                          <span data-ttu-id="aaeb8-117">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="aaeb8-117">Description</span></span>                                                                                                                                                           |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <span data-ttu-id="aaeb8-118">DependsOn</span><span class="sxs-lookup"><span data-stu-id="aaeb8-118">DependsOn</span></span>            | <span data-ttu-id="aaeb8-119">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="aaeb8-119">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="aaeb8-120">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="aaeb8-120">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
| <span data-ttu-id="aaeb8-121">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="aaeb8-121">PsDscRunAsCredential</span></span> | <span data-ttu-id="aaeb8-122">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="aaeb8-122">Sets the credential for running the entire resource as.</span></span>                                                                                                                                                                                                                                                                        |

> [!NOTE]
> <span data-ttu-id="aaeb8-123">Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="aaeb8-123">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="aaeb8-124">Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="aaeb8-124">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="aaeb8-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="aaeb8-125">Example</span></span>

<span data-ttu-id="aaeb8-126">I följande exempel visas hur du inkluderar ett meddelande i Microsoft-Windows-Desired State Configuration/analytisk händelse logg.</span><span class="sxs-lookup"><span data-stu-id="aaeb8-126">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> [!NOTE]
> <span data-ttu-id="aaeb8-127">Om du kör [test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/test-dscconfiguration) med den här resursen konfigurerad kommer den alltid att returnera **$false** .</span><span class="sxs-lookup"><span data-stu-id="aaeb8-127">If you run [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/test-dscconfiguration) with this resource configured, it will always return **$false** .</span></span>

```powershell
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Log LogExample
        {
            Message = 'This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log.'
        }
    }
}
```
