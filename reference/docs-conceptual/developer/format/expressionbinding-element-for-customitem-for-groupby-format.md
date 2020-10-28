---
ms.date: 09/13/2016
ms.topic: reference
title: ExpressionBinding-element för CustomItem för GroupBy (format)
description: ExpressionBinding-element för CustomItem för GroupBy (format)
ms.openlocfilehash: 742d9f081a674dc3ee4c84d600933aaf57b2aa6b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655301"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a><span data-ttu-id="dd2d7-103">ExpressionBinding-element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="dd2d7-103">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="dd2d7-104">Definierar de data som visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="dd2d7-104">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="dd2d7-105">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="dd2d7-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="dd2d7-106">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element for CustomControl for groupby (format) CustomItem-element för CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="dd2d7-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dd2d7-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="dd2d7-107">Syntax</span></span>

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dd2d7-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="dd2d7-108">Attributes and Elements</span></span>

<span data-ttu-id="dd2d7-109">I följande avsnitt beskrivs attribut, underordnade element och `ExpressionBinding` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="dd2d7-109">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dd2d7-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="dd2d7-110">Attributes</span></span>

<span data-ttu-id="dd2d7-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="dd2d7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dd2d7-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="dd2d7-112">Child Elements</span></span>

|<span data-ttu-id="dd2d7-113">Element</span><span class="sxs-lookup"><span data-stu-id="dd2d7-113">Element</span></span>|<span data-ttu-id="dd2d7-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="dd2d7-114">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="dd2d7-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="dd2d7-115">Optional element.</span></span><br /><br /> <span data-ttu-id="dd2d7-116">Definierar en kontroll som används av den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="dd2d7-116">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="dd2d7-117">CustomControlName-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="dd2d7-117">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="dd2d7-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="dd2d7-118">Optional element.</span></span><br /><br /> <span data-ttu-id="dd2d7-119">Anger namnet på en gemensam kontroll eller en visnings kontroll.</span><span class="sxs-lookup"><span data-stu-id="dd2d7-119">Specifies the name of a common control or a view control.</span></span>|
|<span data-ttu-id="dd2d7-120">[EnumerateCollection-element för ExpressionBinding för groupby (format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) EnumerateCollection-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="dd2d7-120">[EnumerateCollection Element for ExpressionBinding for GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>|<span data-ttu-id="dd2d7-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="dd2d7-121">Optional element.</span></span><br /><br /> <span data-ttu-id="dd2d7-122">Anger att samlings elementen visas.</span><span class="sxs-lookup"><span data-stu-id="dd2d7-122">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="dd2d7-123">ItemSelectionCondition-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="dd2d7-123">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="dd2d7-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="dd2d7-124">Optional element.</span></span><br /><br /> <span data-ttu-id="dd2d7-125">Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="dd2d7-125">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="dd2d7-126">PropertyName-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="dd2d7-126">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="dd2d7-127">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="dd2d7-127">Optional element.</span></span><br /><br /> <span data-ttu-id="dd2d7-128">Anger den .NET-egenskap vars värde visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="dd2d7-128">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="dd2d7-129">ScriptBlock-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="dd2d7-129">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="dd2d7-130">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="dd2d7-130">Optional element.</span></span><br /><br /> <span data-ttu-id="dd2d7-131">Anger det skript vars värde visas i kontrollen.</span><span class="sxs-lookup"><span data-stu-id="dd2d7-131">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="dd2d7-132">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="dd2d7-132">Parent Elements</span></span>

|<span data-ttu-id="dd2d7-133">Element</span><span class="sxs-lookup"><span data-stu-id="dd2d7-133">Element</span></span>|<span data-ttu-id="dd2d7-134">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="dd2d7-134">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dd2d7-135">CustomItem-element för CustomEntry för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="dd2d7-135">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="dd2d7-136">Definierar vilka data som visas i vyn anpassad kontroll och hur den visas.</span><span class="sxs-lookup"><span data-stu-id="dd2d7-136">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="dd2d7-137">Se även</span><span class="sxs-lookup"><span data-stu-id="dd2d7-137">See Also</span></span>

[<span data-ttu-id="dd2d7-138">CustomControlName-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="dd2d7-138">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="dd2d7-139">EnumerateCollection-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="dd2d7-139">EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="dd2d7-140">ItemSelectionCondition-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="dd2d7-140">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="dd2d7-141">PropertyName-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="dd2d7-141">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="dd2d7-142">ScriptBlock-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="dd2d7-142">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="dd2d7-143">CustomItem-element för CustomEntry för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="dd2d7-143">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="dd2d7-144">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="dd2d7-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
