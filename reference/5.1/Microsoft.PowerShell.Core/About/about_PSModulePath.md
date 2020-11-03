---
description: Miljövariabeln PSModulePath innehåller en lista över mappar som genomsöks för att hitta moduler och resurser.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_PSModulePath?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSModulePath
ms.openlocfilehash: 60373e534fb319195c187b8cb26c6aabc0f3b8b7
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271526"
---
# <a name="about-psmodulepath"></a><span data-ttu-id="83181-104">Om PSModulePath</span><span class="sxs-lookup"><span data-stu-id="83181-104">About PSModulePath</span></span>

<span data-ttu-id="83181-105">`$env:PSModulePath`Miljövariabeln innehåller en lista över mappar som genomsöks för att hitta moduler och resurser.</span><span class="sxs-lookup"><span data-stu-id="83181-105">The `$env:PSModulePath` environment variable contains a list of folder locations that are searched to find modules and resources.</span></span>

<span data-ttu-id="83181-106">Som standard är de effektiva platser som `$env:PSModulePath` är tilldelade:</span><span class="sxs-lookup"><span data-stu-id="83181-106">By default, the effective locations assigned to `$env:PSModulePath` are:</span></span>

- <span data-ttu-id="83181-107">Platser i hela systemet: dessa mappar innehåller moduler som levereras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="83181-107">System-wide locations: These folders contain modules that ship with PowerShell.</span></span> <span data-ttu-id="83181-108">Dessa moduler lagras i `$PSHOME\Modules` mappen.</span><span class="sxs-lookup"><span data-stu-id="83181-108">These modules are store in the `$PSHOME\Modules` folder.</span></span> <span data-ttu-id="83181-109">Detta är även platsen där Windows Management-moduler är installerade.</span><span class="sxs-lookup"><span data-stu-id="83181-109">This is also the location where the Windows management modules are installed.</span></span>

- <span data-ttu-id="83181-110">Användare-installerade moduler: de här är moduler som installeras av användaren.</span><span class="sxs-lookup"><span data-stu-id="83181-110">User-installed modules: These are modules installed by the user.</span></span>
  <span data-ttu-id="83181-111">`Install-Module` har en **omfattnings** parameter som gör att du kan ange om modulen är installerad för den aktuella användaren eller för alla användare.</span><span class="sxs-lookup"><span data-stu-id="83181-111">`Install-Module` has a **Scope** parameter that allows you to specify whether the module is installed for the current user or for all users.</span></span> <span data-ttu-id="83181-112">Mer information finns i [install-module](xref:PowerShellGet.Install-Module).</span><span class="sxs-lookup"><span data-stu-id="83181-112">For more information, see [Install-Module](xref:PowerShellGet.Install-Module).</span></span>

  - <span data-ttu-id="83181-113">I Windows är platsen för det användarspecifika **CurrentUser** -omfånget `$HOME\Documents\PowerShell\Modules` mappen.</span><span class="sxs-lookup"><span data-stu-id="83181-113">On Windows, the location of the user-specific **CurrentUser** scope is the `$HOME\Documents\PowerShell\Modules` folder.</span></span> <span data-ttu-id="83181-114">Platsen för **allusers** -omfattningen är `$env:ProgramFiles\PowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="83181-114">The location of the **AllUsers** scope is `$env:ProgramFiles\PowerShell\Modules`.</span></span>
  - <span data-ttu-id="83181-115">På andra datorer än Windows-system är platsen för det användarspecifika **CurrentUser** -omfånget `$HOME/.local/share/powershell/Modules` mappen.</span><span class="sxs-lookup"><span data-stu-id="83181-115">On non-Windows systems, the location of the user-specific **CurrentUser** scope is the `$HOME/.local/share/powershell/Modules` folder.</span></span> <span data-ttu-id="83181-116">Platsen för **allusers** -omfattningen är `/usr/local/share/powershell/Modules` .</span><span class="sxs-lookup"><span data-stu-id="83181-116">The location of the **AllUsers** scope is `/usr/local/share/powershell/Modules`.</span></span>

<span data-ttu-id="83181-117">Dessutom kan installations program som installerar moduler i andra kataloger, till exempel katalogen program filer, lägga till sina platser till värdet `$env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="83181-117">In addition, setup programs that install modules in other directories, such as the Program Files directory, can append their locations to the value of `$env:PSModulePath`.</span></span>

