---
title: SelectionSetName Element för SelectionCondition för EntrySelectedBy för ListEntry (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eae67e47-6c60-4741-8430-78d2cb6067b1
caps.latest.revision: 10
ms.openlocfilehash: ccfc0b772ad3b2d1979c7c832a5153de870035d7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851151"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a><span data-ttu-id="08a62-102">SelectionSetName-element för SelectionCondition för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="08a62-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

<span data-ttu-id="08a62-103">Anger uppsättningen med .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="08a62-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="08a62-104">När någon av typerna i den här uppsättningen finns villkoret uppfylls och objektet visas med hjälp av den här definitionen i listvyn.</span><span class="sxs-lookup"><span data-stu-id="08a62-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the list view.</span></span>

<span data-ttu-id="08a62-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy konfigurationselement för ListEntry (Format) SelectionCondition elementet för EntrySelectedBy för ListEntry (Format) SelectionSetName elementet för SelectionCondition för EntrySelectedBy för ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="08a62-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="08a62-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="08a62-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="08a62-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="08a62-107">Attributes and Elements</span></span>

<span data-ttu-id="08a62-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `SelectionSetName` element.</span><span class="sxs-lookup"><span data-stu-id="08a62-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="08a62-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="08a62-109">Attributes</span></span>

<span data-ttu-id="08a62-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="08a62-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="08a62-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="08a62-111">Child Elements</span></span>

<span data-ttu-id="08a62-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="08a62-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="08a62-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="08a62-113">Parent Elements</span></span>

|<span data-ttu-id="08a62-114">Element</span><span class="sxs-lookup"><span data-stu-id="08a62-114">Element</span></span>|<span data-ttu-id="08a62-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="08a62-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="08a62-116">SelectionCondition Element för EntrySelectedBy för ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="08a62-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="08a62-117">Definierar de villkor som måste finnas för att använda den här definitionen i listvyn.</span><span class="sxs-lookup"><span data-stu-id="08a62-117">Defines the condition that must exist to use this definition of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="08a62-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="08a62-118">Text Value</span></span>

<span data-ttu-id="08a62-119">Ange namnet på val av uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="08a62-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="08a62-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="08a62-120">Remarks</span></span>

<span data-ttu-id="08a62-121">Urvalsvillkoret kan ange en uppsättning för val av eller en .NET-typ, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="08a62-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="08a62-122">Läs mer om hur du använder villkor för val av [definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="08a62-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="08a62-123">Val av som är vanliga grupper av .NET-objekt som kan användas av en vy som definierar filen formatering.</span><span class="sxs-lookup"><span data-stu-id="08a62-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="08a62-124">Läs mer om att skapa och refererar till val av uppsättningar [definiera anger av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="08a62-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="08a62-125">Läs mer om andra komponenter i en listvy, [skapar en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="08a62-125">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="08a62-126">Se även</span><span class="sxs-lookup"><span data-stu-id="08a62-126">See Also</span></span>

[<span data-ttu-id="08a62-127">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="08a62-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="08a62-128">Definiera villkor för när Data visas</span><span class="sxs-lookup"><span data-stu-id="08a62-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="08a62-129">SelectionCondition Element för EntrySelectedBy för ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="08a62-129">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="08a62-130">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="08a62-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
