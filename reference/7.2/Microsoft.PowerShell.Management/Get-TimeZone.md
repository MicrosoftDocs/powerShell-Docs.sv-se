---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-timezone?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TimeZone
ms.openlocfilehash: 22034eeac6988478a5f2ff87b2582cc5e1acc1c0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709492"
---
# <span data-ttu-id="b3fc6-102">Get-TimeZone</span><span class="sxs-lookup"><span data-stu-id="b3fc6-102">Get-TimeZone</span></span>

## <span data-ttu-id="b3fc6-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="b3fc6-103">SYNOPSIS</span></span>
<span data-ttu-id="b3fc6-104">Hämtar den aktuella tids zonen eller en lista över tillgängliga tids zoner.</span><span class="sxs-lookup"><span data-stu-id="b3fc6-104">Gets the current time zone or a list of available time zones.</span></span>

## <span data-ttu-id="b3fc6-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b3fc6-105">SYNTAX</span></span>

### <span data-ttu-id="b3fc6-106">Namn (standard)</span><span class="sxs-lookup"><span data-stu-id="b3fc6-106">Name (Default)</span></span>

```
Get-TimeZone [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="b3fc6-107">Id</span><span class="sxs-lookup"><span data-stu-id="b3fc6-107">Id</span></span>

```
Get-TimeZone -Id <String[]> [<CommonParameters>]
```

### <span data-ttu-id="b3fc6-108">ListAvailable</span><span class="sxs-lookup"><span data-stu-id="b3fc6-108">ListAvailable</span></span>

```
Get-TimeZone [-ListAvailable] [<CommonParameters>]
```

## <span data-ttu-id="b3fc6-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b3fc6-109">DESCRIPTION</span></span>

<span data-ttu-id="b3fc6-110">Cmdleten **Get-timezone** hämtar den aktuella tids zonen eller en lista över tillgängliga tids zoner.</span><span class="sxs-lookup"><span data-stu-id="b3fc6-110">The **Get-TimeZone** cmdlet gets the current time zone or a list of available time zones.</span></span>

## <span data-ttu-id="b3fc6-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="b3fc6-111">EXAMPLES</span></span>

### <span data-ttu-id="b3fc6-112">Exempel 1: Hämta aktuell tidszon</span><span class="sxs-lookup"><span data-stu-id="b3fc6-112">Example 1: Get the current time zone</span></span>

```
PS C:\> Get-TimeZone
Pacific Standard Time
```

<span data-ttu-id="b3fc6-113">Det här kommandot hämtar den aktuella tids zonen.</span><span class="sxs-lookup"><span data-stu-id="b3fc6-113">This command gets the current time zone.</span></span>

### <span data-ttu-id="b3fc6-114">Exempel 2: Hämta tids zoner som matchar en angiven sträng</span><span class="sxs-lookup"><span data-stu-id="b3fc6-114">Example 2: Get time zones that match a specified string</span></span>

```
PS C:\> Get-TimeZone -Name "*pac*"
Pacific Standard Time (Mexico)

(UTC-08:00) Pacific Time (US &amp; Canada)

Pacific Standard Time

SA Pacific Standard Time

Pacific SA Standard Time

West Pacific Standard Time

Central Pacific Standard Time
```

<span data-ttu-id="b3fc6-115">Det här kommandot hämtar alla tids zoner som matchar det angivna jokertecknet.</span><span class="sxs-lookup"><span data-stu-id="b3fc6-115">This command gets all time zones that match the specified wildcard.</span></span>

### <span data-ttu-id="b3fc6-116">Exempel 3: Hämta alla tillgängliga tids zoner</span><span class="sxs-lookup"><span data-stu-id="b3fc6-116">Example 3: Get all available time zones</span></span>

```
PS C:\> Get-TimeZone -ListAvailable
```

<span data-ttu-id="b3fc6-117">Det här kommandot hämtar alla tillgängliga tids zoner.</span><span class="sxs-lookup"><span data-stu-id="b3fc6-117">This command gets all available time zones.</span></span>

## <span data-ttu-id="b3fc6-118">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="b3fc6-118">PARAMETERS</span></span>

### <span data-ttu-id="b3fc6-119">-ID</span><span class="sxs-lookup"><span data-stu-id="b3fc6-119">-Id</span></span>

<span data-ttu-id="b3fc6-120">Anger, som en sträng mat ris, ID eller ID för de tids zoner som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="b3fc6-120">Specifies, as a string array, the ID or IDs of the time zones that this cmdlet gets.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Id
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b3fc6-121">– ListAvailable</span><span class="sxs-lookup"><span data-stu-id="b3fc6-121">-ListAvailable</span></span>

<span data-ttu-id="b3fc6-122">Anger att denna cmdlet hämtar alla tillgängliga tids zoner.</span><span class="sxs-lookup"><span data-stu-id="b3fc6-122">Indicates that this cmdlet gets all available time zones.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ListAvailable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b3fc6-123">-Name</span><span class="sxs-lookup"><span data-stu-id="b3fc6-123">-Name</span></span>

<span data-ttu-id="b3fc6-124">Anger, som en sträng mat ris, namn eller namn på de tids zoner som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="b3fc6-124">Specifies, as a string array, the name or names of the time zones that this cmdlet gets.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="b3fc6-125">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b3fc6-125">CommonParameters</span></span>

<span data-ttu-id="b3fc6-126">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b3fc6-126">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b3fc6-127">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b3fc6-127">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b3fc6-128">INDATA</span><span class="sxs-lookup"><span data-stu-id="b3fc6-128">INPUTS</span></span>

### <span data-ttu-id="b3fc6-129">System.String[]</span><span class="sxs-lookup"><span data-stu-id="b3fc6-129">System.String[]</span></span>

## <span data-ttu-id="b3fc6-130">UTDATA</span><span class="sxs-lookup"><span data-stu-id="b3fc6-130">OUTPUTS</span></span>

### <span data-ttu-id="b3fc6-131">System. TimeZoneInfo []</span><span class="sxs-lookup"><span data-stu-id="b3fc6-131">System.TimeZoneInfo[]</span></span>

## <span data-ttu-id="b3fc6-132">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="b3fc6-132">NOTES</span></span>

<span data-ttu-id="b3fc6-133">Den här cmdleten är endast tillgänglig på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="b3fc6-133">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="b3fc6-134">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="b3fc6-134">RELATED LINKS</span></span>

[<span data-ttu-id="b3fc6-135">Ange-TimeZone</span><span class="sxs-lookup"><span data-stu-id="b3fc6-135">Set-TimeZone</span></span>](Set-TimeZone.md)
