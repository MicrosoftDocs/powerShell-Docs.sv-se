---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-module?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Module
ms.openlocfilehash: f6be453913c82f7b1aa7fa0f212a39afec6a2f57
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266817"
---
# <span data-ttu-id="d5e3e-103">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="d5e3e-103">Remove-Module</span></span>

## <span data-ttu-id="d5e3e-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="d5e3e-104">SYNOPSIS</span></span>
<span data-ttu-id="d5e3e-105">Tar bort moduler från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="d5e3e-105">Removes modules from the current session.</span></span>

## <span data-ttu-id="d5e3e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d5e3e-106">SYNTAX</span></span>

### <span data-ttu-id="d5e3e-107">name</span><span class="sxs-lookup"><span data-stu-id="d5e3e-107">name</span></span>

```
Remove-Module [-Name] <String[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d5e3e-108">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="d5e3e-108">FullyQualifiedName</span></span>

```
Remove-Module [-FullyQualifiedName] <ModuleSpecification[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d5e3e-109">ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="d5e3e-109">ModuleInfo</span></span>

```
Remove-Module [-ModuleInfo] <PSModuleInfo[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="d5e3e-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="d5e3e-110">DESCRIPTION</span></span>

<span data-ttu-id="d5e3e-111">Cmdleten **Remove-module** tar bort medlemmarna i en modul, till exempel cmdlets och functions, från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="d5e3e-111">The **Remove-Module** cmdlet removes the members of a module, such as cmdlets and functions, from the current session.</span></span>

<span data-ttu-id="d5e3e-112">Om modulen innehåller en sammansättning (. dll) tas alla medlemmar som implementeras av sammansättningen bort, men sammansättningen tas inte bort från minnet.</span><span class="sxs-lookup"><span data-stu-id="d5e3e-112">If the module includes an assembly (.dll), all members that are implemented by the assembly are removed, but the assembly is not unloaded.</span></span>

<span data-ttu-id="d5e3e-113">Denna cmdlet avinstallerar inte modulen eller tar bort den från datorn.</span><span class="sxs-lookup"><span data-stu-id="d5e3e-113">This cmdlet does not uninstall the module or delete it from the computer.</span></span>
<span data-ttu-id="d5e3e-114">Den påverkar endast den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="d5e3e-114">It affects only the current PowerShell session.</span></span>

## <span data-ttu-id="d5e3e-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="d5e3e-115">EXAMPLES</span></span>

### <span data-ttu-id="d5e3e-116">Exempel 1: ta bort en modul</span><span class="sxs-lookup"><span data-stu-id="d5e3e-116">Example 1: Remove a module</span></span>

```powershell
Remove-Module -Name "BitsTransfer"
```

<span data-ttu-id="d5e3e-117">Det här kommandot tar bort BitsTransfer-modulen från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="d5e3e-117">This command removes the BitsTransfer module from the current session.</span></span>

### <span data-ttu-id="d5e3e-118">Exempel 2: ta bort alla moduler</span><span class="sxs-lookup"><span data-stu-id="d5e3e-118">Example 2: Remove all modules</span></span>

```powershell
Get-Module | Remove-Module
```

<span data-ttu-id="d5e3e-119">Det här kommandot tar bort alla moduler från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="d5e3e-119">This command removes all modules from the current session.</span></span>

### <span data-ttu-id="d5e3e-120">Exempel 3: ta bort moduler med hjälp av pipelinen</span><span class="sxs-lookup"><span data-stu-id="d5e3e-120">Example 3: Remove modules by using the pipeline</span></span>

```powershell
"FileTransfer", "PSDiagnostics" | Remove-Module -Verbose
```

```Output
VERBOSE: Performing operation "Remove-Module" on Target "filetransfer (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\filetransfer\filetransfer.psd1')".
VERBOSE: Performing operation "Remove-Module" on Target "Microsoft.BackgroundIntelligentTransfer.Management (Path: 'C:\Windows\assembly\GAC_MSIL\Microsoft.BackgroundIntelligentTransfer.Management\1.0.0.0__31bf3856ad364e35\Microsoft.BackgroundIntelligentTransfe
r.Management.dll')".
VERBOSE: Performing operation "Remove-Module" on Target "psdiagnostics (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\psdiagnostics\psdiagnostics.psd1')".
VERBOSE: Removing imported function 'Start-Trace'.
VERBOSE: Removing imported function 'Stop-Trace'.
VERBOSE: Removing imported function 'Enable-WSManTrace'.
VERBOSE: Removing imported function 'Disable-WSManTrace'.
VERBOSE: Removing imported function 'Enable-PSWSManCombinedTrace'.
VERBOSE: Removing imported function 'Disable-PSWSManCombinedTrace'.
VERBOSE: Removing imported function 'Set-LogProperties'.
VERBOSE: Removing imported function 'Get-LogProperties'.
VERBOSE: Removing imported function 'Enable-PSTrace'.
VERBOSE: Removing imported function 'Disable-PSTrace'.
VERBOSE: Performing operation "Remove-Module" on Target "PSDiagnostics (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\psdiagnostics\PSDiagnostics.psm1')".
```

<span data-ttu-id="d5e3e-121">Det här kommandot tar bort BitsTransfer-och PSDiagnostics-modulerna från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="d5e3e-121">This command removes the BitsTransfer and PSDiagnostics modules from the current session.</span></span>

<span data-ttu-id="d5e3e-122">Kommandot använder en pipeline-operator (|) för att skicka modulnamnet till **Remove-module**.</span><span class="sxs-lookup"><span data-stu-id="d5e3e-122">The command uses a pipeline operator (|) to send the module names to **Remove-Module**.</span></span>
<span data-ttu-id="d5e3e-123">Den använder den *utförliga* gemensamma parametern för att få detaljerad information om de medlemmar som tas bort.</span><span class="sxs-lookup"><span data-stu-id="d5e3e-123">It uses the *Verbose* common parameter to get detailed information about the members that are removed.</span></span>

<span data-ttu-id="d5e3e-124">*Utförliga* meddelanden visar de objekt som tas bort.</span><span class="sxs-lookup"><span data-stu-id="d5e3e-124">The *Verbose* messages show the items that are removed.</span></span>
<span data-ttu-id="d5e3e-125">Meddelandena skiljer sig eftersom BitsTransfer-modulen innehåller en sammansättning som implementerar dess cmdlets och en kapslad modul med sin egen sammansättning.</span><span class="sxs-lookup"><span data-stu-id="d5e3e-125">The messages differ because the BitsTransfer module includes an assembly that implements its cmdlets and a nested module with its own assembly.</span></span>
<span data-ttu-id="d5e3e-126">Modulen PSDiagnostics innehåller en modulens skript fil (. psm1) som exporterar funktioner.</span><span class="sxs-lookup"><span data-stu-id="d5e3e-126">The PSDiagnostics module includes a module script file (.psm1) that exports functions.</span></span>

### <span data-ttu-id="d5e3e-127">Exempel 4: ta bort en modul med ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="d5e3e-127">Example 4: Remove a module by using ModuleInfo</span></span>

```powershell
$a = Get-Module BitsTransfer
Remove-Module -ModuleInfo $a
```

<span data-ttu-id="d5e3e-128">Det här kommandot använder parametern *ModuleInfo* för att ta bort BitsTransfer-modulen.</span><span class="sxs-lookup"><span data-stu-id="d5e3e-128">This command uses the *ModuleInfo* parameter to remove the BitsTransfer module.</span></span>

## <span data-ttu-id="d5e3e-129">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="d5e3e-129">PARAMETERS</span></span>

### <span data-ttu-id="d5e3e-130">-Force</span><span class="sxs-lookup"><span data-stu-id="d5e3e-130">-Force</span></span>

<span data-ttu-id="d5e3e-131">Anger att den här cmdleten tar bort skrivskyddade moduler.</span><span class="sxs-lookup"><span data-stu-id="d5e3e-131">Indicates that this cmdlet removes read-only modules.</span></span>
<span data-ttu-id="d5e3e-132">Som standard tar **Remove-modulen** bara bort Läs-och skriv moduler.</span><span class="sxs-lookup"><span data-stu-id="d5e3e-132">By default, **Remove-Module** removes only read-write modules.</span></span>

<span data-ttu-id="d5e3e-133">De **skrivskyddade** och **readwrite** -värdena lagras i egenskapen **AccessMode** för en modul.</span><span class="sxs-lookup"><span data-stu-id="d5e3e-133">The **ReadOnly** and **ReadWrite** values are stored in **AccessMode** property of a module.</span></span>

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

### <span data-ttu-id="d5e3e-134">-FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="d5e3e-134">-FullyQualifiedName</span></span>

<span data-ttu-id="d5e3e-135">Anger de fullständigt kvalificerade namnen på de moduler som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="d5e3e-135">Specifies the fully qualified names of modules to remove.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: FullyQualifiedName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d5e3e-136">-ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="d5e3e-136">-ModuleInfo</span></span>

<span data-ttu-id="d5e3e-137">Anger de modul-objekt som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="d5e3e-137">Specifies the module objects to remove.</span></span>
<span data-ttu-id="d5e3e-138">Ange en variabel som innehåller ett modul objekt ( **PSModuleInfo** ) eller ett kommando som hämtar ett modul-objekt, till exempel ett Get-Module-kommando.</span><span class="sxs-lookup"><span data-stu-id="d5e3e-138">Enter a variable that contains a module object ( **PSModuleInfo** ) or a command that gets a module object, such as a Get-Module command.</span></span>
<span data-ttu-id="d5e3e-139">Du kan också ta bort modul objekt för att **ta bort modulen**.</span><span class="sxs-lookup"><span data-stu-id="d5e3e-139">You can also pipe module objects to **Remove-Module**.</span></span>

```yaml
Type: System.Management.Automation.PSModuleInfo[]
Parameter Sets: ModuleInfo
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d5e3e-140">-Name</span><span class="sxs-lookup"><span data-stu-id="d5e3e-140">-Name</span></span>

<span data-ttu-id="d5e3e-141">Anger namnen på de moduler som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="d5e3e-141">Specifies the names of modules to remove.</span></span>
<span data-ttu-id="d5e3e-142">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="d5e3e-142">Wildcard characters are permitted.</span></span>
<span data-ttu-id="d5e3e-143">Du kan också ta bort namn strängar för att **ta bort modulen**.</span><span class="sxs-lookup"><span data-stu-id="d5e3e-143">You can also pipe name strings to **Remove-Module**.</span></span>

```yaml
Type: System.String[]
Parameter Sets: name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="d5e3e-144">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d5e3e-144">-Confirm</span></span>

<span data-ttu-id="d5e3e-145">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="d5e3e-145">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="d5e3e-146">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d5e3e-146">-WhatIf</span></span>

<span data-ttu-id="d5e3e-147">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="d5e3e-147">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="d5e3e-148">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="d5e3e-148">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="d5e3e-149">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d5e3e-149">CommonParameters</span></span>

<span data-ttu-id="d5e3e-150">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d5e3e-150">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d5e3e-151">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d5e3e-151">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d5e3e-152">INDATA</span><span class="sxs-lookup"><span data-stu-id="d5e3e-152">INPUTS</span></span>

### <span data-ttu-id="d5e3e-153">System. String, system. Management. Automation. PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="d5e3e-153">System.String, System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="d5e3e-154">Du kan ta bort modul namn och modul-objekt för att **ta bort modulen**.</span><span class="sxs-lookup"><span data-stu-id="d5e3e-154">You can pipe module names and module objects to **Remove-Module**.</span></span>

## <span data-ttu-id="d5e3e-155">UTDATA</span><span class="sxs-lookup"><span data-stu-id="d5e3e-155">OUTPUTS</span></span>

### <span data-ttu-id="d5e3e-156">Inget</span><span class="sxs-lookup"><span data-stu-id="d5e3e-156">None</span></span>

<span data-ttu-id="d5e3e-157">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="d5e3e-157">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="d5e3e-158">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="d5e3e-158">NOTES</span></span>

<span data-ttu-id="d5e3e-159">När du tar bort en modul finns det en händelse för den modul som ska köras.</span><span class="sxs-lookup"><span data-stu-id="d5e3e-159">When removing a module, there is an event on the module that will execute.</span></span>
<span data-ttu-id="d5e3e-160">Den här händelsen gör att en modul kan reagera på att tas bort och utföra en del rensning, till exempel för att frigöra resurser.</span><span class="sxs-lookup"><span data-stu-id="d5e3e-160">This event allows a module to react to being removed and perform some cleanup such as freeing up resources.</span></span> <span data-ttu-id="d5e3e-161">Exempel:</span><span class="sxs-lookup"><span data-stu-id="d5e3e-161">Example:</span></span>

<span data-ttu-id="d5e3e-162">$OnRemoveScript = {</span><span class="sxs-lookup"><span data-stu-id="d5e3e-162">$OnRemoveScript = {</span></span>

  <span data-ttu-id="d5e3e-163">\# utför rensning</span><span class="sxs-lookup"><span data-stu-id="d5e3e-163">\# perform cleanup</span></span>

  <span data-ttu-id="d5e3e-164">$cachedSessions | Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="d5e3e-164">$cachedSessions | Remove-PSSession</span></span>

<span data-ttu-id="d5e3e-165">}</span><span class="sxs-lookup"><span data-stu-id="d5e3e-165">}</span></span>

<span data-ttu-id="d5e3e-166">$ExecutionContext. SessionState. module. OnRemove + = $OnRemoveScript</span><span class="sxs-lookup"><span data-stu-id="d5e3e-166">$ExecutionContext.SessionState.Module.OnRemove += $OnRemoveScript</span></span>

<span data-ttu-id="d5e3e-167">För fullständig konsekvens kan det också vara användbart att reagera på stängningen av PowerShell-processen:</span><span class="sxs-lookup"><span data-stu-id="d5e3e-167">For full consistency, it might be also useful to react to the closing of the PowerShell process:</span></span>

<span data-ttu-id="d5e3e-168">Register-EngineEvent-SourceIdentifier ([system. Management. Automation. PsEngineEvent]:: avslutar)-åtgärd $OnRemoveScript</span><span class="sxs-lookup"><span data-stu-id="d5e3e-168">Register-EngineEvent -SourceIdentifier ([System.Management.Automation.PsEngineEvent]::Exiting) -Action $OnRemoveScript</span></span>

## <span data-ttu-id="d5e3e-169">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="d5e3e-169">RELATED LINKS</span></span>

[<span data-ttu-id="d5e3e-170">Hämta modul</span><span class="sxs-lookup"><span data-stu-id="d5e3e-170">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="d5e3e-171">Importera-modul</span><span class="sxs-lookup"><span data-stu-id="d5e3e-171">Import-Module</span></span>](Import-Module.md)
