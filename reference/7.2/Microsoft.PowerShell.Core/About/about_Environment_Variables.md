---
description: Beskriver hur du kommer åt Windows-miljövariabler i PowerShell.
Locale: en-US
ms.date: 09/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_environment_variables?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Environment_Variables
ms.openlocfilehash: 66d2bcd76651a7231a670ee5b02b99d6edd63a72
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710626"
---
# <a name="about-environment-variables"></a><span data-ttu-id="7dc95-103">Om miljövariabler</span><span class="sxs-lookup"><span data-stu-id="7dc95-103">About Environment Variables</span></span>

## <a name="short-description"></a><span data-ttu-id="7dc95-104">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="7dc95-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="7dc95-105">Beskriver hur du kommer åt Windows-miljövariabler i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7dc95-105">Describes how to access Windows environment variables in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="7dc95-106">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="7dc95-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="7dc95-107">Miljövariabler lagrar information om operativ system miljön.</span><span class="sxs-lookup"><span data-stu-id="7dc95-107">Environment variables store information about the operating system environment.</span></span> <span data-ttu-id="7dc95-108">Den här informationen innehåller information som till exempel operativ system Sök vägen, antalet processorer som används av operativ systemet och platsen för temporära mappar.</span><span class="sxs-lookup"><span data-stu-id="7dc95-108">This information includes details such as the operating system path, the number of processors used by the operating system, and the location of temporary folders.</span></span>

<span data-ttu-id="7dc95-109">Miljövariabler lagrar data som används av operativ systemet och andra program.</span><span class="sxs-lookup"><span data-stu-id="7dc95-109">The environment variables store data that is used by the operating system and other programs.</span></span> <span data-ttu-id="7dc95-110">`WINDIR`Miljövariabeln innehåller till exempel platsen för Windows installations katalog.</span><span class="sxs-lookup"><span data-stu-id="7dc95-110">For example, the `WINDIR` environment variable contains the location of the Windows installation directory.</span></span> <span data-ttu-id="7dc95-111">Program kan fråga värdet för den här variabeln för att avgöra var Windows-operativsystemfiler finns.</span><span class="sxs-lookup"><span data-stu-id="7dc95-111">Programs can query the value of this variable to determine where Windows operating system files are located.</span></span>

<span data-ttu-id="7dc95-112">PowerShell kan komma åt och hantera miljövariabler i någon av de operativ system plattformar som stöds.</span><span class="sxs-lookup"><span data-stu-id="7dc95-112">PowerShell can access and manage environment variables in any of the supported operating system platforms.</span></span> <span data-ttu-id="7dc95-113">PowerShell-hälsoleverantören fören klar den här processen genom att göra det enkelt att visa och ändra miljövariabler.</span><span class="sxs-lookup"><span data-stu-id="7dc95-113">The PowerShell environment provider simplifies this process by making it easy to view and change environment variables.</span></span>

<span data-ttu-id="7dc95-114">Miljövariabler, till skillnad från andra typer av variabler i PowerShell, ärvs av underordnade processer, till exempel lokala bakgrunds jobb och sessioner där modul medlemmar körs.</span><span class="sxs-lookup"><span data-stu-id="7dc95-114">Environment variables, unlike other types of variables in PowerShell, are inherited by child processes, such as local background jobs and the sessions in which module members run.</span></span> <span data-ttu-id="7dc95-115">Detta gör miljövariabler bra lämpade för att lagra värden som behövs i både över-och underordnade processer.</span><span class="sxs-lookup"><span data-stu-id="7dc95-115">This makes environment variables well suited to storing values that are needed in both parent and child processes.</span></span>

## <a name="using-and-changing-environment-variables"></a><span data-ttu-id="7dc95-116">Använda och ändra miljövariabler</span><span class="sxs-lookup"><span data-stu-id="7dc95-116">Using and changing environment variables</span></span>

<span data-ttu-id="7dc95-117">I Windows kan miljövariabler definieras i tre omfång:</span><span class="sxs-lookup"><span data-stu-id="7dc95-117">On Windows, environment variables can be defined in three scopes:</span></span>

- <span data-ttu-id="7dc95-118">Datorns (eller systemets) omfång</span><span class="sxs-lookup"><span data-stu-id="7dc95-118">Machine (or System) scope</span></span>
- <span data-ttu-id="7dc95-119">Användar omfång</span><span class="sxs-lookup"><span data-stu-id="7dc95-119">User scope</span></span>
- <span data-ttu-id="7dc95-120">Process omfång</span><span class="sxs-lookup"><span data-stu-id="7dc95-120">Process scope</span></span>