> [!NOTE]
> <span data-ttu-id="83181-118">På Windows är den användarspecifika platsen den `PowerShell\Modules` mapp som finns i mappen **dokument** i din användar profil.</span><span class="sxs-lookup"><span data-stu-id="83181-118">On Windows, the user-specific location is the `PowerShell\Modules` folder located in the **Documents** folder in your user profile.</span></span> <span data-ttu-id="83181-119">Den angivna sökvägen till platsen varierar efter Windows-version och om du använder mappomdirigering.</span><span class="sxs-lookup"><span data-stu-id="83181-119">The specific path of that location varies by version of Windows and whether or not you are using folder redirection.</span></span> <span data-ttu-id="83181-120">Microsoft OneDrive kan också ändra platsen för mappen **dokument** .</span><span class="sxs-lookup"><span data-stu-id="83181-120">Microsoft OneDrive can also change the location of your **Documents** folder.</span></span> <span data-ttu-id="83181-121">Du kan kontrol lera platsen för mappen **dokument** med hjälp av följande kommando: `[Environment]::GetFolderPath('MyDocuments')` .</span><span class="sxs-lookup"><span data-stu-id="83181-121">You can verify the location of your **Documents** folder using the following command: `[Environment]::GetFolderPath('MyDocuments')`.</span></span>

## <a name="modifying-psmodulepath"></a><span data-ttu-id="83181-122">Ändra PSModulePath</span><span class="sxs-lookup"><span data-stu-id="83181-122">Modifying PSModulePath</span></span>

<span data-ttu-id="83181-123">Om du vill ändra standardmodulens kataloger för den aktuella sessionen använder du följande kommando format för att ändra värdet för `PSModulePath` miljö variabeln.</span><span class="sxs-lookup"><span data-stu-id="83181-123">To change the default module directories for the current session, use the following command format to change the value of the `PSModulePath` environment variable.</span></span>

<span data-ttu-id="83181-124">Om du till exempel vill lägga till `C:\Program Files\Fabrikam\Modules` katalogen till värdet för PSModulePath-miljövariabeln, skriver du:</span><span class="sxs-lookup"><span data-stu-id="83181-124">For example, to add the `C:\Program Files\Fabrikam\Modules` directory to the value of the PSModulePath environment variable, type:</span></span>

```powershell
$Env:PSModulePath = $Env:PSModulePath+";C:\Program Files\Fabrikam\Modules"
```

<span data-ttu-id="83181-125">Semikolon ( `;` ) i kommandot avgränsar den nya sökvägen från den sökväg som föregår den i listan.</span><span class="sxs-lookup"><span data-stu-id="83181-125">The semi-colon (`;`) in the command separates the new path from the path that precedes it in the list.</span></span> <span data-ttu-id="83181-126">På andra plattformar än Windows-plattformar `:` separerar kolon () Sök vägarna i miljö variabeln.</span><span class="sxs-lookup"><span data-stu-id="83181-126">On non-Windows platforms, the colon (`:`) separates the path locations in the environment variable.</span></span>

<span data-ttu-id="83181-127">Om du vill ändra värdet för `PSModulePath` i varje session lägger du till föregående kommando i din PowerShell-profil eller använder **SetEnvironmentVariable** -metoden i **miljö** klassen.</span><span class="sxs-lookup"><span data-stu-id="83181-127">To change the value of `PSModulePath` in every session, add the previous command to your PowerShell profile or use the **SetEnvironmentVariable** method of the **Environment** class.</span></span>

<span data-ttu-id="83181-128">Följande kommando använder metoden **GetEnvironmentVariable** för att hämta dator inställningen för `PSModulePath` och metoden **SetEnvironmentVariable** för att lägga till `C:\Program Files\Fabrikam\Modules` sökvägen till värdet.</span><span class="sxs-lookup"><span data-stu-id="83181-128">The following command uses the **GetEnvironmentVariable** method to get the machine setting of `PSModulePath` and the **SetEnvironmentVariable** method to add the `C:\Program Files\Fabrikam\Modules` path to the value.</span></span>

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'Machine')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable('PSModulePath', $newpath, 'Machine')
```

<span data-ttu-id="83181-129">Om du vill lägga till en sökväg till användar inställningen ändrar du värdet för mål till **användare**.</span><span class="sxs-lookup"><span data-stu-id="83181-129">To add a path to the user setting, change the target value to **User**.</span></span>

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'User')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable('PSModulePath', $newpath, 'User')
```

<span data-ttu-id="83181-130">Mer information om metoderna i klassen **system. miljö** finns i [miljö metoder](/dotnet/api/system.environment).</span><span class="sxs-lookup"><span data-stu-id="83181-130">For more information about the methods of the **System.Environment** class, see [Environment Methods](/dotnet/api/system.environment).</span></span>

