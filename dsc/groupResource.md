---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "Tillgänglighetsgruppsresursen DSC"
ms.openlocfilehash: 8a2087455a72ec1f368f890b62228b31cf4ec95a
ms.sourcegitcommit: c72c76f6ed77b3e6f26fef3e8784b157bfc19355
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/06/2018
---
# <a name="dsc-group-resource"></a><span data-ttu-id="0a652-103">Tillgänglighetsgruppsresursen DSC</span><span class="sxs-lookup"><span data-stu-id="0a652-103">DSC Group Resource</span></span>

> <span data-ttu-id="0a652-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0a652-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="0a652-105">Grupp-resurs i Windows PowerShell önskad tillstånd Configuration (DSC) tillhandahåller en mekanism för att hantera lokala grupper på målnoden.</span><span class="sxs-lookup"><span data-stu-id="0a652-105">The Group resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="0a652-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="0a652-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="0a652-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="0a652-107">Properties</span></span>

|  <span data-ttu-id="0a652-108">Egenskap</span><span class="sxs-lookup"><span data-stu-id="0a652-108">Property</span></span>  |  <span data-ttu-id="0a652-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0a652-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="0a652-110">Gruppnamn</span><span class="sxs-lookup"><span data-stu-id="0a652-110">GroupName</span></span>| <span data-ttu-id="0a652-111">Namnet på gruppen som du vill se till att ett visst tillstånd.</span><span class="sxs-lookup"><span data-stu-id="0a652-111">The name of the group for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="0a652-112">autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="0a652-112">Credential</span></span>| <span data-ttu-id="0a652-113">De autentiseringsuppgifter som krävs för att komma åt fjärresurser.</span><span class="sxs-lookup"><span data-stu-id="0a652-113">The credentials required to access remote resources.</span></span> <span data-ttu-id="0a652-114">**Obs**: det här kontot måste ha behörighet att lägga till alla icke-lokala konton i gruppen Active Directory, annars uppstår ett fel när konfigurationen körs på målnoden.</span><span class="sxs-lookup"><span data-stu-id="0a652-114">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error occurs when the configuration is executed on the target node.</span></span>
| <span data-ttu-id="0a652-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0a652-115">Description</span></span>| <span data-ttu-id="0a652-116">Beskrivning av gruppen.</span><span class="sxs-lookup"><span data-stu-id="0a652-116">The description of the group.</span></span>|
| <span data-ttu-id="0a652-117">Se till att</span><span class="sxs-lookup"><span data-stu-id="0a652-117">Ensure</span></span>| <span data-ttu-id="0a652-118">Anger om gruppen finns.</span><span class="sxs-lookup"><span data-stu-id="0a652-118">Indicates if the group exists.</span></span> <span data-ttu-id="0a652-119">Ange den här egenskapen till ”saknas” så att gruppen inte finns.</span><span class="sxs-lookup"><span data-stu-id="0a652-119">Set this property to "Absent" to ensure that the group does not exist.</span></span> <span data-ttu-id="0a652-120">Ange värdet ”finns” (standardvärdet) säkerställer att gruppen finns.</span><span class="sxs-lookup"><span data-stu-id="0a652-120">Setting it to "Present" (the default value) ensures that the group exists.</span></span>|
| <span data-ttu-id="0a652-121">Medlemmar</span><span class="sxs-lookup"><span data-stu-id="0a652-121">Members</span></span>| <span data-ttu-id="0a652-122">Använd den här egenskapen för att ersätta det aktuella gruppmedlemskapet med de angivna medlemmarna.</span><span class="sxs-lookup"><span data-stu-id="0a652-122">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="0a652-123">Värdet för den här egenskapen är en matris med strängar i formuläret *domän*\\*användarnamn*.</span><span class="sxs-lookup"><span data-stu-id="0a652-123">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="0a652-124">Om du anger den här egenskapen i en konfiguration, bör inte använda någon av **MembersToExclude** eller **MembersToInclude** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="0a652-124">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="0a652-125">Detta genererar ett fel.</span><span class="sxs-lookup"><span data-stu-id="0a652-125">Doing so generates an error.</span></span>|
| <span data-ttu-id="0a652-126">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="0a652-126">MembersToExclude</span></span>| <span data-ttu-id="0a652-127">Ta bort medlemmar från det befintliga medlemskapet i gruppen med hjälp av den här egenskapen.</span><span class="sxs-lookup"><span data-stu-id="0a652-127">Use this property to remove members from the existing membership of the group.</span></span> <span data-ttu-id="0a652-128">Värdet för den här egenskapen är en matris med strängar i formuläret *domän*\\*användarnamn*.</span><span class="sxs-lookup"><span data-stu-id="0a652-128">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="0a652-129">Om du anger den här egenskapen i en konfiguration kan du inte använda den **medlemmar** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="0a652-129">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="0a652-130">Detta genererar ett fel.</span><span class="sxs-lookup"><span data-stu-id="0a652-130">Doing so generates an error.</span></span>|
| <span data-ttu-id="0a652-131">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="0a652-131">MembersToInclude</span></span>| <span data-ttu-id="0a652-132">Använd den här egenskapen för att lägga till medlemmar i det befintliga medlemskapet i gruppen.</span><span class="sxs-lookup"><span data-stu-id="0a652-132">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="0a652-133">Värdet för den här egenskapen är en matris med strängar i formuläret *domän*\\*användarnamn*.</span><span class="sxs-lookup"><span data-stu-id="0a652-133">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="0a652-134">Om du anger den här egenskapen i en konfiguration kan du inte använda den **medlemmar** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="0a652-134">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="0a652-135">Detta genererar ett fel.</span><span class="sxs-lookup"><span data-stu-id="0a652-135">Doing so will generate an error.</span></span>|
| <span data-ttu-id="0a652-136">dependsOn</span><span class="sxs-lookup"><span data-stu-id="0a652-136">DependsOn</span></span> | <span data-ttu-id="0a652-137">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="0a652-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="0a652-138">Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis __ResourceName__ och dess typ är __ResourceType__, syntaxen för den här egenskapen är ”DependsOn =” [ResourceType] ResourceName ”''.</span><span class="sxs-lookup"><span data-stu-id="0a652-138">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`\`.</span></span>|

