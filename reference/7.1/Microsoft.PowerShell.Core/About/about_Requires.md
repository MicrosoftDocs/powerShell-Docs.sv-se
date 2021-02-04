---
description: Förhindrar att ett skript körs utan de element som krävs.
Locale: en-US
ms.date: 12/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_requires?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Requires
ms.openlocfilehash: af7b557e399385589f3ddbbeb6b1f514c0f550f5
ms.sourcegitcommit: 9a86cac80402d8193147058d4ba50e07b26059dd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97490500"
---
# <a name="about-requires"></a><span data-ttu-id="02540-103">Om kräver</span><span class="sxs-lookup"><span data-stu-id="02540-103">About Requires</span></span>

## <a name="short-description"></a><span data-ttu-id="02540-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="02540-104">Short description</span></span>
<span data-ttu-id="02540-105">Förhindrar att ett skript körs utan de element som krävs.</span><span class="sxs-lookup"><span data-stu-id="02540-105">Prevents a script from running without the required elements.</span></span>

## <a name="long-description"></a><span data-ttu-id="02540-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="02540-106">Long description</span></span>

<span data-ttu-id="02540-107">`#Requires`Instruktionen förhindrar att ett skript körs om inte PowerShell-versionen, modulerna (och versionen) eller snapin-modulerna (och versionen) och versions krav uppfylls.</span><span class="sxs-lookup"><span data-stu-id="02540-107">The `#Requires` statement prevents a script from running unless the PowerShell version, modules (and version), or snap-ins (and version), and edition prerequisites are met.</span></span> <span data-ttu-id="02540-108">Om kraven inte uppfylls, kör inte PowerShell skriptet.</span><span class="sxs-lookup"><span data-stu-id="02540-108">If the prerequisites aren't met, PowerShell doesn't run the script.</span></span>

### <a name="syntax"></a><span data-ttu-id="02540-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="02540-109">Syntax</span></span>

```
#Requires -Version <N>[.<n>]
#Requires -PSSnapin <PSSnapin-Name> [-Version <N>[.<n>]]
#Requires -Modules { <Module-Name> | <Hashtable> }
#Requires -PSEdition <PSEdition-Name>
#Requires -ShellId <ShellId> -PSSnapin <PSSnapin-Name> [-Version <N>[.<n>]]
#Requires -RunAsAdministrator
```

<span data-ttu-id="02540-110">Mer information om syntaxen finns i [ScriptRequirements](/dotnet/api/system.management.automation.language.scriptrequirements).</span><span class="sxs-lookup"><span data-stu-id="02540-110">For more information about the syntax, see [ScriptRequirements](/dotnet/api/system.management.automation.language.scriptrequirements).</span></span>

### <a name="rules-for-use"></a><span data-ttu-id="02540-111">Regler för användning</span><span class="sxs-lookup"><span data-stu-id="02540-111">Rules for use</span></span>

<span data-ttu-id="02540-112">Ett skript kan innehålla mer än en `#Requires` instruktion.</span><span class="sxs-lookup"><span data-stu-id="02540-112">A script can include more than one `#Requires` statement.</span></span> <span data-ttu-id="02540-113">`#Requires`Uttrycken kan visas på alla rader i ett skript.</span><span class="sxs-lookup"><span data-stu-id="02540-113">The `#Requires` statements can appear on any line in a script.</span></span>

<span data-ttu-id="02540-114">Att placera en `#Requires` instruktion inuti en funktion begränsar inte dess omfång.</span><span class="sxs-lookup"><span data-stu-id="02540-114">Placing a `#Requires` statement inside a function does NOT limit its scope.</span></span> <span data-ttu-id="02540-115">Alla `#Requires` instruktioner tillämpas alltid globalt och måste vara uppfyllda innan skriptet kan köras.</span><span class="sxs-lookup"><span data-stu-id="02540-115">All `#Requires` statements are always applied globally, and must be met, before the script can execute.</span></span>

> [!WARNING]
> <span data-ttu-id="02540-116">Även om en `#Requires` instruktion kan visas på en rad i ett skript, påverkar dess placering i ett skript inte sekvensen för dess program.</span><span class="sxs-lookup"><span data-stu-id="02540-116">Even though a `#Requires` statement can appear on any line in a script, its position in a script does not affect the sequence of its application.</span></span> <span data-ttu-id="02540-117">Det globala tillstånd som `#Requires` instruktionen visar måste vara uppfyllt innan skript körningen.</span><span class="sxs-lookup"><span data-stu-id="02540-117">The global state the `#Requires` statement presents must be met before script execution.</span></span>

