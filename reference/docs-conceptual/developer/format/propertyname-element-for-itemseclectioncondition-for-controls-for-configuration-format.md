---
title: PropertyName-element för ItemSeclectionCondition för kontroll av konfiguration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0e304af1dbe816753d6dcd1dd8149f950f2a0941
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785599"
---
# <a name="propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="2817e-102">PropertyName-element för ItemSeclectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="2817e-102">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="2817e-103">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="2817e-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="2817e-104">När den här egenskapen finns eller när den utvärderas `true` , uppfylls villkoret och kontrollen används.</span><span class="sxs-lookup"><span data-stu-id="2817e-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="2817e-105">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="2817e-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="2817e-106">Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för Configuration (format) CustomEntry-element för CustomControl för kontroller för konfiguration (format) CustomItem-element för CustomEntry for Controls for Configuration ExpressionBinding-element för CustomItem for Controls for Configuration (format) ItemSelectionCondition-element för ExpressionBinding för Controls (format) PropertyName-element för ItemSeclectionCondition för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="2817e-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2817e-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="2817e-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2817e-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="2817e-108">Attributes and Elements</span></span>

<span data-ttu-id="2817e-109">I följande avsnitt beskrivs attribut, underordnade element och `PropertyName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="2817e-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2817e-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="2817e-110">Attributes</span></span>

<span data-ttu-id="2817e-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="2817e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2817e-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="2817e-112">Child Elements</span></span>

<span data-ttu-id="2817e-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="2817e-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2817e-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="2817e-114">Parent Elements</span></span>

|<span data-ttu-id="2817e-115">Element</span><span class="sxs-lookup"><span data-stu-id="2817e-115">Element</span></span>|<span data-ttu-id="2817e-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2817e-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2817e-117">ItemSelectionCondition-element för ExpressionBinding för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="2817e-117">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="2817e-118">Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="2817e-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2817e-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="2817e-119">Text Value</span></span>

<span data-ttu-id="2817e-120">Ange namnet på den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="2817e-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="2817e-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="2817e-121">Remarks</span></span>

<span data-ttu-id="2817e-122">Om det här elementet används kan du inte ange [script block](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) -elementet när du definierar urvals villkoret.</span><span class="sxs-lookup"><span data-stu-id="2817e-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="2817e-123">Se även</span><span class="sxs-lookup"><span data-stu-id="2817e-123">See Also</span></span>

[<span data-ttu-id="2817e-124">ScriptBlock-element för ItemSeclectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="2817e-124">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="2817e-125">ItemSelectionCondition-element för ExpressionBinding för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="2817e-125">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="2817e-126">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="2817e-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
