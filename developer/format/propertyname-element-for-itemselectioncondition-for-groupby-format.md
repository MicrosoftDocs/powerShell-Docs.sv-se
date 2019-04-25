---
title: PropertyName-Element för ItemSelectionCondition för GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 221cbdc2-f794-4f3a-9d40-bfdd8cba1013
caps.latest.revision: 6
ms.openlocfilehash: aae65789cf5572cbcc9251eca802a2d43065e49f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064772"
---
# <a name="propertyname-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="86672-102">PropertyName-element för ItemSelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="86672-102">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="86672-103">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="86672-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="86672-104">När den här egenskapen finns eller att inventera till `true`villkoret uppfylls och kontrollen används.</span><span class="sxs-lookup"><span data-stu-id="86672-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="86672-105">Det här elementet används när du definierar hur en ny grupp med objekt visas.</span><span class="sxs-lookup"><span data-stu-id="86672-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="86672-106">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för Visa (Format) anpassad kontroll elementet för GroupBy (Format) CustomEntries Element för anpassad kontroll för GroupBy (Format) CustomEntry elementet för Anpassad kontroll för GroupBy (Format) CustomItem elementet för CustomEntry för GroupBy (Format) ExpressionBinding elementet för CustomItem för GroupBy (Format) ItemSelectionCondition elementet för ExpressionBinding för GroupBy (Format) PropertyName elementet för ItemSelectionCondition för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="86672-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="86672-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="86672-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="86672-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="86672-108">Attributes and Elements</span></span>

<span data-ttu-id="86672-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `PropertyName` element.</span><span class="sxs-lookup"><span data-stu-id="86672-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="86672-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="86672-110">Attributes</span></span>

<span data-ttu-id="86672-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="86672-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="86672-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="86672-112">Child Elements</span></span>

<span data-ttu-id="86672-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="86672-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="86672-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="86672-114">Parent Elements</span></span>

|<span data-ttu-id="86672-115">Element</span><span class="sxs-lookup"><span data-stu-id="86672-115">Element</span></span>|<span data-ttu-id="86672-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="86672-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="86672-117">ItemSelectionCondition Element för ExpressionBinding för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="86672-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="86672-118">Definierar de villkor som måste finnas för den här kontrollen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="86672-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="86672-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="86672-119">Text Value</span></span>

<span data-ttu-id="86672-120">Ange namnet på egenskapen .NET som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="86672-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="86672-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="86672-121">Remarks</span></span>

<span data-ttu-id="86672-122">Om det här elementet används som du kan inte ange den [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) element när du definierar urvalsvillkoret.</span><span class="sxs-lookup"><span data-stu-id="86672-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="86672-123">Se även</span><span class="sxs-lookup"><span data-stu-id="86672-123">See Also</span></span>

[<span data-ttu-id="86672-124">ScriptBlock Element för ItemSelectionCondition för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="86672-124">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="86672-125">ItemSelectionCondition Element för ExpressionBinding för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="86672-125">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="86672-126">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="86672-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
