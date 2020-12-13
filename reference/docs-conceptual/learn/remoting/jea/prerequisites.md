---
ms.date: 07/10/2019
keywords: Jea, PowerShell, säkerhet
title: JEA-krav
description: I den här artikeln beskrivs förutsättningar som måste vara uppfyllda för att börja använda JEA.
ms.openlocfilehash: 5cc70a06887a2d0a840cc83117f865d3148056e1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92501736"
---
# <a name="prerequisites"></a><span data-ttu-id="fcd56-104">Förutsättningar</span><span class="sxs-lookup"><span data-stu-id="fcd56-104">Prerequisites</span></span>

<span data-ttu-id="fcd56-105">Bara tillräckligt med administration är en funktion som ingår i PowerShell 5,0 och högre.</span><span class="sxs-lookup"><span data-stu-id="fcd56-105">Just Enough Administration is a feature included in PowerShell 5.0 and higher.</span></span> <span data-ttu-id="fcd56-106">I den här artikeln beskrivs förutsättningar som måste vara uppfyllda för att börja använda JEA.</span><span class="sxs-lookup"><span data-stu-id="fcd56-106">This article describes the prerequisites that must be satisfied to start using JEA.</span></span>

## <a name="check-which-version-of-powershell-is-installed"></a><span data-ttu-id="fcd56-107">Kontrol lera vilken version av PowerShell som är installerad</span><span class="sxs-lookup"><span data-stu-id="fcd56-107">Check which version of PowerShell is installed</span></span>

<span data-ttu-id="fcd56-108">Om du vill kontrol lera vilken version av PowerShell som är installerad i systemet kontrollerar du `$PSVersionTable` variabeln i en Windows PowerShell-prompt.</span><span class="sxs-lookup"><span data-stu-id="fcd56-108">To check which version of PowerShell is installed on your system, check the `$PSVersionTable` variable in a Windows PowerShell prompt.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

<span data-ttu-id="fcd56-109">JEA är tillgängligt med PowerShell 5,0 och högre.</span><span class="sxs-lookup"><span data-stu-id="fcd56-109">JEA is available with PowerShell 5.0 and higher.</span></span> <span data-ttu-id="fcd56-110">För alla funktioner rekommenderar vi att du installerar den senaste versionen av PowerShell som är tillgänglig för ditt system.</span><span class="sxs-lookup"><span data-stu-id="fcd56-110">For full functionality, it's recommended that you install the latest version of PowerShell available for your system.</span></span> <span data-ttu-id="fcd56-111">I följande tabell beskrivs JEA tillgänglighet för Windows Server:</span><span class="sxs-lookup"><span data-stu-id="fcd56-111">The following table describes JEA's availability on Windows Server:</span></span>

| <span data-ttu-id="fcd56-112">Serveroperativsystem</span><span class="sxs-lookup"><span data-stu-id="fcd56-112">Server Operating System</span></span> |                <span data-ttu-id="fcd56-113">JEA tillgänglighet</span><span class="sxs-lookup"><span data-stu-id="fcd56-113">JEA Availability</span></span>                |
| ----------------------- | ---------------------------------------------- |
| <span data-ttu-id="fcd56-114">Windows Server 2016 +</span><span class="sxs-lookup"><span data-stu-id="fcd56-114">Windows Server 2016+</span></span>    | <span data-ttu-id="fcd56-115">Förinstallerad</span><span class="sxs-lookup"><span data-stu-id="fcd56-115">Preinstalled</span></span>                                   |
| <span data-ttu-id="fcd56-116">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="fcd56-116">Windows Server 2012 R2</span></span>  | <span data-ttu-id="fcd56-117">Fullständiga funktioner med WMF 5,1</span><span class="sxs-lookup"><span data-stu-id="fcd56-117">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="fcd56-118">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="fcd56-118">Windows Server 2012</span></span>     | <span data-ttu-id="fcd56-119">Fullständiga funktioner med WMF 5,1</span><span class="sxs-lookup"><span data-stu-id="fcd56-119">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="fcd56-120">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="fcd56-120">Windows Server 2008 R2</span></span>  | <span data-ttu-id="fcd56-121">Begränsad funktionalitet<sup>1</sup> med WMF 5,1</span><span class="sxs-lookup"><span data-stu-id="fcd56-121">Reduced functionality<sup>1</sup> with WMF 5.1</span></span> |