## <a name="example-1"></a><span data-ttu-id="0a652-139">Exempel 1</span><span class="sxs-lookup"><span data-stu-id="0a652-139">Example 1</span></span>

<span data-ttu-id="0a652-140">I följande exempel visas hur du kontrollerar att en grupp med namnet ”TestGroup” saknas.</span><span class="sxs-lookup"><span data-stu-id="0a652-140">The following example shows how to ensure that a group called "TestGroup" is absent.</span></span>

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```

## <a name="example-2"></a><span data-ttu-id="0a652-141">Exempel 2</span><span class="sxs-lookup"><span data-stu-id="0a652-141">Example 2</span></span>

<span data-ttu-id="0a652-142">I följande exempel visas hur du lägger till en Active Directory-användare i gruppen lokala administratörer som en del av en flera datorn Lab version om du redan använder en PSCredential för kontot lokal administratör.</span><span class="sxs-lookup"><span data-stu-id="0a652-142">The following example shows how to add an Active Directory User to the local administrators group as part of a Multi-Machine Lab build where you are already using a PSCredential for the Local Adminstrator account.</span></span>
<span data-ttu-id="0a652-143">Eftersom den används också för domänens administratörskonto (efter befordran), behöver vi sedan konvertera den här befintliga PSCredential till en domän egna autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="0a652-143">As this is also used for the Domain Admin Account (after Domain promotion), we then need to convert this existing PSCredential to a Domain Friendly credential.</span></span>
<span data-ttu-id="0a652-144">Vi kan sedan lägga till en domänanvändare i den lokala gruppen Administratörer på medlemsservern.</span><span class="sxs-lookup"><span data-stu-id="0a652-144">Then we can add a Domain User to the Local Administrators Group on the Member server.</span></span>

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

## <a name="example-3"></a><span data-ttu-id="0a652-145">Exempel 3</span><span class="sxs-lookup"><span data-stu-id="0a652-145">Example 3</span></span>

<span data-ttu-id="0a652-146">I följande exempel visas hur du ser du till en lokal grupp TigerTeamAdmins, på servern TigerTeamSource.Contoso.Com innehåller inte ett visst domänkonto Contoso\JerryG.</span><span class="sxs-lookup"><span data-stu-id="0a652-146">The following example shows how to ensure a local group, TigerTeamAdmins, on the server TigerTeamSource.Contoso.Com does not contain a particular domain account, Contoso\JerryG.</span></span>

```powershell
Configuration SecureTigerTeamSrouce {
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
