---
title: PropertyName-element för ItemSelectionCondition för kontroller för vy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c6517b8f63e0511ce071926ac3ac39ba82e7ed21
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783491"
---
# <a name="propertyname-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="20f7d-102">PropertyName-element för ItemSelectionCondition för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="20f7d-102">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="20f7d-103">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="20f7d-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="20f7d-104">När den här egenskapen finns eller när den utvärderas `true` , uppfylls villkoret och kontrollen används.</span><span class="sxs-lookup"><span data-stu-id="20f7d-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="20f7d-105">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="20f7d-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="20f7d-106">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) styr element (format) kontroll element (format) styr element (format) kontroll element för Controls for View (format) CustomControl-element för Control for View (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för för Controls for View (format) CustomItem-element för CustomEntry for Controls for View (format) ExpressionBinding-element för CustomItem for Controls for View (format) ItemSelectionCondition element of ExpressionBinding for Controls for View (format) elementet PropertyName for ItemSelectionCondition for Controls for View (format)</span><span class="sxs-lookup"><span data-stu-id="20f7d-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="20f7d-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="20f7d-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="20f7d-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="20f7d-108">Attributes and Elements</span></span>

<span data-ttu-id="20f7d-109">I följande avsnitt beskrivs attribut, underordnade element och `PropertyName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="20f7d-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="20f7d-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="20f7d-110">Attributes</span></span>

<span data-ttu-id="20f7d-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="20f7d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="20f7d-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="20f7d-112">Child Elements</span></span>

<span data-ttu-id="20f7d-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="20f7d-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="20f7d-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="20f7d-114">Parent Elements</span></span>

|<span data-ttu-id="20f7d-115">Element</span><span class="sxs-lookup"><span data-stu-id="20f7d-115">Element</span></span>|<span data-ttu-id="20f7d-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="20f7d-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="20f7d-117">ItemSelectionCondition-element för ExpressionBinding för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="20f7d-117">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="20f7d-118">Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="20f7d-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="20f7d-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="20f7d-119">Text Value</span></span>

<span data-ttu-id="20f7d-120">Ange namnet på den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="20f7d-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="20f7d-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="20f7d-121">Remarks</span></span>

<span data-ttu-id="20f7d-122">Om det här elementet används kan du inte ange [script block](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) -elementet när du definierar urvals villkoret.</span><span class="sxs-lookup"><span data-stu-id="20f7d-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="20f7d-123">Se även</span><span class="sxs-lookup"><span data-stu-id="20f7d-123">See Also</span></span>

[<span data-ttu-id="20f7d-124">ScriptBlock-element för ItemSelectionCondition för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="20f7d-124">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="20f7d-125">ItemSelectionCondition-element för ExpressionBinding för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="20f7d-125">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="20f7d-126">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="20f7d-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
