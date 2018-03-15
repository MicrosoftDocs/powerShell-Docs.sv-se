---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC ServiceSet resurs
ms.openlocfilehash: 2488dda5212ccb717f7fd5d59ad62ec135ad13d5
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/15/2018
---
# <a name="dsc-serviceset-resource"></a><span data-ttu-id="385d6-103">DSC ServiceSet resurs</span><span class="sxs-lookup"><span data-stu-id="385d6-103">DSC ServiceSet Resource</span></span>

> <span data-ttu-id="385d6-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="385d6-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="385d6-105">Den **ServiceSet** resurs i Windows PowerShell önskad tillstånd Configuration (DSC) ger dig möjlighet att hantera tjänster på målnoden.</span><span class="sxs-lookup"><span data-stu-id="385d6-105">The **ServiceSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span> <span data-ttu-id="385d6-106">Den här resursen är en [sammansatta resurs](authoringResourceComposite.md) som anropar den [tjänsten resurs](serviceResource.md) för varje tjänst som anges i den `Name` egenskapen.</span><span class="sxs-lookup"><span data-stu-id="385d6-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [Service resource](serviceResource.md) for each service specified in the `Name` property.</span></span>

<span data-ttu-id="385d6-107">Använd den här resursen när du vill konfigurera ett antal tjänster till samma tillstånd.</span><span class="sxs-lookup"><span data-stu-id="385d6-107">Use this resource when you want to configure a number of services to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="385d6-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="385d6-108">Syntax</span></span>

```
Service [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Ensure = [string] { Absent | Present }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    
}
```

## <a name="properties"></a><span data-ttu-id="385d6-109">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="385d6-109">Properties</span></span>

|  <span data-ttu-id="385d6-110">Egenskap</span><span class="sxs-lookup"><span data-stu-id="385d6-110">Property</span></span>  |  <span data-ttu-id="385d6-111">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="385d6-111">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="385d6-112">Namn</span><span class="sxs-lookup"><span data-stu-id="385d6-112">Name</span></span>| <span data-ttu-id="385d6-113">Anger tjänstnamn.</span><span class="sxs-lookup"><span data-stu-id="385d6-113">Indicates the service names.</span></span> <span data-ttu-id="385d6-114">Observera att ibland Detta skiljer sig från visningsnamnen.</span><span class="sxs-lookup"><span data-stu-id="385d6-114">Note that sometimes this is different from the display names.</span></span> <span data-ttu-id="385d6-115">Du kan hämta en lista över tjänster och deras aktuella tillstånd med den [Get-Service](https://technet.microsoft.com/library/hh849804.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="385d6-115">You can get a list of the services and their current state with the [Get-Service](https://technet.microsoft.com/library/hh849804.aspx) cmdlet.</span></span>|
| <span data-ttu-id="385d6-116">StartupType</span><span class="sxs-lookup"><span data-stu-id="385d6-116">StartupType</span></span>| <span data-ttu-id="385d6-117">Anger starttypen för tjänsten.</span><span class="sxs-lookup"><span data-stu-id="385d6-117">Indicates the startup type for the service.</span></span> <span data-ttu-id="385d6-118">De värden som tillåts för den här egenskapen är: **automatisk**, **inaktiverad**, och **manuell**</span><span class="sxs-lookup"><span data-stu-id="385d6-118">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**</span></span>|  
| <span data-ttu-id="385d6-119">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="385d6-119">BuiltInAccount</span></span>| <span data-ttu-id="385d6-120">Anger kontot du använder för tjänsterna.</span><span class="sxs-lookup"><span data-stu-id="385d6-120">Indicates the sign-in account to use for the services.</span></span> <span data-ttu-id="385d6-121">De värden som tillåts för den här egenskapen är: **LocalService**, **LocalSystem**, och **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="385d6-121">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span>| 
| <span data-ttu-id="385d6-122">Läge</span><span class="sxs-lookup"><span data-stu-id="385d6-122">State</span></span>| <span data-ttu-id="385d6-123">Visar du vill säkerställa för tjänsterna: **stoppad** eller **kör**.</span><span class="sxs-lookup"><span data-stu-id="385d6-123">Indicates the state you want to ensure for the services: **Stopped** or **Running**.</span></span>| 
| <span data-ttu-id="385d6-124">Se till att</span><span class="sxs-lookup"><span data-stu-id="385d6-124">Ensure</span></span>| <span data-ttu-id="385d6-125">Anger om tjänsterna som finns på systemet.</span><span class="sxs-lookup"><span data-stu-id="385d6-125">Indicates whether the services exist on the system.</span></span> <span data-ttu-id="385d6-126">Den här egenskapen **saknas** så att tjänsten inte finns.</span><span class="sxs-lookup"><span data-stu-id="385d6-126">Set this property to **Absent** to ensure that the services do not exist.</span></span> <span data-ttu-id="385d6-127">Ange värdet till **finns** (standardvärdet) säkerställer att mål-tjänster finns.</span><span class="sxs-lookup"><span data-stu-id="385d6-127">Setting it to **Present** (the default value) ensures that target services exist.</span></span>|
| <span data-ttu-id="385d6-128">autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="385d6-128">Credential</span></span>| <span data-ttu-id="385d6-129">Anger autentiseringsuppgifterna för kontot som tjänsten resursen kommer att köras under.</span><span class="sxs-lookup"><span data-stu-id="385d6-129">Indicates credentials for the account that the service resource will run under.</span></span> <span data-ttu-id="385d6-130">Den här egenskapen och **BuiltinAccount** egenskapen kan inte användas tillsammans.</span><span class="sxs-lookup"><span data-stu-id="385d6-130">This property and the **BuiltinAccount** property cannot be used together.</span></span>| 
| <span data-ttu-id="385d6-131">dependsOn</span><span class="sxs-lookup"><span data-stu-id="385d6-131">DependsOn</span></span>| <span data-ttu-id="385d6-132">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="385d6-132">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="385d6-133">Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis *ResourceName* och dess typ är *ResourceType*, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="385d6-133">For example, if the ID of the resource configuration script block that you want to run first is *ResourceName* and its type is *ResourceType*, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 



## <a name="example"></a><span data-ttu-id="385d6-134">Exempel</span><span class="sxs-lookup"><span data-stu-id="385d6-134">Example</span></span>

<span data-ttu-id="385d6-135">Följande konfiguration startar tjänsterna ”Windows Audio” och ”Remote Desktop Services”.</span><span class="sxs-lookup"><span data-stu-id="385d6-135">The following configuration starts the "Windows Audio" and "Remote Desktop Services" services.</span></span>

```powershell
configuration ServiceSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        ServiceSet ServiceSetExample
        {
            Name        = @("TermService", "Audiosrv")
            StartupType = "Manual"
            State       = "Running"
        } 
    }
}
```

