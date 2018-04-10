---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC för Linux nxService resurs
ms.openlocfilehash: b02fb1153570f628682533cb57a7d429e5cc8762
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-for-linux-nxservice-resource"></a><span data-ttu-id="03cd4-103">DSC för Linux nxService resurs</span><span class="sxs-lookup"><span data-stu-id="03cd4-103">DSC for Linux nxService Resource</span></span>

<span data-ttu-id="03cd4-104">Den **nxService** resurs i PowerShell önskad tillstånd Configuration (DSC) ger dig möjlighet att hantera tjänster på en Linux-nod.</span><span class="sxs-lookup"><span data-stu-id="03cd4-104">The **nxService** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="03cd4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="03cd4-105">Syntax</span></span>

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd }  ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="03cd4-106">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="03cd4-106">Properties</span></span>
|  <span data-ttu-id="03cd4-107">Egenskap</span><span class="sxs-lookup"><span data-stu-id="03cd4-107">Property</span></span> |  <span data-ttu-id="03cd4-108">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="03cd4-108">Description</span></span> |
|---|---|
| <span data-ttu-id="03cd4-109">Namn</span><span class="sxs-lookup"><span data-stu-id="03cd4-109">Name</span></span>| <span data-ttu-id="03cd4-110">Namnet på tjänsten/daemon för att konfigurera.</span><span class="sxs-lookup"><span data-stu-id="03cd4-110">The name of the service/daemon to configure.</span></span>|
| <span data-ttu-id="03cd4-111">Domänkontrollant</span><span class="sxs-lookup"><span data-stu-id="03cd4-111">Controller</span></span>| <span data-ttu-id="03cd4-112">Typ av service controller ska använda när du konfigurerar tjänsten.</span><span class="sxs-lookup"><span data-stu-id="03cd4-112">The type of service controller to use when configuring the service.</span></span>|
| <span data-ttu-id="03cd4-113">Aktiverat</span><span class="sxs-lookup"><span data-stu-id="03cd4-113">Enabled</span></span>| <span data-ttu-id="03cd4-114">Anger om tjänsten startar vid start.</span><span class="sxs-lookup"><span data-stu-id="03cd4-114">Indicates whether the service starts on boot.</span></span>|
| <span data-ttu-id="03cd4-115">Läge</span><span class="sxs-lookup"><span data-stu-id="03cd4-115">State</span></span>| <span data-ttu-id="03cd4-116">Anger om tjänsten körs.</span><span class="sxs-lookup"><span data-stu-id="03cd4-116">Indicates whether the service is running.</span></span> <span data-ttu-id="03cd4-117">Den här egenskapen till ”Stoppad” för att se till att tjänsten inte körs.</span><span class="sxs-lookup"><span data-stu-id="03cd4-117">Set this property to "Stopped" to ensure that the service is not running.</span></span> <span data-ttu-id="03cd4-118">Ange den till ”körs” för att se till att tjänsten inte körs.</span><span class="sxs-lookup"><span data-stu-id="03cd4-118">Set it to "Running" to ensure that the service is not running.</span></span>|
| <span data-ttu-id="03cd4-119">dependsOn</span><span class="sxs-lookup"><span data-stu-id="03cd4-119">DependsOn</span></span> | <span data-ttu-id="03cd4-120">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="03cd4-120">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="03cd4-121">Till exempel om den **ID** resursens configuration skriptblock som du vill köra först är **ResourceName** och dess typ är **ResourceType**, syntaxen för detta Egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="03cd4-121">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="additional-information"></a><span data-ttu-id="03cd4-122">Ytterligare information</span><span class="sxs-lookup"><span data-stu-id="03cd4-122">Additional Information</span></span>

<span data-ttu-id="03cd4-123">Den **nxService** resursen kommer inte att skapa en tjänstdefinitionen eller ett skript för tjänsten om den inte finns.</span><span class="sxs-lookup"><span data-stu-id="03cd4-123">The **nxService** resource will not create a service definition or script for the service if it does not exist.</span></span> <span data-ttu-id="03cd4-124">Du kan använda PowerShell Desired State Configuration **nxFile** resurs resurs som ska hantera förekomsten eller innehållet i tjänstdefinitionsfilen eller skript.</span><span class="sxs-lookup"><span data-stu-id="03cd4-124">You can use the PowerShell Desired State Configuration **nxFile** Resource resource to manage the existence or contents of the service definition file or script.</span></span>

## <a name="example"></a><span data-ttu-id="03cd4-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="03cd4-125">Example</span></span>

<span data-ttu-id="03cd4-126">I följande exempel visas konfigurationen för tjänsten ”httpd” (för Apache http-Server) som registrerats med den **SystemD** tjänsthanteraren.</span><span class="sxs-lookup"><span data-stu-id="03cd4-126">The following example shows configuration of the “httpd” service (for Apache HTTP Server), registered with the **SystemD** service controller.</span></span>

```
Import-DSCResource -Module nx

Node $node {
#Apache Service
nxService ApacheService
{
Name = "httpd"
State = "running"
Enabled = $true
Controller = "systemd"
}
}
```