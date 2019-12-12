---
title: PropertyName-element för ItemSelectionCondition för CustomControl för vy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b12006-8d52-486b-91a3-e6224ca80e56
caps.latest.revision: 6
ms.openlocfilehash: 52d0b0816eaef6752220e0c3b1249e5a0e44a3ee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354133"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="3a6a5-102">PropertyName-element för ItemSelectionCondition för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="3a6a5-102">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="3a6a5-103">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="3a6a5-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="3a6a5-104">När den här egenskapen finns eller när den utvärderas till `true`, uppfylls villkoret och kontrollen används.</span><span class="sxs-lookup"><span data-stu-id="3a6a5-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="3a6a5-105">Det här elementet används när du definierar en anpassad kontrol vy.</span><span class="sxs-lookup"><span data-stu-id="3a6a5-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="3a6a5-106">Konfigurations element (format) ViewDefinitions element (format) View element (format) CustomControl element (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) CustomItem-element för CustomEntry för visnings-(format) ExpressionBinding-element för CustomItem för CustomControl för View (format) ItemSelectionCondition-element för uttrycks bindning för CustomControl för View (format) PropertyName-element för ItemSelectionCondition för CustomControl för vy (format</span><span class="sxs-lookup"><span data-stu-id="3a6a5-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>

## <a name="syntax"></a><span data-ttu-id="3a6a5-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="3a6a5-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3a6a5-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="3a6a5-108">Attributes and Elements</span></span>

<span data-ttu-id="3a6a5-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `PropertyName`-elementet.</span><span class="sxs-lookup"><span data-stu-id="3a6a5-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3a6a5-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="3a6a5-110">Attributes</span></span>

<span data-ttu-id="3a6a5-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="3a6a5-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3a6a5-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="3a6a5-112">Child Elements</span></span>

<span data-ttu-id="3a6a5-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="3a6a5-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3a6a5-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="3a6a5-114">Parent Elements</span></span>

|<span data-ttu-id="3a6a5-115">Element</span><span class="sxs-lookup"><span data-stu-id="3a6a5-115">Element</span></span>|<span data-ttu-id="3a6a5-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3a6a5-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3a6a5-117">ItemSelectionCondition-element för uttrycks bindning för CustomControl för vy (format)</span><span class="sxs-lookup"><span data-stu-id="3a6a5-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="3a6a5-118">Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="3a6a5-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3a6a5-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="3a6a5-119">Text Value</span></span>

<span data-ttu-id="3a6a5-120">Ange namnet på den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="3a6a5-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="3a6a5-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="3a6a5-121">Remarks</span></span>

<span data-ttu-id="3a6a5-122">Om det här elementet används kan du inte ange [script block](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) -elementet när du definierar urvals villkoret.</span><span class="sxs-lookup"><span data-stu-id="3a6a5-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="3a6a5-123">Se även</span><span class="sxs-lookup"><span data-stu-id="3a6a5-123">See Also</span></span>

[<span data-ttu-id="3a6a5-124">Script block-element för ItemSelectionCondition för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="3a6a5-124">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3a6a5-125">ItemSelectionCondition-element för uttrycks bindning för CustomControl för vy (format)</span><span class="sxs-lookup"><span data-stu-id="3a6a5-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="3a6a5-126">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="3a6a5-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
