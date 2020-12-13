---
ms.date: 09/13/2016
ms.topic: reference
title: ScriptBlock-element för SelectionCondition för Controls för Configuration (format)
description: ScriptBlock-element för SelectionCondition för Controls för Configuration (format)
ms.openlocfilehash: 42e9d2b00f7690e46242b2c4602245e4bf391bbf
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664961"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="88d16-103">ScriptBlock-element för SelectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="88d16-103">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="88d16-104">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="88d16-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="88d16-105">När det här skriptet utvärderas `true` , uppfylls villkoret och definitionen används.</span><span class="sxs-lookup"><span data-stu-id="88d16-105">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="88d16-106">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="88d16-106">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="88d16-107">Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för Configuration (format) CustomEntry-elementet för CustomControl for Controls for Configuration (format) EntrySelectedBy-elementet för CustomEntry for Controls for Configuration (format) SelectionCondition element for EntrySelectedBy for Controls for Configuration (format) script block element for SelectionCondition for Controls for Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="88d16-107">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="88d16-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="88d16-108">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="88d16-109">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="88d16-109">Attributes and Elements</span></span>

<span data-ttu-id="88d16-110">I följande avsnitt beskrivs attribut, underordnade element och `ScriptBlock` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="88d16-110">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="88d16-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="88d16-111">Attributes</span></span>

<span data-ttu-id="88d16-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="88d16-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="88d16-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="88d16-113">Child Elements</span></span>

<span data-ttu-id="88d16-114">Inga.</span><span class="sxs-lookup"><span data-stu-id="88d16-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="88d16-115">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="88d16-115">Parent Elements</span></span>

|<span data-ttu-id="88d16-116">Element</span><span class="sxs-lookup"><span data-stu-id="88d16-116">Element</span></span>|<span data-ttu-id="88d16-117">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="88d16-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="88d16-118">SelectionCondition-element för EntrySelectedBy för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="88d16-118">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="88d16-119">Definierar ett villkor som måste finnas för att den gemensamma kontroll definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="88d16-119">Defines a condition that must exist for the common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="88d16-120">Textvärde</span><span class="sxs-lookup"><span data-stu-id="88d16-120">Text Value</span></span>

<span data-ttu-id="88d16-121">Ange det skript som utvärderas.</span><span class="sxs-lookup"><span data-stu-id="88d16-121">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="88d16-122">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="88d16-122">Remarks</span></span>

<span data-ttu-id="88d16-123">Urvals villkoret måste ange minst ett skript eller egenskaps namn som ska utvärderas, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="88d16-123">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="88d16-124">Mer information om hur urvals villkor kan användas finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="88d16-124">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="88d16-125">Se även</span><span class="sxs-lookup"><span data-stu-id="88d16-125">See Also</span></span>

[<span data-ttu-id="88d16-126">SelectionCondition-element för EntrySelectedBy för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="88d16-126">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="88d16-127">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="88d16-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
