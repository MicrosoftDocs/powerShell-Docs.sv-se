---
title: ScriptBlock Element för ItemSelectionCondition för kontroller för att visa (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4191157-bf01-4831-b221-6f8cc581cd53
caps.latest.revision: 6
ms.openlocfilehash: 0cbefbb48427b56d4ae2a5ae27c7726dcfad7b84
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064738"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="e81ab-102">ScriptBlock-element för ItemSelectionCondition för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="e81ab-102">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="e81ab-103">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="e81ab-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="e81ab-104">När det här skriptet ska utvärderas till `true`villkoret uppfylls och kontrollen används.</span><span class="sxs-lookup"><span data-stu-id="e81ab-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="e81ab-105">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="e81ab-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="e81ab-106">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) kontroller Element (Format) kontroll konfigurationselement för kontroller för att visa (Format) anpassad kontroll Element för kontroll för kontroller för att visa (Format) CustomEntries Element för Anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för kontroller för att visa (Format) CustomItem Element för CustomEntry för kontroller för att visa (Format) ExpressionBinding Element för CustomItem för kontroller för att visa (Format) ItemSelectionCondition Element i ExpressionBinding för kontroller för att visa (Format) ScriptBlock Element för ItemSelectionCondition för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="e81ab-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e81ab-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="e81ab-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e81ab-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="e81ab-108">Attributes and Elements</span></span>

<span data-ttu-id="e81ab-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="e81ab-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e81ab-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="e81ab-110">Attributes</span></span>

<span data-ttu-id="e81ab-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="e81ab-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e81ab-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="e81ab-112">Child Elements</span></span>

<span data-ttu-id="e81ab-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="e81ab-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e81ab-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="e81ab-114">Parent Elements</span></span>

|<span data-ttu-id="e81ab-115">Element</span><span class="sxs-lookup"><span data-stu-id="e81ab-115">Element</span></span>|<span data-ttu-id="e81ab-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e81ab-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e81ab-117">ItemSelectionCondition Element i ExpressionBinding för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="e81ab-117">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="e81ab-118">Definierar de villkor som måste finnas för den här kontrollen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="e81ab-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e81ab-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="e81ab-119">Text Value</span></span>

<span data-ttu-id="e81ab-120">Ange det skript som ska utvärderas.</span><span class="sxs-lookup"><span data-stu-id="e81ab-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="e81ab-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="e81ab-121">Remarks</span></span>

<span data-ttu-id="e81ab-122">Om det här elementet används som du kan inte ange den [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) element när du definierar urvalsvillkoret.</span><span class="sxs-lookup"><span data-stu-id="e81ab-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="e81ab-123">Se även</span><span class="sxs-lookup"><span data-stu-id="e81ab-123">See Also</span></span>

[<span data-ttu-id="e81ab-124">PropertyName-Element för ItemSelectionCondition för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="e81ab-124">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="e81ab-125">ItemSelectionCondition Element i ExpressionBinding för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="e81ab-125">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="e81ab-126">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="e81ab-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
