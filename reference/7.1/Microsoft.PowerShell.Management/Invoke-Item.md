---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/invoke-item?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-Item
ms.openlocfilehash: 030e65f2b78ba91ddd4f6e2626372c1716218a78
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263337"
---
# <span data-ttu-id="01359-103">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="01359-103">Invoke-Item</span></span>

## <span data-ttu-id="01359-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="01359-104">SYNOPSIS</span></span>
<span data-ttu-id="01359-105">Utför standard åtgärden på det angivna objektet.</span><span class="sxs-lookup"><span data-stu-id="01359-105">Performs the default action on the specified item.</span></span>

## <span data-ttu-id="01359-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="01359-106">SYNTAX</span></span>

### <span data-ttu-id="01359-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="01359-107">Path (Default)</span></span>

```
Invoke-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="01359-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="01359-108">LiteralPath</span></span>

```
Invoke-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="01359-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="01359-109">DESCRIPTION</span></span>

<span data-ttu-id="01359-110">`Invoke-Item`Cmdleten utför standard åtgärden på det angivna objektet.</span><span class="sxs-lookup"><span data-stu-id="01359-110">The `Invoke-Item` cmdlet performs the default action on the specified item.</span></span>
<span data-ttu-id="01359-111">Till exempel kör den en körbar fil eller öppnar en dokument fil i programmet som är associerat med dokument fil typen.</span><span class="sxs-lookup"><span data-stu-id="01359-111">For example, it runs an executable file or opens a document file in the application associated with the document file type.</span></span>
<span data-ttu-id="01359-112">Standard åtgärden beror på objekt typen och avgörs av PowerShell-providern som ger åtkomst till data.</span><span class="sxs-lookup"><span data-stu-id="01359-112">The default action depends on the type of item and is determined by the PowerShell provider that provides access to the data.</span></span>

## <span data-ttu-id="01359-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="01359-113">EXAMPLES</span></span>

### <span data-ttu-id="01359-114">Exempel 1: öppna en fil</span><span class="sxs-lookup"><span data-stu-id="01359-114">Example 1: Open a file</span></span>

<span data-ttu-id="01359-115">Det här kommandot öppnar filen "aliasApr04.doc" i Microsoft Office Word.</span><span class="sxs-lookup"><span data-stu-id="01359-115">This command opens the file "aliasApr04.doc" in Microsoft Office Word.</span></span>
<span data-ttu-id="01359-116">I det här fallet är standard åtgärden för ". doc"-filer som öppnas i Word.</span><span class="sxs-lookup"><span data-stu-id="01359-116">In this case, opening in Word is the default action for ".doc" files.</span></span>

```powershell
Invoke-Item "C:\Test\aliasApr04.doc"
```

### <span data-ttu-id="01359-117">Exempel 2: öppna alla filer av en speciell typ</span><span class="sxs-lookup"><span data-stu-id="01359-117">Example 2: Open all files of a specific type</span></span>

<span data-ttu-id="01359-118">Detta kommando öppnar alla Microsoft Office Excel-kalkylblad i `C:\Documents and
Settings\Lister\My Documents` mappen.</span><span class="sxs-lookup"><span data-stu-id="01359-118">This command opens all of the Microsoft Office Excel spreadsheets in the `C:\Documents and
Settings\Lister\My Documents` folder.</span></span> <span data-ttu-id="01359-119">Varje kalkyl blad öppnas i en ny instans av Excel.</span><span class="sxs-lookup"><span data-stu-id="01359-119">Each spreadsheet is opened in a new instance of Excel.</span></span>
<span data-ttu-id="01359-120">I detta fall är standard åtgärden för filer som öppnas i Excel `.xls` .</span><span class="sxs-lookup"><span data-stu-id="01359-120">In this case, opening in Excel is the default action for `.xls` files.</span></span>

```powershell
Invoke-Item "C:\Documents and Settings\Lister\My Documents\*.xls"
```

## <span data-ttu-id="01359-121">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="01359-121">PARAMETERS</span></span>

### <span data-ttu-id="01359-122">-Credential</span><span class="sxs-lookup"><span data-stu-id="01359-122">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="01359-123">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="01359-123">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="01359-124">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="01359-124">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="01359-125">-Undanta</span><span class="sxs-lookup"><span data-stu-id="01359-125">-Exclude</span></span>

