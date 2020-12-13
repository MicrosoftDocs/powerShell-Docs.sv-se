---
ms.date: 09/13/2016
ms.topic: reference
title: ExpressionBinding-element för CustomItem för Controls för View (format)
description: ExpressionBinding-element för CustomItem för Controls för View (format)
ms.openlocfilehash: da87bb26d21dcb051871e67997cc3fba7ce73c74
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649890"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="7aae7-103">ExpressionBinding-element för CustomItem för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="7aae7-103">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="7aae7-104">Definierar de data som visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="7aae7-104">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="7aae7-105">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="7aae7-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="7aae7-106">Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) kontroll element (format) styr element (format) för kontroll element för View (format) CustomControl-element för kontroll för Control for View (format) CustomEntries element för CustomControl for View (format) CustomEntry-elementet för CustomEntries for Controls for View (format) CustomItem-elementet for CustomEntry for Controls for View (format) ExpressionBinding element for CustomItem for Controls for View (format)</span><span class="sxs-lookup"><span data-stu-id="7aae7-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7aae7-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="7aae7-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="7aae7-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="7aae7-108">Attributes and Elements</span></span>

<span data-ttu-id="7aae7-109">I följande avsnitt beskrivs attribut, underordnade element och `ExpressionBinding` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="7aae7-109">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7aae7-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="7aae7-110">Attributes</span></span>

<span data-ttu-id="7aae7-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="7aae7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7aae7-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="7aae7-112">Child Elements</span></span>

|<span data-ttu-id="7aae7-113">Element</span><span class="sxs-lookup"><span data-stu-id="7aae7-113">Element</span></span>|<span data-ttu-id="7aae7-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7aae7-114">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="7aae7-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="7aae7-115">Optional element.</span></span><br /><br /> <span data-ttu-id="7aae7-116">Definierar en kontroll som används av den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="7aae7-116">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="7aae7-117">CustomControlName-element för ExpressionBinding för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="7aae7-117">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="7aae7-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="7aae7-118">Optional element.</span></span><br /><br /> <span data-ttu-id="7aae7-119">Anger namnet på en gemensam kontroll eller en visnings kontroll.</span><span class="sxs-lookup"><span data-stu-id="7aae7-119">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="7aae7-120">EnumerateCollection-element för ExpressionBinding för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="7aae7-120">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="7aae7-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="7aae7-121">Optional element.</span></span><br /><br /> <span data-ttu-id="7aae7-122">Anger att elementen i samlingar visas.</span><span class="sxs-lookup"><span data-stu-id="7aae7-122">Specifies that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="7aae7-123">ItemSelectionCondition-element för ExpressionBinding för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="7aae7-123">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="7aae7-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="7aae7-124">Optional element.</span></span><br /><br /> <span data-ttu-id="7aae7-125">Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="7aae7-125">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="7aae7-126">PropertyName-element för ExpressionBinding för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="7aae7-126">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="7aae7-127">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="7aae7-127">Optional element.</span></span><br /><br /> <span data-ttu-id="7aae7-128">Anger den .NET-egenskap vars värde visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="7aae7-128">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="7aae7-129">ScriptBlock-element för ExpressionBinding för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="7aae7-129">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="7aae7-130">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="7aae7-130">Optional element.</span></span><br /><br /> <span data-ttu-id="7aae7-131">Anger det skript vars värde visas i kontrollen.</span><span class="sxs-lookup"><span data-stu-id="7aae7-131">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7aae7-132">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="7aae7-132">Parent Elements</span></span>

|<span data-ttu-id="7aae7-133">Element</span><span class="sxs-lookup"><span data-stu-id="7aae7-133">Element</span></span>|<span data-ttu-id="7aae7-134">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7aae7-134">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7aae7-135">CustomItem-element för CustomEntry för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="7aae7-135">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="7aae7-136">Definierar vilka data som visas av kontrollen och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="7aae7-136">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7aae7-137">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="7aae7-137">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="7aae7-138">Se även</span><span class="sxs-lookup"><span data-stu-id="7aae7-138">See Also</span></span>

[<span data-ttu-id="7aae7-139">CustomItem-element för CustomEntry för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="7aae7-139">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="7aae7-140">CustomControlName-element för ExpressionBinding för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="7aae7-140">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="7aae7-141">EnumerateCollection-element för ExpressionBinding för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="7aae7-141">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="7aae7-142">ItemSelectionCondition-element för ExpressionBinding för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="7aae7-142">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="7aae7-143">PropertyName-element för ExpressionBinding för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="7aae7-143">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="7aae7-144">ScriptBlock-element för ExpressionBinding för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="7aae7-144">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="7aae7-145">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="7aae7-145">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
