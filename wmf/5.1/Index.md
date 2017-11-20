---
ms.date: 2017-08-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
title: WMF 5.1-versionskommentarer
ms.openlocfilehash: 3a6b7fb84d679d9bbe7a89e30c8c769e26f7381a
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/04/2017
---
# <a name="windows-management-framework-wmf-51"></a><span data-ttu-id="d2f84-103">WMF (Windows Management Framework) 5.1</span><span class="sxs-lookup"><span data-stu-id="d2f84-103">Windows Management Framework (WMF) 5.1</span></span> #

<span data-ttu-id="d2f84-104">WMF ger användare möjlighet att uppdatera befintliga Windows-datorer till de versionerna av PowerShell-, WMI-, WinRM- och SIL (Software Inventory Logging)-komponenterna som släpptes med Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="d2f84-104">WMF provides users with the ability to update existing Windows systems to the versions of PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span> 

<span data-ttu-id="d2f84-105">WMF 5.1 kan installeras på Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 och 2012 R2 och erbjuder ett antal förbättringar över WMF 5.0 RTM inklusive:</span><span class="sxs-lookup"><span data-stu-id="d2f84-105">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides a number of improvements over WMF 5.0 RTM including:</span></span>

- <span data-ttu-id="d2f84-106">Nya cmdlet:ar: lokala användare och grupper, Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="d2f84-106">New cmdlets: local users and groups; Get-ComputerInfo</span></span>
- <span data-ttu-id="d2f84-107">PowerShellGet-förbättringarna omfattar att framtvinga signerade moduler och installera JEA-moduler</span><span class="sxs-lookup"><span data-stu-id="d2f84-107">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="d2f84-108">PackageManagement har lagt till stöd för behållare, CBS-installation, EXE-baserad installation, CAB-paket</span><span class="sxs-lookup"><span data-stu-id="d2f84-108">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="d2f84-109">Felsökningsförbättringar för DSC- och PowerShell-klasser</span><span class="sxs-lookup"><span data-stu-id="d2f84-109">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="d2f84-110">Säkerhetsförbättringar, inklusive framtvingning av katalogsignerade moduler som kommer från Pull-servern och när du använder PowerShellGet-cmdletar</span><span class="sxs-lookup"><span data-stu-id="d2f84-110">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="d2f84-111">Svar på ett antal förfrågningar och problem från användare</span><span class="sxs-lookup"><span data-stu-id="d2f84-111">Responses to a number of user requests and issues</span></span>

<span data-ttu-id="d2f84-112">Läs mer om nyheter i den här versionen genom att bläddra i avsnitten som finns under [nya scenarier och funktioner](https://docs.microsoft.com/en-us/powershell/wmf/5.1/scenarios-features).</span><span class="sxs-lookup"><span data-stu-id="d2f84-112">To learn about what is new in this release, browse the topics listed under [New Scenarios and Features](https://docs.microsoft.com/en-us/powershell/wmf/5.1/scenarios-features).</span></span> 

<span data-ttu-id="d2f84-113">Avsnittet [installera och konfigurera](https://docs.microsoft.com/en-us/powershell/wmf/5.1/install-configure) listar kraven och ger installationsanvisningar för WMF.</span><span class="sxs-lookup"><span data-stu-id="d2f84-113">The [Install and Configure](https://docs.microsoft.com/en-us/powershell/wmf/5.1/install-configure) topic lists the requirements and provides installation instructions for WMF.</span></span> 

<span data-ttu-id="d2f84-114">Avsnittet [kompatibilitet](https://docs.microsoft.com/en-us/powershell/wmf/5.1/compatibility) listar vilka versioner av WMF som kan installeras på vilka Windows-utgåvor.</span><span class="sxs-lookup"><span data-stu-id="d2f84-114">The [Compatibility](https://docs.microsoft.com/en-us/powershell/wmf/5.1/compatibility) topic lists which versions of WMF may be installed on which Windows releases.</span></span> 

<span data-ttu-id="d2f84-115">[Produktkompatibilitet](https://docs.microsoft.com/en-us/powershell/wmf/5.1/productincompat) listar de Microsoft-program som ännu inte godkänt WMF 5.1 för användning.</span><span class="sxs-lookup"><span data-stu-id="d2f84-115">[Product Compatibility](https://docs.microsoft.com/en-us/powershell/wmf/5.1/productincompat) lists the Microsoft applications that have not approved WMF 5.1 for use at this time.</span></span> 

<span data-ttu-id="d2f84-116">Information om de olika komponenterna i WMF finns i MSDN-dokumentationen:</span><span class="sxs-lookup"><span data-stu-id="d2f84-116">Details for the components of WMF will be found in MSDN documentation:</span></span>

- [<span data-ttu-id="d2f84-117">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="d2f84-117">PowerShell 5.1</span></span>](https://docs.microsoft.com/en-us/powershell/) 
- <span data-ttu-id="d2f84-118">[WMI](https://msdn.microsoft.com/en-us/library/jj152383(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="d2f84-118">[WMI](https://msdn.microsoft.com/en-us/library/jj152383(v=vs.85).aspx)</span></span>
- <span data-ttu-id="d2f84-119">[WinRM](https://msdn.microsoft.com/en-us/library/aa384426(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="d2f84-119">[WinRM](https://msdn.microsoft.com/en-us/library/aa384426(v=vs.85).aspx)</span></span>
- <span data-ttu-id="d2f84-120">[Loggning av programvaruinventering](https://technet.microsoft.com/en-us/library/dn383584(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="d2f84-120">[Software Inventory Logging](https://technet.microsoft.com/en-us/library/dn383584(v=ws.11).aspx)</span></span>

