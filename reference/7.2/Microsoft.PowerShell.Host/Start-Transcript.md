---
external help file: Microsoft.PowerShell.ConsoleHost.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Host
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.host/start-transcript?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Transcript
ms.openlocfilehash: 24cd9bab242d0165f10721152544fea47b9557e3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709576"
---
# <span data-ttu-id="96607-102">Start-Transcript</span><span class="sxs-lookup"><span data-stu-id="96607-102">Start-Transcript</span></span>

## <span data-ttu-id="96607-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="96607-103">SYNOPSIS</span></span>
<span data-ttu-id="96607-104">Skapar en post med hela eller delar av en PowerShell-session till en textfil.</span><span class="sxs-lookup"><span data-stu-id="96607-104">Creates a record of all or part of a PowerShell session to a text file.</span></span>

## <span data-ttu-id="96607-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="96607-105">SYNTAX</span></span>

### <span data-ttu-id="96607-106">ByPath (standard)</span><span class="sxs-lookup"><span data-stu-id="96607-106">ByPath (Default)</span></span>

```
Start-Transcript [[-Path] <String>] [-Append] [-Force] [-NoClobber] [-IncludeInvocationHeader]
 [-UseMinimalHeader] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

### <span data-ttu-id="96607-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="96607-107">ByLiteralPath</span></span>

```
Start-Transcript [[-LiteralPath] <String>] [-Append] [-Force] [-NoClobber]
 [-IncludeInvocationHeader] [-UseMinimalHeader] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

### <span data-ttu-id="96607-108">ByOutputDirectory</span><span class="sxs-lookup"><span data-stu-id="96607-108">ByOutputDirectory</span></span>

