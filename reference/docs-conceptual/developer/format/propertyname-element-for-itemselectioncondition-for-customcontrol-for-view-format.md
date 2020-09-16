---
title: PropertyName-element för ItemSelectionCondition för CustomControl för vy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0131fa86be4be4daec1d9d24b50397fb8529f050
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785582"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="90f45-102">PropertyName-element för ItemSelectionCondition för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="90f45-102">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="90f45-103">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="90f45-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="90f45-104">När den här egenskapen finns eller när den utvärderas `true` , uppfylls villkoret och kontrollen används.</span><span class="sxs-lookup"><span data-stu-id="90f45-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="90f45-105">Det här elementet används när du definierar en anpassad kontrol vy.</span><span class="sxs-lookup"><span data-stu-id="90f45-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="90f45-106">Konfigurations element (format) ViewDefinitions element (format) View element (format) CustomControl element (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) CustomItem-element för CustomEntry för visnings-(format) ExpressionBinding-element för CustomItem för CustomControl för View (format) ItemSelectionCondition-element för uttrycks bindning för CustomControl för View (format) PropertyName-element för ItemSelectionCondition för View (format</span><span class="sxs-lookup"><span data-stu-id="90f45-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>

## <a name="syntax"></a><span data-ttu-id="90f45-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="90f45-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="90f45-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="90f45-108">Attributes and Elements</span></span>

<span data-ttu-id="90f45-109">I följande avsnitt beskrivs attribut, underordnade element och `PropertyName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="90f45-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="90f45-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="90f45-110">Attributes</span></span>

<span data-ttu-id="90f45-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="90f45-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="90f45-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="90f45-112">Child Elements</span></span>

<span data-ttu-id="90f45-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="90f45-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="90f45-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="90f45-114">Parent Elements</span></span>

|<span data-ttu-id="90f45-115">Element</span><span class="sxs-lookup"><span data-stu-id="90f45-115">Element</span></span>|<span data-ttu-id="90f45-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="90f45-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="90f45-117">ItemSelectionCondition-element för uttrycks bindning för CustomControl för vy (format)</span><span class="sxs-lookup"><span data-stu-id="90f45-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="90f45-118">Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="90f45-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="90f45-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="90f45-119">Text Value</span></span>

<span data-ttu-id="90f45-120">Ange namnet på den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="90f45-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="90f45-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="90f45-121">Remarks</span></span>

<span data-ttu-id="90f45-122">Om det här elementet används kan du inte ange [script block](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) -elementet när du definierar urvals villkoret.</span><span class="sxs-lookup"><span data-stu-id="90f45-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="90f45-123">Se även</span><span class="sxs-lookup"><span data-stu-id="90f45-123">See Also</span></span>

[<span data-ttu-id="90f45-124">ScriptBlock-element för ItemSelectionCondition för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="90f45-124">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="90f45-125">ItemSelectionCondition-element för uttrycks bindning för CustomControl för vy (format)</span><span class="sxs-lookup"><span data-stu-id="90f45-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="90f45-126">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="90f45-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
