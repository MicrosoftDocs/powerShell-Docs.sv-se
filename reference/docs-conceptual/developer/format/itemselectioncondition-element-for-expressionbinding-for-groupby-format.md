---
ms.date: 09/13/2016
ms.topic: reference
title: ItemSelectionCondition-element för ExpressionBinding för GroupBy (format)
description: ItemSelectionCondition-element för ExpressionBinding för GroupBy (format)
ms.openlocfilehash: 92120ace5ed316fbfbf1d51422071c27d5a604cf
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651979"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="3cddd-103">ItemSelectionCondition-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3cddd-103">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="3cddd-104">Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="3cddd-104">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="3cddd-105">Det finns ingen gräns för antalet urvals villkor som kan anges för ett kontroll objekt.</span><span class="sxs-lookup"><span data-stu-id="3cddd-105">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="3cddd-106">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="3cddd-106">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="3cddd-107">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element for CustomControl for groupby (format) CustomItem-element för CustomEntry (format) ExpressionBinding element for CustomItem för groupby (format) ItemSelectionCondition element for ExpressionBinding</span><span class="sxs-lookup"><span data-stu-id="3cddd-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3cddd-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="3cddd-108">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3cddd-109">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="3cddd-109">Attributes and Elements</span></span>

<span data-ttu-id="3cddd-110">I följande avsnitt beskrivs attribut, underordnade element och `ItemSelectionCondition` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="3cddd-110">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3cddd-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="3cddd-111">Attributes</span></span>

<span data-ttu-id="3cddd-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="3cddd-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3cddd-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="3cddd-113">Child Elements</span></span>

|<span data-ttu-id="3cddd-114">Element</span><span class="sxs-lookup"><span data-stu-id="3cddd-114">Element</span></span>|<span data-ttu-id="3cddd-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3cddd-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3cddd-116">PropertyName-element för ItemSelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3cddd-116">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="3cddd-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="3cddd-117">Optional element.</span></span><br /><br /> <span data-ttu-id="3cddd-118">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="3cddd-118">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="3cddd-119">ScriptBlock-element för ItemSelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3cddd-119">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="3cddd-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="3cddd-120">Optional element.</span></span><br /><br /> <span data-ttu-id="3cddd-121">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="3cddd-121">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3cddd-122">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="3cddd-122">Parent Elements</span></span>

|<span data-ttu-id="3cddd-123">Element</span><span class="sxs-lookup"><span data-stu-id="3cddd-123">Element</span></span>|<span data-ttu-id="3cddd-124">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3cddd-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3cddd-125">ExpressionBinding-element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3cddd-125">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="3cddd-126">Definierar de data som visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="3cddd-126">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3cddd-127">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="3cddd-127">Remarks</span></span>

<span data-ttu-id="3cddd-128">Du kan ange ett egenskaps namn eller ett skript för villkoret, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="3cddd-128">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="3cddd-129">Se även</span><span class="sxs-lookup"><span data-stu-id="3cddd-129">See Also</span></span>

[<span data-ttu-id="3cddd-130">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="3cddd-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="3cddd-131">ExpressionBinding-element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3cddd-131">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)
