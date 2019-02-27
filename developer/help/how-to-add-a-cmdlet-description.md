---
title: Hur du lägger till en beskrivning för cmdleten | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47af9d57-bd63-4596-816a-0b717418476b
caps.latest.revision: 10
ms.openlocfilehash: a2e4c4d42566d5a52006924eab02295c37cf3159
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851431"
---
# <a name="how-to-add-a-cmdlet-description"></a><span data-ttu-id="9e156-102">Lägga till en cmdlet-beskrivning</span><span class="sxs-lookup"><span data-stu-id="9e156-102">How to Add a Cmdlet Description</span></span>

<span data-ttu-id="9e156-103">Det här avsnittet beskrivs hur du lägger till innehåll som visas i avsnittet beskrivning i cmdlet-hjälpen.</span><span class="sxs-lookup"><span data-stu-id="9e156-103">This section describes how to add content that is displayed in the DESCRIPTION section of the cmdlet Help.</span></span> <span data-ttu-id="9e156-104">Det här innehållet har lagts till noden kommando för varje cmdlet i hjälpfilen.</span><span class="sxs-lookup"><span data-stu-id="9e156-104">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="9e156-105">För en fullständig överblick över en hjälpfilen, öppna en av dll-Help.xml-filerna finns i installationskatalogen för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9e156-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="9e156-106">Till exempel innehåller filen Microsoft.PowerShell.Commands.Management.dll Help.xml innehåll för flera av Windows PowerShell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="9e156-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-a-description"></a><span data-ttu-id="9e156-107">Att lägga till en beskrivning</span><span class="sxs-lookup"><span data-stu-id="9e156-107">To Add a Description</span></span>

- <span data-ttu-id="9e156-108">Börja genom att förklara de grundläggande funktionerna i cmdlet: en i detalj.</span><span class="sxs-lookup"><span data-stu-id="9e156-108">Begin by explaining the basic features of the cmdlet in more detail.</span></span> <span data-ttu-id="9e156-109">I många fall kan du förklara termer som används i cmdlet-namn och illustrera begrepp som är bekant med ett exempel.</span><span class="sxs-lookup"><span data-stu-id="9e156-109">In many cases, you can explain the terms used in the cmdlet name and illustrate unfamiliar concepts with an example.</span></span> <span data-ttu-id="9e156-110">Om cmdlet: en lägger till data till en fil, till exempel, förklara det lägger till data i slutet av en befintlig fil.</span><span class="sxs-lookup"><span data-stu-id="9e156-110">For example, if the cmdlet appends data to a file, explain that it adds data to the end of an existing file.</span></span>

- <span data-ttu-id="9e156-111">Granska listan över för att hitta alla funktioner i cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9e156-111">To find all of the features of the cmdlet, review the parameter list.</span></span> <span data-ttu-id="9e156-112">Beskriver den främsta uppgiften för cmdlet: en och sedan inkludera andra funktioner och funktioner.</span><span class="sxs-lookup"><span data-stu-id="9e156-112">Describe the primary function of the cmdlet, and then include other functions and features.</span></span> <span data-ttu-id="9e156-113">Anta exempelvis att om Huvudsyftet med cmdlet: en är att ändra en egenskap, men cmdlet: en kan ändra alla egenskaper, så i den detaljerade beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="9e156-113">For example, if the main function of the cmdlet is to change one property, but the cmdlet can change all of the properties, say so in the detailed description.</span></span> <span data-ttu-id="9e156-114">Om cmdlet-parametrarna låter användarna begära information på olika sätt, förklara det.</span><span class="sxs-lookup"><span data-stu-id="9e156-114">If the cmdlet parameters let the users solicit information in different ways, explain it.</span></span>

- <span data-ttu-id="9e156-115">Innehåller information om hur användare kan använda cmdlet: en, förutom uppenbara används.</span><span class="sxs-lookup"><span data-stu-id="9e156-115">Include information on ways that users can use the cmdlet, in addition to the obvious uses.</span></span> <span data-ttu-id="9e156-116">Du kan till exempel använda objektet som den `Get-Host` cmdlet: en hämtar om du vill ändra färgen på texten i Windows PowerShell-kommandofönster.</span><span class="sxs-lookup"><span data-stu-id="9e156-116">For example, you can use the object that the `Get-Host` cmdlet retrieves to change the color of text in the Windows PowerShell command window.</span></span>

  <span data-ttu-id="9e156-117">Exempel:  ”Den `Get-Acl` cmdlet hämtar objekt som representerar säkerhetsbeskrivningen för en fil eller resurs.</span><span class="sxs-lookup"><span data-stu-id="9e156-117">Example:  "The `Get-Acl` cmdlet gets objects that represent the security descriptor of a file or resource.</span></span> <span data-ttu-id="9e156-118">Säkerhetsbeskrivningen innehåller åtkomstkontrollistor (ACL) för resursen.</span><span class="sxs-lookup"><span data-stu-id="9e156-118">The security descriptor contains the access control lists (ACLs) of the resource.</span></span> <span data-ttu-id="9e156-119">ACL: Anger de behörigheter som användare och användargrupper som har åtkomst till resursen ”.</span><span class="sxs-lookup"><span data-stu-id="9e156-119">The ACL specifies the permissions that users and user groups have to access the resource."</span></span>

- <span data-ttu-id="9e156-120">Den detaljerade beskrivningen bör beskriva cmdleten, men det bör inte beskriver begrepp som använder cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="9e156-120">The detailed description should describe the cmdlet, but it should not describe concepts that the cmdlet uses.</span></span> <span data-ttu-id="9e156-121">Placera konceptet definitioner i ytterligare information.</span><span class="sxs-lookup"><span data-stu-id="9e156-121">Place concept definitions in Additional Notes.</span></span>

## <a name="see-also"></a><span data-ttu-id="9e156-122">Se även</span><span class="sxs-lookup"><span data-stu-id="9e156-122">See Also</span></span>

[<span data-ttu-id="9e156-123">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="9e156-123">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
