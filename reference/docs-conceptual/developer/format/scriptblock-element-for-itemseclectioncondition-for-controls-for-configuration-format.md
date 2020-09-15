---
title: Script block-element för ItemSeclectionCondition för kontroll av konfiguration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: f44b1a7f059fa5f41c19eed93762b61eda5110e8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772900"
---
# <a name="scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="66919-102">ScriptBlock-element för ItemSeclectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="66919-102">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="66919-103">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="66919-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="66919-104">När det här skriptet utvärderas `true` , uppfylls villkoret och kontrollen används.</span><span class="sxs-lookup"><span data-stu-id="66919-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="66919-105">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="66919-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="66919-106">Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för Configuration (format) CustomEntry-element för CustomControl för kontroller för konfiguration (format) CustomItem-element för CustomEntry for Controls for Configuration ExpressionBinding element for CustomItem for Controls for Configuration (format) ItemSelectionCondition element for ExpressionBinding for Controls for Configuration (format) script block element for ItemSelectionCondition for Controls for Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="66919-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="66919-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="66919-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="66919-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="66919-108">Attributes and Elements</span></span>

<span data-ttu-id="66919-109">I följande avsnitt beskrivs attribut, underordnade element och `ScriptBlock` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="66919-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="66919-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="66919-110">Attributes</span></span>

<span data-ttu-id="66919-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="66919-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="66919-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="66919-112">Child Elements</span></span>

<span data-ttu-id="66919-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="66919-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="66919-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="66919-114">Parent Elements</span></span>

|<span data-ttu-id="66919-115">Element</span><span class="sxs-lookup"><span data-stu-id="66919-115">Element</span></span>|<span data-ttu-id="66919-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="66919-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="66919-117">ItemSelectionCondition-element för ExpressionBinding för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="66919-117">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="66919-118">Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="66919-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="66919-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="66919-119">Text Value</span></span>

<span data-ttu-id="66919-120">Ange det skript som utvärderas.</span><span class="sxs-lookup"><span data-stu-id="66919-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="66919-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="66919-121">Remarks</span></span>

<span data-ttu-id="66919-122">Om det här elementet används kan du inte ange elementet [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) när du definierar urvals villkoret.</span><span class="sxs-lookup"><span data-stu-id="66919-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="66919-123">Se även</span><span class="sxs-lookup"><span data-stu-id="66919-123">See Also</span></span>

[<span data-ttu-id="66919-124">PropertyName-element för ItemSeclectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="66919-124">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="66919-125">ItemSelectionCondition-element för ExpressionBinding för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="66919-125">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="66919-126">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="66919-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
