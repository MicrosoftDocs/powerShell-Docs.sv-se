---
title: ExpressionBinding Element för CustomItem för GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eae5088-7605-4ef2-a703-faf3e5a5fc94
caps.latest.revision: 8
ms.openlocfilehash: 4714bfd1530585aa80aabc010b86d25bf0c7f9c4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846062"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a><span data-ttu-id="bf86d-102">ExpressionBinding-element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="bf86d-102">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="bf86d-103">Definierar de data som visas i kontrollen.</span><span class="sxs-lookup"><span data-stu-id="bf86d-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="bf86d-104">Det här elementet används när du definierar hur en ny grupp med objekt visas.</span><span class="sxs-lookup"><span data-stu-id="bf86d-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="bf86d-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för Visa (Format) anpassad kontroll elementet för GroupBy (Format) CustomEntries Element för anpassad kontroll för GroupBy (Format) CustomEntry elementet för Anpassad kontroll för GroupBy (Format) CustomItem elementet för CustomEntry för GroupBy (Format) ExpressionBinding elementet för CustomItem för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="bf86d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bf86d-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="bf86d-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="bf86d-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="bf86d-107">Attributes and Elements</span></span>

<span data-ttu-id="bf86d-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ExpressionBinding` element.</span><span class="sxs-lookup"><span data-stu-id="bf86d-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bf86d-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="bf86d-109">Attributes</span></span>

<span data-ttu-id="bf86d-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="bf86d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bf86d-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="bf86d-111">Child Elements</span></span>

|<span data-ttu-id="bf86d-112">Element</span><span class="sxs-lookup"><span data-stu-id="bf86d-112">Element</span></span>|<span data-ttu-id="bf86d-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="bf86d-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="bf86d-114">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="bf86d-114">Optional element.</span></span><br /><br /> <span data-ttu-id="bf86d-115">Definierar en kontroll som används av den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="bf86d-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="bf86d-116">CustomControlName Element för ExpressionBinding för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="bf86d-116">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="bf86d-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="bf86d-117">Optional element.</span></span><br /><br /> <span data-ttu-id="bf86d-118">Anger namnet på en gemensam kontroll eller en kontroll.</span><span class="sxs-lookup"><span data-stu-id="bf86d-118">Specifies the name of a common control or a view control.</span></span>|
|<span data-ttu-id="bf86d-119">[EnumerateCollection Element för ExpressionBinding för GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection Element för ExpressionBinding för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="bf86d-119">[EnumerateCollection Element for ExpressionBinding for GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>|<span data-ttu-id="bf86d-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="bf86d-120">Optional element.</span></span><br /><br /> <span data-ttu-id="bf86d-121">Ange att elementen i samlingar visas.</span><span class="sxs-lookup"><span data-stu-id="bf86d-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="bf86d-122">ItemSelectionCondition Element för ExpressionBinding för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="bf86d-122">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="bf86d-123">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="bf86d-123">Optional element.</span></span><br /><br /> <span data-ttu-id="bf86d-124">Definierar de villkor som måste finnas för den här kontrollen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="bf86d-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="bf86d-125">PropertyName-Element för ExpressionBinding för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="bf86d-125">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="bf86d-126">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="bf86d-126">Optional element.</span></span><br /><br /> <span data-ttu-id="bf86d-127">Anger egenskapen .NET vars värde visas i kontrollen.</span><span class="sxs-lookup"><span data-stu-id="bf86d-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="bf86d-128">ScriptBlock Element för ExpressionBinding för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="bf86d-128">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="bf86d-129">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="bf86d-129">Optional element.</span></span><br /><br /> <span data-ttu-id="bf86d-130">Anger skriptet vars värde visas i kontrollen.</span><span class="sxs-lookup"><span data-stu-id="bf86d-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bf86d-131">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="bf86d-131">Parent Elements</span></span>

|<span data-ttu-id="bf86d-132">Element</span><span class="sxs-lookup"><span data-stu-id="bf86d-132">Element</span></span>|<span data-ttu-id="bf86d-133">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="bf86d-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bf86d-134">CustomItem Element för CustomEntry för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="bf86d-134">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="bf86d-135">Definierar vilka data som visas i vyn anpassad kontroll och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="bf86d-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="bf86d-136">Se även</span><span class="sxs-lookup"><span data-stu-id="bf86d-136">See Also</span></span>

[<span data-ttu-id="bf86d-137">CustomControlName Element för ExpressionBinding för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="bf86d-137">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="bf86d-138">EnumerateCollection Element för ExpressionBinding för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="bf86d-138">EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="bf86d-139">ItemSelectionCondition Element för ExpressionBinding för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="bf86d-139">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="bf86d-140">PropertyName-Element för ExpressionBinding för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="bf86d-140">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="bf86d-141">ScriptBlock Element för ExpressionBinding för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="bf86d-141">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="bf86d-142">CustomItem Element för CustomEntry för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="bf86d-142">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="bf86d-143">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="bf86d-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
