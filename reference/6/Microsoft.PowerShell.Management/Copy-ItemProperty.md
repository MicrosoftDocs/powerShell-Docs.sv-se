---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/copy-itemproperty?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Copy-ItemProperty
ms.openlocfilehash: debfe25e8ab977e1f994a94430988254ce5da5d0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264008"
---
# <span data-ttu-id="a5130-103">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a5130-103">Copy-ItemProperty</span></span>

## <span data-ttu-id="a5130-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="a5130-104">SYNOPSIS</span></span>
<span data-ttu-id="a5130-105">Kopierar en egenskap och ett värde från en angiven plats till en annan plats.</span><span class="sxs-lookup"><span data-stu-id="a5130-105">Copies a property and value from a specified location to another location.</span></span>

## <span data-ttu-id="a5130-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a5130-106">SYNTAX</span></span>

### <span data-ttu-id="a5130-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="a5130-107">Path (Default)</span></span>

```
Copy-ItemProperty [-Path] <String[]> [-Name] <String> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a5130-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a5130-108">LiteralPath</span></span>

```
Copy-ItemProperty -LiteralPath <String[]> [-Name] <String> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="a5130-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a5130-109">DESCRIPTION</span></span>

<span data-ttu-id="a5130-110">`Copy-ItemProperty`Cmdleten kopierar en egenskap och ett värde från en angiven plats till en annan plats.</span><span class="sxs-lookup"><span data-stu-id="a5130-110">The `Copy-ItemProperty` cmdlet copies a property and value from a specified location to another location.</span></span>
<span data-ttu-id="a5130-111">Du kan till exempel använda denna cmdlet för att kopiera en eller flera register poster från en register nyckel till en annan register nyckel.</span><span class="sxs-lookup"><span data-stu-id="a5130-111">For instance, you can use this cmdlet to copy one or more registry entries from one registry key to another registry key.</span></span>

## <span data-ttu-id="a5130-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="a5130-112">EXAMPLES</span></span>

### <span data-ttu-id="a5130-113">Exempel 1: kopiera en egenskap från en register nyckel till en annan register nyckel</span><span class="sxs-lookup"><span data-stu-id="a5130-113">Example 1: Copy a property from a registry key to another registry key</span></span>

<span data-ttu-id="a5130-114">Detta kommando kopierar egenskapen "egenskap" från register nyckeln "Mina program" till register nyckeln "MyApplicationRev2".</span><span class="sxs-lookup"><span data-stu-id="a5130-114">This command copies the property named "MyProperty" from the "MyApplication" registry key to the "MyApplicationRev2" registry key.</span></span>

```powershell
Copy-ItemProperty -Path "MyApplication" -Destination "HKLM:\Software\MyApplicationRev2" -Name "MyProperty"
```

## <span data-ttu-id="a5130-115">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="a5130-115">PARAMETERS</span></span>

### <span data-ttu-id="a5130-116">-Credential</span><span class="sxs-lookup"><span data-stu-id="a5130-116">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="a5130-117">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a5130-117">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="a5130-118">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="a5130-118">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="a5130-119">-Mål</span><span class="sxs-lookup"><span data-stu-id="a5130-119">-Destination</span></span>

<span data-ttu-id="a5130-120">Anger sökvägen till mål platsen.</span><span class="sxs-lookup"><span data-stu-id="a5130-120">Specifies the path to the destination location.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a5130-121">-Undanta</span><span class="sxs-lookup"><span data-stu-id="a5130-121">-Exclude</span></span>

<span data-ttu-id="a5130-122">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="a5130-122">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="a5130-123">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="a5130-123">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="a5130-124">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="a5130-124">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="a5130-125">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="a5130-125">Wildcard characters are permitted.</span></span> <span data-ttu-id="a5130-126">Parametern **exclude** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="a5130-126">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="a5130-127">-Filter</span><span class="sxs-lookup"><span data-stu-id="a5130-127">-Filter</span></span>

