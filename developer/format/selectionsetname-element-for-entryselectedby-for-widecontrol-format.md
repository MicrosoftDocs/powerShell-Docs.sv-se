---
title: SelectionSetName Element för EntrySelectedBy för WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9c6e18f-6cca-465c-bd20-3969e7897a96
caps.latest.revision: 10
ms.openlocfilehash: 6b6a4a4647412d11d947f1dc4ea12d1e05ff536e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064041"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="b5e1c-102">SelectionSetName-element för EntrySelectedBy för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="b5e1c-102">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="b5e1c-103">Anger en uppsättning med .NET-objekt för definitionen.</span><span class="sxs-lookup"><span data-stu-id="b5e1c-103">Specifies a set of .NET objects for the definition.</span></span> <span data-ttu-id="b5e1c-104">Definitionen används när en av de här objekten visas.</span><span class="sxs-lookup"><span data-stu-id="b5e1c-104">The definition is used whenever one of these objects is displayed.</span></span>

<span data-ttu-id="b5e1c-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy konfigurationselement för WideEntry (Format) SelectionSetName elementet för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="b5e1c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b5e1c-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="b5e1c-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="b5e1c-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="b5e1c-107">Attributes and Elements</span></span>

<span data-ttu-id="b5e1c-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `SelectionSetName` element.</span><span class="sxs-lookup"><span data-stu-id="b5e1c-108">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b5e1c-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="b5e1c-109">Attributes</span></span>

<span data-ttu-id="b5e1c-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="b5e1c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b5e1c-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="b5e1c-111">Child Elements</span></span>

<span data-ttu-id="b5e1c-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="b5e1c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b5e1c-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="b5e1c-113">Parent Elements</span></span>

|<span data-ttu-id="b5e1c-114">Element</span><span class="sxs-lookup"><span data-stu-id="b5e1c-114">Element</span></span>|<span data-ttu-id="b5e1c-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b5e1c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b5e1c-116">EntrySelectedBy Element för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="b5e1c-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="b5e1c-117">Definierar vilka typer av .NET som använder den här wide posten eller villkor som måste finnas för den här posten som ska användas.</span><span class="sxs-lookup"><span data-stu-id="b5e1c-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b5e1c-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="b5e1c-118">Text Value</span></span>

<span data-ttu-id="b5e1c-119">Ange namnet på val av uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="b5e1c-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="b5e1c-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="b5e1c-120">Remarks</span></span>

<span data-ttu-id="b5e1c-121">Varje definition måste ange ett namn, val av set eller urvalsvillkoret.</span><span class="sxs-lookup"><span data-stu-id="b5e1c-121">Each definition must specify one type name, selection set, or selection condition.</span></span>

<span data-ttu-id="b5e1c-122">Inställningarna används vanligtvis när du vill definiera en grupp med objekt som används i flera vyer.</span><span class="sxs-lookup"><span data-stu-id="b5e1c-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="b5e1c-123">Du kanske vill skapa en tabell och en listvy för samma uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="b5e1c-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="b5e1c-124">Mer information om hur du definierar inställningarna finns i [definiera anger av objekt för en vy](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="b5e1c-124">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="b5e1c-125">Mer information om andra komponenter för en bred vy finns i [skapar en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="b5e1c-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b5e1c-126">Se även</span><span class="sxs-lookup"><span data-stu-id="b5e1c-126">See Also</span></span>

[<span data-ttu-id="b5e1c-127">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="b5e1c-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="b5e1c-128">Definiera inställningarna</span><span class="sxs-lookup"><span data-stu-id="b5e1c-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="b5e1c-129">EntrySelectedBy Element för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="b5e1c-129">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="b5e1c-130">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="b5e1c-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
