---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC-tjänst resurs
ms.openlocfilehash: 0bef6aa6d3526c9d8d92187c1e738d5c46b5665a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71941315"
---
# <a name="dsc-service-resource"></a><span data-ttu-id="45ce7-103">DSC-tjänst resurs</span><span class="sxs-lookup"><span data-stu-id="45ce7-103">DSC Service Resource</span></span>

> <span data-ttu-id="45ce7-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5. x</span><span class="sxs-lookup"><span data-stu-id="45ce7-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="45ce7-105">**Tjänst** resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera tjänster på målnoden.</span><span class="sxs-lookup"><span data-stu-id="45ce7-105">The **Service** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="45ce7-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="45ce7-106">Syntax</span></span>

```Syntax
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Path = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="45ce7-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="45ce7-107">Properties</span></span>

|<span data-ttu-id="45ce7-108">Egenskap</span><span class="sxs-lookup"><span data-stu-id="45ce7-108">Property</span></span> |<span data-ttu-id="45ce7-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="45ce7-109">Description</span></span> |
|---|---|
|<span data-ttu-id="45ce7-110">Namn</span><span class="sxs-lookup"><span data-stu-id="45ce7-110">Name</span></span> |<span data-ttu-id="45ce7-111">Anger tjänstens namn.</span><span class="sxs-lookup"><span data-stu-id="45ce7-111">Indicates the service name.</span></span> <span data-ttu-id="45ce7-112">Observera att ibland skiljer det sig från visnings namnet.</span><span class="sxs-lookup"><span data-stu-id="45ce7-112">Note that sometimes this is different from the display name.</span></span> <span data-ttu-id="45ce7-113">Du kan hämta en lista över tjänsterna och deras aktuella status med `Get-Service`-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="45ce7-113">You can get a list of the services and their current state with the `Get-Service` cmdlet.</span></span> |
|<span data-ttu-id="45ce7-114">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="45ce7-114">BuiltInAccount</span></span> |<span data-ttu-id="45ce7-115">Anger det inloggnings konto som ska användas för tjänsten.</span><span class="sxs-lookup"><span data-stu-id="45ce7-115">Indicates the sign-in account to use for the service.</span></span> <span data-ttu-id="45ce7-116">De värden som tillåts för den här egenskapen är: **LocalService**, **LocalSystem**och **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="45ce7-116">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span> |
|<span data-ttu-id="45ce7-117">Autentiseringsuppgift</span><span class="sxs-lookup"><span data-stu-id="45ce7-117">Credential</span></span> |<span data-ttu-id="45ce7-118">Anger autentiseringsuppgifter för det konto som tjänsten ska köras under.</span><span class="sxs-lookup"><span data-stu-id="45ce7-118">Indicates credentials for the account that the service will run under.</span></span> <span data-ttu-id="45ce7-119">Den här egenskapen och egenskapen **BuiltinAccount** kan inte användas tillsammans.</span><span class="sxs-lookup"><span data-stu-id="45ce7-119">This property and the **BuiltinAccount** property cannot be used together.</span></span> |
|<span data-ttu-id="45ce7-120">Startuptype tjänst</span><span class="sxs-lookup"><span data-stu-id="45ce7-120">StartupType</span></span> |<span data-ttu-id="45ce7-121">Anger tjänstens starttyp.</span><span class="sxs-lookup"><span data-stu-id="45ce7-121">Indicates the startup type for the service.</span></span> <span data-ttu-id="45ce7-122">De värden som tillåts för den här egenskapen är: **Automatisk**, **inaktive rad**och **manuell**.</span><span class="sxs-lookup"><span data-stu-id="45ce7-122">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**.</span></span> |
|<span data-ttu-id="45ce7-123">Tillstånd</span><span class="sxs-lookup"><span data-stu-id="45ce7-123">State</span></span> |<span data-ttu-id="45ce7-124">Anger det tillstånd som du vill säkerställa för tjänsten.</span><span class="sxs-lookup"><span data-stu-id="45ce7-124">Indicates the state you want to ensure for the service.</span></span> <span data-ttu-id="45ce7-125">Värdena är: **körs** eller **stoppas**.</span><span class="sxs-lookup"><span data-stu-id="45ce7-125">The values are: **Running** or **Stopped**.</span></span> |
|<span data-ttu-id="45ce7-126">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="45ce7-126">Description</span></span> |<span data-ttu-id="45ce7-127">Anger beskrivningen av mål tjänsten.</span><span class="sxs-lookup"><span data-stu-id="45ce7-127">Indicates the description of the target service.</span></span> |
|<span data-ttu-id="45ce7-128">Visningsnamn</span><span class="sxs-lookup"><span data-stu-id="45ce7-128">DisplayName</span></span> |<span data-ttu-id="45ce7-129">Anger visnings namnet för mål tjänsten.</span><span class="sxs-lookup"><span data-stu-id="45ce7-129">Indicates the display name of the target service.</span></span> |
|<span data-ttu-id="45ce7-130">Sökväg</span><span class="sxs-lookup"><span data-stu-id="45ce7-130">Path</span></span> |<span data-ttu-id="45ce7-131">Anger sökvägen till den binära filen för en ny tjänst.</span><span class="sxs-lookup"><span data-stu-id="45ce7-131">Indicates the path to the binary file for a new service.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="45ce7-132">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="45ce7-132">Common properties</span></span>

|<span data-ttu-id="45ce7-133">Egenskap</span><span class="sxs-lookup"><span data-stu-id="45ce7-133">Property</span></span> |<span data-ttu-id="45ce7-134">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="45ce7-134">Description</span></span> |
|---|---|
|<span data-ttu-id="45ce7-135">DependsOn</span><span class="sxs-lookup"><span data-stu-id="45ce7-135">DependsOn</span></span> |<span data-ttu-id="45ce7-136">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="45ce7-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="45ce7-137">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="45ce7-137">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="45ce7-138">Kontrol</span><span class="sxs-lookup"><span data-stu-id="45ce7-138">Ensure</span></span> |<span data-ttu-id="45ce7-139">Anger om mål tjänsten finns i systemet.</span><span class="sxs-lookup"><span data-stu-id="45ce7-139">Indicates whether the target service exists on the system.</span></span> <span data-ttu-id="45ce7-140">Ange den här egenskapen som **saknas** för att säkerställa att mål tjänsten inte finns.</span><span class="sxs-lookup"><span data-stu-id="45ce7-140">Set this property to **Absent** to ensure that the target service does not exist.</span></span> <span data-ttu-id="45ce7-141">Att ställa in den så att den **visar** garanterar att mål tjänsten finns.</span><span class="sxs-lookup"><span data-stu-id="45ce7-141">Setting it to **Present** ensures that target service exists.</span></span> <span data-ttu-id="45ce7-142">Standardvärdet finns **.**</span><span class="sxs-lookup"><span data-stu-id="45ce7-142">The default value is **Present**.</span></span> |
|<span data-ttu-id="45ce7-143">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="45ce7-143">PsDscRunAsCredential</span></span> |<span data-ttu-id="45ce7-144">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="45ce7-144">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="45ce7-145">Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="45ce7-145">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="45ce7-146">Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="45ce7-146">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="45ce7-147">Exempel</span><span class="sxs-lookup"><span data-stu-id="45ce7-147">Example</span></span>

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