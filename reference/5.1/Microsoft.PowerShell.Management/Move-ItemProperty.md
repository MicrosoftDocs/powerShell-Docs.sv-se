---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/move-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Move-ItemProperty
ms.openlocfilehash: 4cf883964e1ff86487bf5abca8789af62b274c8a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265533"
---
# <span data-ttu-id="a2d0c-103">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a2d0c-103">Move-ItemProperty</span></span>

## <span data-ttu-id="a2d0c-104">Sammanfattning</span><span class="sxs-lookup"><span data-stu-id="a2d0c-104">Synopsis</span></span>
<span data-ttu-id="a2d0c-105">Flyttar en egenskap från en plats till en annan.</span><span class="sxs-lookup"><span data-stu-id="a2d0c-105">Moves a property from one location to another.</span></span>

## <span data-ttu-id="a2d0c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a2d0c-106">SYNTAX</span></span>

### <span data-ttu-id="a2d0c-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="a2d0c-107">Path (Default)</span></span>

```
Move-ItemProperty [-Path] <String[]> [-Name] <String[]> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="a2d0c-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a2d0c-108">LiteralPath</span></span>

```
Move-ItemProperty -LiteralPath <String[]> [-Name] <String[]> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="a2d0c-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a2d0c-109">Description</span></span>

<span data-ttu-id="a2d0c-110">`Move-ItemProperty`Cmdleten flyttar en egenskap för ett objekt från ett objekt till ett annat.</span><span class="sxs-lookup"><span data-stu-id="a2d0c-110">The `Move-ItemProperty` cmdlet moves a property of an item from one item to another item.</span></span>
<span data-ttu-id="a2d0c-111">Till exempel kan den flytta en register post från en register nyckel till en annan register nyckel.</span><span class="sxs-lookup"><span data-stu-id="a2d0c-111">For instance, it can move a registry entry from one registry key to another registry key.</span></span>
<span data-ttu-id="a2d0c-112">När du flyttar en objekt egenskap läggs den till på den nya platsen och tas bort från den ursprungliga platsen.</span><span class="sxs-lookup"><span data-stu-id="a2d0c-112">When you move an item property, it is added to the new location and deleted from its original location.</span></span>

## <span data-ttu-id="a2d0c-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="a2d0c-113">EXAMPLES</span></span>

### <span data-ttu-id="a2d0c-114">Exempel 1: flytta ett register värde och dess data till en annan nyckel</span><span class="sxs-lookup"><span data-stu-id="a2d0c-114">Example 1: Move a registry value and its data to another key</span></span>

<span data-ttu-id="a2d0c-115">Det här kommandot flyttar versionens register värde och dess data från under nyckeln "MyApp" till under nyckeln NewApp i `HKLM\Software\MyCompany` register nyckeln.</span><span class="sxs-lookup"><span data-stu-id="a2d0c-115">This command moves the Version registry value, and its data, from the "MyApp" subkey to the NewApp subkey of the `HKLM\Software\MyCompany` registry key.</span></span>

```powershell
Move-ItemProperty "HKLM:\Software\MyCompany\MyApp" -Name "Version" -Destination "HKLM:\Software\MyCompany\NewApp"
```

## <span data-ttu-id="a2d0c-116">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="a2d0c-116">PARAMETERS</span></span>

### <span data-ttu-id="a2d0c-117">-Credential</span><span class="sxs-lookup"><span data-stu-id="a2d0c-117">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="a2d0c-118">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a2d0c-118">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="a2d0c-119">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="a2d0c-119">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="a2d0c-120">-Mål</span><span class="sxs-lookup"><span data-stu-id="a2d0c-120">-Destination</span></span>

<span data-ttu-id="a2d0c-121">Anger sökvägen till mål platsen.</span><span class="sxs-lookup"><span data-stu-id="a2d0c-121">Specifies the path to the destination location.</span></span>

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

### <span data-ttu-id="a2d0c-122">-Undanta</span><span class="sxs-lookup"><span data-stu-id="a2d0c-122">-Exclude</span></span>

<span data-ttu-id="a2d0c-123">Anger, som en sträng mat ris, en egenskap eller egenskap som denna cmdlet exkluderar från åtgärden.</span><span class="sxs-lookup"><span data-stu-id="a2d0c-123">Specifies, as a string array, a property or property that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="a2d0c-124">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="a2d0c-124">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="a2d0c-125">Ange ett Sök vägs element eller ett mönster, till exempel "\*. txt".</span><span class="sxs-lookup"><span data-stu-id="a2d0c-125">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="a2d0c-126">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="a2d0c-126">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="a2d0c-127">-Filter</span><span class="sxs-lookup"><span data-stu-id="a2d0c-127">-Filter</span></span>

<span data-ttu-id="a2d0c-128">Anger ett filter i formatet eller språket för providern.</span><span class="sxs-lookup"><span data-stu-id="a2d0c-128">Specifies a filter in the format or language of the provider.</span></span>
<span data-ttu-id="a2d0c-129">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="a2d0c-129">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="a2d0c-130">Syntaxen för filtret, inklusive användning av jokertecken, är beroende av providern.</span><span class="sxs-lookup"><span data-stu-id="a2d0c-130">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span>
<span data-ttu-id="a2d0c-131">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="a2d0c-131">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="a2d0c-132">-Force</span><span class="sxs-lookup"><span data-stu-id="a2d0c-132">-Force</span></span>

