---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-location?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Location
ms.openlocfilehash: 0c511ea30d55c1e6949f687c81d1edef809546fc
ms.sourcegitcommit: fe1e20f8523e3663d68546093aaf3670182337b8
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/14/2020
ms.locfileid: "93269216"
---
# <span data-ttu-id="b3c9f-103">Set-Location</span><span class="sxs-lookup"><span data-stu-id="b3c9f-103">Set-Location</span></span>

## <span data-ttu-id="b3c9f-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="b3c9f-104">SYNOPSIS</span></span>
<span data-ttu-id="b3c9f-105">Anger den aktuella arbets platsen till en angiven plats.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-105">Sets the current working location to a specified location.</span></span>

## <span data-ttu-id="b3c9f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b3c9f-106">SYNTAX</span></span>

### <span data-ttu-id="b3c9f-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="b3c9f-107">Path (Default)</span></span>

```
Set-Location [[-Path] <String>] [-PassThru] [<CommonParameters>]
```

### <span data-ttu-id="b3c9f-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b3c9f-108">LiteralPath</span></span>

```
Set-Location -LiteralPath <String> [-PassThru] [<CommonParameters>]
```

### <span data-ttu-id="b3c9f-109">Stack</span><span class="sxs-lookup"><span data-stu-id="b3c9f-109">Stack</span></span>

```
Set-Location [-PassThru] [-StackName <String>] [<CommonParameters>]
```

## <span data-ttu-id="b3c9f-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b3c9f-110">DESCRIPTION</span></span>

<span data-ttu-id="b3c9f-111">`Set-Location`Cmdleten anger arbets platsen till en angiven plats.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-111">The `Set-Location` cmdlet sets the working location to a specified location.</span></span> <span data-ttu-id="b3c9f-112">Platsen kan vara en katalog, en under katalog, en register plats eller en sökväg till en provider.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-112">That location could be a directory, a subdirectory, a registry location, or any provider path.</span></span>

<span data-ttu-id="b3c9f-113">PowerShell 6,2 har lagt till stöd för `-` och `+` som värden för parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="b3c9f-113">PowerShell 6.2 added support for `-` and `+` as a values for the **Path** parameter.</span></span> <span data-ttu-id="b3c9f-114">PowerShell har en historik över de senaste 20 platserna som kan nås med `-` och `+` .</span><span class="sxs-lookup"><span data-stu-id="b3c9f-114">PowerShell maintains a history of the last 20 locations that can be accessed with `-` and `+`.</span></span> <span data-ttu-id="b3c9f-115">Den här listan är oberoende av den plats stack som nås med hjälp av parametern **StackName** .</span><span class="sxs-lookup"><span data-stu-id="b3c9f-115">This list is independent from the location stack that is accessed using the **StackName** parameter.</span></span>

## <span data-ttu-id="b3c9f-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="b3c9f-116">EXAMPLES</span></span>

### <span data-ttu-id="b3c9f-117">Exempel 1: Ange den aktuella platsen</span><span class="sxs-lookup"><span data-stu-id="b3c9f-117">Example 1: Set the current location</span></span>

```
PS C:\> Set-Location -Path "HKLM:\"
PS HKLM:\>
```

<span data-ttu-id="b3c9f-118">Det här kommandot anger den aktuella platsen till `HKLM:` enhetens rot.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-118">This command sets the current location to the root of the `HKLM:` drive.</span></span>

### <span data-ttu-id="b3c9f-119">Exempel 2: Ange den aktuella platsen och visa platsen</span><span class="sxs-lookup"><span data-stu-id="b3c9f-119">Example 2: Set the current location and display that location</span></span>

```
PS C:\> Set-Location -Path "Env:\" -PassThru
```

```Output
Path
----
Env:\

PS Env:\>
```

