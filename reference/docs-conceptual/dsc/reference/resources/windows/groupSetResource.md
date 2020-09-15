---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
description: Tillhandahåller en mekanism för att hantera lokala grupper på målnoden.
title: DSC GroupSet-resurs
ms.openlocfilehash: 90e0c3f0e09c6a300988869265dfdb432ed5d217
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464204"
---
# <a name="dsc-groupset-resource"></a><span data-ttu-id="7d428-104">DSC GroupSet-resurs</span><span class="sxs-lookup"><span data-stu-id="7d428-104">DSC GroupSet Resource</span></span>

> <span data-ttu-id="7d428-105">Gäller för: Windows PowerShell 5. x</span><span class="sxs-lookup"><span data-stu-id="7d428-105">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="7d428-106">**GroupSet** -resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera lokala grupper på målnoden.</span><span class="sxs-lookup"><span data-stu-id="7d428-106">The **GroupSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span> <span data-ttu-id="7d428-107">Den här resursen är en [sammansatt resurs](../../../resources/authoringResourceComposite.md) som anropar [grupp resursen](groupResource.md) för varje grupp som anges i `GroupName` parametern.</span><span class="sxs-lookup"><span data-stu-id="7d428-107">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [Group resource](groupResource.md) for each group specified in the `GroupName` parameter.</span></span>

<span data-ttu-id="7d428-108">Använd den här resursen när du vill lägga till och/eller ta bort samma lista med medlemmar till mer än en grupp, ta bort mer än en grupp eller lägga till mer än en grupp med samma lista med medlemmar.</span><span class="sxs-lookup"><span data-stu-id="7d428-108">Use this resource when you want to add and/or remove the same list of members to more than one group, remove more than one group, or add more than one group with the same list of members.</span></span>

## <a name="syntax"></a><span data-ttu-id="7d428-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="7d428-109">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="7d428-110">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="7d428-110">Properties</span></span>

|<span data-ttu-id="7d428-111">Egenskap</span><span class="sxs-lookup"><span data-stu-id="7d428-111">Property</span></span> |<span data-ttu-id="7d428-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d428-112">Description</span></span> |
|---|---|
|<span data-ttu-id="7d428-113">Namn</span><span class="sxs-lookup"><span data-stu-id="7d428-113">GroupName</span></span> |<span data-ttu-id="7d428-114">Namnen på de grupper som du vill säkerställa ett enskilt tillstånd för.</span><span class="sxs-lookup"><span data-stu-id="7d428-114">The names of the groups for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="7d428-115">Medlemmar</span><span class="sxs-lookup"><span data-stu-id="7d428-115">Members</span></span> |<span data-ttu-id="7d428-116">Använd den här egenskapen för att ersätta det aktuella grupp medlemskapet med de angivna medlemmarna.</span><span class="sxs-lookup"><span data-stu-id="7d428-116">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="7d428-117">Värdet för den här egenskapen är en matris med strängar i formuläret `Domain\UserName` .</span><span class="sxs-lookup"><span data-stu-id="7d428-117">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="7d428-118">Om du ställer in den här egenskapen i en konfiguration ska du inte använda någon av egenskaperna **MembersToExclude** eller **MembersToInclude** .</span><span class="sxs-lookup"><span data-stu-id="7d428-118">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="7d428-119">Om du gör det skapas ett fel.</span><span class="sxs-lookup"><span data-stu-id="7d428-119">Doing so will generate an error.</span></span> |
|<span data-ttu-id="7d428-120">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="7d428-120">MembersToInclude</span></span> |<span data-ttu-id="7d428-121">Använd den här egenskapen för att lägga till medlemmar i det befintliga medlemskapet i gruppen.</span><span class="sxs-lookup"><span data-stu-id="7d428-121">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="7d428-122">Värdet för den här egenskapen är en matris med strängar i formuläret `Domain\UserName` .</span><span class="sxs-lookup"><span data-stu-id="7d428-122">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="7d428-123">Om du ställer in den här egenskapen i en konfiguration ska du inte använda egenskapen **medlemmar** .</span><span class="sxs-lookup"><span data-stu-id="7d428-123">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="7d428-124">Om du gör det skapas ett fel.</span><span class="sxs-lookup"><span data-stu-id="7d428-124">Doing so will generate an error.</span></span> |
|<span data-ttu-id="7d428-125">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="7d428-125">MembersToExclude</span></span> |<span data-ttu-id="7d428-126">Använd den här egenskapen för att ta bort medlemmar från de befintliga medlemskapet i grupperna.</span><span class="sxs-lookup"><span data-stu-id="7d428-126">Use this property to remove members from the existing membership of the groups.</span></span> <span data-ttu-id="7d428-127">Värdet för den här egenskapen är en matris med strängar i formuläret `Domain\UserName` .</span><span class="sxs-lookup"><span data-stu-id="7d428-127">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="7d428-128">Om du ställer in den här egenskapen i en konfiguration ska du inte använda egenskapen **medlemmar** .</span><span class="sxs-lookup"><span data-stu-id="7d428-128">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="7d428-129">Om du gör det skapas ett fel.</span><span class="sxs-lookup"><span data-stu-id="7d428-129">Doing so will generate an error.</span></span> |
|<span data-ttu-id="7d428-130">Autentiseringsuppgift</span><span class="sxs-lookup"><span data-stu-id="7d428-130">Credential</span></span> |<span data-ttu-id="7d428-131">De autentiseringsuppgifter som krävs för att komma åt fjär resurser.</span><span class="sxs-lookup"><span data-stu-id="7d428-131">The credentials required to access remote resources.</span></span> <span data-ttu-id="7d428-132">Det här kontot måste ha rätt Active Directory behörighet för att lägga till alla icke-lokala konton i gruppen. annars sker ett fel.</span><span class="sxs-lookup"><span data-stu-id="7d428-132">This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error will occur.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="7d428-133">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="7d428-133">Common properties</span></span>

