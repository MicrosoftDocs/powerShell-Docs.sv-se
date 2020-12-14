---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-timespan?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-TimeSpan
ms.openlocfilehash: 5808685a5560d1cbf91c6705b90643c35702b28a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710086"
---
# <span data-ttu-id="35c1a-102">New-TimeSpan</span><span class="sxs-lookup"><span data-stu-id="35c1a-102">New-TimeSpan</span></span>

## <span data-ttu-id="35c1a-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="35c1a-103">SYNOPSIS</span></span>
<span data-ttu-id="35c1a-104">Skapar ett TimeSpan-objekt.</span><span class="sxs-lookup"><span data-stu-id="35c1a-104">Creates a TimeSpan object.</span></span>

## <span data-ttu-id="35c1a-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="35c1a-105">SYNTAX</span></span>

### <span data-ttu-id="35c1a-106">Datum (standard)</span><span class="sxs-lookup"><span data-stu-id="35c1a-106">Date (Default)</span></span>

```
New-TimeSpan [[-Start] <DateTime>] [[-End] <DateTime>] [<CommonParameters>]
```

### <span data-ttu-id="35c1a-107">Tid</span><span class="sxs-lookup"><span data-stu-id="35c1a-107">Time</span></span>

```
New-TimeSpan [-Days <Int32>] [-Hours <Int32>] [-Minutes <Int32>] [-Seconds <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="35c1a-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="35c1a-108">DESCRIPTION</span></span>

<span data-ttu-id="35c1a-109">`New-TimeSpan`Cmdleten skapar ett **TimeSpan** -objekt som representerar ett tidsintervall.</span><span class="sxs-lookup"><span data-stu-id="35c1a-109">The `New-TimeSpan` cmdlet creates a **TimeSpan** object that represents a time interval.</span></span>
<span data-ttu-id="35c1a-110">Du kan använda ett **TimeSpan** -objekt för att lägga till eller ta bort tid från **datetime** -objekt.</span><span class="sxs-lookup"><span data-stu-id="35c1a-110">You can use a **TimeSpan** object to add or subtract time from **DateTime** objects.</span></span>

<span data-ttu-id="35c1a-111">Utan parametrar returnerar ett- `New-TimeSpan` kommando ett **TimeSpan** -objekt som representerar ett tidsintervall som är noll.</span><span class="sxs-lookup"><span data-stu-id="35c1a-111">Without parameters, a `New-TimeSpan` command returns a **TimeSpan** object that represents a time interval of zero.</span></span>

## <span data-ttu-id="35c1a-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="35c1a-112">EXAMPLES</span></span>

### <span data-ttu-id="35c1a-113">Exempel 1: skapa ett TimeSpan-objekt för en angiven varaktighet</span><span class="sxs-lookup"><span data-stu-id="35c1a-113">Example 1: Create a TimeSpan object for a specified duration</span></span>

<span data-ttu-id="35c1a-114">Det här kommandot skapar ett **TimeSpan** -objekt med en varaktighet på 1 timme och 25 minuter och lagrar det i en variabel med namnet `$TimeSpan` .</span><span class="sxs-lookup"><span data-stu-id="35c1a-114">This command creates a **TimeSpan** object with a duration of 1 hour and 25 minutes and stores it in a variable named `$TimeSpan`.</span></span> <span data-ttu-id="35c1a-115">Den visar en representation av **TimeSpan** -objektet.</span><span class="sxs-lookup"><span data-stu-id="35c1a-115">It displays a representation of the **TimeSpan** object.</span></span>

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

### <span data-ttu-id="35c1a-116">Exempel 2: skapa ett TimeSpan-objekt för ett tidsintervall</span><span class="sxs-lookup"><span data-stu-id="35c1a-116">Example 2: Create a TimeSpan object for a time interval</span></span>

<span data-ttu-id="35c1a-117">Det här exemplet skapar ett nytt **TimeSpan** -objekt som representerar intervallet mellan tidpunkten då kommandot körs och 1 januari 2010.</span><span class="sxs-lookup"><span data-stu-id="35c1a-117">This example creates a new **TimeSpan** object that represents the interval between the time that the command is run and January 1, 2010.</span></span>

<span data-ttu-id="35c1a-118">Det här kommandot kräver inte **Start** parametern eftersom standardvärdet för **Start** parametern är aktuellt datum och aktuell tid.</span><span class="sxs-lookup"><span data-stu-id="35c1a-118">This command does not require the **Start** parameter, because the default value of the **Start** parameter is the current date and time.</span></span>

```powershell
New-TimeSpan -End (Get-Date -Year 2010 -Month 1 -Day 1)
```

### <span data-ttu-id="35c1a-119">Exempel 3: Hämta datumet 90 dagar från det aktuella datumet</span><span class="sxs-lookup"><span data-stu-id="35c1a-119">Example 3: Get the date 90 days from the current date</span></span>

```powershell
$90days = New-TimeSpan -Days 90
(Get-Date) + $90days
```

<span data-ttu-id="35c1a-120">De här kommandona returnerar det datum som är 90 dagar efter det aktuella datumet.</span><span class="sxs-lookup"><span data-stu-id="35c1a-120">These commands return the date that is 90 days after the current date.</span></span>

### <span data-ttu-id="35c1a-121">Exempel 4: identifiera TimeSpan sedan en fil uppdaterades</span><span class="sxs-lookup"><span data-stu-id="35c1a-121">Example 4: Discover the TimeSpan since a file was updated</span></span>

<span data-ttu-id="35c1a-122">Det här kommandot anger hur lång tid det har sedan den [about_remote](../Microsoft.PowerShell.Core/About/about_Remote.md) hjälp filen senast uppdaterades.</span><span class="sxs-lookup"><span data-stu-id="35c1a-122">This command tells you how long it has been since the [about_remote](../Microsoft.PowerShell.Core/About/about_Remote.md) help file was last updated.</span></span>
<span data-ttu-id="35c1a-123">Du kan använda det här kommando formatet på alla filer eller andra objekt som har en **LastWriteTime** -egenskap.</span><span class="sxs-lookup"><span data-stu-id="35c1a-123">You can use this command format on any file, or any other object that has a **LastWriteTime** property.</span></span>

<span data-ttu-id="35c1a-124">Det här kommandot fungerar eftersom **Start** parametern för `New-TimeSpan` har ett alias för **LastWriteTime**.</span><span class="sxs-lookup"><span data-stu-id="35c1a-124">This command works because the **Start** parameter of `New-TimeSpan` has an alias of **LastWriteTime**.</span></span> <span data-ttu-id="35c1a-125">När du rör ett objekt som har en **LastWriteTime** -egenskap till `New-TimeSpan` , använder PowerShell värdet för egenskapen **LastWriteTime** som värdet för **Start** parametern.</span><span class="sxs-lookup"><span data-stu-id="35c1a-125">When you pipe an object that has a **LastWriteTime** property to `New-TimeSpan`, PowerShell uses the value of the **LastWriteTime** property as the value of the **Start** parameter.</span></span>

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

## <span data-ttu-id="35c1a-126">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="35c1a-126">PARAMETERS</span></span>

### <span data-ttu-id="35c1a-127">-Dagar</span><span class="sxs-lookup"><span data-stu-id="35c1a-127">-Days</span></span>

<span data-ttu-id="35c1a-128">Anger dagar i tidsintervallet.</span><span class="sxs-lookup"><span data-stu-id="35c1a-128">Specifies the days in the time span.</span></span>
<span data-ttu-id="35c1a-129">Standardvärdet är 0.</span><span class="sxs-lookup"><span data-stu-id="35c1a-129">The default value is 0.</span></span>

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

### <span data-ttu-id="35c1a-130">-Slut</span><span class="sxs-lookup"><span data-stu-id="35c1a-130">-End</span></span>

<span data-ttu-id="35c1a-131">Anger slutet på ett tidsintervall.</span><span class="sxs-lookup"><span data-stu-id="35c1a-131">Specifies the end of a time span.</span></span>
<span data-ttu-id="35c1a-132">Standardvärdet är aktuellt datum och aktuell tid.</span><span class="sxs-lookup"><span data-stu-id="35c1a-132">The default value is the current date and time.</span></span>

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

### <span data-ttu-id="35c1a-133">-Timmar</span><span class="sxs-lookup"><span data-stu-id="35c1a-133">-Hours</span></span>

<span data-ttu-id="35c1a-134">Anger timmarna i tidsintervallet.</span><span class="sxs-lookup"><span data-stu-id="35c1a-134">Specifies the hours in the time span.</span></span>
<span data-ttu-id="35c1a-135">Standardvärdet är noll.</span><span class="sxs-lookup"><span data-stu-id="35c1a-135">The default value is zero.</span></span>

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

### <span data-ttu-id="35c1a-136">– Minuter</span><span class="sxs-lookup"><span data-stu-id="35c1a-136">-Minutes</span></span>

<span data-ttu-id="35c1a-137">Anger minuterna i tidsintervallet.</span><span class="sxs-lookup"><span data-stu-id="35c1a-137">Specifies the minutes in the time span.</span></span>
<span data-ttu-id="35c1a-138">Standardvärdet är 0.</span><span class="sxs-lookup"><span data-stu-id="35c1a-138">The default value is 0.</span></span>

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

### <span data-ttu-id="35c1a-139">– Sekunder</span><span class="sxs-lookup"><span data-stu-id="35c1a-139">-Seconds</span></span>

<span data-ttu-id="35c1a-140">Anger tids periodens längd i sekunder.</span><span class="sxs-lookup"><span data-stu-id="35c1a-140">Specifies the length of the time span in seconds.</span></span>
<span data-ttu-id="35c1a-141">Standardvärdet är 0.</span><span class="sxs-lookup"><span data-stu-id="35c1a-141">The default value is 0.</span></span>

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

### <span data-ttu-id="35c1a-142">-Start</span><span class="sxs-lookup"><span data-stu-id="35c1a-142">-Start</span></span>

<span data-ttu-id="35c1a-143">Anger början på ett tidsintervall.</span><span class="sxs-lookup"><span data-stu-id="35c1a-143">Specifies the start of a time span.</span></span>
<span data-ttu-id="35c1a-144">Ange en sträng som representerar datum och tid, till exempel "3/15/09" eller ett **datetime** -objekt, till exempel ett från ett `Get-Date` kommando.</span><span class="sxs-lookup"><span data-stu-id="35c1a-144">Enter a string that represents the date and time, such as "3/15/09" or a **DateTime** object, such as one from a `Get-Date` command.</span></span> <span data-ttu-id="35c1a-145">Standardvärdet är aktuellt datum och aktuell tid.</span><span class="sxs-lookup"><span data-stu-id="35c1a-145">The default value is the current date and time.</span></span>

<span data-ttu-id="35c1a-146">Du kan använda **Start** eller dess alias, **LastWriteTime**.</span><span class="sxs-lookup"><span data-stu-id="35c1a-146">You can use **Start** or its alias, **LastWriteTime**.</span></span>
<span data-ttu-id="35c1a-147">Med **LastWriteTime** -aliaset kan du skicka pipe-objekt som har en **LastWriteTime** -egenskap, till exempel filer i fil systemet `[System.Io.FileIO]` , till **Start** parametern för `New-TimeSpan` .</span><span class="sxs-lookup"><span data-stu-id="35c1a-147">The **LastWriteTime** alias lets you pipe objects that have a **LastWriteTime** property, such as files in the file system `[System.Io.FileIO]`, to the **Start** parameter of `New-TimeSpan`.</span></span>

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

### <span data-ttu-id="35c1a-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="35c1a-148">CommonParameters</span></span>

<span data-ttu-id="35c1a-149">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="35c1a-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="35c1a-150">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="35c1a-150">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="35c1a-151">INDATA</span><span class="sxs-lookup"><span data-stu-id="35c1a-151">INPUTS</span></span>

### <span data-ttu-id="35c1a-152">System. DateTime</span><span class="sxs-lookup"><span data-stu-id="35c1a-152">System.DateTime</span></span>

<span data-ttu-id="35c1a-153">Du kan skicka vidare ett **datetime** -objekt som representerar start tiden till `New-TimeSpan` .</span><span class="sxs-lookup"><span data-stu-id="35c1a-153">You can pipe a **DateTime** object that represents that start time to `New-TimeSpan`.</span></span>

## <span data-ttu-id="35c1a-154">UTDATA</span><span class="sxs-lookup"><span data-stu-id="35c1a-154">OUTPUTS</span></span>

### <span data-ttu-id="35c1a-155">System. TimeSpan</span><span class="sxs-lookup"><span data-stu-id="35c1a-155">System.TimeSpan</span></span>

<span data-ttu-id="35c1a-156">`New-TimeSpan` Returnerar ett objekt som representerar tidsintervallet.</span><span class="sxs-lookup"><span data-stu-id="35c1a-156">`New-TimeSpan` returns an object that represents the time span.</span></span>

## <span data-ttu-id="35c1a-157">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="35c1a-157">NOTES</span></span>

## <span data-ttu-id="35c1a-158">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="35c1a-158">RELATED LINKS</span></span>

[<span data-ttu-id="35c1a-159">Hämta datum</span><span class="sxs-lookup"><span data-stu-id="35c1a-159">Get-Date</span></span>](Get-Date.md)

[<span data-ttu-id="35c1a-160">Ange datum</span><span class="sxs-lookup"><span data-stu-id="35c1a-160">Set-Date</span></span>](Set-Date.md)

