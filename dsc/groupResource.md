---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "Tillgänglighetsgruppsresursen DSC"
ms.openlocfilehash: 6fb6c5f9593687d7204ff31fddd9bca978ed2707
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-group-resource"></a><span data-ttu-id="7ad1d-103">Tillgänglighetsgruppsresursen DSC</span><span class="sxs-lookup"><span data-stu-id="7ad1d-103">DSC Group Resource</span></span>

> <span data-ttu-id="7ad1d-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7ad1d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="7ad1d-105">Grupp-resurs i Windows PowerShell önskad tillstånd Configuration (DSC) tillhandahåller en mekanism för att hantera lokala grupper på målnoden.</span><span class="sxs-lookup"><span data-stu-id="7ad1d-105">The Group resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="7ad1d-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="7ad1d-106">Syntax</span></span>
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

## <a name="properties"></a><span data-ttu-id="7ad1d-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="7ad1d-107">Properties</span></span>

|  <span data-ttu-id="7ad1d-108">Egenskap</span><span class="sxs-lookup"><span data-stu-id="7ad1d-108">Property</span></span>  |  <span data-ttu-id="7ad1d-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7ad1d-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="7ad1d-110">Gruppnamn</span><span class="sxs-lookup"><span data-stu-id="7ad1d-110">GroupName</span></span>| <span data-ttu-id="7ad1d-111">Namnet på gruppen som du vill se till att ett visst tillstånd.</span><span class="sxs-lookup"><span data-stu-id="7ad1d-111">The name of the group for which you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="7ad1d-112">autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="7ad1d-112">Credential</span></span>| <span data-ttu-id="7ad1d-113">De autentiseringsuppgifter som krävs för att komma åt fjärresurser.</span><span class="sxs-lookup"><span data-stu-id="7ad1d-113">The credentials required to access remote resources.</span></span> <span data-ttu-id="7ad1d-114">**Obs**: det här kontot måste ha behörighet att lägga till alla icke-lokala konton i gruppen Active Directory, annars uppstår ett fel när konfigurationen körs på målnoden.</span><span class="sxs-lookup"><span data-stu-id="7ad1d-114">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error occurs when the configuration is executed on the target node.</span></span>  
| <span data-ttu-id="7ad1d-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7ad1d-115">Description</span></span>| <span data-ttu-id="7ad1d-116">Beskrivning av gruppen.</span><span class="sxs-lookup"><span data-stu-id="7ad1d-116">The description of the group.</span></span>| 
| <span data-ttu-id="7ad1d-117">Se till att</span><span class="sxs-lookup"><span data-stu-id="7ad1d-117">Ensure</span></span>| <span data-ttu-id="7ad1d-118">Anger om gruppen finns.</span><span class="sxs-lookup"><span data-stu-id="7ad1d-118">Indicates if the group exists.</span></span> <span data-ttu-id="7ad1d-119">Ange den här egenskapen till ”saknas” så att gruppen inte finns.</span><span class="sxs-lookup"><span data-stu-id="7ad1d-119">Set this property to "Absent" to ensure that the group does not exist.</span></span> <span data-ttu-id="7ad1d-120">Ange värdet ”finns” (standardvärdet) säkerställer att gruppen finns.</span><span class="sxs-lookup"><span data-stu-id="7ad1d-120">Setting it to "Present" (the default value) ensures that the group exists.</span></span>| 
| <span data-ttu-id="7ad1d-121">Medlemmar</span><span class="sxs-lookup"><span data-stu-id="7ad1d-121">Members</span></span>| <span data-ttu-id="7ad1d-122">Använd den här egenskapen för att ersätta det aktuella gruppmedlemskapet med de angivna medlemmarna.</span><span class="sxs-lookup"><span data-stu-id="7ad1d-122">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="7ad1d-123">Värdet för den här egenskapen är en matris med strängar i formuläret *domän*\\*användarnamn*.</span><span class="sxs-lookup"><span data-stu-id="7ad1d-123">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="7ad1d-124">Om du anger den här egenskapen i en konfiguration, bör inte använda någon av **MembersToExclude** eller **MembersToInclude** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="7ad1d-124">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="7ad1d-125">Detta genererar ett fel.</span><span class="sxs-lookup"><span data-stu-id="7ad1d-125">Doing so generates an error.</span></span>| 
| <span data-ttu-id="7ad1d-126">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="7ad1d-126">MembersToExclude</span></span>| <span data-ttu-id="7ad1d-127">Ta bort medlemmar från det befintliga medlemskapet i gruppen med hjälp av den här egenskapen.</span><span class="sxs-lookup"><span data-stu-id="7ad1d-127">Use this property to remove members from the existing membership of the group.</span></span> <span data-ttu-id="7ad1d-128">Värdet för den här egenskapen är en matris med strängar i formuläret *domän*\\*användarnamn*.</span><span class="sxs-lookup"><span data-stu-id="7ad1d-128">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="7ad1d-129">Om du anger den här egenskapen i en konfiguration kan du inte använda den **medlemmar** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="7ad1d-129">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="7ad1d-130">Detta genererar ett fel.</span><span class="sxs-lookup"><span data-stu-id="7ad1d-130">Doing so generates an error.</span></span>| 
| <span data-ttu-id="7ad1d-131">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="7ad1d-131">MembersToInclude</span></span>| <span data-ttu-id="7ad1d-132">Använd den här egenskapen för att lägga till medlemmar i det befintliga medlemskapet i gruppen.</span><span class="sxs-lookup"><span data-stu-id="7ad1d-132">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="7ad1d-133">Värdet för den här egenskapen är en matris med strängar i formuläret *domän*\\*användarnamn*.</span><span class="sxs-lookup"><span data-stu-id="7ad1d-133">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="7ad1d-134">Om du anger den här egenskapen i en konfiguration kan du inte använda den **medlemmar** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="7ad1d-134">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="7ad1d-135">Detta genererar ett fel.</span><span class="sxs-lookup"><span data-stu-id="7ad1d-135">Doing so will generate an error.</span></span>| 
| <span data-ttu-id="7ad1d-136">dependsOn</span><span class="sxs-lookup"><span data-stu-id="7ad1d-136">DependsOn</span></span> | <span data-ttu-id="7ad1d-137">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="7ad1d-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7ad1d-138">Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis __ResourceName__ och dess typ är __ResourceType__, syntaxen för den här egenskapen är ”DependsOn =” [ResourceType] ResourceName ”''.</span><span class="sxs-lookup"><span data-stu-id="7ad1d-138">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`\`.</span></span>| 

## <a name="example-1"></a><span data-ttu-id="7ad1d-139">Exempel 1</span><span class="sxs-lookup"><span data-stu-id="7ad1d-139">Example 1</span></span>

<span data-ttu-id="7ad1d-140">I följande exempel visas hur du kontrollerar att en grupp med namnet ”TestGroup” saknas.</span><span class="sxs-lookup"><span data-stu-id="7ad1d-140">The following example shows how to ensure that a group called "TestGroup" is absent.</span></span> 

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```
## <a name="example-2"></a><span data-ttu-id="7ad1d-141">Exempel 2</span><span class="sxs-lookup"><span data-stu-id="7ad1d-141">Example 2</span></span>
<span data-ttu-id="7ad1d-142">I följande exempel visas hur du lägger till en Active Directory-användare i gruppen lokala administratörer som en del av en flera datorn Lab version om du redan använder en PSCredential för kontot lokal administratör.</span><span class="sxs-lookup"><span data-stu-id="7ad1d-142">The following example shows how to add an Active Directory User to the local administrators group as part of a Multi-Machine Lab build where you are already using a PSCredential for the Local Adminstrator account.</span></span> <span data-ttu-id="7ad1d-143">Eftersom den används också för domänens administratörskonto (efter befordran) behöver vi sedan konvertera den här befintliga PSCredential till en domän egna autentiseringsuppgifter för att hjälpa oss att lägga till en domänanvändare i den lokala gruppen Administratörer på medlemsservern.</span><span class="sxs-lookup"><span data-stu-id="7ad1d-143">As this is also used for the Domain Admin Account (after Domain promotion) we then need to convert this existing PSCredential to a Domain Friendly credential to enable us to add a Domain User to the Local Administrators Group on the Member server.</span></span>

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

