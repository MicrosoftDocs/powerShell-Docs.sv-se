---
description: Miljövariabeln PSModulePath innehåller en lista över mappar som genomsöks för att hitta moduler och resurser.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_PSModulePath?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSModulePath
ms.openlocfilehash: c3a64cf3602d1a2c3acd1c4478cd61943c0f020f
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524393"
---
# <a name="about-psmodulepath"></a><span data-ttu-id="ea5a6-104">Om PSModulePath</span><span class="sxs-lookup"><span data-stu-id="ea5a6-104">About PSModulePath</span></span>

<span data-ttu-id="ea5a6-105">`$env:PSModulePath`Miljövariabeln innehåller en lista över mappar som genomsöks för att hitta moduler och resurser.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-105">The `$env:PSModulePath` environment variable contains a list of folder locations that are searched to find modules and resources.</span></span> <span data-ttu-id="ea5a6-106">PowerShell söker rekursivt igenom varje mapp efter modul ( `.psd1` eller `.psm1` ) filer.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-106">PowerShell recursively searches each folder for module (`.psd1` or `.psm1`) files.</span></span>

<span data-ttu-id="ea5a6-107">Som standard är de effektiva platser som `$env:PSModulePath` är tilldelade:</span><span class="sxs-lookup"><span data-stu-id="ea5a6-107">By default, the effective locations assigned to `$env:PSModulePath` are:</span></span>

- <span data-ttu-id="ea5a6-108">Platser i hela systemet: dessa mappar innehåller moduler som levereras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-108">System-wide locations: These folders contain modules that ship with PowerShell.</span></span> <span data-ttu-id="ea5a6-109">Dessa moduler lagras i `$PSHOME\Modules` mappen.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-109">These modules are store in the `$PSHOME\Modules` folder.</span></span> <span data-ttu-id="ea5a6-110">Detta är även platsen där Windows Management-moduler är installerade.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-110">This is also the location where the Windows management modules are installed.</span></span>

- <span data-ttu-id="ea5a6-111">Användare-installerade moduler: de här är moduler som installeras av användaren.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-111">User-installed modules: These are modules installed by the user.</span></span>
  <span data-ttu-id="ea5a6-112">`Install-Module` har en **omfattnings** parameter som gör att du kan ange om modulen är installerad för den aktuella användaren eller för alla användare.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-112">`Install-Module` has a **Scope** parameter that allows you to specify whether the module is installed for the current user or for all users.</span></span> <span data-ttu-id="ea5a6-113">Mer information finns i [install-module](xref:PowerShellGet.Install-Module).</span><span class="sxs-lookup"><span data-stu-id="ea5a6-113">For more information, see [Install-Module](xref:PowerShellGet.Install-Module).</span></span>

  - <span data-ttu-id="ea5a6-114">I Windows är platsen för det användarspecifika **CurrentUser** -omfånget `$HOME\Documents\PowerShell\Modules` mappen.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-114">On Windows, the location of the user-specific **CurrentUser** scope is the `$HOME\Documents\PowerShell\Modules` folder.</span></span> <span data-ttu-id="ea5a6-115">Platsen för **allusers** -omfattningen är `$env:ProgramFiles\PowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="ea5a6-115">The location of the **AllUsers** scope is `$env:ProgramFiles\PowerShell\Modules`.</span></span>
  - <span data-ttu-id="ea5a6-116">På andra datorer än Windows-system är platsen för det användarspecifika **CurrentUser** -omfånget `$HOME/.local/share/powershell/Modules` mappen.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-116">On non-Windows systems, the location of the user-specific **CurrentUser** scope is the `$HOME/.local/share/powershell/Modules` folder.</span></span> <span data-ttu-id="ea5a6-117">Platsen för **allusers** -omfattningen är `/usr/local/share/powershell/Modules` .</span><span class="sxs-lookup"><span data-stu-id="ea5a6-117">The location of the **AllUsers** scope is `/usr/local/share/powershell/Modules`.</span></span>

