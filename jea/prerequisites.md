---
ms.date: 06/12/2017
keywords: jea, powershell, säkerhet
title: JEA-krav
ms.openlocfilehash: acc16c0c7eec357b621c0706a66b8752ae5578cd
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893043"
---
# <a name="prerequisites"></a><span data-ttu-id="cf84c-103">Förutsättningar</span><span class="sxs-lookup"><span data-stu-id="cf84c-103">Prerequisites</span></span>

> <span data-ttu-id="cf84c-104">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="cf84c-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="cf84c-105">Just Enough Administration är en funktion som ingår i Windows PowerShell 5.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="cf84c-105">Just Enough Administration is a feature included with Windows PowerShell 5.0 and higher.</span></span>
<span data-ttu-id="cf84c-106">Det här avsnittet beskrivs de krav som måste uppfyllas för att kunna börja använda JEA.</span><span class="sxs-lookup"><span data-stu-id="cf84c-106">This topic describes the prerequisites that must be satisfied in order to start using JEA.</span></span>

## <a name="install-jea"></a><span data-ttu-id="cf84c-107">Installera JEA</span><span class="sxs-lookup"><span data-stu-id="cf84c-107">Install JEA</span></span>

<span data-ttu-id="cf84c-108">JEA är tillgängliga med Windows PowerShell 5.0 och senare, men för alla funktioner rekommenderas att du installerar den senaste versionen av PowerShell som är tillgängliga för ditt system.</span><span class="sxs-lookup"><span data-stu-id="cf84c-108">JEA is available with Windows PowerShell 5.0 and higher, but for full functionality it is recommended that you install the latest version of PowerShell available for your system.</span></span>
<span data-ttu-id="cf84c-109">I följande tabell beskrivs JEAS tillgänglighet på Windows Server:</span><span class="sxs-lookup"><span data-stu-id="cf84c-109">The following table describes JEA's availability on Windows Server:</span></span>

<span data-ttu-id="cf84c-110">Serveroperativsystem</span><span class="sxs-lookup"><span data-stu-id="cf84c-110">Server Operating System</span></span>   | <span data-ttu-id="cf84c-111">JEA-tillgänglighet</span><span class="sxs-lookup"><span data-stu-id="cf84c-111">JEA Availability</span></span>
--------------------------|--------------------------------
<span data-ttu-id="cf84c-112">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="cf84c-112">Windows Server 2016</span></span>       | <span data-ttu-id="cf84c-113">Förinstallerad</span><span class="sxs-lookup"><span data-stu-id="cf84c-113">Preinstalled</span></span>
<span data-ttu-id="cf84c-114">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="cf84c-114">Windows Server 2012 R2</span></span>    | <span data-ttu-id="cf84c-115">Alla funktioner i WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="cf84c-115">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="cf84c-116">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="cf84c-116">Windows Server 2012</span></span>       | <span data-ttu-id="cf84c-117">Alla funktioner i WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="cf84c-117">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="cf84c-118">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="cf84c-118">Windows Server 2008 R2</span></span>    | <span data-ttu-id="cf84c-119">Funktioner<sup>1</sup> med WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="cf84c-119">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>

<span data-ttu-id="cf84c-120">Du kan också använda JEA på datorn hem- eller arbetsnätverk:</span><span class="sxs-lookup"><span data-stu-id="cf84c-120">You can also use JEA on your home or work computer:</span></span>

<span data-ttu-id="cf84c-121">Klientoperativsystem</span><span class="sxs-lookup"><span data-stu-id="cf84c-121">Client Operating System</span></span>   | <span data-ttu-id="cf84c-122">JEA-tillgänglighet</span><span class="sxs-lookup"><span data-stu-id="cf84c-122">JEA Availability</span></span>
--------------------------|-----------------------------------------------------
<span data-ttu-id="cf84c-123">Windows 10 1607 +</span><span class="sxs-lookup"><span data-stu-id="cf84c-123">Windows 10 1607+</span></span>          | <span data-ttu-id="cf84c-124">Förinstallerad</span><span class="sxs-lookup"><span data-stu-id="cf84c-124">Preinstalled</span></span>
<span data-ttu-id="cf84c-125">Windows 10 1603 1511</span><span class="sxs-lookup"><span data-stu-id="cf84c-125">Windows 10 1603, 1511</span></span>     | <span data-ttu-id="cf84c-126">Förinstallerad, med nedsatt funktionalitet<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="cf84c-126">Preinstalled, with reduced functionality<sup>2</sup></span></span>
<span data-ttu-id="cf84c-127">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="cf84c-127">Windows 10 1507</span></span>           | <span data-ttu-id="cf84c-128">Inte tillgänglig</span><span class="sxs-lookup"><span data-stu-id="cf84c-128">Not available</span></span>
<span data-ttu-id="cf84c-129">Windows 8, 8.1</span><span class="sxs-lookup"><span data-stu-id="cf84c-129">Windows 8, 8.1</span></span>            | <span data-ttu-id="cf84c-130">Alla funktioner i WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="cf84c-130">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="cf84c-131">Windows 7</span><span class="sxs-lookup"><span data-stu-id="cf84c-131">Windows 7</span></span>                 | <span data-ttu-id="cf84c-132">Funktioner<sup>1</sup> med WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="cf84c-132">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>

