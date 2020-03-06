---
title: Nyheter i PowerShell 7,0
description: Nya funktioner och ändringar som lanseras i PowerShell 7,0
ms.date: 03/04/2020
ms.openlocfilehash: 6915bb70d6e54da86d2b935e3feed8d7f3770ba9
ms.sourcegitcommit: 4a26c05f162c4fa347a9d67e339f8a33e230b9ba
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78404984"
---
# <a name="whats-new-in-powershell-70"></a><span data-ttu-id="812cf-103">Nyheter i PowerShell 7,0</span><span class="sxs-lookup"><span data-stu-id="812cf-103">What's New in PowerShell 7.0</span></span>

<span data-ttu-id="812cf-104">PowerShell 7,0 är en utgåva med öppen källkod, plattforms oberoende plattform (Windows, macOS och Linux) av PowerShell, som är byggd för att hantera heterogena miljöer och hybrid moln.</span><span class="sxs-lookup"><span data-stu-id="812cf-104">PowerShell 7.0 is an open-source, cross-platform (Windows, macOS, and Linux) edition of PowerShell, built to manage heterogeneous environments and hybrid cloud.</span></span>

<span data-ttu-id="812cf-105">I den här versionen har vi introducerat ett antal nya funktioner, bland annat:</span><span class="sxs-lookup"><span data-stu-id="812cf-105">In this release, we're introducing a number of new features, including:</span></span>

- <span data-ttu-id="812cf-106">Pipeline-parallellisering med `ForEach-Object -Parallel`</span><span class="sxs-lookup"><span data-stu-id="812cf-106">Pipeline parallelization with `ForEach-Object -Parallel`</span></span>
- <span data-ttu-id="812cf-107">Nya operatorer:</span><span class="sxs-lookup"><span data-stu-id="812cf-107">New operators:</span></span>
  - <span data-ttu-id="812cf-108">Ternär operator: `a ? b : c`</span><span class="sxs-lookup"><span data-stu-id="812cf-108">Ternary operator: `a ? b : c`</span></span>
  - <span data-ttu-id="812cf-109">Operatorer för pipeline-kedjan: `||` och `&&`</span><span class="sxs-lookup"><span data-stu-id="812cf-109">Pipeline chain operators: `||` and `&&`</span></span>
  - <span data-ttu-id="812cf-110">Null-villkorliga operatorer: `??` och `??=`</span><span class="sxs-lookup"><span data-stu-id="812cf-110">Null conditional operators: `??` and `??=`</span></span>
- <span data-ttu-id="812cf-111">En förenklad och dynamisk felvy och `Get-Error` cmdlet för enklare undersökning av fel</span><span class="sxs-lookup"><span data-stu-id="812cf-111">A simplified and dynamic error view and `Get-Error` cmdlet for easier investigation of errors</span></span>
- <span data-ttu-id="812cf-112">Ett kompatibilitetsläge som gör det möjligt för användare att importera moduler i en implicit Windows PowerShell-session</span><span class="sxs-lookup"><span data-stu-id="812cf-112">A compatibility layer that enables users to import modules in an implicit Windows PowerShell session</span></span>
- <span data-ttu-id="812cf-113">Automatiska nya versions meddelanden</span><span class="sxs-lookup"><span data-stu-id="812cf-113">Automatic new version notifications</span></span>
- <span data-ttu-id="812cf-114">Möjligheten att anropa DSC-resurser direkt från PowerShell 7 (experimentell)</span><span class="sxs-lookup"><span data-stu-id="812cf-114">The ability to invoke DSC resources directly from PowerShell 7 (experimental)</span></span>

<span data-ttu-id="812cf-115">Om du vill se en fullständig lista över funktioner och korrigeringar går du till [ChangeLogs](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.0.md).</span><span class="sxs-lookup"><span data-stu-id="812cf-115">To see a full list of features and fixes, see the [changelogs](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.0.md).</span></span>

## <a name="where-can-i-install-powershell"></a><span data-ttu-id="812cf-116">Var kan jag installera PowerShell?</span><span class="sxs-lookup"><span data-stu-id="812cf-116">Where can I install PowerShell?</span></span>

<span data-ttu-id="812cf-117">PowerShell 7 har för närvarande stöd för följande operativ system på x64, inklusive:</span><span class="sxs-lookup"><span data-stu-id="812cf-117">PowerShell 7 currently supports the following operating systems on x64, including:</span></span>

- <span data-ttu-id="812cf-118">Windows 8,1 och 10</span><span class="sxs-lookup"><span data-stu-id="812cf-118">Windows 8.1, and 10</span></span>
- <span data-ttu-id="812cf-119">Windows Server 2012, 2012 R2, 2016 och 2019</span><span class="sxs-lookup"><span data-stu-id="812cf-119">Windows Server 2012, 2012 R2, 2016, and 2019</span></span>
- <span data-ttu-id="812cf-120">macOS 10.13 +</span><span class="sxs-lookup"><span data-stu-id="812cf-120">macOS 10.13+</span></span>
- <span data-ttu-id="812cf-121">Red Hat Enterprise Linux (RHEL)/CentOS 7</span><span class="sxs-lookup"><span data-stu-id="812cf-121">Red Hat Enterprise Linux (RHEL) / CentOS 7</span></span>
- <span data-ttu-id="812cf-122">Fedora 30 +</span><span class="sxs-lookup"><span data-stu-id="812cf-122">Fedora 30+</span></span>
- <span data-ttu-id="812cf-123">Debian 9</span><span class="sxs-lookup"><span data-stu-id="812cf-123">Debian 9</span></span>
- <span data-ttu-id="812cf-124">Ubuntu LTS 16.04 +</span><span class="sxs-lookup"><span data-stu-id="812cf-124">Ubuntu LTS 16.04+</span></span>
- <span data-ttu-id="812cf-125">Alpine Linux 3.8 +</span><span class="sxs-lookup"><span data-stu-id="812cf-125">Alpine Linux 3.8+</span></span>

<span data-ttu-id="812cf-126">Dessutom stöder PowerShell 7,0 ARM32 och ARM64 varianter för Debian, Ubuntu och ARM64 Alpine Linux.</span><span class="sxs-lookup"><span data-stu-id="812cf-126">Additionally, PowerShell 7.0 supports ARM32 and ARM64 flavors of Debian, Ubuntu, and ARM64 Alpine Linux.</span></span>

