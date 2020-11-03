---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-formatdata?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-FormatData
ms.openlocfilehash: 9f88dc77288a0fd24efdbb486e54bc60c2658c14
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265094"
---
# <span data-ttu-id="0ea40-103">Export-FormatData</span><span class="sxs-lookup"><span data-stu-id="0ea40-103">Export-FormatData</span></span>

## <span data-ttu-id="0ea40-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="0ea40-104">SYNOPSIS</span></span>
<span data-ttu-id="0ea40-105">Sparar formatering av data från den aktuella sessionen i en format fil.</span><span class="sxs-lookup"><span data-stu-id="0ea40-105">Saves formatting data from the current session in a formatting file.</span></span>

## <span data-ttu-id="0ea40-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0ea40-106">SYNTAX</span></span>

### <span data-ttu-id="0ea40-107">ByPath (standard)</span><span class="sxs-lookup"><span data-stu-id="0ea40-107">ByPath (Default)</span></span>

```
Export-FormatData -InputObject <ExtendedTypeDefinition[]> -Path <String> [-Force] [-NoClobber]
 [-IncludeScriptBlock] [<CommonParameters>]
```

### <span data-ttu-id="0ea40-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="0ea40-108">ByLiteralPath</span></span>

```
Export-FormatData -InputObject <ExtendedTypeDefinition[]> -LiteralPath <String> [-Force] [-NoClobber]
 [-IncludeScriptBlock] [<CommonParameters>]
```

## <span data-ttu-id="0ea40-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="0ea40-109">DESCRIPTION</span></span>

<span data-ttu-id="0ea40-110">`Export-FormatData`Cmdleten skapar filer för Windows PowerShell-formatering (format.ps1XML) från formateringselement i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="0ea40-110">The `Export-FormatData` cmdlet creates Windows PowerShell formatting files (format.ps1xml) from the formatting objects in the current session.</span></span> <span data-ttu-id="0ea40-111">Det tar **ExtendedTypeDefinition** -objekt som `Get-FormatData` returnerar och sparar dem i en fil i XML-format.</span><span class="sxs-lookup"><span data-stu-id="0ea40-111">It takes the **ExtendedTypeDefinition** objects that `Get-FormatData` returns and saves them in a file in XML format.</span></span>

<span data-ttu-id="0ea40-112">Windows PowerShell använder datan i att formatera filer (format.ps1XML) för att generera standard visningen av Microsoft .NET Ramverks objekt i sessionen.</span><span class="sxs-lookup"><span data-stu-id="0ea40-112">Windows PowerShell uses the data in formatting files (format.ps1xml) to generate the default display of Microsoft .NET Framework objects in the session.</span></span> <span data-ttu-id="0ea40-113">Du kan visa och redigera formateringsattribut och använda Update-FormatData cmdlet för att lägga till formaterings data i en session.</span><span class="sxs-lookup"><span data-stu-id="0ea40-113">You can view and edit the formatting files and use the Update-FormatData cmdlet to add the formatting data to a session.</span></span>

