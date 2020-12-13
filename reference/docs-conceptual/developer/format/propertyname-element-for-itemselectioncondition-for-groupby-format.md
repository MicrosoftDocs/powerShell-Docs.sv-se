---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName-element för ItemSelectionCondition för GroupBy (format)
description: PropertyName-element för ItemSelectionCondition för GroupBy (format)
ms.openlocfilehash: 9667a389ded33d0744f0f7f8d739635a8b21d98b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666118"
---
# <a name="propertyname-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="0ebf8-103">PropertyName-element för ItemSelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="0ebf8-103">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="0ebf8-104">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="0ebf8-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="0ebf8-105">När den här egenskapen finns eller när den utvärderas `true` , uppfylls villkoret och kontrollen används.</span><span class="sxs-lookup"><span data-stu-id="0ebf8-105">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="0ebf8-106">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="0ebf8-106">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="0ebf8-107">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element för CustomControl för GroupBy (format) CustomItem-element för CustomEntry for GroupBy (format) ExpressionBinding-element för CustomItem for GroupBy (format) ItemSelectionCondition element for ExpressionBinding for GroupBy (format) elementet PropertyName för ItemSelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="0ebf8-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0ebf8-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="0ebf8-108">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0ebf8-109">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="0ebf8-109">Attributes and Elements</span></span>

<span data-ttu-id="0ebf8-110">I följande avsnitt beskrivs attribut, underordnade element och `PropertyName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="0ebf8-110">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0ebf8-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="0ebf8-111">Attributes</span></span>

<span data-ttu-id="0ebf8-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="0ebf8-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0ebf8-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="0ebf8-113">Child Elements</span></span>

<span data-ttu-id="0ebf8-114">Inga.</span><span class="sxs-lookup"><span data-stu-id="0ebf8-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0ebf8-115">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="0ebf8-115">Parent Elements</span></span>

|<span data-ttu-id="0ebf8-116">Element</span><span class="sxs-lookup"><span data-stu-id="0ebf8-116">Element</span></span>|<span data-ttu-id="0ebf8-117">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0ebf8-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0ebf8-118">ItemSelectionCondition-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="0ebf8-118">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="0ebf8-119">Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="0ebf8-119">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0ebf8-120">Textvärde</span><span class="sxs-lookup"><span data-stu-id="0ebf8-120">Text Value</span></span>

<span data-ttu-id="0ebf8-121">Ange namnet på den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="0ebf8-121">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="0ebf8-122">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="0ebf8-122">Remarks</span></span>

<span data-ttu-id="0ebf8-123">Om det här elementet används kan du inte ange [script block](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) -elementet när du definierar urvals villkoret.</span><span class="sxs-lookup"><span data-stu-id="0ebf8-123">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ebf8-124">Se även</span><span class="sxs-lookup"><span data-stu-id="0ebf8-124">See Also</span></span>

[<span data-ttu-id="0ebf8-125">ScriptBlock-element för ItemSelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="0ebf8-125">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="0ebf8-126">ItemSelectionCondition-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="0ebf8-126">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="0ebf8-127">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="0ebf8-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
