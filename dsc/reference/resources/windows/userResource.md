---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC-användarresurs
ms.openlocfilehash: 04543351df19160a2da05ccea96e5d392d8c55bf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076913"
---
# <a name="dsc-user-resource"></a><span data-ttu-id="7049d-103">DSC-användarresurs</span><span class="sxs-lookup"><span data-stu-id="7049d-103">DSC User Resource</span></span>

<span data-ttu-id="7049d-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7049d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="7049d-105">Den **användaren** resursen i Windows PowerShell Desired State Configuration (DSC) ger dig möjlighet att hantera lokala användarkonton på målnoden.</span><span class="sxs-lookup"><span data-stu-id="7049d-105">The **User** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local user accounts on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="7049d-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="7049d-106">Syntax</span></span>

```
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="7049d-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="7049d-107">Properties</span></span>

|  <span data-ttu-id="7049d-108">Egenskap</span><span class="sxs-lookup"><span data-stu-id="7049d-108">Property</span></span>  |  <span data-ttu-id="7049d-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7049d-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="7049d-110">UserName</span><span class="sxs-lookup"><span data-stu-id="7049d-110">UserName</span></span>| <span data-ttu-id="7049d-111">Anger namnet på kontot som du vill se till att ett visst tillstånd.</span><span class="sxs-lookup"><span data-stu-id="7049d-111">Indicates the account name for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="7049d-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7049d-112">Description</span></span>| <span data-ttu-id="7049d-113">Anger den beskrivning som du vill använda för användarkontot.</span><span class="sxs-lookup"><span data-stu-id="7049d-113">Indicates the description you want to use for the user account.</span></span>|
| <span data-ttu-id="7049d-114">Inaktiverat</span><span class="sxs-lookup"><span data-stu-id="7049d-114">Disabled</span></span>| <span data-ttu-id="7049d-115">Anger om kontot är aktiverat.</span><span class="sxs-lookup"><span data-stu-id="7049d-115">Indicates if the account is enabled.</span></span> <span data-ttu-id="7049d-116">Den här egenskapen `$true` så att det här kontot är inaktiverat och ange den till `$false` så att den är aktiverad.</span><span class="sxs-lookup"><span data-stu-id="7049d-116">Set this property to `$true` to ensure that this account is disabled, and set it to `$false` to ensure that it is enabled.</span></span>|
| <span data-ttu-id="7049d-117">Se till att</span><span class="sxs-lookup"><span data-stu-id="7049d-117">Ensure</span></span>| <span data-ttu-id="7049d-118">Anger om kontot finns.</span><span class="sxs-lookup"><span data-stu-id="7049d-118">Indicates if the account exists.</span></span> <span data-ttu-id="7049d-119">Ange den här egenskapen ”aktuella” så att konton som finns och ange den till ”” så att kontot inte finns.</span><span class="sxs-lookup"><span data-stu-id="7049d-119">Set this property to "Present" to ensure that the account exists, and set it to "Absent" to ensure that the account does not exist.</span></span>|
| <span data-ttu-id="7049d-120">FullName</span><span class="sxs-lookup"><span data-stu-id="7049d-120">FullName</span></span>| <span data-ttu-id="7049d-121">Representerar en sträng med det fullständiga namnet som du vill använda för användarkontot.</span><span class="sxs-lookup"><span data-stu-id="7049d-121">Represents a string with the full name you want to use for the user account.</span></span>|
| <span data-ttu-id="7049d-122">Lösenord</span><span class="sxs-lookup"><span data-stu-id="7049d-122">Password</span></span>| <span data-ttu-id="7049d-123">Anger det lösenord som du vill använda för det här kontot.</span><span class="sxs-lookup"><span data-stu-id="7049d-123">Indicates the password you want to use for this account.</span></span> |
| <span data-ttu-id="7049d-124">PasswordChangeNotAllowed</span><span class="sxs-lookup"><span data-stu-id="7049d-124">PasswordChangeNotAllowed</span></span>| <span data-ttu-id="7049d-125">Anger om användaren kan ändra lösenordet.</span><span class="sxs-lookup"><span data-stu-id="7049d-125">Indicates if the user can change the password.</span></span> <span data-ttu-id="7049d-126">Den här egenskapen `$true` så att användaren inte kan ändra lösenordet och ange den till `$false` att tillåta användare att ändra lösenordet.</span><span class="sxs-lookup"><span data-stu-id="7049d-126">Set this property to `$true` to ensure that the user cannot change the password, and set it to `$false` to allow the user to change the password.</span></span> <span data-ttu-id="7049d-127">Standardvärdet är `$false`.</span><span class="sxs-lookup"><span data-stu-id="7049d-127">The default value is `$false`.</span></span>|
| <span data-ttu-id="7049d-128">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="7049d-128">PasswordChangeRequired</span></span>| <span data-ttu-id="7049d-129">Anger om användaren måste byta lösenord vid nästa inloggning.</span><span class="sxs-lookup"><span data-stu-id="7049d-129">Indicates if the user must change the password at the next sign in.</span></span> <span data-ttu-id="7049d-130">Den här egenskapen `$true` om användaren måste byta lösenord.</span><span class="sxs-lookup"><span data-stu-id="7049d-130">Set this property to `$true` if the user must change the password.</span></span> <span data-ttu-id="7049d-131">Standardvärdet är `$true`.</span><span class="sxs-lookup"><span data-stu-id="7049d-131">The default value is `$true`.</span></span>|
| <span data-ttu-id="7049d-132">PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="7049d-132">PasswordNeverExpires</span></span>| <span data-ttu-id="7049d-133">Anger om lösenordet upphör att gälla.</span><span class="sxs-lookup"><span data-stu-id="7049d-133">Indicates if the password will expire.</span></span> <span data-ttu-id="7049d-134">Att säkerställa att lösenordet för det här kontot upphör aldrig att gälla, ange egenskapen till `$true`, och ge den värdet `$false` om lösenordet upphör att gälla.</span><span class="sxs-lookup"><span data-stu-id="7049d-134">To ensure that the password for this account will never expire, set this property to `$true`, and set it to `$false` if the password will expire.</span></span> <span data-ttu-id="7049d-135">Standardvärdet är `$false`.</span><span class="sxs-lookup"><span data-stu-id="7049d-135">The default value is `$false`.</span></span>|
| <span data-ttu-id="7049d-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="7049d-136">DependsOn</span></span> | <span data-ttu-id="7049d-137">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="7049d-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7049d-138">Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är **ResourceName** och är av typen **ResourceType**, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="7049d-138">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="7049d-139">Exempel</span><span class="sxs-lookup"><span data-stu-id="7049d-139">Example</span></span>

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```