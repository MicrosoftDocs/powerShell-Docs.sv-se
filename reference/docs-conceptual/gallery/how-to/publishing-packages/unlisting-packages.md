---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galleri, PowerShell, cmdlet, psgallery
title: Avlista paket
ms.openlocfilehash: 4291b910dcea65b2ca241e55838ea00d4ec53ee4
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692357"
---
# <a name="unlisting-packages"></a><span data-ttu-id="025dd-103">Avlista paket</span><span class="sxs-lookup"><span data-stu-id="025dd-103">Unlisting Packages</span></span>

<span data-ttu-id="025dd-104">**Varför tar jag bort ett paket från PowerShell-galleriet som inte visas som ett alternativ?**</span><span class="sxs-lookup"><span data-stu-id="025dd-104">**Why is removing a package from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="025dd-105">PowerShell-galleriet stöder inte att användare tar bort sina paket permanent.</span><span class="sxs-lookup"><span data-stu-id="025dd-105">The PowerShell Gallery does not support users permanently deleting their packages.</span></span>
<span data-ttu-id="025dd-106">Detta gör det möjligt för andra att ta beroenden i dina paket utan att oroa dig för eventuella avbrott i framtiden.</span><span class="sxs-lookup"><span data-stu-id="025dd-106">This enables others to take dependencies on your packages without worrying about possible breaks in the future.</span></span>
<span data-ttu-id="025dd-107">Om pester-modulen exempelvis är beroende av Azure-modulen och Azure-modulen tas bort från galleriet, kan användarna inte längre använda pester-modulen.</span><span class="sxs-lookup"><span data-stu-id="025dd-107">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then users can no longer use the Pester module.</span></span>

<span data-ttu-id="025dd-108">I stället för att ta bort ett paket kan du ta bort listan.</span><span class="sxs-lookup"><span data-stu-id="025dd-108">Instead of removing a package you can unlist it.</span></span>

<span data-ttu-id="025dd-109">**Vad ingår i en lista med ett paket på PowerShell-galleriet?**</span><span class="sxs-lookup"><span data-stu-id="025dd-109">**What does unlisting a package on PowerShell Gallery do?**</span></span>

<span data-ttu-id="025dd-110">Om du avvisar ett paket som en modul eller ett skript i PowerShell-galleriet tas det bort från fliken paket. Dessutom går det inte att identifiera paket som inte finns i listan med hjälp av Sök fältet.</span><span class="sxs-lookup"><span data-stu-id="025dd-110">Unlisting a package such as a module or script in the PowerShell Gallery removes it from the Packages tab. In addition, unlisted packages will not be discoverable using the search bar.</span></span>
<span data-ttu-id="025dd-111">Det enda sättet att ladda ned ett paket som inte finns på är att ange det exakta namnet och versionen av paketet.</span><span class="sxs-lookup"><span data-stu-id="025dd-111">The only way to download an unlisted package is to specify the exact name and version of the package.</span></span>
<span data-ttu-id="025dd-112">Därför bryter inte listering av ett paket andra moduler eller skript som är beroende av det.</span><span class="sxs-lookup"><span data-stu-id="025dd-112">Because of this, the unlisting of a package will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="025dd-113">Om du vill ta bort en lista över ditt paket går du till sidan med paket information och väljer Ta bort modul.</span><span class="sxs-lookup"><span data-stu-id="025dd-113">To unlist your package, visit the package details page and select 'Delete Module'.</span></span> <span data-ttu-id="025dd-114">Avmarkera kryss rutan i listan och välj Spara.</span><span class="sxs-lookup"><span data-stu-id="025dd-114">Uncheck the 'Listed' checkbox, and select 'Save'.</span></span>

<span data-ttu-id="025dd-115">**Hur kan jag ta bort ett paket?**</span><span class="sxs-lookup"><span data-stu-id="025dd-115">**How can I remove a package?**</span></span>

<span data-ttu-id="025dd-116">Kontakta PowerShell-galleriet-administratörer om du får ett scenario där borttagning av paketet är nödvändigt.</span><span class="sxs-lookup"><span data-stu-id="025dd-116">If you experience a scenario where package deletion is necessary, contact the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="025dd-117">Giltiga borttagnings scenarier är:</span><span class="sxs-lookup"><span data-stu-id="025dd-117">Valid deletion scenarios are:</span></span>

- <span data-ttu-id="025dd-118">Problem med upphovs rätts intrång.</span><span class="sxs-lookup"><span data-stu-id="025dd-118">Issues of copyright infringement.</span></span>
- <span data-ttu-id="025dd-119">Paketet innehåller potentiellt skadligt innehåll.</span><span class="sxs-lookup"><span data-stu-id="025dd-119">Package contains potentially harmful content.</span></span>
- <span data-ttu-id="025dd-120">Paketet innehåller känsliga data.</span><span class="sxs-lookup"><span data-stu-id="025dd-120">Package contains sensitive data.</span></span>

<span data-ttu-id="025dd-121">Om du vill skicka en begäran om att ta bort paket till PowerShell-galleriet-administratörer besöker du paketets informations sida och väljer kontakta support.</span><span class="sxs-lookup"><span data-stu-id="025dd-121">To submit a Delete Package Request to the PowerShell Gallery Administrators, visit your package's detail page and select Contact Support.</span></span>
