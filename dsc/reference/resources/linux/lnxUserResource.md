---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC för Linux nxUser-resurs
ms.openlocfilehash: 6d7b52809741813af7fa80b1c6372b267aff4777
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71324622"
---
# <a name="dsc-for-linux-nxuser-resource"></a><span data-ttu-id="b832b-103">DSC för Linux nxUser-resurs</span><span class="sxs-lookup"><span data-stu-id="b832b-103">DSC for Linux nxUser Resource</span></span>

<span data-ttu-id="b832b-104">**NxUser** -resursen i PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera lokala användare på en Linux-nod.</span><span class="sxs-lookup"><span data-stu-id="b832b-104">The **nxUser** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local users on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="b832b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b832b-105">Syntax</span></span>

```Syntax
nxUser <string> #ResourceName
{
    UserName = <string>
    [ FullName = <string> ]
    [ Description = <string> ]
    [ Password = <string> ]
    [ Disabled = <bool> ]
    [ PasswordChangeRequired = <bool> ]
    [ HomeDirectory = <string> ]
    [ GroupID = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="b832b-106">properties</span><span class="sxs-lookup"><span data-stu-id="b832b-106">Properties</span></span>

|<span data-ttu-id="b832b-107">Egenskap</span><span class="sxs-lookup"><span data-stu-id="b832b-107">Property</span></span> |<span data-ttu-id="b832b-108">Anger det konto namn som du vill säkerställa ett speciellt tillstånd för.</span><span class="sxs-lookup"><span data-stu-id="b832b-108">Indicates the account name for which you want to ensure a specific state.</span></span> |
|---|---|
|<span data-ttu-id="b832b-109">UserName</span><span class="sxs-lookup"><span data-stu-id="b832b-109">UserName</span></span> |<span data-ttu-id="b832b-110">Anger den plats där du vill kontrol lera statusen för en fil eller katalog.</span><span class="sxs-lookup"><span data-stu-id="b832b-110">Specifies the location where you want to ensure the state for a file or directory.</span></span> |
|<span data-ttu-id="b832b-111">FullName</span><span class="sxs-lookup"><span data-stu-id="b832b-111">FullName</span></span> |<span data-ttu-id="b832b-112">En sträng som innehåller det fullständiga namnet som ska användas för användar kontot.</span><span class="sxs-lookup"><span data-stu-id="b832b-112">A string that contains the full name to use for the user account.</span></span> |
|<span data-ttu-id="b832b-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b832b-113">Description</span></span> |<span data-ttu-id="b832b-114">Beskrivning av användar kontot.</span><span class="sxs-lookup"><span data-stu-id="b832b-114">The description for the user account.</span></span> |
|<span data-ttu-id="b832b-115">lösenordsinställning</span><span class="sxs-lookup"><span data-stu-id="b832b-115">Password</span></span> |<span data-ttu-id="b832b-116">Hash för användarens lösen ord i rätt format för Linux-datorn.</span><span class="sxs-lookup"><span data-stu-id="b832b-116">The hash of the users password in the appropriate form for the Linux computer.</span></span> <span data-ttu-id="b832b-117">Detta är vanligt vis en saltad SHA-256-eller SHA-512-Hash.</span><span class="sxs-lookup"><span data-stu-id="b832b-117">Typically, this is a salted SHA-256, or SHA-512 hash.</span></span> <span data-ttu-id="b832b-118">I Debian och Ubuntu Linux kan det här värdet genereras med `mkpasswd` kommandot.</span><span class="sxs-lookup"><span data-stu-id="b832b-118">On Debian and Ubuntu Linux, this value can be generated with the `mkpasswd` command.</span></span> <span data-ttu-id="b832b-119">För andra Linux-distributioner kan du använda metoden cryption för python: s krypterings bibliotek för att generera hashen.</span><span class="sxs-lookup"><span data-stu-id="b832b-119">For other Linux distros, the crypt method of Python's Crypt library can be used to generate the hash.</span></span> |
|<span data-ttu-id="b832b-120">Inaktiverad</span><span class="sxs-lookup"><span data-stu-id="b832b-120">Disabled</span></span> |<span data-ttu-id="b832b-121">Anger om kontot är aktiverat.</span><span class="sxs-lookup"><span data-stu-id="b832b-121">Indicates whether the account is enabled.</span></span> <span data-ttu-id="b832b-122">Ange den här egenskapen `$true` till för att säkerställa att det här kontot är inaktiverat `$false` och ange det för att säkerställa att det är aktiverat.</span><span class="sxs-lookup"><span data-stu-id="b832b-122">Set this property to `$true` to ensure that this account is disabled, and set it to `$false` to ensure that it is enabled.</span></span> |
|<span data-ttu-id="b832b-123">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="b832b-123">PasswordChangeRequired</span></span> |<span data-ttu-id="b832b-124">Anger om användaren kan ändra lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="b832b-124">Indicates whether the user can change the password.</span></span> <span data-ttu-id="b832b-125">Ange den här egenskapen `$true` till om du vill se till att användaren inte kan ändra lösen ordet och `$false` ange det som tillåter användaren att ändra lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="b832b-125">Set this property to `$true` to ensure that the user cannot change the password, and set it to `$false` to allow the user to change the password.</span></span> <span data-ttu-id="b832b-126">Standardvärdet är `$false`.</span><span class="sxs-lookup"><span data-stu-id="b832b-126">The default value is `$false`.</span></span> <span data-ttu-id="b832b-127">Den här egenskapen utvärderas bara om användar kontot inte fanns tidigare och skapas.</span><span class="sxs-lookup"><span data-stu-id="b832b-127">This property is only evaluated if the user account did not exist previously and is being created.</span></span> |
|<span data-ttu-id="b832b-128">HomeDirectory</span><span class="sxs-lookup"><span data-stu-id="b832b-128">HomeDirectory</span></span> |<span data-ttu-id="b832b-129">Användarens Hem Katalog.</span><span class="sxs-lookup"><span data-stu-id="b832b-129">The home directory for the user.</span></span> |
|<span data-ttu-id="b832b-130">GroupID</span><span class="sxs-lookup"><span data-stu-id="b832b-130">GroupID</span></span> |<span data-ttu-id="b832b-131">Användarens primära grupp-ID.</span><span class="sxs-lookup"><span data-stu-id="b832b-131">The primary group ID for the user.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="b832b-132">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="b832b-132">Common properties</span></span>

|<span data-ttu-id="b832b-133">Egenskap</span><span class="sxs-lookup"><span data-stu-id="b832b-133">Property</span></span> |<span data-ttu-id="b832b-134">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b832b-134">Description</span></span> |
|---|---|
|<span data-ttu-id="b832b-135">DependsOn</span><span class="sxs-lookup"><span data-stu-id="b832b-135">DependsOn</span></span> |<span data-ttu-id="b832b-136">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="b832b-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="b832b-137">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är `DependsOn = "[ResourceType]ResourceName"`syntaxen för att använda den här egenskapen.</span><span class="sxs-lookup"><span data-stu-id="b832b-137">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="b832b-138">Kontrol</span><span class="sxs-lookup"><span data-stu-id="b832b-138">Ensure</span></span> |<span data-ttu-id="b832b-139">Anger om kontot finns.</span><span class="sxs-lookup"><span data-stu-id="b832b-139">Specifies whether the account exists.</span></span> <span data-ttu-id="b832b-140">Ange att den här egenskapen **finns för att** se till att kontot finns och att det inte finns **något att se** till att kontot inte finns.</span><span class="sxs-lookup"><span data-stu-id="b832b-140">Set this property to **Present** to ensure that the account exists, and set it to **Absent** to ensure that the account does not exist.</span></span> |

## <a name="example"></a><span data-ttu-id="b832b-141">Exempel</span><span class="sxs-lookup"><span data-stu-id="b832b-141">Example</span></span>

<span data-ttu-id="b832b-142">I följande exempel ser du till att användaren "monuser" finns och är medlem i gruppen "DBusers".</span><span class="sxs-lookup"><span data-stu-id="b832b-142">The following example ensures that the user "monuser" exists and is a member of the group "DBusers".</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
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