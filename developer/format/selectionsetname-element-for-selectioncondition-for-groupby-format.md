---
title: SelectionSetName Element för SelectionCondition för GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b9a4912-d755-42f3-8058-53c0797e28e4
caps.latest.revision: 6
ms.openlocfilehash: 371913eda2b09ff6788494b68738f2ad53ccb115
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847343"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="b1619-102">SelectionSetName-element för SelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="b1619-102">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="b1619-103">Anger uppsättningen med .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="b1619-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="b1619-104">När någon av typerna i den här uppsättningen finns villkoret uppfylls och objektet visas med hjälp av den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="b1619-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="b1619-105">Det här elementet används när du definierar hur en ny grupp med objekt visas.</span><span class="sxs-lookup"><span data-stu-id="b1619-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="b1619-106">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för Visa (Format) anpassad kontroll elementet för GroupBy (Format) CustomEntries Element för anpassad kontroll för GroupBy (Format) CustomEntry elementet för Anpassad kontroll för GroupBy (Format) EntrySelectedBy elementet för CustomEntry för GroupBy (Format) SelectionCondition elementet för EntrySelectedBy för GroupBy (Format) SelectionSetName elementet för SelectionCondition för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b1619-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b1619-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="b1619-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b1619-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="b1619-108">Attributes and Elements</span></span>

<span data-ttu-id="b1619-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `SelectionSetName` element.</span><span class="sxs-lookup"><span data-stu-id="b1619-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b1619-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="b1619-110">Attributes</span></span>

<span data-ttu-id="b1619-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="b1619-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b1619-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="b1619-112">Child Elements</span></span>

<span data-ttu-id="b1619-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="b1619-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b1619-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="b1619-114">Parent Elements</span></span>

|<span data-ttu-id="b1619-115">Element</span><span class="sxs-lookup"><span data-stu-id="b1619-115">Element</span></span>|<span data-ttu-id="b1619-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b1619-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b1619-117">SelectionCondition Element för EntrySelectedBy för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b1619-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="b1619-118">Definierar ett villkor som måste finnas för kontrolldefinition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="b1619-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b1619-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="b1619-119">Text Value</span></span>

<span data-ttu-id="b1619-120">Ange namnet på val av uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="b1619-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="b1619-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="b1619-121">Remarks</span></span>

<span data-ttu-id="b1619-122">Val av som är vanliga grupper av .NET-objekt som kan användas av en vy som definierar filen formatering.</span><span class="sxs-lookup"><span data-stu-id="b1619-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="b1619-123">Läs mer om att skapa och refererar till val av uppsättningar [definiera val av anger](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="b1619-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="b1619-124">När det här elementet har angetts ska du inte ange den [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) element.</span><span class="sxs-lookup"><span data-stu-id="b1619-124">When this element is specified, you cannot specify the [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) element.</span></span> <span data-ttu-id="b1619-125">Läs mer om hur du definierar villkoren för val av [definiera villkor för att visa Data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="b1619-125">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b1619-126">Se även</span><span class="sxs-lookup"><span data-stu-id="b1619-126">See Also</span></span>

[<span data-ttu-id="b1619-127">TypeName-Element för SelectionCondition för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b1619-127">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="b1619-128">SelectionCondition Element för EntrySelectedBy för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="b1619-128">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="b1619-129">Definiera villkor för när Data visas</span><span class="sxs-lookup"><span data-stu-id="b1619-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="b1619-130">Definiera inställningarna</span><span class="sxs-lookup"><span data-stu-id="b1619-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="b1619-131">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="b1619-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
