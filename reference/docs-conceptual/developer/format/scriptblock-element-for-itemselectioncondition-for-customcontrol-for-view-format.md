---
title: Script block-element för ItemSelectionCondition för CustomControl för View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 31873e886af04f8eedaf859af1d6bc1d5bcfdbf7
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772883"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="6b066-102">ScriptBlock-element för ItemSelectionCondition för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="6b066-102">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="6b066-103">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="6b066-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="6b066-104">När det här skriptet utvärderas `true` , uppfylls villkoret och kontrollen används.</span><span class="sxs-lookup"><span data-stu-id="6b066-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="6b066-105">Det här elementet används när du definierar en anpassad kontrol vy.</span><span class="sxs-lookup"><span data-stu-id="6b066-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="6b066-106">Konfigurations element (format) ViewDefinitions element (format) View element (format) CustomControl element (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) CustomItem-element för CustomEntry för visnings-(format) ExpressionBinding-element för CustomItem för CustomControl för View (format) ItemSelectionCondition-element för uttrycks bindning för CustomControl för View (format) script block-element för ItemSelectionCondition för View (format)</span><span class="sxs-lookup"><span data-stu-id="6b066-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6b066-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="6b066-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6b066-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="6b066-108">Attributes and Elements</span></span>

<span data-ttu-id="6b066-109">I följande avsnitt beskrivs attribut, underordnade element och `ScriptBlock` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="6b066-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6b066-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="6b066-110">Attributes</span></span>

<span data-ttu-id="6b066-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="6b066-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6b066-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="6b066-112">Child Elements</span></span>

<span data-ttu-id="6b066-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="6b066-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6b066-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="6b066-114">Parent Elements</span></span>

|<span data-ttu-id="6b066-115">Element</span><span class="sxs-lookup"><span data-stu-id="6b066-115">Element</span></span>|<span data-ttu-id="6b066-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6b066-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6b066-117">ItemSelectionCondition-element för uttrycks bindning för CustomControl för vy (format)</span><span class="sxs-lookup"><span data-stu-id="6b066-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="6b066-118">Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="6b066-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6b066-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="6b066-119">Text Value</span></span>

<span data-ttu-id="6b066-120">Ange det skript som utvärderas.</span><span class="sxs-lookup"><span data-stu-id="6b066-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="6b066-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="6b066-121">Remarks</span></span>

<span data-ttu-id="6b066-122">Om det här elementet används kan du inte ange elementet [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) när du definierar urvals villkoret.</span><span class="sxs-lookup"><span data-stu-id="6b066-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="6b066-123">Se även</span><span class="sxs-lookup"><span data-stu-id="6b066-123">See Also</span></span>

[<span data-ttu-id="6b066-124">PropertyName-element för ItemSelectionCondition för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="6b066-124">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="6b066-125">ItemSelectionCondition-element för uttrycks bindning för CustomControl för vy (format)</span><span class="sxs-lookup"><span data-stu-id="6b066-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="6b066-126">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="6b066-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
