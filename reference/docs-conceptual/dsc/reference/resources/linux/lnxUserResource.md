---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC för Linux nxUser-resurs
ms.openlocfilehash: 4cf8080fbfa58e082ed007d42d6aa2648d1cf58a
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557183"
---
# <a name="dsc-for-linux-nxuser-resource"></a><span data-ttu-id="c4ab7-103">DSC för Linux nxUser-resurs</span><span class="sxs-lookup"><span data-stu-id="c4ab7-103">DSC for Linux nxUser Resource</span></span>

<span data-ttu-id="c4ab7-104">**NxUser** -resursen i PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera lokala användare på en Linux-nod.</span><span class="sxs-lookup"><span data-stu-id="c4ab7-104">The **nxUser** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local users on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="c4ab7-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c4ab7-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="c4ab7-106">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="c4ab7-106">Properties</span></span>

|<span data-ttu-id="c4ab7-107">Egenskap</span><span class="sxs-lookup"><span data-stu-id="c4ab7-107">Property</span></span> |<span data-ttu-id="c4ab7-108">Anger det konto namn som du vill säkerställa ett speciellt tillstånd för.</span><span class="sxs-lookup"><span data-stu-id="c4ab7-108">Indicates the account name for which you want to ensure a specific state.</span></span> |
|---|---|
|<span data-ttu-id="c4ab7-109">UserName</span><span class="sxs-lookup"><span data-stu-id="c4ab7-109">UserName</span></span> |<span data-ttu-id="c4ab7-110">Anger den plats där du vill kontrol lera statusen för en fil eller katalog.</span><span class="sxs-lookup"><span data-stu-id="c4ab7-110">Specifies the location where you want to ensure the state for a file or directory.</span></span> |
|<span data-ttu-id="c4ab7-111">FullName</span><span class="sxs-lookup"><span data-stu-id="c4ab7-111">FullName</span></span> |<span data-ttu-id="c4ab7-112">En sträng som innehåller det fullständiga namnet som ska användas för användar kontot.</span><span class="sxs-lookup"><span data-stu-id="c4ab7-112">A string that contains the full name to use for the user account.</span></span> |
|<span data-ttu-id="c4ab7-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c4ab7-113">Description</span></span> |<span data-ttu-id="c4ab7-114">Beskrivning av användar kontot.</span><span class="sxs-lookup"><span data-stu-id="c4ab7-114">The description for the user account.</span></span> |
|<span data-ttu-id="c4ab7-115">lösenordsinställning</span><span class="sxs-lookup"><span data-stu-id="c4ab7-115">Password</span></span> |<span data-ttu-id="c4ab7-116">Hash för användarens lösen ord i rätt format för Linux-datorn.</span><span class="sxs-lookup"><span data-stu-id="c4ab7-116">The hash of the users password in the appropriate form for the Linux computer.</span></span> <span data-ttu-id="c4ab7-117">Detta är vanligt vis en saltad SHA-256-eller SHA-512-Hash.</span><span class="sxs-lookup"><span data-stu-id="c4ab7-117">Typically, this is a salted SHA-256, or SHA-512 hash.</span></span> <span data-ttu-id="c4ab7-118">I Debian och Ubuntu Linux kan det här värdet genereras med `mkpasswd` kommandot.</span><span class="sxs-lookup"><span data-stu-id="c4ab7-118">On Debian and Ubuntu Linux, this value can be generated with the `mkpasswd` command.</span></span> <span data-ttu-id="c4ab7-119">För andra Linux-distributioner kan du använda metoden cryption för python: s krypterings bibliotek för att generera hashen.</span><span class="sxs-lookup"><span data-stu-id="c4ab7-119">For other Linux distros, the crypt method of Python's Crypt library can be used to generate the hash.</span></span> |
|<span data-ttu-id="c4ab7-120">Disabled</span><span class="sxs-lookup"><span data-stu-id="c4ab7-120">Disabled</span></span> |<span data-ttu-id="c4ab7-121">Anger om kontot är aktiverat.</span><span class="sxs-lookup"><span data-stu-id="c4ab7-121">Indicates whether the account is enabled.</span></span> <span data-ttu-id="c4ab7-122">Ange den här egenskapen till `$true` för att säkerställa att det här kontot är inaktiverat och ange det för att `$false` säkerställa att det är aktiverat.</span><span class="sxs-lookup"><span data-stu-id="c4ab7-122">Set this property to `$true` to ensure that this account is disabled, and set it to `$false` to ensure that it is enabled.</span></span> |
|<span data-ttu-id="c4ab7-123">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="c4ab7-123">PasswordChangeRequired</span></span> |<span data-ttu-id="c4ab7-124">Anger om användaren kan ändra lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="c4ab7-124">Indicates whether the user can change the password.</span></span> <span data-ttu-id="c4ab7-125">Ange den här egenskapen till `$true` om du vill se till att användaren inte kan ändra lösen ordet och ange det som `$false` tillåter användaren att ändra lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="c4ab7-125">Set this property to `$true` to ensure that the user cannot change the password, and set it to `$false` to allow the user to change the password.</span></span> <span data-ttu-id="c4ab7-126">Standardvärdet är `$false`.</span><span class="sxs-lookup"><span data-stu-id="c4ab7-126">The default value is `$false`.</span></span> <span data-ttu-id="c4ab7-127">Den här egenskapen utvärderas bara om användar kontot inte fanns tidigare och skapas.</span><span class="sxs-lookup"><span data-stu-id="c4ab7-127">This property is only evaluated if the user account did not exist previously and is being created.</span></span> |
|<span data-ttu-id="c4ab7-128">HomeDirectory</span><span class="sxs-lookup"><span data-stu-id="c4ab7-128">HomeDirectory</span></span> |<span data-ttu-id="c4ab7-129">Användarens Hem Katalog.</span><span class="sxs-lookup"><span data-stu-id="c4ab7-129">The home directory for the user.</span></span> |
|<span data-ttu-id="c4ab7-130">GroupID</span><span class="sxs-lookup"><span data-stu-id="c4ab7-130">GroupID</span></span> |<span data-ttu-id="c4ab7-131">Användarens primära grupp-ID.</span><span class="sxs-lookup"><span data-stu-id="c4ab7-131">The primary group ID for the user.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="c4ab7-132">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="c4ab7-132">Common properties</span></span>