<span data-ttu-id="b3c9f-120">Det här kommandot anger den aktuella platsen till `Env:` enhetens rot.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-120">This command sets the current location to the root of the `Env:` drive.</span></span> <span data-ttu-id="b3c9f-121">Den använder parametern **Passthru** för att dirigera PowerShell för att returnera ett **PathInfo** -objekt som representerar `Env:\` platsen.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-121">It uses the **PassThru** parameter to direct PowerShell to return a **PathInfo** object that represents the `Env:\` location.</span></span>

### <span data-ttu-id="b3c9f-122">Exempel 3: Ange platsen till den aktuella platsen i enhet C:</span><span class="sxs-lookup"><span data-stu-id="b3c9f-122">Example 3: Set location to the current location in the C: drive</span></span>

```powershell
PS C:\Windows\> Set-Location HKLM:\
PS HKLM:\> Set-Location C:
PS C:\Windows\>
```

<span data-ttu-id="b3c9f-123">Det första kommandot anger platsen för `HKLM:` enhetens rot i Registry-providern.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-123">The first command sets the location to the root of the `HKLM:` drive in the Registry provider.</span></span>
<span data-ttu-id="b3c9f-124">Det andra kommandot anger platsen för `C:` enhetens aktuella plats i fil systemets Provider.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-124">The second command sets the location to the current location of the `C:` drive in the FileSystem provider.</span></span>
<span data-ttu-id="b3c9f-125">När enhets namnet anges i formuläret `<DriveName>:` (utan omvänt snedstreck) anger cmdleten platsen till den aktuella platsen i PSDrive.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-125">When the drive name is specified in the form `<DriveName>:` (without backslash), the cmdlet sets the location to the current location in the PSDrive.</span></span>
<span data-ttu-id="b3c9f-126">För att hämta den aktuella platsen i kommandot PSDrive use `Get-Location -PSDrive <DriveName>` .</span><span class="sxs-lookup"><span data-stu-id="b3c9f-126">To get the current location in the PSDrive use `Get-Location -PSDrive <DriveName>` command.</span></span>

### <span data-ttu-id="b3c9f-127">Exempel 4: Ange den aktuella platsen som en namngiven stack</span><span class="sxs-lookup"><span data-stu-id="b3c9f-127">Example 4: Set the current location to a named stack</span></span>

```
PS C:\> Push-Location -Path 'C:\Program Files\PowerShell\' -StackName "Paths"
PS C:\Program Files\PowerShell\> Set-Location -StackName "Paths"
PS C:\Program Files\PowerShell\> Get-Location -Stack
```

```Output
Path
----
C:\
```

<span data-ttu-id="b3c9f-128">Det första kommandot lägger till den aktuella platsen i sökvägar-stacken.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-128">The first command adds the current location to the Paths stack.</span></span>
<span data-ttu-id="b3c9f-129">Det andra kommandot gör Sök vägs platsen stack för den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-129">The second command makes the Paths location stack the current location stack.</span></span>
<span data-ttu-id="b3c9f-130">Det tredje kommandot visar platserna i den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-130">The third command displays the locations in the current location stack.</span></span>

<span data-ttu-id="b3c9f-131">`*-Location`Cmdletarna använder den aktuella plats stacken om inte en annan plats stack anges i kommandot.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-131">The `*-Location` cmdlets use the current location stack unless a different location stack is specified in the command.</span></span> <span data-ttu-id="b3c9f-132">Information om plats stackar finns i [anteckningarna](#notes).</span><span class="sxs-lookup"><span data-stu-id="b3c9f-132">For information about location stacks, see the [Notes](#notes).</span></span>

### <span data-ttu-id="b3c9f-133">Exempel 5: navigera plats historiken med `+` eller `-`</span><span class="sxs-lookup"><span data-stu-id="b3c9f-133">Example 5: Navigate location history using `+` or `-`</span></span>

```
PS C:\> Set-Location -Path $env:SystemRoot
PS C:\Windows> Set-Location -Path Cert:\
PS Cert:\> Set-Location -Path HKLM:\
PS HKLM:\>

# Navigate back through the history using "-"
PS HKLM:\> Set-Location -Path -
PS Cert:\> Set-Location -Path -
PS C:\Windows>

