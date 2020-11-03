---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-process?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Process
ms.openlocfilehash: 4efa22e8f2a7339e381d92270c1b127054c219cb
ms.sourcegitcommit: 11abf355ac545531c2b04217a08ebe6be609c0bb
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/18/2020
ms.locfileid: "93269540"
---
# <span data-ttu-id="50031-103">Stop-Process</span><span class="sxs-lookup"><span data-stu-id="50031-103">Stop-Process</span></span>

## <span data-ttu-id="50031-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="50031-104">SYNOPSIS</span></span>
<span data-ttu-id="50031-105">Stoppar en eller flera processer som körs.</span><span class="sxs-lookup"><span data-stu-id="50031-105">Stops one or more running processes.</span></span>

## <span data-ttu-id="50031-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="50031-106">SYNTAX</span></span>

### <span data-ttu-id="50031-107">ID (standard)</span><span class="sxs-lookup"><span data-stu-id="50031-107">Id (Default)</span></span>

```
Stop-Process [-Id] <Int32[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="50031-108">Name</span><span class="sxs-lookup"><span data-stu-id="50031-108">Name</span></span>

```
Stop-Process -Name <String[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="50031-109">InputObject</span><span class="sxs-lookup"><span data-stu-id="50031-109">InputObject</span></span>

```
Stop-Process [-InputObject] <Process[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="50031-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="50031-110">DESCRIPTION</span></span>

<span data-ttu-id="50031-111">Cmdleten **Stop process** stoppar en eller flera processer som körs.</span><span class="sxs-lookup"><span data-stu-id="50031-111">The **Stop-Process** cmdlet stops one or more running processes.</span></span>
<span data-ttu-id="50031-112">Du kan ange en process efter process namn eller process-ID (PID) eller skicka ett process objekt till **stopp processen**.</span><span class="sxs-lookup"><span data-stu-id="50031-112">You can specify a process by process name or process ID (PID), or pass a process object to **Stop-Process**.</span></span>
<span data-ttu-id="50031-113">**Stop-processen** fungerar bara på processer som körs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="50031-113">**Stop-Process** works only on processes running on the local computer.</span></span>

<span data-ttu-id="50031-114">I Windows Vista och senare versioner av Windows operativ system, för att stoppa en process som inte ägs av den aktuella användaren, måste du starta PowerShell med alternativet Kör som administratör.</span><span class="sxs-lookup"><span data-stu-id="50031-114">On Windows Vista and later versions of the Windows operating system, to stop a process that is not owned by the current user, you must start PowerShell by using the Run as administrator option.</span></span>
<span data-ttu-id="50031-115">Du behöver inte heller bekräfta en bekräftelse om du inte anger parametern *Bekräfta* .</span><span class="sxs-lookup"><span data-stu-id="50031-115">Also, you are not prompted for confirmation unless you specify the *Confirm* parameter.</span></span>

## <span data-ttu-id="50031-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="50031-116">EXAMPLES</span></span>

### <span data-ttu-id="50031-117">Exempel 1: stoppa alla instanser av en process</span><span class="sxs-lookup"><span data-stu-id="50031-117">Example 1: Stop all instances of a process</span></span>

```
PS C:\> Stop-Process -Name "notepad"
```

<span data-ttu-id="50031-118">Det här kommandot stoppar alla instanser av anteckningar-processen på datorn.</span><span class="sxs-lookup"><span data-stu-id="50031-118">This command stops all instances of the Notepad process on the computer.</span></span>
<span data-ttu-id="50031-119">Varje instans av anteckningar körs i sin egen process.</span><span class="sxs-lookup"><span data-stu-id="50031-119">Each instance of Notepad runs in its own process.</span></span>
<span data-ttu-id="50031-120">Parametern *Name* används för att ange processer som har samma namn.</span><span class="sxs-lookup"><span data-stu-id="50031-120">It uses the *Name* parameter to specify the processes, all of which have the same name.</span></span>
<span data-ttu-id="50031-121">Om du vill använda *ID-* parametern för att stoppa samma processer måste du ange process-ID: n för varje instans av anteckningar.</span><span class="sxs-lookup"><span data-stu-id="50031-121">If you were to use the *Id* parameter to stop the same processes, you would have to list the process IDs of each instance of Notepad.</span></span>

### <span data-ttu-id="50031-122">Exempel 2: stoppa en speciell instans av en process</span><span class="sxs-lookup"><span data-stu-id="50031-122">Example 2: Stop a specific instance of a process</span></span>

```
PS C:\> Stop-Process -Id 3952 -Confirm -PassThru
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "notepad (3952)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):y
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
41       2      996       3212    31            3952 notepad
```

<span data-ttu-id="50031-123">Det här kommandot stoppar en viss instans av anteckningar-processen.</span><span class="sxs-lookup"><span data-stu-id="50031-123">This command stops a particular instance of the Notepad process.</span></span>
<span data-ttu-id="50031-124">Den använder process-ID: t 3952 för att identifiera processen.</span><span class="sxs-lookup"><span data-stu-id="50031-124">It uses the process ID, 3952, to identify the process.</span></span>
<span data-ttu-id="50031-125">Parametern *Confirm* instruerar PowerShell att fråga dig innan processen stoppas.</span><span class="sxs-lookup"><span data-stu-id="50031-125">The *Confirm* parameter directs PowerShell to prompt you before it stops the process.</span></span>
<span data-ttu-id="50031-126">Eftersom meddelandet innehåller process namnet förutom ID: t, är det här bästa praxis.</span><span class="sxs-lookup"><span data-stu-id="50031-126">Because the prompt includes the process namein addition to its ID, this is best practice.</span></span>
<span data-ttu-id="50031-127">Parametern *Passthru* skickar processobjektet till Formatter för visning.</span><span class="sxs-lookup"><span data-stu-id="50031-127">The *PassThru* parameter passes the process object to the formatter for display.</span></span>
<span data-ttu-id="50031-128">Utan den här parametern visas ingen visning efter ett kommando för att **stoppa processen** .</span><span class="sxs-lookup"><span data-stu-id="50031-128">Without this parameter, there would be no display after a **Stop-Process** command.</span></span>

### <span data-ttu-id="50031-129">Exempel 3: stoppa en process och identifiera att den har stoppats</span><span class="sxs-lookup"><span data-stu-id="50031-129">Example 3: Stop a process and detect that it has stopped</span></span>

```
PS C:\> calc
PS C:\> $p = Get-Process -Name "calc"
PS C:\> Stop-Process -InputObject $p
PS C:\> Get-Process | Where-Object {$_.HasExited}
```

<span data-ttu-id="50031-130">Den här serien med kommandon startar och stoppar Calc-processen och identifierar sedan processer som har stoppats.</span><span class="sxs-lookup"><span data-stu-id="50031-130">This series of commands starts and stops the Calc process, and then detects processes that have stopped.</span></span>

<span data-ttu-id="50031-131">Det första kommandot startar en variant av kalkylatorn.</span><span class="sxs-lookup"><span data-stu-id="50031-131">The first command starts an instance of the calculator.</span></span>

<span data-ttu-id="50031-132">Det andra kommandot använder **Get-process** hämtar ett objekt som representerar Calc-processen och lagrar det sedan i variabeln $p.</span><span class="sxs-lookup"><span data-stu-id="50031-132">The second command uses **Get-Process** gets an object that represents the Calc process, and then stores it in the $p variable.</span></span>

<span data-ttu-id="50031-133">Det tredje kommandot stoppar Calc-processen.</span><span class="sxs-lookup"><span data-stu-id="50031-133">The third command stops the Calc process.</span></span>
<span data-ttu-id="50031-134">Parametern *InputObject* används för att skicka objektet till **Stop-process**.</span><span class="sxs-lookup"><span data-stu-id="50031-134">It uses the *InputObject* parameter to pass the object to **Stop-Process**.</span></span>

<span data-ttu-id="50031-135">Det sista kommandot hämtar alla processer på datorn som kördes men som nu har stoppats.</span><span class="sxs-lookup"><span data-stu-id="50031-135">The last command gets all of the processes on the computer that were running but that are now stopped.</span></span>
<span data-ttu-id="50031-136">Den använder **Get-process** för att hämta alla processer på datorn.</span><span class="sxs-lookup"><span data-stu-id="50031-136">It uses **Get-Process** to get all of the processes on the computer.</span></span>
<span data-ttu-id="50031-137">Pipeline-operatorn (|) skickar resultatet till Where-Object-cmdleten, som väljer de där värdet för egenskapen **HasExited** är $true.</span><span class="sxs-lookup"><span data-stu-id="50031-137">The pipeline operator (|) passes the results to the Where-Object cmdlet, which selects the ones where the value of the **HasExited** property is $True.</span></span>
<span data-ttu-id="50031-138">**HasExited** är bara en egenskap för process objekt.</span><span class="sxs-lookup"><span data-stu-id="50031-138">**HasExited** is just one property of process objects.</span></span>
<span data-ttu-id="50031-139">Om du vill söka efter alla egenskaper skriver du `Get-Process | Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="50031-139">To find all the properties, type `Get-Process | Get-Member`.</span></span>

### <span data-ttu-id="50031-140">Exempel 4: stoppa en process som inte ägs av den aktuella användaren</span><span class="sxs-lookup"><span data-stu-id="50031-140">Example 4: Stop a process not owned by the current user</span></span>

```
PS C:\> Get-Process -Name "lsass" | Stop-Process

Stop-Process : Cannot stop process 'lsass (596)' because of the following error: Access is denied
At line:1 char:34
+ Get-Process -Name "lsass" | Stop-Process <<<<

[ADMIN]: PS C:\> Get-Process -Name "lsass" | Stop-Process

Warning!
Are you sure you want to perform this action?
Performing operation 'Stop-Process' on Target 'lsass(596)'
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
[ADMIN]: PS C:\> Get-Process -Name "lsass" | Stop-Process -Force
[ADMIN]: PS C:\>
```

<span data-ttu-id="50031-141">De här kommandona visar effekterna av att använda *tvång* för att stoppa en process som inte ägs av användaren.</span><span class="sxs-lookup"><span data-stu-id="50031-141">These commands show the effect of using *Force* to stop a process that is not owned by the user.</span></span>

<span data-ttu-id="50031-142">Det första kommandot använder **Get-process** för att hämta lsass-processen.</span><span class="sxs-lookup"><span data-stu-id="50031-142">The first command uses **Get-Process** to get the Lsass process.</span></span>
<span data-ttu-id="50031-143">En pipeline-operator skickar processen till **stopp-processen** för att stoppa den.</span><span class="sxs-lookup"><span data-stu-id="50031-143">A pipeline operator sends the process to **Stop-Process** to stop it.</span></span>
<span data-ttu-id="50031-144">Som visas i exemplet på utdata Miss lyckas det första kommandot med ett meddelande om nekad åtkomst, eftersom den här processen endast kan stoppas av en medlem i administratörs gruppen på datorn.</span><span class="sxs-lookup"><span data-stu-id="50031-144">As shown in the sample output, the first command fails with an Access denied message, because this process can be stopped only by a member of the Administrator group on the computer.</span></span>

<span data-ttu-id="50031-145">När PowerShell öppnas med alternativet Kör som administratör och kommandot upprepas, uppmanas du i PowerShell att bekräfta.</span><span class="sxs-lookup"><span data-stu-id="50031-145">When PowerShell is opened by using the Run as administrator option, and the command is repeated, PowerShell prompts you for confirmation.</span></span>

<span data-ttu-id="50031-146">Det andra kommandot anger *tvinga* att utelämna prompten.</span><span class="sxs-lookup"><span data-stu-id="50031-146">The second command specifies *Force* to suppress the prompt.</span></span>
<span data-ttu-id="50031-147">Därför stoppas processen utan bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="50031-147">As a result, the process is stopped without confirmation.</span></span>

## <span data-ttu-id="50031-148">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="50031-148">PARAMETERS</span></span>

### <span data-ttu-id="50031-149">-Force</span><span class="sxs-lookup"><span data-stu-id="50031-149">-Force</span></span>

<span data-ttu-id="50031-150">Stoppar de angivna processerna utan att uppmanas att bekräfta.</span><span class="sxs-lookup"><span data-stu-id="50031-150">Stops the specified processes without prompting for confirmation.</span></span>
<span data-ttu-id="50031-151">Som standard uppmanas du att **Bekräfta genom att** bekräfta innan du stoppar en process som inte ägs av den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="50031-151">By default, **Stop-Process** prompts for confirmation before stopping any process that is not owned by the current user.</span></span>

<span data-ttu-id="50031-152">Om du vill hitta ägaren till en process använder du `Get-CimInstance` cmdleten för att hämta ett **Win32_Process** -objekt som representerar processen och använder sedan **GetOwner** -metoden för objektet.</span><span class="sxs-lookup"><span data-stu-id="50031-152">To find the owner of a process, use the `Get-CimInstance` cmdlet to get a **Win32_Process** object that represents the process, and then use the **GetOwner** method of the object.</span></span>

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

### <span data-ttu-id="50031-153">-ID</span><span class="sxs-lookup"><span data-stu-id="50031-153">-Id</span></span>

<span data-ttu-id="50031-154">Anger process-ID: n för de processer som ska stoppas.</span><span class="sxs-lookup"><span data-stu-id="50031-154">Specifies the process IDs of the processes to stop.</span></span>
<span data-ttu-id="50031-155">Använd kommatecken för att avgränsa ID: n för att ange flera ID: n.</span><span class="sxs-lookup"><span data-stu-id="50031-155">To specify multiple IDs, use commas to separate the IDs.</span></span>
<span data-ttu-id="50031-156">Om du vill hitta ett process-ID skriver du `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="50031-156">To find the PID of a process, type `Get-Process`.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="50031-157">– InputObject</span><span class="sxs-lookup"><span data-stu-id="50031-157">-InputObject</span></span>

<span data-ttu-id="50031-158">Anger de process objekt som ska stoppas.</span><span class="sxs-lookup"><span data-stu-id="50031-158">Specifies the process objects to stop.</span></span>
<span data-ttu-id="50031-159">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="50031-159">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="50031-160">-Name</span><span class="sxs-lookup"><span data-stu-id="50031-160">-Name</span></span>

<span data-ttu-id="50031-161">Anger process namnen för de processer som ska stoppas.</span><span class="sxs-lookup"><span data-stu-id="50031-161">Specifies the process names of the processes to stop.</span></span>
<span data-ttu-id="50031-162">Du kan skriva flera process namn, avgränsade med kommatecken eller använda jokertecken.</span><span class="sxs-lookup"><span data-stu-id="50031-162">You can type multiple process names, separated by commas, or use wildcard characters.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases: ProcessName

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="50031-163">– PassThru</span><span class="sxs-lookup"><span data-stu-id="50031-163">-PassThru</span></span>

<span data-ttu-id="50031-164">Returnerar ett objekt som representerar processen.</span><span class="sxs-lookup"><span data-stu-id="50031-164">Returns an object that represents the process.</span></span>
<span data-ttu-id="50031-165">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="50031-165">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="50031-166">-Confirm</span><span class="sxs-lookup"><span data-stu-id="50031-166">-Confirm</span></span>

<span data-ttu-id="50031-167">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="50031-167">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="50031-168">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="50031-168">-WhatIf</span></span>

<span data-ttu-id="50031-169">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="50031-169">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="50031-170">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="50031-170">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="50031-171">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="50031-171">CommonParameters</span></span>

<span data-ttu-id="50031-172">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="50031-172">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="50031-173">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="50031-173">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="50031-174">INDATA</span><span class="sxs-lookup"><span data-stu-id="50031-174">INPUTS</span></span>

### <span data-ttu-id="50031-175">System. Diagnostics. process</span><span class="sxs-lookup"><span data-stu-id="50031-175">System.Diagnostics.Process</span></span>

<span data-ttu-id="50031-176">Du kan skicka vidare ett process objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="50031-176">You can pipe a process object to this cmdlet.</span></span>

## <span data-ttu-id="50031-177">UTDATA</span><span class="sxs-lookup"><span data-stu-id="50031-177">OUTPUTS</span></span>

### <span data-ttu-id="50031-178">Ingen, system. Diagnostics. process</span><span class="sxs-lookup"><span data-stu-id="50031-178">None, System.Diagnostics.Process</span></span>

<span data-ttu-id="50031-179">Denna cmdlet returnerar ett **system. Diagnostics. process** -objekt som representerar den stoppade processen, om du anger parametern *Passthru* .</span><span class="sxs-lookup"><span data-stu-id="50031-179">This cmdlet returns a **System.Diagnostics.Process** object that represents the stopped process, if you specify the *PassThru* parameter.</span></span>
<span data-ttu-id="50031-180">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="50031-180">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="50031-181">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="50031-181">NOTES</span></span>

* <span data-ttu-id="50031-182">Du kan också referera till **stopp processen** med hjälp av inbyggda alias, **Kill** och **SPPs**.</span><span class="sxs-lookup"><span data-stu-id="50031-182">You can also refer to **Stop-Process** by its built-in aliases, **kill** and **spps**.</span></span> <span data-ttu-id="50031-183">Mer information finns i about_Aliases.</span><span class="sxs-lookup"><span data-stu-id="50031-183">For more information, see about_Aliases.</span></span>

  <span data-ttu-id="50031-184">Du kan också använda egenskaperna och metoderna för **Win32_Process** -objektet Windows Management Instrumentation (WMI) i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="50031-184">You can also use the properties and methods of the Windows Management Instrumentation (WMI) **Win32_Process** object in Windows PowerShell.</span></span>
<span data-ttu-id="50031-185">Mer information finns i `Get-CimInstance` och WMI SDK.</span><span class="sxs-lookup"><span data-stu-id="50031-185">For more information, see `Get-CimInstance` and the WMI SDK.</span></span>

* <span data-ttu-id="50031-186">När du stoppar processer kan du tänka på att processen som stoppar processen kan stoppa processer och tjänster som är beroende av processen.</span><span class="sxs-lookup"><span data-stu-id="50031-186">When stopping processes, realize that stopping a process can stop process and services that depend on the process.</span></span>
<span data-ttu-id="50031-187">I ett extrema fall kan en process stoppa Windows.</span><span class="sxs-lookup"><span data-stu-id="50031-187">In an extreme case, stopping a process can stop Windows.</span></span>

## <span data-ttu-id="50031-188">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="50031-188">RELATED LINKS</span></span>

[<span data-ttu-id="50031-189">Fel sökning – process</span><span class="sxs-lookup"><span data-stu-id="50031-189">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="50031-190">Hämta process</span><span class="sxs-lookup"><span data-stu-id="50031-190">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="50031-191">Start process</span><span class="sxs-lookup"><span data-stu-id="50031-191">Start-Process</span></span>](Start-Process.md)

[<span data-ttu-id="50031-192">Stoppa – process</span><span class="sxs-lookup"><span data-stu-id="50031-192">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="50031-193">Vänta-process</span><span class="sxs-lookup"><span data-stu-id="50031-193">Wait-Process</span></span>](Wait-Process.md)
