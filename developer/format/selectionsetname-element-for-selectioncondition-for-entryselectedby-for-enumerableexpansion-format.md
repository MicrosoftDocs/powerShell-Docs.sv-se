---
title: SelectionSetName Element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b7af0b2-68e6-43c3-adcc-7c58007fced8
caps.latest.revision: 13
ms.openlocfilehash: 6f7c8d9af3c1c2fbda0208148b0088161701fdbe
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063868"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="3f428-102">SelectionSetName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="3f428-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="3f428-103">Anger uppsättningen med .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="3f428-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="3f428-104">När någon av typerna i den här uppsättningen finns är villkoret uppfyllt.</span><span class="sxs-lookup"><span data-stu-id="3f428-104">When any of the types in this set are present, the condition is met.</span></span>

<span data-ttu-id="3f428-105">Elementet DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansions Element (Format) EntrySelectedBy konfigurationselement för EnumerableExpansion (Format) SelectionCondition elementet för EntrySelectedBy för EnumerableExpansion (Format) SelectionSetName Element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="3f428-105">Configuration Element DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansions Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3f428-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="3f428-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3f428-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="3f428-107">Attributes and Elements</span></span>

<span data-ttu-id="3f428-108">I följande avsnitt beskrivs attribut, underordnade element och överordnade elementet i den `SelectionSetName` element.</span><span class="sxs-lookup"><span data-stu-id="3f428-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3f428-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="3f428-109">Attributes</span></span>

<span data-ttu-id="3f428-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="3f428-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3f428-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="3f428-111">Child Elements</span></span>

<span data-ttu-id="3f428-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="3f428-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3f428-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="3f428-113">Parent Elements</span></span>

|<span data-ttu-id="3f428-114">Element</span><span class="sxs-lookup"><span data-stu-id="3f428-114">Element</span></span>|<span data-ttu-id="3f428-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3f428-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3f428-116">SelectionCondition Element för EntrySelectedBy för EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="3f428-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="3f428-117">Definierar de villkor som måste finnas för att expandera samlingen objekt av den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="3f428-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3f428-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="3f428-118">Text Value</span></span>

<span data-ttu-id="3f428-119">Ange namnet på val av uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="3f428-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="3f428-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="3f428-120">Remarks</span></span>

<span data-ttu-id="3f428-121">Urvalsvillkoret kan ange en uppsättning för val av eller en .NET-typ, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="3f428-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="3f428-122">Läs mer om hur du använder villkor för val av [definiera villkor för att visa Data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="3f428-122">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="3f428-123">Val av som är vanliga grupper av .NET-objekt som kan användas av en vy som definierar filen formatering.</span><span class="sxs-lookup"><span data-stu-id="3f428-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="3f428-124">Läs mer om att skapa och refererar till val av uppsättningar [definiera val av anger](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="3f428-124">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3f428-125">Se även</span><span class="sxs-lookup"><span data-stu-id="3f428-125">See Also</span></span>

[<span data-ttu-id="3f428-126">Definiera inställningarna</span><span class="sxs-lookup"><span data-stu-id="3f428-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="3f428-127">SelectionCondition Element för EntrySelectedBy för EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="3f428-127">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="3f428-128">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="3f428-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
