---
title: ScriptBlock Element för ItemSelectionCondition för anpassad kontroll för vy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 946cd2b5-ac37-4a13-bb49-29fbc70ec8d7
caps.latest.revision: 6
ms.openlocfilehash: 0c07ab0e5d04c4056a7e7215bfa55773bfccb41d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851179"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="e5a02-102">ScriptBlock-element för ItemSelectionCondition för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="e5a02-102">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="e5a02-103">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="e5a02-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="e5a02-104">När det här skriptet ska utvärderas till `true`villkoret uppfylls och kontrollen används.</span><span class="sxs-lookup"><span data-stu-id="e5a02-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="e5a02-105">Det här elementet används när du definierar en anpassad kontroll vy.</span><span class="sxs-lookup"><span data-stu-id="e5a02-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="e5a02-106">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) anpassad kontroll Element (Format) CustomEntries konfigurationselement för anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för vyn (Format) CustomItem elementet för CustomEntry för Visa (Format) ExpressionBinding elementet för CustomItem för anpassad kontroll för Visa (Format) ItemSelectionCondition elementet för uttrycket bindningen för anpassad kontroll för Visa (Format) ScriptBlock elementet för ItemSelectionCondition för Anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="e5a02-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e5a02-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="e5a02-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e5a02-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="e5a02-108">Attributes and Elements</span></span>

<span data-ttu-id="e5a02-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="e5a02-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e5a02-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="e5a02-110">Attributes</span></span>

<span data-ttu-id="e5a02-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="e5a02-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e5a02-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="e5a02-112">Child Elements</span></span>

<span data-ttu-id="e5a02-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="e5a02-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e5a02-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="e5a02-114">Parent Elements</span></span>

|<span data-ttu-id="e5a02-115">Element</span><span class="sxs-lookup"><span data-stu-id="e5a02-115">Element</span></span>|<span data-ttu-id="e5a02-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e5a02-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5a02-117">ItemSelectionCondition Element för uttrycket bindningen för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="e5a02-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="e5a02-118">Definierar de villkor som måste finnas för den här kontrollen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="e5a02-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e5a02-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="e5a02-119">Text Value</span></span>

<span data-ttu-id="e5a02-120">Ange det skript som ska utvärderas.</span><span class="sxs-lookup"><span data-stu-id="e5a02-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="e5a02-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="e5a02-121">Remarks</span></span>

<span data-ttu-id="e5a02-122">Om det här elementet används som du kan inte ange den [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element när du definierar urvalsvillkoret.</span><span class="sxs-lookup"><span data-stu-id="e5a02-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="e5a02-123">Se även</span><span class="sxs-lookup"><span data-stu-id="e5a02-123">See Also</span></span>

[<span data-ttu-id="e5a02-124">PropertyName-Element för ItemSelectionCondition för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="e5a02-124">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e5a02-125">ItemSelectionCondition Element för uttrycket bindningen för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="e5a02-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="e5a02-126">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="e5a02-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
