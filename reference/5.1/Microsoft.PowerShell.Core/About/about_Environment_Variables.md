---
description: Beskriver hur du kommer åt Windows-miljövariabler i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_environment_variables?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Environment_Variables
ms.openlocfilehash: 3004e01e59d30005ad2fbfa92897f43471a41384
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272162"
---
# <a name="about-environment-variables"></a><span data-ttu-id="728e4-104">Om miljövariabler</span><span class="sxs-lookup"><span data-stu-id="728e4-104">About Environment Variables</span></span>

## <a name="short-description"></a><span data-ttu-id="728e4-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="728e4-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="728e4-106">Beskriver hur du kommer åt Windows-miljövariabler i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="728e4-106">Describes how to access Windows environment variables in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="728e4-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="728e4-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="728e4-108">Miljövariabler lagrar information om operativ system miljön.</span><span class="sxs-lookup"><span data-stu-id="728e4-108">Environment variables store information about the operating system environment.</span></span> <span data-ttu-id="728e4-109">Den här informationen innehåller information som till exempel operativ system Sök vägen, antalet processorer som används av operativ systemet och platsen för temporära mappar.</span><span class="sxs-lookup"><span data-stu-id="728e4-109">This information includes details such as the operating system path, the number of processors used by the operating system, and the location of temporary folders.</span></span>

<span data-ttu-id="728e4-110">Miljövariabler lagrar data som används av operativ systemet och andra program.</span><span class="sxs-lookup"><span data-stu-id="728e4-110">The environment variables store data that is used by the operating system and other programs.</span></span> <span data-ttu-id="728e4-111">`WINDIR`Miljövariabeln innehåller till exempel platsen för Windows installations katalog.</span><span class="sxs-lookup"><span data-stu-id="728e4-111">For example, the `WINDIR` environment variable contains the location of the Windows installation directory.</span></span> <span data-ttu-id="728e4-112">Program kan fråga värdet för den här variabeln för att avgöra var Windows-operativsystemfiler finns.</span><span class="sxs-lookup"><span data-stu-id="728e4-112">Programs can query the value of this variable to determine where Windows operating system files are located.</span></span>

<span data-ttu-id="728e4-113">PowerShell kan komma åt och hantera miljövariabler i någon av de operativ system plattformar som stöds.</span><span class="sxs-lookup"><span data-stu-id="728e4-113">PowerShell can access and manage environment variables in any of the supported operating system platforms.</span></span> <span data-ttu-id="728e4-114">PowerShell-hälsoleverantören fören klar den här processen genom att göra det enkelt att visa och ändra miljövariabler.</span><span class="sxs-lookup"><span data-stu-id="728e4-114">The PowerShell environment provider simplifies this process by making it easy to view and change environment variables.</span></span>

<span data-ttu-id="728e4-115">Miljövariabler, till skillnad från andra typer av variabler i PowerShell, ärvs av underordnade processer, till exempel lokala bakgrunds jobb och sessioner där modul medlemmar körs.</span><span class="sxs-lookup"><span data-stu-id="728e4-115">Environment variables, unlike other types of variables in PowerShell, are inherited by child processes, such as local background jobs and the sessions in which module members run.</span></span> <span data-ttu-id="728e4-116">Detta gör miljövariabler bra lämpade för att lagra värden som behövs i både över-och underordnade processer.</span><span class="sxs-lookup"><span data-stu-id="728e4-116">This makes environment variables well suited to storing values that are needed in both parent and child processes.</span></span>

## <a name="using-and-changing-environment-variables"></a><span data-ttu-id="728e4-117">Använda och ändra miljövariabler</span><span class="sxs-lookup"><span data-stu-id="728e4-117">Using and changing environment variables</span></span>

<span data-ttu-id="728e4-118">I Windows kan miljövariabler definieras i tre omfång:</span><span class="sxs-lookup"><span data-stu-id="728e4-118">On Windows, environment variables can be defined in three scopes:</span></span>