<span data-ttu-id="fcd56-122">Du kan också använda JEA på din hem-eller arbets dator:</span><span class="sxs-lookup"><span data-stu-id="fcd56-122">You can also use JEA on your home or work computer:</span></span>

| <span data-ttu-id="fcd56-123">Klientoperativsystem:</span><span class="sxs-lookup"><span data-stu-id="fcd56-123">Client Operating System</span></span> |                   <span data-ttu-id="fcd56-124">JEA tillgänglighet</span><span class="sxs-lookup"><span data-stu-id="fcd56-124">JEA Availability</span></span>                   |
| ----------------------- | ---------------------------------------------------- |
| <span data-ttu-id="fcd56-125">Windows 10 1607 +</span><span class="sxs-lookup"><span data-stu-id="fcd56-125">Windows 10 1607+</span></span>        | <span data-ttu-id="fcd56-126">Förinstallerad</span><span class="sxs-lookup"><span data-stu-id="fcd56-126">Preinstalled</span></span>                                         |
| <span data-ttu-id="fcd56-127">Windows 10 1603, 1511</span><span class="sxs-lookup"><span data-stu-id="fcd56-127">Windows 10 1603, 1511</span></span>   | <span data-ttu-id="fcd56-128">Förinstallerad med begränsad funktionalitet<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="fcd56-128">Preinstalled, with reduced functionality<sup>2</sup></span></span> |
| <span data-ttu-id="fcd56-129">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="fcd56-129">Windows 10 1507</span></span>         | <span data-ttu-id="fcd56-130">Inte tillgängligt</span><span class="sxs-lookup"><span data-stu-id="fcd56-130">Not available</span></span>                                        |
| <span data-ttu-id="fcd56-131">Windows 8, 8,1</span><span class="sxs-lookup"><span data-stu-id="fcd56-131">Windows 8, 8.1</span></span>          | <span data-ttu-id="fcd56-132">Fullständiga funktioner med WMF 5,1</span><span class="sxs-lookup"><span data-stu-id="fcd56-132">Full functionality with WMF 5.1</span></span>                      |
| <span data-ttu-id="fcd56-133">Windows 7</span><span class="sxs-lookup"><span data-stu-id="fcd56-133">Windows 7</span></span>               | <span data-ttu-id="fcd56-134">Begränsad funktionalitet<sup>1</sup> med WMF 5,1</span><span class="sxs-lookup"><span data-stu-id="fcd56-134">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>       |

- <span data-ttu-id="fcd56-135"><sup>1</sup> Jea kan inte konfigureras för användning av grupphanterade tjänst konton i Windows Server 2008 R2 eller Windows 7.</span><span class="sxs-lookup"><span data-stu-id="fcd56-135"><sup>1</sup> JEA can't be configured to use group-managed service accounts on Windows Server 2008 R2 or Windows 7.</span></span> <span data-ttu-id="fcd56-136">Virtuella konton och andra JEA- *funktioner stöds* .</span><span class="sxs-lookup"><span data-stu-id="fcd56-136">Virtual accounts and other JEA features *are* supported.</span></span>

- <span data-ttu-id="fcd56-137"><sup>2</sup> följande Jea-funktioner stöds inte i Windows 10-versionerna 1511 och 1603:</span><span class="sxs-lookup"><span data-stu-id="fcd56-137"><sup>2</sup> The following JEA features aren't supported on Windows 10 versions 1511 and 1603:</span></span>

  - <span data-ttu-id="fcd56-138">Köra som ett grupphanterat tjänst konto</span><span class="sxs-lookup"><span data-stu-id="fcd56-138">Running as a group-managed service account</span></span>
  - <span data-ttu-id="fcd56-139">Regler för villkorlig åtkomst i konfigurationer för sessioner</span><span class="sxs-lookup"><span data-stu-id="fcd56-139">Conditional access rules in session configurations</span></span>
  - <span data-ttu-id="fcd56-140">Användar enheten</span><span class="sxs-lookup"><span data-stu-id="fcd56-140">The user drive</span></span>
  - <span data-ttu-id="fcd56-141">Bevilja åtkomst till lokala användar konton</span><span class="sxs-lookup"><span data-stu-id="fcd56-141">Granting access to local user accounts</span></span>

  <span data-ttu-id="fcd56-142">Om du vill ha stöd för dessa funktioner uppdaterar du Windows till version 1607 (uppdaterings uppdatering) eller högre.</span><span class="sxs-lookup"><span data-stu-id="fcd56-142">To get support for these features, update Windows to version 1607 (Anniversary Update) or higher.</span></span>