|<span data-ttu-id="c4ab7-133">Egenskap</span><span class="sxs-lookup"><span data-stu-id="c4ab7-133">Property</span></span> |<span data-ttu-id="c4ab7-134">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c4ab7-134">Description</span></span> |
|---|---|
|<span data-ttu-id="c4ab7-135">DependsOn</span><span class="sxs-lookup"><span data-stu-id="c4ab7-135">DependsOn</span></span> |<span data-ttu-id="c4ab7-136">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="c4ab7-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c4ab7-137">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="c4ab7-137">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="c4ab7-138">Kontrol</span><span class="sxs-lookup"><span data-stu-id="c4ab7-138">Ensure</span></span> |<span data-ttu-id="c4ab7-139">Anger om kontot finns.</span><span class="sxs-lookup"><span data-stu-id="c4ab7-139">Specifies whether the account exists.</span></span> <span data-ttu-id="c4ab7-140">Ange att den här egenskapen **finns för att** se till att kontot finns och att det inte finns **något att se** till att kontot inte finns.</span><span class="sxs-lookup"><span data-stu-id="c4ab7-140">Set this property to **Present** to ensure that the account exists, and set it to **Absent** to ensure that the account does not exist.</span></span> |

## <a name="example"></a><span data-ttu-id="c4ab7-141">Exempel</span><span class="sxs-lookup"><span data-stu-id="c4ab7-141">Example</span></span>

<span data-ttu-id="c4ab7-142">I följande exempel ser du till att användaren "monuser" finns och är medlem i gruppen "DBusers".</span><span class="sxs-lookup"><span data-stu-id="c4ab7-142">The following example ensures that the user "monuser" exists and is a member of the group "DBusers".</span></span>

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