```
Start-Transcript [[-OutputDirectory] <String>] [-Append] [-Force] [-NoClobber]
 [-IncludeInvocationHeader] [-UseMinimalHeader] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

## <span data-ttu-id="96607-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="96607-109">DESCRIPTION</span></span>

<span data-ttu-id="96607-110">`Start-Transcript`Cmdleten skapar en post med hela eller delar av en PowerShell-session till en textfil.</span><span class="sxs-lookup"><span data-stu-id="96607-110">The `Start-Transcript` cmdlet creates a record of all or part of a PowerShell session to a text file.</span></span> <span data-ttu-id="96607-111">Avskriften innehåller alla kommandon som användaren skriver och alla utdata som visas i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="96607-111">The transcript includes all command that the user types and all output that appears on the console.</span></span>

<span data-ttu-id="96607-112">Från och med Windows PowerShell 5,0 `Start-Transcript` innehåller värd namnet i det genererade fil namnet för alla avskrifter.</span><span class="sxs-lookup"><span data-stu-id="96607-112">Starting in Windows PowerShell 5.0, `Start-Transcript` includes the hostname in the generated file name of all transcripts.</span></span> <span data-ttu-id="96607-113">Detta är särskilt användbart när företagets loggning är centraliserad.</span><span class="sxs-lookup"><span data-stu-id="96607-113">This is especially useful when your enterprise's logging is centralized.</span></span>
<span data-ttu-id="96607-114">Filer som skapas av `Start-Transcript` cmdleten innehåller slumpmässiga tecken i namn för att förhindra eventuell överskrivning eller duplicering när två eller fler avskrifter startas samtidigt.</span><span class="sxs-lookup"><span data-stu-id="96607-114">Files that are created by the `Start-Transcript` cmdlet include random characters in names to prevent potential overwrites or duplication when two or more transcripts are started simultaneously.</span></span>
<span data-ttu-id="96607-115">Detta förhindrar även obehörig identifiering av avskrifter som lagras i en centraliserad fil resurs.</span><span class="sxs-lookup"><span data-stu-id="96607-115">This also prevents unauthorized discovery of transcripts that are stored in a centralized file share.</span></span>

## <span data-ttu-id="96607-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="96607-116">EXAMPLES</span></span>

### <span data-ttu-id="96607-117">Exempel 1: starta en avskrifts fil med standardinställningar</span><span class="sxs-lookup"><span data-stu-id="96607-117">Example 1: Start a transcript file with default settings</span></span>

```powershell
Start-Transcript
```

<span data-ttu-id="96607-118">Det här kommandot startar en avskrift på standard platsen för filen.</span><span class="sxs-lookup"><span data-stu-id="96607-118">This command starts a transcript in the default file location.</span></span>

### <span data-ttu-id="96607-119">Exempel 2: starta en avskrifts fil på en angiven plats</span><span class="sxs-lookup"><span data-stu-id="96607-119">Example 2: Start a transcript file at a specific location</span></span>

```powershell
Start-Transcript -Path "C:\transcripts\transcript0.txt" -NoClobber
```

<span data-ttu-id="96607-120">Det här kommandot startar en avskrift i `Transcript0.txt` filen i `C:\transcripts` .</span><span class="sxs-lookup"><span data-stu-id="96607-120">This command starts a transcript in the `Transcript0.txt` file in `C:\transcripts`.</span></span> <span data-ttu-id="96607-121">Eftersom parametern **NoClobber** används förhindrar kommandot att eventuella befintliga filer skrivs över.</span><span class="sxs-lookup"><span data-stu-id="96607-121">Since the **NoClobber** parameter is used, the command prevents any existing files from being overwritten.</span></span> <span data-ttu-id="96607-122">`Transcript0.txt`Kommandot Miss lyckas om filen redan finns.</span><span class="sxs-lookup"><span data-stu-id="96607-122">If the `Transcript0.txt` file already exists, the command fails.</span></span>

## <span data-ttu-id="96607-123">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="96607-123">PARAMETERS</span></span>

### <span data-ttu-id="96607-124">-Lägg till</span><span class="sxs-lookup"><span data-stu-id="96607-124">-Append</span></span>

<span data-ttu-id="96607-125">Anger att den här cmdleten lägger till den nya avskriften i slutet av en befintlig fil.</span><span class="sxs-lookup"><span data-stu-id="96607-125">Indicates that this cmdlet adds the new transcript to the end of an existing file.</span></span> <span data-ttu-id="96607-126">Använd parametern **Path** för att ange filen.</span><span class="sxs-lookup"><span data-stu-id="96607-126">Use the **Path** parameter to specify the file.</span></span>

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

### <span data-ttu-id="96607-127">-Force</span><span class="sxs-lookup"><span data-stu-id="96607-127">-Force</span></span>

<span data-ttu-id="96607-128">Tillåter cmdleten att lägga till avskriften i en befintlig skrivskyddad fil.</span><span class="sxs-lookup"><span data-stu-id="96607-128">Allows the cmdlet to append the transcript to an existing read-only file.</span></span> <span data-ttu-id="96607-129">När den används i en skrivskyddad fil ändrar cmdleten fil behörighet till Read-Write.</span><span class="sxs-lookup"><span data-stu-id="96607-129">When used on a read-only file, the cmdlet changes the file permission to read-write.</span></span> <span data-ttu-id="96607-130">Cmdleten kan inte åsidosätta säkerhets begränsningar när den här parametern används.</span><span class="sxs-lookup"><span data-stu-id="96607-130">The cmdlet cannot override security restrictions when this parameter is used.</span></span>

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

### <span data-ttu-id="96607-131">-IncludeInvocationHeader</span><span class="sxs-lookup"><span data-stu-id="96607-131">-IncludeInvocationHeader</span></span>

<span data-ttu-id="96607-132">Anger att denna cmdlet loggar tidsstämpeln när kommandon körs.</span><span class="sxs-lookup"><span data-stu-id="96607-132">Indicates that this cmdlet logs the time stamp when commands are run.</span></span>

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

### <span data-ttu-id="96607-133">-UseMinimalHeader</span><span class="sxs-lookup"><span data-stu-id="96607-133">-UseMinimalHeader</span></span>

<span data-ttu-id="96607-134">Lägga en kort rubrik till avskriften, i stället för den detaljerade rubriken som ingår som standard.</span><span class="sxs-lookup"><span data-stu-id="96607-134">Prepend a short header to the transcript, instead of the detailed header included by default.</span></span> <span data-ttu-id="96607-135">Den här parametern lades till i PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="96607-135">This parameter was added in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="96607-136">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="96607-136">-LiteralPath</span></span>

<span data-ttu-id="96607-137">Anger en plats för avskrifts filen.</span><span class="sxs-lookup"><span data-stu-id="96607-137">Specifies a location to the transcript file.</span></span> <span data-ttu-id="96607-138">Till skillnad från parametern **Path** används värdet för parametern **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="96607-138">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="96607-139">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="96607-139">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="96607-140">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="96607-140">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="96607-141">Enkla citat tecken meddelar PowerShell att inte tolka några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="96607-141">Single quotation marks inform PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="96607-142">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="96607-142">-NoClobber</span></span>

<span data-ttu-id="96607-143">Anger att denna cmdlet inte kommer att skriva över en befintlig fil.</span><span class="sxs-lookup"><span data-stu-id="96607-143">Indicates that this cmdlet will not overwrite of an existing file.</span></span> <span data-ttu-id="96607-144">Om det finns en avskrifts fil som finns på den angivna sökvägen `Start-Transcript` skrivs filen som standard över utan varning.</span><span class="sxs-lookup"><span data-stu-id="96607-144">By default, if a transcript file exists in the specified path, `Start-Transcript` overwrites the file without warning.</span></span>

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

### <span data-ttu-id="96607-145">– OutputDirectory</span><span class="sxs-lookup"><span data-stu-id="96607-145">-OutputDirectory</span></span>

<span data-ttu-id="96607-146">Anger en angiven sökväg och mapp där du vill spara en avskrift.</span><span class="sxs-lookup"><span data-stu-id="96607-146">Specifies a specific path and folder in which to save a transcript.</span></span> <span data-ttu-id="96607-147">PowerShell tilldelar automatiskt avskrifts namnet.</span><span class="sxs-lookup"><span data-stu-id="96607-147">PowerShell automatically assigns the transcript name.</span></span>

```yaml
Type: System.String
Parameter Sets: ByOutputDirectory
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="96607-148">-Path</span><span class="sxs-lookup"><span data-stu-id="96607-148">-Path</span></span>

