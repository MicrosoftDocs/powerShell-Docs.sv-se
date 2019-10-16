---
title: ItemSelectionCondition-element för ExpressionBinding för kontroll av konfiguration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd3ddc33-b21c-4464-b3f2-a78dbe0062a8
caps.latest.revision: 8
ms.openlocfilehash: 4865d716ebe0460b662253a3019e93e82428b882
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354469"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a><span data-ttu-id="11933-102">ItemSelectionCondition-element för ExpressionBinding för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="11933-102">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

<span data-ttu-id="11933-103">Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="11933-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="11933-104">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="11933-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="11933-105">Konfigurations element (format) styr element i konfigurations-(format) kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för konfiguration ( Format) CustomEntry-element för CustomControl for Controls for Configuration (format) CustomItem element for CustomEntry for Controls for Configuration ExpressionBinding element for CustomItem for Controls for Configuration (format) ItemSelectionCondition-element för ExpressionBinding för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="11933-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="11933-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="11933-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="11933-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="11933-107">Attributes and Elements</span></span>

<span data-ttu-id="11933-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `ItemSelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="11933-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="11933-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="11933-109">Attributes</span></span>

<span data-ttu-id="11933-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="11933-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="11933-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="11933-111">Child Elements</span></span>

|<span data-ttu-id="11933-112">Element</span><span class="sxs-lookup"><span data-stu-id="11933-112">Element</span></span>|<span data-ttu-id="11933-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11933-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="11933-114">PropertyName-element för ItemSelectionCondition för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="11933-114">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="11933-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="11933-115">Optional element.</span></span><br /><br /> <span data-ttu-id="11933-116">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="11933-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="11933-117">Script block-element för ItemSelectionCondition för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="11933-117">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="11933-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="11933-118">Optional element.</span></span><br /><br /> <span data-ttu-id="11933-119">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="11933-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="11933-120">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="11933-120">Parent Elements</span></span>

|<span data-ttu-id="11933-121">Element</span><span class="sxs-lookup"><span data-stu-id="11933-121">Element</span></span>|<span data-ttu-id="11933-122">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11933-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="11933-123">ExpressionBinding-element för CustomItem för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="11933-123">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="11933-124">Definierar de data som visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="11933-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="11933-125">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="11933-125">Remarks</span></span>

<span data-ttu-id="11933-126">Du kan ange ett egenskaps namn eller ett skript för villkoret, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="11933-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="11933-127">Se även</span><span class="sxs-lookup"><span data-stu-id="11933-127">See Also</span></span>

[<span data-ttu-id="11933-128">PropertyName-element för ItemSelectionCondition för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="11933-128">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="11933-129">Script block-element för ItemSelectionCondition för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="11933-129">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="11933-130">ExpressionBinding-element för CustomItem för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="11933-130">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="11933-131">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="11933-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
