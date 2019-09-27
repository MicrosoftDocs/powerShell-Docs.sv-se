---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: Galleri, PowerShell, cmdlet, psgallery
title: Paket med kompatibla PowerShell-utgåvor eller operativ system
ms.openlocfilehash: 14038aa9b0453e1d06e6587e97da391b56297c75
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71329150"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a><span data-ttu-id="330ad-103">Paket med kompatibla PowerShell-utgåvor eller operativ system</span><span class="sxs-lookup"><span data-stu-id="330ad-103">Packages with compatible PowerShell Editions or Operating Systems</span></span>

<span data-ttu-id="330ad-104">Från och med version 5,1 är PowerShell tillgängligt i olika utgåvor som kännetecknar varierande funktions uppsättningar och plattforms oberoende plattformar.</span><span class="sxs-lookup"><span data-stu-id="330ad-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibilities.</span></span>

## <a name="searching-by-powershell-edition"></a><span data-ttu-id="330ad-105">Söker efter PowerShell-utgåva</span><span class="sxs-lookup"><span data-stu-id="330ad-105">Searching by PowerShell Edition</span></span>

<span data-ttu-id="330ad-106">De två versionerna av PowerShell är:</span><span class="sxs-lookup"><span data-stu-id="330ad-106">The two editions of PowerShell are:</span></span>
- <span data-ttu-id="330ad-107">**Desktop Edition:** Bygger på .NET Framework och ger kompatibilitet med skript och moduler som mål versioner av PowerShell som körs på fullständiga versioner av Windows, till exempel Server Core och Windows Desktop.</span><span class="sxs-lookup"><span data-stu-id="330ad-107">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="330ad-108">**Core-utgåva:** Bygger på .NET Core och ger kompatibilitet med skript och moduler som mål versioner av PowerShell som körs på begränsade versioner av Windows, till exempel Nano Server och Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="330ad-108">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a><span data-ttu-id="330ad-109">Med PowerShell-galleriet kan du filtrera paket som är kompatibla med vissa PowerShell-versioner</span><span class="sxs-lookup"><span data-stu-id="330ad-109">PowerShell Gallery allows you to filter packages compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="330ad-110">Om ett paket har kompatibla PSEditions anges de som en del av "PowerShell-versioner" på paketets visnings sida och även i paket resultat.</span><span class="sxs-lookup"><span data-stu-id="330ad-110">If a package has compatible PSEditions specified, they are listed as part of 'PowerShell Editions' in the package display page and also in packages results.</span></span>
<span data-ttu-id="330ad-111">Du kan också söka efter kompatibla paket med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="330ad-111">You can also search for compatible packages using PowerShell.</span></span>

