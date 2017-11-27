---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
description: "Tillhandahåller en mekanism för att hantera lokala grupper på målnoden."
title: DSC GroupSet resurs
ms.openlocfilehash: 0907a968bfc660adc873c28e8be6572d1d5cb993
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-groupset-resource"></a><span data-ttu-id="4a56c-104">DSC GroupSet resurs</span><span class="sxs-lookup"><span data-stu-id="4a56c-104">DSC GroupSet Resource</span></span>

> <span data-ttu-id="4a56c-105">Gäller för: Windows Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4a56c-105">Applies To: Windows Windows PowerShell 5.0</span></span>

<span data-ttu-id="4a56c-106">Den **GroupSet** resurs i Windows PowerShell önskad tillstånd Configuration (DSC) ger dig möjlighet att hantera lokala grupper på målnoden.</span><span class="sxs-lookup"><span data-stu-id="4a56c-106">The **GroupSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span> <span data-ttu-id="4a56c-107">Resursen är en [sammansatta resurs](authoringResourceComposite.md) som anropar den [gruppen resurs](groupResource.md) för varje grupp som anges i den `GroupName` parameter.</span><span class="sxs-lookup"><span data-stu-id="4a56c-107">This resource is a [composite resource](authoringResourceComposite.md) that calls the [Group resource](groupResource.md) for each group specified in the `GroupName` parameter.</span></span>

<span data-ttu-id="4a56c-108">Använd den här resursen när du vill lägga till och/eller ta bort samma lista över medlemmar i mer än en grupp, ta bort mer än en grupp eller Lägg till mer än en grupp med samma lista över medlemmar.</span><span class="sxs-lookup"><span data-stu-id="4a56c-108">Use this resource when you want to add and/or remove the same list of members to more than one group, remove more than one group, or add more than one group with the same list of members.</span></span>

##<a name="syntax"></a><span data-ttu-id="4a56c-109">Syntaxen ##</span><span class="sxs-lookup"><span data-stu-id="4a56c-109">Syntax##</span></span>
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

## <a name="properties"></a><span data-ttu-id="4a56c-110">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="4a56c-110">Properties</span></span>

