---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-process?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Process
ms.openlocfilehash: 8c9e520f1f19444fd538fabee99a48ec08c69992
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710159"
---
# <span data-ttu-id="95cef-102">Stop-Process</span><span class="sxs-lookup"><span data-stu-id="95cef-102">Stop-Process</span></span>

## <span data-ttu-id="95cef-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="95cef-103">SYNOPSIS</span></span>
<span data-ttu-id="95cef-104">Stoppar en eller flera processer som körs.</span><span class="sxs-lookup"><span data-stu-id="95cef-104">Stops one or more running processes.</span></span>

## <span data-ttu-id="95cef-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="95cef-105">SYNTAX</span></span>

### <span data-ttu-id="95cef-106">ID (standard)</span><span class="sxs-lookup"><span data-stu-id="95cef-106">Id (Default)</span></span>

```
Stop-Process [-Id] <Int32[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="95cef-107">Namn</span><span class="sxs-lookup"><span data-stu-id="95cef-107">Name</span></span>

```
Stop-Process -Name <String[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="95cef-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="95cef-108">InputObject</span></span>

```
Stop-Process [-InputObject] <Process[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="95cef-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="95cef-109">DESCRIPTION</span></span>

<span data-ttu-id="95cef-110">Cmdleten **Stop process** stoppar en eller flera processer som körs.</span><span class="sxs-lookup"><span data-stu-id="95cef-110">The **Stop-Process** cmdlet stops one or more running processes.</span></span>
<span data-ttu-id="95cef-111">Du kan ange en process efter process namn eller process-ID (PID) eller skicka ett process objekt till **stopp processen**.</span><span class="sxs-lookup"><span data-stu-id="95cef-111">You can specify a process by process name or process ID (PID), or pass a process object to **Stop-Process**.</span></span>
<span data-ttu-id="95cef-112">**Stop-processen** fungerar bara på processer som körs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="95cef-112">**Stop-Process** works only on processes running on the local computer.</span></span>

<span data-ttu-id="95cef-113">I Windows Vista och senare versioner av Windows operativ system, för att stoppa en process som inte ägs av den aktuella användaren, måste du starta PowerShell med alternativet Kör som administratör.</span><span class="sxs-lookup"><span data-stu-id="95cef-113">On Windows Vista and later versions of the Windows operating system, to stop a process that is not owned by the current user, you must start PowerShell by using the Run as administrator option.</span></span>
<span data-ttu-id="95cef-114">Du behöver inte heller bekräfta en bekräftelse om du inte anger parametern *Bekräfta* .</span><span class="sxs-lookup"><span data-stu-id="95cef-114">Also, you are not prompted for confirmation unless you specify the *Confirm* parameter.</span></span>

## <span data-ttu-id="95cef-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="95cef-115">EXAMPLES</span></span>

### <span data-ttu-id="95cef-116">Exempel 1: stoppa alla instanser av en process</span><span class="sxs-lookup"><span data-stu-id="95cef-116">Example 1: Stop all instances of a process</span></span>

```
PS C:\> Stop-Process -Name "notepad"
```

<span data-ttu-id="95cef-117">Det här kommandot stoppar alla instanser av anteckningar-processen på datorn.</span><span class="sxs-lookup"><span data-stu-id="95cef-117">This command stops all instances of the Notepad process on the computer.</span></span>
<span data-ttu-id="95cef-118">Varje instans av anteckningar körs i sin egen process.</span><span class="sxs-lookup"><span data-stu-id="95cef-118">Each instance of Notepad runs in its own process.</span></span>
<span data-ttu-id="95cef-119">Parametern *Name* används för att ange processer som har samma namn.</span><span class="sxs-lookup"><span data-stu-id="95cef-119">It uses the *Name* parameter to specify the processes, all of which have the same name.</span></span>
<span data-ttu-id="95cef-120">Om du vill använda *ID-* parametern för att stoppa samma processer måste du ange process-ID: n för varje instans av anteckningar.</span><span class="sxs-lookup"><span data-stu-id="95cef-120">If you were to use the *Id* parameter to stop the same processes, you would have to list the process IDs of each instance of Notepad.</span></span>

### <span data-ttu-id="95cef-121">Exempel 2: stoppa en speciell instans av en process</span><span class="sxs-lookup"><span data-stu-id="95cef-121">Example 2: Stop a specific instance of a process</span></span>

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

<span data-ttu-id="95cef-122">Det här kommandot stoppar en viss instans av anteckningar-processen.</span><span class="sxs-lookup"><span data-stu-id="95cef-122">This command stops a particular instance of the Notepad process.</span></span>
<span data-ttu-id="95cef-123">Den använder process-ID: t 3952 för att identifiera processen.</span><span class="sxs-lookup"><span data-stu-id="95cef-123">It uses the process ID, 3952, to identify the process.</span></span>
<span data-ttu-id="95cef-124">Parametern *Confirm* instruerar PowerShell att fråga dig innan processen stoppas.</span><span class="sxs-lookup"><span data-stu-id="95cef-124">The *Confirm* parameter directs PowerShell to prompt you before it stops the process.</span></span>
<span data-ttu-id="95cef-125">Eftersom meddelandet innehåller process namnet förutom ID: t, är det här bästa praxis.</span><span class="sxs-lookup"><span data-stu-id="95cef-125">Because the prompt includes the process namein addition to its ID, this is best practice.</span></span>
<span data-ttu-id="95cef-126">Parametern *Passthru* skickar processobjektet till Formatter för visning.</span><span class="sxs-lookup"><span data-stu-id="95cef-126">The *PassThru* parameter passes the process object to the formatter for display.</span></span>
<span data-ttu-id="95cef-127">Utan den här parametern visas ingen visning efter ett kommando för att **stoppa processen** .</span><span class="sxs-lookup"><span data-stu-id="95cef-127">Without this parameter, there would be no display after a **Stop-Process** command.</span></span>

### <span data-ttu-id="95cef-128">Exempel 3: stoppa en process och identifiera att den har stoppats</span><span class="sxs-lookup"><span data-stu-id="95cef-128">Example 3: Stop a process and detect that it has stopped</span></span>

```
PS C:\> calc
PS C:\> $p = Get-Process -Name "calc"
PS C:\> Stop-Process -InputObject $p
PS C:\> Get-Process | Where-Object {$_.HasExited}
```

<span data-ttu-id="95cef-129">Den här serien med kommandon startar och stoppar Calc-processen och identifierar sedan processer som har stoppats.</span><span class="sxs-lookup"><span data-stu-id="95cef-129">This series of commands starts and stops the Calc process, and then detects processes that have stopped.</span></span>

<span data-ttu-id="95cef-130">Det första kommandot startar en variant av kalkylatorn.</span><span class="sxs-lookup"><span data-stu-id="95cef-130">The first command starts an instance of the calculator.</span></span>

<span data-ttu-id="95cef-131">Det andra kommandot använder **Get-process** hämtar ett objekt som representerar Calc-processen och lagrar det sedan i variabeln $p.</span><span class="sxs-lookup"><span data-stu-id="95cef-131">The second command uses **Get-Process** gets an object that represents the Calc process, and then stores it in the $p variable.</span></span>

<span data-ttu-id="95cef-132">Det tredje kommandot stoppar Calc-processen.</span><span class="sxs-lookup"><span data-stu-id="95cef-132">The third command stops the Calc process.</span></span>
<span data-ttu-id="95cef-133">Parametern *InputObject* används för att skicka objektet till **Stop-process**.</span><span class="sxs-lookup"><span data-stu-id="95cef-133">It uses the *InputObject* parameter to pass the object to **Stop-Process**.</span></span>

<span data-ttu-id="95cef-134">Det sista kommandot hämtar alla processer på datorn som kördes men som nu har stoppats.</span><span class="sxs-lookup"><span data-stu-id="95cef-134">The last command gets all of the processes on the computer that were running but that are now stopped.</span></span>
<span data-ttu-id="95cef-135">Den använder **Get-process** för att hämta alla processer på datorn.</span><span class="sxs-lookup"><span data-stu-id="95cef-135">It uses **Get-Process** to get all of the processes on the computer.</span></span>
<span data-ttu-id="95cef-136">Pipeline-operatorn (|) skickar resultatet till Where-Object-cmdleten, som väljer de där värdet för egenskapen **HasExited** är $true.</span><span class="sxs-lookup"><span data-stu-id="95cef-136">The pipeline operator (|) passes the results to the Where-Object cmdlet, which selects the ones where the value of the **HasExited** property is $True.</span></span>
<span data-ttu-id="95cef-137">**HasExited** är bara en egenskap för process objekt.</span><span class="sxs-lookup"><span data-stu-id="95cef-137">**HasExited** is just one property of process objects.</span></span>
<span data-ttu-id="95cef-138">Om du vill söka efter alla egenskaper skriver du `Get-Process | Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="95cef-138">To find all the properties, type `Get-Process | Get-Member`.</span></span>

### <span data-ttu-id="95cef-139">Exempel 4: stoppa en process som inte ägs av den aktuella användaren</span><span class="sxs-lookup"><span data-stu-id="95cef-139">Example 4: Stop a process not owned by the current user</span></span>

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

<span data-ttu-id="95cef-140">De här kommandona visar effekterna av att använda *tvång* för att stoppa en process som inte ägs av användaren.</span><span class="sxs-lookup"><span data-stu-id="95cef-140">These commands show the effect of using *Force* to stop a process that is not owned by the user.</span></span>

<span data-ttu-id="95cef-141">Det första kommandot använder **Get-process** för att hämta lsass-processen.</span><span class="sxs-lookup"><span data-stu-id="95cef-141">The first command uses **Get-Process** to get the Lsass process.</span></span>
<span data-ttu-id="95cef-142">En pipeline-operator skickar processen till **stopp-processen** för att stoppa den.</span><span class="sxs-lookup"><span data-stu-id="95cef-142">A pipeline operator sends the process to **Stop-Process** to stop it.</span></span>
<span data-ttu-id="95cef-143">Som visas i exemplet på utdata Miss lyckas det första kommandot med ett meddelande om nekad åtkomst, eftersom den här processen endast kan stoppas av en medlem i administratörs gruppen på datorn.</span><span class="sxs-lookup"><span data-stu-id="95cef-143">As shown in the sample output, the first command fails with an Access denied message, because this process can be stopped only by a member of the Administrator group on the computer.</span></span>

<span data-ttu-id="95cef-144">När PowerShell öppnas med alternativet Kör som administratör och kommandot upprepas, uppmanas du i PowerShell att bekräfta.</span><span class="sxs-lookup"><span data-stu-id="95cef-144">When PowerShell is opened by using the Run as administrator option, and the command is repeated, PowerShell prompts you for confirmation.</span></span>

<span data-ttu-id="95cef-145">Det andra kommandot anger *tvinga* att utelämna prompten.</span><span class="sxs-lookup"><span data-stu-id="95cef-145">The second command specifies *Force* to suppress the prompt.</span></span>
<span data-ttu-id="95cef-146">Därför stoppas processen utan bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="95cef-146">As a result, the process is stopped without confirmation.</span></span>

## <span data-ttu-id="95cef-147">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="95cef-147">PARAMETERS</span></span>

### <span data-ttu-id="95cef-148">-Force</span><span class="sxs-lookup"><span data-stu-id="95cef-148">-Force</span></span>

<span data-ttu-id="95cef-149">Stoppar de angivna processerna utan att uppmanas att bekräfta.</span><span class="sxs-lookup"><span data-stu-id="95cef-149">Stops the specified processes without prompting for confirmation.</span></span>
<span data-ttu-id="95cef-150">Som standard uppmanas du att **Bekräfta genom att** bekräfta innan du stoppar en process som inte ägs av den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="95cef-150">By default, **Stop-Process** prompts for confirmation before stopping any process that is not owned by the current user.</span></span>

<span data-ttu-id="95cef-151">Om du vill hitta ägaren till en process använder du `Get-CimInstance` cmdleten för att hämta ett **Win32_Process** -objekt som representerar processen och använder sedan **GetOwner** -metoden för objektet.</span><span class="sxs-lookup"><span data-stu-id="95cef-151">To find the owner of a process, use the `Get-CimInstance` cmdlet to get a **Win32_Process** object that represents the process, and then use the **GetOwner** method of the object.</span></span>

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

### <span data-ttu-id="95cef-152">-ID</span><span class="sxs-lookup"><span data-stu-id="95cef-152">-Id</span></span>

<span data-ttu-id="95cef-153">Anger process-ID: n för de processer som ska stoppas.</span><span class="sxs-lookup"><span data-stu-id="95cef-153">Specifies the process IDs of the processes to stop.</span></span>
<span data-ttu-id="95cef-154">Använd kommatecken för att avgränsa ID: n för att ange flera ID: n.</span><span class="sxs-lookup"><span data-stu-id="95cef-154">To specify multiple IDs, use commas to separate the IDs.</span></span>
<span data-ttu-id="95cef-155">Om du vill hitta ett process-ID skriver du `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="95cef-155">To find the PID of a process, type `Get-Process`.</span></span>

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

### <span data-ttu-id="95cef-156">– InputObject</span><span class="sxs-lookup"><span data-stu-id="95cef-156">-InputObject</span></span>

<span data-ttu-id="95cef-157">Anger de process objekt som ska stoppas.</span><span class="sxs-lookup"><span data-stu-id="95cef-157">Specifies the process objects to stop.</span></span>
<span data-ttu-id="95cef-158">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="95cef-158">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="95cef-159">-Name</span><span class="sxs-lookup"><span data-stu-id="95cef-159">-Name</span></span>

<span data-ttu-id="95cef-160">Anger process namnen för de processer som ska stoppas.</span><span class="sxs-lookup"><span data-stu-id="95cef-160">Specifies the process names of the processes to stop.</span></span>
<span data-ttu-id="95cef-161">Du kan skriva flera process namn, avgränsade med kommatecken eller använda jokertecken.</span><span class="sxs-lookup"><span data-stu-id="95cef-161">You can type multiple process names, separated by commas, or use wildcard characters.</span></span>

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

### <span data-ttu-id="95cef-162">– PassThru</span><span class="sxs-lookup"><span data-stu-id="95cef-162">-PassThru</span></span>

<span data-ttu-id="95cef-163">Returnerar ett objekt som representerar processen.</span><span class="sxs-lookup"><span data-stu-id="95cef-163">Returns an object that represents the process.</span></span>
<span data-ttu-id="95cef-164">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="95cef-164">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="95cef-165">-Confirm</span><span class="sxs-lookup"><span data-stu-id="95cef-165">-Confirm</span></span>

<span data-ttu-id="95cef-166">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="95cef-166">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="95cef-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="95cef-167">-WhatIf</span></span>

<span data-ttu-id="95cef-168">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="95cef-168">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="95cef-169">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="95cef-169">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="95cef-170">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="95cef-170">CommonParameters</span></span>
<span data-ttu-id="95cef-171">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="95cef-171">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="95cef-172">Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="95cef-172">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="95cef-173">INDATA</span><span class="sxs-lookup"><span data-stu-id="95cef-173">INPUTS</span></span>

### <span data-ttu-id="95cef-174">System. Diagnostics. process</span><span class="sxs-lookup"><span data-stu-id="95cef-174">System.Diagnostics.Process</span></span>

<span data-ttu-id="95cef-175">Du kan skicka vidare ett process objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="95cef-175">You can pipe a process object to this cmdlet.</span></span>

## <span data-ttu-id="95cef-176">UTDATA</span><span class="sxs-lookup"><span data-stu-id="95cef-176">OUTPUTS</span></span>

### <span data-ttu-id="95cef-177">Ingen, system. Diagnostics. process</span><span class="sxs-lookup"><span data-stu-id="95cef-177">None, System.Diagnostics.Process</span></span>

<span data-ttu-id="95cef-178">Denna cmdlet returnerar ett **system. Diagnostics. process** -objekt som representerar den stoppade processen, om du anger parametern *Passthru* .</span><span class="sxs-lookup"><span data-stu-id="95cef-178">This cmdlet returns a **System.Diagnostics.Process** object that represents the stopped process, if you specify the *PassThru* parameter.</span></span>
<span data-ttu-id="95cef-179">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="95cef-179">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="95cef-180">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="95cef-180">NOTES</span></span>

* <span data-ttu-id="95cef-181">Du kan också referera till **stopp processen** med hjälp av inbyggda alias, **Kill** och **SPPs**.</span><span class="sxs-lookup"><span data-stu-id="95cef-181">You can also refer to **Stop-Process** by its built-in aliases, **kill** and **spps**.</span></span> <span data-ttu-id="95cef-182">Mer information finns i about_Aliases.</span><span class="sxs-lookup"><span data-stu-id="95cef-182">For more information, see about_Aliases.</span></span>

  <span data-ttu-id="95cef-183">Du kan också använda egenskaperna och metoderna för **Win32_Process** -objektet Windows Management Instrumentation (WMI) i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="95cef-183">You can also use the properties and methods of the Windows Management Instrumentation (WMI) **Win32_Process** object in Windows PowerShell.</span></span>
<span data-ttu-id="95cef-184">Mer information finns i `Get-CimInstance` och WMI SDK.</span><span class="sxs-lookup"><span data-stu-id="95cef-184">For more information, see `Get-CimInstance` and the WMI SDK.</span></span>

* <span data-ttu-id="95cef-185">När du stoppar processer kan du tänka på att processen som stoppar processen kan stoppa processer och tjänster som är beroende av processen.</span><span class="sxs-lookup"><span data-stu-id="95cef-185">When stopping processes, realize that stopping a process can stop process and services that depend on the process.</span></span>
<span data-ttu-id="95cef-186">I ett extrema fall kan en process stoppa Windows.</span><span class="sxs-lookup"><span data-stu-id="95cef-186">In an extreme case, stopping a process can stop Windows.</span></span>

## <span data-ttu-id="95cef-187">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="95cef-187">RELATED LINKS</span></span>

[<span data-ttu-id="95cef-188">Fel sökning – process</span><span class="sxs-lookup"><span data-stu-id="95cef-188">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="95cef-189">Hämta process</span><span class="sxs-lookup"><span data-stu-id="95cef-189">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="95cef-190">Start process</span><span class="sxs-lookup"><span data-stu-id="95cef-190">Start-Process</span></span>](Start-Process.md)

[<span data-ttu-id="95cef-191">Stoppa – process</span><span class="sxs-lookup"><span data-stu-id="95cef-191">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="95cef-192">Vänta-process</span><span class="sxs-lookup"><span data-stu-id="95cef-192">Wait-Process</span></span>](Wait-Process.md)
