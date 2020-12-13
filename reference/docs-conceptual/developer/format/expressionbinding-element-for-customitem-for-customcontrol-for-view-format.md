---
ms.date: 09/13/2016
ms.topic: reference
title: ExpressionBinding-element för CustomItem för CustomControl för View (format)
description: ExpressionBinding-element för CustomItem för CustomControl för View (format)
ms.openlocfilehash: 8f4bfef4f6c65c6dabc7a776dda1083bac11fdf7
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648199"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="f03ff-103">ExpressionBinding-element för CustomItem för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="f03ff-103">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="f03ff-104">Definierar de data som visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="f03ff-104">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="f03ff-105">Det här elementet används när du definierar en anpassad kontrol vy.</span><span class="sxs-lookup"><span data-stu-id="f03ff-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="f03ff-106">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) CustomControl-element för View (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för CustomControl för View (format) CustomItem-element för CustomEntry för CustomControl för View (format) ExpressionBinding-element för CustomItem för View (format)</span><span class="sxs-lookup"><span data-stu-id="f03ff-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f03ff-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="f03ff-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="f03ff-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="f03ff-108">Attributes and Elements</span></span>

<span data-ttu-id="f03ff-109">I följande avsnitt beskrivs attribut, underordnade element och `ExpressionBinding` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="f03ff-109">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f03ff-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="f03ff-110">Attributes</span></span>

<span data-ttu-id="f03ff-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="f03ff-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f03ff-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="f03ff-112">Child Elements</span></span>

|<span data-ttu-id="f03ff-113">Element</span><span class="sxs-lookup"><span data-stu-id="f03ff-113">Element</span></span>|<span data-ttu-id="f03ff-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f03ff-114">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="f03ff-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="f03ff-115">Optional element.</span></span><br /><br /> <span data-ttu-id="f03ff-116">Definierar en kontroll som används av den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="f03ff-116">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="f03ff-117">CustomControlName-element för ExpressionBinding för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="f03ff-117">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="f03ff-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="f03ff-118">Optional element.</span></span><br /><br /> <span data-ttu-id="f03ff-119">Anger namnet på en gemensam kontroll eller en visnings kontroll.</span><span class="sxs-lookup"><span data-stu-id="f03ff-119">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="f03ff-120">EnumerateCollection-element för ExpressionBinding för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="f03ff-120">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="f03ff-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="f03ff-121">Optional element.</span></span><br /><br /> <span data-ttu-id="f03ff-122">Anger att samlings elementen visas.</span><span class="sxs-lookup"><span data-stu-id="f03ff-122">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="f03ff-123">ItemSelectionCondition-element för ExpressionBinding för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="f03ff-123">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="f03ff-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="f03ff-124">Optional element.</span></span><br /><br /> <span data-ttu-id="f03ff-125">Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="f03ff-125">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="f03ff-126">PropertyName-element för ExpressionBinding för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="f03ff-126">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="f03ff-127">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="f03ff-127">Optional element.</span></span><br /><br /> <span data-ttu-id="f03ff-128">Anger den .NET-egenskap vars värde visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="f03ff-128">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="f03ff-129">Script block-element för ExpressionBinding för CustomCustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="f03ff-129">ScriptBlock Element for ExpressionBinding for CustomCustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="f03ff-130">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="f03ff-130">Optional element.</span></span><br /><br /> <span data-ttu-id="f03ff-131">Anger det skript vars värde visas i kontrollen.</span><span class="sxs-lookup"><span data-stu-id="f03ff-131">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f03ff-132">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="f03ff-132">Parent Elements</span></span>

|<span data-ttu-id="f03ff-133">Element</span><span class="sxs-lookup"><span data-stu-id="f03ff-133">Element</span></span>|<span data-ttu-id="f03ff-134">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f03ff-134">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f03ff-135">CustomItem-element för CustomEntry för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="f03ff-135">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="f03ff-136">Definierar vilka data som visas i vyn anpassad kontroll och hur den visas.</span><span class="sxs-lookup"><span data-stu-id="f03ff-136">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f03ff-137">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="f03ff-137">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="f03ff-138">Se även</span><span class="sxs-lookup"><span data-stu-id="f03ff-138">See Also</span></span>

[<span data-ttu-id="f03ff-139">CustomControlName-element för ExpressionBinding för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="f03ff-139">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="f03ff-140">EnumerateCollection-element för ExpressionBinding för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="f03ff-140">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="f03ff-141">ItemSelectionCondition-element för ExpressionBinding för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="f03ff-141">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="f03ff-142">PropertyName-element för ExpressionBinding för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="f03ff-142">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="f03ff-143">ScriptBlock-element för ExpressionBinding för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="f03ff-143">ScriptBlock Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="f03ff-144">CustomItem-element för CustomEntry för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="f03ff-144">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="f03ff-145">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="f03ff-145">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
