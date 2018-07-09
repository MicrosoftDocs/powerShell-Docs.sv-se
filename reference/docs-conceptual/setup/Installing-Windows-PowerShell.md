---
ms.date: 08/09/2017
keywords: PowerShell, cmdlet, hämta, installera, inställningar, windows 10, windows 8.1, windows 8.0, windows 7
title: Installera Windows PowerShell
ms.openlocfilehash: e703d3444b1d661c482b314781cf9a1cb16ef7ed
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893529"
---
# <a name="installing-windows-powershell"></a><span data-ttu-id="d5b73-103">Installera Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5b73-103">Installing Windows PowerShell</span></span>

<span data-ttu-id="d5b73-104">Windows PowerShell är installerat som standard i alla Windows, från och med Windows 7 SP1 och Windows Server 2008 R2 SP1.</span><span class="sxs-lookup"><span data-stu-id="d5b73-104">Windows PowerShell comes installed by default in every Windows, starting with Windows 7 SP1 and Windows Server 2008 R2 SP1.</span></span>

<span data-ttu-id="d5b73-105">Om du är intresserad av i PowerShell 6 och senare, måste du installera PowerShell Core i stället för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5b73-105">If you are interested in PowerShell 6 and later, you need to install PowerShell Core instead of Windows PowerShell.</span></span> <span data-ttu-id="d5b73-106">För att se [installera PowerShell Core på Windows](Installing-PowerShell-Core-on-Windows.md).</span><span class="sxs-lookup"><span data-stu-id="d5b73-106">For that, see [Installing PowerShell Core on Windows](Installing-PowerShell-Core-on-Windows.md).</span></span>

## <a name="finding-powershell-in-windows-10-81-80-and-7"></a><span data-ttu-id="d5b73-107">Att hitta PowerShell i Windows 10, 8.1, 8.0 och 7</span><span class="sxs-lookup"><span data-stu-id="d5b73-107">Finding PowerShell in Windows 10, 8.1, 8.0, and 7</span></span>

<span data-ttu-id="d5b73-108">Ibland hitta PowerShell kan ISE (Integrated Scripting Environment) i Windows-konsolen eller konsolen vara svårt, när dess plats flyttas från en version av Windows till nästa.</span><span class="sxs-lookup"><span data-stu-id="d5b73-108">Sometimes locating PowerShell console or ISE (Integrated Scripting Environment) in Windows can be difficult, as it's location moves from one version of Windows to the next.</span></span>

<span data-ttu-id="d5b73-109">I tabellerna nedan hjälper dig att hitta PowerShell i din Windows-version.</span><span class="sxs-lookup"><span data-stu-id="d5b73-109">The following tables should help you find PowerShell in your Windows version.</span></span>
<span data-ttu-id="d5b73-110">Alla versioner som anges här är den ursprungliga versionen som lanseras med inga uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="d5b73-110">All versions listed here are the original version, as released, with no updates.</span></span>

### <a name="for-console"></a><span data-ttu-id="d5b73-111">För konsolen</span><span class="sxs-lookup"><span data-stu-id="d5b73-111">For Console</span></span>

<span data-ttu-id="d5b73-112">Version</span><span class="sxs-lookup"><span data-stu-id="d5b73-112">Version</span></span> | <span data-ttu-id="d5b73-113">Position</span><span class="sxs-lookup"><span data-stu-id="d5b73-113">Location</span></span>
-- | --
<span data-ttu-id="d5b73-114">Windows 10</span><span class="sxs-lookup"><span data-stu-id="d5b73-114">Windows 10</span></span> | <span data-ttu-id="d5b73-115">Klicka på nedre hörnet Windows ikonen till vänster, börja skriva PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5b73-115">Click left lower corner Windows icon, start typing PowerShell</span></span>
<span data-ttu-id="d5b73-116">Windows 8.1, 8.0</span><span class="sxs-lookup"><span data-stu-id="d5b73-116">Windows 8.1, 8.0</span></span> | <span data-ttu-id="d5b73-117">Börja skriva PowerShell på start-skärmen.</span><span class="sxs-lookup"><span data-stu-id="d5b73-117">On the start screen, start typing PowerShell.</span></span><br/><span data-ttu-id="d5b73-118">Om du är på skrivbordet klickar du på lägre hörnet Windows ikonen till vänster, börja skriva PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5b73-118">If on desktop, click left lower corner Windows icon, start typing PowerShell</span></span>
<span data-ttu-id="d5b73-119">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="d5b73-119">Windows 7 SP1</span></span> | <span data-ttu-id="d5b73-120">Klicka på nedre hörnet Windows ikonen till vänster, på att skriva PowerShell search box början</span><span class="sxs-lookup"><span data-stu-id="d5b73-120">Click left lower corner Windows icon, on the search box start typing PowerShell</span></span>