<span data-ttu-id="a2d0c-133">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="a2d0c-133">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="a2d0c-134">Implementeringen varierar från providern till providern.</span><span class="sxs-lookup"><span data-stu-id="a2d0c-134">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="a2d0c-135">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="a2d0c-135">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="a2d0c-136">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="a2d0c-136">-Include</span></span>

<span data-ttu-id="a2d0c-137">Anger, som en sträng mat ris, en egenskap eller egenskap som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="a2d0c-137">Specifies, as a string array, a property or property that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="a2d0c-138">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="a2d0c-138">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="a2d0c-139">Ange ett Sök vägs element eller ett mönster, till exempel "\*. txt".</span><span class="sxs-lookup"><span data-stu-id="a2d0c-139">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="a2d0c-140">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="a2d0c-140">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="a2d0c-141">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a2d0c-141">-LiteralPath</span></span>

<span data-ttu-id="a2d0c-142">Anger sökvägen till egenskapens aktuella plats.</span><span class="sxs-lookup"><span data-stu-id="a2d0c-142">Specifies the path to the current location of the property.</span></span>
<span data-ttu-id="a2d0c-143">Till skillnad från parametern **Path** används värdet för **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="a2d0c-143">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="a2d0c-144">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="a2d0c-144">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="a2d0c-145">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="a2d0c-145">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="a2d0c-146">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="a2d0c-146">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a2d0c-147">-Name</span><span class="sxs-lookup"><span data-stu-id="a2d0c-147">-Name</span></span>

<span data-ttu-id="a2d0c-148">Anger namnet på den egenskap som ska flyttas.</span><span class="sxs-lookup"><span data-stu-id="a2d0c-148">Specifies the name of the property to be moved.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a2d0c-149">– PassThru</span><span class="sxs-lookup"><span data-stu-id="a2d0c-149">-PassThru</span></span>

<span data-ttu-id="a2d0c-150">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="a2d0c-150">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="a2d0c-151">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="a2d0c-151">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="a2d0c-152">-Path</span><span class="sxs-lookup"><span data-stu-id="a2d0c-152">-Path</span></span>

<span data-ttu-id="a2d0c-153">Anger sökvägen till egenskapens aktuella plats.</span><span class="sxs-lookup"><span data-stu-id="a2d0c-153">Specifies the path to the current location of the property.</span></span>
<span data-ttu-id="a2d0c-154">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="a2d0c-154">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="a2d0c-155">– UseTransaction</span><span class="sxs-lookup"><span data-stu-id="a2d0c-155">-UseTransaction</span></span>

<span data-ttu-id="a2d0c-156">Inkluderar kommandot i den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="a2d0c-156">Includes the command in the active transaction.</span></span>
<span data-ttu-id="a2d0c-157">Den här parametern är bara giltig medan en transaktion pågår.</span><span class="sxs-lookup"><span data-stu-id="a2d0c-157">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="a2d0c-158">Mer information finns i about_Transactions.</span><span class="sxs-lookup"><span data-stu-id="a2d0c-158">For more information, see about_Transactions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a2d0c-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a2d0c-159">-Confirm</span></span>

<span data-ttu-id="a2d0c-160">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a2d0c-160">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a2d0c-161">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a2d0c-161">-WhatIf</span></span>

<span data-ttu-id="a2d0c-162">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="a2d0c-162">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="a2d0c-163">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="a2d0c-163">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a2d0c-164">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a2d0c-164">CommonParameters</span></span>

<span data-ttu-id="a2d0c-165">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="a2d0c-165">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="a2d0c-166">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="a2d0c-166">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="a2d0c-167">INDATA</span><span class="sxs-lookup"><span data-stu-id="a2d0c-167">INPUTS</span></span>

### <span data-ttu-id="a2d0c-168">System. String</span><span class="sxs-lookup"><span data-stu-id="a2d0c-168">System.String</span></span>

<span data-ttu-id="a2d0c-169">Du kan skicka vidare en sträng som innehåller en sökväg till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a2d0c-169">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="a2d0c-170">UTDATA</span><span class="sxs-lookup"><span data-stu-id="a2d0c-170">OUTPUTS</span></span>

### <span data-ttu-id="a2d0c-171">Ingen eller system. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="a2d0c-171">None or System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="a2d0c-172">När du använder parametern **Passthru** genererar den här cmdleten en **PSCustomObject** som representerar den flyttade objekt egenskapen.</span><span class="sxs-lookup"><span data-stu-id="a2d0c-172">When you use the **PassThru** parameter, this cmdlet generates a **PSCustomObject** representing the moved item property.</span></span>
<span data-ttu-id="a2d0c-173">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="a2d0c-173">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="a2d0c-174">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="a2d0c-174">NOTES</span></span>

<span data-ttu-id="a2d0c-175">Denna cmdlet är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="a2d0c-175">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="a2d0c-176">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="a2d0c-176">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="a2d0c-177">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="a2d0c-177">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="a2d0c-178">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="a2d0c-178">RELATED LINKS</span></span>

[<span data-ttu-id="a2d0c-179">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a2d0c-179">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="a2d0c-180">Kopiera – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a2d0c-180">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="a2d0c-181">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a2d0c-181">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="a2d0c-182">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a2d0c-182">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="a2d0c-183">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a2d0c-183">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="a2d0c-184">Byt namn – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a2d0c-184">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="a2d0c-185">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a2d0c-185">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="a2d0c-186">about_Providers</span><span class="sxs-lookup"><span data-stu-id="a2d0c-186">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
