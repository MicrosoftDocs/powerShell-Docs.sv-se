---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC-Gruppresurs
ms.openlocfilehash: 123e09b54a923af942a15f80fa7291c555b4235f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077355"
---
# <a name="dsc-group-resource"></a><span data-ttu-id="2f3cd-103">DSC-Gruppresurs</span><span class="sxs-lookup"><span data-stu-id="2f3cd-103">DSC Group Resource</span></span>

> <span data-ttu-id="2f3cd-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="2f3cd-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="2f3cd-105">Gruppresurs i Windows PowerShell Desired State Configuration (DSC) är en mekanism för att hantera lokala grupper på målnoden.</span><span class="sxs-lookup"><span data-stu-id="2f3cd-105">The Group resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="2f3cd-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="2f3cd-106">Syntax</span></span>

```
Group [string] #ResourceName
{
    GroupName          = [string]
    [ Credential       = [PSCredential] ]
    [ Description      = [string[]] ]
    [ Ensure           = [string] { Absent | Present }  ]
    [ Members          = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn        = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="2f3cd-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="2f3cd-107">Properties</span></span>

|  <span data-ttu-id="2f3cd-108">Egenskap</span><span class="sxs-lookup"><span data-stu-id="2f3cd-108">Property</span></span>  |  <span data-ttu-id="2f3cd-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2f3cd-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="2f3cd-110">Gruppnamn</span><span class="sxs-lookup"><span data-stu-id="2f3cd-110">GroupName</span></span>| <span data-ttu-id="2f3cd-111">Namnet på gruppen som du vill se till att ett visst tillstånd.</span><span class="sxs-lookup"><span data-stu-id="2f3cd-111">The name of the group for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="2f3cd-112">Autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="2f3cd-112">Credential</span></span>| <span data-ttu-id="2f3cd-113">De autentiseringsuppgifter som krävs för att få åtkomst till fjärranslutna resurser.</span><span class="sxs-lookup"><span data-stu-id="2f3cd-113">The credentials required to access remote resources.</span></span> <span data-ttu-id="2f3cd-114">**Obs**: Det här kontot måste ha behörighet som Active Directory så att lägga till alla icke-lokala konton i gruppen. Annars uppstår ett fel när konfigurationen körs på målnoden.</span><span class="sxs-lookup"><span data-stu-id="2f3cd-114">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error occurs when the configuration is executed on the target node.</span></span>
| <span data-ttu-id="2f3cd-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2f3cd-115">Description</span></span>| <span data-ttu-id="2f3cd-116">Beskrivning av gruppen.</span><span class="sxs-lookup"><span data-stu-id="2f3cd-116">The description of the group.</span></span>|
| <span data-ttu-id="2f3cd-117">Se till att</span><span class="sxs-lookup"><span data-stu-id="2f3cd-117">Ensure</span></span>| <span data-ttu-id="2f3cd-118">Anger om gruppen finns.</span><span class="sxs-lookup"><span data-stu-id="2f3cd-118">Indicates if the group exists.</span></span> <span data-ttu-id="2f3cd-119">Ange den här egenskapen till ”” så att gruppen inte finns.</span><span class="sxs-lookup"><span data-stu-id="2f3cd-119">Set this property to "Absent" to ensure that the group does not exist.</span></span> <span data-ttu-id="2f3cd-120">Ange värdet till ”Visa” (standardvärdet) säkerställer att gruppen finns.</span><span class="sxs-lookup"><span data-stu-id="2f3cd-120">Setting it to "Present" (the default value) ensures that the group exists.</span></span>|
| <span data-ttu-id="2f3cd-121">Medlemmar</span><span class="sxs-lookup"><span data-stu-id="2f3cd-121">Members</span></span>| <span data-ttu-id="2f3cd-122">Använd den här egenskapen för att ersätta det aktuella gruppmedlemskapet med de angivna medlemmarna.</span><span class="sxs-lookup"><span data-stu-id="2f3cd-122">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="2f3cd-123">Värdet för den här egenskapen är en matris med strängar i formatet *domän*\\*användarnamn*.</span><span class="sxs-lookup"><span data-stu-id="2f3cd-123">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="2f3cd-124">Om du anger den här egenskapen i en konfiguration kan inte använda antingen den **MembersToExclude** eller **MembersToInclude** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="2f3cd-124">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="2f3cd-125">Detta genererar ett fel.</span><span class="sxs-lookup"><span data-stu-id="2f3cd-125">Doing so generates an error.</span></span>|
| <span data-ttu-id="2f3cd-126">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="2f3cd-126">MembersToExclude</span></span>| <span data-ttu-id="2f3cd-127">Ta bort medlemmar från det befintliga medlemskapet i gruppen med hjälp av den här egenskapen.</span><span class="sxs-lookup"><span data-stu-id="2f3cd-127">Use this property to remove members from the existing membership of the group.</span></span> <span data-ttu-id="2f3cd-128">Värdet för den här egenskapen är en matris med strängar i formatet *domän*\\*användarnamn*.</span><span class="sxs-lookup"><span data-stu-id="2f3cd-128">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="2f3cd-129">Om du ställer in den här egenskapen i en konfiguration, Använd inte den **medlemmar** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="2f3cd-129">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="2f3cd-130">Detta genererar ett fel.</span><span class="sxs-lookup"><span data-stu-id="2f3cd-130">Doing so generates an error.</span></span>|
| <span data-ttu-id="2f3cd-131">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="2f3cd-131">MembersToInclude</span></span>| <span data-ttu-id="2f3cd-132">Använd den här egenskapen för att lägga till medlemmar i det befintliga medlemskapet i gruppen.</span><span class="sxs-lookup"><span data-stu-id="2f3cd-132">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="2f3cd-133">Värdet för den här egenskapen är en matris med strängar i formatet *domän*\\*användarnamn*.</span><span class="sxs-lookup"><span data-stu-id="2f3cd-133">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="2f3cd-134">Om du ställer in den här egenskapen i en konfiguration, Använd inte den **medlemmar** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="2f3cd-134">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="2f3cd-135">Detta genererar ett fel.</span><span class="sxs-lookup"><span data-stu-id="2f3cd-135">Doing so will generate an error.</span></span>|
| <span data-ttu-id="2f3cd-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="2f3cd-136">DependsOn</span></span> | <span data-ttu-id="2f3cd-137">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="2f3cd-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="2f3cd-138">Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är __ResourceName__ och är av typen __ResourceType__, syntaxen för den här egenskapen är ”DependsOn =” [ ResourceType] ResourceName ”''.</span><span class="sxs-lookup"><span data-stu-id="2f3cd-138">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example-1"></a><span data-ttu-id="2f3cd-139">Exempel 1</span><span class="sxs-lookup"><span data-stu-id="2f3cd-139">Example 1</span></span>

<span data-ttu-id="2f3cd-140">I följande exempel visas hur du säkerställer att en grupp med namnet ”TestGroup” inte finns.</span><span class="sxs-lookup"><span data-stu-id="2f3cd-140">The following example shows how to ensure that a group called "TestGroup" is absent.</span></span>

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```

