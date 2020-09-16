---
title: ExpressionBinding-element för CustomItem för kontroller för vy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6760bf17be58411948ecb3437bf18bce40073954
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773818"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="c2330-102">ExpressionBinding-element för CustomItem för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="c2330-102">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="c2330-103">Definierar de data som visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="c2330-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="c2330-104">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="c2330-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="c2330-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) kontroll element (format) styr element (format) för kontroll element för View (format) CustomControl-element för kontroll för Control for View (format) CustomEntries element för CustomControl for View (format) CustomEntry-elementet för CustomEntries for Controls for View (format) CustomItem-elementet for CustomEntry for Controls for View (format) ExpressionBinding element for CustomItem for Controls for View (format)</span><span class="sxs-lookup"><span data-stu-id="c2330-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c2330-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="c2330-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="c2330-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="c2330-107">Attributes and Elements</span></span>

<span data-ttu-id="c2330-108">I följande avsnitt beskrivs attribut, underordnade element och `ExpressionBinding` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="c2330-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c2330-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="c2330-109">Attributes</span></span>

<span data-ttu-id="c2330-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="c2330-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c2330-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="c2330-111">Child Elements</span></span>

|<span data-ttu-id="c2330-112">Element</span><span class="sxs-lookup"><span data-stu-id="c2330-112">Element</span></span>|<span data-ttu-id="c2330-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c2330-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="c2330-114">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="c2330-114">Optional element.</span></span><br /><br /> <span data-ttu-id="c2330-115">Definierar en kontroll som används av den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="c2330-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="c2330-116">CustomControlName-element för ExpressionBinding för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="c2330-116">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="c2330-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="c2330-117">Optional element.</span></span><br /><br /> <span data-ttu-id="c2330-118">Anger namnet på en gemensam kontroll eller en visnings kontroll.</span><span class="sxs-lookup"><span data-stu-id="c2330-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="c2330-119">EnumerateCollection-element för ExpressionBinding för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="c2330-119">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="c2330-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="c2330-120">Optional element.</span></span><br /><br /> <span data-ttu-id="c2330-121">Anger att elementen i samlingar visas.</span><span class="sxs-lookup"><span data-stu-id="c2330-121">Specifies that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="c2330-122">ItemSelectionCondition-element för ExpressionBinding för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="c2330-122">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="c2330-123">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="c2330-123">Optional element.</span></span><br /><br /> <span data-ttu-id="c2330-124">Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="c2330-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="c2330-125">PropertyName-element för ExpressionBinding för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="c2330-125">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="c2330-126">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="c2330-126">Optional element.</span></span><br /><br /> <span data-ttu-id="c2330-127">Anger den .NET-egenskap vars värde visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="c2330-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="c2330-128">ScriptBlock-element för ExpressionBinding för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="c2330-128">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="c2330-129">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="c2330-129">Optional element.</span></span><br /><br /> <span data-ttu-id="c2330-130">Anger det skript vars värde visas i kontrollen.</span><span class="sxs-lookup"><span data-stu-id="c2330-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c2330-131">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="c2330-131">Parent Elements</span></span>

|<span data-ttu-id="c2330-132">Element</span><span class="sxs-lookup"><span data-stu-id="c2330-132">Element</span></span>|<span data-ttu-id="c2330-133">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c2330-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c2330-134">CustomItem-element för CustomEntry för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="c2330-134">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="c2330-135">Definierar vilka data som visas av kontrollen och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="c2330-135">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c2330-136">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="c2330-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="c2330-137">Se även</span><span class="sxs-lookup"><span data-stu-id="c2330-137">See Also</span></span>

[<span data-ttu-id="c2330-138">CustomItem-element för CustomEntry för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="c2330-138">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="c2330-139">CustomControlName-element för ExpressionBinding för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="c2330-139">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="c2330-140">EnumerateCollection-element för ExpressionBinding för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="c2330-140">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="c2330-141">ItemSelectionCondition-element för ExpressionBinding för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="c2330-141">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="c2330-142">PropertyName-element för ExpressionBinding för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="c2330-142">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="c2330-143">ScriptBlock-element för ExpressionBinding för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="c2330-143">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="c2330-144">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="c2330-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
