---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC för Linux nxUser-resurs
ms.openlocfilehash: 1b02be1559957585a2a1733630cb93440e8182f9
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048646"
---
# <a name="dsc-for-linux-nxuser-resource"></a><span data-ttu-id="bef6c-103">DSC för Linux nxUser-resurs</span><span class="sxs-lookup"><span data-stu-id="bef6c-103">DSC for Linux nxUser Resource</span></span>

<span data-ttu-id="bef6c-104">Den **nxUser** resursen i PowerShell Desired State Configuration (DSC) ger dig möjlighet att hantera lokala användare på en Linux-nod.</span><span class="sxs-lookup"><span data-stu-id="bef6c-104">The **nxUser** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local users on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="bef6c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="bef6c-105">Syntax</span></span>

```
nxUser <string> #ResourceName
{
    UserName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ FullName = <string> ]
    [ Description = <string> ]
    [ Password = <string> ]
    [ Disabled = <bool> ]
    [ PasswordChangeRequired = <bool> ]
    [ HomeDirectory = <string> ]
    [ GroupID = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="bef6c-106">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="bef6c-106">Properties</span></span>

|  <span data-ttu-id="bef6c-107">Egenskap</span><span class="sxs-lookup"><span data-stu-id="bef6c-107">Property</span></span> |  <span data-ttu-id="bef6c-108">Anger namnet på kontot som du vill se till att ett visst tillstånd.</span><span class="sxs-lookup"><span data-stu-id="bef6c-108">Indicates the account name for which you want to ensure a specific state.</span></span> |
|---|---|
| <span data-ttu-id="bef6c-109">UserName</span><span class="sxs-lookup"><span data-stu-id="bef6c-109">UserName</span></span>| <span data-ttu-id="bef6c-110">Anger den plats där du vill kontrollera status för en fil eller katalog.</span><span class="sxs-lookup"><span data-stu-id="bef6c-110">Specifies the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="bef6c-111">Se till att</span><span class="sxs-lookup"><span data-stu-id="bef6c-111">Ensure</span></span>| <span data-ttu-id="bef6c-112">Anger om kontot finns.</span><span class="sxs-lookup"><span data-stu-id="bef6c-112">Specifies whether the account exists.</span></span> <span data-ttu-id="bef6c-113">Ange den här egenskapen ”aktuella” så att konton som finns och ange den till ”” så att kontot inte finns.</span><span class="sxs-lookup"><span data-stu-id="bef6c-113">Set this property to "Present" to ensure that the account exists, and set it to "Absent" to ensure that the account does not exist.</span></span>|
| <span data-ttu-id="bef6c-114">FullName</span><span class="sxs-lookup"><span data-stu-id="bef6c-114">FullName</span></span>| <span data-ttu-id="bef6c-115">En sträng som innehåller det fullständiga namnet för användarkontot.</span><span class="sxs-lookup"><span data-stu-id="bef6c-115">A string that contains the full name to use for the user account.</span></span>|
| <span data-ttu-id="bef6c-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="bef6c-116">Description</span></span>| <span data-ttu-id="bef6c-117">Beskrivning för användarkontot.</span><span class="sxs-lookup"><span data-stu-id="bef6c-117">The description for the user account.</span></span>|
| <span data-ttu-id="bef6c-118">Lösenord</span><span class="sxs-lookup"><span data-stu-id="bef6c-118">Password</span></span>| <span data-ttu-id="bef6c-119">Hash för användarnas lösenord på sätt som passar för Linux-dator.</span><span class="sxs-lookup"><span data-stu-id="bef6c-119">The hash of the users password in the appropriate form for the Linux computer.</span></span> <span data-ttu-id="bef6c-120">Detta är vanligtvis en saltat SHA-256 eller SHA-512 hash.</span><span class="sxs-lookup"><span data-stu-id="bef6c-120">Typically, this is a salted SHA-256, or SHA-512 hash.</span></span> <span data-ttu-id="bef6c-121">Det här värdet kan genereras med kommandot mkpasswd på Debian och Ubuntu Linux.</span><span class="sxs-lookup"><span data-stu-id="bef6c-121">On Debian and Ubuntu Linux, this value can be generated with the mkpasswd command.</span></span> <span data-ttu-id="bef6c-122">För andra Linux-distributioner kan metoden crypt i Python's Crypt biblioteket användas för att generera en hash.</span><span class="sxs-lookup"><span data-stu-id="bef6c-122">For other Linux distros, the crypt method of Python’s Crypt library can be used to generate the hash.</span></span>|
| <span data-ttu-id="bef6c-123">Inaktiverad</span><span class="sxs-lookup"><span data-stu-id="bef6c-123">Disabled</span></span>| <span data-ttu-id="bef6c-124">Anger om kontot har aktiverats.</span><span class="sxs-lookup"><span data-stu-id="bef6c-124">Indicates whether the account is enabled.</span></span> <span data-ttu-id="bef6c-125">Den här egenskapen **$true** så att det här kontot är inaktiverat och ange den till **$false** så att den är aktiverad.</span><span class="sxs-lookup"><span data-stu-id="bef6c-125">Set this property to **$true** to ensure that this account is disabled, and set it to **$false** to ensure that it is enabled.</span></span>|
| <span data-ttu-id="bef6c-126">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="bef6c-126">PasswordChangeRequired</span></span>| <span data-ttu-id="bef6c-127">Anger om användaren kan ändra lösenordet.</span><span class="sxs-lookup"><span data-stu-id="bef6c-127">Indicates whether the user can change the password.</span></span> <span data-ttu-id="bef6c-128">Den här egenskapen **$true** så att användaren inte kan ändra lösenordet och ange den till **$false** att tillåta användare att ändra lösenordet.</span><span class="sxs-lookup"><span data-stu-id="bef6c-128">Set this property to **$true** to ensure that the user cannot change the password, and set it to **$false** to allow the user to change the password.</span></span> <span data-ttu-id="bef6c-129">Standardvärdet är **$false**.</span><span class="sxs-lookup"><span data-stu-id="bef6c-129">The default value is **$false**.</span></span> <span data-ttu-id="bef6c-130">Den här egenskapen utvärderas bara om användarkontot inte fanns tidigare och håller på att skapas.</span><span class="sxs-lookup"><span data-stu-id="bef6c-130">This property is only evaluated if the user account did not exist previously and is being created.</span></span>|
| <span data-ttu-id="bef6c-131">Arbetskatalog</span><span class="sxs-lookup"><span data-stu-id="bef6c-131">HomeDirectory</span></span>| <span data-ttu-id="bef6c-132">Arbetskatalog för användaren.</span><span class="sxs-lookup"><span data-stu-id="bef6c-132">The home directory for the user.</span></span>|
| <span data-ttu-id="bef6c-133">Grupp-ID</span><span class="sxs-lookup"><span data-stu-id="bef6c-133">GroupID</span></span>| <span data-ttu-id="bef6c-134">Primär grupp-ID för användaren.</span><span class="sxs-lookup"><span data-stu-id="bef6c-134">The primary group ID for the user.</span></span>|
| <span data-ttu-id="bef6c-135">DependsOn</span><span class="sxs-lookup"><span data-stu-id="bef6c-135">DependsOn</span></span> | <span data-ttu-id="bef6c-136">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="bef6c-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="bef6c-137">Till exempel om ID för resursen configuration skriptblocket som du vill köra först är ”ResourceName” och ”ResourceType” är av typen, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="bef6c-137">For example, if the ID of the resource configuration script block that you want to run first is "ResourceName" and its type is "ResourceType", the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="bef6c-138">Exempel</span><span class="sxs-lookup"><span data-stu-id="bef6c-138">Example</span></span>

<span data-ttu-id="bef6c-139">I följande exempel säkerställer att användare ”monuser” finns och är medlem i gruppen ”DBusers”.</span><span class="sxs-lookup"><span data-stu-id="bef6c-139">The following example ensures that the user "monuser" exists and is a member of the group "DBusers".</span></span>

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