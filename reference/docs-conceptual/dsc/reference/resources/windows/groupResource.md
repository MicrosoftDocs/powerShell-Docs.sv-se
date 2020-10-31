---
ms.date: 07/16/2020
ms.topic: reference
title: DSC-gruppresurs
description: DSC-gruppresurs
ms.openlocfilehash: 8e2d1139c9573d7e310fec2410b14df04b79e1b2
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142454"
---
# <a name="dsc-group-resource"></a><span data-ttu-id="8220c-103">DSC-gruppresurs</span><span class="sxs-lookup"><span data-stu-id="8220c-103">DSC Group Resource</span></span>

> <span data-ttu-id="8220c-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5. x</span><span class="sxs-lookup"><span data-stu-id="8220c-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="8220c-105">**Grupp** resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera lokala grupper på målnoden.</span><span class="sxs-lookup"><span data-stu-id="8220c-105">The **Group** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span>

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a><span data-ttu-id="8220c-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="8220c-106">Syntax</span></span>

```Syntax
Group [string] #ResourceName
{
    GroupName = [string]
    [ Credential = [PSCredential] ]
    [ Description = [string[]] ]
    [ Members = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="8220c-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="8220c-107">Properties</span></span>

|<span data-ttu-id="8220c-108">Egenskap</span><span class="sxs-lookup"><span data-stu-id="8220c-108">Property</span></span> |<span data-ttu-id="8220c-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8220c-109">Description</span></span> |
|---|---|
|<span data-ttu-id="8220c-110">Namn</span><span class="sxs-lookup"><span data-stu-id="8220c-110">GroupName</span></span> |<span data-ttu-id="8220c-111">Namnet på den grupp som du vill säkerställa ett speciellt tillstånd för.</span><span class="sxs-lookup"><span data-stu-id="8220c-111">The name of the group for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="8220c-112">Autentiseringsuppgift</span><span class="sxs-lookup"><span data-stu-id="8220c-112">Credential</span></span> |<span data-ttu-id="8220c-113">De autentiseringsuppgifter som krävs för att komma åt fjär resurser.</span><span class="sxs-lookup"><span data-stu-id="8220c-113">The credentials required to access remote resources.</span></span> <span data-ttu-id="8220c-114">Det här kontot måste ha rätt Active Directory behörighet för att lägga till alla icke-lokala konton i gruppen. annars inträffar ett fel när konfigurationen körs på målnoden.</span><span class="sxs-lookup"><span data-stu-id="8220c-114">This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error occurs when the configuration is executed on the target node.</span></span>
|<span data-ttu-id="8220c-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8220c-115">Description</span></span> |<span data-ttu-id="8220c-116">Beskrivning av gruppen.</span><span class="sxs-lookup"><span data-stu-id="8220c-116">The description of the group.</span></span> |
|<span data-ttu-id="8220c-117">Medlemmar</span><span class="sxs-lookup"><span data-stu-id="8220c-117">Members</span></span> |<span data-ttu-id="8220c-118">Använd den här egenskapen för att ersätta det aktuella grupp medlemskapet med de angivna medlemmarna.</span><span class="sxs-lookup"><span data-stu-id="8220c-118">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="8220c-119">Värdet för den här egenskapen är en matris med strängar i formuläret `Domain\UserName` .</span><span class="sxs-lookup"><span data-stu-id="8220c-119">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="8220c-120">Om du ställer in den här egenskapen i en konfiguration ska du inte använda någon av egenskaperna **MembersToExclude** eller **MembersToInclude** .</span><span class="sxs-lookup"><span data-stu-id="8220c-120">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="8220c-121">Detta genererar ett fel.</span><span class="sxs-lookup"><span data-stu-id="8220c-121">Doing so generates an error.</span></span> |
|<span data-ttu-id="8220c-122">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="8220c-122">MembersToExclude</span></span> |<span data-ttu-id="8220c-123">Använd den här egenskapen för att ta bort medlemmar från det befintliga medlemskapet i gruppen.</span><span class="sxs-lookup"><span data-stu-id="8220c-123">Use this property to remove members from the existing membership of the group.</span></span> <span data-ttu-id="8220c-124">Värdet för den här egenskapen är en matris med strängar i formuläret `Domain\UserName` .</span><span class="sxs-lookup"><span data-stu-id="8220c-124">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="8220c-125">Om du ställer in den här egenskapen i en konfiguration ska du inte använda egenskapen **medlemmar** .</span><span class="sxs-lookup"><span data-stu-id="8220c-125">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="8220c-126">Detta genererar ett fel.</span><span class="sxs-lookup"><span data-stu-id="8220c-126">Doing so generates an error.</span></span> |
|<span data-ttu-id="8220c-127">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="8220c-127">MembersToInclude</span></span> |<span data-ttu-id="8220c-128">Använd den här egenskapen för att lägga till medlemmar i det befintliga medlemskapet i gruppen.</span><span class="sxs-lookup"><span data-stu-id="8220c-128">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="8220c-129">Värdet för den här egenskapen är en matris med strängar i formuläret `Domain\UserName` .</span><span class="sxs-lookup"><span data-stu-id="8220c-129">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="8220c-130">Om du ställer in den här egenskapen i en konfiguration ska du inte använda egenskapen **medlemmar** .</span><span class="sxs-lookup"><span data-stu-id="8220c-130">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="8220c-131">Om du gör det skapas ett fel.</span><span class="sxs-lookup"><span data-stu-id="8220c-131">Doing so will generate an error.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="8220c-132">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="8220c-132">Common properties</span></span>

|<span data-ttu-id="8220c-133">Egenskap</span><span class="sxs-lookup"><span data-stu-id="8220c-133">Property</span></span> |<span data-ttu-id="8220c-134">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8220c-134">Description</span></span> |
|---|---|
|<span data-ttu-id="8220c-135">DependsOn</span><span class="sxs-lookup"><span data-stu-id="8220c-135">DependsOn</span></span> |<span data-ttu-id="8220c-136">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="8220c-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="8220c-137">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="8220c-137">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="8220c-138">Kontrol</span><span class="sxs-lookup"><span data-stu-id="8220c-138">Ensure</span></span> |<span data-ttu-id="8220c-139">Anger om gruppen finns.</span><span class="sxs-lookup"><span data-stu-id="8220c-139">Indicates if the group exists.</span></span> <span data-ttu-id="8220c-140">Ange den här egenskapen som **saknas** för att säkerställa att gruppen inte finns.</span><span class="sxs-lookup"><span data-stu-id="8220c-140">Set this property to **Absent** to ensure that the group does not exist.</span></span> <span data-ttu-id="8220c-141">Att ställa in det för att **Visa** garanterar att gruppen finns.</span><span class="sxs-lookup"><span data-stu-id="8220c-141">Setting it to **Present** ensures that the group exists.</span></span> <span data-ttu-id="8220c-142">Standardvärdet finns **.**</span><span class="sxs-lookup"><span data-stu-id="8220c-142">The default value is **Present** .</span></span> |
|<span data-ttu-id="8220c-143">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="8220c-143">PsDscRunAsCredential</span></span> |<span data-ttu-id="8220c-144">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="8220c-144">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="8220c-145">Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="8220c-145">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="8220c-146">Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="8220c-146">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example-1-ensure-group-is-not-present"></a><span data-ttu-id="8220c-147">Exempel 1: kontrol lera att gruppen inte finns</span><span class="sxs-lookup"><span data-stu-id="8220c-147">Example 1: Ensure group is not present</span></span>

<span data-ttu-id="8220c-148">I följande exempel visas hur du ser till att en grupp med namnet "TestGroup" saknas.</span><span class="sxs-lookup"><span data-stu-id="8220c-148">The following example shows how to ensure that a group called "TestGroup" is absent.</span></span>

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present"
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```

