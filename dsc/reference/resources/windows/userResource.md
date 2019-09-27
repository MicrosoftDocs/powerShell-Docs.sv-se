---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC-användar resurs
ms.openlocfilehash: dec432c2ff1b4e4408165fef391e77cbf1d85ac4
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71324058"
---
# <a name="dsc-user-resource"></a><span data-ttu-id="fda1e-103">DSC-användar resurs</span><span class="sxs-lookup"><span data-stu-id="fda1e-103">DSC User Resource</span></span>

> <span data-ttu-id="fda1e-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5. x</span><span class="sxs-lookup"><span data-stu-id="fda1e-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="fda1e-105">**Användar** resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera lokala användar konton på målnoden.</span><span class="sxs-lookup"><span data-stu-id="fda1e-105">The **User** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local user accounts on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="fda1e-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="fda1e-106">Syntax</span></span>

```Syntax
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="fda1e-107">properties</span><span class="sxs-lookup"><span data-stu-id="fda1e-107">Properties</span></span>

|<span data-ttu-id="fda1e-108">Egenskap</span><span class="sxs-lookup"><span data-stu-id="fda1e-108">Property</span></span> |<span data-ttu-id="fda1e-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="fda1e-109">Description</span></span> |
|---|---|
|<span data-ttu-id="fda1e-110">UserName</span><span class="sxs-lookup"><span data-stu-id="fda1e-110">UserName</span></span> |<span data-ttu-id="fda1e-111">Anger det konto namn som du vill säkerställa ett speciellt tillstånd för.</span><span class="sxs-lookup"><span data-stu-id="fda1e-111">Indicates the account name for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="fda1e-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="fda1e-112">Description</span></span> |<span data-ttu-id="fda1e-113">Anger beskrivningen som du vill använda för användar kontot.</span><span class="sxs-lookup"><span data-stu-id="fda1e-113">Indicates the description you want to use for the user account.</span></span> |
|<span data-ttu-id="fda1e-114">Inaktiverad</span><span class="sxs-lookup"><span data-stu-id="fda1e-114">Disabled</span></span> |<span data-ttu-id="fda1e-115">Anger om kontot är aktiverat.</span><span class="sxs-lookup"><span data-stu-id="fda1e-115">Indicates if the account is enabled.</span></span> <span data-ttu-id="fda1e-116">Ange den här egenskapen `$true` till för att säkerställa att det här kontot är inaktiverat `$false` och ange det för att säkerställa att det är aktiverat.</span><span class="sxs-lookup"><span data-stu-id="fda1e-116">Set this property to `$true` to ensure that this account is disabled, and set it to `$false` to ensure that it is enabled.</span></span> |
|<span data-ttu-id="fda1e-117">FullName</span><span class="sxs-lookup"><span data-stu-id="fda1e-117">FullName</span></span> |<span data-ttu-id="fda1e-118">Representerar en sträng med det fullständiga namn som du vill använda för användar kontot.</span><span class="sxs-lookup"><span data-stu-id="fda1e-118">Represents a string with the full name you want to use for the user account.</span></span> |
|<span data-ttu-id="fda1e-119">lösenordsinställning</span><span class="sxs-lookup"><span data-stu-id="fda1e-119">Password</span></span> |<span data-ttu-id="fda1e-120">Anger det lösen ord som du vill använda för det här kontot.</span><span class="sxs-lookup"><span data-stu-id="fda1e-120">Indicates the password you want to use for this account.</span></span> |
|<span data-ttu-id="fda1e-121">PasswordChangeNotAllowed</span><span class="sxs-lookup"><span data-stu-id="fda1e-121">PasswordChangeNotAllowed</span></span> |<span data-ttu-id="fda1e-122">Anger om användaren kan ändra lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="fda1e-122">Indicates if the user can change the password.</span></span> <span data-ttu-id="fda1e-123">Ange den här egenskapen `$true` till om du vill se till att användaren inte kan ändra lösen ordet och `$false` ange det som tillåter användaren att ändra lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="fda1e-123">Set this property to `$true` to ensure that the user cannot change the password, and set it to `$false` to allow the user to change the password.</span></span> <span data-ttu-id="fda1e-124">Standardvärdet är `$false`.</span><span class="sxs-lookup"><span data-stu-id="fda1e-124">The default value is `$false`.</span></span> |
|<span data-ttu-id="fda1e-125">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="fda1e-125">PasswordChangeRequired</span></span> |<span data-ttu-id="fda1e-126">Anger om användaren måste ändra lösen ordet vid nästa inloggning.</span><span class="sxs-lookup"><span data-stu-id="fda1e-126">Indicates if the user must change the password at the next sign in.</span></span> <span data-ttu-id="fda1e-127">Ange den här egenskapen `$true` till om användaren måste ändra lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="fda1e-127">Set this property to `$true` if the user must change the password.</span></span> <span data-ttu-id="fda1e-128">Standardvärdet är `$true`.</span><span class="sxs-lookup"><span data-stu-id="fda1e-128">The default value is `$true`.</span></span> |
|<span data-ttu-id="fda1e-129">PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="fda1e-129">PasswordNeverExpires</span></span> |<span data-ttu-id="fda1e-130">Anger om lösen ordet upphör att gälla.</span><span class="sxs-lookup"><span data-stu-id="fda1e-130">Indicates if the password will expire.</span></span> <span data-ttu-id="fda1e-131">För att se till att lösen ordet för det här kontot aldrig upphör att gälla, anger `$true`du egenskapen till.</span><span class="sxs-lookup"><span data-stu-id="fda1e-131">To ensure that the password for this account will never expire, set this property to `$true`.</span></span> <span data-ttu-id="fda1e-132">Ange det som `$false` om lösen ordet upphör att gälla.</span><span class="sxs-lookup"><span data-stu-id="fda1e-132">Set it to `$false` if the password will expire.</span></span> <span data-ttu-id="fda1e-133">Standardvärdet är `$false`.</span><span class="sxs-lookup"><span data-stu-id="fda1e-133">The default value is `$false`.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="fda1e-134">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="fda1e-134">Common properties</span></span>

|<span data-ttu-id="fda1e-135">Egenskap</span><span class="sxs-lookup"><span data-stu-id="fda1e-135">Property</span></span> |<span data-ttu-id="fda1e-136">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="fda1e-136">Description</span></span> |
|---|---|
|<span data-ttu-id="fda1e-137">DependsOn</span><span class="sxs-lookup"><span data-stu-id="fda1e-137">DependsOn</span></span> |<span data-ttu-id="fda1e-138">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="fda1e-138">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="fda1e-139">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är `DependsOn = "[ResourceType]ResourceName"`syntaxen för att använda den här egenskapen.</span><span class="sxs-lookup"><span data-stu-id="fda1e-139">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="fda1e-140">Kontrol</span><span class="sxs-lookup"><span data-stu-id="fda1e-140">Ensure</span></span> |<span data-ttu-id="fda1e-141">Anger om kontot finns.</span><span class="sxs-lookup"><span data-stu-id="fda1e-141">Indicates if the account exists.</span></span> <span data-ttu-id="fda1e-142">Ange att den här egenskapen **finns för att** se till att kontot finns och att det inte finns **något att se** till att kontot inte finns.</span><span class="sxs-lookup"><span data-stu-id="fda1e-142">Set this property to **Present** to ensure that the account exists, and set it to **Absent** to ensure that the account does not exist.</span></span> <span data-ttu-id="fda1e-143">Standardvärdet finns **.**</span><span class="sxs-lookup"><span data-stu-id="fda1e-143">The default value is **Present**.</span></span> |
|<span data-ttu-id="fda1e-144">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="fda1e-144">PsDscRunAsCredential</span></span> |<span data-ttu-id="fda1e-145">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="fda1e-145">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="fda1e-146">Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="fda1e-146">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="fda1e-147">Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="fda1e-147">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="fda1e-148">Exempel</span><span class="sxs-lookup"><span data-stu-id="fda1e-148">Example</span></span>

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```