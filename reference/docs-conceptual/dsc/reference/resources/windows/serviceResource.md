---
ms.date: 09/20/2019
ms.topic: reference
title: DSC-tjänst resurs
description: DSC-tjänst resurs
ms.openlocfilehash: 68055983a8d2880b4d556fe990310f439afffe41
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664184"
---
# <a name="dsc-service-resource"></a><span data-ttu-id="4dd50-103">DSC-tjänst resurs</span><span class="sxs-lookup"><span data-stu-id="4dd50-103">DSC Service Resource</span></span>

> <span data-ttu-id="4dd50-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5. x</span><span class="sxs-lookup"><span data-stu-id="4dd50-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="4dd50-105">**Tjänst** resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera tjänster på målnoden.</span><span class="sxs-lookup"><span data-stu-id="4dd50-105">The **Service** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="4dd50-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="4dd50-106">Syntax</span></span>

```Syntax
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ StartupTimeout = [uint32]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Ignore | Running | Stopped }  ]
    [ Dependencies = [string[]] ]
    [ Description = [string] ]
    [ DesktopInteract = [boolean]]
    [ DisplayName = [string] ]
    [ Path = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
    [ TerminateTimeout = [uint32] ]
}
```

## <a name="properties"></a><span data-ttu-id="4dd50-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="4dd50-107">Properties</span></span>

|<span data-ttu-id="4dd50-108">Egenskap</span><span class="sxs-lookup"><span data-stu-id="4dd50-108">Property</span></span> |<span data-ttu-id="4dd50-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4dd50-109">Description</span></span> |
|---|---|
|<span data-ttu-id="4dd50-110">Namn</span><span class="sxs-lookup"><span data-stu-id="4dd50-110">Name</span></span> |<span data-ttu-id="4dd50-111">Anger tjänstens namn.</span><span class="sxs-lookup"><span data-stu-id="4dd50-111">Indicates the service name.</span></span> <span data-ttu-id="4dd50-112">Observera att ibland skiljer det sig från visnings namnet.</span><span class="sxs-lookup"><span data-stu-id="4dd50-112">Note that sometimes this is different from the display name.</span></span> <span data-ttu-id="4dd50-113">Du kan hämta en lista över tjänsterna och deras aktuella status med `Get-Service` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4dd50-113">You can get a list of the services and their current state with the `Get-Service` cmdlet.</span></span> |
|<span data-ttu-id="4dd50-114">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="4dd50-114">BuiltInAccount</span></span> |<span data-ttu-id="4dd50-115">Anger det inloggnings konto som ska användas för tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4dd50-115">Indicates the sign-in account to use for the service.</span></span> <span data-ttu-id="4dd50-116">De värden som tillåts för den här egenskapen är: **LocalService** , **LocalSystem** och **NetworkService** .</span><span class="sxs-lookup"><span data-stu-id="4dd50-116">The values that are allowed for this property are: **LocalService** , **LocalSystem** , and **NetworkService** .</span></span> |
|<span data-ttu-id="4dd50-117">Autentiseringsuppgift</span><span class="sxs-lookup"><span data-stu-id="4dd50-117">Credential</span></span> |<span data-ttu-id="4dd50-118">Anger autentiseringsuppgifter för det konto som tjänsten ska köras under.</span><span class="sxs-lookup"><span data-stu-id="4dd50-118">Indicates credentials for the account that the service will run under.</span></span> <span data-ttu-id="4dd50-119">Den här egenskapen och egenskapen **BuiltinAccount** kan inte användas tillsammans.</span><span class="sxs-lookup"><span data-stu-id="4dd50-119">This property and the **BuiltinAccount** property cannot be used together.</span></span> |
|<span data-ttu-id="4dd50-120">StartupTimeout</span><span class="sxs-lookup"><span data-stu-id="4dd50-120">StartupTimeout</span></span> | <span data-ttu-id="4dd50-121">Vänte tiden innan tjänsten körs i millisekunder.</span><span class="sxs-lookup"><span data-stu-id="4dd50-121">The time to wait for the service to be running in milliseconds.</span></span>|
|<span data-ttu-id="4dd50-122">Startuptype tjänst</span><span class="sxs-lookup"><span data-stu-id="4dd50-122">StartupType</span></span> |<span data-ttu-id="4dd50-123">Anger tjänstens starttyp.</span><span class="sxs-lookup"><span data-stu-id="4dd50-123">Indicates the startup type for the service.</span></span> <span data-ttu-id="4dd50-124">De värden som tillåts för den här egenskapen är: **Automatisk** , **inaktive rad** och **manuell** .</span><span class="sxs-lookup"><span data-stu-id="4dd50-124">The values that are allowed for this property are: **Automatic** , **Disabled** , and **Manual** .</span></span> |
|<span data-ttu-id="4dd50-125">Tillstånd</span><span class="sxs-lookup"><span data-stu-id="4dd50-125">State</span></span> |<span data-ttu-id="4dd50-126">Anger det tillstånd som du vill säkerställa för tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4dd50-126">Indicates the state you want to ensure for the service.</span></span> <span data-ttu-id="4dd50-127">Värdena är: **körs** eller **stoppas** .</span><span class="sxs-lookup"><span data-stu-id="4dd50-127">The values are: **Running** or **Stopped** .</span></span> |
|<span data-ttu-id="4dd50-128">TerminateTimeout</span><span class="sxs-lookup"><span data-stu-id="4dd50-128">TerminateTimeout</span></span> |<span data-ttu-id="4dd50-129">Vänte tiden innan tjänsten stoppas i millisekunder.</span><span class="sxs-lookup"><span data-stu-id="4dd50-129">The time to wait for the service to be stopped in milliseconds.</span></span>|
|<span data-ttu-id="4dd50-130">Beroenden</span><span class="sxs-lookup"><span data-stu-id="4dd50-130">Dependencies</span></span> | <span data-ttu-id="4dd50-131">En matris med namnen på de beroenden som tjänsten ska ha.</span><span class="sxs-lookup"><span data-stu-id="4dd50-131">An array of the names of the dependencies the service should have.</span></span> |
|<span data-ttu-id="4dd50-132">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4dd50-132">Description</span></span> |<span data-ttu-id="4dd50-133">Anger beskrivningen av mål tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4dd50-133">Indicates the description of the target service.</span></span> |
|<span data-ttu-id="4dd50-134">DesktopInteract</span><span class="sxs-lookup"><span data-stu-id="4dd50-134">DesktopInteract</span></span> | <span data-ttu-id="4dd50-135">Anger om tjänsten ska kunna kommunicera med ett fönster på Skriv bordet.</span><span class="sxs-lookup"><span data-stu-id="4dd50-135">Indicates whether or not the service should be able to communicate with a window on the desktop.</span></span> <span data-ttu-id="4dd50-136">Måste vara false för tjänster som inte körs som LocalSystem.</span><span class="sxs-lookup"><span data-stu-id="4dd50-136">Must be false for services not running as LocalSystem.</span></span>|
|<span data-ttu-id="4dd50-137">DisplayName</span><span class="sxs-lookup"><span data-stu-id="4dd50-137">DisplayName</span></span> |<span data-ttu-id="4dd50-138">Anger visnings namnet för mål tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4dd50-138">Indicates the display name of the target service.</span></span> |
|<span data-ttu-id="4dd50-139">Sökväg</span><span class="sxs-lookup"><span data-stu-id="4dd50-139">Path</span></span> |<span data-ttu-id="4dd50-140">Anger sökvägen till den binära filen för en ny tjänst.</span><span class="sxs-lookup"><span data-stu-id="4dd50-140">Indicates the path to the binary file for a new service.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="4dd50-141">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="4dd50-141">Common properties</span></span>

