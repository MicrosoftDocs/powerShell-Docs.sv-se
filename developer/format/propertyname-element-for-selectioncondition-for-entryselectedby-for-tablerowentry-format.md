---
title: PropertyName-Element för SelectionCondition för EntrySelectedBy för TableRowEntry (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3b4d9b-2b8c-4a3a-8887-6c606eb9d490
caps.latest.revision: 10
ms.openlocfilehash: 48011950ed64e78a84292762f2c7779003dc59fd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064670"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format"></a><span data-ttu-id="687fd-102">PropertyName-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="687fd-102">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

<span data-ttu-id="687fd-103">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="687fd-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="687fd-104">När den här egenskapen finns eller att inventera till `true`villkoret uppfylls och tabellposten används.</span><span class="sxs-lookup"><span data-stu-id="687fd-104">When this property is present or when it evaluates to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="687fd-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy konfigurationselement för TableRowEntry (Format) SelectionCondition Element för EntrySelectedBy för TableRowEntry (Format) PropertyName elementet för SelectionCondition för EntrySelectedBy för TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="687fd-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="687fd-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="687fd-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="687fd-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="687fd-107">Attributes and Elements</span></span>

<span data-ttu-id="687fd-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `PropertyName` element.</span><span class="sxs-lookup"><span data-stu-id="687fd-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="687fd-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="687fd-109">Attributes</span></span>

<span data-ttu-id="687fd-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="687fd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="687fd-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="687fd-111">Child Elements</span></span>

<span data-ttu-id="687fd-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="687fd-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="687fd-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="687fd-113">Parent Elements</span></span>

|<span data-ttu-id="687fd-114">Element</span><span class="sxs-lookup"><span data-stu-id="687fd-114">Element</span></span>|<span data-ttu-id="687fd-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="687fd-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="687fd-116">SelectionCondition Element för EntrySelectedBy för TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="687fd-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="687fd-117">Definierar de villkor som måste finnas för den här tabellposten som ska användas.</span><span class="sxs-lookup"><span data-stu-id="687fd-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="687fd-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="687fd-118">Text Value</span></span>

<span data-ttu-id="687fd-119">Ange namnet på .NET-egenskapen.</span><span class="sxs-lookup"><span data-stu-id="687fd-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="687fd-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="687fd-120">Remarks</span></span>

<span data-ttu-id="687fd-121">Urvalsvillkoret måste ange minst en egenskapsnamn eller ett skriptblock, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="687fd-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="687fd-122">Läs mer om hur du kan använda villkor för val av [definiera villkor för när en post i vyn eller objektet används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="687fd-122">For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="687fd-123">Läs mer om komponenterna i en tabellvy, [skapar en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="687fd-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="687fd-124">Se även</span><span class="sxs-lookup"><span data-stu-id="687fd-124">See Also</span></span>

[<span data-ttu-id="687fd-125">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="687fd-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="687fd-126">Definiera villkor för när Data visas</span><span class="sxs-lookup"><span data-stu-id="687fd-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="687fd-127">ScriptBlock Element för SelectionCondition för EntrySelectedBy för TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="687fd-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="687fd-128">SelectionCondition Element för EntrySelectedBy för TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="687fd-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="687fd-129">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="687fd-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
