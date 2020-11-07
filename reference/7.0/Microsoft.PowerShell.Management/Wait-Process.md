---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/wait-process?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Process
ms.openlocfilehash: 1325b1e604bc450f0aaec3ec4e99afa281aa1d91
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94346198"
---
# <span data-ttu-id="ab5c8-103">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="ab5c8-103">Wait-Process</span></span>

## <span data-ttu-id="ab5c8-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="ab5c8-104">SYNOPSIS</span></span>
<span data-ttu-id="ab5c8-105">Väntar på att processerna ska stoppas innan du accepterar mer information.</span><span class="sxs-lookup"><span data-stu-id="ab5c8-105">Waits for the processes to be stopped before accepting more input.</span></span>

## <span data-ttu-id="ab5c8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ab5c8-106">SYNTAX</span></span>

### <span data-ttu-id="ab5c8-107">Namn (standard)</span><span class="sxs-lookup"><span data-stu-id="ab5c8-107">Name (Default)</span></span>

```
Wait-Process [-Name] <String[]> [[-Timeout] <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="ab5c8-108">Id</span><span class="sxs-lookup"><span data-stu-id="ab5c8-108">Id</span></span>

```
Wait-Process [-Id] <Int32[]> [[-Timeout] <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="ab5c8-109">InputObject</span><span class="sxs-lookup"><span data-stu-id="ab5c8-109">InputObject</span></span>

```
Wait-Process [[-Timeout] <Int32>] -InputObject <Process[]> [<CommonParameters>]
```

## <span data-ttu-id="ab5c8-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ab5c8-110">DESCRIPTION</span></span>

<span data-ttu-id="ab5c8-111">Cmdleten **wait process** väntar på att en eller flera processer som körs ska stoppas innan indatamängden accepteras.</span><span class="sxs-lookup"><span data-stu-id="ab5c8-111">The **Wait-Process** cmdlet waits for one or more running processes to be stopped before accepting input.</span></span>
<span data-ttu-id="ab5c8-112">I PowerShell-konsolen ignorerar denna cmdlet kommando tolken tills processerna har stoppats.</span><span class="sxs-lookup"><span data-stu-id="ab5c8-112">In the PowerShell console, this cmdlet suppresses the command prompt until the processes are stopped.</span></span>
<span data-ttu-id="ab5c8-113">Du kan ange en process efter process namn eller process-ID (PID) eller skicka ett process objekt till **wait-process**.</span><span class="sxs-lookup"><span data-stu-id="ab5c8-113">You can specify a process by process name or process ID (PID), or pipe a process object to **Wait-Process**.</span></span>

<span data-ttu-id="ab5c8-114">**Wait-process** fungerar bara på processer som körs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="ab5c8-114">**Wait-Process** works only on processes running on the local computer.</span></span>

## <span data-ttu-id="ab5c8-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="ab5c8-115">EXAMPLES</span></span>

### <span data-ttu-id="ab5c8-116">Exempel 1: stoppa en process och vänta</span><span class="sxs-lookup"><span data-stu-id="ab5c8-116">Example 1: Stop a process and wait</span></span>

```
PS C:\> $nid = (Get-Process notepad).id
PS C:\> Stop-Process -Id $nid
PS C:\> Wait-Process -Id $nid
```

<span data-ttu-id="ab5c8-117">Det här exemplet stoppar anteckningar-processen och väntar sedan på att processen ska stoppas innan nästa kommando fortsätter.</span><span class="sxs-lookup"><span data-stu-id="ab5c8-117">This example stops the Notepad process and then waits for the process to be stopped before it continues with the next command.</span></span>

<span data-ttu-id="ab5c8-118">Det första kommandot använder cmdleten **Get-process** för att hämta ID: t för anteckningar-processen.</span><span class="sxs-lookup"><span data-stu-id="ab5c8-118">The first command uses the **Get-Process** cmdlet to get the ID of the Notepad process.</span></span>
<span data-ttu-id="ab5c8-119">Den lagrar ID: t i variabeln $nid.</span><span class="sxs-lookup"><span data-stu-id="ab5c8-119">It stores the ID in the $nid variable.</span></span>

<span data-ttu-id="ab5c8-120">Det andra kommandot använder cmdleten Stop-Process för att stoppa processen med det ID som lagras i $nid.</span><span class="sxs-lookup"><span data-stu-id="ab5c8-120">The second command uses the Stop-Process cmdlet to stop the process with the ID stored in $nid.</span></span>

<span data-ttu-id="ab5c8-121">Det tredje kommandot använder **wait-process** för att vänta tills anteckningar-processen har stoppats.</span><span class="sxs-lookup"><span data-stu-id="ab5c8-121">The third command uses **Wait-Process** to wait until the Notepad process is stopped.</span></span>
<span data-ttu-id="ab5c8-122">Den använder *ID* -parametern för **wait process** för att identifiera processen.</span><span class="sxs-lookup"><span data-stu-id="ab5c8-122">It uses the *Id* parameter of **Wait-Process** to identify the process.</span></span>

### <span data-ttu-id="ab5c8-123">Exempel 2: Ange en process</span><span class="sxs-lookup"><span data-stu-id="ab5c8-123">Example 2: Specifying a process</span></span>

```
PS C:\> $p = Get-Process notepad
PS C:\> Wait-Process -Id $p.id
PS C:\> Wait-Process -Name "notepad"
PS C:\> Wait-Process -InputObject $p
```

<span data-ttu-id="ab5c8-124">De här kommandona visar tre olika metoder för att ange en process till **wait-process**.</span><span class="sxs-lookup"><span data-stu-id="ab5c8-124">These commands show three different methods of specifying a process to **Wait-Process**.</span></span>
<span data-ttu-id="ab5c8-125">Det första kommandot hämtar anteckningar-processen och lagrar det i $p variabeln.</span><span class="sxs-lookup"><span data-stu-id="ab5c8-125">The first command gets the Notepad process and stores it in the $p variable.</span></span>

<span data-ttu-id="ab5c8-126">Det andra kommandot använder *ID-* parametern, det tredje kommandot använder parametern *Name* och det fjärde kommandot använder parametern *InputObject* .</span><span class="sxs-lookup"><span data-stu-id="ab5c8-126">The second command uses the *Id* parameter, the third command uses the *Name* parameter, and the fourth command uses the *InputObject* parameter.</span></span>

<span data-ttu-id="ab5c8-127">Dessa kommandon har samma resultat och kan användas utbytbart.</span><span class="sxs-lookup"><span data-stu-id="ab5c8-127">These commands have the same results and can be used interchangeably.</span></span>

### <span data-ttu-id="ab5c8-128">Exempel 3: vänta på processer under en angiven tid</span><span class="sxs-lookup"><span data-stu-id="ab5c8-128">Example 3: Wait for processes for a specified time</span></span>

```
PS C:\> Wait-Process -Name outlook, winword -Timeout 30
```

<span data-ttu-id="ab5c8-129">Det här kommandot väntar 30 sekunder på att Outlook-och Winword-processerna ska stoppas.</span><span class="sxs-lookup"><span data-stu-id="ab5c8-129">This command waits 30 seconds for the Outlook and Winword processes to stop.</span></span>
<span data-ttu-id="ab5c8-130">Om båda processerna inte har stoppats visar cmdleten ett icke-avslutande fel och kommando tolken.</span><span class="sxs-lookup"><span data-stu-id="ab5c8-130">If both processes are not stopped, the cmdlet displays a non-terminating error and the command prompt.</span></span>

## <span data-ttu-id="ab5c8-131">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="ab5c8-131">PARAMETERS</span></span>

### <span data-ttu-id="ab5c8-132">-ID</span><span class="sxs-lookup"><span data-stu-id="ab5c8-132">-Id</span></span>

<span data-ttu-id="ab5c8-133">Anger process-ID: n för processerna.</span><span class="sxs-lookup"><span data-stu-id="ab5c8-133">Specifies the process IDs of the processes.</span></span>
<span data-ttu-id="ab5c8-134">Använd kommatecken för att avgränsa ID: n för att ange flera ID: n.</span><span class="sxs-lookup"><span data-stu-id="ab5c8-134">To specify multiple IDs, use commas to separate the IDs.</span></span>
<span data-ttu-id="ab5c8-135">Om du vill hitta ett process-ID skriver du `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="ab5c8-135">To find the PID of a process, type `Get-Process`.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases: PID, ProcessId

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ab5c8-136">– InputObject</span><span class="sxs-lookup"><span data-stu-id="ab5c8-136">-InputObject</span></span>

<span data-ttu-id="ab5c8-137">Anger processerna genom att skicka process objekt.</span><span class="sxs-lookup"><span data-stu-id="ab5c8-137">Specifies the processes by submitting process objects.</span></span>
<span data-ttu-id="ab5c8-138">Ange en variabel som innehåller process objekt, eller Skriv ett kommando eller uttryck som hämtar process objekt, t. ex. Get-Process-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ab5c8-138">Enter a variable that contains the process objects, or type a command or expression that gets the process objects, such as the Get-Process cmdlet.</span></span>

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ab5c8-139">-Name</span><span class="sxs-lookup"><span data-stu-id="ab5c8-139">-Name</span></span>

<span data-ttu-id="ab5c8-140">Anger processernas process namn.</span><span class="sxs-lookup"><span data-stu-id="ab5c8-140">Specifies the process names of the processes.</span></span>
<span data-ttu-id="ab5c8-141">Om du vill ange flera namn använder du kommatecken för att avgränsa namnen.</span><span class="sxs-lookup"><span data-stu-id="ab5c8-141">To specify multiple names, use commas to separate the names.</span></span>
<span data-ttu-id="ab5c8-142">Jokertecken stöds inte.</span><span class="sxs-lookup"><span data-stu-id="ab5c8-142">Wildcard characters are not supported.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases: ProcessName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ab5c8-143">-Timeout</span><span class="sxs-lookup"><span data-stu-id="ab5c8-143">-Timeout</span></span>

<span data-ttu-id="ab5c8-144">Anger den maximala tiden, i sekunder, som denna cmdlet väntar på att de angivna processerna ska stoppas.</span><span class="sxs-lookup"><span data-stu-id="ab5c8-144">Specifies the maximum time, in seconds, that this cmdlet waits for the specified processes to stop.</span></span>
<span data-ttu-id="ab5c8-145">När det här intervallet går ut visar kommandot ett icke-avslutande fel som visar de processer som fortfarande körs och slutar vänta.</span><span class="sxs-lookup"><span data-stu-id="ab5c8-145">When this interval expires, the command displays a non-terminating error that lists the processes that are still running, and ends the wait.</span></span>
<span data-ttu-id="ab5c8-146">Som standard finns det ingen tids gräns.</span><span class="sxs-lookup"><span data-stu-id="ab5c8-146">By default, there is no time-out.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ab5c8-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ab5c8-147">CommonParameters</span></span>

<span data-ttu-id="ab5c8-148">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ab5c8-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ab5c8-149">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ab5c8-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ab5c8-150">INDATA</span><span class="sxs-lookup"><span data-stu-id="ab5c8-150">INPUTS</span></span>

### <span data-ttu-id="ab5c8-151">System. Diagnostics. process</span><span class="sxs-lookup"><span data-stu-id="ab5c8-151">System.Diagnostics.Process</span></span>

<span data-ttu-id="ab5c8-152">Du kan skicka vidare ett process objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ab5c8-152">You can pipe a process object to this cmdlet.</span></span>

## <span data-ttu-id="ab5c8-153">UTDATA</span><span class="sxs-lookup"><span data-stu-id="ab5c8-153">OUTPUTS</span></span>

### <span data-ttu-id="ab5c8-154">Inget</span><span class="sxs-lookup"><span data-stu-id="ab5c8-154">None</span></span>

<span data-ttu-id="ab5c8-155">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="ab5c8-155">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="ab5c8-156">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="ab5c8-156">NOTES</span></span>

<span data-ttu-id="ab5c8-157">Cmdleten stöds endast på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="ab5c8-157">The cmdlet is only supported on Windows platforms.</span></span>

<span data-ttu-id="ab5c8-158">Denna cmdlet använder metoden **WaitForExit** i klassen **system. Diagnostics. process** .</span><span class="sxs-lookup"><span data-stu-id="ab5c8-158">This cmdlet uses the **WaitForExit** method of the **System.Diagnostics.Process** class.</span></span>

## <span data-ttu-id="ab5c8-159">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="ab5c8-159">RELATED LINKS</span></span>

[<span data-ttu-id="ab5c8-160">Fel sökning – process</span><span class="sxs-lookup"><span data-stu-id="ab5c8-160">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="ab5c8-161">Hämta process</span><span class="sxs-lookup"><span data-stu-id="ab5c8-161">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="ab5c8-162">Start process</span><span class="sxs-lookup"><span data-stu-id="ab5c8-162">Start-Process</span></span>](Start-Process.md)

[<span data-ttu-id="ab5c8-163">Stoppa – process</span><span class="sxs-lookup"><span data-stu-id="ab5c8-163">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="ab5c8-164">Vänta-process</span><span class="sxs-lookup"><span data-stu-id="ab5c8-164">Wait-Process</span></span>](Wait-Process.md)
