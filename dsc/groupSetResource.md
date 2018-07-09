---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
description: Är en mekanism för att hantera lokala grupper på målnoden.
title: DSC GroupSet-resurs
ms.openlocfilehash: 487a76ca7703b2c57b940b4c5bd176eada6c8019
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892434"
---
# <a name="dsc-groupset-resource"></a><span data-ttu-id="af01b-104">DSC GroupSet-resurs</span><span class="sxs-lookup"><span data-stu-id="af01b-104">DSC GroupSet Resource</span></span>

> <span data-ttu-id="af01b-105">Gäller för: Windows Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="af01b-105">Applies To: Windows Windows PowerShell 5.0</span></span>

<span data-ttu-id="af01b-106">Den **GroupSet** resursen i Windows PowerShell Desired State Configuration (DSC) ger dig möjlighet att hantera lokala grupper på målnoden.</span><span class="sxs-lookup"><span data-stu-id="af01b-106">The **GroupSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span> <span data-ttu-id="af01b-107">Den här resursen är en [sammansatta resource](authoringResourceComposite.md) som anropar den [gruppen resource](groupResource.md) för varje grupp som anges i den `GroupName` parametern.</span><span class="sxs-lookup"><span data-stu-id="af01b-107">This resource is a [composite resource](authoringResourceComposite.md) that calls the [Group resource](groupResource.md) for each group specified in the `GroupName` parameter.</span></span>

<span data-ttu-id="af01b-108">Använd den här resursen när du vill lägga till och/eller ta bort samma listan över medlemmar i mer än en grupp, ta bort mer än en grupp eller lägga till mer än en grupp med samma lista över medlemmar.</span><span class="sxs-lookup"><span data-stu-id="af01b-108">Use this resource when you want to add and/or remove the same list of members to more than one group, remove more than one group, or add more than one group with the same list of members.</span></span>

## <a name="syntax"></a><span data-ttu-id="af01b-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="af01b-109">Syntax</span></span>

