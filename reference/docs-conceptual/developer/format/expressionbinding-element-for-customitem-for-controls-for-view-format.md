---
title: ExpressionBinding-element för CustomItem för kontroller för vy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355071"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="47084-102">ExpressionBinding-element för CustomItem för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="47084-102">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="47084-103">Definierar de data som visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="47084-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="47084-104">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="47084-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="47084-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) styr element för Controls (format) CustomControl-element för kontroll för Control for View (format) CustomEntries-element för CustomControl för visnings-(format) CustomEntry-element för CustomEntries for Controls for View (format) CustomItem-elementet for CustomEntry for Controls for View (format) ExpressionBinding element for CustomItem for Controls for View (format)</span><span class="sxs-lookup"><span data-stu-id="47084-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="47084-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="47084-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="47084-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="47084-107">Attributes and Elements</span></span>

<span data-ttu-id="47084-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `ExpressionBinding`-elementet.</span><span class="sxs-lookup"><span data-stu-id="47084-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="47084-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="47084-109">Attributes</span></span>

<span data-ttu-id="47084-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="47084-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="47084-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="47084-111">Child Elements</span></span>

|<span data-ttu-id="47084-112">Element</span><span class="sxs-lookup"><span data-stu-id="47084-112">Element</span></span>|<span data-ttu-id="47084-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="47084-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="47084-114">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="47084-114">Optional element.</span></span><br /><br /> <span data-ttu-id="47084-115">Definierar en kontroll som används av den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="47084-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="47084-116">CustomControlName-element för ExpressionBinding för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="47084-116">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="47084-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="47084-117">Optional element.</span></span><br /><br /> <span data-ttu-id="47084-118">Anger namnet på en gemensam kontroll eller en visnings kontroll.</span><span class="sxs-lookup"><span data-stu-id="47084-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="47084-119">EnumerateCollection-element för ExpressionBinding för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="47084-119">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="47084-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="47084-120">Optional element.</span></span><br /><br /> <span data-ttu-id="47084-121">Anger att elementen i samlingar visas.</span><span class="sxs-lookup"><span data-stu-id="47084-121">Specifies that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="47084-122">ItemSelectionCondition-element för ExpressionBinding för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="47084-122">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="47084-123">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="47084-123">Optional element.</span></span><br /><br /> <span data-ttu-id="47084-124">Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="47084-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="47084-125">PropertyName-element för ExpressionBinding för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="47084-125">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="47084-126">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="47084-126">Optional element.</span></span><br /><br /> <span data-ttu-id="47084-127">Anger den .NET-egenskap vars värde visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="47084-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="47084-128">Script block-element för ExpressionBinding för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="47084-128">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="47084-129">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="47084-129">Optional element.</span></span><br /><br /> <span data-ttu-id="47084-130">Anger det skript vars värde visas i kontrollen.</span><span class="sxs-lookup"><span data-stu-id="47084-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="47084-131">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="47084-131">Parent Elements</span></span>

|<span data-ttu-id="47084-132">Element</span><span class="sxs-lookup"><span data-stu-id="47084-132">Element</span></span>|<span data-ttu-id="47084-133">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="47084-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="47084-134">CustomItem-element för CustomEntry för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="47084-134">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="47084-135">Definierar vilka data som visas av kontrollen och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="47084-135">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="47084-136">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="47084-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="47084-137">Se även</span><span class="sxs-lookup"><span data-stu-id="47084-137">See Also</span></span>

[<span data-ttu-id="47084-138">CustomItem-element för CustomEntry för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="47084-138">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="47084-139">CustomControlName-element för ExpressionBinding för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="47084-139">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="47084-140">EnumerateCollection-element för ExpressionBinding för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="47084-140">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="47084-141">ItemSelectionCondition-element för ExpressionBinding för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="47084-141">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="47084-142">PropertyName-element för ExpressionBinding för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="47084-142">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="47084-143">Script block-element för ExpressionBinding för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="47084-143">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="47084-144">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="47084-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
