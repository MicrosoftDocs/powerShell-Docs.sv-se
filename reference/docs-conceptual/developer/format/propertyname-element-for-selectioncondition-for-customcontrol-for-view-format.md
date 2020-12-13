---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName-element för SelectionCondition för CustomControl för View (format)
description: PropertyName-element för SelectionCondition för CustomControl för View (format)
ms.openlocfilehash: 1dd325a58b29a0f13b1341559c2a7dfe251c6b36
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665863"
---
# <a name="propertyname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="c86de-103">PropertyName-element för SelectionCondition för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="c86de-103">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="c86de-104">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="c86de-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="c86de-105">När den här egenskapen finns eller när den utvärderas `true` , uppfylls villkoret och definitionen används.</span><span class="sxs-lookup"><span data-stu-id="c86de-105">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="c86de-106">Det här elementet används när du definierar en anpassad kontrol vy.</span><span class="sxs-lookup"><span data-stu-id="c86de-106">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="c86de-107">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) CustomControl-element för View (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för CustomControl för View (format) CustomItem-element för CustomEntry för CustomControl för View (format) EntrySelectedBy-element för CustomEntry för CustomControl för View (format) SelectionCondition-element för EntrySelectedBy för CustomControl för View (format) PropertyName-element för SelectionCondition för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="c86de-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c86de-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="c86de-108">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c86de-109">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="c86de-109">Attributes and Elements</span></span>

<span data-ttu-id="c86de-110">I följande avsnitt beskrivs attribut, underordnade element och `PropertyName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="c86de-110">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c86de-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="c86de-111">Attributes</span></span>

<span data-ttu-id="c86de-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="c86de-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c86de-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="c86de-113">Child Elements</span></span>

<span data-ttu-id="c86de-114">Inga.</span><span class="sxs-lookup"><span data-stu-id="c86de-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c86de-115">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="c86de-115">Parent Elements</span></span>

|<span data-ttu-id="c86de-116">Element</span><span class="sxs-lookup"><span data-stu-id="c86de-116">Element</span></span>|<span data-ttu-id="c86de-117">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c86de-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c86de-118">SelectionCondition-element för EntrySelectedBy för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="c86de-118">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="c86de-119">Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="c86de-119">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c86de-120">Textvärde</span><span class="sxs-lookup"><span data-stu-id="c86de-120">Text Value</span></span>

<span data-ttu-id="c86de-121">Ange .NET-egenskaps namnet.</span><span class="sxs-lookup"><span data-stu-id="c86de-121">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="c86de-122">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="c86de-122">Remarks</span></span>

<span data-ttu-id="c86de-123">Urvals villkoret måste ange minst ett egenskaps namn eller ett skript, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="c86de-123">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="c86de-124">Mer information om hur urvals villkor kan användas finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="c86de-124">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c86de-125">Se även</span><span class="sxs-lookup"><span data-stu-id="c86de-125">See Also</span></span>

[<span data-ttu-id="c86de-126">SelectionCondition-element för EntrySelectedBy för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="c86de-126">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="c86de-127">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="c86de-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
