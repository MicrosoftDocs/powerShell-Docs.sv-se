---
title: ExpressionBinding Element för CustomItem för kontroller för att visa (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065962"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="1d873-102">ExpressionBinding-element för CustomItem för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="1d873-102">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="1d873-103">Definierar de data som visas i kontrollen.</span><span class="sxs-lookup"><span data-stu-id="1d873-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="1d873-104">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="1d873-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="1d873-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) kontroller Element (Format) kontroll konfigurationselement för kontroller för att visa (Format) anpassad kontroll Element för kontroll för kontroller för att visa (Format) CustomEntries Element för Anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för kontroller för att visa (Format) CustomItem Element för CustomEntry för kontroller för att visa (Format) ExpressionBinding Element för CustomItem för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="1d873-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1d873-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="1d873-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="1d873-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="1d873-107">Attributes and Elements</span></span>

<span data-ttu-id="1d873-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ExpressionBinding` element.</span><span class="sxs-lookup"><span data-stu-id="1d873-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1d873-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="1d873-109">Attributes</span></span>

<span data-ttu-id="1d873-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="1d873-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1d873-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="1d873-111">Child Elements</span></span>

|<span data-ttu-id="1d873-112">Element</span><span class="sxs-lookup"><span data-stu-id="1d873-112">Element</span></span>|<span data-ttu-id="1d873-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1d873-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="1d873-114">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="1d873-114">Optional element.</span></span><br /><br /> <span data-ttu-id="1d873-115">Definierar en kontroll som används av den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="1d873-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="1d873-116">CustomControlName Element för ExpressionBinding för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="1d873-116">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="1d873-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="1d873-117">Optional element.</span></span><br /><br /> <span data-ttu-id="1d873-118">Anger namnet på en gemensam kontroll eller en kontroll.</span><span class="sxs-lookup"><span data-stu-id="1d873-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="1d873-119">EnumerateCollection Element för ExpressionBinding för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="1d873-119">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="1d873-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="1d873-120">Optional element.</span></span><br /><br /> <span data-ttu-id="1d873-121">Anger att elementen i samlingar visas.</span><span class="sxs-lookup"><span data-stu-id="1d873-121">Specifies that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="1d873-122">ItemSelectionCondition Element i ExpressionBinding för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="1d873-122">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="1d873-123">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="1d873-123">Optional element.</span></span><br /><br /> <span data-ttu-id="1d873-124">Definierar de villkor som måste finnas för den här kontrollen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="1d873-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="1d873-125">PropertyName-Element för ExpressionBinding för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="1d873-125">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="1d873-126">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="1d873-126">Optional element.</span></span><br /><br /> <span data-ttu-id="1d873-127">Anger egenskapen .NET vars värde visas i kontrollen.</span><span class="sxs-lookup"><span data-stu-id="1d873-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="1d873-128">ScriptBlock Element för ExpressionBinding för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="1d873-128">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="1d873-129">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="1d873-129">Optional element.</span></span><br /><br /> <span data-ttu-id="1d873-130">Anger skriptet vars värde visas i kontrollen.</span><span class="sxs-lookup"><span data-stu-id="1d873-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1d873-131">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="1d873-131">Parent Elements</span></span>

|<span data-ttu-id="1d873-132">Element</span><span class="sxs-lookup"><span data-stu-id="1d873-132">Element</span></span>|<span data-ttu-id="1d873-133">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1d873-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1d873-134">CustomItem Element för CustomEntry för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="1d873-134">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="1d873-135">Definierar vilka data som visas av kontrollen och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="1d873-135">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1d873-136">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="1d873-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="1d873-137">Se även</span><span class="sxs-lookup"><span data-stu-id="1d873-137">See Also</span></span>

[<span data-ttu-id="1d873-138">CustomItem Element för CustomEntry för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="1d873-138">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="1d873-139">CustomControlName Element för ExpressionBinding för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="1d873-139">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="1d873-140">EnumerateCollection Element för ExpressionBinding för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="1d873-140">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="1d873-141">ItemSelectionCondition Element i ExpressionBinding för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="1d873-141">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="1d873-142">PropertyName-Element för ExpressionBinding för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="1d873-142">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="1d873-143">ScriptBlock Element för ExpressionBinding för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="1d873-143">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="1d873-144">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="1d873-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
