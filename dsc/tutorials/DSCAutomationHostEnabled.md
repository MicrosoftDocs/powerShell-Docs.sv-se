---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSCAutomationHostEnabled-registernyckel
ms.openlocfilehash: 2bccd2738b9f61efd656fdf0f98cf71affdbe781
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684803"
---
><span data-ttu-id="43138-103">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="43138-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="43138-104">DSCAutomationHostEnabled-registernyckel</span><span class="sxs-lookup"><span data-stu-id="43138-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="43138-105">DSC-använder den **DSCAutomationHostEnabled** registernyckel under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** att konfigurationen av dator vid första uppstart.</span><span class="sxs-lookup"><span data-stu-id="43138-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="43138-106">**DSCAutomationHostEnabled** stöder tre lägen:</span><span class="sxs-lookup"><span data-stu-id="43138-106">**DSCAutomationHostEnabled** supports three modes:</span></span>

|  <span data-ttu-id="43138-107">DSCAutomationHostEnabled-värde</span><span class="sxs-lookup"><span data-stu-id="43138-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="43138-108">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="43138-108">Description</span></span>   |
|---|---|
<span data-ttu-id="43138-109">0</span><span class="sxs-lookup"><span data-stu-id="43138-109">0</span></span> | <span data-ttu-id="43138-110">Inaktivera konfigurerar datorn vid uppstart.</span><span class="sxs-lookup"><span data-stu-id="43138-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="43138-111">1</span><span class="sxs-lookup"><span data-stu-id="43138-111">1</span></span> | <span data-ttu-id="43138-112">Aktivera konfigurerar datorn vid uppstart.</span><span class="sxs-lookup"><span data-stu-id="43138-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="43138-113">2</span><span class="sxs-lookup"><span data-stu-id="43138-113">2</span></span> | <span data-ttu-id="43138-114">Aktivera konfigurerar datorn endast om DSC är i väntande eller aktuella tillstånd.</span><span class="sxs-lookup"><span data-stu-id="43138-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="43138-115">Det här är standardkonfigurationen.</span><span class="sxs-lookup"><span data-stu-id="43138-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="43138-116">Se även</span><span class="sxs-lookup"><span data-stu-id="43138-116">See Also</span></span>

<span data-ttu-id="43138-117">Ett exempel på hur du använder den här funktionen körs konfigurationer vid första uppstart finns i [konfigurera en virtuell dator vid första uppstart med hjälp av DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="43138-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>
