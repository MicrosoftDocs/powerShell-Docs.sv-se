---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: DSCAutomationHostEnabled-registernyckel
description: Den här artikeln definierar de värden som kan anges i register nyckeln Dscautomationhostenabled registernyckel
ms.openlocfilehash: 50f752dd882e9b0787ed4a4cbc22731fc1d608f5
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656186"
---
# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="75932-104">DSCAutomationHostEnabled-registernyckel</span><span class="sxs-lookup"><span data-stu-id="75932-104">DSCAutomationHostEnabled registry key</span></span>

> <span data-ttu-id="75932-105">Gäller för: Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="75932-105">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="75932-106">DSC använder register nyckeln **dscautomationhostenabled registernyckel** under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** för att aktivera konfiguration av datorn vid första start.</span><span class="sxs-lookup"><span data-stu-id="75932-106">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** to enable configuration of the machine at initial boot-up.</span></span> <span data-ttu-id="75932-107">**Dscautomationhostenabled registernyckel** stöder tre lägen:</span><span class="sxs-lookup"><span data-stu-id="75932-107">**DSCAutomationHostEnabled** supports three modes:</span></span>

| <span data-ttu-id="75932-108">Dscautomationhostenabled registernyckel-värde</span><span class="sxs-lookup"><span data-stu-id="75932-108">DSCAutomationHostEnabled Value</span></span> |                                              <span data-ttu-id="75932-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="75932-109">Description</span></span>                                              |
| ------------------------------ | ----------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="75932-110">0</span><span class="sxs-lookup"><span data-stu-id="75932-110">0</span></span>                              | <span data-ttu-id="75932-111">Inaktivera konfigurering av datorn vid uppstart.</span><span class="sxs-lookup"><span data-stu-id="75932-111">Disable configuring the machine at boot-up.</span></span>                                                           |
| <span data-ttu-id="75932-112">1</span><span class="sxs-lookup"><span data-stu-id="75932-112">1</span></span>                              | <span data-ttu-id="75932-113">Aktivera konfigurering av datorn vid uppstart.</span><span class="sxs-lookup"><span data-stu-id="75932-113">Enable configuring the machine at boot-up.</span></span>                                                            |
| <span data-ttu-id="75932-114">2</span><span class="sxs-lookup"><span data-stu-id="75932-114">2</span></span>                              | <span data-ttu-id="75932-115">Aktivera endast konfigurering av datorn om DSC är i vänte läge eller aktuellt tillstånd.</span><span class="sxs-lookup"><span data-stu-id="75932-115">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="75932-116">Detta är standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="75932-116">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="75932-117">Se även</span><span class="sxs-lookup"><span data-stu-id="75932-117">See Also</span></span>

<span data-ttu-id="75932-118">Ett exempel på hur du använder den här funktionen för att köra konfigurationer vid första uppstarten finns i [Konfigurera en virtuell dator vid första uppstarten med hjälp av DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="75932-118">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>