<span data-ttu-id="a5130-128">Anger ett filter för att kvalificera **Sök vägs** parametern.</span><span class="sxs-lookup"><span data-stu-id="a5130-128">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="a5130-129">[Fil Systems](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) leverantören är den enda installerade PowerShell-providern som stöder användningen av filter.</span><span class="sxs-lookup"><span data-stu-id="a5130-129">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="a5130-130">Du kan hitta syntaxen för filter språket för **fil systemet** i [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="a5130-130">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="a5130-131">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="a5130-131">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="a5130-132">-Force</span><span class="sxs-lookup"><span data-stu-id="a5130-132">-Force</span></span>

<span data-ttu-id="a5130-133">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="a5130-133">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="a5130-134">Implementeringen varierar från providern till providern.</span><span class="sxs-lookup"><span data-stu-id="a5130-134">Implementation varies from provider to provider.</span></span>

<span data-ttu-id="a5130-135">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="a5130-135">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="a5130-136">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="a5130-136">-Include</span></span>

<span data-ttu-id="a5130-137">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="a5130-137">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="a5130-138">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="a5130-138">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="a5130-139">Ange ett Sök vägs element eller ett mönster, till exempel `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="a5130-139">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="a5130-140">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="a5130-140">Wildcard characters are permitted.</span></span> <span data-ttu-id="a5130-141">Parametern **include** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="a5130-141">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="a5130-142">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a5130-142">-LiteralPath</span></span>

<span data-ttu-id="a5130-143">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="a5130-143">Specifies a path to one or more locations.</span></span> <span data-ttu-id="a5130-144">Värdet för **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="a5130-144">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="a5130-145">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="a5130-145">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="a5130-146">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="a5130-146">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="a5130-147">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="a5130-147">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="a5130-148">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="a5130-148">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="a5130-149">-Name</span><span class="sxs-lookup"><span data-stu-id="a5130-149">-Name</span></span>

<span data-ttu-id="a5130-150">Anger namnet på den egenskap som ska kopieras.</span><span class="sxs-lookup"><span data-stu-id="a5130-150">Specifies the name of the property to be copied.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a5130-151">– PassThru</span><span class="sxs-lookup"><span data-stu-id="a5130-151">-PassThru</span></span>

<span data-ttu-id="a5130-152">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="a5130-152">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="a5130-153">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="a5130-153">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="a5130-154">-Path</span><span class="sxs-lookup"><span data-stu-id="a5130-154">-Path</span></span>

<span data-ttu-id="a5130-155">Anger, som en sträng mat ris, sökvägen till den egenskap som ska kopieras.</span><span class="sxs-lookup"><span data-stu-id="a5130-155">Specifies, as a string array, the path to the property to be copied.</span></span>
<span data-ttu-id="a5130-156">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="a5130-156">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="a5130-157">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a5130-157">-Confirm</span></span>

<span data-ttu-id="a5130-158">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a5130-158">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a5130-159">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a5130-159">-WhatIf</span></span>

<span data-ttu-id="a5130-160">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="a5130-160">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="a5130-161">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="a5130-161">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a5130-162">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a5130-162">CommonParameters</span></span>

<span data-ttu-id="a5130-163">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="a5130-163">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="a5130-164">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="a5130-164">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="a5130-165">INDATA</span><span class="sxs-lookup"><span data-stu-id="a5130-165">INPUTS</span></span>

### <span data-ttu-id="a5130-166">System. String</span><span class="sxs-lookup"><span data-stu-id="a5130-166">System.String</span></span>

<span data-ttu-id="a5130-167">Du kan skicka vidare en sträng som innehåller en sökväg till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a5130-167">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="a5130-168">UTDATA</span><span class="sxs-lookup"><span data-stu-id="a5130-168">OUTPUTS</span></span>

### <span data-ttu-id="a5130-169">Ingen eller system. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="a5130-169">None or System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="a5130-170">När du använder parametern **Passthru** genererar denna cmdlet en **PsCustomObject** som representerar egenskapen kopierat objekt.</span><span class="sxs-lookup"><span data-stu-id="a5130-170">When you use the **Passthru** parameter, this cmdlet generates a **PsCustomObject** representing the copied item property.</span></span> <span data-ttu-id="a5130-171">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="a5130-171">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="a5130-172">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="a5130-172">NOTES</span></span>

<span data-ttu-id="a5130-173">Denna cmdlet är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="a5130-173">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="a5130-174">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="a5130-174">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="a5130-175">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="a5130-175">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="a5130-176">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="a5130-176">RELATED LINKS</span></span>

[<span data-ttu-id="a5130-177">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a5130-177">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="a5130-178">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a5130-178">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="a5130-179">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a5130-179">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="a5130-180">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a5130-180">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="a5130-181">Byt namn – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a5130-181">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="a5130-182">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a5130-182">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="a5130-183">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="a5130-183">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="a5130-184">about_Providers</span><span class="sxs-lookup"><span data-stu-id="a5130-184">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
