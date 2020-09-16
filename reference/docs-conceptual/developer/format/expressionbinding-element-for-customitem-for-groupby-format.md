---
title: ExpressionBinding-element för CustomItem for GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5b0017e487aab4ffcbf901cd44aad9b275b22832
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773733"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a><span data-ttu-id="b532a-102">ExpressionBinding-element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="b532a-102">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="b532a-103">Definierar de data som visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="b532a-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="b532a-104">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="b532a-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="b532a-105">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element for CustomControl for groupby (format) CustomItem-element för CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="b532a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b532a-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="b532a-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="b532a-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="b532a-107">Attributes and Elements</span></span>

<span data-ttu-id="b532a-108">I följande avsnitt beskrivs attribut, underordnade element och `ExpressionBinding` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="b532a-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b532a-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="b532a-109">Attributes</span></span>

<span data-ttu-id="b532a-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="b532a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b532a-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="b532a-111">Child Elements</span></span>

|<span data-ttu-id="b532a-112">Element</span><span class="sxs-lookup"><span data-stu-id="b532a-112">Element</span></span>|<span data-ttu-id="b532a-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b532a-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="b532a-114">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="b532a-114">Optional element.</span></span><br /><br /> <span data-ttu-id="b532a-115">Definierar en kontroll som används av den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="b532a-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="b532a-116">CustomControlName-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="b532a-116">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="b532a-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="b532a-117">Optional element.</span></span><br /><br /> <span data-ttu-id="b532a-118">Anger namnet på en gemensam kontroll eller en visnings kontroll.</span><span class="sxs-lookup"><span data-stu-id="b532a-118">Specifies the name of a common control or a view control.</span></span>|
|<span data-ttu-id="b532a-119">[EnumerateCollection-element för ExpressionBinding för groupby (format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) EnumerateCollection-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="b532a-119">[EnumerateCollection Element for ExpressionBinding for GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>|<span data-ttu-id="b532a-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="b532a-120">Optional element.</span></span><br /><br /> <span data-ttu-id="b532a-121">Anger att samlings elementen visas.</span><span class="sxs-lookup"><span data-stu-id="b532a-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="b532a-122">ItemSelectionCondition-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="b532a-122">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="b532a-123">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="b532a-123">Optional element.</span></span><br /><br /> <span data-ttu-id="b532a-124">Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="b532a-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="b532a-125">PropertyName-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="b532a-125">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="b532a-126">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="b532a-126">Optional element.</span></span><br /><br /> <span data-ttu-id="b532a-127">Anger den .NET-egenskap vars värde visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="b532a-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="b532a-128">ScriptBlock-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="b532a-128">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="b532a-129">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="b532a-129">Optional element.</span></span><br /><br /> <span data-ttu-id="b532a-130">Anger det skript vars värde visas i kontrollen.</span><span class="sxs-lookup"><span data-stu-id="b532a-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b532a-131">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="b532a-131">Parent Elements</span></span>

|<span data-ttu-id="b532a-132">Element</span><span class="sxs-lookup"><span data-stu-id="b532a-132">Element</span></span>|<span data-ttu-id="b532a-133">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b532a-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b532a-134">CustomItem-element för CustomEntry för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="b532a-134">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="b532a-135">Definierar vilka data som visas i vyn anpassad kontroll och hur den visas.</span><span class="sxs-lookup"><span data-stu-id="b532a-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="b532a-136">Se även</span><span class="sxs-lookup"><span data-stu-id="b532a-136">See Also</span></span>

[<span data-ttu-id="b532a-137">CustomControlName-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="b532a-137">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="b532a-138">EnumerateCollection-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="b532a-138">EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="b532a-139">ItemSelectionCondition-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="b532a-139">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="b532a-140">PropertyName-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="b532a-140">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="b532a-141">ScriptBlock-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="b532a-141">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="b532a-142">CustomItem-element för CustomEntry för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="b532a-142">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="b532a-143">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="b532a-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
