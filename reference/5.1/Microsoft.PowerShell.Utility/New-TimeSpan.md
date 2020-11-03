---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 5/1/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-timespan?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-TimeSpan
ms.openlocfilehash: 89f277f658645f18d0ae5f2f3ad0e81a8fbdb4a6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264920"
---
# <span data-ttu-id="82f81-103">New-TimeSpan</span><span class="sxs-lookup"><span data-stu-id="82f81-103">New-TimeSpan</span></span>

## <span data-ttu-id="82f81-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="82f81-104">SYNOPSIS</span></span>
<span data-ttu-id="82f81-105">Skapar ett TimeSpan-objekt.</span><span class="sxs-lookup"><span data-stu-id="82f81-105">Creates a TimeSpan object.</span></span>

## <span data-ttu-id="82f81-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="82f81-106">SYNTAX</span></span>

### <span data-ttu-id="82f81-107">Datum (standard)</span><span class="sxs-lookup"><span data-stu-id="82f81-107">Date (Default)</span></span>

```
New-TimeSpan [[-Start] <DateTime>] [[-End] <DateTime>] [<CommonParameters>]
```

### <span data-ttu-id="82f81-108">Tid</span><span class="sxs-lookup"><span data-stu-id="82f81-108">Time</span></span>

```
New-TimeSpan [-Days <Int32>] [-Hours <Int32>] [-Minutes <Int32>] [-Seconds <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="82f81-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="82f81-109">DESCRIPTION</span></span>

<span data-ttu-id="82f81-110">`New-TimeSpan`Cmdleten skapar ett **TimeSpan** -objekt som representerar ett tidsintervall.</span><span class="sxs-lookup"><span data-stu-id="82f81-110">The `New-TimeSpan` cmdlet creates a **TimeSpan** object that represents a time interval.</span></span>
<span data-ttu-id="82f81-111">Du kan använda ett **TimeSpan** -objekt för att lägga till eller ta bort tid från **datetime** -objekt.</span><span class="sxs-lookup"><span data-stu-id="82f81-111">You can use a **TimeSpan** object to add or subtract time from **DateTime** objects.</span></span>

<span data-ttu-id="82f81-112">Utan parametrar returnerar ett- `New-TimeSpan` kommando ett **TimeSpan** -objekt som representerar ett tidsintervall som är noll.</span><span class="sxs-lookup"><span data-stu-id="82f81-112">Without parameters, a `New-TimeSpan` command returns a **TimeSpan** object that represents a time interval of zero.</span></span>

## <span data-ttu-id="82f81-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="82f81-113">EXAMPLES</span></span>

### <span data-ttu-id="82f81-114">Exempel 1: skapa ett TimeSpan-objekt för en angiven varaktighet</span><span class="sxs-lookup"><span data-stu-id="82f81-114">Example 1: Create a TimeSpan object for a specified duration</span></span>

<span data-ttu-id="82f81-115">Det här kommandot skapar ett **TimeSpan** -objekt med en varaktighet på 1 timme och 25 minuter och lagrar det i en variabel med namnet `$TimeSpan` .</span><span class="sxs-lookup"><span data-stu-id="82f81-115">This command creates a **TimeSpan** object with a duration of 1 hour and 25 minutes and stores it in a variable named `$TimeSpan`.</span></span> <span data-ttu-id="82f81-116">Den visar en representation av **TimeSpan** -objektet.</span><span class="sxs-lookup"><span data-stu-id="82f81-116">It displays a representation of the **TimeSpan** object.</span></span>

```powershell
$TimeSpan = New-TimeSpan -Hours 1 -Minutes 25
$TimeSpan
```

```Output
Days              : 0
Hours             : 1
Minutes           : 25
Seconds           : 0
Milliseconds      : 0
Ticks             : 51000000000
TotalDays         : 0.0590277777777778
TotalHours        : 1.41666666666667
TotalMinutes      : 85
TotalSeconds      : 5100
TotalMilliseconds : 5100000
```

### <span data-ttu-id="82f81-117">Exempel 2: skapa ett TimeSpan-objekt för ett tidsintervall</span><span class="sxs-lookup"><span data-stu-id="82f81-117">Example 2: Create a TimeSpan object for a time interval</span></span>

<span data-ttu-id="82f81-118">Det här exemplet skapar ett nytt **TimeSpan** -objekt som representerar intervallet mellan tidpunkten då kommandot körs och 1 januari 2010.</span><span class="sxs-lookup"><span data-stu-id="82f81-118">This example creates a new **TimeSpan** object that represents the interval between the time that the command is run and January 1, 2010.</span></span>

<span data-ttu-id="82f81-119">Det här kommandot kräver inte **Start** parametern eftersom standardvärdet för **Start** parametern är aktuellt datum och aktuell tid.</span><span class="sxs-lookup"><span data-stu-id="82f81-119">This command does not require the **Start** parameter, because the default value of the **Start** parameter is the current date and time.</span></span>

```powershell
New-TimeSpan -End (Get-Date -Year 2010 -Month 1 -Day 1)
```

### <span data-ttu-id="82f81-120">Exempel 3: Hämta datumet 90 dagar från det aktuella datumet</span><span class="sxs-lookup"><span data-stu-id="82f81-120">Example 3: Get the date 90 days from the current date</span></span>

```powershell
$90days = New-TimeSpan -Days 90
(Get-Date) + $90days
```

<span data-ttu-id="82f81-121">De här kommandona returnerar det datum som är 90 dagar efter det aktuella datumet.</span><span class="sxs-lookup"><span data-stu-id="82f81-121">These commands return the date that is 90 days after the current date.</span></span>

### <span data-ttu-id="82f81-122">Exempel 4: identifiera TimeSpan sedan en fil uppdaterades</span><span class="sxs-lookup"><span data-stu-id="82f81-122">Example 4: Discover the TimeSpan since a file was updated</span></span>

<span data-ttu-id="82f81-123">Det här kommandot anger hur lång tid det har sedan den [about_remote](../Microsoft.PowerShell.Core/About/about_Remote.md) hjälp filen senast uppdaterades.</span><span class="sxs-lookup"><span data-stu-id="82f81-123">This command tells you how long it has been since the [about_remote](../Microsoft.PowerShell.Core/About/about_Remote.md) help file was last updated.</span></span>
<span data-ttu-id="82f81-124">Du kan använda det här kommando formatet på alla filer eller andra objekt som har en **LastWriteTime** -egenskap.</span><span class="sxs-lookup"><span data-stu-id="82f81-124">You can use this command format on any file, or any other object that has a **LastWriteTime** property.</span></span>

<span data-ttu-id="82f81-125">Det här kommandot fungerar eftersom **Start** parametern för `New-TimeSpan` har ett alias för **LastWriteTime**.</span><span class="sxs-lookup"><span data-stu-id="82f81-125">This command works because the **Start** parameter of `New-TimeSpan` has an alias of **LastWriteTime**.</span></span> <span data-ttu-id="82f81-126">När du rör ett objekt som har en **LastWriteTime** -egenskap till `New-TimeSpan` , använder PowerShell värdet för egenskapen **LastWriteTime** som värdet för **Start** parametern.</span><span class="sxs-lookup"><span data-stu-id="82f81-126">When you pipe an object that has a **LastWriteTime** property to `New-TimeSpan`, PowerShell uses the value of the **LastWriteTime** property as the value of the **Start** parameter.</span></span>

```powershell
Get-ChildItem $PSHOME\en-us\about_remote.help.txt | New-TimeSpan
```

```Output
Days              : 321
Hours             : 21
Minutes           : 59
Seconds           : 22
Milliseconds      : 312
Ticks             : 278135623127728
TotalDays         : 321.916230471907
TotalHours        : 7725.98953132578
TotalMinutes      : 463559.371879547
TotalSeconds      : 27813562.3127728
TotalMilliseconds : 27813562312.7728
```

## <span data-ttu-id="82f81-127">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="82f81-127">PARAMETERS</span></span>

### <span data-ttu-id="82f81-128">-Dagar</span><span class="sxs-lookup"><span data-stu-id="82f81-128">-Days</span></span>

<span data-ttu-id="82f81-129">Anger dagar i tidsintervallet.</span><span class="sxs-lookup"><span data-stu-id="82f81-129">Specifies the days in the time span.</span></span>
<span data-ttu-id="82f81-130">Standardvärdet är 0.</span><span class="sxs-lookup"><span data-stu-id="82f81-130">The default value is 0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="82f81-131">-Slut</span><span class="sxs-lookup"><span data-stu-id="82f81-131">-End</span></span>

<span data-ttu-id="82f81-132">Anger slutet på ett tidsintervall.</span><span class="sxs-lookup"><span data-stu-id="82f81-132">Specifies the end of a time span.</span></span>
<span data-ttu-id="82f81-133">Standardvärdet är aktuellt datum och aktuell tid.</span><span class="sxs-lookup"><span data-stu-id="82f81-133">The default value is the current date and time.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: Date
Aliases:

Required: False
Position: 1
Default value: Current date and time
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="82f81-134">-Timmar</span><span class="sxs-lookup"><span data-stu-id="82f81-134">-Hours</span></span>

<span data-ttu-id="82f81-135">Anger timmarna i tidsintervallet.</span><span class="sxs-lookup"><span data-stu-id="82f81-135">Specifies the hours in the time span.</span></span>
<span data-ttu-id="82f81-136">Standardvärdet är noll.</span><span class="sxs-lookup"><span data-stu-id="82f81-136">The default value is zero.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="82f81-137">– Minuter</span><span class="sxs-lookup"><span data-stu-id="82f81-137">-Minutes</span></span>

<span data-ttu-id="82f81-138">Anger minuterna i tidsintervallet.</span><span class="sxs-lookup"><span data-stu-id="82f81-138">Specifies the minutes in the time span.</span></span>
<span data-ttu-id="82f81-139">Standardvärdet är 0.</span><span class="sxs-lookup"><span data-stu-id="82f81-139">The default value is 0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="82f81-140">– Sekunder</span><span class="sxs-lookup"><span data-stu-id="82f81-140">-Seconds</span></span>

<span data-ttu-id="82f81-141">Anger tids periodens längd i sekunder.</span><span class="sxs-lookup"><span data-stu-id="82f81-141">Specifies the length of the time span in seconds.</span></span>
<span data-ttu-id="82f81-142">Standardvärdet är 0.</span><span class="sxs-lookup"><span data-stu-id="82f81-142">The default value is 0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="82f81-143">-Start</span><span class="sxs-lookup"><span data-stu-id="82f81-143">-Start</span></span>

<span data-ttu-id="82f81-144">Anger början på ett tidsintervall.</span><span class="sxs-lookup"><span data-stu-id="82f81-144">Specifies the start of a time span.</span></span>
<span data-ttu-id="82f81-145">Ange en sträng som representerar datum och tid, till exempel "3/15/09" eller ett **datetime** -objekt, till exempel ett från ett `Get-Date` kommando.</span><span class="sxs-lookup"><span data-stu-id="82f81-145">Enter a string that represents the date and time, such as "3/15/09" or a **DateTime** object, such as one from a `Get-Date` command.</span></span> <span data-ttu-id="82f81-146">Standardvärdet är aktuellt datum och aktuell tid.</span><span class="sxs-lookup"><span data-stu-id="82f81-146">The default value is the current date and time.</span></span>

<span data-ttu-id="82f81-147">Du kan använda **Start** eller dess alias, **LastWriteTime**.</span><span class="sxs-lookup"><span data-stu-id="82f81-147">You can use **Start** or its alias, **LastWriteTime**.</span></span>
<span data-ttu-id="82f81-148">Med **LastWriteTime** -aliaset kan du skicka pipe-objekt som har en **LastWriteTime** -egenskap, till exempel filer i fil systemet `[System.Io.FileIO]` , till **Start** parametern för `New-TimeSpan` .</span><span class="sxs-lookup"><span data-stu-id="82f81-148">The **LastWriteTime** alias lets you pipe objects that have a **LastWriteTime** property, such as files in the file system `[System.Io.FileIO]`, to the **Start** parameter of `New-TimeSpan`.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: Date
Aliases: LastWriteTime

Required: False
Position: 0
Default value: Current date and time
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="82f81-149">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="82f81-149">CommonParameters</span></span>

<span data-ttu-id="82f81-150">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="82f81-150">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="82f81-151">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="82f81-151">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="82f81-152">INDATA</span><span class="sxs-lookup"><span data-stu-id="82f81-152">INPUTS</span></span>

### <span data-ttu-id="82f81-153">System. DateTime</span><span class="sxs-lookup"><span data-stu-id="82f81-153">System.DateTime</span></span>

<span data-ttu-id="82f81-154">Du kan skicka vidare ett **datetime** -objekt som representerar start tiden till `New-TimeSpan` .</span><span class="sxs-lookup"><span data-stu-id="82f81-154">You can pipe a **DateTime** object that represents that start time to `New-TimeSpan`.</span></span>

## <span data-ttu-id="82f81-155">UTDATA</span><span class="sxs-lookup"><span data-stu-id="82f81-155">OUTPUTS</span></span>

### <span data-ttu-id="82f81-156">System. TimeSpan</span><span class="sxs-lookup"><span data-stu-id="82f81-156">System.TimeSpan</span></span>

<span data-ttu-id="82f81-157">`New-TimeSpan` Returnerar ett objekt som representerar tidsintervallet.</span><span class="sxs-lookup"><span data-stu-id="82f81-157">`New-TimeSpan` returns an object that represents the time span.</span></span>

## <span data-ttu-id="82f81-158">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="82f81-158">NOTES</span></span>

## <span data-ttu-id="82f81-159">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="82f81-159">RELATED LINKS</span></span>

[<span data-ttu-id="82f81-160">Hämta datum</span><span class="sxs-lookup"><span data-stu-id="82f81-160">Get-Date</span></span>](Get-Date.md)

[<span data-ttu-id="82f81-161">Ange datum</span><span class="sxs-lookup"><span data-stu-id="82f81-161">Set-Date</span></span>](Set-Date.md)
