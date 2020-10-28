---
ms.date: 09/13/2016
ms.topic: reference
title: ItemSelectionCondition-element för ExpressionBinding för Controls för Configuration (format)
description: ItemSelectionCondition-element för ExpressionBinding för Controls för Configuration (format)
ms.openlocfilehash: 6bd3d386ba64b33a1744fcc9e602cf13404765a0
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648084"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a><span data-ttu-id="94c03-103">ItemSelectionCondition-element för ExpressionBinding för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="94c03-103">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

<span data-ttu-id="94c03-104">Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="94c03-104">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="94c03-105">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="94c03-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="94c03-106">Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för konfiguration (format) CustomEntry-element för CustomControl for Controls for Configuration (format) CustomItem-elementet för CustomEntry för Controls för Configuration ExpressionBinding-element för CustomItem för Controls (format) ItemSelectionCondition-element för ExpressionBinding för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="94c03-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="94c03-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="94c03-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="94c03-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="94c03-108">Attributes and Elements</span></span>

<span data-ttu-id="94c03-109">I följande avsnitt beskrivs attribut, underordnade element och `ItemSelectionCondition` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="94c03-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="94c03-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="94c03-110">Attributes</span></span>

<span data-ttu-id="94c03-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="94c03-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="94c03-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="94c03-112">Child Elements</span></span>

|<span data-ttu-id="94c03-113">Element</span><span class="sxs-lookup"><span data-stu-id="94c03-113">Element</span></span>|<span data-ttu-id="94c03-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="94c03-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="94c03-115">PropertyName-element för ItemSelectionCondition för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="94c03-115">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="94c03-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="94c03-116">Optional element.</span></span><br /><br /> <span data-ttu-id="94c03-117">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="94c03-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="94c03-118">Script block-element för ItemSelectionCondition för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="94c03-118">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="94c03-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="94c03-119">Optional element.</span></span><br /><br /> <span data-ttu-id="94c03-120">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="94c03-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="94c03-121">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="94c03-121">Parent Elements</span></span>

|<span data-ttu-id="94c03-122">Element</span><span class="sxs-lookup"><span data-stu-id="94c03-122">Element</span></span>|<span data-ttu-id="94c03-123">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="94c03-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="94c03-124">ExpressionBinding-element för CustomItem för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="94c03-124">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="94c03-125">Definierar de data som visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="94c03-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="94c03-126">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="94c03-126">Remarks</span></span>

<span data-ttu-id="94c03-127">Du kan ange ett egenskaps namn eller ett skript för villkoret, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="94c03-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="94c03-128">Se även</span><span class="sxs-lookup"><span data-stu-id="94c03-128">See Also</span></span>

[<span data-ttu-id="94c03-129">PropertyName-element för ItemSelectionCondition för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="94c03-129">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="94c03-130">Script block-element för ItemSelectionCondition för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="94c03-130">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="94c03-131">ExpressionBinding-element för CustomItem för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="94c03-131">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="94c03-132">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="94c03-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
