---
title: TypeName-Element för SelectionCondition för EntrySelectedBy för TableControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e97d56fb-4e35-447a-9282-26f10d0a4609
caps.latest.revision: 11
ms.openlocfilehash: fe65ac95cead7df0069ffdae666fb34b7309fbb6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847161"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="6a843-102">TypeName-element för SelectionCondition för EntrySelectedBy för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="6a843-102">TypeName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="6a843-103">Anger ett .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="6a843-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="6a843-104">Om den här typen finns villkoret uppfylls och tabellraden används.</span><span class="sxs-lookup"><span data-stu-id="6a843-104">When this type is present, the condition is met, and the table row is used.</span></span>

<span data-ttu-id="6a843-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy konfigurationselement för TableRowEntry (Format) SelectionCondition Element för EntrySelectedBy för TableRowEntry (Format) TypeName-elementet för SelectionCondition för EntrySelectedBy för TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6a843-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6a843-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="6a843-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6a843-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="6a843-107">Attributes and Elements</span></span>

<span data-ttu-id="6a843-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `TypeName` element.</span><span class="sxs-lookup"><span data-stu-id="6a843-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6a843-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="6a843-109">Attributes</span></span>

<span data-ttu-id="6a843-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="6a843-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6a843-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="6a843-111">Child Elements</span></span>

<span data-ttu-id="6a843-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="6a843-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6a843-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="6a843-113">Parent Elements</span></span>

|<span data-ttu-id="6a843-114">Element</span><span class="sxs-lookup"><span data-stu-id="6a843-114">Element</span></span>|<span data-ttu-id="6a843-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6a843-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6a843-116">SelectionCondition Element för EntrySelectedBy för TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6a843-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="6a843-117">Definierar de villkor som måste finnas för den här tabellraden som ska användas.</span><span class="sxs-lookup"><span data-stu-id="6a843-117">Defines the condition that must exist for this table row to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6a843-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="6a843-118">Text Value</span></span>

<span data-ttu-id="6a843-119">Ange det fullständigt kvalificerade namnet för .NET-typ, till exempel `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="6a843-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="6a843-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="6a843-120">Remarks</span></span>

<span data-ttu-id="6a843-121">Urvalsvillkoret kan ange valfritt antal typer i .NET eller val av anger, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="6a843-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="6a843-122">Läs mer om hur du använder villkor för val av [definiera villkor för när en post i vyn eller objektet används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="6a843-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="6a843-123">Läs mer om komponenterna i en tabellvy, [skapar en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="6a843-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6a843-124">Se även</span><span class="sxs-lookup"><span data-stu-id="6a843-124">See Also</span></span>

[<span data-ttu-id="6a843-125">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="6a843-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="6a843-126">Definiera villkor för när Data visas</span><span class="sxs-lookup"><span data-stu-id="6a843-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="6a843-127">SelectionCondition Element för EntrySelectedBy för TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6a843-127">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="6a843-128">SelectionSetName Element för SelectionCondition för EntrySelectedBy för TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6a843-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="6a843-129">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="6a843-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
