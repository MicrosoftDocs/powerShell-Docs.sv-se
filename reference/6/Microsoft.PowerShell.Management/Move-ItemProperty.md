---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/move-itemproperty?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Move-ItemProperty
ms.openlocfilehash: 235991da33ae49f8d1dd9b379432963a8930ebc0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264465"
---
# <span data-ttu-id="985b4-103">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="985b4-103">Move-ItemProperty</span></span>

## <span data-ttu-id="985b4-104">Sammanfattning</span><span class="sxs-lookup"><span data-stu-id="985b4-104">Synopsis</span></span>
<span data-ttu-id="985b4-105">Flyttar en egenskap från en plats till en annan.</span><span class="sxs-lookup"><span data-stu-id="985b4-105">Moves a property from one location to another.</span></span>

## <span data-ttu-id="985b4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="985b4-106">SYNTAX</span></span>

### <span data-ttu-id="985b4-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="985b4-107">Path (Default)</span></span>

```
Move-ItemProperty [-Path] <String[]> [-Name] <String[]> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="985b4-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="985b4-108">LiteralPath</span></span>

```
Move-ItemProperty -LiteralPath <String[]> [-Name] <String[]> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="985b4-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="985b4-109">Description</span></span>

<span data-ttu-id="985b4-110">`Move-ItemProperty`Cmdleten flyttar en egenskap för ett objekt från ett objekt till ett annat.</span><span class="sxs-lookup"><span data-stu-id="985b4-110">The `Move-ItemProperty` cmdlet moves a property of an item from one item to another item.</span></span>
<span data-ttu-id="985b4-111">Till exempel kan den flytta en register post från en register nyckel till en annan register nyckel.</span><span class="sxs-lookup"><span data-stu-id="985b4-111">For instance, it can move a registry entry from one registry key to another registry key.</span></span>
<span data-ttu-id="985b4-112">När du flyttar en objekt egenskap läggs den till på den nya platsen och tas bort från den ursprungliga platsen.</span><span class="sxs-lookup"><span data-stu-id="985b4-112">When you move an item property, it is added to the new location and deleted from its original location.</span></span>

## <span data-ttu-id="985b4-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="985b4-113">EXAMPLES</span></span>

### <span data-ttu-id="985b4-114">Exempel 1: flytta ett register värde och dess data till en annan nyckel</span><span class="sxs-lookup"><span data-stu-id="985b4-114">Example 1: Move a registry value and its data to another key</span></span>

<span data-ttu-id="985b4-115">Det här kommandot flyttar versionens register värde och dess data från under nyckeln "MyApp" till under nyckeln NewApp i `HKLM\Software\MyCompany` register nyckeln.</span><span class="sxs-lookup"><span data-stu-id="985b4-115">This command moves the Version registry value, and its data, from the "MyApp" subkey to the NewApp subkey of the `HKLM\Software\MyCompany` registry key.</span></span>

```powershell
Move-ItemProperty "HKLM:\Software\MyCompany\MyApp" -Name "Version" -Destination "HKLM:\Software\MyCompany\NewApp"
```

## <span data-ttu-id="985b4-116">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="985b4-116">PARAMETERS</span></span>

### <span data-ttu-id="985b4-117">-Credential</span><span class="sxs-lookup"><span data-stu-id="985b4-117">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="985b4-118">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="985b4-118">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="985b4-119">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="985b4-119">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="985b4-120">-Mål</span><span class="sxs-lookup"><span data-stu-id="985b4-120">-Destination</span></span>

<span data-ttu-id="985b4-121">Anger sökvägen till mål platsen.</span><span class="sxs-lookup"><span data-stu-id="985b4-121">Specifies the path to the destination location.</span></span>

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

### <span data-ttu-id="985b4-122">-Undanta</span><span class="sxs-lookup"><span data-stu-id="985b4-122">-Exclude</span></span>

<span data-ttu-id="985b4-123">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="985b4-123">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="985b4-124">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="985b4-124">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="985b4-125">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="985b4-125">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="985b4-126">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="985b4-126">Wildcard characters are permitted.</span></span> <span data-ttu-id="985b4-127">Parametern **exclude** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="985b4-127">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="985b4-128">-Filter</span><span class="sxs-lookup"><span data-stu-id="985b4-128">-Filter</span></span>