# Navigate using the Set-Location alias "cd" and the implicit positional Path parameter
PS C:\Windows> cd -
PS C:\> cd +
PS C:\Windows> cd +
PS Cert:\>
```

<span data-ttu-id="b3c9f-134">Med hjälp av aliaset `cd -` eller `cd +` är ett enkelt sätt att navigera genom plats historiken i terminalen.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-134">Using the alias, `cd -` or `cd +` is an easy way to navigate through your location history while in your terminal.</span></span> <span data-ttu-id="b3c9f-135">Mer information om hur du navigerar med `-` / `+` finns i parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="b3c9f-135">For more information on navigating with `-`/`+`, see the **Path** parameter.</span></span>

## <span data-ttu-id="b3c9f-136">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="b3c9f-136">PARAMETERS</span></span>

### <span data-ttu-id="b3c9f-137">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b3c9f-137">-LiteralPath</span></span>

<span data-ttu-id="b3c9f-138">Anger sökvägen till platsen.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-138">Specifies a path of the location.</span></span> <span data-ttu-id="b3c9f-139">Värdet för parametern **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-139">The value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="b3c9f-140">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-140">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="b3c9f-141">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-141">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="b3c9f-142">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-142">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b3c9f-143">– PassThru</span><span class="sxs-lookup"><span data-stu-id="b3c9f-143">-PassThru</span></span>

<span data-ttu-id="b3c9f-144">Returnerar ett **PathInfo** -objekt som representerar platsen.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-144">Returns a **PathInfo** object that represents the location.</span></span> <span data-ttu-id="b3c9f-145">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-145">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="b3c9f-146">-Path</span><span class="sxs-lookup"><span data-stu-id="b3c9f-146">-Path</span></span>

<span data-ttu-id="b3c9f-147">Ange sökvägen till en ny arbets plats.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-147">Specify the path of a new working location.</span></span> <span data-ttu-id="b3c9f-148">Om ingen sökväg anges används `Set-Location` den aktuella användarens hem katalog som standard.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-148">If no path is provided, `Set-Location` defaults to the current user's home directory.</span></span> <span data-ttu-id="b3c9f-149">När jokertecken används, väljer cmdleten den första sökvägen som matchar mönstret jokertecken.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-149">When wildcards are used, the cmdlet chooses the first path that matches the wildcard pattern.</span></span>

<span data-ttu-id="b3c9f-150">PowerShell behåller en historik över de senaste 20 platserna som du har angett.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-150">PowerShell keeps a history of the last 20 locations you have set.</span></span> <span data-ttu-id="b3c9f-151">Om värdet för parametern **Path** är ett `-` blank steg, kommer den nya arbets platsen att vara den tidigare arbets platsen i historiken (om den finns).</span><span class="sxs-lookup"><span data-stu-id="b3c9f-151">If the **Path** parameter value is the `-` character, then the new working location will be the previous working location in history (if it exists).</span></span> <span data-ttu-id="b3c9f-152">På samma sätt `+` kommer den nya arbets platsen att vara nästa arbets plats i historiken (om det finns), om värdet är ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-152">Similarly, if the value is the `+` character, then the new working location will be the next working location in history (if it exists).</span></span> <span data-ttu-id="b3c9f-153">Detta påminner om att använda `Pop-Location` och `Push-Location` förutom att historiken är en lista, inte en stack, och spåras implicit, inte manuellt kontrollerad.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-153">This is similar to using `Pop-Location` and `Push-Location` except that the history is a list, not a stack, and is implicitly tracked, not manually controlled.</span></span> <span data-ttu-id="b3c9f-154">Det finns för närvarande inget sätt att visa historik listan.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-154">Currently, there is no way to view the history list.</span></span>

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="b3c9f-155">-StackName</span><span class="sxs-lookup"><span data-stu-id="b3c9f-155">-StackName</span></span>

<span data-ttu-id="b3c9f-156">Anger det befintliga plats stack namnet som den här cmdleten gör den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-156">Specifies the existing location stack name that this cmdlet makes the current location stack.</span></span> <span data-ttu-id="b3c9f-157">Ange ett plats stack namn.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-157">Enter a location stack name.</span></span> <span data-ttu-id="b3c9f-158">Om du vill ange den namnlösa standard plats stacken skriver `$null` eller en tom sträng ( `""` ).</span><span class="sxs-lookup"><span data-stu-id="b3c9f-158">To indicate the unnamed default location stack, type `$null` or an empty string (`""`).</span></span>

<span data-ttu-id="b3c9f-159">`*-Location`Cmdletarna fungerar på den aktuella stacken om du inte använder parametern **StackName** för att ange en annan stack.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-159">The `*-Location` cmdlets act on the current stack unless you use the **StackName** parameter to specify a different stack.</span></span> <span data-ttu-id="b3c9f-160">Mer information om plats stackar finns i [anteckningarna](#notes).</span><span class="sxs-lookup"><span data-stu-id="b3c9f-160">For more information about location stacks, see the [Notes](#notes).</span></span>

```yaml
Type: System.String
Parameter Sets: Stack
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b3c9f-161">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b3c9f-161">CommonParameters</span></span>

<span data-ttu-id="b3c9f-162">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-162">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b3c9f-163">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b3c9f-163">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b3c9f-164">INDATA</span><span class="sxs-lookup"><span data-stu-id="b3c9f-164">INPUTS</span></span>

