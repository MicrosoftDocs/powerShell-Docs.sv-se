---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: Avlista paket
ms.openlocfilehash: fb66fd23dae1d4640056a764c31426f61f56d910
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004174"
---
# <a name="unlisting-packages"></a><span data-ttu-id="12a73-103">Ta paket</span><span class="sxs-lookup"><span data-stu-id="12a73-103">Unlisting Packages</span></span>

<span data-ttu-id="12a73-104">**Varför tar bort ett paket från PowerShell-galleriet visas inte som ett alternativ?**</span><span class="sxs-lookup"><span data-stu-id="12a73-104">**Why is removing a package from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="12a73-105">PowerShell-galleriet har inte stöd för användare som har sina paket tas bort permanent.</span><span class="sxs-lookup"><span data-stu-id="12a73-105">The PowerShell Gallery does not support users permanently deleting their packages.</span></span>
<span data-ttu-id="12a73-106">Detta gör att andra kan ta beroenden på dina paket utan att behöva bekymra dig om möjligt radbrytningar i framtiden.</span><span class="sxs-lookup"><span data-stu-id="12a73-106">This enables others to take dependencies on your packages without worrying about possible breaks in the future.</span></span>
<span data-ttu-id="12a73-107">Om modulen Pester beror på Azure-modulen och Azure-modulen tas bort från galleriet, och användaren kan inte längre använder exempelvis modulen Pester.</span><span class="sxs-lookup"><span data-stu-id="12a73-107">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then user can no longer uses the Pester module.</span></span>

<span data-ttu-id="12a73-108">I stället för att ta bort ett paket, men du kan ta bort den i stället.</span><span class="sxs-lookup"><span data-stu-id="12a73-108">Instead of removing an package, however, you can unlist it instead.</span></span>

<span data-ttu-id="12a73-109">**Vad kostar avlista ett paket på PowerShell-galleriet göra?**</span><span class="sxs-lookup"><span data-stu-id="12a73-109">**What does unlisting a package on PowerShell Gallery do?**</span></span>

<span data-ttu-id="12a73-110">Avlista ett paket, till exempel modulen eller skript i PowerShell-galleriet tas den bort från fliken paket. Dessutom är olistade paket inte synliga i sökfältet.</span><span class="sxs-lookup"><span data-stu-id="12a73-110">Unlisting a package such as module or script on PowerShell Gallery will remove it from the Packages tab. In addition, unlisted packages will not be discoverable using the search bar.</span></span>
<span data-ttu-id="12a73-111">Det enda sättet att ladda ned ett paket som inte finns i listan är att ange de exakta namnet och versionen av paketet.</span><span class="sxs-lookup"><span data-stu-id="12a73-111">The only way to download an unlisted package is to specify the exact name and version of the package.</span></span>
<span data-ttu-id="12a73-112">Därför som avlista av ett paket påverkar andra moduler och skript som är beroende av den.</span><span class="sxs-lookup"><span data-stu-id="12a73-112">Because of this, the unlisting of an package will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="12a73-113">Om du vill ta bort ditt paket, gå till sidan med paket och välj Ta bort modulen.</span><span class="sxs-lookup"><span data-stu-id="12a73-113">To unlist your package, visit the package details page and select 'Delete Module'.</span></span> <span data-ttu-id="12a73-114">Avmarkera kryssrutan ”listan” och klicka på Spara.</span><span class="sxs-lookup"><span data-stu-id="12a73-114">Uncheck the 'Listed' checkbox, and click Save.</span></span>

<span data-ttu-id="12a73-115">**Hur tar jag bort ett paket?**</span><span class="sxs-lookup"><span data-stu-id="12a73-115">**How can I remove an package?**</span></span>

<span data-ttu-id="12a73-116">Om det uppstår ett scenario där det är nödvändigt att ta bort paketet kan du kontakta administratörer för PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="12a73-116">If you experience a scenario where package deletion is necessary, contact the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="12a73-117">Giltigt borttagning scenarier är:</span><span class="sxs-lookup"><span data-stu-id="12a73-117">Valid deletion scenarios are:</span></span>
- <span data-ttu-id="12a73-118">Problem med upphovsrättsintrång.</span><span class="sxs-lookup"><span data-stu-id="12a73-118">Issues of copyright infringement.</span></span>
- <span data-ttu-id="12a73-119">Paketet innehåller potentiellt skadligt innehåll.</span><span class="sxs-lookup"><span data-stu-id="12a73-119">Package contains potentially harmful content.</span></span>
- <span data-ttu-id="12a73-120">Paketet innehåller känsliga data.</span><span class="sxs-lookup"><span data-stu-id="12a73-120">Package contains sensitive data.</span></span>

<span data-ttu-id="12a73-121">Ditt paket information på sidan för att skicka en ta bort paketet begäran till administratörer för PowerShell-galleriet, och välj kontakta Support.</span><span class="sxs-lookup"><span data-stu-id="12a73-121">To submit a Delete Package Request to the PowerShell Gallery Administrators, visit your package's detail page and select Contact Support.</span></span>
