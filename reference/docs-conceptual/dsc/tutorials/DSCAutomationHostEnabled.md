---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: DSCAutomationHostEnabled-registernyckel
ms.openlocfilehash: 0f35a798e5b7d51fdfb66e4e79ceab0e36ccea5b
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808341"
---
# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="5561d-103">DSCAutomationHostEnabled-registernyckel</span><span class="sxs-lookup"><span data-stu-id="5561d-103">DSCAutomationHostEnabled registry key</span></span>

> <span data-ttu-id="5561d-104">Gäller för: Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="5561d-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="5561d-105">DSC använder register nyckeln **dscautomationhostenabled registernyckel** under **HKEY_LOCAL_MACHINE \software\microsoft\windows\currentversion\policies\system** för att aktivera konfiguration av datorn vid första uppstarten.</span><span class="sxs-lookup"><span data-stu-id="5561d-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="5561d-106">**Dscautomationhostenabled registernyckel** stöder tre lägen:</span><span class="sxs-lookup"><span data-stu-id="5561d-106">**DSCAutomationHostEnabled** supports three modes:</span></span>

|  <span data-ttu-id="5561d-107">Dscautomationhostenabled registernyckel-värde</span><span class="sxs-lookup"><span data-stu-id="5561d-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="5561d-108">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5561d-108">Description</span></span>   |
|---|---|
<span data-ttu-id="5561d-109">0</span><span class="sxs-lookup"><span data-stu-id="5561d-109">0</span></span> | <span data-ttu-id="5561d-110">Inaktivera konfigurering av datorn vid uppstart.</span><span class="sxs-lookup"><span data-stu-id="5561d-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="5561d-111">1</span><span class="sxs-lookup"><span data-stu-id="5561d-111">1</span></span> | <span data-ttu-id="5561d-112">Aktivera konfigurering av datorn vid uppstart.</span><span class="sxs-lookup"><span data-stu-id="5561d-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="5561d-113">2</span><span class="sxs-lookup"><span data-stu-id="5561d-113">2</span></span> | <span data-ttu-id="5561d-114">Aktivera endast konfigurering av datorn om DSC är i vänte läge eller aktuellt tillstånd.</span><span class="sxs-lookup"><span data-stu-id="5561d-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="5561d-115">Detta är standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="5561d-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="5561d-116">Se även</span><span class="sxs-lookup"><span data-stu-id="5561d-116">See Also</span></span>

<span data-ttu-id="5561d-117">Ett exempel på hur du använder den här funktionen för att köra konfigurationer vid första uppstarten finns i [Konfigurera en virtuell dator vid första uppstarten med hjälp av DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="5561d-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>