<span data-ttu-id="ea5a6-118">Dessutom kan installations program som installerar moduler i andra kataloger, till exempel katalogen program filer, lägga till sina platser till värdet `$env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="ea5a6-118">In addition, setup programs that install modules in other directories, such as the Program Files directory, can append their locations to the value of `$env:PSModulePath`.</span></span>

> [!NOTE]
> <span data-ttu-id="ea5a6-119">På Windows är den användarspecifika platsen den `PowerShell\Modules` mapp som finns i mappen **dokument** i din användar profil.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-119">On Windows, the user-specific location is the `PowerShell\Modules` folder located in the **Documents** folder in your user profile.</span></span> <span data-ttu-id="ea5a6-120">Den angivna sökvägen till platsen varierar efter Windows-version och om du använder mappomdirigering.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-120">The specific path of that location varies by version of Windows and whether or not you are using folder redirection.</span></span> <span data-ttu-id="ea5a6-121">Microsoft OneDrive kan också ändra platsen för mappen **dokument** .</span><span class="sxs-lookup"><span data-stu-id="ea5a6-121">Microsoft OneDrive can also change the location of your **Documents** folder.</span></span> <span data-ttu-id="ea5a6-122">Du kan kontrol lera platsen för mappen **dokument** med hjälp av följande kommando: `[Environment]::GetFolderPath('MyDocuments')` .</span><span class="sxs-lookup"><span data-stu-id="ea5a6-122">You can verify the location of your **Documents** folder using the following command: `[Environment]::GetFolderPath('MyDocuments')`.</span></span>

## <a name="modifying-psmodulepath"></a><span data-ttu-id="ea5a6-123">Ändra PSModulePath</span><span class="sxs-lookup"><span data-stu-id="ea5a6-123">Modifying PSModulePath</span></span>

<span data-ttu-id="ea5a6-124">Om du vill ändra standardmodulens kataloger för den aktuella sessionen använder du följande kommando format för att ändra värdet för `PSModulePath` miljö variabeln.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-124">To change the default module directories for the current session, use the following command format to change the value of the `PSModulePath` environment variable.</span></span>

<span data-ttu-id="ea5a6-125">Om du till exempel vill lägga till `C:\Program Files\Fabrikam\Modules` katalogen till värdet för PSModulePath-miljövariabeln, skriver du:</span><span class="sxs-lookup"><span data-stu-id="ea5a6-125">For example, to add the `C:\Program Files\Fabrikam\Modules` directory to the value of the PSModulePath environment variable, type:</span></span>

```powershell
$Env:PSModulePath = $Env:PSModulePath+";C:\Program Files\Fabrikam\Modules"
```

<span data-ttu-id="ea5a6-126">Semikolon ( `;` ) i kommandot avgränsar den nya sökvägen från den sökväg som föregår den i listan.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-126">The semi-colon (`;`) in the command separates the new path from the path that precedes it in the list.</span></span> <span data-ttu-id="ea5a6-127">På andra plattformar än Windows-plattformar `:` separerar kolon () Sök vägarna i miljö variabeln.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-127">On non-Windows platforms, the colon (`:`) separates the path locations in the environment variable.</span></span>

<span data-ttu-id="ea5a6-128">Om du vill ändra värdet för `PSModulePath` i varje session lägger du till föregående kommando i din PowerShell-profil eller använder **SetEnvironmentVariable** -metoden i **miljö** klassen.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-128">To change the value of `PSModulePath` in every session, add the previous command to your PowerShell profile or use the **SetEnvironmentVariable** method of the **Environment** class.</span></span>

<span data-ttu-id="ea5a6-129">Följande kommando använder metoden **GetEnvironmentVariable** för att hämta dator inställningen för `PSModulePath` och metoden **SetEnvironmentVariable** för att lägga till `C:\Program Files\Fabrikam\Modules` sökvägen till värdet.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-129">The following command uses the **GetEnvironmentVariable** method to get the machine setting of `PSModulePath` and the **SetEnvironmentVariable** method to add the `C:\Program Files\Fabrikam\Modules` path to the value.</span></span>

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'Machine')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable('PSModulePath', $newpath, 'Machine')
```

