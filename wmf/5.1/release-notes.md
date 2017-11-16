---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
title: WMF 5.1 viktig information
ms.openlocfilehash: ce9bc7791facfcc2cce9468689e88a26154bda7d
ms.sourcegitcommit: 3f49bd2e0b786e69c71393c00ad85d05a8466753
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/04/2017
---
# <a name="windows-management-framework-wmf-51-release-notes"></a><span data-ttu-id="100d0-103">Viktig information om Windows Management Framework (WMF) 5.1</span><span class="sxs-lookup"><span data-stu-id="100d0-103">Windows Management Framework (WMF) 5.1 Release Notes</span></span> #

<span data-ttu-id="100d0-104">WMF 5.1 innehåller PowerShell, WMI, WinRM och Software Inventory Logging (SIL) komponenter som släpptes med Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="100d0-104">WMF 5.1 includes the PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span>
<span data-ttu-id="100d0-105">WMF 5.1 kan installeras på Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 och 2012 R2, och ger ett antal förbättringar över WMF 5.0 RTM inklusive:</span><span class="sxs-lookup"><span data-stu-id="100d0-105">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides a number of improvements over WMF 5.0 RTM including:</span></span>

- <span data-ttu-id="100d0-106">Nya cmdlet: ar: lokala användare och grupper. Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="100d0-106">New cmdlets: local users and groups; Get-ComputerInfo</span></span>
- <span data-ttu-id="100d0-107">PowerShellGet förbättringar omfattar att använda signerade moduler och installera JEA moduler</span><span class="sxs-lookup"><span data-stu-id="100d0-107">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="100d0-108">PackageManagement tillagt stöd för behållare, CBS installationsprogrammet EXE-baserad installation, CAB-paket</span><span class="sxs-lookup"><span data-stu-id="100d0-108">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="100d0-109">Förbättringar av DSC-och PowerShell-felsökning</span><span class="sxs-lookup"><span data-stu-id="100d0-109">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="100d0-110">Förbättringar av säkerhet inklusive tillämpning av katalogen signerats moduler som kommer från servern hämtar och när du använder PowerShellGet-cmdlets</span><span class="sxs-lookup"><span data-stu-id="100d0-110">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="100d0-111">Svar på ett antal frågor och problem</span><span class="sxs-lookup"><span data-stu-id="100d0-111">Responses to a number of user requests and issues</span></span>

<span data-ttu-id="100d0-112">**Viktig information:**</span><span class="sxs-lookup"><span data-stu-id="100d0-112">**Important notes:**</span></span>

- <span data-ttu-id="100d0-113">**WMF 5.1 kräver .NET Framework 4.5.2** (eller senare).</span><span class="sxs-lookup"><span data-stu-id="100d0-113">**WMF 5.1 requires the .NET Framework 4.5.2** (or above).</span></span> <span data-ttu-id="100d0-114">Installationen lyckas, men viktiga funktioner misslyckas om .NET 4.5.2 (eller senare) har inte installerats.</span><span class="sxs-lookup"><span data-stu-id="100d0-114">Installation will succeed, but key features will fail if .NET 4.5.2 (or above) is not installed.</span></span> <span data-ttu-id="100d0-115">Instruktioner finns i den [installera och konfigurera WMF 5.1 ](https://msdn.microsoft.com/en-us/powershell/wmf/5.1/install-configure) avsnittet.</span><span class="sxs-lookup"><span data-stu-id="100d0-115">Instructions are available in the [Install and Configure WMF 5.1 ](https://msdn.microsoft.com/en-us/powershell/wmf/5.1/install-configure) topic.</span></span>
- <span data-ttu-id="100d0-116">WMF 5.1 Preview måste avinstalleras innan du installerar WMF 5.1 RTM.</span><span class="sxs-lookup"><span data-stu-id="100d0-116">WMF 5.1 Preview must be uninstalled before installing WMF 5.1 RTM.</span></span>
- <span data-ttu-id="100d0-117">WMF 5.1 kan installeras direkt via WMF 5.0 eller WMF 4.0.</span><span class="sxs-lookup"><span data-stu-id="100d0-117">WMF 5.1 may be installed directly over WMF 5.0 or WMF 4.0.</span></span>
- <span data-ttu-id="100d0-118">Det är __krävs inte__ att installera WMF 4.0 innan du installerar WMF 5.1 på Windows 7 och Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="100d0-118">It is __not required__ to install WMF 4.0 prior to installing WMF 5.1 on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="100d0-119">Som var ett problem för WMF 5.1 förhandsversionen och har lösts.</span><span class="sxs-lookup"><span data-stu-id="100d0-119">That was an issue for the WMF 5.1 Preview release, and has been resolved.</span></span>  