### <a name="for-ise"></a><span data-ttu-id="d5b73-121">För ISE</span><span class="sxs-lookup"><span data-stu-id="d5b73-121">For ISE</span></span>

<span data-ttu-id="d5b73-122">Version</span><span class="sxs-lookup"><span data-stu-id="d5b73-122">Version</span></span> | <span data-ttu-id="d5b73-123">Position</span><span class="sxs-lookup"><span data-stu-id="d5b73-123">Location</span></span>
-- | --
<span data-ttu-id="d5b73-124">Windows 10</span><span class="sxs-lookup"><span data-stu-id="d5b73-124">Windows 10</span></span> | <span data-ttu-id="d5b73-125">Klicka på nedre hörnet Windows ikonen till vänster, börja skriva ISE</span><span class="sxs-lookup"><span data-stu-id="d5b73-125">Click left lower corner Windows icon, start typing ISE</span></span>
<span data-ttu-id="d5b73-126">Windows 8.1, 8.0</span><span class="sxs-lookup"><span data-stu-id="d5b73-126">Windows 8.1, 8.0</span></span> | <span data-ttu-id="d5b73-127">Skriv på startskärmen **PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="d5b73-127">On the start screen, type **PowerShell ISE**.</span></span><br/><span data-ttu-id="d5b73-128">Om fältet lämnas lägre hörnikon i Windows på skrivbordet, klicka på, skriver **PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="d5b73-128">If on desktop, click left lower corner Windows icon, type **PowerShell ISE**</span></span>
<span data-ttu-id="d5b73-129">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="d5b73-129">Windows 7 SP1</span></span> | <span data-ttu-id="d5b73-130">Klicka på nedre hörnet Windows ikonen till vänster, på att skriva PowerShell search box början</span><span class="sxs-lookup"><span data-stu-id="d5b73-130">Click left lower corner Windows icon, on the search box start typing PowerShell</span></span>

## <a name="finding-powershell-in-windows-server-versions"></a><span data-ttu-id="d5b73-131">Att hitta PowerShell i Windows Server-versioner</span><span class="sxs-lookup"><span data-stu-id="d5b73-131">Finding PowerShell in Windows Server versions</span></span>

<span data-ttu-id="d5b73-132">Från och med Windows Server 2008 R2, installeras Windows-operativsystem utan det grafiska användargränssnittet (GUI).</span><span class="sxs-lookup"><span data-stu-id="d5b73-132">Starting with Windows Server 2008 R2, Windows operating system can be installed without the graphical user interface (GUI).</span></span>
<span data-ttu-id="d5b73-133">Versioner av Windows Server utan GUI namnges **Core** versioner och utgåvor med det grafiska Användargränssnittet är namngivna **Desktop**.</span><span class="sxs-lookup"><span data-stu-id="d5b73-133">Editions of Windows Server without GUI are named **Core** editions, and editions with the GUI are named **Desktop**.</span></span>

### <a name="windows-server-core-editions"></a><span data-ttu-id="d5b73-134">Windows Server Core-utgåvor</span><span class="sxs-lookup"><span data-stu-id="d5b73-134">Windows Server Core editions</span></span>

<span data-ttu-id="d5b73-135">I alla Core-utgåvor när du loggar in på servern får du du ett kommandotolksfönster i Windows.</span><span class="sxs-lookup"><span data-stu-id="d5b73-135">In all Core editions, when you log to the server you get a Windows command prompt window.</span></span>

<span data-ttu-id="d5b73-136">Typ `powershell` och tryck på **RETUR** starta PowerShell i kommandotolk-session.</span><span class="sxs-lookup"><span data-stu-id="d5b73-136">Type `powershell` and press **ENTER** to start PowerShell inside the command prompt session.</span></span>
<span data-ttu-id="d5b73-137">Typ `exit` att avsluta PowerShell-sessionen och återgår till Kommandotolken.</span><span class="sxs-lookup"><span data-stu-id="d5b73-137">Type `exit` to terminate the PowerShell session and return to command prompt.</span></span>

