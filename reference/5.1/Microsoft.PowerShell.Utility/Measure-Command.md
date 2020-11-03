---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/24/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/measure-command?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Measure-Command
ms.openlocfilehash: f0a45a4b7360c0870cbcd0702066380df4c21b80
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264951"
---
# <span data-ttu-id="1b711-103">Measure-Command</span><span class="sxs-lookup"><span data-stu-id="1b711-103">Measure-Command</span></span>

## <span data-ttu-id="1b711-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="1b711-104">SYNOPSIS</span></span>
<span data-ttu-id="1b711-105">Mäter den tid det tar att köra skript block och cmdlets.</span><span class="sxs-lookup"><span data-stu-id="1b711-105">Measures the time it takes to run script blocks and cmdlets.</span></span>

## <span data-ttu-id="1b711-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1b711-106">SYNTAX</span></span>

```
Measure-Command [-InputObject <PSObject>] [-Expression] <ScriptBlock> [<CommonParameters>]
```

## <span data-ttu-id="1b711-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="1b711-107">DESCRIPTION</span></span>

<span data-ttu-id="1b711-108">`Measure-Command`Cmdlet: en kör ett skript block eller en cmdlet internt, gånger körningen av åtgärden och returnerar körnings tiden.</span><span class="sxs-lookup"><span data-stu-id="1b711-108">The `Measure-Command` cmdlet runs a script block or cmdlet internally, times the execution of the operation, and returns the execution time.</span></span>

> [!NOTE]
> <span data-ttu-id="1b711-109">Skript block körs genom `Measure-Command` körning i det aktuella omfånget, inte en underordnad omfattning.</span><span class="sxs-lookup"><span data-stu-id="1b711-109">Script blocks run by `Measure-Command` run in the current scope, not a child scope.</span></span>

## <span data-ttu-id="1b711-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="1b711-110">EXAMPLES</span></span>

### <span data-ttu-id="1b711-111">Exempel 1: mäta ett kommando</span><span class="sxs-lookup"><span data-stu-id="1b711-111">Example 1: Measure a command</span></span>

<span data-ttu-id="1b711-112">Det här exemplet mäter hur lång tid det tar att köra ett `Get-EventLog` kommando som hämtar händelser i händelse loggen i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1b711-112">This example measures the time it takes to run a `Get-EventLog` command that gets the events in the Windows PowerShell event log.</span></span>

```powershell
Measure-Command { Get-EventLog "windows powershell" }
```

### <span data-ttu-id="1b711-113">Exempel 2: Jämför två utdata från Measure-Command</span><span class="sxs-lookup"><span data-stu-id="1b711-113">Example 2: Compare two outputs from Measure-Command</span></span>

<span data-ttu-id="1b711-114">Det första kommandot mäter den tid det tar att bearbeta ett rekursivt `Get-ChildItem` kommando som använder parametern **Path** för att bara hämta `.txt` filer i `C:\Windows` katalogen och dess under kataloger.</span><span class="sxs-lookup"><span data-stu-id="1b711-114">The first command measures the time it takes to process a recursive `Get-ChildItem` command that uses the **Path** parameter to get only `.txt` files in the `C:\Windows` directory and its subdirectories.</span></span>