<span data-ttu-id="02540-118">Exempel:</span><span class="sxs-lookup"><span data-stu-id="02540-118">Example:</span></span>

```powershell
Get-Module AzureRM.Netcore | Remove-Module
#Requires -Modules AzureRM.Netcore
```

<span data-ttu-id="02540-119">Du kanske tror att ovanstående kod inte ska köras eftersom modulen som krävs togs bort före `#Requires` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="02540-119">You might think that the above code shouldn't run because the required module was removed before the `#Requires` statement.</span></span> <span data-ttu-id="02540-120">Men `#Requires` läget var uppfyllt innan skriptet kan köras.</span><span class="sxs-lookup"><span data-stu-id="02540-120">However, the `#Requires` state had to be met before the script could even execute.</span></span> <span data-ttu-id="02540-121">Den första raden i skriptet har ogiltig status.</span><span class="sxs-lookup"><span data-stu-id="02540-121">Then the first line of the script invalidated the required state.</span></span>

### <a name="parameters"></a><span data-ttu-id="02540-122">Parametrar</span><span class="sxs-lookup"><span data-stu-id="02540-122">Parameters</span></span>

#### <a name="-assembly-assembly-path--net-assembly-specification"></a><span data-ttu-id="02540-123">– Sammansättning \<Assembly path> |\<.NET assembly specification></span><span class="sxs-lookup"><span data-stu-id="02540-123">-Assembly \<Assembly path> | \<.NET assembly specification></span></span>

> [!IMPORTANT]
> <span data-ttu-id="02540-124">`-Assembly`Syntaxen är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="02540-124">The `-Assembly` syntax is deprecated.</span></span> <span data-ttu-id="02540-125">Funktionen fungerar inte.</span><span class="sxs-lookup"><span data-stu-id="02540-125">It serves no function.</span></span> <span data-ttu-id="02540-126">Syntaxen lades till i PowerShell 5,1 men stöd koden har aldrig implementerats.</span><span class="sxs-lookup"><span data-stu-id="02540-126">The syntax was added in PowerShell 5.1 but the supporting code was never implemented.</span></span> <span data-ttu-id="02540-127">Syntaxen accepteras fortfarande för bakåtkompatibilitet.</span><span class="sxs-lookup"><span data-stu-id="02540-127">The syntax is still accepted for backward compatibility.</span></span>

<span data-ttu-id="02540-128">Anger sökvägen till sammansättnings-DLL-filen eller ett .NET-sammansättnings namn.</span><span class="sxs-lookup"><span data-stu-id="02540-128">Specifies the path to the assembly DLL file or a .NET assembly name.</span></span> <span data-ttu-id="02540-129">**Sammansättnings** parametern introducerades i PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="02540-129">The **Assembly** parameter was introduced in PowerShell 5.0.</span></span> <span data-ttu-id="02540-130">Mer information om .NET-sammansättningar finns i [sammansättnings namn](/dotnet/standard/assembly/names).</span><span class="sxs-lookup"><span data-stu-id="02540-130">For more information about .NET assemblies, see [Assembly names](/dotnet/standard/assembly/names).</span></span>

<span data-ttu-id="02540-131">Exempel:</span><span class="sxs-lookup"><span data-stu-id="02540-131">For example:</span></span>

```
#Requires -Assembly path\to\foo.dll
```

```
#Requires -Assembly "System.Management.Automation, Version=3.0.0.0,
  Culture=neutral, PublicKeyToken=31bf3856ad364e35"
```

#### <a name="-version-nn"></a><span data-ttu-id="02540-132">-Version \<N\> [. \<n\> ]</span><span class="sxs-lookup"><span data-stu-id="02540-132">-Version \<N\>[.\<n\>]</span></span>

<span data-ttu-id="02540-133">Anger den lägsta version av PowerShell som skriptet kräver.</span><span class="sxs-lookup"><span data-stu-id="02540-133">Specifies the minimum version of PowerShell that the script requires.</span></span> <span data-ttu-id="02540-134">Ange ett högre versions nummer och ett valfritt lägre versions nummer.</span><span class="sxs-lookup"><span data-stu-id="02540-134">Enter a major version number and optional minor version number.</span></span>

