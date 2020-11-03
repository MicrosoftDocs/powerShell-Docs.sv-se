---
description: Förhindrar att ett skript körs utan de element som krävs.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_requires?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Requires
ms.openlocfilehash: c6b10137ca58da93caff365a50b125929fd4d11a
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272331"
---
# <a name="about-requires"></a><span data-ttu-id="26809-104">Om kräver</span><span class="sxs-lookup"><span data-stu-id="26809-104">About Requires</span></span>

## <a name="short-description"></a><span data-ttu-id="26809-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="26809-105">Short description</span></span>
<span data-ttu-id="26809-106">Förhindrar att ett skript körs utan de element som krävs.</span><span class="sxs-lookup"><span data-stu-id="26809-106">Prevents a script from running without the required elements.</span></span>

## <a name="long-description"></a><span data-ttu-id="26809-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="26809-107">Long description</span></span>

<span data-ttu-id="26809-108">`#Requires`Instruktionen förhindrar att ett skript körs om inte PowerShell-versionen, modulerna (och versionen) eller snapin-modulerna (och versionen) och versions krav uppfylls.</span><span class="sxs-lookup"><span data-stu-id="26809-108">The `#Requires` statement prevents a script from running unless the PowerShell version, modules (and version), or snap-ins (and version), and edition prerequisites are met.</span></span> <span data-ttu-id="26809-109">Om kraven inte uppfylls, kör inte PowerShell skriptet.</span><span class="sxs-lookup"><span data-stu-id="26809-109">If the prerequisites aren't met, PowerShell doesn't run the script.</span></span>

### <a name="syntax"></a><span data-ttu-id="26809-110">Syntax</span><span class="sxs-lookup"><span data-stu-id="26809-110">Syntax</span></span>

```
#Requires -Assembly { <Path to .dll> | <.NET assembly specification> }
#Requires -Version <N>[.<n>]
#Requires -PSSnapin <PSSnapin-Name> [-Version <N>[.<n>]]
#Requires -Modules { <Module-Name> | <Hashtable> }
#Requires -PSEdition <PSEdition-Name>
#Requires -ShellId <ShellId> -PSSnapin <PSSnapin-Name> [-Version <N>[.<n>]]
#Requires -RunAsAdministrator
```

<span data-ttu-id="26809-111">Mer information om syntaxen finns i [ScriptRequirements](/dotnet/api/system.management.automation.language.scriptrequirements).</span><span class="sxs-lookup"><span data-stu-id="26809-111">For more information about the syntax, see [ScriptRequirements](/dotnet/api/system.management.automation.language.scriptrequirements).</span></span>

### <a name="rules-for-use"></a><span data-ttu-id="26809-112">Regler för användning</span><span class="sxs-lookup"><span data-stu-id="26809-112">Rules for use</span></span>

<span data-ttu-id="26809-113">Ett skript kan innehålla mer än en `#Requires` instruktion.</span><span class="sxs-lookup"><span data-stu-id="26809-113">A script can include more than one `#Requires` statement.</span></span> <span data-ttu-id="26809-114">`#Requires`Uttrycken kan visas på alla rader i ett skript.</span><span class="sxs-lookup"><span data-stu-id="26809-114">The `#Requires` statements can appear on any line in a script.</span></span>

<span data-ttu-id="26809-115">Att placera en `#Requires` instruktion inuti en funktion begränsar inte dess omfång.</span><span class="sxs-lookup"><span data-stu-id="26809-115">Placing a `#Requires` statement inside a function does NOT limit its scope.</span></span> <span data-ttu-id="26809-116">Alla `#Requires` instruktioner tillämpas alltid globalt och måste vara uppfyllda innan skriptet kan köras.</span><span class="sxs-lookup"><span data-stu-id="26809-116">All `#Requires` statements are always applied globally, and must be met, before the script can execute.</span></span>

