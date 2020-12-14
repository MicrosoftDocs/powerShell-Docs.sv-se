---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 08/03/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/install-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Module
ms.openlocfilehash: f4fcf349c439baf4813c37af4bf56c26a46c7877
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889267"
---
# <span data-ttu-id="3307c-102">Install-Module</span><span class="sxs-lookup"><span data-stu-id="3307c-102">Install-Module</span></span>

## <span data-ttu-id="3307c-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="3307c-103">SYNOPSIS</span></span>
<span data-ttu-id="3307c-104">Laddar ned en eller flera moduler från en lagrings plats och installerar dem på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="3307c-104">Downloads one or more modules from a repository, and installs them on the local computer.</span></span>

## <span data-ttu-id="3307c-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3307c-105">SYNTAX</span></span>

### <span data-ttu-id="3307c-106">NameParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="3307c-106">NameParameterSet (Default)</span></span>

```
Install-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Credential <PSCredential>] [-Scope <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllowClobber] [-SkipPublisherCheck] [-Force]
 [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="3307c-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="3307c-107">InputObject</span></span>

```
Install-Module [-InputObject] <PSObject[]> [-Credential <PSCredential>] [-Scope <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllowClobber] [-SkipPublisherCheck] [-Force]
 [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="3307c-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="3307c-108">DESCRIPTION</span></span>

<span data-ttu-id="3307c-109">`Install-Module`Cmdlet: en hämtar en eller flera moduler som uppfyller de angivna kriterierna från en online-lagringsplats.</span><span class="sxs-lookup"><span data-stu-id="3307c-109">The `Install-Module` cmdlet gets one or more modules that meet specified criteria from an online repository.</span></span> <span data-ttu-id="3307c-110">Cmdleten verifierar att Sök resultaten är giltiga moduler och kopierar modulens mappar till installations platsen.</span><span class="sxs-lookup"><span data-stu-id="3307c-110">The cmdlet verifies that search results are valid modules and copies the module folders to the installation location.</span></span> <span data-ttu-id="3307c-111">Installerade moduler importeras inte automatiskt efter installationen.</span><span class="sxs-lookup"><span data-stu-id="3307c-111">Installed modules are not automatically imported after installation.</span></span>
<span data-ttu-id="3307c-112">Du kan filtrera vilken modul som installeras baserat på de lägsta, högsta och exakta versionerna av de angivna modulerna.</span><span class="sxs-lookup"><span data-stu-id="3307c-112">You can filter which module is installed based on the minimum, maximum, and exact versions of specified modules.</span></span>

<span data-ttu-id="3307c-113">Om modulen som installeras har samma namn eller version, eller innehåller kommandon i en befintlig modul, visas varnings meddelanden.</span><span class="sxs-lookup"><span data-stu-id="3307c-113">If the module being installed has the same name or version, or contains commands in an existing module, warning messages are displayed.</span></span> <span data-ttu-id="3307c-114">När du har bekräftat att du vill installera modulen och åsidosätta varningarna använder du `-Force` parametrarna och `-AllowClobber` .</span><span class="sxs-lookup"><span data-stu-id="3307c-114">After you confirm that you want to install the module and override the warnings, use the `-Force` and `-AllowClobber` parameters.</span></span> <span data-ttu-id="3307c-115">Beroende på dina lagrings plats inställningar kan du behöva besvara en prompt för att modulen ska kunna fortsätta.</span><span class="sxs-lookup"><span data-stu-id="3307c-115">Dependent upon your repository settings, you might need to answer a prompt for the module installation to continue.</span></span>

<span data-ttu-id="3307c-116">I de här exemplen används [PowerShell-galleriet](https://www.powershellgallery.com/) som den enda registrerade lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="3307c-116">These examples use the [PowerShell Gallery](https://www.powershellgallery.com/) as the only registered repository.</span></span> <span data-ttu-id="3307c-117">`Get-PSRepository` visar de registrerade databaserna.</span><span class="sxs-lookup"><span data-stu-id="3307c-117">`Get-PSRepository` displays the registered repositories.</span></span> <span data-ttu-id="3307c-118">Om du har flera registrerade databaser använder du `-Repository` parametern för att ange namnet på lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="3307c-118">If you have multiple registered repositories, use the `-Repository` parameter to specify the repository's name.</span></span>

## <span data-ttu-id="3307c-119">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="3307c-119">EXAMPLES</span></span>

### <span data-ttu-id="3307c-120">Exempel 1: söka efter och installera en modul</span><span class="sxs-lookup"><span data-stu-id="3307c-120">Example 1: Find and install a module</span></span>

<span data-ttu-id="3307c-121">I det här exemplet hittar du en modul i lagrings platsen och installerar modulen.</span><span class="sxs-lookup"><span data-stu-id="3307c-121">This example finds a module in the repository and installs the module.</span></span>

```powershell
Find-Module -Name PowerShellGet | Install-Module
```

<span data-ttu-id="3307c-122">`Find-Module`Använder parametern **Name** för att ange **PowerShellGet** -modulen.</span><span class="sxs-lookup"><span data-stu-id="3307c-122">The `Find-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="3307c-123">Den nyaste versionen av modulen laddas som standard ned från lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="3307c-123">By default, the newest version of the module is downloaded from the repository.</span></span> <span data-ttu-id="3307c-124">Objektet skickas ned pipelinen till `Install-Module` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="3307c-124">The object is sent down the pipeline to the `Install-Module` cmdlet.</span></span> <span data-ttu-id="3307c-125">`Install-Module` installerar modulen för alla användare i `$env:ProgramFiles\PowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="3307c-125">`Install-Module` installs the module for all users in `$env:ProgramFiles\PowerShell\Modules`.</span></span>

### <span data-ttu-id="3307c-126">Exempel 2: installera en modul efter namn</span><span class="sxs-lookup"><span data-stu-id="3307c-126">Example 2: Install a module by name</span></span>

<span data-ttu-id="3307c-127">I det här exemplet installeras den nyaste versionen av **PowerShellGet** -modulen.</span><span class="sxs-lookup"><span data-stu-id="3307c-127">In this example, the newest version of the **PowerShellGet** module is installed.</span></span>

```powershell
Install-Module -Name PowerShellGet
```

<span data-ttu-id="3307c-128">`Install-Module`Använder parametern **Name** för att ange **PowerShellGet** -modulen.</span><span class="sxs-lookup"><span data-stu-id="3307c-128">The `Install-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="3307c-129">Den nyaste versionen av modulen laddas som standard ned från lagrings platsen och installeras.</span><span class="sxs-lookup"><span data-stu-id="3307c-129">By default, the newest version of the module is downloaded from the repository and installed.</span></span>

### <span data-ttu-id="3307c-130">Exempel 3: installera en modul med dess lägsta version</span><span class="sxs-lookup"><span data-stu-id="3307c-130">Example 3: Install a module using its minimum version</span></span>

<span data-ttu-id="3307c-131">I det här exemplet installeras den lägsta versionen av **PowerShellGet** -modulen.</span><span class="sxs-lookup"><span data-stu-id="3307c-131">In this example, the minimum version of the **PowerShellGet** module is installed.</span></span> <span data-ttu-id="3307c-132">Parametern **MinimumVersion** anger den lägsta versionen av modulen som ska installeras.</span><span class="sxs-lookup"><span data-stu-id="3307c-132">The **MinimumVersion** parameter specifies the lowest version of the module that should be installed.</span></span> <span data-ttu-id="3307c-133">Om en nyare version av modulen är tillgänglig laddas den versionen ned och installeras för alla användare.</span><span class="sxs-lookup"><span data-stu-id="3307c-133">If a newer version of the module is available, that version is downloaded and installed for all users.</span></span>

```powershell
Install-Module -Name PowerShellGet -MinimumVersion 2.0.1
```

<span data-ttu-id="3307c-134">`Install-Module`Använder parametern **Name** för att ange **PowerShellGet** -modulen.</span><span class="sxs-lookup"><span data-stu-id="3307c-134">The `Install-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="3307c-135">Parametern **MinimumVersion** anger att version **2.0.1** hämtas från lagrings platsen och installeras.</span><span class="sxs-lookup"><span data-stu-id="3307c-135">The **MinimumVersion** parameter specifies that version **2.0.1** is downloaded from the repository and installed.</span></span> <span data-ttu-id="3307c-136">Eftersom version **2.0.4** är tillgänglig laddas den versionen ned och installeras för alla användare.</span><span class="sxs-lookup"><span data-stu-id="3307c-136">Because version **2.0.4** is available, that version is downloaded and installed for all users.</span></span>

### <span data-ttu-id="3307c-137">Exempel 4: installera en angiven version av en modul</span><span class="sxs-lookup"><span data-stu-id="3307c-137">Example 4: Install a specific version of a module</span></span>

<span data-ttu-id="3307c-138">I det här exemplet installeras en angiven version av **PowerShellGet** -modulen.</span><span class="sxs-lookup"><span data-stu-id="3307c-138">In this example, a specific version of the **PowerShellGet** module is installed.</span></span>

```powershell
Install-Module -Name PowerShellGet -RequiredVersion 2.0.0
```

<span data-ttu-id="3307c-139">`Install-Module`Använder parametern **Name** för att ange **PowerShellGet** -modulen.</span><span class="sxs-lookup"><span data-stu-id="3307c-139">The `Install-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="3307c-140">Parametern **RequiredVersion** anger att version **2.0.0** har laddats ned och installerats för alla användare.</span><span class="sxs-lookup"><span data-stu-id="3307c-140">The **RequiredVersion** parameter specifies that version **2.0.0** is downloaded and installed for all users.</span></span>

### <span data-ttu-id="3307c-141">Exempel 5: installera bara en modul för den aktuella användaren</span><span class="sxs-lookup"><span data-stu-id="3307c-141">Example 5: Install a module only for the current user</span></span>

<span data-ttu-id="3307c-142">I det här exemplet hämtas och installeras den senaste versionen av en modul, bara för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="3307c-142">This example downloads and installs the newest version of a module, only for the current user.</span></span>

```powershell
Install-Module -Name PowerShellGet -Scope CurrentUser
```

<span data-ttu-id="3307c-143">`Install-Module`Använder parametern **Name** för att ange **PowerShellGet** -modulen.</span><span class="sxs-lookup"><span data-stu-id="3307c-143">The `Install-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span>
<span data-ttu-id="3307c-144">`Install-Module` laddar ned och installerar den senaste versionen av **PowerShellGet** i den aktuella användarens katalog `$home\Documents\PowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="3307c-144">`Install-Module` downloads and installs the newest version of **PowerShellGet** into the current user's directory, `$home\Documents\PowerShell\Modules`.</span></span>

## <span data-ttu-id="3307c-145">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="3307c-145">PARAMETERS</span></span>

### <span data-ttu-id="3307c-146">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="3307c-146">-AcceptLicense</span></span>

<span data-ttu-id="3307c-147">För moduler som kräver en licens accepterar **AcceptLicense** automatiskt licens avtalet under installationen.</span><span class="sxs-lookup"><span data-stu-id="3307c-147">For modules that require a license, **AcceptLicense** automatically accepts the license agreement during installation.</span></span> <span data-ttu-id="3307c-148">Mer information finns i [moduler som kräver licens godkännande](/powershell/scripting/gallery/concepts/module-license-acceptance).</span><span class="sxs-lookup"><span data-stu-id="3307c-148">For more information, see [Modules Requiring License Acceptance](/powershell/scripting/gallery/concepts/module-license-acceptance).</span></span>

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

### <span data-ttu-id="3307c-149">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="3307c-149">-AllowClobber</span></span>

<span data-ttu-id="3307c-150">Åsidosätter varnings meddelanden om installations konflikter för befintliga kommandon på en dator.</span><span class="sxs-lookup"><span data-stu-id="3307c-150">Overrides warning messages about installation conflicts about existing commands on a computer.</span></span>
<span data-ttu-id="3307c-151">Skriver över befintliga kommandon som har samma namn som kommandon som installeras av en modul.</span><span class="sxs-lookup"><span data-stu-id="3307c-151">Overwrites existing commands that have the same name as commands being installed by a module.</span></span>
<span data-ttu-id="3307c-152">**AllowClobber** och **Force** kan användas tillsammans i ett `Install-Module` kommando.</span><span class="sxs-lookup"><span data-stu-id="3307c-152">**AllowClobber** and **Force** can be used together in an `Install-Module` command.</span></span>

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

### <span data-ttu-id="3307c-153">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="3307c-153">-AllowPrerelease</span></span>

<span data-ttu-id="3307c-154">Gör att du kan installera en modul som är markerad som en för hands version.</span><span class="sxs-lookup"><span data-stu-id="3307c-154">Allows you to install a module marked as a pre-release.</span></span>

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

### <span data-ttu-id="3307c-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="3307c-155">-Confirm</span></span>

<span data-ttu-id="3307c-156">Du uppmanas att bekräfta innan du kör `Install-Module` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="3307c-156">Prompts you for confirmation before running the `Install-Module` cmdlet.</span></span>

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

### <span data-ttu-id="3307c-157">-Credential</span><span class="sxs-lookup"><span data-stu-id="3307c-157">-Credential</span></span>

<span data-ttu-id="3307c-158">Anger ett användar konto som har behörighet att installera en modul för en angiven paket leverantör eller källa.</span><span class="sxs-lookup"><span data-stu-id="3307c-158">Specifies a user account that has rights to install a module for a specified package provider or source.</span></span>

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

### <span data-ttu-id="3307c-159">-Force</span><span class="sxs-lookup"><span data-stu-id="3307c-159">-Force</span></span>

<span data-ttu-id="3307c-160">Installerar en modul och åsidosätter varnings meddelanden om installations konflikter i modulen.</span><span class="sxs-lookup"><span data-stu-id="3307c-160">Installs a module and overrides warning messages about module installation conflicts.</span></span> <span data-ttu-id="3307c-161">Om det redan finns en modul med samma namn på datorn, tillåter **Force** att flera versioner är installerade.</span><span class="sxs-lookup"><span data-stu-id="3307c-161">If a module with the same name already exists on the computer, **Force** allows for multiple versions to be installed.</span></span> <span data-ttu-id="3307c-162">Om det finns en befintlig modul med samma namn och version, kommer **Framtvinga** att skriva över den versionen.</span><span class="sxs-lookup"><span data-stu-id="3307c-162">If there is an existing module with the same name and version, **Force** overwrites that version.</span></span> <span data-ttu-id="3307c-163">**Force** och **AllowClobber** kan användas tillsammans i ett `Install-Module` kommando.</span><span class="sxs-lookup"><span data-stu-id="3307c-163">**Force** and **AllowClobber** can be used together in an `Install-Module` command.</span></span>

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

### <span data-ttu-id="3307c-164">– InputObject</span><span class="sxs-lookup"><span data-stu-id="3307c-164">-InputObject</span></span>

<span data-ttu-id="3307c-165">Används för pipeline-ininformation.</span><span class="sxs-lookup"><span data-stu-id="3307c-165">Used for pipeline input.</span></span>

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

### <span data-ttu-id="3307c-166">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="3307c-166">-MaximumVersion</span></span>

<span data-ttu-id="3307c-167">Anger den maximala version av en enskild modul som ska installeras.</span><span class="sxs-lookup"><span data-stu-id="3307c-167">Specifies the maximum version of a single module to install.</span></span> <span data-ttu-id="3307c-168">Den installerade versionen måste vara mindre än eller lika med **MaximumVersion**.</span><span class="sxs-lookup"><span data-stu-id="3307c-168">The version installed must be less than or equal to **MaximumVersion**.</span></span> <span data-ttu-id="3307c-169">Om du vill installera flera moduler kan du inte använda **MaximumVersion**.</span><span class="sxs-lookup"><span data-stu-id="3307c-169">If you want to install multiple modules, you cannot use **MaximumVersion**.</span></span> <span data-ttu-id="3307c-170">Det går inte att använda **MaximumVersion** och **RequiredVersion** i samma `Install-Module` kommando.</span><span class="sxs-lookup"><span data-stu-id="3307c-170">**MaximumVersion** and **RequiredVersion** cannot be used in the same `Install-Module` command.</span></span>

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

### <span data-ttu-id="3307c-171">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="3307c-171">-MinimumVersion</span></span>

<span data-ttu-id="3307c-172">Anger den lägsta version av en enskild modul som ska installeras.</span><span class="sxs-lookup"><span data-stu-id="3307c-172">Specifies the minimum version of a single module to install.</span></span> <span data-ttu-id="3307c-173">Den installerade versionen måste vara större än eller lika med **MinimumVersion**.</span><span class="sxs-lookup"><span data-stu-id="3307c-173">The version installed must be greater than or equal to **MinimumVersion**.</span></span> <span data-ttu-id="3307c-174">Om det finns en nyare version av modulen som är tillgänglig installeras den nyare versionen.</span><span class="sxs-lookup"><span data-stu-id="3307c-174">If there is a newer version of the module available, the newer version is installed.</span></span> <span data-ttu-id="3307c-175">Om du vill installera flera moduler kan du inte använda **MinimumVersion**.</span><span class="sxs-lookup"><span data-stu-id="3307c-175">If you want to install multiple modules, you cannot use **MinimumVersion**.</span></span>
<span data-ttu-id="3307c-176">Det går inte att använda **MinimumVersion** och **RequiredVersion** i samma `Install-Module` kommando.</span><span class="sxs-lookup"><span data-stu-id="3307c-176">**MinimumVersion** and **RequiredVersion** cannot be used in the same `Install-Module` command.</span></span>

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

### <span data-ttu-id="3307c-177">-Name</span><span class="sxs-lookup"><span data-stu-id="3307c-177">-Name</span></span>

<span data-ttu-id="3307c-178">Anger de exakta namnen på de moduler som ska installeras från onlinegalleri.</span><span class="sxs-lookup"><span data-stu-id="3307c-178">Specifies the exact names of modules to install from the online gallery.</span></span> <span data-ttu-id="3307c-179">En kommaavgränsad lista med Modulnamn accepteras.</span><span class="sxs-lookup"><span data-stu-id="3307c-179">A comma-separated list of module names is accepted.</span></span> <span data-ttu-id="3307c-180">Modulnamnet måste matcha modulens namn i lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="3307c-180">The module name must match the module name in the repository.</span></span> <span data-ttu-id="3307c-181">Används `Find-Module` för att hämta en lista över modulnamn.</span><span class="sxs-lookup"><span data-stu-id="3307c-181">Use `Find-Module` to get a list of module names.</span></span>

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

### <span data-ttu-id="3307c-182">– PassThru</span><span class="sxs-lookup"><span data-stu-id="3307c-182">-PassThru</span></span>

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

### <span data-ttu-id="3307c-183">-Proxy</span><span class="sxs-lookup"><span data-stu-id="3307c-183">-Proxy</span></span>

<span data-ttu-id="3307c-184">Anger en proxyserver för begäran, i stället för att ansluta direkt till Internet resursen.</span><span class="sxs-lookup"><span data-stu-id="3307c-184">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="3307c-185">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="3307c-185">-ProxyCredential</span></span>

<span data-ttu-id="3307c-186">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="3307c-186">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="3307c-187">– Databas</span><span class="sxs-lookup"><span data-stu-id="3307c-187">-Repository</span></span>

<span data-ttu-id="3307c-188">Använd parametern **lagrings plats** för att ange vilken databas som används för att ladda ned och installera en modul.</span><span class="sxs-lookup"><span data-stu-id="3307c-188">Use the **Repository** parameter to specify which repository is used to download and install a module.</span></span> <span data-ttu-id="3307c-189">Används när flera databaser har registrerats.</span><span class="sxs-lookup"><span data-stu-id="3307c-189">Used when multiple repositories are registered.</span></span> <span data-ttu-id="3307c-190">Anger namnet på en registrerad databas i `Install-Module` kommandot.</span><span class="sxs-lookup"><span data-stu-id="3307c-190">Specifies the name of a registered repository in the `Install-Module` command.</span></span> <span data-ttu-id="3307c-191">Använd om du vill registrera en lagrings plats `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="3307c-191">To register a repository, use `Register-PSRepository`.</span></span>
<span data-ttu-id="3307c-192">Använd om du vill visa registrerade databaser `Get-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="3307c-192">To display registered repositories, use `Get-PSRepository`.</span></span>

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

### <span data-ttu-id="3307c-193">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="3307c-193">-RequiredVersion</span></span>

<span data-ttu-id="3307c-194">Anger den exakta versionen av en enda modul som ska installeras.</span><span class="sxs-lookup"><span data-stu-id="3307c-194">Specifies the exact version of a single module to install.</span></span> <span data-ttu-id="3307c-195">Om det inte finns någon matchning i lagrings platsen för den angivna versionen visas ett fel.</span><span class="sxs-lookup"><span data-stu-id="3307c-195">If there is no match in the repository for the specified version, an error is displayed.</span></span> <span data-ttu-id="3307c-196">Om du vill installera flera moduler kan du inte använda **RequiredVersion**.</span><span class="sxs-lookup"><span data-stu-id="3307c-196">If you want to install multiple modules, you cannot use **RequiredVersion**.</span></span> <span data-ttu-id="3307c-197">**RequiredVersion** kan inte användas i samma `Install-Module` kommando som **MinimumVersion** eller **MaximumVersion**.</span><span class="sxs-lookup"><span data-stu-id="3307c-197">**RequiredVersion** cannot be used in the same `Install-Module` command as **MinimumVersion** or **MaximumVersion**.</span></span>

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

### <span data-ttu-id="3307c-198">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="3307c-198">-Scope</span></span>

<span data-ttu-id="3307c-199">Anger modulens installations omfång.</span><span class="sxs-lookup"><span data-stu-id="3307c-199">Specifies the installation scope of the module.</span></span> <span data-ttu-id="3307c-200">De acceptabla värdena för den här parametern är **allusers** och **CurrentUser**.</span><span class="sxs-lookup"><span data-stu-id="3307c-200">The acceptable values for this parameter are **AllUsers** and **CurrentUser**.</span></span>

<span data-ttu-id="3307c-201">**Allusers** scope installerar moduler på en plats som är tillgänglig för alla användare av datorn:</span><span class="sxs-lookup"><span data-stu-id="3307c-201">The **AllUsers** scope installs modules in a location that is accessible to all users of the computer:</span></span>

`$env:ProgramFiles\PowerShell\Modules`

<span data-ttu-id="3307c-202">**CurrentUser** installerar moduler på en plats som endast är tillgänglig för den aktuella användaren av datorn.</span><span class="sxs-lookup"><span data-stu-id="3307c-202">The **CurrentUser** installs modules in a location that is accessible only to the current user of the computer.</span></span> <span data-ttu-id="3307c-203">Exempel:</span><span class="sxs-lookup"><span data-stu-id="3307c-203">For example:</span></span>

`$home\Documents\PowerShell\Modules`

<span data-ttu-id="3307c-204">När inget **omfång** har definierats anges standardvärdet baserat på PowerShellGet-versionen.</span><span class="sxs-lookup"><span data-stu-id="3307c-204">When no **Scope** is defined, the default is set based on the PowerShellGet version.</span></span>

- <span data-ttu-id="3307c-205">I PowerShellGet-versioner 2.0.0 och senare är standardvärdet **CurrentUser**, vilket inte kräver höjning för installation.</span><span class="sxs-lookup"><span data-stu-id="3307c-205">In PowerShellGet versions 2.0.0 and above, the default is **CurrentUser**, which does not require elevation for install.</span></span>
- <span data-ttu-id="3307c-206">I PowerShellGet 1. x-versioner är standardvärdet **allusers**, vilket kräver höjning för installation.</span><span class="sxs-lookup"><span data-stu-id="3307c-206">In PowerShellGet 1.x versions, the default is **AllUsers**, which requires elevation for install.</span></span>

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

### <span data-ttu-id="3307c-207">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="3307c-207">-SkipPublisherCheck</span></span>

<span data-ttu-id="3307c-208">Gör att du kan installera en nyare version av en modul som redan finns på datorn.</span><span class="sxs-lookup"><span data-stu-id="3307c-208">Allows you to install a newer version of a module that already exists on your computer.</span></span> <span data-ttu-id="3307c-209">Till exempel när en befintlig modul signeras digitalt av en betrodd utgivare men den nya versionen inte signeras digitalt av en betrodd utgivare.</span><span class="sxs-lookup"><span data-stu-id="3307c-209">For example, when an existing module is digitally signed by a trusted publisher but the new version is not digitally signed by a trusted publisher.</span></span>

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

### <span data-ttu-id="3307c-210">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="3307c-210">-WhatIf</span></span>

<span data-ttu-id="3307c-211">Visar vad som händer om ett `Install-Module` kommando kördes.</span><span class="sxs-lookup"><span data-stu-id="3307c-211">Shows what would happen if an `Install-Module` command was run.</span></span> <span data-ttu-id="3307c-212">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="3307c-212">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="3307c-213">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3307c-213">CommonParameters</span></span>

<span data-ttu-id="3307c-214">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3307c-214">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3307c-215">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="3307c-215">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3307c-216">INDATA</span><span class="sxs-lookup"><span data-stu-id="3307c-216">INPUTS</span></span>

### <span data-ttu-id="3307c-217">PSRepositoryItemInfo</span><span class="sxs-lookup"><span data-stu-id="3307c-217">PSRepositoryItemInfo</span></span>

<span data-ttu-id="3307c-218">`Find-Module` skapar **PSRepositoryItemInfo** -objekt som kan skickas till pipelinen till `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="3307c-218">`Find-Module` creates **PSRepositoryItemInfo** objects that can be sent down the pipeline to `Install-Module`.</span></span>

### <span data-ttu-id="3307c-219">System.String[]</span><span class="sxs-lookup"><span data-stu-id="3307c-219">System.String[]</span></span>

### <span data-ttu-id="3307c-220">System. Management. Automation. PSObject []</span><span class="sxs-lookup"><span data-stu-id="3307c-220">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="3307c-221">System. String</span><span class="sxs-lookup"><span data-stu-id="3307c-221">System.String</span></span>

### <span data-ttu-id="3307c-222">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="3307c-222">System.Management.Automation.PSCredential</span></span>

### <span data-ttu-id="3307c-223">System. URI</span><span class="sxs-lookup"><span data-stu-id="3307c-223">System.Uri</span></span>

## <span data-ttu-id="3307c-224">UTDATA</span><span class="sxs-lookup"><span data-stu-id="3307c-224">OUTPUTS</span></span>

### <span data-ttu-id="3307c-225">Microsoft. PowerShell. commands. PSRepositoryItemInfo</span><span class="sxs-lookup"><span data-stu-id="3307c-225">Microsoft.PowerShell.Commands.PSRepositoryItemInfo</span></span>

<span data-ttu-id="3307c-226">När du använder parametern **Passthru** `Install-Module` matar ut ett **PSRepositoryItemInfo** -objekt för modulen.</span><span class="sxs-lookup"><span data-stu-id="3307c-226">When using the **PassThru** parameter, `Install-Module` outputs a **PSRepositoryItemInfo** object for the module.</span></span> <span data-ttu-id="3307c-227">Detta är samma information som du hämtar från `Find-Module` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="3307c-227">This is the same information that you get from the `Find-Module` cmdlet.</span></span>

## <span data-ttu-id="3307c-228">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="3307c-228">NOTES</span></span>

<span data-ttu-id="3307c-229">`Install-Module` körs på PowerShell 5,0 eller senare versioner, på Windows 7 eller Windows 2008 R2 och senare versioner av Windows.</span><span class="sxs-lookup"><span data-stu-id="3307c-229">`Install-Module` runs on PowerShell 5.0 or later releases, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3307c-230">Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1.</span><span class="sxs-lookup"><span data-stu-id="3307c-230">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="3307c-231">Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="3307c-231">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="3307c-232">Använd följande kommando för att se till att du använder TLS 1,2:</span><span class="sxs-lookup"><span data-stu-id="3307c-232">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="3307c-233">Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="3307c-233">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

<span data-ttu-id="3307c-234">Som en säkerhets åtgärd bör du utvärdera modulens kod innan du kör några cmdlets eller Functions för första gången.</span><span class="sxs-lookup"><span data-stu-id="3307c-234">As a security best practice, evaluate a module's code before running any cmdlets or functions for the first time.</span></span> <span data-ttu-id="3307c-235">För att förhindra att moduler som innehåller skadlig kod körs, importeras inte installerade moduler automatiskt efter installationen.</span><span class="sxs-lookup"><span data-stu-id="3307c-235">To prevent running modules that contain malicious code, installed modules are not automatically imported after installation.</span></span>

<span data-ttu-id="3307c-236">Om det Modulnamn som anges av **namn** parametern inte finns i databasen `Install-Module` returneras ett fel.</span><span class="sxs-lookup"><span data-stu-id="3307c-236">If the module name specified by the **Name** parameter does not exist in the repository, `Install-Module` returns an error.</span></span>

<span data-ttu-id="3307c-237">Om du vill installera flera moduler använder du parametern **Name** och anger en kommaavgränsad matris med modulnamn.</span><span class="sxs-lookup"><span data-stu-id="3307c-237">To install multiple modules, use the **Name** parameter and specify a comma-separated array of module names.</span></span> <span data-ttu-id="3307c-238">Om du anger flera modulnamn kan du inte använda **MinimumVersion**, **MaximumVersion** eller **RequiredVersion**.</span><span class="sxs-lookup"><span data-stu-id="3307c-238">If you specify multiple module names, you cannot use **MinimumVersion**, **MaximumVersion**, or **RequiredVersion**.</span></span> <span data-ttu-id="3307c-239">`Find-Module` skapar **PSRepositoryItemInfo** -objekt som kan skickas till pipelinen till `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="3307c-239">`Find-Module` creates **PSRepositoryItemInfo** objects that can be sent down the pipeline to `Install-Module`.</span></span> <span data-ttu-id="3307c-240">Pipelinen är ett annat sätt att ange flera moduler som ska installeras i ett enda kommando.</span><span class="sxs-lookup"><span data-stu-id="3307c-240">The pipeline is another way to specify multiple modules to install in a single command.</span></span>

<span data-ttu-id="3307c-241">Som standard installeras moduler för omfånget för **allusers** i `$env:ProgramFiles\PowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="3307c-241">By default, modules for the scope of **AllUsers** are installed in `$env:ProgramFiles\PowerShell\Modules`.</span></span> <span data-ttu-id="3307c-242">Standard förhindrar förvirring när du installerar PowerShell-resurser för Desired State Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="3307c-242">The default prevents confusion when you install PowerShell Desired State Configuration (DSC) resources.</span></span>

<span data-ttu-id="3307c-243">En modul installeras inte och kan inte importeras om den inte har något `.psm1` , `.psd1` eller `.dll` av samma namn i mappen.</span><span class="sxs-lookup"><span data-stu-id="3307c-243">A module installation fails and cannot be imported if it does not have a `.psm1`, `.psd1`, or `.dll` of the same name within the folder.</span></span> <span data-ttu-id="3307c-244">Använd parametern **Force** för att installera modulen.</span><span class="sxs-lookup"><span data-stu-id="3307c-244">Use the **Force** parameter to install the module.</span></span>

<span data-ttu-id="3307c-245">Om en befintlig moduls version matchar namnet som anges av parametern **Name** , och parametern **MinimumVersion** eller **RequiredVersion** inte används, `Install-Module` fortsätter tyst men installerar inte modulen.</span><span class="sxs-lookup"><span data-stu-id="3307c-245">If an existing module's version matches the name specified by the **Name** parameter, and the **MinimumVersion** or **RequiredVersion** parameter are not used, `Install-Module` silently continues but does not install the module.</span></span>

<span data-ttu-id="3307c-246">Om en befintlig moduls version är större än värdet för parametern **MinimumVersion** , eller är lika med värdet för parametern **RequiredVersion** , `Install-Module` fortsätter obevakat, men modulen installeras inte.</span><span class="sxs-lookup"><span data-stu-id="3307c-246">If an existing module's version is greater than the value of the **MinimumVersion** parameter, or equal to the value of the **RequiredVersion** parameter, `Install-Module` silently continues but does not install the module.</span></span>

<span data-ttu-id="3307c-247">Om den befintliga modulen inte matchar värdena som anges i parametrarna **MinimumVersion** eller **RequiredVersion** inträffar ett fel i `Install-Module` kommandot.</span><span class="sxs-lookup"><span data-stu-id="3307c-247">If the existing module does not match the values specified by the **MinimumVersion** or **RequiredVersion** parameters, an error occurs in the `Install-Module` command.</span></span> <span data-ttu-id="3307c-248">Till exempel, om versionen för den befintliga installerade modulen är lägre än **MinimumVersion** -värdet eller inte lika med **RequiredVersion** -värdet.</span><span class="sxs-lookup"><span data-stu-id="3307c-248">For example, if the version of the existing installed module is lower than the **MinimumVersion** value or not equal to the **RequiredVersion** value.</span></span>

<span data-ttu-id="3307c-249">Vid en installation av en modul installeras även eventuella beroende moduler som anges i modulen utgivare.</span><span class="sxs-lookup"><span data-stu-id="3307c-249">A module installation will also install any dependent modules specified as required by the module publisher.</span></span>
<span data-ttu-id="3307c-250">Utgivaren anger de moduler och versioner som krävs i manifestet för modulen.</span><span class="sxs-lookup"><span data-stu-id="3307c-250">The publisher will specify the required modules and their versions in the module manifest.</span></span>

## <span data-ttu-id="3307c-251">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="3307c-251">RELATED LINKS</span></span>

[<span data-ttu-id="3307c-252">Sök-modul</span><span class="sxs-lookup"><span data-stu-id="3307c-252">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="3307c-253">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="3307c-253">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="3307c-254">Importera-modul</span><span class="sxs-lookup"><span data-stu-id="3307c-254">Import-Module</span></span>](../Microsoft.PowerShell.Core/Import-Module.md)

[<span data-ttu-id="3307c-255">Publicera-modul</span><span class="sxs-lookup"><span data-stu-id="3307c-255">Publish-Module</span></span>](Publish-Module.md)

[<span data-ttu-id="3307c-256">Registrera – PSRepository</span><span class="sxs-lookup"><span data-stu-id="3307c-256">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="3307c-257">Avinstallera-modul</span><span class="sxs-lookup"><span data-stu-id="3307c-257">Uninstall-Module</span></span>](Uninstall-Module.md)

[<span data-ttu-id="3307c-258">Update-modul</span><span class="sxs-lookup"><span data-stu-id="3307c-258">Update-Module</span></span>](Update-Module.md)

[<span data-ttu-id="3307c-259">about_Module</span><span class="sxs-lookup"><span data-stu-id="3307c-259">about_Module</span></span>](../Microsoft.PowerShell.Core/About/about_Modules.md)