<span data-ttu-id="02540-135">Exempel:</span><span class="sxs-lookup"><span data-stu-id="02540-135">For example:</span></span>

```powershell
#Requires -Version 6.0
```

#### <a name="-pssnapin-pssnapin-name--version-nn"></a><span data-ttu-id="02540-136">-PSSnapin \<PSSnapin-Name\> [-version \<N\> [. \<n\> ]]</span><span class="sxs-lookup"><span data-stu-id="02540-136">-PSSnapin \<PSSnapin-Name\> [-Version \<N\>[.\<n\>]]</span></span>

<span data-ttu-id="02540-137">Anger en PowerShell-snapin-modul som skriptet kräver.</span><span class="sxs-lookup"><span data-stu-id="02540-137">Specifies a PowerShell snap-in that the script requires.</span></span> <span data-ttu-id="02540-138">Ange namnet på snapin-modulen och ett valfritt versions nummer.</span><span class="sxs-lookup"><span data-stu-id="02540-138">Enter the snap-in name and an optional version number.</span></span>

<span data-ttu-id="02540-139">Exempel:</span><span class="sxs-lookup"><span data-stu-id="02540-139">For example:</span></span>

```powershell
#Requires -PSSnapin DiskSnapin -Version 1.2
```

#### <a name="-modules-module-name--hashtable"></a><span data-ttu-id="02540-140">– Moduler \<Module-Name\> |\<Hashtable\></span><span class="sxs-lookup"><span data-stu-id="02540-140">-Modules \<Module-Name\> | \<Hashtable\></span></span>

<span data-ttu-id="02540-141">Anger PowerShell-moduler som skriptet kräver.</span><span class="sxs-lookup"><span data-stu-id="02540-141">Specifies PowerShell modules that the script requires.</span></span> <span data-ttu-id="02540-142">Ange modulens namn och ett valfritt versions nummer.</span><span class="sxs-lookup"><span data-stu-id="02540-142">Enter the module name and an optional version number.</span></span>

<span data-ttu-id="02540-143">Om de moduler som krävs inte finns i den aktuella sessionen importeras de av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="02540-143">If the required modules aren't in the current session, PowerShell imports them.</span></span>
<span data-ttu-id="02540-144">Om modulerna inte kan importeras, genererar PowerShell ett avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="02540-144">If the modules can't be imported, PowerShell throws a terminating error.</span></span>

<span data-ttu-id="02540-145">Ange modulnamnet ( \<String\> ) eller en hash-tabell för varje modul.</span><span class="sxs-lookup"><span data-stu-id="02540-145">For each module, type the module name (\<String\>) or a hash table.</span></span> <span data-ttu-id="02540-146">Värdet kan vara en kombination av strängar och hash-tabeller.</span><span class="sxs-lookup"><span data-stu-id="02540-146">The value can be a combination of strings and hash tables.</span></span> <span data-ttu-id="02540-147">Hash-tabellen har följande nycklar.</span><span class="sxs-lookup"><span data-stu-id="02540-147">The hash table has the following keys.</span></span>

- <span data-ttu-id="02540-148">`ModuleName` - **Krävs** Anger namnet på modulen.</span><span class="sxs-lookup"><span data-stu-id="02540-148">`ModuleName` - **Required** Specifies the module name.</span></span>
- <span data-ttu-id="02540-149">`GUID` - **Valfritt** Anger modulens GUID.</span><span class="sxs-lookup"><span data-stu-id="02540-149">`GUID` - **Optional** Specifies the GUID of the module.</span></span>
- <span data-ttu-id="02540-150">Du **måste** också ange en av de tre nycklarna nedan.</span><span class="sxs-lookup"><span data-stu-id="02540-150">It's also **Required** to specify one of the three below keys.</span></span> <span data-ttu-id="02540-151">Nycklarna kan inte användas tillsammans.</span><span class="sxs-lookup"><span data-stu-id="02540-151">These keys can't be used together.</span></span>
  - <span data-ttu-id="02540-152">`ModuleVersion` -Anger en minsta godtagbar version av modulen.</span><span class="sxs-lookup"><span data-stu-id="02540-152">`ModuleVersion` - Specifies a minimum acceptable version of the module.</span></span>
  - <span data-ttu-id="02540-153">`RequiredVersion` -Anger en exakt, obligatorisk version av modulen.</span><span class="sxs-lookup"><span data-stu-id="02540-153">`RequiredVersion` - Specifies an exact, required version of the module.</span></span>
  - <span data-ttu-id="02540-154">`MaximumVersion` -Anger den högsta godkända versionen av modulen.</span><span class="sxs-lookup"><span data-stu-id="02540-154">`MaximumVersion` - Specifies the maximum acceptable version of the module.</span></span>