<span data-ttu-id="ea5a6-130">Om du vill lägga till en sökväg till användar inställningen ändrar du värdet för mål till **användare**.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-130">To add a path to the user setting, change the target value to **User**.</span></span>

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'User')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable('PSModulePath', $newpath, 'User')
```

<span data-ttu-id="ea5a6-131">Mer information om metoderna i klassen **system. miljö** finns i [miljö metoder](/dotnet/api/system.environment).</span><span class="sxs-lookup"><span data-stu-id="ea5a6-131">For more information about the methods of the **System.Environment** class, see [Environment Methods](/dotnet/api/system.environment).</span></span>

## <a name="powershell-psmodulepath-construction"></a><span data-ttu-id="ea5a6-132">PowerShell-PSModulePath konstruktion</span><span class="sxs-lookup"><span data-stu-id="ea5a6-132">PowerShell PSModulePath construction</span></span>

<span data-ttu-id="ea5a6-133">Värdet för `$env:PSModulePath` konstrueras varje gången PowerShell startar.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-133">The value of `$env:PSModulePath` is constructed each time PowerShell starts.</span></span>
<span data-ttu-id="ea5a6-134">Värdet varierar efter version av PowerShell och hur det startas.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-134">The value varies by version of PowerShell and how it is launched.</span></span>

### <a name="windows-powershell-startup"></a><span data-ttu-id="ea5a6-135">Windows PowerShell-start</span><span class="sxs-lookup"><span data-stu-id="ea5a6-135">Windows PowerShell startup</span></span>

<span data-ttu-id="ea5a6-136">Windows PowerShell använder följande logik för att skapa `PSModulePath` vid start:</span><span class="sxs-lookup"><span data-stu-id="ea5a6-136">Windows PowerShell uses the following logic to construct the `PSModulePath` at startup:</span></span>

- <span data-ttu-id="ea5a6-137">Om `PSModulePath` det inte finns, kombinera **CurrentUser** , **allusers** och `$PSHOME` modulens sökvägar</span><span class="sxs-lookup"><span data-stu-id="ea5a6-137">If `PSModulePath` doesn't exist, combine **CurrentUser** , **AllUsers** , and the `$PSHOME` modules paths</span></span>
- <span data-ttu-id="ea5a6-138">IF `PSModulePath` finns:</span><span class="sxs-lookup"><span data-stu-id="ea5a6-138">If `PSModulePath` does exist:</span></span>
  - <span data-ttu-id="ea5a6-139">Om `PSModulePath` innehåller en `$PSHOME` sökväg för moduler:</span><span class="sxs-lookup"><span data-stu-id="ea5a6-139">If `PSModulePath` contains `$PSHOME` modules path:</span></span>
    - <span data-ttu-id="ea5a6-140">Sökvägen till **allusers** -moduler infogas före `$PSHOME` sökvägen till moduler</span><span class="sxs-lookup"><span data-stu-id="ea5a6-140">**AllUsers** modules path is inserted before `$PSHOME` modules path</span></span>
  - <span data-ttu-id="ea5a6-141">tilläggs</span><span class="sxs-lookup"><span data-stu-id="ea5a6-141">else:</span></span>
    - <span data-ttu-id="ea5a6-142">Används bara `PSModulePath` enligt definitionen eftersom användaren medvetet tog bort `$PSHOME` platsen</span><span class="sxs-lookup"><span data-stu-id="ea5a6-142">Just use `PSModulePath` as defined since the user deliberately removed the `$PSHOME` location</span></span>

<span data-ttu-id="ea5a6-143">**CurrentUser** module-sökvägen är för fast fast endast om användar omfånget `$env:PSModulePath` inte finns.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-143">The **CurrentUser** module path is prefixed only if User scope `$env:PSModulePath` doesn't exist.</span></span> <span data-ttu-id="ea5a6-144">Annars används användar omfånget `$env:PSModulePath` enligt definitionen.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-144">Otherwise, the User scope `$env:PSModulePath` is used as defined.</span></span>

### <a name="powershell-core-6-startup"></a><span data-ttu-id="ea5a6-145">PowerShell Core 6-start</span><span class="sxs-lookup"><span data-stu-id="ea5a6-145">PowerShell Core 6 startup</span></span>

<span data-ttu-id="ea5a6-146">PowerShell Core 6 använder inte innehåll i `$env:PSModulePath` om den upptäcker att den har startats från PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-146">PowerShell Core 6 doesn't use contents of `$env:PSModulePath` if it detects it was started from PowerShell.</span></span> <span data-ttu-id="ea5a6-147">Den skriver över den med:</span><span class="sxs-lookup"><span data-stu-id="ea5a6-147">It overwrites it with:</span></span>

- <span data-ttu-id="ea5a6-148">**CurrentUser** modules sökväg + **allusers** modules sökväg + `$PSHOME` moduler sökväg + sökväg för Windows PowerShell- `$PSHOME` moduler.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-148">**CurrentUser** modules path + **AllUsers** modules path + `$PSHOME` modules path + Windows PowerShell `$PSHOME` modules path.</span></span>

### <a name="powershell-7-startup"></a><span data-ttu-id="ea5a6-149">PowerShell 7-Start</span><span class="sxs-lookup"><span data-stu-id="ea5a6-149">PowerShell 7 startup</span></span>

<span data-ttu-id="ea5a6-150">I Windows, för de flesta miljövariabler, använder en ny process bara det värdet även om det finns en dator som omfattas av samma namn för de flesta miljövariabler.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-150">In Windows, for most environment variables, if the User-scoped variable exists, a new process uses that value only even if a Machine-scoped variable of the same name exists.</span></span>

<span data-ttu-id="ea5a6-151">I PowerShell 7 `PSModulePath` behandlas liknande hur `Path` miljövariabeln behandlas i Windows.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-151">In PowerShell 7, `PSModulePath` is treated similar to how the `Path` environment variable is treated on Windows.</span></span> <span data-ttu-id="ea5a6-152">I Windows `Path` behandlas det annorlunda jämfört med andra miljövariabler.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-152">On Windows, `Path` is treated differently from other environment variables.</span></span> <span data-ttu-id="ea5a6-153">När en process startas kombinerar Windows den användare som omfattas av `Path` datorns omfång `Path` .</span><span class="sxs-lookup"><span data-stu-id="ea5a6-153">When a process is started, Windows combines the User-scoped `Path` with the Machine-scoped `Path`.</span></span>

- <span data-ttu-id="ea5a6-154">Hämta användar omfattningen `PSModulePath`</span><span class="sxs-lookup"><span data-stu-id="ea5a6-154">Retrieve the User-scoped `PSModulePath`</span></span>
- <span data-ttu-id="ea5a6-155">Jämför med att bearbeta en ärvd `PSModulePath` miljö variabel</span><span class="sxs-lookup"><span data-stu-id="ea5a6-155">Compare to process inherited `PSModulePath` environment variable</span></span>
  - <span data-ttu-id="ea5a6-156">Om samma:</span><span class="sxs-lookup"><span data-stu-id="ea5a6-156">If the same:</span></span>
    - <span data-ttu-id="ea5a6-157">Lägg till **allusers** `PSModulePath` till slutet efter semantiken för `Path` miljö variabeln</span><span class="sxs-lookup"><span data-stu-id="ea5a6-157">Append the **AllUsers** `PSModulePath` to the end following the semantics of the `Path` environment variable</span></span>
    - <span data-ttu-id="ea5a6-158">Windows- `System32` sökvägen kommer från den dator som definierats `PSModulePath` så behöver inte uttryckligen läggas till</span><span class="sxs-lookup"><span data-stu-id="ea5a6-158">The Windows `System32` path comes from the machine defined `PSModulePath` so does not need to be added explicitly</span></span>
  - <span data-ttu-id="ea5a6-159">Om det skiljer sig, behandla som om användaren uttryckligen ändrade den och inte lägger till **allusers**`PSModulePath`</span><span class="sxs-lookup"><span data-stu-id="ea5a6-159">If different, treat as though user explicitly modified it and don't append **AllUsers** `PSModulePath`</span></span>
- <span data-ttu-id="ea5a6-160">Prefix med PS7-användare, system och `$PSHOME` sökvägar i den ordningen</span><span class="sxs-lookup"><span data-stu-id="ea5a6-160">Prefix with PS7 User, System, and `$PSHOME` paths in that order</span></span>
  - <span data-ttu-id="ea5a6-161">Om `powershell.config.json` innehåller en användare `PSModulePath` som är begränsad använder du den i stället för standardvärdet för användaren</span><span class="sxs-lookup"><span data-stu-id="ea5a6-161">If `powershell.config.json` contains a user scoped `PSModulePath`, use that instead of the default for the user</span></span>
  - <span data-ttu-id="ea5a6-162">Om `powershell.config.json` innehåller ett system område `PSModulePath` använder du det i stället för standardvärdet för systemet</span><span class="sxs-lookup"><span data-stu-id="ea5a6-162">If `powershell.config.json` contains a system scoped `PSModulePath`, use that instead of the default for the system</span></span>

<span data-ttu-id="ea5a6-163">UNIX-system har ingen åtskillnad mellan användar-och systemmiljövariabler.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-163">Unix systems don't have a separation of User and System environment variables.</span></span>
<span data-ttu-id="ea5a6-164">`PSModulePath` ärvs och PS7 sökvägar är före fast om de inte redan har definierats.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-164">`PSModulePath` is inherited and the PS7-specific paths are prefixed if not already defined.</span></span>

### <a name="starting-windows-powershell-from-powershell-7"></a><span data-ttu-id="ea5a6-165">Starta Windows PowerShell från PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="ea5a6-165">Starting Windows PowerShell from PowerShell 7</span></span>

<span data-ttu-id="ea5a6-166">I den här diskussionen innebär _Windows PowerShell_ både `powershell.exe` och `powershell_ise.exe` .</span><span class="sxs-lookup"><span data-stu-id="ea5a6-166">For this discussion, _Windows PowerShell_ means both `powershell.exe` and `powershell_ise.exe`.</span></span>

<span data-ttu-id="ea5a6-167">Värdet för `$env:PSModulePath` kopieras till `WinPSModulePath` med följande ändringar:</span><span class="sxs-lookup"><span data-stu-id="ea5a6-167">The value of `$env:PSModulePath` is copied to `WinPSModulePath` with the following modifications:</span></span>

- <span data-ttu-id="ea5a6-168">Ta bort PS7 sökväg till användar modulen</span><span class="sxs-lookup"><span data-stu-id="ea5a6-168">Remove PS7 the User module path</span></span>
- <span data-ttu-id="ea5a6-169">Ta bort PS7-sökvägen till system-modulen</span><span class="sxs-lookup"><span data-stu-id="ea5a6-169">Remove PS7 the System module path</span></span>
- <span data-ttu-id="ea5a6-170">Ta bort PS7 `$PSHOME`</span><span class="sxs-lookup"><span data-stu-id="ea5a6-170">Remove PS7 the `$PSHOME` module path</span></span>

<span data-ttu-id="ea5a6-171">PS7-sökvägarna tas bort så att PS7-moduler inte kan läsas in i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-171">The PS7 paths are removed so that PS7 modules don't get loaded in Windows PowerShell.</span></span> <span data-ttu-id="ea5a6-172">`WinPSModulePath`Värdet används när du startar Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-172">The `WinPSModulePath` value is used when starting Windows PowerShell.</span></span>

### <a name="starting-powershell-7-from-windows-powershell"></a><span data-ttu-id="ea5a6-173">Starta PowerShell 7 från Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ea5a6-173">Starting PowerShell 7 from Windows PowerShell</span></span>

<span data-ttu-id="ea5a6-174">PowerShell 7-starten fortsätter i befintligt skick med att ärva sökvägar som har lagts till i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-174">The PowerShell 7 startup continues as-is with the addition of inheriting paths that Windows PowerShell added.</span></span> <span data-ttu-id="ea5a6-175">Eftersom PS7 sökvägar är i förväg finns det inget funktionellt problem.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-175">Since the PS7-specific paths are prefixed, there is no functional issue.</span></span>

### <a name="starting-powershell-6-from-powershell-7"></a><span data-ttu-id="ea5a6-176">Starta PowerShell 6 från PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="ea5a6-176">Starting PowerShell 6 from PowerShell 7</span></span>

<span data-ttu-id="ea5a6-177">PowerShell Core 6 skriver över `$env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="ea5a6-177">PowerShell Core 6 overwrites `$env:PSModulePath`.</span></span> <span data-ttu-id="ea5a6-178">Inga ändringar har gjorts.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-178">No changes are made.</span></span>