![Objekt visnings sidan med PSEditions](../../Images/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a><span data-ttu-id="330ad-113">Sök efter paket i galleriet för galleriet som fungerar på PowerShell-kärnan</span><span class="sxs-lookup"><span data-stu-id="330ad-113">Search for packages in the gallery UI that work on PowerShell Core</span></span>

<span data-ttu-id="330ad-114">Använd Taggar: "PSEdition_Desktop" och Taggar: "PSEdition_Core" för att filtrera paketen på PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="330ad-114">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the packages on PowerShell Gallery.</span></span>

### <a name="use-tagspsedition_core-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="330ad-115">Använd Taggar: "PSEdition_Core" om du vill söka efter objekt som är kompatibla med PowerShell Core Edition.</span><span class="sxs-lookup"><span data-stu-id="330ad-115">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>

![Sök Resultat för objekt som är kompatibla med Core-PSEdition](../../Images/searchresultswithpseditions.PNG)

### <a name="use-tagspsedition_desktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="330ad-117">Använd Taggar: "PSEdition_Desktop" om du vill söka efter objekt som är kompatibla med PowerShell Desktop Edition.</span><span class="sxs-lookup"><span data-stu-id="330ad-117">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>

![Sök Resultat för objekt som är kompatibla med Desktop-PSEdition](../../Images/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a><span data-ttu-id="330ad-119">Sök efter paket för att hitta kompatibla utgåvor med PowerShell</span><span class="sxs-lookup"><span data-stu-id="330ad-119">Search for packages to find compatible editions using PowerShell</span></span>
<span data-ttu-id="330ad-120">Du kan ange taggar för att filtrera PowerShell-versionen och operativ systemet.</span><span class="sxs-lookup"><span data-stu-id="330ad-120">You can specify tags to filter for the PowerShell edition and OS.</span></span>
<span data-ttu-id="330ad-121">Du använder `Find-Package` cmdleten som `-Tag` anger parametern för att ange den utgåva (och OS) som du är mål för.</span><span class="sxs-lookup"><span data-stu-id="330ad-121">You use the `Find-Package` cmdlet specifying the `-Tag` parameter to specify the edition (and OS) you are targeting.</span></span>
<span data-ttu-id="330ad-122">Gillar det här:</span><span class="sxs-lookup"><span data-stu-id="330ad-122">Like this:</span></span>

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a><span data-ttu-id="330ad-123">Söker efter operativ system</span><span class="sxs-lookup"><span data-stu-id="330ad-123">Searching by Operating System</span></span>

<span data-ttu-id="330ad-124">Eftersom PowerShell Core är tillgängligt för Windows, Linux och MacOS, kan paket i galleriet utformas för alla kombinationer av dessa operativ system.</span><span class="sxs-lookup"><span data-stu-id="330ad-124">Since PowerShell Core is available for Windows, Linux, and MacOS, packages in the Gallery may be designed for any combination of these operating systems.</span></span> <span data-ttu-id="330ad-125">I galleriet Galleri använder du följande söktaggar för att hitta paket märkta med operativ system:</span><span class="sxs-lookup"><span data-stu-id="330ad-125">In the gallery UI use the following searchs tags to find packages tagged by operating system:</span></span>

- <span data-ttu-id="330ad-126">Taggen Aktivitets</span><span class="sxs-lookup"><span data-stu-id="330ad-126">Tags: "Windows"</span></span>
- <span data-ttu-id="330ad-127">Taggen Linux</span><span class="sxs-lookup"><span data-stu-id="330ad-127">Tags: "Linux"</span></span>
- <span data-ttu-id="330ad-128">Taggen MacOS</span><span class="sxs-lookup"><span data-stu-id="330ad-128">Tags: "MacOS"</span></span>

<span data-ttu-id="330ad-129">Du kan ange taggarna på `Find-Module` (och andra cmdletar i PowerShellGet-modulen), så här:</span><span class="sxs-lookup"><span data-stu-id="330ad-129">You can specify these tags on `Find-Module` (and other cmdlets in the PowerShellGet module), like this:</span></span>

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a><span data-ttu-id="330ad-130">Söker efter flera kompatibiliteter</span><span class="sxs-lookup"><span data-stu-id="330ad-130">Searching for Multiple Compatibilities</span></span>

<span data-ttu-id="330ad-131">Du kan söka efter ett paket som har flera-kompatibilitet med hjälp av syntaxen:</span><span class="sxs-lookup"><span data-stu-id="330ad-131">You can look for a package that has multiple compatibilities by using the syntax:</span></span>

<span data-ttu-id="330ad-132">Taggen "Compatibility1" "Compatibility2"</span><span class="sxs-lookup"><span data-stu-id="330ad-132">Tags: "Compatibility1" "Compatibility2"</span></span>

<span data-ttu-id="330ad-133">Om du till exempel söker efter ett paket med PowerShell-kompatibilitet som körs på både mina Windows-och Linux-datorer använder du Sök taggarna:</span><span class="sxs-lookup"><span data-stu-id="330ad-133">For example, if you are looking for a package with PowerShell Core Compatibility that runs on both my Windows and Linux machines, use the search tags:</span></span>

<span data-ttu-id="330ad-134">Taggen "PSEdition_Core" "Windows" "Linux"</span><span class="sxs-lookup"><span data-stu-id="330ad-134">Tags: "PSEdition_Core" "Windows" "Linux"</span></span>

<span data-ttu-id="330ad-135">Om du vill söka med PowerShell kan du använda `Find-Module` (och de andra cmdletarna i PowerShellGet-modulen), så här:</span><span class="sxs-lookup"><span data-stu-id="330ad-135">To search using PowerShell, you can use the `Find-Module` (and the other cmdlets in the PowerShellGet module), like this:</span></span>

```powershell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a><span data-ttu-id="330ad-136">Mer information om hur du redigerar och söker efter paket med kompatibla PowerShell-versioner</span><span class="sxs-lookup"><span data-stu-id="330ad-136">More details on authoring and finding the packages with compatible PowerShell Editions</span></span>

- [<span data-ttu-id="330ad-137">Moduler med PSEditions</span><span class="sxs-lookup"><span data-stu-id="330ad-137">Modules with PSEditions</span></span>](../../concepts/module-psedition-support.md)
- [<span data-ttu-id="330ad-138">Skript med PSEditions</span><span class="sxs-lookup"><span data-stu-id="330ad-138">Scripts with PSEditions</span></span>](../../concepts/script-psedition-support.md)