> [!NOTE]
> <span data-ttu-id="02540-155">`RequiredVersion` lades till i Windows PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="02540-155">`RequiredVersion` was added in Windows PowerShell 5.0.</span></span>
> <span data-ttu-id="02540-156">`MaximumVersion` lades till i Windows PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="02540-156">`MaximumVersion` was added in Windows PowerShell 5.1.</span></span>

<span data-ttu-id="02540-157">Exempel:</span><span class="sxs-lookup"><span data-stu-id="02540-157">For example:</span></span>

<span data-ttu-id="02540-158">Kräv att `AzureRM.Netcore` (version `0.12.0` eller större) är installerad.</span><span class="sxs-lookup"><span data-stu-id="02540-158">Require that `AzureRM.Netcore` (version `0.12.0` or greater) is installed.</span></span>

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; ModuleVersion="0.12.0" }
```

<span data-ttu-id="02540-159">Kräv att `AzureRM.Netcore` (**endast** version `0.12.0` ) är installerat.</span><span class="sxs-lookup"><span data-stu-id="02540-159">Require that `AzureRM.Netcore` (**only** version `0.12.0`) is installed.</span></span>

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; RequiredVersion="0.12.0" }
```

<span data-ttu-id="02540-160">Kräver att `AzureRM.Netcore` (version `0.12.0` eller lägre) är installerad.</span><span class="sxs-lookup"><span data-stu-id="02540-160">Requires that `AzureRM.Netcore` (version `0.12.0` or lesser) is installed.</span></span>

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; MaximumVersion="0.12.0" }
```

<span data-ttu-id="02540-161">Kräv att alla versioner av `AzureRM.Netcore` och `PowerShellGet` är installerade.</span><span class="sxs-lookup"><span data-stu-id="02540-161">Require that any version of `AzureRM.Netcore` and `PowerShellGet` is installed.</span></span>

```powershell
#Requires -Modules AzureRM.Netcore, PowerShellGet
```

<span data-ttu-id="02540-162">När du använder `RequiredVersion` nyckeln måste du se till att versions strängen exakt matchar den versions sträng du behöver.</span><span class="sxs-lookup"><span data-stu-id="02540-162">When using the `RequiredVersion` key, ensure your version string exactly matches the version string you require.</span></span>

```powershell
Get-Module AzureRM.Netcore -ListAvailable
```

```Output
    Directory: /home/azureuser/.local/share/powershell/Modules

ModuleType Version Name            PSEdition ExportedCommands
---------- ------- ----            --------- ----------------
Script     0.12.0  AzureRM.Netcore Core
```

<span data-ttu-id="02540-163">Följande exempel Miss lyckas eftersom **0,12** inte exakt matchar **0.12.0**.</span><span class="sxs-lookup"><span data-stu-id="02540-163">The following example fails because **0.12** doesn't exactly match **0.12.0**.</span></span>

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; RequiredVersion="0.12" }
```

#### <a name="-psedition-psedition-name"></a><span data-ttu-id="02540-164">– PSEdition \<PSEdition-Name\></span><span class="sxs-lookup"><span data-stu-id="02540-164">-PSEdition \<PSEdition-Name\></span></span>

<span data-ttu-id="02540-165">Anger en PowerShell-utgåva som skriptet kräver.</span><span class="sxs-lookup"><span data-stu-id="02540-165">Specifies a PowerShell edition that the script requires.</span></span> <span data-ttu-id="02540-166">Giltiga värden är **Core** för PowerShell-kärnan och **Desktop** för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="02540-166">Valid values are **Core** for PowerShell Core and **Desktop** for Windows PowerShell.</span></span>

<span data-ttu-id="02540-167">Exempel:</span><span class="sxs-lookup"><span data-stu-id="02540-167">For example:</span></span>

