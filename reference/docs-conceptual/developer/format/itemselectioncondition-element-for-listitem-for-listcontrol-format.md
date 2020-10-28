---
ms.date: 09/13/2016
ms.topic: reference
title: ItemSelectionCondition-element för ListItem för ListControl (format)
description: ItemSelectionCondition-element för ListItem för ListControl (format)
ms.openlocfilehash: 13d925da10c2386123983d52b109c03a0c3c63ab
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667818"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="47769-103">ItemSelectionCondition-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="47769-103">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="47769-104">Definierar det villkor som måste finnas för att listobjektet ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="47769-104">Defines the condition that must exist for this list item to be used.</span></span>

<span data-ttu-id="47769-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) ListEntries-element för ListControl (format) ListEntry-element för ListEntries för ListControl (format) ListItems element for ListEntry for ListControl (format) ListItem element for ListItems for ListControl (format) ItemSelectionCondition element for ListItem for ListControl for (format)</span><span class="sxs-lookup"><span data-stu-id="47769-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="47769-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="47769-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="47769-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="47769-107">Attributes and Elements</span></span>

<span data-ttu-id="47769-108">I följande avsnitt beskrivs attribut, underordnade element och `ItemSelectionCondition` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="47769-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="47769-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="47769-109">Attributes</span></span>

<span data-ttu-id="47769-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="47769-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="47769-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="47769-111">Child Elements</span></span>

|<span data-ttu-id="47769-112">Element</span><span class="sxs-lookup"><span data-stu-id="47769-112">Element</span></span>|<span data-ttu-id="47769-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="47769-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="47769-114">PropertyName-element för ItemSelectionCondition för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="47769-114">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="47769-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="47769-115">Optional element.</span></span><br /><br /> <span data-ttu-id="47769-116">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="47769-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="47769-117">ScriptBlock-element för ItemSelectionCondition för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="47769-117">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="47769-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="47769-118">Optional element.</span></span><br /><br /> <span data-ttu-id="47769-119">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="47769-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="47769-120">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="47769-120">Parent Elements</span></span>

|<span data-ttu-id="47769-121">Element</span><span class="sxs-lookup"><span data-stu-id="47769-121">Element</span></span>|<span data-ttu-id="47769-122">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="47769-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="47769-123">ListItem-element för ListItems för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="47769-123">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="47769-124">Definierar egenskapen eller skriptet vars värde visas i en rad i list visningen.</span><span class="sxs-lookup"><span data-stu-id="47769-124">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="47769-125">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="47769-125">Remarks</span></span>

<span data-ttu-id="47769-126">Du kan ange ett egenskaps namn eller ett skript för villkoret, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="47769-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="47769-127">Se även</span><span class="sxs-lookup"><span data-stu-id="47769-127">See Also</span></span>

[<span data-ttu-id="47769-128">ListItem-element för ListItems för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="47769-128">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="47769-129">PropertyName-element för ItemSelectionCondition för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="47769-129">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="47769-130">ScriptBlock-element för ItemSelectionCondition för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="47769-130">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="47769-131">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="47769-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
