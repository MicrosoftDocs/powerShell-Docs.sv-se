---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/push-location?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Push-Location
ms.openlocfilehash: eaa7622e29680de4228579f8b77a6c829a586bf8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710195"
---
# <span data-ttu-id="dbc84-102">Push-Location</span><span class="sxs-lookup"><span data-stu-id="dbc84-102">Push-Location</span></span>

## <span data-ttu-id="dbc84-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="dbc84-103">SYNOPSIS</span></span>
<span data-ttu-id="dbc84-104">Lägger till den aktuella platsen överst i en plats stack.</span><span class="sxs-lookup"><span data-stu-id="dbc84-104">Adds the current location to the top of a location stack.</span></span>

## <span data-ttu-id="dbc84-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="dbc84-105">SYNTAX</span></span>

### <span data-ttu-id="dbc84-106">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="dbc84-106">Path (Default)</span></span>

```
Push-Location [[-Path] <String>] [-PassThru] [-StackName <String>] [<CommonParameters>]
```

### <span data-ttu-id="dbc84-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="dbc84-107">LiteralPath</span></span>

```
Push-Location [-LiteralPath <String>] [-PassThru] [-StackName <String>] [<CommonParameters>]
```

## <span data-ttu-id="dbc84-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="dbc84-108">DESCRIPTION</span></span>

<span data-ttu-id="dbc84-109">`Push-Location`Cmdleten lägger till ("pushs") den aktuella platsen till en plats stack.</span><span class="sxs-lookup"><span data-stu-id="dbc84-109">The `Push-Location` cmdlet adds ("pushes") the current location onto a location stack.</span></span> <span data-ttu-id="dbc84-110">Om du anger en sökväg, `Push-Location` pushar den aktuella platsen till en plats stack och ändrar sedan den aktuella platsen till den plats som anges i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="dbc84-110">If you specify a path, `Push-Location` pushes the current location onto a location stack and then changes the current location to the location specified by the path.</span></span> <span data-ttu-id="dbc84-111">Du kan använda `Pop-Location` cmdleten för att hämta platser från plats stacken.</span><span class="sxs-lookup"><span data-stu-id="dbc84-111">You can use the `Pop-Location` cmdlet to get locations from the location stack.</span></span>

<span data-ttu-id="dbc84-112">Som standard push-överför `Push-Location` cmdleten den aktuella platsen till den aktuella plats-stacken, men du kan använda parametern **StackName** för att ange en alternativ plats stack.</span><span class="sxs-lookup"><span data-stu-id="dbc84-112">By default, the `Push-Location` cmdlet pushes the current location onto the current location stack, but you can use the **StackName** parameter to specify an alternate location stack.</span></span> <span data-ttu-id="dbc84-113">Om stacken inte finns `Push-Location` skapas den.</span><span class="sxs-lookup"><span data-stu-id="dbc84-113">If the stack does not exist, `Push-Location` creates it.</span></span>

