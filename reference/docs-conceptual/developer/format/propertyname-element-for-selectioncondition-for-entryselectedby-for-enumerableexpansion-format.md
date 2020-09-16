---
title: PropertyName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c0081cb724ccaf1c04241aafa177880d7c0e5dbe
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783474"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="d720a-102">PropertyName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="d720a-102">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="d720a-103">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="d720a-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="d720a-104">När den här egenskapen finns eller när den utvärderas `true` , uppfylls villkoret och definitionen används.</span><span class="sxs-lookup"><span data-stu-id="d720a-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="d720a-105">Konfigurations element (format) DefaultSettings-element (format) EnumerableExpansions-element (format) EnumerableExpansion element (format) EntrySelectedBy-element för EnumerableExpansion (format) SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format) PropertyName-element för SelectionCondition för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="d720a-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d720a-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="d720a-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d720a-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="d720a-107">Attributes and Elements</span></span>

<span data-ttu-id="d720a-108">I följande avsnitt beskrivs attribut, underordnade element och `PropertyName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="d720a-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d720a-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="d720a-109">Attributes</span></span>

<span data-ttu-id="d720a-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="d720a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d720a-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="d720a-111">Child Elements</span></span>

<span data-ttu-id="d720a-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="d720a-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d720a-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="d720a-113">Parent Elements</span></span>

|<span data-ttu-id="d720a-114">Element</span><span class="sxs-lookup"><span data-stu-id="d720a-114">Element</span></span>|<span data-ttu-id="d720a-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d720a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d720a-116">SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="d720a-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="d720a-117">Definierar det villkor som måste finnas för att expandera samlings objekt i den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="d720a-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d720a-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="d720a-118">Text Value</span></span>

<span data-ttu-id="d720a-119">Ange .NET-egenskaps namnet.</span><span class="sxs-lookup"><span data-stu-id="d720a-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="d720a-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="d720a-120">Remarks</span></span>

<span data-ttu-id="d720a-121">Urvals villkoret måste innehålla minst ett egenskaps namn eller ett skript som ska utvärderas, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="d720a-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="d720a-122">Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d720a-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d720a-123">Se även</span><span class="sxs-lookup"><span data-stu-id="d720a-123">See Also</span></span>

[<span data-ttu-id="d720a-124">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="d720a-124">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="d720a-125">ScriptBlock-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="d720a-125">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="d720a-126">SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="d720a-126">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="d720a-127">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="d720a-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
