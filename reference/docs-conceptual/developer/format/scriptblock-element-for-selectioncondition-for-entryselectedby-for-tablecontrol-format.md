---
title: Script block-element för SelectionCondition för EntrySelectedBy för TableControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b11fbcf-3426-48ae-9319-2c847969f723
caps.latest.revision: 10
ms.openlocfilehash: 7afc834e68ef332bee1e23da782fb5c5527fcf54
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358920"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="95b28-102">ScriptBlock-element för SelectionCondition för EntrySelectedBy för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="95b28-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="95b28-103">Anger det skript block som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="95b28-103">Specifies the script block that triggers the condition.</span></span> <span data-ttu-id="95b28-104">När det här skriptet utvärderas till `true`, uppfylls villkoret och tabell posten används.</span><span class="sxs-lookup"><span data-stu-id="95b28-104">When this script is evaluated to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="95b28-105">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) TableControl-element (format) TableRowEntries-element (format) TableRowEntry element (format) EntrySelectedBy-element för TableRowEntry (format) SelectionCondition-element för EntrySelectedBy för TableRowEntry (format) script block-elementet för SelectionCondition för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="95b28-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="95b28-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="95b28-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="95b28-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="95b28-107">Attributes and Elements</span></span>

<span data-ttu-id="95b28-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `ScriptBlock`-elementet.</span><span class="sxs-lookup"><span data-stu-id="95b28-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="95b28-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="95b28-109">Attributes</span></span>

<span data-ttu-id="95b28-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="95b28-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="95b28-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="95b28-111">Child Elements</span></span>

<span data-ttu-id="95b28-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="95b28-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="95b28-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="95b28-113">Parent Elements</span></span>

|<span data-ttu-id="95b28-114">Element</span><span class="sxs-lookup"><span data-stu-id="95b28-114">Element</span></span>|<span data-ttu-id="95b28-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="95b28-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="95b28-116">SelectionCondition-element för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="95b28-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="95b28-117">Definierar det villkor som måste finnas för att den här tabell posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="95b28-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="95b28-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="95b28-118">Text Value</span></span>

<span data-ttu-id="95b28-119">Ange det skript som utvärderas.</span><span class="sxs-lookup"><span data-stu-id="95b28-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="95b28-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="95b28-120">Remarks</span></span>

<span data-ttu-id="95b28-121">Markerings villkoret måste innehålla minst ett skript block eller egenskaps namn, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="95b28-121">The selection condition must specify at least one script block or property name, but cannot specify both.</span></span> <span data-ttu-id="95b28-122">Mer information om hur du använder urvals villkor finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="95b28-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="95b28-123">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="95b28-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="95b28-124">Se även</span><span class="sxs-lookup"><span data-stu-id="95b28-124">See Also</span></span>

[<span data-ttu-id="95b28-125">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="95b28-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="95b28-126">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="95b28-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="95b28-127">PropertyName-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="95b28-127">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="95b28-128">SelectionCondition-element för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="95b28-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="95b28-129">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="95b28-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