### <a name="install-windows-management-framework"></a><span data-ttu-id="fcd56-143">Installera Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="fcd56-143">Install Windows Management Framework</span></span>

<span data-ttu-id="fcd56-144">Om du kör en äldre version av PowerShell kan du behöva uppdatera systemet med den senaste WMF-uppdateringen (Windows Management Framework).</span><span class="sxs-lookup"><span data-stu-id="fcd56-144">If you're running an older version of PowerShell, you may need to update your system with the latest Windows Management Framework (WMF) update.</span></span> <span data-ttu-id="fcd56-145">Mer information finns i WMF- [dokumentationen](/powershell/scripting/wmf/overview).</span><span class="sxs-lookup"><span data-stu-id="fcd56-145">For more information, see the [WMF documentation](/powershell/scripting/wmf/overview).</span></span>

<span data-ttu-id="fcd56-146">Vi rekommenderar att du testar din arbets belastnings kompatibilitet med WMF innan du uppgraderar alla dina servrar.</span><span class="sxs-lookup"><span data-stu-id="fcd56-146">It's recommended that you test your workload's compatibility with WMF before upgrading all of your servers.</span></span>

<span data-ttu-id="fcd56-147">Windows 10-användare bör installera de senaste funktions uppdateringarna för att hämta den aktuella versionen av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fcd56-147">Windows 10 users should install the latest feature updates to obtain the current version of Windows PowerShell.</span></span>

## <a name="enable-powershell-remoting"></a><span data-ttu-id="fcd56-148">Aktivera PowerShell-fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="fcd56-148">Enable PowerShell Remoting</span></span>

<span data-ttu-id="fcd56-149">PowerShell-fjärrkommunikation tillhandahåller den grund som JEA bygger på.</span><span class="sxs-lookup"><span data-stu-id="fcd56-149">PowerShell Remoting provides the foundation on which JEA is built.</span></span> <span data-ttu-id="fcd56-150">Det är nödvändigt att se till att PowerShell-fjärrkommunikation är aktiverat och ordentligt säkert innan du kan använda JEA.</span><span class="sxs-lookup"><span data-stu-id="fcd56-150">It's necessary to ensure PowerShell Remoting is enabled and properly secured before you can use JEA.</span></span> <span data-ttu-id="fcd56-151">Mer information finns i [WinRM Security](/powershell/scripting/learn/remoting/winrmsecurity).</span><span class="sxs-lookup"><span data-stu-id="fcd56-151">For more information, see [WinRM Security](/powershell/scripting/learn/remoting/winrmsecurity).</span></span>

<span data-ttu-id="fcd56-152">PowerShell-fjärrkommunikation är aktiverat som standard på Windows Server 2012, 2012 R2 och 2016.</span><span class="sxs-lookup"><span data-stu-id="fcd56-152">PowerShell Remoting is enabled by default on Windows Server 2012, 2012 R2, and 2016.</span></span> <span data-ttu-id="fcd56-153">Du kan aktivera PowerShell-fjärrkommunikation genom att köra följande kommando i ett upphöjd PowerShell-fönster.</span><span class="sxs-lookup"><span data-stu-id="fcd56-153">You can enable PowerShell Remoting by running the following command in an elevated PowerShell window.</span></span>

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a><span data-ttu-id="fcd56-154">Aktivera PowerShell-modul och skript Blocks loggning (valfritt)</span><span class="sxs-lookup"><span data-stu-id="fcd56-154">Enable PowerShell module and script block logging (optional)</span></span>

<span data-ttu-id="fcd56-155">Följande steg aktiverar loggning för alla PowerShell-åtgärder i systemet.</span><span class="sxs-lookup"><span data-stu-id="fcd56-155">The following steps enable logging for all PowerShell actions on your system.</span></span> <span data-ttu-id="fcd56-156">Loggning av PowerShell-modul krävs inte för JEA, men vi rekommenderar att du aktiverar loggning för att se till att de kommandon som användare kör loggas på en central plats.</span><span class="sxs-lookup"><span data-stu-id="fcd56-156">PowerShell Module Logging isn't required for JEA, however it's recommended you turn on logging to ensure the commands users run are logged in a central location.</span></span>

<span data-ttu-id="fcd56-157">Du kan konfigurera PowerShell-modulens loggnings princip med grupprincip.</span><span class="sxs-lookup"><span data-stu-id="fcd56-157">You can configure the PowerShell Module Logging policy using Group Policy.</span></span>

