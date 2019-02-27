---
title: PropertyName-Element för SelectionCondition för anpassad kontroll för vy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc48a417-2083-46d4-ac38-16c12e65b6b9
caps.latest.revision: 7
ms.openlocfilehash: e08037d5d051d3be51e90193c7e87cc2e738f78a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850290"
---
# <a name="propertyname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="55500-102">PropertyName-element för SelectionCondition för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="55500-102">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="55500-103">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="55500-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="55500-104">När den här egenskapen finns eller att inventera till `true`villkoret uppfylls och definitionen används.</span><span class="sxs-lookup"><span data-stu-id="55500-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="55500-105">Det här elementet används när du definierar en anpassad kontroll vy.</span><span class="sxs-lookup"><span data-stu-id="55500-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="55500-106">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) anpassad kontroll konfigurationselement för Visa (Format) CustomEntries elementet för anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för anpassad kontroll för Visa ( Format) CustomItem Element för CustomEntry för anpassad kontroll för Visa (Format) EntrySelectedBy elementet för CustomEntry för anpassad kontroll för Visa (Format) SelectionCondition elementet för EntrySelectedBy för anpassad kontroll för PropertyName vy (Format) Element för SelectionCondition för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="55500-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="55500-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="55500-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="55500-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="55500-108">Attributes and Elements</span></span>

<span data-ttu-id="55500-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `PropertyName` element.</span><span class="sxs-lookup"><span data-stu-id="55500-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="55500-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="55500-110">Attributes</span></span>

<span data-ttu-id="55500-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="55500-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="55500-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="55500-112">Child Elements</span></span>

<span data-ttu-id="55500-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="55500-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="55500-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="55500-114">Parent Elements</span></span>

|<span data-ttu-id="55500-115">Element</span><span class="sxs-lookup"><span data-stu-id="55500-115">Element</span></span>|<span data-ttu-id="55500-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="55500-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="55500-117">SelectionCondition Element för EntrySelectedBy för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="55500-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="55500-118">Definierar ett villkor som måste finnas för kontrolldefinition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="55500-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="55500-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="55500-119">Text Value</span></span>

<span data-ttu-id="55500-120">Ange namnet på .NET-egenskapen.</span><span class="sxs-lookup"><span data-stu-id="55500-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="55500-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="55500-121">Remarks</span></span>

<span data-ttu-id="55500-122">Urvalsvillkoret måste ange ett namn med minst en egenskap eller ett skript, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="55500-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="55500-123">Läs mer om hur du kan använda villkor för val av [definiera villkor för att visa Data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="55500-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="55500-124">Se även</span><span class="sxs-lookup"><span data-stu-id="55500-124">See Also</span></span>

[<span data-ttu-id="55500-125">SelectionCondition Element för EntrySelectedBy för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="55500-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="55500-126">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="55500-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
