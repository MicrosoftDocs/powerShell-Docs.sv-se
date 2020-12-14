---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/16/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-module?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Module
ms.openlocfilehash: ee94ba7808cb364306826325cfbc3df2cf9834a5
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892594"
---
# <span data-ttu-id="a868c-103">Update-Module</span><span class="sxs-lookup"><span data-stu-id="a868c-103">Update-Module</span></span>

## <span data-ttu-id="a868c-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="a868c-104">SYNOPSIS</span></span>
<span data-ttu-id="a868c-105">Hämtar och installerar den senaste versionen av angivna moduler från ett onlinegalleri till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="a868c-105">Downloads and installs the newest version of specified modules from an online gallery to the local computer.</span></span>

## <span data-ttu-id="a868c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a868c-106">SYNTAX</span></span>

### <span data-ttu-id="a868c-107">Alla</span><span class="sxs-lookup"><span data-stu-id="a868c-107">All</span></span>

```
Update-Module [[-Name] <String[]>] [-RequiredVersion <String>] [-MaximumVersion <String>]
 [-Credential <PSCredential>] [-Scope <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Force] [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="a868c-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a868c-108">DESCRIPTION</span></span>

<span data-ttu-id="a868c-109">`Update-Module`Cmdleten installerar en moduls nyaste version från ett onlinegalleri.</span><span class="sxs-lookup"><span data-stu-id="a868c-109">The `Update-Module` cmdlet installs a module's newest version from an online gallery.</span></span> <span data-ttu-id="a868c-110">Du uppmanas att bekräfta uppdateringen innan den installeras.</span><span class="sxs-lookup"><span data-stu-id="a868c-110">You're prompted to confirm the update before it's installed.</span></span> <span data-ttu-id="a868c-111">Uppdateringar installeras bara för moduler som har installerats på den lokala datorn med `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="a868c-111">Updates are installed only for modules that were installed on the local computer with `Install-Module`.</span></span> <span data-ttu-id="a868c-112">`Update-Module` söker efter `$env:PSModulePath` installerade moduler.</span><span class="sxs-lookup"><span data-stu-id="a868c-112">`Update-Module` searches `$env:PSModulePath` for installed modules.</span></span>

<span data-ttu-id="a868c-113">`Update-Module` Om inga parametrar har angetts uppdaterar alla installerade moduler.</span><span class="sxs-lookup"><span data-stu-id="a868c-113">`Update-Module` with no parameters specified updates all installed modules.</span></span> <span data-ttu-id="a868c-114">Om du vill ange en modul som ska uppdateras använder du parametern **Name** .</span><span class="sxs-lookup"><span data-stu-id="a868c-114">To specify a module to update, use the **Name** parameter.</span></span> <span data-ttu-id="a868c-115">Du kan uppdatera till en moduls aktuella version med hjälp av parametern **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="a868c-115">You can update to a module's specific version by using the **RequiredVersion** parameter.</span></span>

<span data-ttu-id="a868c-116">Om en installerad modul redan är den senaste versionen, uppdateras inte modulen.</span><span class="sxs-lookup"><span data-stu-id="a868c-116">If an installed module is already the newest version, the module isn't updated.</span></span> <span data-ttu-id="a868c-117">Om modulen inte finns i `$env:PSModulePath` visas ett fel.</span><span class="sxs-lookup"><span data-stu-id="a868c-117">If the module isn't found in `$env:PSModulePath`, an error is displayed.</span></span>

<span data-ttu-id="a868c-118">Använd om du vill visa de installerade modulerna `Get-InstalledModule` .</span><span class="sxs-lookup"><span data-stu-id="a868c-118">To display the installed modules, use `Get-InstalledModule`.</span></span>

## <span data-ttu-id="a868c-119">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="a868c-119">EXAMPLES</span></span>

### <span data-ttu-id="a868c-120">Exempel 1: uppdatera alla moduler</span><span class="sxs-lookup"><span data-stu-id="a868c-120">Example 1: Update all modules</span></span>

