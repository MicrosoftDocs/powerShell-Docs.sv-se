---
ms.date: 09/13/2016
ms.topic: reference
title: ItemSelectionCondition-element för ExpressionBinding för CustomControl (format)
description: ItemSelectionCondition-element för ExpressionBinding för CustomControl (format)
ms.openlocfilehash: 38c88ad47e57cd20902c6b8aabdb0b8e8b682ba4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648037"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a><span data-ttu-id="70fee-103">ItemSelectionCondition-element för ExpressionBinding för CustomControl (format)</span><span class="sxs-lookup"><span data-stu-id="70fee-103">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>

<span data-ttu-id="70fee-104">Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="70fee-104">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="70fee-105">Det finns ingen gräns för antalet urvals villkor som kan anges för ett kontroll objekt.</span><span class="sxs-lookup"><span data-stu-id="70fee-105">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="70fee-106">Det här elementet används när du definierar en anpassad kontrol vy.</span><span class="sxs-lookup"><span data-stu-id="70fee-106">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="70fee-107">Konfigurations element (format) ViewDefinitions element (format) View-element (format) CustomControl-element (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) CustomItem-element för CustomEntry för View (format) ExpressionBinding-element för CustomItem för View (format) CustomControl-element för ItemSelectionCondition för View (format) CustomControl-element för för View</span><span class="sxs-lookup"><span data-stu-id="70fee-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="70fee-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="70fee-108">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="70fee-109">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="70fee-109">Attributes and Elements</span></span>

<span data-ttu-id="70fee-110">I följande avsnitt beskrivs attribut, underordnade element och `ItemSelectionCondition` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="70fee-110">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="70fee-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="70fee-111">Attributes</span></span>

<span data-ttu-id="70fee-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="70fee-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="70fee-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="70fee-113">Child Elements</span></span>

|<span data-ttu-id="70fee-114">Element</span><span class="sxs-lookup"><span data-stu-id="70fee-114">Element</span></span>|<span data-ttu-id="70fee-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="70fee-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="70fee-116">PropertyName-element för ItemSelectionCondition för CustomControl för visning (format</span><span class="sxs-lookup"><span data-stu-id="70fee-116">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="70fee-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="70fee-117">Optional element.</span></span><br /><br /> <span data-ttu-id="70fee-118">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="70fee-118">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="70fee-119">ScriptBlock-element för ItemSelectionCondition för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="70fee-119">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="70fee-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="70fee-120">Optional element.</span></span><br /><br /> <span data-ttu-id="70fee-121">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="70fee-121">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="70fee-122">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="70fee-122">Parent Elements</span></span>

|<span data-ttu-id="70fee-123">Element</span><span class="sxs-lookup"><span data-stu-id="70fee-123">Element</span></span>|<span data-ttu-id="70fee-124">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="70fee-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="70fee-125">ExpressionBinding-element för CustomItem för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="70fee-125">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="70fee-126">Definierar de data som visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="70fee-126">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="70fee-127">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="70fee-127">Remarks</span></span>

<span data-ttu-id="70fee-128">Du kan ange ett egenskaps namn eller ett skript för villkoret, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="70fee-128">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="70fee-129">Se även</span><span class="sxs-lookup"><span data-stu-id="70fee-129">See Also</span></span>

[<span data-ttu-id="70fee-130">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="70fee-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="70fee-131">ExpressionBinding-element för CustomItem för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="70fee-131">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
