---
title: SelectionSetName-element för SelectionCondition för EntrySelectedBy för ListEntry (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eae67e47-6c60-4741-8430-78d2cb6067b1
caps.latest.revision: 10
ms.openlocfilehash: ccfc0b772ad3b2d1979c7c832a5153de870035d7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358831"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a><span data-ttu-id="e5fcd-102">SelectionSetName-element för SelectionCondition för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="e5fcd-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

<span data-ttu-id="e5fcd-103">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="e5fcd-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="e5fcd-104">När någon av typerna i den här uppsättningen finns, uppfylls villkoret och objektet visas med hjälp av den här definitionen av listvyn.</span><span class="sxs-lookup"><span data-stu-id="e5fcd-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the list view.</span></span>

<span data-ttu-id="e5fcd-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) ListEntries-element (format) ListEntry element (format) EntrySelectedBy-element för ListEntry (format) SelectionCondition-element för EntrySelectedBy för ListEntry (format) SelectionSetName-element för SelectionCondition för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="e5fcd-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e5fcd-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e5fcd-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e5fcd-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="e5fcd-107">Attributes and Elements</span></span>

<span data-ttu-id="e5fcd-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `SelectionSetName`-elementet.</span><span class="sxs-lookup"><span data-stu-id="e5fcd-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e5fcd-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="e5fcd-109">Attributes</span></span>

<span data-ttu-id="e5fcd-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="e5fcd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e5fcd-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="e5fcd-111">Child Elements</span></span>

<span data-ttu-id="e5fcd-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="e5fcd-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e5fcd-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="e5fcd-113">Parent Elements</span></span>

|<span data-ttu-id="e5fcd-114">Element</span><span class="sxs-lookup"><span data-stu-id="e5fcd-114">Element</span></span>|<span data-ttu-id="e5fcd-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e5fcd-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5fcd-116">SelectionCondition-element för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="e5fcd-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="e5fcd-117">Definierar det villkor som måste finnas för att använda den här definitionen av listvyn.</span><span class="sxs-lookup"><span data-stu-id="e5fcd-117">Defines the condition that must exist to use this definition of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e5fcd-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="e5fcd-118">Text Value</span></span>

<span data-ttu-id="e5fcd-119">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="e5fcd-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="e5fcd-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="e5fcd-120">Remarks</span></span>

<span data-ttu-id="e5fcd-121">Urvals villkoret kan ange en urvals uppsättning eller en .NET-typ, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="e5fcd-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="e5fcd-122">Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e5fcd-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="e5fcd-123">Urvals uppsättningar är vanliga grupper av .NET-objekt som kan användas av alla vyer som format filen definierar.</span><span class="sxs-lookup"><span data-stu-id="e5fcd-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="e5fcd-124">Mer information om hur du skapar och refererar till urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="e5fcd-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="e5fcd-125">Mer information om andra komponenter i en listvy finns i [skapa en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="e5fcd-125">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e5fcd-126">Se även</span><span class="sxs-lookup"><span data-stu-id="e5fcd-126">See Also</span></span>

[<span data-ttu-id="e5fcd-127">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="e5fcd-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="e5fcd-128">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="e5fcd-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="e5fcd-129">SelectionCondition-element för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="e5fcd-129">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="e5fcd-130">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="e5fcd-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
