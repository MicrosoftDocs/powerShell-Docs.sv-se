---
ms.date: 07/10/2019
keywords: jea, powershell, säkerhet
title: JEA-krav
ms.openlocfilehash: 8fca5c068412e86acfdb8bed400699f721b76191
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734288"
---
# <a name="prerequisites"></a><span data-ttu-id="234d9-103">Förutsättningar</span><span class="sxs-lookup"><span data-stu-id="234d9-103">Prerequisites</span></span>

<span data-ttu-id="234d9-104">Just Enough Administration är en funktion som ingår i PowerShell 5.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="234d9-104">Just Enough Administration is a feature included in PowerShell 5.0 and higher.</span></span> <span data-ttu-id="234d9-105">Den här artikeln beskrivs de krav som måste uppfyllas för att börja använda JEA.</span><span class="sxs-lookup"><span data-stu-id="234d9-105">This article describes the prerequisites that must be satisfied to start using JEA.</span></span>


## <a name="check-which-version-of-powershell-is-installed"></a><span data-ttu-id="234d9-106">Kontrollera vilken version av PowerShell är installerat</span><span class="sxs-lookup"><span data-stu-id="234d9-106">Check which version of PowerShell is installed</span></span>

<span data-ttu-id="234d9-107">Om du vill kontrollera vilken version av PowerShell är installerat på datorn, kontrollera den `$PSVersionTable` variabel i en Windows PowerShell-kommandotolk.</span><span class="sxs-lookup"><span data-stu-id="234d9-107">To check which version of PowerShell is installed on your system, check the `$PSVersionTable` variable in a Windows PowerShell prompt.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

<span data-ttu-id="234d9-108">JEA är tillgängliga i PowerShell 5.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="234d9-108">JEA is available with PowerShell 5.0 and higher.</span></span> <span data-ttu-id="234d9-109">Full funktionalitet får rekommenderar vi att du installerar den senaste versionen av PowerShell som är tillgängliga för ditt system.</span><span class="sxs-lookup"><span data-stu-id="234d9-109">For full functionality, it's recommended that you install the latest version of PowerShell available for your system.</span></span> <span data-ttu-id="234d9-110">I följande tabell beskrivs JEAS tillgänglighet på Windows Server:</span><span class="sxs-lookup"><span data-stu-id="234d9-110">The following table describes JEA's availability on Windows Server:</span></span>

| <span data-ttu-id="234d9-111">Serveroperativsystem</span><span class="sxs-lookup"><span data-stu-id="234d9-111">Server Operating System</span></span> |                <span data-ttu-id="234d9-112">JEA-tillgänglighet</span><span class="sxs-lookup"><span data-stu-id="234d9-112">JEA Availability</span></span>                |
| ----------------------- | ---------------------------------------------- |
| <span data-ttu-id="234d9-113">Windows Server 2016+</span><span class="sxs-lookup"><span data-stu-id="234d9-113">Windows Server 2016+</span></span>    | <span data-ttu-id="234d9-114">Förinstallerad</span><span class="sxs-lookup"><span data-stu-id="234d9-114">Preinstalled</span></span>                                   |
| <span data-ttu-id="234d9-115">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="234d9-115">Windows Server 2012 R2</span></span>  | <span data-ttu-id="234d9-116">Alla funktioner i WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="234d9-116">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="234d9-117">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="234d9-117">Windows Server 2012</span></span>     | <span data-ttu-id="234d9-118">Alla funktioner i WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="234d9-118">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="234d9-119">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="234d9-119">Windows Server 2008 R2</span></span>  | <span data-ttu-id="234d9-120">Funktioner<sup>1</sup> med WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="234d9-120">Reduced functionality<sup>1</sup> with WMF 5.1</span></span> |

<span data-ttu-id="234d9-121">Du kan också använda JEA på datorn hem- eller arbetsnätverk:</span><span class="sxs-lookup"><span data-stu-id="234d9-121">You can also use JEA on your home or work computer:</span></span>

