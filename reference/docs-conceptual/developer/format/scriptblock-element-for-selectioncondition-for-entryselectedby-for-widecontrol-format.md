---
ms.date: 09/13/2016
ms.topic: reference
title: ScriptBlock-element för SelectionCondition för EntrySelectedBy för WideControl (format)
description: ScriptBlock-element för SelectionCondition för EntrySelectedBy för WideControl (format)
ms.openlocfilehash: 53d3eba9d453dbcc96afbe8f81a16b61573f2874
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651965"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="9fbc7-103">ScriptBlock-element för SelectionCondition för EntrySelectedBy för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="9fbc7-103">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="9fbc7-104">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="9fbc7-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="9fbc7-105">När det här skriptet utvärderas `true` , uppfylls villkoret och den breda post definitionen används.</span><span class="sxs-lookup"><span data-stu-id="9fbc7-105">When this script is evaluated to `true`, the condition is met, and the wide entry definition is used.</span></span>

<span data-ttu-id="9fbc7-106">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) WideControl-element (format) WideEntries-element (format) WideEntry-element (format) EntrySelectedBy-element för WideEntry (format) SelectionCondition element for EntrySelectedBy for WideEntry (format) script block-element för SelectionCondition för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="9fbc7-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9fbc7-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="9fbc7-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9fbc7-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="9fbc7-108">Attributes and Elements</span></span>

<span data-ttu-id="9fbc7-109">I följande avsnitt beskrivs attribut, underordnade element och `ScriptBlock` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="9fbc7-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9fbc7-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="9fbc7-110">Attributes</span></span>

<span data-ttu-id="9fbc7-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="9fbc7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9fbc7-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="9fbc7-112">Child Elements</span></span>

<span data-ttu-id="9fbc7-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="9fbc7-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9fbc7-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="9fbc7-114">Parent Elements</span></span>

|<span data-ttu-id="9fbc7-115">Element</span><span class="sxs-lookup"><span data-stu-id="9fbc7-115">Element</span></span>|<span data-ttu-id="9fbc7-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="9fbc7-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9fbc7-117">SelectionCondition-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="9fbc7-117">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="9fbc7-118">Definierar det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="9fbc7-118">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9fbc7-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="9fbc7-119">Text Value</span></span>

<span data-ttu-id="9fbc7-120">Ange det skript som utvärderas.</span><span class="sxs-lookup"><span data-stu-id="9fbc7-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="9fbc7-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="9fbc7-121">Remarks</span></span>

<span data-ttu-id="9fbc7-122">Urvals villkoret måste innehålla minst ett skript eller egenskaps namn som ska utvärderas, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="9fbc7-122">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="9fbc7-123">Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="9fbc7-123">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="9fbc7-124">Mer information om andra komponenter i en bred vy finns i [wide View](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="9fbc7-124">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9fbc7-125">Se även</span><span class="sxs-lookup"><span data-stu-id="9fbc7-125">See Also</span></span>

[<span data-ttu-id="9fbc7-126">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="9fbc7-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="9fbc7-127">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="9fbc7-127">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="9fbc7-128">PropertyName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="9fbc7-128">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="9fbc7-129">SelectionCondition-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="9fbc7-129">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="9fbc7-130">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="9fbc7-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
