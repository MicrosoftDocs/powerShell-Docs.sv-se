---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName-element för ItemSelectionCondition för Controls för View (format)
description: PropertyName-element för ItemSelectionCondition för Controls för View (format)
ms.openlocfilehash: 9fb7a21e19338dbf59dab14291e1b02736835040
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645807"
---
# <a name="propertyname-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="96a62-103">PropertyName-element för ItemSelectionCondition för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="96a62-103">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="96a62-104">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="96a62-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="96a62-105">När den här egenskapen finns eller när den utvärderas `true` , uppfylls villkoret och kontrollen används.</span><span class="sxs-lookup"><span data-stu-id="96a62-105">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="96a62-106">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="96a62-106">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="96a62-107">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) styr element (format) kontroll element (format) styr element (format) kontroll element för Controls for View (format) CustomControl-element för Control for View (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för för Controls for View (format) CustomItem-element för CustomEntry for Controls for View (format) ExpressionBinding-element för CustomItem for Controls for View (format) ItemSelectionCondition element of ExpressionBinding for Controls for View (format) elementet PropertyName for ItemSelectionCondition for Controls for View (format)</span><span class="sxs-lookup"><span data-stu-id="96a62-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="96a62-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="96a62-108">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="96a62-109">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="96a62-109">Attributes and Elements</span></span>

<span data-ttu-id="96a62-110">I följande avsnitt beskrivs attribut, underordnade element och `PropertyName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="96a62-110">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="96a62-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="96a62-111">Attributes</span></span>

<span data-ttu-id="96a62-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="96a62-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="96a62-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="96a62-113">Child Elements</span></span>

<span data-ttu-id="96a62-114">Inga.</span><span class="sxs-lookup"><span data-stu-id="96a62-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="96a62-115">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="96a62-115">Parent Elements</span></span>

|<span data-ttu-id="96a62-116">Element</span><span class="sxs-lookup"><span data-stu-id="96a62-116">Element</span></span>|<span data-ttu-id="96a62-117">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="96a62-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="96a62-118">ItemSelectionCondition-element för ExpressionBinding för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="96a62-118">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="96a62-119">Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="96a62-119">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="96a62-120">Textvärde</span><span class="sxs-lookup"><span data-stu-id="96a62-120">Text Value</span></span>

<span data-ttu-id="96a62-121">Ange namnet på den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="96a62-121">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="96a62-122">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="96a62-122">Remarks</span></span>

<span data-ttu-id="96a62-123">Om det här elementet används kan du inte ange [script block](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) -elementet när du definierar urvals villkoret.</span><span class="sxs-lookup"><span data-stu-id="96a62-123">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="96a62-124">Se även</span><span class="sxs-lookup"><span data-stu-id="96a62-124">See Also</span></span>

[<span data-ttu-id="96a62-125">ScriptBlock-element för ItemSelectionCondition för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="96a62-125">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="96a62-126">ItemSelectionCondition-element för ExpressionBinding för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="96a62-126">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="96a62-127">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="96a62-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