| <span data-ttu-id="234d9-122">Klientoperativsystem</span><span class="sxs-lookup"><span data-stu-id="234d9-122">Client Operating System</span></span> |                   <span data-ttu-id="234d9-123">JEA-tillgänglighet</span><span class="sxs-lookup"><span data-stu-id="234d9-123">JEA Availability</span></span>                   |
| ----------------------- | ---------------------------------------------------- |
| <span data-ttu-id="234d9-124">Windows 10 1607+</span><span class="sxs-lookup"><span data-stu-id="234d9-124">Windows 10 1607+</span></span>        | <span data-ttu-id="234d9-125">Förinstallerad</span><span class="sxs-lookup"><span data-stu-id="234d9-125">Preinstalled</span></span>                                         |
| <span data-ttu-id="234d9-126">Windows 10 1603, 1511</span><span class="sxs-lookup"><span data-stu-id="234d9-126">Windows 10 1603, 1511</span></span>   | <span data-ttu-id="234d9-127">Förinstallerad, med nedsatt funktionalitet<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="234d9-127">Preinstalled, with reduced functionality<sup>2</sup></span></span> |
| <span data-ttu-id="234d9-128">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="234d9-128">Windows 10 1507</span></span>         | <span data-ttu-id="234d9-129">Inte tillgänglig</span><span class="sxs-lookup"><span data-stu-id="234d9-129">Not available</span></span>                                        |
| <span data-ttu-id="234d9-130">Windows 8, 8.1</span><span class="sxs-lookup"><span data-stu-id="234d9-130">Windows 8, 8.1</span></span>          | <span data-ttu-id="234d9-131">Alla funktioner i WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="234d9-131">Full functionality with WMF 5.1</span></span>                      |
| <span data-ttu-id="234d9-132">Windows 7</span><span class="sxs-lookup"><span data-stu-id="234d9-132">Windows 7</span></span>               | <span data-ttu-id="234d9-133">Funktioner<sup>1</sup> med WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="234d9-133">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>       |

- <span data-ttu-id="234d9-134"><sup>1</sup> JEA kan inte konfigureras för att använda gruppen hanterade tjänstkonton på Windows Server 2008 R2 eller Windows 7.</span><span class="sxs-lookup"><span data-stu-id="234d9-134"><sup>1</sup> JEA can't be configured to use group-managed service accounts on Windows Server 2008 R2 or Windows 7.</span></span> <span data-ttu-id="234d9-135">Virtuella konton och andra funktioner för JEA *är* stöds.</span><span class="sxs-lookup"><span data-stu-id="234d9-135">Virtual accounts and other JEA features *are* supported.</span></span>

- <span data-ttu-id="234d9-136"><sup>2</sup> följande JEA-funktioner stöds inte på Windows 10 version 1511 och 1603:</span><span class="sxs-lookup"><span data-stu-id="234d9-136"><sup>2</sup> The following JEA features aren't supported on Windows 10 versions 1511 and 1603:</span></span>

  - <span data-ttu-id="234d9-137">Körs som ett-grupphanterat tjänstkonto</span><span class="sxs-lookup"><span data-stu-id="234d9-137">Running as a group-managed service account</span></span>
  - <span data-ttu-id="234d9-138">Regler för villkorlig åtkomst i sessionskonfigurationer</span><span class="sxs-lookup"><span data-stu-id="234d9-138">Conditional access rules in session configurations</span></span>
  - <span data-ttu-id="234d9-139">Användare-enhet</span><span class="sxs-lookup"><span data-stu-id="234d9-139">The user drive</span></span>
  - <span data-ttu-id="234d9-140">Bevilja åtkomst till lokala användarkonton</span><span class="sxs-lookup"><span data-stu-id="234d9-140">Granting access to local user accounts</span></span>

  <span data-ttu-id="234d9-141">För att få stöd för dessa funktioner kan du uppdatera Windows till version 1607 (Anniversary Update) eller högre.</span><span class="sxs-lookup"><span data-stu-id="234d9-141">To get support for these features, update Windows to version 1607 (Anniversary Update) or higher.</span></span>

### <a name="install-windows-management-framework"></a><span data-ttu-id="234d9-142">Installera Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="234d9-142">Install Windows Management Framework</span></span>

