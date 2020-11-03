---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-uiculture?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-UICulture
ms.openlocfilehash: cd5bbcae124b1c24438d2821c4da9d71a22d38a2
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/02/2020
ms.locfileid: "93261619"
---
# <span data-ttu-id="c3ba3-103">Get-UICulture</span><span class="sxs-lookup"><span data-stu-id="c3ba3-103">Get-UICulture</span></span>

## <span data-ttu-id="c3ba3-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="c3ba3-104">SYNOPSIS</span></span>
<span data-ttu-id="c3ba3-105">Hämtar de aktuella inställningarna för användar gränssnitts kulturen i operativ systemet.</span><span class="sxs-lookup"><span data-stu-id="c3ba3-105">Gets the current UI culture settings in the operating system.</span></span>

## <span data-ttu-id="c3ba3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c3ba3-106">SYNTAX</span></span>

```
Get-UICulture [<CommonParameters>]
```

## <span data-ttu-id="c3ba3-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="c3ba3-107">DESCRIPTION</span></span>

<span data-ttu-id="c3ba3-108">`Get-UICulture`Cmdleten hämtar information om de aktuella användar gränssnittets inställningar för användar gränssnitt (UI) för Windows.</span><span class="sxs-lookup"><span data-stu-id="c3ba3-108">The `Get-UICulture` cmdlet gets information about the current user interface (UI) culture settings for Windows.</span></span>
<span data-ttu-id="c3ba3-109">ANVÄNDAR gränssnittets kultur avgör vilka text strängar som används för gränssnitts element, till exempel menyer och meddelanden.</span><span class="sxs-lookup"><span data-stu-id="c3ba3-109">The UI culture determines which text strings are used for user interface elements, such as menus and messages.</span></span>

<span data-ttu-id="c3ba3-110">Du kan också använda `Get-Culture` cmdleten, som hämtar den aktuella kulturen i systemet.</span><span class="sxs-lookup"><span data-stu-id="c3ba3-110">You can also use the `Get-Culture` cmdlet, which gets the current culture on the system.</span></span>
<span data-ttu-id="c3ba3-111">Kulturen bestämmer visnings formatet för objekt som tal, valuta och datum.</span><span class="sxs-lookup"><span data-stu-id="c3ba3-111">The culture determines the display format of items such as numbers, currency, and dates.</span></span>

## <span data-ttu-id="c3ba3-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="c3ba3-112">EXAMPLES</span></span>

### <span data-ttu-id="c3ba3-113">Exempel 1: Hämta UI-kulturen</span><span class="sxs-lookup"><span data-stu-id="c3ba3-113">Example 1: Get the UI culture</span></span>

```powershell
Get-UICulture
```

<span data-ttu-id="c3ba3-114">Det här kommandot hämtar den aktuella kultur informationen för användar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="c3ba3-114">This command gets the current UI culture information.</span></span>

### <span data-ttu-id="c3ba3-115">Exempel 2: Hämta UI-kulturen och formatera resultaten</span><span class="sxs-lookup"><span data-stu-id="c3ba3-115">Example 2: Get the UI culture and format the results</span></span>

```powershell
Get-UICulture | Format-List *
```

<span data-ttu-id="c3ba3-116">Det här kommandot visar värdena för alla egenskaper för den aktuella UI-kulturen i en lista.</span><span class="sxs-lookup"><span data-stu-id="c3ba3-116">This command displays the values of all of the properties of the current UI culture in a list.</span></span>

### <span data-ttu-id="c3ba3-117">Exempel 3: Hämta värdet för kalender egenskapen</span><span class="sxs-lookup"><span data-stu-id="c3ba3-117">Example 3: Get the value of the Calendar property</span></span>

```powershell
(Get-UICulture).Calendar
```

