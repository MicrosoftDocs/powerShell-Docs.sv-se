---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-uptime?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Uptime
ms.openlocfilehash: d06dbc66d9674b59df4d75f8ae333d4fe24aa7eb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264345"
---
# <span data-ttu-id="964cb-102">Get-Uptime</span><span class="sxs-lookup"><span data-stu-id="964cb-102">Get-Uptime</span></span>

## <span data-ttu-id="964cb-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="964cb-103">SYNOPSIS</span></span>
<span data-ttu-id="964cb-104">Hämta **TimeSpan** sedan senaste start.</span><span class="sxs-lookup"><span data-stu-id="964cb-104">Get the **TimeSpan** since last boot.</span></span>

## <span data-ttu-id="964cb-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="964cb-105">SYNTAX</span></span>

### <span data-ttu-id="964cb-106">TimeSpan (standard)</span><span class="sxs-lookup"><span data-stu-id="964cb-106">Timespan (Default)</span></span>

```
Get-Uptime [<CommonParameters>]
```

### <span data-ttu-id="964cb-107">Starta</span><span class="sxs-lookup"><span data-stu-id="964cb-107">Since</span></span>

```
Get-Uptime [-Since] [<CommonParameters>]
```

## <span data-ttu-id="964cb-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="964cb-108">DESCRIPTION</span></span>

<span data-ttu-id="964cb-109">Den här cmdleten returnerar den tid som gått sedan den senaste starten av operativ systemet.</span><span class="sxs-lookup"><span data-stu-id="964cb-109">This cmdlet returns the time elapsed since the last boot of the operating system.</span></span>

<span data-ttu-id="964cb-110">`Get-Uptime`Cmdleten introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="964cb-110">The `Get-Uptime` cmdlet was introduced in PowerShell 6.0.</span></span>

## <span data-ttu-id="964cb-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="964cb-111">EXAMPLES</span></span>

### <span data-ttu-id="964cb-112">Exempel 1 – Visa tid sedan senaste start</span><span class="sxs-lookup"><span data-stu-id="964cb-112">Example 1 - Show time since last boot</span></span>

```powershell
Get-Uptime
```

```Output
Days              : 9
Hours             : 0
Minutes           : 9
Seconds           : 45
Milliseconds      : 0
Ticks             : 7781850000000
TotalDays         : 9.00677083333333
TotalHours        : 216.1625
TotalMinutes      : 12969.75
TotalSeconds      : 778185
TotalMilliseconds : 778185000
```

### <span data-ttu-id="964cb-113">Exempel 2 – Visa tiden för den senaste starten</span><span class="sxs-lookup"><span data-stu-id="964cb-113">Example 2 - Show the time of the last boot</span></span>

```powershell
Get-Uptime -Since
```

```Output
Tuesday, June 18, 2019 2:34:56 PM
```

## <span data-ttu-id="964cb-114">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="964cb-114">PARAMETERS</span></span>

### <span data-ttu-id="964cb-115">-Sedan</span><span class="sxs-lookup"><span data-stu-id="964cb-115">-Since</span></span>

<span data-ttu-id="964cb-116">Orsaka att cmdleten returnerar ett **datetime** -objekt som representerar den senaste gången operativ systemet startades.</span><span class="sxs-lookup"><span data-stu-id="964cb-116">Cause the cmdlet to return a **DateTime** object representing the last time that the operating system was booted.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Since
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="964cb-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="964cb-117">CommonParameters</span></span>

<span data-ttu-id="964cb-118">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="964cb-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="964cb-119">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="964cb-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="964cb-120">INDATA</span><span class="sxs-lookup"><span data-stu-id="964cb-120">INPUTS</span></span>

### <span data-ttu-id="964cb-121">Inget</span><span class="sxs-lookup"><span data-stu-id="964cb-121">None</span></span>

## <span data-ttu-id="964cb-122">UTDATA</span><span class="sxs-lookup"><span data-stu-id="964cb-122">OUTPUTS</span></span>

### <span data-ttu-id="964cb-123">System. TimeSpan</span><span class="sxs-lookup"><span data-stu-id="964cb-123">System.TimeSpan</span></span>

<span data-ttu-id="964cb-124">Det här är standard retur typen när inga parametrar används.</span><span class="sxs-lookup"><span data-stu-id="964cb-124">This is the default return type when no parameters are used.</span></span>

### <span data-ttu-id="964cb-125">System. DateTime</span><span class="sxs-lookup"><span data-stu-id="964cb-125">System.DateTime</span></span>

<span data-ttu-id="964cb-126">Den här typen returneras när parametern **sedan** används.</span><span class="sxs-lookup"><span data-stu-id="964cb-126">This type is returned when using the **Since** parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="964cb-127">Om snabb start av Windows har Aktiver ATS, uppdaterar Windows inte värdet som lagras i **LastBootUpTime**.</span><span class="sxs-lookup"><span data-stu-id="964cb-127">If Windows fast startup is enabled, Windows does not update the value stored in **LastBootUpTime**.</span></span> <span data-ttu-id="964cb-128">Om du vill inaktivera snabb start kör du följande kommando: `Powercfg -h off` .</span><span class="sxs-lookup"><span data-stu-id="964cb-128">To disable fast startup, run the following command: `Powercfg -h off`.</span></span>
>
> <span data-ttu-id="964cb-129">Mer information om snabb start i Windows finns i avsnittet [Skilj snabb starten från Väcknings från vilo läge](/windows-hardware/drivers/kernel/distinguishing-fast-startup-from-wake-from-hibernation).</span><span class="sxs-lookup"><span data-stu-id="964cb-129">For more information about Windows fast startup, see [Distinguishing Fast Startup from Wake-from-Hibernation](/windows-hardware/drivers/kernel/distinguishing-fast-startup-from-wake-from-hibernation).</span></span>

## <span data-ttu-id="964cb-130">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="964cb-130">NOTES</span></span>

<span data-ttu-id="964cb-131">I Windows är det returnerade värdet detsamma som egenskapen **LastBootUpTime** för klassen **Win32_OperatingSystem** i WMI.</span><span class="sxs-lookup"><span data-stu-id="964cb-131">On Windows, the value returned is the same as the **LastBootUpTime** property of the **Win32_OperatingSystem** class in WMI.</span></span>

## <span data-ttu-id="964cb-132">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="964cb-132">RELATED LINKS</span></span>

[<span data-ttu-id="964cb-133">Win32_OperatingSystem</span><span class="sxs-lookup"><span data-stu-id="964cb-133">Win32_OperatingSystem</span></span>](/windows/win32/cimwin32prov/win32-operatingsystem#properties)

