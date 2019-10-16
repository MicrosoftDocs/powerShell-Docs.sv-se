---
title: SelectionSetName-element för EntrySelectedBy för WideControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9c6e18f-6cca-465c-bd20-3969e7897a96
caps.latest.revision: 10
ms.openlocfilehash: 6b6a4a4647412d11d947f1dc4ea12d1e05ff536e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353811"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="c56ad-102">SelectionSetName-element för EntrySelectedBy för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="c56ad-102">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="c56ad-103">Anger en uppsättning .NET-objekt för definitionen.</span><span class="sxs-lookup"><span data-stu-id="c56ad-103">Specifies a set of .NET objects for the definition.</span></span> <span data-ttu-id="c56ad-104">Definitionen används när något av dessa objekt visas.</span><span class="sxs-lookup"><span data-stu-id="c56ad-104">The definition is used whenever one of these objects is displayed.</span></span>

<span data-ttu-id="c56ad-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) WideEntries-element (format) WideEntry element (format) EntrySelectedBy-element för WideEntry (format) SelectionSetName-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="c56ad-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c56ad-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="c56ad-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="c56ad-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="c56ad-107">Attributes and Elements</span></span>

<span data-ttu-id="c56ad-108">I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet för elementet `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="c56ad-108">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c56ad-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="c56ad-109">Attributes</span></span>

<span data-ttu-id="c56ad-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="c56ad-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c56ad-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="c56ad-111">Child Elements</span></span>

<span data-ttu-id="c56ad-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="c56ad-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c56ad-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="c56ad-113">Parent Elements</span></span>

|<span data-ttu-id="c56ad-114">Element</span><span class="sxs-lookup"><span data-stu-id="c56ad-114">Element</span></span>|<span data-ttu-id="c56ad-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c56ad-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c56ad-116">EntrySelectedBy-element för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="c56ad-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="c56ad-117">Definierar de .NET-typer som använder den här breda posten eller det villkor som måste finnas för att den här posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="c56ad-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c56ad-118">Text värde</span><span class="sxs-lookup"><span data-stu-id="c56ad-118">Text Value</span></span>

<span data-ttu-id="c56ad-119">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="c56ad-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="c56ad-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="c56ad-120">Remarks</span></span>

<span data-ttu-id="c56ad-121">Varje definition måste ange ett typ namn, en urvals uppsättning eller ett markerings villkor.</span><span class="sxs-lookup"><span data-stu-id="c56ad-121">Each definition must specify one type name, selection set, or selection condition.</span></span>

<span data-ttu-id="c56ad-122">Urvals uppsättningar används vanligt vis när du vill definiera en grupp objekt som används i flera vyer.</span><span class="sxs-lookup"><span data-stu-id="c56ad-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="c56ad-123">Du kanske till exempel vill skapa en tabellvy och en listvy för samma uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="c56ad-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="c56ad-124">Mer information om hur du definierar urvals uppsättningar finns i [definiera uppsättningar av objekt för en vy](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="c56ad-124">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="c56ad-125">Mer information om andra komponenter i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="c56ad-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c56ad-126">Se även</span><span class="sxs-lookup"><span data-stu-id="c56ad-126">See Also</span></span>

[<span data-ttu-id="c56ad-127">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="c56ad-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="c56ad-128">Definiera urvals uppsättningar</span><span class="sxs-lookup"><span data-stu-id="c56ad-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="c56ad-129">EntrySelectedBy-element för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="c56ad-129">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="c56ad-130">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="c56ad-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
