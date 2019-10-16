---
title: Script block-element för ItemSelectionCondition för CustomControl för View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 946cd2b5-ac37-4a13-bb49-29fbc70ec8d7
caps.latest.revision: 6
ms.openlocfilehash: 0c07ab0e5d04c4056a7e7215bfa55773bfccb41d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353874"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="f2dc8-102">ScriptBlock-element för ItemSelectionCondition för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="f2dc8-102">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="f2dc8-103">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="f2dc8-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="f2dc8-104">När det här skriptet utvärderas till `true`, uppfylls villkoret och kontrollen används.</span><span class="sxs-lookup"><span data-stu-id="f2dc8-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="f2dc8-105">Det här elementet används när du definierar en anpassad kontrol vy.</span><span class="sxs-lookup"><span data-stu-id="f2dc8-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="f2dc8-106">Konfigurations element (format) ViewDefinitions element (format) View element (format) CustomControl element (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) CustomItem-element för CustomEntry för visnings-(format) ExpressionBinding-element för CustomItem för CustomControl för View (format) ItemSelectionCondition-element för uttrycks bindning för CustomControl för View (format) script block-element för ItemSelectionCondition för CustomControl för vy (format)</span><span class="sxs-lookup"><span data-stu-id="f2dc8-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f2dc8-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="f2dc8-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f2dc8-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="f2dc8-108">Attributes and Elements</span></span>

<span data-ttu-id="f2dc8-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="f2dc8-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f2dc8-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="f2dc8-110">Attributes</span></span>

<span data-ttu-id="f2dc8-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="f2dc8-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f2dc8-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="f2dc8-112">Child Elements</span></span>

<span data-ttu-id="f2dc8-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="f2dc8-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f2dc8-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="f2dc8-114">Parent Elements</span></span>

|<span data-ttu-id="f2dc8-115">Element</span><span class="sxs-lookup"><span data-stu-id="f2dc8-115">Element</span></span>|<span data-ttu-id="f2dc8-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f2dc8-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f2dc8-117">ItemSelectionCondition-element för uttrycks bindning för CustomControl för vy (format)</span><span class="sxs-lookup"><span data-stu-id="f2dc8-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="f2dc8-118">Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="f2dc8-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f2dc8-119">Text värde</span><span class="sxs-lookup"><span data-stu-id="f2dc8-119">Text Value</span></span>

<span data-ttu-id="f2dc8-120">Ange det skript som utvärderas.</span><span class="sxs-lookup"><span data-stu-id="f2dc8-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="f2dc8-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="f2dc8-121">Remarks</span></span>

<span data-ttu-id="f2dc8-122">Om det här elementet används kan du inte ange elementet [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) när du definierar urvals villkoret.</span><span class="sxs-lookup"><span data-stu-id="f2dc8-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2dc8-123">Se även</span><span class="sxs-lookup"><span data-stu-id="f2dc8-123">See Also</span></span>

[<span data-ttu-id="f2dc8-124">PropertyName-element för ItemSelectionCondition för CustomControl för vy (format)</span><span class="sxs-lookup"><span data-stu-id="f2dc8-124">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="f2dc8-125">ItemSelectionCondition-element för uttrycks bindning för CustomControl för vy (format)</span><span class="sxs-lookup"><span data-stu-id="f2dc8-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="f2dc8-126">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="f2dc8-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
