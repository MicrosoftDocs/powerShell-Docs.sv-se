---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/18/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-timezone?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-TimeZone
ms.openlocfilehash: 3738ac6202fa7a46c9a742e48edaeb1b82b5d749
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94345127"
---
# <span data-ttu-id="7473f-103">Set-TimeZone</span><span class="sxs-lookup"><span data-stu-id="7473f-103">Set-TimeZone</span></span>

## <span data-ttu-id="7473f-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="7473f-104">SYNOPSIS</span></span>
<span data-ttu-id="7473f-105">Ställer in system tids zonen till en angiven tidszon.</span><span class="sxs-lookup"><span data-stu-id="7473f-105">Sets the system time zone to a specified time zone.</span></span>

## <span data-ttu-id="7473f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7473f-106">SYNTAX</span></span>

### <span data-ttu-id="7473f-107">Namn (standard)</span><span class="sxs-lookup"><span data-stu-id="7473f-107">Name (Default)</span></span>

```
Set-TimeZone [-Name] <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7473f-108">Id</span><span class="sxs-lookup"><span data-stu-id="7473f-108">Id</span></span>

```
Set-TimeZone -Id <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7473f-109">InputObject</span><span class="sxs-lookup"><span data-stu-id="7473f-109">InputObject</span></span>

```
Set-TimeZone [-InputObject] <TimeZoneInfo> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="7473f-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="7473f-110">DESCRIPTION</span></span>

<span data-ttu-id="7473f-111">`Set-TimeZone`Cmdleten anger system tids zonen till en angiven tidszon.</span><span class="sxs-lookup"><span data-stu-id="7473f-111">The `Set-TimeZone` cmdlet sets the system time zone to a specified time zone.</span></span>

## <span data-ttu-id="7473f-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="7473f-112">EXAMPLES</span></span>

### <span data-ttu-id="7473f-113">Exempel 1: Ange tids zonen efter ID</span><span class="sxs-lookup"><span data-stu-id="7473f-113">Example 1: Set the time zone by Id</span></span>

<span data-ttu-id="7473f-114">I det här exemplet anges tids zonen på den lokala datorn till ryska, normal tid.</span><span class="sxs-lookup"><span data-stu-id="7473f-114">This example sets the time zone on the local computer to Russian Standard Time.</span></span>

```powershell
Set-TimeZone -Id "Russian Standard Time" -PassThru
```

```Output
Id                         : Russian Standard Time
DisplayName                : (UTC+03:00) Moscow, St. Petersburg
StandardName               : Russia TZ 2 Standard Time
DaylightName               : Russia TZ 2 Daylight Time
BaseUtcOffset              : 03:00:00
SupportsDaylightSavingTime : True
```

### <span data-ttu-id="7473f-115">Exempel 2: Ange tids zonen efter namn</span><span class="sxs-lookup"><span data-stu-id="7473f-115">Example 2: Set the time zone by name</span></span>

<span data-ttu-id="7473f-116">I det här exemplet anges tids zonen på den lokala datorn till ryska, normal tid.</span><span class="sxs-lookup"><span data-stu-id="7473f-116">This example sets the time zone on the local computer to Russian Standard Time.</span></span>

```powershell
Set-TimeZone -Name "Russia TZ 2 Standard Time"
```

<span data-ttu-id="7473f-117">Som vi såg i föregående exempel stämmer inte alltid med **ID** och **namnet** för tids zonen.</span><span class="sxs-lookup"><span data-stu-id="7473f-117">As we saw in the previous example, the **Id** and the **Name** of the Time Zone do not always match.</span></span>
<span data-ttu-id="7473f-118">Parametern **Name** måste matcha **StandardName** -eller **DaylightName** -egenskaperna för **TimeZoneInfo** -objektet.</span><span class="sxs-lookup"><span data-stu-id="7473f-118">The **Name** parameter must match the **StandardName** or **DaylightName** properties of the **TimeZoneInfo** object.</span></span>

## <span data-ttu-id="7473f-119">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="7473f-119">PARAMETERS</span></span>

### <span data-ttu-id="7473f-120">-ID</span><span class="sxs-lookup"><span data-stu-id="7473f-120">-Id</span></span>

<span data-ttu-id="7473f-121">Anger ID för den tidszon som denna cmdlet anger.</span><span class="sxs-lookup"><span data-stu-id="7473f-121">Specifies the ID of the time zone that this cmdlet sets.</span></span> <span data-ttu-id="7473f-122">En fullständig lista över tids zons-ID: n kan erhållas genom att köra följande kommando: `Get-TimeZone -ListAvailable` .</span><span class="sxs-lookup"><span data-stu-id="7473f-122">A full list of Time Zone IDs can be obtained by running the following command: `Get-TimeZone -ListAvailable`.</span></span>

```yaml
Type: System.String
Parameter Sets: Id
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="7473f-123">– InputObject</span><span class="sxs-lookup"><span data-stu-id="7473f-123">-InputObject</span></span>

<span data-ttu-id="7473f-124">Anger ett **TimeZoneInfo** -objekt som ska användas som indatamängd.</span><span class="sxs-lookup"><span data-stu-id="7473f-124">Specifies a **TimeZoneInfo** object to use as input.</span></span>

```yaml
Type: System.TimeZoneInfo
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="7473f-125">-Name</span><span class="sxs-lookup"><span data-stu-id="7473f-125">-Name</span></span>

<span data-ttu-id="7473f-126">Anger namnet på den tidszon som denna cmdlet anger.</span><span class="sxs-lookup"><span data-stu-id="7473f-126">Specifies the name of the time zone that this cmdlet sets.</span></span> <span data-ttu-id="7473f-127">En fullständig lista över tids zons namn kan hämtas genom att köra följande kommando: `Get-TimeZone -ListAvailable` .</span><span class="sxs-lookup"><span data-stu-id="7473f-127">A full list of Time Zone names can be obtained by running the following command: `Get-TimeZone -ListAvailable`.</span></span>

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7473f-128">– PassThru</span><span class="sxs-lookup"><span data-stu-id="7473f-128">-PassThru</span></span>

<span data-ttu-id="7473f-129">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="7473f-129">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="7473f-130">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="7473f-130">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="7473f-131">-Confirm</span><span class="sxs-lookup"><span data-stu-id="7473f-131">-Confirm</span></span>

<span data-ttu-id="7473f-132">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7473f-132">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="7473f-133">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="7473f-133">-WhatIf</span></span>

<span data-ttu-id="7473f-134">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="7473f-134">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="7473f-135">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="7473f-135">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="7473f-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7473f-136">CommonParameters</span></span>

<span data-ttu-id="7473f-137">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7473f-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7473f-138">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="7473f-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7473f-139">INDATA</span><span class="sxs-lookup"><span data-stu-id="7473f-139">INPUTS</span></span>

### <span data-ttu-id="7473f-140">System. String, system. TimeZoneInfo, system. String</span><span class="sxs-lookup"><span data-stu-id="7473f-140">System.String, System.TimeZoneInfo, System.String</span></span>

## <span data-ttu-id="7473f-141">UTDATA</span><span class="sxs-lookup"><span data-stu-id="7473f-141">OUTPUTS</span></span>

## <span data-ttu-id="7473f-142">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="7473f-142">NOTES</span></span>

<span data-ttu-id="7473f-143">Den här cmdleten är endast tillgänglig på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="7473f-143">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="7473f-144">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="7473f-144">RELATED LINKS</span></span>

[<span data-ttu-id="7473f-145">Get-TimeZone</span><span class="sxs-lookup"><span data-stu-id="7473f-145">Get-TimeZone</span></span>](Get-TimeZone.md)
