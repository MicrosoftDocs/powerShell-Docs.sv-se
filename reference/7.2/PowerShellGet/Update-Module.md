---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/16/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Module
ms.openlocfilehash: f29c208805894634960085cd3816ce7780b7602f
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891848"
---
# <span data-ttu-id="ffd04-102">Update-Module</span><span class="sxs-lookup"><span data-stu-id="ffd04-102">Update-Module</span></span>

## <span data-ttu-id="ffd04-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="ffd04-103">SYNOPSIS</span></span>
<span data-ttu-id="ffd04-104">Hämtar och installerar den senaste versionen av angivna moduler från ett onlinegalleri till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="ffd04-104">Downloads and installs the newest version of specified modules from an online gallery to the local computer.</span></span>

## <span data-ttu-id="ffd04-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ffd04-105">SYNTAX</span></span>

### <span data-ttu-id="ffd04-106">Alla</span><span class="sxs-lookup"><span data-stu-id="ffd04-106">All</span></span>

```
Update-Module [[-Name] <String[]>] [-RequiredVersion <String>] [-MaximumVersion <String>]
 [-Credential <PSCredential>] [-Scope <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Force] [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ffd04-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ffd04-107">DESCRIPTION</span></span>

<span data-ttu-id="ffd04-108">`Update-Module`Cmdleten installerar en moduls nyaste version från ett onlinegalleri.</span><span class="sxs-lookup"><span data-stu-id="ffd04-108">The `Update-Module` cmdlet installs a module's newest version from an online gallery.</span></span> <span data-ttu-id="ffd04-109">Du uppmanas att bekräfta uppdateringen innan den installeras.</span><span class="sxs-lookup"><span data-stu-id="ffd04-109">You're prompted to confirm the update before it's installed.</span></span> <span data-ttu-id="ffd04-110">Uppdateringar installeras bara för moduler som har installerats på den lokala datorn med `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="ffd04-110">Updates are installed only for modules that were installed on the local computer with `Install-Module`.</span></span> <span data-ttu-id="ffd04-111">`Update-Module` söker efter `$env:PSModulePath` installerade moduler.</span><span class="sxs-lookup"><span data-stu-id="ffd04-111">`Update-Module` searches `$env:PSModulePath` for installed modules.</span></span>

<span data-ttu-id="ffd04-112">`Update-Module` Om inga parametrar har angetts uppdaterar alla installerade moduler.</span><span class="sxs-lookup"><span data-stu-id="ffd04-112">`Update-Module` with no parameters specified updates all installed modules.</span></span> <span data-ttu-id="ffd04-113">Om du vill ange en modul som ska uppdateras använder du parametern **Name** .</span><span class="sxs-lookup"><span data-stu-id="ffd04-113">To specify a module to update, use the **Name** parameter.</span></span> <span data-ttu-id="ffd04-114">Du kan uppdatera till en moduls aktuella version med hjälp av parametern **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="ffd04-114">You can update to a module's specific version by using the **RequiredVersion** parameter.</span></span>

<span data-ttu-id="ffd04-115">Om en installerad modul redan är den senaste versionen, uppdateras inte modulen.</span><span class="sxs-lookup"><span data-stu-id="ffd04-115">If an installed module is already the newest version, the module isn't updated.</span></span> <span data-ttu-id="ffd04-116">Om modulen inte finns i `$env:PSModulePath` visas ett fel.</span><span class="sxs-lookup"><span data-stu-id="ffd04-116">If the module isn't found in `$env:PSModulePath`, an error is displayed.</span></span>

<span data-ttu-id="ffd04-117">Använd om du vill visa de installerade modulerna `Get-InstalledModule` .</span><span class="sxs-lookup"><span data-stu-id="ffd04-117">To display the installed modules, use `Get-InstalledModule`.</span></span>

## <span data-ttu-id="ffd04-118">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="ffd04-118">EXAMPLES</span></span>

