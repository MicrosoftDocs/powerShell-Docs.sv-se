---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-location?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Location
ms.openlocfilehash: ec6f69d1d4a0b382ceec26b9409d01501edb814f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710399"
---
# <span data-ttu-id="33167-102">Set-Location</span><span class="sxs-lookup"><span data-stu-id="33167-102">Set-Location</span></span>

## <span data-ttu-id="33167-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="33167-103">SYNOPSIS</span></span>
<span data-ttu-id="33167-104">Anger den aktuella arbets platsen till en angiven plats.</span><span class="sxs-lookup"><span data-stu-id="33167-104">Sets the current working location to a specified location.</span></span>

## <span data-ttu-id="33167-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="33167-105">SYNTAX</span></span>

### <span data-ttu-id="33167-106">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="33167-106">Path (Default)</span></span>

```
Set-Location [[-Path] <String>] [-PassThru] [<CommonParameters>]
```

### <span data-ttu-id="33167-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="33167-107">LiteralPath</span></span>

```
Set-Location -LiteralPath <String> [-PassThru] [<CommonParameters>]
```

### <span data-ttu-id="33167-108">Stack</span><span class="sxs-lookup"><span data-stu-id="33167-108">Stack</span></span>

```
Set-Location [-PassThru] [-StackName <String>] [<CommonParameters>]
```

## <span data-ttu-id="33167-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="33167-109">DESCRIPTION</span></span>

<span data-ttu-id="33167-110">`Set-Location`Cmdleten anger arbets platsen till en angiven plats.</span><span class="sxs-lookup"><span data-stu-id="33167-110">The `Set-Location` cmdlet sets the working location to a specified location.</span></span> <span data-ttu-id="33167-111">Platsen kan vara en katalog, en under katalog, en register plats eller en sökväg till en provider.</span><span class="sxs-lookup"><span data-stu-id="33167-111">That location could be a directory, a subdirectory, a registry location, or any provider path.</span></span>

<span data-ttu-id="33167-112">PowerShell 6,2 har lagt till stöd för `-` och `+` som värden för parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="33167-112">PowerShell 6.2 added support for `-` and `+` as a values for the **Path** parameter.</span></span> <span data-ttu-id="33167-113">PowerShell har en historik över de senaste 20 platserna som kan nås med `-` och `+` .</span><span class="sxs-lookup"><span data-stu-id="33167-113">PowerShell maintains a history of the last 20 locations that can be accessed with `-` and `+`.</span></span> <span data-ttu-id="33167-114">Den här listan är oberoende av den plats stack som nås med hjälp av parametern **StackName** .</span><span class="sxs-lookup"><span data-stu-id="33167-114">This list is independent from the location stack that is accessed using the **StackName** parameter.</span></span>

## <span data-ttu-id="33167-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="33167-115">EXAMPLES</span></span>

### <span data-ttu-id="33167-116">Exempel 1: Ange den aktuella platsen</span><span class="sxs-lookup"><span data-stu-id="33167-116">Example 1: Set the current location</span></span>

```
PS C:\> Set-Location -Path "HKLM:\"
PS HKLM:\>
```

<span data-ttu-id="33167-117">Det här kommandot anger den aktuella platsen till `HKLM:` enhetens rot.</span><span class="sxs-lookup"><span data-stu-id="33167-117">This command sets the current location to the root of the `HKLM:` drive.</span></span>

### <span data-ttu-id="33167-118">Exempel 2: Ange den aktuella platsen och visa platsen</span><span class="sxs-lookup"><span data-stu-id="33167-118">Example 2: Set the current location and display that location</span></span>

```
PS C:\> Set-Location -Path "Env:\" -PassThru
```

```Output
Path
----
Env:\

PS Env:\>
```

