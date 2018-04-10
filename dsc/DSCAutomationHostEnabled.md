---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSCAutomationHostEnabled-registernyckel
ms.openlocfilehash: 9fd71120b4959a7b14094922b453b05b217f3736
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
><span data-ttu-id="24e18-103">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="24e18-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="24e18-104">DSCAutomationHostEnabled-registernyckel</span><span class="sxs-lookup"><span data-stu-id="24e18-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="24e18-105">DSC använder den **DSCAutomationHostEnabled** registernyckel under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** att konfigurationen av datorn på första uppstart.</span><span class="sxs-lookup"><span data-stu-id="24e18-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="24e18-106">DSCAutomationHostEnabled stöder tre lägen:</span><span class="sxs-lookup"><span data-stu-id="24e18-106">DSCAutomationHostEnabled supports three modes:</span></span>

|  <span data-ttu-id="24e18-107">DSCAutomationHostEnabled värde</span><span class="sxs-lookup"><span data-stu-id="24e18-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="24e18-108">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="24e18-108">Description</span></span>   |
|---|---|
<span data-ttu-id="24e18-109">0</span><span class="sxs-lookup"><span data-stu-id="24e18-109">0</span></span> | <span data-ttu-id="24e18-110">Inaktivera konfigurerar datorn vid uppstart.</span><span class="sxs-lookup"><span data-stu-id="24e18-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="24e18-111">1</span><span class="sxs-lookup"><span data-stu-id="24e18-111">1</span></span> | <span data-ttu-id="24e18-112">Aktivera konfigurerar datorn vid uppstart.</span><span class="sxs-lookup"><span data-stu-id="24e18-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="24e18-113">2</span><span class="sxs-lookup"><span data-stu-id="24e18-113">2</span></span> | <span data-ttu-id="24e18-114">Aktivera konfigurerar datorn bara om DSC i väntande eller aktuella tillstånd.</span><span class="sxs-lookup"><span data-stu-id="24e18-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="24e18-115">Det här är standardkonfigurationen.</span><span class="sxs-lookup"><span data-stu-id="24e18-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="24e18-116">Se även</span><span class="sxs-lookup"><span data-stu-id="24e18-116">See Also</span></span>

<span data-ttu-id="24e18-117">Ett exempel på hur du använder den här funktionen körs konfigurationer vid första uppstart finns [konfigurera en virtuella datorer på första uppstart med hjälp av DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="24e18-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>