1. <span data-ttu-id="fcd56-158">Öppna redigerare för lokalt grupprincipobjekt på en arbets Station eller ett grupprincip objekt i konsolen grupprinciphantering på en Active Directory-domän kontrollant</span><span class="sxs-lookup"><span data-stu-id="fcd56-158">Open the Local Group Policy Editor on a workstation or a Group Policy Object in the Group Policy Management Console on an Active Directory Domain Controller</span></span>
2. <span data-ttu-id="fcd56-159">Navigera till **dator konfiguration \\ administrativa mallar \\ Windows- \\ komponenter Windows PowerShell**</span><span class="sxs-lookup"><span data-stu-id="fcd56-159">Navigate to **Computer Configuration\\Administrative Templates\\Windows Components\\Windows PowerShell**</span></span>
3. <span data-ttu-id="fcd56-160">Dubbelklicka på **Aktivera modul loggning**</span><span class="sxs-lookup"><span data-stu-id="fcd56-160">Double-click on **Turn on Module Logging**</span></span>
4. <span data-ttu-id="fcd56-161">Klicka på **aktive rad**</span><span class="sxs-lookup"><span data-stu-id="fcd56-161">Click **Enabled**</span></span>
5. <span data-ttu-id="fcd56-162">I avsnittet alternativ klickar du på **Visa** bredvid Modulnamn</span><span class="sxs-lookup"><span data-stu-id="fcd56-162">In the Options section, click on **Show** next to Module Names</span></span>
6. <span data-ttu-id="fcd56-163">Skriv `*` i popup-fönstret för att logga kommandon från alla moduler.</span><span class="sxs-lookup"><span data-stu-id="fcd56-163">Type `*` in the pop-up window to log commands from all modules.</span></span>
7. <span data-ttu-id="fcd56-164">Klicka på **OK** för att ange principen</span><span class="sxs-lookup"><span data-stu-id="fcd56-164">Click **OK** to set the policy</span></span>
8. <span data-ttu-id="fcd56-165">Dubbelklicka på **Aktivera loggning av PowerShell-skriptkommando**</span><span class="sxs-lookup"><span data-stu-id="fcd56-165">Double-click on **Turn on PowerShell Script Block Logging**</span></span>
9. <span data-ttu-id="fcd56-166">Klicka på **aktive rad**</span><span class="sxs-lookup"><span data-stu-id="fcd56-166">Click **Enabled**</span></span>
10. <span data-ttu-id="fcd56-167">Klicka på **OK** för att ange principen</span><span class="sxs-lookup"><span data-stu-id="fcd56-167">Click **OK** to set the policy</span></span>
11. <span data-ttu-id="fcd56-168">(Endast på domänanslutna datorer) Kör `gpupdate` eller vänta tills Grupprincip att bearbeta den uppdaterade principen och tillämpa inställningarna</span><span class="sxs-lookup"><span data-stu-id="fcd56-168">(On domain-joined machines only) Run `gpupdate` or wait for Group Policy to process the updated policy and apply the settings</span></span>

<span data-ttu-id="fcd56-169">Du kan också aktivera PowerShell-avskrifter i hela systemet genom grupprincip.</span><span class="sxs-lookup"><span data-stu-id="fcd56-169">You can also enable system-wide PowerShell transcription through Group Policy.</span></span>

## <a name="next-steps"></a><span data-ttu-id="fcd56-170">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="fcd56-170">Next steps</span></span>

[<span data-ttu-id="fcd56-171">Skapa en roll funktions fil</span><span class="sxs-lookup"><span data-stu-id="fcd56-171">Create a role capability file</span></span>](role-capabilities.md)

[<span data-ttu-id="fcd56-172">Skapa en konfigurations fil för sessionen</span><span class="sxs-lookup"><span data-stu-id="fcd56-172">Create a session configuration file</span></span>](session-configurations.md)

## <a name="see-also"></a><span data-ttu-id="fcd56-173">Se även</span><span class="sxs-lookup"><span data-stu-id="fcd56-173">See also</span></span>

[<span data-ttu-id="fcd56-174">WinRM-säkerhet</span><span class="sxs-lookup"><span data-stu-id="fcd56-174">WinRM Security</span></span>](/powershell/scripting/learn/remoting/winrmsecurity)

[<span data-ttu-id="fcd56-175">PowerShell ♥ det blå teamet</span><span class="sxs-lookup"><span data-stu-id="fcd56-175">PowerShell ♥ the Blue Team</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