<span data-ttu-id="1b711-115">Det andra kommandot mäter den tid det tar att bearbeta ett rekursivt `Get-ChildItem` kommando som använder den providerspecifika parametern.</span><span class="sxs-lookup"><span data-stu-id="1b711-115">The second command measures the time it takes to process a recursive `Get-ChildItem` command that uses the provider-specific \` parameter.</span></span>

<span data-ttu-id="1b711-116">Dessa kommandon visar värdet för att använda ett providerspecifik filter i PowerShell-kommandon.</span><span class="sxs-lookup"><span data-stu-id="1b711-116">These commands show the value of using a provider-specific filter in PowerShell commands.</span></span>

```powershell
Measure-Command { Get-ChildItem -Path C:\Windows\*.txt -Recurse }
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 8
Milliseconds      : 618
Ticks             : 86182763
TotalDays         : 9.9748568287037E-05
TotalHours        : 0.00239396563888889
TotalMinutes      : 0.143637938333333
TotalSeconds      : 8.6182763
TotalMilliseconds : 8618.2763
```

```powershell
Measure-Command {Get-ChildItem C:\Windows -Filter "*.txt" -Recurse}
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 1
Milliseconds      : 140
Ticks             : 11409189
TotalDays         : 1.32050798611111E-05
TotalHours        : 0.000316921916666667
TotalMinutes      : 0.019015315
TotalSeconds      : 1.1409189
TotalMilliseconds : 1140.9189
```

### <span data-ttu-id="1b711-117">Exempel 3: rör inström till Measure-Command</span><span class="sxs-lookup"><span data-stu-id="1b711-117">Example 3: Piping input to Measure-Command</span></span>

<span data-ttu-id="1b711-118">Objekt som skickas till `Measure-Command` är tillgängliga för det skript block som skickas till **uttrycks** parametern.</span><span class="sxs-lookup"><span data-stu-id="1b711-118">Objects that are piped to `Measure-Command` are available to the script block that is passed to the **Expression** parameter.</span></span> <span data-ttu-id="1b711-119">Skript blocket körs en gång för varje objekt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="1b711-119">The script block is executed once for each object on the pipeline.</span></span>

```powershell
# Perform a simple operation to demonstrate the InputObject parameter
# Note that no output is displayed.
10, 20, 50 | Measure-Command -Expression { for ($i=0; $i -lt $_ i++) {$i} }
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 0
Milliseconds      : 12
Ticks             : 122672
TotalDays         : 1.41981481481481E-07
TotalHours        : 3.40755555555556E-06
TotalMinutes      : 0.000204453333333333
TotalSeconds      : 0.0122672
TotalMilliseconds : 12.2672
```

### <span data-ttu-id="1b711-120">Exempel 4: Visa utdata från kommandot mätt</span><span class="sxs-lookup"><span data-stu-id="1b711-120">Example 4: Displaying output of measured command</span></span>

<span data-ttu-id="1b711-121">Om du vill visa utmatningar av uttryck i `Measure-Command` kan du använda en pipe till `Out-Default` .</span><span class="sxs-lookup"><span data-stu-id="1b711-121">To display output of expression in `Measure-Command` you can use a pipe to `Out-Default`.</span></span>

```powershell
# Perform the same operation as above adding Out-Default to every execution.
# This will show that the ScriptBlock is in fact executing for every item.
10, 20, 50 | Measure-Command -Expression {for ($i=0; $i -lt $_; $i++) {$i}; "$($_)" | Out-Default }
```

```Output
10
20
50


Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 0
Milliseconds      : 11
Ticks             : 113745
TotalDays         : 1.31649305555556E-07
TotalHours        : 3.15958333333333E-06
TotalMinutes      : 0.000189575
TotalSeconds      : 0.0113745
TotalMilliseconds : 11.3745
```

### <span data-ttu-id="1b711-122">Exempel 5: mäta körning i ett underordnat omfång</span><span class="sxs-lookup"><span data-stu-id="1b711-122">Example 5: Measuring execution in a child scope</span></span>

<span data-ttu-id="1b711-123">`Measure-Command` Kör skript blocket i det aktuella omfånget, så att skript blocket kan ändra värden i det aktuella omfånget.</span><span class="sxs-lookup"><span data-stu-id="1b711-123">`Measure-Command` runs the script block in the current scope, so the script block can modify values in the current scope.</span></span> <span data-ttu-id="1b711-124">För att undvika ändringar i det aktuella omfånget måste du omsluta skript blocket inom klammerparenteser ( `{}` ) och använda anrops operatorn ( `&` ) för att köra blocket i en underordnad omfattning.</span><span class="sxs-lookup"><span data-stu-id="1b711-124">To avoid changes to the current scope, you must wrap the script block in braces (`{}`) and use the invocation operator (`&`) to execute the block in a child scope.</span></span>

```powershell
$foo = 'Value 1'
$null = Measure-Command { $foo = 'Value 2' }
$foo
$null = Measure-Command { & { $foo = 'Value 3' } }
$foo
```

```Output
Value 2
Value 2
```

<span data-ttu-id="1b711-125">Mer information om anrops operatorn finns [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md#call-operator-).</span><span class="sxs-lookup"><span data-stu-id="1b711-125">For more information about the invocation operator, see [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md#call-operator-).</span></span>

## <span data-ttu-id="1b711-126">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="1b711-126">PARAMETERS</span></span>

### <span data-ttu-id="1b711-127">– Uttryck</span><span class="sxs-lookup"><span data-stu-id="1b711-127">-Expression</span></span>

<span data-ttu-id="1b711-128">Anger det uttryck som är tids gräns.</span><span class="sxs-lookup"><span data-stu-id="1b711-128">Specifies the expression that is being timed.</span></span> <span data-ttu-id="1b711-129">Omge uttrycket med klammerparenteser ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="1b711-129">Enclose the expression in braces (`{}`).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1b711-130">– InputObject</span><span class="sxs-lookup"><span data-stu-id="1b711-130">-InputObject</span></span>

<span data-ttu-id="1b711-131">Objekt som är kopplade till **InputObject** -parametern är valfria indatatyper för det skript block som skickas till **uttrycks** parametern.</span><span class="sxs-lookup"><span data-stu-id="1b711-131">Objects bound to the **InputObject** parameter are optional input for the script block passed to the **Expression** parameter.</span></span> <span data-ttu-id="1b711-132">Inuti-skript blocket `$_` kan användas för att referera till det aktuella objektet i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="1b711-132">Inside the script block, `$_` can be used to reference the current object in the pipeline.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="1b711-133">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1b711-133">CommonParameters</span></span>

<span data-ttu-id="1b711-134">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1b711-134">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1b711-135">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1b711-135">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1b711-136">INDATA</span><span class="sxs-lookup"><span data-stu-id="1b711-136">INPUTS</span></span>

### <span data-ttu-id="1b711-137">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="1b711-137">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="1b711-138">Du kan skicka vidare ett objekt till `Measure-Command` .</span><span class="sxs-lookup"><span data-stu-id="1b711-138">You can pipe an object to `Measure-Command`.</span></span>

## <span data-ttu-id="1b711-139">UTDATA</span><span class="sxs-lookup"><span data-stu-id="1b711-139">OUTPUTS</span></span>

### <span data-ttu-id="1b711-140">System. TimeSpan</span><span class="sxs-lookup"><span data-stu-id="1b711-140">System.TimeSpan</span></span>

<span data-ttu-id="1b711-141">`Measure-Command` Returnerar ett tidsintervall objekt som representerar resultatet.</span><span class="sxs-lookup"><span data-stu-id="1b711-141">`Measure-Command` returns a time span object that represents the result.</span></span>

## <span data-ttu-id="1b711-142">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="1b711-142">NOTES</span></span>

## <span data-ttu-id="1b711-143">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="1b711-143">RELATED LINKS</span></span>

[<span data-ttu-id="1b711-144">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="1b711-144">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="1b711-145">Spåra-kommando</span><span class="sxs-lookup"><span data-stu-id="1b711-145">Trace-Command</span></span>](Trace-Command.md)