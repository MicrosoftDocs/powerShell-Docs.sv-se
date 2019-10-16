---
title: PropertyName-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3b4d9b-2b8c-4a3a-8887-6c606eb9d490
caps.latest.revision: 10
ms.openlocfilehash: 48011950ed64e78a84292762f2c7779003dc59fd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355925"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format"></a><span data-ttu-id="8f678-102">PropertyName-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="8f678-102">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

<span data-ttu-id="8f678-103">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="8f678-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="8f678-104">När den här egenskapen finns eller när den utvärderas till `true`, uppfylls villkoret och tabell posten används.</span><span class="sxs-lookup"><span data-stu-id="8f678-104">When this property is present or when it evaluates to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="8f678-105">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) TableControl-element (format) TableRowEntries-element (format) TableRowEntry element (format) EntrySelectedBy-element för TableRowEntry (format) SelectionCondition-element för EntrySelectedBy för TableRowEntry (format) PropertyName-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="8f678-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8f678-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="8f678-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8f678-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="8f678-107">Attributes and Elements</span></span>

<span data-ttu-id="8f678-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="8f678-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8f678-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="8f678-109">Attributes</span></span>

<span data-ttu-id="8f678-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="8f678-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8f678-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="8f678-111">Child Elements</span></span>

<span data-ttu-id="8f678-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="8f678-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8f678-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="8f678-113">Parent Elements</span></span>

|<span data-ttu-id="8f678-114">Element</span><span class="sxs-lookup"><span data-stu-id="8f678-114">Element</span></span>|<span data-ttu-id="8f678-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8f678-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8f678-116">SelectionCondition-element för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="8f678-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="8f678-117">Definierar det villkor som måste finnas för att den här tabell posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="8f678-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8f678-118">Text värde</span><span class="sxs-lookup"><span data-stu-id="8f678-118">Text Value</span></span>

<span data-ttu-id="8f678-119">Ange .NET-egenskaps namnet.</span><span class="sxs-lookup"><span data-stu-id="8f678-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="8f678-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="8f678-120">Remarks</span></span>

<span data-ttu-id="8f678-121">Urvals villkoret måste innehålla minst ett egenskaps namn eller ett skript block, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="8f678-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="8f678-122">Mer information om hur urvals villkor kan användas finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="8f678-122">For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="8f678-123">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="8f678-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8f678-124">Se även</span><span class="sxs-lookup"><span data-stu-id="8f678-124">See Also</span></span>

[<span data-ttu-id="8f678-125">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="8f678-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="8f678-126">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="8f678-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="8f678-127">Script block-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="8f678-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="8f678-128">SelectionCondition-element för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="8f678-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="8f678-129">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="8f678-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
