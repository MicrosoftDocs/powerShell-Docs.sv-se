---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/copy-itemproperty?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Copy-ItemProperty
ms.openlocfilehash: d6dd6d21d7c0022e8ca1ea7dbd8e1cab8a680de6
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709540"
---
# <span data-ttu-id="cdee9-102">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="cdee9-102">Copy-ItemProperty</span></span>

## <span data-ttu-id="cdee9-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="cdee9-103">SYNOPSIS</span></span>
<span data-ttu-id="cdee9-104">Kopierar en egenskap och ett värde från en angiven plats till en annan plats.</span><span class="sxs-lookup"><span data-stu-id="cdee9-104">Copies a property and value from a specified location to another location.</span></span>

## <span data-ttu-id="cdee9-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cdee9-105">SYNTAX</span></span>

### <span data-ttu-id="cdee9-106">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="cdee9-106">Path (Default)</span></span>

```
Copy-ItemProperty [-Path] <String[]> [-Name] <String> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="cdee9-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="cdee9-107">LiteralPath</span></span>

```
Copy-ItemProperty -LiteralPath <String[]> [-Name] <String> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="cdee9-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="cdee9-108">DESCRIPTION</span></span>

<span data-ttu-id="cdee9-109">`Copy-ItemProperty`Cmdleten kopierar en egenskap och ett värde från en angiven plats till en annan plats.</span><span class="sxs-lookup"><span data-stu-id="cdee9-109">The `Copy-ItemProperty` cmdlet copies a property and value from a specified location to another location.</span></span>
<span data-ttu-id="cdee9-110">Du kan till exempel använda denna cmdlet för att kopiera en eller flera register poster från en register nyckel till en annan register nyckel.</span><span class="sxs-lookup"><span data-stu-id="cdee9-110">For instance, you can use this cmdlet to copy one or more registry entries from one registry key to another registry key.</span></span>

## <span data-ttu-id="cdee9-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="cdee9-111">EXAMPLES</span></span>

### <span data-ttu-id="cdee9-112">Exempel 1: kopiera en egenskap från en register nyckel till en annan register nyckel</span><span class="sxs-lookup"><span data-stu-id="cdee9-112">Example 1: Copy a property from a registry key to another registry key</span></span>

<span data-ttu-id="cdee9-113">Detta kommando kopierar egenskapen "egenskap" från register nyckeln "Mina program" till register nyckeln "MyApplicationRev2".</span><span class="sxs-lookup"><span data-stu-id="cdee9-113">This command copies the property named "MyProperty" from the "MyApplication" registry key to the "MyApplicationRev2" registry key.</span></span>

```powershell
Copy-ItemProperty -Path "MyApplication" -Destination "HKLM:\Software\MyApplicationRev2" -Name "MyProperty"
```

## <span data-ttu-id="cdee9-114">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="cdee9-114">PARAMETERS</span></span>

### <span data-ttu-id="cdee9-115">-Credential</span><span class="sxs-lookup"><span data-stu-id="cdee9-115">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="cdee9-116">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cdee9-116">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="cdee9-117">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="cdee9-117">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="cdee9-118">-Mål</span><span class="sxs-lookup"><span data-stu-id="cdee9-118">-Destination</span></span>

<span data-ttu-id="cdee9-119">Anger sökvägen till mål platsen.</span><span class="sxs-lookup"><span data-stu-id="cdee9-119">Specifies the path to the destination location.</span></span>

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

### <span data-ttu-id="cdee9-120">-Undanta</span><span class="sxs-lookup"><span data-stu-id="cdee9-120">-Exclude</span></span>

<span data-ttu-id="cdee9-121">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="cdee9-121">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="cdee9-122">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="cdee9-122">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="cdee9-123">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="cdee9-123">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="cdee9-124">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="cdee9-124">Wildcard characters are permitted.</span></span> <span data-ttu-id="cdee9-125">Parametern **exclude** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="cdee9-125">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="cdee9-126">-Filter</span><span class="sxs-lookup"><span data-stu-id="cdee9-126">-Filter</span></span>