```
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="af01b-110">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="af01b-110">Properties</span></span>

|  <span data-ttu-id="af01b-111">Egenskap</span><span class="sxs-lookup"><span data-stu-id="af01b-111">Property</span></span>  |  <span data-ttu-id="af01b-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="af01b-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="af01b-113">Gruppnamn</span><span class="sxs-lookup"><span data-stu-id="af01b-113">GroupName</span></span>| <span data-ttu-id="af01b-114">Namnen på de grupper som du vill se till att ett visst tillstånd.</span><span class="sxs-lookup"><span data-stu-id="af01b-114">The names of the groups for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="af01b-115">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="af01b-115">MembersToExclude</span></span>| <span data-ttu-id="af01b-116">Använd den här egenskapen att ta bort medlemmar från det befintliga medlemskapet i grupperna.</span><span class="sxs-lookup"><span data-stu-id="af01b-116">Use this property to remove members from the existing membership of the groups.</span></span> <span data-ttu-id="af01b-117">Värdet för den här egenskapen är en matris med strängar i formatet *domän*\\*användarnamn*.</span><span class="sxs-lookup"><span data-stu-id="af01b-117">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="af01b-118">Om du ställer in den här egenskapen i en konfiguration, Använd inte den **medlemmar** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="af01b-118">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="af01b-119">Detta genererar ett fel.</span><span class="sxs-lookup"><span data-stu-id="af01b-119">Doing so will generate an error.</span></span>|
| <span data-ttu-id="af01b-120">Autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="af01b-120">Credential</span></span>| <span data-ttu-id="af01b-121">De autentiseringsuppgifter som krävs för att få åtkomst till fjärranslutna resurser.</span><span class="sxs-lookup"><span data-stu-id="af01b-121">The credentials required to access remote resources.</span></span> <span data-ttu-id="af01b-122">**Obs**: det här kontot måste ha behörighet att lägga till alla icke-lokala konton i gruppen Active Directory, annars uppstår ett fel.</span><span class="sxs-lookup"><span data-stu-id="af01b-122">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error will occur.</span></span>
| <span data-ttu-id="af01b-123">Se till att</span><span class="sxs-lookup"><span data-stu-id="af01b-123">Ensure</span></span>| <span data-ttu-id="af01b-124">Anger om det finns grupperna.</span><span class="sxs-lookup"><span data-stu-id="af01b-124">Indicates whether the groups exist.</span></span> <span data-ttu-id="af01b-125">Ange den här egenskapen till ”” så att grupperna som inte finns.</span><span class="sxs-lookup"><span data-stu-id="af01b-125">Set this property to "Absent" to ensure that the groups do not exist.</span></span> <span data-ttu-id="af01b-126">Ange värdet till ”Visa” (standardvärdet) säkerställer att grupperna som finns.</span><span class="sxs-lookup"><span data-stu-id="af01b-126">Setting it to "Present" (the default value) ensures that the groups exist.</span></span>|
| <span data-ttu-id="af01b-127">Medlemmar</span><span class="sxs-lookup"><span data-stu-id="af01b-127">Members</span></span>| <span data-ttu-id="af01b-128">Använd den här egenskapen för att ersätta det aktuella gruppmedlemskapet med de angivna medlemmarna.</span><span class="sxs-lookup"><span data-stu-id="af01b-128">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="af01b-129">Värdet för den här egenskapen är en matris med strängar i formatet *domän*\\*användarnamn*.</span><span class="sxs-lookup"><span data-stu-id="af01b-129">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="af01b-130">Om du anger den här egenskapen i en konfiguration kan inte använda antingen den **MembersToExclude** eller **MembersToInclude** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="af01b-130">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="af01b-131">Detta genererar ett fel.</span><span class="sxs-lookup"><span data-stu-id="af01b-131">Doing so will generate an error.</span></span>|
| <span data-ttu-id="af01b-132">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="af01b-132">MembersToInclude</span></span>| <span data-ttu-id="af01b-133">Använd den här egenskapen för att lägga till medlemmar i det befintliga medlemskapet i gruppen.</span><span class="sxs-lookup"><span data-stu-id="af01b-133">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="af01b-134">Värdet för den här egenskapen är en matris med strängar i formatet *domän*\\*användarnamn*.</span><span class="sxs-lookup"><span data-stu-id="af01b-134">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="af01b-135">Om du ställer in den här egenskapen i en konfiguration, Använd inte den **medlemmar** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="af01b-135">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="af01b-136">Detta genererar ett fel.</span><span class="sxs-lookup"><span data-stu-id="af01b-136">Doing so will generate an error.</span></span>|
| <span data-ttu-id="af01b-137">DependsOn</span><span class="sxs-lookup"><span data-stu-id="af01b-137">DependsOn</span></span> | <span data-ttu-id="af01b-138">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="af01b-138">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="af01b-139">Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är __ResourceName__ och är av typen __ResourceType__, syntaxen för den här egenskapen är ”DependsOn =” [ ResourceType] ResourceName ”''.</span><span class="sxs-lookup"><span data-stu-id="af01b-139">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example-1-ensuring-groups-are-present"></a><span data-ttu-id="af01b-140">Exempel 1: Säkerställa grupper finns</span><span class="sxs-lookup"><span data-stu-id="af01b-140">Example 1: Ensuring Groups are present</span></span>

<span data-ttu-id="af01b-141">I följande exempel visar hur du se till att det finns två grupper som kallas ”myGroup” och ”myOtherGroup”.</span><span class="sxs-lookup"><span data-stu-id="af01b-141">The following example shows how to ensure that two groups called "myGroup" and "myOtherGroup" are present.</span></span>

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
> <span data-ttu-id="af01b-142">Det här exemplet använder autentiseringsuppgifter i klartext för enkelhetens skull.</span><span class="sxs-lookup"><span data-stu-id="af01b-142">This example uses plaintext credentials for simplicity.</span></span> <span data-ttu-id="af01b-143">Information om hur du krypterar autentiseringsuppgifterna i MOF-konfigurationsfilen finns i [skydda MOF-filen](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="af01b-143">For information about how to encrypt credentials in the configuration MOF file, see [Securing the MOF File](secureMOF.md).</span></span>
