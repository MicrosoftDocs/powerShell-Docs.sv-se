---
title: PropertyName-Element för ItemSeclectionCondition för kontroller för konfiguration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad8ab181-c559-492e-a0cf-299e381fdcc3
caps.latest.revision: 6
ms.openlocfilehash: ce25789bdfc2679372ca9e42f99dcc6a30ae2def
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064915"
---
# <a name="propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="96bdc-102">PropertyName-element för ItemSeclectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="96bdc-102">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="96bdc-103">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="96bdc-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="96bdc-104">När den här egenskapen finns eller att inventera till `true`villkoret uppfylls och kontrollen används.</span><span class="sxs-lookup"><span data-stu-id="96bdc-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="96bdc-105">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="96bdc-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="96bdc-106">Konfigurationselementet Element (Format) kontroller av (Format) kontroll konfigurationselement för kontroller för (Format) anpassad kontroll konfigurationselement för kontroll för (Format) CustomEntries konfigurationselement för anpassad kontroll för konfiguration ( Format) CustomEntry Element för anpassad kontroll för kontroller för (Format) CustomItem konfigurationselement för CustomEntry för kontroller för ExpressionBinding konfigurationselement för CustomItem för kontroller för konfiguration (Format) ItemSelectionCondition Element för ExpressionBinding för kontroller för (Format) PropertyName konfigurationselement för ItemSeclectionCondition för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="96bdc-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="96bdc-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="96bdc-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="96bdc-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="96bdc-108">Attributes and Elements</span></span>

<span data-ttu-id="96bdc-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `PropertyName` element.</span><span class="sxs-lookup"><span data-stu-id="96bdc-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="96bdc-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="96bdc-110">Attributes</span></span>

<span data-ttu-id="96bdc-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="96bdc-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="96bdc-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="96bdc-112">Child Elements</span></span>

<span data-ttu-id="96bdc-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="96bdc-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="96bdc-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="96bdc-114">Parent Elements</span></span>

|<span data-ttu-id="96bdc-115">Element</span><span class="sxs-lookup"><span data-stu-id="96bdc-115">Element</span></span>|<span data-ttu-id="96bdc-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="96bdc-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="96bdc-117">ItemSelectionCondition Element för ExpressionBinding för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="96bdc-117">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="96bdc-118">Definierar de villkor som måste finnas för den här kontrollen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="96bdc-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="96bdc-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="96bdc-119">Text Value</span></span>

<span data-ttu-id="96bdc-120">Ange namnet på egenskapen .NET som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="96bdc-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="96bdc-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="96bdc-121">Remarks</span></span>

<span data-ttu-id="96bdc-122">Om det här elementet används som du kan inte ange den [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element när du definierar urvalsvillkoret.</span><span class="sxs-lookup"><span data-stu-id="96bdc-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="96bdc-123">Se även</span><span class="sxs-lookup"><span data-stu-id="96bdc-123">See Also</span></span>

[<span data-ttu-id="96bdc-124">ScriptBlock Element för ItemSeclectionCondition för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="96bdc-124">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="96bdc-125">ItemSelectionCondition Element för ExpressionBinding för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="96bdc-125">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="96bdc-126">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="96bdc-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
