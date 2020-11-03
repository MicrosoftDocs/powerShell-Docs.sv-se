---
description: Beskriver funktionerna i Windows PowerShell för PowerShell 7.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_powershell_compatibility?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_PowerShell_Compatibility
ms.openlocfilehash: 522c9d2169e49584915450813ad28dfc5e0d5ca2
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270135"
---
# <a name="about-windows-powershell-compatibility"></a><span data-ttu-id="e5aeb-104">Om Windows PowerShell-kompatibilitet</span><span class="sxs-lookup"><span data-stu-id="e5aeb-104">About Windows PowerShell compatibility</span></span>

## <a name="short-description"></a><span data-ttu-id="e5aeb-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e5aeb-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="e5aeb-106">Beskriver funktionerna i Windows PowerShell för PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="e5aeb-106">Describes the Windows PowerShell Compatibility functionality for PowerShell 7.</span></span>

## <a name="long-description"></a><span data-ttu-id="e5aeb-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e5aeb-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="e5aeb-108">Om module-manifestet inte anger att modulen är kompatibel med PowerShell Core läses modulerna i `%windir%\system32\WindowsPowerShell\v1.0\Modules` mappen in i en Windows powershell 5,1-process med Windows PowerShell-kompatibilitet.</span><span class="sxs-lookup"><span data-stu-id="e5aeb-108">Unless the module manifest indicates that module is compatible with PowerShell Core, modules in the `%windir%\system32\WindowsPowerShell\v1.0\Modules` folder are loaded in a background Windows PowerShell 5.1 process by Windows PowerShell Compatibility feature.</span></span>

### <a name="using-the-compatibility-feature"></a><span data-ttu-id="e5aeb-109">Använda funktionen kompatibilitet</span><span class="sxs-lookup"><span data-stu-id="e5aeb-109">Using the Compatibility feature</span></span>

<span data-ttu-id="e5aeb-110">När den första modulen importeras med funktionen Windows PowerShell-kompatibilitet, skapar PowerShell en fjärrsession med namnet `WinPSCompatSession` som körs i en bakgrunds process i Windows powershell 5,1.</span><span class="sxs-lookup"><span data-stu-id="e5aeb-110">When the first module is imported using Windows PowerShell Compatibility feature, PowerShell creates a remote session named `WinPSCompatSession` that is running in a background Windows PowerShell 5.1 process.</span></span> <span data-ttu-id="e5aeb-111">Den här processen skapas när funktionen kompatibilitet importerar den första modulen.</span><span class="sxs-lookup"><span data-stu-id="e5aeb-111">This process is created when the Compatibility feature imports the first module.</span></span> <span data-ttu-id="e5aeb-112">Processen stängs när den sista modulen tas bort (med `Remove-Module` ) eller när PowerShell-processen avslutas.</span><span class="sxs-lookup"><span data-stu-id="e5aeb-112">The process is closed when the last such module is removed (using `Remove-Module`) or when PowerShell process exits.</span></span>

<span data-ttu-id="e5aeb-113">Modulerna som läses in i `WinPSCompatSession` sessionen används via implicit fjärr kommunikation och återspeglas i den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="e5aeb-113">The modules loaded in the `WinPSCompatSession` session are used via implicit remoting and reflected into current PowerShell session.</span></span> <span data-ttu-id="e5aeb-114">Detta är samma transport metod som används för PowerShell-jobb.</span><span class="sxs-lookup"><span data-stu-id="e5aeb-114">This is the same transport method used for PowerShell jobs.</span></span>

<span data-ttu-id="e5aeb-115">När en modul importeras till `WinPSCompatSession` sessionen genererar implicit fjärr kommunikation en proxy-modul i användarens `$env:Temp` katalog och importerar denna proxy-modul till den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="e5aeb-115">When a module is imported into the `WinPSCompatSession` session, implicit remoting generates a proxy module in the user's `$env:Temp` directory and imports this proxy module into current PowerShell session.</span></span> <span data-ttu-id="e5aeb-116">Detta gör att PowerShell kan identifiera att modulen har lästs in med Windows PowerShell-kompatibilitet.</span><span class="sxs-lookup"><span data-stu-id="e5aeb-116">This allows PowerShell to detect that the module was loaded using Windows PowerShell Compatibility functionality.</span></span>

