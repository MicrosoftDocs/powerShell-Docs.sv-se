---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: DSCAutomationHostEnabled-registernyckel
ms.openlocfilehash: 2bccd2738b9f61efd656fdf0f98cf71affdbe781
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942169"
---
><span data-ttu-id="eb676-103">Gäller för: Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="eb676-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="eb676-104">DSCAutomationHostEnabled-registernyckel</span><span class="sxs-lookup"><span data-stu-id="eb676-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="eb676-105">DSC använder register nyckeln **dscautomationhostenabled registernyckel** under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** för att aktivera konfiguration av datorn vid första uppstarten.</span><span class="sxs-lookup"><span data-stu-id="eb676-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="eb676-106">**Dscautomationhostenabled registernyckel** stöder tre lägen:</span><span class="sxs-lookup"><span data-stu-id="eb676-106">**DSCAutomationHostEnabled** supports three modes:</span></span>

|  <span data-ttu-id="eb676-107">Dscautomationhostenabled registernyckel-värde</span><span class="sxs-lookup"><span data-stu-id="eb676-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="eb676-108">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eb676-108">Description</span></span>   |
|---|---|
<span data-ttu-id="eb676-109">0</span><span class="sxs-lookup"><span data-stu-id="eb676-109">0</span></span> | <span data-ttu-id="eb676-110">Inaktivera konfigurering av datorn vid uppstart.</span><span class="sxs-lookup"><span data-stu-id="eb676-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="eb676-111">1</span><span class="sxs-lookup"><span data-stu-id="eb676-111">1</span></span> | <span data-ttu-id="eb676-112">Aktivera konfigurering av datorn vid uppstart.</span><span class="sxs-lookup"><span data-stu-id="eb676-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="eb676-113">2</span><span class="sxs-lookup"><span data-stu-id="eb676-113">2</span></span> | <span data-ttu-id="eb676-114">Aktivera endast konfigurering av datorn om DSC är i vänte läge eller aktuellt tillstånd.</span><span class="sxs-lookup"><span data-stu-id="eb676-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="eb676-115">Detta är standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="eb676-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="eb676-116">Se även</span><span class="sxs-lookup"><span data-stu-id="eb676-116">See Also</span></span>

<span data-ttu-id="eb676-117">Ett exempel på hur du använder den här funktionen för att köra konfigurationer vid första uppstarten finns i [Konfigurera en virtuell dator vid första uppstarten med hjälp av DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="eb676-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>
