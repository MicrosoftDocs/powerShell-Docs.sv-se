---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 08/03/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/install-module?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Module
ms.openlocfilehash: ec9862e9003bd73e952422a8d15d373193a80c12
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889784"
---
# <span data-ttu-id="82dd1-103">Install-Module</span><span class="sxs-lookup"><span data-stu-id="82dd1-103">Install-Module</span></span>

## <span data-ttu-id="82dd1-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="82dd1-104">SYNOPSIS</span></span>
<span data-ttu-id="82dd1-105">Laddar ned en eller flera moduler från en lagrings plats och installerar dem på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="82dd1-105">Downloads one or more modules from a repository, and installs them on the local computer.</span></span>

## <span data-ttu-id="82dd1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="82dd1-106">SYNTAX</span></span>

### <span data-ttu-id="82dd1-107">NameParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="82dd1-107">NameParameterSet (Default)</span></span>

```
Install-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Credential <PSCredential>] [-Scope <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllowClobber] [-SkipPublisherCheck] [-Force]
 [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="82dd1-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="82dd1-108">InputObject</span></span>

```
Install-Module [-InputObject] <PSObject[]> [-Credential <PSCredential>] [-Scope <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllowClobber] [-SkipPublisherCheck] [-Force]
 [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="82dd1-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="82dd1-109">DESCRIPTION</span></span>

<span data-ttu-id="82dd1-110">`Install-Module`Cmdlet: en hämtar en eller flera moduler som uppfyller de angivna kriterierna från en online-lagringsplats.</span><span class="sxs-lookup"><span data-stu-id="82dd1-110">The `Install-Module` cmdlet gets one or more modules that meet specified criteria from an online repository.</span></span> <span data-ttu-id="82dd1-111">Cmdleten verifierar att Sök resultaten är giltiga moduler och kopierar modulens mappar till installations platsen.</span><span class="sxs-lookup"><span data-stu-id="82dd1-111">The cmdlet verifies that search results are valid modules and copies the module folders to the installation location.</span></span> <span data-ttu-id="82dd1-112">Installerade moduler importeras inte automatiskt efter installationen.</span><span class="sxs-lookup"><span data-stu-id="82dd1-112">Installed modules are not automatically imported after installation.</span></span>
<span data-ttu-id="82dd1-113">Du kan filtrera vilken modul som installeras baserat på de lägsta, högsta och exakta versionerna av de angivna modulerna.</span><span class="sxs-lookup"><span data-stu-id="82dd1-113">You can filter which module is installed based on the minimum, maximum, and exact versions of specified modules.</span></span>

<span data-ttu-id="82dd1-114">Om modulen som installeras har samma namn eller version, eller innehåller kommandon i en befintlig modul, visas varnings meddelanden.</span><span class="sxs-lookup"><span data-stu-id="82dd1-114">If the module being installed has the same name or version, or contains commands in an existing module, warning messages are displayed.</span></span> <span data-ttu-id="82dd1-115">När du har bekräftat att du vill installera modulen och åsidosätta varningarna använder du `-Force` parametrarna och `-AllowClobber` .</span><span class="sxs-lookup"><span data-stu-id="82dd1-115">After you confirm that you want to install the module and override the warnings, use the `-Force` and `-AllowClobber` parameters.</span></span> <span data-ttu-id="82dd1-116">Beroende på dina lagrings plats inställningar kan du behöva besvara en prompt för att modulen ska kunna fortsätta.</span><span class="sxs-lookup"><span data-stu-id="82dd1-116">Dependent upon your repository settings, you might need to answer a prompt for the module installation to continue.</span></span>

<span data-ttu-id="82dd1-117">I de här exemplen används [PowerShell-galleriet](https://www.powershellgallery.com/) som den enda registrerade lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="82dd1-117">These examples use the [PowerShell Gallery](https://www.powershellgallery.com/) as the only registered repository.</span></span> <span data-ttu-id="82dd1-118">`Get-PSRepository` visar de registrerade databaserna.</span><span class="sxs-lookup"><span data-stu-id="82dd1-118">`Get-PSRepository` displays the registered repositories.</span></span> <span data-ttu-id="82dd1-119">Om du har flera registrerade databaser använder du `-Repository` parametern för att ange namnet på lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="82dd1-119">If you have multiple registered repositories, use the `-Repository` parameter to specify the repository's name.</span></span>

## <span data-ttu-id="82dd1-120">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="82dd1-120">EXAMPLES</span></span>

### <span data-ttu-id="82dd1-121">Exempel 1: söka efter och installera en modul</span><span class="sxs-lookup"><span data-stu-id="82dd1-121">Example 1: Find and install a module</span></span>

<span data-ttu-id="82dd1-122">I det här exemplet hittar du en modul i lagrings platsen och installerar modulen.</span><span class="sxs-lookup"><span data-stu-id="82dd1-122">This example finds a module in the repository and installs the module.</span></span>

```powershell
Find-Module -Name PowerShellGet | Install-Module
```

<span data-ttu-id="82dd1-123">`Find-Module`Använder parametern **Name** för att ange **PowerShellGet** -modulen.</span><span class="sxs-lookup"><span data-stu-id="82dd1-123">The `Find-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="82dd1-124">Den nyaste versionen av modulen laddas som standard ned från lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="82dd1-124">By default, the newest version of the module is downloaded from the repository.</span></span> <span data-ttu-id="82dd1-125">Objektet skickas ned pipelinen till `Install-Module` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="82dd1-125">The object is sent down the pipeline to the `Install-Module` cmdlet.</span></span> <span data-ttu-id="82dd1-126">`Install-Module` installerar modulen för alla användare i `$env:ProgramFiles\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="82dd1-126">`Install-Module` installs the module for all users in `$env:ProgramFiles\WindowsPowerShell\Modules`.</span></span>

### <span data-ttu-id="82dd1-127">Exempel 2: installera en modul efter namn</span><span class="sxs-lookup"><span data-stu-id="82dd1-127">Example 2: Install a module by name</span></span>

<span data-ttu-id="82dd1-128">I det här exemplet installeras den nyaste versionen av **PowerShellGet** -modulen.</span><span class="sxs-lookup"><span data-stu-id="82dd1-128">In this example, the newest version of the **PowerShellGet** module is installed.</span></span>

```powershell
Install-Module -Name PowerShellGet
```

<span data-ttu-id="82dd1-129">`Install-Module`Använder parametern **Name** för att ange **PowerShellGet** -modulen.</span><span class="sxs-lookup"><span data-stu-id="82dd1-129">The `Install-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="82dd1-130">Den nyaste versionen av modulen laddas som standard ned från lagrings platsen och installeras.</span><span class="sxs-lookup"><span data-stu-id="82dd1-130">By default, the newest version of the module is downloaded from the repository and installed.</span></span>

### <span data-ttu-id="82dd1-131">Exempel 3: installera en modul med dess lägsta version</span><span class="sxs-lookup"><span data-stu-id="82dd1-131">Example 3: Install a module using its minimum version</span></span>

<span data-ttu-id="82dd1-132">I det här exemplet installeras den lägsta versionen av **PowerShellGet** -modulen.</span><span class="sxs-lookup"><span data-stu-id="82dd1-132">In this example, the minimum version of the **PowerShellGet** module is installed.</span></span> <span data-ttu-id="82dd1-133">Parametern **MinimumVersion** anger den lägsta versionen av modulen som ska installeras.</span><span class="sxs-lookup"><span data-stu-id="82dd1-133">The **MinimumVersion** parameter specifies the lowest version of the module that should be installed.</span></span> <span data-ttu-id="82dd1-134">Om en nyare version av modulen är tillgänglig laddas den versionen ned och installeras för alla användare.</span><span class="sxs-lookup"><span data-stu-id="82dd1-134">If a newer version of the module is available, that version is downloaded and installed for all users.</span></span>

```powershell
Install-Module -Name PowerShellGet -MinimumVersion 2.0.1
```

<span data-ttu-id="82dd1-135">`Install-Module`Använder parametern **Name** för att ange **PowerShellGet** -modulen.</span><span class="sxs-lookup"><span data-stu-id="82dd1-135">The `Install-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="82dd1-136">Parametern **MinimumVersion** anger att version **2.0.1** hämtas från lagrings platsen och installeras.</span><span class="sxs-lookup"><span data-stu-id="82dd1-136">The **MinimumVersion** parameter specifies that version **2.0.1** is downloaded from the repository and installed.</span></span> <span data-ttu-id="82dd1-137">Eftersom version **2.0.4** är tillgänglig laddas den versionen ned och installeras för alla användare.</span><span class="sxs-lookup"><span data-stu-id="82dd1-137">Because version **2.0.4** is available, that version is downloaded and installed for all users.</span></span>

### <span data-ttu-id="82dd1-138">Exempel 4: installera en angiven version av en modul</span><span class="sxs-lookup"><span data-stu-id="82dd1-138">Example 4: Install a specific version of a module</span></span>

<span data-ttu-id="82dd1-139">I det här exemplet installeras en angiven version av **PowerShellGet** -modulen.</span><span class="sxs-lookup"><span data-stu-id="82dd1-139">In this example, a specific version of the **PowerShellGet** module is installed.</span></span>

```powershell
Install-Module -Name PowerShellGet -RequiredVersion 2.0.0
```

<span data-ttu-id="82dd1-140">`Install-Module`Använder parametern **Name** för att ange **PowerShellGet** -modulen.</span><span class="sxs-lookup"><span data-stu-id="82dd1-140">The `Install-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="82dd1-141">Parametern **RequiredVersion** anger att version **2.0.0** har laddats ned och installerats för alla användare.</span><span class="sxs-lookup"><span data-stu-id="82dd1-141">The **RequiredVersion** parameter specifies that version **2.0.0** is downloaded and installed for all users.</span></span>

### <span data-ttu-id="82dd1-142">Exempel 5: installera bara en modul för den aktuella användaren</span><span class="sxs-lookup"><span data-stu-id="82dd1-142">Example 5: Install a module only for the current user</span></span>

<span data-ttu-id="82dd1-143">I det här exemplet hämtas och installeras den senaste versionen av en modul, bara för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="82dd1-143">This example downloads and installs the newest version of a module, only for the current user.</span></span>

```powershell
Install-Module -Name PowerShellGet -Scope CurrentUser
```

<span data-ttu-id="82dd1-144">`Install-Module`Använder parametern **Name** för att ange **PowerShellGet** -modulen.</span><span class="sxs-lookup"><span data-stu-id="82dd1-144">The `Install-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span>
<span data-ttu-id="82dd1-145">`Install-Module` laddar ned och installerar den senaste versionen av **PowerShellGet** i den aktuella användarens katalog `$home\Documents\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="82dd1-145">`Install-Module` downloads and installs the newest version of **PowerShellGet** into the current user's directory, `$home\Documents\WindowsPowerShell\Modules`.</span></span>

## <span data-ttu-id="82dd1-146">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="82dd1-146">PARAMETERS</span></span>

### <span data-ttu-id="82dd1-147">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="82dd1-147">-AcceptLicense</span></span>

<span data-ttu-id="82dd1-148">För moduler som kräver en licens accepterar **AcceptLicense** automatiskt licens avtalet under installationen.</span><span class="sxs-lookup"><span data-stu-id="82dd1-148">For modules that require a license, **AcceptLicense** automatically accepts the license agreement during installation.</span></span> <span data-ttu-id="82dd1-149">Mer information finns i [moduler som kräver licens godkännande](/powershell/scripting/gallery/concepts/module-license-acceptance).</span><span class="sxs-lookup"><span data-stu-id="82dd1-149">For more information, see [Modules Requiring License Acceptance](/powershell/scripting/gallery/concepts/module-license-acceptance).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="82dd1-150">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="82dd1-150">-AllowClobber</span></span>

<span data-ttu-id="82dd1-151">Åsidosätter varnings meddelanden om installations konflikter för befintliga kommandon på en dator.</span><span class="sxs-lookup"><span data-stu-id="82dd1-151">Overrides warning messages about installation conflicts about existing commands on a computer.</span></span>
<span data-ttu-id="82dd1-152">Skriver över befintliga kommandon som har samma namn som kommandon som installeras av en modul.</span><span class="sxs-lookup"><span data-stu-id="82dd1-152">Overwrites existing commands that have the same name as commands being installed by a module.</span></span>
<span data-ttu-id="82dd1-153">**AllowClobber** och **Force** kan användas tillsammans i ett `Install-Module` kommando.</span><span class="sxs-lookup"><span data-stu-id="82dd1-153">**AllowClobber** and **Force** can be used together in an `Install-Module` command.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="82dd1-154">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="82dd1-154">-AllowPrerelease</span></span>

<span data-ttu-id="82dd1-155">Gör att du kan installera en modul som är markerad som en för hands version.</span><span class="sxs-lookup"><span data-stu-id="82dd1-155">Allows you to install a module marked as a pre-release.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="82dd1-156">-Confirm</span><span class="sxs-lookup"><span data-stu-id="82dd1-156">-Confirm</span></span>

<span data-ttu-id="82dd1-157">Du uppmanas att bekräfta innan du kör `Install-Module` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="82dd1-157">Prompts you for confirmation before running the `Install-Module` cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="82dd1-158">-Credential</span><span class="sxs-lookup"><span data-stu-id="82dd1-158">-Credential</span></span>

<span data-ttu-id="82dd1-159">Anger ett användar konto som har behörighet att installera en modul för en angiven paket leverantör eller källa.</span><span class="sxs-lookup"><span data-stu-id="82dd1-159">Specifies a user account that has rights to install a module for a specified package provider or source.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="82dd1-160">-Force</span><span class="sxs-lookup"><span data-stu-id="82dd1-160">-Force</span></span>

<span data-ttu-id="82dd1-161">Installerar en modul och åsidosätter varnings meddelanden om installations konflikter i modulen.</span><span class="sxs-lookup"><span data-stu-id="82dd1-161">Installs a module and overrides warning messages about module installation conflicts.</span></span> <span data-ttu-id="82dd1-162">Om det redan finns en modul med samma namn på datorn, tillåter **Force** att flera versioner är installerade.</span><span class="sxs-lookup"><span data-stu-id="82dd1-162">If a module with the same name already exists on the computer, **Force** allows for multiple versions to be installed.</span></span> <span data-ttu-id="82dd1-163">Om det finns en befintlig modul med samma namn och version, kommer **Framtvinga** att skriva över den versionen.</span><span class="sxs-lookup"><span data-stu-id="82dd1-163">If there is an existing module with the same name and version, **Force** overwrites that version.</span></span> <span data-ttu-id="82dd1-164">**Force** och **AllowClobber** kan användas tillsammans i ett `Install-Module` kommando.</span><span class="sxs-lookup"><span data-stu-id="82dd1-164">**Force** and **AllowClobber** can be used together in an `Install-Module` command.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="82dd1-165">– InputObject</span><span class="sxs-lookup"><span data-stu-id="82dd1-165">-InputObject</span></span>

<span data-ttu-id="82dd1-166">Används för pipeline-ininformation.</span><span class="sxs-lookup"><span data-stu-id="82dd1-166">Used for pipeline input.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="82dd1-167">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="82dd1-167">-MaximumVersion</span></span>

<span data-ttu-id="82dd1-168">Anger den maximala version av en enskild modul som ska installeras.</span><span class="sxs-lookup"><span data-stu-id="82dd1-168">Specifies the maximum version of a single module to install.</span></span> <span data-ttu-id="82dd1-169">Den installerade versionen måste vara mindre än eller lika med **MaximumVersion**.</span><span class="sxs-lookup"><span data-stu-id="82dd1-169">The version installed must be less than or equal to **MaximumVersion**.</span></span> <span data-ttu-id="82dd1-170">Om du vill installera flera moduler kan du inte använda **MaximumVersion**.</span><span class="sxs-lookup"><span data-stu-id="82dd1-170">If you want to install multiple modules, you cannot use **MaximumVersion**.</span></span> <span data-ttu-id="82dd1-171">Det går inte att använda **MaximumVersion** och **RequiredVersion** i samma `Install-Module` kommando.</span><span class="sxs-lookup"><span data-stu-id="82dd1-171">**MaximumVersion** and **RequiredVersion** cannot be used in the same `Install-Module` command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="82dd1-172">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="82dd1-172">-MinimumVersion</span></span>

<span data-ttu-id="82dd1-173">Anger den lägsta version av en enskild modul som ska installeras.</span><span class="sxs-lookup"><span data-stu-id="82dd1-173">Specifies the minimum version of a single module to install.</span></span> <span data-ttu-id="82dd1-174">Den installerade versionen måste vara större än eller lika med **MinimumVersion**.</span><span class="sxs-lookup"><span data-stu-id="82dd1-174">The version installed must be greater than or equal to **MinimumVersion**.</span></span> <span data-ttu-id="82dd1-175">Om det finns en nyare version av modulen som är tillgänglig installeras den nyare versionen.</span><span class="sxs-lookup"><span data-stu-id="82dd1-175">If there is a newer version of the module available, the newer version is installed.</span></span> <span data-ttu-id="82dd1-176">Om du vill installera flera moduler kan du inte använda **MinimumVersion**.</span><span class="sxs-lookup"><span data-stu-id="82dd1-176">If you want to install multiple modules, you cannot use **MinimumVersion**.</span></span>
<span data-ttu-id="82dd1-177">Det går inte att använda **MinimumVersion** och **RequiredVersion** i samma `Install-Module` kommando.</span><span class="sxs-lookup"><span data-stu-id="82dd1-177">**MinimumVersion** and **RequiredVersion** cannot be used in the same `Install-Module` command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="82dd1-178">-Name</span><span class="sxs-lookup"><span data-stu-id="82dd1-178">-Name</span></span>

<span data-ttu-id="82dd1-179">Anger de exakta namnen på de moduler som ska installeras från onlinegalleri.</span><span class="sxs-lookup"><span data-stu-id="82dd1-179">Specifies the exact names of modules to install from the online gallery.</span></span> <span data-ttu-id="82dd1-180">En kommaavgränsad lista med Modulnamn accepteras.</span><span class="sxs-lookup"><span data-stu-id="82dd1-180">A comma-separated list of module names is accepted.</span></span> <span data-ttu-id="82dd1-181">Modulnamnet måste matcha modulens namn i lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="82dd1-181">The module name must match the module name in the repository.</span></span> <span data-ttu-id="82dd1-182">Används `Find-Module` för att hämta en lista över modulnamn.</span><span class="sxs-lookup"><span data-stu-id="82dd1-182">Use `Find-Module` to get a list of module names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="82dd1-183">– PassThru</span><span class="sxs-lookup"><span data-stu-id="82dd1-183">-PassThru</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="82dd1-184">-Proxy</span><span class="sxs-lookup"><span data-stu-id="82dd1-184">-Proxy</span></span>

<span data-ttu-id="82dd1-185">Anger en proxyserver för begäran, i stället för att ansluta direkt till Internet resursen.</span><span class="sxs-lookup"><span data-stu-id="82dd1-185">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="82dd1-186">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="82dd1-186">-ProxyCredential</span></span>

<span data-ttu-id="82dd1-187">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="82dd1-187">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="82dd1-188">– Databas</span><span class="sxs-lookup"><span data-stu-id="82dd1-188">-Repository</span></span>

<span data-ttu-id="82dd1-189">Använd parametern **lagrings plats** för att ange vilken databas som används för att ladda ned och installera en modul.</span><span class="sxs-lookup"><span data-stu-id="82dd1-189">Use the **Repository** parameter to specify which repository is used to download and install a module.</span></span> <span data-ttu-id="82dd1-190">Används när flera databaser har registrerats.</span><span class="sxs-lookup"><span data-stu-id="82dd1-190">Used when multiple repositories are registered.</span></span> <span data-ttu-id="82dd1-191">Anger namnet på en registrerad databas i `Install-Module` kommandot.</span><span class="sxs-lookup"><span data-stu-id="82dd1-191">Specifies the name of a registered repository in the `Install-Module` command.</span></span> <span data-ttu-id="82dd1-192">Använd om du vill registrera en lagrings plats `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="82dd1-192">To register a repository, use `Register-PSRepository`.</span></span>
<span data-ttu-id="82dd1-193">Använd om du vill visa registrerade databaser `Get-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="82dd1-193">To display registered repositories, use `Get-PSRepository`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="82dd1-194">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="82dd1-194">-RequiredVersion</span></span>

<span data-ttu-id="82dd1-195">Anger den exakta versionen av en enda modul som ska installeras.</span><span class="sxs-lookup"><span data-stu-id="82dd1-195">Specifies the exact version of a single module to install.</span></span> <span data-ttu-id="82dd1-196">Om det inte finns någon matchning i lagrings platsen för den angivna versionen visas ett fel.</span><span class="sxs-lookup"><span data-stu-id="82dd1-196">If there is no match in the repository for the specified version, an error is displayed.</span></span> <span data-ttu-id="82dd1-197">Om du vill installera flera moduler kan du inte använda **RequiredVersion**.</span><span class="sxs-lookup"><span data-stu-id="82dd1-197">If you want to install multiple modules, you cannot use **RequiredVersion**.</span></span> <span data-ttu-id="82dd1-198">**RequiredVersion** kan inte användas i samma `Install-Module` kommando som **MinimumVersion** eller **MaximumVersion**.</span><span class="sxs-lookup"><span data-stu-id="82dd1-198">**RequiredVersion** cannot be used in the same `Install-Module` command as **MinimumVersion** or **MaximumVersion**.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="82dd1-199">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="82dd1-199">-Scope</span></span>

<span data-ttu-id="82dd1-200">Anger modulens installations omfång.</span><span class="sxs-lookup"><span data-stu-id="82dd1-200">Specifies the installation scope of the module.</span></span> <span data-ttu-id="82dd1-201">De acceptabla värdena för den här parametern är **allusers** och **CurrentUser**.</span><span class="sxs-lookup"><span data-stu-id="82dd1-201">The acceptable values for this parameter are **AllUsers** and **CurrentUser**.</span></span>

<span data-ttu-id="82dd1-202">**Allusers** scope installerar moduler på en plats som är tillgänglig för alla användare av datorn:</span><span class="sxs-lookup"><span data-stu-id="82dd1-202">The **AllUsers** scope installs modules in a location that is accessible to all users of the computer:</span></span>

`$env:ProgramFiles\WindowsPowerShell\Modules`

<span data-ttu-id="82dd1-203">**CurrentUser** installerar moduler på en plats som endast är tillgänglig för den aktuella användaren av datorn.</span><span class="sxs-lookup"><span data-stu-id="82dd1-203">The **CurrentUser** installs modules in a location that is accessible only to the current user of the computer.</span></span> <span data-ttu-id="82dd1-204">Exempel:</span><span class="sxs-lookup"><span data-stu-id="82dd1-204">For example:</span></span>

`$home\Documents\WindowsPowerShell\Modules`

<span data-ttu-id="82dd1-205">När inget **omfång** har definierats anges standardvärdet baserat på PowerShellGet-versionen.</span><span class="sxs-lookup"><span data-stu-id="82dd1-205">When no **Scope** is defined, the default is set based on the PowerShellGet version.</span></span>

- <span data-ttu-id="82dd1-206">I PowerShellGet-versioner 2.0.0 och senare är standardvärdet **CurrentUser**, vilket inte kräver höjning för installation.</span><span class="sxs-lookup"><span data-stu-id="82dd1-206">In PowerShellGet versions 2.0.0 and above, the default is **CurrentUser**, which does not require elevation for install.</span></span>
- <span data-ttu-id="82dd1-207">I PowerShellGet 1. x-versioner är standardvärdet **allusers**, vilket kräver höjning för installation.</span><span class="sxs-lookup"><span data-stu-id="82dd1-207">In PowerShellGet 1.x versions, the default is **AllUsers**, which requires elevation for install.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="82dd1-208">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="82dd1-208">-SkipPublisherCheck</span></span>

<span data-ttu-id="82dd1-209">Gör att du kan installera en nyare version av en modul som redan finns på datorn.</span><span class="sxs-lookup"><span data-stu-id="82dd1-209">Allows you to install a newer version of a module that already exists on your computer.</span></span> <span data-ttu-id="82dd1-210">Till exempel när en befintlig modul signeras digitalt av en betrodd utgivare men den nya versionen inte signeras digitalt av en betrodd utgivare.</span><span class="sxs-lookup"><span data-stu-id="82dd1-210">For example, when an existing module is digitally signed by a trusted publisher but the new version is not digitally signed by a trusted publisher.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="82dd1-211">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="82dd1-211">-WhatIf</span></span>

<span data-ttu-id="82dd1-212">Visar vad som händer om ett `Install-Module` kommando kördes.</span><span class="sxs-lookup"><span data-stu-id="82dd1-212">Shows what would happen if an `Install-Module` command was run.</span></span> <span data-ttu-id="82dd1-213">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="82dd1-213">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="82dd1-214">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="82dd1-214">CommonParameters</span></span>

<span data-ttu-id="82dd1-215">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="82dd1-215">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="82dd1-216">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="82dd1-216">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="82dd1-217">INDATA</span><span class="sxs-lookup"><span data-stu-id="82dd1-217">INPUTS</span></span>

### <span data-ttu-id="82dd1-218">PSRepositoryItemInfo</span><span class="sxs-lookup"><span data-stu-id="82dd1-218">PSRepositoryItemInfo</span></span>

<span data-ttu-id="82dd1-219">`Find-Module` skapar **PSRepositoryItemInfo** -objekt som kan skickas till pipelinen till `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="82dd1-219">`Find-Module` creates **PSRepositoryItemInfo** objects that can be sent down the pipeline to `Install-Module`.</span></span>

### <span data-ttu-id="82dd1-220">System.String[]</span><span class="sxs-lookup"><span data-stu-id="82dd1-220">System.String[]</span></span>

### <span data-ttu-id="82dd1-221">System. Management. Automation. PSObject []</span><span class="sxs-lookup"><span data-stu-id="82dd1-221">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="82dd1-222">System. String</span><span class="sxs-lookup"><span data-stu-id="82dd1-222">System.String</span></span>

### <span data-ttu-id="82dd1-223">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="82dd1-223">System.Management.Automation.PSCredential</span></span>

### <span data-ttu-id="82dd1-224">System. URI</span><span class="sxs-lookup"><span data-stu-id="82dd1-224">System.Uri</span></span>

## <span data-ttu-id="82dd1-225">UTDATA</span><span class="sxs-lookup"><span data-stu-id="82dd1-225">OUTPUTS</span></span>

### <span data-ttu-id="82dd1-226">Microsoft. PowerShell. commands. PSRepositoryItemInfo</span><span class="sxs-lookup"><span data-stu-id="82dd1-226">Microsoft.PowerShell.Commands.PSRepositoryItemInfo</span></span>

<span data-ttu-id="82dd1-227">När du använder parametern **Passthru** `Install-Module` matar ut ett **PSRepositoryItemInfo** -objekt för modulen.</span><span class="sxs-lookup"><span data-stu-id="82dd1-227">When using the **PassThru** parameter, `Install-Module` outputs a **PSRepositoryItemInfo** object for the module.</span></span> <span data-ttu-id="82dd1-228">Detta är samma information som du hämtar från `Find-Module` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="82dd1-228">This is the same information that you get from the `Find-Module` cmdlet.</span></span>

## <span data-ttu-id="82dd1-229">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="82dd1-229">NOTES</span></span>

<span data-ttu-id="82dd1-230">`Install-Module` körs på PowerShell 5,0 eller senare versioner, på Windows 7 eller Windows 2008 R2 och senare versioner av Windows.</span><span class="sxs-lookup"><span data-stu-id="82dd1-230">`Install-Module` runs on PowerShell 5.0 or later releases, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="82dd1-231">Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1.</span><span class="sxs-lookup"><span data-stu-id="82dd1-231">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="82dd1-232">Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="82dd1-232">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="82dd1-233">Använd följande kommando för att se till att du använder TLS 1,2:</span><span class="sxs-lookup"><span data-stu-id="82dd1-233">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="82dd1-234">Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="82dd1-234">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

<span data-ttu-id="82dd1-235">Som en säkerhets åtgärd bör du utvärdera modulens kod innan du kör några cmdlets eller Functions för första gången.</span><span class="sxs-lookup"><span data-stu-id="82dd1-235">As a security best practice, evaluate a module's code before running any cmdlets or functions for the first time.</span></span> <span data-ttu-id="82dd1-236">För att förhindra att moduler som innehåller skadlig kod körs, importeras inte installerade moduler automatiskt efter installationen.</span><span class="sxs-lookup"><span data-stu-id="82dd1-236">To prevent running modules that contain malicious code, installed modules are not automatically imported after installation.</span></span>

<span data-ttu-id="82dd1-237">Om det Modulnamn som anges av **namn** parametern inte finns i databasen `Install-Module` returneras ett fel.</span><span class="sxs-lookup"><span data-stu-id="82dd1-237">If the module name specified by the **Name** parameter does not exist in the repository, `Install-Module` returns an error.</span></span>

<span data-ttu-id="82dd1-238">Om du vill installera flera moduler använder du parametern **Name** och anger en kommaavgränsad matris med modulnamn.</span><span class="sxs-lookup"><span data-stu-id="82dd1-238">To install multiple modules, use the **Name** parameter and specify a comma-separated array of module names.</span></span> <span data-ttu-id="82dd1-239">Om du anger flera modulnamn kan du inte använda **MinimumVersion**, **MaximumVersion** eller **RequiredVersion**.</span><span class="sxs-lookup"><span data-stu-id="82dd1-239">If you specify multiple module names, you cannot use **MinimumVersion**, **MaximumVersion**, or **RequiredVersion**.</span></span> <span data-ttu-id="82dd1-240">`Find-Module` skapar **PSRepositoryItemInfo** -objekt som kan skickas till pipelinen till `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="82dd1-240">`Find-Module` creates **PSRepositoryItemInfo** objects that can be sent down the pipeline to `Install-Module`.</span></span> <span data-ttu-id="82dd1-241">Pipelinen är ett annat sätt att ange flera moduler som ska installeras i ett enda kommando.</span><span class="sxs-lookup"><span data-stu-id="82dd1-241">The pipeline is another way to specify multiple modules to install in a single command.</span></span>

<span data-ttu-id="82dd1-242">Som standard installeras moduler för omfånget för **allusers** i `$env:ProgramFiles\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="82dd1-242">By default, modules for the scope of **AllUsers** are installed in `$env:ProgramFiles\WindowsPowerShell\Modules`.</span></span> <span data-ttu-id="82dd1-243">Standard förhindrar förvirring när du installerar PowerShell-resurser för Desired State Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="82dd1-243">The default prevents confusion when you install PowerShell Desired State Configuration (DSC) resources.</span></span>

<span data-ttu-id="82dd1-244">En modul installeras inte och kan inte importeras om den inte har något `.psm1` , `.psd1` eller `.dll` av samma namn i mappen.</span><span class="sxs-lookup"><span data-stu-id="82dd1-244">A module installation fails and cannot be imported if it does not have a `.psm1`, `.psd1`, or `.dll` of the same name within the folder.</span></span> <span data-ttu-id="82dd1-245">Använd parametern **Force** för att installera modulen.</span><span class="sxs-lookup"><span data-stu-id="82dd1-245">Use the **Force** parameter to install the module.</span></span>

<span data-ttu-id="82dd1-246">Om en befintlig moduls version matchar namnet som anges av parametern **Name** , och parametern **MinimumVersion** eller **RequiredVersion** inte används, `Install-Module` fortsätter tyst men installerar inte modulen.</span><span class="sxs-lookup"><span data-stu-id="82dd1-246">If an existing module's version matches the name specified by the **Name** parameter, and the **MinimumVersion** or **RequiredVersion** parameter are not used, `Install-Module` silently continues but does not install the module.</span></span>

<span data-ttu-id="82dd1-247">Om en befintlig moduls version är större än värdet för parametern **MinimumVersion** , eller är lika med värdet för parametern **RequiredVersion** , `Install-Module` fortsätter obevakat, men modulen installeras inte.</span><span class="sxs-lookup"><span data-stu-id="82dd1-247">If an existing module's version is greater than the value of the **MinimumVersion** parameter, or equal to the value of the **RequiredVersion** parameter, `Install-Module` silently continues but does not install the module.</span></span>

<span data-ttu-id="82dd1-248">Om den befintliga modulen inte matchar värdena som anges i parametrarna **MinimumVersion** eller **RequiredVersion** inträffar ett fel i `Install-Module` kommandot.</span><span class="sxs-lookup"><span data-stu-id="82dd1-248">If the existing module does not match the values specified by the **MinimumVersion** or **RequiredVersion** parameters, an error occurs in the `Install-Module` command.</span></span> <span data-ttu-id="82dd1-249">Till exempel, om versionen för den befintliga installerade modulen är lägre än **MinimumVersion** -värdet eller inte lika med **RequiredVersion** -värdet.</span><span class="sxs-lookup"><span data-stu-id="82dd1-249">For example, if the version of the existing installed module is lower than the **MinimumVersion** value or not equal to the **RequiredVersion** value.</span></span>

<span data-ttu-id="82dd1-250">Vid en installation av en modul installeras även eventuella beroende moduler som anges i modulen utgivare.</span><span class="sxs-lookup"><span data-stu-id="82dd1-250">A module installation will also install any dependent modules specified as required by the module publisher.</span></span>
<span data-ttu-id="82dd1-251">Utgivaren anger de moduler och versioner som krävs i manifestet för modulen.</span><span class="sxs-lookup"><span data-stu-id="82dd1-251">The publisher will specify the required modules and their versions in the module manifest.</span></span>

## <span data-ttu-id="82dd1-252">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="82dd1-252">RELATED LINKS</span></span>

[<span data-ttu-id="82dd1-253">Sök-modul</span><span class="sxs-lookup"><span data-stu-id="82dd1-253">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="82dd1-254">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="82dd1-254">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="82dd1-255">Importera-modul</span><span class="sxs-lookup"><span data-stu-id="82dd1-255">Import-Module</span></span>](../Microsoft.PowerShell.Core/Import-Module.md)

[<span data-ttu-id="82dd1-256">Publicera-modul</span><span class="sxs-lookup"><span data-stu-id="82dd1-256">Publish-Module</span></span>](Publish-Module.md)

[<span data-ttu-id="82dd1-257">Registrera – PSRepository</span><span class="sxs-lookup"><span data-stu-id="82dd1-257">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="82dd1-258">Avinstallera-modul</span><span class="sxs-lookup"><span data-stu-id="82dd1-258">Uninstall-Module</span></span>](Uninstall-Module.md)

[<span data-ttu-id="82dd1-259">Update-modul</span><span class="sxs-lookup"><span data-stu-id="82dd1-259">Update-Module</span></span>](Update-Module.md)

[<span data-ttu-id="82dd1-260">about_Module</span><span class="sxs-lookup"><span data-stu-id="82dd1-260">about_Module</span></span>](../Microsoft.PowerShell.Core/About/about_Modules.md)