```powershell
#Requires -PSEdition Core
```

#### <a name="-shellid"></a><span data-ttu-id="02540-168">-ShellId</span><span class="sxs-lookup"><span data-stu-id="02540-168">-ShellId</span></span>

<span data-ttu-id="02540-169">Anger det gränssnitt som skriptet kräver.</span><span class="sxs-lookup"><span data-stu-id="02540-169">Specifies the shell that the script requires.</span></span> <span data-ttu-id="02540-170">Ange gränssnitts-ID: t.</span><span class="sxs-lookup"><span data-stu-id="02540-170">Enter the shell ID.</span></span> <span data-ttu-id="02540-171">Om du använder parametern **ShellId** måste du också ta med parametern **PSSnapin** .</span><span class="sxs-lookup"><span data-stu-id="02540-171">If you use the **ShellId** parameter, you must also include the **PSSnapin** parameter.</span></span>
<span data-ttu-id="02540-172">Du kan hitta den aktuella **ShellId** genom att fråga den `$ShellId` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="02540-172">You can find the current **ShellId** by querying the `$ShellId` automatic variable.</span></span>

<span data-ttu-id="02540-173">Exempel:</span><span class="sxs-lookup"><span data-stu-id="02540-173">For example:</span></span>

```powershell
#Requires -ShellId MyLocalShell -PSSnapin Microsoft.PowerShell.Core
```

> [!NOTE]
> <span data-ttu-id="02540-174">Den här parametern är avsedd för användning i mini-Shells, som är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="02540-174">This parameter is intended for use in mini-shells, which have been deprecated.</span></span>

#### <a name="-runasadministrator"></a><span data-ttu-id="02540-175">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="02540-175">-RunAsAdministrator</span></span>

<span data-ttu-id="02540-176">När den här växel parametern läggs till i din `#Requires` instruktion, anger den att den PowerShell-session där du kör skriptet måste startas med utökade användar rättigheter.</span><span class="sxs-lookup"><span data-stu-id="02540-176">When this switch parameter is added to your `#Requires` statement, it specifies that the PowerShell session in which you're running the script must be started with elevated user rights.</span></span> <span data-ttu-id="02540-177">Parametern **RunAsAdministrator** ignoreras på ett operativ system som inte är från Windows.</span><span class="sxs-lookup"><span data-stu-id="02540-177">The **RunAsAdministrator** parameter is ignored on a non-Windows operating system.</span></span> <span data-ttu-id="02540-178">**RunAsAdministrator** -parametern introducerades i PowerShell 4,0.</span><span class="sxs-lookup"><span data-stu-id="02540-178">The **RunAsAdministrator** parameter was introduced in PowerShell 4.0.</span></span>

<span data-ttu-id="02540-179">Exempel:</span><span class="sxs-lookup"><span data-stu-id="02540-179">For example:</span></span>

```powershell
#Requires -RunAsAdministrator
```

### <a name="examples"></a><span data-ttu-id="02540-180">Exempel</span><span class="sxs-lookup"><span data-stu-id="02540-180">Examples</span></span>

<span data-ttu-id="02540-181">Följande skript har två `#Requires` instruktioner.</span><span class="sxs-lookup"><span data-stu-id="02540-181">The following script has two `#Requires` statements.</span></span> <span data-ttu-id="02540-182">Om kraven som anges i båda uttrycken inte uppfylls, körs inte skriptet.</span><span class="sxs-lookup"><span data-stu-id="02540-182">If the requirements specified in both statements aren't met, the script doesn't run.</span></span> <span data-ttu-id="02540-183">Varje `#Requires` instruktion måste vara det första objektet på en rad:</span><span class="sxs-lookup"><span data-stu-id="02540-183">Each `#Requires` statement must be the first item on a line:</span></span>

```powershell
#Requires -Modules AzureRM.Netcore
#Requires -Version 6.0
Param
(
    [parameter(Mandatory=$true)]
    [String[]]
    $Path
)
...
```

## <a name="see-also"></a><span data-ttu-id="02540-184">Se även</span><span class="sxs-lookup"><span data-stu-id="02540-184">See also</span></span>

[<span data-ttu-id="02540-185">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="02540-185">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="02540-186">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="02540-186">about_Language_Keywords</span></span>](about_Language_Keywords.md)