<span data-ttu-id="e5aeb-117">När sessionen har skapats kan den användas för åtgärder som inte fungerar korrekt på avserialiserade objekt.</span><span class="sxs-lookup"><span data-stu-id="e5aeb-117">Once the session is created, it can be used for operations that don't work correctly on deserialized objects.</span></span> <span data-ttu-id="e5aeb-118">Hela pipelinen körs i Windows PowerShell och endast det slutliga resultatet returneras.</span><span class="sxs-lookup"><span data-stu-id="e5aeb-118">The entire pipeline is executed in Windows PowerShell and only the final result is returned.</span></span> <span data-ttu-id="e5aeb-119">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="e5aeb-119">For example:</span></span>

```powershell
$s = Get-PSSession -Name WinPSCompatSession
Invoke-Command -Session $s -ScriptBlock {
  "Running in Windows PowerShell version $($PSVersionTable.PSVersion)"
}
```

<span data-ttu-id="e5aeb-120">Funktionen kompatibilitet kan anropas på två sätt:</span><span class="sxs-lookup"><span data-stu-id="e5aeb-120">The Compatibility feature can be invoked in two ways:</span></span>

- <span data-ttu-id="e5aeb-121">Uttryckligen genom att importera en modul med parametern **UseWindowsPowerShell**</span><span class="sxs-lookup"><span data-stu-id="e5aeb-121">Explicitly by importing a module using the **UseWindowsPowerShell** parameter</span></span>

   ```powershell
   Import-Module -Name ScheduledTasks -UseWindowsPowerShell
   ```

- <span data-ttu-id="e5aeb-122">Implicit genom att importera en Windows PowerShell-modul efter Modulnamn, sökväg eller automatisk inläsning via kommando identifiering.</span><span class="sxs-lookup"><span data-stu-id="e5aeb-122">Implicitly by importing a Windows PowerShell module by module name, path, or autoloading via command discovery.</span></span>

   ```powershell
   Import-Module -Name ServerManager
   Get-AppLockerPolicy -Local
   ```

   <span data-ttu-id="e5aeb-123">Om den inte redan har lästs in läses AppLocker-modulen in när du kör  `Get-AppLockerPolicy` .</span><span class="sxs-lookup"><span data-stu-id="e5aeb-123">If not already loaded, the AppLocker module is autoloaded when you run  `Get-AppLockerPolicy`.</span></span>

<span data-ttu-id="e5aeb-124">Windows PowerShell-kompatibilitet inläsning av moduler som anges i `WindowsPowerShellCompatibilityModuleDenyList` inställningen i PowerShell-konfigurationsfilen.</span><span class="sxs-lookup"><span data-stu-id="e5aeb-124">Windows PowerShell Compatibility blocks loading of modules that are listed in the `WindowsPowerShellCompatibilityModuleDenyList` setting in PowerShell configuration file.</span></span>

<span data-ttu-id="e5aeb-125">Standardvärdet för den här inställningen är:</span><span class="sxs-lookup"><span data-stu-id="e5aeb-125">The default value of this setting is:</span></span>

```json
"WindowsPowerShellCompatibilityModuleDenyList":  [
   "PSScheduledJob","BestPractices","UpdateServices"
]
```

### <a name="managing-implicit-module-loading"></a><span data-ttu-id="e5aeb-126">Hantera inläsning av implicit modul</span><span class="sxs-lookup"><span data-stu-id="e5aeb-126">Managing implicit module loading</span></span>

<span data-ttu-id="e5aeb-127">Använd inställningen i en PowerShell-konfigurationsfil om du vill inaktivera funktionen för kompatibilitet med Windows PowerShell för implicit import `DisableImplicitWinCompat` .</span><span class="sxs-lookup"><span data-stu-id="e5aeb-127">To disable implicit import behavior of the Windows PowerShell Compatibility feature, use the `DisableImplicitWinCompat` setting in a PowerShell configuration file.</span></span> <span data-ttu-id="e5aeb-128">Den här inställningen kan läggas till i `powershell.config.json` filen.</span><span class="sxs-lookup"><span data-stu-id="e5aeb-128">This setting can be added to the `powershell.config.json` file.</span></span> <span data-ttu-id="e5aeb-129">Mer information finns i [about_powershell_config](about_powershell_config.md).</span><span class="sxs-lookup"><span data-stu-id="e5aeb-129">For more information, see [about_powershell_config](about_powershell_config.md).</span></span>

