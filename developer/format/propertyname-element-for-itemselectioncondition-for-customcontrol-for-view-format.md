---
title: PropertyName-Element för ItemSelectionCondition för anpassad kontroll för vy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b12006-8d52-486b-91a3-e6224ca80e56
caps.latest.revision: 6
ms.openlocfilehash: 52d0b0816eaef6752220e0c3b1249e5a0e44a3ee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064874"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="13618-102">PropertyName-element för ItemSelectionCondition för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="13618-102">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="13618-103">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="13618-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="13618-104">När den här egenskapen finns eller att inventera till `true`villkoret uppfylls och kontrollen används.</span><span class="sxs-lookup"><span data-stu-id="13618-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="13618-105">Det här elementet används när du definierar en anpassad kontroll vy.</span><span class="sxs-lookup"><span data-stu-id="13618-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="13618-106">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) anpassad kontroll Element (Format) CustomEntries konfigurationselement för anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för vyn (Format) CustomItem elementet för CustomEntry för Visa (Format) ExpressionBinding elementet för CustomItem för anpassad kontroll för Visa (Format) ItemSelectionCondition elementet för uttrycket bindningen för anpassad kontroll för Visa (Format) PropertyName elementet för ItemSelectionCondition för Anpassad kontroll för vy (Format</span><span class="sxs-lookup"><span data-stu-id="13618-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>

## <a name="syntax"></a><span data-ttu-id="13618-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="13618-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="13618-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="13618-108">Attributes and Elements</span></span>

<span data-ttu-id="13618-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `PropertyName` element.</span><span class="sxs-lookup"><span data-stu-id="13618-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="13618-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="13618-110">Attributes</span></span>

<span data-ttu-id="13618-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="13618-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="13618-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="13618-112">Child Elements</span></span>

<span data-ttu-id="13618-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="13618-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="13618-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="13618-114">Parent Elements</span></span>

|<span data-ttu-id="13618-115">Element</span><span class="sxs-lookup"><span data-stu-id="13618-115">Element</span></span>|<span data-ttu-id="13618-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13618-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="13618-117">ItemSelectionCondition Element för uttrycket bindningen för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="13618-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="13618-118">Definierar de villkor som måste finnas för den här kontrollen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="13618-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="13618-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="13618-119">Text Value</span></span>

<span data-ttu-id="13618-120">Ange namnet på egenskapen .NET som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="13618-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="13618-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="13618-121">Remarks</span></span>

<span data-ttu-id="13618-122">Om det här elementet används som du kan inte ange den [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element när du definierar urvalsvillkoret.</span><span class="sxs-lookup"><span data-stu-id="13618-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="13618-123">Se även</span><span class="sxs-lookup"><span data-stu-id="13618-123">See Also</span></span>

[<span data-ttu-id="13618-124">ScriptBlock Element för ItemSelectionCondition för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="13618-124">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="13618-125">ItemSelectionCondition Element för uttrycket bindningen för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="13618-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="13618-126">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="13618-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
