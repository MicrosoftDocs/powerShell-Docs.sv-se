---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSCAutomationHostEnabled registernyckel
ms.openlocfilehash: c58b7a8f2485ff02f09763749a3de8a75f882d19
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
><span data-ttu-id="fcbfc-103">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="fcbfc-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="fcbfc-104">DSCAutomationHostEnabled registernyckel</span><span class="sxs-lookup"><span data-stu-id="fcbfc-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="fcbfc-105">DSC använder den **DSCAutomationHostEnabled** registernyckel under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** att konfigurationen av datorn på första uppstart.</span><span class="sxs-lookup"><span data-stu-id="fcbfc-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="fcbfc-106">DSCAutomationHostEnabled stöder tre lägen:</span><span class="sxs-lookup"><span data-stu-id="fcbfc-106">DSCAutomationHostEnabled supports three modes:</span></span>

|  <span data-ttu-id="fcbfc-107">DSCAutomationHostEnabled värde</span><span class="sxs-lookup"><span data-stu-id="fcbfc-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="fcbfc-108">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="fcbfc-108">Description</span></span>   | 
|---|---| 
<span data-ttu-id="fcbfc-109">0</span><span class="sxs-lookup"><span data-stu-id="fcbfc-109">0</span></span> | <span data-ttu-id="fcbfc-110">Inaktivera konfigurerar datorn vid uppstart.</span><span class="sxs-lookup"><span data-stu-id="fcbfc-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="fcbfc-111">1</span><span class="sxs-lookup"><span data-stu-id="fcbfc-111">1</span></span> | <span data-ttu-id="fcbfc-112">Aktivera konfigurerar datorn vid uppstart.</span><span class="sxs-lookup"><span data-stu-id="fcbfc-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="fcbfc-113">2</span><span class="sxs-lookup"><span data-stu-id="fcbfc-113">2</span></span> | <span data-ttu-id="fcbfc-114">Aktivera konfigurerar datorn bara om DSC i väntande eller aktuella tillstånd.</span><span class="sxs-lookup"><span data-stu-id="fcbfc-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="fcbfc-115">Det här är standardkonfigurationen.</span><span class="sxs-lookup"><span data-stu-id="fcbfc-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="fcbfc-116">Se även</span><span class="sxs-lookup"><span data-stu-id="fcbfc-116">See Also</span></span>

<span data-ttu-id="fcbfc-117">Ett exempel på hur du använder den här funktionen körs konfigurationer vid första uppstart finns [konfigurera en virtuella datorer på första uppstart med hjälp av DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="fcbfc-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>