### <a name="windows-server-desktop-editions"></a><span data-ttu-id="d5b73-138">Windows Server-Desktop-versioner</span><span class="sxs-lookup"><span data-stu-id="d5b73-138">Windows Server Desktop editions</span></span>

<span data-ttu-id="d5b73-139">I alla utgåvor av skrivbord, klickar du på den vänstra lägre Windows hörnikon, börja skriva PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5b73-139">In all desktop editions, click the left lower corner Windows icon, start typing PowerShell.</span></span>
<span data-ttu-id="d5b73-140">Du får alternativ för både konsolen och ISE.</span><span class="sxs-lookup"><span data-stu-id="d5b73-140">You get both console and ISE options.</span></span>

<span data-ttu-id="d5b73-141">Det enda undantaget till ovanstående är ISE i Windows Server 2008 R2 SP1; i det här fallet klickar du på den vänstra lägre Windows hörnikon, Skriv PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="d5b73-141">The only exception to the above rule is the ISE in Windows Server 2008 R2 SP1; in this case, click the left lower corner Windows icon, type PowerShell ISE.</span></span>

## <a name="how-to-check-the-version-of-powershell"></a><span data-ttu-id="d5b73-142">Hur du kontrollerar versionen av PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5b73-142">How to check the version of PowerShell</span></span>

<span data-ttu-id="d5b73-143">Starta en PowerShell-konsol (eller ISE) för att hitta vilken version av PowerShell som du har installerat, och skriv `$PSVersionTable` och tryck på **RETUR**.</span><span class="sxs-lookup"><span data-stu-id="d5b73-143">To find which version of PowerShell you have installed, start a PowerShell console (or the ISE) and type `$PSVersionTable` and press **ENTER**.</span></span> <span data-ttu-id="d5b73-144">Leta efter den `PSVersion` värde.</span><span class="sxs-lookup"><span data-stu-id="d5b73-144">Look for the `PSVersion` value.</span></span>

## <a name="upgrading-existing-windows-powershell"></a><span data-ttu-id="d5b73-145">Uppgradera den befintliga Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5b73-145">Upgrading existing Windows PowerShell</span></span>

<span data-ttu-id="d5b73-146">Installationspaketet för PowerShell kommer i ett installationsprogram för WMF.</span><span class="sxs-lookup"><span data-stu-id="d5b73-146">The installation package for PowerShell comes inside a WMF installer.</span></span>
<span data-ttu-id="d5b73-147">Versionen av WMF installationsprogrammet matchar versionen av PowerShell; Det finns inget fristående installationsprogram för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5b73-147">The version of the WMF installer matches the version of PowerShell; there's no stand alone installer for Windows PowerShell.</span></span>

<span data-ttu-id="d5b73-148">Om du vill uppdatera den befintliga versionen av PowerShell i Windows, Använd följande tabell för att hitta installationsprogrammet för den versionen av PowerShell som du vill uppdatera till.</span><span class="sxs-lookup"><span data-stu-id="d5b73-148">If you need to update your existing version of PowerShell, in Windows, use the following table to locate the installer for the version of PowerShell you want to update to.</span></span>