### <a name="starting-powershell-7-from-powershell-6"></a><span data-ttu-id="ea5a6-179">Starta PowerShell 7 från PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="ea5a6-179">Starting PowerShell 7 from PowerShell 6</span></span>

<span data-ttu-id="ea5a6-180">PowerShell 7-starten fortsätter i befintligt skick med att ärva sökvägar som PowerShell Core 6 lagt till.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-180">The PowerShell 7 startup continues as-is with the addition of inheriting paths that PowerShell Core 6 added.</span></span> <span data-ttu-id="ea5a6-181">Eftersom PS7 sökvägar är i förväg finns det inget funktionellt problem.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-181">Since the PS7-specific paths are prefixed, there is no functional issue.</span></span>

## <a name="module-search-behavior"></a><span data-ttu-id="ea5a6-182">Beteende för modul sökning</span><span class="sxs-lookup"><span data-stu-id="ea5a6-182">Module search behavior</span></span>

<span data-ttu-id="ea5a6-183">PowerShell söker rekursivt igenom varje mapp i **PSModulePath** efter modul ( `.psd1` eller `.psm1` ) filer.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-183">PowerShell recursively searches each folder in the **PSModulePath** for module (`.psd1` or `.psm1`) files.</span></span> <span data-ttu-id="ea5a6-184">Med det här Sök mönstret kan flera versioner av samma modul installeras i olika mappar.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-184">This search pattern allows multiple versions of the same module to be installed in different folders.</span></span> <span data-ttu-id="ea5a6-185">Exempel:</span><span class="sxs-lookup"><span data-stu-id="ea5a6-185">For example:</span></span>