> [!WARNING]
> <span data-ttu-id="26809-117">Även om en `#Requires` instruktion kan visas på en rad i ett skript, påverkar dess placering i ett skript inte sekvensen för dess program.</span><span class="sxs-lookup"><span data-stu-id="26809-117">Even though a `#Requires` statement can appear on any line in a script, its position in a script does not affect the sequence of its application.</span></span> <span data-ttu-id="26809-118">Det globala tillstånd som `#Requires` instruktionen visar måste vara uppfyllt innan skript körningen.</span><span class="sxs-lookup"><span data-stu-id="26809-118">The global state the `#Requires` statement presents must be met before script execution.</span></span>

<span data-ttu-id="26809-119">Exempel:</span><span class="sxs-lookup"><span data-stu-id="26809-119">Example:</span></span>

```powershell
Get-Module AzureRM.Netcore | Remove-Module
#Requires -Modules AzureRM.Netcore
```

<span data-ttu-id="26809-120">Du kanske tror att ovanstående kod inte ska köras eftersom modulen som krävs togs bort före `#Requires` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="26809-120">You might think that the above code shouldn't run because the required module was removed before the `#Requires` statement.</span></span> <span data-ttu-id="26809-121">Men `#Requires` läget var uppfyllt innan skriptet kan köras.</span><span class="sxs-lookup"><span data-stu-id="26809-121">However, the `#Requires` state had to be met before the script could even execute.</span></span> <span data-ttu-id="26809-122">Den första raden i skriptet har ogiltig status.</span><span class="sxs-lookup"><span data-stu-id="26809-122">Then the first line of the script invalidated the required state.</span></span>

### <a name="parameters"></a><span data-ttu-id="26809-123">Parametrar</span><span class="sxs-lookup"><span data-stu-id="26809-123">Parameters</span></span>

#### <a name="-assembly-assembly-path--net-assembly-specification"></a><span data-ttu-id="26809-124">– Sammansättning \<Assembly path> |\<.NET assembly specification></span><span class="sxs-lookup"><span data-stu-id="26809-124">-Assembly \<Assembly path> | \<.NET assembly specification></span></span>

<span data-ttu-id="26809-125">Anger sökvägen till sammansättnings-DLL-filen eller ett .NET-sammansättnings namn.</span><span class="sxs-lookup"><span data-stu-id="26809-125">Specifies the path to the assembly DLL file or a .NET assembly name.</span></span> <span data-ttu-id="26809-126">**Sammansättnings** parametern introducerades i PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="26809-126">The **Assembly** parameter was introduced in PowerShell 5.0.</span></span> <span data-ttu-id="26809-127">Mer information om .NET-sammansättningar finns i [sammansättnings namn](/dotnet/standard/assembly/names).</span><span class="sxs-lookup"><span data-stu-id="26809-127">For more information about .NET assemblies, see [Assembly names](/dotnet/standard/assembly/names).</span></span>

<span data-ttu-id="26809-128">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="26809-128">For example:</span></span>

```
#Requires -Assembly path\to\foo.dll
```

```
#Requires -Assembly "System.Management.Automation, Version=3.0.0.0,
  Culture=neutral, PublicKeyToken=31bf3856ad364e35"
```

#### <a name="-version-nn"></a><span data-ttu-id="26809-129">-Version \<N\> [. \<n\> ]</span><span class="sxs-lookup"><span data-stu-id="26809-129">-Version \<N\>[.\<n\>]</span></span>

<span data-ttu-id="26809-130">Anger den lägsta version av PowerShell som skriptet kräver.</span><span class="sxs-lookup"><span data-stu-id="26809-130">Specifies the minimum version of PowerShell that the script requires.</span></span> <span data-ttu-id="26809-131">Ange ett högre versions nummer och ett valfritt lägre versions nummer.</span><span class="sxs-lookup"><span data-stu-id="26809-131">Enter a major version number and optional minor version number.</span></span>

<span data-ttu-id="26809-132">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="26809-132">For example:</span></span>

```powershell
#Requires -Version 6.0
```

