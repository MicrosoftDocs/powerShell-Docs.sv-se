---
title: PropertyName-element för ItemSelectionCondition för kontroller för vy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3955bc-f3a1-4ef6-86ac-80ffc133ad1b
caps.latest.revision: 6
ms.openlocfilehash: 28ad31be4be7be20f1f43ea1b69ad5d294de86f6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354161"
---
# <a name="propertyname-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="94919-102">PropertyName-element för ItemSelectionCondition för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="94919-102">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="94919-103">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="94919-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="94919-104">När den här egenskapen finns eller när den utvärderas till `true`, uppfylls villkoret och kontrollen används.</span><span class="sxs-lookup"><span data-stu-id="94919-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="94919-105">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="94919-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="94919-106">Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) styr element för Controls (format) CustomControl-element för kontroll för Control for View (format) CustomEntries-element för CustomControl för visnings-(format) CustomEntry-element för CustomEntries for Controls for View (format) CustomItem-elementet for CustomEntry for Controls for View (format) ExpressionBinding element for CustomItem for Controls for View (format) ItemSelectionCondition-element för ExpressionBinding för Controls för View (format) PropertyName-element för ItemSelectionCondition för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="94919-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="94919-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="94919-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="94919-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="94919-108">Attributes and Elements</span></span>

<span data-ttu-id="94919-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `PropertyName`-elementet.</span><span class="sxs-lookup"><span data-stu-id="94919-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="94919-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="94919-110">Attributes</span></span>

<span data-ttu-id="94919-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="94919-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="94919-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="94919-112">Child Elements</span></span>

<span data-ttu-id="94919-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="94919-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="94919-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="94919-114">Parent Elements</span></span>

|<span data-ttu-id="94919-115">Element</span><span class="sxs-lookup"><span data-stu-id="94919-115">Element</span></span>|<span data-ttu-id="94919-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="94919-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="94919-117">ItemSelectionCondition-element för ExpressionBinding för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="94919-117">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="94919-118">Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="94919-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="94919-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="94919-119">Text Value</span></span>

<span data-ttu-id="94919-120">Ange namnet på den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="94919-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="94919-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="94919-121">Remarks</span></span>

<span data-ttu-id="94919-122">Om det här elementet används kan du inte ange [script block](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) -elementet när du definierar urvals villkoret.</span><span class="sxs-lookup"><span data-stu-id="94919-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="94919-123">Se även</span><span class="sxs-lookup"><span data-stu-id="94919-123">See Also</span></span>

[<span data-ttu-id="94919-124">Script block-element för ItemSelectionCondition för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="94919-124">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="94919-125">ItemSelectionCondition-element för ExpressionBinding för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="94919-125">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="94919-126">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="94919-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
