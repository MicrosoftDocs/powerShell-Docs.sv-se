---
title: SelectionSetName-element för EntrySelectedBy för EnumerableExpansion (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 936d09f2-2c48-49e8-ab2d-0c8729199a2e
caps.latest.revision: 8
ms.openlocfilehash: 8ba8931ea5e34f610878351396cad42023393ad6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358859"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="e783f-102">SelectionSetName-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="e783f-102">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="e783f-103">Anger den uppsättning av .NET-typer som expanderas av den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="e783f-103">Specifies the set of .NET types that are expanded by this definition.</span></span>

<span data-ttu-id="e783f-104">Konfigurations element (format) DefaultSettings-element (format) EnumerableExpansions-element (format) EnumerableExpansion-element (format) EntrySelectedBy-element för EnumerableExpansion (format) SelectionSetName-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="e783f-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e783f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e783f-105">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="e783f-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="e783f-106">Attributes and Elements</span></span>

<span data-ttu-id="e783f-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `SelectionSetName`-elementet.</span><span class="sxs-lookup"><span data-stu-id="e783f-107">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e783f-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="e783f-108">Attributes</span></span>

<span data-ttu-id="e783f-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="e783f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e783f-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="e783f-110">Child Elements</span></span>

<span data-ttu-id="e783f-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="e783f-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e783f-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="e783f-112">Parent Elements</span></span>

|<span data-ttu-id="e783f-113">Element</span><span class="sxs-lookup"><span data-stu-id="e783f-113">Element</span></span>|<span data-ttu-id="e783f-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e783f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e783f-115">EntrySelectedBy-element för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="e783f-115">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="e783f-116">Definierar de .NET-samlings objekt som ska expanderas av den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="e783f-116">Defines the .NET collection objects that are expanded by this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e783f-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="e783f-117">Text Value</span></span>

<span data-ttu-id="e783f-118">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="e783f-118">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="e783f-119">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="e783f-119">Remarks</span></span>

<span data-ttu-id="e783f-120">Varje definition måste ange ett eller flera typnamn, en markerings uppsättning eller ett markerings villkor.</span><span class="sxs-lookup"><span data-stu-id="e783f-120">Each definition must specify one or more type names, a selection set, or a selection condition.</span></span>

<span data-ttu-id="e783f-121">Urvals uppsättningar används vanligt vis när du vill definiera en grupp objekt som används i flera vyer.</span><span class="sxs-lookup"><span data-stu-id="e783f-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="e783f-122">Du kanske till exempel vill skapa en tabellvy och en listvy för samma uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="e783f-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="e783f-123">Mer information om hur du definierar urvals uppsättningar finns i [definiera uppsättningar av objekt för en vy](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="e783f-123">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e783f-124">Se även</span><span class="sxs-lookup"><span data-stu-id="e783f-124">See Also</span></span>

[<span data-ttu-id="e783f-125">Definiera urvals uppsättningar</span><span class="sxs-lookup"><span data-stu-id="e783f-125">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="e783f-126">EntrySelectedBy-element för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="e783f-126">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)

[<span data-ttu-id="e783f-127">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="e783f-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