## <a name="powershell-psmodulepath-construction"></a><span data-ttu-id="83181-131">PowerShell-PSModulePath konstruktion</span><span class="sxs-lookup"><span data-stu-id="83181-131">PowerShell PSModulePath construction</span></span>

<span data-ttu-id="83181-132">Värdet för `$env:PSModulePath` konstrueras varje gången PowerShell startar.</span><span class="sxs-lookup"><span data-stu-id="83181-132">The value of `$env:PSModulePath` is constructed each time PowerShell starts.</span></span>
<span data-ttu-id="83181-133">Värdet varierar efter version av PowerShell och hur det startas.</span><span class="sxs-lookup"><span data-stu-id="83181-133">The value varies by version of PowerShell and how it is launched.</span></span>

### <a name="windows-powershell-startup"></a><span data-ttu-id="83181-134">Windows PowerShell-start</span><span class="sxs-lookup"><span data-stu-id="83181-134">Windows PowerShell startup</span></span>

<span data-ttu-id="83181-135">Windows PowerShell använder följande logik för att skapa `PSModulePath` vid start:</span><span class="sxs-lookup"><span data-stu-id="83181-135">Windows PowerShell uses the following logic to construct the `PSModulePath` at startup:</span></span>

- <span data-ttu-id="83181-136">Om `PSModulePath` det inte finns, kombinera **CurrentUser** , **allusers** och `$PSHOME` modulens sökvägar</span><span class="sxs-lookup"><span data-stu-id="83181-136">If `PSModulePath` doesn't exist, combine **CurrentUser** , **AllUsers** , and the `$PSHOME` modules paths</span></span>
- <span data-ttu-id="83181-137">IF `PSModulePath` finns:</span><span class="sxs-lookup"><span data-stu-id="83181-137">If `PSModulePath` does exist:</span></span>
  - <span data-ttu-id="83181-138">Om `PSModulePath` innehåller en `$PSHOME` sökväg för moduler:</span><span class="sxs-lookup"><span data-stu-id="83181-138">If `PSModulePath` contains `$PSHOME` modules path:</span></span>
    - <span data-ttu-id="83181-139">Sökvägen till **allusers** -moduler infogas före `$PSHOME` sökvägen till moduler</span><span class="sxs-lookup"><span data-stu-id="83181-139">**AllUsers** modules path is inserted before `$PSHOME` modules path</span></span>
  - <span data-ttu-id="83181-140">tilläggs</span><span class="sxs-lookup"><span data-stu-id="83181-140">else:</span></span>
    - <span data-ttu-id="83181-141">Används bara `PSModulePath` enligt definitionen eftersom användaren medvetet tog bort `$PSHOME` platsen</span><span class="sxs-lookup"><span data-stu-id="83181-141">Just use `PSModulePath` as defined since the user deliberately removed the `$PSHOME` location</span></span>

<span data-ttu-id="83181-142">**CurrentUser** module-sökvägen är för fast fast endast om användar omfånget `$env:PSModulePath` inte finns.</span><span class="sxs-lookup"><span data-stu-id="83181-142">The **CurrentUser** module path is prefixed only if User scope `$env:PSModulePath` doesn't exist.</span></span> <span data-ttu-id="83181-143">Annars används användar omfånget `$env:PSModulePath` enligt definitionen.</span><span class="sxs-lookup"><span data-stu-id="83181-143">Otherwise, the User scope `$env:PSModulePath` is used as defined.</span></span>

### <a name="powershell-core-6-startup"></a><span data-ttu-id="83181-144">PowerShell Core 6-start</span><span class="sxs-lookup"><span data-stu-id="83181-144">PowerShell Core 6 startup</span></span>

<span data-ttu-id="83181-145">PowerShell Core 6 använder inte innehåll i `$env:PSModulePath` om den upptäcker att den har startats från PowerShell.</span><span class="sxs-lookup"><span data-stu-id="83181-145">PowerShell Core 6 doesn't use contents of `$env:PSModulePath` if it detects it was started from PowerShell.</span></span> <span data-ttu-id="83181-146">Den skriver över den med:</span><span class="sxs-lookup"><span data-stu-id="83181-146">It overwrites it with:</span></span>

- <span data-ttu-id="83181-147">**CurrentUser** modules sökväg + **allusers** modules sökväg + `$PSHOME` moduler sökväg + sökväg för Windows PowerShell- `$PSHOME` moduler.</span><span class="sxs-lookup"><span data-stu-id="83181-147">**CurrentUser** modules path + **AllUsers** modules path + `$PSHOME` modules path + Windows PowerShell `$PSHOME` modules path.</span></span>

