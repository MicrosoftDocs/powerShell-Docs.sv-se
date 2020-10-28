---
ms.date: 09/13/2016
ms.topic: reference
title: ScriptBlock-element för SelectionCondition för CustomControl för View (format)
description: ScriptBlock-element för SelectionCondition för CustomControl för View (format)
ms.openlocfilehash: 78b977548243b6f3a658f15a0249d8cad12e2f1b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664916"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="1f86d-103">ScriptBlock-element för SelectionCondition för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="1f86d-103">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="1f86d-104">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="1f86d-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="1f86d-105">När det här skriptet utvärderas `true` , uppfylls villkoret och definitionen används.</span><span class="sxs-lookup"><span data-stu-id="1f86d-105">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="1f86d-106">Det här elementet används när du definierar en anpassad kontrol vy.</span><span class="sxs-lookup"><span data-stu-id="1f86d-106">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="1f86d-107">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) CustomControl-element för CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för CustomControl för View (format) CustomItem-element för CustomEntry för CustomControl för View (format) SelectionCondition-element för EntrySelectedBy för CustomControl för View (format) script block-element för SelectionCondition för View (format)</span><span class="sxs-lookup"><span data-stu-id="1f86d-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1f86d-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="1f86d-108">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1f86d-109">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="1f86d-109">Attributes and Elements</span></span>

<span data-ttu-id="1f86d-110">I följande avsnitt beskrivs attribut, underordnade element och `ScriptBlock` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="1f86d-110">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1f86d-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="1f86d-111">Attributes</span></span>

<span data-ttu-id="1f86d-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="1f86d-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1f86d-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="1f86d-113">Child Elements</span></span>

<span data-ttu-id="1f86d-114">Inga.</span><span class="sxs-lookup"><span data-stu-id="1f86d-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1f86d-115">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="1f86d-115">Parent Elements</span></span>

|<span data-ttu-id="1f86d-116">Element</span><span class="sxs-lookup"><span data-stu-id="1f86d-116">Element</span></span>|<span data-ttu-id="1f86d-117">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1f86d-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1f86d-118">SelectionCondition-element för EntrySelectedBy för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="1f86d-118">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="1f86d-119">Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="1f86d-119">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1f86d-120">Textvärde</span><span class="sxs-lookup"><span data-stu-id="1f86d-120">Text Value</span></span>

<span data-ttu-id="1f86d-121">Ange det skript som utvärderas.</span><span class="sxs-lookup"><span data-stu-id="1f86d-121">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="1f86d-122">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="1f86d-122">Remarks</span></span>

<span data-ttu-id="1f86d-123">Urvals villkoret måste ange minst ett skript eller egenskaps namn som ska utvärderas, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="1f86d-123">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="1f86d-124">Mer information om hur urvals villkor kan användas finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="1f86d-124">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1f86d-125">Se även</span><span class="sxs-lookup"><span data-stu-id="1f86d-125">See Also</span></span>

[<span data-ttu-id="1f86d-126">SelectionCondition-element för EntrySelectedBy för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="1f86d-126">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="1f86d-127">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="1f86d-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