<span data-ttu-id="d5b73-149">Windows</span><span class="sxs-lookup"><span data-stu-id="d5b73-149">Windows</span></span> | <span data-ttu-id="d5b73-150">PS 3.0</span><span class="sxs-lookup"><span data-stu-id="d5b73-150">PS 3.0</span></span> | <span data-ttu-id="d5b73-151">PS 4.0</span><span class="sxs-lookup"><span data-stu-id="d5b73-151">PS 4.0</span></span> | <span data-ttu-id="d5b73-152">PS 5.0</span><span class="sxs-lookup"><span data-stu-id="d5b73-152">PS 5.0</span></span> | <span data-ttu-id="d5b73-153">PS 5.1</span><span class="sxs-lookup"><span data-stu-id="d5b73-153">PS 5.1</span></span> |
--|--|--|--|--|
<span data-ttu-id="d5b73-154">Windows 10 (se Note1)</span><span class="sxs-lookup"><span data-stu-id="d5b73-154">Windows 10 (see Note1)</span></span><br/><span data-ttu-id="d5b73-155">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="d5b73-155">Windows Server 2016</span></span> | - | - | - | <span data-ttu-id="d5b73-156">installerad</span><span class="sxs-lookup"><span data-stu-id="d5b73-156">installed</span></span>
<span data-ttu-id="d5b73-157">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="d5b73-157">Windows 8.1</span></span><br/><span data-ttu-id="d5b73-158">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="d5b73-158">Windows Server 2012 R2</span></span> | - | <span data-ttu-id="d5b73-159">installerad</span><span class="sxs-lookup"><span data-stu-id="d5b73-159">installed</span></span> | [<span data-ttu-id="d5b73-160">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="d5b73-160">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="d5b73-161">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="d5b73-161">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
<span data-ttu-id="d5b73-162">Windows 8</span><span class="sxs-lookup"><span data-stu-id="d5b73-162">Windows 8</span></span><br/><span data-ttu-id="d5b73-163">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="d5b73-163">Windows Server 2012</span></span> | <span data-ttu-id="d5b73-164">installerad</span><span class="sxs-lookup"><span data-stu-id="d5b73-164">installed</span></span> | [<span data-ttu-id="d5b73-165">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="d5b73-165">WMF 4.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [<span data-ttu-id="d5b73-166">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="d5b73-166">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="d5b73-167">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="d5b73-167">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
<span data-ttu-id="d5b73-168">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="d5b73-168">Windows 7 SP1</span></span><br/><span data-ttu-id="d5b73-169">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="d5b73-169">Windows Server 2008 R2 SP1</span></span> | [<span data-ttu-id="d5b73-170">WMF 3.0</span><span class="sxs-lookup"><span data-stu-id="d5b73-170">WMF 3.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=34595) | [<span data-ttu-id="d5b73-171">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="d5b73-171">WMF 4.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [<span data-ttu-id="d5b73-172">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="d5b73-172">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="d5b73-173">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="d5b73-173">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)

> [!NOTE]
>
> <span data-ttu-id="d5b73-174">På den första versionen av Windows 10, med automatiska uppdateringar aktiverad, uppdateras PowerShell från version 5.0 5.1.</span><span class="sxs-lookup"><span data-stu-id="d5b73-174">On the initial release of Windows 10, with automatic updates enabled, PowerShell gets updated from version 5.0 to 5.1.</span></span>
>
> <span data-ttu-id="d5b73-175">Om den ursprungliga versionen av Windows 10 inte uppdateras via Windows-uppdateringar, är versionen av PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="d5b73-175">If the original version of Windows 10 is not updated through Windows Updates, the version of PowerShell is 5.0.</span></span>

## <a name="need-azure-powershell"></a><span data-ttu-id="d5b73-176">Behöver ha Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5b73-176">Need Azure PowerShell</span></span>

<span data-ttu-id="d5b73-177">Om du letar efter **Azure PowerShell**, du kan börja med [översikt av Azure PowerShell](/powershell/azure/overview).</span><span class="sxs-lookup"><span data-stu-id="d5b73-177">If you're looking for **Azure PowerShell**, you could start with [Overview of Azure PowerShell](/powershell/azure/overview).</span></span>

<span data-ttu-id="d5b73-178">I annat fall kanske du behöver är [installera och konfigurera Azure PowerShell](/powershell/azure/install-azurerm-ps)</span><span class="sxs-lookup"><span data-stu-id="d5b73-178">Otherwise, what you might need is [Install and configure Azure PowerShell](/powershell/azure/install-azurerm-ps)</span></span>

## <a name="see-also"></a><span data-ttu-id="d5b73-179">Se även</span><span class="sxs-lookup"><span data-stu-id="d5b73-179">See Also</span></span>

[<span data-ttu-id="d5b73-180">Windows PowerShell-systemkrav</span><span class="sxs-lookup"><span data-stu-id="d5b73-180">Windows PowerShell System Requirements</span></span>](Windows-PowerShell-System-Requirements.md)

[<span data-ttu-id="d5b73-181">Starta Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5b73-181">Starting Windows PowerShell</span></span>](Starting-Windows-PowerShell.md)