### <a name="powershell-7-startup"></a><span data-ttu-id="83181-148">PowerShell 7-Start</span><span class="sxs-lookup"><span data-stu-id="83181-148">PowerShell 7 startup</span></span>

<span data-ttu-id="83181-149">I Windows, för de flesta miljövariabler, använder en ny process bara det värdet även om det finns en dator som omfattas av samma namn för de flesta miljövariabler.</span><span class="sxs-lookup"><span data-stu-id="83181-149">In Windows, for most environment variables, if the User-scoped variable exists, a new process uses that value only even if a Machine-scoped variable of the same name exists.</span></span>

<span data-ttu-id="83181-150">I PowerShell 7 `PSModulePath` behandlas liknande hur `Path` miljövariabeln behandlas i Windows.</span><span class="sxs-lookup"><span data-stu-id="83181-150">In PowerShell 7, `PSModulePath` is treated similar to how the `Path` environment variable is treated on Windows.</span></span> <span data-ttu-id="83181-151">I Windows `Path` behandlas det annorlunda jämfört med andra miljövariabler.</span><span class="sxs-lookup"><span data-stu-id="83181-151">On Windows, `Path` is treated differently from other environment variables.</span></span> <span data-ttu-id="83181-152">När en process startas kombinerar Windows den användare som omfattas av `Path` datorns omfång `Path` .</span><span class="sxs-lookup"><span data-stu-id="83181-152">When a process is started, Windows combines the User-scoped `Path` with the Machine-scoped `Path`.</span></span>

- <span data-ttu-id="83181-153">Hämta användar omfattningen `PSModulePath`</span><span class="sxs-lookup"><span data-stu-id="83181-153">Retrieve the User-scoped `PSModulePath`</span></span>
- <span data-ttu-id="83181-154">Jämför med att bearbeta en ärvd `PSModulePath` miljö variabel</span><span class="sxs-lookup"><span data-stu-id="83181-154">Compare to process inherited `PSModulePath` environment variable</span></span>
  - <span data-ttu-id="83181-155">Om samma:</span><span class="sxs-lookup"><span data-stu-id="83181-155">If the same:</span></span>
    - <span data-ttu-id="83181-156">Lägg till **allusers** `PSModulePath` till slutet efter semantiken för `Path` miljö variabeln</span><span class="sxs-lookup"><span data-stu-id="83181-156">Append the **AllUsers** `PSModulePath` to the end following the semantics of the `Path` environment variable</span></span>
    - <span data-ttu-id="83181-157">Windows- `System32` sökvägen kommer från den dator som definierats `PSModulePath` så behöver inte uttryckligen läggas till</span><span class="sxs-lookup"><span data-stu-id="83181-157">The Windows `System32` path comes from the machine defined `PSModulePath` so does not need to be added explicitly</span></span>
  - <span data-ttu-id="83181-158">Om det skiljer sig, behandla som om användaren uttryckligen ändrade den och inte lägger till **allusers**`PSModulePath`</span><span class="sxs-lookup"><span data-stu-id="83181-158">If different, treat as though user explicitly modified it and don't append **AllUsers** `PSModulePath`</span></span>
- <span data-ttu-id="83181-159">Prefix med PS7-användare, system och `$PSHOME` sökvägar i den ordningen</span><span class="sxs-lookup"><span data-stu-id="83181-159">Prefix with PS7 User, System, and `$PSHOME` paths in that order</span></span>
  - <span data-ttu-id="83181-160">Om `powershell.config.json` innehåller en användare `PSModulePath` som är begränsad använder du den i stället för standardvärdet för användaren</span><span class="sxs-lookup"><span data-stu-id="83181-160">If `powershell.config.json` contains a user scoped `PSModulePath`, use that instead of the default for the user</span></span>
  - <span data-ttu-id="83181-161">Om `powershell.config.json` innehåller ett system område `PSModulePath` använder du det i stället för standardvärdet för systemet</span><span class="sxs-lookup"><span data-stu-id="83181-161">If `powershell.config.json` contains a system scoped `PSModulePath`, use that instead of the default for the system</span></span>

<span data-ttu-id="83181-162">UNIX-system har ingen åtskillnad mellan användar-och systemmiljövariabler.</span><span class="sxs-lookup"><span data-stu-id="83181-162">Unix systems don't have a separation of User and System environment variables.</span></span>
<span data-ttu-id="83181-163">`PSModulePath` ärvs och PS7 sökvägar är före fast om de inte redan har definierats.</span><span class="sxs-lookup"><span data-stu-id="83181-163">`PSModulePath` is inherited and the PS7-specific paths are prefixed if not already defined.</span></span>