<span data-ttu-id="234d9-143">Om du kör en äldre version av PowerShell, kan du behöva uppdatera datorn med den senaste uppdateringen av Windows Management Framework (WMF).</span><span class="sxs-lookup"><span data-stu-id="234d9-143">If you're running an older version of PowerShell, you may need to update your system with the latest Windows Management Framework (WMF) update.</span></span> <span data-ttu-id="234d9-144">Mer information finns i den [WMF dokumentation](/powershell/wmf/overview).</span><span class="sxs-lookup"><span data-stu-id="234d9-144">For more information, see the [WMF documentation](/powershell/wmf/overview).</span></span>

<span data-ttu-id="234d9-145">Vi rekommenderar att du testar din arbetsbelastning kompatibilitet med WMF innan du uppgraderar alla dina servrar.</span><span class="sxs-lookup"><span data-stu-id="234d9-145">It's recommended that you test your workload's compatibility with WMF before upgrading all of your servers.</span></span>

<span data-ttu-id="234d9-146">Windows 10-användare bör installera de senaste funktionsuppdateringarna för att hämta den aktuella versionen av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="234d9-146">Windows 10 users should install the latest feature updates to obtain the current version of Windows PowerShell.</span></span>

## <a name="enable-powershell-remoting"></a><span data-ttu-id="234d9-147">Aktivera PowerShell-fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="234d9-147">Enable PowerShell Remoting</span></span>

<span data-ttu-id="234d9-148">PowerShell-fjärrkommunikation utgör grunden som JEA har skapats.</span><span class="sxs-lookup"><span data-stu-id="234d9-148">PowerShell Remoting provides the foundation on which JEA is built.</span></span> <span data-ttu-id="234d9-149">Det är nödvändigt att säkerställa att PowerShell-fjärrkommunikation är aktiverad och korrekt skyddade innan du kan använda JEA.</span><span class="sxs-lookup"><span data-stu-id="234d9-149">It's necessary to ensure PowerShell Remoting is enabled and properly secured before you can use JEA.</span></span> <span data-ttu-id="234d9-150">Mer information finns i [WinRM Security](/powershell/scripting/learn/remoting/winrmsecurity).</span><span class="sxs-lookup"><span data-stu-id="234d9-150">For more information, see [WinRM Security](/powershell/scripting/learn/remoting/winrmsecurity).</span></span>

<span data-ttu-id="234d9-151">PowerShell-fjärrkommunikation är aktiverat som standard på Windows Server 2012, 2012 R2 och 2016.</span><span class="sxs-lookup"><span data-stu-id="234d9-151">PowerShell Remoting is enabled by default on Windows Server 2012, 2012 R2, and 2016.</span></span> <span data-ttu-id="234d9-152">Du kan aktivera PowerShell-fjärrkommunikation genom att köra följande kommando i ett upphöjt PowerShell-fönster.</span><span class="sxs-lookup"><span data-stu-id="234d9-152">You can enable PowerShell Remoting by running the following command in an elevated PowerShell window.</span></span>

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a><span data-ttu-id="234d9-153">Aktivera PowerShell-modulen och skript block loggning (valfritt)</span><span class="sxs-lookup"><span data-stu-id="234d9-153">Enable PowerShell module and script block logging (optional)</span></span>

<span data-ttu-id="234d9-154">Följande steg aktiverar loggning för alla PowerShell-åtgärder på datorn.</span><span class="sxs-lookup"><span data-stu-id="234d9-154">The following steps enable logging for all PowerShell actions on your system.</span></span> <span data-ttu-id="234d9-155">Loggning av PowerShell-modulen krävs inte för JEA, men det rekommenderas du aktiverar loggning för att se till att köra kommandon användare är inloggade på en central plats.</span><span class="sxs-lookup"><span data-stu-id="234d9-155">PowerShell Module Logging isn't required for JEA, however it's recommended you turn on logging to ensure the commands users run are logged in a central location.</span></span>

<span data-ttu-id="234d9-156">Du kan konfigurera principen för loggning av PowerShell-modulen med hjälp av en Grupprincip.</span><span class="sxs-lookup"><span data-stu-id="234d9-156">You can configure the PowerShell Module Logging policy using Group Policy.</span></span>