<span data-ttu-id="a868c-121">I det här exemplet uppdateras alla installerade moduler till den senaste versionen i ett onlinegalleri.</span><span class="sxs-lookup"><span data-stu-id="a868c-121">This example updates all installed modules to the newest version in an online gallery.</span></span>

```powershell
Update-Module
```

### <span data-ttu-id="a868c-122">Exempel 2: uppdatera en modul efter namn</span><span class="sxs-lookup"><span data-stu-id="a868c-122">Example 2: Update a module by name</span></span>

<span data-ttu-id="a868c-123">Det här exemplet uppdaterar en speciell modul till den senaste versionen i ett onlinegalleri.</span><span class="sxs-lookup"><span data-stu-id="a868c-123">This example updates a specific module to the newest version in an online gallery.</span></span>

```powershell
Update-Module -Name SpeculationControl
```

<span data-ttu-id="a868c-124">`Update-Module` använder **namn** parametern för att uppdatera en speciell modul, **SpeculationControl**.</span><span class="sxs-lookup"><span data-stu-id="a868c-124">`Update-Module` uses the **Name** parameter to update a specific module, **SpeculationControl**.</span></span>

### <span data-ttu-id="a868c-125">Exempel 3: Visa vad-om-Update-Module körs</span><span class="sxs-lookup"><span data-stu-id="a868c-125">Example 3: View what-if Update-Module runs</span></span>

<span data-ttu-id="a868c-126">Det här exemplet gör ett konsekvens scenario för att visa vad som händer om körs `Update-Module` .</span><span class="sxs-lookup"><span data-stu-id="a868c-126">This example does a what-if scenario to show what happens if `Update-Module` is run.</span></span> <span data-ttu-id="a868c-127">Kommandot körs inte.</span><span class="sxs-lookup"><span data-stu-id="a868c-127">The command isn't run.</span></span>

```powershell
Update-Module -WhatIf
```

```Output
What if: Performing the operation "Update-Module" on target "Version '2.8.0' of module
  'Carbon', updating to version '2.8.1'".
What if: Performing the operation "Update-Module" on target "Version '1.0.10' of module
  'SpeculationControl', updating to version '1.0.14'".
```

<span data-ttu-id="a868c-128">`Update-Module` använder parametern **whatIf** som visar vad som skulle hända om kördes `Update-Module` .</span><span class="sxs-lookup"><span data-stu-id="a868c-128">`Update-Module` uses the **WhatIf** parameter display what would happen if `Update-Module` were run.</span></span>

### <span data-ttu-id="a868c-129">Exempel 4: uppdatera en modul till en angiven version</span><span class="sxs-lookup"><span data-stu-id="a868c-129">Example 4: Update a module to a specified version</span></span>

<span data-ttu-id="a868c-130">I det här exemplet uppdateras en modul till en angiven version.</span><span class="sxs-lookup"><span data-stu-id="a868c-130">In this example, a module is updated to a specific version.</span></span> <span data-ttu-id="a868c-131">Versionen måste finnas i online-galleriet eller så visas ett fel.</span><span class="sxs-lookup"><span data-stu-id="a868c-131">The version must exist in the online gallery or an error is displayed.</span></span>

```powershell
Update-Module -Name SpeculationControl -RequiredVersion 1.0.14
```

<span data-ttu-id="a868c-132">`Update-Module` använder parametern **Name** för att ange modulen **SpeculationControl**.</span><span class="sxs-lookup"><span data-stu-id="a868c-132">`Update-Module` uses the **Name** parameter to specify the module, **SpeculationControl**.</span></span> <span data-ttu-id="a868c-133">Parametern **RequiredVersion** anger versionen, **1.0.14**.</span><span class="sxs-lookup"><span data-stu-id="a868c-133">The **RequiredVersion** parameter specifies the version, **1.0.14**.</span></span>