- <span data-ttu-id="728e4-119">Datorns (eller systemets) omfång</span><span class="sxs-lookup"><span data-stu-id="728e4-119">Machine (or System) scope</span></span>
- <span data-ttu-id="728e4-120">Användar omfång</span><span class="sxs-lookup"><span data-stu-id="728e4-120">User scope</span></span>
- <span data-ttu-id="728e4-121">Process omfång</span><span class="sxs-lookup"><span data-stu-id="728e4-121">Process scope</span></span>

<span data-ttu-id="728e4-122">_Process_ omfånget innehåller de miljövariabler som är tillgängliga i den aktuella processen eller PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="728e4-122">The _Process_ scope contains the environment variables available in the current process, or PowerShell session.</span></span> <span data-ttu-id="728e4-123">Den här listan över variabler ärvs från den överordnade processen och är konstruerad från variablerna i _dator_ -och _användar_ omfång.</span><span class="sxs-lookup"><span data-stu-id="728e4-123">This list of variables is inherited from the parent process and is constructed from the variables in the _Machine_ and _User_ scopes.</span></span>

<span data-ttu-id="728e4-124">Du kan visa och ändra värdena för miljövariabler utan att använda en-cmdlet med hjälp av en variabel syntax med-miljö leverantören.</span><span class="sxs-lookup"><span data-stu-id="728e4-124">You can display and change the values of environment variables without using a cmdlet by using a variable syntax with the environment provider.</span></span> <span data-ttu-id="728e4-125">Om du vill visa värdet för en miljö variabel använder du följande syntax:</span><span class="sxs-lookup"><span data-stu-id="728e4-125">To display the value of an environment variable, use the following syntax:</span></span>

```
$Env:<variable-name>
```

<span data-ttu-id="728e4-126">Om du till exempel vill visa värdet för `WINDIR` miljövariabeln, skriver du följande kommando i PowerShell-kommando tolken:</span><span class="sxs-lookup"><span data-stu-id="728e4-126">For example, to display the value of the `WINDIR` environment variable, type the following command at the PowerShell command prompt:</span></span>

```powershell
$Env:windir
```

<span data-ttu-id="728e4-127">I den här syntaxen visar dollar tecknet ( `$` ) en variabel och enhets namnet ( `Env:` ) anger en miljö variabel följt av variabel namnet ( `windir` ).</span><span class="sxs-lookup"><span data-stu-id="728e4-127">In this syntax, the dollar sign (`$`) indicates a variable, and the drive name (`Env:`) indicates an environment variable followed by the variable name (`windir`).</span></span>

<span data-ttu-id="728e4-128">När du ändrar miljövariabler i PowerShell påverkar ändringen endast den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="728e4-128">When you change environment variables in PowerShell, the change affects only the current session.</span></span> <span data-ttu-id="728e4-129">Detta beteende påminner om `Set` kommandots beteende i Windows Command Shell och `Setenv` kommandot i UNIX-baserade miljöer.</span><span class="sxs-lookup"><span data-stu-id="728e4-129">This behavior resembles the behavior of the `Set` command in the Windows Command Shell and the `Setenv` command in UNIX-based environments.</span></span> <span data-ttu-id="728e4-130">Om du vill ändra värden i dator-eller användar omfång måste du använda metoderna i klassen **system. Environment** .</span><span class="sxs-lookup"><span data-stu-id="728e4-130">To change values in the Machine or User scopes, you must use the methods of the **System.Environment** class.</span></span>

<span data-ttu-id="728e4-131">För att göra ändringar i webbprogramsomfattande variabler måste även ha behörighet.</span><span class="sxs-lookup"><span data-stu-id="728e4-131">To make changes to Machine-scoped variables, must also have permission.</span></span> <span data-ttu-id="728e4-132">Om du försöker ändra ett värde utan tillräcklig behörighet, Miss lyckas kommandot och PowerShell visar ett fel.</span><span class="sxs-lookup"><span data-stu-id="728e4-132">If you try to change a value without sufficient permission, the command fails and PowerShell displays an error.</span></span>

<span data-ttu-id="728e4-133">Du kan ändra värdena för variabler utan att använda en cmdlet med hjälp av följande syntax:</span><span class="sxs-lookup"><span data-stu-id="728e4-133">You can change the values of variables without using a cmdlet using the following syntax:</span></span>

```powershell
$Env:<variable-name> = "<new-value>"
```

