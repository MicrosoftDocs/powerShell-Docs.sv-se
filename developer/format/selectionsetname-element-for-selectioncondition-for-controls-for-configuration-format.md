---
title: SelectionSetName Element för SelectionCondition för kontroller för konfiguration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7dcaeadb-4e79-47a0-96e2-8952af26abbe
caps.latest.revision: 7
ms.openlocfilehash: 5db35a8094ea2bb966c8d6a96802c72f64c05c17
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064038"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="16fa8-102">SelectionSetName-element för SelectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="16fa8-102">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="16fa8-103">Anger uppsättningen med .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="16fa8-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="16fa8-104">När någon av typerna i den här uppsättningen finns villkoret uppfylls och objektet visas med hjälp av den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="16fa8-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="16fa8-105">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="16fa8-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="16fa8-106">Konfigurationselementet Element (Format) kontroller av (Format) kontroll konfigurationselement för kontroller för (Format) anpassad kontroll konfigurationselement för kontroll för (Format) CustomEntries konfigurationselement för anpassad kontroll för kontroller för (Format) CustomEntry konfigurationselement för anpassad kontroll för kontroller för (Format) EntrySelectedBy konfigurationselement för CustomEntry för kontroller för (Format) SelectionCondition konfigurationselement för EntrySelectedBy för kontroller för (Format) SelectionSetName konfigurationselement för SelectionCondition för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="16fa8-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="16fa8-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="16fa8-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="16fa8-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="16fa8-108">Attributes and Elements</span></span>

<span data-ttu-id="16fa8-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `SelectionSetName` element.</span><span class="sxs-lookup"><span data-stu-id="16fa8-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="16fa8-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="16fa8-110">Attributes</span></span>

<span data-ttu-id="16fa8-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="16fa8-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="16fa8-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="16fa8-112">Child Elements</span></span>

<span data-ttu-id="16fa8-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="16fa8-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="16fa8-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="16fa8-114">Parent Elements</span></span>

|<span data-ttu-id="16fa8-115">Element</span><span class="sxs-lookup"><span data-stu-id="16fa8-115">Element</span></span>|<span data-ttu-id="16fa8-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="16fa8-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="16fa8-117">SelectionCondition Element för EntrySelectedBy för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="16fa8-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="16fa8-118">Definierar ett villkor som måste finnas för kontrolldefinition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="16fa8-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="16fa8-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="16fa8-119">Text Value</span></span>

<span data-ttu-id="16fa8-120">Ange namnet på val av uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="16fa8-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="16fa8-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="16fa8-121">Remarks</span></span>

<span data-ttu-id="16fa8-122">Val av som är vanliga grupper av .NET-objekt som kan användas av en vy som definierar filen formatering.</span><span class="sxs-lookup"><span data-stu-id="16fa8-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="16fa8-123">Läs mer om att skapa och refererar till val av uppsättningar [definiera anger av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="16fa8-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="16fa8-124">Urvalsvillkoret kan ange en uppsättning för val av eller en .NET-typ, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="16fa8-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="16fa8-125">Läs mer om hur du använder villkor för val av [definiera villkor för att visa Data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="16fa8-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="16fa8-126">Se även</span><span class="sxs-lookup"><span data-stu-id="16fa8-126">See Also</span></span>

[<span data-ttu-id="16fa8-127">SelectionCondition Element för EntrySelectedBy för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="16fa8-127">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="16fa8-128">Definiera villkor för när Data visas</span><span class="sxs-lookup"><span data-stu-id="16fa8-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="16fa8-129">Definiera inställningarna</span><span class="sxs-lookup"><span data-stu-id="16fa8-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="16fa8-130">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="16fa8-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
