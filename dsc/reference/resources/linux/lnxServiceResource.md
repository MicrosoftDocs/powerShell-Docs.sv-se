---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC för Linux nxService-resurs
ms.openlocfilehash: 6bb58796c4deff1153f932f61c328d84f8c4d2ca
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71324645"
---
# <a name="dsc-for-linux-nxservice-resource"></a><span data-ttu-id="7f20d-103">DSC för Linux nxService-resurs</span><span class="sxs-lookup"><span data-stu-id="7f20d-103">DSC for Linux nxService Resource</span></span>

<span data-ttu-id="7f20d-104">**NxService** -resursen i PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera tjänster på en Linux-nod.</span><span class="sxs-lookup"><span data-stu-id="7f20d-104">The **nxService** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="7f20d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7f20d-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="7f20d-106">properties</span><span class="sxs-lookup"><span data-stu-id="7f20d-106">Properties</span></span>

|<span data-ttu-id="7f20d-107">Egenskap</span><span class="sxs-lookup"><span data-stu-id="7f20d-107">Property</span></span> |<span data-ttu-id="7f20d-108">Description</span><span class="sxs-lookup"><span data-stu-id="7f20d-108">Description</span></span> |
|---|---|
|<span data-ttu-id="7f20d-109">Name</span><span class="sxs-lookup"><span data-stu-id="7f20d-109">Name</span></span> |<span data-ttu-id="7f20d-110">Namnet på tjänsten/daemon som ska konfigureras.</span><span class="sxs-lookup"><span data-stu-id="7f20d-110">The name of the service/daemon to configure.</span></span> |
|<span data-ttu-id="7f20d-111">Domänkontrollant</span><span class="sxs-lookup"><span data-stu-id="7f20d-111">Controller</span></span> |<span data-ttu-id="7f20d-112">Typ av tjänst kontrollant som ska användas när tjänsten konfigureras.</span><span class="sxs-lookup"><span data-stu-id="7f20d-112">The type of service controller to use when configuring the service.</span></span> |
|<span data-ttu-id="7f20d-113">Aktiverad</span><span class="sxs-lookup"><span data-stu-id="7f20d-113">Enabled</span></span> |<span data-ttu-id="7f20d-114">Anger om tjänsten startar vid start.</span><span class="sxs-lookup"><span data-stu-id="7f20d-114">Indicates whether the service starts on boot.</span></span> |
|<span data-ttu-id="7f20d-115">State</span><span class="sxs-lookup"><span data-stu-id="7f20d-115">State</span></span> |<span data-ttu-id="7f20d-116">Anger om tjänsten körs.</span><span class="sxs-lookup"><span data-stu-id="7f20d-116">Indicates whether the service is running.</span></span> <span data-ttu-id="7f20d-117">Ange att den här egenskapen ska **stoppas** för att säkerställa att tjänsten inte körs.</span><span class="sxs-lookup"><span data-stu-id="7f20d-117">Set this property to **Stopped** to ensure that the service is not running.</span></span> <span data-ttu-id="7f20d-118">Ange att den ska **köras** för att säkerställa att tjänsten körs.</span><span class="sxs-lookup"><span data-stu-id="7f20d-118">Set it to **Running** to ensure that the service is running.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="7f20d-119">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="7f20d-119">Common properties</span></span>

|<span data-ttu-id="7f20d-120">Egenskap</span><span class="sxs-lookup"><span data-stu-id="7f20d-120">Property</span></span> |<span data-ttu-id="7f20d-121">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7f20d-121">Description</span></span> |
|---|---|
|<span data-ttu-id="7f20d-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="7f20d-122">DependsOn</span></span> |<span data-ttu-id="7f20d-123">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="7f20d-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7f20d-124">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är `DependsOn = "[ResourceType]ResourceName"`syntaxen för att använda den här egenskapen.</span><span class="sxs-lookup"><span data-stu-id="7f20d-124">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |

## <a name="additional-information"></a><span data-ttu-id="7f20d-125">Ytterligare information</span><span class="sxs-lookup"><span data-stu-id="7f20d-125">Additional Information</span></span>

<span data-ttu-id="7f20d-126">**NxService** -resursen skapar inte någon tjänst definition eller ett skript för tjänsten om den inte finns.</span><span class="sxs-lookup"><span data-stu-id="7f20d-126">The **nxService** resource will not create a service definition or script for the service if it does not exist.</span></span> <span data-ttu-id="7f20d-127">Du kan använda PowerShell- **nxFile** resurs resurs för att hantera förekomst eller innehåll i tjänst definitions filen eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="7f20d-127">You can use the PowerShell Desired State Configuration **nxFile** Resource resource to manage the existence or contents of the service definition file or script.</span></span>

## <a name="example"></a><span data-ttu-id="7f20d-128">Exempel</span><span class="sxs-lookup"><span data-stu-id="7f20d-128">Example</span></span>

<span data-ttu-id="7f20d-129">I följande exempel visas konfigurationen av tjänsten "httpd" (för Apache HTTP-server) som är registrerad hos **system** tjänst hanteraren.</span><span class="sxs-lookup"><span data-stu-id="7f20d-129">The following example shows configuration of the 'httpd' service (for Apache HTTP Server), registered with the **SystemD** service controller.</span></span>

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