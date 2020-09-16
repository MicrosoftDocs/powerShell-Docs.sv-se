---
title: Script block-element för ItemSelectionCondition for GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7738b180f328c7360275058cdb9dea01df6ea285
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787656"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="dea6b-102">ScriptBlock-element för ItemSelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="dea6b-102">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="dea6b-103">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="dea6b-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="dea6b-104">När det här skriptet utvärderas `true` , uppfylls villkoret och kontrollen används.</span><span class="sxs-lookup"><span data-stu-id="dea6b-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="dea6b-105">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="dea6b-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="dea6b-106">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element för CustomControl för GroupBy (format) CustomItem-element för CustomEntry for GroupBy (format) ExpressionBinding-element för CustomItem for GroupBy (format) ItemSelectionCondition-element för ExpressionBinding för GroupBy (format) script block element for ItemSelectionCondition for groupby (format)</span><span class="sxs-lookup"><span data-stu-id="dea6b-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dea6b-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="dea6b-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dea6b-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="dea6b-108">Attributes and Elements</span></span>

<span data-ttu-id="dea6b-109">I följande avsnitt beskrivs attribut, underordnade element och `ScriptBlock` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="dea6b-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dea6b-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="dea6b-110">Attributes</span></span>

<span data-ttu-id="dea6b-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="dea6b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dea6b-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="dea6b-112">Child Elements</span></span>

<span data-ttu-id="dea6b-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="dea6b-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="dea6b-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="dea6b-114">Parent Elements</span></span>

|<span data-ttu-id="dea6b-115">Element</span><span class="sxs-lookup"><span data-stu-id="dea6b-115">Element</span></span>|<span data-ttu-id="dea6b-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="dea6b-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dea6b-117">ItemSelectionCondition-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="dea6b-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="dea6b-118">Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="dea6b-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="dea6b-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="dea6b-119">Text Value</span></span>

<span data-ttu-id="dea6b-120">Ange det skript som utvärderas.</span><span class="sxs-lookup"><span data-stu-id="dea6b-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="dea6b-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="dea6b-121">Remarks</span></span>

<span data-ttu-id="dea6b-122">Om det här elementet används kan du inte ange elementet [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) när du definierar urvals villkoret.</span><span class="sxs-lookup"><span data-stu-id="dea6b-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="dea6b-123">Se även</span><span class="sxs-lookup"><span data-stu-id="dea6b-123">See Also</span></span>

[<span data-ttu-id="dea6b-124">ItemSelectionCondition-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="dea6b-124">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="dea6b-125">PropertyName-element för ItemSelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="dea6b-125">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="dea6b-126">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="dea6b-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