#### <a name="-pssnapin-pssnapin-name--version-nn"></a><span data-ttu-id="26809-133">-PSSnapin \<PSSnapin-Name\> [-version \<N\> [. \<n\> ]]</span><span class="sxs-lookup"><span data-stu-id="26809-133">-PSSnapin \<PSSnapin-Name\> [-Version \<N\>[.\<n\>]]</span></span>

<span data-ttu-id="26809-134">Anger en PowerShell-snapin-modul som skriptet kräver.</span><span class="sxs-lookup"><span data-stu-id="26809-134">Specifies a PowerShell snap-in that the script requires.</span></span> <span data-ttu-id="26809-135">Ange namnet på snapin-modulen och ett valfritt versions nummer.</span><span class="sxs-lookup"><span data-stu-id="26809-135">Enter the snap-in name and an optional version number.</span></span>

<span data-ttu-id="26809-136">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="26809-136">For example:</span></span>

```powershell
#Requires -PSSnapin DiskSnapin -Version 1.2
```

#### <a name="-modules-module-name--hashtable"></a><span data-ttu-id="26809-137">– Moduler \<Module-Name\> |\<Hashtable\></span><span class="sxs-lookup"><span data-stu-id="26809-137">-Modules \<Module-Name\> | \<Hashtable\></span></span>

<span data-ttu-id="26809-138">Anger PowerShell-moduler som skriptet kräver.</span><span class="sxs-lookup"><span data-stu-id="26809-138">Specifies PowerShell modules that the script requires.</span></span> <span data-ttu-id="26809-139">Ange modulens namn och ett valfritt versions nummer.</span><span class="sxs-lookup"><span data-stu-id="26809-139">Enter the module name and an optional version number.</span></span>

<span data-ttu-id="26809-140">Om de moduler som krävs inte finns i den aktuella sessionen importeras de av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="26809-140">If the required modules aren't in the current session, PowerShell imports them.</span></span>
<span data-ttu-id="26809-141">Om modulerna inte kan importeras, genererar PowerShell ett avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="26809-141">If the modules can't be imported, PowerShell throws a terminating error.</span></span>

<span data-ttu-id="26809-142">Ange modulnamnet ( \<String\> ) eller en hash-tabell för varje modul.</span><span class="sxs-lookup"><span data-stu-id="26809-142">For each module, type the module name (\<String\>) or a hash table.</span></span> <span data-ttu-id="26809-143">Värdet kan vara en kombination av strängar och hash-tabeller.</span><span class="sxs-lookup"><span data-stu-id="26809-143">The value can be a combination of strings and hash tables.</span></span> <span data-ttu-id="26809-144">Hash-tabellen har följande nycklar.</span><span class="sxs-lookup"><span data-stu-id="26809-144">The hash table has the following keys.</span></span>

- <span data-ttu-id="26809-145">`ModuleName` - **Krävs** Anger namnet på modulen.</span><span class="sxs-lookup"><span data-stu-id="26809-145">`ModuleName` - **Required** Specifies the module name.</span></span>
- <span data-ttu-id="26809-146">`GUID` - **Valfritt** Anger modulens GUID.</span><span class="sxs-lookup"><span data-stu-id="26809-146">`GUID` - **Optional** Specifies the GUID of the module.</span></span>
- <span data-ttu-id="26809-147">Du **måste** också ange en av de tre nycklarna nedan.</span><span class="sxs-lookup"><span data-stu-id="26809-147">It's also **Required** to specify one of the three below keys.</span></span> <span data-ttu-id="26809-148">Nycklarna kan inte användas tillsammans.</span><span class="sxs-lookup"><span data-stu-id="26809-148">These keys can't be used together.</span></span>
  - <span data-ttu-id="26809-149">`ModuleVersion` -Anger en minsta godtagbar version av modulen.</span><span class="sxs-lookup"><span data-stu-id="26809-149">`ModuleVersion` - Specifies a minimum acceptable version of the module.</span></span>
  - <span data-ttu-id="26809-150">`RequiredVersion` -Anger en exakt, obligatorisk version av modulen.</span><span class="sxs-lookup"><span data-stu-id="26809-150">`RequiredVersion` - Specifies an exact, required version of the module.</span></span>
  - <span data-ttu-id="26809-151">`MaximumVersion` -Anger den högsta godkända versionen av modulen.</span><span class="sxs-lookup"><span data-stu-id="26809-151">`MaximumVersion` - Specifies the maximum acceptable version of the module.</span></span>

