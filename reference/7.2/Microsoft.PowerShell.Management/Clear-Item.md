---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Item
ms.openlocfilehash: fb3f95f51578f9dc02d9f68b3c0be5a6531aca17
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708402"
---
# <span data-ttu-id="20fa3-102">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="20fa3-102">Clear-Item</span></span>

## <span data-ttu-id="20fa3-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="20fa3-103">SYNOPSIS</span></span>
<span data-ttu-id="20fa3-104">Rensar innehållet i ett objekt, men tar inte bort objektet.</span><span class="sxs-lookup"><span data-stu-id="20fa3-104">Clears the contents of an item, but does not delete the item.</span></span>

## <span data-ttu-id="20fa3-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="20fa3-105">SYNTAX</span></span>

### <span data-ttu-id="20fa3-106">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="20fa3-106">Path (Default)</span></span>

```
Clear-Item [-Path] <String[]> [-Force] [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="20fa3-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="20fa3-107">LiteralPath</span></span>

```
Clear-Item -LiteralPath <String[]> [-Force] [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="20fa3-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="20fa3-108">DESCRIPTION</span></span>

<span data-ttu-id="20fa3-109">`Clear-Item`Cmdleten rensar innehållet i ett objekt, men objektet tas inte bort.</span><span class="sxs-lookup"><span data-stu-id="20fa3-109">The `Clear-Item` cmdlet clears the content of an item, but it does not delete the item.</span></span>
<span data-ttu-id="20fa3-110">Till exempel `Clear-Item` kan cmdleten ta bort värdet för en variabel, men den tar inte bort variabeln.</span><span class="sxs-lookup"><span data-stu-id="20fa3-110">For example, the `Clear-Item` cmdlet can delete the value of a variable, but it does not delete the variable.</span></span> <span data-ttu-id="20fa3-111">Värdet som används för att representera ett avmarkerat objekt definieras av varje PowerShell-Provider.</span><span class="sxs-lookup"><span data-stu-id="20fa3-111">The value that used to represent a cleared item is defined by each PowerShell provider.</span></span>
<span data-ttu-id="20fa3-112">Denna cmdlet liknar `Clear-Content` , men den fungerar på alias och variabler i stället för filer.</span><span class="sxs-lookup"><span data-stu-id="20fa3-112">This cmdlet is similar to `Clear-Content`, but it works on aliases and variables, instead of files.</span></span>

## <span data-ttu-id="20fa3-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="20fa3-113">EXAMPLES</span></span>

### <span data-ttu-id="20fa3-114">Exempel 1: ta bort värdet för en variabel</span><span class="sxs-lookup"><span data-stu-id="20fa3-114">Example 1: Clear the value of a variable</span></span>

<span data-ttu-id="20fa3-115">Det här kommandot rensar värdet för variabeln med namnet `TestVar1` .</span><span class="sxs-lookup"><span data-stu-id="20fa3-115">This command clears the value of the variable named `TestVar1`.</span></span>
<span data-ttu-id="20fa3-116">Variabeln är kvar och är giltig, men dess värde är inställt på `$null` .</span><span class="sxs-lookup"><span data-stu-id="20fa3-116">The variable remains and is valid, but its value is set to `$null`.</span></span>
<span data-ttu-id="20fa3-117">Variabel namnet föregås av `Variable:` för att ange PowerShell-variabeln Provider.</span><span class="sxs-lookup"><span data-stu-id="20fa3-117">The variable name is prefixed with `Variable:` to indicate the PowerShell Variable provider.</span></span>

<span data-ttu-id="20fa3-118">De alternativa kommandona visar att du kan få samma resultat genom att växla till PowerShell- `Variable:` enheten och sedan köra `Clear-Item` kommandot.</span><span class="sxs-lookup"><span data-stu-id="20fa3-118">The alternate commands show that, to get the same result, you can switch to the PowerShell `Variable:` drive and then run the `Clear-Item` command.</span></span>

```powershell
Clear-Item Variable:TestVar1
```

```
Set-Location Variable:
PS Variable:\> Clear-Item TestVar1
```

### <span data-ttu-id="20fa3-119">Exempel 2: Rensa alla register poster</span><span class="sxs-lookup"><span data-stu-id="20fa3-119">Example 2: Clear all registry entries</span></span>

<span data-ttu-id="20fa3-120">Det här kommandot rensar alla register poster i "MyKey"-under nyckeln, men endast efter att du har angett att du vill bekräfta din avsikt.</span><span class="sxs-lookup"><span data-stu-id="20fa3-120">This command clears all registry entries in the "MyKey" subkey, but only after prompting you to confirm your intent.</span></span>
<span data-ttu-id="20fa3-121">Den tar inte bort "MyKey"-undernyckeln eller påverkar eventuellt andra register nycklar eller poster.</span><span class="sxs-lookup"><span data-stu-id="20fa3-121">It does not delete the "MyKey" subkey or affect any other registry keys or entries.</span></span>
<span data-ttu-id="20fa3-122">Du kan använda parametrarna **include** och **exclude** för att identifiera särskilda register nycklar, men du kan inte använda dem för att identifiera register poster.</span><span class="sxs-lookup"><span data-stu-id="20fa3-122">You can use the **Include** and **Exclude** parameters to identify particular registry keys, but you cannot use them to identify registry entries.</span></span>

- <span data-ttu-id="20fa3-123">Om du vill ta bort vissa register poster använder du `Remove-ItemProperty` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="20fa3-123">To delete particular registry entries, use the `Remove-ItemProperty` cmdlet.</span></span>
- <span data-ttu-id="20fa3-124">Om du vill ta bort värdet för en register post använder du `Clear-ItemProperty cmdlet` .</span><span class="sxs-lookup"><span data-stu-id="20fa3-124">To delete the value of a registry entry, use the `Clear-ItemProperty cmdlet`.</span></span>

```powershell
Clear-Item HKLM:\Software\MyCompany\MyKey -Confirm
```

## <span data-ttu-id="20fa3-125">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="20fa3-125">PARAMETERS</span></span>

### <span data-ttu-id="20fa3-126">-Credential</span><span class="sxs-lookup"><span data-stu-id="20fa3-126">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="20fa3-127">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="20fa3-127">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="20fa3-128">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="20fa3-128">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="20fa3-129">-Undanta</span><span class="sxs-lookup"><span data-stu-id="20fa3-129">-Exclude</span></span>

<span data-ttu-id="20fa3-130">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="20fa3-130">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="20fa3-131">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="20fa3-131">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="20fa3-132">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="20fa3-132">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="20fa3-133">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="20fa3-133">Wildcard characters are permitted.</span></span> <span data-ttu-id="20fa3-134">Parametern **exclude** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="20fa3-134">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="20fa3-135">-Filter</span><span class="sxs-lookup"><span data-stu-id="20fa3-135">-Filter</span></span>

<span data-ttu-id="20fa3-136">Anger ett filter för att kvalificera **Sök vägs** parametern.</span><span class="sxs-lookup"><span data-stu-id="20fa3-136">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="20fa3-137">[Fil Systems](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) leverantören är den enda installerade PowerShell-providern som stöder användningen av filter.</span><span class="sxs-lookup"><span data-stu-id="20fa3-137">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="20fa3-138">Du kan hitta syntaxen för filter språket för **fil systemet** i [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="20fa3-138">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="20fa3-139">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="20fa3-139">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="20fa3-140">-Force</span><span class="sxs-lookup"><span data-stu-id="20fa3-140">-Force</span></span>

<span data-ttu-id="20fa3-141">Anger att cmdleten rensar objekt som inte kan ändras på annat sätt, t. ex. skrivskyddade alias.</span><span class="sxs-lookup"><span data-stu-id="20fa3-141">Indicates that the cmdlet clears items that cannot otherwise be changed, such as read- only aliases.</span></span>
<span data-ttu-id="20fa3-142">Cmdleten kan inte ta bort konstanter.</span><span class="sxs-lookup"><span data-stu-id="20fa3-142">The cmdlet cannot clear constants.</span></span>
<span data-ttu-id="20fa3-143">Implementeringen varierar från providern till providern.</span><span class="sxs-lookup"><span data-stu-id="20fa3-143">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="20fa3-144">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="20fa3-144">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
<span data-ttu-id="20fa3-145">Cmdleten kan inte åsidosätta säkerhets begränsningar, även om **Force** -parametern används.</span><span class="sxs-lookup"><span data-stu-id="20fa3-145">The cmdlet cannot override security restrictions, even when the **Force** parameter is used.</span></span>

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

### <span data-ttu-id="20fa3-146">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="20fa3-146">-Include</span></span>

<span data-ttu-id="20fa3-147">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="20fa3-147">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="20fa3-148">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="20fa3-148">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="20fa3-149">Ange ett Sök vägs element eller ett mönster, till exempel `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="20fa3-149">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="20fa3-150">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="20fa3-150">Wildcard characters are permitted.</span></span> <span data-ttu-id="20fa3-151">Parametern **include** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="20fa3-151">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="20fa3-152">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="20fa3-152">-LiteralPath</span></span>

<span data-ttu-id="20fa3-153">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="20fa3-153">Specifies a path to one or more locations.</span></span> <span data-ttu-id="20fa3-154">Värdet för **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="20fa3-154">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="20fa3-155">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="20fa3-155">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="20fa3-156">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="20fa3-156">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="20fa3-157">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="20fa3-157">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="20fa3-158">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="20fa3-158">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="20fa3-159">-Path</span><span class="sxs-lookup"><span data-stu-id="20fa3-159">-Path</span></span>

<span data-ttu-id="20fa3-160">Anger sökvägen till objekten som rensas.</span><span class="sxs-lookup"><span data-stu-id="20fa3-160">Specifies the path to the items being cleared.</span></span>
<span data-ttu-id="20fa3-161">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="20fa3-161">Wildcard characters are permitted.</span></span>
<span data-ttu-id="20fa3-162">Den här parametern är obligatorisk, men parameterns namn **Sök väg** är valfri.</span><span class="sxs-lookup"><span data-stu-id="20fa3-162">This parameter is required, but the parameter name **Path** is optional.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="20fa3-163">-Confirm</span><span class="sxs-lookup"><span data-stu-id="20fa3-163">-Confirm</span></span>

<span data-ttu-id="20fa3-164">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="20fa3-164">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="20fa3-165">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="20fa3-165">-WhatIf</span></span>

<span data-ttu-id="20fa3-166">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="20fa3-166">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="20fa3-167">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="20fa3-167">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="20fa3-168">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="20fa3-168">CommonParameters</span></span>

<span data-ttu-id="20fa3-169">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="20fa3-169">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="20fa3-170">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="20fa3-170">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="20fa3-171">INDATA</span><span class="sxs-lookup"><span data-stu-id="20fa3-171">INPUTS</span></span>

### <span data-ttu-id="20fa3-172">System. String</span><span class="sxs-lookup"><span data-stu-id="20fa3-172">System.String</span></span>

<span data-ttu-id="20fa3-173">Du kan skicka en Sök vägs sträng till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="20fa3-173">You can pipe a path string to this cmdlet.</span></span>

## <span data-ttu-id="20fa3-174">UTDATA</span><span class="sxs-lookup"><span data-stu-id="20fa3-174">OUTPUTS</span></span>

### <span data-ttu-id="20fa3-175">Inga</span><span class="sxs-lookup"><span data-stu-id="20fa3-175">None</span></span>

<span data-ttu-id="20fa3-176">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="20fa3-176">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="20fa3-177">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="20fa3-177">NOTES</span></span>

- <span data-ttu-id="20fa3-178">`Clear-Item`Cmdleten stöds bara av flera PowerShell-leverantörer, inklusive **alias**, **miljö**, **funktion**, **register** och **variabel** leverantörer.</span><span class="sxs-lookup"><span data-stu-id="20fa3-178">The `Clear-Item` cmdlet is supported only by several PowerShell providers, including the **Alias**, **Environment**, **Function**, **Registry**, and **Variable** providers.</span></span> <span data-ttu-id="20fa3-179">På så sätt kan du använda `Clear-Item` för att ta bort innehållet i objekt i leverantörens namn områden.</span><span class="sxs-lookup"><span data-stu-id="20fa3-179">As such, you can use `Clear-Item` to delete the content of items in the provider namespaces.</span></span> <span data-ttu-id="20fa3-180">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="20fa3-180">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="20fa3-181">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="20fa3-181">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
- <span data-ttu-id="20fa3-182">Du kan inte använda `Clear-Item` för att ta bort innehållet i en fil eftersom PowerShell-filprovidern inte stöder denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="20fa3-182">You cannot use `Clear-Item` to delete the contents of a file, because the PowerShell FileSystem provider does not support this cmdlet.</span></span> <span data-ttu-id="20fa3-183">Om du vill rensa filer använder du `Clear-Content` .</span><span class="sxs-lookup"><span data-stu-id="20fa3-183">To clear files, use the `Clear-Content`.</span></span>

## <span data-ttu-id="20fa3-184">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="20fa3-184">RELATED LINKS</span></span>

[<span data-ttu-id="20fa3-185">Kopiera objekt</span><span class="sxs-lookup"><span data-stu-id="20fa3-185">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="20fa3-186">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="20fa3-186">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="20fa3-187">Anropa-objekt</span><span class="sxs-lookup"><span data-stu-id="20fa3-187">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="20fa3-188">Flytta objekt</span><span class="sxs-lookup"><span data-stu-id="20fa3-188">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="20fa3-189">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="20fa3-189">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="20fa3-190">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="20fa3-190">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="20fa3-191">Byt namn – objekt</span><span class="sxs-lookup"><span data-stu-id="20fa3-191">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="20fa3-192">Ange objekt</span><span class="sxs-lookup"><span data-stu-id="20fa3-192">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="20fa3-193">about_Providers</span><span class="sxs-lookup"><span data-stu-id="20fa3-193">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

