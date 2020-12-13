---
ms.date: 09/13/2016
ms.topic: reference
title: ScriptBlock-element för SelectionCondition för Controls för View (format)
description: ScriptBlock-element för SelectionCondition för Controls för View (format)
ms.openlocfilehash: 7eed3b8a06bc45396026b8e2a7454447b3090d74
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664941"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="d0d04-103">ScriptBlock-element för SelectionCondition för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="d0d04-103">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="d0d04-104">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="d0d04-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="d0d04-105">När det här skriptet utvärderas `true` , uppfylls villkoret och definitionen används.</span><span class="sxs-lookup"><span data-stu-id="d0d04-105">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="d0d04-106">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="d0d04-106">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="d0d04-107">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) styr element (format) styr element (format) styr element (format) kontroll element för Controls for View (format) CustomControl-element för kontroll för kontroller för View (format) CustomEntries-element för CustomControl för kontroller (format) CustomEntry-element för CustomEntries for Controls for View (format) EntrySelectedBy-element för CustomEntry for Controls for View (format) SelectionCondition-elementet for EntrySelectedBy for Controls for View (format) script block element for SelectionCondition for Controls for View (format)</span><span class="sxs-lookup"><span data-stu-id="d0d04-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d0d04-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="d0d04-108">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d0d04-109">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="d0d04-109">Attributes and Elements</span></span>

<span data-ttu-id="d0d04-110">I följande avsnitt beskrivs attribut, underordnade element och `ScriptBlock` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="d0d04-110">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d0d04-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="d0d04-111">Attributes</span></span>

<span data-ttu-id="d0d04-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="d0d04-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d0d04-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="d0d04-113">Child Elements</span></span>

<span data-ttu-id="d0d04-114">Inga.</span><span class="sxs-lookup"><span data-stu-id="d0d04-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d0d04-115">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="d0d04-115">Parent Elements</span></span>

|<span data-ttu-id="d0d04-116">Element</span><span class="sxs-lookup"><span data-stu-id="d0d04-116">Element</span></span>|<span data-ttu-id="d0d04-117">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d0d04-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d0d04-118">SelectionCondition-element för EntrySelectedBy för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="d0d04-118">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="d0d04-119">Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="d0d04-119">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d0d04-120">Textvärde</span><span class="sxs-lookup"><span data-stu-id="d0d04-120">Text Value</span></span>

<span data-ttu-id="d0d04-121">Ange det skript som utvärderas.</span><span class="sxs-lookup"><span data-stu-id="d0d04-121">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="d0d04-122">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="d0d04-122">Remarks</span></span>

<span data-ttu-id="d0d04-123">Urvals villkoret måste ange minst ett skript eller egenskaps namn som ska utvärderas, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="d0d04-123">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="d0d04-124">Mer information om hur urvals villkor kan användas finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d0d04-124">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d0d04-125">Se även</span><span class="sxs-lookup"><span data-stu-id="d0d04-125">See Also</span></span>

[<span data-ttu-id="d0d04-126">SelectionCondition-element för EntrySelectedBy för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="d0d04-126">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="d0d04-127">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="d0d04-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
