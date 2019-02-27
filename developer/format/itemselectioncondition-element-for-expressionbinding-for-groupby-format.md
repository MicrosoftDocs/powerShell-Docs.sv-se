---
title: ItemSelectionCondition Element för ExpressionBinding för GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6af3be7d-921e-4cf7-bd5a-d87aa0b4efbd
caps.latest.revision: 7
ms.openlocfilehash: b2b0a0d1996392614807e08b820a72978e38a0cb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844809"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="8fcb5-102">ItemSelectionCondition-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="8fcb5-102">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="8fcb5-103">Definierar de villkor som måste finnas för den här kontrollen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="8fcb5-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="8fcb5-104">Det finns ingen gräns för hur många val av villkor som kan anges för ett kontrollobjekt.</span><span class="sxs-lookup"><span data-stu-id="8fcb5-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="8fcb5-105">Det här elementet används när du definierar hur en ny grupp med objekt visas.</span><span class="sxs-lookup"><span data-stu-id="8fcb5-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="8fcb5-106">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för Visa (Format) anpassad kontroll elementet för GroupBy (Format) CustomEntries Element för anpassad kontroll för GroupBy (Format) CustomEntry elementet för Anpassad kontroll för GroupBy (Format) CustomItem elementet för CustomEntry för GroupBy (Format) ExpressionBinding elementet för CustomItem för GroupBy (Format) ItemSelectionCondition elementet för ExpressionBinding för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="8fcb5-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8fcb5-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="8fcb5-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8fcb5-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="8fcb5-108">Attributes and Elements</span></span>

<span data-ttu-id="8fcb5-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ItemSelectionCondition` element.</span><span class="sxs-lookup"><span data-stu-id="8fcb5-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8fcb5-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="8fcb5-110">Attributes</span></span>

<span data-ttu-id="8fcb5-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="8fcb5-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8fcb5-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="8fcb5-112">Child Elements</span></span>

|<span data-ttu-id="8fcb5-113">Element</span><span class="sxs-lookup"><span data-stu-id="8fcb5-113">Element</span></span>|<span data-ttu-id="8fcb5-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8fcb5-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8fcb5-115">PropertyName-Element för ItemSelectionCondition för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="8fcb5-115">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="8fcb5-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="8fcb5-116">Optional element.</span></span><br /><br /> <span data-ttu-id="8fcb5-117">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="8fcb5-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="8fcb5-118">ScriptBlock Element för ItemSelectionCondition för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="8fcb5-118">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="8fcb5-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="8fcb5-119">Optional element.</span></span><br /><br /> <span data-ttu-id="8fcb5-120">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="8fcb5-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8fcb5-121">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="8fcb5-121">Parent Elements</span></span>

|<span data-ttu-id="8fcb5-122">Element</span><span class="sxs-lookup"><span data-stu-id="8fcb5-122">Element</span></span>|<span data-ttu-id="8fcb5-123">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8fcb5-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8fcb5-124">ExpressionBinding Element för CustomItem för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="8fcb5-124">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="8fcb5-125">Definierar de data som visas i kontrollen.</span><span class="sxs-lookup"><span data-stu-id="8fcb5-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8fcb5-126">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="8fcb5-126">Remarks</span></span>

<span data-ttu-id="8fcb5-127">Du kan ange ett egenskapsnamn eller ett skript för det här villkoret men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="8fcb5-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="8fcb5-128">Se även</span><span class="sxs-lookup"><span data-stu-id="8fcb5-128">See Also</span></span>

[<span data-ttu-id="8fcb5-129">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="8fcb5-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="8fcb5-130">ExpressionBinding Element för CustomItem för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="8fcb5-130">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)
