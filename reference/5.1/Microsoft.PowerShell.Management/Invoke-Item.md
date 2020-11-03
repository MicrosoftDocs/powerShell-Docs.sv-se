---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/invoke-item?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-Item
ms.openlocfilehash: 6aac74b9b084996377b97997ab78972cb28b0959
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266097"
---
# <span data-ttu-id="32f25-103">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="32f25-103">Invoke-Item</span></span>

## <span data-ttu-id="32f25-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="32f25-104">SYNOPSIS</span></span>
<span data-ttu-id="32f25-105">Utför standard åtgärden på det angivna objektet.</span><span class="sxs-lookup"><span data-stu-id="32f25-105">Performs the default action on the specified item.</span></span>

## <span data-ttu-id="32f25-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="32f25-106">SYNTAX</span></span>

### <span data-ttu-id="32f25-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="32f25-107">Path (Default)</span></span>

```
Invoke-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="32f25-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="32f25-108">LiteralPath</span></span>

```
Invoke-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="32f25-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="32f25-109">DESCRIPTION</span></span>

<span data-ttu-id="32f25-110">`Invoke-Item`Cmdleten utför standard åtgärden på det angivna objektet.</span><span class="sxs-lookup"><span data-stu-id="32f25-110">The `Invoke-Item` cmdlet performs the default action on the specified item.</span></span>
<span data-ttu-id="32f25-111">Till exempel kör den en körbar fil eller öppnar en dokument fil i programmet som är associerat med dokument fil typen.</span><span class="sxs-lookup"><span data-stu-id="32f25-111">For example, it runs an executable file or opens a document file in the application associated with the document file type.</span></span>
<span data-ttu-id="32f25-112">Standard åtgärden beror på objekt typen och avgörs av PowerShell-providern som ger åtkomst till data.</span><span class="sxs-lookup"><span data-stu-id="32f25-112">The default action depends on the type of item and is determined by the PowerShell provider that provides access to the data.</span></span>

## <span data-ttu-id="32f25-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="32f25-113">EXAMPLES</span></span>

### <span data-ttu-id="32f25-114">Exempel 1: öppna en fil</span><span class="sxs-lookup"><span data-stu-id="32f25-114">Example 1: Open a file</span></span>

<span data-ttu-id="32f25-115">Det här kommandot öppnar filen "aliasApr04.doc" i Microsoft Office Word.</span><span class="sxs-lookup"><span data-stu-id="32f25-115">This command opens the file "aliasApr04.doc" in Microsoft Office Word.</span></span>
<span data-ttu-id="32f25-116">I det här fallet är standard åtgärden för ". doc"-filer som öppnas i Word.</span><span class="sxs-lookup"><span data-stu-id="32f25-116">In this case, opening in Word is the default action for ".doc" files.</span></span>

```powershell
Invoke-Item "C:\Test\aliasApr04.doc"
```

### <span data-ttu-id="32f25-117">Exempel 2: öppna alla filer av en speciell typ</span><span class="sxs-lookup"><span data-stu-id="32f25-117">Example 2: Open all files of a specific type</span></span>

<span data-ttu-id="32f25-118">Detta kommando öppnar alla Microsoft Office Excel-kalkylblad i mappen "C:\Documents and Settings\Lister\My Documents".</span><span class="sxs-lookup"><span data-stu-id="32f25-118">This command opens all of the Microsoft Office Excel spreadsheets in the "C:\Documents and Settings\Lister\My Documents" folder.</span></span>
<span data-ttu-id="32f25-119">Varje kalkyl blad öppnas i en ny instans av Excel.</span><span class="sxs-lookup"><span data-stu-id="32f25-119">Each spreadsheet is opened in a new instance of Excel.</span></span>
<span data-ttu-id="32f25-120">I det här fallet är det att öppna i Excel standard åtgärden för ". xls"-filer.</span><span class="sxs-lookup"><span data-stu-id="32f25-120">In this case, opening in Excel is the default action for ".xls" files.</span></span>

```powershell
Invoke-Item "C:\Documents and Settings\Lister\My Documents\*.xls"
```

## <span data-ttu-id="32f25-121">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="32f25-121">PARAMETERS</span></span>

### <span data-ttu-id="32f25-122">-Credential</span><span class="sxs-lookup"><span data-stu-id="32f25-122">-Credential</span></span>

<span data-ttu-id="32f25-123">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="32f25-123">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="32f25-124">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="32f25-124">The default is the current user.</span></span>

<span data-ttu-id="32f25-125">Ange ett användar namn, till exempel "user01" eller "Domain01\User01", eller ange ett **PSCredential** -objekt, t. ex. ett som genererades av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="32f25-125">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>
<span data-ttu-id="32f25-126">Om du anger ett användar namn uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="32f25-126">If you type a user name, you are prompted for a password.</span></span>

> [!WARNING]
> <span data-ttu-id="32f25-127">Den här parametern stöds inte av några providrar som installeras med Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="32f25-127">This parameter is not supported by any providers installed with Windows PowerShell.</span></span>

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

### <span data-ttu-id="32f25-128">-Undanta</span><span class="sxs-lookup"><span data-stu-id="32f25-128">-Exclude</span></span>

