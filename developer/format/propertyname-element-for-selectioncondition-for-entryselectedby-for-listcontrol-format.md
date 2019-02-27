---
title: PropertyName-Element för SelectionCondition för EntrySelectedBy för ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71c3f1f6-6fe2-42f1-8260-6974d3871748
caps.latest.revision: 11
ms.openlocfilehash: f857f5944b9e971215a06d6f5c39f7c22c6cf99f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844921"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="4ffd9-102">PropertyName-element för SelectionCondition för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="4ffd9-102">PropertyName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="4ffd9-103">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="4ffd9-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="4ffd9-104">När den här egenskapen finns eller att inventera till `true`villkoret uppfylls och kortet används.</span><span class="sxs-lookup"><span data-stu-id="4ffd9-104">When this property is present or when it evaluates to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="4ffd9-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy konfigurationselement för ListEntry (Format) SelectionCondition elementet för EntrySelectedBy för ListEntry (Format) PropertyName elementet för SelectionCondition för EmtrySelectedBy för ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="4ffd9-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) PropertyName Element for SelectionCondition for EmtrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4ffd9-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="4ffd9-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4ffd9-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="4ffd9-107">Attributes and Elements</span></span>

<span data-ttu-id="4ffd9-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `PropertyName` element.</span><span class="sxs-lookup"><span data-stu-id="4ffd9-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4ffd9-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="4ffd9-109">Attributes</span></span>

<span data-ttu-id="4ffd9-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="4ffd9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4ffd9-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="4ffd9-111">Child Elements</span></span>

<span data-ttu-id="4ffd9-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="4ffd9-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4ffd9-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="4ffd9-113">Parent Elements</span></span>

|<span data-ttu-id="4ffd9-114">Element</span><span class="sxs-lookup"><span data-stu-id="4ffd9-114">Element</span></span>|<span data-ttu-id="4ffd9-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4ffd9-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4ffd9-116">SelectionCondition Element för EntrySelectedBy för ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="4ffd9-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="4ffd9-117">Definierar de villkor som måste finnas för den här posten som ska användas.</span><span class="sxs-lookup"><span data-stu-id="4ffd9-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4ffd9-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="4ffd9-118">Text Value</span></span>

<span data-ttu-id="4ffd9-119">Ange namnet på .NET-egenskapen.</span><span class="sxs-lookup"><span data-stu-id="4ffd9-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="4ffd9-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="4ffd9-120">Remarks</span></span>

<span data-ttu-id="4ffd9-121">Urvalsvillkoret måste ange minst en egenskapsnamn eller ett skriptblock, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="4ffd9-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="4ffd9-122">Läs mer om hur du använder villkor för val av [definiera villkor för när en post i vyn eller objektet används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="4ffd9-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="4ffd9-123">Läs mer om andra komponenter i en listvy, [skapar listvyn](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="4ffd9-123">For more information about other components of a list view, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4ffd9-124">Se även</span><span class="sxs-lookup"><span data-stu-id="4ffd9-124">See Also</span></span>

[<span data-ttu-id="4ffd9-125">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="4ffd9-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="4ffd9-126">Definiera villkor för när Data visas</span><span class="sxs-lookup"><span data-stu-id="4ffd9-126">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="4ffd9-127">ListEntry Element (Format)</span><span class="sxs-lookup"><span data-stu-id="4ffd9-127">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="4ffd9-128">ScriptBlock Element för SelectionCondition för EntrySelectedBy för ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="4ffd9-128">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="4ffd9-129">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="4ffd9-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