<span data-ttu-id="7dc95-121">_Process_ omfånget innehåller de miljövariabler som är tillgängliga i den aktuella processen eller PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="7dc95-121">The _Process_ scope contains the environment variables available in the current process, or PowerShell session.</span></span> <span data-ttu-id="7dc95-122">Den här listan över variabler ärvs från den överordnade processen och är konstruerad från variablerna i _dator_ -och _användar_ omfång.</span><span class="sxs-lookup"><span data-stu-id="7dc95-122">This list of variables is inherited from the parent process and is constructed from the variables in the _Machine_ and _User_ scopes.</span></span> <span data-ttu-id="7dc95-123">UNIX-baserade plattformar har bara _process_ omfånget.</span><span class="sxs-lookup"><span data-stu-id="7dc95-123">Unix-based platforms only have the _Process_ scope.</span></span>

<span data-ttu-id="7dc95-124">Du kan visa och ändra värdena för miljövariabler utan att använda en-cmdlet med hjälp av en variabel syntax med-miljö leverantören.</span><span class="sxs-lookup"><span data-stu-id="7dc95-124">You can display and change the values of environment variables without using a cmdlet by using a variable syntax with the environment provider.</span></span> <span data-ttu-id="7dc95-125">Om du vill visa värdet för en miljö variabel använder du följande syntax:</span><span class="sxs-lookup"><span data-stu-id="7dc95-125">To display the value of an environment variable, use the following syntax:</span></span>

```
$Env:<variable-name>
```

<span data-ttu-id="7dc95-126">Om du till exempel vill visa värdet för `WINDIR` miljövariabeln, skriver du följande kommando i PowerShell-kommando tolken:</span><span class="sxs-lookup"><span data-stu-id="7dc95-126">For example, to display the value of the `WINDIR` environment variable, type the following command at the PowerShell command prompt:</span></span>

```powershell
$Env:windir
```

<span data-ttu-id="7dc95-127">I den här syntaxen visar dollar tecknet ( `$` ) en variabel och enhets namnet ( `Env:` ) anger en miljö variabel följt av variabel namnet ( `windir` ).</span><span class="sxs-lookup"><span data-stu-id="7dc95-127">In this syntax, the dollar sign (`$`) indicates a variable, and the drive name (`Env:`) indicates an environment variable followed by the variable name (`windir`).</span></span>

<span data-ttu-id="7dc95-128">När du ändrar miljövariabler i PowerShell påverkar ändringen endast den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="7dc95-128">When you change environment variables in PowerShell, the change affects only the current session.</span></span> <span data-ttu-id="7dc95-129">Detta beteende påminner om `Set` kommandots beteende i Windows Command Shell och `Setenv` kommandot i UNIX-baserade miljöer.</span><span class="sxs-lookup"><span data-stu-id="7dc95-129">This behavior resembles the behavior of the `Set` command in the Windows Command Shell and the `Setenv` command in UNIX-based environments.</span></span> <span data-ttu-id="7dc95-130">Om du vill ändra värden i dator-eller användar omfång måste du använda metoderna i klassen **system. Environment** .</span><span class="sxs-lookup"><span data-stu-id="7dc95-130">To change values in the Machine or User scopes, you must use the methods of the **System.Environment** class.</span></span>

<span data-ttu-id="7dc95-131">För att göra ändringar i webbprogramsomfattande variabler måste även ha behörighet.</span><span class="sxs-lookup"><span data-stu-id="7dc95-131">To make changes to Machine-scoped variables, must also have permission.</span></span> <span data-ttu-id="7dc95-132">Om du försöker ändra ett värde utan tillräcklig behörighet, Miss lyckas kommandot och PowerShell visar ett fel.</span><span class="sxs-lookup"><span data-stu-id="7dc95-132">If you try to change a value without sufficient permission, the command fails and PowerShell displays an error.</span></span>

<span data-ttu-id="7dc95-133">Du kan ändra värdena för variabler utan att använda en cmdlet med hjälp av följande syntax:</span><span class="sxs-lookup"><span data-stu-id="7dc95-133">You can change the values of variables without using a cmdlet using the following syntax:</span></span>

```powershell
$Env:<variable-name> = "<new-value>"
```

<span data-ttu-id="7dc95-134">Om du till exempel vill lägga till `;c:\temp` värdet för `Path` miljövariabeln, använder du följande syntax:</span><span class="sxs-lookup"><span data-stu-id="7dc95-134">For example, to append `;c:\temp` to the value of the `Path` environment variable, use the following syntax:</span></span>

```powershell
$Env:Path += ";c:\temp"
```

