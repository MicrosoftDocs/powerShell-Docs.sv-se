---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC för Linux nxService-resurs
ms.openlocfilehash: fe8043995205649378725f2ab0a78e19313739c9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077701"
---
# <a name="dsc-for-linux-nxservice-resource"></a><span data-ttu-id="d1798-103">DSC för Linux nxService-resurs</span><span class="sxs-lookup"><span data-stu-id="d1798-103">DSC for Linux nxService Resource</span></span>

<span data-ttu-id="d1798-104">Den **nxService** resurs i PowerShell Desired State Configuration (DSC) är en mekanism för att hantera tjänster på en Linux-nod.</span><span class="sxs-lookup"><span data-stu-id="d1798-104">The **nxService** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="d1798-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d1798-105">Syntax</span></span>

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd } ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="d1798-106">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="d1798-106">Properties</span></span>

| <span data-ttu-id="d1798-107">Egenskap</span><span class="sxs-lookup"><span data-stu-id="d1798-107">Property</span></span> | <span data-ttu-id="d1798-108">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d1798-108">Description</span></span> |
|---|---|
| <span data-ttu-id="d1798-109">Namn</span><span class="sxs-lookup"><span data-stu-id="d1798-109">Name</span></span>| <span data-ttu-id="d1798-110">Namnet på tjänsten/daemon för att konfigurera.</span><span class="sxs-lookup"><span data-stu-id="d1798-110">The name of the service/daemon to configure.</span></span>|
| <span data-ttu-id="d1798-111">domänkontrollant</span><span class="sxs-lookup"><span data-stu-id="d1798-111">Controller</span></span>| <span data-ttu-id="d1798-112">Typ av tjänsthanteraren för att använda när du konfigurerar tjänsten.</span><span class="sxs-lookup"><span data-stu-id="d1798-112">The type of service controller to use when configuring the service.</span></span>|
| <span data-ttu-id="d1798-113">Aktiverad</span><span class="sxs-lookup"><span data-stu-id="d1798-113">Enabled</span></span>| <span data-ttu-id="d1798-114">Anger om tjänsten startar vid start.</span><span class="sxs-lookup"><span data-stu-id="d1798-114">Indicates whether the service starts on boot.</span></span>|
| <span data-ttu-id="d1798-115">Tillstånd</span><span class="sxs-lookup"><span data-stu-id="d1798-115">State</span></span>| <span data-ttu-id="d1798-116">Anger om tjänsten körs.</span><span class="sxs-lookup"><span data-stu-id="d1798-116">Indicates whether the service is running.</span></span> <span data-ttu-id="d1798-117">Ange den här egenskapen till ”Stoppad” för att säkerställa att tjänsten inte körs.</span><span class="sxs-lookup"><span data-stu-id="d1798-117">Set this property to "Stopped" to ensure that the service is not running.</span></span> <span data-ttu-id="d1798-118">Ange den till ”körs” för att säkerställa att tjänsten inte körs.</span><span class="sxs-lookup"><span data-stu-id="d1798-118">Set it to "Running" to ensure that the service is not running.</span></span>|
| <span data-ttu-id="d1798-119">DependsOn</span><span class="sxs-lookup"><span data-stu-id="d1798-119">DependsOn</span></span> | <span data-ttu-id="d1798-120">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="d1798-120">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="d1798-121">Till exempel om den **ID** för resursen configuration-skriptblock som du vill köra först är **ResourceName** och är av typen **ResourceType**, syntaxen för detta Egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="d1798-121">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="additional-information"></a><span data-ttu-id="d1798-122">Ytterligare information</span><span class="sxs-lookup"><span data-stu-id="d1798-122">Additional Information</span></span>

<span data-ttu-id="d1798-123">Den **nxService** resurs skapar inte en tjänstdefinition eller ett skript för tjänsten om den inte finns.</span><span class="sxs-lookup"><span data-stu-id="d1798-123">The **nxService** resource will not create a service definition or script for the service if it does not exist.</span></span> <span data-ttu-id="d1798-124">Du kan använda PowerShell Desired State Configuration **nxFile** resursen att hantera förekomsten eller innehållet i tjänstdefinitionsfilen eller skript.</span><span class="sxs-lookup"><span data-stu-id="d1798-124">You can use the PowerShell Desired State Configuration **nxFile** Resource resource to manage the existence or contents of the service definition file or script.</span></span>

## <a name="example"></a><span data-ttu-id="d1798-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="d1798-125">Example</span></span>

<span data-ttu-id="d1798-126">I följande exempel visas konfigurationen för tjänsten ”httpd” (för Apache HTTP Server), som registrerats med den **SystemD** tjänsthanteraren.</span><span class="sxs-lookup"><span data-stu-id="d1798-126">The following example shows configuration of the 'httpd' service (for Apache HTTP Server), registered with the **SystemD** service controller.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node {
    #Apache Service
    nxService ApacheService {
        Name = 'httpd'
        State = 'running'
        Enabled = $true
        Controller = 'systemd'
    }
}
```