### <span data-ttu-id="ffd04-119">Exempel 1: uppdatera alla moduler</span><span class="sxs-lookup"><span data-stu-id="ffd04-119">Example 1: Update all modules</span></span>

<span data-ttu-id="ffd04-120">I det här exemplet uppdateras alla installerade moduler till den senaste versionen i ett onlinegalleri.</span><span class="sxs-lookup"><span data-stu-id="ffd04-120">This example updates all installed modules to the newest version in an online gallery.</span></span>

```powershell
Update-Module
```

### <span data-ttu-id="ffd04-121">Exempel 2: uppdatera en modul efter namn</span><span class="sxs-lookup"><span data-stu-id="ffd04-121">Example 2: Update a module by name</span></span>

<span data-ttu-id="ffd04-122">Det här exemplet uppdaterar en speciell modul till den senaste versionen i ett onlinegalleri.</span><span class="sxs-lookup"><span data-stu-id="ffd04-122">This example updates a specific module to the newest version in an online gallery.</span></span>

```powershell
Update-Module -Name SpeculationControl
```

<span data-ttu-id="ffd04-123">`Update-Module` använder **namn** parametern för att uppdatera en speciell modul, **SpeculationControl**.</span><span class="sxs-lookup"><span data-stu-id="ffd04-123">`Update-Module` uses the **Name** parameter to update a specific module, **SpeculationControl**.</span></span>

### <span data-ttu-id="ffd04-124">Exempel 3: Visa vad-om-Update-Module körs</span><span class="sxs-lookup"><span data-stu-id="ffd04-124">Example 3: View what-if Update-Module runs</span></span>

<span data-ttu-id="ffd04-125">Det här exemplet gör ett konsekvens scenario för att visa vad som händer om körs `Update-Module` .</span><span class="sxs-lookup"><span data-stu-id="ffd04-125">This example does a what-if scenario to show what happens if `Update-Module` is run.</span></span> <span data-ttu-id="ffd04-126">Kommandot körs inte.</span><span class="sxs-lookup"><span data-stu-id="ffd04-126">The command isn't run.</span></span>

```powershell
Update-Module -WhatIf
```

```Output
What if: Performing the operation "Update-Module" on target "Version '2.8.0' of module
  'Carbon', updating to version '2.8.1'".
What if: Performing the operation "Update-Module" on target "Version '1.0.10' of module
  'SpeculationControl', updating to version '1.0.14'".
```

<span data-ttu-id="ffd04-127">`Update-Module` använder parametern **whatIf** som visar vad som skulle hända om kördes `Update-Module` .</span><span class="sxs-lookup"><span data-stu-id="ffd04-127">`Update-Module` uses the **WhatIf** parameter display what would happen if `Update-Module` were run.</span></span>

### <span data-ttu-id="ffd04-128">Exempel 4: uppdatera en modul till en angiven version</span><span class="sxs-lookup"><span data-stu-id="ffd04-128">Example 4: Update a module to a specified version</span></span>

<span data-ttu-id="ffd04-129">I det här exemplet uppdateras en modul till en angiven version.</span><span class="sxs-lookup"><span data-stu-id="ffd04-129">In this example, a module is updated to a specific version.</span></span> <span data-ttu-id="ffd04-130">Versionen måste finnas i online-galleriet eller så visas ett fel.</span><span class="sxs-lookup"><span data-stu-id="ffd04-130">The version must exist in the online gallery or an error is displayed.</span></span>

```powershell
Update-Module -Name SpeculationControl -RequiredVersion 1.0.14
```

<span data-ttu-id="ffd04-131">`Update-Module` använder parametern **Name** för att ange modulen **SpeculationControl**.</span><span class="sxs-lookup"><span data-stu-id="ffd04-131">`Update-Module` uses the **Name** parameter to specify the module, **SpeculationControl**.</span></span> <span data-ttu-id="ffd04-132">Parametern **RequiredVersion** anger versionen, **1.0.14**.</span><span class="sxs-lookup"><span data-stu-id="ffd04-132">The **RequiredVersion** parameter specifies the version, **1.0.14**.</span></span>

