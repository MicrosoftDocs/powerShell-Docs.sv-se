---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC för Linux nxUser resurs
ms.openlocfilehash: ca77bcd1f23a78ddb9e2ac988e4aadfec504bbbe
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-for-linux-nxuser-resource"></a><span data-ttu-id="8cc6e-103">DSC för Linux nxUser resurs</span><span class="sxs-lookup"><span data-stu-id="8cc6e-103">DSC for Linux nxUser Resource</span></span>

<span data-ttu-id="8cc6e-104">Den **nxUser** resurs i PowerShell önskad tillstånd Configuration (DSC) ger möjlighet till att hantera lokala användare på en Linux-nod.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-104">The **nxUser** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage local users on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="8cc6e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="8cc6e-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="8cc6e-106">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="8cc6e-106">Properties</span></span>

|  <span data-ttu-id="8cc6e-107">Egenskap</span><span class="sxs-lookup"><span data-stu-id="8cc6e-107">Property</span></span> |  <span data-ttu-id="8cc6e-108">Anger namnet på kontot som du vill se till att ett visst tillstånd.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-108">Indicates the account name for which you want to ensure a specific state.</span></span> |
|---|---|
| <span data-ttu-id="8cc6e-109">UserName</span><span class="sxs-lookup"><span data-stu-id="8cc6e-109">UserName</span></span>| <span data-ttu-id="8cc6e-110">Anger den plats där du vill kontrollera tillståndet för en fil eller katalog.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-110">Specifies the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="8cc6e-111">Se till att</span><span class="sxs-lookup"><span data-stu-id="8cc6e-111">Ensure</span></span>| <span data-ttu-id="8cc6e-112">Anger om kontot finns.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-112">Specifies whether the account exists.</span></span> <span data-ttu-id="8cc6e-113">Ange egenskapen ”aktuella” för att säkerställa att finns ett konto och ange den till ”saknas” så att kontot inte finns.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-113">Set this property to "Present" to ensure that the account exists, and set it to "Absent" to ensure that the account does not exist.</span></span>|
| <span data-ttu-id="8cc6e-114">Fullständigt namn</span><span class="sxs-lookup"><span data-stu-id="8cc6e-114">FullName</span></span>| <span data-ttu-id="8cc6e-115">En sträng som innehåller det fullständiga namnet för användarkontot.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-115">A string that contains the full name to use for the user account.</span></span>|
| <span data-ttu-id="8cc6e-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8cc6e-116">Description</span></span>| <span data-ttu-id="8cc6e-117">Beskrivning för användarkontot.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-117">The description for the user account.</span></span>|
| <span data-ttu-id="8cc6e-118">Lösenord</span><span class="sxs-lookup"><span data-stu-id="8cc6e-118">Password</span></span>| <span data-ttu-id="8cc6e-119">Hash för lösenordet användare på sätt som passar för Linux-datorn.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-119">The hash of the users password in the appropriate form for the Linux computer.</span></span> <span data-ttu-id="8cc6e-120">Detta är vanligtvis en saltat SHA-256 eller SHA-512 hash.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-120">Typically, this is a salted SHA-256, or SHA-512 hash.</span></span> <span data-ttu-id="8cc6e-121">Det här värdet kan skapas med kommandot mkpasswd på Debian och Ubuntu Linux.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-121">On Debian and Ubuntu Linux, this value can be generated with the mkpasswd command.</span></span> <span data-ttu-id="8cc6e-122">För andra Linux-distributioner kan metoden crypt i Python's Crypt biblioteket användas för att generera hash-algoritmen.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-122">For other Linux distros, the crypt method of Python’s Crypt library can be used to generate the hash.</span></span>|
| <span data-ttu-id="8cc6e-123">Inaktiverad</span><span class="sxs-lookup"><span data-stu-id="8cc6e-123">Disabled</span></span>| <span data-ttu-id="8cc6e-124">Anger om kontot är aktiverat.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-124">Indicates whether the account is enabled.</span></span> <span data-ttu-id="8cc6e-125">Den här egenskapen **$true** så att det här kontot är inaktiverad och inställd på **$false** så att den är aktiverad.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-125">Set this property to **$true** to ensure that this account is disabled, and set it to **$false** to ensure that it is enabled.</span></span>|
| <span data-ttu-id="8cc6e-126">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="8cc6e-126">PasswordChangeRequired</span></span>| <span data-ttu-id="8cc6e-127">Anger om användaren kan ändra lösenordet.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-127">Indicates whether the user can change the password.</span></span> <span data-ttu-id="8cc6e-128">Den här egenskapen **$true** så att användaren inte kan ändra lösenordet och Ställ in den på **$false** att tillåta användaren att ändra lösenordet.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-128">Set this property to **$true** to ensure that the user cannot change the password, and set it to **$false** to allow the user to change the password.</span></span> <span data-ttu-id="8cc6e-129">Standardvärdet är **$false**.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-129">The default value is **$false**.</span></span> <span data-ttu-id="8cc6e-130">Den här egenskapen utvärderas endast om användarkontot inte fanns tidigare och håller på att skapas.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-130">This property is only evaluated if the user account did not exist previously and is being created.</span></span>|
| <span data-ttu-id="8cc6e-131">Arbetskatalog</span><span class="sxs-lookup"><span data-stu-id="8cc6e-131">HomeDirectory</span></span>| <span data-ttu-id="8cc6e-132">Arbetskatalog för användaren.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-132">The home directory for the user.</span></span>|
| <span data-ttu-id="8cc6e-133">Grupp-ID</span><span class="sxs-lookup"><span data-stu-id="8cc6e-133">GroupID</span></span>| <span data-ttu-id="8cc6e-134">Primär grupp-ID för användaren.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-134">The primary group ID for the user.</span></span>|
| <span data-ttu-id="8cc6e-135">dependsOn</span><span class="sxs-lookup"><span data-stu-id="8cc6e-135">DependsOn</span></span> | <span data-ttu-id="8cc6e-136">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="8cc6e-137">Till exempel om ID för resursen configuration skriptblock som du vill köra först är ”ResourceName” och ”ResourceType” är av typen syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-137">For example, if the ID of the resource configuration script block that you want to run first is "ResourceName" and its type is "ResourceType", the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="8cc6e-138">Exempel</span><span class="sxs-lookup"><span data-stu-id="8cc6e-138">Example</span></span>

<span data-ttu-id="8cc6e-139">I följande exempel säkerställer att användare ”monuser” finns och är medlem i gruppen ”DBusers”.</span><span class="sxs-lookup"><span data-stu-id="8cc6e-139">The following example ensures that the user "monuser" exists and is a member of the group "DBusers".</span></span>

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