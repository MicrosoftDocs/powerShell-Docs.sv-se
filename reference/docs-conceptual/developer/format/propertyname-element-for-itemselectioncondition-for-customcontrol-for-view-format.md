---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName-element för ItemSelectionCondition för CustomControl för View (format)
description: PropertyName-element för ItemSelectionCondition för CustomControl för View (format)
ms.openlocfilehash: 5687bb781ce2db27b875f829147ee8b436f04adc
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666135"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="1e88f-103">PropertyName-element för ItemSelectionCondition för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="1e88f-103">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="1e88f-104">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="1e88f-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="1e88f-105">När den här egenskapen finns eller när den utvärderas `true` , uppfylls villkoret och kontrollen används.</span><span class="sxs-lookup"><span data-stu-id="1e88f-105">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="1e88f-106">Det här elementet används när du definierar en anpassad kontrol vy.</span><span class="sxs-lookup"><span data-stu-id="1e88f-106">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="1e88f-107">Konfigurations element (format) ViewDefinitions element (format) View element (format) CustomControl element (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) CustomItem-element för CustomEntry för visnings-(format) ExpressionBinding-element för CustomItem för CustomControl för View (format) ItemSelectionCondition-element för uttrycks bindning för CustomControl för View (format) PropertyName-element för ItemSelectionCondition för View (format</span><span class="sxs-lookup"><span data-stu-id="1e88f-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>

## <a name="syntax"></a><span data-ttu-id="1e88f-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="1e88f-108">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1e88f-109">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="1e88f-109">Attributes and Elements</span></span>

<span data-ttu-id="1e88f-110">I följande avsnitt beskrivs attribut, underordnade element och `PropertyName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="1e88f-110">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1e88f-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="1e88f-111">Attributes</span></span>

<span data-ttu-id="1e88f-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="1e88f-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1e88f-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="1e88f-113">Child Elements</span></span>

<span data-ttu-id="1e88f-114">Inga.</span><span class="sxs-lookup"><span data-stu-id="1e88f-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1e88f-115">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="1e88f-115">Parent Elements</span></span>

|<span data-ttu-id="1e88f-116">Element</span><span class="sxs-lookup"><span data-stu-id="1e88f-116">Element</span></span>|<span data-ttu-id="1e88f-117">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1e88f-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1e88f-118">ItemSelectionCondition-element för uttrycks bindning för CustomControl för vy (format)</span><span class="sxs-lookup"><span data-stu-id="1e88f-118">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="1e88f-119">Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="1e88f-119">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1e88f-120">Textvärde</span><span class="sxs-lookup"><span data-stu-id="1e88f-120">Text Value</span></span>

<span data-ttu-id="1e88f-121">Ange namnet på den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="1e88f-121">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="1e88f-122">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="1e88f-122">Remarks</span></span>

<span data-ttu-id="1e88f-123">Om det här elementet används kan du inte ange [script block](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) -elementet när du definierar urvals villkoret.</span><span class="sxs-lookup"><span data-stu-id="1e88f-123">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="1e88f-124">Se även</span><span class="sxs-lookup"><span data-stu-id="1e88f-124">See Also</span></span>

[<span data-ttu-id="1e88f-125">ScriptBlock-element för ItemSelectionCondition för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="1e88f-125">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="1e88f-126">ItemSelectionCondition-element för uttrycks bindning för CustomControl för vy (format)</span><span class="sxs-lookup"><span data-stu-id="1e88f-126">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="1e88f-127">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="1e88f-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
