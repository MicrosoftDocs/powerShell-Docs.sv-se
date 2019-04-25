---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSCAutomationHostEnabled-registernyckel
ms.openlocfilehash: 2bccd2738b9f61efd656fdf0f98cf71affdbe781
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076503"
---
><span data-ttu-id="a21b9-103">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a21b9-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="a21b9-104">DSCAutomationHostEnabled-registernyckel</span><span class="sxs-lookup"><span data-stu-id="a21b9-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="a21b9-105">DSC-använder den **DSCAutomationHostEnabled** registernyckel under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** att konfigurationen av dator vid första uppstart.</span><span class="sxs-lookup"><span data-stu-id="a21b9-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="a21b9-106">**DSCAutomationHostEnabled** stöder tre lägen:</span><span class="sxs-lookup"><span data-stu-id="a21b9-106">**DSCAutomationHostEnabled** supports three modes:</span></span>

|  <span data-ttu-id="a21b9-107">DSCAutomationHostEnabled-värde</span><span class="sxs-lookup"><span data-stu-id="a21b9-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="a21b9-108">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a21b9-108">Description</span></span>   |
|---|---|
<span data-ttu-id="a21b9-109">0</span><span class="sxs-lookup"><span data-stu-id="a21b9-109">0</span></span> | <span data-ttu-id="a21b9-110">Inaktivera konfigurerar datorn vid uppstart.</span><span class="sxs-lookup"><span data-stu-id="a21b9-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="a21b9-111">1</span><span class="sxs-lookup"><span data-stu-id="a21b9-111">1</span></span> | <span data-ttu-id="a21b9-112">Aktivera konfigurerar datorn vid uppstart.</span><span class="sxs-lookup"><span data-stu-id="a21b9-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="a21b9-113">2</span><span class="sxs-lookup"><span data-stu-id="a21b9-113">2</span></span> | <span data-ttu-id="a21b9-114">Aktivera konfigurerar datorn endast om DSC är i väntande eller aktuella tillstånd.</span><span class="sxs-lookup"><span data-stu-id="a21b9-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="a21b9-115">Detta är standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="a21b9-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="a21b9-116">Se även</span><span class="sxs-lookup"><span data-stu-id="a21b9-116">See Also</span></span>

<span data-ttu-id="a21b9-117">Ett exempel på hur du använder den här funktionen körs konfigurationer vid första uppstart finns i [konfigurera en virtuell dator vid första uppstart med hjälp av DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="a21b9-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>
