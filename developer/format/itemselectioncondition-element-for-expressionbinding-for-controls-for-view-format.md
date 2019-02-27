---
title: ItemSelectionCondition Element för ExpressionBinding för kontroller för att visa (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c15014-2440-410d-b02d-b7f1a49240a0
caps.latest.revision: 7
ms.openlocfilehash: 80f375c53c205c793600655fa6031d114871618e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850906"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="87426-102">ItemSelectionCondition-element för ExpressionBinding för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="87426-102">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="87426-103">Definierar de villkor som måste finnas för den här kontrollen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="87426-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="87426-104">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="87426-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="87426-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) kontroller Element (Format) kontroll konfigurationselement för kontroller för att visa (Format) anpassad kontroll Element för kontroll för kontroller för att visa (Format) CustomEntries Element för Anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för kontroller för att visa (Format) CustomItem Element för CustomEntry för kontroller för att visa (Format) ExpressionBinding Element för CustomItem för kontroller för att visa (Format) ItemSelectionCondition Element i ExpressionBinding för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="87426-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="87426-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="87426-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="87426-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="87426-107">Attributes and Elements</span></span>

<span data-ttu-id="87426-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ItemSelectionCondition` element.</span><span class="sxs-lookup"><span data-stu-id="87426-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="87426-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="87426-109">Attributes</span></span>

<span data-ttu-id="87426-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="87426-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="87426-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="87426-111">Child Elements</span></span>

|<span data-ttu-id="87426-112">Element</span><span class="sxs-lookup"><span data-stu-id="87426-112">Element</span></span>|<span data-ttu-id="87426-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="87426-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="87426-114">PropertyName-Element för ItemSelectionCondition för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="87426-114">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="87426-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="87426-115">Optional element.</span></span><br /><br /> <span data-ttu-id="87426-116">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="87426-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="87426-117">ScriptBlock Element för ItemSelectionCondition för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="87426-117">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="87426-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="87426-118">Optional element.</span></span><br /><br /> <span data-ttu-id="87426-119">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="87426-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="87426-120">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="87426-120">Parent Elements</span></span>

|<span data-ttu-id="87426-121">Element</span><span class="sxs-lookup"><span data-stu-id="87426-121">Element</span></span>|<span data-ttu-id="87426-122">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="87426-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="87426-123">ExpressionBinding Element för CustomItem för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="87426-123">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="87426-124">Definierar de data som visas i kontrollen.</span><span class="sxs-lookup"><span data-stu-id="87426-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="87426-125">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="87426-125">Remarks</span></span>

<span data-ttu-id="87426-126">Du kan ange ett egenskapsnamn eller ett skript för det här villkoret men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="87426-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="87426-127">Se även</span><span class="sxs-lookup"><span data-stu-id="87426-127">See Also</span></span>

[<span data-ttu-id="87426-128">PropertyName-Element för ItemSelectionCondition för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="87426-128">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="87426-129">ScriptBlock Element för ItemSelectionCondition för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="87426-129">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="87426-130">ExpressionBinding Element för CustomItem för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="87426-130">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="87426-131">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="87426-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
