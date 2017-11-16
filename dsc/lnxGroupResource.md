---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "DSC för Linux nxGroup resurs"
ms.openlocfilehash: fcd1dfd3110b1358ed7ef9ca8d57154186b271f6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-for-linux-nxgroup-resource"></a><span data-ttu-id="7e56a-103">DSC för Linux nxGroup resurs</span><span class="sxs-lookup"><span data-stu-id="7e56a-103">DSC for Linux nxGroup Resource</span></span>

<span data-ttu-id="7e56a-104">Den **nxGroup** resurs i PowerShell önskad tillstånd Configuration (DSC) ger dig möjlighet att hantera lokala grupper på en Linux-nod.</span><span class="sxs-lookup"><span data-stu-id="7e56a-104">The **nxGroup** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="7e56a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7e56a-105">Syntax</span></span>

```powershell
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Members = <string[]> ]
    [ MebersToInclude = <string[]>]
    [ MembersToExclude = <string[]> ]
    [ DependsOn = <string[]> ]
}

```

## <a name="properties"></a><span data-ttu-id="7e56a-106">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="7e56a-106">Properties</span></span>

|  <span data-ttu-id="7e56a-107">Egenskap</span><span class="sxs-lookup"><span data-stu-id="7e56a-107">Property</span></span> |  <span data-ttu-id="7e56a-108">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7e56a-108">Description</span></span> | 
|---|---|
| <span data-ttu-id="7e56a-109">Gruppnamn</span><span class="sxs-lookup"><span data-stu-id="7e56a-109">GroupName</span></span>| <span data-ttu-id="7e56a-110">Anger namnet på gruppen som du vill se till att ett visst tillstånd.</span><span class="sxs-lookup"><span data-stu-id="7e56a-110">Specifies the name of the group for which you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="7e56a-111">Se till att</span><span class="sxs-lookup"><span data-stu-id="7e56a-111">Ensure</span></span>| <span data-ttu-id="7e56a-112">Anger om du vill kontrollera att gruppen finns.</span><span class="sxs-lookup"><span data-stu-id="7e56a-112">Determines whether to check if the group exists.</span></span> <span data-ttu-id="7e56a-113">Ange egenskapen ”aktuella” för att se till att gruppen finns.</span><span class="sxs-lookup"><span data-stu-id="7e56a-113">Set this property to "Present" to ensure the group exists.</span></span> <span data-ttu-id="7e56a-114">Ange den till ”saknas” för att se till att gruppen inte finns.</span><span class="sxs-lookup"><span data-stu-id="7e56a-114">Set it to "Absent" to ensure the group does not exist.</span></span> <span data-ttu-id="7e56a-115">Standardvärdet är ”saknas”.</span><span class="sxs-lookup"><span data-stu-id="7e56a-115">The default value is "Present".</span></span>| 
| <span data-ttu-id="7e56a-116">Medlemmar</span><span class="sxs-lookup"><span data-stu-id="7e56a-116">Members</span></span>| <span data-ttu-id="7e56a-117">Anger de medlemmar som utgör gruppen.</span><span class="sxs-lookup"><span data-stu-id="7e56a-117">Specifies the members that form the group.</span></span>| 
| <span data-ttu-id="7e56a-118">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="7e56a-118">MembersToInclude</span></span>| <span data-ttu-id="7e56a-119">Anger de användare som du vill kontrollera är medlemmar i gruppen.</span><span class="sxs-lookup"><span data-stu-id="7e56a-119">Specifies the users who you want to ensure are members of the group.</span></span>| 
| <span data-ttu-id="7e56a-120">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="7e56a-120">MembersToExclude</span></span>| <span data-ttu-id="7e56a-121">Anger de användare som du vill se till att inte är medlemmar i gruppen.</span><span class="sxs-lookup"><span data-stu-id="7e56a-121">Specifies the users who you want to ensure are not members of the group.</span></span>| 
| <span data-ttu-id="7e56a-122">PreferredGroupID</span><span class="sxs-lookup"><span data-stu-id="7e56a-122">PreferredGroupID</span></span>| <span data-ttu-id="7e56a-123">Anger om möjligt grupp-id till det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="7e56a-123">Sets the group id to the provided value if possible.</span></span> <span data-ttu-id="7e56a-124">Om grupp-id är för närvarande används, används nästa tillgängliga grupp-id.</span><span class="sxs-lookup"><span data-stu-id="7e56a-124">If the group id is currently in use, the next available group id is used.</span></span>| 
| <span data-ttu-id="7e56a-125">dependsOn</span><span class="sxs-lookup"><span data-stu-id="7e56a-125">DependsOn</span></span> | <span data-ttu-id="7e56a-126">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="7e56a-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7e56a-127">Till exempel om den **ID** resursens configuration skriptblock som du vill köra först är **ResourceName** och dess typ är **ResourceType**, syntaxen för detta Egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="7e56a-127">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="example"></a><span data-ttu-id="7e56a-128">Exempel</span><span class="sxs-lookup"><span data-stu-id="7e56a-128">Example</span></span>

<span data-ttu-id="7e56a-129">I följande exempel säkerställer att användare ”monuser” finns och är medlem i gruppen ”DBusers”.</span><span class="sxs-lookup"><span data-stu-id="7e56a-129">The following example ensures that the user “monuser” exists and is a member of the group "DBusers".</span></span>

```
Import-DSCResource -Module nx 

Node $node {

nxUser UserExample{
   UserName = "monuser"
   Description = "Monitoring user"
   Password  =    '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
   Ensure = "Present"
   HomeDirectory = "/home/monuser"
}
 
nxGroup GroupExample{
   GroupName = "DBusers"
   Ensure = "Present"
   MembersToInclude = "monuser"
   DependsOn = "[nxUser]UserExample"            
}
}
```

