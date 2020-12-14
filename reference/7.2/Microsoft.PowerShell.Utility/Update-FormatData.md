---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-formatdata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-FormatData
ms.openlocfilehash: 91d0274e485573de96d9960fa49f6d327156a79a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709414"
---
# <span data-ttu-id="eca22-102">Update-FormatData</span><span class="sxs-lookup"><span data-stu-id="eca22-102">Update-FormatData</span></span>

## <span data-ttu-id="eca22-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="eca22-103">SYNOPSIS</span></span>
<span data-ttu-id="eca22-104">Uppdaterar formaterings data i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="eca22-104">Updates the formatting data in the current session.</span></span>

## <span data-ttu-id="eca22-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="eca22-105">SYNTAX</span></span>

```
Update-FormatData [[-AppendPath] <String[]>] [-PrependPath <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="eca22-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="eca22-106">DESCRIPTION</span></span>

<span data-ttu-id="eca22-107">`Update-FormatData`Cmdlet: en läser in formaterings data från att filerna formateras i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="eca22-107">The `Update-FormatData` cmdlet reloads the formatting data from formatting files into the current session.</span></span> <span data-ttu-id="eca22-108">Med den här cmdleten kan du uppdatera formaterings data utan att starta om PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eca22-108">This cmdlet lets you update the formatting data without restarting PowerShell.</span></span>

<span data-ttu-id="eca22-109">Utan parametrar `Update-FormatData` laddar om de filer som lästs in tidigare.</span><span class="sxs-lookup"><span data-stu-id="eca22-109">Without parameters, `Update-FormatData` reloads the formatting files that it loaded previously.</span></span>
<span data-ttu-id="eca22-110">Du kan använda parametrarna för `Update-FormatData` för att lägga till nya filer i sessionen.</span><span class="sxs-lookup"><span data-stu-id="eca22-110">You can use the parameters of `Update-FormatData` to add new formatting files to the session.</span></span>

<span data-ttu-id="eca22-111">Filer formateras som textfiler i XML-format med `format.ps1xml` fil namns tillägget.</span><span class="sxs-lookup"><span data-stu-id="eca22-111">Formatting files are text files in XML format with the `format.ps1xml` file name extension.</span></span> <span data-ttu-id="eca22-112">Formaterings data i filerna definierar hur Microsoft .NET Ramverks objekt i sessionen.</span><span class="sxs-lookup"><span data-stu-id="eca22-112">The formatting data in the files defines the display of Microsoft .NET Framework objects in the session.</span></span>

<span data-ttu-id="eca22-113">När PowerShell startar läses format data in från PowerShell-källkoden.</span><span class="sxs-lookup"><span data-stu-id="eca22-113">When PowerShell starts, it loads the format data from the PowerShell source code.</span></span> <span data-ttu-id="eca22-114">Du kan dock skapa anpassade format.ps1XML-filer för att uppdatera formateringen i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="eca22-114">However, you can create custom format.ps1xml files to update formatting in the current session.</span></span> <span data-ttu-id="eca22-115">Du kan använda `Update-FormatData` för att läsa in formaterings data i den aktuella sessionen utan att starta om PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eca22-115">You can use `Update-FormatData` to reload the formatting data into the current session without restarting PowerShell.</span></span> <span data-ttu-id="eca22-116">Detta är användbart när du har lagt till eller ändrat en format fil, men inte vill avbryta sessionen.</span><span class="sxs-lookup"><span data-stu-id="eca22-116">This is useful when you have added or changed a formatting file, but do not want to interrupt the session.</span></span>

<span data-ttu-id="eca22-117">Mer information om hur du formaterar filer i PowerShell finns i [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span><span class="sxs-lookup"><span data-stu-id="eca22-117">For more information about formatting files in PowerShell, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

## <span data-ttu-id="eca22-118">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="eca22-118">EXAMPLES</span></span>

### <span data-ttu-id="eca22-119">Exempel 1: Läs in tidigare inlästa filer igen</span><span class="sxs-lookup"><span data-stu-id="eca22-119">Example 1: Reload previously loaded formatting files</span></span>

```powershell
Update-FormatData
```

<span data-ttu-id="eca22-120">Det här kommandot laddar om de filer som lästes in tidigare.</span><span class="sxs-lookup"><span data-stu-id="eca22-120">This command reloads the formatting files that it loaded previously.</span></span>

### <span data-ttu-id="eca22-121">Exempel 2: läsa in filer för formatering och spåra och logga formatering</span><span class="sxs-lookup"><span data-stu-id="eca22-121">Example 2: Reload formatting files and trace and log formatting files</span></span>

```powershell
Update-FormatData -AppendPath "trace.format.ps1xml, log.format.ps1xml"
```

<span data-ttu-id="eca22-122">Detta kommando laddar om filerna till sessionen, inklusive två nya filer, Trace.format.ps1XML och Log.format.ps1XML.</span><span class="sxs-lookup"><span data-stu-id="eca22-122">This command reloads the formatting files into the session, including two new files, Trace.format.ps1xml and Log.format.ps1xml.</span></span>

<span data-ttu-id="eca22-123">Eftersom kommandot använder parametern **AppendPath** läses formateringen i de nya filerna in efter formateringen från de inbyggda filerna.</span><span class="sxs-lookup"><span data-stu-id="eca22-123">Because the command uses the **AppendPath** parameter, the formatting data in the new files is loaded after the formatting data from the built-in files.</span></span>

<span data-ttu-id="eca22-124">Parametern **AppendPath** används eftersom de nya filerna innehåller formaterings data för objekt som inte refereras till i de inbyggda filerna.</span><span class="sxs-lookup"><span data-stu-id="eca22-124">The **AppendPath** parameter is used because the new files contain formatting data for objects that are not referenced in the built-in files.</span></span>

### <span data-ttu-id="eca22-125">Exempel 3: redigera en fil format och Läs in den igen</span><span class="sxs-lookup"><span data-stu-id="eca22-125">Example 3: Edit a formatting file and reload it</span></span>

```powershell
Update-FormatData -PrependPath "c:\test\NewFiles.format.ps1xml"

