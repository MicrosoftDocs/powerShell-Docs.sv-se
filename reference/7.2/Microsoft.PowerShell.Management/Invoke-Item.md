---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/invoke-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-Item
ms.openlocfilehash: ebb79f16447aef2dd194505d805a34353f710e69
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709486"
---
# <span data-ttu-id="c532c-102">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="c532c-102">Invoke-Item</span></span>

## <span data-ttu-id="c532c-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="c532c-103">SYNOPSIS</span></span>
<span data-ttu-id="c532c-104">Utför standard åtgärden på det angivna objektet.</span><span class="sxs-lookup"><span data-stu-id="c532c-104">Performs the default action on the specified item.</span></span>

## <span data-ttu-id="c532c-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c532c-105">SYNTAX</span></span>

### <span data-ttu-id="c532c-106">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="c532c-106">Path (Default)</span></span>

```
Invoke-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="c532c-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c532c-107">LiteralPath</span></span>

```
Invoke-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="c532c-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="c532c-108">DESCRIPTION</span></span>

<span data-ttu-id="c532c-109">`Invoke-Item`Cmdleten utför standard åtgärden på det angivna objektet.</span><span class="sxs-lookup"><span data-stu-id="c532c-109">The `Invoke-Item` cmdlet performs the default action on the specified item.</span></span>
<span data-ttu-id="c532c-110">Till exempel kör den en körbar fil eller öppnar en dokument fil i programmet som är associerat med dokument fil typen.</span><span class="sxs-lookup"><span data-stu-id="c532c-110">For example, it runs an executable file or opens a document file in the application associated with the document file type.</span></span>
<span data-ttu-id="c532c-111">Standard åtgärden beror på objekt typen och avgörs av PowerShell-providern som ger åtkomst till data.</span><span class="sxs-lookup"><span data-stu-id="c532c-111">The default action depends on the type of item and is determined by the PowerShell provider that provides access to the data.</span></span>

## <span data-ttu-id="c532c-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="c532c-112">EXAMPLES</span></span>

### <span data-ttu-id="c532c-113">Exempel 1: öppna en fil</span><span class="sxs-lookup"><span data-stu-id="c532c-113">Example 1: Open a file</span></span>

<span data-ttu-id="c532c-114">Det här kommandot öppnar filen "aliasApr04.doc" i Microsoft Office Word.</span><span class="sxs-lookup"><span data-stu-id="c532c-114">This command opens the file "aliasApr04.doc" in Microsoft Office Word.</span></span>
<span data-ttu-id="c532c-115">I det här fallet är standard åtgärden för ". doc"-filer som öppnas i Word.</span><span class="sxs-lookup"><span data-stu-id="c532c-115">In this case, opening in Word is the default action for ".doc" files.</span></span>

```powershell
Invoke-Item "C:\Test\aliasApr04.doc"
```

### <span data-ttu-id="c532c-116">Exempel 2: öppna alla filer av en speciell typ</span><span class="sxs-lookup"><span data-stu-id="c532c-116">Example 2: Open all files of a specific type</span></span>

<span data-ttu-id="c532c-117">Detta kommando öppnar alla Microsoft Office Excel-kalkylblad i `C:\Documents and
Settings\Lister\My Documents` mappen.</span><span class="sxs-lookup"><span data-stu-id="c532c-117">This command opens all of the Microsoft Office Excel spreadsheets in the `C:\Documents and
Settings\Lister\My Documents` folder.</span></span> <span data-ttu-id="c532c-118">Varje kalkyl blad öppnas i en ny instans av Excel.</span><span class="sxs-lookup"><span data-stu-id="c532c-118">Each spreadsheet is opened in a new instance of Excel.</span></span>
<span data-ttu-id="c532c-119">I detta fall är standard åtgärden för filer som öppnas i Excel `.xls` .</span><span class="sxs-lookup"><span data-stu-id="c532c-119">In this case, opening in Excel is the default action for `.xls` files.</span></span>

```powershell
Invoke-Item "C:\Documents and Settings\Lister\My Documents\*.xls"
```

## <span data-ttu-id="c532c-120">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="c532c-120">PARAMETERS</span></span>

### <span data-ttu-id="c532c-121">-Credential</span><span class="sxs-lookup"><span data-stu-id="c532c-121">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="c532c-122">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c532c-122">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="c532c-123">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="c532c-123">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="c532c-124">-Undanta</span><span class="sxs-lookup"><span data-stu-id="c532c-124">-Exclude</span></span>

