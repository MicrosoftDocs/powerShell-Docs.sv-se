---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC för Linux nxService-resurs
ms.openlocfilehash: 6bb58796c4deff1153f932f61c328d84f8c4d2ca
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71942568"
---
# <a name="dsc-for-linux-nxservice-resource"></a><span data-ttu-id="026e0-103">DSC för Linux nxService-resurs</span><span class="sxs-lookup"><span data-stu-id="026e0-103">DSC for Linux nxService Resource</span></span>

<span data-ttu-id="026e0-104">**NxService** -resursen i PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera tjänster på en Linux-nod.</span><span class="sxs-lookup"><span data-stu-id="026e0-104">The **nxService** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="026e0-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="026e0-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="026e0-106">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="026e0-106">Properties</span></span>

|<span data-ttu-id="026e0-107">Egenskap</span><span class="sxs-lookup"><span data-stu-id="026e0-107">Property</span></span> |<span data-ttu-id="026e0-108">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="026e0-108">Description</span></span> |
|---|---|
|<span data-ttu-id="026e0-109">Name</span><span class="sxs-lookup"><span data-stu-id="026e0-109">Name</span></span> |<span data-ttu-id="026e0-110">Namnet på tjänsten/daemon som ska konfigureras.</span><span class="sxs-lookup"><span data-stu-id="026e0-110">The name of the service/daemon to configure.</span></span> |
|<span data-ttu-id="026e0-111">Domänkontrollant</span><span class="sxs-lookup"><span data-stu-id="026e0-111">Controller</span></span> |<span data-ttu-id="026e0-112">Typ av tjänst kontrollant som ska användas när tjänsten konfigureras.</span><span class="sxs-lookup"><span data-stu-id="026e0-112">The type of service controller to use when configuring the service.</span></span> |
|<span data-ttu-id="026e0-113">Enabled</span><span class="sxs-lookup"><span data-stu-id="026e0-113">Enabled</span></span> |<span data-ttu-id="026e0-114">Anger om tjänsten startar vid start.</span><span class="sxs-lookup"><span data-stu-id="026e0-114">Indicates whether the service starts on boot.</span></span> |
|<span data-ttu-id="026e0-115">Status</span><span class="sxs-lookup"><span data-stu-id="026e0-115">State</span></span> |<span data-ttu-id="026e0-116">Anger om tjänsten körs.</span><span class="sxs-lookup"><span data-stu-id="026e0-116">Indicates whether the service is running.</span></span> <span data-ttu-id="026e0-117">Ange att den här egenskapen ska **stoppas** för att säkerställa att tjänsten inte körs.</span><span class="sxs-lookup"><span data-stu-id="026e0-117">Set this property to **Stopped** to ensure that the service is not running.</span></span> <span data-ttu-id="026e0-118">Ange att den ska **köras** för att säkerställa att tjänsten körs.</span><span class="sxs-lookup"><span data-stu-id="026e0-118">Set it to **Running** to ensure that the service is running.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="026e0-119">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="026e0-119">Common properties</span></span>

|<span data-ttu-id="026e0-120">Egenskap</span><span class="sxs-lookup"><span data-stu-id="026e0-120">Property</span></span> |<span data-ttu-id="026e0-121">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="026e0-121">Description</span></span> |
|---|---|
|<span data-ttu-id="026e0-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="026e0-122">DependsOn</span></span> |<span data-ttu-id="026e0-123">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="026e0-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="026e0-124">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är `DependsOn = "[ResourceType]ResourceName"`syntaxen för att använda den här egenskapen.</span><span class="sxs-lookup"><span data-stu-id="026e0-124">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |

## <a name="additional-information"></a><span data-ttu-id="026e0-125">Ytterligare information</span><span class="sxs-lookup"><span data-stu-id="026e0-125">Additional Information</span></span>

<span data-ttu-id="026e0-126">**NxService** -resursen skapar inte någon tjänst definition eller ett skript för tjänsten om den inte finns.</span><span class="sxs-lookup"><span data-stu-id="026e0-126">The **nxService** resource will not create a service definition or script for the service if it does not exist.</span></span> <span data-ttu-id="026e0-127">Du kan använda PowerShell- **nxFile** resurs resurs för att hantera förekomst eller innehåll i tjänst definitions filen eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="026e0-127">You can use the PowerShell Desired State Configuration **nxFile** Resource resource to manage the existence or contents of the service definition file or script.</span></span>

## <a name="example"></a><span data-ttu-id="026e0-128">Exempel</span><span class="sxs-lookup"><span data-stu-id="026e0-128">Example</span></span>

<span data-ttu-id="026e0-129">I följande exempel visas konfigurationen av tjänsten "httpd" (för Apache HTTP-server) som är registrerad hos **system** tjänst hanteraren.</span><span class="sxs-lookup"><span data-stu-id="026e0-129">The following example shows configuration of the 'httpd' service (for Apache HTTP Server), registered with the **SystemD** service controller.</span></span>

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