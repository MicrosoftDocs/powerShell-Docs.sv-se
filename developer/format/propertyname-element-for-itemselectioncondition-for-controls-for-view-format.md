---
title: PropertyName-Element för ItemSelectionCondition för kontroller för att visa (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3955bc-f3a1-4ef6-86ac-80ffc133ad1b
caps.latest.revision: 6
ms.openlocfilehash: 28ad31be4be7be20f1f43ea1b69ad5d294de86f6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847952"
---
# <a name="propertyname-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="8247a-102">PropertyName-element för ItemSelectionCondition för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="8247a-102">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="8247a-103">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="8247a-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="8247a-104">När den här egenskapen finns eller att inventera till `true`villkoret uppfylls och kontrollen används.</span><span class="sxs-lookup"><span data-stu-id="8247a-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="8247a-105">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="8247a-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="8247a-106">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) kontroller Element (Format) kontroll konfigurationselement för kontroller för att visa (Format) anpassad kontroll Element för kontroll för kontroller för att visa (Format) CustomEntries Element för Anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för kontroller för att visa (Format) CustomItem Element för CustomEntry för kontroller för att visa (Format) ExpressionBinding Element för CustomItem för kontroller för att visa (Format) ItemSelectionCondition Element i ExpressionBinding för kontroller för att visa (Format) PropertyName Element för ItemSelectionCondition för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="8247a-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8247a-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="8247a-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8247a-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="8247a-108">Attributes and Elements</span></span>

<span data-ttu-id="8247a-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `PropertyName` element.</span><span class="sxs-lookup"><span data-stu-id="8247a-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8247a-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="8247a-110">Attributes</span></span>

<span data-ttu-id="8247a-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="8247a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8247a-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="8247a-112">Child Elements</span></span>

<span data-ttu-id="8247a-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="8247a-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8247a-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="8247a-114">Parent Elements</span></span>

|<span data-ttu-id="8247a-115">Element</span><span class="sxs-lookup"><span data-stu-id="8247a-115">Element</span></span>|<span data-ttu-id="8247a-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8247a-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8247a-117">ItemSelectionCondition Element i ExpressionBinding för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="8247a-117">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="8247a-118">Definierar de villkor som måste finnas för den här kontrollen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="8247a-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8247a-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="8247a-119">Text Value</span></span>

<span data-ttu-id="8247a-120">Ange namnet på egenskapen .NET som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="8247a-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="8247a-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="8247a-121">Remarks</span></span>

<span data-ttu-id="8247a-122">Om det här elementet används som du kan inte ange den [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) element när du definierar urvalsvillkoret.</span><span class="sxs-lookup"><span data-stu-id="8247a-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="8247a-123">Se även</span><span class="sxs-lookup"><span data-stu-id="8247a-123">See Also</span></span>

[<span data-ttu-id="8247a-124">ScriptBlock Element för ItemSelectionCondition för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="8247a-124">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="8247a-125">ItemSelectionCondition Element i ExpressionBinding för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="8247a-125">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="8247a-126">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="8247a-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
