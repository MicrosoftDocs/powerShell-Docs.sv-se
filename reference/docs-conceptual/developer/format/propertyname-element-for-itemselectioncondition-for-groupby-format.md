---
title: PropertyName-element för ItemSelectionCondition för GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: f6d671035bfd2ef6323b638fdd951bb020bd6548
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780890"
---
# <a name="propertyname-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="0310f-102">PropertyName-element för ItemSelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="0310f-102">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="0310f-103">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="0310f-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="0310f-104">När den här egenskapen finns eller när den utvärderas `true` , uppfylls villkoret och kontrollen används.</span><span class="sxs-lookup"><span data-stu-id="0310f-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="0310f-105">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="0310f-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="0310f-106">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element för CustomControl för GroupBy (format) CustomItem-element för CustomEntry for GroupBy (format) ExpressionBinding-element för CustomItem for GroupBy (format) ItemSelectionCondition element for ExpressionBinding for GroupBy (format) elementet PropertyName för ItemSelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="0310f-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0310f-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="0310f-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0310f-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="0310f-108">Attributes and Elements</span></span>

<span data-ttu-id="0310f-109">I följande avsnitt beskrivs attribut, underordnade element och `PropertyName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="0310f-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0310f-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="0310f-110">Attributes</span></span>

<span data-ttu-id="0310f-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="0310f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0310f-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="0310f-112">Child Elements</span></span>

<span data-ttu-id="0310f-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="0310f-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0310f-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="0310f-114">Parent Elements</span></span>

|<span data-ttu-id="0310f-115">Element</span><span class="sxs-lookup"><span data-stu-id="0310f-115">Element</span></span>|<span data-ttu-id="0310f-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0310f-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0310f-117">ItemSelectionCondition-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="0310f-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="0310f-118">Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="0310f-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0310f-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="0310f-119">Text Value</span></span>

<span data-ttu-id="0310f-120">Ange namnet på den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="0310f-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="0310f-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="0310f-121">Remarks</span></span>

<span data-ttu-id="0310f-122">Om det här elementet används kan du inte ange [script block](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) -elementet när du definierar urvals villkoret.</span><span class="sxs-lookup"><span data-stu-id="0310f-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="0310f-123">Se även</span><span class="sxs-lookup"><span data-stu-id="0310f-123">See Also</span></span>

[<span data-ttu-id="0310f-124">ScriptBlock-element för ItemSelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="0310f-124">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="0310f-125">ItemSelectionCondition-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="0310f-125">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="0310f-126">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="0310f-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