### <span data-ttu-id="b3c9f-165">System. String</span><span class="sxs-lookup"><span data-stu-id="b3c9f-165">System.String</span></span>

<span data-ttu-id="b3c9f-166">Du kan skicka vidare en sträng som innehåller en sökväg, men inte en literal sökväg, till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-166">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="b3c9f-167">UTDATA</span><span class="sxs-lookup"><span data-stu-id="b3c9f-167">OUTPUTS</span></span>

### <span data-ttu-id="b3c9f-168">Ingen, system. Management. Automation. PathInfo, system. Management. Automation. PathInfoStack</span><span class="sxs-lookup"><span data-stu-id="b3c9f-168">None, System.Management.Automation.PathInfo, System.Management.Automation.PathInfoStack</span></span>

<span data-ttu-id="b3c9f-169">Denna cmdlet genererar inga utdata om du inte anger parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="b3c9f-169">This cmdlet does not generate any output unless you specify the **PassThru** parameter.</span></span> <span data-ttu-id="b3c9f-170">Om du använder **Passthru** med **Path** eller **LiteralPath** genereras ett **PathInfo** -objekt som representerar den nya platsen.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-170">Using **PassThru** with **Path** or **LiteralPath** generates a **PathInfo** object that represents the new location.</span></span> <span data-ttu-id="b3c9f-171">Om du använder **Passthru** med **StackName** genereras ett **PathInfoStack** -objekt som representerar den nya stack kontexten.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-171">Using **PassThru** with **StackName** generates a **PathInfoStack** object representing the new stack context.</span></span>

## <span data-ttu-id="b3c9f-172">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="b3c9f-172">NOTES</span></span>

<span data-ttu-id="b3c9f-173">PowerShell stöder flera körnings utrymmen per process.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-173">PowerShell supports multiple runspaces per process.</span></span> <span data-ttu-id="b3c9f-174">Varje körnings utrymme har sin egen _aktuella katalog_.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-174">Each runspace has its own _current directory_.</span></span>
<span data-ttu-id="b3c9f-175">Detta är inte samma som `[System.Environment]::CurrentDirectory` .</span><span class="sxs-lookup"><span data-stu-id="b3c9f-175">This is not the same as `[System.Environment]::CurrentDirectory`.</span></span> <span data-ttu-id="b3c9f-176">Det här problemet kan vara ett problem när du anropar .NET-API: er eller kör ursprungliga program utan att ange explicita katalog Sök vägar.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-176">This behavior can be an issue when calling .NET APIs or running native applications without providing explicit directory paths.</span></span>

<span data-ttu-id="b3c9f-177">Även om plats-cmdletarna har angett den aktuella katalogen för hela processen, är du inte beroende av den eftersom en annan körnings utrymme kan ändra den när som helst.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-177">Even if the location cmdlets did set the process-wide current directory, you can't depend on it because another runspace might change it at any time.</span></span> <span data-ttu-id="b3c9f-178">Du bör använda plats-cmdletar för att utföra vägbaserade åtgärder med hjälp av den aktuella arbets katalogen som är unik för den aktuella körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-178">You should use the location cmdlets to perform path-based operations using the current working directory specific to the current runspace.</span></span>

<span data-ttu-id="b3c9f-179">`Set-Location`Cmdleten är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-179">The `Set-Location` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="b3c9f-180">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="b3c9f-180">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="b3c9f-181">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/about/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="b3c9f-181">For more information, see [about_Providers](../Microsoft.PowerShell.Core/about/about_Providers.md).</span></span>

<span data-ttu-id="b3c9f-182">En stack är en sista ingångs lista i som endast det objekt som lagts till senast lades till.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-182">A stack is a last-in, first-out list in which only the most recently added item can be accessed.</span></span> <span data-ttu-id="b3c9f-183">Du lägger till objekt i en stack i den ordning som du använder dem och hämtar dem sedan för användning i omvänd ordning.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-183">You add items to a stack in the order that you use them, and then retrieve them for use in the reverse order.</span></span> <span data-ttu-id="b3c9f-184">Med PowerShell kan du lagra leverantörs platser i plats stackar.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-184">PowerShell lets you store provider locations in location stacks.</span></span> <span data-ttu-id="b3c9f-185">PowerShell skapar en namnlös standard plats stack.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-185">PowerShell creates an unnamed default location stack.</span></span> <span data-ttu-id="b3c9f-186">Du kan skapa flera namngivna plats grupper.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-186">You can create multiple named location stacks.</span></span> <span data-ttu-id="b3c9f-187">Om du inte anger något stack namn använder PowerShell den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-187">If you do not specify a stack name, PowerShell uses the current location stack.</span></span> <span data-ttu-id="b3c9f-188">Som standard är den namnlösa standard platsen den aktuella plats stacken, men du kan använda `Set-Location` cmdleten för att ändra den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-188">By default, the unnamed default location is the current location stack, but you can use the `Set-Location` cmdlet to change the current location stack.</span></span>

