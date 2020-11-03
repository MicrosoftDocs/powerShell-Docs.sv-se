---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 4/30/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-date?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Date
ms.openlocfilehash: 1c2a029a20b80826f74662a2b68d4a5f32276b00
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263462"
---
# <span data-ttu-id="1c1b9-103">Set-Date</span><span class="sxs-lookup"><span data-stu-id="1c1b9-103">Set-Date</span></span>

## <span data-ttu-id="1c1b9-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="1c1b9-104">SYNOPSIS</span></span>
<span data-ttu-id="1c1b9-105">Ändrar system klockan på datorn till en tidpunkt som du anger.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-105">Changes the system time on the computer to a time that you specify.</span></span>

## <span data-ttu-id="1c1b9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1c1b9-106">SYNTAX</span></span>

### <span data-ttu-id="1c1b9-107">Datum (standard)</span><span class="sxs-lookup"><span data-stu-id="1c1b9-107">Date (Default)</span></span>

```
Set-Date [-Date] <DateTime> [-DisplayHint <DisplayHintType>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="1c1b9-108">Automatiskt</span><span class="sxs-lookup"><span data-stu-id="1c1b9-108">Adjust</span></span>

```
Set-Date [-Adjust] <TimeSpan> [-DisplayHint <DisplayHintType>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="1c1b9-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="1c1b9-109">DESCRIPTION</span></span>

<span data-ttu-id="1c1b9-110">`Set-Date`Cmdleten ändrar system datum och-tid på datorn till ett datum och en tidpunkt som du anger.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-110">The `Set-Date` cmdlet changes the system date and time on the computer to a date and time that you specify.</span></span>
<span data-ttu-id="1c1b9-111">Du kan ange ett nytt datum och/eller tid genom att skriva en sträng eller genom att skicka ett **datetime** -eller **TimeSpan** -objekt till `Set-Date` .</span><span class="sxs-lookup"><span data-stu-id="1c1b9-111">You can specify a new date and/or time by typing a string or by passing a **DateTime** or **TimeSpan** object to `Set-Date`.</span></span> <span data-ttu-id="1c1b9-112">Om du vill ange ett nytt datum eller en ny tid använder du parametern **date** .</span><span class="sxs-lookup"><span data-stu-id="1c1b9-112">To specify a new date or time, use the **Date** parameter.</span></span>
<span data-ttu-id="1c1b9-113">Om du vill ange ett ändrings intervall använder du parametern **Justera** .</span><span class="sxs-lookup"><span data-stu-id="1c1b9-113">To specify a change interval, use the **Adjust** parameter.</span></span>

## <span data-ttu-id="1c1b9-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="1c1b9-114">EXAMPLES</span></span>

### <span data-ttu-id="1c1b9-115">Exempel 1: Lägg till tre dagar till system datumet</span><span class="sxs-lookup"><span data-stu-id="1c1b9-115">Example 1: Add three days to the system date</span></span>

<span data-ttu-id="1c1b9-116">Det här kommandot lägger till tre dagar till det aktuella system datumet.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-116">This command adds three days to the current system date.</span></span>
<span data-ttu-id="1c1b9-117">Den påverkar inte tiden.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-117">It does not affect the time.</span></span>
<span data-ttu-id="1c1b9-118">Kommandot använder **datum** parametern för att ange datumet.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-118">The command uses the **Date** parameter to specify the date.</span></span>

<span data-ttu-id="1c1b9-119">`Get-Date`Cmdleten returnerar det aktuella datumet som ett **datetime** -objekt.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-119">The `Get-Date` cmdlet returns the current date as a **DateTime** object.</span></span> <span data-ttu-id="1c1b9-120">**AddDays** -metoden för **datetime** -objektet lägger till ett angivet antal dagar (3) till det aktuella **datetime** -objektet.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-120">The **DateTime** object's **AddDays** method adds a specified number of days (3) to the current **DateTime** object.</span></span>

```powershell
Set-Date -Date (Get-Date).AddDays(3)
```

### <span data-ttu-id="1c1b9-121">Exempel 2: Ställ tillbaka system klockan 10 minuter</span><span class="sxs-lookup"><span data-stu-id="1c1b9-121">Example 2: Set the system clock back 10 minutes</span></span>

<span data-ttu-id="1c1b9-122">I det här exemplet anges den aktuella system tiden tillbaka med 10 minuter.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-122">This example sets the current system time back by 10 minutes.</span></span>

<span data-ttu-id="1c1b9-123">Med **justerings** parametern kan du ange ett ändrings intervall (minus tio minuter) i standard tids formatet för språkvarianten.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-123">The **Adjust** parameter allows you to specify an interval of change (minus ten minutes) in the standard time format for the locale.</span></span>

<span data-ttu-id="1c1b9-124">Parametern **DisplayHint** anger att PowerShell endast visar tiden, men det påverkar inte det **datetime** -objekt som `Set-Date` returneras.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-124">The **DisplayHint** parameter tells PowerShell to display only the time, but it does not affect the **DateTime** object that `Set-Date` returns.</span></span>

```powershell
Set-Date -Adjust -0:10:0 -DisplayHint Time
```

### <span data-ttu-id="1c1b9-125">Exempel 3: Ange datum och tid till ett variabel värde</span><span class="sxs-lookup"><span data-stu-id="1c1b9-125">Example 3: Set the date and time to a variable value</span></span>

<span data-ttu-id="1c1b9-126">De här kommandona ändrar system datum och-tid på den lokala datorn till datum och tid som sparats i variabeln `$T` .</span><span class="sxs-lookup"><span data-stu-id="1c1b9-126">These commands change the system date and time on local computer to the date and time saved in the variable `$T`.</span></span> <span data-ttu-id="1c1b9-127">Det första kommandot hämtar datumet och lagrar det i `$T` .</span><span class="sxs-lookup"><span data-stu-id="1c1b9-127">The first command gets the date and stores it in `$T`.</span></span>

<span data-ttu-id="1c1b9-128">Det andra kommandot använder **datum** parametern för att skicka **datetime** -objektet `$T` till- `Set-Date` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-128">The second command uses the **Date** parameter to pass the **DateTime** object in `$T` to the `Set-Date` cmdlet.</span></span>

```powershell
$T = Get-Date
Set-Date -Date $T
```

### <span data-ttu-id="1c1b9-129">Exempel 4: Lägg till 90 minuter på system klockan</span><span class="sxs-lookup"><span data-stu-id="1c1b9-129">Example 4: Add 90 minutes to the system clock</span></span>

<span data-ttu-id="1c1b9-130">Dessa kommandon förflyttar system klockan på den lokala datorn med 90 minuter.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-130">These commands advance the system time on the local computer by 90 minutes.</span></span>

<span data-ttu-id="1c1b9-131">Det första kommandot använder `New-TimeSpan` cmdleten för att skapa ett **TimeSpan** -objekt med ett intervall på 90 minuter och sparar det i `$90mins` variabeln.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-131">The first command uses the `New-TimeSpan` cmdlet to create a **TimeSpan** object with a 90-minute interval, and saves it in the `$90mins` variable.</span></span>

<span data-ttu-id="1c1b9-132">Det andra kommandot använder parametern **Justera** för `Set-Date` för att justera datumet med värdet för **TimeSpan** -objektet i `$90mins` variabeln.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-132">The second command uses the **Adjust** parameter of `Set-Date` to adjust the date by the value of the **TimeSpan** object in the `$90mins` variable.</span></span>

```powershell
$90mins = New-TimeSpan -Minutes 90
Set-Date -Adjust $90mins
```

## <span data-ttu-id="1c1b9-133">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="1c1b9-133">PARAMETERS</span></span>

### <span data-ttu-id="1c1b9-134">– Justera</span><span class="sxs-lookup"><span data-stu-id="1c1b9-134">-Adjust</span></span>

<span data-ttu-id="1c1b9-135">Anger värdet för vilket denna cmdlet lägger till eller undervärderar från aktuellt datum och aktuell tid.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-135">Specifies the value for which this cmdlet adds or subtracts from the current date and time.</span></span>
<span data-ttu-id="1c1b9-136">kan skriva en justering i standard datum-och tids format för dina nationella inställningar eller använda parametern **Justera** för att skicka ett **TimeSpan** -objekt från `New-TimeSpan` till `Set-Date` .</span><span class="sxs-lookup"><span data-stu-id="1c1b9-136">can type an adjustment in standard date and time format for your locale or use the **Adjust** parameter to pass a **TimeSpan** object from `New-TimeSpan` to `Set-Date`.</span></span>

```yaml
Type: System.TimeSpan
Parameter Sets: Adjust
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1c1b9-137">-Datum</span><span class="sxs-lookup"><span data-stu-id="1c1b9-137">-Date</span></span>

<span data-ttu-id="1c1b9-138">Ändrar datum och tid till de angivna värdena.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-138">Changes the date and time to the specified values.</span></span>
<span data-ttu-id="1c1b9-139">Du kan ange ett nytt datum i kort datum format och en tid i standardformatet för ditt språk.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-139">You can type a new date in the short date format and a time in the standard time format for your locale.</span></span> <span data-ttu-id="1c1b9-140">Du kan också skicka ett **datetime** -objekt från `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="1c1b9-140">Or, you can pass a **DateTime** object from `Get-Date`.</span></span>

<span data-ttu-id="1c1b9-141">Om du anger ett datum, men inte en tid, `Set-Date` ändras tiden till midnatt på det angivna datumet.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-141">If you specify a date, but not a time, `Set-Date` changes the time to midnight on the specified date.</span></span> <span data-ttu-id="1c1b9-142">Om du bara anger en tid ändras inte datumet.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-142">If you specify only a time, it does not change the date.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: Date
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="1c1b9-143">-DisplayHint</span><span class="sxs-lookup"><span data-stu-id="1c1b9-143">-DisplayHint</span></span>

<span data-ttu-id="1c1b9-144">Anger vilka element i datum och tid som visas. De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="1c1b9-144">Specifies which elements of the date and time are displayed.The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="1c1b9-145">Ikraftträdande.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-145">Date.</span></span>
  <span data-ttu-id="1c1b9-146">visar endast datumet.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-146">displays only the date.</span></span>
- <span data-ttu-id="1c1b9-147">Tid.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-147">Time.</span></span>
  <span data-ttu-id="1c1b9-148">visar endast tiden.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-148">displays only the time.</span></span>
- <span data-ttu-id="1c1b9-149">DateTime.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-149">DateTime.</span></span>
  <span data-ttu-id="1c1b9-150">visar datum och tid.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-150">displays the date and time.</span></span>

<span data-ttu-id="1c1b9-151">Den här parametern påverkar endast visningen.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-151">This parameter affects only the display.</span></span>
<span data-ttu-id="1c1b9-152">Det påverkar inte det **datetime** -objekt som `Get-Date` hämtas.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-152">It does not affect the **DateTime** object that `Get-Date` retrieves.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.DisplayHintType
Parameter Sets: (All)
Aliases:
Accepted values: Date, Time, DateTime

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c1b9-153">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1c1b9-153">-Confirm</span></span>

<span data-ttu-id="1c1b9-154">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-154">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="1c1b9-155">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1c1b9-155">-WhatIf</span></span>

<span data-ttu-id="1c1b9-156">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-156">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="1c1b9-157">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-157">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="1c1b9-158">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1c1b9-158">CommonParameters</span></span>

<span data-ttu-id="1c1b9-159">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-159">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1c1b9-160">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="1c1b9-160">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="1c1b9-161">INDATA</span><span class="sxs-lookup"><span data-stu-id="1c1b9-161">INPUTS</span></span>

### <span data-ttu-id="1c1b9-162">System. DateTime</span><span class="sxs-lookup"><span data-stu-id="1c1b9-162">System.DateTime</span></span>

<span data-ttu-id="1c1b9-163">Du kan skicka vidare ett datum till `Set-Date` .</span><span class="sxs-lookup"><span data-stu-id="1c1b9-163">You can pipe a date to `Set-Date`.</span></span>

## <span data-ttu-id="1c1b9-164">UTDATA</span><span class="sxs-lookup"><span data-stu-id="1c1b9-164">OUTPUTS</span></span>

### <span data-ttu-id="1c1b9-165">System. DateTime</span><span class="sxs-lookup"><span data-stu-id="1c1b9-165">System.DateTime</span></span>

<span data-ttu-id="1c1b9-166">`Set-Date` Returnerar ett objekt som representerar det datum som angetts.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-166">`Set-Date` returns an object that represents the date that it set.</span></span>

## <span data-ttu-id="1c1b9-167">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="1c1b9-167">NOTES</span></span>

- <span data-ttu-id="1c1b9-168">Använd denna cmdlet försiktigt när du ändrar datum och tid på datorn.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-168">Use this cmdlet cautiously when changing the date and time on the computer.</span></span> <span data-ttu-id="1c1b9-169">Ändringen kan förhindra att datorn tar emot systemomfattande händelser och uppdateringar som utlöses av ett datum eller en tid.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-169">The change might prevent the computer from receiving system-wide events and updates that are triggered by a date or time.</span></span> <span data-ttu-id="1c1b9-170">Använd parametrarna **whatIf** och **Confirm** för att undvika fel.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-170">Use the **WhatIf** and **Confirm** parameters to avoid errors.</span></span>
- <span data-ttu-id="1c1b9-171">Du kan använda standard-.NET-metoder med **datetime** -och **TimeSpan** -objekten som används med `Set-Date` , till exempel **AddDays** , **AddMonths** och **FromFileTime**.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-171">You can use standard .NET methods with the **DateTime** and **TimeSpan** objects used with `Set-Date`, such as **AddDays** , **AddMonths** , and **FromFileTime**.</span></span> <span data-ttu-id="1c1b9-172">Mer information finns i [datetime-metoder](/dotnet/api/system.datetime) och</span><span class="sxs-lookup"><span data-stu-id="1c1b9-172">For more information, see [DateTime Methods](/dotnet/api/system.datetime) and</span></span>

  <span data-ttu-id="1c1b9-173">[TimeSpan-metoder](/dotnet/api/system.timespan) i MSDN-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="1c1b9-173">[TimeSpan Methods](/dotnet/api/system.timespan) in the MSDN library.</span></span>

## <span data-ttu-id="1c1b9-174">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="1c1b9-174">RELATED LINKS</span></span>

[<span data-ttu-id="1c1b9-175">Hämta datum</span><span class="sxs-lookup"><span data-stu-id="1c1b9-175">Get-Date</span></span>](Get-Date.md)

[<span data-ttu-id="1c1b9-176">New-TimeSpan</span><span class="sxs-lookup"><span data-stu-id="1c1b9-176">New-TimeSpan</span></span>](New-TimeSpan.md)
