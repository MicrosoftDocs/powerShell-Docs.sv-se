---
title: Script block-element för SelectionCondition för CustomControl för View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d3506188d32ce85ad6345dc0d0866dd789a1f293
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785412"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="ab8f7-102">ScriptBlock-element för SelectionCondition för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="ab8f7-102">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="ab8f7-103">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="ab8f7-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="ab8f7-104">När det här skriptet utvärderas `true` , uppfylls villkoret och definitionen används.</span><span class="sxs-lookup"><span data-stu-id="ab8f7-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="ab8f7-105">Det här elementet används när du definierar en anpassad kontrol vy.</span><span class="sxs-lookup"><span data-stu-id="ab8f7-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="ab8f7-106">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) CustomControl-element för CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för CustomControl för View (format) CustomItem-element för CustomEntry för CustomControl för View (format) SelectionCondition-element för EntrySelectedBy för CustomControl för View (format) script block-element för SelectionCondition för View (format)</span><span class="sxs-lookup"><span data-stu-id="ab8f7-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ab8f7-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="ab8f7-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ab8f7-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="ab8f7-108">Attributes and Elements</span></span>

<span data-ttu-id="ab8f7-109">I följande avsnitt beskrivs attribut, underordnade element och `ScriptBlock` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="ab8f7-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ab8f7-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="ab8f7-110">Attributes</span></span>

<span data-ttu-id="ab8f7-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="ab8f7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ab8f7-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="ab8f7-112">Child Elements</span></span>

<span data-ttu-id="ab8f7-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="ab8f7-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ab8f7-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="ab8f7-114">Parent Elements</span></span>

|<span data-ttu-id="ab8f7-115">Element</span><span class="sxs-lookup"><span data-stu-id="ab8f7-115">Element</span></span>|<span data-ttu-id="ab8f7-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ab8f7-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ab8f7-117">SelectionCondition-element för EntrySelectedBy för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="ab8f7-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="ab8f7-118">Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="ab8f7-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ab8f7-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="ab8f7-119">Text Value</span></span>

<span data-ttu-id="ab8f7-120">Ange det skript som utvärderas.</span><span class="sxs-lookup"><span data-stu-id="ab8f7-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="ab8f7-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="ab8f7-121">Remarks</span></span>

<span data-ttu-id="ab8f7-122">Urvals villkoret måste ange minst ett skript eller egenskaps namn som ska utvärderas, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="ab8f7-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="ab8f7-123">Mer information om hur urvals villkor kan användas finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="ab8f7-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ab8f7-124">Se även</span><span class="sxs-lookup"><span data-stu-id="ab8f7-124">See Also</span></span>

[<span data-ttu-id="ab8f7-125">SelectionCondition-element för EntrySelectedBy för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="ab8f7-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="ab8f7-126">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="ab8f7-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
