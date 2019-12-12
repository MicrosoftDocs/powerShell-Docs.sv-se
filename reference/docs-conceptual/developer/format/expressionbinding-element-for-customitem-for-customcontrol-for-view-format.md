---
title: ExpressionBinding-element för CustomItem för CustomControl för View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354630"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="e5c24-102">ExpressionBinding-element för CustomItem för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="e5c24-102">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="e5c24-103">Definierar de data som visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="e5c24-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="e5c24-104">Det här elementet används när du definierar en anpassad kontrol vy.</span><span class="sxs-lookup"><span data-stu-id="e5c24-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="e5c24-105">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) CustomControl-element för View (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View Format) CustomItem-element för CustomEntry för CustomControl för View (format) ExpressionBinding-elementet för CustomItem för View (format)</span><span class="sxs-lookup"><span data-stu-id="e5c24-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e5c24-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e5c24-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="e5c24-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="e5c24-107">Attributes and Elements</span></span>

<span data-ttu-id="e5c24-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `ExpressionBinding`-elementet.</span><span class="sxs-lookup"><span data-stu-id="e5c24-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e5c24-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="e5c24-109">Attributes</span></span>

<span data-ttu-id="e5c24-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="e5c24-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e5c24-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="e5c24-111">Child Elements</span></span>

|<span data-ttu-id="e5c24-112">Element</span><span class="sxs-lookup"><span data-stu-id="e5c24-112">Element</span></span>|<span data-ttu-id="e5c24-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e5c24-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="e5c24-114">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e5c24-114">Optional element.</span></span><br /><br /> <span data-ttu-id="e5c24-115">Definierar en kontroll som används av den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="e5c24-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="e5c24-116">CustomControlName-element för ExpressionBinding för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="e5c24-116">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="e5c24-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e5c24-117">Optional element.</span></span><br /><br /> <span data-ttu-id="e5c24-118">Anger namnet på en gemensam kontroll eller en visnings kontroll.</span><span class="sxs-lookup"><span data-stu-id="e5c24-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="e5c24-119">EnumerateCollection-element för ExpressionBinding för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="e5c24-119">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="e5c24-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e5c24-120">Optional element.</span></span><br /><br /> <span data-ttu-id="e5c24-121">Anger att samlings elementen visas.</span><span class="sxs-lookup"><span data-stu-id="e5c24-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="e5c24-122">ItemSelectionCondition-element för ExpressionBinding för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="e5c24-122">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="e5c24-123">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e5c24-123">Optional element.</span></span><br /><br /> <span data-ttu-id="e5c24-124">Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="e5c24-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="e5c24-125">PropertyName-element för ExpressionBinding för CustomControl för vy (format)</span><span class="sxs-lookup"><span data-stu-id="e5c24-125">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="e5c24-126">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e5c24-126">Optional element.</span></span><br /><br /> <span data-ttu-id="e5c24-127">Anger den .NET-egenskap vars värde visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="e5c24-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="e5c24-128">Script block-element för ExpressionBinding för CustomCustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="e5c24-128">ScriptBlock Element for ExpressionBinding for CustomCustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="e5c24-129">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e5c24-129">Optional element.</span></span><br /><br /> <span data-ttu-id="e5c24-130">Anger det skript vars värde visas i kontrollen.</span><span class="sxs-lookup"><span data-stu-id="e5c24-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e5c24-131">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="e5c24-131">Parent Elements</span></span>

|<span data-ttu-id="e5c24-132">Element</span><span class="sxs-lookup"><span data-stu-id="e5c24-132">Element</span></span>|<span data-ttu-id="e5c24-133">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e5c24-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5c24-134">CustomItem-element för CustomEntry för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="e5c24-134">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="e5c24-135">Definierar vilka data som visas i vyn anpassad kontroll och hur den visas.</span><span class="sxs-lookup"><span data-stu-id="e5c24-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e5c24-136">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="e5c24-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="e5c24-137">Se även</span><span class="sxs-lookup"><span data-stu-id="e5c24-137">See Also</span></span>

[<span data-ttu-id="e5c24-138">CustomControlName-element för ExpressionBinding för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="e5c24-138">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e5c24-139">EnumerateCollection-element för ExpressionBinding för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="e5c24-139">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e5c24-140">ItemSelectionCondition-element för ExpressionBinding för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="e5c24-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="e5c24-141">PropertyName-element för ExpressionBinding för CustomControl för vy (format)</span><span class="sxs-lookup"><span data-stu-id="e5c24-141">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e5c24-142">Script block-element för ExpressionBinding för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="e5c24-142">ScriptBlock Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e5c24-143">CustomItem-element för CustomEntry för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="e5c24-143">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e5c24-144">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="e5c24-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