|  <span data-ttu-id="4a56c-111">Egenskap</span><span class="sxs-lookup"><span data-stu-id="4a56c-111">Property</span></span>  |  <span data-ttu-id="4a56c-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4a56c-112">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="4a56c-113">Gruppnamn</span><span class="sxs-lookup"><span data-stu-id="4a56c-113">GroupName</span></span>| <span data-ttu-id="4a56c-114">Namnen på de grupper som du vill se till att ett visst tillstånd.</span><span class="sxs-lookup"><span data-stu-id="4a56c-114">The names of the groups for which you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="4a56c-115">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="4a56c-115">MembersToExclude</span></span>| <span data-ttu-id="4a56c-116">Använd den här egenskapen för att ta bort medlemmar från det befintliga medlemskapet i grupperna.</span><span class="sxs-lookup"><span data-stu-id="4a56c-116">Use this property to remove members from the existing membership of the groups.</span></span> <span data-ttu-id="4a56c-117">Värdet för den här egenskapen är en matris med strängar i formuläret *domän*\\*användarnamn*.</span><span class="sxs-lookup"><span data-stu-id="4a56c-117">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="4a56c-118">Om du anger den här egenskapen i en konfiguration kan du inte använda den **medlemmar** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="4a56c-118">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="4a56c-119">Detta genererar ett fel.</span><span class="sxs-lookup"><span data-stu-id="4a56c-119">Doing so will generate an error.</span></span>| 
| <span data-ttu-id="4a56c-120">autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="4a56c-120">Credential</span></span>| <span data-ttu-id="4a56c-121">De autentiseringsuppgifter som krävs för att komma åt fjärresurser.</span><span class="sxs-lookup"><span data-stu-id="4a56c-121">The credentials required to access remote resources.</span></span> <span data-ttu-id="4a56c-122">**Obs**: det här kontot måste ha behörighet att lägga till alla icke-lokala konton i gruppen Active Directory, annars uppstår ett fel.</span><span class="sxs-lookup"><span data-stu-id="4a56c-122">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error will occur.</span></span>
| <span data-ttu-id="4a56c-123">Se till att</span><span class="sxs-lookup"><span data-stu-id="4a56c-123">Ensure</span></span>| <span data-ttu-id="4a56c-124">Anger om det finns grupperna.</span><span class="sxs-lookup"><span data-stu-id="4a56c-124">Indicates whether the groups exist.</span></span> <span data-ttu-id="4a56c-125">Ange den här egenskapen till ”saknas” för att se till att grupperna inte finns.</span><span class="sxs-lookup"><span data-stu-id="4a56c-125">Set this property to "Absent" to ensure that the groups do not exist.</span></span> <span data-ttu-id="4a56c-126">Ange värdet ”finns” (standardvärdet) ser du till att grupperna finns.</span><span class="sxs-lookup"><span data-stu-id="4a56c-126">Setting it to "Present" (the default value) ensures that the groups exist.</span></span>| 
| <span data-ttu-id="4a56c-127">Medlemmar</span><span class="sxs-lookup"><span data-stu-id="4a56c-127">Members</span></span>| <span data-ttu-id="4a56c-128">Använd den här egenskapen för att ersätta det aktuella gruppmedlemskapet med de angivna medlemmarna.</span><span class="sxs-lookup"><span data-stu-id="4a56c-128">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="4a56c-129">Värdet för den här egenskapen är en matris med strängar i formuläret *domän*\\*användarnamn*.</span><span class="sxs-lookup"><span data-stu-id="4a56c-129">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="4a56c-130">Om du anger den här egenskapen i en konfiguration, bör inte använda någon av **MembersToExclude** eller **MembersToInclude** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="4a56c-130">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="4a56c-131">Detta genererar ett fel.</span><span class="sxs-lookup"><span data-stu-id="4a56c-131">Doing so will generate an error.</span></span>| 
| <span data-ttu-id="4a56c-132">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="4a56c-132">MembersToInclude</span></span>| <span data-ttu-id="4a56c-133">Använd den här egenskapen för att lägga till medlemmar i det befintliga medlemskapet i gruppen.</span><span class="sxs-lookup"><span data-stu-id="4a56c-133">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="4a56c-134">Värdet för den här egenskapen är en matris med strängar i formuläret *domän*\\*användarnamn*.</span><span class="sxs-lookup"><span data-stu-id="4a56c-134">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="4a56c-135">Om du anger den här egenskapen i en konfiguration kan du inte använda den **medlemmar** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="4a56c-135">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="4a56c-136">Detta genererar ett fel.</span><span class="sxs-lookup"><span data-stu-id="4a56c-136">Doing so will generate an error.</span></span>| 
| <span data-ttu-id="4a56c-137">dependsOn</span><span class="sxs-lookup"><span data-stu-id="4a56c-137">DependsOn</span></span> | <span data-ttu-id="4a56c-138">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="4a56c-138">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="4a56c-139">Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis __ResourceName__ och dess typ är __ResourceType__, syntaxen för den här egenskapen är ”DependsOn =” [ResourceType] ResourceName ”''.</span><span class="sxs-lookup"><span data-stu-id="4a56c-139">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`\`.</span></span>| 

## <a name="example-1"></a><span data-ttu-id="4a56c-140">Exempel 1</span><span class="sxs-lookup"><span data-stu-id="4a56c-140">Example 1</span></span>

<span data-ttu-id="4a56c-141">I följande exempel visas hur du kontrollerar att det finns två grupper som kallas ”myGroup” och ”myOtherGroup”.</span><span class="sxs-lookup"><span data-stu-id="4a56c-141">The following example shows how to ensure that two groups called "myGroup" and "myOtherGroup" are present.</span></span> 

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

><span data-ttu-id="4a56c-142">**Obs:** det här exemplet använder autentiseringsuppgifter i klartext för enkelhetens skull.</span><span class="sxs-lookup"><span data-stu-id="4a56c-142">**Note:** This example uses plaintext credentials for simplicity.</span></span> <span data-ttu-id="4a56c-143">Information om hur du krypterar autentiseringsuppgifter i MOF-konfigurationsfilen finns [skydda MOF-filen](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="4a56c-143">For information about how to encrypt credentials in the configuration MOF file, see [Securing the MOF File](secureMOF.md).</span></span>