<span data-ttu-id="01359-126">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="01359-126">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="01359-127">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="01359-127">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="01359-128">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="01359-128">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="01359-129">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="01359-129">Wildcard characters are permitted.</span></span> <span data-ttu-id="01359-130">Parametern **exclude** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="01359-130">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="01359-131">-Filter</span><span class="sxs-lookup"><span data-stu-id="01359-131">-Filter</span></span>

<span data-ttu-id="01359-132">Anger ett filter för att kvalificera **Sök vägs** parametern.</span><span class="sxs-lookup"><span data-stu-id="01359-132">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="01359-133">[Fil Systems](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) leverantören är den enda installerade PowerShell-providern som stöder användningen av filter.</span><span class="sxs-lookup"><span data-stu-id="01359-133">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="01359-134">Du kan hitta syntaxen för filter språket för **fil systemet** i [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="01359-134">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="01359-135">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="01359-135">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="01359-136">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="01359-136">-Include</span></span>

<span data-ttu-id="01359-137">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="01359-137">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="01359-138">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="01359-138">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="01359-139">Ange ett Sök vägs element eller ett mönster, till exempel `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="01359-139">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="01359-140">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="01359-140">Wildcard characters are permitted.</span></span> <span data-ttu-id="01359-141">Parametern **include** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="01359-141">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="01359-142">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="01359-142">-LiteralPath</span></span>

<span data-ttu-id="01359-143">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="01359-143">Specifies a path to one or more locations.</span></span> <span data-ttu-id="01359-144">Värdet för **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="01359-144">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="01359-145">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="01359-145">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="01359-146">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="01359-146">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="01359-147">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="01359-147">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="01359-148">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="01359-148">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="01359-149">-Path</span><span class="sxs-lookup"><span data-stu-id="01359-149">-Path</span></span>

<span data-ttu-id="01359-150">Anger sökvägen till det markerade objektet.</span><span class="sxs-lookup"><span data-stu-id="01359-150">Specifies the path to the selected item.</span></span>
<span data-ttu-id="01359-151">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="01359-151">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="01359-152">-Confirm</span><span class="sxs-lookup"><span data-stu-id="01359-152">-Confirm</span></span>

<span data-ttu-id="01359-153">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="01359-153">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="01359-154">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="01359-154">-WhatIf</span></span>

<span data-ttu-id="01359-155">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="01359-155">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="01359-156">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="01359-156">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="01359-157">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="01359-157">CommonParameters</span></span>

<span data-ttu-id="01359-158">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="01359-158">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="01359-159">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="01359-159">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="01359-160">INDATA</span><span class="sxs-lookup"><span data-stu-id="01359-160">INPUTS</span></span>

### <span data-ttu-id="01359-161">System. String</span><span class="sxs-lookup"><span data-stu-id="01359-161">System.String</span></span>

<span data-ttu-id="01359-162">Du kan skicka vidare en sträng som innehåller en sökväg till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="01359-162">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="01359-163">UTDATA</span><span class="sxs-lookup"><span data-stu-id="01359-163">OUTPUTS</span></span>

### <span data-ttu-id="01359-164">Inget</span><span class="sxs-lookup"><span data-stu-id="01359-164">None</span></span>

<span data-ttu-id="01359-165">Kommandot genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="01359-165">The command does not generate any output.</span></span>
<span data-ttu-id="01359-166">Utdata kan dock genereras av det objekt som anropas.</span><span class="sxs-lookup"><span data-stu-id="01359-166">However, output might be generated by the item that it invokes.</span></span>

## <span data-ttu-id="01359-167">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="01359-167">NOTES</span></span>

<span data-ttu-id="01359-168">Denna cmdlet är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="01359-168">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="01359-169">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="01359-169">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="01359-170">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="01359-170">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="01359-171">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="01359-171">RELATED LINKS</span></span>

[<span data-ttu-id="01359-172">Rensa objekt</span><span class="sxs-lookup"><span data-stu-id="01359-172">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="01359-173">Kopiera objekt</span><span class="sxs-lookup"><span data-stu-id="01359-173">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="01359-174">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="01359-174">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="01359-175">Flytta objekt</span><span class="sxs-lookup"><span data-stu-id="01359-175">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="01359-176">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="01359-176">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="01359-177">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="01359-177">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="01359-178">Byt namn – objekt</span><span class="sxs-lookup"><span data-stu-id="01359-178">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="01359-179">Ange objekt</span><span class="sxs-lookup"><span data-stu-id="01359-179">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="01359-180">about_Providers</span><span class="sxs-lookup"><span data-stu-id="01359-180">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