### <span data-ttu-id="ffd04-133">Exempel 5: uppdatera en modul utan bekräftelse</span><span class="sxs-lookup"><span data-stu-id="ffd04-133">Example 5: Update a module without confirmation</span></span>

<span data-ttu-id="ffd04-134">Det här exemplet begär inte bekräftelse för att uppdatera modulen till den senaste versionen från ett onlinegalleri.</span><span class="sxs-lookup"><span data-stu-id="ffd04-134">This example doesn't request confirmation to update the module to the newest version from an online gallery.</span></span> <span data-ttu-id="ffd04-135">Om modulen redan är installerad installerar **Force** -parametern om modulen.</span><span class="sxs-lookup"><span data-stu-id="ffd04-135">If the module is already installed, the **Force** parameter reinstalls the module.</span></span>

```powershell
Update-Module -Name SpeculationControl -Force
```

<span data-ttu-id="ffd04-136">`Update-Module` använder parametern **Name** för att ange modulen **SpeculationControl**.</span><span class="sxs-lookup"><span data-stu-id="ffd04-136">`Update-Module` uses the **Name** parameter to specify the module, **SpeculationControl**.</span></span> <span data-ttu-id="ffd04-137">Parametern **Force** uppdaterar modulen utan att begära bekräftelse från användaren.</span><span class="sxs-lookup"><span data-stu-id="ffd04-137">The **Force** parameter updates the module without requesting user confirmation.</span></span>

## <span data-ttu-id="ffd04-138">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="ffd04-138">PARAMETERS</span></span>

### <span data-ttu-id="ffd04-139">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="ffd04-139">-AcceptLicense</span></span>

<span data-ttu-id="ffd04-140">Godkänn licens avtalet automatiskt under installationen om paketet kräver det.</span><span class="sxs-lookup"><span data-stu-id="ffd04-140">Automatically accept the license agreement during installation if the package requires it.</span></span>

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

### <span data-ttu-id="ffd04-141">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="ffd04-141">-AllowPrerelease</span></span>

<span data-ttu-id="ffd04-142">Gör att du kan uppdatera en modul med den nyare modulen markerad som en för hands version.</span><span class="sxs-lookup"><span data-stu-id="ffd04-142">Allows you to update a module with the newer module marked as a prerelease.</span></span>

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

### <span data-ttu-id="ffd04-143">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ffd04-143">-Confirm</span></span>

<span data-ttu-id="ffd04-144">Du uppmanas att bekräfta innan du kör `Update-Module` .</span><span class="sxs-lookup"><span data-stu-id="ffd04-144">Prompts you for confirmation before running `Update-Module`.</span></span>

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

### <span data-ttu-id="ffd04-145">-Credential</span><span class="sxs-lookup"><span data-stu-id="ffd04-145">-Credential</span></span>

<span data-ttu-id="ffd04-146">Anger ett användar konto som har behörighet att uppdatera en modul.</span><span class="sxs-lookup"><span data-stu-id="ffd04-146">Specifies a user account that has permission to update a module.</span></span>

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

### <span data-ttu-id="ffd04-147">-Force</span><span class="sxs-lookup"><span data-stu-id="ffd04-147">-Force</span></span>

<span data-ttu-id="ffd04-148">Tvingar fram en uppdatering av varje angiven modul utan att uppmana att begära bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="ffd04-148">Forces an update of each specified module without a prompt to request confirmation.</span></span> <span data-ttu-id="ffd04-149">Om modulen redan är installerad **installerar du om** modulen.</span><span class="sxs-lookup"><span data-stu-id="ffd04-149">If the module is already installed, **Force** reinstalls the module.</span></span>

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

### <span data-ttu-id="ffd04-150">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="ffd04-150">-MaximumVersion</span></span>