### <a name="starting-windows-powershell-from-powershell-7"></a><span data-ttu-id="83181-164">Starta Windows PowerShell från PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="83181-164">Starting Windows PowerShell from PowerShell 7</span></span>

<span data-ttu-id="83181-165">I den här diskussionen innebär _Windows PowerShell_ både `powershell.exe` och `powershell_ise.exe` .</span><span class="sxs-lookup"><span data-stu-id="83181-165">For this discussion, _Windows PowerShell_ means both `powershell.exe` and `powershell_ise.exe`.</span></span>

<span data-ttu-id="83181-166">Värdet för `$env:PSModulePath` kopieras till `WinPSModulePath` med följande ändringar:</span><span class="sxs-lookup"><span data-stu-id="83181-166">The value of `$env:PSModulePath` is copied to `WinPSModulePath` with the following modifications:</span></span>

- <span data-ttu-id="83181-167">Ta bort PS7 sökväg till användar modulen</span><span class="sxs-lookup"><span data-stu-id="83181-167">Remove PS7 the User module path</span></span>
- <span data-ttu-id="83181-168">Ta bort PS7-sökvägen till system-modulen</span><span class="sxs-lookup"><span data-stu-id="83181-168">Remove PS7 the System module path</span></span>
- <span data-ttu-id="83181-169">Ta bort PS7 `$PSHOME`</span><span class="sxs-lookup"><span data-stu-id="83181-169">Remove PS7 the `$PSHOME` module path</span></span>

<span data-ttu-id="83181-170">PS7-sökvägarna tas bort så att PS7-moduler inte kan läsas in i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="83181-170">The PS7 paths are removed so that PS7 modules don't get loaded in Windows PowerShell.</span></span> <span data-ttu-id="83181-171">`WinPSModulePath`Värdet används när du startar Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="83181-171">The `WinPSModulePath` value is used when starting Windows PowerShell.</span></span>

### <a name="starting-powershell-7-from-windows-powershell"></a><span data-ttu-id="83181-172">Starta PowerShell 7 från Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="83181-172">Starting PowerShell 7 from Windows PowerShell</span></span>

<span data-ttu-id="83181-173">PowerShell 7-starten fortsätter i befintligt skick med att ärva sökvägar som har lagts till i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="83181-173">The PowerShell 7 startup continues as-is with the addition of inheriting paths that Windows PowerShell added.</span></span> <span data-ttu-id="83181-174">Eftersom PS7 sökvägar är i förväg finns det inget funktionellt problem.</span><span class="sxs-lookup"><span data-stu-id="83181-174">Since the PS7-specific paths are prefixed, there is no functional issue.</span></span>

### <a name="starting-powershell-6-from-powershell-7"></a><span data-ttu-id="83181-175">Starta PowerShell 6 från PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="83181-175">Starting PowerShell 6 from PowerShell 7</span></span>

<span data-ttu-id="83181-176">PowerShell Core 6 skriver över `$env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="83181-176">PowerShell Core 6 overwrites `$env:PSModulePath`.</span></span> <span data-ttu-id="83181-177">Inga ändringar har gjorts.</span><span class="sxs-lookup"><span data-stu-id="83181-177">No changes are made.</span></span>

### <a name="starting-powershell-7-from-powershell-6"></a><span data-ttu-id="83181-178">Starta PowerShell 7 från PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="83181-178">Starting PowerShell 7 from PowerShell 6</span></span>

<span data-ttu-id="83181-179">PowerShell 7-starten fortsätter i befintligt skick med att ärva sökvägar som PowerShell Core 6 lagt till.</span><span class="sxs-lookup"><span data-stu-id="83181-179">The PowerShell 7 startup continues as-is with the addition of inheriting paths that PowerShell Core 6 added.</span></span> <span data-ttu-id="83181-180">Eftersom PS7 sökvägar är i förväg finns det inget funktionellt problem.</span><span class="sxs-lookup"><span data-stu-id="83181-180">Since the PS7-specific paths are prefixed, there is no functional issue.</span></span>

## <a name="see-also"></a><span data-ttu-id="83181-181">Se även</span><span class="sxs-lookup"><span data-stu-id="83181-181">See also</span></span>

- [<span data-ttu-id="83181-182">about_Modules</span><span class="sxs-lookup"><span data-stu-id="83181-182">about_Modules</span></span>](about_Modules.md)
- [<span data-ttu-id="83181-183">Miljö metoder</span><span class="sxs-lookup"><span data-stu-id="83181-183">Environment Methods</span></span>](/dotnet/api/system.environment)