Group AddADUserToLocalAdminGroup
        {
            GroupName='Administrators'   
            Ensure= 'Present'             
            MembersToInclude= "$domain\$($Node.AdminAccount)"
            Credential = $dCredential    
            PsDscRunAsCredential = $DCredential
        }
```

## <a name="example-3"></a><span data-ttu-id="7ad1d-144">Exempel 3</span><span class="sxs-lookup"><span data-stu-id="7ad1d-144">Example 3</span></span>
<span data-ttu-id="7ad1d-145">I följande exempel visas hur du ser du till en lokal grupp TigerTeamAdmins, på servern TigerTeamSource.Contoso.Com innehåller inte ett visst domänkonto Contoso\JerryG.</span><span class="sxs-lookup"><span data-stu-id="7ad1d-145">The following example shows how to ensure a local group, TigerTeamAdmins, on the server TigerTeamSource.Contoso.Com does not contain a particular domain account, Contoso\JerryG.</span></span>  

```powershell

Configuration SecureTigerTeamSrouce 
{
  Import-DscResource -ModuleName 'PSDesiredStateConfiguration'
  
  Node TigerTeamSource.Contoso.Com {
  Group TigerTeamAdmins
    {
       GroupName        = 'TigerTeamAdmins'   
       Ensure           = 'Absent'             
       MembersToInclude = "Contoso\JerryG"
    }
  }
}
```

