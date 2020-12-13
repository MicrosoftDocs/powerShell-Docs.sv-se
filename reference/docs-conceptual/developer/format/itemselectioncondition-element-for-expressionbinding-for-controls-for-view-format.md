---
ms.date: 09/13/2016
ms.topic: reference
title: ItemSelectionCondition-element för ExpressionBinding för Controls för View (format)
description: ItemSelectionCondition-element för ExpressionBinding för Controls för View (format)
ms.openlocfilehash: adbe747bdb4f6c1d180e5b630247de0fd3d72b85
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648055"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="67321-103">ItemSelectionCondition-element för ExpressionBinding för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="67321-103">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="67321-104">Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="67321-104">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="67321-105">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="67321-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="67321-106">Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) styr element för Controls (format) CustomControl-element för Control for View (format) CustomEntries-element för CustomControl för visning (format) CustomEntry-element för CustomEntries for Controls for View (format) CustomItem element for CustomEntry for Controls for View (format) ExpressionBinding element for CustomItem for Controls for View (format) ItemSelectionCondition element of ExpressionBinding for Controls for View (format)</span><span class="sxs-lookup"><span data-stu-id="67321-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="67321-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="67321-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="67321-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="67321-108">Attributes and Elements</span></span>

<span data-ttu-id="67321-109">I följande avsnitt beskrivs attribut, underordnade element och `ItemSelectionCondition` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="67321-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="67321-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="67321-110">Attributes</span></span>

<span data-ttu-id="67321-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="67321-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="67321-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="67321-112">Child Elements</span></span>

|<span data-ttu-id="67321-113">Element</span><span class="sxs-lookup"><span data-stu-id="67321-113">Element</span></span>|<span data-ttu-id="67321-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="67321-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="67321-115">PropertyName-element för ItemSelectionCondition för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="67321-115">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="67321-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="67321-116">Optional element.</span></span><br /><br /> <span data-ttu-id="67321-117">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="67321-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="67321-118">ScriptBlock-element för ItemSelectionCondition för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="67321-118">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="67321-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="67321-119">Optional element.</span></span><br /><br /> <span data-ttu-id="67321-120">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="67321-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="67321-121">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="67321-121">Parent Elements</span></span>

|<span data-ttu-id="67321-122">Element</span><span class="sxs-lookup"><span data-stu-id="67321-122">Element</span></span>|<span data-ttu-id="67321-123">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="67321-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="67321-124">ExpressionBinding-element för CustomItem för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="67321-124">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="67321-125">Definierar de data som visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="67321-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="67321-126">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="67321-126">Remarks</span></span>

<span data-ttu-id="67321-127">Du kan ange ett egenskaps namn eller ett skript för villkoret, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="67321-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="67321-128">Se även</span><span class="sxs-lookup"><span data-stu-id="67321-128">See Also</span></span>

[<span data-ttu-id="67321-129">PropertyName-element för ItemSelectionCondition för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="67321-129">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="67321-130">ScriptBlock-element för ItemSelectionCondition för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="67321-130">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="67321-131">ExpressionBinding-element för CustomItem för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="67321-131">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="67321-132">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="67321-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