<span data-ttu-id="ffd04-151">Anger den maximala version av en enskild modul som ska uppdateras.</span><span class="sxs-lookup"><span data-stu-id="ffd04-151">Specifies the maximum version of a single module to update.</span></span> <span data-ttu-id="ffd04-152">Du kan inte lägga till den här parametern om du försöker uppdatera flera moduler.</span><span class="sxs-lookup"><span data-stu-id="ffd04-152">You can't add this parameter if you're attempting to update multiple modules.</span></span> <span data-ttu-id="ffd04-153">Parametrarna **MaximumVersion** och **RequiredVersion** kan inte användas i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="ffd04-153">The **MaximumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ffd04-154">-Name</span><span class="sxs-lookup"><span data-stu-id="ffd04-154">-Name</span></span>

<span data-ttu-id="ffd04-155">Anger namnen på en eller flera moduler som ska uppdateras.</span><span class="sxs-lookup"><span data-stu-id="ffd04-155">Specifies the names of one or more modules to update.</span></span> <span data-ttu-id="ffd04-156">`Update-Module` söker efter `$env:PSModulePath` moduler att uppdatera.</span><span class="sxs-lookup"><span data-stu-id="ffd04-156">`Update-Module` searches `$env:PSModulePath` for the modules to update.</span></span> <span data-ttu-id="ffd04-157">Om det inte finns några matchningar i `$env:PSModulePath` för angivet Modulnamn uppstår ett fel.</span><span class="sxs-lookup"><span data-stu-id="ffd04-157">If no matches are found in `$env:PSModulePath` for the specified module name, an error occurs.</span></span>

<span data-ttu-id="ffd04-158">Jokertecken accepteras i modulnamn.</span><span class="sxs-lookup"><span data-stu-id="ffd04-158">Wildcards are accepted in module names.</span></span> <span data-ttu-id="ffd04-159">Om du lägger till jokertecken till det angivna namnet och inga matchningar hittas inträffar inget fel.</span><span class="sxs-lookup"><span data-stu-id="ffd04-159">If you add wildcard characters to the specified name and no matches are found, no error occurs.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="ffd04-160">– PassThru</span><span class="sxs-lookup"><span data-stu-id="ffd04-160">-PassThru</span></span>

<span data-ttu-id="ffd04-161">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="ffd04-161">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="ffd04-162">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="ffd04-162">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="ffd04-163">-Proxy</span><span class="sxs-lookup"><span data-stu-id="ffd04-163">-Proxy</span></span>

<span data-ttu-id="ffd04-164">Anger en proxyserver för begäran, i stället för att ansluta direkt till en Internet resurs.</span><span class="sxs-lookup"><span data-stu-id="ffd04-164">Specifies a proxy server for the request, rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="ffd04-165">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="ffd04-165">-ProxyCredential</span></span>

<span data-ttu-id="ffd04-166">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="ffd04-166">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="ffd04-167">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="ffd04-167">-RequiredVersion</span></span>

<span data-ttu-id="ffd04-168">Anger den exakta version som den befintliga installerade modulen ska uppdateras till.</span><span class="sxs-lookup"><span data-stu-id="ffd04-168">Specifies the exact version to which the existing installed module will be updated.</span></span> <span data-ttu-id="ffd04-169">Versionen som anges av **RequiredVersion** måste finnas i online-galleriet eller så visas ett fel.</span><span class="sxs-lookup"><span data-stu-id="ffd04-169">The version specified by **RequiredVersion** must exist in the online gallery or an error is displayed.</span></span> <span data-ttu-id="ffd04-170">Om mer än en modul uppdateras i ett enda kommando kan du inte använda **RequiredVersion**.</span><span class="sxs-lookup"><span data-stu-id="ffd04-170">If more than one module is updated in a single command, you can't use **RequiredVersion**.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ffd04-171">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="ffd04-171">-Scope</span></span>

