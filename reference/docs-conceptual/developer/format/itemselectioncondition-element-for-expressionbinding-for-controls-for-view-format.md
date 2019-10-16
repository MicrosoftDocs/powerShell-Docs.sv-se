---
title: ItemSelectionCondition-element för ExpressionBinding för kontroller för vy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c15014-2440-410d-b02d-b7f1a49240a0
caps.latest.revision: 7
ms.openlocfilehash: 80f375c53c205c793600655fa6031d114871618e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354483"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="d5ad8-102">ItemSelectionCondition-element för ExpressionBinding för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="d5ad8-102">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="d5ad8-103">Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="d5ad8-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="d5ad8-104">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="d5ad8-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="d5ad8-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) styr element för Controls (format) CustomControl-element för kontroll för Control for View (format) CustomEntries-element för CustomControl för visnings-(format) CustomEntry-element för CustomEntries for Controls for View (format) CustomItem-elementet for CustomEntry for Controls for View (format) ExpressionBinding element for CustomItem for Controls for View (format) ItemSelectionCondition-element för ExpressionBinding för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="d5ad8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d5ad8-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="d5ad8-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d5ad8-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="d5ad8-107">Attributes and Elements</span></span>

<span data-ttu-id="d5ad8-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `ItemSelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="d5ad8-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d5ad8-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="d5ad8-109">Attributes</span></span>

<span data-ttu-id="d5ad8-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="d5ad8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d5ad8-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="d5ad8-111">Child Elements</span></span>

|<span data-ttu-id="d5ad8-112">Element</span><span class="sxs-lookup"><span data-stu-id="d5ad8-112">Element</span></span>|<span data-ttu-id="d5ad8-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d5ad8-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d5ad8-114">PropertyName-element för ItemSelectionCondition för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="d5ad8-114">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="d5ad8-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="d5ad8-115">Optional element.</span></span><br /><br /> <span data-ttu-id="d5ad8-116">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="d5ad8-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="d5ad8-117">Script block-element för ItemSelectionCondition för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="d5ad8-117">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="d5ad8-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="d5ad8-118">Optional element.</span></span><br /><br /> <span data-ttu-id="d5ad8-119">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="d5ad8-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d5ad8-120">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="d5ad8-120">Parent Elements</span></span>

|<span data-ttu-id="d5ad8-121">Element</span><span class="sxs-lookup"><span data-stu-id="d5ad8-121">Element</span></span>|<span data-ttu-id="d5ad8-122">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d5ad8-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d5ad8-123">ExpressionBinding-element för CustomItem för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="d5ad8-123">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="d5ad8-124">Definierar de data som visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="d5ad8-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d5ad8-125">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="d5ad8-125">Remarks</span></span>

<span data-ttu-id="d5ad8-126">Du kan ange ett egenskaps namn eller ett skript för villkoret, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="d5ad8-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="d5ad8-127">Se även</span><span class="sxs-lookup"><span data-stu-id="d5ad8-127">See Also</span></span>

[<span data-ttu-id="d5ad8-128">PropertyName-element för ItemSelectionCondition för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="d5ad8-128">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="d5ad8-129">Script block-element för ItemSelectionCondition för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="d5ad8-129">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="d5ad8-130">ExpressionBinding-element för CustomItem för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="d5ad8-130">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="d5ad8-131">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="d5ad8-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