<span data-ttu-id="c3ba3-118">Det här kommandot visar de aktuella värdena för **kalender** egenskapen för den aktuella UI-kulturen.</span><span class="sxs-lookup"><span data-stu-id="c3ba3-118">This command displays the current values for the **Calendar** property of the current UI culture.</span></span>
<span data-ttu-id="c3ba3-119">Kalendern är bara en egenskap för användar gränssnitts kulturen.</span><span class="sxs-lookup"><span data-stu-id="c3ba3-119">Calendar is just one property of UI culture.</span></span>
<span data-ttu-id="c3ba3-120">Om du vill se alla egenskaper skriver du `Get-UICulture | Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="c3ba3-120">To see all of the properties, type `Get-UICulture | Get-Member`.</span></span>

### <span data-ttu-id="c3ba3-121">Exempel 4: Hämta kort datum mönster</span><span class="sxs-lookup"><span data-stu-id="c3ba3-121">Example 4: Get the short date pattern</span></span>

```powershell
(Get-UICulture).DateTimeFormat.ShortDatePattern
```

<span data-ttu-id="c3ba3-122">Det här kommandot visar kort datum mönstret för den aktuella kulturen i användar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="c3ba3-122">This command displays the short date pattern for the current UI culture.</span></span>
<span data-ttu-id="c3ba3-123">Om du vill se alla subegenskaper för **DateTimeFormat** -egenskapen för användar gränssnitts kulturen skriver du `(Get-UICulture).DateTimeFormat | gm` .</span><span class="sxs-lookup"><span data-stu-id="c3ba3-123">To see all of the subproperties of the **DateTimeFormat** property of the UI culture, type `(Get-UICulture).DateTimeFormat | gm`.</span></span>

## <span data-ttu-id="c3ba3-124">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="c3ba3-124">PARAMETERS</span></span>

### <span data-ttu-id="c3ba3-125">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c3ba3-125">CommonParameters</span></span>

<span data-ttu-id="c3ba3-126">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c3ba3-126">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c3ba3-127">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="c3ba3-127">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="c3ba3-128">INDATA</span><span class="sxs-lookup"><span data-stu-id="c3ba3-128">INPUTS</span></span>

### <span data-ttu-id="c3ba3-129">Inget</span><span class="sxs-lookup"><span data-stu-id="c3ba3-129">None</span></span>

<span data-ttu-id="c3ba3-130">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c3ba3-130">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="c3ba3-131">UTDATA</span><span class="sxs-lookup"><span data-stu-id="c3ba3-131">OUTPUTS</span></span>

### <span data-ttu-id="c3ba3-132">System. globalisering. CultureInfo, Microsoft. PowerShell. VistaCultureInfo</span><span class="sxs-lookup"><span data-stu-id="c3ba3-132">System.Globalization.CultureInfo, Microsoft.PowerShell.VistaCultureInfo</span></span>

<span data-ttu-id="c3ba3-133">`Get-UICulture` Returnerar ett objekt som representerar den aktuella kulturen för användar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="c3ba3-133">`Get-UICulture` returns an object that represents the current UI culture.</span></span>
<span data-ttu-id="c3ba3-134">I Windows PowerShell 3,0 returnerar den ett **CultureInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="c3ba3-134">In Windows PowerShell 3.0, it returns a **CultureInfo** object.</span></span>
<span data-ttu-id="c3ba3-135">I Windows PowerShell 2,0 returnerar den ett **VistaCultureInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="c3ba3-135">In Windows PowerShell 2.0, it returns a **VistaCultureInfo** object.</span></span>

## <span data-ttu-id="c3ba3-136">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="c3ba3-136">NOTES</span></span>

- <span data-ttu-id="c3ba3-137">Du kan också använda `$PsCulture` `$PsUICulture` variablerna och.</span><span class="sxs-lookup"><span data-stu-id="c3ba3-137">You can also use the `$PsCulture` and `$PsUICulture` variables.</span></span> <span data-ttu-id="c3ba3-138">`$PsCulture`Variabeln lagrar namnet på den aktuella kulturen och `$PsUICulture` variabeln lagrar namnet på den aktuella kulturen för användar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="c3ba3-138">The `$PsCulture` variable stores the name of the current culture, and the `$PsUICulture` variable stores the name of the current UI culture.</span></span>

## <span data-ttu-id="c3ba3-139">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="c3ba3-139">RELATED LINKS</span></span>
