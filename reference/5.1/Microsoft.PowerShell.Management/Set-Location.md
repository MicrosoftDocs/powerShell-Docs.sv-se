---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-location?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Location
ms.openlocfilehash: 06b1596366c9c9e20857b55aa9a17342bab07028
ms.sourcegitcommit: fe1e20f8523e3663d68546093aaf3670182337b8
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/14/2020
ms.locfileid: "93269199"
---
# <span data-ttu-id="ed833-103">Set-Location</span><span class="sxs-lookup"><span data-stu-id="ed833-103">Set-Location</span></span>

## <span data-ttu-id="ed833-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="ed833-104">SYNOPSIS</span></span>
<span data-ttu-id="ed833-105">Anger den aktuella arbets platsen till en angiven plats.</span><span class="sxs-lookup"><span data-stu-id="ed833-105">Sets the current working location to a specified location.</span></span>

## <span data-ttu-id="ed833-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ed833-106">SYNTAX</span></span>

### <span data-ttu-id="ed833-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="ed833-107">Path (Default)</span></span>

```
Set-Location [[-Path] <String>] [-PassThru] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="ed833-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="ed833-108">LiteralPath</span></span>

```
Set-Location -LiteralPath <String> [-PassThru] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="ed833-109">Stack</span><span class="sxs-lookup"><span data-stu-id="ed833-109">Stack</span></span>

```
Set-Location [-PassThru] [-StackName <String>] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="ed833-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ed833-110">DESCRIPTION</span></span>

<span data-ttu-id="ed833-111">`Set-Location`Cmdleten anger arbets platsen till en angiven plats.</span><span class="sxs-lookup"><span data-stu-id="ed833-111">The `Set-Location` cmdlet sets the working location to a specified location.</span></span> <span data-ttu-id="ed833-112">Platsen kan vara en katalog, en under katalog, en register plats eller en sökväg till en provider.</span><span class="sxs-lookup"><span data-stu-id="ed833-112">That location could be a directory, a subdirectory, a registry location, or any provider path.</span></span>

<span data-ttu-id="ed833-113">Du kan också använda parametern **StackName** för att skapa en namngiven plats stack den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="ed833-113">You can also use the **StackName** parameter to make a named location stack the current location stack.</span></span> <span data-ttu-id="ed833-114">Mer information om plats stackar finns i anteckningarna.</span><span class="sxs-lookup"><span data-stu-id="ed833-114">For more information about location stacks, see the Notes.</span></span>

## <span data-ttu-id="ed833-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="ed833-115">EXAMPLES</span></span>

### <span data-ttu-id="ed833-116">Exempel 1: Ange den aktuella platsen</span><span class="sxs-lookup"><span data-stu-id="ed833-116">Example 1: Set the current location</span></span>

```powershell
PS C:\> Set-Location -Path "HKLM:\"
```

```output
PS HKLM:\>
```

<span data-ttu-id="ed833-117">Det här kommandot anger den aktuella platsen till `HKLM:` enhetens rot.</span><span class="sxs-lookup"><span data-stu-id="ed833-117">This command sets the current location to the root of the `HKLM:` drive.</span></span>

### <span data-ttu-id="ed833-118">Exempel 2: Ange den aktuella platsen och visa platsen</span><span class="sxs-lookup"><span data-stu-id="ed833-118">Example 2: Set the current location and display that location</span></span>

```powershell
PS C:\> Set-Location -Path "Env:\" -PassThru
```

```output
Path
----
Env:\

