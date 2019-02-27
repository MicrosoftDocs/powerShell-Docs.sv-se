---
title: ScriptBlock Element för SelectionCondition för EntrySelectedBy för ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a1adad7-e864-4892-9d26-a6476a9698d2
caps.latest.revision: 7
ms.openlocfilehash: fd708473d04a76bcf6cf3a8f8278e1d15fb9addf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848673"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="57774-102">ScriptBlock-element för SelectionCondition för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="57774-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="57774-103">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="57774-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="57774-104">När det här skriptet ska utvärderas till `true`villkoret uppfylls och kortet används.</span><span class="sxs-lookup"><span data-stu-id="57774-104">When this script is evaluated to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="57774-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy konfigurationselement för ListEntry (Format) SelectionCondition elementet för EntrySelectedBy för ListEntry (Format) ScriptBlock elementet för SelectionCondition för EntrySelectedBy för ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="57774-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="57774-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="57774-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="57774-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="57774-107">Attributes and Elements</span></span>

<span data-ttu-id="57774-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="57774-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="57774-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="57774-109">Attributes</span></span>

<span data-ttu-id="57774-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="57774-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="57774-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="57774-111">Child Elements</span></span>

<span data-ttu-id="57774-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="57774-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="57774-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="57774-113">Parent Elements</span></span>

|<span data-ttu-id="57774-114">Element</span><span class="sxs-lookup"><span data-stu-id="57774-114">Element</span></span>|<span data-ttu-id="57774-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="57774-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="57774-116">SelectionCondition Element för EntrySelectedBy för ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="57774-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="57774-117">Definierar de villkor som måste finnas för den här posten som ska användas.</span><span class="sxs-lookup"><span data-stu-id="57774-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="57774-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="57774-118">Text Value</span></span>

<span data-ttu-id="57774-119">Ange det skript som ska utvärderas.</span><span class="sxs-lookup"><span data-stu-id="57774-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="57774-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="57774-120">Remarks</span></span>

<span data-ttu-id="57774-121">Urvalsvillkoret måste ange ett minst ett skript eller egenskapen namn för att utvärdera, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="57774-121">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="57774-122">(Läs mer om hur du kan använda villkor för val av [definiera villkor för när en post i vyn eller objektet används](./defining-conditions-for-displaying-data.md).)</span><span class="sxs-lookup"><span data-stu-id="57774-122">(For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).)</span></span>

<span data-ttu-id="57774-123">Läs mer om de andra komponenterna i en listvy, [listvyn](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="57774-123">For more information about the other components of a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="57774-124">Se även</span><span class="sxs-lookup"><span data-stu-id="57774-124">See Also</span></span>

[<span data-ttu-id="57774-125">ListEntry Element (Format)</span><span class="sxs-lookup"><span data-stu-id="57774-125">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="57774-126">PropertyName-Element för SelectionCondition för EmtrySelectedBy för ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="57774-126">PropertyName Element for SelectionCondition for EmtrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="57774-127">SelectionCondition Element för EntrySelectedBy för ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="57774-127">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="57774-128">Listvy</span><span class="sxs-lookup"><span data-stu-id="57774-128">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="57774-129">Definiera villkor för när en post för vyn eller objekt används</span><span class="sxs-lookup"><span data-stu-id="57774-129">Defining Conditions for when a View Entry or Item is Used</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="57774-130">Skriva ett Windows PowerShell formatering och skriver fil</span><span class="sxs-lookup"><span data-stu-id="57774-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
