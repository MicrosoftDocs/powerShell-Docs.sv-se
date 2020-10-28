---
ms.date: 07/17/2020
ms.topic: reference
title: DSC för Linux nxService-resurs
description: DSC för Linux nxService-resurs
ms.openlocfilehash: 4eefe491c491c9245732def1cc85260f368ef9e1
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648795"
---
# <a name="dsc-for-linux-nxservice-resource"></a><span data-ttu-id="2e0e3-103">DSC för Linux nxService-resurs</span><span class="sxs-lookup"><span data-stu-id="2e0e3-103">DSC for Linux nxService Resource</span></span>

<span data-ttu-id="2e0e3-104">**NxService** -resursen i PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera tjänster på en Linux-nod.</span><span class="sxs-lookup"><span data-stu-id="2e0e3-104">The **nxService** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="2e0e3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="2e0e3-105">Syntax</span></span>

```Syntax
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd } ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="2e0e3-106">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="2e0e3-106">Properties</span></span>

|<span data-ttu-id="2e0e3-107">Egenskap</span><span class="sxs-lookup"><span data-stu-id="2e0e3-107">Property</span></span> |<span data-ttu-id="2e0e3-108">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2e0e3-108">Description</span></span> |
|---|---|
|<span data-ttu-id="2e0e3-109">Namn</span><span class="sxs-lookup"><span data-stu-id="2e0e3-109">Name</span></span> |<span data-ttu-id="2e0e3-110">Namnet på tjänsten/daemon som ska konfigureras.</span><span class="sxs-lookup"><span data-stu-id="2e0e3-110">The name of the service/daemon to configure.</span></span> |
|<span data-ttu-id="2e0e3-111">Domänkontrollant</span><span class="sxs-lookup"><span data-stu-id="2e0e3-111">Controller</span></span> |<span data-ttu-id="2e0e3-112">Typ av tjänst kontrollant som ska användas när tjänsten konfigureras.</span><span class="sxs-lookup"><span data-stu-id="2e0e3-112">The type of service controller to use when configuring the service.</span></span> |
|<span data-ttu-id="2e0e3-113">Enabled</span><span class="sxs-lookup"><span data-stu-id="2e0e3-113">Enabled</span></span> |<span data-ttu-id="2e0e3-114">Anger om tjänsten startar vid start.</span><span class="sxs-lookup"><span data-stu-id="2e0e3-114">Indicates whether the service starts on boot.</span></span> |
|<span data-ttu-id="2e0e3-115">Tillstånd</span><span class="sxs-lookup"><span data-stu-id="2e0e3-115">State</span></span> |<span data-ttu-id="2e0e3-116">Anger om tjänsten körs.</span><span class="sxs-lookup"><span data-stu-id="2e0e3-116">Indicates whether the service is running.</span></span> <span data-ttu-id="2e0e3-117">Ange att den här egenskapen ska **stoppas** för att säkerställa att tjänsten inte körs.</span><span class="sxs-lookup"><span data-stu-id="2e0e3-117">Set this property to **Stopped** to ensure that the service is not running.</span></span> <span data-ttu-id="2e0e3-118">Ange att den ska **köras** för att säkerställa att tjänsten körs.</span><span class="sxs-lookup"><span data-stu-id="2e0e3-118">Set it to **Running** to ensure that the service is running.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="2e0e3-119">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="2e0e3-119">Common properties</span></span>

|<span data-ttu-id="2e0e3-120">Egenskap</span><span class="sxs-lookup"><span data-stu-id="2e0e3-120">Property</span></span> |<span data-ttu-id="2e0e3-121">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2e0e3-121">Description</span></span> |
|---|---|
|<span data-ttu-id="2e0e3-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="2e0e3-122">DependsOn</span></span> |<span data-ttu-id="2e0e3-123">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="2e0e3-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="2e0e3-124">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="2e0e3-124">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |

## <a name="additional-information"></a><span data-ttu-id="2e0e3-125">Ytterligare information</span><span class="sxs-lookup"><span data-stu-id="2e0e3-125">Additional Information</span></span>

<span data-ttu-id="2e0e3-126">**NxService** -resursen skapar inte någon tjänst definition eller ett skript för tjänsten om den inte finns.</span><span class="sxs-lookup"><span data-stu-id="2e0e3-126">The **nxService** resource will not create a service definition or script for the service if it does not exist.</span></span> <span data-ttu-id="2e0e3-127">Du kan använda PowerShell- **nxFile** resurs resurs för att hantera förekomst eller innehåll i tjänst definitions filen eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="2e0e3-127">You can use the PowerShell Desired State Configuration **nxFile** Resource resource to manage the existence or contents of the service definition file or script.</span></span>

## <a name="example"></a><span data-ttu-id="2e0e3-128">Exempel</span><span class="sxs-lookup"><span data-stu-id="2e0e3-128">Example</span></span>

<span data-ttu-id="2e0e3-129">I följande exempel visas konfigurationen av tjänsten "httpd" (för Apache HTTP-server) som är registrerad hos **system** tjänst hanteraren.</span><span class="sxs-lookup"><span data-stu-id="2e0e3-129">The following example shows configuration of the 'httpd' service (for Apache HTTP Server), registered with the **SystemD** service controller.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
    #Apache Service
    nxService ApacheService {
        Name = 'httpd'
        State = 'running'
        Enabled = $true
        Controller = 'systemd'
    }
}
```