<span data-ttu-id="0ea40-114">Mer information om hur du formaterar filer i Windows PowerShell finns i [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span><span class="sxs-lookup"><span data-stu-id="0ea40-114">For more information about formatting files in Windows PowerShell, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

## <span data-ttu-id="0ea40-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="0ea40-115">EXAMPLES</span></span>

### <span data-ttu-id="0ea40-116">Exempel 1: exportera session format data</span><span class="sxs-lookup"><span data-stu-id="0ea40-116">Example 1: Export session format data</span></span>

```powershell
Get-FormatData -TypeName "*" | Export-FormatData -Path "allformat.ps1xml" -IncludeScriptBlock
```

<span data-ttu-id="0ea40-117">Detta kommando exporterar alla format data i sessionen till AllFormat.ps1XML-filen.</span><span class="sxs-lookup"><span data-stu-id="0ea40-117">This command exports all of the format data in the session to the AllFormat.ps1xml file.</span></span>

<span data-ttu-id="0ea40-118">Kommandot använder `Get-FormatData` cmdleten för att hämta format data i sessionen.</span><span class="sxs-lookup"><span data-stu-id="0ea40-118">The command uses the `Get-FormatData` cmdlet to get the format data in the session.</span></span> <span data-ttu-id="0ea40-119">Värdet `*` (alla) för parametern **TypeName** dirigerar cmdleten för att hämta alla data i sessionen.</span><span class="sxs-lookup"><span data-stu-id="0ea40-119">A value of `*` (all) for the **TypeName** parameter directs the cmdlet to get all of the data in the session.</span></span>

<span data-ttu-id="0ea40-120">Kommandot använder en pipeline-operator ( `|` ) för att skicka format data från `Get-FormatData` kommandot till `Export-FormatData` cmdleten, som exporterar format data till AllFormat.ps1-filen.</span><span class="sxs-lookup"><span data-stu-id="0ea40-120">The command uses a pipeline operator (`|`) to send the format data from the `Get-FormatData` command to the `Export-FormatData` cmdlet, which exports the format data to the AllFormat.ps1 file.</span></span>

<span data-ttu-id="0ea40-121">`Export-FormatData`Kommandot använder parametern **IncludeScriptBlock** för att inkludera skript block i format data i filen.</span><span class="sxs-lookup"><span data-stu-id="0ea40-121">The `Export-FormatData` command uses the **IncludeScriptBlock** parameter to include script blocks in the format data in the file.</span></span>

### <span data-ttu-id="0ea40-122">Exempel 2: exportera format data för en typ</span><span class="sxs-lookup"><span data-stu-id="0ea40-122">Example 2: Export format data for a type</span></span>

```powershell
$F = Get-FormatData -TypeName "helpinfoshort"
Export-FormatData -InputObject $F -Path "c:\test\help.format.ps1xml" -IncludeScriptBlock
```

<span data-ttu-id="0ea40-123">Dessa kommandon exporterar format data för **HelpInfoShort** -typen till Help.format.ps1XML-filen.</span><span class="sxs-lookup"><span data-stu-id="0ea40-123">These commands export the format data for the **HelpInfoShort** type to the Help.format.ps1xml file.</span></span>

<span data-ttu-id="0ea40-124">Det första kommandot använder `Get-FormatData` cmdleten för att hämta format data för **HelpInfoShort** -typen, och den sparas i `$F` variabeln.</span><span class="sxs-lookup"><span data-stu-id="0ea40-124">The first command uses the `Get-FormatData` cmdlet to get the format data for the **HelpInfoShort** type, and it saves it in the `$F` variable.</span></span>

<span data-ttu-id="0ea40-125">Det andra kommandot använder cmdlet: en **InputObject** -parameter för `Export-FormatData` att ange de format data som sparats i `$F` variabeln.</span><span class="sxs-lookup"><span data-stu-id="0ea40-125">The second command uses the **InputObject** parameter of the `Export-FormatData` cmdlet to enter the format data saved in the `$F` variable.</span></span> <span data-ttu-id="0ea40-126">Den använder också parametern **IncludeScriptBlock** för att inkludera skript block i utdata.</span><span class="sxs-lookup"><span data-stu-id="0ea40-126">It also uses the **IncludeScriptBlock** parameter to include script blocks in the output.</span></span>

### <span data-ttu-id="0ea40-127">Exempel 3: exportera format data utan ett skript block</span><span class="sxs-lookup"><span data-stu-id="0ea40-127">Example 3: Export format data without a script block</span></span>

```powershell
Get-FormatData -TypeName "System.Diagnostics.Process" | Export-FormatData -Path process.format.ps1xml
Update-FormatData -PrependPath ".\process.format.ps1xml"
Get-Process p*
```

```Output
Handles  NPM(K)  PM(K)  WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------  -----  ----- -----   ------    -- -----------
323                                       5600 powershell
336                                       3900 powershell_ise
138                                       4076 PresentationFontCache
```

<span data-ttu-id="0ea40-128">Det här exemplet visar effekterna av att utelämna parametern **IncludeScriptBlock** från ett `Export-FormatData` kommando.</span><span class="sxs-lookup"><span data-stu-id="0ea40-128">This example shows the effect of omitting the **IncludeScriptBlock** parameter from an `Export-FormatData` command.</span></span>

<span data-ttu-id="0ea40-129">Det första kommandot använder `Get-FormatData` cmdleten för att hämta format data för objektet **system. Diagnostics. Process** som Get-Process cmdlet returnerar.</span><span class="sxs-lookup"><span data-stu-id="0ea40-129">The first command uses the `Get-FormatData` cmdlet to get the format data for the **System.Diagnostics.Process** object that the Get-Process cmdlet returns.</span></span> <span data-ttu-id="0ea40-130">Kommandot använder en pipeline-operator ( `|` ) för att skicka formaterings data till `Export-FormatData` cmdleten, som exporterar den till Process.format.ps1XML-fil i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="0ea40-130">The command uses a pipeline operator (`|`) to send the formatting data to the `Export-FormatData` cmdlet, which exports it to the Process.format.ps1xml file in the current directory.</span></span>

<span data-ttu-id="0ea40-131">I det här fallet `Export-FormatData` använder kommandot inte parametern **IncludeScriptBlock** .</span><span class="sxs-lookup"><span data-stu-id="0ea40-131">In this case, the `Export-FormatData` command does not use the **IncludeScriptBlock** parameter.</span></span>

<span data-ttu-id="0ea40-132">Det andra kommandot använder `Update-FormatData` cmdleten för att lägga till Process.format.ps1XML-filen i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="0ea40-132">The second command uses the `Update-FormatData` cmdlet to add the Process.format.ps1xml file to the current session.</span></span> <span data-ttu-id="0ea40-133">Kommandot använder parametern **PrependPath** för att se till att formaterings data för process objekt i Process.format.ps1XML-filen hittas före standardformateringen för process objekt.</span><span class="sxs-lookup"><span data-stu-id="0ea40-133">The command uses the **PrependPath** parameter to ensure that the formatting data for process objects in the Process.format.ps1xml file is found before the standard formatting data for process objects.</span></span>

<span data-ttu-id="0ea40-134">Det tredje kommandot visar effekterna av den här ändringen.</span><span class="sxs-lookup"><span data-stu-id="0ea40-134">The third command shows the effects of this change.</span></span> <span data-ttu-id="0ea40-135">Kommandot använder `Get-Process` cmdleten för att hämta processer som har namn som börjar med P. Utdata visar att egenskaps värden som beräknas med hjälp av skript block saknas i visningen.</span><span class="sxs-lookup"><span data-stu-id="0ea40-135">The command uses the `Get-Process` cmdlet to get processes that have names that begin with P. The output shows that property values that are calculated by using script blocks are missing from the display.</span></span>

## <span data-ttu-id="0ea40-136">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="0ea40-136">PARAMETERS</span></span>

### <span data-ttu-id="0ea40-137">-Force</span><span class="sxs-lookup"><span data-stu-id="0ea40-137">-Force</span></span>

<span data-ttu-id="0ea40-138">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="0ea40-138">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="0ea40-139">-IncludeScriptBlock</span><span class="sxs-lookup"><span data-stu-id="0ea40-139">-IncludeScriptBlock</span></span>

<span data-ttu-id="0ea40-140">Anger om skript block i format data ska exporteras.</span><span class="sxs-lookup"><span data-stu-id="0ea40-140">Indicates whether script blocks in the format data are exported.</span></span>

<span data-ttu-id="0ea40-141">Eftersom skript block innehåller kod och kan användas på ett skadligt sätt exporteras de inte som standard.</span><span class="sxs-lookup"><span data-stu-id="0ea40-141">Because script blocks contain code and can be used maliciously, they are not exported by default.</span></span>

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

### <span data-ttu-id="0ea40-142">– InputObject</span><span class="sxs-lookup"><span data-stu-id="0ea40-142">-InputObject</span></span>

<span data-ttu-id="0ea40-143">Anger det format data objekt som ska exporteras.</span><span class="sxs-lookup"><span data-stu-id="0ea40-143">Specifies the format data objects to be exported.</span></span> <span data-ttu-id="0ea40-144">Ange en variabel som innehåller objekten eller ett kommando som hämtar objekten, till exempel ett `Get-FormatData` kommando.</span><span class="sxs-lookup"><span data-stu-id="0ea40-144">Enter a variable that contains the objects or a command that gets the objects, such as a `Get-FormatData` command.</span></span> <span data-ttu-id="0ea40-145">Du kan också skicka objekt från `Get-FormatData` till `Export-FormatData` .</span><span class="sxs-lookup"><span data-stu-id="0ea40-145">You can also pipe the objects from `Get-FormatData` to `Export-FormatData`.</span></span>

```yaml
Type: System.Management.Automation.ExtendedTypeDefinition[]
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="0ea40-146">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="0ea40-146">-LiteralPath</span></span>

<span data-ttu-id="0ea40-147">Anger en plats för utdatafilen.</span><span class="sxs-lookup"><span data-stu-id="0ea40-147">Specifies a location for the output file.</span></span> <span data-ttu-id="0ea40-148">Till skillnad från parametern **Path** används värdet för **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="0ea40-148">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="0ea40-149">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="0ea40-149">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="0ea40-150">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="0ea40-150">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="0ea40-151">Enkla citat tecken anger att Windows PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="0ea40-151">Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0ea40-152">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="0ea40-152">-NoClobber</span></span>

<span data-ttu-id="0ea40-153">Anger att cmdleten inte skriver över befintliga filer.</span><span class="sxs-lookup"><span data-stu-id="0ea40-153">Indicates that the cmdlet does not overwrite existing files.</span></span> <span data-ttu-id="0ea40-154">Som standard `Export-FormatData` skriver överskrivna filer utan varning om inte filen har attributet skrivskyddad.</span><span class="sxs-lookup"><span data-stu-id="0ea40-154">By default, `Export-FormatData` overwrites files without warning unless the file has the read-only attribute.</span></span>

<span data-ttu-id="0ea40-155">Om du vill dirigera `Export-FormatData` Skriv över skrivskyddade filer använder du parametern **Force** .</span><span class="sxs-lookup"><span data-stu-id="0ea40-155">To direct `Export-FormatData` to overwrite read-only files, use the **Force** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0ea40-156">-Path</span><span class="sxs-lookup"><span data-stu-id="0ea40-156">-Path</span></span>

<span data-ttu-id="0ea40-157">Anger en plats för utdatafilen.</span><span class="sxs-lookup"><span data-stu-id="0ea40-157">Specifies a location for the output file.</span></span>
<span data-ttu-id="0ea40-158">Ange en sökväg (valfritt) och fil namn med fil namns tillägget format.ps1XML.</span><span class="sxs-lookup"><span data-stu-id="0ea40-158">Enter a path (optional) and file name with a format.ps1xml file name extension.</span></span>
<span data-ttu-id="0ea40-159">Om du utelämnar sökvägen `Export-FormatData` skapas filen i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="0ea40-159">If you omit the path, `Export-FormatData` creates the file in the current directory.</span></span>

<span data-ttu-id="0ea40-160">Om du använder ett fil namns tillägg som inte är. ps1xml `Update-FormatData` känner inte cmdleten igen filen.</span><span class="sxs-lookup"><span data-stu-id="0ea40-160">If you use a file name extension other than .ps1xml, the `Update-FormatData` cmdlet will not recognize the file.</span></span>

<span data-ttu-id="0ea40-161">Om du anger en befintlig fil `Export-FormatData` skrivs filen över utan varning, om inte filen har attributet skrivskyddad.</span><span class="sxs-lookup"><span data-stu-id="0ea40-161">If you specify an existing file, `Export-FormatData` overwrites the file without warning, unless the file has the read-only attribute.</span></span> <span data-ttu-id="0ea40-162">Använd parametern **Force** om du vill skriva över en skrivskyddad fil.</span><span class="sxs-lookup"><span data-stu-id="0ea40-162">To overwrite a read-only file, use the **Force** parameter.</span></span> <span data-ttu-id="0ea40-163">Använd parametern **NoClobber** om du vill förhindra att filer skrivs över.</span><span class="sxs-lookup"><span data-stu-id="0ea40-163">To prevent files from being overwritten, use the **NoClobber** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases: FilePath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0ea40-164">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0ea40-164">CommonParameters</span></span>

<span data-ttu-id="0ea40-165">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0ea40-165">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0ea40-166">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="0ea40-166">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0ea40-167">INDATA</span><span class="sxs-lookup"><span data-stu-id="0ea40-167">INPUTS</span></span>

### <span data-ttu-id="0ea40-168">System. Management. Automation. ExtendedTypeDefinition</span><span class="sxs-lookup"><span data-stu-id="0ea40-168">System.Management.Automation.ExtendedTypeDefinition</span></span>

<span data-ttu-id="0ea40-169">Du kan skicka pipe- **ExtendedTypeDefinition** objekt från `Get-FormatData` till `Export-FormatData` .</span><span class="sxs-lookup"><span data-stu-id="0ea40-169">You can pipe **ExtendedTypeDefinition** objects from `Get-FormatData` to `Export-FormatData`.</span></span>

## <span data-ttu-id="0ea40-170">UTDATA</span><span class="sxs-lookup"><span data-stu-id="0ea40-170">OUTPUTS</span></span>

### <span data-ttu-id="0ea40-171">Inget</span><span class="sxs-lookup"><span data-stu-id="0ea40-171">None</span></span>

<span data-ttu-id="0ea40-172">`Export-FormatData` returnerar inga objekt.</span><span class="sxs-lookup"><span data-stu-id="0ea40-172">`Export-FormatData` does not return any objects.</span></span>
<span data-ttu-id="0ea40-173">Den genererar en fil och sparar den på den angivna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="0ea40-173">It generates a file and saves it in the specified path.</span></span>

## <span data-ttu-id="0ea40-174">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="0ea40-174">NOTES</span></span>

- <span data-ttu-id="0ea40-175">Om du vill använda en format fil, inklusive en exporterad formatering, måste körnings principen för sessionen tillåta att skript och konfigurationsfiler körs.</span><span class="sxs-lookup"><span data-stu-id="0ea40-175">To use any formatting file, including an exported formatting file, the execution policy for the session must allow scripts and configuration files to run.</span></span> <span data-ttu-id="0ea40-176">Mer information finns i [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="0ea40-176">For more information, see [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).</span></span>

## <span data-ttu-id="0ea40-177">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="0ea40-177">RELATED LINKS</span></span>

[<span data-ttu-id="0ea40-178">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="0ea40-178">Get-FormatData</span></span>](Get-FormatData.md)

[<span data-ttu-id="0ea40-179">Uppdatera – FormatData</span><span class="sxs-lookup"><span data-stu-id="0ea40-179">Update-FormatData</span></span>](Update-FormatData.md)