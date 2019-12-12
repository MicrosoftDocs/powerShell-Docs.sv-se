---
title: PropertyName-element för ItemSeclectionCondition för kontroll av konfiguration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad8ab181-c559-492e-a0cf-299e381fdcc3
caps.latest.revision: 6
ms.openlocfilehash: ce25789bdfc2679372ca9e42f99dcc6a30ae2def
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354196"
---
# <a name="propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="7f9bf-102">PropertyName-element för ItemSeclectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="7f9bf-102">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="7f9bf-103">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="7f9bf-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="7f9bf-104">När den här egenskapen finns eller när den utvärderas till `true`, uppfylls villkoret och kontrollen används.</span><span class="sxs-lookup"><span data-stu-id="7f9bf-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="7f9bf-105">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="7f9bf-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="7f9bf-106">Konfigurations element (format) styr element i konfigurations-(format) kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för konfiguration ( Format) CustomEntry-element för CustomControl for Controls for Configuration (format) CustomItem element for CustomEntry for Controls for Configuration ExpressionBinding element for CustomItem for Controls for Configuration (format) ItemSelectionCondition-element för ExpressionBinding for Controls for Configuration (format) PropertyName-element för ItemSeclectionCondition för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="7f9bf-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7f9bf-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="7f9bf-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7f9bf-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="7f9bf-108">Attributes and Elements</span></span>

<span data-ttu-id="7f9bf-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `PropertyName`-elementet.</span><span class="sxs-lookup"><span data-stu-id="7f9bf-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7f9bf-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="7f9bf-110">Attributes</span></span>

<span data-ttu-id="7f9bf-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="7f9bf-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7f9bf-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="7f9bf-112">Child Elements</span></span>

<span data-ttu-id="7f9bf-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="7f9bf-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7f9bf-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="7f9bf-114">Parent Elements</span></span>

|<span data-ttu-id="7f9bf-115">Element</span><span class="sxs-lookup"><span data-stu-id="7f9bf-115">Element</span></span>|<span data-ttu-id="7f9bf-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7f9bf-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7f9bf-117">ItemSelectionCondition-element för ExpressionBinding för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="7f9bf-117">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="7f9bf-118">Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="7f9bf-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7f9bf-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="7f9bf-119">Text Value</span></span>

<span data-ttu-id="7f9bf-120">Ange namnet på den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="7f9bf-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="7f9bf-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="7f9bf-121">Remarks</span></span>

<span data-ttu-id="7f9bf-122">Om det här elementet används kan du inte ange [script block](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) -elementet när du definierar urvals villkoret.</span><span class="sxs-lookup"><span data-stu-id="7f9bf-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="7f9bf-123">Se även</span><span class="sxs-lookup"><span data-stu-id="7f9bf-123">See Also</span></span>

[<span data-ttu-id="7f9bf-124">Script block-element för ItemSeclectionCondition för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="7f9bf-124">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="7f9bf-125">ItemSelectionCondition-element för ExpressionBinding för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="7f9bf-125">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="7f9bf-126">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="7f9bf-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
