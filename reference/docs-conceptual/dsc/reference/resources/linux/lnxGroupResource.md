---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC för Linux nxGroup-resurs
ms.openlocfilehash: 098ae2e8ab183934ec3c185c0fd237731b1353dc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71941427"
---
# <a name="dsc-for-linux-nxgroup-resource"></a><span data-ttu-id="6f86d-103">DSC för Linux nxGroup-resurs</span><span class="sxs-lookup"><span data-stu-id="6f86d-103">DSC for Linux nxGroup Resource</span></span>

<span data-ttu-id="6f86d-104">**NxGroup** -resursen i PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera lokala grupper på en Linux-nod.</span><span class="sxs-lookup"><span data-stu-id="6f86d-104">The **nxGroup** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="6f86d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6f86d-105">Syntax</span></span>

```Syntax
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Members = <string[]> ]
    [ MembersToInclude = <string[]> ]
    [ MembersToExclude = <string[]> ]
    [ PreferredGroupID = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present } ]
}
```

## <a name="properties"></a><span data-ttu-id="6f86d-106">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="6f86d-106">Properties</span></span>

|<span data-ttu-id="6f86d-107">Egenskap</span><span class="sxs-lookup"><span data-stu-id="6f86d-107">Property</span></span> |<span data-ttu-id="6f86d-108">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6f86d-108">Description</span></span> |
|---|---|
|<span data-ttu-id="6f86d-109">Namn</span><span class="sxs-lookup"><span data-stu-id="6f86d-109">GroupName</span></span> |<span data-ttu-id="6f86d-110">Anger namnet på den grupp som du vill säkerställa ett speciellt tillstånd för.</span><span class="sxs-lookup"><span data-stu-id="6f86d-110">Specifies the name of the group for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="6f86d-111">Medlemmar</span><span class="sxs-lookup"><span data-stu-id="6f86d-111">Members</span></span> |<span data-ttu-id="6f86d-112">Anger de medlemmar som utgör gruppen.</span><span class="sxs-lookup"><span data-stu-id="6f86d-112">Specifies the members that form the group.</span></span> |
|<span data-ttu-id="6f86d-113">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="6f86d-113">MembersToInclude</span></span> |<span data-ttu-id="6f86d-114">Anger de användare som du vill ska vara medlemmar i gruppen.</span><span class="sxs-lookup"><span data-stu-id="6f86d-114">Specifies the users who you want to ensure are members of the group.</span></span> |
|<span data-ttu-id="6f86d-115">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="6f86d-115">MembersToExclude</span></span> |<span data-ttu-id="6f86d-116">Anger de användare som du vill säkerställa inte är medlemmar i gruppen.</span><span class="sxs-lookup"><span data-stu-id="6f86d-116">Specifies the users who you want to ensure are not members of the group.</span></span> |
|<span data-ttu-id="6f86d-117">PreferredGroupID</span><span class="sxs-lookup"><span data-stu-id="6f86d-117">PreferredGroupID</span></span> |<span data-ttu-id="6f86d-118">Anger grupp-ID till det angivna värdet om det är möjligt.</span><span class="sxs-lookup"><span data-stu-id="6f86d-118">Sets the group id to the provided value if possible.</span></span> <span data-ttu-id="6f86d-119">Om grupp-ID: t används för närvarande används nästa tillgängliga grupp-ID.</span><span class="sxs-lookup"><span data-stu-id="6f86d-119">If the group id is currently in use, the next available group id is used.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="6f86d-120">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="6f86d-120">Common properties</span></span>

|<span data-ttu-id="6f86d-121">Egenskap</span><span class="sxs-lookup"><span data-stu-id="6f86d-121">Property</span></span> |<span data-ttu-id="6f86d-122">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6f86d-122">Description</span></span> |
|---|---|
|<span data-ttu-id="6f86d-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="6f86d-123">DependsOn</span></span> |<span data-ttu-id="6f86d-124">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="6f86d-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="6f86d-125">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="6f86d-125">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="6f86d-126">Kontrol</span><span class="sxs-lookup"><span data-stu-id="6f86d-126">Ensure</span></span> |<span data-ttu-id="6f86d-127">Anger om gruppen finns eller inte.</span><span class="sxs-lookup"><span data-stu-id="6f86d-127">Determines whether to check if the group exists.</span></span> <span data-ttu-id="6f86d-128">Ange att den här egenskapen **finns för att** säkerställa att gruppen finns.</span><span class="sxs-lookup"><span data-stu-id="6f86d-128">Set this property to **Present** to ensure the group exists.</span></span> <span data-ttu-id="6f86d-129">Ange det som **frånvarande** för att se till att gruppen inte finns.</span><span class="sxs-lookup"><span data-stu-id="6f86d-129">Set it to **Absent** to ensure the group does not exist.</span></span> <span data-ttu-id="6f86d-130">Standardvärdet finns **.**</span><span class="sxs-lookup"><span data-stu-id="6f86d-130">The default value is **Present**.</span></span> |

## <a name="example"></a><span data-ttu-id="6f86d-131">Exempel</span><span class="sxs-lookup"><span data-stu-id="6f86d-131">Example</span></span>

<span data-ttu-id="6f86d-132">I följande exempel ser du till att användaren ' monuser ' finns och är medlem i gruppen ' DBusers '.</span><span class="sxs-lookup"><span data-stu-id="6f86d-132">The following example ensures that the user 'monuser' exists and is a member of the group 'DBusers'.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
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