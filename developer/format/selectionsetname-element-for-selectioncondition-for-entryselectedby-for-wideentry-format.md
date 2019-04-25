---
title: SelectionSetName Element för SelectionCondition för EntrySelectedBy för WideEntry (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a13a429c-a31b-4e29-828c-c0c0917b5415
caps.latest.revision: 11
ms.openlocfilehash: baea89e4b259611dfa45b6bcf94fa0bf2df6b9de
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075485"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="e54d4-102">SelectionSetName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="e54d4-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="e54d4-103">Anger uppsättningen med .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="e54d4-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="e54d4-104">När någon av typerna i den här uppsättningen finns villkoret uppfylls och objektet visas med hjälp av den här definitionen av bred vy.</span><span class="sxs-lookup"><span data-stu-id="e54d4-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the wide view.</span></span>

<span data-ttu-id="e54d4-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy konfigurationselement för WideEntry (Format) SelectionCondition elementet för EntrySelectedBy för WideEntry (Format) SelectionSetName elementet för SelectionCondition för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="e54d4-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e54d4-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e54d4-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e54d4-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="e54d4-107">Attributes and Elements</span></span>

<span data-ttu-id="e54d4-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `SelectionSetName` element.</span><span class="sxs-lookup"><span data-stu-id="e54d4-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e54d4-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="e54d4-109">Attributes</span></span>

<span data-ttu-id="e54d4-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="e54d4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e54d4-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="e54d4-111">Child Elements</span></span>

<span data-ttu-id="e54d4-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="e54d4-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e54d4-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="e54d4-113">Parent Elements</span></span>

|<span data-ttu-id="e54d4-114">Element</span><span class="sxs-lookup"><span data-stu-id="e54d4-114">Element</span></span>|<span data-ttu-id="e54d4-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e54d4-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e54d4-116">SelectionCondition Element för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="e54d4-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="e54d4-117">Definierar de villkor som måste finnas för den här definitionen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="e54d4-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e54d4-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="e54d4-118">Text Value</span></span>

<span data-ttu-id="e54d4-119">Ange namnet på val av uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="e54d4-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="e54d4-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="e54d4-120">Remarks</span></span>

<span data-ttu-id="e54d4-121">Urvalsvillkoret kan ange en uppsättning för val av eller en .NET-typ, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="e54d4-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="e54d4-122">Läs mer om hur du använder villkor för val av [definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e54d4-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="e54d4-123">Val av som är vanliga grupper av .NET-objekt som kan användas av en vy som definierar filen formatering.</span><span class="sxs-lookup"><span data-stu-id="e54d4-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="e54d4-124">Läs mer om att skapa och refererar till val av uppsättningar [definiera anger av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="e54d4-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="e54d4-125">Mer information om andra komponenter för en bred vy finns i [skapar en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="e54d4-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e54d4-126">Se även</span><span class="sxs-lookup"><span data-stu-id="e54d4-126">See Also</span></span>

[<span data-ttu-id="e54d4-127">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="e54d4-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="e54d4-128">Definiera villkor för när Data visas</span><span class="sxs-lookup"><span data-stu-id="e54d4-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="e54d4-129">Definiera inställningarna</span><span class="sxs-lookup"><span data-stu-id="e54d4-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="e54d4-130">SelectionCondition Element för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="e54d4-130">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="e54d4-131">TypeName-Element för SelectionCondition för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="e54d4-131">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="e54d4-132">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="e54d4-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
