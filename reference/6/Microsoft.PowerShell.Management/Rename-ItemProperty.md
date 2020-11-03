---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-itemproperty?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-ItemProperty
ms.openlocfilehash: 3768a24438b0cc33711ebe61dc63c57c27bac976
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263823"
---
# <span data-ttu-id="41f52-103">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="41f52-103">Rename-ItemProperty</span></span>

## <span data-ttu-id="41f52-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="41f52-104">SYNOPSIS</span></span>
<span data-ttu-id="41f52-105">Byter namn på en egenskap för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="41f52-105">Renames a property of an item.</span></span>

## <span data-ttu-id="41f52-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="41f52-106">SYNTAX</span></span>

### <span data-ttu-id="41f52-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="41f52-107">Path (Default)</span></span>

```
Rename-ItemProperty [-Path] <String> [-Name] <String> [-NewName] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="41f52-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="41f52-108">LiteralPath</span></span>

```
Rename-ItemProperty -LiteralPath <String> [-Name] <String> [-NewName] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="41f52-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="41f52-109">DESCRIPTION</span></span>

<span data-ttu-id="41f52-110">`Rename-ItemProperty`Cmdleten ändrar namnet på en angiven objekt egenskap.</span><span class="sxs-lookup"><span data-stu-id="41f52-110">The `Rename-ItemProperty` cmdlet changes the name of a specified item property.</span></span>
<span data-ttu-id="41f52-111">Egenskapens värde har inte ändrats.</span><span class="sxs-lookup"><span data-stu-id="41f52-111">The value of the property is not changed.</span></span>
<span data-ttu-id="41f52-112">Du kan till exempel använda `Rename-ItemProperty` för att ändra namnet på en register post.</span><span class="sxs-lookup"><span data-stu-id="41f52-112">For example, you can use `Rename-ItemProperty` to change the name of a registry entry.</span></span>

## <span data-ttu-id="41f52-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="41f52-113">EXAMPLES</span></span>

### <span data-ttu-id="41f52-114">Exempel 1: Byt namn på en register post</span><span class="sxs-lookup"><span data-stu-id="41f52-114">Example 1: Rename a registry entry</span></span>

<span data-ttu-id="41f52-115">Detta kommando byter namn på register posten config som finns i `HKEY_LOCAL_MACHINE\Software\SmpApplication` nyckeln till "oldconfig".</span><span class="sxs-lookup"><span data-stu-id="41f52-115">This command renames the config registry entry that is contained in the `HKEY_LOCAL_MACHINE\Software\SmpApplication` key to "oldconfig".</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\Software\SmpApplication -Name config -NewName oldconfig
```

## <span data-ttu-id="41f52-116">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="41f52-116">PARAMETERS</span></span>

### <span data-ttu-id="41f52-117">-Credential</span><span class="sxs-lookup"><span data-stu-id="41f52-117">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="41f52-118">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="41f52-118">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="41f52-119">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="41f52-119">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="41f52-120">-Undanta</span><span class="sxs-lookup"><span data-stu-id="41f52-120">-Exclude</span></span>

<span data-ttu-id="41f52-121">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="41f52-121">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="41f52-122">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="41f52-122">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="41f52-123">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="41f52-123">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="41f52-124">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="41f52-124">Wildcard characters are permitted.</span></span> <span data-ttu-id="41f52-125">Parametern **exclude** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="41f52-125">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="41f52-126">-Filter</span><span class="sxs-lookup"><span data-stu-id="41f52-126">-Filter</span></span>

<span data-ttu-id="41f52-127">Anger ett filter för att kvalificera **Sök vägs** parametern.</span><span class="sxs-lookup"><span data-stu-id="41f52-127">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="41f52-128">[Fil Systems](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) leverantören är den enda installerade PowerShell-providern som stöder användningen av filter.</span><span class="sxs-lookup"><span data-stu-id="41f52-128">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="41f52-129">Du kan hitta syntaxen för filter språket för **fil systemet** i [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="41f52-129">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="41f52-130">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="41f52-130">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="41f52-131">-Force</span><span class="sxs-lookup"><span data-stu-id="41f52-131">-Force</span></span>

<span data-ttu-id="41f52-132">Tvingar cmdleten att byta namn på en egenskap för ett objekt som annars inte kan kommas åt av användaren.</span><span class="sxs-lookup"><span data-stu-id="41f52-132">Forces the cmdlet to rename a property of an object that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="41f52-133">Implementeringen varierar från providern till providern.</span><span class="sxs-lookup"><span data-stu-id="41f52-133">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="41f52-134">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="41f52-134">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="41f52-135">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="41f52-135">-Include</span></span>

<span data-ttu-id="41f52-136">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="41f52-136">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="41f52-137">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="41f52-137">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="41f52-138">Ange ett Sök vägs element eller ett mönster, till exempel `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="41f52-138">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="41f52-139">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="41f52-139">Wildcard characters are permitted.</span></span> <span data-ttu-id="41f52-140">Parametern **include** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="41f52-140">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="41f52-141">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="41f52-141">-LiteralPath</span></span>