<span data-ttu-id="ffd04-172">Anger modulens installations omfång.</span><span class="sxs-lookup"><span data-stu-id="ffd04-172">Specifies the installation scope of the module.</span></span> <span data-ttu-id="ffd04-173">De acceptabla värdena för den här parametern är **allusers** och **CurrentUser**.</span><span class="sxs-lookup"><span data-stu-id="ffd04-173">The acceptable values for this parameter are **AllUsers** and **CurrentUser**.</span></span> <span data-ttu-id="ffd04-174">Om **omfång** inte anges installeras uppdateringen i **CurrentUser** -omfånget.</span><span class="sxs-lookup"><span data-stu-id="ffd04-174">If **Scope** isn't specified, the update is installed in the **CurrentUser** scope.</span></span>

<span data-ttu-id="ffd04-175">**Allusers** -omfånget kräver förhöjd behörighet och installerar moduler på en plats som är tillgänglig för alla användare av datorn:</span><span class="sxs-lookup"><span data-stu-id="ffd04-175">The **AllUsers** scope requires elevated permissions and installs modules in a location that is accessible to all users of the computer:</span></span>

`$env:ProgramFiles\PowerShell\Modules`

<span data-ttu-id="ffd04-176">**CurrentUser** kräver inte utökade behörigheter och installerar moduler på en plats som endast är tillgänglig för den aktuella användaren av datorn:</span><span class="sxs-lookup"><span data-stu-id="ffd04-176">The **CurrentUser** doesn't require elevated permissions and installs modules in a location that is accessible only to the current user of the computer:</span></span>

`$home\Documents\PowerShell\Modules`

<span data-ttu-id="ffd04-177">När inget **omfång** har definierats anges standardvärdet baserat på PowerShellGet-versionen.</span><span class="sxs-lookup"><span data-stu-id="ffd04-177">When no **Scope** is defined, the default is set based on the PowerShellGet version.</span></span>

- <span data-ttu-id="ffd04-178">I PowerShellGet-versioner 2.0.0 och senare är standardvärdet **CurrentUser**, vilket inte kräver höjning för installation.</span><span class="sxs-lookup"><span data-stu-id="ffd04-178">In PowerShellGet versions 2.0.0 and above, the default is **CurrentUser**, which does not require elevation for install.</span></span>
- <span data-ttu-id="ffd04-179">I PowerShellGet 1. x-versioner är standardvärdet **allusers**, vilket kräver höjning för installation.</span><span class="sxs-lookup"><span data-stu-id="ffd04-179">In PowerShellGet 1.x versions, the default is **AllUsers**, which requires elevation for install.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: CurrentUser
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ffd04-180">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ffd04-180">-WhatIf</span></span>

<span data-ttu-id="ffd04-181">Visar vad som händer om `Update-Module` körs.</span><span class="sxs-lookup"><span data-stu-id="ffd04-181">Shows what would happen if `Update-Module` runs.</span></span> <span data-ttu-id="ffd04-182">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="ffd04-182">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="ffd04-183">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ffd04-183">CommonParameters</span></span>

<span data-ttu-id="ffd04-184">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ffd04-184">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ffd04-185">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ffd04-185">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ffd04-186">INDATA</span><span class="sxs-lookup"><span data-stu-id="ffd04-186">INPUTS</span></span>

### <span data-ttu-id="ffd04-187">System.String[]</span><span class="sxs-lookup"><span data-stu-id="ffd04-187">System.String[]</span></span>

### <span data-ttu-id="ffd04-188">System. String</span><span class="sxs-lookup"><span data-stu-id="ffd04-188">System.String</span></span>

### <span data-ttu-id="ffd04-189">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="ffd04-189">System.Management.Automation.PSCredential</span></span>

### <span data-ttu-id="ffd04-190">System. URI</span><span class="sxs-lookup"><span data-stu-id="ffd04-190">System.Uri</span></span>

## <span data-ttu-id="ffd04-191">UTDATA</span><span class="sxs-lookup"><span data-stu-id="ffd04-191">OUTPUTS</span></span>

