---
title: ItemSelectionCondition-element för ExpressionBinding för kontroller för vy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e8e3ea64fd947fbb2b98c410ac08533f386c9505
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781213"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="8808b-102">ItemSelectionCondition-element för ExpressionBinding för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="8808b-102">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="8808b-103">Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="8808b-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="8808b-104">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="8808b-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="8808b-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) styr element för Controls (format) CustomControl-element för Control for View (format) CustomEntries-element för CustomControl för visning (format) CustomEntry-element för CustomEntries for Controls for View (format) CustomItem element for CustomEntry for Controls for View (format) ExpressionBinding element for CustomItem for Controls for View (format) ItemSelectionCondition element of ExpressionBinding for Controls for View (format)</span><span class="sxs-lookup"><span data-stu-id="8808b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8808b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="8808b-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8808b-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="8808b-107">Attributes and Elements</span></span>

<span data-ttu-id="8808b-108">I följande avsnitt beskrivs attribut, underordnade element och `ItemSelectionCondition` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="8808b-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8808b-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="8808b-109">Attributes</span></span>

<span data-ttu-id="8808b-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="8808b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8808b-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="8808b-111">Child Elements</span></span>

|<span data-ttu-id="8808b-112">Element</span><span class="sxs-lookup"><span data-stu-id="8808b-112">Element</span></span>|<span data-ttu-id="8808b-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8808b-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8808b-114">PropertyName-element för ItemSelectionCondition för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="8808b-114">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="8808b-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="8808b-115">Optional element.</span></span><br /><br /> <span data-ttu-id="8808b-116">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="8808b-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="8808b-117">ScriptBlock-element för ItemSelectionCondition för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="8808b-117">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="8808b-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="8808b-118">Optional element.</span></span><br /><br /> <span data-ttu-id="8808b-119">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="8808b-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8808b-120">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="8808b-120">Parent Elements</span></span>

|<span data-ttu-id="8808b-121">Element</span><span class="sxs-lookup"><span data-stu-id="8808b-121">Element</span></span>|<span data-ttu-id="8808b-122">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8808b-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8808b-123">ExpressionBinding-element för CustomItem för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="8808b-123">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="8808b-124">Definierar de data som visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="8808b-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8808b-125">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="8808b-125">Remarks</span></span>

<span data-ttu-id="8808b-126">Du kan ange ett egenskaps namn eller ett skript för villkoret, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="8808b-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="8808b-127">Se även</span><span class="sxs-lookup"><span data-stu-id="8808b-127">See Also</span></span>

[<span data-ttu-id="8808b-128">PropertyName-element för ItemSelectionCondition för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="8808b-128">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="8808b-129">ScriptBlock-element för ItemSelectionCondition för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="8808b-129">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="8808b-130">ExpressionBinding-element för CustomItem för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="8808b-130">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="8808b-131">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="8808b-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
