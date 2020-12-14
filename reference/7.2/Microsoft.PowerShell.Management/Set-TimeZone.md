---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/18/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-timezone?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-TimeZone
ms.openlocfilehash: ddce638972aabb1afc1c8fe500df380dd01dff14
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710387"
---
# <span data-ttu-id="1894d-102">Set-TimeZone</span><span class="sxs-lookup"><span data-stu-id="1894d-102">Set-TimeZone</span></span>

## <span data-ttu-id="1894d-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="1894d-103">SYNOPSIS</span></span>
<span data-ttu-id="1894d-104">Ställer in system tids zonen till en angiven tidszon.</span><span class="sxs-lookup"><span data-stu-id="1894d-104">Sets the system time zone to a specified time zone.</span></span>

## <span data-ttu-id="1894d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1894d-105">SYNTAX</span></span>

### <span data-ttu-id="1894d-106">Namn (standard)</span><span class="sxs-lookup"><span data-stu-id="1894d-106">Name (Default)</span></span>

```
Set-TimeZone [-Name] <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="1894d-107">Id</span><span class="sxs-lookup"><span data-stu-id="1894d-107">Id</span></span>

```
Set-TimeZone -Id <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="1894d-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="1894d-108">InputObject</span></span>

```
Set-TimeZone [-InputObject] <TimeZoneInfo> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="1894d-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="1894d-109">DESCRIPTION</span></span>

<span data-ttu-id="1894d-110">`Set-TimeZone`Cmdleten anger system tids zonen till en angiven tidszon.</span><span class="sxs-lookup"><span data-stu-id="1894d-110">The `Set-TimeZone` cmdlet sets the system time zone to a specified time zone.</span></span>

## <span data-ttu-id="1894d-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="1894d-111">EXAMPLES</span></span>

### <span data-ttu-id="1894d-112">Exempel 1: Ange tids zonen efter ID</span><span class="sxs-lookup"><span data-stu-id="1894d-112">Example 1: Set the time zone by Id</span></span>

<span data-ttu-id="1894d-113">I det här exemplet anges tids zonen på den lokala datorn till ryska, normal tid.</span><span class="sxs-lookup"><span data-stu-id="1894d-113">This example sets the time zone on the local computer to Russian Standard Time.</span></span>

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

### <span data-ttu-id="1894d-114">Exempel 2: Ange tids zonen efter namn</span><span class="sxs-lookup"><span data-stu-id="1894d-114">Example 2: Set the time zone by name</span></span>

<span data-ttu-id="1894d-115">I det här exemplet anges tids zonen på den lokala datorn till ryska, normal tid.</span><span class="sxs-lookup"><span data-stu-id="1894d-115">This example sets the time zone on the local computer to Russian Standard Time.</span></span>

```powershell
Set-TimeZone -Name "Russia TZ 2 Standard Time"
```

<span data-ttu-id="1894d-116">Som vi såg i föregående exempel stämmer inte alltid med **ID** och **namnet** för tids zonen.</span><span class="sxs-lookup"><span data-stu-id="1894d-116">As we saw in the previous example, the **Id** and the **Name** of the Time Zone do not always match.</span></span>
<span data-ttu-id="1894d-117">Parametern **Name** måste matcha **StandardName** -eller **DaylightName** -egenskaperna för **TimeZoneInfo** -objektet.</span><span class="sxs-lookup"><span data-stu-id="1894d-117">The **Name** parameter must match the **StandardName** or **DaylightName** properties of the **TimeZoneInfo** object.</span></span>

## <span data-ttu-id="1894d-118">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="1894d-118">PARAMETERS</span></span>

### <span data-ttu-id="1894d-119">-ID</span><span class="sxs-lookup"><span data-stu-id="1894d-119">-Id</span></span>

<span data-ttu-id="1894d-120">Anger ID för den tidszon som denna cmdlet anger.</span><span class="sxs-lookup"><span data-stu-id="1894d-120">Specifies the ID of the time zone that this cmdlet sets.</span></span> <span data-ttu-id="1894d-121">En fullständig lista över tids zons-ID: n kan erhållas genom att köra följande kommando: `Get-TimeZone -ListAvailable` .</span><span class="sxs-lookup"><span data-stu-id="1894d-121">A full list of Time Zone IDs can be obtained by running the following command: `Get-TimeZone -ListAvailable`.</span></span>

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

### <span data-ttu-id="1894d-122">– InputObject</span><span class="sxs-lookup"><span data-stu-id="1894d-122">-InputObject</span></span>

<span data-ttu-id="1894d-123">Anger ett **TimeZoneInfo** -objekt som ska användas som indatamängd.</span><span class="sxs-lookup"><span data-stu-id="1894d-123">Specifies a **TimeZoneInfo** object to use as input.</span></span>

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

### <span data-ttu-id="1894d-124">-Name</span><span class="sxs-lookup"><span data-stu-id="1894d-124">-Name</span></span>

<span data-ttu-id="1894d-125">Anger namnet på den tidszon som denna cmdlet anger.</span><span class="sxs-lookup"><span data-stu-id="1894d-125">Specifies the name of the time zone that this cmdlet sets.</span></span> <span data-ttu-id="1894d-126">En fullständig lista över tids zons namn kan hämtas genom att köra följande kommando: `Get-TimeZone -ListAvailable` .</span><span class="sxs-lookup"><span data-stu-id="1894d-126">A full list of Time Zone names can be obtained by running the following command: `Get-TimeZone -ListAvailable`.</span></span>

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

### <span data-ttu-id="1894d-127">– PassThru</span><span class="sxs-lookup"><span data-stu-id="1894d-127">-PassThru</span></span>

<span data-ttu-id="1894d-128">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="1894d-128">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="1894d-129">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="1894d-129">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="1894d-130">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1894d-130">-Confirm</span></span>

<span data-ttu-id="1894d-131">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1894d-131">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="1894d-132">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1894d-132">-WhatIf</span></span>

<span data-ttu-id="1894d-133">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="1894d-133">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="1894d-134">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="1894d-134">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="1894d-135">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1894d-135">CommonParameters</span></span>

<span data-ttu-id="1894d-136">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1894d-136">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1894d-137">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1894d-137">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1894d-138">INDATA</span><span class="sxs-lookup"><span data-stu-id="1894d-138">INPUTS</span></span>

### <span data-ttu-id="1894d-139">System. String, system. TimeZoneInfo, system. String</span><span class="sxs-lookup"><span data-stu-id="1894d-139">System.String, System.TimeZoneInfo, System.String</span></span>

## <span data-ttu-id="1894d-140">UTDATA</span><span class="sxs-lookup"><span data-stu-id="1894d-140">OUTPUTS</span></span>

## <span data-ttu-id="1894d-141">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="1894d-141">NOTES</span></span>

<span data-ttu-id="1894d-142">Den här cmdleten är endast tillgänglig på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="1894d-142">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="1894d-143">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="1894d-143">RELATED LINKS</span></span>

[<span data-ttu-id="1894d-144">Get-TimeZone</span><span class="sxs-lookup"><span data-stu-id="1894d-144">Get-TimeZone</span></span>](Get-TimeZone.md)
