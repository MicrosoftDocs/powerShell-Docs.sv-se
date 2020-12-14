---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/24/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/measure-command?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Measure-Command
ms.openlocfilehash: 0c2346dc7177e091c0921cd4775422938305e2be
ms.sourcegitcommit: 165d10405d9db3a68c417a239d3181378fd02b9b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96935950"
---
# <span data-ttu-id="76bb3-102">Measure-Command</span><span class="sxs-lookup"><span data-stu-id="76bb3-102">Measure-Command</span></span>

## <span data-ttu-id="76bb3-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="76bb3-103">SYNOPSIS</span></span>
<span data-ttu-id="76bb3-104">Mäter den tid det tar att köra skript block och cmdlets.</span><span class="sxs-lookup"><span data-stu-id="76bb3-104">Measures the time it takes to run script blocks and cmdlets.</span></span>

## <span data-ttu-id="76bb3-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="76bb3-105">SYNTAX</span></span>

```
Measure-Command [-InputObject <PSObject>] [-Expression] <ScriptBlock> [<CommonParameters>]
```

## <span data-ttu-id="76bb3-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="76bb3-106">DESCRIPTION</span></span>

<span data-ttu-id="76bb3-107">`Measure-Command`Cmdlet: en kör ett skript block eller en cmdlet internt, gånger körningen av åtgärden och returnerar körnings tiden.</span><span class="sxs-lookup"><span data-stu-id="76bb3-107">The `Measure-Command` cmdlet runs a script block or cmdlet internally, times the execution of the operation, and returns the execution time.</span></span>

> [!NOTE]
> <span data-ttu-id="76bb3-108">Skript block körs genom `Measure-Command` körning i det aktuella omfånget, inte en underordnad omfattning.</span><span class="sxs-lookup"><span data-stu-id="76bb3-108">Script blocks run by `Measure-Command` run in the current scope, not a child scope.</span></span>

## <span data-ttu-id="76bb3-109">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="76bb3-109">EXAMPLES</span></span>

### <span data-ttu-id="76bb3-110">Exempel 1: mäta ett kommando</span><span class="sxs-lookup"><span data-stu-id="76bb3-110">Example 1: Measure a command</span></span>

<span data-ttu-id="76bb3-111">Det här exemplet mäter hur lång tid det tar att köra ett `Get-EventLog` kommando som hämtar händelser i händelse loggen i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="76bb3-111">This example measures the time it takes to run a `Get-EventLog` command that gets the events in the Windows PowerShell event log.</span></span>

```powershell
Measure-Command { Get-EventLog "windows powershell" }
```

### <span data-ttu-id="76bb3-112">Exempel 2: Jämför två utdata från Measure-Command</span><span class="sxs-lookup"><span data-stu-id="76bb3-112">Example 2: Compare two outputs from Measure-Command</span></span>

<span data-ttu-id="76bb3-113">Det första kommandot mäter den tid det tar att bearbeta ett rekursivt `Get-ChildItem` kommando som använder parametern **Path** för att bara hämta `.txt` filer i `C:\Windows` katalogen och dess under kataloger.</span><span class="sxs-lookup"><span data-stu-id="76bb3-113">The first command measures the time it takes to process a recursive `Get-ChildItem` command that uses the **Path** parameter to get only `.txt` files in the `C:\Windows` directory and its subdirectories.</span></span>

<span data-ttu-id="76bb3-114">Det andra kommandot mäter den tid det tar att bearbeta ett rekursivt `Get-ChildItem` kommando som använder den providerspecifika parametern.</span><span class="sxs-lookup"><span data-stu-id="76bb3-114">The second command measures the time it takes to process a recursive `Get-ChildItem` command that uses the provider-specific \` parameter.</span></span>

<span data-ttu-id="76bb3-115">Dessa kommandon visar värdet för att använda ett providerspecifik filter i PowerShell-kommandon.</span><span class="sxs-lookup"><span data-stu-id="76bb3-115">These commands show the value of using a provider-specific filter in PowerShell commands.</span></span>

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

### <span data-ttu-id="76bb3-116">Exempel 3: rör inström till Measure-Command</span><span class="sxs-lookup"><span data-stu-id="76bb3-116">Example 3: Piping input to Measure-Command</span></span>

<span data-ttu-id="76bb3-117">Objekt som skickas till `Measure-Command` är tillgängliga för det skript block som skickas till **uttrycks** parametern.</span><span class="sxs-lookup"><span data-stu-id="76bb3-117">Objects that are piped to `Measure-Command` are available to the script block that is passed to the **Expression** parameter.</span></span> <span data-ttu-id="76bb3-118">Skript blocket körs en gång för varje objekt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="76bb3-118">The script block is executed once for each object on the pipeline.</span></span>

```powershell
# Perform a simple operation to demonstrate the InputObject parameter
# Note that no output is displayed.
10, 20, 50 | Measure-Command -Expression { for ($i=0; $i -lt $_; $i++) {$i} }
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