|<span data-ttu-id="4dd50-142">Egenskap</span><span class="sxs-lookup"><span data-stu-id="4dd50-142">Property</span></span> |<span data-ttu-id="4dd50-143">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4dd50-143">Description</span></span> |
|---|---|
|<span data-ttu-id="4dd50-144">DependsOn</span><span class="sxs-lookup"><span data-stu-id="4dd50-144">DependsOn</span></span> |<span data-ttu-id="4dd50-145">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="4dd50-145">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="4dd50-146">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="4dd50-146">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="4dd50-147">Kontrol</span><span class="sxs-lookup"><span data-stu-id="4dd50-147">Ensure</span></span> |<span data-ttu-id="4dd50-148">Anger om mål tjänsten finns i systemet.</span><span class="sxs-lookup"><span data-stu-id="4dd50-148">Indicates whether the target service exists on the system.</span></span> <span data-ttu-id="4dd50-149">Ange den här egenskapen som **saknas** för att säkerställa att mål tjänsten inte finns.</span><span class="sxs-lookup"><span data-stu-id="4dd50-149">Set this property to **Absent** to ensure that the target service does not exist.</span></span> <span data-ttu-id="4dd50-150">Att ställa in den så att den **visar** garanterar att mål tjänsten finns.</span><span class="sxs-lookup"><span data-stu-id="4dd50-150">Setting it to **Present** ensures that target service exists.</span></span> <span data-ttu-id="4dd50-151">Standardvärdet finns **.**</span><span class="sxs-lookup"><span data-stu-id="4dd50-151">The default value is **Present** .</span></span> |
|<span data-ttu-id="4dd50-152">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="4dd50-152">PsDscRunAsCredential</span></span> |<span data-ttu-id="4dd50-153">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="4dd50-153">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="4dd50-154">Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="4dd50-154">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="4dd50-155">Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="4dd50-155">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="4dd50-156">Exempel</span><span class="sxs-lookup"><span data-stu-id="4dd50-156">Example</span></span>

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
