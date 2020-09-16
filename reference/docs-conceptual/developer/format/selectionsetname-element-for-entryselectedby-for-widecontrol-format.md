---
title: SelectionSetName-element för EntrySelectedBy för WideControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 546225b0619ebec83d04a7e27bbc298ffef0a14d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785259"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="334bb-102">SelectionSetName-element för EntrySelectedBy för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="334bb-102">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="334bb-103">Anger en uppsättning .NET-objekt för definitionen.</span><span class="sxs-lookup"><span data-stu-id="334bb-103">Specifies a set of .NET objects for the definition.</span></span> <span data-ttu-id="334bb-104">Definitionen används när något av dessa objekt visas.</span><span class="sxs-lookup"><span data-stu-id="334bb-104">The definition is used whenever one of these objects is displayed.</span></span>

<span data-ttu-id="334bb-105">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) WideControl-element (format) WideEntries-element (format) WideEntry element (format) EntrySelectedBy-element för WideEntry (format) SelectionSetName-element för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="334bb-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="334bb-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="334bb-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="334bb-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="334bb-107">Attributes and Elements</span></span>

<span data-ttu-id="334bb-108">I följande avsnitt beskrivs attributen, underordnade element och `SelectionSetName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="334bb-108">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="334bb-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="334bb-109">Attributes</span></span>

<span data-ttu-id="334bb-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="334bb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="334bb-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="334bb-111">Child Elements</span></span>

<span data-ttu-id="334bb-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="334bb-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="334bb-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="334bb-113">Parent Elements</span></span>

|<span data-ttu-id="334bb-114">Element</span><span class="sxs-lookup"><span data-stu-id="334bb-114">Element</span></span>|<span data-ttu-id="334bb-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="334bb-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="334bb-116">EntrySelectedBy-element för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="334bb-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="334bb-117">Definierar de .NET-typer som använder den här breda posten eller det villkor som måste finnas för att den här posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="334bb-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="334bb-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="334bb-118">Text Value</span></span>

<span data-ttu-id="334bb-119">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="334bb-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="334bb-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="334bb-120">Remarks</span></span>

<span data-ttu-id="334bb-121">Varje definition måste ange ett typ namn, en urvals uppsättning eller ett markerings villkor.</span><span class="sxs-lookup"><span data-stu-id="334bb-121">Each definition must specify one type name, selection set, or selection condition.</span></span>

<span data-ttu-id="334bb-122">Urvals uppsättningar används vanligt vis när du vill definiera en grupp objekt som används i flera vyer.</span><span class="sxs-lookup"><span data-stu-id="334bb-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="334bb-123">Du kanske till exempel vill skapa en tabellvy och en listvy för samma uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="334bb-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="334bb-124">Mer information om hur du definierar urvals uppsättningar finns i [definiera uppsättningar av objekt för en vy](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="334bb-124">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="334bb-125">Mer information om andra komponenter i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="334bb-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="334bb-126">Se även</span><span class="sxs-lookup"><span data-stu-id="334bb-126">See Also</span></span>

[<span data-ttu-id="334bb-127">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="334bb-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="334bb-128">Definiera valuppsättningar</span><span class="sxs-lookup"><span data-stu-id="334bb-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="334bb-129">EntrySelectedBy-element för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="334bb-129">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="334bb-130">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="334bb-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