<span data-ttu-id="7dc95-135">Kolon () i kommandot på Linux eller MacOS `:` separerar den nya sökvägen från den sökväg som föregår den i listan.</span><span class="sxs-lookup"><span data-stu-id="7dc95-135">On Linux or MacOS, the colon (`:`) in the command separates the new path from the path that precedes it in the list.</span></span>

```powershell
$Env:PATH += ":/usr/local/temp"
```

<span data-ttu-id="7dc95-136">Du kan också använda objekt-cmdletar, till exempel `Set-Item` , `Remove-Item` , och `Copy-Item` för att ändra värdena för miljövariabler.</span><span class="sxs-lookup"><span data-stu-id="7dc95-136">You can also use the Item cmdlets, such as `Set-Item`, `Remove-Item`, and `Copy-Item` to change the values of environment variables.</span></span> <span data-ttu-id="7dc95-137">Om du till exempel vill använda `Set-Item` cmdleten för att lägga till `;c:\temp` värdet för `Path` miljövariabeln, använder du följande syntax:</span><span class="sxs-lookup"><span data-stu-id="7dc95-137">For example, to use the `Set-Item` cmdlet to append `;c:\temp` to the value of the `Path` environment variable, use the following syntax:</span></span>

```powershell
Set-Item -Path Env:Path -Value ($Env:Path + ";C:\Temp")
```

<span data-ttu-id="7dc95-138">I det här kommandot omges värdet av parenteser så att det tolkas som en enhet.</span><span class="sxs-lookup"><span data-stu-id="7dc95-138">In this command, the value is enclosed in parentheses so that it is interpreted as a unit.</span></span>

## <a name="environment-variables-that-store-preferences"></a><span data-ttu-id="7dc95-139">Miljövariabler som lagrar inställningar</span><span class="sxs-lookup"><span data-stu-id="7dc95-139">Environment variables that store preferences</span></span>