<span data-ttu-id="33167-119">Det här kommandot anger den aktuella platsen till `Env:` enhetens rot.</span><span class="sxs-lookup"><span data-stu-id="33167-119">This command sets the current location to the root of the `Env:` drive.</span></span> <span data-ttu-id="33167-120">Den använder parametern **Passthru** för att dirigera PowerShell för att returnera ett **PathInfo** -objekt som representerar `Env:\` platsen.</span><span class="sxs-lookup"><span data-stu-id="33167-120">It uses the **PassThru** parameter to direct PowerShell to return a **PathInfo** object that represents the `Env:\` location.</span></span>

### <span data-ttu-id="33167-121">Exempel 3: Ange platsen till den aktuella platsen i enhet C:</span><span class="sxs-lookup"><span data-stu-id="33167-121">Example 3: Set location to the current location in the C: drive</span></span>

```powershell
PS C:\Windows\> Set-Location HKLM:\
PS HKLM:\> Set-Location C:
PS C:\Windows\>
```

<span data-ttu-id="33167-122">Det första kommandot anger platsen för `HKLM:` enhetens rot i Registry-providern.</span><span class="sxs-lookup"><span data-stu-id="33167-122">The first command sets the location to the root of the `HKLM:` drive in the Registry provider.</span></span>
<span data-ttu-id="33167-123">Det andra kommandot anger platsen för `C:` enhetens aktuella plats i fil systemets Provider.</span><span class="sxs-lookup"><span data-stu-id="33167-123">The second command sets the location to the current location of the `C:` drive in the FileSystem provider.</span></span>
<span data-ttu-id="33167-124">När enhets namnet anges i formuläret `<DriveName>:` (utan omvänt snedstreck) anger cmdleten platsen till den aktuella platsen i PSDrive.</span><span class="sxs-lookup"><span data-stu-id="33167-124">When the drive name is specified in the form `<DriveName>:` (without backslash), the cmdlet sets the location to the current location in the PSDrive.</span></span>
<span data-ttu-id="33167-125">För att hämta den aktuella platsen i kommandot PSDrive use `Get-Location -PSDrive <DriveName>` .</span><span class="sxs-lookup"><span data-stu-id="33167-125">To get the current location in the PSDrive use `Get-Location -PSDrive <DriveName>` command.</span></span>

### <span data-ttu-id="33167-126">Exempel 4: Ange den aktuella platsen som en namngiven stack</span><span class="sxs-lookup"><span data-stu-id="33167-126">Example 4: Set the current location to a named stack</span></span>

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

<span data-ttu-id="33167-127">Det första kommandot lägger till den aktuella platsen i sökvägar-stacken.</span><span class="sxs-lookup"><span data-stu-id="33167-127">The first command adds the current location to the Paths stack.</span></span>
<span data-ttu-id="33167-128">Det andra kommandot gör Sök vägs platsen stack för den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="33167-128">The second command makes the Paths location stack the current location stack.</span></span>
<span data-ttu-id="33167-129">Det tredje kommandot visar platserna i den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="33167-129">The third command displays the locations in the current location stack.</span></span>

<span data-ttu-id="33167-130">`*-Location`Cmdletarna använder den aktuella plats stacken om inte en annan plats stack anges i kommandot.</span><span class="sxs-lookup"><span data-stu-id="33167-130">The `*-Location` cmdlets use the current location stack unless a different location stack is specified in the command.</span></span> <span data-ttu-id="33167-131">Information om plats stackar finns i [anteckningarna](#notes).</span><span class="sxs-lookup"><span data-stu-id="33167-131">For information about location stacks, see the [Notes](#notes).</span></span>

### <span data-ttu-id="33167-132">Exempel 5: navigera plats historiken med `+` eller `-`</span><span class="sxs-lookup"><span data-stu-id="33167-132">Example 5: Navigate location history using `+` or `-`</span></span>

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

<span data-ttu-id="33167-133">Med hjälp av aliaset `cd -` eller `cd +` är ett enkelt sätt att navigera genom plats historiken i terminalen.</span><span class="sxs-lookup"><span data-stu-id="33167-133">Using the alias, `cd -` or `cd +` is an easy way to navigate through your location history while in your terminal.</span></span> <span data-ttu-id="33167-134">Mer information om hur du navigerar med `-` / `+` finns i parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="33167-134">For more information on navigating with `-`/`+`, see the **Path** parameter.</span></span>

## <span data-ttu-id="33167-135">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="33167-135">PARAMETERS</span></span>

### <span data-ttu-id="33167-136">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="33167-136">-LiteralPath</span></span>

<span data-ttu-id="33167-137">Anger sökvägen till platsen.</span><span class="sxs-lookup"><span data-stu-id="33167-137">Specifies a path of the location.</span></span> <span data-ttu-id="33167-138">Värdet för parametern **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="33167-138">The value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="33167-139">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="33167-139">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="33167-140">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="33167-140">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="33167-141">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="33167-141">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="33167-142">– PassThru</span><span class="sxs-lookup"><span data-stu-id="33167-142">-PassThru</span></span>

<span data-ttu-id="33167-143">Returnerar ett **PathInfo** -objekt som representerar platsen.</span><span class="sxs-lookup"><span data-stu-id="33167-143">Returns a **PathInfo** object that represents the location.</span></span> <span data-ttu-id="33167-144">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="33167-144">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="33167-145">-Path</span><span class="sxs-lookup"><span data-stu-id="33167-145">-Path</span></span>

<span data-ttu-id="33167-146">Ange sökvägen till en ny arbets plats.</span><span class="sxs-lookup"><span data-stu-id="33167-146">Specify the path of a new working location.</span></span> <span data-ttu-id="33167-147">Om ingen sökväg anges används `Set-Location` den aktuella användarens hem katalog som standard.</span><span class="sxs-lookup"><span data-stu-id="33167-147">If no path is provided, `Set-Location` defaults to the current user's home directory.</span></span> <span data-ttu-id="33167-148">När jokertecken används, väljer cmdleten den första sökvägen som matchar mönstret jokertecken.</span><span class="sxs-lookup"><span data-stu-id="33167-148">When wildcards are used, the cmdlet chooses the first path that matches the wildcard pattern.</span></span>

<span data-ttu-id="33167-149">PowerShell behåller en historik över de senaste 20 platserna som du har angett.</span><span class="sxs-lookup"><span data-stu-id="33167-149">PowerShell keeps a history of the last 20 locations you have set.</span></span> <span data-ttu-id="33167-150">Om värdet för parametern **Path** är ett `-` blank steg, kommer den nya arbets platsen att vara den tidigare arbets platsen i historiken (om den finns).</span><span class="sxs-lookup"><span data-stu-id="33167-150">If the **Path** parameter value is the `-` character, then the new working location will be the previous working location in history (if it exists).</span></span> <span data-ttu-id="33167-151">På samma sätt `+` kommer den nya arbets platsen att vara nästa arbets plats i historiken (om det finns), om värdet är ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="33167-151">Similarly, if the value is the `+` character, then the new working location will be the next working location in history (if it exists).</span></span> <span data-ttu-id="33167-152">Detta påminner om att använda `Pop-Location` och `Push-Location` förutom att historiken är en lista, inte en stack, och spåras implicit, inte manuellt kontrollerad.</span><span class="sxs-lookup"><span data-stu-id="33167-152">This is similar to using `Pop-Location` and `Push-Location` except that the history is a list, not a stack, and is implicitly tracked, not manually controlled.</span></span> <span data-ttu-id="33167-153">Det finns för närvarande inget sätt att visa historik listan.</span><span class="sxs-lookup"><span data-stu-id="33167-153">Currently, there is no way to view the history list.</span></span>

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

### <span data-ttu-id="33167-154">-StackName</span><span class="sxs-lookup"><span data-stu-id="33167-154">-StackName</span></span>

<span data-ttu-id="33167-155">Anger det befintliga plats stack namnet som den här cmdleten gör den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="33167-155">Specifies the existing location stack name that this cmdlet makes the current location stack.</span></span> <span data-ttu-id="33167-156">Ange ett plats stack namn.</span><span class="sxs-lookup"><span data-stu-id="33167-156">Enter a location stack name.</span></span> <span data-ttu-id="33167-157">Om du vill ange den namnlösa standard plats stacken skriver `$null` eller en tom sträng ( `""` ).</span><span class="sxs-lookup"><span data-stu-id="33167-157">To indicate the unnamed default location stack, type `$null` or an empty string (`""`).</span></span>

<span data-ttu-id="33167-158">`*-Location`Cmdletarna fungerar på den aktuella stacken om du inte använder parametern **StackName** för att ange en annan stack.</span><span class="sxs-lookup"><span data-stu-id="33167-158">The `*-Location` cmdlets act on the current stack unless you use the **StackName** parameter to specify a different stack.</span></span> <span data-ttu-id="33167-159">Mer information om plats stackar finns i [anteckningarna](#notes).</span><span class="sxs-lookup"><span data-stu-id="33167-159">For more information about location stacks, see the [Notes](#notes).</span></span>

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

### <span data-ttu-id="33167-160">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="33167-160">CommonParameters</span></span>

<span data-ttu-id="33167-161">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="33167-161">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="33167-162">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="33167-162">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="33167-163">INDATA</span><span class="sxs-lookup"><span data-stu-id="33167-163">INPUTS</span></span>

### <span data-ttu-id="33167-164">System. String</span><span class="sxs-lookup"><span data-stu-id="33167-164">System.String</span></span>

<span data-ttu-id="33167-165">Du kan skicka vidare en sträng som innehåller en sökväg, men inte en literal sökväg, till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="33167-165">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="33167-166">UTDATA</span><span class="sxs-lookup"><span data-stu-id="33167-166">OUTPUTS</span></span>

### <span data-ttu-id="33167-167">Ingen, system. Management. Automation. PathInfo, system. Management. Automation. PathInfoStack</span><span class="sxs-lookup"><span data-stu-id="33167-167">None, System.Management.Automation.PathInfo, System.Management.Automation.PathInfoStack</span></span>

<span data-ttu-id="33167-168">Denna cmdlet genererar inga utdata om du inte anger parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="33167-168">This cmdlet does not generate any output unless you specify the **PassThru** parameter.</span></span> <span data-ttu-id="33167-169">Om du använder **Passthru** med **Path** eller **LiteralPath** genereras ett **PathInfo** -objekt som representerar den nya platsen.</span><span class="sxs-lookup"><span data-stu-id="33167-169">Using **PassThru** with **Path** or **LiteralPath** generates a **PathInfo** object that represents the new location.</span></span> <span data-ttu-id="33167-170">Om du använder **Passthru** med **StackName** genereras ett **PathInfoStack** -objekt som representerar den nya stack kontexten.</span><span class="sxs-lookup"><span data-stu-id="33167-170">Using **PassThru** with **StackName** generates a **PathInfoStack** object representing the new stack context.</span></span>

## <span data-ttu-id="33167-171">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="33167-171">NOTES</span></span>

<span data-ttu-id="33167-172">PowerShell stöder flera körnings utrymmen per process.</span><span class="sxs-lookup"><span data-stu-id="33167-172">PowerShell supports multiple runspaces per process.</span></span> <span data-ttu-id="33167-173">Varje körnings utrymme har sin egen _aktuella katalog_.</span><span class="sxs-lookup"><span data-stu-id="33167-173">Each runspace has its own _current directory_.</span></span>
<span data-ttu-id="33167-174">Detta är inte samma som `[System.Environment]::CurrentDirectory` .</span><span class="sxs-lookup"><span data-stu-id="33167-174">This is not the same as `[System.Environment]::CurrentDirectory`.</span></span> <span data-ttu-id="33167-175">Det här problemet kan vara ett problem när du anropar .NET-API: er eller kör ursprungliga program utan att ange explicita katalog Sök vägar.</span><span class="sxs-lookup"><span data-stu-id="33167-175">This behavior can be an issue when calling .NET APIs or running native applications without providing explicit directory paths.</span></span>

<span data-ttu-id="33167-176">Även om plats-cmdletarna har angett den aktuella katalogen för hela processen, är du inte beroende av den eftersom en annan körnings utrymme kan ändra den när som helst.</span><span class="sxs-lookup"><span data-stu-id="33167-176">Even if the location cmdlets did set the process-wide current directory, you can't depend on it because another runspace might change it at any time.</span></span> <span data-ttu-id="33167-177">Du bör använda plats-cmdletar för att utföra vägbaserade åtgärder med hjälp av den aktuella arbets katalogen som är unik för den aktuella körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="33167-177">You should use the location cmdlets to perform path-based operations using the current working directory specific to the current runspace.</span></span>

<span data-ttu-id="33167-178">`Set-Location`Cmdleten är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="33167-178">The `Set-Location` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="33167-179">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="33167-179">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="33167-180">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/about/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="33167-180">For more information, see [about_Providers](../Microsoft.PowerShell.Core/about/about_Providers.md).</span></span>

<span data-ttu-id="33167-181">En stack är en sista ingångs lista i som endast det objekt som lagts till senast lades till.</span><span class="sxs-lookup"><span data-stu-id="33167-181">A stack is a last-in, first-out list in which only the most recently added item can be accessed.</span></span> <span data-ttu-id="33167-182">Du lägger till objekt i en stack i den ordning som du använder dem och hämtar dem sedan för användning i omvänd ordning.</span><span class="sxs-lookup"><span data-stu-id="33167-182">You add items to a stack in the order that you use them, and then retrieve them for use in the reverse order.</span></span> <span data-ttu-id="33167-183">Med PowerShell kan du lagra leverantörs platser i plats stackar.</span><span class="sxs-lookup"><span data-stu-id="33167-183">PowerShell lets you store provider locations in location stacks.</span></span> <span data-ttu-id="33167-184">PowerShell skapar en namnlös standard plats stack.</span><span class="sxs-lookup"><span data-stu-id="33167-184">PowerShell creates an unnamed default location stack.</span></span> <span data-ttu-id="33167-185">Du kan skapa flera namngivna plats grupper.</span><span class="sxs-lookup"><span data-stu-id="33167-185">You can create multiple named location stacks.</span></span> <span data-ttu-id="33167-186">Om du inte anger något stack namn använder PowerShell den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="33167-186">If you do not specify a stack name, PowerShell uses the current location stack.</span></span> <span data-ttu-id="33167-187">Som standard är den namnlösa standard platsen den aktuella plats stacken, men du kan använda `Set-Location` cmdleten för att ändra den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="33167-187">By default, the unnamed default location is the current location stack, but you can use the `Set-Location` cmdlet to change the current location stack.</span></span>

<span data-ttu-id="33167-188">Om du vill hantera plats stackar använder du `*-Location` cmdletarna på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="33167-188">To manage location stacks, use the `*-Location` cmdlets, as follows:</span></span>

- <span data-ttu-id="33167-189">Om du vill lägga till en plats i en plats stack använder du `Push-Location` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="33167-189">To add a location to a location stack, use the `Push-Location` cmdlet.</span></span>

- <span data-ttu-id="33167-190">Använd cmdleten för att hämta en plats från en plats stack `Pop-Location` .</span><span class="sxs-lookup"><span data-stu-id="33167-190">To get a location from a location stack, use the `Pop-Location` cmdlet.</span></span>

- <span data-ttu-id="33167-191">Om du vill visa platserna i den aktuella platsens stack, använder du cmdlet-parametern **stack** `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="33167-191">To display the locations in the current location stack, use the **Stack** parameter of the `Get-Location` cmdlet.</span></span> <span data-ttu-id="33167-192">Om du vill visa platserna i en namngiven plats stack använder du parametern **StackName** i `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="33167-192">To display the locations in a named location stack, use the **StackName** parameter of `Get-Location`.</span></span>

- <span data-ttu-id="33167-193">Om du vill skapa en ny plats stack använder du parametern **StackName** i `Push-Location` .</span><span class="sxs-lookup"><span data-stu-id="33167-193">To create a new location stack, use the **StackName** parameter of `Push-Location`.</span></span> <span data-ttu-id="33167-194">Om du anger en stack som inte finns `Push-Location` skapar stacken.</span><span class="sxs-lookup"><span data-stu-id="33167-194">If you specify a stack that does not exist, `Push-Location` creates the stack.</span></span>

- <span data-ttu-id="33167-195">Om du vill skapa en plats stack för den aktuella plats stacken använder du parametern **StackName** i `Set-Location` .</span><span class="sxs-lookup"><span data-stu-id="33167-195">To make a location stack the current location stack, use the **StackName** parameter of `Set-Location`.</span></span>

<span data-ttu-id="33167-196">Den namnlösa standard plats stacken är endast tillgänglig när den är den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="33167-196">The unnamed default location stack is fully accessible only when it is the current location stack.</span></span>
<span data-ttu-id="33167-197">Om du skapar en namngiven plats stack för den aktuella plats stacken kan du inte längre använda `Push-Location` `Pop-Location` cmdletarna eller för att lägga till eller hämta objekt från standard stacken eller `Get-Location` använda cmdleten för att Visa platserna i den namnlösa stacken.</span><span class="sxs-lookup"><span data-stu-id="33167-197">If you make a named location stack the current location stack, you can no longer use the `Push-Location` or `Pop-Location` cmdlets to add or get items from the default stack or use the `Get-Location` cmdlet to display the locations in the unnamed stack.</span></span> <span data-ttu-id="33167-198">Om du vill göra den namnlösa stacken till den aktuella stacken använder du parametern **StackName** för `Set-Location` cmdleten med värdet `$null` eller en tom sträng ( `""` ).</span><span class="sxs-lookup"><span data-stu-id="33167-198">To make the unnamed stack the current stack, use the **StackName** parameter of the `Set-Location` cmdlet with a value of `$null` or an empty string (`""`).</span></span>

## <span data-ttu-id="33167-199">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="33167-199">RELATED LINKS</span></span>

[<span data-ttu-id="33167-200">Get-location</span><span class="sxs-lookup"><span data-stu-id="33167-200">Get-Location</span></span>](Get-Location.md)

[<span data-ttu-id="33167-201">Pop-location</span><span class="sxs-lookup"><span data-stu-id="33167-201">Pop-Location</span></span>](Pop-Location.md)

[<span data-ttu-id="33167-202">Push-plats</span><span class="sxs-lookup"><span data-stu-id="33167-202">Push-Location</span></span>](Push-Location.md)