<span data-ttu-id="dbc84-114">Mer information om plats stackar finns i [anteckningarna](#notes).</span><span class="sxs-lookup"><span data-stu-id="dbc84-114">For more information about location stacks, see the [Notes](#notes).</span></span>

## <span data-ttu-id="dbc84-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="dbc84-115">EXAMPLES</span></span>

### <span data-ttu-id="dbc84-116">Exempel 1</span><span class="sxs-lookup"><span data-stu-id="dbc84-116">Example 1</span></span>

<span data-ttu-id="dbc84-117">I det här exemplet skickas den aktuella platsen till standard plats stacken och sedan ändras platsen till `C:\Windows` .</span><span class="sxs-lookup"><span data-stu-id="dbc84-117">This example pushes the current location onto the default location stack and then changes the location to `C:\Windows`.</span></span>

```
PS C:\> Push-Location C:\Windows
```

### <span data-ttu-id="dbc84-118">Exempel 2</span><span class="sxs-lookup"><span data-stu-id="dbc84-118">Example 2</span></span>

<span data-ttu-id="dbc84-119">Det här exemplet pushrar den aktuella platsen till RegFunction-stacken och ändrar den aktuella platsen till `HKLM:\Software\Policies` platsen.</span><span class="sxs-lookup"><span data-stu-id="dbc84-119">This example pushes the current location onto the RegFunction stack and changes the current location to the `HKLM:\Software\Policies` location.</span></span>

```
PS C:\> Push-Location HKLM:\Software\Policies -StackName RegFunction
```

<span data-ttu-id="dbc84-120">Du kan använda plats-cmdletar i valfri PowerShell-enhet (PSDrive).</span><span class="sxs-lookup"><span data-stu-id="dbc84-120">You can use the Location cmdlets in any PowerShell drive (PSDrive).</span></span>

### <span data-ttu-id="dbc84-121">Exempel 3</span><span class="sxs-lookup"><span data-stu-id="dbc84-121">Example 3</span></span>

<span data-ttu-id="dbc84-122">Det här kommandot push-överför den aktuella platsen till standard stacken.</span><span class="sxs-lookup"><span data-stu-id="dbc84-122">This command pushes the current location onto the default stack.</span></span> <span data-ttu-id="dbc84-123">Den ändrar inte platsen.</span><span class="sxs-lookup"><span data-stu-id="dbc84-123">It does not change the location.</span></span>

```
PS C:\> Push-Location
```

### <span data-ttu-id="dbc84-124">Exempel 4 – Skapa och Använd en namngiven stack</span><span class="sxs-lookup"><span data-stu-id="dbc84-124">Example 4 - Create and use a named stack</span></span>

<span data-ttu-id="dbc84-125">De här kommandona visar hur du skapar och använder en namngiven plats stack.</span><span class="sxs-lookup"><span data-stu-id="dbc84-125">These commands show how to create and use a named location stack.</span></span>

```
PS C:\> Push-Location ~ -StackName Stack2
PS C:\Users\User01> Pop-Location -StackName Stack2
PS C:\>
```

<span data-ttu-id="dbc84-126">Det första kommandot push-överför den aktuella platsen till en ny stack med namnet Stack2 och ändrar sedan den aktuella platsen till arbets katalogen, som visas i kommandot med tilde ( `~` ), som när det används på ett fil Systems leverantörs enheter motsvarar `$HOME` och `$env:USERPROFILE` .</span><span class="sxs-lookup"><span data-stu-id="dbc84-126">The first command pushes the current location onto a new stack named Stack2, and then changes the current location to the home directory, represented in the command by the tilde symbol (`~`), which when used on a FileSystem provider drives is equivalent to `$HOME` and `$env:USERPROFILE`.</span></span>

<span data-ttu-id="dbc84-127">Om Stack2 inte redan finns i sessionen `Push-Location` skapas den.</span><span class="sxs-lookup"><span data-stu-id="dbc84-127">If Stack2 does not already exist in the session, `Push-Location` creates it.</span></span> <span data-ttu-id="dbc84-128">Det andra kommandot använder `Pop-Location` cmdleten för att plocka den ursprungliga platsen ( `C:\` ) från Stack2-stacken.</span><span class="sxs-lookup"><span data-stu-id="dbc84-128">The second command uses the `Pop-Location` cmdlet to pop the original location (`C:\`) from the Stack2 stack.</span></span> <span data-ttu-id="dbc84-129">Om du inte använder parametern **StackName** `Pop-Location` skulle platsen kunna visas från den namnlösa standard stacken.</span><span class="sxs-lookup"><span data-stu-id="dbc84-129">Without the **StackName** parameter, `Pop-Location` would pop the location from the unnamed default stack.</span></span>

<span data-ttu-id="dbc84-130">Mer information om plats stackar finns i [anteckningarna](#notes).</span><span class="sxs-lookup"><span data-stu-id="dbc84-130">For more information about location stacks, see the [Notes](#notes).</span></span>

## <span data-ttu-id="dbc84-131">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="dbc84-131">PARAMETERS</span></span>

### <span data-ttu-id="dbc84-132">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="dbc84-132">-LiteralPath</span></span>

<span data-ttu-id="dbc84-133">Anger sökvägen till den nya platsen.</span><span class="sxs-lookup"><span data-stu-id="dbc84-133">Specifies the path to the new location.</span></span> <span data-ttu-id="dbc84-134">Till skillnad från parametern **Path** används värdet för parametern **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="dbc84-134">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="dbc84-135">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="dbc84-135">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="dbc84-136">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="dbc84-136">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="dbc84-137">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="dbc84-137">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="dbc84-138">– PassThru</span><span class="sxs-lookup"><span data-stu-id="dbc84-138">-PassThru</span></span>

<span data-ttu-id="dbc84-139">Skickar ett objekt som representerar platsen för pipelinen.</span><span class="sxs-lookup"><span data-stu-id="dbc84-139">Passes an object representing the location to the pipeline.</span></span> <span data-ttu-id="dbc84-140">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="dbc84-140">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="dbc84-141">-Path</span><span class="sxs-lookup"><span data-stu-id="dbc84-141">-Path</span></span>

<span data-ttu-id="dbc84-142">Ändrar platsen till den plats som anges av den här sökvägen efter att den lägger till (push-överför) den aktuella platsen överst i stacken.</span><span class="sxs-lookup"><span data-stu-id="dbc84-142">Changes your location to the location specified by this path after it adds (pushes) the current location onto the top of the stack.</span></span> <span data-ttu-id="dbc84-143">Ange en sökväg till en plats vars provider stöder denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dbc84-143">Enter a path to any location whose provider supports this cmdlet.</span></span> <span data-ttu-id="dbc84-144">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="dbc84-144">Wildcards are permitted.</span></span> <span data-ttu-id="dbc84-145">Parameter namnet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="dbc84-145">The parameter name is optional.</span></span>

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="dbc84-146">-StackName</span><span class="sxs-lookup"><span data-stu-id="dbc84-146">-StackName</span></span>

<span data-ttu-id="dbc84-147">Anger den plats stack som den aktuella platsen ska läggas till i.</span><span class="sxs-lookup"><span data-stu-id="dbc84-147">Specifies the location stack to which the current location is added.</span></span> <span data-ttu-id="dbc84-148">Ange ett plats stack namn.</span><span class="sxs-lookup"><span data-stu-id="dbc84-148">Enter a location stack name.</span></span>
<span data-ttu-id="dbc84-149">Om stacken inte finns `Push-Location` skapas den.</span><span class="sxs-lookup"><span data-stu-id="dbc84-149">If the stack does not exist, `Push-Location` creates it.</span></span>

<span data-ttu-id="dbc84-150">Utan den här parametern `Push-Location` lägger till platsen i den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="dbc84-150">Without this parameter, `Push-Location` adds the location to the current location stack.</span></span> <span data-ttu-id="dbc84-151">Som standard är den aktuella plats stacken den namnlösa standard plats stacken som PowerShell skapar.</span><span class="sxs-lookup"><span data-stu-id="dbc84-151">By default, the current location stack is the unnamed default location stack that PowerShell creates.</span></span>
<span data-ttu-id="dbc84-152">Om du vill skapa en plats stack för den aktuella plats stacken använder du parametern **StackName** för `Set-Location` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="dbc84-152">To make a location stack the current location stack, use the **StackName** parameter of the `Set-Location` cmdlet.</span></span> <span data-ttu-id="dbc84-153">Mer information om plats stackar finns i [anteckningarna](#notes).</span><span class="sxs-lookup"><span data-stu-id="dbc84-153">For more information about location stacks, see the [Notes](#notes).</span></span>

> [!NOTE]
> <span data-ttu-id="dbc84-154">`Push-Location` Det går inte att lägga till en plats i den namnlösa standard stacken om den inte är den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="dbc84-154">`Push-Location` cannot add a location to the unnamed default stack unless it is the current location stack.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Default stack
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="dbc84-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="dbc84-155">CommonParameters</span></span>

<span data-ttu-id="dbc84-156">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="dbc84-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="dbc84-157">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="dbc84-157">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="dbc84-158">INDATA</span><span class="sxs-lookup"><span data-stu-id="dbc84-158">INPUTS</span></span>

### <span data-ttu-id="dbc84-159">System. String</span><span class="sxs-lookup"><span data-stu-id="dbc84-159">System.String</span></span>

<span data-ttu-id="dbc84-160">Du kan skicka vidare en sträng som innehåller en sökväg (men inte en literal sökväg) till `Push-Location` .</span><span class="sxs-lookup"><span data-stu-id="dbc84-160">You can pipe a string that contains a path (but not a literal path) to `Push-Location`.</span></span>

## <span data-ttu-id="dbc84-161">UTDATA</span><span class="sxs-lookup"><span data-stu-id="dbc84-161">OUTPUTS</span></span>

### <span data-ttu-id="dbc84-162">Ingen eller system. Management. Automation. PathInfo</span><span class="sxs-lookup"><span data-stu-id="dbc84-162">None or System.Management.Automation.PathInfo</span></span>

<span data-ttu-id="dbc84-163">När du använder parametern **Passthru** `Push-Location` genereras ett **system. Management. Automation. PathInfo** -objekt som representerar platsen.</span><span class="sxs-lookup"><span data-stu-id="dbc84-163">When you use the **PassThru** parameter, `Push-Location` generates a **System.Management.Automation.PathInfo** object that represents the location.</span></span> <span data-ttu-id="dbc84-164">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="dbc84-164">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="dbc84-165">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="dbc84-165">NOTES</span></span>

<span data-ttu-id="dbc84-166">PowerShell stöder flera körnings utrymmen per process.</span><span class="sxs-lookup"><span data-stu-id="dbc84-166">PowerShell supports multiple runspaces per process.</span></span> <span data-ttu-id="dbc84-167">Varje körnings utrymme har sin egen _aktuella katalog_.</span><span class="sxs-lookup"><span data-stu-id="dbc84-167">Each runspace has its own _current directory_.</span></span>
<span data-ttu-id="dbc84-168">Detta är inte samma som `[System.Environment]::CurrentDirectory` .</span><span class="sxs-lookup"><span data-stu-id="dbc84-168">This is not the same as `[System.Environment]::CurrentDirectory`.</span></span> <span data-ttu-id="dbc84-169">Det här problemet kan vara ett problem när du anropar .NET-API: er eller kör ursprungliga program utan att ange explicita katalog Sök vägar.</span><span class="sxs-lookup"><span data-stu-id="dbc84-169">This behavior can be an issue when calling .NET APIs or running native applications without providing explicit directory paths.</span></span>

<span data-ttu-id="dbc84-170">Även om plats-cmdletarna har angett den aktuella katalogen för hela processen, är du inte beroende av den eftersom en annan körnings utrymme kan ändra den när som helst.</span><span class="sxs-lookup"><span data-stu-id="dbc84-170">Even if the location cmdlets did set the process-wide current directory, you can't depend on it because another runspace might change it at any time.</span></span> <span data-ttu-id="dbc84-171">Du bör använda plats-cmdletar för att utföra vägbaserade åtgärder med hjälp av den aktuella arbets katalogen som är unik för den aktuella körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="dbc84-171">You should use the location cmdlets to perform path-based operations using the current working directory specific to the current runspace.</span></span>

<span data-ttu-id="dbc84-172">En stack är en sista ingångs punkt som endast det objekt som lagts till senast har åtkomst till.</span><span class="sxs-lookup"><span data-stu-id="dbc84-172">A stack is a last-in, first-out list in which only the most recently added item is accessible.</span></span>
<span data-ttu-id="dbc84-173">Du lägger till objekt i en stack i den ordning som du använder dem och hämtar dem sedan för användning i omvänd ordning.</span><span class="sxs-lookup"><span data-stu-id="dbc84-173">You add items to a stack in the order that you use them, and then retrieve them for use in the reverse order.</span></span> <span data-ttu-id="dbc84-174">Med PowerShell kan du lagra leverantörs platser i plats stackar.</span><span class="sxs-lookup"><span data-stu-id="dbc84-174">PowerShell lets you store provider locations in location stacks.</span></span>

<span data-ttu-id="dbc84-175">PowerShell skapar en namnlös standard plats stack och du kan skapa flera namngivna plats stackar.</span><span class="sxs-lookup"><span data-stu-id="dbc84-175">PowerShell creates an unnamed default location stack and you can create multiple named location stacks.</span></span> <span data-ttu-id="dbc84-176">Om du inte anger något stack namn använder PowerShell den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="dbc84-176">If you do not specify a stack name, PowerShell uses the current location stack.</span></span> <span data-ttu-id="dbc84-177">Som standard är den namnlösa standard platsen den aktuella plats stacken, men du kan använda `Set-Location` cmdleten för att ändra den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="dbc84-177">By default, the unnamed default location is the current location stack, but you can use the `Set-Location` cmdlet to change the current location stack.</span></span>

<span data-ttu-id="dbc84-178">Om du vill hantera plats stackar använder du cmdletarna för PowerShell-platsen på följande sätt.</span><span class="sxs-lookup"><span data-stu-id="dbc84-178">To manage location stacks, use the PowerShell Location cmdlets, as follows.</span></span>

- <span data-ttu-id="dbc84-179">Om du vill lägga till en plats i en plats stack använder du `Push-Location` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="dbc84-179">To add a location to a location stack, use the `Push-Location` cmdlet.</span></span>

- <span data-ttu-id="dbc84-180">Använd cmdleten för att hämta en plats från en plats stack `Pop-Location` .</span><span class="sxs-lookup"><span data-stu-id="dbc84-180">To get a location from a location stack, use the `Pop-Location` cmdlet.</span></span>

- <span data-ttu-id="dbc84-181">Om du vill visa platserna i den aktuella platsens stack, använder du cmdlet-parametern **stack** `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="dbc84-181">To display the locations in the current location stack, use the **Stack** parameter of the `Get-Location` cmdlet.</span></span>

- <span data-ttu-id="dbc84-182">Om du vill visa platserna i en namngiven plats stack använder du parametern **StackName** för `Get-Location` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="dbc84-182">To display the locations in a named location stack, use the **StackName** parameter of the `Get-Location` cmdlet.</span></span>

- <span data-ttu-id="dbc84-183">Om du vill skapa en ny plats stack använder du parametern StackName för `Push-Location` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="dbc84-183">To create a new location stack, use the StackName parameter of the `Push-Location` cmdlet.</span></span> <span data-ttu-id="dbc84-184">Om du anger en stack som inte finns `Push-Location` skapar stacken.</span><span class="sxs-lookup"><span data-stu-id="dbc84-184">If you specify a stack that does not exist, `Push-Location` creates the stack.</span></span>

- <span data-ttu-id="dbc84-185">Om du vill skapa en plats stack för den aktuella plats stacken använder du parametern StackName för `Set-Location` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="dbc84-185">To make a location stack the current location stack, use the StackName parameter of the `Set-Location` cmdlet.</span></span>

<span data-ttu-id="dbc84-186">Den namnlösa standard plats stacken är endast tillgänglig när den är den aktuella plats stacken.</span><span class="sxs-lookup"><span data-stu-id="dbc84-186">The unnamed default location stack is fully accessible only when it is the current location stack.</span></span>
<span data-ttu-id="dbc84-187">Om du skapar en namngiven plats stack för den aktuella plats stacken kan du inte längre använda `Push-Location` `Pop-Location` cmdletarna eller för att lägga till eller hämta objekt från standard stacken eller `Get-Location` använda cmdleten för att Visa platserna i den namnlösa stacken.</span><span class="sxs-lookup"><span data-stu-id="dbc84-187">If you make a named location stack the current location stack, you can no longer use the `Push-Location` or `Pop-Location` cmdlets to add or get items from the default stack or use the `Get-Location` cmdlet to display the locations in the unnamed stack.</span></span> <span data-ttu-id="dbc84-188">Om du vill göra den namnlösa stacken till den aktuella stacken använder du parametern **StackName** för `Set-Location` cmdleten med värdet `$null` eller en tom sträng ( `""` ).</span><span class="sxs-lookup"><span data-stu-id="dbc84-188">To make the unnamed stack the current stack, use the **StackName** parameter of the `Set-Location` cmdlet with a value of `$null` or an empty string (`""`).</span></span>

<span data-ttu-id="dbc84-189">Du kan också referera till `Push-Location` med dess inbyggda alias `pushd` .</span><span class="sxs-lookup"><span data-stu-id="dbc84-189">You can also refer to `Push-Location` by its built-in alias, `pushd`.</span></span> <span data-ttu-id="dbc84-190">Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="dbc84-190">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="dbc84-191">`Push-Location`Cmdleten är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="dbc84-191">The `Push-Location` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="dbc84-192">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="dbc84-192">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="dbc84-193">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="dbc84-193">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="dbc84-194">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="dbc84-194">RELATED LINKS</span></span>

[<span data-ttu-id="dbc84-195">Get-location</span><span class="sxs-lookup"><span data-stu-id="dbc84-195">Get-Location</span></span>](Get-Location.md)

[<span data-ttu-id="dbc84-196">Pop-location</span><span class="sxs-lookup"><span data-stu-id="dbc84-196">Pop-Location</span></span>](Pop-Location.md)

[<span data-ttu-id="dbc84-197">Ange plats</span><span class="sxs-lookup"><span data-stu-id="dbc84-197">Set-Location</span></span>](Set-Location.md)

[<span data-ttu-id="dbc84-198">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="dbc84-198">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="dbc84-199">about_Providers</span><span class="sxs-lookup"><span data-stu-id="dbc84-199">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)