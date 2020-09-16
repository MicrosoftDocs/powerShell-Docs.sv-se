---
title: Script block-element för SelectionCondition för kontroller för vy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e5f4295a989307cb6ffb655c2c39596f3d1ea806
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785429"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="11fac-102">ScriptBlock-element för SelectionCondition för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="11fac-102">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="11fac-103">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="11fac-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="11fac-104">När det här skriptet utvärderas `true` , uppfylls villkoret och definitionen används.</span><span class="sxs-lookup"><span data-stu-id="11fac-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="11fac-105">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="11fac-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="11fac-106">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) styr element (format) styr element (format) styr element (format) kontroll element för Controls for View (format) CustomControl-element för kontroll för kontroller för View (format) CustomEntries-element för CustomControl för kontroller (format) CustomEntry-element för CustomEntries for Controls for View (format) EntrySelectedBy-element för CustomEntry for Controls for View (format) SelectionCondition-elementet for EntrySelectedBy for Controls for View (format) script block element for SelectionCondition for Controls for View (format)</span><span class="sxs-lookup"><span data-stu-id="11fac-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="11fac-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="11fac-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="11fac-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="11fac-108">Attributes and Elements</span></span>

<span data-ttu-id="11fac-109">I följande avsnitt beskrivs attribut, underordnade element och `ScriptBlock` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="11fac-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="11fac-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="11fac-110">Attributes</span></span>

<span data-ttu-id="11fac-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="11fac-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="11fac-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="11fac-112">Child Elements</span></span>

<span data-ttu-id="11fac-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="11fac-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="11fac-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="11fac-114">Parent Elements</span></span>

|<span data-ttu-id="11fac-115">Element</span><span class="sxs-lookup"><span data-stu-id="11fac-115">Element</span></span>|<span data-ttu-id="11fac-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11fac-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="11fac-117">SelectionCondition-element för EntrySelectedBy för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="11fac-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="11fac-118">Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="11fac-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="11fac-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="11fac-119">Text Value</span></span>

<span data-ttu-id="11fac-120">Ange det skript som utvärderas.</span><span class="sxs-lookup"><span data-stu-id="11fac-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="11fac-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="11fac-121">Remarks</span></span>

<span data-ttu-id="11fac-122">Urvals villkoret måste ange minst ett skript eller egenskaps namn som ska utvärderas, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="11fac-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="11fac-123">Mer information om hur urvals villkor kan användas finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="11fac-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="11fac-124">Se även</span><span class="sxs-lookup"><span data-stu-id="11fac-124">See Also</span></span>

[<span data-ttu-id="11fac-125">SelectionCondition-element för EntrySelectedBy för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="11fac-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="11fac-126">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="11fac-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
