---
title: ExpressionBinding Element för CustomItem för anpassad kontroll för vy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065928"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="d48af-102">ExpressionBinding-element för CustomItem för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="d48af-102">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="d48af-103">Definierar de data som visas i kontrollen.</span><span class="sxs-lookup"><span data-stu-id="d48af-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="d48af-104">Det här elementet används när du definierar en anpassad kontroll vy.</span><span class="sxs-lookup"><span data-stu-id="d48af-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="d48af-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) anpassad kontroll konfigurationselement för Visa (Format) CustomEntries elementet för anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för anpassad kontroll för Visa ( Format) CustomItem Element för CustomEntry för anpassad kontroll för Visa (Format) ExpressionBinding elementet för CustomItem för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="d48af-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d48af-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="d48af-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="d48af-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="d48af-107">Attributes and Elements</span></span>

<span data-ttu-id="d48af-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ExpressionBinding` element.</span><span class="sxs-lookup"><span data-stu-id="d48af-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d48af-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="d48af-109">Attributes</span></span>

<span data-ttu-id="d48af-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="d48af-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d48af-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="d48af-111">Child Elements</span></span>

|<span data-ttu-id="d48af-112">Element</span><span class="sxs-lookup"><span data-stu-id="d48af-112">Element</span></span>|<span data-ttu-id="d48af-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d48af-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="d48af-114">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="d48af-114">Optional element.</span></span><br /><br /> <span data-ttu-id="d48af-115">Definierar en kontroll som används av den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="d48af-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="d48af-116">CustomControlName Element för ExpressionBinding för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="d48af-116">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="d48af-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="d48af-117">Optional element.</span></span><br /><br /> <span data-ttu-id="d48af-118">Anger namnet på en gemensam kontroll eller en kontroll.</span><span class="sxs-lookup"><span data-stu-id="d48af-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="d48af-119">EnumerateCollection Element för ExpressionBinding för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="d48af-119">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="d48af-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="d48af-120">Optional element.</span></span><br /><br /> <span data-ttu-id="d48af-121">Ange att elementen i samlingar visas.</span><span class="sxs-lookup"><span data-stu-id="d48af-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="d48af-122">ItemSelectionCondition Element för ExpressionBinding för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="d48af-122">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="d48af-123">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="d48af-123">Optional element.</span></span><br /><br /> <span data-ttu-id="d48af-124">Definierar de villkor som måste finnas för den här kontrollen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="d48af-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="d48af-125">PropertyName-Element för ExpressionBinding för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="d48af-125">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="d48af-126">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="d48af-126">Optional element.</span></span><br /><br /> <span data-ttu-id="d48af-127">Anger egenskapen .NET vars värde visas i kontrollen.</span><span class="sxs-lookup"><span data-stu-id="d48af-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="d48af-128">ScriptBlock Element för ExpressionBinding för CustomCustomControl för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="d48af-128">ScriptBlock Element for ExpressionBinding for CustomCustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="d48af-129">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="d48af-129">Optional element.</span></span><br /><br /> <span data-ttu-id="d48af-130">Anger skriptet vars värde visas i kontrollen.</span><span class="sxs-lookup"><span data-stu-id="d48af-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d48af-131">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="d48af-131">Parent Elements</span></span>

|<span data-ttu-id="d48af-132">Element</span><span class="sxs-lookup"><span data-stu-id="d48af-132">Element</span></span>|<span data-ttu-id="d48af-133">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d48af-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d48af-134">CustomItem Element för CustomEntry för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="d48af-134">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="d48af-135">Definierar vilka data som visas i vyn anpassad kontroll och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="d48af-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d48af-136">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="d48af-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="d48af-137">Se även</span><span class="sxs-lookup"><span data-stu-id="d48af-137">See Also</span></span>

[<span data-ttu-id="d48af-138">CustomControlName Element för ExpressionBinding för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="d48af-138">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d48af-139">EnumerateCollection Element för ExpressionBinding för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="d48af-139">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d48af-140">ItemSelectionCondition Element för ExpressionBinding för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="d48af-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="d48af-141">PropertyName-Element för ExpressionBinding för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="d48af-141">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d48af-142">ScriptBlock Element för ExpressionBinding för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="d48af-142">ScriptBlock Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d48af-143">CustomItem Element för CustomEntry för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="d48af-143">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d48af-144">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="d48af-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
