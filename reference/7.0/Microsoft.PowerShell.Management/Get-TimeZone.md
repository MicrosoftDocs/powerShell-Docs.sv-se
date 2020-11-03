---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-timezone?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TimeZone
ms.openlocfilehash: 4ed02426fbce279adc3f30af0c95b11966fe75a5
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262845"
---
# <span data-ttu-id="053fc-103">Get-TimeZone</span><span class="sxs-lookup"><span data-stu-id="053fc-103">Get-TimeZone</span></span>

## <span data-ttu-id="053fc-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="053fc-104">SYNOPSIS</span></span>
<span data-ttu-id="053fc-105">Hämtar den aktuella tids zonen eller en lista över tillgängliga tids zoner.</span><span class="sxs-lookup"><span data-stu-id="053fc-105">Gets the current time zone or a list of available time zones.</span></span>

## <span data-ttu-id="053fc-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="053fc-106">SYNTAX</span></span>

### <span data-ttu-id="053fc-107">Namn (standard)</span><span class="sxs-lookup"><span data-stu-id="053fc-107">Name (Default)</span></span>

```
Get-TimeZone [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="053fc-108">Id</span><span class="sxs-lookup"><span data-stu-id="053fc-108">Id</span></span>

```
Get-TimeZone -Id <String[]> [<CommonParameters>]
```

### <span data-ttu-id="053fc-109">ListAvailable</span><span class="sxs-lookup"><span data-stu-id="053fc-109">ListAvailable</span></span>

```
Get-TimeZone [-ListAvailable] [<CommonParameters>]
```

## <span data-ttu-id="053fc-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="053fc-110">DESCRIPTION</span></span>

<span data-ttu-id="053fc-111">Cmdleten **Get-timezone** hämtar den aktuella tids zonen eller en lista över tillgängliga tids zoner.</span><span class="sxs-lookup"><span data-stu-id="053fc-111">The **Get-TimeZone** cmdlet gets the current time zone or a list of available time zones.</span></span>

## <span data-ttu-id="053fc-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="053fc-112">EXAMPLES</span></span>

### <span data-ttu-id="053fc-113">Exempel 1: Hämta aktuell tidszon</span><span class="sxs-lookup"><span data-stu-id="053fc-113">Example 1: Get the current time zone</span></span>

```
PS C:\> Get-TimeZone
Pacific Standard Time
```

<span data-ttu-id="053fc-114">Det här kommandot hämtar den aktuella tids zonen.</span><span class="sxs-lookup"><span data-stu-id="053fc-114">This command gets the current time zone.</span></span>

### <span data-ttu-id="053fc-115">Exempel 2: Hämta tids zoner som matchar en angiven sträng</span><span class="sxs-lookup"><span data-stu-id="053fc-115">Example 2: Get time zones that match a specified string</span></span>

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

<span data-ttu-id="053fc-116">Det här kommandot hämtar alla tids zoner som matchar det angivna jokertecknet.</span><span class="sxs-lookup"><span data-stu-id="053fc-116">This command gets all time zones that match the specified wildcard.</span></span>

### <span data-ttu-id="053fc-117">Exempel 3: Hämta alla tillgängliga tids zoner</span><span class="sxs-lookup"><span data-stu-id="053fc-117">Example 3: Get all available time zones</span></span>

```
PS C:\> Get-TimeZone -ListAvailable
```

<span data-ttu-id="053fc-118">Det här kommandot hämtar alla tillgängliga tids zoner.</span><span class="sxs-lookup"><span data-stu-id="053fc-118">This command gets all available time zones.</span></span>

## <span data-ttu-id="053fc-119">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="053fc-119">PARAMETERS</span></span>

### <span data-ttu-id="053fc-120">-ID</span><span class="sxs-lookup"><span data-stu-id="053fc-120">-Id</span></span>

<span data-ttu-id="053fc-121">Anger, som en sträng mat ris, ID eller ID för de tids zoner som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="053fc-121">Specifies, as a string array, the ID or IDs of the time zones that this cmdlet gets.</span></span>

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

### <span data-ttu-id="053fc-122">– ListAvailable</span><span class="sxs-lookup"><span data-stu-id="053fc-122">-ListAvailable</span></span>

<span data-ttu-id="053fc-123">Anger att denna cmdlet hämtar alla tillgängliga tids zoner.</span><span class="sxs-lookup"><span data-stu-id="053fc-123">Indicates that this cmdlet gets all available time zones.</span></span>

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

### <span data-ttu-id="053fc-124">-Name</span><span class="sxs-lookup"><span data-stu-id="053fc-124">-Name</span></span>

<span data-ttu-id="053fc-125">Anger, som en sträng mat ris, namn eller namn på de tids zoner som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="053fc-125">Specifies, as a string array, the name or names of the time zones that this cmdlet gets.</span></span>

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

### <span data-ttu-id="053fc-126">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="053fc-126">CommonParameters</span></span>

<span data-ttu-id="053fc-127">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="053fc-127">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="053fc-128">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="053fc-128">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="053fc-129">INDATA</span><span class="sxs-lookup"><span data-stu-id="053fc-129">INPUTS</span></span>

### <span data-ttu-id="053fc-130">System.String[]</span><span class="sxs-lookup"><span data-stu-id="053fc-130">System.String[]</span></span>

## <span data-ttu-id="053fc-131">UTDATA</span><span class="sxs-lookup"><span data-stu-id="053fc-131">OUTPUTS</span></span>

### <span data-ttu-id="053fc-132">System. TimeZoneInfo []</span><span class="sxs-lookup"><span data-stu-id="053fc-132">System.TimeZoneInfo[]</span></span>

## <span data-ttu-id="053fc-133">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="053fc-133">NOTES</span></span>

## <span data-ttu-id="053fc-134">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="053fc-134">RELATED LINKS</span></span>

[<span data-ttu-id="053fc-135">Ange-TimeZone</span><span class="sxs-lookup"><span data-stu-id="053fc-135">Set-TimeZone</span></span>](Set-TimeZone.md)