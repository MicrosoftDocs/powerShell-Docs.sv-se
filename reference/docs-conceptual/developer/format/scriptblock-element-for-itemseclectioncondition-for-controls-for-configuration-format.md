---
title: Script block-element för ItemSeclectionCondition för kontroll av konfiguration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51f7aec9-7b01-4370-84f4-1e58508a851f
caps.latest.revision: 6
ms.openlocfilehash: e92b2dfff07358132c480c47c34279e5365fe400
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353909"
---
# <a name="scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="116e1-102">ScriptBlock-element för ItemSeclectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="116e1-102">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="116e1-103">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="116e1-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="116e1-104">När det här skriptet utvärderas till `true`, uppfylls villkoret och kontrollen används.</span><span class="sxs-lookup"><span data-stu-id="116e1-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="116e1-105">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="116e1-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="116e1-106">Konfigurations element (format) styr element i konfigurations-(format) kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för konfiguration ( Format) CustomEntry-element för CustomControl for Controls for Configuration (format) CustomItem element for CustomEntry for Controls for Configuration ExpressionBinding element for CustomItem for Controls for Configuration (format) ItemSelectionCondition-element för ExpressionBinding för kontroller för Configuration (format) script block-element för ItemSelectionCondition för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="116e1-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="116e1-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="116e1-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="116e1-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="116e1-108">Attributes and Elements</span></span>

<span data-ttu-id="116e1-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `ScriptBlock`-elementet.</span><span class="sxs-lookup"><span data-stu-id="116e1-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="116e1-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="116e1-110">Attributes</span></span>

<span data-ttu-id="116e1-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="116e1-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="116e1-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="116e1-112">Child Elements</span></span>

<span data-ttu-id="116e1-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="116e1-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="116e1-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="116e1-114">Parent Elements</span></span>

|<span data-ttu-id="116e1-115">Element</span><span class="sxs-lookup"><span data-stu-id="116e1-115">Element</span></span>|<span data-ttu-id="116e1-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="116e1-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="116e1-117">ItemSelectionCondition-element för ExpressionBinding för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="116e1-117">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="116e1-118">Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="116e1-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="116e1-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="116e1-119">Text Value</span></span>

<span data-ttu-id="116e1-120">Ange det skript som utvärderas.</span><span class="sxs-lookup"><span data-stu-id="116e1-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="116e1-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="116e1-121">Remarks</span></span>

<span data-ttu-id="116e1-122">Om det här elementet används kan du inte ange elementet [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) när du definierar urvals villkoret.</span><span class="sxs-lookup"><span data-stu-id="116e1-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="116e1-123">Se även</span><span class="sxs-lookup"><span data-stu-id="116e1-123">See Also</span></span>

[<span data-ttu-id="116e1-124">PropertyName-element för ItemSeclectionCondition för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="116e1-124">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="116e1-125">ItemSelectionCondition-element för ExpressionBinding för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="116e1-125">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="116e1-126">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="116e1-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
