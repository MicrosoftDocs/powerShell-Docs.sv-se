---
title: Script block-element för SelectionCondition för EntrySelectedBy för WideControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c8f2223d4a1217786a930eb82390c24b81d2f72e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787622"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="ff1f1-102">ScriptBlock-element för SelectionCondition för EntrySelectedBy för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="ff1f1-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="ff1f1-103">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="ff1f1-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="ff1f1-104">När det här skriptet utvärderas `true` , uppfylls villkoret och den breda post definitionen används.</span><span class="sxs-lookup"><span data-stu-id="ff1f1-104">When this script is evaluated to `true`, the condition is met, and the wide entry definition is used.</span></span>

<span data-ttu-id="ff1f1-105">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) WideControl-element (format) WideEntries-element (format) WideEntry-element (format) EntrySelectedBy-element för WideEntry (format) SelectionCondition element for EntrySelectedBy for WideEntry (format) script block-element för SelectionCondition för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="ff1f1-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ff1f1-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="ff1f1-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ff1f1-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="ff1f1-107">Attributes and Elements</span></span>

<span data-ttu-id="ff1f1-108">I följande avsnitt beskrivs attribut, underordnade element och `ScriptBlock` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="ff1f1-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ff1f1-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="ff1f1-109">Attributes</span></span>

<span data-ttu-id="ff1f1-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="ff1f1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ff1f1-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="ff1f1-111">Child Elements</span></span>

<span data-ttu-id="ff1f1-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="ff1f1-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ff1f1-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="ff1f1-113">Parent Elements</span></span>

|<span data-ttu-id="ff1f1-114">Element</span><span class="sxs-lookup"><span data-stu-id="ff1f1-114">Element</span></span>|<span data-ttu-id="ff1f1-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ff1f1-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ff1f1-116">SelectionCondition-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ff1f1-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="ff1f1-117">Definierar det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="ff1f1-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ff1f1-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="ff1f1-118">Text Value</span></span>

<span data-ttu-id="ff1f1-119">Ange det skript som utvärderas.</span><span class="sxs-lookup"><span data-stu-id="ff1f1-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="ff1f1-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="ff1f1-120">Remarks</span></span>

<span data-ttu-id="ff1f1-121">Urvals villkoret måste innehålla minst ett skript eller egenskaps namn som ska utvärderas, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="ff1f1-121">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="ff1f1-122">Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="ff1f1-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="ff1f1-123">Mer information om andra komponenter i en bred vy finns i [wide View](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="ff1f1-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ff1f1-124">Se även</span><span class="sxs-lookup"><span data-stu-id="ff1f1-124">See Also</span></span>

[<span data-ttu-id="ff1f1-125">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="ff1f1-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="ff1f1-126">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="ff1f1-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="ff1f1-127">PropertyName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ff1f1-127">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="ff1f1-128">SelectionCondition-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ff1f1-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="ff1f1-129">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="ff1f1-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
