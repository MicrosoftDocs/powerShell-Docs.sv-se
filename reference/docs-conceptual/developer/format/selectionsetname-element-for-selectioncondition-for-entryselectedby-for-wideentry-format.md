---
title: SelectionSetName-element för SelectionCondition för EntrySelectedBy för WideEntry (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a13a429c-a31b-4e29-828c-c0c0917b5415
caps.latest.revision: 11
ms.openlocfilehash: baea89e4b259611dfa45b6bcf94fa0bf2df6b9de
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358819"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="1b9fb-102">SelectionSetName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="1b9fb-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="1b9fb-103">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="1b9fb-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="1b9fb-104">När någon av typerna i den här uppsättningen finns, uppfylls villkoret och objektet visas genom att använda den här definitionen av wide View.</span><span class="sxs-lookup"><span data-stu-id="1b9fb-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the wide view.</span></span>

<span data-ttu-id="1b9fb-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) WideEntries-element (format) WideEntry element (format) EntrySelectedBy-element för WideEntry (format) SelectionCondition-element för EntrySelectedBy för WideEntry (format) SelectionSetName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="1b9fb-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1b9fb-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="1b9fb-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1b9fb-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="1b9fb-107">Attributes and Elements</span></span>

<span data-ttu-id="1b9fb-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `SelectionSetName`-elementet.</span><span class="sxs-lookup"><span data-stu-id="1b9fb-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1b9fb-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="1b9fb-109">Attributes</span></span>

<span data-ttu-id="1b9fb-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="1b9fb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1b9fb-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="1b9fb-111">Child Elements</span></span>

<span data-ttu-id="1b9fb-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="1b9fb-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1b9fb-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="1b9fb-113">Parent Elements</span></span>

|<span data-ttu-id="1b9fb-114">Element</span><span class="sxs-lookup"><span data-stu-id="1b9fb-114">Element</span></span>|<span data-ttu-id="1b9fb-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1b9fb-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1b9fb-116">SelectionCondition-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="1b9fb-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="1b9fb-117">Definierar det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="1b9fb-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1b9fb-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="1b9fb-118">Text Value</span></span>

<span data-ttu-id="1b9fb-119">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="1b9fb-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="1b9fb-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="1b9fb-120">Remarks</span></span>

<span data-ttu-id="1b9fb-121">Urvals villkoret kan ange en urvals uppsättning eller en .NET-typ, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="1b9fb-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="1b9fb-122">Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="1b9fb-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="1b9fb-123">Urvals uppsättningar är vanliga grupper av .NET-objekt som kan användas av alla vyer som format filen definierar.</span><span class="sxs-lookup"><span data-stu-id="1b9fb-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="1b9fb-124">Mer information om hur du skapar och refererar till urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="1b9fb-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="1b9fb-125">Mer information om andra komponenter i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="1b9fb-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1b9fb-126">Se även</span><span class="sxs-lookup"><span data-stu-id="1b9fb-126">See Also</span></span>

[<span data-ttu-id="1b9fb-127">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="1b9fb-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="1b9fb-128">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="1b9fb-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="1b9fb-129">Definiera urvals uppsättningar</span><span class="sxs-lookup"><span data-stu-id="1b9fb-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="1b9fb-130">SelectionCondition-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="1b9fb-130">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="1b9fb-131">Elementet TypeName för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="1b9fb-131">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="1b9fb-132">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="1b9fb-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