> [!NOTE]
> <span data-ttu-id="26809-152">`RequiredVersion` lades till i Windows PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="26809-152">`RequiredVersion` was added in Windows PowerShell 5.0.</span></span>
> <span data-ttu-id="26809-153">`MaximumVersion` lades till i Windows PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="26809-153">`MaximumVersion` was added in Windows PowerShell 5.1.</span></span>

<span data-ttu-id="26809-154">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="26809-154">For example:</span></span>

<span data-ttu-id="26809-155">Kräv att `AzureRM.Netcore` (version `0.12.0` eller större) är installerad.</span><span class="sxs-lookup"><span data-stu-id="26809-155">Require that `AzureRM.Netcore` (version `0.12.0` or greater) is installed.</span></span>

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; ModuleVersion="0.12.0" }
```

<span data-ttu-id="26809-156">Kräv att `AzureRM.Netcore` ( **endast** version `0.12.0` ) är installerat.</span><span class="sxs-lookup"><span data-stu-id="26809-156">Require that `AzureRM.Netcore` ( **only** version `0.12.0`) is installed.</span></span>

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; RequiredVersion="0.12.0" }
```

<span data-ttu-id="26809-157">Kräver att `AzureRM.Netcore` (version `0.12.0` eller lägre) är installerad.</span><span class="sxs-lookup"><span data-stu-id="26809-157">Requires that `AzureRM.Netcore` (version `0.12.0` or lesser) is installed.</span></span>

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; MaximumVersion="0.12.0" }
```

<span data-ttu-id="26809-158">Kräv att alla versioner av `AzureRM.Netcore` och `PowerShellGet` är installerade.</span><span class="sxs-lookup"><span data-stu-id="26809-158">Require that any version of `AzureRM.Netcore` and `PowerShellGet` is installed.</span></span>

```powershell
#Requires -Modules AzureRM.Netcore, PowerShellGet
```

<span data-ttu-id="26809-159">När du använder `RequiredVersion` nyckeln måste du se till att versions strängen exakt matchar den versions sträng du behöver.</span><span class="sxs-lookup"><span data-stu-id="26809-159">When using the `RequiredVersion` key, ensure your version string exactly matches the version string you require.</span></span>

```powershell
Get-Module AzureRM.Netcore -ListAvailable
```

```Output
    Directory: /home/azureuser/.local/share/powershell/Modules

ModuleType Version Name            PSEdition ExportedCommands
---------- ------- ----            --------- ----------------
Script     0.12.0  AzureRM.Netcore Core
```

<span data-ttu-id="26809-160">Följande exempel Miss lyckas eftersom **0,12** inte exakt matchar **0.12.0**.</span><span class="sxs-lookup"><span data-stu-id="26809-160">The following example fails because **0.12** doesn't exactly match **0.12.0**.</span></span>

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; RequiredVersion="0.12" }
```

#### <a name="-psedition-psedition-name"></a><span data-ttu-id="26809-161">– PSEdition \<PSEdition-Name\></span><span class="sxs-lookup"><span data-stu-id="26809-161">-PSEdition \<PSEdition-Name\></span></span>

<span data-ttu-id="26809-162">Anger en PowerShell-utgåva som skriptet kräver.</span><span class="sxs-lookup"><span data-stu-id="26809-162">Specifies a PowerShell edition that the script requires.</span></span> <span data-ttu-id="26809-163">Giltiga värden är **Core** för PowerShell-kärnan och **Desktop** för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="26809-163">Valid values are **Core** for PowerShell Core and **Desktop** for Windows PowerShell.</span></span>

