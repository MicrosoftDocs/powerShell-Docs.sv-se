---
title: Script block-element för ItemSelectionCondition for GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 58d25835-4636-4c58-9f6c-0332b9318051
caps.latest.revision: 6
ms.openlocfilehash: 4045196e306e766cd805b3e7ae31bfcb3de184ee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355806"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="815bd-102">ScriptBlock-element för ItemSelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="815bd-102">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="815bd-103">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="815bd-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="815bd-104">När det här skriptet utvärderas till `true`, uppfylls villkoret och kontrollen används.</span><span class="sxs-lookup"><span data-stu-id="815bd-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="815bd-105">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="815bd-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="815bd-106">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element för CustomControl for GroupBy (format) CustomItem-element för CustomEntry för GroupBy (format) ExpressionBinding-element för CustomItem för GroupBy (format) ItemSelectionCondition-element för ExpressionBinding för GroupBy (format) script block-element för ItemSelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="815bd-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="815bd-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="815bd-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="815bd-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="815bd-108">Attributes and Elements</span></span>

<span data-ttu-id="815bd-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `ScriptBlock`-elementet.</span><span class="sxs-lookup"><span data-stu-id="815bd-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="815bd-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="815bd-110">Attributes</span></span>

<span data-ttu-id="815bd-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="815bd-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="815bd-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="815bd-112">Child Elements</span></span>

<span data-ttu-id="815bd-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="815bd-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="815bd-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="815bd-114">Parent Elements</span></span>

|<span data-ttu-id="815bd-115">Element</span><span class="sxs-lookup"><span data-stu-id="815bd-115">Element</span></span>|<span data-ttu-id="815bd-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="815bd-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="815bd-117">ItemSelectionCondition-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="815bd-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="815bd-118">Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="815bd-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="815bd-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="815bd-119">Text Value</span></span>

<span data-ttu-id="815bd-120">Ange det skript som utvärderas.</span><span class="sxs-lookup"><span data-stu-id="815bd-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="815bd-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="815bd-121">Remarks</span></span>

<span data-ttu-id="815bd-122">Om det här elementet används kan du inte ange elementet [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) när du definierar urvals villkoret.</span><span class="sxs-lookup"><span data-stu-id="815bd-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="815bd-123">Se även</span><span class="sxs-lookup"><span data-stu-id="815bd-123">See Also</span></span>

[<span data-ttu-id="815bd-124">ItemSelectionCondition-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="815bd-124">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="815bd-125">PropertyName-element för ItemSelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="815bd-125">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="815bd-126">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="815bd-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
