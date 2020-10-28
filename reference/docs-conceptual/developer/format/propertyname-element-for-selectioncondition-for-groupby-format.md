---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName-element för SelectionCondition för GroupBy (format)
description: PropertyName-element för SelectionCondition för GroupBy (format)
ms.openlocfilehash: b89fead6185c88ca03956dc265135833696b91d7
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92665676"
---
# <a name="propertyname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="e07f1-103">PropertyName-element för SelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="e07f1-103">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="e07f1-104">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="e07f1-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="e07f1-105">När den här egenskapen finns eller när den utvärderas `true` , uppfylls villkoret och definitionen används.</span><span class="sxs-lookup"><span data-stu-id="e07f1-105">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="e07f1-106">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="e07f1-106">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="e07f1-107">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element for CustomControl for groupby (format) EntrySelectedBy-element för CustomEntry för groupby (format) SelectionCondition-element för</span><span class="sxs-lookup"><span data-stu-id="e07f1-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e07f1-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="e07f1-108">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e07f1-109">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="e07f1-109">Attributes and Elements</span></span>

<span data-ttu-id="e07f1-110">I följande avsnitt beskrivs attribut, underordnade element och `PropertyName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="e07f1-110">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e07f1-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="e07f1-111">Attributes</span></span>

<span data-ttu-id="e07f1-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="e07f1-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e07f1-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="e07f1-113">Child Elements</span></span>

<span data-ttu-id="e07f1-114">Inga.</span><span class="sxs-lookup"><span data-stu-id="e07f1-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e07f1-115">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="e07f1-115">Parent Elements</span></span>

|<span data-ttu-id="e07f1-116">Element</span><span class="sxs-lookup"><span data-stu-id="e07f1-116">Element</span></span>|<span data-ttu-id="e07f1-117">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e07f1-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e07f1-118">SelectionCondition-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="e07f1-118">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="e07f1-119">Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="e07f1-119">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e07f1-120">Textvärde</span><span class="sxs-lookup"><span data-stu-id="e07f1-120">Text Value</span></span>

<span data-ttu-id="e07f1-121">Ange .NET-egenskaps namnet.</span><span class="sxs-lookup"><span data-stu-id="e07f1-121">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="e07f1-122">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="e07f1-122">Remarks</span></span>

<span data-ttu-id="e07f1-123">Urvals villkoret måste ange minst ett egenskaps namn eller ett skript, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="e07f1-123">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="e07f1-124">Mer information om hur urvals villkor kan användas finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e07f1-124">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e07f1-125">Se även</span><span class="sxs-lookup"><span data-stu-id="e07f1-125">See Also</span></span>

[<span data-ttu-id="e07f1-126">SelectionCondition-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="e07f1-126">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="e07f1-127">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="e07f1-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