<span data-ttu-id="32f25-129">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar från åtgärden.</span><span class="sxs-lookup"><span data-stu-id="32f25-129">Specifies, as a string array, an item or items that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="32f25-130">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="32f25-130">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="32f25-131">Ange ett Sök vägs element eller ett mönster, till exempel "\*. txt".</span><span class="sxs-lookup"><span data-stu-id="32f25-131">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="32f25-132">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="32f25-132">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="32f25-133">-Filter</span><span class="sxs-lookup"><span data-stu-id="32f25-133">-Filter</span></span>

<span data-ttu-id="32f25-134">Anger ett filter i formatet eller språket för providern.</span><span class="sxs-lookup"><span data-stu-id="32f25-134">Specifies a filter in the format or language of the provider.</span></span>
<span data-ttu-id="32f25-135">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="32f25-135">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="32f25-136">Syntaxen för filtret, inklusive användning av jokertecken, är beroende av providern.</span><span class="sxs-lookup"><span data-stu-id="32f25-136">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span>
<span data-ttu-id="32f25-137">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="32f25-137">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="32f25-138">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="32f25-138">-Include</span></span>

<span data-ttu-id="32f25-139">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="32f25-139">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="32f25-140">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="32f25-140">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="32f25-141">Ange ett Sök vägs element eller ett mönster, till exempel "\*. txt".</span><span class="sxs-lookup"><span data-stu-id="32f25-141">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="32f25-142">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="32f25-142">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="32f25-143">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="32f25-143">-LiteralPath</span></span>

<span data-ttu-id="32f25-144">Anger en sökväg till objektet.</span><span class="sxs-lookup"><span data-stu-id="32f25-144">Specifies a path to the item.</span></span>
<span data-ttu-id="32f25-145">Till skillnad från parametern **Path** används värdet för **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="32f25-145">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="32f25-146">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="32f25-146">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="32f25-147">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="32f25-147">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="32f25-148">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="32f25-148">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="32f25-149">-Path</span><span class="sxs-lookup"><span data-stu-id="32f25-149">-Path</span></span>

<span data-ttu-id="32f25-150">Anger sökvägen till det markerade objektet.</span><span class="sxs-lookup"><span data-stu-id="32f25-150">Specifies the path to the selected item.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="32f25-151">– UseTransaction</span><span class="sxs-lookup"><span data-stu-id="32f25-151">-UseTransaction</span></span>

<span data-ttu-id="32f25-152">Inkluderar kommandot i den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="32f25-152">Includes the command in the active transaction.</span></span>
<span data-ttu-id="32f25-153">Den här parametern är bara giltig medan en transaktion pågår.</span><span class="sxs-lookup"><span data-stu-id="32f25-153">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="32f25-154">Mer information finns i about_transactions.</span><span class="sxs-lookup"><span data-stu-id="32f25-154">For more information, see about_transactions.</span></span>

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

### <span data-ttu-id="32f25-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="32f25-155">-Confirm</span></span>
<span data-ttu-id="32f25-156">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="32f25-156">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="32f25-157">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="32f25-157">-WhatIf</span></span>

<span data-ttu-id="32f25-158">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="32f25-158">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="32f25-159">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="32f25-159">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="32f25-160">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="32f25-160">CommonParameters</span></span>

<span data-ttu-id="32f25-161">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="32f25-161">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="32f25-162">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="32f25-162">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="32f25-163">INDATA</span><span class="sxs-lookup"><span data-stu-id="32f25-163">INPUTS</span></span>

### <span data-ttu-id="32f25-164">System. String</span><span class="sxs-lookup"><span data-stu-id="32f25-164">System.String</span></span>

<span data-ttu-id="32f25-165">Du kan skicka vidare en sträng som innehåller en sökväg till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="32f25-165">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="32f25-166">UTDATA</span><span class="sxs-lookup"><span data-stu-id="32f25-166">OUTPUTS</span></span>

### <span data-ttu-id="32f25-167">Inget</span><span class="sxs-lookup"><span data-stu-id="32f25-167">None</span></span>

<span data-ttu-id="32f25-168">Kommandot genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="32f25-168">The command does not generate any output.</span></span>
<span data-ttu-id="32f25-169">Utdata kan dock genereras av det objekt som anropas.</span><span class="sxs-lookup"><span data-stu-id="32f25-169">However, output might be generated by the item that it invokes.</span></span>

## <span data-ttu-id="32f25-170">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="32f25-170">NOTES</span></span>

<span data-ttu-id="32f25-171">Denna cmdlet är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="32f25-171">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="32f25-172">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="32f25-172">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="32f25-173">Mer information finns i about_Providers.</span><span class="sxs-lookup"><span data-stu-id="32f25-173">For more information, see about_Providers.</span></span>

## <span data-ttu-id="32f25-174">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="32f25-174">RELATED LINKS</span></span>

[<span data-ttu-id="32f25-175">Rensa objekt</span><span class="sxs-lookup"><span data-stu-id="32f25-175">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="32f25-176">Kopiera objekt</span><span class="sxs-lookup"><span data-stu-id="32f25-176">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="32f25-177">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="32f25-177">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="32f25-178">Flytta objekt</span><span class="sxs-lookup"><span data-stu-id="32f25-178">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="32f25-179">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="32f25-179">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="32f25-180">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="32f25-180">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="32f25-181">Byt namn – objekt</span><span class="sxs-lookup"><span data-stu-id="32f25-181">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="32f25-182">Ange objekt</span><span class="sxs-lookup"><span data-stu-id="32f25-182">Set-Item</span></span>](Set-Item.md)
