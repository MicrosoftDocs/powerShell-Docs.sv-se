---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-formatdata?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-FormatData
ms.openlocfilehash: 209e5cf9ab5809767b4135817640ffe7c2d69175
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262490"
---
# <span data-ttu-id="ea6e9-103">Update-FormatData</span><span class="sxs-lookup"><span data-stu-id="ea6e9-103">Update-FormatData</span></span>

## <span data-ttu-id="ea6e9-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="ea6e9-104">SYNOPSIS</span></span>
<span data-ttu-id="ea6e9-105">Uppdaterar formaterings data i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-105">Updates the formatting data in the current session.</span></span>

## <span data-ttu-id="ea6e9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ea6e9-106">SYNTAX</span></span>

```
Update-FormatData [[-AppendPath] <String[]>] [-PrependPath <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="ea6e9-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ea6e9-107">DESCRIPTION</span></span>

<span data-ttu-id="ea6e9-108">`Update-FormatData`Cmdlet: en läser in formaterings data från att filerna formateras i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-108">The `Update-FormatData` cmdlet reloads the formatting data from formatting files into the current session.</span></span> <span data-ttu-id="ea6e9-109">Med den här cmdleten kan du uppdatera formaterings data utan att starta om PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-109">This cmdlet lets you update the formatting data without restarting PowerShell.</span></span>

<span data-ttu-id="ea6e9-110">Utan parametrar `Update-FormatData` laddar om de filer som lästs in tidigare.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-110">Without parameters, `Update-FormatData` reloads the formatting files that it loaded previously.</span></span>
<span data-ttu-id="ea6e9-111">Du kan använda parametrarna för `Update-FormatData` för att lägga till nya filer i sessionen.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-111">You can use the parameters of `Update-FormatData` to add new formatting files to the session.</span></span>

<span data-ttu-id="ea6e9-112">Filer formateras som textfiler i XML-format med `format.ps1xml` fil namns tillägget.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-112">Formatting files are text files in XML format with the `format.ps1xml` file name extension.</span></span> <span data-ttu-id="ea6e9-113">Formaterings data i filerna definierar hur Microsoft .NET Ramverks objekt i sessionen.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-113">The formatting data in the files defines the display of Microsoft .NET Framework objects in the session.</span></span>

<span data-ttu-id="ea6e9-114">När PowerShell startar läses format data in från PowerShell-källkoden.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-114">When PowerShell starts, it loads the format data from the PowerShell source code.</span></span> <span data-ttu-id="ea6e9-115">Du kan dock skapa anpassade format.ps1XML-filer för att uppdatera formateringen i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-115">However, you can create custom format.ps1xml files to update formatting in the current session.</span></span> <span data-ttu-id="ea6e9-116">Du kan använda `Update-FormatData` för att läsa in formaterings data i den aktuella sessionen utan att starta om PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-116">You can use `Update-FormatData` to reload the formatting data into the current session without restarting PowerShell.</span></span> <span data-ttu-id="ea6e9-117">Detta är användbart när du har lagt till eller ändrat en format fil, men inte vill avbryta sessionen.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-117">This is useful when you have added or changed a formatting file, but do not want to interrupt the session.</span></span>

<span data-ttu-id="ea6e9-118">Mer information om hur du formaterar filer i PowerShell finns i [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span><span class="sxs-lookup"><span data-stu-id="ea6e9-118">For more information about formatting files in PowerShell, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

## <span data-ttu-id="ea6e9-119">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="ea6e9-119">EXAMPLES</span></span>

### <span data-ttu-id="ea6e9-120">Exempel 1: Läs in tidigare inlästa filer igen</span><span class="sxs-lookup"><span data-stu-id="ea6e9-120">Example 1: Reload previously loaded formatting files</span></span>

```powershell
Update-FormatData
```

<span data-ttu-id="ea6e9-121">Det här kommandot laddar om de filer som lästes in tidigare.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-121">This command reloads the formatting files that it loaded previously.</span></span>

### <span data-ttu-id="ea6e9-122">Exempel 2: läsa in filer för formatering och spåra och logga formatering</span><span class="sxs-lookup"><span data-stu-id="ea6e9-122">Example 2: Reload formatting files and trace and log formatting files</span></span>

```powershell
Update-FormatData -AppendPath "trace.format.ps1xml, log.format.ps1xml"
```

<span data-ttu-id="ea6e9-123">Detta kommando laddar om filerna till sessionen, inklusive två nya filer, Trace.format.ps1XML och Log.format.ps1XML.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-123">This command reloads the formatting files into the session, including two new files, Trace.format.ps1xml and Log.format.ps1xml.</span></span>

<span data-ttu-id="ea6e9-124">Eftersom kommandot använder parametern **AppendPath** läses formateringen i de nya filerna in efter formateringen från de inbyggda filerna.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-124">Because the command uses the **AppendPath** parameter, the formatting data in the new files is loaded after the formatting data from the built-in files.</span></span>

<span data-ttu-id="ea6e9-125">Parametern **AppendPath** används eftersom de nya filerna innehåller formaterings data för objekt som inte refereras till i de inbyggda filerna.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-125">The **AppendPath** parameter is used because the new files contain formatting data for objects that are not referenced in the built-in files.</span></span>

### <span data-ttu-id="ea6e9-126">Exempel 3: redigera en fil format och Läs in den igen</span><span class="sxs-lookup"><span data-stu-id="ea6e9-126">Example 3: Edit a formatting file and reload it</span></span>

```powershell
Update-FormatData -PrependPath "c:\test\NewFiles.format.ps1xml"