<span data-ttu-id="728e4-134">Om du till exempel vill lägga till `;c:\temp` värdet för `Path` miljövariabeln, använder du följande syntax:</span><span class="sxs-lookup"><span data-stu-id="728e4-134">For example, to append `;c:\temp` to the value of the `Path` environment variable, use the following syntax:</span></span>

```powershell
$Env:Path += ";c:\temp"
```

<span data-ttu-id="728e4-135">Du kan också använda objekt-cmdletar, till exempel `Set-Item` , `Remove-Item` , och `Copy-Item` för att ändra värdena för miljövariabler.</span><span class="sxs-lookup"><span data-stu-id="728e4-135">You can also use the Item cmdlets, such as `Set-Item`, `Remove-Item`, and `Copy-Item` to change the values of environment variables.</span></span> <span data-ttu-id="728e4-136">Om du till exempel vill använda `Set-Item` cmdleten för att lägga till `;c:\temp` värdet för `Path` miljövariabeln, använder du följande syntax:</span><span class="sxs-lookup"><span data-stu-id="728e4-136">For example, to use the `Set-Item` cmdlet to append `;c:\temp` to the value of the `Path` environment variable, use the following syntax:</span></span>

```powershell
Set-Item -Path Env:Path -Value ($Env:Path + ";C:\Temp")
```

<span data-ttu-id="728e4-137">I det här kommandot omges värdet av parenteser så att det tolkas som en enhet.</span><span class="sxs-lookup"><span data-stu-id="728e4-137">In this command, the value is enclosed in parentheses so that it is interpreted as a unit.</span></span>

## <a name="environment-variables-that-store-preferences"></a><span data-ttu-id="728e4-138">Miljövariabler som lagrar inställningar</span><span class="sxs-lookup"><span data-stu-id="728e4-138">Environment variables that store preferences</span></span>

