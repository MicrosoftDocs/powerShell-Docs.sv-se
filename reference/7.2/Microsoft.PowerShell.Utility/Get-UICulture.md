---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-uiculture?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-UICulture
ms.openlocfilehash: 4bd912db3f86ffa8b495faf3e62259f207340938
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709763"
---
# <span data-ttu-id="1dbdb-102">Get-UICulture</span><span class="sxs-lookup"><span data-stu-id="1dbdb-102">Get-UICulture</span></span>

## <span data-ttu-id="1dbdb-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="1dbdb-103">SYNOPSIS</span></span>
<span data-ttu-id="1dbdb-104">Hämtar de aktuella inställningarna för användar gränssnitts kulturen i operativ systemet.</span><span class="sxs-lookup"><span data-stu-id="1dbdb-104">Gets the current UI culture settings in the operating system.</span></span>

## <span data-ttu-id="1dbdb-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1dbdb-105">SYNTAX</span></span>

```
Get-UICulture [<CommonParameters>]
```

## <span data-ttu-id="1dbdb-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="1dbdb-106">DESCRIPTION</span></span>

<span data-ttu-id="1dbdb-107">`Get-UICulture`Cmdleten hämtar information om de aktuella användar gränssnittets inställningar för användar gränssnitt (UI) för Windows.</span><span class="sxs-lookup"><span data-stu-id="1dbdb-107">The `Get-UICulture` cmdlet gets information about the current user interface (UI) culture settings for Windows.</span></span>
<span data-ttu-id="1dbdb-108">ANVÄNDAR gränssnittets kultur avgör vilka text strängar som används för gränssnitts element, till exempel menyer och meddelanden.</span><span class="sxs-lookup"><span data-stu-id="1dbdb-108">The UI culture determines which text strings are used for user interface elements, such as menus and messages.</span></span>

<span data-ttu-id="1dbdb-109">Du kan också använda `Get-Culture` cmdleten, som hämtar den aktuella kulturen i systemet.</span><span class="sxs-lookup"><span data-stu-id="1dbdb-109">You can also use the `Get-Culture` cmdlet, which gets the current culture on the system.</span></span>
<span data-ttu-id="1dbdb-110">Kulturen bestämmer visnings formatet för objekt som tal, valuta och datum.</span><span class="sxs-lookup"><span data-stu-id="1dbdb-110">The culture determines the display format of items such as numbers, currency, and dates.</span></span>

## <span data-ttu-id="1dbdb-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="1dbdb-111">EXAMPLES</span></span>

### <span data-ttu-id="1dbdb-112">Exempel 1: Hämta UI-kulturen</span><span class="sxs-lookup"><span data-stu-id="1dbdb-112">Example 1: Get the UI culture</span></span>

```powershell
Get-UICulture
```

<span data-ttu-id="1dbdb-113">Det här kommandot hämtar den aktuella kultur informationen för användar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="1dbdb-113">This command gets the current UI culture information.</span></span>

### <span data-ttu-id="1dbdb-114">Exempel 2: Hämta UI-kulturen och formatera resultaten</span><span class="sxs-lookup"><span data-stu-id="1dbdb-114">Example 2: Get the UI culture and format the results</span></span>

```powershell
Get-UICulture | Format-List *
```

<span data-ttu-id="1dbdb-115">Det här kommandot visar värdena för alla egenskaper för den aktuella UI-kulturen i en lista.</span><span class="sxs-lookup"><span data-stu-id="1dbdb-115">This command displays the values of all of the properties of the current UI culture in a list.</span></span>

### <span data-ttu-id="1dbdb-116">Exempel 3: Hämta värdet för kalender egenskapen</span><span class="sxs-lookup"><span data-stu-id="1dbdb-116">Example 3: Get the value of the Calendar property</span></span>

```powershell
(Get-UICulture).Calendar
```

