---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: a6366e18b4b6478bfab89475bc6975e6491da9f7
ms.sourcegitcommit: 735ccab3fb3834ccd8559fab6700b798e8e5ffbf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/25/2018
---
# <a name="windows-management-framework-wmf-50-rtm-release-notes-overview"></a><span data-ttu-id="d3cac-102">Windows Management Framework (WMF) 5.0 RTM versionen anteckningar: översikt</span><span class="sxs-lookup"><span data-stu-id="d3cac-102">Windows Management Framework (WMF) 5.0 RTM Release Notes Overview</span></span>

<span data-ttu-id="d3cac-103">**WMF 5.0 är superceeded av WMF 5.1. Användare med WMF 5.0 måste uppgradera till WMF 5.1 få support. Följ den [installation intructions WMF 5.1](../5.1/install-configure.md)**</span><span class="sxs-lookup"><span data-stu-id="d3cac-103">**WMF 5.0 is superceeded by WMF 5.1. Users with WMF 5.0 must upgrade to WMF 5.1 to receive support. Please follow the [installation intructions of WMF 5.1](../5.1/install-configure.md)**</span></span>

<span data-ttu-id="d3cac-104">Windows Management Framework (WMF) 5.0 ger RTM funktioner som har uppdaterats från WMF 4.0.</span><span class="sxs-lookup"><span data-stu-id="d3cac-104">Windows Management Framework (WMF) 5.0 RTM brings functionality that has been updated from WMF 4.0.</span></span> <span data-ttu-id="d3cac-105">WMF 5.0 RTM är tillgängligt endast för installation på **Windows Server 2012 R2**, **Windows Server 2012**, **Windows Server 2008 R2**, **Windows 8.1**, och **Windows 7 SP1** och innehåller uppdaterade versioner eller Introduktion av följande funktioner:</span><span class="sxs-lookup"><span data-stu-id="d3cac-105">WMF 5.0 RTM is available for installation only on **Windows Server 2012 R2**, **Windows Server 2012**, **Windows Server 2008 R2**, **Windows 8.1**, and **Windows 7 SP1** and contains updated versions or introduction of the following features:</span></span>

- <span data-ttu-id="d3cac-106">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d3cac-106">Windows PowerShell</span></span>
- <span data-ttu-id="d3cac-107">JEA (Just Enough Administration)</span><span class="sxs-lookup"><span data-stu-id="d3cac-107">Just Enough Administration (JEA)</span></span>
- <span data-ttu-id="d3cac-108">Önskad tillståndskonfiguration i Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d3cac-108">Windows PowerShell Desired State Configuration (DSC)</span></span>
- <span data-ttu-id="d3cac-109">Windows PowerShell® Integrated Scripting Environment (ISE)</span><span class="sxs-lookup"><span data-stu-id="d3cac-109">Windows PowerShell Integrated Scripting Environment (ISE)</span></span>
- <span data-ttu-id="d3cac-110">Windows PowerShell-webbtjänster (Management OData IIS Extension)</span><span class="sxs-lookup"><span data-stu-id="d3cac-110">Windows PowerShell Web Services (Management OData IIS Extension)</span></span>
- <span data-ttu-id="d3cac-111">Windows Remote Management (WinRM)</span><span class="sxs-lookup"><span data-stu-id="d3cac-111">Windows Remote Management (WinRM)</span></span>
- <span data-ttu-id="d3cac-112">Windows Management Instrumentation (WMI)</span><span class="sxs-lookup"><span data-stu-id="d3cac-112">Windows Management Instrumentation (WMI)</span></span>

<span data-ttu-id="d3cac-113">WMF 5.0 RTM ersätter den [WMF 5.0 produktion Preview](http://blogs.msdn.com/b/powershell/archive/2015/08/31/windows-management-framework-5-0-production-preview-is-now-available.aspx).</span><span class="sxs-lookup"><span data-stu-id="d3cac-113">WMF 5.0 RTM replaces the [WMF 5.0 Production Preview](http://blogs.msdn.com/b/powershell/archive/2015/08/31/windows-management-framework-5-0-production-preview-is-now-available.aspx).</span></span> <span data-ttu-id="d3cac-114">Du kan installera WMF 5.0 RTM utan att avinstallera WMF 5.0 produktion Preview, men du måste avinstallera alla andra äldre versioner av WMF 5.0 förhandsgranskningar innan du installerar WMF 5.0 RTM.</span><span class="sxs-lookup"><span data-stu-id="d3cac-114">You can install WMF 5.0 RTM without uninstalling WMF 5.0 Production Preview, but you must uninstall all other older releases of WMF 5.0 previews before installing the WMF 5.0 RTM.</span></span>

<span data-ttu-id="d3cac-115">*Obs:* om du kör Windows 10 kan du få samma uppsättning funktioner som är tillgängliga i WMF 5.0 RTM genom att uppdatera till November uppdateringen av Windows 10 (Version 1511).</span><span class="sxs-lookup"><span data-stu-id="d3cac-115">*Note:* If you are running Windows 10, you can get the same set of functionality available in WMF 5.0 RTM by updating to the November update of Windows 10 (Version 1511).</span></span> <span data-ttu-id="d3cac-116">Om du inte redan har uppdaterat din Windows 10-system, klicka på knappen Start och välj sedan Inställningar > uppdatering och säkerhet > Windows Update > Sök efter uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="d3cac-116">If you have not already updated your Windows 10 system, select the Start button, then select Settings > Update & security > Windows Update > Check for updates.</span></span>
