---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName-element för ItemSelectionCondition för ListControl (format)
description: PropertyName-element för ItemSelectionCondition för ListControl (format)
ms.openlocfilehash: c515efe70afdb1c1186c0a07fe1f52dc49ad57b9
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92665999"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="06354-103">PropertyName-element för ItemSelectionCondition för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="06354-103">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="06354-104">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="06354-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="06354-105">När den här egenskapen finns eller när den utvärderas `true` , uppfylls villkoret och vyn används.</span><span class="sxs-lookup"><span data-stu-id="06354-105">When this property is present or when it evaluates to `true`, the condition is met, and the view is used.</span></span> <span data-ttu-id="06354-106">Det här elementet används när du definierar en listvy.</span><span class="sxs-lookup"><span data-stu-id="06354-106">This element is used when defining a list view.</span></span>

<span data-ttu-id="06354-107">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) ListEntries-element (format) ListEntry-element för ListControl (format) ListItems-element för ListEntry (format) ListControl-element för ListItem (format) ListItems-element för ListControl (format) ItemSelectionCondition-element för ListItem-elementet ListControls (format)</span><span class="sxs-lookup"><span data-stu-id="06354-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControls PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="06354-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="06354-108">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="06354-109">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="06354-109">Attributes and Elements</span></span>

<span data-ttu-id="06354-110">I följande avsnitt beskrivs attribut, underordnade element och `PropertyName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="06354-110">The following sections describe attributes, child elements, and the parent elements of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="06354-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="06354-111">Attributes</span></span>

<span data-ttu-id="06354-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="06354-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="06354-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="06354-113">Child Elements</span></span>

<span data-ttu-id="06354-114">Inga.</span><span class="sxs-lookup"><span data-stu-id="06354-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="06354-115">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="06354-115">Parent Elements</span></span>

|<span data-ttu-id="06354-116">Element</span><span class="sxs-lookup"><span data-stu-id="06354-116">Element</span></span>|<span data-ttu-id="06354-117">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="06354-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="06354-118">ItemSelectionCondition-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="06354-118">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a><span data-ttu-id="06354-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="06354-119">Text Value</span></span>

<span data-ttu-id="06354-120">Ange namnet på den egenskap vars värde visas.</span><span class="sxs-lookup"><span data-stu-id="06354-120">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="06354-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="06354-121">Remarks</span></span>

<span data-ttu-id="06354-122">Om det här elementet används kan du inte ange [script block](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) -elementet när du definierar urvals villkoret.</span><span class="sxs-lookup"><span data-stu-id="06354-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="06354-123">Se även</span><span class="sxs-lookup"><span data-stu-id="06354-123">See Also</span></span>

[<span data-ttu-id="06354-124">Script block-element för ItemSelectionCondition för ListIControl (format)</span><span class="sxs-lookup"><span data-stu-id="06354-124">ScriptBlock Element for ItemSelectionCondition for ListIControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="06354-125">ItemSelectionCondition-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="06354-125">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="06354-126">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="06354-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