1. <span data-ttu-id="234d9-157">Öppna Redigeraren för lokal princip på en arbetsstation eller ett grupprincipobjekt i Group Policy Management Console på en Active Directory-domänkontrollant</span><span class="sxs-lookup"><span data-stu-id="234d9-157">Open the Local Group Policy Editor on a workstation or a Group Policy Object in the Group Policy Management Console on an Active Directory Domain Controller</span></span>
2. <span data-ttu-id="234d9-158">Gå till **Datorkonfiguration\\Administrationsmallar\\Windows-komponenter\\Windows PowerShell**</span><span class="sxs-lookup"><span data-stu-id="234d9-158">Navigate to **Computer Configuration\\Administrative Templates\\Windows Components\\Windows PowerShell**</span></span>
3. <span data-ttu-id="234d9-159">Dubbelklicka på **aktiverar loggning av modul**</span><span class="sxs-lookup"><span data-stu-id="234d9-159">Double-click on **Turn on Module Logging**</span></span>
4. <span data-ttu-id="234d9-160">Klicka på **aktiverat**</span><span class="sxs-lookup"><span data-stu-id="234d9-160">Click **Enabled**</span></span>
5. <span data-ttu-id="234d9-161">I avsnittet alternativ klickar du på **visa** bredvid Modulnamnen</span><span class="sxs-lookup"><span data-stu-id="234d9-161">In the Options section, click on **Show** next to Module Names</span></span>
6. <span data-ttu-id="234d9-162">Typ `*` i popup-fönstret för att logga kommandon från alla moduler.</span><span class="sxs-lookup"><span data-stu-id="234d9-162">Type `*` in the pop-up window to log commands from all modules.</span></span>
7. <span data-ttu-id="234d9-163">Klicka på **OK** att ställa in principen</span><span class="sxs-lookup"><span data-stu-id="234d9-163">Click **OK** to set the policy</span></span>
8. <span data-ttu-id="234d9-164">Dubbelklicka på **aktivera PowerShell-skriptblock loggning**</span><span class="sxs-lookup"><span data-stu-id="234d9-164">Double-click on **Turn on PowerShell Script Block Logging**</span></span>
9. <span data-ttu-id="234d9-165">Klicka på **aktiverat**</span><span class="sxs-lookup"><span data-stu-id="234d9-165">Click **Enabled**</span></span>
10. <span data-ttu-id="234d9-166">Klicka på **OK** att ställa in principen</span><span class="sxs-lookup"><span data-stu-id="234d9-166">Click **OK** to set the policy</span></span>
11. <span data-ttu-id="234d9-167">(På domänanslutna datorer endast) Kör `gpupdate` eller vänta tills en grupprincip för att bearbeta den uppdaterade policyn och tillämpa inställningarna</span><span class="sxs-lookup"><span data-stu-id="234d9-167">(On domain-joined machines only) Run `gpupdate` or wait for Group Policy to process the updated policy and apply the settings</span></span>

<span data-ttu-id="234d9-168">Du kan också aktivera systemomfattande PowerShell avskrift via en Grupprincip.</span><span class="sxs-lookup"><span data-stu-id="234d9-168">You can also enable system-wide PowerShell transcription through Group Policy.</span></span>

## <a name="next-steps"></a><span data-ttu-id="234d9-169">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="234d9-169">Next steps</span></span>

[<span data-ttu-id="234d9-170">Skapa en roll funktionen fil</span><span class="sxs-lookup"><span data-stu-id="234d9-170">Create a role capability file</span></span>](role-capabilities.md)

[<span data-ttu-id="234d9-171">Skapa en konfigurationsfil för session</span><span class="sxs-lookup"><span data-stu-id="234d9-171">Create a session configuration file</span></span>](session-configurations.md)

## <a name="see-also"></a><span data-ttu-id="234d9-172">Se även</span><span class="sxs-lookup"><span data-stu-id="234d9-172">See also</span></span>

[<span data-ttu-id="234d9-173">WinRM-säkerhet</span><span class="sxs-lookup"><span data-stu-id="234d9-173">WinRM Security</span></span>](/powershell/scripting/learn/remoting/winrmsecurity)

[<span data-ttu-id="234d9-174">PowerShell ♥ blå teamet</span><span class="sxs-lookup"><span data-stu-id="234d9-174">PowerShell ♥ the Blue Team</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
