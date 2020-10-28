---
ms.date: 09/20/2019
ms.topic: reference
title: DSC GroupSet-resurs
description: DSC GroupSet-resurs
ms.openlocfilehash: f0e10409b0c80658ee05358c506b32da4b9deca7
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650474"
---
# <a name="dsc-groupset-resource"></a><span data-ttu-id="39d84-103">DSC GroupSet-resurs</span><span class="sxs-lookup"><span data-stu-id="39d84-103">DSC GroupSet Resource</span></span>

> <span data-ttu-id="39d84-104">Gäller för: Windows PowerShell 5. x</span><span class="sxs-lookup"><span data-stu-id="39d84-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="39d84-105">**GroupSet** -resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera lokala grupper på målnoden.</span><span class="sxs-lookup"><span data-stu-id="39d84-105">The **GroupSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span> <span data-ttu-id="39d84-106">Den här resursen är en [sammansatt resurs](../../../resources/authoringResourceComposite.md) som anropar [grupp resursen](groupResource.md) för varje grupp som anges i `GroupName` parametern.</span><span class="sxs-lookup"><span data-stu-id="39d84-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [Group resource](groupResource.md) for each group specified in the `GroupName` parameter.</span></span>

<span data-ttu-id="39d84-107">Använd den här resursen när du vill lägga till och/eller ta bort samma lista med medlemmar till mer än en grupp, ta bort mer än en grupp eller lägga till mer än en grupp med samma lista med medlemmar.</span><span class="sxs-lookup"><span data-stu-id="39d84-107">Use this resource when you want to add and/or remove the same list of members to more than one group, remove more than one group, or add more than one group with the same list of members.</span></span>

## <a name="syntax"></a><span data-ttu-id="39d84-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="39d84-108">Syntax</span></span>

