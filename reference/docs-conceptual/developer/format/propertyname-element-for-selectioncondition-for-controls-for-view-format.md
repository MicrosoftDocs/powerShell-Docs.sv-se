---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName-element för SelectionCondition för Controls för View (format)
description: PropertyName-element för SelectionCondition för Controls för View (format)
ms.openlocfilehash: 7783e5a9b7f8ec3d3077d87778e9f77ffe858a7f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92665880"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="aa11c-103">PropertyName-element för SelectionCondition för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="aa11c-103">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="aa11c-104">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="aa11c-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="aa11c-105">När den här egenskapen finns eller när den utvärderas `true` , uppfylls villkoret och posten används.</span><span class="sxs-lookup"><span data-stu-id="aa11c-105">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="aa11c-106">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="aa11c-106">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="aa11c-107">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) styr element (format) styr element (format) styr element (format) kontroll element för Controls for View (format) CustomControl-element för kontroll för kontroller för View (format) CustomEntries-element för CustomControl för kontroller (format) CustomEntry-element för CustomEntries for Controls for View (format) EntrySelectedBy-element för CustomEntry for Controls for View (format) SelectionCondition-element for EntrySelectedBy for Controls for View (format) PropertyName-element för SelectionCondition för Controls for View (format)</span><span class="sxs-lookup"><span data-stu-id="aa11c-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="aa11c-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="aa11c-108">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="aa11c-109">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="aa11c-109">Attributes and Elements</span></span>

<span data-ttu-id="aa11c-110">I följande avsnitt beskrivs attribut, underordnade element och `PropertyName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="aa11c-110">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="aa11c-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="aa11c-111">Attributes</span></span>

<span data-ttu-id="aa11c-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="aa11c-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="aa11c-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="aa11c-113">Child Elements</span></span>

<span data-ttu-id="aa11c-114">Inga.</span><span class="sxs-lookup"><span data-stu-id="aa11c-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="aa11c-115">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="aa11c-115">Parent Elements</span></span>

|<span data-ttu-id="aa11c-116">Element</span><span class="sxs-lookup"><span data-stu-id="aa11c-116">Element</span></span>|<span data-ttu-id="aa11c-117">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="aa11c-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="aa11c-118">SelectionCondition-element för EntrySelectedBy för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="aa11c-118">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="aa11c-119">Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="aa11c-119">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="aa11c-120">Textvärde</span><span class="sxs-lookup"><span data-stu-id="aa11c-120">Text Value</span></span>

<span data-ttu-id="aa11c-121">Ange .NET-egenskaps namnet.</span><span class="sxs-lookup"><span data-stu-id="aa11c-121">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="aa11c-122">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="aa11c-122">Remarks</span></span>

<span data-ttu-id="aa11c-123">Urvals villkoret måste ange minst ett egenskaps namn eller ett skript, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="aa11c-123">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="aa11c-124">Mer information om hur urvals villkor kan användas finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="aa11c-124">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="aa11c-125">Se även</span><span class="sxs-lookup"><span data-stu-id="aa11c-125">See Also</span></span>

[<span data-ttu-id="aa11c-126">SelectionCondition-element för EntrySelectedBy för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="aa11c-126">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="aa11c-127">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="aa11c-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