<span data-ttu-id="985b4-129">Anger ett filter för att kvalificera **Sök vägs** parametern.</span><span class="sxs-lookup"><span data-stu-id="985b4-129">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="985b4-130">[Fil Systems](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) leverantören är den enda installerade PowerShell-providern som stöder användningen av filter.</span><span class="sxs-lookup"><span data-stu-id="985b4-130">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="985b4-131">Du kan hitta syntaxen för filter språket för **fil systemet** i [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="985b4-131">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="985b4-132">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="985b4-132">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="985b4-133">-Force</span><span class="sxs-lookup"><span data-stu-id="985b4-133">-Force</span></span>

<span data-ttu-id="985b4-134">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="985b4-134">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="985b4-135">Implementeringen varierar från providern till providern.</span><span class="sxs-lookup"><span data-stu-id="985b4-135">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="985b4-136">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="985b4-136">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="985b4-137">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="985b4-137">-Include</span></span>

<span data-ttu-id="985b4-138">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="985b4-138">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="985b4-139">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="985b4-139">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="985b4-140">Ange ett Sök vägs element eller ett mönster, till exempel `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="985b4-140">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="985b4-141">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="985b4-141">Wildcard characters are permitted.</span></span> <span data-ttu-id="985b4-142">Parametern **include** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="985b4-142">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="985b4-143">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="985b4-143">-LiteralPath</span></span>

<span data-ttu-id="985b4-144">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="985b4-144">Specifies a path to one or more locations.</span></span> <span data-ttu-id="985b4-145">Värdet för **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="985b4-145">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="985b4-146">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="985b4-146">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="985b4-147">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="985b4-147">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="985b4-148">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="985b4-148">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="985b4-149">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="985b4-149">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="985b4-150">-Name</span><span class="sxs-lookup"><span data-stu-id="985b4-150">-Name</span></span>

<span data-ttu-id="985b4-151">Anger namnet på den egenskap som ska flyttas.</span><span class="sxs-lookup"><span data-stu-id="985b4-151">Specifies the name of the property to be moved.</span></span>

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

### <span data-ttu-id="985b4-152">– PassThru</span><span class="sxs-lookup"><span data-stu-id="985b4-152">-PassThru</span></span>

<span data-ttu-id="985b4-153">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="985b4-153">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="985b4-154">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="985b4-154">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="985b4-155">-Path</span><span class="sxs-lookup"><span data-stu-id="985b4-155">-Path</span></span>

<span data-ttu-id="985b4-156">Anger sökvägen till egenskapens aktuella plats.</span><span class="sxs-lookup"><span data-stu-id="985b4-156">Specifies the path to the current location of the property.</span></span>
<span data-ttu-id="985b4-157">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="985b4-157">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="985b4-158">-Confirm</span><span class="sxs-lookup"><span data-stu-id="985b4-158">-Confirm</span></span>

<span data-ttu-id="985b4-159">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="985b4-159">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="985b4-160">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="985b4-160">-WhatIf</span></span>

<span data-ttu-id="985b4-161">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="985b4-161">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="985b4-162">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="985b4-162">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="985b4-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="985b4-163">CommonParameters</span></span>

<span data-ttu-id="985b4-164">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="985b4-164">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="985b4-165">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="985b4-165">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="985b4-166">INDATA</span><span class="sxs-lookup"><span data-stu-id="985b4-166">INPUTS</span></span>

### <span data-ttu-id="985b4-167">System. String</span><span class="sxs-lookup"><span data-stu-id="985b4-167">System.String</span></span>

<span data-ttu-id="985b4-168">Du kan skicka vidare en sträng som innehåller en sökväg till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="985b4-168">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="985b4-169">UTDATA</span><span class="sxs-lookup"><span data-stu-id="985b4-169">OUTPUTS</span></span>

### <span data-ttu-id="985b4-170">Ingen eller system. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="985b4-170">None or System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="985b4-171">När du använder parametern **Passthru** genererar den här cmdleten en **PSCustomObject** som representerar den flyttade objekt egenskapen.</span><span class="sxs-lookup"><span data-stu-id="985b4-171">When you use the **PassThru** parameter, this cmdlet generates a **PSCustomObject** representing the moved item property.</span></span> <span data-ttu-id="985b4-172">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="985b4-172">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="985b4-173">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="985b4-173">NOTES</span></span>

<span data-ttu-id="985b4-174">Denna cmdlet är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="985b4-174">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="985b4-175">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="985b4-175">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="985b4-176">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="985b4-176">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="985b4-177">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="985b4-177">RELATED LINKS</span></span>

[<span data-ttu-id="985b4-178">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="985b4-178">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="985b4-179">Kopiera – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="985b4-179">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="985b4-180">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="985b4-180">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="985b4-181">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="985b4-181">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="985b4-182">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="985b4-182">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="985b4-183">Byt namn – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="985b4-183">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="985b4-184">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="985b4-184">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="985b4-185">about_Providers</span><span class="sxs-lookup"><span data-stu-id="985b4-185">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