<span data-ttu-id="96607-149">Anger en plats för avskrifts filen.</span><span class="sxs-lookup"><span data-stu-id="96607-149">Specifies a location to the transcript file.</span></span> <span data-ttu-id="96607-150">Ange en sökväg till en `.txt` fil.</span><span class="sxs-lookup"><span data-stu-id="96607-150">Enter a path to a `.txt` file.</span></span> <span data-ttu-id="96607-151">Jokertecken är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="96607-151">Wildcards are not permitted.</span></span>

<span data-ttu-id="96607-152">Om du inte anger en sökväg, `Start-Transcript` använder sökvägen i värdet för den `$Transcript` globala variabeln.</span><span class="sxs-lookup"><span data-stu-id="96607-152">If you do not specify a path, `Start-Transcript` uses the path in the value of the `$Transcript` global variable.</span></span> <span data-ttu-id="96607-153">Om du inte har skapat den här variabeln `Start-Transcript` lagras avskrifterna i `$Home\My Documents directory as \PowerShell_transcript.<time-stamp>.txt` filerna.</span><span class="sxs-lookup"><span data-stu-id="96607-153">If you have not created this variable, `Start-Transcript` stores the transcripts in the `$Home\My Documents directory as \PowerShell_transcript.<time-stamp>.txt` files.</span></span>

<span data-ttu-id="96607-154">Om någon av katalogerna i sökvägen inte finns, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="96607-154">If any of the directories in the path do not exist, the command fails.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="96607-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="96607-155">-Confirm</span></span>

<span data-ttu-id="96607-156">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="96607-156">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="96607-157">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="96607-157">-WhatIf</span></span>

<span data-ttu-id="96607-158">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="96607-158">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="96607-159">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="96607-159">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="96607-160">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="96607-160">CommonParameters</span></span>

<span data-ttu-id="96607-161">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="96607-161">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="96607-162">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="96607-162">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="96607-163">INDATA</span><span class="sxs-lookup"><span data-stu-id="96607-163">INPUTS</span></span>

### <span data-ttu-id="96607-164">Inga</span><span class="sxs-lookup"><span data-stu-id="96607-164">None</span></span>

<span data-ttu-id="96607-165">Det går inte att skicka pipe-objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="96607-165">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="96607-166">UTDATA</span><span class="sxs-lookup"><span data-stu-id="96607-166">OUTPUTS</span></span>

### <span data-ttu-id="96607-167">System. String</span><span class="sxs-lookup"><span data-stu-id="96607-167">System.String</span></span>

<span data-ttu-id="96607-168">Denna cmdlet returnerar en sträng som innehåller ett bekräftelse meddelande och sökvägen till utdatafilen.</span><span class="sxs-lookup"><span data-stu-id="96607-168">This cmdlet returns a string that contains a confirmation message and the path to the output file.</span></span>

## <span data-ttu-id="96607-169">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="96607-169">NOTES</span></span>

<span data-ttu-id="96607-170">Om du vill stoppa en avskrift använder du `Stop-Transcript` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="96607-170">To stop a transcript, use the `Stop-Transcript` cmdlet.</span></span>

<span data-ttu-id="96607-171">Om du vill spela in en hel session lägger du till `Start-Transcript` kommandot i din profil.</span><span class="sxs-lookup"><span data-stu-id="96607-171">To record an entire session, add the `Start-Transcript` command to your profile.</span></span> <span data-ttu-id="96607-172">Mer information finns i [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="96607-172">For more information, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

## <span data-ttu-id="96607-173">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="96607-173">RELATED LINKS</span></span>

[<span data-ttu-id="96607-174">Stopp-avskrift</span><span class="sxs-lookup"><span data-stu-id="96607-174">Stop-Transcript</span></span>](Stop-Transcript.md)

