---
title: ScriptBlock Element för SelectionCondition för EntrySelectedBy för WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec68309-7826-4643-a521-e29c996663fb
caps.latest.revision: 11
ms.openlocfilehash: 649a978e21e9421a3f3e953261e1d309e23c3f9c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851676"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="d5541-102">ScriptBlock-element för SelectionCondition för EntrySelectedBy för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="d5541-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="d5541-103">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="d5541-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="d5541-104">När det här skriptet ska utvärderas till `true`villkoret uppfylls och definitionen för bred posten används.</span><span class="sxs-lookup"><span data-stu-id="d5541-104">When this script is evaluated to `true`, the condition is met, and the wide entry definition is used.</span></span>

<span data-ttu-id="d5541-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy konfigurationselement för WideEntry (Format) SelectionCondition elementet för EntrySelectedBy för WideEntry (Format) ScriptBlock elementet för SelectionCondition för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="d5541-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d5541-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="d5541-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d5541-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="d5541-107">Attributes and Elements</span></span>

<span data-ttu-id="d5541-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="d5541-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d5541-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="d5541-109">Attributes</span></span>

<span data-ttu-id="d5541-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="d5541-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d5541-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="d5541-111">Child Elements</span></span>

<span data-ttu-id="d5541-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="d5541-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d5541-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="d5541-113">Parent Elements</span></span>

|<span data-ttu-id="d5541-114">Element</span><span class="sxs-lookup"><span data-stu-id="d5541-114">Element</span></span>|<span data-ttu-id="d5541-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d5541-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d5541-116">SelectionCondition Element för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="d5541-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="d5541-117">Definierar de villkor som måste finnas för den här definitionen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="d5541-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d5541-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="d5541-118">Text Value</span></span>

<span data-ttu-id="d5541-119">Ange det skript som ska utvärderas.</span><span class="sxs-lookup"><span data-stu-id="d5541-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="d5541-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="d5541-120">Remarks</span></span>

<span data-ttu-id="d5541-121">Urvalsvillkoret måste ange minst ett skript eller egenskapen namn för att utvärdera, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="d5541-121">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="d5541-122">Läs mer om hur du använder villkor för val av [definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d5541-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="d5541-123">Mer information om andra komponenter för en bred vy finns i [bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="d5541-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d5541-124">Se även</span><span class="sxs-lookup"><span data-stu-id="d5541-124">See Also</span></span>

[<span data-ttu-id="d5541-125">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="d5541-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="d5541-126">Definiera villkor för när Data visas</span><span class="sxs-lookup"><span data-stu-id="d5541-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="d5541-127">PropertyName-Element för SelectionCondition för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="d5541-127">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="d5541-128">SelectionCondition Element för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="d5541-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="d5541-129">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="d5541-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
