---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC-tjänstresurs
ms.openlocfilehash: 09571bd0eaa428e7d0bb7a533d6ad1c0c936e2cf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076910"
---
# <a name="dsc-service-resource"></a><span data-ttu-id="c9a2d-103">DSC-tjänstresurs</span><span class="sxs-lookup"><span data-stu-id="c9a2d-103">DSC Service Resource</span></span>

> <span data-ttu-id="c9a2d-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c9a2d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="c9a2d-105">Den **Service** resursen i Windows PowerShell Desired State Configuration (DSC) är en mekanism för att hantera tjänster på målnoden.</span><span class="sxs-lookup"><span data-stu-id="c9a2d-105">The **Service** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="c9a2d-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="c9a2d-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="c9a2d-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="c9a2d-107">Properties</span></span>

|  <span data-ttu-id="c9a2d-108">Egenskap</span><span class="sxs-lookup"><span data-stu-id="c9a2d-108">Property</span></span>  |  <span data-ttu-id="c9a2d-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c9a2d-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="c9a2d-110">Namn</span><span class="sxs-lookup"><span data-stu-id="c9a2d-110">Name</span></span>| <span data-ttu-id="c9a2d-111">Anger namnet på tjänsten.</span><span class="sxs-lookup"><span data-stu-id="c9a2d-111">Indicates the service name.</span></span> <span data-ttu-id="c9a2d-112">Observera att ibland Detta skiljer sig från visningsnamnet.</span><span class="sxs-lookup"><span data-stu-id="c9a2d-112">Note that sometimes this is different from the display name.</span></span> <span data-ttu-id="c9a2d-113">Du kan hämta en lista över tjänsterna samt enheternas aktuella status med cmdleten Get-Service.</span><span class="sxs-lookup"><span data-stu-id="c9a2d-113">You can get a list of the services and their current state with the Get-Service cmdlet.</span></span>|
| <span data-ttu-id="c9a2d-114">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="c9a2d-114">BuiltInAccount</span></span>| <span data-ttu-id="c9a2d-115">Anger kontot du använder för tjänsten.</span><span class="sxs-lookup"><span data-stu-id="c9a2d-115">Indicates the sign-in account to use for the service.</span></span> <span data-ttu-id="c9a2d-116">De värden som tillåts för den här egenskapen är: **LocalService**, **LocalSystem**, och **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="c9a2d-116">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span>|
| <span data-ttu-id="c9a2d-117">Autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="c9a2d-117">Credential</span></span>| <span data-ttu-id="c9a2d-118">Anger autentiseringsuppgifterna för kontot som tjänsten ska köras under.</span><span class="sxs-lookup"><span data-stu-id="c9a2d-118">Indicates credentials for the account that the service will run under.</span></span> <span data-ttu-id="c9a2d-119">Den här egenskapen och __BuiltinAccount__ egenskapen kan inte användas tillsammans.</span><span class="sxs-lookup"><span data-stu-id="c9a2d-119">This property and the __BuiltinAccount__ property cannot be used together.</span></span>|
| <span data-ttu-id="c9a2d-120">DependsOn</span><span class="sxs-lookup"><span data-stu-id="c9a2d-120">DependsOn</span></span>| <span data-ttu-id="c9a2d-121">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="c9a2d-121">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c9a2d-122">Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är __ResourceName__ och är av typen __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="c9a2d-122">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="c9a2d-123">Startuptype för</span><span class="sxs-lookup"><span data-stu-id="c9a2d-123">StartupType</span></span>| <span data-ttu-id="c9a2d-124">Anger starttypen för tjänsten.</span><span class="sxs-lookup"><span data-stu-id="c9a2d-124">Indicates the startup type for the service.</span></span> <span data-ttu-id="c9a2d-125">De värden som tillåts för den här egenskapen är: **Automatisk**, **inaktiverad**, och **manuell**</span><span class="sxs-lookup"><span data-stu-id="c9a2d-125">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**</span></span>|
| <span data-ttu-id="c9a2d-126">Tillstånd</span><span class="sxs-lookup"><span data-stu-id="c9a2d-126">State</span></span>| <span data-ttu-id="c9a2d-127">Anger det tillstånd som du vill säkerställa för tjänsten.</span><span class="sxs-lookup"><span data-stu-id="c9a2d-127">Indicates the state you want to ensure for the service.</span></span>|
| <span data-ttu-id="c9a2d-128">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c9a2d-128">Description</span></span> | <span data-ttu-id="c9a2d-129">Anger beskrivningen av Måltjänsten.</span><span class="sxs-lookup"><span data-stu-id="c9a2d-129">Indicates the description of the target service.</span></span>|
| <span data-ttu-id="c9a2d-130">Visningsnamn</span><span class="sxs-lookup"><span data-stu-id="c9a2d-130">DisplayName</span></span> | <span data-ttu-id="c9a2d-131">Anger visningsnamnet för Måltjänsten.</span><span class="sxs-lookup"><span data-stu-id="c9a2d-131">Indicates the display name of the target service.</span></span>|
| <span data-ttu-id="c9a2d-132">Se till att</span><span class="sxs-lookup"><span data-stu-id="c9a2d-132">Ensure</span></span> | <span data-ttu-id="c9a2d-133">Anger om Måltjänsten finns i systemet.</span><span class="sxs-lookup"><span data-stu-id="c9a2d-133">Indicates whether the target service exists on the system.</span></span> <span data-ttu-id="c9a2d-134">Den här egenskapen **frånvarande** så inte finns target-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="c9a2d-134">Set this property to **Absent** to ensure that the target service does not exist.</span></span> <span data-ttu-id="c9a2d-135">Ange värdet till **finns** (standardvärdet) säkerställer att Måltjänsten finns.</span><span class="sxs-lookup"><span data-stu-id="c9a2d-135">Setting it to **Present** (the default value) ensures that target service exists.</span></span>|
| <span data-ttu-id="c9a2d-136">Sökväg</span><span class="sxs-lookup"><span data-stu-id="c9a2d-136">Path</span></span> | <span data-ttu-id="c9a2d-137">Anger sökvägen till den binära filen för en ny tjänst.</span><span class="sxs-lookup"><span data-stu-id="c9a2d-137">Indicates the path to the binary file for a new service.</span></span>|

## <a name="example"></a><span data-ttu-id="c9a2d-138">Exempel</span><span class="sxs-lookup"><span data-stu-id="c9a2d-138">Example</span></span>

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