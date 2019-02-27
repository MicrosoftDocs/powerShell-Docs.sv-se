---
title: ItemSelectionCondition Element för ExpressionBinding för anpassad kontroll (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4bea9d8-27ad-410e-ad48-287f807d3e4e
caps.latest.revision: 7
ms.openlocfilehash: 18b0113c9b7b0895a1093cb0b56cd2d02c74a6c1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848344"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a><span data-ttu-id="e0db4-102">ItemSelectionCondition-element för ExpressionBinding för CustomControl (format)</span><span class="sxs-lookup"><span data-stu-id="e0db4-102">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>

<span data-ttu-id="e0db4-103">Definierar de villkor som måste finnas för den här kontrollen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="e0db4-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="e0db4-104">Det finns ingen gräns för hur många val av villkor som kan anges för ett kontrollobjekt.</span><span class="sxs-lookup"><span data-stu-id="e0db4-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="e0db4-105">Det här elementet används när du definierar en anpassad kontroll vy.</span><span class="sxs-lookup"><span data-stu-id="e0db4-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="e0db4-106">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) anpassad kontroll Element (Format) CustomEntries konfigurationselement för anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för vyn (Format) CustomItem elementet för CustomEntry för Visa (Format) ExpressionBinding elementet för CustomItem för anpassad kontroll för Visa (Format) ItemSelectionCondition elementet för uttrycket bindningen för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="e0db4-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e0db4-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="e0db4-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e0db4-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="e0db4-108">Attributes and Elements</span></span>

<span data-ttu-id="e0db4-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ItemSelectionCondition` element.</span><span class="sxs-lookup"><span data-stu-id="e0db4-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e0db4-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="e0db4-110">Attributes</span></span>

<span data-ttu-id="e0db4-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="e0db4-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e0db4-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="e0db4-112">Child Elements</span></span>

|<span data-ttu-id="e0db4-113">Element</span><span class="sxs-lookup"><span data-stu-id="e0db4-113">Element</span></span>|<span data-ttu-id="e0db4-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e0db4-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e0db4-115">PropertyName-Element för ItemSelectionCondition för anpassad kontroll för vy (Format</span><span class="sxs-lookup"><span data-stu-id="e0db4-115">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="e0db4-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e0db4-116">Optional element.</span></span><br /><br /> <span data-ttu-id="e0db4-117">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="e0db4-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="e0db4-118">ScriptBlock Element för ItemSelectionCondition för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="e0db4-118">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="e0db4-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e0db4-119">Optional element.</span></span><br /><br /> <span data-ttu-id="e0db4-120">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="e0db4-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e0db4-121">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="e0db4-121">Parent Elements</span></span>

|<span data-ttu-id="e0db4-122">Element</span><span class="sxs-lookup"><span data-stu-id="e0db4-122">Element</span></span>|<span data-ttu-id="e0db4-123">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e0db4-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e0db4-124">ExpressionBinding Element för CustomItem för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="e0db4-124">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="e0db4-125">Definierar de data som visas i kontrollen.</span><span class="sxs-lookup"><span data-stu-id="e0db4-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e0db4-126">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="e0db4-126">Remarks</span></span>

<span data-ttu-id="e0db4-127">Du kan ange ett egenskapsnamn eller ett skript för det här villkoret men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="e0db4-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="e0db4-128">Se även</span><span class="sxs-lookup"><span data-stu-id="e0db4-128">See Also</span></span>

[<span data-ttu-id="e0db4-129">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="e0db4-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="e0db4-130">ExpressionBinding Element för CustomItem för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="e0db4-130">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