<span data-ttu-id="26809-164">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="26809-164">For example:</span></span>

```powershell
#Requires -PSEdition Core
```

#### <a name="-shellid"></a><span data-ttu-id="26809-165">-ShellId</span><span class="sxs-lookup"><span data-stu-id="26809-165">-ShellId</span></span>

<span data-ttu-id="26809-166">Anger det gränssnitt som skriptet kräver.</span><span class="sxs-lookup"><span data-stu-id="26809-166">Specifies the shell that the script requires.</span></span> <span data-ttu-id="26809-167">Ange gränssnitts-ID: t.</span><span class="sxs-lookup"><span data-stu-id="26809-167">Enter the shell ID.</span></span> <span data-ttu-id="26809-168">Om du använder parametern **ShellId** måste du också ta med parametern **PSSnapin** .</span><span class="sxs-lookup"><span data-stu-id="26809-168">If you use the **ShellId** parameter, you must also include the **PSSnapin** parameter.</span></span>
<span data-ttu-id="26809-169">Du kan hitta den aktuella **ShellId** genom att fråga den `$ShellId` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="26809-169">You can find the current **ShellId** by querying the `$ShellId` automatic variable.</span></span>

<span data-ttu-id="26809-170">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="26809-170">For example:</span></span>

```powershell
#Requires -ShellId MyLocalShell -PSSnapin Microsoft.PowerShell.Core
```

> [!NOTE]
> <span data-ttu-id="26809-171">Den här parametern är avsedd för användning i mini-Shells, som är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="26809-171">This parameter is intended for use in mini-shells, which have been deprecated.</span></span>

#### <a name="-runasadministrator"></a><span data-ttu-id="26809-172">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="26809-172">-RunAsAdministrator</span></span>

<span data-ttu-id="26809-173">När den här växel parametern läggs till i din `#Requires` instruktion, anger den att den PowerShell-session där du kör skriptet måste startas med utökade användar rättigheter.</span><span class="sxs-lookup"><span data-stu-id="26809-173">When this switch parameter is added to your `#Requires` statement, it specifies that the PowerShell session in which you're running the script must be started with elevated user rights.</span></span> <span data-ttu-id="26809-174">Parametern **RunAsAdministrator** ignoreras på ett operativ system som inte är från Windows.</span><span class="sxs-lookup"><span data-stu-id="26809-174">The **RunAsAdministrator** parameter is ignored on a non-Windows operating system.</span></span> <span data-ttu-id="26809-175">**RunAsAdministrator** -parametern introducerades i PowerShell 4,0.</span><span class="sxs-lookup"><span data-stu-id="26809-175">The **RunAsAdministrator** parameter was introduced in PowerShell 4.0.</span></span>

<span data-ttu-id="26809-176">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="26809-176">For example:</span></span>

```powershell
#Requires -RunAsAdministrator
```

### <a name="examples"></a><span data-ttu-id="26809-177">Exempel</span><span class="sxs-lookup"><span data-stu-id="26809-177">Examples</span></span>

<span data-ttu-id="26809-178">Följande skript har två `#Requires` instruktioner.</span><span class="sxs-lookup"><span data-stu-id="26809-178">The following script has two `#Requires` statements.</span></span> <span data-ttu-id="26809-179">Om kraven som anges i båda uttrycken inte uppfylls, körs inte skriptet.</span><span class="sxs-lookup"><span data-stu-id="26809-179">If the requirements specified in both statements aren't met, the script doesn't run.</span></span> <span data-ttu-id="26809-180">Varje `#Requires` instruktion måste vara det första objektet på en rad:</span><span class="sxs-lookup"><span data-stu-id="26809-180">Each `#Requires` statement must be the first item on a line:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="26809-181">Se även</span><span class="sxs-lookup"><span data-stu-id="26809-181">See also</span></span>

[<span data-ttu-id="26809-182">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="26809-182">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="26809-183">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="26809-183">about_Language_Keywords</span></span>](about_Language_Keywords.md)
