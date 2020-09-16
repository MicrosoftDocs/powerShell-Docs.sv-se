---
title: PropertyName-element för SelectionCondition för GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 8ada9a8ca7fbfdba5b2fea1881b2670c56a71d4f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773087"
---
# <a name="propertyname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="348f5-102">PropertyName-element för SelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="348f5-102">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="348f5-103">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="348f5-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="348f5-104">När den här egenskapen finns eller när den utvärderas `true` , uppfylls villkoret och definitionen används.</span><span class="sxs-lookup"><span data-stu-id="348f5-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="348f5-105">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="348f5-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="348f5-106">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element for CustomControl for groupby (format) EntrySelectedBy-element för CustomEntry för groupby (format) SelectionCondition-element för</span><span class="sxs-lookup"><span data-stu-id="348f5-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="348f5-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="348f5-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="348f5-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="348f5-108">Attributes and Elements</span></span>

<span data-ttu-id="348f5-109">I följande avsnitt beskrivs attribut, underordnade element och `PropertyName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="348f5-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="348f5-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="348f5-110">Attributes</span></span>

<span data-ttu-id="348f5-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="348f5-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="348f5-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="348f5-112">Child Elements</span></span>

<span data-ttu-id="348f5-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="348f5-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="348f5-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="348f5-114">Parent Elements</span></span>

|<span data-ttu-id="348f5-115">Element</span><span class="sxs-lookup"><span data-stu-id="348f5-115">Element</span></span>|<span data-ttu-id="348f5-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="348f5-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="348f5-117">SelectionCondition-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="348f5-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="348f5-118">Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="348f5-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="348f5-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="348f5-119">Text Value</span></span>

<span data-ttu-id="348f5-120">Ange .NET-egenskaps namnet.</span><span class="sxs-lookup"><span data-stu-id="348f5-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="348f5-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="348f5-121">Remarks</span></span>

<span data-ttu-id="348f5-122">Urvals villkoret måste ange minst ett egenskaps namn eller ett skript, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="348f5-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="348f5-123">Mer information om hur urvals villkor kan användas finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="348f5-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="348f5-124">Se även</span><span class="sxs-lookup"><span data-stu-id="348f5-124">See Also</span></span>

[<span data-ttu-id="348f5-125">SelectionCondition-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="348f5-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="348f5-126">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="348f5-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
