---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/export-console?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Console
ms.openlocfilehash: 7b643b5f9b6868a5da988b19b65dead24f986f67
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263636"
---
# <span data-ttu-id="88e9d-103">Export-Console</span><span class="sxs-lookup"><span data-stu-id="88e9d-103">Export-Console</span></span>

## <span data-ttu-id="88e9d-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="88e9d-104">SYNOPSIS</span></span>
<span data-ttu-id="88e9d-105">Exporterar namn på snapin-moduler i den aktuella sessionen till en konsol fil.</span><span class="sxs-lookup"><span data-stu-id="88e9d-105">Exports the names of snap-ins in the current session to a console file.</span></span>

## <span data-ttu-id="88e9d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="88e9d-106">SYNTAX</span></span>

```
Export-Console [[-Path] <String>] [-Force] [-NoClobber] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="88e9d-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="88e9d-107">DESCRIPTION</span></span>
<span data-ttu-id="88e9d-108">Cmdleten **export-Console** exporterar namnen på Windows PowerShell-snapin-modulerna i den aktuella sessionen till en Windows PowerShell-konsol fil (. psc1).</span><span class="sxs-lookup"><span data-stu-id="88e9d-108">The **Export-Console** cmdlet exports the names of the Windows PowerShell snap-ins in the current session to a Windows PowerShell console file (.psc1).</span></span>
<span data-ttu-id="88e9d-109">Du kan använda denna cmdlet för att spara snapin-modulerna som ska användas i framtida sessioner.</span><span class="sxs-lookup"><span data-stu-id="88e9d-109">You can use this cmdlet to save the snap-ins for use in future sessions.</span></span>

<span data-ttu-id="88e9d-110">Om du vill lägga till snapin-modulerna i. psc1-konsol filen i en session startar du Windows PowerShell (Powershell.exe) på kommando raden genom att använda Cmd.exe eller en annan Windows PowerShell-session och använder sedan *PSConsoleFile* -parametern för Powershell.exe för att ange konsol filen.</span><span class="sxs-lookup"><span data-stu-id="88e9d-110">To add the snap-ins in the .psc1 console file to a session, start Windows PowerShell (Powershell.exe) at the command line by using Cmd.exe or another Windows PowerShell session, and then use the *PSConsoleFile* parameter of Powershell.exe to specify the console file.</span></span>

<span data-ttu-id="88e9d-111">Mer information om snapin-moduler för Windows PowerShell finns i about_PSSnapins.</span><span class="sxs-lookup"><span data-stu-id="88e9d-111">For more information about Windows PowerShell snap-ins, see about_PSSnapins.</span></span>

## <span data-ttu-id="88e9d-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="88e9d-112">EXAMPLES</span></span>

### <span data-ttu-id="88e9d-113">Exempel 1: exportera namnen på snapin-modulerna i den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="88e9d-113">Example 1: Export the names of snap-ins in the current session</span></span>

```
PS C:\> Export-Console -Path $pshome\Consoles\ConsoleS1.psc1
```

<span data-ttu-id="88e9d-114">Detta kommando exporterar namnen på Windows PowerShell-snapin-modulerna i den aktuella sessionen till filen ConsoleS1. psc1 i mappen konsoler i installationsmappen för Windows PowerShell $pshome.</span><span class="sxs-lookup"><span data-stu-id="88e9d-114">This command exports the names of Windows PowerShell snap-ins in the current session to the ConsoleS1.psc1 file in the Consoles folder of the Windows PowerShell installation folder, $pshome.</span></span>

### <span data-ttu-id="88e9d-115">Exempel 2: exportera namn på snapin-moduler till den senaste konsol filen</span><span class="sxs-lookup"><span data-stu-id="88e9d-115">Example 2: Export the names of snap-ins to the most recent console file</span></span>

```
PS C:\> Export-Console
```

<span data-ttu-id="88e9d-116">Detta kommando exporterar namnen på Windows PowerShell-snapin-moduler från den aktuella sessionen till Windows PowerShell-konsolen som senast användes i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="88e9d-116">This command exports the names of Windows PowerShell snap-ins from current session to the Windows PowerShell console file that was most recently used in the current session.</span></span>
<span data-ttu-id="88e9d-117">Det skriver över det tidigare fil innehållet.</span><span class="sxs-lookup"><span data-stu-id="88e9d-117">It overwrites the previous file contents.</span></span>

<span data-ttu-id="88e9d-118">Om du inte har exporterat en konsol fil under den aktuella sessionen uppmanas du att ange behörighet för att fortsätta och sedan ange ett fil namn.</span><span class="sxs-lookup"><span data-stu-id="88e9d-118">If you have not exported a console file during the current session, you are prompted for permission to continue and then prompted for a file name.</span></span>

### <span data-ttu-id="88e9d-119">Exempel 3: Lägg till en snapin-modul och exportera namnen på snapin-modulerna</span><span class="sxs-lookup"><span data-stu-id="88e9d-119">Example 3: Add a snap-in and export the names of snap-ins</span></span>

```
PS C:\> Add-PSSnapin NewPSSnapin
PS C:\> Export-Console -path NewPSSnapinConsole.psc1
PS C:\> powershell.exe -PsConsoleFile NewPsSnapinConsole.psc1
```

<span data-ttu-id="88e9d-120">Dessa kommandon lägger till Windows PowerShell-snapin-modulen NewPSSnapin i den aktuella sessionen, exporterar namnen på Windows PowerShell-snapin-modulerna i den aktuella sessionen till en konsol fil och startar sedan en Windows PowerShell-session med konsol filen.</span><span class="sxs-lookup"><span data-stu-id="88e9d-120">These commands add the NewPSSnapin Windows PowerShell snap-in to the current session, export the names of Windows PowerShell snap-ins in the current session to a console file, and then start a Windows PowerShell session with the console file.</span></span>

<span data-ttu-id="88e9d-121">Det första kommandot använder cmdleten **Add-PSSnapin** för att lägga till snapin-modulen NewPSSnapin i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="88e9d-121">The first command uses the **Add-PSSnapin** cmdlet to add the NewPSSnapin snap-in to the current session.</span></span>
<span data-ttu-id="88e9d-122">Du kan bara lägga till Windows PowerShell-snapin-moduler som är registrerade i systemet.</span><span class="sxs-lookup"><span data-stu-id="88e9d-122">You can only add Windows PowerShell snap-ins that are registered on your system.</span></span>

<span data-ttu-id="88e9d-123">Det andra kommandot exporterar Windows PowerShell-snapin-modulernas namn till filen NewPSSnapinConsole. psc1.</span><span class="sxs-lookup"><span data-stu-id="88e9d-123">The second command exports the Windows PowerShell snap-in names to the NewPSSnapinConsole.psc1 file.</span></span>

<span data-ttu-id="88e9d-124">Det tredje kommandot startar Windows PowerShell med filen NewPSSnapinConsole. psc1.</span><span class="sxs-lookup"><span data-stu-id="88e9d-124">The third command starts Windows PowerShell with the NewPSSnapinConsole.psc1 file.</span></span>
<span data-ttu-id="88e9d-125">Eftersom konsol filen innehåller namnet på Windows PowerShell-snapin-modulen är cmdletarna och providers i snapin-modulen tillgängliga i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="88e9d-125">Because the console file includes the Windows PowerShell snap-in name, the cmdlets and providers in the snap-in are available in the current session.</span></span>

### <span data-ttu-id="88e9d-126">Exempel 4: exportera namn på snapin-moduler till en angiven plats</span><span class="sxs-lookup"><span data-stu-id="88e9d-126">Example 4: Export names of snap-ins to a specified location</span></span>

```
PS C:\> export-console -path Console01
PS C:\> notepad console01.psc1
<?xml version="1.0" encoding="utf-8"?>
<PSConsoleFile ConsoleSchemaVersion="1.0">
  <PSVersion>2.0</PSVersion>
  <PSSnapIns>
     <PSSnapIn Name="NewPSSnapin" />
  </PSSnapIns>