<span data-ttu-id="7dc95-140">PowerShell-funktioner kan använda miljövariabler för att lagra användar inställningar.</span><span class="sxs-lookup"><span data-stu-id="7dc95-140">PowerShell features can use environment variables to store user preferences.</span></span>
<span data-ttu-id="7dc95-141">Dessa variabler fungerar som Preference-variabler, men de ärvs av underordnade sessioner av de sessioner som de skapas i.</span><span class="sxs-lookup"><span data-stu-id="7dc95-141">These variables work like preference variables, but they are inherited by child sessions of the sessions in which they are created.</span></span> <span data-ttu-id="7dc95-142">Mer information om Preferences-variabler finns i [about_Preference_Variables](about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="7dc95-142">For more information about preference variables, see [about_preference_variables](about_Preference_Variables.md).</span></span>

<span data-ttu-id="7dc95-143">Miljövariablerna som lagrar inställningarna är:</span><span class="sxs-lookup"><span data-stu-id="7dc95-143">The environment variables that store preferences include:</span></span>

- <span data-ttu-id="7dc95-144">PSExecutionPolicyPreference</span><span class="sxs-lookup"><span data-stu-id="7dc95-144">PSExecutionPolicyPreference</span></span>

  <span data-ttu-id="7dc95-145">Lagrar körnings princip uppsättningen för den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="7dc95-145">Stores the execution policy set for the current session.</span></span> <span data-ttu-id="7dc95-146">Denna miljö variabel finns bara när du anger en körnings princip för en enskild session.</span><span class="sxs-lookup"><span data-stu-id="7dc95-146">This environment variable exists only when you set an execution policy for a single session.</span></span>
  <span data-ttu-id="7dc95-147">Du kan göra detta på två olika sätt.</span><span class="sxs-lookup"><span data-stu-id="7dc95-147">You can do this in two different ways.</span></span>

  - <span data-ttu-id="7dc95-148">Starta en session från kommando raden med hjälp av parametern **ExecutionPolicy** för att ange körnings principen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="7dc95-148">Start a session from the command line using the **ExecutionPolicy** parameter to set the execution policy for the session.</span></span>

  - <span data-ttu-id="7dc95-149">Använd `Set-ExecutionPolicy` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7dc95-149">Use the `Set-ExecutionPolicy` cmdlet.</span></span> <span data-ttu-id="7dc95-150">Använd omfattnings parametern med värdet "process".</span><span class="sxs-lookup"><span data-stu-id="7dc95-150">Use the Scope parameter with a value of "Process".</span></span>

    <span data-ttu-id="7dc95-151">Mer information finns i [about_Execution_Policies](about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="7dc95-151">For more information, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

- <span data-ttu-id="7dc95-152">PSModuleAnalysisCachePath</span><span class="sxs-lookup"><span data-stu-id="7dc95-152">PSModuleAnalysisCachePath</span></span>

  <span data-ttu-id="7dc95-153">PowerShell ger kontroll över filen som används för att cachelagra data om moduler och deras cmdlets.</span><span class="sxs-lookup"><span data-stu-id="7dc95-153">PowerShell provides control over the file that is used to cache data about modules and their cmdlets.</span></span> <span data-ttu-id="7dc95-154">Cachen läses vid start vid sökning efter ett kommando och skrivs i en bakgrunds tråd någon gång efter att en modul har importer ATS.</span><span class="sxs-lookup"><span data-stu-id="7dc95-154">The cache is read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

  <span data-ttu-id="7dc95-155">Standard platsen för cachen är:</span><span class="sxs-lookup"><span data-stu-id="7dc95-155">Default location of the cache is:</span></span>

  - <span data-ttu-id="7dc95-156">Windows PowerShell 5,1: `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell`</span><span class="sxs-lookup"><span data-stu-id="7dc95-156">Windows PowerShell 5.1: `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell`</span></span>
  - <span data-ttu-id="7dc95-157">PowerShell 6,0 och högre: `$env:LOCALAPPDATA\Microsoft\PowerShell`</span><span class="sxs-lookup"><span data-stu-id="7dc95-157">PowerShell 6.0 and higher: `$env:LOCALAPPDATA\Microsoft\PowerShell`</span></span>
  - <span data-ttu-id="7dc95-158">Standard som inte är Windows: `~/.cache/powershell`</span><span class="sxs-lookup"><span data-stu-id="7dc95-158">Non-Windows default: `~/.cache/powershell`</span></span>

  <span data-ttu-id="7dc95-159">Standard namnet för cachen är `ModuleAnalysisCache` .</span><span class="sxs-lookup"><span data-stu-id="7dc95-159">The default filename for the cache is `ModuleAnalysisCache`.</span></span> <span data-ttu-id="7dc95-160">När du har flera instanser av PowerShell installerat innehåller fil namnet ett hexadecimalt suffix så att det finns ett unikt fil namn per installation.</span><span class="sxs-lookup"><span data-stu-id="7dc95-160">When you have multiple instances of PowerShell installed, the filename includes a hexadecimal suffix so that there is a a unique filename per installation.</span></span>

  > [!NOTE]
  > <span data-ttu-id="7dc95-161">Om kommando identifieringen inte fungerar som den ska, till exempel om IntelliSense visar kommandon som inte finns kan du ta bort cachefilen.</span><span class="sxs-lookup"><span data-stu-id="7dc95-161">If command discovery isn't working correctly, for example Intellisense shows commands that don't exist, you can delete the cache file.</span></span> <span data-ttu-id="7dc95-162">Cachen återskapas nästa gången du startar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7dc95-162">The cache is recreated the next time you start PowerShell.</span></span>

  <span data-ttu-id="7dc95-163">Om du vill ändra standard platsen för cacheminnet anger du miljövariabeln innan du startar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7dc95-163">To change the default location of the cache, set the environment variable before starting PowerShell.</span></span> <span data-ttu-id="7dc95-164">Ändringar av denna miljö variabel påverkar bara underordnade processer.</span><span class="sxs-lookup"><span data-stu-id="7dc95-164">Changes to this environment variable only affect child processes.</span></span> <span data-ttu-id="7dc95-165">Värdet bör ge en fullständig sökväg (inklusive fil namnet) som PowerShell har behörighet att skapa och skriva filer.</span><span class="sxs-lookup"><span data-stu-id="7dc95-165">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span>

  <span data-ttu-id="7dc95-166">Om du vill inaktivera filcachen ställer du in det här värdet på en ogiltig plats, till exempel:</span><span class="sxs-lookup"><span data-stu-id="7dc95-166">To disable the file cache, set this value to an invalid location, for example:</span></span>

  ```powershell
  # `NUL` here is a special device on Windows that cannot be written to,
  # on non-Windows you would use `/dev/null`
  $env:PSModuleAnalysisCachePath = 'NUL'
  ```

  <span data-ttu-id="7dc95-167">Detta anger sökvägen till **NUL** -enheten.</span><span class="sxs-lookup"><span data-stu-id="7dc95-167">This sets the path to the **NUL** device.</span></span> <span data-ttu-id="7dc95-168">PowerShell kan inte skriva till sökvägen, men inget fel returneras.</span><span class="sxs-lookup"><span data-stu-id="7dc95-168">PowerShell can't write to the path but no error is returned.</span></span> <span data-ttu-id="7dc95-169">Du kan se de fel som rapporteras med hjälp av en spårning:</span><span class="sxs-lookup"><span data-stu-id="7dc95-169">You can see the errors reported using a tracer:</span></span>

  ```powershell
  Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
  ```

- <span data-ttu-id="7dc95-170">PSDisableModuleAnalysisCacheCleanup</span><span class="sxs-lookup"><span data-stu-id="7dc95-170">PSDisableModuleAnalysisCacheCleanup</span></span>

  <span data-ttu-id="7dc95-171">När du skriver ut modulens analys-cache söker PowerShell efter moduler som inte längre finns för att undvika en onödigt stor cache.</span><span class="sxs-lookup"><span data-stu-id="7dc95-171">When writing out the module analysis cache, PowerShell checks for modules that no longer exist to avoid an unnecessarily large cache.</span></span> <span data-ttu-id="7dc95-172">Ibland är de här kontrollerna inte önskvärda, i så fall kan du inaktivera dem genom att ange miljövariabeln värde till `1` .</span><span class="sxs-lookup"><span data-stu-id="7dc95-172">Sometimes these checks are not desirable, in which case you can turn them off by setting this environment variable value to `1`.</span></span>

  <span data-ttu-id="7dc95-173">Att ställa in den här miljövariabeln börjar gälla direkt i den aktuella processen.</span><span class="sxs-lookup"><span data-stu-id="7dc95-173">Setting this environment variable takes effect immediately in the current process.</span></span>

- <span data-ttu-id="7dc95-174">PSModulePath</span><span class="sxs-lookup"><span data-stu-id="7dc95-174">PSModulePath</span></span>

  <span data-ttu-id="7dc95-175">`$env:PSModulePath`Miljövariabeln innehåller en lista över mappar som genomsöks för att hitta moduler och resurser.</span><span class="sxs-lookup"><span data-stu-id="7dc95-175">The `$env:PSModulePath` environment variable contains a list of folder locations that are searched to find modules and resources.</span></span>

  <span data-ttu-id="7dc95-176">Som standard är de effektiva platser som `$env:PSModulePath` är tilldelade:</span><span class="sxs-lookup"><span data-stu-id="7dc95-176">By default, the effective locations assigned to `$env:PSModulePath` are:</span></span>

  - <span data-ttu-id="7dc95-177">Platser i hela systemet: dessa mappar innehåller moduler som levereras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7dc95-177">System-wide locations: These folders contain modules that ship with PowerShell.</span></span> <span data-ttu-id="7dc95-178">Modulerna lagras på `$PSHOME\Modules` platsen.</span><span class="sxs-lookup"><span data-stu-id="7dc95-178">The modules are store in the `$PSHOME\Modules` location.</span></span> <span data-ttu-id="7dc95-179">Detta är också den plats där Windows Management-modulerna är installerade.</span><span class="sxs-lookup"><span data-stu-id="7dc95-179">Also, This is the location where the Windows management modules are installed.</span></span>

  - <span data-ttu-id="7dc95-180">Användare-installerade moduler: de här är moduler som installeras av användaren.</span><span class="sxs-lookup"><span data-stu-id="7dc95-180">User-installed modules: These are modules installed by the user.</span></span>
    <span data-ttu-id="7dc95-181">`Install-Module` har en **omfattnings** parameter som gör att du kan ange om modulen är installerad för den aktuella användaren eller för alla användare.</span><span class="sxs-lookup"><span data-stu-id="7dc95-181">`Install-Module` has a **Scope** parameter that allows you to specify whether the module is installed for the current user or for all users.</span></span> <span data-ttu-id="7dc95-182">Mer information finns i [install-module](xref:PowerShellGet.Install-Module).</span><span class="sxs-lookup"><span data-stu-id="7dc95-182">For more information, see [Install-Module](xref:PowerShellGet.Install-Module).</span></span>

    - <span data-ttu-id="7dc95-183">I Windows är platsen för det användarspecifika **CurrentUser** -omfånget `$HOME\Documents\PowerShell\Modules` mappen.</span><span class="sxs-lookup"><span data-stu-id="7dc95-183">On Windows, the location of the user-specific **CurrentUser** scope is the `$HOME\Documents\PowerShell\Modules` folder.</span></span> <span data-ttu-id="7dc95-184">Platsen för **allusers** -omfattningen är `$env:ProgramFiles\PowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="7dc95-184">The location of the **AllUsers** scope is `$env:ProgramFiles\PowerShell\Modules`.</span></span>
    - <span data-ttu-id="7dc95-185">På andra datorer än Windows-system är platsen för det användarspecifika **CurrentUser** -omfånget `$HOME/.local/share/powershell/Modules` mappen.</span><span class="sxs-lookup"><span data-stu-id="7dc95-185">On non-Windows systems, the location of the user-specific **CurrentUser** scope is the `$HOME/.local/share/powershell/Modules` folder.</span></span> <span data-ttu-id="7dc95-186">Platsen för **allusers** -omfattningen är `/usr/local/share/powershell/Modules` .</span><span class="sxs-lookup"><span data-stu-id="7dc95-186">The location of the **AllUsers** scope is `/usr/local/share/powershell/Modules`.</span></span>

  <span data-ttu-id="7dc95-187">Dessutom kan installations program som installerar moduler i andra kataloger, till exempel katalogen program filer, lägga till sina platser till värdet `$env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="7dc95-187">In addition, setup programs that install modules in other directories, such as the Program Files directory, can append their locations to the value of `$env:PSModulePath`.</span></span>

  <span data-ttu-id="7dc95-188">Mer information finns i [about_PSModulePath](about_PSModulePath.md).</span><span class="sxs-lookup"><span data-stu-id="7dc95-188">For more information, see [about_PSModulePath](about_PSModulePath.md).</span></span>

## <a name="managing-environment-variables"></a><span data-ttu-id="7dc95-189">Hantera miljövariabler</span><span class="sxs-lookup"><span data-stu-id="7dc95-189">Managing environment variables</span></span>

<span data-ttu-id="7dc95-190">PowerShell tillhandahåller flera olika metoder för att hantera miljövariabler.</span><span class="sxs-lookup"><span data-stu-id="7dc95-190">PowerShell provides several different methods for managing environment variables.</span></span>

- <span data-ttu-id="7dc95-191">Miljö leverantören het</span><span class="sxs-lookup"><span data-stu-id="7dc95-191">The Environment provider drive</span></span>
- <span data-ttu-id="7dc95-192">Objekt-cmdletar</span><span class="sxs-lookup"><span data-stu-id="7dc95-192">The Item cmdlets</span></span>
- <span data-ttu-id="7dc95-193">Klassen .NET **system. Environment**</span><span class="sxs-lookup"><span data-stu-id="7dc95-193">The .NET **System.Environment** class</span></span>
- <span data-ttu-id="7dc95-194">I Windows, kontroll panelen system</span><span class="sxs-lookup"><span data-stu-id="7dc95-194">On Windows, the System Control Panel</span></span>

### <a name="using-the-environment-provider"></a><span data-ttu-id="7dc95-195">Använda-miljö leverantören</span><span class="sxs-lookup"><span data-stu-id="7dc95-195">Using the Environment provider</span></span>

<span data-ttu-id="7dc95-196">Varje miljö variabel representeras av en instans av klassen **system. Collections. typen DictionaryEntry** .</span><span class="sxs-lookup"><span data-stu-id="7dc95-196">Each environment variable is represented by an instance of the **System.Collections.DictionaryEntry** class.</span></span> <span data-ttu-id="7dc95-197">I varje **typen DictionaryEntry** -objekt är namnet på miljövariabeln ord listans nyckel.</span><span class="sxs-lookup"><span data-stu-id="7dc95-197">In each **DictionaryEntry** object, the name of the environment variable is the dictionary key.</span></span> <span data-ttu-id="7dc95-198">Värdet för variabeln är värdet för ord listan.</span><span class="sxs-lookup"><span data-stu-id="7dc95-198">The value of the variable is the dictionary value.</span></span>

<span data-ttu-id="7dc95-199">Använd cmdleten för att visa egenskaper och metoder för objektet som representerar en miljö variabel i PowerShell `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="7dc95-199">To display the properties and methods of the object that represents an environment variable in PowerShell, use the `Get-Member` cmdlet.</span></span> <span data-ttu-id="7dc95-200">Om du till exempel vill visa metoder och egenskaper för alla objekt i `Env:` enheten skriver du:</span><span class="sxs-lookup"><span data-stu-id="7dc95-200">For example, to display the methods and properties of all the objects in the `Env:` drive, type:</span></span>

```powershell
Get-Item -Path Env:* | Get-Member
```

<span data-ttu-id="7dc95-201">PowerShell-hälsoleverantören ger dig åtkomst till miljövariabler i en PowerShell-enhet ( `Env:` enheten).</span><span class="sxs-lookup"><span data-stu-id="7dc95-201">The PowerShell Environment provider lets you access environment variables in a PowerShell drive (the `Env:` drive).</span></span> <span data-ttu-id="7dc95-202">Den här enheten ser ut ungefär som en fil system enhet.</span><span class="sxs-lookup"><span data-stu-id="7dc95-202">This drive looks much like a file system drive.</span></span> <span data-ttu-id="7dc95-203">Om du vill gå till `Env:` enheten skriver du:</span><span class="sxs-lookup"><span data-stu-id="7dc95-203">To go to the `Env:` drive, type:</span></span>

```powershell
Set-Location Env:
```

<span data-ttu-id="7dc95-204">Använd innehålls-cmdletar för att hämta eller ange värden för en miljö variabel.</span><span class="sxs-lookup"><span data-stu-id="7dc95-204">Use the Content cmdlets to get or set the values of an environment variable.</span></span>

```powershell
PS Env:\> Set-Content -Path Test -Value 'Test value'
PS Env:\> Get-Content -Path Test
Test value
```

<span data-ttu-id="7dc95-205">Du kan visa miljövariablerna i `Env:` enheten från andra PowerShell-enheter, och du kan gå in på `Env:` enheten för att visa och ändra miljövariablerna.</span><span class="sxs-lookup"><span data-stu-id="7dc95-205">You can view the environment variables in the `Env:` drive from any other PowerShell drive, and you can go into the `Env:` drive to view and change the environment variables.</span></span>

### <a name="using-item-cmdlets"></a><span data-ttu-id="7dc95-206">Använda objekt-cmdletar</span><span class="sxs-lookup"><span data-stu-id="7dc95-206">Using Item cmdlets</span></span>

<span data-ttu-id="7dc95-207">När du refererar till en miljö variabel, anger du `Env:` enhetens namn följt av namnet på variabeln.</span><span class="sxs-lookup"><span data-stu-id="7dc95-207">When you refer to an environment variable, type the `Env:` drive name followed by the name of the variable.</span></span> <span data-ttu-id="7dc95-208">Om du till exempel vill visa värdet för `COMPUTERNAME` miljö variabeln, skriver du:</span><span class="sxs-lookup"><span data-stu-id="7dc95-208">For example, to display the value of the `COMPUTERNAME` environment variable, type:</span></span>

```powershell
Get-ChildItem Env:Computername
```

<span data-ttu-id="7dc95-209">Om du vill visa värdena för alla miljövariabler skriver du:</span><span class="sxs-lookup"><span data-stu-id="7dc95-209">To display the values of all the environment variables, type:</span></span>

```powershell
Get-ChildItem Env:
```

<span data-ttu-id="7dc95-210">Eftersom miljövariablerna inte har underordnade objekt är resultatet av `Get-Item` och `Get-ChildItem` samma.</span><span class="sxs-lookup"><span data-stu-id="7dc95-210">Because environment variables do not have child items, the output of `Get-Item` and `Get-ChildItem` is the same.</span></span>

<span data-ttu-id="7dc95-211">Som standard visar PowerShell miljövariablerna i den ordning som de hämtar dem.</span><span class="sxs-lookup"><span data-stu-id="7dc95-211">By default, PowerShell displays the environment variables in the order in which it retrieves them.</span></span> <span data-ttu-id="7dc95-212">Om du vill sortera listan över miljövariabler efter variabel namn, skickar du ut resultatet av ett `Get-ChildItem` kommando till `Sort-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7dc95-212">To sort the list of environment variables by variable name, pipe the output of a `Get-ChildItem` command to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="7dc95-213">Till exempel, från valfri PowerShell-enhet, skriver du:</span><span class="sxs-lookup"><span data-stu-id="7dc95-213">For example, from any PowerShell drive, type:</span></span>

```powershell
Get-ChildItem Env: | Sort Name
```

<span data-ttu-id="7dc95-214">Du kan också gå in på `Env:` enheten med hjälp av `Set-Location` cmdleten:</span><span class="sxs-lookup"><span data-stu-id="7dc95-214">You can also go into the `Env:` drive by using the `Set-Location` cmdlet:</span></span>

```powershell
Set-Location Env:
```

<span data-ttu-id="7dc95-215">När du är i `Env:` enheten kan du utelämna `Env:` enhets namnet från sökvägen.</span><span class="sxs-lookup"><span data-stu-id="7dc95-215">When you are in the `Env:` drive, you can omit the `Env:` drive name from the path.</span></span> <span data-ttu-id="7dc95-216">Om du till exempel vill visa alla miljövariabler skriver du:</span><span class="sxs-lookup"><span data-stu-id="7dc95-216">For example, to display all the environment variables, type:</span></span>

```powershell
PS Env:\> Get-ChildItem
```

<span data-ttu-id="7dc95-217">Om du vill visa värdet för `COMPUTERNAME` variabeln inifrån `Env:` enheten skriver du:</span><span class="sxs-lookup"><span data-stu-id="7dc95-217">To display the value of the `COMPUTERNAME` variable from within the `Env:` drive, type:</span></span>

```powershell
PS Env:\> Get-ChildItem ComputerName
```

### <a name="saving-changes-to-environment-variables"></a><span data-ttu-id="7dc95-218">Spara ändringar i miljövariabler</span><span class="sxs-lookup"><span data-stu-id="7dc95-218">Saving changes to environment variables</span></span>

<span data-ttu-id="7dc95-219">Om du vill göra en beständig ändring i en miljö variabel i Windows kan du använda system kontroll panelen.</span><span class="sxs-lookup"><span data-stu-id="7dc95-219">To make a persistent change to an environment variable on Windows, use the System Control Panel.</span></span> <span data-ttu-id="7dc95-220">Välj **Avancerade systeminställningar**.</span><span class="sxs-lookup"><span data-stu-id="7dc95-220">Select **Advanced System Settings**.</span></span> <span data-ttu-id="7dc95-221">På fliken **Avancerat** klickar du på **miljö variabel...**. Du kan lägga till eller redigera befintliga miljövariabler i scope för **användare** och **system** (datorer).</span><span class="sxs-lookup"><span data-stu-id="7dc95-221">On the **Advanced** tab, click **Environment Variable...**. You can add or edit existing environment variables in the **User** and **System** (Machine) scopes.</span></span> <span data-ttu-id="7dc95-222">Windows skriver dessa värden till registret så att de behålls mellan sessioner och omstarter av systemet.</span><span class="sxs-lookup"><span data-stu-id="7dc95-222">Windows writes these values to the Registry so that they persist across sessions and system restarts.</span></span>

<span data-ttu-id="7dc95-223">Alternativt kan du lägga till eller ändra miljövariabler i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="7dc95-223">Alternately, you can add or change environment variables in your PowerShell profile.</span></span> <span data-ttu-id="7dc95-224">Den här metoden fungerar för alla versioner av PowerShell på alla plattformar som stöds.</span><span class="sxs-lookup"><span data-stu-id="7dc95-224">This method works for any version of PowerShell on any supported platform.</span></span>

### <a name="using-systemenvironment-methods"></a><span data-ttu-id="7dc95-225">Använda system. miljö metoder</span><span class="sxs-lookup"><span data-stu-id="7dc95-225">Using System.Environment methods</span></span>

<span data-ttu-id="7dc95-226">Klassen **system. Environment** tillhandahåller **GetEnvironmentVariable** -och **SetEnvironmentVariable** -metoder som gör att du kan ange variabelns omfång.</span><span class="sxs-lookup"><span data-stu-id="7dc95-226">The **System.Environment** class provides **GetEnvironmentVariable** and **SetEnvironmentVariable** methods that allow you to specify the scope of the variable.</span></span>

<span data-ttu-id="7dc95-227">I följande exempel används metoden **GetEnvironmentVariable** för att hämta dator inställningen för `PSModulePath` och metoden **SetEnvironmentVariable** för att lägga till `C:\Program Files\Fabrikam\Modules` sökvägen till värdet.</span><span class="sxs-lookup"><span data-stu-id="7dc95-227">The following example uses the **GetEnvironmentVariable** method to get the machine setting of `PSModulePath` and the **SetEnvironmentVariable** method to add the `C:\Program Files\Fabrikam\Modules` path to the value.</span></span>

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'Machine')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable("PSModulePath", $newpath, 'Machine')
```

<span data-ttu-id="7dc95-228">Mer information om metoderna i klassen **system. miljö** finns i [miljö metoder](/dotnet/api/system.environment).</span><span class="sxs-lookup"><span data-stu-id="7dc95-228">For more information about the methods of the **System.Environment** class, see [Environment Methods](/dotnet/api/system.environment).</span></span>

## <a name="see-also"></a><span data-ttu-id="7dc95-229">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="7dc95-229">SEE ALSO</span></span>

- [<span data-ttu-id="7dc95-230">Miljö (Provider)</span><span class="sxs-lookup"><span data-stu-id="7dc95-230">Environment (provider)</span></span>](../About/about_Environment_Provider.md)
- [<span data-ttu-id="7dc95-231">about_Modules</span><span class="sxs-lookup"><span data-stu-id="7dc95-231">about_Modules</span></span>](about_Modules.md)

