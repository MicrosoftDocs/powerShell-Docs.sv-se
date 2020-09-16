---
title: ItemSelectionCondition-element för ExpressionBinding för CustomControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6a5c66a63c02980b16c2d2d9dd689410c8aec51c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781196"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a><span data-ttu-id="803f6-102">ItemSelectionCondition-element för ExpressionBinding för CustomControl (format)</span><span class="sxs-lookup"><span data-stu-id="803f6-102">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>

<span data-ttu-id="803f6-103">Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="803f6-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="803f6-104">Det finns ingen gräns för antalet urvals villkor som kan anges för ett kontroll objekt.</span><span class="sxs-lookup"><span data-stu-id="803f6-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="803f6-105">Det här elementet används när du definierar en anpassad kontrol vy.</span><span class="sxs-lookup"><span data-stu-id="803f6-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="803f6-106">Konfigurations element (format) ViewDefinitions element (format) View-element (format) CustomControl-element (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) CustomItem-element för CustomEntry för View (format) ExpressionBinding-element för CustomItem för View (format) CustomControl-element för ItemSelectionCondition för View (format) CustomControl-element för för View</span><span class="sxs-lookup"><span data-stu-id="803f6-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="803f6-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="803f6-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="803f6-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="803f6-108">Attributes and Elements</span></span>

<span data-ttu-id="803f6-109">I följande avsnitt beskrivs attribut, underordnade element och `ItemSelectionCondition` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="803f6-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="803f6-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="803f6-110">Attributes</span></span>

<span data-ttu-id="803f6-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="803f6-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="803f6-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="803f6-112">Child Elements</span></span>

|<span data-ttu-id="803f6-113">Element</span><span class="sxs-lookup"><span data-stu-id="803f6-113">Element</span></span>|<span data-ttu-id="803f6-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="803f6-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="803f6-115">PropertyName-element för ItemSelectionCondition för CustomControl för visning (format</span><span class="sxs-lookup"><span data-stu-id="803f6-115">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="803f6-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="803f6-116">Optional element.</span></span><br /><br /> <span data-ttu-id="803f6-117">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="803f6-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="803f6-118">ScriptBlock-element för ItemSelectionCondition för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="803f6-118">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="803f6-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="803f6-119">Optional element.</span></span><br /><br /> <span data-ttu-id="803f6-120">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="803f6-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="803f6-121">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="803f6-121">Parent Elements</span></span>

|<span data-ttu-id="803f6-122">Element</span><span class="sxs-lookup"><span data-stu-id="803f6-122">Element</span></span>|<span data-ttu-id="803f6-123">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="803f6-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="803f6-124">ExpressionBinding-element för CustomItem för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="803f6-124">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="803f6-125">Definierar de data som visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="803f6-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="803f6-126">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="803f6-126">Remarks</span></span>

<span data-ttu-id="803f6-127">Du kan ange ett egenskaps namn eller ett skript för villkoret, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="803f6-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="803f6-128">Se även</span><span class="sxs-lookup"><span data-stu-id="803f6-128">See Also</span></span>

[<span data-ttu-id="803f6-129">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="803f6-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="803f6-130">ExpressionBinding-element för CustomItem för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="803f6-130">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