### <span data-ttu-id="a868c-134">Exempel 5: uppdatera en modul utan bekräftelse</span><span class="sxs-lookup"><span data-stu-id="a868c-134">Example 5: Update a module without confirmation</span></span>

<span data-ttu-id="a868c-135">Det här exemplet begär inte bekräftelse för att uppdatera modulen till den senaste versionen från ett onlinegalleri.</span><span class="sxs-lookup"><span data-stu-id="a868c-135">This example doesn't request confirmation to update the module to the newest version from an online gallery.</span></span> <span data-ttu-id="a868c-136">Om modulen redan är installerad installerar **Force** -parametern om modulen.</span><span class="sxs-lookup"><span data-stu-id="a868c-136">If the module is already installed, the **Force** parameter reinstalls the module.</span></span>

```powershell
Update-Module -Name SpeculationControl -Force
```

<span data-ttu-id="a868c-137">`Update-Module` använder parametern **Name** för att ange modulen **SpeculationControl**.</span><span class="sxs-lookup"><span data-stu-id="a868c-137">`Update-Module` uses the **Name** parameter to specify the module, **SpeculationControl**.</span></span> <span data-ttu-id="a868c-138">Parametern **Force** uppdaterar modulen utan att begära bekräftelse från användaren.</span><span class="sxs-lookup"><span data-stu-id="a868c-138">The **Force** parameter updates the module without requesting user confirmation.</span></span>

## <span data-ttu-id="a868c-139">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="a868c-139">PARAMETERS</span></span>

### <span data-ttu-id="a868c-140">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="a868c-140">-AcceptLicense</span></span>

<span data-ttu-id="a868c-141">Godkänn licens avtalet automatiskt under installationen om paketet kräver det.</span><span class="sxs-lookup"><span data-stu-id="a868c-141">Automatically accept the license agreement during installation if the package requires it.</span></span>

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

### <span data-ttu-id="a868c-142">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="a868c-142">-AllowPrerelease</span></span>

<span data-ttu-id="a868c-143">Gör att du kan uppdatera en modul med den nyare modulen markerad som en för hands version.</span><span class="sxs-lookup"><span data-stu-id="a868c-143">Allows you to update a module with the newer module marked as a prerelease.</span></span>

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

### <span data-ttu-id="a868c-144">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a868c-144">-Confirm</span></span>

<span data-ttu-id="a868c-145">Du uppmanas att bekräfta innan du kör `Update-Module` .</span><span class="sxs-lookup"><span data-stu-id="a868c-145">Prompts you for confirmation before running `Update-Module`.</span></span>

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

### <span data-ttu-id="a868c-146">-Credential</span><span class="sxs-lookup"><span data-stu-id="a868c-146">-Credential</span></span>

<span data-ttu-id="a868c-147">Anger ett användar konto som har behörighet att uppdatera en modul.</span><span class="sxs-lookup"><span data-stu-id="a868c-147">Specifies a user account that has permission to update a module.</span></span>

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

### <span data-ttu-id="a868c-148">-Force</span><span class="sxs-lookup"><span data-stu-id="a868c-148">-Force</span></span>

<span data-ttu-id="a868c-149">Tvingar fram en uppdatering av varje angiven modul utan att uppmana att begära bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="a868c-149">Forces an update of each specified module without a prompt to request confirmation.</span></span> <span data-ttu-id="a868c-150">Om modulen redan är installerad **installerar du om** modulen.</span><span class="sxs-lookup"><span data-stu-id="a868c-150">If the module is already installed, **Force** reinstalls the module.</span></span>

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

### <span data-ttu-id="a868c-151">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="a868c-151">-MaximumVersion</span></span>

<span data-ttu-id="a868c-152">Anger den maximala version av en enskild modul som ska uppdateras.</span><span class="sxs-lookup"><span data-stu-id="a868c-152">Specifies the maximum version of a single module to update.</span></span> <span data-ttu-id="a868c-153">Du kan inte lägga till den här parametern om du försöker uppdatera flera moduler.</span><span class="sxs-lookup"><span data-stu-id="a868c-153">You can't add this parameter if you're attempting to update multiple modules.</span></span> <span data-ttu-id="a868c-154">Parametrarna **MaximumVersion** och **RequiredVersion** kan inte användas i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="a868c-154">The **MaximumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="a868c-155">-Name</span><span class="sxs-lookup"><span data-stu-id="a868c-155">-Name</span></span>