## <a name="example-2-add-domain-user-to-local-group"></a><span data-ttu-id="8220c-149">Exempel 2: Lägg till domän användare i lokal grupp</span><span class="sxs-lookup"><span data-stu-id="8220c-149">Example 2: Add domain user to local group</span></span>

<span data-ttu-id="8220c-150">I följande exempel visas hur du lägger till en Active Directory användare i den lokala gruppen Administratörer som en del av en labb version med flera datorer där du redan använder en PSCredential för det lokala administratörs kontot.</span><span class="sxs-lookup"><span data-stu-id="8220c-150">The following example shows how to add an Active Directory User to the local administrators group as part of a Multi-Machine Lab build where you are already using a PSCredential for the Local Administrator account.</span></span> <span data-ttu-id="8220c-151">Eftersom detta också används för domän administratörs kontot (efter domän befordran), måste du konvertera det befintliga PSCredential till en domän med egna autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="8220c-151">As this is also used for the Domain Admin Account (after Domain promotion), we then need to convert this existing PSCredential to a Domain Friendly credential.</span></span> <span data-ttu-id="8220c-152">Sedan kan vi lägga till en domän användare i den lokala gruppen Administratörer på medlems servern.</span><span class="sxs-lookup"><span data-stu-id="8220c-152">Then we can add a Domain User to the Local Administrators Group on the Member server.</span></span>

```powershell
@{
    AllNodes = @(
        @{
            NodeName = '*';
            DomainName = 'SubTest.contoso.com';
         }
        @{
            NodeName = 'Box2';
            AdminAccount = 'Admin-Dave_Alexanderson'
        }
    )
}

$domain = $node.DomainName.split('.')[0]
$DCredential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList ("$domain\$($credential.Username)", $Credential.Password)

Group AddADUserToLocalAdminGroup {
    GroupName='Administrators'
    Ensure= 'Present'
    MembersToInclude= "$domain\$($Node.AdminAccount)"
    Credential = $dCredential
    PsDscRunAsCredential = $DCredential
}
```

## <a name="example-3"></a><span data-ttu-id="8220c-153">Exempel 3</span><span class="sxs-lookup"><span data-stu-id="8220c-153">Example 3</span></span>

<span data-ttu-id="8220c-154">I följande exempel visas hur du ser till att en lokal grupp, TigerTeamAdmins, på Server TigerTeamSource.Contoso.Com inte innehåller ett visst domän konto, Contoso\JerryG.</span><span class="sxs-lookup"><span data-stu-id="8220c-154">The following example shows how to ensure a local group, TigerTeamAdmins, on the server TigerTeamSource.Contoso.Com does not contain a particular domain account, Contoso\JerryG.</span></span>

```powershell
Configuration SecureTigerTeamSource {
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node TigerTeamSource.Contoso.Com {
        Group TigerTeamAdmins {
            GroupName        = 'TigerTeamAdmins'
            Ensure           = 'Present'
            MembersToExclude = "Contoso\JerryG"
        }
    }
}
```