<span data-ttu-id="1dbdb-117">Det här kommandot visar de aktuella värdena för **kalender** egenskapen för den aktuella UI-kulturen.</span><span class="sxs-lookup"><span data-stu-id="1dbdb-117">This command displays the current values for the **Calendar** property of the current UI culture.</span></span>
<span data-ttu-id="1dbdb-118">Kalendern är bara en egenskap för användar gränssnitts kulturen.</span><span class="sxs-lookup"><span data-stu-id="1dbdb-118">Calendar is just one property of UI culture.</span></span>
<span data-ttu-id="1dbdb-119">Om du vill se alla egenskaper skriver du `Get-UICulture | Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="1dbdb-119">To see all of the properties, type `Get-UICulture | Get-Member`.</span></span>

### <span data-ttu-id="1dbdb-120">Exempel 4: Hämta kort datum mönster</span><span class="sxs-lookup"><span data-stu-id="1dbdb-120">Example 4: Get the short date pattern</span></span>

```powershell
(Get-UICulture).DateTimeFormat.ShortDatePattern
```

<span data-ttu-id="1dbdb-121">Det här kommandot visar kort datum mönstret för den aktuella kulturen i användar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="1dbdb-121">This command displays the short date pattern for the current UI culture.</span></span>
<span data-ttu-id="1dbdb-122">Om du vill se alla subegenskaper för **DateTimeFormat** -egenskapen för användar gränssnitts kulturen skriver du `(Get-UICulture).DateTimeFormat | gm` .</span><span class="sxs-lookup"><span data-stu-id="1dbdb-122">To see all of the subproperties of the **DateTimeFormat** property of the UI culture, type `(Get-UICulture).DateTimeFormat | gm`.</span></span>

## <span data-ttu-id="1dbdb-123">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="1dbdb-123">PARAMETERS</span></span>

### <span data-ttu-id="1dbdb-124">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1dbdb-124">CommonParameters</span></span>

<span data-ttu-id="1dbdb-125">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1dbdb-125">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1dbdb-126">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="1dbdb-126">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="1dbdb-127">INDATA</span><span class="sxs-lookup"><span data-stu-id="1dbdb-127">INPUTS</span></span>

### <span data-ttu-id="1dbdb-128">Inga</span><span class="sxs-lookup"><span data-stu-id="1dbdb-128">None</span></span>

<span data-ttu-id="1dbdb-129">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1dbdb-129">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="1dbdb-130">UTDATA</span><span class="sxs-lookup"><span data-stu-id="1dbdb-130">OUTPUTS</span></span>

### <span data-ttu-id="1dbdb-131">System. globalisering. CultureInfo, Microsoft. PowerShell. VistaCultureInfo</span><span class="sxs-lookup"><span data-stu-id="1dbdb-131">System.Globalization.CultureInfo, Microsoft.PowerShell.VistaCultureInfo</span></span>

<span data-ttu-id="1dbdb-132">`Get-UICulture` Returnerar ett objekt som representerar den aktuella kulturen för användar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="1dbdb-132">`Get-UICulture` returns an object that represents the current UI culture.</span></span>
<span data-ttu-id="1dbdb-133">I Windows PowerShell 3,0 returnerar den ett **CultureInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="1dbdb-133">In Windows PowerShell 3.0, it returns a **CultureInfo** object.</span></span>
<span data-ttu-id="1dbdb-134">I Windows PowerShell 2,0 returnerar den ett **VistaCultureInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="1dbdb-134">In Windows PowerShell 2.0, it returns a **VistaCultureInfo** object.</span></span>

## <span data-ttu-id="1dbdb-135">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="1dbdb-135">NOTES</span></span>

- <span data-ttu-id="1dbdb-136">Du kan också använda `$PsCulture` `$PsUICulture` variablerna och.</span><span class="sxs-lookup"><span data-stu-id="1dbdb-136">You can also use the `$PsCulture` and `$PsUICulture` variables.</span></span> <span data-ttu-id="1dbdb-137">`$PsCulture`Variabeln lagrar namnet på den aktuella kulturen och `$PsUICulture` variabeln lagrar namnet på den aktuella kulturen för användar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="1dbdb-137">The `$PsCulture` variable stores the name of the current culture, and the `$PsUICulture` variable stores the name of the current UI culture.</span></span>

## <span data-ttu-id="1dbdb-138">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="1dbdb-138">RELATED LINKS</span></span>