<span data-ttu-id="41f52-142">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="41f52-142">Specifies a path to one or more locations.</span></span> <span data-ttu-id="41f52-143">Värdet för **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="41f52-143">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="41f52-144">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="41f52-144">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="41f52-145">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="41f52-145">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="41f52-146">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="41f52-146">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="41f52-147">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="41f52-147">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="41f52-148">-Name</span><span class="sxs-lookup"><span data-stu-id="41f52-148">-Name</span></span>

<span data-ttu-id="41f52-149">Anger det aktuella namnet på egenskapen som ska byta namn.</span><span class="sxs-lookup"><span data-stu-id="41f52-149">Specifies the current name of the property to rename.</span></span>

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

### <span data-ttu-id="41f52-150">-Nyttnamn</span><span class="sxs-lookup"><span data-stu-id="41f52-150">-NewName</span></span>

<span data-ttu-id="41f52-151">Anger det nya namnet för egenskapen.</span><span class="sxs-lookup"><span data-stu-id="41f52-151">Specifies the new name for the property.</span></span>

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

### <span data-ttu-id="41f52-152">– PassThru</span><span class="sxs-lookup"><span data-stu-id="41f52-152">-PassThru</span></span>

<span data-ttu-id="41f52-153">Returnerar ett objekt som representerar egenskapen Item.</span><span class="sxs-lookup"><span data-stu-id="41f52-153">Returns an object that represents the item property.</span></span>
<span data-ttu-id="41f52-154">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="41f52-154">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="41f52-155">-Path</span><span class="sxs-lookup"><span data-stu-id="41f52-155">-Path</span></span>

<span data-ttu-id="41f52-156">Anger sökvägen till det objekt som ska bytas namn på.</span><span class="sxs-lookup"><span data-stu-id="41f52-156">Specifies the path of the item to rename.</span></span>
<span data-ttu-id="41f52-157">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="41f52-157">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="41f52-158">-Confirm</span><span class="sxs-lookup"><span data-stu-id="41f52-158">-Confirm</span></span>

<span data-ttu-id="41f52-159">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="41f52-159">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="41f52-160">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="41f52-160">-WhatIf</span></span>

<span data-ttu-id="41f52-161">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="41f52-161">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="41f52-162">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="41f52-162">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="41f52-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="41f52-163">CommonParameters</span></span>

<span data-ttu-id="41f52-164">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="41f52-164">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="41f52-165">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="41f52-165">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="41f52-166">INDATA</span><span class="sxs-lookup"><span data-stu-id="41f52-166">INPUTS</span></span>

### <span data-ttu-id="41f52-167">System. String</span><span class="sxs-lookup"><span data-stu-id="41f52-167">System.String</span></span>

<span data-ttu-id="41f52-168">Du kan skicka vidare en sträng som innehåller en sökväg, men inte en literal sökväg, till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="41f52-168">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="41f52-169">UTDATA</span><span class="sxs-lookup"><span data-stu-id="41f52-169">OUTPUTS</span></span>

### <span data-ttu-id="41f52-170">Ingen, system. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="41f52-170">None, System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="41f52-171">Den här cmdleten genererar en **PSCustomObject** som representerar egenskapen döpte item, om du anger parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="41f52-171">This cmdlet generates a **PSCustomObject** that represents the renamed item property, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="41f52-172">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="41f52-172">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="41f52-173">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="41f52-173">NOTES</span></span>

<span data-ttu-id="41f52-174">`Remove-ItemProperty` är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="41f52-174">`Remove-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="41f52-175">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="41f52-175">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="41f52-176">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="41f52-176">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="41f52-177">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="41f52-177">RELATED LINKS</span></span>

[<span data-ttu-id="41f52-178">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="41f52-178">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="41f52-179">Kopiera – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="41f52-179">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="41f52-180">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="41f52-180">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="41f52-181">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="41f52-181">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="41f52-182">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="41f52-182">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="41f52-183">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="41f52-183">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="41f52-184">Byt namn – objekt</span><span class="sxs-lookup"><span data-stu-id="41f52-184">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="41f52-185">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="41f52-185">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="41f52-186">about_Providers</span><span class="sxs-lookup"><span data-stu-id="41f52-186">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
