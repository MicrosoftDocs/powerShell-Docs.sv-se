---
ms.date: 09/13/2016
ms.topic: reference
title: Lägga till en cmdlet-beskrivning
description: Lägga till en cmdlet-beskrivning
ms.openlocfilehash: 08d21a281881678423bbe3c382279875ed2868db
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651216"
---
# <a name="how-to-add-a-cmdlet-description"></a><span data-ttu-id="dba57-103">Lägga till en cmdlet-beskrivning</span><span class="sxs-lookup"><span data-stu-id="dba57-103">How to Add a Cmdlet Description</span></span>

<span data-ttu-id="dba57-104">I det här avsnittet beskrivs hur du lägger till innehåll som visas i avsnittet **Beskrivning** i cmdlet-hjälpen.</span><span class="sxs-lookup"><span data-stu-id="dba57-104">This section describes how to add content that is displayed in the **DESCRIPTION** section of the cmdlet Help.</span></span> <span data-ttu-id="dba57-105">I Hjälp filen läggs det här innehållet till i **kommando** -noden för varje cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dba57-105">In the Help file, this content is added to the **Command** node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="dba57-106">Om du vill se en fullständig vy över en hjälpfil öppnar du en av `dll-Help.xml` filerna som finns i installations katalogen för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dba57-106">For a complete view of a Help file, open one of the `dll-Help.xml` files located in the PowerShell installation directory.</span></span> <span data-ttu-id="dba57-107">Filen innehåller till exempel `Microsoft.PowerShell.Commands.Management.dll-Help.xml` innehåll för flera av PowerShell-cmdletarna.</span><span class="sxs-lookup"><span data-stu-id="dba57-107">For example, the `Microsoft.PowerShell.Commands.Management.dll-Help.xml` file contains content for several of the PowerShell cmdlets.</span></span>

### <a name="to-add-a-description"></a><span data-ttu-id="dba57-108">Lägga till en beskrivning</span><span class="sxs-lookup"><span data-stu-id="dba57-108">To Add a Description</span></span>

- <span data-ttu-id="dba57-109">Börja med att förklara de grundläggande funktionerna i cmdleten mer detaljerat.</span><span class="sxs-lookup"><span data-stu-id="dba57-109">Begin by explaining the basic features of the cmdlet in more detail.</span></span> <span data-ttu-id="dba57-110">I många fall kan du förklara de termer som används i cmdlet-namnet och illustrera okända begrepp med ett exempel.</span><span class="sxs-lookup"><span data-stu-id="dba57-110">In many cases, you can explain the terms used in the cmdlet name and illustrate unfamiliar concepts with an example.</span></span> <span data-ttu-id="dba57-111">Om till exempel cmdleten lägger till data i en fil, förklarar du att den lägger till data i slutet av en befintlig fil.</span><span class="sxs-lookup"><span data-stu-id="dba57-111">For example, if the cmdlet appends data to a file, explain that it adds data to the end of an existing file.</span></span>

- <span data-ttu-id="dba57-112">Om du vill hitta alla funktioner i cmdleten granskar du parameter listan.</span><span class="sxs-lookup"><span data-stu-id="dba57-112">To find all of the features of the cmdlet, review the parameter list.</span></span> <span data-ttu-id="dba57-113">Beskriv den primära funktionen i cmdleten och ta sedan med andra funktioner och funktioner.</span><span class="sxs-lookup"><span data-stu-id="dba57-113">Describe the primary function of the cmdlet, and then include other functions and features.</span></span> <span data-ttu-id="dba57-114">Om till exempel huvud funktionen för cmdlet: en är att ändra en egenskap, men cmdleten kan ändra alla egenskaper, så i den detaljerade beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="dba57-114">For example, if the main function of the cmdlet is to change one property, but the cmdlet can change all of the properties, say so in the detailed description.</span></span> <span data-ttu-id="dba57-115">Om cmdlet-parametrarna gör det möjligt för användarna att begära information på olika sätt, förklarar du det.</span><span class="sxs-lookup"><span data-stu-id="dba57-115">If the cmdlet parameters let the users solicit information in different ways, explain it.</span></span>

- <span data-ttu-id="dba57-116">Ta med information om hur användarna kan använda cmdleten, förutom den uppenbara användningen.</span><span class="sxs-lookup"><span data-stu-id="dba57-116">Include information on ways that users can use the cmdlet, in addition to the obvious uses.</span></span> <span data-ttu-id="dba57-117">Du kan till exempel använda objektet som `Get-Host` cmdleten hämtar för att ändra färg på text i Windows PowerShell-kommando fönstret.</span><span class="sxs-lookup"><span data-stu-id="dba57-117">For example, you can use the object that the `Get-Host` cmdlet retrieves to change the color of text in the Windows PowerShell command window.</span></span>

  <span data-ttu-id="dba57-118">Exempel: " `Get-Acl` cmdleten hämtar objekt som representerar säkerhets beskrivningen för en fil eller resurs.</span><span class="sxs-lookup"><span data-stu-id="dba57-118">Example: "The `Get-Acl` cmdlet gets objects that represent the security descriptor of a file or resource.</span></span> <span data-ttu-id="dba57-119">Säkerhets beskrivningen innehåller åtkomst kontrol listorna (ACL) för resursen.</span><span class="sxs-lookup"><span data-stu-id="dba57-119">The security descriptor contains the access control lists (ACLs) of the resource.</span></span> <span data-ttu-id="dba57-120">ACL: en anger de behörigheter som användare och användar grupper har åtkomst till resursen. "</span><span class="sxs-lookup"><span data-stu-id="dba57-120">The ACL specifies the permissions that users and user groups have to access the resource."</span></span>

- <span data-ttu-id="dba57-121">Den detaljerade beskrivningen ska beskriva cmdleten, men den bör inte beskriva de begrepp som cmdleten använder.</span><span class="sxs-lookup"><span data-stu-id="dba57-121">The detailed description should describe the cmdlet, but it should not describe concepts that the cmdlet uses.</span></span> <span data-ttu-id="dba57-122">Placera koncept definitioner i ytterligare anteckningar.</span><span class="sxs-lookup"><span data-stu-id="dba57-122">Place concept definitions in Additional Notes.</span></span>

## <a name="see-also"></a><span data-ttu-id="dba57-123">Se även</span><span class="sxs-lookup"><span data-stu-id="dba57-123">See Also</span></span>

[<span data-ttu-id="dba57-124">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="dba57-124">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