<span data-ttu-id="a868c-156">Anger namnen på en eller flera moduler som ska uppdateras.</span><span class="sxs-lookup"><span data-stu-id="a868c-156">Specifies the names of one or more modules to update.</span></span> <span data-ttu-id="a868c-157">`Update-Module` söker efter `$env:PSModulePath` moduler att uppdatera.</span><span class="sxs-lookup"><span data-stu-id="a868c-157">`Update-Module` searches `$env:PSModulePath` for the modules to update.</span></span> <span data-ttu-id="a868c-158">Om det inte finns några matchningar i `$env:PSModulePath` för angivet Modulnamn uppstår ett fel.</span><span class="sxs-lookup"><span data-stu-id="a868c-158">If no matches are found in `$env:PSModulePath` for the specified module name, an error occurs.</span></span>

<span data-ttu-id="a868c-159">Jokertecken accepteras i modulnamn.</span><span class="sxs-lookup"><span data-stu-id="a868c-159">Wildcards are accepted in module names.</span></span> <span data-ttu-id="a868c-160">Om du lägger till jokertecken till det angivna namnet och inga matchningar hittas inträffar inget fel.</span><span class="sxs-lookup"><span data-stu-id="a868c-160">If you add wildcard characters to the specified name and no matches are found, no error occurs.</span></span>

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

### <span data-ttu-id="a868c-161">– PassThru</span><span class="sxs-lookup"><span data-stu-id="a868c-161">-PassThru</span></span>

<span data-ttu-id="a868c-162">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="a868c-162">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="a868c-163">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="a868c-163">By default, this cmdlet does not generate any output.</span></span> <span data-ttu-id="a868c-164">Stöd för **Passthru** -parameter har lagts till i **PowerShellGet** 2.0.0</span><span class="sxs-lookup"><span data-stu-id="a868c-164">The **PassThru** parameter support was added in **PowerShellGet** 2.0.0</span></span>

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

### <span data-ttu-id="a868c-165">-Proxy</span><span class="sxs-lookup"><span data-stu-id="a868c-165">-Proxy</span></span>

<span data-ttu-id="a868c-166">Anger en proxyserver för begäran, i stället för att ansluta direkt till en Internet resurs.</span><span class="sxs-lookup"><span data-stu-id="a868c-166">Specifies a proxy server for the request, rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="a868c-167">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="a868c-167">-ProxyCredential</span></span>

<span data-ttu-id="a868c-168">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="a868c-168">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="a868c-169">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="a868c-169">-RequiredVersion</span></span>

<span data-ttu-id="a868c-170">Anger den exakta version som den befintliga installerade modulen ska uppdateras till.</span><span class="sxs-lookup"><span data-stu-id="a868c-170">Specifies the exact version to which the existing installed module will be updated.</span></span> <span data-ttu-id="a868c-171">Versionen som anges av **RequiredVersion** måste finnas i online-galleriet eller så visas ett fel.</span><span class="sxs-lookup"><span data-stu-id="a868c-171">The version specified by **RequiredVersion** must exist in the online gallery or an error is displayed.</span></span> <span data-ttu-id="a868c-172">Om mer än en modul uppdateras i ett enda kommando kan du inte använda **RequiredVersion**.</span><span class="sxs-lookup"><span data-stu-id="a868c-172">If more than one module is updated in a single command, you can't use **RequiredVersion**.</span></span>

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

### <span data-ttu-id="a868c-173">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="a868c-173">-Scope</span></span>

