---
title: Nyheter i PowerShell 7,1
description: Nya funktioner och ändringar som lanseras i PowerShell 7,1
ms.date: 12/15/2020
ms.openlocfilehash: 6bbeccd07dd696ee019828bdcd68ce3f6ee627e3
ms.sourcegitcommit: 1628fd2a1f50aec2f31ffb1c451a3ce77c08983c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/16/2020
ms.locfileid: "97577215"
---
# <a name="whats-new-in-powershell-71"></a><span data-ttu-id="68440-103">Nyheter i PowerShell 7,1</span><span class="sxs-lookup"><span data-stu-id="68440-103">What's New in PowerShell 7.1</span></span>

<span data-ttu-id="68440-104">Den 11 november 2020 [presenterade](https://devblogs.microsoft.com/powershell/announcing-powershell-7-1/) vi den allmänna tillgängligheten för PowerShell 7,1.</span><span class="sxs-lookup"><span data-stu-id="68440-104">On November 11, 2020 we [announced](https://devblogs.microsoft.com/powershell/announcing-powershell-7-1/) the general availability of PowerShell 7.1.</span></span> <span data-ttu-id="68440-105">Vi bygger på stiftelsen som etablerats i PowerShell 7,0, våra ansträngningar fokuserar på community-problem och inkluderar ett antal förbättringar och korrigeringar.</span><span class="sxs-lookup"><span data-stu-id="68440-105">Building on the foundation established in PowerShell 7.0, our efforts focused on community issues and include a number of improvements and fixes.</span></span> <span data-ttu-id="68440-106">Vi strävar efter att se till att PowerShell är en stabil och genomförd plattform.</span><span class="sxs-lookup"><span data-stu-id="68440-106">We are committed to ensuring that PowerShell remains a stable and performant platform.</span></span>

<span data-ttu-id="68440-107">PowerShell 7,1 innehåller följande funktioner, uppdateringar och brytande ändringar.</span><span class="sxs-lookup"><span data-stu-id="68440-107">PowerShell 7.1 includes the following features, updates, and breaking changes.</span></span>

- <span data-ttu-id="68440-108">PSReadLine 2.1.0, som innehåller förutsägande IntelliSense</span><span class="sxs-lookup"><span data-stu-id="68440-108">PSReadLine 2.1.0, which includes Predictive IntelliSense</span></span>
- <span data-ttu-id="68440-109">PowerShell 7,1 har publicerats på Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="68440-109">PowerShell 7.1 has been published to the Microsoft Store</span></span>
- <span data-ttu-id="68440-110">Installations paket har uppdaterats för nya OS-versioner med stöd för ARM64</span><span class="sxs-lookup"><span data-stu-id="68440-110">Installer packages updated for new OS versions with support for ARM64</span></span>
- <span data-ttu-id="68440-111">4 nya experimentella funktioner och 2 experimentella funktioner upphöjt till vanlig</span><span class="sxs-lookup"><span data-stu-id="68440-111">4 new experimental features and 2 experimental features promoted to mainstream</span></span>
- <span data-ttu-id="68440-112">Flera större ändringar för att förbättra användbarhet</span><span class="sxs-lookup"><span data-stu-id="68440-112">Several breaking changes to improve usability</span></span>

<span data-ttu-id="68440-113">En fullständig lista över ändringar finns i [ändringsloggen](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.1.md) i GitHub-lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="68440-113">For a complete list of changes, see the [CHANGELOG](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.1.md) in the GitHub repository.</span></span>

## <a name="psreadline-210"></a><span data-ttu-id="68440-114">PSReadLine 2.1.0</span><span class="sxs-lookup"><span data-stu-id="68440-114">PSReadLine 2.1.0</span></span>

<span data-ttu-id="68440-115">PowerShell 7,1 inkluderar även PSReadLine 2.1.0.</span><span class="sxs-lookup"><span data-stu-id="68440-115">PowerShell 7.1 also include PSReadLine 2.1.0.</span></span> <span data-ttu-id="68440-116">Den här versionen innehåller förutsägande IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="68440-116">This version includes Predictive IntelliSense.</span></span> <span data-ttu-id="68440-117">Mer information om funktionen förutsägande IntelliSense finns i [meddelandet](https://devblogs.microsoft.com/powershell/announcing-psreadline-2-1-with-predictive-intellisense/) i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="68440-117">For more information about the Predictive IntelliSense feature, see the [announcement](https://devblogs.microsoft.com/powershell/announcing-psreadline-2-1-with-predictive-intellisense/) in the PowerShell blog.</span></span>

## <a name="microsoft-store-installer-package"></a><span data-ttu-id="68440-118">Microsoft Store installations paket</span><span class="sxs-lookup"><span data-stu-id="68440-118">Microsoft Store installer package</span></span>

<span data-ttu-id="68440-119">PowerShell 7,1 har publicerats till Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="68440-119">PowerShell 7.1 has been published to the Microsoft Store.</span></span> <span data-ttu-id="68440-120">Du hittar PowerShell-versionen på [Microsoft Store](https://www.microsoft.com/store/apps/9MZ1SNWT0N5D) webbplats eller i Store-programmet i Windows.</span><span class="sxs-lookup"><span data-stu-id="68440-120">You can find the PowerShell release on the [Microsoft Store](https://www.microsoft.com/store/apps/9MZ1SNWT0N5D) website or in the Store application in Windows.</span></span>

<span data-ttu-id="68440-121">Fördelar med Microsoft Store-paketet:</span><span class="sxs-lookup"><span data-stu-id="68440-121">Benefits of the Microsoft Store package:</span></span>

- <span data-ttu-id="68440-122">Automatiska uppdateringar har skapats direkt i Windows 10</span><span class="sxs-lookup"><span data-stu-id="68440-122">Automatic updates built right into Windows 10</span></span>
- <span data-ttu-id="68440-123">Integreras med andra mekanismer för program varu distribution som Intune och SCCM</span><span class="sxs-lookup"><span data-stu-id="68440-123">Integrates with other software distribution mechanisms like Intune and SCCM</span></span>

> [!NOTE]
> <span data-ttu-id="68440-124">Eventuella konfigurations inställningar på system nivå som lagras i `$PSHOME` kan inte ändras.</span><span class="sxs-lookup"><span data-stu-id="68440-124">Any system-level configuration settings stored in `$PSHOME` cannot be modified.</span></span> <span data-ttu-id="68440-125">Detta inkluderar WSMAN-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="68440-125">This includes the WSMAN configuration.</span></span> <span data-ttu-id="68440-126">Detta förhindrar att fjärrsessioner ansluter till Store-baserade installationer av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="68440-126">This prevents remote sessions from connecting to Store-based installs of PowerShell.</span></span> <span data-ttu-id="68440-127">Konfigurationer på användar nivå och SSH-fjärrkommunikation stöds.</span><span class="sxs-lookup"><span data-stu-id="68440-127">User-level configurations and SSH remoting are supported.</span></span>

## <a name="other-installers"></a><span data-ttu-id="68440-128">Andra installations program</span><span class="sxs-lookup"><span data-stu-id="68440-128">Other installers</span></span>

<span data-ttu-id="68440-129">Mer uppdaterad information om operativ system och support livs cykel som stöds finns i [PowerShell-Supportens livs cykel](/powershell/scripting/powershell-support-lifecycle).</span><span class="sxs-lookup"><span data-stu-id="68440-129">For more up-to-date information about supported operating systems and support lifecycle, see the [PowerShell Support Lifecycle](/powershell/scripting/powershell-support-lifecycle).</span></span>

<span data-ttu-id="68440-130">Kontrol lera installations anvisningarna för det önskade operativ systemet:</span><span class="sxs-lookup"><span data-stu-id="68440-130">Check the installation instructions for your preferred operating system:</span></span>

- [<span data-ttu-id="68440-131">Windows</span><span class="sxs-lookup"><span data-stu-id="68440-131">Windows</span></span>](/powershell/scripting/install/installing-powershell-core-on-windows)
- [<span data-ttu-id="68440-132">macOS</span><span class="sxs-lookup"><span data-stu-id="68440-132">macOS</span></span>](/powershell/scripting/install/installing-powershell-core-on-macos)
- [<span data-ttu-id="68440-133">Linux</span><span class="sxs-lookup"><span data-stu-id="68440-133">Linux</span></span>](/powershell/scripting/install/installing-powershell-core-on-linux)

<span data-ttu-id="68440-134">Dessutom stöder PowerShell 7,1 ARM32 och ARM64 varianter för Debian, Ubuntu och ARM64 Alpine Linux.</span><span class="sxs-lookup"><span data-stu-id="68440-134">Additionally, PowerShell 7.1 supports ARM32 and ARM64 flavors of Debian, Ubuntu, and ARM64 Alpine Linux.</span></span>

<span data-ttu-id="68440-135">Även om den inte stöds officiellt har communityn även tillhandahållit paket för [båge](https://aur.archlinux.org/packages/powershell/) och Kali Linux.</span><span class="sxs-lookup"><span data-stu-id="68440-135">While not officially supported, the community has also provided packages for [Arch](https://aur.archlinux.org/packages/powershell/) and Kali Linux.</span></span>

> [!NOTE]
> <span data-ttu-id="68440-136">Debian 10 +, CentOS 8 +, Ubuntu 20,04, alpina och arm stöder för närvarande inte WinRM-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="68440-136">Debian 10+, CentOS 8+, Ubuntu 20.04, Alpine and Arm currently do not support WinRM remoting.</span></span> <span data-ttu-id="68440-137">Mer information om hur du konfigurerar SSH-baserad fjärr kommunikation finns i [PowerShell-fjärrkommunikation via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span><span class="sxs-lookup"><span data-stu-id="68440-137">For details on setting up SSH-based remoting, see [PowerShell Remoting over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

## <a name="experimental-features"></a><span data-ttu-id="68440-138">Experimentella funktioner</span><span class="sxs-lookup"><span data-stu-id="68440-138">Experimental Features</span></span>

<span data-ttu-id="68440-139">Mer information om experiment funktionerna finns i [använda experimentella funktioner](../learn/experimental-features.md).</span><span class="sxs-lookup"><span data-stu-id="68440-139">For more information about the Experimental Features, see [Using Experimental Features](../learn/experimental-features.md).</span></span>

<span data-ttu-id="68440-140">Följande experimentella funktioner är nu vanliga funktioner i den här versionen:</span><span class="sxs-lookup"><span data-stu-id="68440-140">The following experimental features are now mainstream features in this release:</span></span>

- [<span data-ttu-id="68440-141">PSNullConditionalOperators</span><span class="sxs-lookup"><span data-stu-id="68440-141">PSNullConditionalOperators</span></span>](../learn/experimental-features.md#psnullconditionaloperators)
- [<span data-ttu-id="68440-142">PSUnixFileStat</span><span class="sxs-lookup"><span data-stu-id="68440-142">PSUnixFileStat</span></span>](../learn/experimental-features.md#psunixfilestat)

<span data-ttu-id="68440-143">Följande experimentella funktioner har lagts till i den här versionen:</span><span class="sxs-lookup"><span data-stu-id="68440-143">The following experimental features were added in this release:</span></span>

- [<span data-ttu-id="68440-144">Microsoft. PowerShell. Utility. PSManageBreakpointsInRunspace</span><span class="sxs-lookup"><span data-stu-id="68440-144">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span></span>](../learn/experimental-features.md#microsoftpowershellutilitypsmanagebreakpointsinrunspace)
  - <span data-ttu-id="68440-145">PowerShell 7,1 utökar den här experimentella funktionen för att lägga till **körnings utrymme** -parametern i alla `*-PSBreakpoint` cmdletar.</span><span class="sxs-lookup"><span data-stu-id="68440-145">PowerShell 7.1 extends this experimental feature to add the **Runspace** parameter to all `*-PSBreakpoint` cmdlets.</span></span> <span data-ttu-id="68440-146">Parametern **körnings utrymme** anger ett **körnings utrymme** -objekt som interagerar med Bryt punkter i den angivna körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="68440-146">The **Runspace** parameter specifies a **Runspace** object to interact with breakpoints in the specified runspace.</span></span>

- <span data-ttu-id="68440-147">[PSNativePSPathResolution](../learn/experimental-features.md#psnativepspathresolution) – med den här funktionen kan du skicka PowerShell-providerns sökvägar till interna kommandon som inte stöder PowerShell-syntax för sökväg.</span><span class="sxs-lookup"><span data-stu-id="68440-147">[PSNativePSPathResolution](../learn/experimental-features.md#psnativepspathresolution) - This feature allows you to pass PowerShell provider paths to native commands that don't support PowerShell path syntax.</span></span>

- <span data-ttu-id="68440-148">[PSCultureInvariantReplaceOperator](../learn/experimental-features.md#pscultureinvariantreplaceoperator) – när den vänstra operanden i en `-replace` operator-instruktion inte är en sträng, konverteras den operanden till en sträng.</span><span class="sxs-lookup"><span data-stu-id="68440-148">[PSCultureInvariantReplaceOperator](../learn/experimental-features.md#pscultureinvariantreplaceoperator) - When the left-hand operand in a `-replace` operator statement is not a string, that operand is converted to a string.</span></span> <span data-ttu-id="68440-149">När funktionen är aktive rad använder inte konverteringen kultur inställningar för sträng konvertering.</span><span class="sxs-lookup"><span data-stu-id="68440-149">With the feature enabled, the conversion does not use Culture settings for string conversion.</span></span>

- <span data-ttu-id="68440-150">[PSSubsystemPluginModel](../learn/experimental-features.md#pssubsystempluginmodel) hjälper till att stödja framtida förutsägande IntelliSense-plugin-program.</span><span class="sxs-lookup"><span data-stu-id="68440-150">[PSSubsystemPluginModel](../learn/experimental-features.md#pssubsystempluginmodel) lays the groundwork to support future Predictive IntelliSense plug-ins.</span></span>

## <a name="breaking-changes-and-improvements"></a><span data-ttu-id="68440-151">Bryta ändringar och förbättringar</span><span class="sxs-lookup"><span data-stu-id="68440-151">Breaking Changes and Improvements</span></span>

- <span data-ttu-id="68440-152">Korrigera `$?` till inte `$false` när det interna kommandot skriver till `stderr` ([#13395](https://github.com/PowerShell/PowerShell/pull/13395))</span><span class="sxs-lookup"><span data-stu-id="68440-152">Fix `$?` to not be `$false` when native command writes to `stderr` ([#13395](https://github.com/PowerShell/PowerShell/pull/13395))</span></span>

  <span data-ttu-id="68440-153">Det är vanligt att de interna kommandona skrivs till utan att det är `stderr` något som tyder på ett haveri.</span><span class="sxs-lookup"><span data-stu-id="68440-153">It is common for native commands to write to `stderr` without intending to indicate a failure.</span></span>
  <span data-ttu-id="68440-154">Med den här ändringen `$?` anges till `$false` endast när det inbyggda kommandot också har en slutkod som inte är noll.</span><span class="sxs-lookup"><span data-stu-id="68440-154">With this change `$?` is set to `$false` only when the native command also has a non-zero exit code.</span></span> <span data-ttu-id="68440-155">Den här ändringen är inte relaterad till experiment funktionen `PSNotApplyErrorActionToStderr` .</span><span class="sxs-lookup"><span data-stu-id="68440-155">This change is unrelated to the experimental feature `PSNotApplyErrorActionToStderr`.</span></span>

- <span data-ttu-id="68440-156">`$ErrorActionPreference`Påverkar inte `stderr` utdata från interna kommandon ([#13361](https://github.com/PowerShell/PowerShell/pull/13361))</span><span class="sxs-lookup"><span data-stu-id="68440-156">Make `$ErrorActionPreference` not affect `stderr` output of native commands ([#13361](https://github.com/PowerShell/PowerShell/pull/13361))</span></span>

  <span data-ttu-id="68440-157">Det är vanligt att de interna kommandona skrivs till utan att det är `stderr` något som tyder på ett haveri.</span><span class="sxs-lookup"><span data-stu-id="68440-157">It is common for native commands to write to `stderr` without intending to indicate a failure.</span></span>
  <span data-ttu-id="68440-158">Med den här ändringen `stderr` fångas utdata fortfarande in i **ErrorRecord** -objekt, men körningen gäller inte längre `$ErrorActionPreference` om **ErrorRecord** kommer från ett internt kommando.</span><span class="sxs-lookup"><span data-stu-id="68440-158">With this change, `stderr` output is still captured in **ErrorRecord** objects, but the runtime no longer applies `$ErrorActionPreference` if the **ErrorRecord** comes from a native command.</span></span>

- <span data-ttu-id="68440-159">Byt namn `-FromUnixTime` till `-UnixTimeSeconds` på för `Get-Date` att tillåta UNIX-tidsinformation ([#13084](https://github.com/PowerShell/PowerShell/pull/13084)) (tack @aetos382 !)</span><span class="sxs-lookup"><span data-stu-id="68440-159">Rename `-FromUnixTime` to `-UnixTimeSeconds` on `Get-Date` to allow Unix time input ([#13084](https://github.com/PowerShell/PowerShell/pull/13084)) (Thanks @aetos382!)</span></span>

  <span data-ttu-id="68440-160">`-FromUnixTime`Parametern lades till under 7,1-för hands version. 2.</span><span class="sxs-lookup"><span data-stu-id="68440-160">The `-FromUnixTime` parameter was added during 7.1-preview.2.</span></span> <span data-ttu-id="68440-161">Parametern har bytt namn för att bättre matcha data typen.</span><span class="sxs-lookup"><span data-stu-id="68440-161">The parameter was renamed to better match the data type.</span></span> <span data-ttu-id="68440-162">Den här parametern använder ett heltals värde som representerar i sekunder sedan 1 januari 1970, 0:00:00.</span><span class="sxs-lookup"><span data-stu-id="68440-162">This parameter takes an integer value that represents in seconds since January 1, 1970, 0:00:00.</span></span>

  <span data-ttu-id="68440-163">I det här exemplet konverteras en UNIX-tid (som representeras av antalet sekunder sedan 1970-01-01 0:00:00) till DateTime.</span><span class="sxs-lookup"><span data-stu-id="68440-163">This example converts a Unix time (represented by the number of seconds since 1970-01-01 0:00:00) to DateTime.</span></span>

  ```powershell
  Get-Date -UnixTimeSeconds 1577836800

  Wednesday, January 01, 2020 12:00:00 AM
  ```

- <span data-ttu-id="68440-164">Tillåt explicit angiven namngiven parameter att ersätta samma med en hash-ihopbuntning (#13162)</span><span class="sxs-lookup"><span data-stu-id="68440-164">Allow explicitly specified named parameter to supersede the same one from hashtable splatting (#13162)</span></span>

  <span data-ttu-id="68440-165">Med den här ändringen flyttas de namngivna parametrarna från ihopbuntning till slutet av parameter listan så att de binds efter att alla explicit angivna namngivna parametrar är kopplade till varandra.</span><span class="sxs-lookup"><span data-stu-id="68440-165">With this change, the named parameters from splatting are moved to the end of the parameter list so that they are bound after all explicitly specified named parameters are bound.</span></span> <span data-ttu-id="68440-166">Parameter bindning för enkla funktioner genererar inte ett fel när det inte går att hitta en angiven namngiven parameter.</span><span class="sxs-lookup"><span data-stu-id="68440-166">Parameter binding for simple functions doesn't throw an error when a specified named parameter cannot be found.</span></span> <span data-ttu-id="68440-167">Okända namngivna parametrar är kopplade till den `$args` enkla funktionens parameter.</span><span class="sxs-lookup"><span data-stu-id="68440-167">Unknown named parameters are bound to the `$args` parameter of the simple function.</span></span> <span data-ttu-id="68440-168">Om du flyttar ihopbuntning till slutet av argument listan ändras den ordning som parametrarna visas i `$args` .</span><span class="sxs-lookup"><span data-stu-id="68440-168">Moving splatting to the end of the argument list changes the order the parameters appears in `$args`.</span></span>

  <span data-ttu-id="68440-169">Exempel:</span><span class="sxs-lookup"><span data-stu-id="68440-169">For example:</span></span>

  ```powershell
  function SimpleTest {
      param(
          $Name,
          $Path
      )
      "Name: $Name; Path: $Path; Args: $args"
  }
  ```

  <span data-ttu-id="68440-170">I föregående beteende är inte **sökvägen** kopplad till `-Path` eftersom det är det tredje argumentet i argument listan.</span><span class="sxs-lookup"><span data-stu-id="68440-170">In the previous behavior, **MyPath** is not bound to `-Path` because it's the third argument in the argument list.</span></span> <span data-ttu-id="68440-171"># # Så att det slutar att vara fyllda i "$args" tillsammans med `Blah = "World"`</span><span class="sxs-lookup"><span data-stu-id="68440-171">## So it ends up being stuffed into '$args' along with `Blah = "World"`</span></span>

  ```powershell
  PS> $hash = @{ Name = "Hello"; Blah = "World" }
  PS> SimpleTest @hash "MyPath"
  Name: Hello; Path: ; Args: -Blah: World MyPath
  ```

  <span data-ttu-id="68440-172">Med den här ändringen flyttas argumenten från `@hash` till slutet av argument listan.</span><span class="sxs-lookup"><span data-stu-id="68440-172">With this change, the arguments from `@hash` are moved to the end of the argument list.</span></span> <span data-ttu-id="68440-173">**Sökvägar** blir det första argumentet i listan, så den är kopplad till `-Path` .</span><span class="sxs-lookup"><span data-stu-id="68440-173">**MyPath** becomes the first argument in the list, so it is bound to `-Path`.</span></span>

  ```powershell
  PS> SimpleTest @hash "MyPath"
  Name: Hello; Path: MyPath; Args: -Blah: World
  ```

- <span data-ttu-id="68440-174">Gör att växel parametern `-Qualifier` inte placeras för `Split-Path` ([#12960](https://github.com/PowerShell/PowerShell/pull/12960)) (tack @yecril71pl !)</span><span class="sxs-lookup"><span data-stu-id="68440-174">Make the switch parameter `-Qualifier` not positional for `Split-Path` ([#12960](https://github.com/PowerShell/PowerShell/pull/12960)) (Thanks @yecril71pl!)</span></span>

- <span data-ttu-id="68440-175">Matcha arbets katalogen som en litteral sökväg för `Start-Process` när den inte har angetts ([#11946](https://github.com/PowerShell/PowerShell/pull/11946)) (tack @NoMoreFood !)</span><span class="sxs-lookup"><span data-stu-id="68440-175">Resolve the working directory as literal path for `Start-Process` when it's not specified ([#11946](https://github.com/PowerShell/PowerShell/pull/11946)) (Thanks @NoMoreFood!)</span></span>

- <span data-ttu-id="68440-176">Skapa `-OutFile` en parameter i webb-cmdlets som fungerar som `-LiteralPath` ([#11701](https://github.com/PowerShell/PowerShell/pull/11701)) (tack @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="68440-176">Make `-OutFile` parameter in web cmdlets to work like `-LiteralPath` ([#11701](https://github.com/PowerShell/PowerShell/pull/11701)) (Thanks @iSazonov!)</span></span>

- <span data-ttu-id="68440-177">Korrigera sträng parameter bindning för `BigInteger` numeriska literaler ([#11634](https://github.com/PowerShell/PowerShell/pull/11634)) (tack @vexx32 !)</span><span class="sxs-lookup"><span data-stu-id="68440-177">Fix string parameter binding for `BigInteger` numeric literals ([#11634](https://github.com/PowerShell/PowerShell/pull/11634)) (Thanks @vexx32!)</span></span>

- <span data-ttu-id="68440-178">I Windows `Start-Process` skapar en process miljö med alla miljövariabler från den aktuella sessionen, med `-UseNewEnvironment` en ny standard process miljö ([#10830](https://github.com/PowerShell/PowerShell/pull/10830)) (tack @iSazonov !)</span><span class="sxs-lookup"><span data-stu-id="68440-178">On Windows, `Start-Process` creates a process environment with all the environment variables from current session, using `-UseNewEnvironment` creates a new default process environment ([#10830](https://github.com/PowerShell/PowerShell/pull/10830)) (Thanks @iSazonov!)</span></span>

- <span data-ttu-id="68440-179">Bryt inte retur resultat i `PSObject` vid konvertering av ett `ScriptBlock` till ett ombud ([#10619](https://github.com/PowerShell/PowerShell/pull/10619))</span><span class="sxs-lookup"><span data-stu-id="68440-179">Do not wrap return result in `PSObject` when converting a `ScriptBlock` to a delegate ([#10619](https://github.com/PowerShell/PowerShell/pull/10619))</span></span>

  <span data-ttu-id="68440-180">När en `ScriptBlock` konverteras till en Delegerings typ som ska användas i C#-kontexten får du onödiga problem genom att figursätta resultatet i a `PSObject` :</span><span class="sxs-lookup"><span data-stu-id="68440-180">When a `ScriptBlock` is converted to a delegate type to be used in C# context, wrapping the result in a `PSObject` brings unneeded troubles:</span></span>

  - <span data-ttu-id="68440-181">När värdet konverteras till den delegerade retur typen, blir det i `PSObject` själva verket figursatt.</span><span class="sxs-lookup"><span data-stu-id="68440-181">When the value is converted to the delegate return type, the `PSObject` essentially gets unwrapped.</span></span> <span data-ttu-id="68440-182">Så den `PSObject` är inte nödvändig.</span><span class="sxs-lookup"><span data-stu-id="68440-182">So the `PSObject` is unneeded.</span></span>
  - <span data-ttu-id="68440-183">När den här svars typen är, omsluts `object` den i en `PSObject` gör det svårt att arbeta med i C#-kod.</span><span class="sxs-lookup"><span data-stu-id="68440-183">When the delegate return type is `object`, it gets wrapped in a `PSObject` making it hard to work with in C# code.</span></span>

  <span data-ttu-id="68440-184">Efter den här ändringen är det returnerade objektet det underliggande objektet.</span><span class="sxs-lookup"><span data-stu-id="68440-184">After this change, the returned object is the underlying object.</span></span>