<span data-ttu-id="cf84c-133"><sup>1</sup> JEA kan inte konfigureras för att använda grupphanterade tjänstkonton på Windows Server 2008 R2 eller Windows 7.</span><span class="sxs-lookup"><span data-stu-id="cf84c-133"><sup>1</sup> JEA cannot be configured to use group managed service accounts on Windows Server 2008 R2 or Windows 7.</span></span>
<span data-ttu-id="cf84c-134">Virtuella konton och andra funktioner för JEA *är* stöds.</span><span class="sxs-lookup"><span data-stu-id="cf84c-134">Virtual accounts and other JEA features *are* supported.</span></span>

<span data-ttu-id="cf84c-135"><sup>2</sup> Windows 10 version 1511 och 1603 stöder inte följande funktioner i JEA: körs som ett grupphanterat tjänstkonto, regler för villkorlig åtkomst i sessionskonfigurationer, enheten och att bevilja åtkomst till lokala användarkonton.</span><span class="sxs-lookup"><span data-stu-id="cf84c-135"><sup>2</sup> Windows 10 versions 1511 and 1603 do not support the following JEA features: running as a group managed service account, conditional access rules in session configurations, the user drive, and granting access to local user accounts.</span></span>
<span data-ttu-id="cf84c-136">För att få stöd för dessa funktioner kan du uppdatera Windows till version 1607 (Anniversary Update) eller högre.</span><span class="sxs-lookup"><span data-stu-id="cf84c-136">To get support for these features, update Windows to version 1607 (Anniversary Update) or higher.</span></span>

### <a name="check-which-version-of-powershell-is-installed"></a><span data-ttu-id="cf84c-137">Kontrollera vilken version av PowerShell är installerat</span><span class="sxs-lookup"><span data-stu-id="cf84c-137">Check which version of PowerShell is installed</span></span>

<span data-ttu-id="cf84c-138">Om du vill kontrollera vilken version av PowerShell är installerat på datorn, kontrollera den `$PSVersionTable` variabel i en Windows PowerShell-kommandotolk.</span><span class="sxs-lookup"><span data-stu-id="cf84c-138">To check which version of PowerShell is installed on your system, check the `$PSVersionTable` variable in a Windows PowerShell prompt.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

<span data-ttu-id="cf84c-139">Du är redo att använda JEA om den *större* version är lika med eller större än **5**.</span><span class="sxs-lookup"><span data-stu-id="cf84c-139">You are ready to use JEA if the *Major* version is equal to or greater than **5**.</span></span>
<span data-ttu-id="cf84c-140">För bästa möjliga upplevelse och ska ha åtkomst till alla de senaste funktionerna, rekommenderar vi att du uppgraderar till PowerShell-version **5.1** när det är möjligt.</span><span class="sxs-lookup"><span data-stu-id="cf84c-140">For the best experience, and to have access to all the latest features, it is recommended that you upgrade to PowerShell version **5.1** when possible.</span></span>

### <a name="install-windows-management-framework"></a><span data-ttu-id="cf84c-141">Installera Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="cf84c-141">Install Windows Management Framework</span></span>

