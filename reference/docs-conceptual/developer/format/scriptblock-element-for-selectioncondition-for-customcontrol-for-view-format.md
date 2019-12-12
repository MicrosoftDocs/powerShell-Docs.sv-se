---
title: Script block-element för SelectionCondition för CustomControl för View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7031fa8b-3e2b-4ea8-89cb-95171f467b5a
caps.latest.revision: 6
ms.openlocfilehash: e55d1c5aa533005b258ecbbbf3ed9d55f852eab6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358950"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="2a9f8-102">ScriptBlock-element för SelectionCondition för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="2a9f8-102">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="2a9f8-103">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="2a9f8-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="2a9f8-104">När det här skriptet utvärderas till `true`, uppfylls villkoret och definitionen används.</span><span class="sxs-lookup"><span data-stu-id="2a9f8-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="2a9f8-105">Det här elementet används när du definierar en anpassad kontrol vy.</span><span class="sxs-lookup"><span data-stu-id="2a9f8-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="2a9f8-106">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) CustomControl-element för View (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View Format) CustomItem-element för CustomEntry för CustomControl för View (format) SelectionCondition-element för EntrySelectedBy för CustomControl för View (format) script block-element för SelectionCondition för View (format)</span><span class="sxs-lookup"><span data-stu-id="2a9f8-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2a9f8-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="2a9f8-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2a9f8-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="2a9f8-108">Attributes and Elements</span></span>

<span data-ttu-id="2a9f8-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `ScriptBlock`-elementet.</span><span class="sxs-lookup"><span data-stu-id="2a9f8-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2a9f8-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="2a9f8-110">Attributes</span></span>

<span data-ttu-id="2a9f8-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="2a9f8-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2a9f8-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="2a9f8-112">Child Elements</span></span>

<span data-ttu-id="2a9f8-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="2a9f8-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2a9f8-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="2a9f8-114">Parent Elements</span></span>

|<span data-ttu-id="2a9f8-115">Element</span><span class="sxs-lookup"><span data-stu-id="2a9f8-115">Element</span></span>|<span data-ttu-id="2a9f8-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2a9f8-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2a9f8-117">SelectionCondition-element för EntrySelectedBy för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="2a9f8-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="2a9f8-118">Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="2a9f8-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2a9f8-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="2a9f8-119">Text Value</span></span>

<span data-ttu-id="2a9f8-120">Ange det skript som utvärderas.</span><span class="sxs-lookup"><span data-stu-id="2a9f8-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="2a9f8-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="2a9f8-121">Remarks</span></span>

<span data-ttu-id="2a9f8-122">Urvals villkoret måste ange minst ett skript eller egenskaps namn som ska utvärderas, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="2a9f8-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="2a9f8-123">Mer information om hur urvals villkor kan användas finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="2a9f8-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2a9f8-124">Se även</span><span class="sxs-lookup"><span data-stu-id="2a9f8-124">See Also</span></span>

[<span data-ttu-id="2a9f8-125">SelectionCondition-element för EntrySelectedBy för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="2a9f8-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="2a9f8-126">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="2a9f8-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
