---
title: ItemSelectionCondition Element för ExpressionBinding för kontroller för konfiguration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd3ddc33-b21c-4464-b3f2-a78dbe0062a8
caps.latest.revision: 8
ms.openlocfilehash: 4865d716ebe0460b662253a3019e93e82428b882
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065520"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a><span data-ttu-id="33520-102">ItemSelectionCondition-element för ExpressionBinding för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="33520-102">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

<span data-ttu-id="33520-103">Definierar de villkor som måste finnas för den här kontrollen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="33520-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="33520-104">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="33520-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="33520-105">Konfigurationselementet Element (Format) kontroller av (Format) kontroll konfigurationselement för kontroller för (Format) anpassad kontroll konfigurationselement för kontroll för (Format) CustomEntries konfigurationselement för anpassad kontroll för konfiguration ( Format) CustomEntry Element för anpassad kontroll för kontroller för (Format) CustomItem konfigurationselement för CustomEntry för kontroller för ExpressionBinding konfigurationselement för CustomItem för kontroller för konfiguration (Format) ItemSelectionCondition Element för ExpressionBinding för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="33520-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="33520-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="33520-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="33520-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="33520-107">Attributes and Elements</span></span>

<span data-ttu-id="33520-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ItemSelectionCondition` element.</span><span class="sxs-lookup"><span data-stu-id="33520-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="33520-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="33520-109">Attributes</span></span>

<span data-ttu-id="33520-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="33520-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="33520-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="33520-111">Child Elements</span></span>

|<span data-ttu-id="33520-112">Element</span><span class="sxs-lookup"><span data-stu-id="33520-112">Element</span></span>|<span data-ttu-id="33520-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33520-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="33520-114">PropertyName-Element för ItemSelectionCondition för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="33520-114">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="33520-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="33520-115">Optional element.</span></span><br /><br /> <span data-ttu-id="33520-116">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="33520-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="33520-117">ScriptBlock Element för ItemSelectionCondition för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="33520-117">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="33520-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="33520-118">Optional element.</span></span><br /><br /> <span data-ttu-id="33520-119">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="33520-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="33520-120">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="33520-120">Parent Elements</span></span>

|<span data-ttu-id="33520-121">Element</span><span class="sxs-lookup"><span data-stu-id="33520-121">Element</span></span>|<span data-ttu-id="33520-122">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="33520-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="33520-123">ExpressionBinding Element för CustomItem för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="33520-123">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="33520-124">Definierar de data som visas i kontrollen.</span><span class="sxs-lookup"><span data-stu-id="33520-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="33520-125">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="33520-125">Remarks</span></span>

<span data-ttu-id="33520-126">Du kan ange ett egenskapsnamn eller ett skript för det här villkoret men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="33520-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="33520-127">Se även</span><span class="sxs-lookup"><span data-stu-id="33520-127">See Also</span></span>

[<span data-ttu-id="33520-128">PropertyName-Element för ItemSelectionCondition för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="33520-128">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="33520-129">ScriptBlock Element för ItemSelectionCondition för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="33520-129">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="33520-130">ExpressionBinding Element för CustomItem för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="33520-130">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="33520-131">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="33520-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
