---
ms.date: 09/13/2016
ms.topic: reference
title: ScriptBlock-element för ItemSelectionCondition för GroupBy (format)
description: ScriptBlock-element för ItemSelectionCondition för GroupBy (format)
ms.openlocfilehash: fe366fa31b93e8d69409cc49c3fe2c350d4d06d9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665087"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="a7169-103">ScriptBlock-element för ItemSelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="a7169-103">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="a7169-104">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="a7169-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="a7169-105">När det här skriptet utvärderas `true` , uppfylls villkoret och kontrollen används.</span><span class="sxs-lookup"><span data-stu-id="a7169-105">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="a7169-106">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="a7169-106">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="a7169-107">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element för CustomControl för GroupBy (format) CustomItem-element för CustomEntry for GroupBy (format) ExpressionBinding-element för CustomItem for GroupBy (format) ItemSelectionCondition-element för ExpressionBinding för GroupBy (format) script block element for ItemSelectionCondition for groupby (format)</span><span class="sxs-lookup"><span data-stu-id="a7169-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a7169-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="a7169-108">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a7169-109">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="a7169-109">Attributes and Elements</span></span>

<span data-ttu-id="a7169-110">I följande avsnitt beskrivs attribut, underordnade element och `ScriptBlock` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="a7169-110">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a7169-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="a7169-111">Attributes</span></span>

<span data-ttu-id="a7169-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="a7169-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a7169-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="a7169-113">Child Elements</span></span>

<span data-ttu-id="a7169-114">Inga.</span><span class="sxs-lookup"><span data-stu-id="a7169-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a7169-115">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="a7169-115">Parent Elements</span></span>

|<span data-ttu-id="a7169-116">Element</span><span class="sxs-lookup"><span data-stu-id="a7169-116">Element</span></span>|<span data-ttu-id="a7169-117">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a7169-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a7169-118">ItemSelectionCondition-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="a7169-118">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="a7169-119">Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="a7169-119">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a7169-120">Textvärde</span><span class="sxs-lookup"><span data-stu-id="a7169-120">Text Value</span></span>

<span data-ttu-id="a7169-121">Ange det skript som utvärderas.</span><span class="sxs-lookup"><span data-stu-id="a7169-121">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="a7169-122">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="a7169-122">Remarks</span></span>

<span data-ttu-id="a7169-123">Om det här elementet används kan du inte ange elementet [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) när du definierar urvals villkoret.</span><span class="sxs-lookup"><span data-stu-id="a7169-123">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="a7169-124">Se även</span><span class="sxs-lookup"><span data-stu-id="a7169-124">See Also</span></span>

[<span data-ttu-id="a7169-125">ItemSelectionCondition-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="a7169-125">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="a7169-126">PropertyName-element för ItemSelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="a7169-126">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="a7169-127">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="a7169-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
