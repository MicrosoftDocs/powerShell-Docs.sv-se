---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName-element för ItemSeclectionCondition för Controls för Configuration (format)
description: PropertyName-element för ItemSeclectionCondition för Controls för Configuration (format)
ms.openlocfilehash: 860683eb54b2a3579767640c1d3f0937897b8f8e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655124"
---
# <a name="propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="b78ff-103">PropertyName-element för ItemSeclectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="b78ff-103">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="b78ff-104">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="b78ff-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="b78ff-105">När den här egenskapen finns eller när den utvärderas `true` , uppfylls villkoret och kontrollen används.</span><span class="sxs-lookup"><span data-stu-id="b78ff-105">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="b78ff-106">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="b78ff-106">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="b78ff-107">Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för Configuration (format) CustomEntry-element för CustomControl för kontroller för konfiguration (format) CustomItem-element för CustomEntry for Controls for Configuration ExpressionBinding-element för CustomItem for Controls for Configuration (format) ItemSelectionCondition-element för ExpressionBinding för Controls (format) PropertyName-element för ItemSeclectionCondition för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="b78ff-107">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b78ff-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="b78ff-108">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b78ff-109">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="b78ff-109">Attributes and Elements</span></span>

<span data-ttu-id="b78ff-110">I följande avsnitt beskrivs attribut, underordnade element och `PropertyName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="b78ff-110">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b78ff-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="b78ff-111">Attributes</span></span>

<span data-ttu-id="b78ff-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="b78ff-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b78ff-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="b78ff-113">Child Elements</span></span>

<span data-ttu-id="b78ff-114">Inga.</span><span class="sxs-lookup"><span data-stu-id="b78ff-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b78ff-115">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="b78ff-115">Parent Elements</span></span>

|<span data-ttu-id="b78ff-116">Element</span><span class="sxs-lookup"><span data-stu-id="b78ff-116">Element</span></span>|<span data-ttu-id="b78ff-117">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b78ff-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b78ff-118">ItemSelectionCondition-element för ExpressionBinding för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="b78ff-118">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="b78ff-119">Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="b78ff-119">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b78ff-120">Textvärde</span><span class="sxs-lookup"><span data-stu-id="b78ff-120">Text Value</span></span>

<span data-ttu-id="b78ff-121">Ange namnet på den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="b78ff-121">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="b78ff-122">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="b78ff-122">Remarks</span></span>

<span data-ttu-id="b78ff-123">Om det här elementet används kan du inte ange [script block](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) -elementet när du definierar urvals villkoret.</span><span class="sxs-lookup"><span data-stu-id="b78ff-123">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="b78ff-124">Se även</span><span class="sxs-lookup"><span data-stu-id="b78ff-124">See Also</span></span>

[<span data-ttu-id="b78ff-125">ScriptBlock-element för ItemSeclectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="b78ff-125">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="b78ff-126">ItemSelectionCondition-element för ExpressionBinding för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="b78ff-126">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="b78ff-127">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="b78ff-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
