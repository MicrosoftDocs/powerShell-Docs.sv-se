---
title: ItemSelectionCondition-element för ExpressionBinding for GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6af3be7d-921e-4cf7-bd5a-d87aa0b4efbd
caps.latest.revision: 7
ms.openlocfilehash: b2b0a0d1996392614807e08b820a72978e38a0cb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356128"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="8263a-102">ItemSelectionCondition-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="8263a-102">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="8263a-103">Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="8263a-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="8263a-104">Det finns ingen gräns för antalet urvals villkor som kan anges för ett kontroll objekt.</span><span class="sxs-lookup"><span data-stu-id="8263a-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="8263a-105">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="8263a-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="8263a-106">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element för CustomControl for GroupBy (format) CustomItem-element för CustomEntry för GroupBy (format) ExpressionBinding-element för CustomItem för GroupBy (format) ItemSelectionCondition-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="8263a-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8263a-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="8263a-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8263a-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="8263a-108">Attributes and Elements</span></span>

<span data-ttu-id="8263a-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `ItemSelectionCondition`-elementet.</span><span class="sxs-lookup"><span data-stu-id="8263a-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8263a-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="8263a-110">Attributes</span></span>

<span data-ttu-id="8263a-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="8263a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8263a-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="8263a-112">Child Elements</span></span>

|<span data-ttu-id="8263a-113">Element</span><span class="sxs-lookup"><span data-stu-id="8263a-113">Element</span></span>|<span data-ttu-id="8263a-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8263a-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8263a-115">PropertyName-element för ItemSelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="8263a-115">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="8263a-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="8263a-116">Optional element.</span></span><br /><br /> <span data-ttu-id="8263a-117">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="8263a-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="8263a-118">Script block-element för ItemSelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="8263a-118">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="8263a-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="8263a-119">Optional element.</span></span><br /><br /> <span data-ttu-id="8263a-120">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="8263a-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8263a-121">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="8263a-121">Parent Elements</span></span>

|<span data-ttu-id="8263a-122">Element</span><span class="sxs-lookup"><span data-stu-id="8263a-122">Element</span></span>|<span data-ttu-id="8263a-123">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8263a-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8263a-124">ExpressionBinding-element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="8263a-124">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="8263a-125">Definierar de data som visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="8263a-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8263a-126">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="8263a-126">Remarks</span></span>

<span data-ttu-id="8263a-127">Du kan ange ett egenskaps namn eller ett skript för villkoret, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="8263a-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="8263a-128">Se även</span><span class="sxs-lookup"><span data-stu-id="8263a-128">See Also</span></span>

[<span data-ttu-id="8263a-129">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="8263a-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="8263a-130">ExpressionBinding-element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="8263a-130">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)
