---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-item?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Item
ms.openlocfilehash: 5fbdb8345f0d8a1e83a40dbbad2e26fd89960f1d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263721"
---
# <span data-ttu-id="c8d0c-103">Set-Item</span><span class="sxs-lookup"><span data-stu-id="c8d0c-103">Set-Item</span></span>

## <span data-ttu-id="c8d0c-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="c8d0c-104">SYNOPSIS</span></span>
<span data-ttu-id="c8d0c-105">Ändrar värdet för ett objekt till det värde som anges i kommandot.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-105">Changes the value of an item to the value specified in the command.</span></span>

## <span data-ttu-id="c8d0c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c8d0c-106">SYNTAX</span></span>

### <span data-ttu-id="c8d0c-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="c8d0c-107">Path (Default)</span></span>

```
Set-Item [-Path] <String[]> [[-Value] <Object>] [-Force] [-PassThru] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="c8d0c-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c8d0c-108">LiteralPath</span></span>

```
Set-Item -LiteralPath <String[]> [[-Value] <Object>] [-Force] [-PassThru] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="c8d0c-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="c8d0c-109">DESCRIPTION</span></span>

<span data-ttu-id="c8d0c-110">`Set-Item`Cmdleten ändrar värdet för ett objekt, till exempel en variabel eller register nyckel, till det värde som anges i kommandot.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-110">The `Set-Item` cmdlet changes the value of an item, such as a variable or registry key, to the value specified in the command.</span></span>

## <span data-ttu-id="c8d0c-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="c8d0c-111">EXAMPLES</span></span>

### <span data-ttu-id="c8d0c-112">Exempel 1: skapa ett alias</span><span class="sxs-lookup"><span data-stu-id="c8d0c-112">Example 1: Create an alias</span></span>

<span data-ttu-id="c8d0c-113">Det här kommandot skapar ett alias för NP för anteckningar.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-113">This command creates an alias of np for Notepad.</span></span>

```powershell
Set-Item -Path alias:np -Value "c:\windows\notepad.exe"
```

### <span data-ttu-id="c8d0c-114">Exempel 2: ändra värdet för en miljö variabel</span><span class="sxs-lookup"><span data-stu-id="c8d0c-114">Example 2: Change the value of an environment variable</span></span>

<span data-ttu-id="c8d0c-115">Det här kommandot ändrar värdet för UserRole-miljövariabeln till administratör.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-115">This command changes the value of the UserRole environment variable to Administrator.</span></span>

```powershell
Set-Item -Path env:UserRole -Value "Administrator"
```

### <span data-ttu-id="c8d0c-116">Exempel 3: ändra prompt-funktionen</span><span class="sxs-lookup"><span data-stu-id="c8d0c-116">Example 3: Modify your prompt function</span></span>

<span data-ttu-id="c8d0c-117">Det här kommandot ändrar prompt-funktionen så att den visar tiden före sökvägen.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-117">This command changes the prompt function so that it displays the time before the path.</span></span>

```powershell
Set-Item -Path function:prompt -Value {'PS '+ (Get-Date -Format t) + " " + (Get-Location) + '> '}
```

### <span data-ttu-id="c8d0c-118">Exempel 4: Ange alternativ för din prompt-funktion</span><span class="sxs-lookup"><span data-stu-id="c8d0c-118">Example 4: Set options for your prompt function</span></span>

<span data-ttu-id="c8d0c-119">Det här kommandot anger **AllScope** -och **ReadOnly** -alternativen för prompt-funktionen.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-119">This command sets the **AllScope** and **ReadOnly** options for the prompt function.</span></span>
<span data-ttu-id="c8d0c-120">Det här kommandot använder den dynamiska parametern **alternativ** i `Set-Item` .</span><span class="sxs-lookup"><span data-stu-id="c8d0c-120">This command uses the **Options** dynamic parameter of `Set-Item`.</span></span>
<span data-ttu-id="c8d0c-121">**Alternativ** -parametern är bara tillgänglig `Set-Item` när du använder den med **alias** -eller **funktions** leverantören.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-121">The **Options** parameter is available in `Set-Item` only when you use it with the **Alias** or **Function** provider.</span></span>

```powershell
Set-Item -Path function:prompt -Options "AllScope,ReadOnly"
```