<span data-ttu-id="cf84c-142">Om du kör en äldre version av PowerShell, kommer du behöva uppdatera datorn med den senaste uppdateringen av Windows Management Framework (WMF).</span><span class="sxs-lookup"><span data-stu-id="cf84c-142">If you are running an older version of PowerShell, you will need to update your system with the latest Windows Management Framework (WMF) update.</span></span>
<span data-ttu-id="cf84c-143">Uppdateringspaket och en länk till senaste WMF viktig information finns i den [Download Center](https://blogs.msdn.microsoft.com/powershell/2016/02/24/windows-management-framework-wmf-5-0-rtm-packages-has-been-republished/).</span><span class="sxs-lookup"><span data-stu-id="cf84c-143">Update packages and a link to the latest WMF release notes are available in the [Download Center](https://blogs.msdn.microsoft.com/powershell/2016/02/24/windows-management-framework-wmf-5-0-rtm-packages-has-been-republished/).</span></span>

<span data-ttu-id="cf84c-144">Vi rekommenderar starkt att du testar din arbetsbelastning kompatibilitet med WMF innan du uppgraderar alla dina servrar.</span><span class="sxs-lookup"><span data-stu-id="cf84c-144">It is strongly recommended that you test your workload's compatibility with WMF before upgrading all of your servers.</span></span>

<span data-ttu-id="cf84c-145">Windows 10-användare bör installera de senaste funktionsuppdateringarna för att hämta den aktuella versionen av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cf84c-145">Windows 10 users should install the latest feature updates to obtain the current version of Windows PowerShell.</span></span>

## <a name="enable-powershell-remoting"></a><span data-ttu-id="cf84c-146">Aktivera PowerShell-fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="cf84c-146">Enable PowerShell Remoting</span></span>

<span data-ttu-id="cf84c-147">PowerShell-fjärrkommunikation utgör grunden som JEA har skapats.</span><span class="sxs-lookup"><span data-stu-id="cf84c-147">PowerShell Remoting provides the foundation on which JEA is built.</span></span>
<span data-ttu-id="cf84c-148">Det är därför nödvändigt att säkerställa att PowerShell-fjärrkommunikation är aktiverat och [ordentligt](/powershell/scripting/setup/winrmsecurity) på datorn innan du kan använda JEA.</span><span class="sxs-lookup"><span data-stu-id="cf84c-148">It is therefore necessary to ensure PowerShell Remoting is enabled and [properly secured](/powershell/scripting/setup/winrmsecurity) on your system before you can use JEA.</span></span>

<span data-ttu-id="cf84c-149">PowerShell-fjärrkommunikation är aktiverat som standard på Windows Server 2012, 2012 R2 och 2016.</span><span class="sxs-lookup"><span data-stu-id="cf84c-149">PowerShell Remoting is enabled by default on Windows Server 2012, 2012 R2, and 2016.</span></span>
<span data-ttu-id="cf84c-150">Du kan aktivera PowerShell-fjärrkommunikation genom att köra följande kommando i ett upphöjt PowerShell-fönster.</span><span class="sxs-lookup"><span data-stu-id="cf84c-150">You can enable PowerShell Remoting by running the following command in an elevated PowerShell window.</span></span>

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a><span data-ttu-id="cf84c-151">Aktivera PowerShell-modulen och skript block loggning (valfritt)</span><span class="sxs-lookup"><span data-stu-id="cf84c-151">Enable PowerShell module and script block logging (optional)</span></span>

<span data-ttu-id="cf84c-152">Följande steg aktiverar loggning för alla PowerShell-åtgärder på datorn.</span><span class="sxs-lookup"><span data-stu-id="cf84c-152">The following steps enable logging for all PowerShell actions on your system.</span></span>
<span data-ttu-id="cf84c-153">Loggning av PowerShell-modulen krävs inte för JEA, men vi rekommenderar starkt att du aktiverar det att se till att köra kommandon användare är inloggade på en central plats.</span><span class="sxs-lookup"><span data-stu-id="cf84c-153">PowerShell Module Logging is not required for JEA, however it is strongly recommended that you turn it on to ensure the commands users run are logged in a central location.</span></span>

<span data-ttu-id="cf84c-154">Du kan konfigurera principen för loggning av PowerShell-modulen med hjälp av en Grupprincip.</span><span class="sxs-lookup"><span data-stu-id="cf84c-154">You can configure the PowerShell Module Logging policy using Group Policy.</span></span>

1. <span data-ttu-id="cf84c-155">Öppna Redigeraren för lokal princip på en arbetsstation eller ett grupprincipobjekt i Group Policy Management Console på en Active Directory-domänkontrollant</span><span class="sxs-lookup"><span data-stu-id="cf84c-155">Open the Local Group Policy Editor on a workstation or a Group Policy Object in the Group Policy Management Console on an Active Directory Domain Controller</span></span>
2. <span data-ttu-id="cf84c-156">Gå till **Datorkonfiguration\\Administrationsmallar\\Windows-komponenter\\Windows PowerShell**</span><span class="sxs-lookup"><span data-stu-id="cf84c-156">Navigate to **Computer Configuration\\Administrative Templates\\Windows Components\\Windows PowerShell**</span></span>
3. <span data-ttu-id="cf84c-157">Dubbelklicka på **aktiverar loggning av modul**</span><span class="sxs-lookup"><span data-stu-id="cf84c-157">Double click on **Turn on Module Logging**</span></span>
4. <span data-ttu-id="cf84c-158">Klicka på **aktiverat**</span><span class="sxs-lookup"><span data-stu-id="cf84c-158">Click **Enabled**</span></span>
5. <span data-ttu-id="cf84c-159">I avsnittet alternativ klickar du på **visa** bredvid Modulnamnen</span><span class="sxs-lookup"><span data-stu-id="cf84c-159">In the Options section, click on **Show** next to Module Names</span></span>
6. <span data-ttu-id="cf84c-160">Typ `\*` i popup-fönstret.</span><span class="sxs-lookup"><span data-stu-id="cf84c-160">Type `\*` in the pop up window.</span></span> <span data-ttu-id="cf84c-161">Detta instruerar PowerShell för att logga kommandon från alla moduler.</span><span class="sxs-lookup"><span data-stu-id="cf84c-161">This instructs PowerShell to log commands from all modules.</span></span>
7. <span data-ttu-id="cf84c-162">Klicka på **OK** att ställa in principen</span><span class="sxs-lookup"><span data-stu-id="cf84c-162">Click **OK** to set the policy</span></span>
8. <span data-ttu-id="cf84c-163">Dubbelklicka på **aktiverar loggning för PowerShell-skript Block**</span><span class="sxs-lookup"><span data-stu-id="cf84c-163">Double click on **Turn on PowerShell Script Block Logging**</span></span>
9. <span data-ttu-id="cf84c-164">Klicka på **aktiverat**</span><span class="sxs-lookup"><span data-stu-id="cf84c-164">Click **Enabled**</span></span>
10. <span data-ttu-id="cf84c-165">Klicka på **OK** att ställa in principen</span><span class="sxs-lookup"><span data-stu-id="cf84c-165">Click **OK** to set the policy</span></span>
11. <span data-ttu-id="cf84c-166">(På domänanslutna datorer endast) Kör `gpupdate` eller vänta tills en grupprincip för att bearbeta den uppdaterade policyn och tillämpa inställningarna</span><span class="sxs-lookup"><span data-stu-id="cf84c-166">(On domain-joined machines only) Run `gpupdate` or wait for Group Policy to process the updated policy and apply the settings</span></span>

<span data-ttu-id="cf84c-167">Du kan också aktivera systemomfattande PowerShell avskrift via en Grupprincip.</span><span class="sxs-lookup"><span data-stu-id="cf84c-167">You can also enable system-wide PowerShell transcription through Group Policy.</span></span>

## <a name="next-steps"></a><span data-ttu-id="cf84c-168">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="cf84c-168">Next steps</span></span>

[<span data-ttu-id="cf84c-169">Skapa en roll funktionen fil</span><span class="sxs-lookup"><span data-stu-id="cf84c-169">Create a role capability file</span></span>](role-capabilities.md)

[<span data-ttu-id="cf84c-170">Skapa en konfigurationsfil för session</span><span class="sxs-lookup"><span data-stu-id="cf84c-170">Create a session configuration file</span></span>](session-configurations.md)

## <a name="see-also"></a><span data-ttu-id="cf84c-171">Se även</span><span class="sxs-lookup"><span data-stu-id="cf84c-171">See also</span></span>

[<span data-ttu-id="cf84c-172">Mer information om PowerShell-fjärrkommunikation och WinRM-säkerhet</span><span class="sxs-lookup"><span data-stu-id="cf84c-172">Additional information about PowerShell Remoting and WinRM security</span></span>](/powershell/scripting/setup/winrmsecurity)

[<span data-ttu-id="cf84c-173">*PowerShell ♥ blå teamet* blogginlägg om säkerhet</span><span class="sxs-lookup"><span data-stu-id="cf84c-173">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)