---
title: Script block-element för ItemSelectionCondition för kontroller för vy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4191157-bf01-4831-b221-6f8cc581cd53
caps.latest.revision: 6
ms.openlocfilehash: 0cbefbb48427b56d4ae2a5ae27c7726dcfad7b84
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355869"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="17d90-102">ScriptBlock-element för ItemSelectionCondition för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="17d90-102">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="17d90-103">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="17d90-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="17d90-104">När det här skriptet utvärderas till `true`, uppfylls villkoret och kontrollen används.</span><span class="sxs-lookup"><span data-stu-id="17d90-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="17d90-105">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="17d90-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="17d90-106">Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) styr element för Controls (format) CustomControl-element för kontroll för Control for View (format) CustomEntries-element för CustomControl för visnings-(format) CustomEntry-element för CustomEntries for Controls for View (format) CustomItem-elementet for CustomEntry for Controls for View (format) ExpressionBinding element for CustomItem for Controls for View (format) ItemSelectionCondition-element för ExpressionBinding för Controls för View (format) script block-element för ItemSelectionCondition för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="17d90-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="17d90-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="17d90-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="17d90-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="17d90-108">Attributes and Elements</span></span>

<span data-ttu-id="17d90-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `ScriptBlock`.</span><span class="sxs-lookup"><span data-stu-id="17d90-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="17d90-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="17d90-110">Attributes</span></span>

<span data-ttu-id="17d90-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="17d90-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="17d90-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="17d90-112">Child Elements</span></span>

<span data-ttu-id="17d90-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="17d90-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="17d90-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="17d90-114">Parent Elements</span></span>

|<span data-ttu-id="17d90-115">Element</span><span class="sxs-lookup"><span data-stu-id="17d90-115">Element</span></span>|<span data-ttu-id="17d90-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="17d90-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="17d90-117">ItemSelectionCondition-element för ExpressionBinding för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="17d90-117">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="17d90-118">Definierar det villkor som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="17d90-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="17d90-119">Text värde</span><span class="sxs-lookup"><span data-stu-id="17d90-119">Text Value</span></span>

<span data-ttu-id="17d90-120">Ange det skript som utvärderas.</span><span class="sxs-lookup"><span data-stu-id="17d90-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="17d90-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="17d90-121">Remarks</span></span>

<span data-ttu-id="17d90-122">Om det här elementet används kan du inte ange elementet [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) när du definierar urvals villkoret.</span><span class="sxs-lookup"><span data-stu-id="17d90-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="17d90-123">Se även</span><span class="sxs-lookup"><span data-stu-id="17d90-123">See Also</span></span>

[<span data-ttu-id="17d90-124">PropertyName-element för ItemSelectionCondition för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="17d90-124">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="17d90-125">ItemSelectionCondition-element för ExpressionBinding för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="17d90-125">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="17d90-126">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="17d90-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
