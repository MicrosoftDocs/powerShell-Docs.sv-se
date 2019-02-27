---
title: PropertyName-Element för SelectionCondition för EntrySelectedBy för WideEntry (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 340abb12-6df1-42f4-bdae-b0509c90952c
caps.latest.revision: 11
ms.openlocfilehash: 196877b97db9ed0592e357486c1318dc1e7efd31
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849905"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="4a729-102">PropertyName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="4a729-102">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="4a729-103">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="4a729-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="4a729-104">När den här egenskapen finns eller att inventera till `true`villkoret uppfylls och definitionen används.</span><span class="sxs-lookup"><span data-stu-id="4a729-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="4a729-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy konfigurationselement för WideEntry (Format) SelectionCondition elementet för EntrySelectedBy för WideEntry (Format) PropertyName elementet för SelectionCondition för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="4a729-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4a729-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="4a729-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

```

## <a name="attributes-and-elements"></a><span data-ttu-id="4a729-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="4a729-107">Attributes and Elements</span></span>

<span data-ttu-id="4a729-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `PropertyName` element.</span><span class="sxs-lookup"><span data-stu-id="4a729-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4a729-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="4a729-109">Attributes</span></span>

<span data-ttu-id="4a729-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="4a729-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4a729-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="4a729-111">Child Elements</span></span>

<span data-ttu-id="4a729-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="4a729-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4a729-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="4a729-113">Parent Elements</span></span>

|<span data-ttu-id="4a729-114">Element</span><span class="sxs-lookup"><span data-stu-id="4a729-114">Element</span></span>|<span data-ttu-id="4a729-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4a729-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4a729-116">SelectionCondition Element för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="4a729-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="4a729-117">Definierar de villkor som måste finnas för den här definitionen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="4a729-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4a729-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="4a729-118">Text Value</span></span>

<span data-ttu-id="4a729-119">Ange namnet på .NET-egenskapen.</span><span class="sxs-lookup"><span data-stu-id="4a729-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="4a729-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="4a729-120">Remarks</span></span>

<span data-ttu-id="4a729-121">Urvalsvillkoret måste ange minst en egenskapsnamn eller ett skript för att utvärdera, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="4a729-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="4a729-122">Läs mer om hur du använder villkor för val av [definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="4a729-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="4a729-123">Mer information om andra komponenter för en bred vy finns i [bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="4a729-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4a729-124">Se även</span><span class="sxs-lookup"><span data-stu-id="4a729-124">See Also</span></span>

[<span data-ttu-id="4a729-125">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="4a729-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="4a729-126">Definiera villkor för när Data visas</span><span class="sxs-lookup"><span data-stu-id="4a729-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="4a729-127">ScriptBlock Element för SelectionCondition för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="4a729-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="4a729-128">SelectionCondition Element för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="4a729-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="4a729-129">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="4a729-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
