---
title: ScriptBlock Element för ItemSelectionCondition för GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 58d25835-4636-4c58-9f6c-0332b9318051
caps.latest.revision: 6
ms.openlocfilehash: 4045196e306e766cd805b3e7ae31bfcb3de184ee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064551"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="beccf-102">ScriptBlock-element för ItemSelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="beccf-102">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="beccf-103">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="beccf-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="beccf-104">När det här skriptet ska utvärderas till `true`villkoret uppfylls och kontrollen används.</span><span class="sxs-lookup"><span data-stu-id="beccf-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="beccf-105">Det här elementet används när du definierar hur en ny grupp med objekt visas.</span><span class="sxs-lookup"><span data-stu-id="beccf-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="beccf-106">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för Visa (Format) anpassad kontroll elementet för GroupBy (Format) CustomEntries Element för anpassad kontroll för GroupBy (Format) CustomEntry elementet för Anpassad kontroll för GroupBy (Format) CustomItem elementet för CustomEntry för GroupBy (Format) ExpressionBinding elementet för CustomItem för GroupBy (Format) ItemSelectionCondition elementet för ExpressionBinding för GroupBy (Format) ScriptBlock elementet för ItemSelectionCondition för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="beccf-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="beccf-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="beccf-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="beccf-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="beccf-108">Attributes and Elements</span></span>

<span data-ttu-id="beccf-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="beccf-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="beccf-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="beccf-110">Attributes</span></span>

<span data-ttu-id="beccf-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="beccf-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="beccf-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="beccf-112">Child Elements</span></span>

<span data-ttu-id="beccf-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="beccf-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="beccf-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="beccf-114">Parent Elements</span></span>

|<span data-ttu-id="beccf-115">Element</span><span class="sxs-lookup"><span data-stu-id="beccf-115">Element</span></span>|<span data-ttu-id="beccf-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="beccf-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="beccf-117">ItemSelectionCondition Element för ExpressionBinding för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="beccf-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="beccf-118">Definierar de villkor som måste finnas för den här kontrollen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="beccf-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="beccf-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="beccf-119">Text Value</span></span>

<span data-ttu-id="beccf-120">Ange det skript som ska utvärderas.</span><span class="sxs-lookup"><span data-stu-id="beccf-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="beccf-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="beccf-121">Remarks</span></span>

<span data-ttu-id="beccf-122">Om det här elementet används som du kan inte ange den [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) element när du definierar urvalsvillkoret.</span><span class="sxs-lookup"><span data-stu-id="beccf-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="beccf-123">Se även</span><span class="sxs-lookup"><span data-stu-id="beccf-123">See Also</span></span>

[<span data-ttu-id="beccf-124">ItemSelectionCondition Element för ExpressionBinding för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="beccf-124">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="beccf-125">PropertyName-Element för ItemSelectionCondition för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="beccf-125">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="beccf-126">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="beccf-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