<span data-ttu-id="a868c-174">Anger modulens installations omfång.</span><span class="sxs-lookup"><span data-stu-id="a868c-174">Specifies the installation scope of the module.</span></span> <span data-ttu-id="a868c-175">De acceptabla värdena för den här parametern är **allusers** och **CurrentUser**.</span><span class="sxs-lookup"><span data-stu-id="a868c-175">The acceptable values for this parameter are **AllUsers** and **CurrentUser**.</span></span> <span data-ttu-id="a868c-176">Om **omfång** inte anges installeras uppdateringen i **CurrentUser** -omfånget.</span><span class="sxs-lookup"><span data-stu-id="a868c-176">If **Scope** isn't specified, the update is installed in the **CurrentUser** scope.</span></span>

<span data-ttu-id="a868c-177">**Allusers** -omfånget kräver förhöjd behörighet och installerar moduler på en plats som är tillgänglig för alla användare av datorn:</span><span class="sxs-lookup"><span data-stu-id="a868c-177">The **AllUsers** scope requires elevated permissions and installs modules in a location that is accessible to all users of the computer:</span></span>

`$env:ProgramFiles\PowerShell\Modules`

<span data-ttu-id="a868c-178">**CurrentUser** kräver inte utökade behörigheter och installerar moduler på en plats som endast är tillgänglig för den aktuella användaren av datorn:</span><span class="sxs-lookup"><span data-stu-id="a868c-178">The **CurrentUser** doesn't require elevated permissions and installs modules in a location that is accessible only to the current user of the computer:</span></span>

`$home\Documents\PowerShell\Modules`

<span data-ttu-id="a868c-179">När inget **omfång** har definierats anges standardvärdet baserat på PowerShellGet-versionen.</span><span class="sxs-lookup"><span data-stu-id="a868c-179">When no **Scope** is defined, the default is set based on the PowerShellGet version.</span></span>

- <span data-ttu-id="a868c-180">I PowerShellGet-versioner 2.0.0 och senare är standardvärdet **allusers** när du kör en upphöjd session och **CurrentUser** för alla andra.</span><span class="sxs-lookup"><span data-stu-id="a868c-180">In PowerShellGet versions 2.0.0 and above, the default is **AllUsers** when running an elevated session and **CurrentUser** for all others.</span></span>
- <span data-ttu-id="a868c-181">I PowerShellGet 1. x-versioner är standardvärdet **allusers**, vilket kräver höjning för installation.</span><span class="sxs-lookup"><span data-stu-id="a868c-181">In PowerShellGet 1.x versions, the default is **AllUsers**, which requires elevation for install.</span></span>

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

### <span data-ttu-id="a868c-182">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a868c-182">-WhatIf</span></span>

<span data-ttu-id="a868c-183">Visar vad som händer om `Update-Module` körs.</span><span class="sxs-lookup"><span data-stu-id="a868c-183">Shows what would happen if `Update-Module` runs.</span></span> <span data-ttu-id="a868c-184">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="a868c-184">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="a868c-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a868c-185">CommonParameters</span></span>

<span data-ttu-id="a868c-186">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a868c-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a868c-187">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a868c-187">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a868c-188">INDATA</span><span class="sxs-lookup"><span data-stu-id="a868c-188">INPUTS</span></span>

### <span data-ttu-id="a868c-189">System.String[]</span><span class="sxs-lookup"><span data-stu-id="a868c-189">System.String[]</span></span>

### <span data-ttu-id="a868c-190">System. String</span><span class="sxs-lookup"><span data-stu-id="a868c-190">System.String</span></span>

### <span data-ttu-id="a868c-191">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="a868c-191">System.Management.Automation.PSCredential</span></span>

### <span data-ttu-id="a868c-192">System. URI</span><span class="sxs-lookup"><span data-stu-id="a868c-192">System.Uri</span></span>

## <span data-ttu-id="a868c-193">UTDATA</span><span class="sxs-lookup"><span data-stu-id="a868c-193">OUTPUTS</span></span>