|<span data-ttu-id="7d428-134">Egenskap</span><span class="sxs-lookup"><span data-stu-id="7d428-134">Property</span></span> |<span data-ttu-id="7d428-135">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d428-135">Description</span></span> |
|---|---|
|<span data-ttu-id="7d428-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="7d428-136">DependsOn</span></span> |<span data-ttu-id="7d428-137">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="7d428-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7d428-138">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="7d428-138">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="7d428-139">Kontrol</span><span class="sxs-lookup"><span data-stu-id="7d428-139">Ensure</span></span> |<span data-ttu-id="7d428-140">Anger om grupperna finns.</span><span class="sxs-lookup"><span data-stu-id="7d428-140">Indicates whether the groups exist.</span></span> <span data-ttu-id="7d428-141">Ange den här egenskapen som **saknas** för att se till att grupperna inte finns.</span><span class="sxs-lookup"><span data-stu-id="7d428-141">Set this property to **Absent** to ensure that the groups do not exist.</span></span> <span data-ttu-id="7d428-142">Att ställa in det för att **Visa** ser till att grupperna finns.</span><span class="sxs-lookup"><span data-stu-id="7d428-142">Setting it to **Present** ensures that the groups exist.</span></span> <span data-ttu-id="7d428-143">Standardvärdet finns **.**</span><span class="sxs-lookup"><span data-stu-id="7d428-143">The default value is **Present**.</span></span> |
|<span data-ttu-id="7d428-144">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="7d428-144">PsDscRunAsCredential</span></span> |<span data-ttu-id="7d428-145">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="7d428-145">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="7d428-146">Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="7d428-146">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="7d428-147">Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="7d428-147">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example-1-ensuring-groups-are-present"></a><span data-ttu-id="7d428-148">Exempel 1: se till att grupper finns</span><span class="sxs-lookup"><span data-stu-id="7d428-148">Example 1: Ensuring Groups are present</span></span>

<span data-ttu-id="7d428-149">I följande exempel visas hur du ser till att två grupper som kallas "min grupp" och "myOtherGroup" finns.</span><span class="sxs-lookup"><span data-stu-id="7d428-149">The following example shows how to ensure that two groups called "myGroup" and "myOtherGroup" are present.</span></span>

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
> <span data-ttu-id="7d428-150">I det här exemplet används autentiseringsuppgifter för oformaterad text för enkelhet.</span><span class="sxs-lookup"><span data-stu-id="7d428-150">This example uses plaintext credentials for simplicity.</span></span> <span data-ttu-id="7d428-151">Information om hur du krypterar autentiseringsuppgifter i MOF-konfigurationsfilen finns i [skydda MOF-filen](../../../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="7d428-151">For information about how to encrypt credentials in the configuration MOF file, see [Securing the MOF File](../../../pull-server/secureMOF.md).</span></span>