<span data-ttu-id="728e4-139">PowerShell-funktioner kan använda miljövariabler för att lagra användar inställningar.</span><span class="sxs-lookup"><span data-stu-id="728e4-139">PowerShell features can use environment variables to store user preferences.</span></span>
<span data-ttu-id="728e4-140">Dessa variabler fungerar som Preference-variabler, men de ärvs av underordnade sessioner av de sessioner som de skapas i.</span><span class="sxs-lookup"><span data-stu-id="728e4-140">These variables work like preference variables, but they are inherited by child sessions of the sessions in which they are created.</span></span> <span data-ttu-id="728e4-141">Mer information om Preferences-variabler finns i [about_Preference_Variables](about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="728e4-141">For more information about preference variables, see [about_preference_variables](about_Preference_Variables.md).</span></span>

<span data-ttu-id="728e4-142">Miljövariablerna som lagrar inställningarna är:</span><span class="sxs-lookup"><span data-stu-id="728e4-142">The environment variables that store preferences include:</span></span>

- <span data-ttu-id="728e4-143">PSExecutionPolicyPreference</span><span class="sxs-lookup"><span data-stu-id="728e4-143">PSExecutionPolicyPreference</span></span>

  <span data-ttu-id="728e4-144">Lagrar körnings princip uppsättningen för den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="728e4-144">Stores the execution policy set for the current session.</span></span> <span data-ttu-id="728e4-145">Denna miljö variabel finns bara när du anger en körnings princip för en enskild session.</span><span class="sxs-lookup"><span data-stu-id="728e4-145">This environment variable exists only when you set an execution policy for a single session.</span></span>
  <span data-ttu-id="728e4-146">Du kan göra detta på två olika sätt.</span><span class="sxs-lookup"><span data-stu-id="728e4-146">You can do this in two different ways.</span></span>

  - <span data-ttu-id="728e4-147">Starta en session från kommando raden med hjälp av parametern **ExecutionPolicy** för att ange körnings principen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="728e4-147">Start a session from the command line using the **ExecutionPolicy** parameter to set the execution policy for the session.</span></span>

  - <span data-ttu-id="728e4-148">Använd `Set-ExecutionPolicy` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="728e4-148">Use the `Set-ExecutionPolicy` cmdlet.</span></span> <span data-ttu-id="728e4-149">Använd omfattnings parametern med värdet "process".</span><span class="sxs-lookup"><span data-stu-id="728e4-149">Use the Scope parameter with a value of "Process".</span></span>

    <span data-ttu-id="728e4-150">Mer information finns i [about_Execution_Policies](about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="728e4-150">For more information, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

- <span data-ttu-id="728e4-151">PSModuleAnalysisCachePath</span><span class="sxs-lookup"><span data-stu-id="728e4-151">PSModuleAnalysisCachePath</span></span>

  <span data-ttu-id="728e4-152">PowerShell ger kontroll över filen som används för att cachelagra data om moduler och deras cmdlets.</span><span class="sxs-lookup"><span data-stu-id="728e4-152">PowerShell provides control over the file that is used to cache data about modules and their cmdlets.</span></span> <span data-ttu-id="728e4-153">Cachen läses vid start vid sökning efter ett kommando och skrivs i en bakgrunds tråd någon gång efter att en modul har importer ATS.</span><span class="sxs-lookup"><span data-stu-id="728e4-153">The cache is read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

  <span data-ttu-id="728e4-154">Standard platsen för cachen är:</span><span class="sxs-lookup"><span data-stu-id="728e4-154">Default location of the cache is:</span></span>

  - `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell`

  <span data-ttu-id="728e4-155">Standard namnet för cachen är `ModuleAnalysisCache` .</span><span class="sxs-lookup"><span data-stu-id="728e4-155">The default filename for the cache is `ModuleAnalysisCache`.</span></span> <span data-ttu-id="728e4-156">Om du vill ändra standard platsen för cacheminnet anger du miljövariabeln innan du startar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="728e4-156">To change the default location of the cache, set the environment variable before starting PowerShell.</span></span> <span data-ttu-id="728e4-157">Ändringar av denna miljö variabel påverkar bara underordnade processer.</span><span class="sxs-lookup"><span data-stu-id="728e4-157">Changes to this environment variable only affect child processes.</span></span>
  <span data-ttu-id="728e4-158">Värdet bör ge en fullständig sökväg (inklusive fil namnet) som PowerShell har behörighet att skapa och skriva filer.</span><span class="sxs-lookup"><span data-stu-id="728e4-158">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span>

  > [!NOTE]
  > <span data-ttu-id="728e4-159">Om kommando identifieringen inte fungerar som den ska, till exempel om IntelliSense visar kommandon som inte finns kan du ta bort cachefilen.</span><span class="sxs-lookup"><span data-stu-id="728e4-159">If command discovery isn't working correctly, for example Intellisense shows commands that don't exist, you can delete the cache file.</span></span> <span data-ttu-id="728e4-160">Cachen återskapas nästa gången du startar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="728e4-160">The cache is recreated the next time you start PowerShell.</span></span>

  <span data-ttu-id="728e4-161">Om du vill inaktivera filcachen ställer du in det här värdet på en ogiltig plats, till exempel:</span><span class="sxs-lookup"><span data-stu-id="728e4-161">To disable the file cache, set this value to an invalid location, for example:</span></span>

  ```powershell
  # `NUL` here is a special device on Windows that cannot be written to
  $env:PSModuleAnalysisCachePath = 'NUL'
  ```

  <span data-ttu-id="728e4-162">Detta anger sökvägen till **NUL** -enheten.</span><span class="sxs-lookup"><span data-stu-id="728e4-162">This sets the path to the **NUL** device.</span></span> <span data-ttu-id="728e4-163">PowerShell kan inte skriva till sökvägen, men inget fel returneras.</span><span class="sxs-lookup"><span data-stu-id="728e4-163">PowerShell can't write to the path but no error is returned.</span></span> <span data-ttu-id="728e4-164">Du kan se de fel som rapporteras med hjälp av en spårning:</span><span class="sxs-lookup"><span data-stu-id="728e4-164">You can see the errors reported using a tracer:</span></span>

  ```powershell
  Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
  ```

- <span data-ttu-id="728e4-165">PSDisableModuleAnalysisCacheCleanup</span><span class="sxs-lookup"><span data-stu-id="728e4-165">PSDisableModuleAnalysisCacheCleanup</span></span>

  <span data-ttu-id="728e4-166">När du skriver ut modulens analys-cache söker PowerShell efter moduler som inte längre finns för att undvika en onödigt stor cache.</span><span class="sxs-lookup"><span data-stu-id="728e4-166">When writing out the module analysis cache, PowerShell checks for modules that no longer exist to avoid an unnecessarily large cache.</span></span> <span data-ttu-id="728e4-167">Ibland är de här kontrollerna inte önskvärda, i så fall kan du inaktivera dem genom att ange miljövariabeln värde till `1` .</span><span class="sxs-lookup"><span data-stu-id="728e4-167">Sometimes these checks are not desirable, in which case you can turn them off by setting this environment variable value to `1`.</span></span>

  <span data-ttu-id="728e4-168">Att ställa in den här miljövariabeln börjar gälla direkt i den aktuella processen.</span><span class="sxs-lookup"><span data-stu-id="728e4-168">Setting this environment variable takes effect immediately in the current process.</span></span>

- <span data-ttu-id="728e4-169">PSModulePath</span><span class="sxs-lookup"><span data-stu-id="728e4-169">PSModulePath</span></span>

  <span data-ttu-id="728e4-170">`$env:PSModulePath`Miljövariabeln innehåller en lista över mappar som genomsöks för att hitta moduler och resurser.</span><span class="sxs-lookup"><span data-stu-id="728e4-170">The `$env:PSModulePath` environment variable contains a list of folder locations that are searched to find modules and resources.</span></span>

  <span data-ttu-id="728e4-171">Som standard är de effektiva platser som `$env:PSModulePath` är tilldelade:</span><span class="sxs-lookup"><span data-stu-id="728e4-171">By default, the effective locations assigned to `$env:PSModulePath` are:</span></span>

  - <span data-ttu-id="728e4-172">Platser i hela systemet: dessa mappar innehåller moduler som levereras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="728e4-172">System-wide locations: These folders contain modules that ship with PowerShell.</span></span> <span data-ttu-id="728e4-173">Modulerna lagras på `$PSHOME\Modules` platsen.</span><span class="sxs-lookup"><span data-stu-id="728e4-173">The modules are store in the `$PSHOME\Modules` location.</span></span> <span data-ttu-id="728e4-174">Detta är också den plats där Windows Management-modulerna är installerade.</span><span class="sxs-lookup"><span data-stu-id="728e4-174">Also, This is the location where the Windows management modules are installed.</span></span>

  - <span data-ttu-id="728e4-175">Användare-installerade moduler: de här är moduler som installeras av användaren.</span><span class="sxs-lookup"><span data-stu-id="728e4-175">User-installed modules: These are modules installed by the user.</span></span>
    <span data-ttu-id="728e4-176">`Install-Module` har en **omfattnings** parameter som gör att du kan ange om modulen är installerad för den aktuella användaren eller för alla användare.</span><span class="sxs-lookup"><span data-stu-id="728e4-176">`Install-Module` has a **Scope** parameter that allows you to specify whether the module is installed for the current user or for all users.</span></span> <span data-ttu-id="728e4-177">Mer information finns i [install-module](xref:PowerShellGet.Install-Module).</span><span class="sxs-lookup"><span data-stu-id="728e4-177">For more information, see [Install-Module](xref:PowerShellGet.Install-Module).</span></span>

    - <span data-ttu-id="728e4-178">I Windows är platsen för det användarspecifika **CurrentUser** -omfånget `$HOME\Documents\PowerShell\Modules` mappen.</span><span class="sxs-lookup"><span data-stu-id="728e4-178">On Windows, the location of the user-specific **CurrentUser** scope is the `$HOME\Documents\PowerShell\Modules` folder.</span></span> <span data-ttu-id="728e4-179">Platsen för **allusers** -omfattningen är `$env:ProgramFiles\PowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="728e4-179">The location of the **AllUsers** scope is `$env:ProgramFiles\PowerShell\Modules`.</span></span>

  <span data-ttu-id="728e4-180">Dessutom kan installations program som installerar moduler i andra kataloger, till exempel katalogen program filer, lägga till sina platser till värdet `$env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="728e4-180">In addition, setup programs that install modules in other directories, such as the Program Files directory, can append their locations to the value of `$env:PSModulePath`.</span></span>

  <span data-ttu-id="728e4-181">Mer information finns i [about_PSModulePath](about_PSModulePath.md).</span><span class="sxs-lookup"><span data-stu-id="728e4-181">For more information, see [about_PSModulePath](about_PSModulePath.md).</span></span>

## <a name="managing-environment-variables"></a><span data-ttu-id="728e4-182">Hantera miljövariabler</span><span class="sxs-lookup"><span data-stu-id="728e4-182">Managing environment variables</span></span>

<span data-ttu-id="728e4-183">PowerShell tillhandahåller flera olika metoder för att hantera miljövariabler.</span><span class="sxs-lookup"><span data-stu-id="728e4-183">PowerShell provides several different methods for managing environment variables.</span></span>

- <span data-ttu-id="728e4-184">Miljö leverantören het</span><span class="sxs-lookup"><span data-stu-id="728e4-184">The Environment provider drive</span></span>
- <span data-ttu-id="728e4-185">Objekt-cmdletar</span><span class="sxs-lookup"><span data-stu-id="728e4-185">The Item cmdlets</span></span>
- <span data-ttu-id="728e4-186">Klassen .NET **system. Environment**</span><span class="sxs-lookup"><span data-stu-id="728e4-186">The .NET **System.Environment** class</span></span>
- <span data-ttu-id="728e4-187">I Windows, kontroll panelen system</span><span class="sxs-lookup"><span data-stu-id="728e4-187">On Windows, the System Control Panel</span></span>

### <a name="using-the-environment-provider"></a><span data-ttu-id="728e4-188">Använda-miljö leverantören</span><span class="sxs-lookup"><span data-stu-id="728e4-188">Using the Environment provider</span></span>

<span data-ttu-id="728e4-189">Varje miljö variabel representeras av en instans av klassen **system. Collections. typen DictionaryEntry** .</span><span class="sxs-lookup"><span data-stu-id="728e4-189">Each environment variable is represented by an instance of the **System.Collections.DictionaryEntry** class.</span></span> <span data-ttu-id="728e4-190">I varje **typen DictionaryEntry** -objekt är namnet på miljövariabeln ord listans nyckel.</span><span class="sxs-lookup"><span data-stu-id="728e4-190">In each **DictionaryEntry** object, the name of the environment variable is the dictionary key.</span></span> <span data-ttu-id="728e4-191">Värdet för variabeln är värdet för ord listan.</span><span class="sxs-lookup"><span data-stu-id="728e4-191">The value of the variable is the dictionary value.</span></span>

<span data-ttu-id="728e4-192">Använd cmdleten för att visa egenskaper och metoder för objektet som representerar en miljö variabel i PowerShell `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="728e4-192">To display the properties and methods of the object that represents an environment variable in PowerShell, use the `Get-Member` cmdlet.</span></span> <span data-ttu-id="728e4-193">Om du till exempel vill visa metoder och egenskaper för alla objekt i `Env:` enheten skriver du:</span><span class="sxs-lookup"><span data-stu-id="728e4-193">For example, to display the methods and properties of all the objects in the `Env:` drive, type:</span></span>

```powershell
Get-Item -Path Env:* | Get-Member
```

<span data-ttu-id="728e4-194">PowerShell-hälsoleverantören ger dig åtkomst till miljövariabler i en PowerShell-enhet ( `Env:` enheten).</span><span class="sxs-lookup"><span data-stu-id="728e4-194">The PowerShell Environment provider lets you access environment variables in a PowerShell drive (the `Env:` drive).</span></span> <span data-ttu-id="728e4-195">Den här enheten ser ut ungefär som en fil system enhet.</span><span class="sxs-lookup"><span data-stu-id="728e4-195">This drive looks much like a file system drive.</span></span> <span data-ttu-id="728e4-196">Om du vill gå till `Env:` enheten skriver du:</span><span class="sxs-lookup"><span data-stu-id="728e4-196">To go to the `Env:` drive, type:</span></span>

```powershell
Set-Location Env:
```

<span data-ttu-id="728e4-197">Använd innehålls-cmdletar för att hämta eller ange värden för en miljö variabel.</span><span class="sxs-lookup"><span data-stu-id="728e4-197">Use the Content cmdlets to get or set the values of an environment variable.</span></span>

```powershell
PS Env:\> Set-Content -Path Test -Value 'Test value'
PS Env:\> Get-Content -Path Test
Test value
```

<span data-ttu-id="728e4-198">Du kan visa miljövariablerna i `Env:` enheten från andra PowerShell-enheter, och du kan gå in på `Env:` enheten för att visa och ändra miljövariablerna.</span><span class="sxs-lookup"><span data-stu-id="728e4-198">You can view the environment variables in the `Env:` drive from any other PowerShell drive, and you can go into the `Env:` drive to view and change the environment variables.</span></span>

### <a name="using-item-cmdlets"></a><span data-ttu-id="728e4-199">Använda objekt-cmdletar</span><span class="sxs-lookup"><span data-stu-id="728e4-199">Using Item cmdlets</span></span>

<span data-ttu-id="728e4-200">När du refererar till en miljö variabel, anger du `Env:` enhetens namn följt av namnet på variabeln.</span><span class="sxs-lookup"><span data-stu-id="728e4-200">When you refer to an environment variable, type the `Env:` drive name followed by the name of the variable.</span></span> <span data-ttu-id="728e4-201">Om du till exempel vill visa värdet för `COMPUTERNAME` miljö variabeln, skriver du:</span><span class="sxs-lookup"><span data-stu-id="728e4-201">For example, to display the value of the `COMPUTERNAME` environment variable, type:</span></span>

```powershell
Get-ChildItem Env:Computername
```

<span data-ttu-id="728e4-202">Om du vill visa värdena för alla miljövariabler skriver du:</span><span class="sxs-lookup"><span data-stu-id="728e4-202">To display the values of all the environment variables, type:</span></span>

```powershell
Get-ChildItem Env:
```

<span data-ttu-id="728e4-203">Eftersom miljövariablerna inte har underordnade objekt är resultatet av `Get-Item` och `Get-ChildItem` samma.</span><span class="sxs-lookup"><span data-stu-id="728e4-203">Because environment variables do not have child items, the output of `Get-Item` and `Get-ChildItem` is the same.</span></span>

<span data-ttu-id="728e4-204">Som standard visar PowerShell miljövariablerna i den ordning som de hämtar dem.</span><span class="sxs-lookup"><span data-stu-id="728e4-204">By default, PowerShell displays the environment variables in the order in which it retrieves them.</span></span> <span data-ttu-id="728e4-205">Om du vill sortera listan över miljövariabler efter variabel namn, skickar du ut resultatet av ett `Get-ChildItem` kommando till `Sort-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="728e4-205">To sort the list of environment variables by variable name, pipe the output of a `Get-ChildItem` command to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="728e4-206">Till exempel, från valfri PowerShell-enhet, skriver du:</span><span class="sxs-lookup"><span data-stu-id="728e4-206">For example, from any PowerShell drive, type:</span></span>

```powershell
Get-ChildItem Env: | Sort Name
```

<span data-ttu-id="728e4-207">Du kan också gå in på `Env:` enheten med hjälp av `Set-Location` cmdleten:</span><span class="sxs-lookup"><span data-stu-id="728e4-207">You can also go into the `Env:` drive by using the `Set-Location` cmdlet:</span></span>

```powershell
Set-Location Env:
```

<span data-ttu-id="728e4-208">När du är i `Env:` enheten kan du utelämna `Env:` enhets namnet från sökvägen.</span><span class="sxs-lookup"><span data-stu-id="728e4-208">When you are in the `Env:` drive, you can omit the `Env:` drive name from the path.</span></span> <span data-ttu-id="728e4-209">Om du till exempel vill visa alla miljövariabler skriver du:</span><span class="sxs-lookup"><span data-stu-id="728e4-209">For example, to display all the environment variables, type:</span></span>

```powershell
PS Env:\> Get-ChildItem
```

<span data-ttu-id="728e4-210">Om du vill visa värdet för `COMPUTERNAME` variabeln inifrån `Env:` enheten skriver du:</span><span class="sxs-lookup"><span data-stu-id="728e4-210">To display the value of the `COMPUTERNAME` variable from within the `Env:` drive, type:</span></span>

```powershell
PS Env:\> Get-ChildItem ComputerName
```

### <a name="saving-changes-to-environment-variables"></a><span data-ttu-id="728e4-211">Spara ändringar i miljövariabler</span><span class="sxs-lookup"><span data-stu-id="728e4-211">Saving changes to environment variables</span></span>

<span data-ttu-id="728e4-212">Om du vill göra en beständig ändring i en miljö variabel i Windows kan du använda system kontroll panelen.</span><span class="sxs-lookup"><span data-stu-id="728e4-212">To make a persistent change to an environment variable on Windows, use the System Control Panel.</span></span> <span data-ttu-id="728e4-213">Välj **Avancerade systeminställningar**.</span><span class="sxs-lookup"><span data-stu-id="728e4-213">Select **Advanced System Settings**.</span></span> <span data-ttu-id="728e4-214">På fliken **Avancerat** klickar du på **miljö variabel...**. Du kan lägga till eller redigera befintliga miljövariabler i scope för **användare** och **system** (datorer).</span><span class="sxs-lookup"><span data-stu-id="728e4-214">On the **Advanced** tab, click **Environment Variable...**. You can add or edit existing environment variables in the **User** and **System** (Machine) scopes.</span></span> <span data-ttu-id="728e4-215">Windows skriver dessa värden till registret så att de behålls mellan sessioner och omstarter av systemet.</span><span class="sxs-lookup"><span data-stu-id="728e4-215">Windows writes these values to the Registry so that they persist across sessions and system restarts.</span></span>

<span data-ttu-id="728e4-216">Alternativt kan du lägga till eller ändra miljövariabler i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="728e4-216">Alternately, you can add or change environment variables in your PowerShell profile.</span></span> <span data-ttu-id="728e4-217">Den här metoden fungerar för alla versioner av PowerShell på alla plattformar som stöds.</span><span class="sxs-lookup"><span data-stu-id="728e4-217">This method works for any version of PowerShell on any supported platform.</span></span>

### <a name="using-systemenvironment-methods"></a><span data-ttu-id="728e4-218">Använda system. miljö metoder</span><span class="sxs-lookup"><span data-stu-id="728e4-218">Using System.Environment methods</span></span>

<span data-ttu-id="728e4-219">Klassen **system. Environment** tillhandahåller **GetEnvironmentVariable** -och **SetEnvironmentVariable** -metoder som gör att du kan ange variabelns omfång.</span><span class="sxs-lookup"><span data-stu-id="728e4-219">The **System.Environment** class provides **GetEnvironmentVariable** and **SetEnvironmentVariable** methods that allow you to specify the scope of the variable.</span></span>

<span data-ttu-id="728e4-220">I följande exempel används metoden **GetEnvironmentVariable** för att hämta dator inställningen för `PSModulePath` och metoden **SetEnvironmentVariable** för att lägga till `C:\Program Files\Fabrikam\Modules` sökvägen till värdet.</span><span class="sxs-lookup"><span data-stu-id="728e4-220">The following example uses the **GetEnvironmentVariable** method to get the machine setting of `PSModulePath` and the **SetEnvironmentVariable** method to add the `C:\Program Files\Fabrikam\Modules` path to the value.</span></span>

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'Machine')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable("PSModulePath", $newpath, 'Machine')
```

<span data-ttu-id="728e4-221">Mer information om metoderna i klassen **system. miljö** finns i [miljö metoder](/dotnet/api/system.environment).</span><span class="sxs-lookup"><span data-stu-id="728e4-221">For more information about the methods of the **System.Environment** class, see [Environment Methods](/dotnet/api/system.environment).</span></span>

## <a name="see-also"></a><span data-ttu-id="728e4-222">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="728e4-222">SEE ALSO</span></span>

- [<span data-ttu-id="728e4-223">Miljö (Provider)</span><span class="sxs-lookup"><span data-stu-id="728e4-223">Environment (provider)</span></span>](../About/about_Environment_Provider.md)
- [<span data-ttu-id="728e4-224">about_Modules</span><span class="sxs-lookup"><span data-stu-id="728e4-224">about_Modules</span></span>](about_Modules.md)