# Edit the NewFiles.format.ps1 file.

Update-FormatData
```

<span data-ttu-id="ea6e9-127">Det här exemplet visar hur du läser in en fil format igen när du har redigerat den.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-127">This example shows how to reload a formatting file after you have edited it.</span></span>

<span data-ttu-id="ea6e9-128">Det första kommandot lägger till NewFiles.format.ps1XML-filen i sessionen.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-128">The first command adds the NewFiles.format.ps1xml file to the session.</span></span> <span data-ttu-id="ea6e9-129">Parametern **PrependPath** används eftersom filen innehåller format data för objekt som refereras till i de inbyggda filerna.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-129">It uses the **PrependPath** parameter because the file contains formatting data for objects that are referenced in the built-in files.</span></span>

<span data-ttu-id="ea6e9-130">När du har lagt till NewFiles.format.ps1XML-filen och testat den i dessa sessioner redigerar författaren filen.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-130">After adding the NewFiles.format.ps1xml file and testing it in these sessions, the author edits the file.</span></span>

<span data-ttu-id="ea6e9-131">Det andra kommandot använder `Update-FormatData` cmdleten för att läsa in formateringsattribut igen.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-131">The second command uses the `Update-FormatData` cmdlet to reload the formatting files.</span></span> <span data-ttu-id="ea6e9-132">Eftersom NewFiles.format.ps1XML-filen tidigare lästes `Update-FormatData` in igen, laddar den automatiskt om den utan att använda parametrar.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-132">Because the NewFiles.format.ps1xml file was previously loaded, `Update-FormatData` automatically reloads it without using parameters.</span></span>

## <span data-ttu-id="ea6e9-133">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="ea6e9-133">PARAMETERS</span></span>

### <span data-ttu-id="ea6e9-134">-AppendPath</span><span class="sxs-lookup"><span data-stu-id="ea6e9-134">-AppendPath</span></span>

<span data-ttu-id="ea6e9-135">Anger formateringsattribut som denna cmdlet lägger till i sessionen.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-135">Specifies formatting files that this cmdlet adds to the session.</span></span> <span data-ttu-id="ea6e9-136">Filerna läses in efter att PowerShell har läst in de inbyggda filerna.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-136">The files are loaded after PowerShell loads the built-in formatting files.</span></span>

<span data-ttu-id="ea6e9-137">När .NET-objekt formateras, använder PowerShell den första format definition som hittas för varje .NET-typ.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-137">When formatting .NET objects, PowerShell uses the first formatting definition that it finds for each .NET type.</span></span> <span data-ttu-id="ea6e9-138">Om du använder parametern **AppendPath** söker PowerShell igenom data från de inbyggda filerna innan de påträffar de format data som du lägger till.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-138">If you use the **AppendPath** parameter, PowerShell searches the data from the built-in files before it encounters the formatting data that you are adding.</span></span>

<span data-ttu-id="ea6e9-139">Använd den här parametern för att lägga till en fil som formaterar ett .NET-objekt som inte refereras till i de inbyggda filerna.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-139">Use this parameter to add a file that formats a .NET object that is not referenced in the built-in formatting files.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSPath, Path

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ea6e9-140">-PrependPath</span><span class="sxs-lookup"><span data-stu-id="ea6e9-140">-PrependPath</span></span>

<span data-ttu-id="ea6e9-141">Anger formateringsattribut som denna cmdlet lägger till i sessionen.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-141">Specifies formatting files that this cmdlet adds to the session.</span></span> <span data-ttu-id="ea6e9-142">Filerna läses in innan PowerShell läser in de inbyggda filerna.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-142">The files are loaded before PowerShell loads the built-in formatting files.</span></span>

<span data-ttu-id="ea6e9-143">När .NET-objekt formateras, använder PowerShell den första format definition som hittas för varje .NET-typ.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-143">When formatting .NET objects, PowerShell uses the first formatting definition that it finds for each .NET type.</span></span> <span data-ttu-id="ea6e9-144">Om du använder parametern **PrependPath** söker PowerShell igenom data från filerna som du lägger till innan de påträffar formaterings data från de inbyggda filerna.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-144">If you use the **PrependPath** parameter, PowerShell searches the data from the files that you are adding before it encounters the formatting data from the built-in files.</span></span>

<span data-ttu-id="ea6e9-145">Använd den här parametern för att lägga till en fil som formaterar ett .NET-objekt som också refereras till i de inbyggda filerna.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-145">Use this parameter to add a file that formats a .NET object that is also referenced in the built-in formatting files.</span></span>

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

### <span data-ttu-id="ea6e9-146">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ea6e9-146">-Confirm</span></span>

<span data-ttu-id="ea6e9-147">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-147">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ea6e9-148">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ea6e9-148">-WhatIf</span></span>

<span data-ttu-id="ea6e9-149">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-149">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="ea6e9-150">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-150">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="ea6e9-151">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ea6e9-151">CommonParameters</span></span>

<span data-ttu-id="ea6e9-152">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-152">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ea6e9-153">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ea6e9-153">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ea6e9-154">INDATA</span><span class="sxs-lookup"><span data-stu-id="ea6e9-154">INPUTS</span></span>

### <span data-ttu-id="ea6e9-155">System. String</span><span class="sxs-lookup"><span data-stu-id="ea6e9-155">System.String</span></span>

<span data-ttu-id="ea6e9-156">Du kan lägga till en sträng som innehåller sökvägen till `Update-FormatData` .</span><span class="sxs-lookup"><span data-stu-id="ea6e9-156">You can pipe a string that contains the append path to `Update-FormatData`.</span></span>

## <span data-ttu-id="ea6e9-157">UTDATA</span><span class="sxs-lookup"><span data-stu-id="ea6e9-157">OUTPUTS</span></span>

### <span data-ttu-id="ea6e9-158">Inget</span><span class="sxs-lookup"><span data-stu-id="ea6e9-158">None</span></span>

<span data-ttu-id="ea6e9-159">Cmdleten returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-159">The cmdlet does not return any output.</span></span>

## <span data-ttu-id="ea6e9-160">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="ea6e9-160">NOTES</span></span>

- <span data-ttu-id="ea6e9-161">`Update-FormatData` uppdaterar också formaterings data för kommandon i sessionen som har importer ATS från moduler.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-161">`Update-FormatData` also updates the formatting data for commands in the session that were imported from modules.</span></span> <span data-ttu-id="ea6e9-162">Om format filen för en modul ändras kan du köra ett `Update-FormatData` kommando för att uppdatera formateringen för importerade kommandon.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-162">If the formatting file for a module changes, you can run an `Update-FormatData` command to update the formatting data for imported commands.</span></span> <span data-ttu-id="ea6e9-163">Du behöver inte importera modulen igen.</span><span class="sxs-lookup"><span data-stu-id="ea6e9-163">You do not need to import the module again.</span></span>

## <span data-ttu-id="ea6e9-164">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="ea6e9-164">RELATED LINKS</span></span>

[<span data-ttu-id="ea6e9-165">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="ea6e9-165">Get-FormatData</span></span>](Get-FormatData.md)

[<span data-ttu-id="ea6e9-166">Exportera – FormatData</span><span class="sxs-lookup"><span data-stu-id="ea6e9-166">Export-FormatData</span></span>](Export-FormatData.md)