```Syntax
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="39d84-109">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="39d84-109">Properties</span></span>

|<span data-ttu-id="39d84-110">Egenskap</span><span class="sxs-lookup"><span data-stu-id="39d84-110">Property</span></span> |<span data-ttu-id="39d84-111">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="39d84-111">Description</span></span> |
|---|---|
|<span data-ttu-id="39d84-112">Namn</span><span class="sxs-lookup"><span data-stu-id="39d84-112">GroupName</span></span> |<span data-ttu-id="39d84-113">Namnen på de grupper som du vill säkerställa ett enskilt tillstånd för.</span><span class="sxs-lookup"><span data-stu-id="39d84-113">The names of the groups for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="39d84-114">Medlemmar</span><span class="sxs-lookup"><span data-stu-id="39d84-114">Members</span></span> |<span data-ttu-id="39d84-115">Använd den här egenskapen för att ersätta det aktuella grupp medlemskapet med de angivna medlemmarna.</span><span class="sxs-lookup"><span data-stu-id="39d84-115">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="39d84-116">Värdet för den här egenskapen är en matris med strängar i formuläret `Domain\UserName` .</span><span class="sxs-lookup"><span data-stu-id="39d84-116">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="39d84-117">Om du ställer in den här egenskapen i en konfiguration ska du inte använda någon av egenskaperna **MembersToExclude** eller **MembersToInclude** .</span><span class="sxs-lookup"><span data-stu-id="39d84-117">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="39d84-118">Om du gör det skapas ett fel.</span><span class="sxs-lookup"><span data-stu-id="39d84-118">Doing so will generate an error.</span></span> |
|<span data-ttu-id="39d84-119">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="39d84-119">MembersToInclude</span></span> |<span data-ttu-id="39d84-120">Använd den här egenskapen för att lägga till medlemmar i det befintliga medlemskapet i gruppen.</span><span class="sxs-lookup"><span data-stu-id="39d84-120">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="39d84-121">Värdet för den här egenskapen är en matris med strängar i formuläret `Domain\UserName` .</span><span class="sxs-lookup"><span data-stu-id="39d84-121">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="39d84-122">Om du ställer in den här egenskapen i en konfiguration ska du inte använda egenskapen **medlemmar** .</span><span class="sxs-lookup"><span data-stu-id="39d84-122">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="39d84-123">Om du gör det skapas ett fel.</span><span class="sxs-lookup"><span data-stu-id="39d84-123">Doing so will generate an error.</span></span> |
|<span data-ttu-id="39d84-124">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="39d84-124">MembersToExclude</span></span> |<span data-ttu-id="39d84-125">Använd den här egenskapen för att ta bort medlemmar från de befintliga medlemskapet i grupperna.</span><span class="sxs-lookup"><span data-stu-id="39d84-125">Use this property to remove members from the existing membership of the groups.</span></span> <span data-ttu-id="39d84-126">Värdet för den här egenskapen är en matris med strängar i formuläret `Domain\UserName` .</span><span class="sxs-lookup"><span data-stu-id="39d84-126">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="39d84-127">Om du ställer in den här egenskapen i en konfiguration ska du inte använda egenskapen **medlemmar** .</span><span class="sxs-lookup"><span data-stu-id="39d84-127">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="39d84-128">Om du gör det skapas ett fel.</span><span class="sxs-lookup"><span data-stu-id="39d84-128">Doing so will generate an error.</span></span> |
|<span data-ttu-id="39d84-129">Autentiseringsuppgift</span><span class="sxs-lookup"><span data-stu-id="39d84-129">Credential</span></span> |<span data-ttu-id="39d84-130">De autentiseringsuppgifter som krävs för att komma åt fjär resurser.</span><span class="sxs-lookup"><span data-stu-id="39d84-130">The credentials required to access remote resources.</span></span> <span data-ttu-id="39d84-131">Det här kontot måste ha rätt Active Directory behörighet för att lägga till alla icke-lokala konton i gruppen. annars sker ett fel.</span><span class="sxs-lookup"><span data-stu-id="39d84-131">This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error will occur.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="39d84-132">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="39d84-132">Common properties</span></span>

|<span data-ttu-id="39d84-133">Egenskap</span><span class="sxs-lookup"><span data-stu-id="39d84-133">Property</span></span> |<span data-ttu-id="39d84-134">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="39d84-134">Description</span></span> |
|---|---|
|<span data-ttu-id="39d84-135">DependsOn</span><span class="sxs-lookup"><span data-stu-id="39d84-135">DependsOn</span></span> |<span data-ttu-id="39d84-136">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="39d84-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="39d84-137">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="39d84-137">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="39d84-138">Kontrol</span><span class="sxs-lookup"><span data-stu-id="39d84-138">Ensure</span></span> |<span data-ttu-id="39d84-139">Anger om grupperna finns.</span><span class="sxs-lookup"><span data-stu-id="39d84-139">Indicates whether the groups exist.</span></span> <span data-ttu-id="39d84-140">Ange den här egenskapen som **saknas** för att se till att grupperna inte finns.</span><span class="sxs-lookup"><span data-stu-id="39d84-140">Set this property to **Absent** to ensure that the groups do not exist.</span></span> <span data-ttu-id="39d84-141">Att ställa in det för att **Visa** ser till att grupperna finns.</span><span class="sxs-lookup"><span data-stu-id="39d84-141">Setting it to **Present** ensures that the groups exist.</span></span> <span data-ttu-id="39d84-142">Standardvärdet finns **.**</span><span class="sxs-lookup"><span data-stu-id="39d84-142">The default value is **Present** .</span></span> |
|<span data-ttu-id="39d84-143">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="39d84-143">PsDscRunAsCredential</span></span> |<span data-ttu-id="39d84-144">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="39d84-144">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="39d84-145">Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="39d84-145">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="39d84-146">Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="39d84-146">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example-1-ensuring-groups-are-present"></a><span data-ttu-id="39d84-147">Exempel 1: se till att grupper finns</span><span class="sxs-lookup"><span data-stu-id="39d84-147">Example 1: Ensuring Groups are present</span></span>

<span data-ttu-id="39d84-148">I följande exempel visas hur du ser till att två grupper som kallas "min grupp" och "myOtherGroup" finns.</span><span class="sxs-lookup"><span data-stu-id="39d84-148">The following example shows how to ensure that two groups called "myGroup" and "myOtherGroup" are present.</span></span>

```powershell
configuration GroupSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        GroupSet GroupSetTest
        {
            GroupName        = @("myGroup", "myOtherGroup")
            Ensure           = "Present"
            MembersToInclude = @("contoso\alice", "contoso\bob")
            MembersToExclude = $("contoso\john")
            Credential       = Get-Credential
        }
    }
}
$cd = @{
    AllNodes = @(
        @{
            NodeName                    = 'localhost'
            PSDscAllowPlainTextPassword = $true
            PSDscAllowDomainUser        = $true
        }
    )
}

GroupSetTest -ConfigurationData $cd
```

> [!NOTE]
> <span data-ttu-id="39d84-149">I det här exemplet används autentiseringsuppgifter för oformaterad text för enkelhet.</span><span class="sxs-lookup"><span data-stu-id="39d84-149">This example uses plaintext credentials for simplicity.</span></span> <span data-ttu-id="39d84-150">Information om hur du krypterar autentiseringsuppgifter i MOF-konfigurationsfilen finns i [skydda MOF-filen](../../../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="39d84-150">For information about how to encrypt credentials in the configuration MOF file, see [Securing the MOF File](../../../pull-server/secureMOF.md).</span></span>
