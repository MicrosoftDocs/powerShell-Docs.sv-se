---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: galleriet, powershell, cmdlet, psgallery
title: psgallery_unlist_items
ms.openlocfilehash: af48f2ca889dcc101d466e40f2ecbe0cdf62c066
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="unlisting-items"></a><span data-ttu-id="082d9-103">Avlista objekt</span><span class="sxs-lookup"><span data-stu-id="082d9-103">Unlisting items</span></span>

<span data-ttu-id="082d9-104">**Anledningen att ta bort ett objekt från PowerShell-galleriet som inte visas som ett alternativ?**</span><span class="sxs-lookup"><span data-stu-id="082d9-104">**Why is removing an item from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="082d9-105">PowerShell-galleriet stöder inte användarna sina objekt tas bort permanent.</span><span class="sxs-lookup"><span data-stu-id="082d9-105">The PowerShell Gallery does not support users permanently deleting their items.</span></span>
<span data-ttu-id="082d9-106">Detta gör det möjligt för andra att ta beroenden på objekten utan att bekymra dig om eventuella radbrytningar i framtiden.</span><span class="sxs-lookup"><span data-stu-id="082d9-106">This enables others to take dependencies on your items without worrying about possible breaks in the future.</span></span>
<span data-ttu-id="082d9-107">Om modulen Pester beror på Azure-modulen och Azure-modulen tas bort från galleriet, och sedan kan användaren inte längre använder exempelvis modulen Pester.</span><span class="sxs-lookup"><span data-stu-id="082d9-107">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then user can no longer uses the Pester module.</span></span>

<span data-ttu-id="082d9-108">I stället för att ta bort ett objekt, men du kan ta bort den i stället.</span><span class="sxs-lookup"><span data-stu-id="082d9-108">Instead of removing an item, however, you can unlist it instead.</span></span>

<span data-ttu-id="082d9-109">**Vad gör Användarhanteraren ett objekt i PowerShell-galleriet göra?**</span><span class="sxs-lookup"><span data-stu-id="082d9-109">**What does unlisting an item on PowerShell Gallery do?**</span></span>

<span data-ttu-id="082d9-110">Ett objekt, till exempel modulen eller skript på PowerShell-galleriet Användarhanteraren tas det bort från fliken objekt. Dessutom är olistade objekt inte kan identifieras med hjälp av sökfältet.</span><span class="sxs-lookup"><span data-stu-id="082d9-110">Unlisting an item such as module or script on PowerShell Gallery will remove it from the Items tab. In addition, unlisted items will not be discoverable using the search bar.</span></span>
<span data-ttu-id="082d9-111">Det enda sättet att hämta ett objekt som inte finns i listan är att ange den exakta namnet och versionen av objektet.</span><span class="sxs-lookup"><span data-stu-id="082d9-111">The only way to download an unlisted item is to specify the exact name and version of the item.</span></span>
<span data-ttu-id="082d9-112">Därför bryts Användarhanteraren för ett objekt inte andra moduler eller skript som är beroende av den.</span><span class="sxs-lookup"><span data-stu-id="082d9-112">Because of this, the unlisting of an item will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="082d9-113">Om du vill ta bort objektet finns på informationssidan för objektet och väljer Ta bort objekt.</span><span class="sxs-lookup"><span data-stu-id="082d9-113">To unlist your item, visit the item details page and select 'Delete Item'.</span></span> <span data-ttu-id="082d9-114">Avmarkera kryssrutan om-listan, och klicka på Spara.</span><span class="sxs-lookup"><span data-stu-id="082d9-114">Uncheck the 'Listed' checkbox, and click Save.</span></span>

<span data-ttu-id="082d9-115">**Hur kan jag ta bort ett objekt**</span><span class="sxs-lookup"><span data-stu-id="082d9-115">**How can I remove an item?**</span></span>

<span data-ttu-id="082d9-116">Om du får ett scenario där borttagning av objekt är nödvändiga, kontakta administratörer för PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="082d9-116">If you experience a scenario where item deletion is necessary, contact the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="082d9-117">Ogiltig borttagning scenarier är:</span><span class="sxs-lookup"><span data-stu-id="082d9-117">Valid deletion scenarios are:</span></span>
- <span data-ttu-id="082d9-118">Frågor om upphovsrättsintrång.</span><span class="sxs-lookup"><span data-stu-id="082d9-118">Issues of copyright infringement.</span></span>
- <span data-ttu-id="082d9-119">Objektet innehåller potentiellt skadligt innehåll.</span><span class="sxs-lookup"><span data-stu-id="082d9-119">Item contains potentially harmful content.</span></span>
- <span data-ttu-id="082d9-120">Objektet innehåller känsliga data.</span><span class="sxs-lookup"><span data-stu-id="082d9-120">Item contains sensitive data.</span></span>

<span data-ttu-id="082d9-121">Om du vill skicka en ta bort objektet begäran till PowerShell-galleriet administratörer finns objektet detaljsida och välj kontakta Support.</span><span class="sxs-lookup"><span data-stu-id="082d9-121">To submit a Delete Item Request to the PowerShell Gallery Administrators, visit your item's detail page and select Contact Support.</span></span>