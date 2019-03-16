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
ms.openlocfilehash: 7d526372cf80327b3fb9b79b6e83429c57780183
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059022"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="17034-102">PropertyName-element för SelectionCondition för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="17034-102">PropertyName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="17034-103">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="17034-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="17034-104">När den här egenskapen finns eller att inventera till `true`villkoret uppfylls och kortet används.</span><span class="sxs-lookup"><span data-stu-id="17034-104">When this property is present or when it evaluates to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="17034-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy konfigurationselement för ListEntry (Format) SelectionCondition elementet för EntrySelectedBy för ListEntry (Format) PropertyName elementet för SelectionCondition för EntrySelectedBy för ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="17034-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="17034-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="17034-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="17034-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="17034-107">Attributes and Elements</span></span>

<span data-ttu-id="17034-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `PropertyName` element.</span><span class="sxs-lookup"><span data-stu-id="17034-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="17034-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="17034-109">Attributes</span></span>

<span data-ttu-id="17034-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="17034-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="17034-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="17034-111">Child Elements</span></span>

<span data-ttu-id="17034-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="17034-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="17034-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="17034-113">Parent Elements</span></span>

|<span data-ttu-id="17034-114">Element</span><span class="sxs-lookup"><span data-stu-id="17034-114">Element</span></span>|<span data-ttu-id="17034-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="17034-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="17034-116">SelectionCondition Element för EntrySelectedBy för ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="17034-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="17034-117">Definierar de villkor som måste finnas för den här posten som ska användas.</span><span class="sxs-lookup"><span data-stu-id="17034-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="17034-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="17034-118">Text Value</span></span>

<span data-ttu-id="17034-119">Ange namnet på .NET-egenskapen.</span><span class="sxs-lookup"><span data-stu-id="17034-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="17034-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="17034-120">Remarks</span></span>

<span data-ttu-id="17034-121">Urvalsvillkoret måste ange minst en egenskapsnamn eller ett skriptblock, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="17034-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="17034-122">Läs mer om hur du använder villkor för val av [definiera villkor för när en post i vyn eller objektet används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="17034-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="17034-123">Läs mer om andra komponenter i en listvy, [skapar listvyn](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="17034-123">For more information about other components of a list view, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="17034-124">Se även</span><span class="sxs-lookup"><span data-stu-id="17034-124">See Also</span></span>

[<span data-ttu-id="17034-125">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="17034-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="17034-126">Definiera villkor för när Data visas</span><span class="sxs-lookup"><span data-stu-id="17034-126">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="17034-127">ListEntry Element (Format)</span><span class="sxs-lookup"><span data-stu-id="17034-127">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="17034-128">ScriptBlock Element för SelectionCondition för EntrySelectedBy för ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="17034-128">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="17034-129">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="17034-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
