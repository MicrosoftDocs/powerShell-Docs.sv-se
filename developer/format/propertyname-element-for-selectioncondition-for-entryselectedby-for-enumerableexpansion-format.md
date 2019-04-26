---
title: PropertyName-Element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ae11924-0072-451e-bf70-c5ffb25dccc0
caps.latest.revision: 13
ms.openlocfilehash: 0c20512e660c8d2b61d063dbd7078b55b23efeb8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064960"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="cd94c-102">PropertyName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="cd94c-102">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="cd94c-103">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="cd94c-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="cd94c-104">När den här egenskapen finns eller att inventera till `true`villkoret uppfylls och definitionen används.</span><span class="sxs-lookup"><span data-stu-id="cd94c-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="cd94c-105">Elementet (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy konfigurationselement för EnumerableExpansion (Format) SelectionCondition elementet för EntrySelectedBy för EnumerableExpansion (Format) PropertyName Element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="cd94c-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cd94c-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="cd94c-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cd94c-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="cd94c-107">Attributes and Elements</span></span>

<span data-ttu-id="cd94c-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `PropertyName` element.</span><span class="sxs-lookup"><span data-stu-id="cd94c-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cd94c-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="cd94c-109">Attributes</span></span>

<span data-ttu-id="cd94c-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="cd94c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cd94c-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="cd94c-111">Child Elements</span></span>

<span data-ttu-id="cd94c-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="cd94c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cd94c-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="cd94c-113">Parent Elements</span></span>

|<span data-ttu-id="cd94c-114">Element</span><span class="sxs-lookup"><span data-stu-id="cd94c-114">Element</span></span>|<span data-ttu-id="cd94c-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="cd94c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cd94c-116">SelectionCondition Element för EntrySelectedBy för EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="cd94c-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="cd94c-117">Definierar de villkor som måste finnas för att expandera samlingen objekt av den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="cd94c-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="cd94c-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="cd94c-118">Text Value</span></span>

<span data-ttu-id="cd94c-119">Ange namnet på .NET-egenskapen.</span><span class="sxs-lookup"><span data-stu-id="cd94c-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="cd94c-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="cd94c-120">Remarks</span></span>

<span data-ttu-id="cd94c-121">Urvalsvillkoret måste ange minst en egenskapsnamn eller ett skript för att utvärdera, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="cd94c-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="cd94c-122">Läs mer om hur du använder villkor för val av [definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="cd94c-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cd94c-123">Se även</span><span class="sxs-lookup"><span data-stu-id="cd94c-123">See Also</span></span>

[<span data-ttu-id="cd94c-124">Definiera villkor för när Data visas</span><span class="sxs-lookup"><span data-stu-id="cd94c-124">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="cd94c-125">ScriptBlock Element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="cd94c-125">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="cd94c-126">SelectionCondition Element för EntrySelectedBy för EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="cd94c-126">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="cd94c-127">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="cd94c-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
