---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "DSC-tjänstresurs"
ms.openlocfilehash: 611729e5d971ebaf15ac947454cffadc6797927b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-service-resource"></a><span data-ttu-id="4e751-103">DSC-tjänstresurs</span><span class="sxs-lookup"><span data-stu-id="4e751-103">DSC Service Resource</span></span>

> <span data-ttu-id="4e751-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4e751-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="4e751-105">Den **Service** resurs i Windows PowerShell önskad tillstånd Configuration (DSC) ger dig möjlighet att hantera tjänster på målnoden.</span><span class="sxs-lookup"><span data-stu-id="4e751-105">The **Service** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="4e751-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="4e751-106">Syntax</span></span>

```
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Path = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="4e751-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="4e751-107">Properties</span></span>

|  <span data-ttu-id="4e751-108">Egenskap</span><span class="sxs-lookup"><span data-stu-id="4e751-108">Property</span></span>  |  <span data-ttu-id="4e751-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4e751-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="4e751-110">Namn</span><span class="sxs-lookup"><span data-stu-id="4e751-110">Name</span></span>| <span data-ttu-id="4e751-111">Anger namnet på tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4e751-111">Indicates the service name.</span></span> <span data-ttu-id="4e751-112">Observera att ibland Detta skiljer sig från namnet.</span><span class="sxs-lookup"><span data-stu-id="4e751-112">Note that sometimes this is different from the display name.</span></span> <span data-ttu-id="4e751-113">Du kan hämta en lista över tjänster och det aktuella tillståndet med cmdleten Get-Service.</span><span class="sxs-lookup"><span data-stu-id="4e751-113">You can get a list of the services and their current state with the Get-Service cmdlet.</span></span>| 
| <span data-ttu-id="4e751-114">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="4e751-114">BuiltInAccount</span></span>| <span data-ttu-id="4e751-115">Anger kontot du använder för tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4e751-115">Indicates the sign-in account to use for the service.</span></span> <span data-ttu-id="4e751-116">De värden som tillåts för den här egenskapen är: **LocalService**, **LocalSystem**, och **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="4e751-116">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span>| 
| <span data-ttu-id="4e751-117">autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="4e751-117">Credential</span></span>| <span data-ttu-id="4e751-118">Anger autentiseringsuppgifterna för kontot som tjänsten ska köras under.</span><span class="sxs-lookup"><span data-stu-id="4e751-118">Indicates credentials for the account that the service will run under.</span></span> <span data-ttu-id="4e751-119">Den här egenskapen och __BuiltinAccount__ egenskapen kan inte användas tillsammans.</span><span class="sxs-lookup"><span data-stu-id="4e751-119">This property and the __BuiltinAccount__ property cannot be used together.</span></span>| 
| <span data-ttu-id="4e751-120">dependsOn</span><span class="sxs-lookup"><span data-stu-id="4e751-120">DependsOn</span></span>| <span data-ttu-id="4e751-121">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="4e751-121">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="4e751-122">Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis __ResourceName__ och dess typ är __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="4e751-122">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
| <span data-ttu-id="4e751-123">StartupType</span><span class="sxs-lookup"><span data-stu-id="4e751-123">StartupType</span></span>| <span data-ttu-id="4e751-124">Anger starttypen för tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4e751-124">Indicates the startup type for the service.</span></span> <span data-ttu-id="4e751-125">De värden som tillåts för den här egenskapen är: **automatisk**, **inaktiverad**, och **manuell**</span><span class="sxs-lookup"><span data-stu-id="4e751-125">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**</span></span>| 
| <span data-ttu-id="4e751-126">Läge</span><span class="sxs-lookup"><span data-stu-id="4e751-126">State</span></span>| <span data-ttu-id="4e751-127">Visar du vill säkerställa för tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4e751-127">Indicates the state you want to ensure for the service.</span></span>| 
| <span data-ttu-id="4e751-128">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4e751-128">Description</span></span> | <span data-ttu-id="4e751-129">Anger beskrivningen av Måltjänsten.</span><span class="sxs-lookup"><span data-stu-id="4e751-129">Indicates the description of the target service.</span></span>| 
| <span data-ttu-id="4e751-130">Visningsnamn</span><span class="sxs-lookup"><span data-stu-id="4e751-130">DisplayName</span></span> | <span data-ttu-id="4e751-131">Anger visningsnamnet för Måltjänsten.</span><span class="sxs-lookup"><span data-stu-id="4e751-131">Indicates the display name of the target service.</span></span>| 
| <span data-ttu-id="4e751-132">Se till att</span><span class="sxs-lookup"><span data-stu-id="4e751-132">Ensure</span></span> | <span data-ttu-id="4e751-133">Anger om Måltjänsten finns på systemet.</span><span class="sxs-lookup"><span data-stu-id="4e751-133">Indicates whether the target service exists on the system.</span></span> <span data-ttu-id="4e751-134">Den här egenskapen **saknas** så att Måltjänsten inte finns.</span><span class="sxs-lookup"><span data-stu-id="4e751-134">Set this property to **Absent** to ensure that the target service does not exist.</span></span> <span data-ttu-id="4e751-135">Ange värdet till **finns** (standardvärdet) säkerställer att Måltjänsten finns.</span><span class="sxs-lookup"><span data-stu-id="4e751-135">Setting it to **Present** (the default value) ensures that target service exists.</span></span>|
| <span data-ttu-id="4e751-136">Sökväg</span><span class="sxs-lookup"><span data-stu-id="4e751-136">Path</span></span> | <span data-ttu-id="4e751-137">Anger sökvägen till den binära fil för en ny tjänst.</span><span class="sxs-lookup"><span data-stu-id="4e751-137">Indicates the path to the binary file for a new service.</span></span>| 

## <a name="example"></a><span data-ttu-id="4e751-138">Exempel</span><span class="sxs-lookup"><span data-stu-id="4e751-138">Example</span></span>

```powershell
configuration ServiceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        Service ServiceExample
        {
            Name        = "TermService"
            StartupType = "Manual"
            State       = "Running"
        } 
    }
}
```

