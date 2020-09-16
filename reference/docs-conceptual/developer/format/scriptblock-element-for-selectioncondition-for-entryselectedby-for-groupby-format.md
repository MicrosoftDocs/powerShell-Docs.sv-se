---
title: Script block-element för SelectionCondition för EntrySelectedBy för GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e70e1555a8f2fe0d15d3e864d80d35527af81b03
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785395"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="ccc31-102">ScriptBlock-element för SelectionCondition för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="ccc31-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="ccc31-103">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="ccc31-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="ccc31-104">När det här skriptet utvärderas `true` , uppfylls villkoret och definitionen används.</span><span class="sxs-lookup"><span data-stu-id="ccc31-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="ccc31-105">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="ccc31-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="ccc31-106">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element for CustomControl for groupby (format) EntrySelectedBy-element för CustomEntry (format) SelectionCondition element for EntrySelectedBy för groupby (format) script block element for SelectionCondition</span><span class="sxs-lookup"><span data-stu-id="ccc31-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ccc31-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="ccc31-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ccc31-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="ccc31-108">Attributes and Elements</span></span>

<span data-ttu-id="ccc31-109">I följande avsnitt beskrivs attribut, underordnade element och `ScriptBlock` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="ccc31-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ccc31-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="ccc31-110">Attributes</span></span>

<span data-ttu-id="ccc31-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="ccc31-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ccc31-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="ccc31-112">Child Elements</span></span>

<span data-ttu-id="ccc31-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="ccc31-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ccc31-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="ccc31-114">Parent Elements</span></span>

|<span data-ttu-id="ccc31-115">Element</span><span class="sxs-lookup"><span data-stu-id="ccc31-115">Element</span></span>|<span data-ttu-id="ccc31-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ccc31-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ccc31-117">SelectionCondition-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="ccc31-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="ccc31-118">Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="ccc31-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ccc31-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="ccc31-119">Text Value</span></span>

<span data-ttu-id="ccc31-120">Ange det skript som utvärderas.</span><span class="sxs-lookup"><span data-stu-id="ccc31-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="ccc31-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="ccc31-121">Remarks</span></span>

<span data-ttu-id="ccc31-122">Urvals villkoret måste ange minst ett skript eller egenskaps namn som ska utvärderas, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="ccc31-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="ccc31-123">Mer information om hur urvals villkor kan användas finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="ccc31-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ccc31-124">Se även</span><span class="sxs-lookup"><span data-stu-id="ccc31-124">See Also</span></span>

[<span data-ttu-id="ccc31-125">SelectionCondition-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="ccc31-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="ccc31-126">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="ccc31-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
