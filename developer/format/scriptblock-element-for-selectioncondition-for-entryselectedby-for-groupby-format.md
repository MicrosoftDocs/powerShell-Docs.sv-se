---
title: ScriptBlock Element för SelectionCondition för EntrySelectedBy för GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e01344bd-ad69-4789-8e9f-2e79880c3a33
caps.latest.revision: 6
ms.openlocfilehash: cb79fb942111cee89c6b2abba75de4c494082b7e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844767"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="262cb-102">ScriptBlock-element för SelectionCondition för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="262cb-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="262cb-103">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="262cb-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="262cb-104">När det här skriptet ska utvärderas till `true`villkoret uppfylls och definitionen används.</span><span class="sxs-lookup"><span data-stu-id="262cb-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="262cb-105">Det här elementet används när du definierar hur en ny grupp med objekt visas.</span><span class="sxs-lookup"><span data-stu-id="262cb-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="262cb-106">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för Visa (Format) anpassad kontroll elementet för GroupBy (Format) CustomEntries Element för anpassad kontroll för GroupBy (Format) CustomEntry elementet för Anpassad kontroll för GroupBy (Format) EntrySelectedBy elementet för CustomEntry för GroupBy (Format) SelectionCondition elementet för EntrySelectedBy för GroupBy (Format) ScriptBlock elementet för SelectionCondition för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="262cb-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="262cb-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="262cb-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="262cb-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="262cb-108">Attributes and Elements</span></span>

<span data-ttu-id="262cb-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="262cb-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="262cb-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="262cb-110">Attributes</span></span>

<span data-ttu-id="262cb-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="262cb-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="262cb-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="262cb-112">Child Elements</span></span>

<span data-ttu-id="262cb-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="262cb-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="262cb-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="262cb-114">Parent Elements</span></span>

|<span data-ttu-id="262cb-115">Element</span><span class="sxs-lookup"><span data-stu-id="262cb-115">Element</span></span>|<span data-ttu-id="262cb-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="262cb-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="262cb-117">SelectionCondition Element för EntrySelectedBy för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="262cb-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="262cb-118">Definierar ett villkor som måste finnas för kontrolldefinition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="262cb-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="262cb-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="262cb-119">Text Value</span></span>

<span data-ttu-id="262cb-120">Ange det skript som ska utvärderas.</span><span class="sxs-lookup"><span data-stu-id="262cb-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="262cb-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="262cb-121">Remarks</span></span>

<span data-ttu-id="262cb-122">Urvalsvillkoret måste ange ett minst ett skript eller egenskapen namn för att utvärdera, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="262cb-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="262cb-123">Läs mer om hur du kan använda villkor för val av [definiera villkor för att visa Data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="262cb-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="262cb-124">Se även</span><span class="sxs-lookup"><span data-stu-id="262cb-124">See Also</span></span>

[<span data-ttu-id="262cb-125">SelectionCondition Element för EntrySelectedBy för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="262cb-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="262cb-126">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="262cb-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