</PSConsoleFile>
```

<span data-ttu-id="88e9d-127">Detta kommando exporterar namnen på Windows PowerShell-snapin-modulerna i den aktuella sessionen till filen Console01. psc1 i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="88e9d-127">This command exports the names of the Windows PowerShell snap-ins in the current session to the Console01.psc1 file in the current directory.</span></span>

<span data-ttu-id="88e9d-128">Det andra kommandot visar innehållet i filen Console01. psc1 i anteckningar.</span><span class="sxs-lookup"><span data-stu-id="88e9d-128">The second command displays the contents of the Console01.psc1 file in Notepad.</span></span>

### <span data-ttu-id="88e9d-129">Exempel 5: Bestäm konsol filen som ska uppdateras</span><span class="sxs-lookup"><span data-stu-id="88e9d-129">Example 5: Determine the console file to update</span></span>

```
PS C:\> powershell.exe -PSConsoleFile Console01.psc1
PS C:\> Add-PSSnapin MySnapin
PS C:\> Export-Console NewConsole.psc1
PS C:\> $ConsoleFileName
PS C:\> Add-PSSnapin SnapIn03
PS C:\> Export-Console
```

<span data-ttu-id="88e9d-130">I det här exemplet visas hur du använder den automatiska variabeln $ConsoleFileName för att fastställa konsol filen som ska uppdateras om du använder **export-konsolen** utan parametern *Path* -värde.</span><span class="sxs-lookup"><span data-stu-id="88e9d-130">This example shows how to use the $ConsoleFileName automatic variable to determine the console file that will be updated if you use **Export-Console** without a *Path* parameter value.</span></span>

<span data-ttu-id="88e9d-131">Det första kommandot använder *PSConsoleFile* -parametern för PowerShell.exe för att öppna Windows PowerShell med filen Console01. psc1.</span><span class="sxs-lookup"><span data-stu-id="88e9d-131">The first command uses the *PSConsoleFile* parameter of PowerShell.exe to open Windows PowerShell with the Console01.psc1 file.</span></span>

<span data-ttu-id="88e9d-132">Det andra kommandot använder cmdleten **Add-PSSnapin** för att lägga till snapin-modulen för snap-in-Windows PowerShell i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="88e9d-132">The second command uses the **Add-PSSnapin** cmdlet to add the MySnapin Windows PowerShell snap-in to the current session.</span></span>

<span data-ttu-id="88e9d-133">Det tredje kommandot använder cmdleten **export-Console** för att exportera namnen på alla Windows PowerShell-snapin-moduler i sessionen till filen NewConsole. psc1.</span><span class="sxs-lookup"><span data-stu-id="88e9d-133">The third command uses the **Export-Console** cmdlet to export the names of all the Windows PowerShell snap-ins in the session to the NewConsole.psc1 file.</span></span>

<span data-ttu-id="88e9d-134">Det fjärde kommandot visar $ConsoleFileName variabeln.</span><span class="sxs-lookup"><span data-stu-id="88e9d-134">The fourth command displays the $ConsoleFileName variable.</span></span>
<span data-ttu-id="88e9d-135">Den innehåller den senast använda konsol filen.</span><span class="sxs-lookup"><span data-stu-id="88e9d-135">It contains the most recently used console file.</span></span>
<span data-ttu-id="88e9d-136">Exemplet på utdata visar att NewConsole.ps1 är den senast använda filen.</span><span class="sxs-lookup"><span data-stu-id="88e9d-136">The sample output shows that NewConsole.ps1 is the most recently used file.</span></span>

<span data-ttu-id="88e9d-137">Det femte kommandot lägger till SnapIn03 i den aktuella konsolen.</span><span class="sxs-lookup"><span data-stu-id="88e9d-137">The fifth command adds SnapIn03 to the current console.</span></span>

<span data-ttu-id="88e9d-138">Det sjätte kommandot använder cmdleten **export-Console** utan en *Sök vägs* parameter.</span><span class="sxs-lookup"><span data-stu-id="88e9d-138">The sixth command uses the **Export-Console** cmdlet without a *Path* parameter.</span></span>
<span data-ttu-id="88e9d-139">Detta kommando exporterar namnen på alla Windows PowerShell-snapin-moduler i den aktuella sessionen till den senast använda filen, NewConsole. psc1.</span><span class="sxs-lookup"><span data-stu-id="88e9d-139">This command exports the names of all the Windows PowerShell snap-ins in the current session to the most recently used file, NewConsole.psc1.</span></span>

## <span data-ttu-id="88e9d-140">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="88e9d-140">PARAMETERS</span></span>

### <span data-ttu-id="88e9d-141">-Force</span><span class="sxs-lookup"><span data-stu-id="88e9d-141">-Force</span></span>
<span data-ttu-id="88e9d-142">Anger att denna cmdlet skriver över data i en konsol fil utan varning, även om filen har attributet skrivskyddad.</span><span class="sxs-lookup"><span data-stu-id="88e9d-142">Indicates that this cmdlet overwrites the data in a console file without warning, even if the file has the read-only attribute.</span></span>
<span data-ttu-id="88e9d-143">Det skrivskyddade attributet har ändrats och återställs inte när kommandot har slutförts.</span><span class="sxs-lookup"><span data-stu-id="88e9d-143">The read-only attribute is changed and is not reset when the command finishes.</span></span>

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

### <span data-ttu-id="88e9d-144">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="88e9d-144">-NoClobber</span></span>
<span data-ttu-id="88e9d-145">Anger att denna cmdlet inte skriver över en befintlig konsol fil.</span><span class="sxs-lookup"><span data-stu-id="88e9d-145">Indicates that this cmdlet does not overwrite  an existing console file.</span></span>
<span data-ttu-id="88e9d-146">Som standard skriver **export konsolen** över filen utan varning om en fil förekommer i den angivna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="88e9d-146">By default, if a file occurs in the specified path, **Export-Console** overwrites the file without warning.</span></span>

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

### <span data-ttu-id="88e9d-147">-Path</span><span class="sxs-lookup"><span data-stu-id="88e9d-147">-Path</span></span>
<span data-ttu-id="88e9d-148">Anger en sökväg och ett fil namn för konsol filen (\*. psc1).</span><span class="sxs-lookup"><span data-stu-id="88e9d-148">Specifies a path and file name for the console file (\*.psc1).</span></span>
<span data-ttu-id="88e9d-149">Ange en valfri sökväg och ett namn.</span><span class="sxs-lookup"><span data-stu-id="88e9d-149">Enter an optional path and name.</span></span>
<span data-ttu-id="88e9d-150">Jokertecken tillåts inte.</span><span class="sxs-lookup"><span data-stu-id="88e9d-150">Wildcard characters are not permitted.</span></span>

<span data-ttu-id="88e9d-151">Om du bara anger ett fil namn skapar **export konsolen** en fil med det namnet och fil namns tillägget. psc1 i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="88e9d-151">If you specify only a file name, **Export-Console** creates a file that has that name and the .psc1 file name extension in the current directory.</span></span>

<span data-ttu-id="88e9d-152">Den här parametern krävs om du inte har öppnat Windows PowerShell med parametern *PSConsoleFile* eller exporterat en konsol fil under den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="88e9d-152">This parameter is required unless you have opened Windows PowerShell with the *PSConsoleFile* parameter or exported a console file during the current session.</span></span>
<span data-ttu-id="88e9d-153">Det krävs också när du använder parametern *NoClobber* för att förhindra att den aktuella konsol filen skrivs över.</span><span class="sxs-lookup"><span data-stu-id="88e9d-153">It is also required when you use the *NoClobber* parameter to prevent the current console file from being overwritten.</span></span>

<span data-ttu-id="88e9d-154">Om du utelämnar den här parametern skriver **export konsolen** över konsol filen som användes senast under den här sessionen.</span><span class="sxs-lookup"><span data-stu-id="88e9d-154">If you omit this parameter, **Export-Console** overwrites the console file that was used most recently in this session.</span></span>
<span data-ttu-id="88e9d-155">Sökvägen till den senast använda konsol filen lagras i värdet för den $ConsoleFileName automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="88e9d-155">The path of the most recently used console file is stored in the value of the $ConsoleFileName automatic variable.</span></span>
<span data-ttu-id="88e9d-156">Mer information finns i about_Automatic_Variables.</span><span class="sxs-lookup"><span data-stu-id="88e9d-156">For more information, see about_Automatic_Variables.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="88e9d-157">-Confirm</span><span class="sxs-lookup"><span data-stu-id="88e9d-157">-Confirm</span></span>
<span data-ttu-id="88e9d-158">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="88e9d-158">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="88e9d-159">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="88e9d-159">-WhatIf</span></span>
<span data-ttu-id="88e9d-160">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="88e9d-160">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="88e9d-161">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="88e9d-161">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="88e9d-162">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="88e9d-162">CommonParameters</span></span>
<span data-ttu-id="88e9d-163">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="88e9d-163">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="88e9d-164">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="88e9d-164">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="88e9d-165">INDATA</span><span class="sxs-lookup"><span data-stu-id="88e9d-165">INPUTS</span></span>

### <span data-ttu-id="88e9d-166">System. String</span><span class="sxs-lookup"><span data-stu-id="88e9d-166">System.String</span></span>
<span data-ttu-id="88e9d-167">Du kan skicka en Sök vägs sträng till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="88e9d-167">You can pipe a path string to this cmdlet.</span></span>

## <span data-ttu-id="88e9d-168">UTDATA</span><span class="sxs-lookup"><span data-stu-id="88e9d-168">OUTPUTS</span></span>

### <span data-ttu-id="88e9d-169">System. IO. FileInfo</span><span class="sxs-lookup"><span data-stu-id="88e9d-169">System.IO.FileInfo</span></span>
<span data-ttu-id="88e9d-170">Denna cmdlet skapar en fil som innehåller de exporterade aliasen.</span><span class="sxs-lookup"><span data-stu-id="88e9d-170">This cmdlet creates a file that contains the exported aliases.</span></span>

## <span data-ttu-id="88e9d-171">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="88e9d-171">NOTES</span></span>

* <span data-ttu-id="88e9d-172">När en konsol fil (. psc1) används för att starta sessionen lagras namnet på konsol filen automatiskt i $ConsoleFileName automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="88e9d-172">When a console file (.psc1) is used to start the session, the name of the console file is automatically stored in the $ConsoleFileName automatic variable.</span></span> <span data-ttu-id="88e9d-173">Värdet för $ConsoleFileName uppdateras när du använder parametern *Path* i **export-konsolen** för att ange en ny konsol fil.</span><span class="sxs-lookup"><span data-stu-id="88e9d-173">The value of $ConsoleFileName is updated when you use the *Path* parameter of **Export-Console** to specify a new console file.</span></span> <span data-ttu-id="88e9d-174">Om ingen konsol fil används har $ConsoleFileName inget värde ($Null).</span><span class="sxs-lookup"><span data-stu-id="88e9d-174">When no console file is used, $ConsoleFileName has no value ($Null).</span></span>

  <span data-ttu-id="88e9d-175">Använd följande syntax för att starta Windows PowerShell för att använda en Windows PowerShell-konsolfil i en ny session:</span><span class="sxs-lookup"><span data-stu-id="88e9d-175">To use a Windows PowerShell console file in a new session, use the following syntax to start Windows PowerShell:</span></span>

  `powershell.exe -PsConsoleFile \<ConsoleFile\>.psc1`

  <span data-ttu-id="88e9d-176">Du kan också spara Windows PowerShell-snapin-moduler för framtida sessioner genom att lägga till ett Add-PSSnapin-kommando i Windows PowerShell-profilen.</span><span class="sxs-lookup"><span data-stu-id="88e9d-176">You can also save Windows PowerShell snap-ins for future sessions by adding an Add-PSSnapin command to your Windows PowerShell profile.</span></span>
<span data-ttu-id="88e9d-177">Mer information finns i about_Profiles.</span><span class="sxs-lookup"><span data-stu-id="88e9d-177">For more information, see about_Profiles.</span></span>


## <span data-ttu-id="88e9d-178">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="88e9d-178">RELATED LINKS</span></span>

[<span data-ttu-id="88e9d-179">Add-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="88e9d-179">Add-PSSnapin</span></span>](Add-PSSnapin.md)

[<span data-ttu-id="88e9d-180">Get-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="88e9d-180">Get-PSSnapin</span></span>](Get-PSSnapin.md)

[<span data-ttu-id="88e9d-181">Remove-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="88e9d-181">Remove-PSSnapin</span></span>](Remove-PSSnapin.md)