## <a name="example-2"></a><span data-ttu-id="2f3cd-141">Exempel 2</span><span class="sxs-lookup"><span data-stu-id="2f3cd-141">Example 2</span></span>

<span data-ttu-id="2f3cd-142">I följande exempel visas hur du lägger till en Active Directory-användare i gruppen lokala administratörer som en del av en flera Machine labb där du redan använder en PSCredential för det lokala administratörskontot.</span><span class="sxs-lookup"><span data-stu-id="2f3cd-142">The following example shows how to add an Active Directory User to the local administrators group as part of a Multi-Machine Lab build where you are already using a PSCredential for the Local Administrator account.</span></span>
<span data-ttu-id="2f3cd-143">Eftersom den används också för administratörskontot för domänen (efter befordran av domän), behöver vi sedan konvertera den här befintliga PSCredential till en domän eget autentiseringsuppgift.</span><span class="sxs-lookup"><span data-stu-id="2f3cd-143">As this is also used for the Domain Admin Account (after Domain promotion), we then need to convert this existing PSCredential to a Domain Friendly credential.</span></span>
<span data-ttu-id="2f3cd-144">Vi kan sedan lägga till en domänanvändare i gruppen lokala administratörer på medlemsservern.</span><span class="sxs-lookup"><span data-stu-id="2f3cd-144">Then we can add a Domain User to the Local Administrators Group on the Member server.</span></span>

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

## <a name="example-3"></a><span data-ttu-id="2f3cd-145">Exempel 3</span><span class="sxs-lookup"><span data-stu-id="2f3cd-145">Example 3</span></span>

<span data-ttu-id="2f3cd-146">I följande exempel visas hur du säkerställer en lokal grupp, TigerTeamAdmins, på servern TigerTeamSource.Contoso.Com innehåller inte ett visst domänkonto Contoso\JerryG.</span><span class="sxs-lookup"><span data-stu-id="2f3cd-146">The following example shows how to ensure a local group, TigerTeamAdmins, on the server TigerTeamSource.Contoso.Com does not contain a particular domain account, Contoso\JerryG.</span></span>

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