<span data-ttu-id="812cf-127">Kontrol lera installations anvisningarna för det önskade operativ systemet [Windows](/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7), [MacOS](/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-7)eller [Linux](/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="812cf-127">Check the installation instructions for your preferred operating system [Windows](/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7), [macOS](/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-7), or [Linux](/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7).</span></span>

<span data-ttu-id="812cf-128">Även om den inte stöds officiellt har communityn även tillhandahållit paket för [båge](https://aur.archlinux.org/packages/powershell/) och Kali Linux.</span><span class="sxs-lookup"><span data-stu-id="812cf-128">While not officially supported, the community has also provided packages for [Arch](https://aur.archlinux.org/packages/powershell/) and Kali Linux.</span></span>

> [!NOTE]
> <span data-ttu-id="812cf-129">Debian 10 och CentOS 8 stöder för närvarande inte WinRM-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="812cf-129">Debian 10 and CentOS 8 currently do not support WinRM remoting.</span></span> <span data-ttu-id="812cf-130">Mer information om hur du konfigurerar SSH-baserad fjärr kommunikation finns i [PowerShell-fjärrkommunikation via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="812cf-130">For details on setting up SSH-based remoting, see [PowerShell Remoting over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core?view=powershell-7).</span></span>

<span data-ttu-id="812cf-131">Mer uppdaterad information om operativ system och support livs cykel som stöds finns i [PowerShell-Supportens livs cykel](/powershell/scripting/powershell-support-lifecycle?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="812cf-131">For more up-to-date information about supported operating systems and support lifecycle, see the [PowerShell Support Lifecycle](/powershell/scripting/powershell-support-lifecycle?view=powershell-7).</span></span>

## <a name="running-powershell-7"></a><span data-ttu-id="812cf-132">Kör PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="812cf-132">Running PowerShell 7</span></span>

<span data-ttu-id="812cf-133">PowerShell 7 installeras i en ny katalog och körs sida vid sida med Windows PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="812cf-133">PowerShell 7 installs to a new directory and runs side-by-side with Windows PowerShell 5.1.</span></span> <span data-ttu-id="812cf-134">För PowerShell Core 6. x är PowerShell 7 en uppgradering på plats som tar bort PowerShell Core 6. x.</span><span class="sxs-lookup"><span data-stu-id="812cf-134">For PowerShell Core 6.x, PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>

- <span data-ttu-id="812cf-135">PowerShell 7 installeras för att `%programfiles%\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="812cf-135">PowerShell 7 is installed to `%programfiles%\PowerShell\7`</span></span>
- <span data-ttu-id="812cf-136">Mappen `%programfiles%\PowerShell\7` läggs till i `$env:PATH`</span><span class="sxs-lookup"><span data-stu-id="812cf-136">The `%programfiles%\PowerShell\7` folder is added to `$env:PATH`</span></span>

<span data-ttu-id="812cf-137">PowerShell 7 installations paket uppgraderar tidigare versioner av PowerShell Core 6. x:</span><span class="sxs-lookup"><span data-stu-id="812cf-137">The PowerShell 7 installer packages upgrade previous versions of PowerShell Core 6.x:</span></span>

- <span data-ttu-id="812cf-138">PowerShell Core 6. x i Windows: `%programfiles%\PowerShell\6` ersätts av `%programfiles%\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="812cf-138">PowerShell Core 6.x on Windows: `%programfiles%\PowerShell\6` is replaced by `%programfiles%\PowerShell\7`</span></span>
- <span data-ttu-id="812cf-139">Linux: `/opt/microsoft/powershell/6` ersätts av `/opt/microsoft/powershell/7`</span><span class="sxs-lookup"><span data-stu-id="812cf-139">Linux: `/opt/microsoft/powershell/6` is replaced by `/opt/microsoft/powershell/7`</span></span>
- <span data-ttu-id="812cf-140">macOS: `/usr/local/microsoft/powershell/6` ersätts av `/usr/local/microsoft/powershell/7`</span><span class="sxs-lookup"><span data-stu-id="812cf-140">macOS: `/usr/local/microsoft/powershell/6` is replaced by `/usr/local/microsoft/powershell/7`</span></span>

> [!NOTE]
> <span data-ttu-id="812cf-141">I Windows PowerShell heter den körbara filen för att starta PowerShell `powershell.exe`.</span><span class="sxs-lookup"><span data-stu-id="812cf-141">In Windows PowerShell, the executable to launch PowerShell is named `powershell.exe`.</span></span> <span data-ttu-id="812cf-142">I version 6 och senare ändras den körbara filen så att den stöder sida-vid-sida-körning.</span><span class="sxs-lookup"><span data-stu-id="812cf-142">In version 6 and above, the executable is changed to support side-by-side execution.</span></span> <span data-ttu-id="812cf-143">Den nya körbara filen för att starta PowerShell 7 är `pwsh.exe`.</span><span class="sxs-lookup"><span data-stu-id="812cf-143">The new executable to launch PowerShell 7 is `pwsh.exe`.</span></span> <span data-ttu-id="812cf-144">För hands versioner kommer att finnas kvar på plats som `pwsh-preview` i stället för `pwsh` under 7-Preview-katalogen.</span><span class="sxs-lookup"><span data-stu-id="812cf-144">Preview builds will remain in-place as `pwsh-preview` instead of `pwsh` under the 7-preview directory.</span></span>

## <a name="improved-backwards-compatibility-with-windows-powershell"></a><span data-ttu-id="812cf-145">Förbättrad bakåtkompatibilitet med Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="812cf-145">Improved backwards compatibility with Windows PowerShell</span></span>

<span data-ttu-id="812cf-146">PowerShell 7,0 markerar en flytta en till .NET Core 3,1, vilket möjliggör betydligt mer bakåtkompatibilitet med befintliga Windows PowerShell-moduler.</span><span class="sxs-lookup"><span data-stu-id="812cf-146">PowerShell 7.0 marks a move a to .NET Core 3.1, enabling significantly more backwards compatibility with existing Windows PowerShell modules.</span></span> <span data-ttu-id="812cf-147">Detta inkluderar många moduler i Windows som kräver GUI-funktioner som `Out-GridView` och `Show-Command`, samt många roll hanterings moduler som levereras som en del av Windows.</span><span class="sxs-lookup"><span data-stu-id="812cf-147">This includes many modules on Windows that require GUI functionality like `Out-GridView` and `Show-Command`, as well as many role management modules that ship as part of Windows.</span></span>

<span data-ttu-id="812cf-148">För Windows läggs en ny växel parameter **UseWindowsPowerShell** till `Import-Module`.</span><span class="sxs-lookup"><span data-stu-id="812cf-148">For Windows, a new switch parameter **UseWindowsPowerShell** is added to `Import-Module`.</span></span> <span data-ttu-id="812cf-149">Den här växeln skapar en proxy-modul i PowerShell 7 som använder en lokal Windows PowerShell-process för att implicit köra alla cmdletar som finns i modulen.</span><span class="sxs-lookup"><span data-stu-id="812cf-149">This switch creates a proxy module in PowerShell 7 that uses a local Windows PowerShell process to implicitly run any cmdlets contained in that module.</span></span> <span data-ttu-id="812cf-150">Mer information om [import-module](/powershell/module/microsoft.powershell.core/import-module?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="812cf-150">For more information on [Import-Module](/powershell/module/microsoft.powershell.core/import-module?view=powershell-7).</span></span>

<span data-ttu-id="812cf-151">Mer information om vilka Microsoft-moduler som fungerar med PowerShell 7,0 finns i [tabellen](https://aka.ms/PSModuleCompat)för kompatibilitetsmodulen.</span><span class="sxs-lookup"><span data-stu-id="812cf-151">For more information on which Microsoft modules work with PowerShell 7.0, see the [Module Compatibility Table](https://aka.ms/PSModuleCompat).</span></span>

## <a name="parallel-execution-added-to-foreach-object"></a><span data-ttu-id="812cf-152">Parallell körning har lagts till i Körningsbegäran – objekt</span><span class="sxs-lookup"><span data-stu-id="812cf-152">Parallel execution added to ForEach-Object</span></span>

<span data-ttu-id="812cf-153">`ForEach-Object`-cmdleten, som itererar objekt i en samling, har nu inbyggd parallellitet med den nya **parallella** parametern.</span><span class="sxs-lookup"><span data-stu-id="812cf-153">The `ForEach-Object` cmdlet, which iterates items in a collection, now has built-in parallelism with the new **Parallel** parameter.</span></span>

<span data-ttu-id="812cf-154">Som standard använder parallella skript block den aktuella arbets katalogen för den anropare som startade parallell aktiviteterna.</span><span class="sxs-lookup"><span data-stu-id="812cf-154">By default, parallel script blocks use the current working directory of the caller that started the parallel tasks.</span></span>

<span data-ttu-id="812cf-155">I det här exemplet hämtas logg poster 50 000 från 5 system loggar på en lokal Windows-dator:</span><span class="sxs-lookup"><span data-stu-id="812cf-155">This example retrieves 50,000 log entries from 5 system logs on a local Windows machine:</span></span>

```powershell
$logNames = 'Security','Application','System','Windows PowerShell','Microsoft-Windows-Store/Operational'

$logEntries = $logNames | ForEach-Object -Parallel {
    Get-WinEvent -LogName $_ -MaxEvents 10000
} -ThrottleLimit 5

$logEntries.Count

50000
```

<span data-ttu-id="812cf-156">Den **parallella** parametern anger det skript block som körs parallellt för varje logg namn.</span><span class="sxs-lookup"><span data-stu-id="812cf-156">The **Parallel** parameter specifies the script block that is run in parallel for each input log name.</span></span>

<span data-ttu-id="812cf-157">Den nya **ThrottleLimit** -parametern begränsar antalet skript block som körs parallellt vid en specifik tidpunkt.</span><span class="sxs-lookup"><span data-stu-id="812cf-157">The new **ThrottleLimit** parameter limits the number of script blocks running in parallel at a given time.</span></span> <span data-ttu-id="812cf-158">Standardvärdet är 5.</span><span class="sxs-lookup"><span data-stu-id="812cf-158">The default is 5.</span></span>

<span data-ttu-id="812cf-159">Använd variabeln `$_` för att representera det aktuella indatamängdet i-skript blocket.</span><span class="sxs-lookup"><span data-stu-id="812cf-159">Use the `$_` variable to represent the current input object in the script block.</span></span> <span data-ttu-id="812cf-160">Använd `$using:`s omfång för att skicka variabel referenser till skript blocket som körs.</span><span class="sxs-lookup"><span data-stu-id="812cf-160">Use the `$using:` scope to pass variable references to the running script block.</span></span>

<span data-ttu-id="812cf-161">Mer information om [solobjekt](/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="812cf-161">For more information about [ForEach-Object](/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7).</span></span>

## <a name="ternary-operator"></a><span data-ttu-id="812cf-162">Ternär operator</span><span class="sxs-lookup"><span data-stu-id="812cf-162">Ternary operator</span></span>

<span data-ttu-id="812cf-163">PowerShell 7,0 introducerar en ternär operator som beter sig som ett förenklat `if-else`-uttryck.</span><span class="sxs-lookup"><span data-stu-id="812cf-163">PowerShell 7.0 introduces a ternary operator which behaves like a simplified `if-else` statement.</span></span>
<span data-ttu-id="812cf-164">PowerShell: s ternära operator modelleras noggrant från C# ternär operatörs syntax:</span><span class="sxs-lookup"><span data-stu-id="812cf-164">PowerShell's ternary operator is closely modeled from the C# ternary operator syntax:</span></span>

```
<condition> ? <if-true> : <if-false>
```

<span data-ttu-id="812cf-165">Villkors uttrycket utvärderas alltid och resultatet konverteras till ett **booleskt värde** för att avgöra vilken gren som utvärderas härnäst:</span><span class="sxs-lookup"><span data-stu-id="812cf-165">The condition-expression is always evaluated and its result converted to a **Boolean** to determine which branch is evaluated next:</span></span>

- <span data-ttu-id="812cf-166">`<if-true>` uttryck körs om `<condition>`s uttrycket är sant</span><span class="sxs-lookup"><span data-stu-id="812cf-166">The `<if-true>` expression is executed if the `<condition>` expression is true</span></span>
- <span data-ttu-id="812cf-167">`<if-false>`-uttrycket körs om `<condition>`-uttrycket är falskt</span><span class="sxs-lookup"><span data-stu-id="812cf-167">The `<if-false>` expression is executed if the `<condition>` expression is false</span></span>

<span data-ttu-id="812cf-168">Exempel:</span><span class="sxs-lookup"><span data-stu-id="812cf-168">For example:</span></span>

```powershell
$message = (Test-Path $path) ? "Path exists" : "Path not found"
```

<span data-ttu-id="812cf-169">I det här exemplet visas **sökvägen** , om sökvägen finns.</span><span class="sxs-lookup"><span data-stu-id="812cf-169">In this example, if the path exists, then **Path exists** is displayed.</span></span> <span data-ttu-id="812cf-170">Om sökvägen inte finns visas **inte sökvägen** .</span><span class="sxs-lookup"><span data-stu-id="812cf-170">If the path does not exist, then **Path not found** is displayed.</span></span>

<span data-ttu-id="812cf-171">För mer information [om](/powershell/module/microsoft.powershell.core/about/about_if?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="812cf-171">For more information [About If](/powershell/module/microsoft.powershell.core/about/about_if?view=powershell-7).</span></span>

## <a name="pipeline-chain-operators"></a><span data-ttu-id="812cf-172">Operatorer för pipeline-kedjan</span><span class="sxs-lookup"><span data-stu-id="812cf-172">Pipeline chain operators</span></span>

<span data-ttu-id="812cf-173">PowerShell 7 implementerar `&&` och `||`-operatörer för att villkorligt kedja pipelines.</span><span class="sxs-lookup"><span data-stu-id="812cf-173">PowerShell 7 implements the `&&` and `||` operators to conditionally chain pipelines.</span></span> <span data-ttu-id="812cf-174">Dessa operatörer är kända i PowerShell som "pipelines kedje operatorer", och liknar och, eller listor i gränssnitt som **bash** och **zsh**, samt villkorsstyrda bearbetnings symboler i Windows Command Shell (**cmd. exe**).</span><span class="sxs-lookup"><span data-stu-id="812cf-174">These operators are known in PowerShell as "pipeline chain operators", and are similar to AND and OR lists in shells like **Bash** and **Zsh**, as well as conditional processing symbols in the Windows Command Shell (**cmd.exe**).</span></span>

<span data-ttu-id="812cf-175">`&&` operatören kör den högra pipelinen om den vänstra pipelinen lyckades.</span><span class="sxs-lookup"><span data-stu-id="812cf-175">The `&&` operator executes the right-hand pipeline, if the left-hand pipeline succeeded.</span></span> <span data-ttu-id="812cf-176">I motsatt fall kör `||`-operatören den högra pipelinen om den vänstra pipelinen misslyckades.</span><span class="sxs-lookup"><span data-stu-id="812cf-176">Conversely, the `||` operator executes the right-hand pipeline if the left-hand pipeline failed.</span></span>

> [!NOTE]
> <span data-ttu-id="812cf-177">Dessa operatörer använder `$?` och `$LASTEXITCODE` variabler för att avgöra om en pipeline misslyckades.</span><span class="sxs-lookup"><span data-stu-id="812cf-177">These operators use the `$?` and `$LASTEXITCODE` variables to determine if a pipeline failed.</span></span> <span data-ttu-id="812cf-178">På så sätt kan du använda dem med inbyggda kommandon och inte bara med cmdlets eller functions.</span><span class="sxs-lookup"><span data-stu-id="812cf-178">This allows you to use them with native commands and not just with cmdlets or functions.</span></span>

<span data-ttu-id="812cf-179">Här är det första kommandot som slutförs och det andra kommandot körs:</span><span class="sxs-lookup"><span data-stu-id="812cf-179">Here, the first command succeeds and the second command is executed:</span></span>

```powershell
Write-Output 'First' && Write-Output 'Second'
```

```Output
First
Second
```

<span data-ttu-id="812cf-180">Det första kommandot Miss lyckas, det andra körs inte:</span><span class="sxs-lookup"><span data-stu-id="812cf-180">Here, the first command fails, the second is not executed:</span></span>

```powershell
Write-Error 'Bad' && Write-Output 'Second'
```

```Output
Write-Error: Bad
```

<span data-ttu-id="812cf-181">Det första kommandot slutförs, det andra kommandot utförs inte:</span><span class="sxs-lookup"><span data-stu-id="812cf-181">Here, the first command succeeds, the second command is not executed:</span></span>

```powershell
Write-Output 'First' || Write-Output 'Second'
```

```Output
First
```

<span data-ttu-id="812cf-182">Det första kommandot Miss lyckas, så det andra kommandot körs:</span><span class="sxs-lookup"><span data-stu-id="812cf-182">Here, the first command fails, so the second command is executed:</span></span>

```powershell
Write-Error 'Bad' || Write-Output 'Second'
```

```Output
Write-Error 'Bad'
Second
```

<span data-ttu-id="812cf-183">Mer information [om operatorer för pipeline-kedjan](/powershell/module/microsoft.powershell.core/about/about_pipeline_chain_operators?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="812cf-183">For more information [About Pipeline Chain Operators](/powershell/module/microsoft.powershell.core/about/about_pipeline_chain_operators?view=powershell-7).</span></span>

## <a name="null-coalescing-assignment-and-conditional-operators"></a><span data-ttu-id="812cf-184">Null-sammanslagning, tilldelning och villkorliga operatorer</span><span class="sxs-lookup"><span data-stu-id="812cf-184">Null-coalescing, assignment, and conditional operators</span></span>

<span data-ttu-id="812cf-185">PowerShell 7 innehåller null-sammanslagnings operator `??`, null villkorlig tilldelning `??=`och null-operatörer för villkorliga medlemmar `?.` och `?[]`.</span><span class="sxs-lookup"><span data-stu-id="812cf-185">PowerShell 7 includes Null coalescing operator `??`, Null conditional assignment `??=`, and Null conditional member access operators `?.` and `?[]`.</span></span>

### <a name="null-coalescing-operator-"></a><span data-ttu-id="812cf-186">Null-sammanslagnings operator??</span><span class="sxs-lookup"><span data-stu-id="812cf-186">Null-coalescing Operator ??</span></span>

<span data-ttu-id="812cf-187">Operatorn null-sammanslagning `??` returnerar värdet för den vänstra operanden om den inte är null.</span><span class="sxs-lookup"><span data-stu-id="812cf-187">The null-coalescing operator `??` returns the value of its left-hand operand if it isn't null.</span></span>
<span data-ttu-id="812cf-188">Annars utvärderar den högra operanden och returnerar resultatet.</span><span class="sxs-lookup"><span data-stu-id="812cf-188">Otherwise, it evaluates the right-hand operand and returns its result.</span></span> <span data-ttu-id="812cf-189">`??` operatorn utvärderar inte sin högra operand om den vänstra operanden utvärderas till icke-null.</span><span class="sxs-lookup"><span data-stu-id="812cf-189">The `??` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

```powershell
$x = $null
$x ?? 100
100
```

<span data-ttu-id="812cf-190">I följande exempel kommer den högra operanden inte att utvärderas:</span><span class="sxs-lookup"><span data-stu-id="812cf-190">In the following example, the right-hand operand won't be evaluated:</span></span>

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ?? (Get-Date).ToShortDateString()
1/10/2020
```

### <a name="null-conditional-assignment-operator-"></a><span data-ttu-id="812cf-191">Null villkorlig tilldelnings operator? =</span><span class="sxs-lookup"><span data-stu-id="812cf-191">Null conditional assignment operator ??=</span></span>

<span data-ttu-id="812cf-192">Operatorn null för villkorlig tilldelning `??=` tilldelar värdet för dess högra operand till sin vänstra operand endast om den vänstra operanden utvärderar till null.</span><span class="sxs-lookup"><span data-stu-id="812cf-192">The null conditional assignment operator `??=` assigns the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to null.</span></span> <span data-ttu-id="812cf-193">`??=` operatorn utvärderar inte sin högra operand om den vänstra operanden utvärderas till icke-null.</span><span class="sxs-lookup"><span data-stu-id="812cf-193">The `??=` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

```powershell
$x = $null
$x ??= 100
$x
100
```

<span data-ttu-id="812cf-194">I följande exempel kommer den högra operanden inte att utvärderas:</span><span class="sxs-lookup"><span data-stu-id="812cf-194">In the following example, the right-hand operand won't be evaluated:</span></span>

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ??= (Get-Date).ToShortDateString()
1/10/2020
```

### <a name="null-conditional-member-access-operators--and--experimental"></a><span data-ttu-id="812cf-195">Null villkorliga medlemmars åtkomst operatörer?.</span><span class="sxs-lookup"><span data-stu-id="812cf-195">Null conditional member access operators ?.</span></span> <span data-ttu-id="812cf-196">särskilt? [] (Experimentell)</span><span class="sxs-lookup"><span data-stu-id="812cf-196">and ?[] (Experimental)</span></span>

> [!NOTE]
> <span data-ttu-id="812cf-197">Det här är en experimentell funktion som heter **PSNullConditionalOperators**.</span><span class="sxs-lookup"><span data-stu-id="812cf-197">This is an experimental feature named **PSNullConditionalOperators**.</span></span> <span data-ttu-id="812cf-198">Läs mer [om experimentella funktioner](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="812cf-198">Learn more [About Experimental Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7).</span></span>

<span data-ttu-id="812cf-199">En villkorlig operator för null tillåter åtkomst till medlemmar, `?.`eller element, `?[]`, till operanden endast om denna operand utvärderar till icke-null. annars returnerar den null.</span><span class="sxs-lookup"><span data-stu-id="812cf-199">A null conditional operator permits member access, `?.`, or element access, `?[]`, to its operand only if that operand evaluates to non-null; otherwise, it returns null.</span></span>

> [!NOTE]
> <span data-ttu-id="812cf-200">Eftersom PowerShell tillåter `?` att ingå i variabel namnet, krävs formell specifikation av variabel namnet för att använda dessa operatorer.</span><span class="sxs-lookup"><span data-stu-id="812cf-200">Since PowerShell allows `?` to be part of the variable name, formal specification of the variable name is required for using these operators.</span></span> <span data-ttu-id="812cf-201">Därför måste du använda `{}` runt variabel namnen som `${a}` eller när `?` är en del av variabeln Name `${a?}`.</span><span class="sxs-lookup"><span data-stu-id="812cf-201">So it is required to use `{}` around the variable names like `${a}` or when `?` is part of the variable name `${a?}`.</span></span>

<span data-ttu-id="812cf-202">I följande exempel returneras värdet för medlems egenskaps **status** :</span><span class="sxs-lookup"><span data-stu-id="812cf-202">In the following example, the value of the member property **Status** is returned:</span></span>

```powershell
$Service = Get-Service -Name 'bits'
${Service}?.status
Stopped
```

<span data-ttu-id="812cf-203">Följande exempel kommer att returnera Null, utan att försöka komma åt medlems namnets **status**:</span><span class="sxs-lookup"><span data-stu-id="812cf-203">The following example will return null, without trying to access the member name **Status**:</span></span>

```powershell
$service = $Null
${Service}?.status
```

<span data-ttu-id="812cf-204">På samma sätt returneras värdet för elementet när du använder `?[]`:</span><span class="sxs-lookup"><span data-stu-id="812cf-204">Similarly, using `?[]`, the value of the element will be returned:</span></span>

```powershell
$a = 1..10
${a}?[0]
1
```

<span data-ttu-id="812cf-205">När operanden är null returneras inte elementet och null returneras:</span><span class="sxs-lookup"><span data-stu-id="812cf-205">And when the operand is null, the element isn't accessed and null is returned:</span></span>

```powershell
$a = $null
${a}?[0]
```

<span data-ttu-id="812cf-206">Mer information [About_Operators](/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="812cf-206">For more information [About_Operators](/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-7).</span></span>

## <a name="new-view-conciseview-and-cmdlet-get-error"></a><span data-ttu-id="812cf-207">New View ConciseView och cmdlet Get-Error</span><span class="sxs-lookup"><span data-stu-id="812cf-207">New view ConciseView and cmdlet Get-Error</span></span>

<span data-ttu-id="812cf-208">Visningen av fel meddelanden har förbättrats för att förbättra läsbarheten för interaktiva och skript fel med en ny standardvy **ConciseView**.</span><span class="sxs-lookup"><span data-stu-id="812cf-208">The display of error messages has been improved to enhance the readability of interactive and script errors with a new default view **ConciseView**.</span></span> <span data-ttu-id="812cf-209">Vyerna är användare som kan väljas via variabeln Preference `$ErrorView`.</span><span class="sxs-lookup"><span data-stu-id="812cf-209">The views are user-selectable through the preference variable `$ErrorView`.</span></span>

<span data-ttu-id="812cf-210">Om ett fel inte är från ett skript eller ett parsningsfel i **ConciseView**, är det ett enda rad fel meddelande:</span><span class="sxs-lookup"><span data-stu-id="812cf-210">With **ConciseView**, if an error is not from a script or parser error, then it's a single line error message:</span></span>

```powershell
Get-Childitem -Path c:\NotReal
```

```Output
Get-ChildItem: Cannot find path 'C:\NotReal' because it does not exist
```

<span data-ttu-id="812cf-211">Om felet inträffar under skript körningen eller är ett parsningsfel returnerar PowerShell ett fel meddelande i flera rader som innehåller felet, en pekare och ett fel meddelande som visar var felet finns på raden.</span><span class="sxs-lookup"><span data-stu-id="812cf-211">If the error occurs during script execution or is a parsing error, PowerShell returns a multiline error message that contains the error, a pointer and error message showing where the error is in that line.</span></span> <span data-ttu-id="812cf-212">Om terminalen inte har stöd för ANSI-färgs escape-sekvenser (VT100) visas inte färger.</span><span class="sxs-lookup"><span data-stu-id="812cf-212">If the terminal doesn't support ANSI color escape sequences (VT100), then colors are not displayed.</span></span>

![Fel vid visning från ett skript](./media/What-s-New-in-PowerShell-70/myscript-error.png)

<span data-ttu-id="812cf-214">Standardvyn i PowerShell 7 är **ConciseView**.</span><span class="sxs-lookup"><span data-stu-id="812cf-214">The default view in PowerShell 7 is **ConciseView**.</span></span> <span data-ttu-id="812cf-215">Den tidigare standardvyn var **NormalView** och användaren kan välja variabeln genom att ställa in variabeln Preference `$ErrorView`.</span><span class="sxs-lookup"><span data-stu-id="812cf-215">The previous default view was **NormalView** and is user selectable by setting the preference variable `$ErrorView`.</span></span>

```powershell
$ErrorView = 'NormalView' # Sets the error view to NormalView
$ErrorView = 'ConciseView' # Sets the error view to ConciseView
```

> [!NOTE]
> <span data-ttu-id="812cf-216">En ny egenskaps- **ErrorAccentColor** läggs till i `$Host.PrivateData` för att stödja ändring av tilläggs färgen för fel meddelandet.</span><span class="sxs-lookup"><span data-stu-id="812cf-216">A new property **ErrorAccentColor** is added to `$Host.PrivateData` to support changing the accent color of the error message.</span></span>

<span data-ttu-id="812cf-217">En ny cmdlet `Get-Error` ger fullständig detaljerad vy över det fullständigt kvalificerade felet när du vill.</span><span class="sxs-lookup"><span data-stu-id="812cf-217">A new cmdlet `Get-Error` provides complete detailed view of the fully qualified error when desired.</span></span>
<span data-ttu-id="812cf-218">Som standard visar cmdleten fullständig information, inklusive inre undantag, av det senaste felet som inträffat.</span><span class="sxs-lookup"><span data-stu-id="812cf-218">By default the cmdlet displays the full details, including inner exceptions, of the last error that occurred.</span></span>

![Visa från get-Error](./media/What-s-New-in-PowerShell-70/myscript-geterror.png)

<span data-ttu-id="812cf-220">`Get-Error`-cmdleten stöder inmatade från pipelinen med hjälp av den inbyggda variabeln `$Error`.</span><span class="sxs-lookup"><span data-stu-id="812cf-220">The `Get-Error` cmdlet supports input from the pipeline using the built-in variable `$Error`.</span></span>
<span data-ttu-id="812cf-221">`Get-Error` visar alla skickas-fel.</span><span class="sxs-lookup"><span data-stu-id="812cf-221">`Get-Error` displays all piped errors.</span></span>

```powershell
$Error | Get-Error
```

<span data-ttu-id="812cf-222">`Get-Error`-cmdleten stöder den **senaste** parametern, så att du kan ange hur många fel från den aktuella sessionen som du vill visa.</span><span class="sxs-lookup"><span data-stu-id="812cf-222">The `Get-Error` cmdlet supports the **Newest** parameter, allowing you to specify how many errors from the current session you wish displayed.</span></span>

```powershell
Get-Error -Newest 3 # Displays the lst three errors that occurred in the session
```

<span data-ttu-id="812cf-223">För ytterligare information om [Get-Error](/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="812cf-223">For more information about [Get-Error](/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7).</span></span>

## <a name="new-version-notification"></a><span data-ttu-id="812cf-224">Nytt versions meddelande</span><span class="sxs-lookup"><span data-stu-id="812cf-224">New version notification</span></span>

<span data-ttu-id="812cf-225">PowerShell 7 använder uppdaterings meddelanden för att varna användarna om att det finns uppdateringar till PowerShell.</span><span class="sxs-lookup"><span data-stu-id="812cf-225">PowerShell 7 uses update notifications to alert users to the existence of updates to PowerShell.</span></span>
<span data-ttu-id="812cf-226">En gång per dag frågar PowerShell en online tjänst för att avgöra om det finns en nyare version.</span><span class="sxs-lookup"><span data-stu-id="812cf-226">Once per day, PowerShell queries an online service to determine if a newer version is available.</span></span>

> [!NOTE]
> <span data-ttu-id="812cf-227">Uppdaterings kontrollen sker under den första sessionen under en viss 24-timmarsperiod.</span><span class="sxs-lookup"><span data-stu-id="812cf-227">The update check happens during the first session in a given 24-hour period.</span></span> <span data-ttu-id="812cf-228">Av prestanda skäl börjar uppdaterings kontrollen 3 sekunder efter att sessionen har börjat.</span><span class="sxs-lookup"><span data-stu-id="812cf-228">For performance reasons, the update check starts 3 seconds after the session begins.</span></span> <span data-ttu-id="812cf-229">Meddelandet visas bara i början av efterföljande sessioner.</span><span class="sxs-lookup"><span data-stu-id="812cf-229">The notification is shown only on the start of subsequent sessions.</span></span>

<span data-ttu-id="812cf-230">Som standard prenumererar PowerShell på en av två olika meddelande kanaler, beroende på dess version/gren.</span><span class="sxs-lookup"><span data-stu-id="812cf-230">By default, PowerShell subscribes to one of two different notification channels depending on its version/branch.</span></span> <span data-ttu-id="812cf-231">Allmänt tillgängliga (GA) versioner av PowerShell returnerar endast aviseringar för uppdaterade GA-versioner.</span><span class="sxs-lookup"><span data-stu-id="812cf-231">Supported, Generally Available (GA) versions of PowerShell only return notifications for updated GA releases.</span></span> <span data-ttu-id="812cf-232">För hands versions-och Release Candidate (RC)-versioner meddelar uppdateringar om uppdateringar för Preview-, RC-och GA-versioner.</span><span class="sxs-lookup"><span data-stu-id="812cf-232">Preview and Release Candidate (RC) releases notify of updates to preview, RC, and GA releases.</span></span>

<span data-ttu-id="812cf-233">Du kan ändra beteendet för uppdaterings aviseringar med hjälp av `$Env:POWERSHELL_UPDATECHECK`-miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="812cf-233">The update notification behavior can be changed using the `$Env:POWERSHELL_UPDATECHECK` environment variable.</span></span> <span data-ttu-id="812cf-234">Följande värden stöds:</span><span class="sxs-lookup"><span data-stu-id="812cf-234">The following values are supported:</span></span>

- <span data-ttu-id="812cf-235">**Standardvärdet** är detsamma som att definiera `$Env:POWERSHELL_UPDATECHECK`</span><span class="sxs-lookup"><span data-stu-id="812cf-235">**Default** is the same as not defining `$Env:POWERSHELL_UPDATECHECK`</span></span>
  - <span data-ttu-id="812cf-236">GA-versioner meddelar uppdateringar till GA-versioner</span><span class="sxs-lookup"><span data-stu-id="812cf-236">GA releases notify of updates to GA releases</span></span>
  - <span data-ttu-id="812cf-237">Preview/RC-versioner meddelar uppdateringar för GA och för hands versioner</span><span class="sxs-lookup"><span data-stu-id="812cf-237">Preview/RC releases notify of updates to GA and preview releases</span></span>
- <span data-ttu-id="812cf-238">**Off** inaktiverar funktionen för uppdaterings avisering</span><span class="sxs-lookup"><span data-stu-id="812cf-238">**Off** turns off the update notification feature</span></span>
- <span data-ttu-id="812cf-239">**LTS** meddelar bara uppdateringar till GA-versioner för långsiktig betjäning (LTS)</span><span class="sxs-lookup"><span data-stu-id="812cf-239">**LTS** only notifies of updates to long-term-servicing (LTS) GA releases</span></span>

> [!NOTE]
> <span data-ttu-id="812cf-240">Miljövariabeln `$Env:POWERSHELL_UPDATECHECK` finns inte förrän den har ställts in för första gången.</span><span class="sxs-lookup"><span data-stu-id="812cf-240">The environment variable `$Env:POWERSHELL_UPDATECHECK` does not exist until it is set for the first time.</span></span>

<span data-ttu-id="812cf-241">Så här anger du versions meddelandet endast för `LTS`-versioner:</span><span class="sxs-lookup"><span data-stu-id="812cf-241">To set the version notification for `LTS` releases only:</span></span>

```powershell
$Env:POWERSHELL_UPDATECHECK = 'LTS'
```

<span data-ttu-id="812cf-242">Så här ställer du in versions meddelandet till `Default` beteendet:</span><span class="sxs-lookup"><span data-stu-id="812cf-242">To set the version notification to the `Default` behavior:</span></span>

```powershell
$Env:POWERSHELL_UPDATECHECK = 'Default'
```

<span data-ttu-id="812cf-243">Mer information [om uppdaterings meddelanden](/powershell/module/microsoft.powershell.core/about/about_update_notifications?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="812cf-243">For more information [About Update Notifications](/powershell/module/microsoft.powershell.core/about/about_update_notifications?view=powershell-7).</span></span>

## <a name="new-dsc-resource-support-with-invoke-dscresource-experimental"></a><span data-ttu-id="812cf-244">Nytt stöd för DSC-resurser med Invoke-Dscresource Keyword Supports (experimentell)</span><span class="sxs-lookup"><span data-stu-id="812cf-244">New DSC Resource support with Invoke-DSCResource (Experimental)</span></span>

> [!NOTE]
> <span data-ttu-id="812cf-245">Det här är en experimentell funktion med namnet **PSDesiredStateConfiguration. InvokeDscResource**.</span><span class="sxs-lookup"><span data-stu-id="812cf-245">This is an experimental feature named **PSDesiredStateConfiguration.InvokeDscResource**.</span></span> <span data-ttu-id="812cf-246">Läs mer [om experimentella funktioner](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="812cf-246">Learn more [About Experimental Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7).</span></span>

<span data-ttu-id="812cf-247">`Invoke-DscResource`-cmdleten kör en metod för en angiven DSC-resurs (Desired State Configuration) för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="812cf-247">The `Invoke-DscResource` cmdlet runs a method of a specified PowerShell Desired State Configuration (DSC) resource.</span></span>

<span data-ttu-id="812cf-248">Den här cmdleten anropar en DSC-resurs direkt utan att skapa ett konfigurations dokument.</span><span class="sxs-lookup"><span data-stu-id="812cf-248">This cmdlet invokes a DSC resource directly, without creating a configuration document.</span></span> <span data-ttu-id="812cf-249">Med den här cmdleten kan konfigurations hanterings produkter hantera Windows eller Linux med hjälp av DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="812cf-249">Using this cmdlet, configuration management products can manage Windows or Linux by using DSC resources.</span></span> <span data-ttu-id="812cf-250">Den här cmdleten aktiverar även fel sökning av resurser när DSC-motorn körs med fel sökning aktiverat.</span><span class="sxs-lookup"><span data-stu-id="812cf-250">This cmdlet also enables debugging of resources when the DSC engine is running with debugging enabled.</span></span>

<span data-ttu-id="812cf-251">Det här kommandot anropar **set** -metoden för en resurs med namnet log och anger en **meddelande** egenskap.</span><span class="sxs-lookup"><span data-stu-id="812cf-251">This command invokes the **Set** method of a resource named Log and specifies a **Message** property.</span></span>

```powershell
Invoke-DscResource -Name Log -Method Set -ModuleName PSDesiredStateConfiguration -Property @{
  Message = 'Hello World'
}
```

<span data-ttu-id="812cf-252">Mer information om [Invoke-dscresource Keyword Supports](/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="812cf-252">For more information about [Invoke-DSCResource](/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7).</span></span>

## <a name="breaking-changes-and-improvements"></a><span data-ttu-id="812cf-253">Bryta ändringar och förbättringar</span><span class="sxs-lookup"><span data-stu-id="812cf-253">Breaking Changes and Improvements</span></span>

### <a name="breaking-changes"></a><span data-ttu-id="812cf-254">Icke-bakåtkompatibla ändringar</span><span class="sxs-lookup"><span data-stu-id="812cf-254">Breaking Changes</span></span>

- <span data-ttu-id="812cf-255">Gör uppdaterings aviseringar stöd för LTS och standard kanaler (#11132)</span><span class="sxs-lookup"><span data-stu-id="812cf-255">Make update notification support LTS and default channels (#11132)</span></span>
- <span data-ttu-id="812cf-256">Uppdatera test-anslutningen så att den fungerar som den som är i Windows PowerShell (#10697) (tack @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="812cf-256">Update Test-Connection to work more like the one in Windows PowerShell (#10697) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="812cf-257">Behåll $?</span><span class="sxs-lookup"><span data-stu-id="812cf-257">Preserve $?</span></span> <span data-ttu-id="812cf-258">för ParenExpression, under uttryck och ArrayExpression (#11040)</span><span class="sxs-lookup"><span data-stu-id="812cf-258">for ParenExpression, SubExpression and ArrayExpression (#11040)</span></span>
- <span data-ttu-id="812cf-259">Ange arbets katalog till den aktuella katalogen i Start-Job (#10920) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="812cf-259">Set working directory to current directory in Start-Job (#10920) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="812cf-260">Se till att $PSCulture konsekvent reflekterar ändringar i kulturen (#10138) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="812cf-260">Make $PSCulture consistently reflect in-session culture changes (#10138) (Thanks @iSazonov!)</span></span>

### <a name="engine-updates-and-fixes"></a><span data-ttu-id="812cf-261">Uppdateringar och korrigeringar för motorn</span><span class="sxs-lookup"><span data-stu-id="812cf-261">Engine Updates and Fixes</span></span>

- <span data-ttu-id="812cf-262">Förbättringar i Bryt punkts-API: er för fjärrscenarier (#11312)</span><span class="sxs-lookup"><span data-stu-id="812cf-262">Improvements in breakpoint APIs for remote scenarios (#11312)</span></span>
- <span data-ttu-id="812cf-263">Korrigera definitions läckor i PowerShell-klassen i en annan körnings utrymme (#11273)</span><span class="sxs-lookup"><span data-stu-id="812cf-263">Fix PowerShell class definition leaking into another Runspace (#11273)</span></span>
- <span data-ttu-id="812cf-264">Åtgärda en regression i formatering som orsakas av FirstOrDefault-primitiven som lagts till i 7.0.0-preview1 (#11258)</span><span class="sxs-lookup"><span data-stu-id="812cf-264">Fix a regression in formatting caused by the FirstOrDefault primitive added in 7.0.0-Preview1 (#11258)</span></span>
- <span data-ttu-id="812cf-265">Ytterligare Microsoft-moduler för att spåra i PS7 telemetri (#10751)</span><span class="sxs-lookup"><span data-stu-id="812cf-265">Additional Microsoft Modules to track in PS7 Telemetry (#10751)</span></span>
- <span data-ttu-id="812cf-266">Gör godkända funktioner icke-experimentella (#11303)</span><span class="sxs-lookup"><span data-stu-id="812cf-266">Make approved features non-experimental (#11303)</span></span>
- <span data-ttu-id="812cf-267">Uppdatera ConciseView för att använda TargetObject om det är tillämpligt (#11075)</span><span class="sxs-lookup"><span data-stu-id="812cf-267">Update ConciseView to use TargetObject if applicable (#11075)</span></span>
- <span data-ttu-id="812cf-268">Åtgärda NullReferenceException i CompletionCompleters offentliga metoder (#11274)</span><span class="sxs-lookup"><span data-stu-id="812cf-268">Fix NullReferenceException in CompletionCompleters public methods (#11274)</span></span>
- <span data-ttu-id="812cf-269">Korrigera status kontroll för fristående trådar på plattformar som inte kommer från Windows (#11301)</span><span class="sxs-lookup"><span data-stu-id="812cf-269">Fix apartment thread state check on non-Windows platforms (#11301)</span></span>
- <span data-ttu-id="812cf-270">Uppdatera inställnings PSModulePath för att sammanfoga variablerna för processen och maskin miljön (#11276)</span><span class="sxs-lookup"><span data-stu-id="812cf-270">Update setting PSModulePath to concatenate the process and machine environment variables (#11276)</span></span>
- <span data-ttu-id="812cf-271">Stöta på .NET Core till 3.1.0 (#11260)</span><span class="sxs-lookup"><span data-stu-id="812cf-271">Bump .NET Core to 3.1.0 (#11260)</span></span>
- <span data-ttu-id="812cf-272">Korrigera identifiering av $PSHOME framför $env:P ÖKVÄG (#11141)</span><span class="sxs-lookup"><span data-stu-id="812cf-272">Fix detection of $PSHOME in front of $env:PATH (#11141)</span></span>
- <span data-ttu-id="812cf-273">Tillåt att pwsh ärver $env:P SModulePath och gör så att PowerShell. exe startar korrekt (#11057)</span><span class="sxs-lookup"><span data-stu-id="812cf-273">Allow pwsh to inherit $env:PSModulePath and enable powershell.exe to start correctly (#11057)</span></span>
- <span data-ttu-id="812cf-274">Flytta till .NET Core 3,1 Preview 1 (#10798)</span><span class="sxs-lookup"><span data-stu-id="812cf-274">Move to .NET Core 3.1 preview 1 (#10798)</span></span>
- <span data-ttu-id="812cf-275">Kontroll av referens tag gen omstrukturering i fil system leverantören (#10431) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="812cf-275">Refactor reparse tag checks in file system provider (#10431) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="812cf-276">Ersätt CR och New-raden med ett 0x23CE-tecken i skript loggning (#10616)</span><span class="sxs-lookup"><span data-stu-id="812cf-276">Replace CR and new line with a 0x23CE character in script logging (#10616)</span></span>
- <span data-ttu-id="812cf-277">Åtgärda en resurs läcka genom att avregistrera händelse hanteraren från AppDomain. CurrentDomain. ProcessExit (#10626)</span><span class="sxs-lookup"><span data-stu-id="812cf-277">Fix a resource leak by unregistering the event handler from AppDomain.CurrentDomain.ProcessExit (#10626)</span></span>
- <span data-ttu-id="812cf-278">Lägg till stöd i Åtgärdsinställning. Break för att bryta till fel sökning när fel sökning, fel, information, förlopp, utförliga eller varnings meddelanden genereras (#8205) (tack @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="812cf-278">Add support to ActionPreference.Break to break into debugger when Debug, Error, Information, Progress, Verbose or Warning messages are generated (#8205) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="812cf-279">Aktivera start av kontroll panels tillägg i PowerShell Core utan att ange. CPL-tillägg.</span><span class="sxs-lookup"><span data-stu-id="812cf-279">Enable starting control panel add-ins within PowerShell Core without specifying .CPL extension.</span></span> <span data-ttu-id="812cf-280">(#9828)</span><span class="sxs-lookup"><span data-stu-id="812cf-280">(#9828)</span></span>

### <a name="general-cmdlet-updates-and-fixes"></a><span data-ttu-id="812cf-281">Allmänna cmdlet-uppdateringar och korrigeringar</span><span class="sxs-lookup"><span data-stu-id="812cf-281">General Cmdlet Updates and Fixes</span></span>

- <span data-ttu-id="812cf-282">Korrigering för problem på Raspbian för att ange datum för fil ändringar i UnixStat experimentell funktion (#11313)</span><span class="sxs-lookup"><span data-stu-id="812cf-282">Fix for issue on Raspbian for setting date of file changes in UnixStat Experimental Feature (#11313)</span></span>
- <span data-ttu-id="812cf-283">Lägg till oformaterad text i ConvertFrom – SecureString (#11142)</span><span class="sxs-lookup"><span data-stu-id="812cf-283">Add -AsPlainText to ConvertFrom-SecureString (#11142)</span></span>
- <span data-ttu-id="812cf-284">WindowsPS-versions kontroll har lagts till för WinCompat (#11148)</span><span class="sxs-lookup"><span data-stu-id="812cf-284">Added WindowsPS version check for WinCompat (#11148)</span></span>
- <span data-ttu-id="812cf-285">Åtgärda fel – rapportering i vissa WinCompat-scenarier (#11259)</span><span class="sxs-lookup"><span data-stu-id="812cf-285">Fix error-reporting in some WinCompat scenarios (#11259)</span></span>
- <span data-ttu-id="812cf-286">Lägg till inbyggd binär matchare (#11032) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="812cf-286">Add native binary resolver (#11032) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="812cf-287">Uppdatera beräkningen av tecken bredden för att respektera CJK-tecken korrekt (#11262)</span><span class="sxs-lookup"><span data-stu-id="812cf-287">Update calculation of char width to respect CJK chars correctly (#11262)</span></span>
- <span data-ttu-id="812cf-288">Lägg till avblockering – fil för macOS (#11137)</span><span class="sxs-lookup"><span data-stu-id="812cf-288">Add Unblock-File for macOS (#11137)</span></span>
- <span data-ttu-id="812cf-289">Fix regression i get-PSCallStack (#11210) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="812cf-289">Fix regression in Get-PSCallStack (#11210) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="812cf-290">Ta bort automatisk inläsning av ScheduledJob-modulen när du använder jobb-cmdletar (#11194)</span><span class="sxs-lookup"><span data-stu-id="812cf-290">Remove autoloading of the ScheduledJob module when using Job cmdlets (#11194)</span></span>
- <span data-ttu-id="812cf-291">Lägg till OutputType i get-Error-cmdleten och bevara de ursprungliga TypeName (#10856)</span><span class="sxs-lookup"><span data-stu-id="812cf-291">Add OutputType to Get-Error cmdlet and preserve original typenames (#10856)</span></span>
- <span data-ttu-id="812cf-292">Korrigera null-referens i egenskapen SupportsVirtualTerminal (#11105)</span><span class="sxs-lookup"><span data-stu-id="812cf-292">Fix null reference in SupportsVirtualTerminal property (#11105)</span></span>
- <span data-ttu-id="812cf-293">Lägg till gräns kontroll i get-WinEvent (#10648) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="812cf-293">Add limit check in Get-WinEvent (#10648) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="812cf-294">Åtgärda kommando körningen så att StopUpstreamCommandsException inte fylls i ErrorVariable (#10840)</span><span class="sxs-lookup"><span data-stu-id="812cf-294">Fix command runtime so StopUpstreamCommandsException doesn't get populated in -ErrorVariable (#10840)</span></span>
- <span data-ttu-id="812cf-295">Ställ in output-kodningen på [Console]:: OutputEncoding för interna kommandon (#10824)</span><span class="sxs-lookup"><span data-stu-id="812cf-295">Set the output encoding to [Console]::OutputEncoding for native commands (#10824)</span></span>
- <span data-ttu-id="812cf-296">Stöd för kod block med flera rader i exempel (#10776) (tack @Greg-Smulko!)</span><span class="sxs-lookup"><span data-stu-id="812cf-296">Support multi-line code blocks in examples (#10776) (Thanks @Greg-Smulko!)</span></span>
- <span data-ttu-id="812cf-297">Lägg till en kultur parameter i SELECT-String-cmdleten (#10943) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="812cf-297">Add Culture parameter to Select-String cmdlet (#10943) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="812cf-298">Åtgärda start jobbets arbets katalog Sök väg med avslutande omvänt snedstreck (#11041)</span><span class="sxs-lookup"><span data-stu-id="812cf-298">Fix Start-Job working directory path with trailing backslash (#11041)</span></span>
- <span data-ttu-id="812cf-299">ConvertFrom-JSON: unwrap Collections som standard (#10861) (tack @danstur!)</span><span class="sxs-lookup"><span data-stu-id="812cf-299">ConvertFrom-Json: Unwrap collections by default (#10861) (Thanks @danstur!)</span></span>
- <span data-ttu-id="812cf-300">Använd Skift läges känslig hash för Group-Object-cmdlet med-CaseSensitive och-AsHashtable växlar (#11030) (tack @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="812cf-300">Use case-sensitive Hashtable for Group-Object cmdlet with -CaseSensitive and -AsHashtable switches (#11030) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="812cf-301">Hantera undantag om det inte går att räkna upp filer när sökvägen återskapas för att ha rätt Skift läge (#11014)</span><span class="sxs-lookup"><span data-stu-id="812cf-301">Handle exception if enumerating files fails when rebuilding path to have correct casing (#11014)</span></span>
- <span data-ttu-id="812cf-302">Åtgärda ConciseView för att visa aktivitet i stället för kommandot mina (#11007)</span><span class="sxs-lookup"><span data-stu-id="812cf-302">Fix ConciseView to show Activity instead of myCommand (#11007)</span></span>
- <span data-ttu-id="812cf-303">Tillåt att webb-cmdlet: ar ignorerar HTTP-felstatuser (#10466) (tack @vdamewood!)</span><span class="sxs-lookup"><span data-stu-id="812cf-303">Allow web cmdlets to ignore HTTP error statuses (#10466) (Thanks @vdamewood!)</span></span>
- <span data-ttu-id="812cf-304">Korrigera överdragningen av fler än en CommandInfo till Get-Command (#10929)</span><span class="sxs-lookup"><span data-stu-id="812cf-304">Fix piping of more than one CommandInfo to Get-Command (#10929)</span></span>
- <span data-ttu-id="812cf-305">Lägg till cmdleten Get-Counter för Windows (#10933)</span><span class="sxs-lookup"><span data-stu-id="812cf-305">Add back Get-Counter cmdlet for Windows (#10933)</span></span>
- <span data-ttu-id="812cf-306">Gör ConvertTo-JSON-behandling [AutomationNull]:: värde och [NullString]:: värde som $null (#10957)</span><span class="sxs-lookup"><span data-stu-id="812cf-306">Make ConvertTo-Json treat [AutomationNull]::Value and [NullString]::Value as $null (#10957)</span></span>
- <span data-ttu-id="812cf-307">Ta bort hakparenteser från IPv6-adressen för SSH-fjärrkommunikation (#10968)</span><span class="sxs-lookup"><span data-stu-id="812cf-307">Remove brackets from ipv6 address for SSH remoting (#10968)</span></span>
- <span data-ttu-id="812cf-308">Åtgärda krasch om kommandot som skickas till pwsh är bara blank steg (#10977)</span><span class="sxs-lookup"><span data-stu-id="812cf-308">Fix crash if command sent to pwsh is just whitespace (#10977)</span></span>
- <span data-ttu-id="812cf-309">Tillägg mellan plattformar get-Urklipp och set-Clipboard (#10340)</span><span class="sxs-lookup"><span data-stu-id="812cf-309">Added cross-platform Get-Clipboard and Set-Clipboard (#10340)</span></span>
- <span data-ttu-id="812cf-310">Korrigera inställning av ursprunglig sökväg för fil Systems objekt till att inte ha ett extra avslutande snedstreck (#10959)</span><span class="sxs-lookup"><span data-stu-id="812cf-310">Fix setting original path of filesystem object to not have extra trailing slash (#10959)</span></span>
- <span data-ttu-id="812cf-311">Stöd $null för ConvertTo-JSON (#10947)</span><span class="sxs-lookup"><span data-stu-id="812cf-311">Support $null for ConvertTo-Json (#10947)</span></span>
- <span data-ttu-id="812cf-312">Lägg till kommandot back ut – skrivare i Windows (#10906)</span><span class="sxs-lookup"><span data-stu-id="812cf-312">Add back Out-Printer command on Windows (#10906)</span></span>
- <span data-ttu-id="812cf-313">Åtgärda start-Job-WorkingDirectory med blank steg (#10951)</span><span class="sxs-lookup"><span data-stu-id="812cf-313">Fix Start-Job -WorkingDirectory with whitespace (#10951)</span></span>
- <span data-ttu-id="812cf-314">Returnera standardvärdet när null hämtas för en inställning i PSConfiguration.cs (#10963) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="812cf-314">Return default value when getting null for a setting in PSConfiguration.cs (#10963) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="812cf-315">Hantera IO-undantag som icke-avslutande (#10950)</span><span class="sxs-lookup"><span data-stu-id="812cf-315">Handle IO exception as non-terminating (#10950)</span></span>
- <span data-ttu-id="812cf-316">Lägg till GraphicalHost-sammansättning för att aktivera out-GridView, show-Command och Get-Help-ShowWindow (#10899)</span><span class="sxs-lookup"><span data-stu-id="812cf-316">Add GraphicalHost assembly to enable Out-GridView, Show-Command, and Get-Help -ShowWindow (#10899)</span></span>
- <span data-ttu-id="812cf-317">Ta dator namn via pipeline i get-HotFix (#10852) (tack @kvprasoon!)</span><span class="sxs-lookup"><span data-stu-id="812cf-317">Take ComputerName via pipeline in Get-HotFix (#10852) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="812cf-318">Korrigera att fliken har slutförts för parametrar så att den visar vanliga parametrar som tillgängliga (#10850)</span><span class="sxs-lookup"><span data-stu-id="812cf-318">Fix tab completion for parameters so that it shows common parameters as available (#10850)</span></span>
- <span data-ttu-id="812cf-319">Korrigera GetCorrectCasedPath () för att först kontrol lera om några system fil poster returneras innan du anropar First () (#10930)</span><span class="sxs-lookup"><span data-stu-id="812cf-319">Fix GetCorrectCasedPath() to first check if any system file entries is returned before calling First() (#10930)</span></span>
- <span data-ttu-id="812cf-320">Ange arbets katalog till den aktuella katalogen i Start-Job (#10920) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="812cf-320">Set working directory to current directory in Start-Job (#10920) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="812cf-321">Ändra TabExpansion2 till att inte kräva-CursorColumn och behandla som $InputScript. length (#10849)</span><span class="sxs-lookup"><span data-stu-id="812cf-321">Change TabExpansion2 to not require -CursorColumn and treat as $InputScript.Length (#10849)</span></span>
- <span data-ttu-id="812cf-322">Hantera fall där värden inte kan returnera rader eller kolumner på skärmen (#10938)</span><span class="sxs-lookup"><span data-stu-id="812cf-322">Handle case where Host may not return Rows or Columns of screen (#10938)</span></span>
- <span data-ttu-id="812cf-323">Korrigera användningen av dekor färger för värdar som inte stöder dem (#10937)</span><span class="sxs-lookup"><span data-stu-id="812cf-323">Fix use of accent colors for hosts that don't support them (#10937)</span></span>
- <span data-ttu-id="812cf-324">Lägg till föregående uppdatering-List kommando (#10922)</span><span class="sxs-lookup"><span data-stu-id="812cf-324">Add back Update-List command (#10922)</span></span>
- <span data-ttu-id="812cf-325">Uppdatera FWLink-ID för Clear-RecycleBin (#10925)</span><span class="sxs-lookup"><span data-stu-id="812cf-325">Update FWLink Id for Clear-RecycleBin (#10925)</span></span>
- <span data-ttu-id="812cf-326">Hoppa över fil vid slut för ande av filer om det inte går att läsa filattribut (#10910)</span><span class="sxs-lookup"><span data-stu-id="812cf-326">During tab completion, skip file if can't read file attributes (#10910)</span></span>
- <span data-ttu-id="812cf-327">Lägg till Clear-RecycleBin för Windows (#10909)</span><span class="sxs-lookup"><span data-stu-id="812cf-327">Add back Clear-RecycleBin for Windows (#10909)</span></span>
- <span data-ttu-id="812cf-328">Lägg till `$env:__SuppressAnsiEscapeSequences` för att kontrol lera om VT-escape-sekvens i utdata (#10814)</span><span class="sxs-lookup"><span data-stu-id="812cf-328">Add `$env:__SuppressAnsiEscapeSequences` to control whether to have VT escape sequence in output (#10814)</span></span>
- <span data-ttu-id="812cf-329">Lägg till nobetonar parameter för att färga Select-String-utdata (#8963) (tack @derek-xia!)</span><span class="sxs-lookup"><span data-stu-id="812cf-329">Add -NoEmphasize parameter to colorize Select-String output (#8963) (Thanks @derek-xia!)</span></span>
- <span data-ttu-id="812cf-330">Lägg till snabb korrigerings-cmdlet för hämtning (#10740)</span><span class="sxs-lookup"><span data-stu-id="812cf-330">Add back Get-HotFix cmdlet (#10740)</span></span>
- <span data-ttu-id="812cf-331">Gör användbara tillägg i program som är värdar för PowerShell (#10587)</span><span class="sxs-lookup"><span data-stu-id="812cf-331">Make Add-Type usable in applications that host PowerShell (#10587)</span></span>
- <span data-ttu-id="812cf-332">Använd en mer effektiv utvärderings ordning i LanguagePrimitives. IsNullLike () (#10781) (tack @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="812cf-332">Use more effective evaluation order in LanguagePrimitives.IsNullLike() (#10781) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="812cf-333">Förbättra hanteringen av skickas-indata och skickas strömmar med blandat indata i format-hex (#8674) (tack @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="812cf-333">Improve handling of mixed-collection piped input and piped streams of input in Format-Hex (#8674) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="812cf-334">Använd typ konvertering i SSHConnection hash när värdet inte matchar förväntad typ (#10720) (tack @SeeminglyScience!)</span><span class="sxs-lookup"><span data-stu-id="812cf-334">Use type conversion in SSHConnection hashtables when value doesn't match expected type (#10720) (Thanks @SeeminglyScience!)</span></span>
- <span data-ttu-id="812cf-335">Korrigera get-Content-ReadCount 0-beteende när-TotalCount har angetts (#10749) (tack @eugenesmlv!)</span><span class="sxs-lookup"><span data-stu-id="812cf-335">Fix Get-Content -ReadCount 0 behavior when -TotalCount is set (#10749) (Thanks @eugenesmlv!)</span></span>
- <span data-ttu-id="812cf-336">Ett fel meddelande om att Word-åtkomst nekades i get-WinEvent (#10639) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="812cf-336">Reword access denied error message in Get-WinEvent (#10639) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="812cf-337">Aktivera slut för ande av TABB för variabel tilldelning som är Enum eller typ begränsad (#10646)</span><span class="sxs-lookup"><span data-stu-id="812cf-337">Enable tab completion for variable assignment that is enum or type constrained (#10646)</span></span>
- <span data-ttu-id="812cf-338">Ta bort den oanvända SourceLength-egenskapen som orsakar problem med formateringen (#10765)</span><span class="sxs-lookup"><span data-stu-id="812cf-338">Remove unused SourceLength remoting property causing formatting issues (#10765)</span></span>
- <span data-ttu-id="812cf-339">Parametern Add-delimiter till ConvertFrom-StringData (#10665) (tack @steviecoaster!)</span><span class="sxs-lookup"><span data-stu-id="812cf-339">Add -Delimiter parameter to ConvertFrom-StringData (#10665) (Thanks @steviecoaster!)</span></span>
- <span data-ttu-id="812cf-340">Lägg till positions parametern för script block när du använder Invoke-Command med SSH (#10721) (tack @machgo!)</span><span class="sxs-lookup"><span data-stu-id="812cf-340">Add positional parameter for ScriptBlock when using Invoke-Command with SSH (#10721) (Thanks @machgo!)</span></span>
- <span data-ttu-id="812cf-341">Visa information om linje kontext om flera rader men inte skript namn för ConciseView (#10746)</span><span class="sxs-lookup"><span data-stu-id="812cf-341">Show line context information if multiple lines but no script name for ConciseView (#10746)</span></span>
- <span data-ttu-id="812cf-342">Lägg till stöd för \\Wsl $ \ sökvägar till fil system leverantören (#10674)</span><span class="sxs-lookup"><span data-stu-id="812cf-342">Add support for \\wsl$\ paths to file system provider (#10674)</span></span>
- <span data-ttu-id="812cf-343">Lägg till den token-text som saknas för TokenKind. QuestionMark i parser (#10706)</span><span class="sxs-lookup"><span data-stu-id="812cf-343">Add the missing token text for TokenKind.QuestionMark in parser (#10706)</span></span>
- <span data-ttu-id="812cf-344">Ange aktuell arbets katalog för varje förgrunds-objekt – parallellt kör skript till samma plats som det anropande skriptet.</span><span class="sxs-lookup"><span data-stu-id="812cf-344">Set current working directory of each ForEach-Object -Parallel running script to the same location as the calling script.</span></span> <span data-ttu-id="812cf-345">(#10672)</span><span class="sxs-lookup"><span data-stu-id="812cf-345">(#10672)</span></span>
- <span data-ttu-id="812cf-346">Ersätt API-ms-win-core-File-L1-2 -2. dll med Kernell32. dll för FindFirstStreamW och FindNextStreamW-API: er (#10680) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="812cf-346">Replace api-ms-win-core-file-l1-2-2.dll with Kernell32.dll for FindFirstStreamW and FindNextStreamW APIs (#10680) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="812cf-347">Ändra skript för hjälp formatering så att det blir mer StrictMode-tolerant (#10563)</span><span class="sxs-lookup"><span data-stu-id="812cf-347">Tweak help formatting script to be more StrictMode tolerant (#10563)</span></span>
- <span data-ttu-id="812cf-348">Add-SecurityDescriptorSDDL-parameter till New-service (#10483) (tack @kvprasoon!)</span><span class="sxs-lookup"><span data-stu-id="812cf-348">Add -SecurityDescriptorSDDL parameter to New-Service (#10483) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="812cf-349">Ta bort informations utdata, konsolidera ping-användning i Test-Connection (#10478) (tack @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="812cf-349">Remove informational output, consolidate ping usage in Test-Connection (#10478) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="812cf-350">Läs särskilda referens punkter utan att komma åt dem (#10662) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="812cf-350">Read special reparse points without accessing them (#10662) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="812cf-351">Direkt rensa värden till terminalen (#10681) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="812cf-351">Direct Clear-Host output to terminal (#10681) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="812cf-352">Lägg till bakgrunds rad för gruppering med format – tabell och-egenskap (#10653)</span><span class="sxs-lookup"><span data-stu-id="812cf-352">Add back newline for grouping with Format-Table and -Property (#10653)</span></span>
- <span data-ttu-id="812cf-353">Ta bort [ValidateNotNullOrEmpty] från-InputObject på Get-slump för att tillåta en tom sträng (#10644)</span><span class="sxs-lookup"><span data-stu-id="812cf-353">Remove [ValidateNotNullOrEmpty] from -InputObject on Get-Random to allow empty string (#10644)</span></span>
- <span data-ttu-id="812cf-354">Gör ett skift läges okänsligt läge för system sträng avstånds okänslighet (#10549) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="812cf-354">Make suggestion system string distance algorithm case-insensitive (#10549) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="812cf-355">Åtgärda null-referens undantag i framliggande objekt-parallell bearbetning av indata (#10577)</span><span class="sxs-lookup"><span data-stu-id="812cf-355">Fix null reference exception in ForEach-Object -Parallel input processing (#10577)</span></span>
- <span data-ttu-id="812cf-356">Lägg till PowerShell-definitioner för grup principer (#10468)</span><span class="sxs-lookup"><span data-stu-id="812cf-356">Add PowerShell Core group policy definitions (#10468)</span></span>
- <span data-ttu-id="812cf-357">Uppdatera konsol värden så att den stöder XTPUSHSGR/XTPOPSGR VT-kontroller som används i sammanställnings scenarier.</span><span class="sxs-lookup"><span data-stu-id="812cf-357">Update console host to support XTPUSHSGR/XTPOPSGR VT control sequences that are used in composability scenarios.</span></span> <span data-ttu-id="812cf-358">(#10208)</span><span class="sxs-lookup"><span data-stu-id="812cf-358">(#10208)</span></span>
- <span data-ttu-id="812cf-359">Lägg till parametern WorkingDirectory till Start-Job (#10324) (tack @davinci26!)</span><span class="sxs-lookup"><span data-stu-id="812cf-359">Add WorkingDirectory parameter to Start-Job (#10324) (Thanks @davinci26!)</span></span>
- <span data-ttu-id="812cf-360">Ta bort händelse hanteraren som orsakade Bryt punkts ändringar som inte skulle replikeras felaktigt till värd körnings utrymme fel sökning (#10503) (tack @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="812cf-360">Remove the event handler that was causing breakpoint changes to be erroneously replicated to the host runspace debugger (#10503) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="812cf-361">Ersätt API-ms-win-core-Job-12-1 -0. dll med Kernell32. dll i Microsoft. PowerShell. commands. NativeMethods P/Invoke API (#10417) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="812cf-361">Replace api-ms-win-core-job-12-1-0.dll with Kernell32.dll in Microsoft.PowerShell.Commands.NativeMethods P/Invoke API(#10417) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="812cf-362">Åtgärda fel utdata för New-service i variabel tilldelning och-avvariabel (#10444) (tack @kvprasoon!)</span><span class="sxs-lookup"><span data-stu-id="812cf-362">Fix wrong output for New-Service in variable assignment and -OutVariable (#10444) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="812cf-363">Åtgärda problem med globala verktyg runt avslutnings kod, kommando rads parametrar och sökväg med blank steg (#10461)</span><span class="sxs-lookup"><span data-stu-id="812cf-363">Fix global tool issues around exit code, command line parameters and path with spaces (#10461)</span></span>
- <span data-ttu-id="812cf-364">Åtgärda rekursion i OneDrive-Change FindFirstFileEx () för att använda SafeFindHandle-typ (#10405)</span><span class="sxs-lookup"><span data-stu-id="812cf-364">Fix recursion into OneDrive - change FindFirstFileEx() to use SafeFindHandle type (#10405)</span></span>
- <span data-ttu-id="812cf-365">Hoppa över automatisk inläsning av PSReadLine i Windows om NVDA skärm läsaren är aktiv (#10385)</span><span class="sxs-lookup"><span data-stu-id="812cf-365">Skip auto-loading PSReadLine on Windows if the NVDA screen reader is active (#10385)</span></span>
- <span data-ttu-id="812cf-366">Öka de inbyggda-med-PowerShell-modulens versioner till 7.0.0.0 (#10356)</span><span class="sxs-lookup"><span data-stu-id="812cf-366">Increase built-with-PowerShell module versions to 7.0.0.0 (#10356)</span></span>
- <span data-ttu-id="812cf-367">Lägg till utlöses ett fel i tilläggs typen om det redan finns en typ med samma namn (#9609) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="812cf-367">Add throwing an error in Add-Type if a type with the same name already exists (#9609) (Thanks @iSazonov!)</span></span>

### <a name="performance"></a><span data-ttu-id="812cf-368">Prestanda</span><span class="sxs-lookup"><span data-stu-id="812cf-368">Performance</span></span>

- <span data-ttu-id="812cf-369">Undvik att använda avslutning i parser. SaveError (#11006)</span><span class="sxs-lookup"><span data-stu-id="812cf-369">Avoid using closure in Parser.SaveError (#11006)</span></span>
- <span data-ttu-id="812cf-370">Förbättra cachelagringen när du skapar nya regex-instanser (#10657) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="812cf-370">Improve the caching when creating new Regex instances (#10657) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="812cf-371">Förbättra bearbetningen av inbyggda PowerShell-Datadata från types. ps1xml, typesV3. ps1xml och GetEvent. types. ps1xml (#10898)</span><span class="sxs-lookup"><span data-stu-id="812cf-371">Improve processing of the PowerShell built-in type data from types.ps1xml, typesV3.ps1xml and GetEvent.types.ps1xml (#10898)</span></span>
- <span data-ttu-id="812cf-372">Uppdatera PSConfiguration. ReadValueFromFile för att göra det snabbare och mer minne effektivt (#10839)</span><span class="sxs-lookup"><span data-stu-id="812cf-372">Update PSConfiguration.ReadValueFromFile to make it faster and more memory efficient (#10839)</span></span>
- <span data-ttu-id="812cf-373">Lägg till mindre prestanda förbättringar för körnings utrymme-initiering (#10569) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="812cf-373">Add minor performance improvements for runspace initialization (#10569) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="812cf-374">Gör en förvarsin-objekt snabbare för de scenarier som används ofta (#10454) och åtgärda de stegvisa prestanda problemen för objekt parallellt med många körnings utrymmen (#10455)</span><span class="sxs-lookup"><span data-stu-id="812cf-374">Make ForEach-Object faster for its commonly used scenarios (#10454) and fix ForEach-Object -Parallel performance problem with many runspaces (#10455)</span></span>

### <a name="code-cleanup"></a><span data-ttu-id="812cf-375">Rensa kod</span><span class="sxs-lookup"><span data-stu-id="812cf-375">Code Cleanup</span></span>

- <span data-ttu-id="812cf-376">Ändra kommentar och element text för att uppfylla Microsofts standarder (#11304)</span><span class="sxs-lookup"><span data-stu-id="812cf-376">Change comment and element text to meet Microsoft standards (#11304)</span></span>
- <span data-ttu-id="812cf-377">Problem med att rensa format i Compiler.cs (#10368) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="812cf-377">Cleanup style issues in Compiler.cs (#10368) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="812cf-378">Ta bort den oanvända typ konverteraren för CommaDelimitedStringCollection (#11000) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="812cf-378">Remove the unused type converter for CommaDelimitedStringCollection (#11000) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="812cf-379">Rensnings format i InitialSessionState.cs (#10865) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="812cf-379">Cleanup style in InitialSessionState.cs (#10865) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="812cf-380">Rensa kod för PSSession-klass (#11001)</span><span class="sxs-lookup"><span data-stu-id="812cf-380">Code clean up for PSSession class (#11001)</span></span>
- <span data-ttu-id="812cf-381">Ta bort körnings funktionen kör uppdatering – hjälp från Get-Help när funktionen Get-Help körs för första gången (#10974)</span><span class="sxs-lookup"><span data-stu-id="812cf-381">Remove the not-working 'run Update-Help from Get-Help when Get-Help runs for the first time' feature (#10974)</span></span>
- <span data-ttu-id="812cf-382">Åtgärda problem med formatmall (#10998) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="812cf-382">Fix style issues (#10998) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="812cf-383">Rensning: Använd det inbyggda aliaset (#10882) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="812cf-383">Cleanup: use the built-in type alias (#10882) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="812cf-384">Ta bort den oanvända inställnings nyckeln ConsolePrompting och Undvik att skapa onödig sträng när du ställer frågor till ExecutionPolicy-inställningen (#10985)</span><span class="sxs-lookup"><span data-stu-id="812cf-384">Remove the unused setting key ConsolePrompting and avoid unnecessary string creation when querying ExecutionPolicy setting (#10985)</span></span>
- <span data-ttu-id="812cf-385">Inaktivera kontroll av uppdaterings meddelande för dagliga builds (#10903) (tack @bergmeister!)</span><span class="sxs-lookup"><span data-stu-id="812cf-385">Disable update notification check for daily builds (#10903) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="812cf-386">Återställa fel söknings-API förlorat i #10338 (#10808)</span><span class="sxs-lookup"><span data-stu-id="812cf-386">Reinstate debugging API lost in #10338 (#10808)</span></span>
- <span data-ttu-id="812cf-387">Ta bort WorkflowJobSourceAdapter-referens som inte längre används (#10326) (tack @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="812cf-387">Remove WorkflowJobSourceAdapter reference that is no longer used (#10326) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="812cf-388">Rensa COM-gränssnitt i snabb List kod genom att åtgärda PreserveSig-attribut (#9899) (tack @weltkante!)</span><span class="sxs-lookup"><span data-stu-id="812cf-388">Cleanup COM interfaces in jump list code by fixing PreserveSig attributes (#9899) (Thanks @weltkante!)</span></span>
- <span data-ttu-id="812cf-389">Lägg till en kommentar som beskriver varför-IA inte är alias för InformationAction common parameter (#10703) (tack @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="812cf-389">Add a comment describing why -ia is not the alias for -InformationAction common parameter (#10703) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="812cf-390">Byt namn på InvokeCommandCmdlet.cs till InvokeExpressionCommand.cs (#10659) (tack @kilasuit!)</span><span class="sxs-lookup"><span data-stu-id="812cf-390">Rename InvokeCommandCmdlet.cs to InvokeExpressionCommand.cs (#10659) (Thanks @kilasuit!)</span></span>
- <span data-ttu-id="812cf-391">Lägg till smärre kod rensningar relaterade till uppdaterings meddelanden (#10698)</span><span class="sxs-lookup"><span data-stu-id="812cf-391">Add minor code cleanups related to update notifications (#10698)</span></span>
- <span data-ttu-id="812cf-392">Ta bort föråldrad arbets flödes logik från konfigurations skripten för fjärr kommunikation (#10320) (tack @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="812cf-392">Remove deprecated workflow logic from the remoting setup scripts (#10320) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="812cf-393">Uppdatera Hjälp formatet så att det använder rätt Skift läge (#10678) (tack @tnieto88!)</span><span class="sxs-lookup"><span data-stu-id="812cf-393">Update help format to use proper case (#10678) (Thanks @tnieto88!)</span></span>
- <span data-ttu-id="812cf-394">Rensa CodeFactor-formatmallar som kommer att utföras under den senaste månaden (#10591) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="812cf-394">Clean up CodeFactor style issues coming in commits for the last month (#10591) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="812cf-395">Korrigera skrivfel i beskrivningen av PSTernaryOperator-experimentell funktion (#10586) (tack @bergmeister!)</span><span class="sxs-lookup"><span data-stu-id="812cf-395">Fix typo in description of PSTernaryOperator experimental feature (#10586) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="812cf-396">Konvertera Åtgärdsinställning. Suspend-uppräkning svärdet till en icke-kompatibel, reserverad status och ta bort begränsningen för att använda Åtgärdsinställning. IGNORE i Preferences-variabler (#10317) (tack @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="812cf-396">Convert ActionPreference.Suspend enumeration value into a non-supported, reserved state, and remove restriction on using ActionPreference.Ignore in preference variables (#10317) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="812cf-397">Ersätt ArrayList med list<T> för att få mer läsbar och tillförlitlig kod utan att ändra funktionerna (#10333) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="812cf-397">Replace ArrayList with List<T> to get more readable and reliable code without changing functionality (#10333) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="812cf-398">Gör kod formats korrigeringar till TestConnectionCommand (#10439) (tack @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="812cf-398">Make code style fixes to TestConnectionCommand (#10439) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="812cf-399">Rensa AutomationEngine och ta bort extra SetSessionStateDrive-metod anrop (#10416) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="812cf-399">Cleanup AutomationEngine and remove extra SetSessionStateDrive method call (#10416) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="812cf-400">Byt namn på standard ParameterSetName tillbaka till avgränsare för ConvertTo-CSV och ConvertFrom-CSV (#10425)</span><span class="sxs-lookup"><span data-stu-id="812cf-400">Rename default ParameterSetName back to Delimiter for ConvertTo-Csv and ConvertFrom-Csv (#10425)</span></span>

### <a name="tools"></a><span data-ttu-id="812cf-401">Verktyg</span><span class="sxs-lookup"><span data-stu-id="812cf-401">Tools</span></span>

- <span data-ttu-id="812cf-402">Lägg till standardinställningen för egenskapen SDKToUse så att den skapas i VS (#11085)</span><span class="sxs-lookup"><span data-stu-id="812cf-402">Add default setting for the SDKToUse property so that it builds in VS (#11085)</span></span>
- <span data-ttu-id="812cf-403">Install-Powershell. ps1: Lägg till parameter för att använda MSI-installation (#10921) (tack @MJECloud!)</span><span class="sxs-lookup"><span data-stu-id="812cf-403">Install-Powershell.ps1: Add parameter to use MSI installation (#10921) (Thanks @MJECloud!)</span></span>
- <span data-ttu-id="812cf-404">Lägg till grundläggande exempel för install-PowerShell. ps1 (#10914) (tack @kilasuit!)</span><span class="sxs-lookup"><span data-stu-id="812cf-404">Add basic examples for install-powershell.ps1 (#10914) (Thanks @kilasuit!)</span></span>
- <span data-ttu-id="812cf-405">Gör Install-PowerShellRemoting. ps1 för att hantera en tom sträng i PowerShellHome-parametern (#10526) (tack @Orca88!)</span><span class="sxs-lookup"><span data-stu-id="812cf-405">Make Install-PowerShellRemoting.ps1 handle empty string in PowerShellHome parameter (#10526) (Thanks @Orca88!)</span></span>
- <span data-ttu-id="812cf-406">Växla från/etc/lsb-release till/etc/OS-release i install-powershell.sh (#10773) (tack @Himura2la!)</span><span class="sxs-lookup"><span data-stu-id="812cf-406">Switch from /etc/lsb-release to /etc/os-release in install-powershell.sh (#10773) (Thanks @Himura2la!)</span></span>
- <span data-ttu-id="812cf-407">Kontrol lera pwsh. exe och pwsh i den dagliga versionen av Windows (#10738) (tack @centreboard!)</span><span class="sxs-lookup"><span data-stu-id="812cf-407">Check pwsh.exe and pwsh in daily version on Windows (#10738) (Thanks @centreboard!)</span></span>
- <span data-ttu-id="812cf-408">Ta bort onödiga tryck i installpsh-osx.sh (#10752)</span><span class="sxs-lookup"><span data-stu-id="812cf-408">Remove unneeded tap in installpsh-osx.sh (#10752)</span></span>
- <span data-ttu-id="812cf-409">Uppdatera install-PowerShell. ps1 för att söka efter redan installerad daglig build (#10489)</span><span class="sxs-lookup"><span data-stu-id="812cf-409">Update install-powershell.ps1 to check for already installed daily build (#10489)</span></span>

### <a name="tests"></a><span data-ttu-id="812cf-410">Resultaten</span><span class="sxs-lookup"><span data-stu-id="812cf-410">Tests</span></span>

- <span data-ttu-id="812cf-411">Gör ett tillförlitligt DSC-test väntar (#11131)</span><span class="sxs-lookup"><span data-stu-id="812cf-411">Make unreliable DSC test pending (#11131)</span></span>
- <span data-ttu-id="812cf-412">Åtgärda stringdata-testet för att verifiera nycklar för hash (#10810)</span><span class="sxs-lookup"><span data-stu-id="812cf-412">Fix stringdata test to correctly validate keys of hashtables (#10810)</span></span>
- <span data-ttu-id="812cf-413">Ta bort testmoduler (#11061) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="812cf-413">Unload test modules (#11061) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="812cf-414">Öka tiden mellan nya test-URL: er (#11015)</span><span class="sxs-lookup"><span data-stu-id="812cf-414">Increase time between retries of testing URL (#11015)</span></span>
- <span data-ttu-id="812cf-415">Uppdatera testerna för att korrekt beskriva test åtgärder.</span><span class="sxs-lookup"><span data-stu-id="812cf-415">Update tests to accurately describe test actions.</span></span> <span data-ttu-id="812cf-416">(#10928) (Tack @romero126!)</span><span class="sxs-lookup"><span data-stu-id="812cf-416">(#10928) (Thanks @romero126!)</span></span>
- <span data-ttu-id="812cf-417">Tillfälligt hoppa över flaky test TestAppDomainProcessExitEvenHandlerNotLeaking (#10827)</span><span class="sxs-lookup"><span data-stu-id="812cf-417">Temporary skip the flaky test TestAppDomainProcessExitEvenHandlerNotLeaking (#10827)</span></span>
- <span data-ttu-id="812cf-418">Gör så att händelse hanteraren läcker testet stabilt (#10790)</span><span class="sxs-lookup"><span data-stu-id="812cf-418">Make the event handler leaking test stable (#10790)</span></span>
- <span data-ttu-id="812cf-419">Synkronisera Skift läge i CI YAML (#10767) (tack @RDIL!)</span><span class="sxs-lookup"><span data-stu-id="812cf-419">Sync capitalization in CI YAML (#10767) (Thanks @RDIL!)</span></span>
- <span data-ttu-id="812cf-420">Lägg till test för korrigering av händelse hanterare som läcker (#10768)</span><span class="sxs-lookup"><span data-stu-id="812cf-420">Add test for the event handler leaking fix (#10768)</span></span>
- <span data-ttu-id="812cf-421">Lägg till get-ChildItem-test (#10507) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="812cf-421">Add Get-ChildItem test (#10507) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="812cf-422">Ersätt tvetydigt språk för test från växla till parameter för noggrannhet (#10666) (tack @romero126!)</span><span class="sxs-lookup"><span data-stu-id="812cf-422">Replace ambiguous language for tests from switch to parameter for accuracy (#10666) (Thanks @romero126!)</span></span>
- <span data-ttu-id="812cf-423">Lägg till experimentell kontroll i förgrunden – objekt parallella tester (#10354) (tack @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="812cf-423">Add experimental check to ForEach-Object -Parallel tests (#10354) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="812cf-424">Uppdatera tester för Alpine-validering (#10428)</span><span class="sxs-lookup"><span data-stu-id="812cf-424">Update tests for Alpine validation (#10428)</span></span>

### <a name="build-and-package-improvements"></a><span data-ttu-id="812cf-425">Förbättringar av build och paket</span><span class="sxs-lookup"><span data-stu-id="812cf-425">Build and Package Improvements</span></span>

- <span data-ttu-id="812cf-426">Åtgärda NuGet-paketets signering för koordinerade paket byggen (#11316)</span><span class="sxs-lookup"><span data-stu-id="812cf-426">Fix Nuget package signing for Coordinated Package build (#11316)</span></span>
- <span data-ttu-id="812cf-427">Uppdatera beroenden från PowerShell-galleriet och NuGet (#11323)</span><span class="sxs-lookup"><span data-stu-id="812cf-427">Update dependencies from PowerShell Gallery and NuGet (#11323)</span></span>
- <span data-ttu-id="812cf-428">Ojämnhet Microsoft. ApplicationInsights från 2.11.0 till 2.12.0 (#11305)</span><span class="sxs-lookup"><span data-stu-id="812cf-428">Bump Microsoft.ApplicationInsights from 2.11.0 to 2.12.0 (#11305)</span></span>
- <span data-ttu-id="812cf-429">Ojämnhet Microsoft. CodeAnalysis. CSharp från 3.3.1 till 3.4.0 (#11265)</span><span class="sxs-lookup"><span data-stu-id="812cf-429">Bump Microsoft.CodeAnalysis.CSharp from 3.3.1 to 3.4.0 (#11265)</span></span>
- <span data-ttu-id="812cf-430">Uppdaterings paket för Debian 10 och 11 (#11236)</span><span class="sxs-lookup"><span data-stu-id="812cf-430">Updates packages for Debian 10 and 11 (#11236)</span></span>
- <span data-ttu-id="812cf-431">Aktivera endast experimentella funktioner före RC (#11162)</span><span class="sxs-lookup"><span data-stu-id="812cf-431">Only enable experimental features prior to RC (#11162)</span></span>
- <span data-ttu-id="812cf-432">Uppdatera lägsta macOS-version (#11163)</span><span class="sxs-lookup"><span data-stu-id="812cf-432">Update macOS minimum version (#11163)</span></span>
- <span data-ttu-id="812cf-433">Ojämnhets NJsonSchema från 10.0.27 till 10.0.28 (#11170)</span><span class="sxs-lookup"><span data-stu-id="812cf-433">Bump NJsonSchema from 10.0.27 to 10.0.28 (#11170)</span></span>
- <span data-ttu-id="812cf-434">Uppdaterar länkar i README.md och metadata. JSON för för hands versionen. 5 (#10854)</span><span class="sxs-lookup"><span data-stu-id="812cf-434">Updating links in README.md and metadata.json for Preview.5 (#10854)</span></span>
- <span data-ttu-id="812cf-435">Välj filer för testning av efterlevnad som ägs av PowerShell (#10837)</span><span class="sxs-lookup"><span data-stu-id="812cf-435">Select the files for compliance tests which are owned by PowerShell (#10837)</span></span>
- <span data-ttu-id="812cf-436">Tillåt att win7x86 msix-paketet skapas.</span><span class="sxs-lookup"><span data-stu-id="812cf-436">Allow win7x86 msix package to build.</span></span> <span data-ttu-id="812cf-437">(Internt 10515)</span><span class="sxs-lookup"><span data-stu-id="812cf-437">(Internal 10515)</span></span>
- <span data-ttu-id="812cf-438">Tillåt att semantiska versioner skickas till NormalizeVersion-funktionen (#11087)</span><span class="sxs-lookup"><span data-stu-id="812cf-438">Allow semantic versions to be passed to NormalizeVersion function (#11087)</span></span>
- <span data-ttu-id="812cf-439">Stöter på .NET Core Framework till 3,1 – för hands version. 3 (#11079)</span><span class="sxs-lookup"><span data-stu-id="812cf-439">Bump .NET core framework to 3.1-preview.3 (#11079)</span></span>
- <span data-ttu-id="812cf-440">Ojämnhet PSReadLine från 2.0.0-beta5 till 2.0.0-beta6 i/src/Modules (#11078)</span><span class="sxs-lookup"><span data-stu-id="812cf-440">Bump PSReadLine from 2.0.0-beta5 to 2.0.0-beta6 in /src/Modules (#11078)</span></span>
- <span data-ttu-id="812cf-441">Ojämnhet Newtonsoft. JSON från 12.0.2 till 12.0.3 (#11037) (#11038)</span><span class="sxs-lookup"><span data-stu-id="812cf-441">Bump Newtonsoft.Json from 12.0.2 to 12.0.3 (#11037) (#11038)</span></span>
- <span data-ttu-id="812cf-442">Lägg till Debian 10, 11 och CentOS 8-paket (#11028)</span><span class="sxs-lookup"><span data-stu-id="812cf-442">Add Debian 10, 11 and CentOS 8 packages (#11028)</span></span>
- <span data-ttu-id="812cf-443">Ladda upp JSON-filen för build-info med ReleaseDate-fältet (#10986)</span><span class="sxs-lookup"><span data-stu-id="812cf-443">Upload Build-Info Json file with the ReleaseDate field (#10986)</span></span>
- <span data-ttu-id="812cf-444">Stöter på .NET Core Framework till 3,1 – för hands version. 2 (#10993)</span><span class="sxs-lookup"><span data-stu-id="812cf-444">Bump .NET core framework to 3.1-preview.2 (#10993)</span></span>
- <span data-ttu-id="812cf-445">Aktivera build av x86 MSIX-paket (#10934)</span><span class="sxs-lookup"><span data-stu-id="812cf-445">Enable build of x86 MSIX package (#10934)</span></span>
- <span data-ttu-id="812cf-446">Uppdatera URL: en för installations skriptet för dotNET SDK i build. psm1 (#10927)</span><span class="sxs-lookup"><span data-stu-id="812cf-446">Update the dotnet SDK install script URL in build.psm1 (#10927)</span></span>
- <span data-ttu-id="812cf-447">Ojämnhet Markdig. signerat från 0.17.1 till 0.18.0 (#10887)</span><span class="sxs-lookup"><span data-stu-id="812cf-447">Bump Markdig.Signed from 0.17.1 to 0.18.0 (#10887)</span></span>
- <span data-ttu-id="812cf-448">Ojämnhets ThreadJob från 2.0.1 till 2.0.2 (#10886)</span><span class="sxs-lookup"><span data-stu-id="812cf-448">Bump ThreadJob from 2.0.1 to 2.0.2 (#10886)</span></span>
- <span data-ttu-id="812cf-449">Uppdatera AppX-manifest och paketera modul så att de överensstämmer med kraven för MS Store (#10878)</span><span class="sxs-lookup"><span data-stu-id="812cf-449">Update AppX Manifest and Packaging module to conform to MS Store requirements (#10878)</span></span>
- <span data-ttu-id="812cf-450">Uppdatera paket referens för PowerShell SDK för för hands version. 5 (internt 10295)</span><span class="sxs-lookup"><span data-stu-id="812cf-450">Update package reference for PowerShell SDK to preview.5 (Internal 10295)</span></span>
- <span data-ttu-id="812cf-451">Uppdatera ThirdPartyNotices. txt (#10834)</span><span class="sxs-lookup"><span data-stu-id="812cf-451">Update ThirdPartyNotices.txt (#10834)</span></span>
- <span data-ttu-id="812cf-452">Ojämnhet Microsoft. PowerShell. Native to 7.0.0 – för hands version. 3 (#10826)</span><span class="sxs-lookup"><span data-stu-id="812cf-452">Bump Microsoft.PowerShell.Native to 7.0.0-preview.3 (#10826)</span></span>
- <span data-ttu-id="812cf-453">Ojämnhet Microsoft. ApplicationInsights från 2.10.0 till 2.11.0 (#10608)</span><span class="sxs-lookup"><span data-stu-id="812cf-453">Bump Microsoft.ApplicationInsights from 2.10.0 to 2.11.0 (#10608)</span></span>
- <span data-ttu-id="812cf-454">Ojämnhets NJsonSchema från 10.0.24 till 10.0.27 (#10756)</span><span class="sxs-lookup"><span data-stu-id="812cf-454">Bump NJsonSchema from 10.0.24 to 10.0.27 (#10756)</span></span>
- <span data-ttu-id="812cf-455">Lägg till MacPorts-stöd för build-systemet (#10736) (tack @Lucius-Q-User!)</span><span class="sxs-lookup"><span data-stu-id="812cf-455">Add MacPorts support to the build system (#10736) (Thanks @Lucius-Q-User!)</span></span>
- <span data-ttu-id="812cf-456">Ojämnhets PackageManagement från 1.4.4 till 1.4.5 (#10728)</span><span class="sxs-lookup"><span data-stu-id="812cf-456">Bump PackageManagement from 1.4.4 to 1.4.5 (#10728)</span></span>
- <span data-ttu-id="812cf-457">Ojämnhets NJsonSchema från 10.0.23 till 10.0.24 (#10635)</span><span class="sxs-lookup"><span data-stu-id="812cf-457">Bump NJsonSchema from 10.0.23 to 10.0.24 (#10635)</span></span>
- <span data-ttu-id="812cf-458">Lägg till en miljö variabel för att skilja klient/server-telemetri i MSI (#10612)</span><span class="sxs-lookup"><span data-stu-id="812cf-458">Add environment variable to differentiate client/server telemetry in MSI (#10612)</span></span>
- <span data-ttu-id="812cf-459">Ojämnhets PSDesiredStateConfiguration från 2.0.3 till 2.0.4 (#10603)</span><span class="sxs-lookup"><span data-stu-id="812cf-459">Bump PSDesiredStateConfiguration from 2.0.3 to 2.0.4 (#10603)</span></span>
- <span data-ttu-id="812cf-460">Ojämnhet Microsoft. CodeAnalysis. CSharp från 3.2.1 till 3.3.1 (#10607)</span><span class="sxs-lookup"><span data-stu-id="812cf-460">Bump Microsoft.CodeAnalysis.CSharp from 3.2.1 to 3.3.1 (#10607)</span></span>
- <span data-ttu-id="812cf-461">Uppdatera till .net Core 3,0 RTM (#10604) (tack @bergmeister!)</span><span class="sxs-lookup"><span data-stu-id="812cf-461">Update to .Net Core 3.0 RTM (#10604) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="812cf-462">Uppdatera MSIX-paket så att versions kraven för Windows Store (#10588)</span><span class="sxs-lookup"><span data-stu-id="812cf-462">Update MSIX packaging so the version to Windows Store requirements (#10588)</span></span>
- <span data-ttu-id="812cf-463">Ojämnhet PowerShellGet-version från 2,2 till 2.2.1 (#10382)</span><span class="sxs-lookup"><span data-stu-id="812cf-463">Bump PowerShellGet version from 2.2 to 2.2.1 (#10382)</span></span>
- <span data-ttu-id="812cf-464">Ojämnhet PackageManagement-version från 1.4.3 till 1.4.4 (#10383)</span><span class="sxs-lookup"><span data-stu-id="812cf-464">Bump PackageManagement version from 1.4.3 to 1.4.4 (#10383)</span></span>
- <span data-ttu-id="812cf-465">Uppdatera README.md och metadata. JSON för 7.0.0-Preview. 4 (internt 10011)</span><span class="sxs-lookup"><span data-stu-id="812cf-465">Update README.md and metadata.json for 7.0.0-preview.4 (Internal 10011)</span></span>
- <span data-ttu-id="812cf-466">Uppgradera .net Core 3,0-versionen från Preview 9 till RC1 (#10552) (tack @bergmeister!)</span><span class="sxs-lookup"><span data-stu-id="812cf-466">Upgrade .Net Core 3.0 version from Preview 9 to RC1 (#10552) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="812cf-467">Åtgärda genereringen av ExperimentalFeature-listor (internt 9996)</span><span class="sxs-lookup"><span data-stu-id="812cf-467">Fix ExperimentalFeature list generation (Internal 9996)</span></span>
- <span data-ttu-id="812cf-468">Ojämnhet PSReadLine-version från 2.0.0-beta4 till 2.0.0-beta5 (#10536)</span><span class="sxs-lookup"><span data-stu-id="812cf-468">Bump PSReadLine version from 2.0.0-beta4 to 2.0.0-beta5 (#10536)</span></span>
- <span data-ttu-id="812cf-469">Korrigera release build-skript för att ange versions tag gen</span><span class="sxs-lookup"><span data-stu-id="812cf-469">Fix release build script to set release tag</span></span>
- <span data-ttu-id="812cf-470">Uppdatera versionen av Microsoft. PowerShell. Native till 7.0.0 – för hands version. 2 (#10519)</span><span class="sxs-lookup"><span data-stu-id="812cf-470">Update version of Microsoft.PowerShell.Native to 7.0.0-preview.2 (#10519)</span></span>
- <span data-ttu-id="812cf-471">Uppgradera till Netcoreapp 3.0 preview9 (#10484) (tack @bergmeister!)</span><span class="sxs-lookup"><span data-stu-id="812cf-471">Upgrade to Netcoreapp3.0 preview9 (#10484) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="812cf-472">Se till att den dagliga samordnade versionen vet att det är en daglig version (#10464)</span><span class="sxs-lookup"><span data-stu-id="812cf-472">Make sure the daily coordinated build, knows it is a daily build (#10464)</span></span>
- <span data-ttu-id="812cf-473">Uppdatera den kombinerade paket versionen för att frigöra de dagliga build-versionerna (#10449)</span><span class="sxs-lookup"><span data-stu-id="812cf-473">Update the combined package build to release the daily builds (#10449)</span></span>
- <span data-ttu-id="812cf-474">Ta bort AppVeyor-referens (#10445) (tack @RDIL!)</span><span class="sxs-lookup"><span data-stu-id="812cf-474">Remove appveyor reference (#10445) (Thanks @RDIL!)</span></span>
- <span data-ttu-id="812cf-475">Ojämnhet NJsonSchema-version från 10.0.22 till 10.0.23 (#10421)</span><span class="sxs-lookup"><span data-stu-id="812cf-475">Bump NJsonSchema version from 10.0.22 to 10.0.23 (#10421)</span></span>
- <span data-ttu-id="812cf-476">Ta bort borttagningen av linux-x64-installationsmappen eftersom vissa beroenden för Alpine behöver den (#10407)</span><span class="sxs-lookup"><span data-stu-id="812cf-476">Remove the deletion of linux-x64 build folder because some dependencies for Alpine need it (#10407)</span></span>

### <a name="documentation-and-help-content"></a><span data-ttu-id="812cf-477">Dokumentation och hjälp innehåll</span><span class="sxs-lookup"><span data-stu-id="812cf-477">Documentation and Help Content</span></span>

- <span data-ttu-id="812cf-478">Ändrings loggar i en logg per utgåva (#11165)</span><span class="sxs-lookup"><span data-stu-id="812cf-478">Refactor change logs into one log per release (#11165)</span></span>
- <span data-ttu-id="812cf-479">Åtgärda FWLinks för PowerShell 7 direkt hjälp dokument (#11071)</span><span class="sxs-lookup"><span data-stu-id="812cf-479">Fix FWLinks for PowerShell 7 online help documents (#11071)</span></span>
- <span data-ttu-id="812cf-480">Uppdatera CONTRIBUTING.md (#11096) (tack @mklement0!)</span><span class="sxs-lookup"><span data-stu-id="812cf-480">Update CONTRIBUTING.md (#11096) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="812cf-481">Åtgärda installations dokument länkar i README.md (#11083)</span><span class="sxs-lookup"><span data-stu-id="812cf-481">Fix installation doc links in README.md (#11083)</span></span>
- <span data-ttu-id="812cf-482">Lägger till exempel i Install-PowerShell. ps1-skriptet (#11024) (tack @kilasuit!)</span><span class="sxs-lookup"><span data-stu-id="812cf-482">Adds examples to install-powershell.ps1 script (#11024) (Thanks @kilasuit!)</span></span>
- <span data-ttu-id="812cf-483">Korrigera för Select-String betoning och import-Dscresource Keyword Supports i CHANGELOG.md (#10890)</span><span class="sxs-lookup"><span data-stu-id="812cf-483">Fix to Select-String emphasis and Import-DscResource in CHANGELOG.md (#10890)</span></span>
- <span data-ttu-id="812cf-484">Ta bort den inaktuella länken från powershell-beginners-guide.md (#10926)</span><span class="sxs-lookup"><span data-stu-id="812cf-484">Remove the stale link from powershell-beginners-guide.md (#10926)</span></span>
- <span data-ttu-id="812cf-485">Sammanfoga stabila och underhålls ändrings loggar (#10527)</span><span class="sxs-lookup"><span data-stu-id="812cf-485">Merge stable and servicing change logs (#10527)</span></span>
- <span data-ttu-id="812cf-486">Uppdatera använda .NET-versionen i build-dokument (#10775) (tack @Greg-Smulko!)</span><span class="sxs-lookup"><span data-stu-id="812cf-486">Update used .NET version in build docs (#10775) (Thanks @Greg-Smulko!)</span></span>
- <span data-ttu-id="812cf-487">Ersätt länkar från MSDN till docs.microsoft.com i powershell-beginners-guide.md (#10778) (tack @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="812cf-487">Replace links from MSDN to docs.microsoft.com in powershell-beginners-guide.md (#10778) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="812cf-488">Korrigera bruten DSC översikts länk (#10702)</span><span class="sxs-lookup"><span data-stu-id="812cf-488">Fix broken DSC overview link (#10702)</span></span>
- <span data-ttu-id="812cf-489">Uppdatera Support_Question. MD för att länka till Stack Overflow som en annan grupp resurs (#10638) (tack @mklement0!)</span><span class="sxs-lookup"><span data-stu-id="812cf-489">Update Support_Question.md to link to Stack Overflow as another community resource (#10638) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="812cf-490">Lägg till processor arkitektur i mallen för distributions förfrågningen (#10661)</span><span class="sxs-lookup"><span data-stu-id="812cf-490">Add processor architecture to distribution request template (#10661)</span></span>
- <span data-ttu-id="812cf-491">Lägg till en ny PowerShell-MoL-bok i Learning PowerShell-dokument (#10602)</span><span class="sxs-lookup"><span data-stu-id="812cf-491">Add new PowerShell MoL book to learning PowerShell docs (#10602)</span></span>
- <span data-ttu-id="812cf-492">Uppdatera README.md och metadata för v 6.1.6 och v 6.2.3-versioner (#10523)</span><span class="sxs-lookup"><span data-stu-id="812cf-492">Update README.md and metadata for v6.1.6 and v6.2.3 releases (#10523)</span></span>
- <span data-ttu-id="812cf-493">Åtgärda ett stavfel i README.md (#10465) (tack @vedhasp!)</span><span class="sxs-lookup"><span data-stu-id="812cf-493">Fix a typo in README.md (#10465) (Thanks @vedhasp!)</span></span>
- <span data-ttu-id="812cf-494">Lägg till en referens till PSKoans-modulen i Learning Resources-dokumentationen (#10369) (tack @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="812cf-494">Add a reference to PSKoans module to Learning Resources documentation (#10369) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="812cf-495">Uppdatera README.md och metadata. JSON för 7.0.0-Preview. 3 (#10393)</span><span class="sxs-lookup"><span data-stu-id="812cf-495">Update README.md and metadata.json for 7.0.0-preview.3 (#10393)</span></span>
