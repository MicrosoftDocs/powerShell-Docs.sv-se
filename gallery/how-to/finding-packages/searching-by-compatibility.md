---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: galleriet, powershell, cmdlet, psgallery
title: Paket med operativsystemet eller kompatibla PowerShell-utgåvor
ms.openlocfilehash: 14038aa9b0453e1d06e6587e97da391b56297c75
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057186"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a><span data-ttu-id="1d4bc-103">Paket med kompatibla PowerShell-utgåvor eller operativsystem</span><span class="sxs-lookup"><span data-stu-id="1d4bc-103">Packages with compatible PowerShell Editions or Operating Systems</span></span>

<span data-ttu-id="1d4bc-104">Från och med version 5.1 finns finns PowerShell i olika utgåvor som anger olika funktionsuppsättningar och plattformen enhetskompatibilitet i hela.</span><span class="sxs-lookup"><span data-stu-id="1d4bc-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibilities.</span></span>

## <a name="searching-by-powershell-edition"></a><span data-ttu-id="1d4bc-105">Söka efter PowerShell-utgåva</span><span class="sxs-lookup"><span data-stu-id="1d4bc-105">Searching by PowerShell Edition</span></span>

<span data-ttu-id="1d4bc-106">Det finns två versioner av PowerShell:</span><span class="sxs-lookup"><span data-stu-id="1d4bc-106">The two editions of PowerShell are:</span></span>
- <span data-ttu-id="1d4bc-107">**Desktop Edition:** Bygger på .NET Framework och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på fullständiga utgåvor av Windows, till exempel Server Core och Windows-skrivbordet.</span><span class="sxs-lookup"><span data-stu-id="1d4bc-107">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="1d4bc-108">**Core Edition:** Bygger på .NET Core och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på begränsade utgåvor av Windows som Nano Server och Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="1d4bc-108">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a><span data-ttu-id="1d4bc-109">PowerShell-galleriet kan du filtrera paket som är kompatibel för specifika PowerShell-utgåvor</span><span class="sxs-lookup"><span data-stu-id="1d4bc-109">PowerShell Gallery allows you to filter packages compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="1d4bc-110">Om ett paket har kompatibla anges PSEditions de listas som en del av PowerShell-utgåvor på sidan paket och på paket resultat.</span><span class="sxs-lookup"><span data-stu-id="1d4bc-110">If a package has compatible PSEditions specified, they are listed as part of 'PowerShell Editions' in the package display page and also in packages results.</span></span>
<span data-ttu-id="1d4bc-111">Du kan också söka efter kompatibla paket med hjälp av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1d4bc-111">You can also search for compatible packages using PowerShell.</span></span>