<span data-ttu-id="c532c-125">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="c532c-125">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="c532c-126">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="c532c-126">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="c532c-127">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="c532c-127">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="c532c-128">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="c532c-128">Wildcard characters are permitted.</span></span> <span data-ttu-id="c532c-129">Parametern **exclude** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="c532c-129">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="c532c-130">-Filter</span><span class="sxs-lookup"><span data-stu-id="c532c-130">-Filter</span></span>

<span data-ttu-id="c532c-131">Anger ett filter för att kvalificera **Sök vägs** parametern.</span><span class="sxs-lookup"><span data-stu-id="c532c-131">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="c532c-132">[Fil Systems](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) leverantören är den enda installerade PowerShell-providern som stöder användningen av filter.</span><span class="sxs-lookup"><span data-stu-id="c532c-132">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="c532c-133">Du kan hitta syntaxen för filter språket för **fil systemet** i [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="c532c-133">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="c532c-134">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="c532c-134">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="c532c-135">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="c532c-135">-Include</span></span>

<span data-ttu-id="c532c-136">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="c532c-136">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="c532c-137">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="c532c-137">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="c532c-138">Ange ett Sök vägs element eller ett mönster, till exempel `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="c532c-138">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="c532c-139">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="c532c-139">Wildcard characters are permitted.</span></span> <span data-ttu-id="c532c-140">Parametern **include** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="c532c-140">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="c532c-141">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c532c-141">-LiteralPath</span></span>

<span data-ttu-id="c532c-142">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="c532c-142">Specifies a path to one or more locations.</span></span> <span data-ttu-id="c532c-143">Värdet för **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="c532c-143">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="c532c-144">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="c532c-144">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="c532c-145">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="c532c-145">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="c532c-146">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="c532c-146">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="c532c-147">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="c532c-147">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="c532c-148">-Path</span><span class="sxs-lookup"><span data-stu-id="c532c-148">-Path</span></span>

<span data-ttu-id="c532c-149">Anger sökvägen till det markerade objektet.</span><span class="sxs-lookup"><span data-stu-id="c532c-149">Specifies the path to the selected item.</span></span>
<span data-ttu-id="c532c-150">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="c532c-150">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="c532c-151">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c532c-151">-Confirm</span></span>

<span data-ttu-id="c532c-152">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c532c-152">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="c532c-153">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c532c-153">-WhatIf</span></span>

<span data-ttu-id="c532c-154">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="c532c-154">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="c532c-155">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="c532c-155">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="c532c-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c532c-156">CommonParameters</span></span>

<span data-ttu-id="c532c-157">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="c532c-157">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="c532c-158">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="c532c-158">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="c532c-159">INDATA</span><span class="sxs-lookup"><span data-stu-id="c532c-159">INPUTS</span></span>

### <span data-ttu-id="c532c-160">System. String</span><span class="sxs-lookup"><span data-stu-id="c532c-160">System.String</span></span>

<span data-ttu-id="c532c-161">Du kan skicka vidare en sträng som innehåller en sökväg till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c532c-161">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="c532c-162">UTDATA</span><span class="sxs-lookup"><span data-stu-id="c532c-162">OUTPUTS</span></span>

### <span data-ttu-id="c532c-163">Inga</span><span class="sxs-lookup"><span data-stu-id="c532c-163">None</span></span>

<span data-ttu-id="c532c-164">Kommandot genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="c532c-164">The command does not generate any output.</span></span>
<span data-ttu-id="c532c-165">Utdata kan dock genereras av det objekt som anropas.</span><span class="sxs-lookup"><span data-stu-id="c532c-165">However, output might be generated by the item that it invokes.</span></span>

## <span data-ttu-id="c532c-166">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="c532c-166">NOTES</span></span>

<span data-ttu-id="c532c-167">Denna cmdlet är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="c532c-167">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="c532c-168">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="c532c-168">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="c532c-169">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="c532c-169">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="c532c-170">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="c532c-170">RELATED LINKS</span></span>

[<span data-ttu-id="c532c-171">Rensa objekt</span><span class="sxs-lookup"><span data-stu-id="c532c-171">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="c532c-172">Kopiera objekt</span><span class="sxs-lookup"><span data-stu-id="c532c-172">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="c532c-173">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="c532c-173">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="c532c-174">Flytta objekt</span><span class="sxs-lookup"><span data-stu-id="c532c-174">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="c532c-175">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="c532c-175">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="c532c-176">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="c532c-176">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="c532c-177">Byt namn – objekt</span><span class="sxs-lookup"><span data-stu-id="c532c-177">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="c532c-178">Ange objekt</span><span class="sxs-lookup"><span data-stu-id="c532c-178">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="c532c-179">about_Providers</span><span class="sxs-lookup"><span data-stu-id="c532c-179">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

