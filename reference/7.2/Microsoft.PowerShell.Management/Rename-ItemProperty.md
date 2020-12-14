---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-itemproperty?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-ItemProperty
ms.openlocfilehash: 4fbd2677d6a978d4d144effe9607bceb376ad43f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709931"
---
# <span data-ttu-id="0ee2e-102">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="0ee2e-102">Rename-ItemProperty</span></span>

## <span data-ttu-id="0ee2e-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="0ee2e-103">SYNOPSIS</span></span>
<span data-ttu-id="0ee2e-104">Byter namn på en egenskap för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="0ee2e-104">Renames a property of an item.</span></span>

## <span data-ttu-id="0ee2e-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0ee2e-105">SYNTAX</span></span>

### <span data-ttu-id="0ee2e-106">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="0ee2e-106">Path (Default)</span></span>

```
Rename-ItemProperty [-Path] <String> [-Name] <String> [-NewName] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="0ee2e-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="0ee2e-107">LiteralPath</span></span>

```
Rename-ItemProperty -LiteralPath <String> [-Name] <String> [-NewName] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="0ee2e-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="0ee2e-108">DESCRIPTION</span></span>

<span data-ttu-id="0ee2e-109">`Rename-ItemProperty`Cmdleten ändrar namnet på en angiven objekt egenskap.</span><span class="sxs-lookup"><span data-stu-id="0ee2e-109">The `Rename-ItemProperty` cmdlet changes the name of a specified item property.</span></span>
<span data-ttu-id="0ee2e-110">Egenskapens värde har inte ändrats.</span><span class="sxs-lookup"><span data-stu-id="0ee2e-110">The value of the property is not changed.</span></span>
<span data-ttu-id="0ee2e-111">Du kan till exempel använda `Rename-ItemProperty` för att ändra namnet på en register post.</span><span class="sxs-lookup"><span data-stu-id="0ee2e-111">For example, you can use `Rename-ItemProperty` to change the name of a registry entry.</span></span>

## <span data-ttu-id="0ee2e-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="0ee2e-112">EXAMPLES</span></span>

### <span data-ttu-id="0ee2e-113">Exempel 1: Byt namn på en register post</span><span class="sxs-lookup"><span data-stu-id="0ee2e-113">Example 1: Rename a registry entry</span></span>

<span data-ttu-id="0ee2e-114">Detta kommando byter namn på register posten config som finns i `HKEY_LOCAL_MACHINE\Software\SmpApplication` nyckeln till "oldconfig".</span><span class="sxs-lookup"><span data-stu-id="0ee2e-114">This command renames the config registry entry that is contained in the `HKEY_LOCAL_MACHINE\Software\SmpApplication` key to "oldconfig".</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\Software\SmpApplication -Name config -NewName oldconfig
```

## <span data-ttu-id="0ee2e-115">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="0ee2e-115">PARAMETERS</span></span>

### <span data-ttu-id="0ee2e-116">-Credential</span><span class="sxs-lookup"><span data-stu-id="0ee2e-116">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="0ee2e-117">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0ee2e-117">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="0ee2e-118">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="0ee2e-118">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="0ee2e-119">-Undanta</span><span class="sxs-lookup"><span data-stu-id="0ee2e-119">-Exclude</span></span>

<span data-ttu-id="0ee2e-120">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="0ee2e-120">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="0ee2e-121">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="0ee2e-121">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="0ee2e-122">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="0ee2e-122">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="0ee2e-123">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="0ee2e-123">Wildcard characters are permitted.</span></span> <span data-ttu-id="0ee2e-124">Parametern **exclude** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="0ee2e-124">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="0ee2e-125">-Filter</span><span class="sxs-lookup"><span data-stu-id="0ee2e-125">-Filter</span></span>

<span data-ttu-id="0ee2e-126">Anger ett filter för att kvalificera **Sök vägs** parametern.</span><span class="sxs-lookup"><span data-stu-id="0ee2e-126">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="0ee2e-127">[Fil Systems](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) leverantören är den enda installerade PowerShell-providern som stöder användningen av filter.</span><span class="sxs-lookup"><span data-stu-id="0ee2e-127">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="0ee2e-128">Du kan hitta syntaxen för filter språket för **fil systemet** i [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="0ee2e-128">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="0ee2e-129">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="0ee2e-129">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="0ee2e-130">-Force</span><span class="sxs-lookup"><span data-stu-id="0ee2e-130">-Force</span></span>

<span data-ttu-id="0ee2e-131">Tvingar cmdleten att byta namn på en egenskap för ett objekt som annars inte kan kommas åt av användaren.</span><span class="sxs-lookup"><span data-stu-id="0ee2e-131">Forces the cmdlet to rename a property of an object that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="0ee2e-132">Implementeringen varierar från providern till providern.</span><span class="sxs-lookup"><span data-stu-id="0ee2e-132">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="0ee2e-133">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="0ee2e-133">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="0ee2e-134">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="0ee2e-134">-Include</span></span>

<span data-ttu-id="0ee2e-135">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="0ee2e-135">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="0ee2e-136">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="0ee2e-136">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="0ee2e-137">Ange ett Sök vägs element eller ett mönster, till exempel `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="0ee2e-137">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="0ee2e-138">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="0ee2e-138">Wildcard characters are permitted.</span></span> <span data-ttu-id="0ee2e-139">Parametern **include** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="0ee2e-139">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="0ee2e-140">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="0ee2e-140">-LiteralPath</span></span>

