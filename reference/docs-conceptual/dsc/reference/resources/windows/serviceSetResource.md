---
ms.date: 07/16/2020
ms.topic: reference
title: DSC ServiceSet-resurs
description: DSC ServiceSet-resurs
ms.openlocfilehash: 4115dd3e19121656c7448b4088346e5a1abf6af1
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664152"
---
# <a name="dsc-serviceset-resource"></a><span data-ttu-id="3824b-103">DSC ServiceSet-resurs</span><span class="sxs-lookup"><span data-stu-id="3824b-103">DSC ServiceSet Resource</span></span>

> <span data-ttu-id="3824b-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5. x</span><span class="sxs-lookup"><span data-stu-id="3824b-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="3824b-105">**ServiceSet** -resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera tjänster på målnoden.</span><span class="sxs-lookup"><span data-stu-id="3824b-105">The **ServiceSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span> <span data-ttu-id="3824b-106">Den här resursen är en [sammansatt resurs](../../../resources/authoringResourceComposite.md) som anropar [tjänst resursen](serviceResource.md) för varje tjänst som anges i egenskapen **Name** .</span><span class="sxs-lookup"><span data-stu-id="3824b-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [Service resource](serviceResource.md) for each service specified in the **Name** property.</span></span>

<span data-ttu-id="3824b-107">Använd den här resursen när du vill konfigurera ett antal tjänster till samma tillstånd.</span><span class="sxs-lookup"><span data-stu-id="3824b-107">Use this resource when you want to configure a number of services to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="3824b-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="3824b-108">Syntax</span></span>

```Syntax
ServiceSet [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="3824b-109">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="3824b-109">Properties</span></span>

|<span data-ttu-id="3824b-110">Egenskap</span><span class="sxs-lookup"><span data-stu-id="3824b-110">Property</span></span> |<span data-ttu-id="3824b-111">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3824b-111">Description</span></span> |
|---|---|
|<span data-ttu-id="3824b-112">Namn</span><span class="sxs-lookup"><span data-stu-id="3824b-112">Name</span></span> |<span data-ttu-id="3824b-113">Anger tjänst namn.</span><span class="sxs-lookup"><span data-stu-id="3824b-113">Indicates the service names.</span></span> <span data-ttu-id="3824b-114">Observera att ibland skiljer det sig från visnings namnen.</span><span class="sxs-lookup"><span data-stu-id="3824b-114">Note that sometimes this is different from the display names.</span></span> <span data-ttu-id="3824b-115">Du kan hämta en lista över tjänsterna och deras aktuella status med `Get-Service` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="3824b-115">You can get a list of the services and their current state with the `Get-Service` cmdlet.</span></span> |
|<span data-ttu-id="3824b-116">Startuptype tjänst</span><span class="sxs-lookup"><span data-stu-id="3824b-116">StartupType</span></span> |<span data-ttu-id="3824b-117">Anger start typen för tjänsterna.</span><span class="sxs-lookup"><span data-stu-id="3824b-117">Indicates the startup type for the services.</span></span> <span data-ttu-id="3824b-118">De värden som tillåts för den här egenskapen är: **Automatisk** , **inaktive rad** och **manuell** .</span><span class="sxs-lookup"><span data-stu-id="3824b-118">The values that are allowed for this property are: **Automatic** , **Disabled** , and **Manual** .</span></span> |
|<span data-ttu-id="3824b-119">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="3824b-119">BuiltInAccount</span></span> |<span data-ttu-id="3824b-120">Anger det inloggnings konto som ska användas för tjänsterna.</span><span class="sxs-lookup"><span data-stu-id="3824b-120">Indicates the sign-in account to use for the services.</span></span> <span data-ttu-id="3824b-121">De värden som tillåts för den här egenskapen är: **LocalService** , **LocalSystem** och **NetworkService** .</span><span class="sxs-lookup"><span data-stu-id="3824b-121">The values that are allowed for this property are: **LocalService** , **LocalSystem** , and **NetworkService** .</span></span> |
|<span data-ttu-id="3824b-122">Tillstånd</span><span class="sxs-lookup"><span data-stu-id="3824b-122">State</span></span> |<span data-ttu-id="3824b-123">Anger det tillstånd som du vill säkerställa för tjänsterna: **stoppas** eller **körs** .</span><span class="sxs-lookup"><span data-stu-id="3824b-123">Indicates the state you want to ensure for the services: **Stopped** or **Running** .</span></span> |
|<span data-ttu-id="3824b-124">Autentiseringsuppgift</span><span class="sxs-lookup"><span data-stu-id="3824b-124">Credential</span></span> |<span data-ttu-id="3824b-125">Anger autentiseringsuppgifter för det konto som tjänst resursen kommer att köras under.</span><span class="sxs-lookup"><span data-stu-id="3824b-125">Indicates credentials for the account that the service resource will run under.</span></span> <span data-ttu-id="3824b-126">Den här egenskapen och egenskapen **BuiltinAccount** kan inte användas tillsammans.</span><span class="sxs-lookup"><span data-stu-id="3824b-126">This property and the **BuiltinAccount** property cannot be used together.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="3824b-127">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="3824b-127">Common properties</span></span>

|<span data-ttu-id="3824b-128">Egenskap</span><span class="sxs-lookup"><span data-stu-id="3824b-128">Property</span></span> |<span data-ttu-id="3824b-129">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3824b-129">Description</span></span> |
|---|---|
|<span data-ttu-id="3824b-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="3824b-130">DependsOn</span></span> |<span data-ttu-id="3824b-131">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="3824b-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="3824b-132">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="3824b-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="3824b-133">Kontrol</span><span class="sxs-lookup"><span data-stu-id="3824b-133">Ensure</span></span> |<span data-ttu-id="3824b-134">Anger om tjänsterna finns i systemet.</span><span class="sxs-lookup"><span data-stu-id="3824b-134">Indicates whether the services exist on the system.</span></span> <span data-ttu-id="3824b-135">Ange den här egenskapen som **saknas** för att säkerställa att tjänsterna inte finns.</span><span class="sxs-lookup"><span data-stu-id="3824b-135">Set this property to **Absent** to ensure that the services do not exist.</span></span> <span data-ttu-id="3824b-136">Att ställa in det för att **Visa** garanterar att mål tjänsterna finns.</span><span class="sxs-lookup"><span data-stu-id="3824b-136">Setting it to **Present** ensures that target services exist.</span></span> <span data-ttu-id="3824b-137">Standardvärdet finns **.**</span><span class="sxs-lookup"><span data-stu-id="3824b-137">The default value is **Present** .</span></span> |
|<span data-ttu-id="3824b-138">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="3824b-138">PsDscRunAsCredential</span></span> |<span data-ttu-id="3824b-139">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="3824b-139">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="3824b-140">Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="3824b-140">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="3824b-141">Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="3824b-141">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="3824b-142">Exempel</span><span class="sxs-lookup"><span data-stu-id="3824b-142">Example</span></span>

<span data-ttu-id="3824b-143">Följande konfiguration startar tjänsterna Windows Audio och Fjärrskrivbordstjänster.</span><span class="sxs-lookup"><span data-stu-id="3824b-143">The following configuration starts the "Windows Audio" and "Remote Desktop Services" services.</span></span>

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
