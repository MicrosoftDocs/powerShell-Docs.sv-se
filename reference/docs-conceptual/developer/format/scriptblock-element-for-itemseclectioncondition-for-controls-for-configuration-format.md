---
ms.date: 09/13/2016
ms.topic: reference
title: ScriptBlock-element för ItemSeclectionCondition för Controls för Configuration (format)
description: ScriptBlock-element för ItemSeclectionCondition för Controls för Configuration (format)
ms.openlocfilehash: 853130da4489e571d7f4026a8d65d029d1889f9b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92665221"
---
# <a name="scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="8b675-103">ScriptBlock-element för ItemSeclectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="8b675-103">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="8b675-104">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="8b675-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="8b675-105">När det här skriptet utvärderas `true` , uppfylls villkoret och kontrollen används.</span><span class="sxs-lookup"><span data-stu-id="8b675-105">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="8b675-106">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="8b675-106">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="8b675-107">Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för Configuration (format) CustomEntry-element för CustomControl för kontroller för konfiguration (format) CustomItem-element för CustomEntry for Controls for Configuration ExpressionBinding element for CustomItem for Controls for Configuration (format) ItemSelectionCondition element for ExpressionBinding for Controls for Configuration (format) script block element for ItemSelectionCondition for Controls for Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="8b675-107">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8b675-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="8b675-108">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8b675-109">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="8b675-109">Attributes and Elements</span></span>

<span data-ttu-id="8b675-110">I följande avsnitt beskrivs attribut, underordnade element och `ScriptBlock` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="8b675-110">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8b675-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="8b675-111">Attributes</span></span>

<span data-ttu-id="8b675-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="8b675-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8b675-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="8b675-113">Child Elements</span></span>

<span data-ttu-id="8b675-114">Inga.</span><span class="sxs-lookup"><span data-stu-id="8b675-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8b675-115">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="8b675-115">Parent Elements</span></span>

|<span data-ttu-id="8b675-116">Element</span><span class="sxs-lookup"><span data-stu-id="8b675-116">Element</span></span>|<span data-ttu-id="8b675-117">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8b675-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8b675-118">ItemSelectionCondition-element för ExpressionBinding för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="8b675-118">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="8b675-119">Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="8b675-119">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8b675-120">Textvärde</span><span class="sxs-lookup"><span data-stu-id="8b675-120">Text Value</span></span>

<span data-ttu-id="8b675-121">Ange det skript som utvärderas.</span><span class="sxs-lookup"><span data-stu-id="8b675-121">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="8b675-122">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="8b675-122">Remarks</span></span>

<span data-ttu-id="8b675-123">Om det här elementet används kan du inte ange elementet [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) när du definierar urvals villkoret.</span><span class="sxs-lookup"><span data-stu-id="8b675-123">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="8b675-124">Se även</span><span class="sxs-lookup"><span data-stu-id="8b675-124">See Also</span></span>

[<span data-ttu-id="8b675-125">PropertyName-element för ItemSeclectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="8b675-125">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="8b675-126">ItemSelectionCondition-element för ExpressionBinding för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="8b675-126">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="8b675-127">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="8b675-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