<span data-ttu-id="cdee9-127">Anger ett filter för att kvalificera **Sök vägs** parametern.</span><span class="sxs-lookup"><span data-stu-id="cdee9-127">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="cdee9-128">[Fil Systems](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) leverantören är den enda installerade PowerShell-providern som stöder användningen av filter.</span><span class="sxs-lookup"><span data-stu-id="cdee9-128">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="cdee9-129">Du kan hitta syntaxen för filter språket för **fil systemet** i [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="cdee9-129">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="cdee9-130">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="cdee9-130">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="cdee9-131">-Force</span><span class="sxs-lookup"><span data-stu-id="cdee9-131">-Force</span></span>

<span data-ttu-id="cdee9-132">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="cdee9-132">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="cdee9-133">Implementeringen varierar från providern till providern.</span><span class="sxs-lookup"><span data-stu-id="cdee9-133">Implementation varies from provider to provider.</span></span>

<span data-ttu-id="cdee9-134">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="cdee9-134">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="cdee9-135">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="cdee9-135">-Include</span></span>

<span data-ttu-id="cdee9-136">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="cdee9-136">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="cdee9-137">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="cdee9-137">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="cdee9-138">Ange ett Sök vägs element eller ett mönster, till exempel `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="cdee9-138">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="cdee9-139">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="cdee9-139">Wildcard characters are permitted.</span></span> <span data-ttu-id="cdee9-140">Parametern **include** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="cdee9-140">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="cdee9-141">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="cdee9-141">-LiteralPath</span></span>

<span data-ttu-id="cdee9-142">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="cdee9-142">Specifies a path to one or more locations.</span></span> <span data-ttu-id="cdee9-143">Värdet för **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="cdee9-143">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="cdee9-144">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="cdee9-144">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="cdee9-145">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="cdee9-145">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="cdee9-146">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="cdee9-146">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="cdee9-147">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="cdee9-147">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="cdee9-148">-Name</span><span class="sxs-lookup"><span data-stu-id="cdee9-148">-Name</span></span>

<span data-ttu-id="cdee9-149">Anger namnet på den egenskap som ska kopieras.</span><span class="sxs-lookup"><span data-stu-id="cdee9-149">Specifies the name of the property to be copied.</span></span>

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

### <span data-ttu-id="cdee9-150">– PassThru</span><span class="sxs-lookup"><span data-stu-id="cdee9-150">-PassThru</span></span>

<span data-ttu-id="cdee9-151">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="cdee9-151">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="cdee9-152">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="cdee9-152">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="cdee9-153">-Path</span><span class="sxs-lookup"><span data-stu-id="cdee9-153">-Path</span></span>

<span data-ttu-id="cdee9-154">Anger, som en sträng mat ris, sökvägen till den egenskap som ska kopieras.</span><span class="sxs-lookup"><span data-stu-id="cdee9-154">Specifies, as a string array, the path to the property to be copied.</span></span>
<span data-ttu-id="cdee9-155">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="cdee9-155">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="cdee9-156">-Confirm</span><span class="sxs-lookup"><span data-stu-id="cdee9-156">-Confirm</span></span>

<span data-ttu-id="cdee9-157">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="cdee9-157">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="cdee9-158">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="cdee9-158">-WhatIf</span></span>

<span data-ttu-id="cdee9-159">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="cdee9-159">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="cdee9-160">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="cdee9-160">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="cdee9-161">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cdee9-161">CommonParameters</span></span>

<span data-ttu-id="cdee9-162">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="cdee9-162">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="cdee9-163">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="cdee9-163">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="cdee9-164">INDATA</span><span class="sxs-lookup"><span data-stu-id="cdee9-164">INPUTS</span></span>

### <span data-ttu-id="cdee9-165">System. String</span><span class="sxs-lookup"><span data-stu-id="cdee9-165">System.String</span></span>

<span data-ttu-id="cdee9-166">Du kan skicka vidare en sträng som innehåller en sökväg till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cdee9-166">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="cdee9-167">UTDATA</span><span class="sxs-lookup"><span data-stu-id="cdee9-167">OUTPUTS</span></span>

### <span data-ttu-id="cdee9-168">Ingen eller system. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="cdee9-168">None or System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="cdee9-169">När du använder parametern **Passthru** genererar denna cmdlet en **PsCustomObject** som representerar egenskapen kopierat objekt.</span><span class="sxs-lookup"><span data-stu-id="cdee9-169">When you use the **Passthru** parameter, this cmdlet generates a **PsCustomObject** representing the copied item property.</span></span> <span data-ttu-id="cdee9-170">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="cdee9-170">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="cdee9-171">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="cdee9-171">NOTES</span></span>

<span data-ttu-id="cdee9-172">Denna cmdlet är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="cdee9-172">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="cdee9-173">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="cdee9-173">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="cdee9-174">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="cdee9-174">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="cdee9-175">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="cdee9-175">RELATED LINKS</span></span>

[<span data-ttu-id="cdee9-176">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="cdee9-176">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="cdee9-177">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="cdee9-177">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="cdee9-178">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="cdee9-178">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="cdee9-179">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="cdee9-179">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="cdee9-180">Byt namn – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="cdee9-180">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="cdee9-181">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="cdee9-181">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="cdee9-182">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="cdee9-182">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="cdee9-183">about_Providers</span><span class="sxs-lookup"><span data-stu-id="cdee9-183">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

