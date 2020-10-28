---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName-element för SelectionCondition för Controls för Configuration (format)
description: PropertyName-element för SelectionCondition för Controls för Configuration (format)
ms.openlocfilehash: 5e4368a9546307c5ff223ae42ecaa1d2872bc587
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92665965"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="e3100-103">PropertyName-element för SelectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="e3100-103">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="e3100-104">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="e3100-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="e3100-105">När den här egenskapen finns eller när den utvärderas `true` , uppfylls villkoret och posten används.</span><span class="sxs-lookup"><span data-stu-id="e3100-105">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="e3100-106">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="e3100-106">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="e3100-107">Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för Configuration (format) CustomEntry-elementet för CustomControl for Controls for Configuration (format) EntrySelectedBy-elementet för CustomEntry for Controls for Configuration (format) SelectionCondition element for EntrySelectedBy for CustomEntry for Configuration (format) PropertyName-element för SelectionCondition för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="e3100-107">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e3100-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="e3100-108">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e3100-109">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="e3100-109">Attributes and Elements</span></span>

<span data-ttu-id="e3100-110">I följande avsnitt beskrivs attribut, underordnade element och `PropertyName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="e3100-110">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e3100-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="e3100-111">Attributes</span></span>

<span data-ttu-id="e3100-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="e3100-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e3100-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="e3100-113">Child Elements</span></span>

<span data-ttu-id="e3100-114">Inga.</span><span class="sxs-lookup"><span data-stu-id="e3100-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e3100-115">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="e3100-115">Parent Elements</span></span>

|<span data-ttu-id="e3100-116">Element</span><span class="sxs-lookup"><span data-stu-id="e3100-116">Element</span></span>|<span data-ttu-id="e3100-117">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e3100-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e3100-118">SelectionCondition-element för EntrySelectedBy för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="e3100-118">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="e3100-119">Definierar ett villkor som måste finnas för att en gemensam kontroll definition ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="e3100-119">Defines a condition that must exist for a common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e3100-120">Textvärde</span><span class="sxs-lookup"><span data-stu-id="e3100-120">Text Value</span></span>

<span data-ttu-id="e3100-121">Ange .NET-egenskaps namnet.</span><span class="sxs-lookup"><span data-stu-id="e3100-121">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="e3100-122">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="e3100-122">Remarks</span></span>

<span data-ttu-id="e3100-123">Urvals villkoret måste ange minst ett egenskaps namn eller ett skript, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="e3100-123">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="e3100-124">Mer information om hur urvals villkor kan användas finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e3100-124">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e3100-125">Se även</span><span class="sxs-lookup"><span data-stu-id="e3100-125">See Also</span></span>

[<span data-ttu-id="e3100-126">SelectionCondition-element för EntrySelectedBy för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="e3100-126">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="e3100-127">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="e3100-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