# Edit the NewFiles.format.ps1 file.

Update-FormatData
```

<span data-ttu-id="eca22-126">Det här exemplet visar hur du läser in en fil format igen när du har redigerat den.</span><span class="sxs-lookup"><span data-stu-id="eca22-126">This example shows how to reload a formatting file after you have edited it.</span></span>

<span data-ttu-id="eca22-127">Det första kommandot lägger till NewFiles.format.ps1XML-filen i sessionen.</span><span class="sxs-lookup"><span data-stu-id="eca22-127">The first command adds the NewFiles.format.ps1xml file to the session.</span></span> <span data-ttu-id="eca22-128">Parametern **PrependPath** används eftersom filen innehåller format data för objekt som refereras till i de inbyggda filerna.</span><span class="sxs-lookup"><span data-stu-id="eca22-128">It uses the **PrependPath** parameter because the file contains formatting data for objects that are referenced in the built-in files.</span></span>

<span data-ttu-id="eca22-129">När du har lagt till NewFiles.format.ps1XML-filen och testat den i dessa sessioner redigerar författaren filen.</span><span class="sxs-lookup"><span data-stu-id="eca22-129">After adding the NewFiles.format.ps1xml file and testing it in these sessions, the author edits the file.</span></span>

<span data-ttu-id="eca22-130">Det andra kommandot använder `Update-FormatData` cmdleten för att läsa in formateringsattribut igen.</span><span class="sxs-lookup"><span data-stu-id="eca22-130">The second command uses the `Update-FormatData` cmdlet to reload the formatting files.</span></span> <span data-ttu-id="eca22-131">Eftersom NewFiles.format.ps1XML-filen tidigare lästes `Update-FormatData` in igen, laddar den automatiskt om den utan att använda parametrar.</span><span class="sxs-lookup"><span data-stu-id="eca22-131">Because the NewFiles.format.ps1xml file was previously loaded, `Update-FormatData` automatically reloads it without using parameters.</span></span>

## <span data-ttu-id="eca22-132">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="eca22-132">PARAMETERS</span></span>

### <span data-ttu-id="eca22-133">-AppendPath</span><span class="sxs-lookup"><span data-stu-id="eca22-133">-AppendPath</span></span>

<span data-ttu-id="eca22-134">Anger formateringsattribut som denna cmdlet lägger till i sessionen.</span><span class="sxs-lookup"><span data-stu-id="eca22-134">Specifies formatting files that this cmdlet adds to the session.</span></span> <span data-ttu-id="eca22-135">Filerna läses in efter att PowerShell har läst in de inbyggda filerna.</span><span class="sxs-lookup"><span data-stu-id="eca22-135">The files are loaded after PowerShell loads the built-in formatting files.</span></span>

<span data-ttu-id="eca22-136">När .NET-objekt formateras, använder PowerShell den första format definition som hittas för varje .NET-typ.</span><span class="sxs-lookup"><span data-stu-id="eca22-136">When formatting .NET objects, PowerShell uses the first formatting definition that it finds for each .NET type.</span></span> <span data-ttu-id="eca22-137">Om du använder parametern **AppendPath** söker PowerShell igenom data från de inbyggda filerna innan de påträffar de format data som du lägger till.</span><span class="sxs-lookup"><span data-stu-id="eca22-137">If you use the **AppendPath** parameter, PowerShell searches the data from the built-in files before it encounters the formatting data that you are adding.</span></span>

<span data-ttu-id="eca22-138">Använd den här parametern för att lägga till en fil som formaterar ett .NET-objekt som inte refereras till i de inbyggda filerna.</span><span class="sxs-lookup"><span data-stu-id="eca22-138">Use this parameter to add a file that formats a .NET object that is not referenced in the built-in formatting files.</span></span>

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

### <span data-ttu-id="eca22-139">-PrependPath</span><span class="sxs-lookup"><span data-stu-id="eca22-139">-PrependPath</span></span>

<span data-ttu-id="eca22-140">Anger formateringsattribut som denna cmdlet lägger till i sessionen.</span><span class="sxs-lookup"><span data-stu-id="eca22-140">Specifies formatting files that this cmdlet adds to the session.</span></span> <span data-ttu-id="eca22-141">Filerna läses in innan PowerShell läser in de inbyggda filerna.</span><span class="sxs-lookup"><span data-stu-id="eca22-141">The files are loaded before PowerShell loads the built-in formatting files.</span></span>

<span data-ttu-id="eca22-142">När .NET-objekt formateras, använder PowerShell den första format definition som hittas för varje .NET-typ.</span><span class="sxs-lookup"><span data-stu-id="eca22-142">When formatting .NET objects, PowerShell uses the first formatting definition that it finds for each .NET type.</span></span> <span data-ttu-id="eca22-143">Om du använder parametern **PrependPath** söker PowerShell igenom data från filerna som du lägger till innan de påträffar formaterings data från de inbyggda filerna.</span><span class="sxs-lookup"><span data-stu-id="eca22-143">If you use the **PrependPath** parameter, PowerShell searches the data from the files that you are adding before it encounters the formatting data from the built-in files.</span></span>

<span data-ttu-id="eca22-144">Använd den här parametern för att lägga till en fil som formaterar ett .NET-objekt som också refereras till i de inbyggda filerna.</span><span class="sxs-lookup"><span data-stu-id="eca22-144">Use this parameter to add a file that formats a .NET object that is also referenced in the built-in formatting files.</span></span>

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

### <span data-ttu-id="eca22-145">-Confirm</span><span class="sxs-lookup"><span data-stu-id="eca22-145">-Confirm</span></span>

<span data-ttu-id="eca22-146">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="eca22-146">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="eca22-147">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="eca22-147">-WhatIf</span></span>

<span data-ttu-id="eca22-148">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="eca22-148">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="eca22-149">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="eca22-149">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="eca22-150">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="eca22-150">CommonParameters</span></span>

<span data-ttu-id="eca22-151">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="eca22-151">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="eca22-152">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="eca22-152">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="eca22-153">INDATA</span><span class="sxs-lookup"><span data-stu-id="eca22-153">INPUTS</span></span>

### <span data-ttu-id="eca22-154">System. String</span><span class="sxs-lookup"><span data-stu-id="eca22-154">System.String</span></span>

<span data-ttu-id="eca22-155">Du kan lägga till en sträng som innehåller sökvägen till `Update-FormatData` .</span><span class="sxs-lookup"><span data-stu-id="eca22-155">You can pipe a string that contains the append path to `Update-FormatData`.</span></span>

## <span data-ttu-id="eca22-156">UTDATA</span><span class="sxs-lookup"><span data-stu-id="eca22-156">OUTPUTS</span></span>

### <span data-ttu-id="eca22-157">Inga</span><span class="sxs-lookup"><span data-stu-id="eca22-157">None</span></span>

<span data-ttu-id="eca22-158">Cmdleten returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="eca22-158">The cmdlet does not return any output.</span></span>

## <span data-ttu-id="eca22-159">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="eca22-159">NOTES</span></span>

- <span data-ttu-id="eca22-160">`Update-FormatData` uppdaterar också formaterings data för kommandon i sessionen som har importer ATS från moduler.</span><span class="sxs-lookup"><span data-stu-id="eca22-160">`Update-FormatData` also updates the formatting data for commands in the session that were imported from modules.</span></span> <span data-ttu-id="eca22-161">Om format filen för en modul ändras kan du köra ett `Update-FormatData` kommando för att uppdatera formateringen för importerade kommandon.</span><span class="sxs-lookup"><span data-stu-id="eca22-161">If the formatting file for a module changes, you can run an `Update-FormatData` command to update the formatting data for imported commands.</span></span> <span data-ttu-id="eca22-162">Du behöver inte importera modulen igen.</span><span class="sxs-lookup"><span data-stu-id="eca22-162">You do not need to import the module again.</span></span>

## <span data-ttu-id="eca22-163">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="eca22-163">RELATED LINKS</span></span>

[<span data-ttu-id="eca22-164">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="eca22-164">Get-FormatData</span></span>](Get-FormatData.md)

[<span data-ttu-id="eca22-165">Exportera – FormatData</span><span class="sxs-lookup"><span data-stu-id="eca22-165">Export-FormatData</span></span>](Export-FormatData.md)
