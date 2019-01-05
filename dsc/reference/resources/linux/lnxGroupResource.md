---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC för Linux nxGroup-resurs
ms.openlocfilehash: c61b6ab4a8c56d085b5297dcfc7582187d54f946
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048784"
---
# <a name="dsc-for-linux-nxgroup-resource"></a><span data-ttu-id="9f915-103">DSC för Linux nxGroup-resurs</span><span class="sxs-lookup"><span data-stu-id="9f915-103">DSC for Linux nxGroup Resource</span></span>

<span data-ttu-id="9f915-104">Den **nxGroup** resursen i PowerShell Desired State Configuration (DSC) ger dig möjlighet att hantera lokala grupper på en Linux-nod.</span><span class="sxs-lookup"><span data-stu-id="9f915-104">The **nxGroup** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="9f915-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9f915-105">Syntax</span></span>

```
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Ensure = <string> { Absent | Present } ]
    [ Members = <string[]> ]
    [ MembersToInclude = <string[]> ]
    [ MembersToExclude = <string[]> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="9f915-106">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="9f915-106">Properties</span></span>

|  <span data-ttu-id="9f915-107">Egenskap</span><span class="sxs-lookup"><span data-stu-id="9f915-107">Property</span></span> |  <span data-ttu-id="9f915-108">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="9f915-108">Description</span></span> |
|---|---|
| <span data-ttu-id="9f915-109">Gruppnamn</span><span class="sxs-lookup"><span data-stu-id="9f915-109">GroupName</span></span>| <span data-ttu-id="9f915-110">Anger namnet på gruppen som du vill se till att ett visst tillstånd.</span><span class="sxs-lookup"><span data-stu-id="9f915-110">Specifies the name of the group for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="9f915-111">Se till att</span><span class="sxs-lookup"><span data-stu-id="9f915-111">Ensure</span></span>| <span data-ttu-id="9f915-112">Anger om du vill kontrollera om gruppen.</span><span class="sxs-lookup"><span data-stu-id="9f915-112">Determines whether to check if the group exists.</span></span> <span data-ttu-id="9f915-113">Ange egenskapen ”aktuella” för att se till att gruppen finns.</span><span class="sxs-lookup"><span data-stu-id="9f915-113">Set this property to "Present" to ensure the group exists.</span></span> <span data-ttu-id="9f915-114">Ange den till ”inte” för att se till att gruppen inte finns.</span><span class="sxs-lookup"><span data-stu-id="9f915-114">Set it to "Absent" to ensure the group does not exist.</span></span> <span data-ttu-id="9f915-115">Standardvärdet är ”tillgänglig”.</span><span class="sxs-lookup"><span data-stu-id="9f915-115">The default value is "Present".</span></span>|
| <span data-ttu-id="9f915-116">Medlemmar</span><span class="sxs-lookup"><span data-stu-id="9f915-116">Members</span></span>| <span data-ttu-id="9f915-117">Anger de medlemmar som utgör gruppen.</span><span class="sxs-lookup"><span data-stu-id="9f915-117">Specifies the members that form the group.</span></span>|
| <span data-ttu-id="9f915-118">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="9f915-118">MembersToInclude</span></span>| <span data-ttu-id="9f915-119">Anger de användare som du vill se till att är medlemmar i gruppen.</span><span class="sxs-lookup"><span data-stu-id="9f915-119">Specifies the users who you want to ensure are members of the group.</span></span>|
| <span data-ttu-id="9f915-120">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="9f915-120">MembersToExclude</span></span>| <span data-ttu-id="9f915-121">Anger de användare som du vill se till att inte är medlemmar i gruppen.</span><span class="sxs-lookup"><span data-stu-id="9f915-121">Specifies the users who you want to ensure are not members of the group.</span></span>|
| <span data-ttu-id="9f915-122">PreferredGroupID</span><span class="sxs-lookup"><span data-stu-id="9f915-122">PreferredGroupID</span></span>| <span data-ttu-id="9f915-123">Anger om möjligt grupp-id till det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="9f915-123">Sets the group id to the provided value if possible.</span></span> <span data-ttu-id="9f915-124">Om grupp-id används, används nästa tillgängliga grupp-id.</span><span class="sxs-lookup"><span data-stu-id="9f915-124">If the group id is currently in use, the next available group id is used.</span></span>|
| <span data-ttu-id="9f915-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="9f915-125">DependsOn</span></span> | <span data-ttu-id="9f915-126">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="9f915-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="9f915-127">Till exempel om den **ID** för resursen configuration-skriptblock som du vill köra först är **ResourceName** och är av typen **ResourceType**, syntaxen för detta Egenskapen är `DependsOn = '[ResourceType]ResourceName'`.</span><span class="sxs-lookup"><span data-stu-id="9f915-127">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = '[ResourceType]ResourceName'`.</span></span>|

## <a name="example"></a><span data-ttu-id="9f915-128">Exempel</span><span class="sxs-lookup"><span data-stu-id="9f915-128">Example</span></span>

<span data-ttu-id="9f915-129">I följande exempel säkerställer att användare monuser finns och är medlem i gruppen 'DBusers'.</span><span class="sxs-lookup"><span data-stu-id="9f915-129">The following example ensures that the user 'monuser' exists and is a member of the group 'DBusers'.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node {
    nxUser UserExample {
       UserName = 'monuser'
       Description = 'Monitoring user'
       Password = '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
       Ensure = 'Present'
       HomeDirectory = '/home/monuser'
    }

    nxGroup GroupExample {
       GroupName = 'DBusers'
       Ensure = 'Present'
       MembersToInclude = 'monuser'
       DependsOn = '[nxUser]UserExample'
    }
}
```