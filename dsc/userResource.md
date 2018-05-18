---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC-användarresurs
ms.openlocfilehash: f2660933aec43967e3f4082a983ef328a5b93851
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
#<a name="dsc-user-resource"></a><span data-ttu-id="44c44-103">DSC-användaren resurs #</span><span class="sxs-lookup"><span data-stu-id="44c44-103">DSC User Resource#</span></span>


><span data-ttu-id="44c44-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="44c44-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="44c44-105">Den __användaren__ resurs i Windows PowerShell önskad tillstånd Configuration (DSC) tillhandahåller en mekanism för att hantera lokala användarkonton på målnoden.</span><span class="sxs-lookup"><span data-stu-id="44c44-105">The __User__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local user accounts on the target node.</span></span>


##<a name="syntax"></a><span data-ttu-id="44c44-106">Syntaxen ##</span><span class="sxs-lookup"><span data-stu-id="44c44-106">Syntax##</span></span>

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

## <a name="properties"></a><span data-ttu-id="44c44-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="44c44-107">Properties</span></span>
|  <span data-ttu-id="44c44-108">Egenskap</span><span class="sxs-lookup"><span data-stu-id="44c44-108">Property</span></span>  |  <span data-ttu-id="44c44-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="44c44-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="44c44-110">UserName</span><span class="sxs-lookup"><span data-stu-id="44c44-110">UserName</span></span>| <span data-ttu-id="44c44-111">Anger namnet på kontot som du vill se till att ett visst tillstånd.</span><span class="sxs-lookup"><span data-stu-id="44c44-111">Indicates the account name for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="44c44-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="44c44-112">Description</span></span>| <span data-ttu-id="44c44-113">Anger den beskrivning som du vill använda för användarkontot.</span><span class="sxs-lookup"><span data-stu-id="44c44-113">Indicates the description you want to use for the user account.</span></span>|
| <span data-ttu-id="44c44-114">Inaktiverad</span><span class="sxs-lookup"><span data-stu-id="44c44-114">Disabled</span></span>| <span data-ttu-id="44c44-115">Anger om kontot är aktiverad.</span><span class="sxs-lookup"><span data-stu-id="44c44-115">Indicates if the account is enabled.</span></span> <span data-ttu-id="44c44-116">Den här egenskapen __$true__ så att det här kontot är inaktiverad och inställd på __$false__ så att den är aktiverad.</span><span class="sxs-lookup"><span data-stu-id="44c44-116">Set this property to __$true__ to ensure that this account is disabled, and set it to __$false__ to ensure that it is enabled.</span></span>|
| <span data-ttu-id="44c44-117">Se till att</span><span class="sxs-lookup"><span data-stu-id="44c44-117">Ensure</span></span>| <span data-ttu-id="44c44-118">Anger om kontot finns.</span><span class="sxs-lookup"><span data-stu-id="44c44-118">Indicates if the account exists.</span></span> <span data-ttu-id="44c44-119">Ange egenskapen ”aktuella” för att säkerställa att finns ett konto och ange den till ”saknas” så att kontot inte finns.</span><span class="sxs-lookup"><span data-stu-id="44c44-119">Set this property to "Present" to ensure that the account exists, and set it to "Absent" to ensure that the account does not exist.</span></span>|
| <span data-ttu-id="44c44-120">Fullständigt namn</span><span class="sxs-lookup"><span data-stu-id="44c44-120">FullName</span></span>| <span data-ttu-id="44c44-121">Representerar en sträng med det fullständiga namnet som du vill använda för användarkontot.</span><span class="sxs-lookup"><span data-stu-id="44c44-121">Represents a string with the full name you want to use for the user account.</span></span>|
| <span data-ttu-id="44c44-122">Lösenord</span><span class="sxs-lookup"><span data-stu-id="44c44-122">Password</span></span>| <span data-ttu-id="44c44-123">Anger lösenordet som du vill använda för det här kontot.</span><span class="sxs-lookup"><span data-stu-id="44c44-123">Indicates the password you want to use for this account.</span></span> |
| <span data-ttu-id="44c44-124">PasswordChangeNotAllowed</span><span class="sxs-lookup"><span data-stu-id="44c44-124">PasswordChangeNotAllowed</span></span>| <span data-ttu-id="44c44-125">Anger om användaren kan ändra lösenordet.</span><span class="sxs-lookup"><span data-stu-id="44c44-125">Indicates if the user can change the password.</span></span> <span data-ttu-id="44c44-126">Den här egenskapen __$true__ så att användaren inte kan ändra lösenordet och Ställ in den på __$false__ att tillåta användaren att ändra lösenordet.</span><span class="sxs-lookup"><span data-stu-id="44c44-126">Set this property to __$true__ to ensure that the user cannot change the password, and set it to __$false__ to allow the user to change the password.</span></span> <span data-ttu-id="44c44-127">Standardvärdet är __$false__.</span><span class="sxs-lookup"><span data-stu-id="44c44-127">The default value is __$false__.</span></span>|
| <span data-ttu-id="44c44-128">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="44c44-128">PasswordChangeRequired</span></span>| <span data-ttu-id="44c44-129">Anger om användaren måste byta lösenord vid nästa inloggning.</span><span class="sxs-lookup"><span data-stu-id="44c44-129">Indicates if the user must change the password at the next sign in.</span></span> <span data-ttu-id="44c44-130">Den här egenskapen __$true__ om användaren måste ändra lösenordet.</span><span class="sxs-lookup"><span data-stu-id="44c44-130">Set this property to __$true__ if the user must change the password.</span></span> <span data-ttu-id="44c44-131">Standardvärdet är __$true__.</span><span class="sxs-lookup"><span data-stu-id="44c44-131">The default value is __$true__.</span></span>|
| <span data-ttu-id="44c44-132">PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="44c44-132">PasswordNeverExpires</span></span>| <span data-ttu-id="44c44-133">Anger om lösenordet upphör att gälla.</span><span class="sxs-lookup"><span data-stu-id="44c44-133">Indicates if the password will expire.</span></span> <span data-ttu-id="44c44-134">Att se till att lösenordet för det här kontot upphör aldrig att gälla, ange egenskapen till __$true__, och ange det till __$false__ om lösenordet upphör att gälla.</span><span class="sxs-lookup"><span data-stu-id="44c44-134">To ensure that the password for this account will never expire, set this property to __$true__, and set it to __$false__ if the password will expire.</span></span> <span data-ttu-id="44c44-135">Standardvärdet är __$false__.</span><span class="sxs-lookup"><span data-stu-id="44c44-135">The default value is __$false__.</span></span>|
| <span data-ttu-id="44c44-136">dependsOn</span><span class="sxs-lookup"><span data-stu-id="44c44-136">DependsOn</span></span> | <span data-ttu-id="44c44-137">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="44c44-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="44c44-138">Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis __ResourceName__ och dess typ är __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="44c44-138">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="44c44-139">Exempel</span><span class="sxs-lookup"><span data-stu-id="44c44-139">Example</span></span>

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```