### <span data-ttu-id="a868c-194">System. Object</span><span class="sxs-lookup"><span data-stu-id="a868c-194">System.Object</span></span>

## <span data-ttu-id="a868c-195">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="a868c-195">NOTES</span></span>

<span data-ttu-id="a868c-196">För PowerShell 5,1 eller lägre är standard omfånget i en upphöjd session **allusers** och i en icke-förhöjd session **CurrentUser**.</span><span class="sxs-lookup"><span data-stu-id="a868c-196">For PowerShell 5.1 or below, the default scope in an elevated session is **AllUsers**, and in a non-elevated session, **CurrentUser**.</span></span> <span data-ttu-id="a868c-197">Uppdatering av modulen för **allusers**, `$env:ProgramFiles\PowerShell\Modules` kräver förhöjd behörighet.</span><span class="sxs-lookup"><span data-stu-id="a868c-197">Module updates for **AllUsers**, `$env:ProgramFiles\PowerShell\Modules`, need elevated permissions.</span></span> <span data-ttu-id="a868c-198">Module-uppdateringar för **CurrentUser**, `$home\Documents\PowerShell\Modules` , behöver inte utökade behörigheter.</span><span class="sxs-lookup"><span data-stu-id="a868c-198">Module updates for **CurrentUser**, `$home\Documents\PowerShell\Modules`, don't need elevated permissions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a868c-199">Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1.</span><span class="sxs-lookup"><span data-stu-id="a868c-199">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="a868c-200">Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="a868c-200">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="a868c-201">Använd följande kommando för att se till att du använder TLS 1,2:</span><span class="sxs-lookup"><span data-stu-id="a868c-201">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="a868c-202">Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="a868c-202">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

<span data-ttu-id="a868c-203">`Update-Module` körs på PowerShell 3,0 eller senare versioner av PowerShell på Windows 7 eller Windows 2008 R2 och senare versioner av Windows.</span><span class="sxs-lookup"><span data-stu-id="a868c-203">`Update-Module` runs on PowerShell 3.0 or later releases of PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>

<span data-ttu-id="a868c-204">Om den modul som du anger med **namn** parametern inte har installerats med hjälp av `Install-Module` , uppstår ett fel.</span><span class="sxs-lookup"><span data-stu-id="a868c-204">If the module that you specify with the **Name** parameter wasn't installed by using `Install-Module`, an error occurs.</span></span>

<span data-ttu-id="a868c-205">Du kan bara köra `Update-Module` i moduler som du har installerat från Onlinegalleri online genom att köra `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="a868c-205">You can only run `Update-Module` on modules that you installed from the online gallery by running `Install-Module`.</span></span>

<span data-ttu-id="a868c-206">Om `Update-Module` försök att uppdatera binärfiler som används, `Update-Module` returnerar ett fel som identifierar problem processerna.</span><span class="sxs-lookup"><span data-stu-id="a868c-206">If `Update-Module` attempts to update binaries that are in use, `Update-Module` returns an error that identifies the problem processes.</span></span> <span data-ttu-id="a868c-207">Användaren meddelas om att försöka igen `Update-Module` efter att processerna har stoppats.</span><span class="sxs-lookup"><span data-stu-id="a868c-207">The user is informed to retry `Update-Module` after the processes are stopped.</span></span>

## <span data-ttu-id="a868c-208">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="a868c-208">RELATED LINKS</span></span>

[<span data-ttu-id="a868c-209">Sök-modul</span><span class="sxs-lookup"><span data-stu-id="a868c-209">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="a868c-210">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="a868c-210">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="a868c-211">Installera-modul</span><span class="sxs-lookup"><span data-stu-id="a868c-211">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="a868c-212">Publicera-modul</span><span class="sxs-lookup"><span data-stu-id="a868c-212">Publish-Module</span></span>](Publish-Module.md)

[<span data-ttu-id="a868c-213">Avinstallera-modul</span><span class="sxs-lookup"><span data-stu-id="a868c-213">Uninstall-Module</span></span>](Uninstall-Module.md)