## <span data-ttu-id="c8d0c-122">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="c8d0c-122">PARAMETERS</span></span>

### <span data-ttu-id="c8d0c-123">-Credential</span><span class="sxs-lookup"><span data-stu-id="c8d0c-123">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="c8d0c-124">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-124">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="c8d0c-125">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="c8d0c-125">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c8d0c-126">-Undanta</span><span class="sxs-lookup"><span data-stu-id="c8d0c-126">-Exclude</span></span>

<span data-ttu-id="c8d0c-127">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-127">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="c8d0c-128">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="c8d0c-128">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="c8d0c-129">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="c8d0c-129">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="c8d0c-130">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-130">Wildcard characters are permitted.</span></span> <span data-ttu-id="c8d0c-131">Parametern **exclude** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-131">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="c8d0c-132">-Filter</span><span class="sxs-lookup"><span data-stu-id="c8d0c-132">-Filter</span></span>

<span data-ttu-id="c8d0c-133">Anger ett filter för att kvalificera **Sök vägs** parametern.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-133">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="c8d0c-134">[Fil Systems](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) leverantören är den enda installerade PowerShell-providern som stöder användningen av filter.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-134">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="c8d0c-135">Du kan hitta syntaxen för filter språket för **fil systemet** i [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="c8d0c-135">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="c8d0c-136">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-136">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="c8d0c-137">-Force</span><span class="sxs-lookup"><span data-stu-id="c8d0c-137">-Force</span></span>

<span data-ttu-id="c8d0c-138">Tvingar cmdleten att ange objekt som annars inte kan ändras, till exempel skrivskyddat alias eller variabler.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-138">Forces the cmdlet to set items that cannot otherwise be changed, such as read-only alias or variables.</span></span> <span data-ttu-id="c8d0c-139">Cmdleten kan inte ändra konstanta alias eller variabler.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-139">The cmdlet cannot change constant aliases or variables.</span></span>
<span data-ttu-id="c8d0c-140">Implementeringen varierar från providern till providern.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-140">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="c8d0c-141">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="c8d0c-141">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
<span data-ttu-id="c8d0c-142">Även om du använder *Force* -parametern kan inte cmdlet: en åsidosätta säkerhets begränsningar.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-142">Even using the *Force* parameter, the cmdlet cannot override security restrictions.</span></span>

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

### <span data-ttu-id="c8d0c-143">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="c8d0c-143">-Include</span></span>

<span data-ttu-id="c8d0c-144">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-144">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="c8d0c-145">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="c8d0c-145">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="c8d0c-146">Ange ett Sök vägs element eller ett mönster, till exempel `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="c8d0c-146">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="c8d0c-147">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-147">Wildcard characters are permitted.</span></span> <span data-ttu-id="c8d0c-148">Parametern **include** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-148">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="c8d0c-149">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c8d0c-149">-LiteralPath</span></span>

<span data-ttu-id="c8d0c-150">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-150">Specifies a path to one or more locations.</span></span> <span data-ttu-id="c8d0c-151">Värdet för **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-151">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="c8d0c-152">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-152">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="c8d0c-153">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-153">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="c8d0c-154">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-154">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="c8d0c-155">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="c8d0c-155">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c8d0c-156">– PassThru</span><span class="sxs-lookup"><span data-stu-id="c8d0c-156">-PassThru</span></span>

<span data-ttu-id="c8d0c-157">Skickar ett objekt som representerar objektet till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-157">Passes an object that represents the item to the pipeline.</span></span>
<span data-ttu-id="c8d0c-158">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-158">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="c8d0c-159">-Path</span><span class="sxs-lookup"><span data-stu-id="c8d0c-159">-Path</span></span>

<span data-ttu-id="c8d0c-160">Anger en sökväg till objektets placering.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-160">Specifies a path of the location of the items.</span></span>
<span data-ttu-id="c8d0c-161">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-161">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="c8d0c-162">-Värde</span><span class="sxs-lookup"><span data-stu-id="c8d0c-162">-Value</span></span>

<span data-ttu-id="c8d0c-163">Anger ett nytt värde för objektet.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-163">Specifies a new value for the item.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c8d0c-164">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c8d0c-164">-Confirm</span></span>

<span data-ttu-id="c8d0c-165">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-165">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="c8d0c-166">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c8d0c-166">-WhatIf</span></span>

<span data-ttu-id="c8d0c-167">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-167">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="c8d0c-168">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-168">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="c8d0c-169">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c8d0c-169">CommonParameters</span></span>

<span data-ttu-id="c8d0c-170">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="c8d0c-170">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="c8d0c-171">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="c8d0c-171">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="c8d0c-172">INDATA</span><span class="sxs-lookup"><span data-stu-id="c8d0c-172">INPUTS</span></span>

### <span data-ttu-id="c8d0c-173">System. Object</span><span class="sxs-lookup"><span data-stu-id="c8d0c-173">System.Object</span></span>

<span data-ttu-id="c8d0c-174">Du kan skicka ett objekt som representerar det nya värdet för objektet till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-174">You can pipe an object that represents the new value of the item to this cmdlet.</span></span>

## <span data-ttu-id="c8d0c-175">UTDATA</span><span class="sxs-lookup"><span data-stu-id="c8d0c-175">OUTPUTS</span></span>

### <span data-ttu-id="c8d0c-176">Ingen eller ett objekt som representerar det nya eller ändrade objektet.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-176">None or an object representing the new or changed item.</span></span>

<span data-ttu-id="c8d0c-177">Denna cmdlet genererar ett objekt som representerar objektet, om du anger parametern *Passthru* .</span><span class="sxs-lookup"><span data-stu-id="c8d0c-177">This cmdlet generates an object that represent the item, if you specify the *PassThru* parameter.</span></span>
<span data-ttu-id="c8d0c-178">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-178">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="c8d0c-179">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="c8d0c-179">NOTES</span></span>

- <span data-ttu-id="c8d0c-180">`Set-Item` stöds inte av PowerShell-filsystem-providern.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-180">`Set-Item` is not supported by the PowerShell FileSystem provider.</span></span> <span data-ttu-id="c8d0c-181">Om du vill ändra värdena för objekt i fil systemet använder du `Set-Content` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-181">To change the values of items in the file system, use the `Set-Content` cmdlet.</span></span>
- <span data-ttu-id="c8d0c-182">I register enheterna `HKLM:` och `HKCU:` `Set-Item` ändrar data i (standard) värdet för en register nyckel.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-182">In the Registry drives, `HKLM:` and `HKCU:`, `Set-Item` changes the data in the (Default) value of a registry key.</span></span>
  - <span data-ttu-id="c8d0c-183">Om du vill skapa och ändra namn på register nycklar använder du `New-Item` `Rename-Item` cmdleten och.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-183">To create and change the names of registry keys, use the `New-Item` and `Rename-Item` cmdlet.</span></span>
  - <span data-ttu-id="c8d0c-184">Använd `New-ItemProperty` cmdletarna, och för att ändra namn och data i register värden `Set-ItemProperty` `Rename-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="c8d0c-184">To change the names and data in registry values, use the `New-ItemProperty`, `Set-ItemProperty`, and `Rename-ItemProperty` cmdlets.</span></span>
- <span data-ttu-id="c8d0c-185">`Set-Item` är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="c8d0c-185">`Set-Item` is designed to work with the data exposed by any provider.</span></span>
  <span data-ttu-id="c8d0c-186">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="c8d0c-186">To list the providers available in your session, type `Get-PsProvider`.</span></span>
  <span data-ttu-id="c8d0c-187">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="c8d0c-187">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="c8d0c-188">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="c8d0c-188">RELATED LINKS</span></span>

[<span data-ttu-id="c8d0c-189">Rensa objekt</span><span class="sxs-lookup"><span data-stu-id="c8d0c-189">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="c8d0c-190">Kopiera objekt</span><span class="sxs-lookup"><span data-stu-id="c8d0c-190">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="c8d0c-191">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="c8d0c-191">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="c8d0c-192">Anropa-objekt</span><span class="sxs-lookup"><span data-stu-id="c8d0c-192">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="c8d0c-193">Flytta objekt</span><span class="sxs-lookup"><span data-stu-id="c8d0c-193">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="c8d0c-194">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="c8d0c-194">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="c8d0c-195">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="c8d0c-195">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="c8d0c-196">Byt namn – objekt</span><span class="sxs-lookup"><span data-stu-id="c8d0c-196">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="c8d0c-197">about_Providers</span><span class="sxs-lookup"><span data-stu-id="c8d0c-197">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

