---
title: SelectionSetName Element för SelectionCondition för anpassad kontroll för vy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52b05a9-762e-4f1c-ad57-9d1710149722
caps.latest.revision: 10
ms.openlocfilehash: 25d46665ca5df3ddf49af5718d513b84c77988c8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851550"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="79555-102">SelectionSetName-element för SelectionCondition för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="79555-102">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="79555-103">Anger uppsättningen med .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="79555-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="79555-104">När någon av typerna i den här uppsättningen finns villkoret uppfylls och objektet visas med hjälp av den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="79555-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="79555-105">Det här elementet används när du definierar en anpassad kontroll vy.</span><span class="sxs-lookup"><span data-stu-id="79555-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="79555-106">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) anpassad kontroll Element (Format) CustomEntries konfigurationselement för anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för EntrySelectedBy vy (Format) Element för CustomEntry för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="79555-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="79555-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="79555-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="79555-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="79555-108">Attributes and Elements</span></span>

<span data-ttu-id="79555-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `SelectionSetName` element.</span><span class="sxs-lookup"><span data-stu-id="79555-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="79555-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="79555-110">Attributes</span></span>

<span data-ttu-id="79555-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="79555-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="79555-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="79555-112">Child Elements</span></span>

<span data-ttu-id="79555-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="79555-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="79555-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="79555-114">Parent Elements</span></span>

|<span data-ttu-id="79555-115">Element</span><span class="sxs-lookup"><span data-stu-id="79555-115">Element</span></span>|<span data-ttu-id="79555-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="79555-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="79555-117">SelectionCondition Element för EntrySelectedBy för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="79555-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="79555-118">Definierar ett villkor som måste finnas för kontrolldefinition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="79555-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="79555-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="79555-119">Text Value</span></span>

<span data-ttu-id="79555-120">Ange namnet på val av uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="79555-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="79555-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="79555-121">Remarks</span></span>

<span data-ttu-id="79555-122">Val av som är vanliga grupper av .NET-objekt som kan användas av en vy som definierar filen formatering.</span><span class="sxs-lookup"><span data-stu-id="79555-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="79555-123">Läs mer om att skapa och refererar till val av uppsättningar [definiera anger av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="79555-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="79555-124">Urvalsvillkoret kan ange en uppsättning för val av eller en .NET-typ, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="79555-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="79555-125">Läs mer om hur du använder villkor för val av [definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="79555-125">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="79555-126">Se även</span><span class="sxs-lookup"><span data-stu-id="79555-126">See Also</span></span>

[<span data-ttu-id="79555-127">SelectionCondition Element för EntrySelectedBy för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="79555-127">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="79555-128">Definiera villkor för när Data visas</span><span class="sxs-lookup"><span data-stu-id="79555-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="79555-129">Definiera inställningarna</span><span class="sxs-lookup"><span data-stu-id="79555-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="79555-130">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="79555-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