### <span data-ttu-id="ffd04-192">System. Object</span><span class="sxs-lookup"><span data-stu-id="ffd04-192">System.Object</span></span>

## <span data-ttu-id="ffd04-193">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="ffd04-193">NOTES</span></span>

<span data-ttu-id="ffd04-194">För PowerShell version 6,0 och senare är standard installations omfånget alltid **CurrentUser**.</span><span class="sxs-lookup"><span data-stu-id="ffd04-194">For PowerShell version 6.0 and above, the default installation scope is always **CurrentUser**.</span></span>
<span data-ttu-id="ffd04-195">Module-uppdateringar för **CurrentUser**, `$home\Documents\PowerShell\Modules` , behöver inte utökade behörigheter.</span><span class="sxs-lookup"><span data-stu-id="ffd04-195">Module updates for **CurrentUser**, `$home\Documents\PowerShell\Modules`, don't need elevated permissions.</span></span> <span data-ttu-id="ffd04-196">Uppdatering av modulen för **allusers**, `$env:ProgramFiles\PowerShell\Modules` kräver förhöjd behörighet.</span><span class="sxs-lookup"><span data-stu-id="ffd04-196">Module updates for **AllUsers**, `$env:ProgramFiles\PowerShell\Modules`, need elevated permissions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ffd04-197">Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1.</span><span class="sxs-lookup"><span data-stu-id="ffd04-197">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="ffd04-198">Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="ffd04-198">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="ffd04-199">Använd följande kommando för att se till att du använder TLS 1,2:</span><span class="sxs-lookup"><span data-stu-id="ffd04-199">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="ffd04-200">Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="ffd04-200">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

<span data-ttu-id="ffd04-201">`Update-Module` körs på PowerShell 3,0 eller senare versioner av PowerShell på Windows 7 eller Windows 2008 R2 och senare versioner av Windows.</span><span class="sxs-lookup"><span data-stu-id="ffd04-201">`Update-Module` runs on PowerShell 3.0 or later releases of PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>

<span data-ttu-id="ffd04-202">Om den modul som du anger med **namn** parametern inte har installerats med hjälp av `Install-Module` , uppstår ett fel.</span><span class="sxs-lookup"><span data-stu-id="ffd04-202">If the module that you specify with the **Name** parameter wasn't installed by using `Install-Module`, an error occurs.</span></span>

<span data-ttu-id="ffd04-203">Du kan bara köra `Update-Module` i moduler som du har installerat från Onlinegalleri online genom att köra `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="ffd04-203">You can only run `Update-Module` on modules that you installed from the online gallery by running `Install-Module`.</span></span>

<span data-ttu-id="ffd04-204">Om `Update-Module` försök att uppdatera binärfiler som används, `Update-Module` returnerar ett fel som identifierar problem processerna.</span><span class="sxs-lookup"><span data-stu-id="ffd04-204">If `Update-Module` attempts to update binaries that are in use, `Update-Module` returns an error that identifies the problem processes.</span></span> <span data-ttu-id="ffd04-205">Användaren meddelas om att försöka igen `Update-Module` efter att processerna har stoppats.</span><span class="sxs-lookup"><span data-stu-id="ffd04-205">The user is informed to retry `Update-Module` after the processes are stopped.</span></span>

## <span data-ttu-id="ffd04-206">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="ffd04-206">RELATED LINKS</span></span>

[<span data-ttu-id="ffd04-207">Sök-modul</span><span class="sxs-lookup"><span data-stu-id="ffd04-207">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="ffd04-208">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="ffd04-208">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="ffd04-209">Installera-modul</span><span class="sxs-lookup"><span data-stu-id="ffd04-209">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="ffd04-210">Publicera-modul</span><span class="sxs-lookup"><span data-stu-id="ffd04-210">Publish-Module</span></span>](Publish-Module.md)

[<span data-ttu-id="ffd04-211">Avinstallera-modul</span><span class="sxs-lookup"><span data-stu-id="ffd04-211">Uninstall-Module</span></span>](Uninstall-Module.md)