<span data-ttu-id="b3c9f-189">Om du vill hantera plats stackar använder du `*-Location` cmdletarna på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="b3c9f-189">To manage location stacks, use the `*-Location` cmdlets, as follows:</span></span>

- <span data-ttu-id="b3c9f-190">Om du vill lägga till en plats i en plats stack använder du `Push-Location` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-190">To add a location to a location stack, use the `Push-Location` cmdlet.</span></span>

- <span data-ttu-id="b3c9f-191">Använd cmdleten för att hämta en plats från en plats stack `Pop-Location` .</span><span class="sxs-lookup"><span data-stu-id="b3c9f-191">To get a location from a location stack, use the `Pop-Location` cmdlet.</span></span>

- <span data-ttu-id="b3c9f-192">Om du vill visa platserna i den aktuella platsens stack, använder du cmdlet-parametern **stack** `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="b3c9f-192">To display the locations in the current location stack, use the **Stack** parameter of the `Get-Location` cmdlet.</span></span> <span data-ttu-id="b3c9f-193">Om du vill visa platserna i en namngiven plats stack använder du parametern **StackName** i `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="b3c9f-193">To display the locations in a named location stack, use the **StackName** parameter of `Get-Location`.</span></span>

- <span data-ttu-id="b3c9f-194">Om du vill skapa en ny plats stack använder du parametern **StackName** i `Push-Location` .</span><span class="sxs-lookup"><span data-stu-id="b3c9f-194">To create a new location stack, use the **StackName** parameter of `Push-Location`.</span></span> <span data-ttu-id="b3c9f-195">Om du anger en stack som inte finns `Push-Location` skapar stacken.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-195">If you specify a stack that does not exist, `Push-Location` creates the stack.</span></span>

- <span data-ttu-id="b3c9f-196">Om du vill skapa en plats stack för den aktuella plats stacken använder du parametern **StackName** i `Set-Location` .</span><span class="sxs-lookup"><span data-stu-id="b3c9f-196">To make a location stack the current location stack, use the **StackName** parameter of `Set-Location`.</span></span>

<span data-ttu-id="b3c9f-197">Den namnlösa standard plats stacken är endast tillgänglig när den är den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-197">The unnamed default location stack is fully accessible only when it is the current location stack.</span></span>
<span data-ttu-id="b3c9f-198">Om du skapar en namngiven plats stack för den aktuella plats stacken kan du inte längre använda `Push-Location` `Pop-Location` cmdletarna eller för att lägga till eller hämta objekt från standard stacken eller `Get-Location` använda cmdleten för att Visa platserna i den namnlösa stacken.</span><span class="sxs-lookup"><span data-stu-id="b3c9f-198">If you make a named location stack the current location stack, you can no longer use the `Push-Location` or `Pop-Location` cmdlets to add or get items from the default stack or use the `Get-Location` cmdlet to display the locations in the unnamed stack.</span></span> <span data-ttu-id="b3c9f-199">Om du vill göra den namnlösa stacken till den aktuella stacken använder du parametern **StackName** för `Set-Location` cmdleten med värdet `$null` eller en tom sträng ( `""` ).</span><span class="sxs-lookup"><span data-stu-id="b3c9f-199">To make the unnamed stack the current stack, use the **StackName** parameter of the `Set-Location` cmdlet with a value of `$null` or an empty string (`""`).</span></span>

## <span data-ttu-id="b3c9f-200">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="b3c9f-200">RELATED LINKS</span></span>

[<span data-ttu-id="b3c9f-201">Get-location</span><span class="sxs-lookup"><span data-stu-id="b3c9f-201">Get-Location</span></span>](Get-Location.md)

[<span data-ttu-id="b3c9f-202">Pop-location</span><span class="sxs-lookup"><span data-stu-id="b3c9f-202">Pop-Location</span></span>](Pop-Location.md)

[<span data-ttu-id="b3c9f-203">Push-plats</span><span class="sxs-lookup"><span data-stu-id="b3c9f-203">Push-Location</span></span>](Push-Location.md)

