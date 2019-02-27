---
title: ScriptBlock Element för SelectionCondition för EntrySelectedBy för TableControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b11fbcf-3426-48ae-9319-2c847969f723
caps.latest.revision: 10
ms.openlocfilehash: 7afc834e68ef332bee1e23da782fb5c5527fcf54
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846517"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="3a1e6-102">ScriptBlock-element för SelectionCondition för EntrySelectedBy för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="3a1e6-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="3a1e6-103">Anger skriptblocket som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="3a1e6-103">Specifies the script block that triggers the condition.</span></span> <span data-ttu-id="3a1e6-104">När det här skriptet ska utvärderas till `true`villkoret uppfylls och tabellposten används.</span><span class="sxs-lookup"><span data-stu-id="3a1e6-104">When this script is evaluated to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="3a1e6-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy konfigurationselement för TableRowEntry (Format) SelectionCondition Element för EntrySelectedBy för TableRowEntry (Format) ScriptBlock elementet för SelectionCondition för EntrySelectedBy för TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="3a1e6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3a1e6-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="3a1e6-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3a1e6-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="3a1e6-107">Attributes and Elements</span></span>

<span data-ttu-id="3a1e6-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="3a1e6-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3a1e6-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="3a1e6-109">Attributes</span></span>

<span data-ttu-id="3a1e6-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="3a1e6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3a1e6-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="3a1e6-111">Child Elements</span></span>

<span data-ttu-id="3a1e6-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="3a1e6-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3a1e6-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="3a1e6-113">Parent Elements</span></span>

|<span data-ttu-id="3a1e6-114">Element</span><span class="sxs-lookup"><span data-stu-id="3a1e6-114">Element</span></span>|<span data-ttu-id="3a1e6-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3a1e6-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3a1e6-116">SelectionCondition Element för EntrySelectedBy för TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="3a1e6-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="3a1e6-117">Definierar de villkor som måste finnas för den här tabellposten som ska användas.</span><span class="sxs-lookup"><span data-stu-id="3a1e6-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3a1e6-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="3a1e6-118">Text Value</span></span>

<span data-ttu-id="3a1e6-119">Ange det skript som ska utvärderas.</span><span class="sxs-lookup"><span data-stu-id="3a1e6-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="3a1e6-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="3a1e6-120">Remarks</span></span>

<span data-ttu-id="3a1e6-121">Urvalsvillkoret måste ange minst en blockera eller egenskapen skriptnamn, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="3a1e6-121">The selection condition must specify at least one script block or property name, but cannot specify both.</span></span> <span data-ttu-id="3a1e6-122">Läs mer om hur du använder villkor för val av [definiera villkor för när en post i vyn eller objektet används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="3a1e6-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="3a1e6-123">Läs mer om komponenterna i en tabellvy, [skapar en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="3a1e6-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3a1e6-124">Se även</span><span class="sxs-lookup"><span data-stu-id="3a1e6-124">See Also</span></span>

[<span data-ttu-id="3a1e6-125">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="3a1e6-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="3a1e6-126">Definiera villkor för när Data visas</span><span class="sxs-lookup"><span data-stu-id="3a1e6-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="3a1e6-127">PropertyName-Element för SelectionCondition för EntrySelectedBy för TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="3a1e6-127">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="3a1e6-128">SelectionCondition Element för EntrySelectedBy för TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="3a1e6-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="3a1e6-129">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="3a1e6-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
