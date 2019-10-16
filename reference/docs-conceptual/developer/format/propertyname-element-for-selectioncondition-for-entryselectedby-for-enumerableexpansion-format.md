---
title: PropertyName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ae11924-0072-451e-bf70-c5ffb25dccc0
caps.latest.revision: 13
ms.openlocfilehash: 0c20512e660c8d2b61d063dbd7078b55b23efeb8
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354049"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="5b53c-102">PropertyName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="5b53c-102">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="5b53c-103">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="5b53c-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="5b53c-104">När den här egenskapen finns eller när den utvärderas till `true`, uppfylls villkoret och definitionen används.</span><span class="sxs-lookup"><span data-stu-id="5b53c-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="5b53c-105">Konfigurations element (format) DefaultSettings-element (format) EnumerableExpansions-element (format) EnumerableExpansion-element (format) EntrySelectedBy-element för EnumerableExpansion (format) SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format) PropertyName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="5b53c-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5b53c-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="5b53c-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5b53c-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="5b53c-107">Attributes and Elements</span></span>

<span data-ttu-id="5b53c-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="5b53c-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5b53c-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="5b53c-109">Attributes</span></span>

<span data-ttu-id="5b53c-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="5b53c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5b53c-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="5b53c-111">Child Elements</span></span>

<span data-ttu-id="5b53c-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="5b53c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5b53c-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="5b53c-113">Parent Elements</span></span>

|<span data-ttu-id="5b53c-114">Element</span><span class="sxs-lookup"><span data-stu-id="5b53c-114">Element</span></span>|<span data-ttu-id="5b53c-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b53c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5b53c-116">SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="5b53c-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="5b53c-117">Definierar det villkor som måste finnas för att expandera samlings objekt i den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="5b53c-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5b53c-118">Text värde</span><span class="sxs-lookup"><span data-stu-id="5b53c-118">Text Value</span></span>

<span data-ttu-id="5b53c-119">Ange .NET-egenskaps namnet.</span><span class="sxs-lookup"><span data-stu-id="5b53c-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="5b53c-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="5b53c-120">Remarks</span></span>

<span data-ttu-id="5b53c-121">Urvals villkoret måste innehålla minst ett egenskaps namn eller ett skript som ska utvärderas, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="5b53c-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="5b53c-122">Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="5b53c-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5b53c-123">Se även</span><span class="sxs-lookup"><span data-stu-id="5b53c-123">See Also</span></span>

[<span data-ttu-id="5b53c-124">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="5b53c-124">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="5b53c-125">Script block-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="5b53c-125">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="5b53c-126">SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="5b53c-126">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="5b53c-127">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="5b53c-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
