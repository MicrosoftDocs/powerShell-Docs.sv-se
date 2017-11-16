---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSCAutomationHostEnabled registernyckel
ms.openlocfilehash: e47c929b366f93738343eabc431aab5a4428352d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
><span data-ttu-id="2ac64-103">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="2ac64-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="2ac64-104">DSCAutomationHostEnabled registernyckel</span><span class="sxs-lookup"><span data-stu-id="2ac64-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="2ac64-105">DSC använder den **DSCAutomationHostEnabled** registernyckel under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** att konfigurationen av datorn på första uppstart.</span><span class="sxs-lookup"><span data-stu-id="2ac64-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="2ac64-106">DSCAutomationHostEnabled stöder tre lägen:</span><span class="sxs-lookup"><span data-stu-id="2ac64-106">DSCAutomationHostEnabled supports three modes:</span></span>

|  <span data-ttu-id="2ac64-107">DSCAutomationHostEnabled värde</span><span class="sxs-lookup"><span data-stu-id="2ac64-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="2ac64-108">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2ac64-108">Description</span></span>   | 
|---|---| 
<span data-ttu-id="2ac64-109">0</span><span class="sxs-lookup"><span data-stu-id="2ac64-109">0</span></span> | <span data-ttu-id="2ac64-110">Inaktivera konfigurerar datorn vid uppstart.</span><span class="sxs-lookup"><span data-stu-id="2ac64-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="2ac64-111">1</span><span class="sxs-lookup"><span data-stu-id="2ac64-111">1</span></span> | <span data-ttu-id="2ac64-112">Aktivera konfigurerar datorn vid uppstart.</span><span class="sxs-lookup"><span data-stu-id="2ac64-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="2ac64-113">2</span><span class="sxs-lookup"><span data-stu-id="2ac64-113">2</span></span> | <span data-ttu-id="2ac64-114">Aktivera konfigurerar datorn bara om DSC i väntande eller aktuella tillstånd.</span><span class="sxs-lookup"><span data-stu-id="2ac64-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="2ac64-115">Det här är standardkonfigurationen.</span><span class="sxs-lookup"><span data-stu-id="2ac64-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="2ac64-116">Se även</span><span class="sxs-lookup"><span data-stu-id="2ac64-116">See Also</span></span>

<span data-ttu-id="2ac64-117">Ett exempel på hur du använder den här funktionen körs konfigurationer vid första uppstart finns [konfigurera en virtuella datorer på första uppstart med hjälp av DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="2ac64-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>


