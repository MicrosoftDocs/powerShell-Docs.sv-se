---
title: ScriptBlock Element för SelectionCondition för anpassad kontroll för vy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7031fa8b-3e2b-4ea8-89cb-95171f467b5a
caps.latest.revision: 6
ms.openlocfilehash: e55d1c5aa533005b258ecbbbf3ed9d55f852eab6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064568"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="96caf-102">ScriptBlock-element för SelectionCondition för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="96caf-102">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="96caf-103">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="96caf-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="96caf-104">När det här skriptet ska utvärderas till `true`villkoret uppfylls och definitionen används.</span><span class="sxs-lookup"><span data-stu-id="96caf-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="96caf-105">Det här elementet används när du definierar en anpassad kontroll vy.</span><span class="sxs-lookup"><span data-stu-id="96caf-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="96caf-106">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) anpassad kontroll konfigurationselement för Visa (Format) CustomEntries elementet för anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för anpassad kontroll för Visa ( Format) CustomItem Element för CustomEntry för anpassad kontroll för Visa (Format) SelectionCondition elementet för EntrySelectedBy för anpassad kontroll för Visa (Format) ScriptBlock elementet för SelectionCondition för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="96caf-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="96caf-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="96caf-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="96caf-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="96caf-108">Attributes and Elements</span></span>

<span data-ttu-id="96caf-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="96caf-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="96caf-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="96caf-110">Attributes</span></span>

<span data-ttu-id="96caf-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="96caf-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="96caf-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="96caf-112">Child Elements</span></span>

<span data-ttu-id="96caf-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="96caf-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="96caf-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="96caf-114">Parent Elements</span></span>

|<span data-ttu-id="96caf-115">Element</span><span class="sxs-lookup"><span data-stu-id="96caf-115">Element</span></span>|<span data-ttu-id="96caf-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="96caf-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="96caf-117">SelectionCondition Element för EntrySelectedBy för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="96caf-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="96caf-118">Definierar ett villkor som måste finnas för kontrolldefinition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="96caf-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="96caf-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="96caf-119">Text Value</span></span>

<span data-ttu-id="96caf-120">Ange det skript som ska utvärderas.</span><span class="sxs-lookup"><span data-stu-id="96caf-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="96caf-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="96caf-121">Remarks</span></span>

<span data-ttu-id="96caf-122">Urvalsvillkoret måste ange ett minst ett skript eller egenskapen namn för att utvärdera, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="96caf-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="96caf-123">Läs mer om hur du kan använda villkor för val av [definiera villkor för att visa Data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="96caf-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="96caf-124">Se även</span><span class="sxs-lookup"><span data-stu-id="96caf-124">See Also</span></span>

[<span data-ttu-id="96caf-125">SelectionCondition Element för EntrySelectedBy för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="96caf-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="96caf-126">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="96caf-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