PS Env:\>
```

<span data-ttu-id="ed833-119">Det här kommandot anger den aktuella platsen till `Env:` enhetens rot.</span><span class="sxs-lookup"><span data-stu-id="ed833-119">This command sets the current location to the root of the `Env:` drive.</span></span> <span data-ttu-id="ed833-120">Den använder parametern **Passthru** för att dirigera PowerShell för att returnera ett **PathInfo** -objekt som representerar `Env:\` platsen.</span><span class="sxs-lookup"><span data-stu-id="ed833-120">It uses the **PassThru** parameter to direct PowerShell to return a **PathInfo** object that represents the `Env:\` location.</span></span>

### <span data-ttu-id="ed833-121">Exempel 3: Ange platsen till den aktuella platsen i enhet C:</span><span class="sxs-lookup"><span data-stu-id="ed833-121">Example 3: Set location to the current location in the C: drive</span></span>

```powershell
PS C:\Windows\> Set-Location HKLM:\
PS HKLM:\> Set-Location C:
PS C:\Windows\>
```

<span data-ttu-id="ed833-122">Det första kommandot anger platsen för `HKLM:` enhetens rot i Registry-providern.</span><span class="sxs-lookup"><span data-stu-id="ed833-122">The first command sets the location to the root of the `HKLM:` drive in the Registry provider.</span></span>
<span data-ttu-id="ed833-123">Det andra kommandot anger platsen för `C:` enhetens aktuella plats i fil systemets Provider.</span><span class="sxs-lookup"><span data-stu-id="ed833-123">The second command sets the location to the current location of the `C:` drive in the FileSystem provider.</span></span>
<span data-ttu-id="ed833-124">När enhets namnet anges i formuläret `<DriveName>:` (utan omvänt snedstreck) anger cmdleten platsen till den aktuella platsen i PSDrive.</span><span class="sxs-lookup"><span data-stu-id="ed833-124">When the drive name is specified in the form `<DriveName>:` (without backslash), the cmdlet sets the location to the current location in the PSDrive.</span></span>
<span data-ttu-id="ed833-125">För att hämta den aktuella platsen i kommandot PSDrive use `Get-Location -PSDrive <DriveName>` .</span><span class="sxs-lookup"><span data-stu-id="ed833-125">To get the current location in the PSDrive use `Get-Location -PSDrive <DriveName>` command.</span></span>

### <span data-ttu-id="ed833-126">Exempel 4: Ange den aktuella platsen som en namngiven stack</span><span class="sxs-lookup"><span data-stu-id="ed833-126">Example 4: Set the current location to a named stack</span></span>

```powershell
PS C:\> Push-Location -Path 'C:\Program Files\PowerShell\' -StackName "Paths"
PS C:\Program Files\PowerShell\> Set-Location -StackName "Paths"
PS C:\Program Files\PowerShell\> Get-Location -Stack
```

```Output
Path
----
C:\
```

<span data-ttu-id="ed833-127">Det första kommandot lägger till den aktuella platsen i sökvägar-stacken.</span><span class="sxs-lookup"><span data-stu-id="ed833-127">The first command adds the current location to the Paths stack.</span></span>
<span data-ttu-id="ed833-128">Det andra kommandot gör Sök vägs platsen stack för den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="ed833-128">The second command makes the Paths location stack the current location stack.</span></span>
<span data-ttu-id="ed833-129">Det tredje kommandot visar platserna i den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="ed833-129">The third command displays the locations in the current location stack.</span></span>

<span data-ttu-id="ed833-130">`*-Location`Cmdletarna använder den aktuella plats stacken om inte en annan plats stack anges i kommandot.</span><span class="sxs-lookup"><span data-stu-id="ed833-130">The `*-Location` cmdlets use the current location stack unless a different location stack is specified in the command.</span></span> <span data-ttu-id="ed833-131">Information om plats stackar finns i [anteckningarna](#notes).</span><span class="sxs-lookup"><span data-stu-id="ed833-131">For information about location stacks, see the [Notes](#notes).</span></span>

## <span data-ttu-id="ed833-132">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="ed833-132">PARAMETERS</span></span>

### <span data-ttu-id="ed833-133">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="ed833-133">-LiteralPath</span></span>

<span data-ttu-id="ed833-134">Anger sökvägen till platsen.</span><span class="sxs-lookup"><span data-stu-id="ed833-134">Specifies a path of the location.</span></span> <span data-ttu-id="ed833-135">Värdet för parametern **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="ed833-135">The value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="ed833-136">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="ed833-136">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="ed833-137">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="ed833-137">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="ed833-138">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="ed833-138">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="ed833-139">Enkla citat tecken anger att Windows PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="ed833-139">Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ed833-140">– PassThru</span><span class="sxs-lookup"><span data-stu-id="ed833-140">-PassThru</span></span>

<span data-ttu-id="ed833-141">Returnerar ett **PathInfo** -objekt som representerar platsen.</span><span class="sxs-lookup"><span data-stu-id="ed833-141">Returns a **PathInfo** object that represents the location.</span></span> <span data-ttu-id="ed833-142">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="ed833-142">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="ed833-143">-Path</span><span class="sxs-lookup"><span data-stu-id="ed833-143">-Path</span></span>

<span data-ttu-id="ed833-144">Ange sökvägen till en ny arbets plats.</span><span class="sxs-lookup"><span data-stu-id="ed833-144">Specify the path of a new working location.</span></span> <span data-ttu-id="ed833-145">Om ingen sökväg anges används `Set-Location` den aktuella användarens hem katalog som standard.</span><span class="sxs-lookup"><span data-stu-id="ed833-145">If no path is provided, `Set-Location` defaults to the current user's home directory.</span></span> <span data-ttu-id="ed833-146">När jokertecken används, väljer cmdleten den första sökvägen som matchar mönstret jokertecken.</span><span class="sxs-lookup"><span data-stu-id="ed833-146">When wildcards are used, the cmdlet chooses the first path that matches the wildcard pattern.</span></span>

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

### <span data-ttu-id="ed833-147">-StackName</span><span class="sxs-lookup"><span data-stu-id="ed833-147">-StackName</span></span>

<span data-ttu-id="ed833-148">Anger det befintliga plats stack namnet som den här cmdleten gör den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="ed833-148">Specifies the existing location stack name that this cmdlet makes the current location stack.</span></span> <span data-ttu-id="ed833-149">Ange ett plats stack namn.</span><span class="sxs-lookup"><span data-stu-id="ed833-149">Enter a location stack name.</span></span> <span data-ttu-id="ed833-150">Om du vill ange den namnlösa standard plats stacken skriver `$null` eller en tom sträng ( `""` ).</span><span class="sxs-lookup"><span data-stu-id="ed833-150">To indicate the unnamed default location stack, type `$null` or an empty string (`""`).</span></span>

<span data-ttu-id="ed833-151">`*-Location`Cmdletarna fungerar på den aktuella stacken om du inte använder parametern **StackName** för att ange en annan stack.</span><span class="sxs-lookup"><span data-stu-id="ed833-151">The `*-Location` cmdlets act on the current stack unless you use the **StackName** parameter to specify a different stack.</span></span>

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

### <span data-ttu-id="ed833-152">– UseTransaction</span><span class="sxs-lookup"><span data-stu-id="ed833-152">-UseTransaction</span></span>

<span data-ttu-id="ed833-153">Inkluderar kommandot i den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="ed833-153">Includes the command in the active transaction.</span></span>
<span data-ttu-id="ed833-154">Den här parametern är bara giltig medan en transaktion pågår.</span><span class="sxs-lookup"><span data-stu-id="ed833-154">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="ed833-155">Mer information finns i about_Transactions.</span><span class="sxs-lookup"><span data-stu-id="ed833-155">For more information, see about_Transactions.</span></span>

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

### <span data-ttu-id="ed833-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ed833-156">CommonParameters</span></span>

<span data-ttu-id="ed833-157">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ed833-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ed833-158">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ed833-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ed833-159">INDATA</span><span class="sxs-lookup"><span data-stu-id="ed833-159">INPUTS</span></span>

### <span data-ttu-id="ed833-160">System. String</span><span class="sxs-lookup"><span data-stu-id="ed833-160">System.String</span></span>

<span data-ttu-id="ed833-161">Du kan skicka vidare en sträng som innehåller en sökväg, men inte en literal sökväg, till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ed833-161">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="ed833-162">UTDATA</span><span class="sxs-lookup"><span data-stu-id="ed833-162">OUTPUTS</span></span>

### <span data-ttu-id="ed833-163">Ingen, system. Management. Automation. PathInfo, system. Management. Automation. PathInfoStack</span><span class="sxs-lookup"><span data-stu-id="ed833-163">None, System.Management.Automation.PathInfo, System.Management.Automation.PathInfoStack</span></span>

<span data-ttu-id="ed833-164">Denna cmdlet genererar inga utdata om du inte anger parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="ed833-164">This cmdlet does not generate any output unless you specify the **PassThru** parameter.</span></span> <span data-ttu-id="ed833-165">Om du använder **Passthru** med **Path** eller **LiteralPath** genereras ett **PathInfo** -objekt som representerar den nya platsen.</span><span class="sxs-lookup"><span data-stu-id="ed833-165">Using **PassThru** with **Path** or **LiteralPath** generates a **PathInfo** object that represents the new location.</span></span> <span data-ttu-id="ed833-166">Om du använder **Passthru** med **StackName** genereras ett **PathInfoStack** -objekt som representerar den nya stack kontexten.</span><span class="sxs-lookup"><span data-stu-id="ed833-166">Using **PassThru** with **StackName** generates a **PathInfoStack** object representing the new stack context.</span></span>

## <span data-ttu-id="ed833-167">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="ed833-167">NOTES</span></span>

<span data-ttu-id="ed833-168">PowerShell stöder flera körnings utrymmen per process.</span><span class="sxs-lookup"><span data-stu-id="ed833-168">PowerShell supports multiple runspaces per process.</span></span> <span data-ttu-id="ed833-169">Varje körnings utrymme har sin egen _aktuella katalog_.</span><span class="sxs-lookup"><span data-stu-id="ed833-169">Each runspace has its own _current directory_.</span></span>
<span data-ttu-id="ed833-170">Detta är inte samma som `[System.Environment]::CurrentDirectory` .</span><span class="sxs-lookup"><span data-stu-id="ed833-170">This is not the same as `[System.Environment]::CurrentDirectory`.</span></span> <span data-ttu-id="ed833-171">Det här problemet kan vara ett problem när du anropar .NET-API: er eller kör ursprungliga program utan att ange explicita katalog Sök vägar.</span><span class="sxs-lookup"><span data-stu-id="ed833-171">This behavior can be an issue when calling .NET APIs or running native applications without providing explicit directory paths.</span></span>

<span data-ttu-id="ed833-172">Även om plats-cmdletarna har angett den aktuella katalogen för hela processen, är du inte beroende av den eftersom en annan körnings utrymme kan ändra den när som helst.</span><span class="sxs-lookup"><span data-stu-id="ed833-172">Even if the location cmdlets did set the process-wide current directory, you can't depend on it because another runspace might change it at any time.</span></span> <span data-ttu-id="ed833-173">Du bör använda plats-cmdletar för att utföra vägbaserade åtgärder med hjälp av den aktuella arbets katalogen som är unik för den aktuella körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="ed833-173">You should use the location cmdlets to perform path-based operations using the current working directory specific to the current runspace.</span></span>

<span data-ttu-id="ed833-174">`Set-Location`Cmdleten är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="ed833-174">The `Set-Location` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="ed833-175">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="ed833-175">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="ed833-176">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/about/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="ed833-176">For more information, see [about_Providers](../Microsoft.PowerShell.Core/about/about_Providers.md).</span></span>

<span data-ttu-id="ed833-177">En stack är en sista ingångs lista i som endast det objekt som lagts till senast lades till.</span><span class="sxs-lookup"><span data-stu-id="ed833-177">A stack is a last-in, first-out list in which only the most recently added item can be accessed.</span></span> <span data-ttu-id="ed833-178">Du lägger till objekt i en stack i den ordning som du använder dem och hämtar dem sedan för användning i omvänd ordning.</span><span class="sxs-lookup"><span data-stu-id="ed833-178">You add items to a stack in the order that you use them, and then retrieve them for use in the reverse order.</span></span> <span data-ttu-id="ed833-179">Med PowerShell kan du lagra leverantörs platser i plats stackar.</span><span class="sxs-lookup"><span data-stu-id="ed833-179">PowerShell lets you store provider locations in location stacks.</span></span> <span data-ttu-id="ed833-180">PowerShell skapar en namnlös standard plats stack.</span><span class="sxs-lookup"><span data-stu-id="ed833-180">PowerShell creates an unnamed default location stack.</span></span> <span data-ttu-id="ed833-181">Du kan skapa flera namngivna plats grupper.</span><span class="sxs-lookup"><span data-stu-id="ed833-181">You can create multiple named location stacks.</span></span> <span data-ttu-id="ed833-182">Om du inte anger något stack namn använder PowerShell den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="ed833-182">If you do not specify a stack name, PowerShell uses the current location stack.</span></span> <span data-ttu-id="ed833-183">Som standard är den namnlösa standard platsen den aktuella plats stacken, men du kan använda `Set-Location` cmdleten för att ändra den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="ed833-183">By default, the unnamed default location is the current location stack, but you can use the `Set-Location` cmdlet to change the current location stack.</span></span>

<span data-ttu-id="ed833-184">Om du vill hantera plats stackar använder du `*-Location` cmdletarna på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="ed833-184">To manage location stacks, use the `*-Location` cmdlets, as follows:</span></span>

- <span data-ttu-id="ed833-185">Om du vill lägga till en plats i en plats stack använder du `Push-Location` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ed833-185">To add a location to a location stack, use the `Push-Location` cmdlet.</span></span>

- <span data-ttu-id="ed833-186">Använd cmdleten för att hämta en plats från en plats stack `Pop-Location` .</span><span class="sxs-lookup"><span data-stu-id="ed833-186">To get a location from a location stack, use the `Pop-Location` cmdlet.</span></span>

- <span data-ttu-id="ed833-187">Om du vill visa platserna i den aktuella platsens stack, använder du cmdlet-parametern **stack** `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="ed833-187">To display the locations in the current location stack, use the **Stack** parameter of the `Get-Location` cmdlet.</span></span> <span data-ttu-id="ed833-188">Om du vill visa platserna i en namngiven plats stack använder du parametern **StackName** i `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="ed833-188">To display the locations in a named location stack, use the **StackName** parameter of `Get-Location`.</span></span>

- <span data-ttu-id="ed833-189">Om du vill skapa en ny plats stack använder du parametern **StackName** i `Push-Location` .</span><span class="sxs-lookup"><span data-stu-id="ed833-189">To create a new location stack, use the **StackName** parameter of `Push-Location`.</span></span> <span data-ttu-id="ed833-190">Om du anger en stack som inte finns `Push-Location` skapar stacken.</span><span class="sxs-lookup"><span data-stu-id="ed833-190">If you specify a stack that does not exist, `Push-Location` creates the stack.</span></span>

- <span data-ttu-id="ed833-191">Om du vill skapa en plats stack för den aktuella plats stacken använder du parametern **StackName** i `Set-Location` .</span><span class="sxs-lookup"><span data-stu-id="ed833-191">To make a location stack the current location stack, use the **StackName** parameter of `Set-Location`.</span></span>

<span data-ttu-id="ed833-192">Den namnlösa standard plats stacken är endast tillgänglig när den är den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="ed833-192">The unnamed default location stack is fully accessible only when it is the current location stack.</span></span>
<span data-ttu-id="ed833-193">Om du skapar en namngiven plats stack för den aktuella plats stacken kan du inte längre använda `Push-Location` `Pop-Location` cmdletarna eller för att lägga till eller hämta objekt från standard stacken eller `Get-Location` använda cmdleten för att Visa platserna i den namnlösa stacken.</span><span class="sxs-lookup"><span data-stu-id="ed833-193">If you make a named location stack the current location stack, you can no longer use the `Push-Location` or `Pop-Location` cmdlets to add or get items from the default stack or use the `Get-Location` cmdlet to display the locations in the unnamed stack.</span></span> <span data-ttu-id="ed833-194">Om du vill göra den namnlösa stacken till den aktuella stacken använder du parametern **StackName** för `Set-Location` cmdleten med värdet `$null` eller en tom sträng ( `""` ).</span><span class="sxs-lookup"><span data-stu-id="ed833-194">To make the unnamed stack the current stack, use the **StackName** parameter of the `Set-Location` cmdlet with a value of `$null` or an empty string (`""`).</span></span>

## <span data-ttu-id="ed833-195">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="ed833-195">RELATED LINKS</span></span>

[<span data-ttu-id="ed833-196">Get-location</span><span class="sxs-lookup"><span data-stu-id="ed833-196">Get-Location</span></span>](Get-Location.md)

[<span data-ttu-id="ed833-197">Pop-location</span><span class="sxs-lookup"><span data-stu-id="ed833-197">Pop-Location</span></span>](Pop-Location.md)

[<span data-ttu-id="ed833-198">Push-plats</span><span class="sxs-lookup"><span data-stu-id="ed833-198">Push-Location</span></span>](Push-Location.md)
