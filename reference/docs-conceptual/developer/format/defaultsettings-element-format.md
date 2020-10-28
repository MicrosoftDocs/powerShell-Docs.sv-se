---
ms.date: 09/13/2016
ms.topic: reference
title: DefaultSettings-element (format)
description: DefaultSettings-element (format)
ms.openlocfilehash: 1c2055b38a416fe2d75fa20c6c87e92d9eed4285
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666730"
---
# <a name="defaultsettings-element-format"></a><span data-ttu-id="12ecd-103">DefaultSettings-element (format)</span><span class="sxs-lookup"><span data-stu-id="12ecd-103">DefaultSettings Element (Format)</span></span>

<span data-ttu-id="12ecd-104">Definierar vanliga inställningar som gäller för alla vyer i formaterings filen.</span><span class="sxs-lookup"><span data-stu-id="12ecd-104">Defines common settings that apply to all the views of the formatting file.</span></span> <span data-ttu-id="12ecd-105">Vanliga inställningar är att visa fel, figursätta text i tabeller, definiera hur samlingar expanderas och mycket mer.</span><span class="sxs-lookup"><span data-stu-id="12ecd-105">Common settings include displaying errors, wrapping text in tables, defining how collections are expanded, and more.</span></span>

<span data-ttu-id="12ecd-106">Konfigurations element (format) DefaultSettings-element (format)</span><span class="sxs-lookup"><span data-stu-id="12ecd-106">Configuration Element (Format) DefaultSettings Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="12ecd-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="12ecd-107">Syntax</span></span>

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="12ecd-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="12ecd-108">Attributes and Elements</span></span>

<span data-ttu-id="12ecd-109">I följande avsnitt beskrivs attribut, underordnade element och `DefaultSettings` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="12ecd-109">The following sections describe attributes, child elements, and the parent element of the `DefaultSettings` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="12ecd-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="12ecd-110">Attributes</span></span>

<span data-ttu-id="12ecd-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="12ecd-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="12ecd-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="12ecd-112">Child Elements</span></span>

|<span data-ttu-id="12ecd-113">Element</span><span class="sxs-lookup"><span data-stu-id="12ecd-113">Element</span></span>|<span data-ttu-id="12ecd-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="12ecd-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="12ecd-115">DisplayError-element (format)</span><span class="sxs-lookup"><span data-stu-id="12ecd-115">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)|<span data-ttu-id="12ecd-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="12ecd-116">Optional element.</span></span><br /><br /> <span data-ttu-id="12ecd-117">Anger att strängen #ERR visas när ett fel inträffar när en del av data visas.</span><span class="sxs-lookup"><span data-stu-id="12ecd-117">Specifies that the string #ERR is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="12ecd-118">EnumerableExpansions-element (format)</span><span class="sxs-lookup"><span data-stu-id="12ecd-118">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="12ecd-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="12ecd-119">Optional element.</span></span><br /><br /> <span data-ttu-id="12ecd-120">Definierar de olika sätt som .NET-objekt expanderas när de visas i en vy.</span><span class="sxs-lookup"><span data-stu-id="12ecd-120">Defines the different ways that .NET objects are expanded when they are displayed in a view.</span></span>|
|[<span data-ttu-id="12ecd-121">PropertyCountForTable (format)</span><span class="sxs-lookup"><span data-stu-id="12ecd-121">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)|<span data-ttu-id="12ecd-122">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="12ecd-122">Optional element.</span></span><br /><br /> <span data-ttu-id="12ecd-123">Anger det minsta antalet egenskaper som ett objekt måste ha för att visa objektet i en tabellvy.</span><span class="sxs-lookup"><span data-stu-id="12ecd-123">Specifies the minimum number of properties that an object must have to display the object in a table view.</span></span>|
|[<span data-ttu-id="12ecd-124">ShowError-element (format)</span><span class="sxs-lookup"><span data-stu-id="12ecd-124">ShowError Element (Format)</span></span>](./showerror-element-format.md)|<span data-ttu-id="12ecd-125">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="12ecd-125">Optional element.</span></span><br /><br /> <span data-ttu-id="12ecd-126">Anger att den fullständiga fel posten visas när ett fel inträffar när en del av data visas.</span><span class="sxs-lookup"><span data-stu-id="12ecd-126">Specifies that the full error record is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="12ecd-127">WrapTables-element (format)</span><span class="sxs-lookup"><span data-stu-id="12ecd-127">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)|<span data-ttu-id="12ecd-128">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="12ecd-128">Optional element.</span></span><br /><br /> <span data-ttu-id="12ecd-129">Anger att data i en tabell flyttas till nästa rad om den inte passar in i kolumnens bredd.</span><span class="sxs-lookup"><span data-stu-id="12ecd-129">Specifies that data in a table is moved to the next line if it does not fit into the width of the column.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="12ecd-130">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="12ecd-130">Parent Elements</span></span>

|<span data-ttu-id="12ecd-131">Element</span><span class="sxs-lookup"><span data-stu-id="12ecd-131">Element</span></span>|<span data-ttu-id="12ecd-132">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="12ecd-132">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="12ecd-133">Konfigurations element</span><span class="sxs-lookup"><span data-stu-id="12ecd-133">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="12ecd-134">Representerar det översta elementet i en textfil.</span><span class="sxs-lookup"><span data-stu-id="12ecd-134">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="12ecd-135">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="12ecd-135">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="12ecd-136">Se även</span><span class="sxs-lookup"><span data-stu-id="12ecd-136">See Also</span></span>

[<span data-ttu-id="12ecd-137">Konfigurations element</span><span class="sxs-lookup"><span data-stu-id="12ecd-137">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="12ecd-138">DisplayError-element (format)</span><span class="sxs-lookup"><span data-stu-id="12ecd-138">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)

[<span data-ttu-id="12ecd-139">EnumerableExpansions-element (format)</span><span class="sxs-lookup"><span data-stu-id="12ecd-139">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)

[<span data-ttu-id="12ecd-140">PropertyCountForTable (format)</span><span class="sxs-lookup"><span data-stu-id="12ecd-140">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)

[<span data-ttu-id="12ecd-141">ShowError-element (format)</span><span class="sxs-lookup"><span data-stu-id="12ecd-141">ShowError Element (Format)</span></span>](./showerror-element-format.md)

[<span data-ttu-id="12ecd-142">WrapTables-element (format)</span><span class="sxs-lookup"><span data-stu-id="12ecd-142">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)

[<span data-ttu-id="12ecd-143">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="12ecd-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