### <span data-ttu-id="76bb3-119">Exempel 4: Visa utdata från kommandot mätt</span><span class="sxs-lookup"><span data-stu-id="76bb3-119">Example 4: Displaying output of measured command</span></span>

<span data-ttu-id="76bb3-120">Om du vill visa utmatningar av uttryck i `Measure-Command` kan du använda en pipe till `Out-Default` .</span><span class="sxs-lookup"><span data-stu-id="76bb3-120">To display output of expression in `Measure-Command` you can use a pipe to `Out-Default`.</span></span>

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

### <span data-ttu-id="76bb3-121">Exempel 5: mäta körning i ett underordnat omfång</span><span class="sxs-lookup"><span data-stu-id="76bb3-121">Example 5: Measuring execution in a child scope</span></span>

<span data-ttu-id="76bb3-122">`Measure-Command` Kör skript blocket i det aktuella omfånget, så att skript blocket kan ändra värden i det aktuella omfånget.</span><span class="sxs-lookup"><span data-stu-id="76bb3-122">`Measure-Command` runs the script block in the current scope, so the script block can modify values in the current scope.</span></span> <span data-ttu-id="76bb3-123">För att undvika ändringar i det aktuella omfånget måste du omsluta skript blocket inom klammerparenteser ( `{}` ) och använda anrops operatorn ( `&` ) för att köra blocket i en underordnad omfattning.</span><span class="sxs-lookup"><span data-stu-id="76bb3-123">To avoid changes to the current scope, you must wrap the script block in braces (`{}`) and use the invocation operator (`&`) to execute the block in a child scope.</span></span>

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

<span data-ttu-id="76bb3-124">Mer information om anrops operatorn finns [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md#call-operator-).</span><span class="sxs-lookup"><span data-stu-id="76bb3-124">For more information about the invocation operator, see [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md#call-operator-).</span></span>

## <span data-ttu-id="76bb3-125">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="76bb3-125">PARAMETERS</span></span>

### <span data-ttu-id="76bb3-126">– Uttryck</span><span class="sxs-lookup"><span data-stu-id="76bb3-126">-Expression</span></span>

<span data-ttu-id="76bb3-127">Anger det uttryck som är tids gräns.</span><span class="sxs-lookup"><span data-stu-id="76bb3-127">Specifies the expression that is being timed.</span></span> <span data-ttu-id="76bb3-128">Omge uttrycket med klammerparenteser ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="76bb3-128">Enclose the expression in braces (`{}`).</span></span>

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

### <span data-ttu-id="76bb3-129">– InputObject</span><span class="sxs-lookup"><span data-stu-id="76bb3-129">-InputObject</span></span>

<span data-ttu-id="76bb3-130">Objekt som är kopplade till **InputObject** -parametern är valfria indatatyper för det skript block som skickas till **uttrycks** parametern.</span><span class="sxs-lookup"><span data-stu-id="76bb3-130">Objects bound to the **InputObject** parameter are optional input for the script block passed to the **Expression** parameter.</span></span> <span data-ttu-id="76bb3-131">Inuti-skript blocket `$_` kan användas för att referera till det aktuella objektet i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="76bb3-131">Inside the script block, `$_` can be used to reference the current object in the pipeline.</span></span>

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

### <span data-ttu-id="76bb3-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="76bb3-132">CommonParameters</span></span>

<span data-ttu-id="76bb3-133">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="76bb3-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="76bb3-134">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="76bb3-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="76bb3-135">INDATA</span><span class="sxs-lookup"><span data-stu-id="76bb3-135">INPUTS</span></span>

### <span data-ttu-id="76bb3-136">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="76bb3-136">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="76bb3-137">Du kan skicka vidare ett objekt till `Measure-Command` .</span><span class="sxs-lookup"><span data-stu-id="76bb3-137">You can pipe an object to `Measure-Command`.</span></span>

## <span data-ttu-id="76bb3-138">UTDATA</span><span class="sxs-lookup"><span data-stu-id="76bb3-138">OUTPUTS</span></span>

### <span data-ttu-id="76bb3-139">System. TimeSpan</span><span class="sxs-lookup"><span data-stu-id="76bb3-139">System.TimeSpan</span></span>

<span data-ttu-id="76bb3-140">`Measure-Command` Returnerar ett tidsintervall objekt som representerar resultatet.</span><span class="sxs-lookup"><span data-stu-id="76bb3-140">`Measure-Command` returns a time span object that represents the result.</span></span>

## <span data-ttu-id="76bb3-141">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="76bb3-141">NOTES</span></span>

## <span data-ttu-id="76bb3-142">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="76bb3-142">RELATED LINKS</span></span>

[<span data-ttu-id="76bb3-143">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="76bb3-143">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="76bb3-144">Spåra-kommando</span><span class="sxs-lookup"><span data-stu-id="76bb3-144">Trace-Command</span></span>](Trace-Command.md)