```Output
    Directory: C:\Program Files\WindowsPowerShell\Modules\PowerShellGet

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d----           8/14/2020  5:56 PM                1.0.0.1
d----           9/13/2019  3:53 PM                2.1.2
```

<span data-ttu-id="ea5a6-186">Som standard laddar PowerShell det högsta versions numret för en modul när flera versioner hittas.</span><span class="sxs-lookup"><span data-stu-id="ea5a6-186">By default, PowerShell loads the highest version number of a module when multiple versions are found.</span></span> <span data-ttu-id="ea5a6-187">Om du vill läsa in en speciell version använder `Import-Module` du med parametern **FullyQualifiedName** .</span><span class="sxs-lookup"><span data-stu-id="ea5a6-187">To load a specific version, use `Import-Module` with the **FullyQualifiedName** parameter.</span></span> <span data-ttu-id="ea5a6-188">Mer information finns i [import-module](xref:Microsoft.PowerShell.Core.Import-Module).</span><span class="sxs-lookup"><span data-stu-id="ea5a6-188">For more information, see [Import-Module](xref:Microsoft.PowerShell.Core.Import-Module).</span></span>

## <a name="see-also"></a><span data-ttu-id="ea5a6-189">Se även</span><span class="sxs-lookup"><span data-stu-id="ea5a6-189">See also</span></span>

- [<span data-ttu-id="ea5a6-190">about_Modules</span><span class="sxs-lookup"><span data-stu-id="ea5a6-190">about_Modules</span></span>](about_Modules.md)
- [<span data-ttu-id="ea5a6-191">Miljö metoder</span><span class="sxs-lookup"><span data-stu-id="ea5a6-191">Environment Methods</span></span>](/dotnet/api/system.environment)