<span data-ttu-id="e5aeb-130">Det här exemplet visar hur du skapar en konfigurations fil som inaktiverar funktionen för implicit modul-inläsning av Windows PowerShell-kompatibilitet.</span><span class="sxs-lookup"><span data-stu-id="e5aeb-130">This example shows how to create a configuration file that disables the implicit module-loading feature of Windows PowerShell Compatibility.</span></span>

```powershell
$ConfigPath = "$PSHOME\DisableWinCompat.powershell.config.json"
$ConfigJSON = ConvertTo-Json -InputObject @{
  "DisableImplicitWinCompat" = $true
  "Microsoft.PowerShell:ExecutionPolicy" = "RemoteSigned"
}
$ConfigJSON | Out-File -Force $ConfigPath
pwsh -settingsFile $ConfigPath
```

<span data-ttu-id="e5aeb-131">Mer information om modulens kompatibilitet finns i [PowerShell 7-modulen Compatibility](https://aka.ms/PSModuleCompat) List.</span><span class="sxs-lookup"><span data-stu-id="e5aeb-131">For more the latest information about module compatibility, see the [PowerShell 7 module compatibility](https://aka.ms/PSModuleCompat) list.</span></span>

### <a name="managing-cmdlet-clobbering"></a><span data-ttu-id="e5aeb-132">Clobbering för att hantera cmdlet</span><span class="sxs-lookup"><span data-stu-id="e5aeb-132">Managing cmdlet clobbering</span></span>

<span data-ttu-id="e5aeb-133">Funktionen Windows PowerShell-kompatibilitet använder implicit fjärr kommunikation för att läsa in moduler i kompatibilitetsläge.</span><span class="sxs-lookup"><span data-stu-id="e5aeb-133">The Windows PowerShell Compatibility feature uses implicit remoting to load modules in compatibility mode.</span></span> <span data-ttu-id="e5aeb-134">Resultatet är att kommandon som exporteras av modulen prioriteras framför kommandon i samma namn i den aktuella PowerShell 7-sessionen.</span><span class="sxs-lookup"><span data-stu-id="e5aeb-134">The result is that commands exported by the module take precedence over commands of the same name in the current PowerShell 7 session.</span></span> <span data-ttu-id="e5aeb-135">I PowerShell 7.0.0-versionen inkluderade de viktigaste modulerna som medföljer PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e5aeb-135">In the PowerShell 7.0.0 release, this included the core modules that ship with PowerShell.</span></span>

<span data-ttu-id="e5aeb-136">I PowerShell 7,1 ändrades beteendet så att följande grundläggande PowerShell-moduler inte är clobbered:</span><span class="sxs-lookup"><span data-stu-id="e5aeb-136">In PowerShell 7.1, the behavior was changed so that the following core PowerShell modules are not clobbered:</span></span>

- <span data-ttu-id="e5aeb-137">Microsoft. PowerShell. ConsoleHost</span><span class="sxs-lookup"><span data-stu-id="e5aeb-137">Microsoft.PowerShell.ConsoleHost</span></span>
- <span data-ttu-id="e5aeb-138">Microsoft. PowerShell. Diagnostics</span><span class="sxs-lookup"><span data-stu-id="e5aeb-138">Microsoft.PowerShell.Diagnostics</span></span>
- <span data-ttu-id="e5aeb-139">Microsoft. PowerShell. Host</span><span class="sxs-lookup"><span data-stu-id="e5aeb-139">Microsoft.PowerShell.Host</span></span>
- <span data-ttu-id="e5aeb-140">Microsoft. PowerShell. Management</span><span class="sxs-lookup"><span data-stu-id="e5aeb-140">Microsoft.PowerShell.Management</span></span>
- <span data-ttu-id="e5aeb-141">Microsoft. PowerShell. Security</span><span class="sxs-lookup"><span data-stu-id="e5aeb-141">Microsoft.PowerShell.Security</span></span>
- <span data-ttu-id="e5aeb-142">Microsoft.PowerShell.Utility</span><span class="sxs-lookup"><span data-stu-id="e5aeb-142">Microsoft.PowerShell.Utility</span></span>
- <span data-ttu-id="e5aeb-143">Microsoft. WSMan. Management</span><span class="sxs-lookup"><span data-stu-id="e5aeb-143">Microsoft.WSMan.Management</span></span>

<span data-ttu-id="e5aeb-144">PowerShell 7,1 har också lagt till möjligheten att lista ytterligare moduler som inte ska vara clobbered i kompatibilitetsläge.</span><span class="sxs-lookup"><span data-stu-id="e5aeb-144">PowerShell 7.1 also added the ability to list additional modules that should not be clobbered by compatibility mode.</span></span>

<span data-ttu-id="e5aeb-145">Du kan lägga till `WindowsPowerShellCompatibilityNoClobberModuleList` inställningen i PowerShell-konfigurationsfilen.</span><span class="sxs-lookup"><span data-stu-id="e5aeb-145">You can add the `WindowsPowerShellCompatibilityNoClobberModuleList` setting to PowerShell configuration file.</span></span> <span data-ttu-id="e5aeb-146">Värdet för den här inställningen är en kommaavgränsad lista med modulnamn.</span><span class="sxs-lookup"><span data-stu-id="e5aeb-146">The value of this setting is a comma-separated list of module names.</span></span> <span data-ttu-id="e5aeb-147">Standardvärdet för den här inställningen är:</span><span class="sxs-lookup"><span data-stu-id="e5aeb-147">The default value of this setting is:</span></span>

```json
"WindowsPowerShellCompatibilityNoClobberModuleList": [ ]
```

## <a name="limitations"></a><span data-ttu-id="e5aeb-148">Begränsningar</span><span class="sxs-lookup"><span data-stu-id="e5aeb-148">Limitations</span></span>

<span data-ttu-id="e5aeb-149">Funktionen Windows PowerShell-kompatibilitet:</span><span class="sxs-lookup"><span data-stu-id="e5aeb-149">The Windows PowerShell Compatibility functionality:</span></span>

1. <span data-ttu-id="e5aeb-150">Fungerar endast lokalt på Windows-datorer</span><span class="sxs-lookup"><span data-stu-id="e5aeb-150">Only works locally on Windows computers</span></span>
1. <span data-ttu-id="e5aeb-151">Kräver att Windows PowerShell 5,1</span><span class="sxs-lookup"><span data-stu-id="e5aeb-151">Requires that Windows PowerShell 5.1</span></span>
1. <span data-ttu-id="e5aeb-152">Körs på serialiserade cmdlet-parametrar och retur värden, inte på Live-objekt</span><span class="sxs-lookup"><span data-stu-id="e5aeb-152">Operates on serialized cmdlet parameters and return values, not on live objects</span></span>
1. <span data-ttu-id="e5aeb-153">Alla moduler som importer ATS till Windows PowerShell-fjärrsessionen delar samma körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="e5aeb-153">All modules imported into the Windows PowerShell remoting session share the same runspace.</span></span>

## <a name="keywords"></a><span data-ttu-id="e5aeb-154">Nyckelord</span><span class="sxs-lookup"><span data-stu-id="e5aeb-154">Keywords</span></span>

<span data-ttu-id="e5aeb-155">about_Windows_PowerShell_Compatibility</span><span class="sxs-lookup"><span data-stu-id="e5aeb-155">about_Windows_PowerShell_Compatibility</span></span>

## <a name="see-also"></a><span data-ttu-id="e5aeb-156">Se även</span><span class="sxs-lookup"><span data-stu-id="e5aeb-156">See also</span></span>

[<span data-ttu-id="e5aeb-157">about_Modules</span><span class="sxs-lookup"><span data-stu-id="e5aeb-157">about_Modules</span></span>](about_Modules.md)

[<span data-ttu-id="e5aeb-158">Importera-modul</span><span class="sxs-lookup"><span data-stu-id="e5aeb-158">Import-Module</span></span>](xref:Microsoft.PowerShell.Core.Import-Module)