![Visa objekt sida med PSEditions](../../Images/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a><span data-ttu-id="1d4bc-113">Sök efter paket i galleriet Användargränssnittet som fungerar i PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="1d4bc-113">Search for packages in the gallery UI that work on PowerShell Core</span></span>

<span data-ttu-id="1d4bc-114">Använd taggar: ”PSEdition_Desktop” och taggar: ”PSEdition_Core” till filter paketen på PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="1d4bc-114">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the packages on PowerShell Gallery.</span></span>

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="1d4bc-115">Använd taggar: ”PSEdition_Core” söker efter objekt som är kompatibel med PowerShell Core Edition.</span><span class="sxs-lookup"><span data-stu-id="1d4bc-115">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>

![Sökresultat för objekt som är kompatibla med grundläggande PSEdition](../../Images/searchresultswithpseditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="1d4bc-117">Använd taggar: ”PSEdition_Desktop” söker efter objekt som är kompatibel med PowerShell Desktop Edition.</span><span class="sxs-lookup"><span data-stu-id="1d4bc-117">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>

![Sökresultat för objekt som är kompatibel med Desktop PSEdition](../../Images/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a><span data-ttu-id="1d4bc-119">Sök efter paket för att hitta kompatibla versioner med hjälp av PowerShell</span><span class="sxs-lookup"><span data-stu-id="1d4bc-119">Search for packages to find compatible editions using PowerShell</span></span>
<span data-ttu-id="1d4bc-120">Du kan ange taggar om du vill filtrera för PowerShell-utgåva och operativsystem.</span><span class="sxs-lookup"><span data-stu-id="1d4bc-120">You can specify tags to filter for the PowerShell edition and OS.</span></span>
<span data-ttu-id="1d4bc-121">Du använder den `Find-Package` cmdlet att ange den `-Tag` parametern för att ange edition (och OS) du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="1d4bc-121">You use the `Find-Package` cmdlet specifying the `-Tag` parameter to specify the edition (and OS) you are targeting.</span></span>
<span data-ttu-id="1d4bc-122">Gillar det här:</span><span class="sxs-lookup"><span data-stu-id="1d4bc-122">Like this:</span></span>

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a><span data-ttu-id="1d4bc-123">Söker efter operativsystem</span><span class="sxs-lookup"><span data-stu-id="1d4bc-123">Searching by Operating System</span></span>

<span data-ttu-id="1d4bc-124">Eftersom PowerShell Core är tillgänglig för Windows, Linux och MacOS kan-paket i galleriet utformas för valfri kombination av dessa operativsystem.</span><span class="sxs-lookup"><span data-stu-id="1d4bc-124">Since PowerShell Core is available for Windows, Linux, and MacOS, packages in the Gallery may be designed for any combination of these operating systems.</span></span> <span data-ttu-id="1d4bc-125">Använd följande taggar om searchs för att hitta paket som taggats med operativsystemet i galleriet Användargränssnittet:</span><span class="sxs-lookup"><span data-stu-id="1d4bc-125">In the gallery UI use the following searchs tags to find packages tagged by operating system:</span></span>

- <span data-ttu-id="1d4bc-126">Taggar: "Windows"</span><span class="sxs-lookup"><span data-stu-id="1d4bc-126">Tags: "Windows"</span></span>
- <span data-ttu-id="1d4bc-127">Taggar: "Linux"</span><span class="sxs-lookup"><span data-stu-id="1d4bc-127">Tags: "Linux"</span></span>
- <span data-ttu-id="1d4bc-128">Taggar: "MacOS"</span><span class="sxs-lookup"><span data-stu-id="1d4bc-128">Tags: "MacOS"</span></span>

<span data-ttu-id="1d4bc-129">Du kan ange dessa taggar på `Find-Module` (och andra cmdlets i modulen PowerShellGet), så här:</span><span class="sxs-lookup"><span data-stu-id="1d4bc-129">You can specify these tags on `Find-Module` (and other cmdlets in the PowerShellGet module), like this:</span></span>

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a><span data-ttu-id="1d4bc-130">Söker efter flera enhetskompatibilitet i hela</span><span class="sxs-lookup"><span data-stu-id="1d4bc-130">Searching for Multiple Compatibilities</span></span>

<span data-ttu-id="1d4bc-131">Du kan se ut för ett paket som har flera enhetskompatibilitet i hela med hjälp av syntaxen:</span><span class="sxs-lookup"><span data-stu-id="1d4bc-131">You can look for a package that has multiple compatibilities by using the syntax:</span></span>

<span data-ttu-id="1d4bc-132">Taggar: ”Compatibility1” ”Compatibility2”</span><span class="sxs-lookup"><span data-stu-id="1d4bc-132">Tags: "Compatibility1" "Compatibility2"</span></span>

<span data-ttu-id="1d4bc-133">Till exempel om du letar efter ett paket med PowerShell Core kompatibilitet som körs på både min Windows- och Linux-datorer, Använd söktaggar:</span><span class="sxs-lookup"><span data-stu-id="1d4bc-133">For example, if you are looking for a package with PowerShell Core Compatibility that runs on both my Windows and Linux machines, use the search tags:</span></span>

<span data-ttu-id="1d4bc-134">Taggar: "PSEdition_Core" "Windows" "Linux"</span><span class="sxs-lookup"><span data-stu-id="1d4bc-134">Tags: "PSEdition_Core" "Windows" "Linux"</span></span>

<span data-ttu-id="1d4bc-135">Om du vill söka med hjälp av PowerShell, kan du använda den `Find-Module` (och andra cmdlets i modulen PowerShellGet), så här:</span><span class="sxs-lookup"><span data-stu-id="1d4bc-135">To search using PowerShell, you can use the `Find-Module` (and the other cmdlets in the PowerShellGet module), like this:</span></span>

```powershell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a><span data-ttu-id="1d4bc-136">Mer information om redigering och söka efter paket med kompatibla PowerShell-utgåvor</span><span class="sxs-lookup"><span data-stu-id="1d4bc-136">More details on authoring and finding the packages with compatible PowerShell Editions</span></span>

- [<span data-ttu-id="1d4bc-137">Moduler med PSEditions</span><span class="sxs-lookup"><span data-stu-id="1d4bc-137">Modules with PSEditions</span></span>](../../concepts/module-psedition-support.md)
- [<span data-ttu-id="1d4bc-138">Skript med PSEditions</span><span class="sxs-lookup"><span data-stu-id="1d4bc-138">Scripts with PSEditions</span></span>](../../concepts/script-psedition-support.md)