<span data-ttu-id="0ee2e-141">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="0ee2e-141">Specifies a path to one or more locations.</span></span> <span data-ttu-id="0ee2e-142">Värdet för **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="0ee2e-142">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="0ee2e-143">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="0ee2e-143">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="0ee2e-144">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="0ee2e-144">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="0ee2e-145">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="0ee2e-145">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="0ee2e-146">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="0ee2e-146">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0ee2e-147">-Name</span><span class="sxs-lookup"><span data-stu-id="0ee2e-147">-Name</span></span>

<span data-ttu-id="0ee2e-148">Anger det aktuella namnet på egenskapen som ska byta namn.</span><span class="sxs-lookup"><span data-stu-id="0ee2e-148">Specifies the current name of the property to rename.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0ee2e-149">-Nyttnamn</span><span class="sxs-lookup"><span data-stu-id="0ee2e-149">-NewName</span></span>

<span data-ttu-id="0ee2e-150">Anger det nya namnet för egenskapen.</span><span class="sxs-lookup"><span data-stu-id="0ee2e-150">Specifies the new name for the property.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0ee2e-151">– PassThru</span><span class="sxs-lookup"><span data-stu-id="0ee2e-151">-PassThru</span></span>

<span data-ttu-id="0ee2e-152">Returnerar ett objekt som representerar egenskapen Item.</span><span class="sxs-lookup"><span data-stu-id="0ee2e-152">Returns an object that represents the item property.</span></span>
<span data-ttu-id="0ee2e-153">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="0ee2e-153">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="0ee2e-154">-Path</span><span class="sxs-lookup"><span data-stu-id="0ee2e-154">-Path</span></span>

<span data-ttu-id="0ee2e-155">Anger sökvägen till det objekt som ska bytas namn på.</span><span class="sxs-lookup"><span data-stu-id="0ee2e-155">Specifies the path of the item to rename.</span></span>
<span data-ttu-id="0ee2e-156">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="0ee2e-156">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="0ee2e-157">-Confirm</span><span class="sxs-lookup"><span data-stu-id="0ee2e-157">-Confirm</span></span>

<span data-ttu-id="0ee2e-158">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="0ee2e-158">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="0ee2e-159">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="0ee2e-159">-WhatIf</span></span>

<span data-ttu-id="0ee2e-160">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="0ee2e-160">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="0ee2e-161">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="0ee2e-161">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="0ee2e-162">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0ee2e-162">CommonParameters</span></span>

<span data-ttu-id="0ee2e-163">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="0ee2e-163">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="0ee2e-164">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="0ee2e-164">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="0ee2e-165">INDATA</span><span class="sxs-lookup"><span data-stu-id="0ee2e-165">INPUTS</span></span>

### <span data-ttu-id="0ee2e-166">System. String</span><span class="sxs-lookup"><span data-stu-id="0ee2e-166">System.String</span></span>

<span data-ttu-id="0ee2e-167">Du kan skicka vidare en sträng som innehåller en sökväg, men inte en literal sökväg, till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0ee2e-167">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="0ee2e-168">UTDATA</span><span class="sxs-lookup"><span data-stu-id="0ee2e-168">OUTPUTS</span></span>

### <span data-ttu-id="0ee2e-169">Ingen, system. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="0ee2e-169">None, System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="0ee2e-170">Den här cmdleten genererar en **PSCustomObject** som representerar egenskapen döpte item, om du anger parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="0ee2e-170">This cmdlet generates a **PSCustomObject** that represents the renamed item property, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="0ee2e-171">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="0ee2e-171">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="0ee2e-172">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="0ee2e-172">NOTES</span></span>

<span data-ttu-id="0ee2e-173">`Remove-ItemProperty` är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="0ee2e-173">`Remove-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="0ee2e-174">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="0ee2e-174">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="0ee2e-175">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="0ee2e-175">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="0ee2e-176">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="0ee2e-176">RELATED LINKS</span></span>

[<span data-ttu-id="0ee2e-177">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="0ee2e-177">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="0ee2e-178">Kopiera – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="0ee2e-178">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="0ee2e-179">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="0ee2e-179">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="0ee2e-180">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="0ee2e-180">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="0ee2e-181">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="0ee2e-181">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="0ee2e-182">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="0ee2e-182">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="0ee2e-183">Byt namn – objekt</span><span class="sxs-lookup"><span data-stu-id="0ee2e-183">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="0ee2e-184">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="0ee2e-184">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="0ee2e-185">about_Providers</span><span class="sxs-lookup"><span data-stu-id="0ee2e-185">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

