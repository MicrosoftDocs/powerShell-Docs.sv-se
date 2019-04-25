---
title: SelectionSetName Element för EntrySelectedBy för GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569c623-2277-49e3-933e-c26262b91cd5
caps.latest.revision: 6
ms.openlocfilehash: 69cd113c444b4e3c5dceabcdfddb439cd1376f6b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064075"
---
# <a name="selectionsetname-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="23a17-102">SelectionSetName-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="23a17-102">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="23a17-103">Anger en uppsättning med .NET-objekt för posten.</span><span class="sxs-lookup"><span data-stu-id="23a17-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="23a17-104">Det finns ingen gräns för hur många uppsättningar för val av som kan anges för en post.</span><span class="sxs-lookup"><span data-stu-id="23a17-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span> <span data-ttu-id="23a17-105">Det här elementet används när du definierar hur en ny grupp med objekt visas.</span><span class="sxs-lookup"><span data-stu-id="23a17-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="23a17-106">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för Visa (Format) anpassad kontroll elementet för GroupBy (Format) CustomEntries Element för anpassad kontroll för GroupBy (Format) CustomEntry elementet för Anpassad kontroll för GroupBy (Format) EntrySelectedBy elementet för CustomEntry för GroupBy (Format) SelectionSetName elementet för EntrySelectedBy för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="23a17-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="23a17-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="23a17-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="23a17-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="23a17-108">Attributes and Elements</span></span>

<span data-ttu-id="23a17-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `SelectionSetName` element.</span><span class="sxs-lookup"><span data-stu-id="23a17-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="23a17-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="23a17-110">Attributes</span></span>

<span data-ttu-id="23a17-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="23a17-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="23a17-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="23a17-112">Child Elements</span></span>

<span data-ttu-id="23a17-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="23a17-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="23a17-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="23a17-114">Parent Elements</span></span>

|<span data-ttu-id="23a17-115">Element</span><span class="sxs-lookup"><span data-stu-id="23a17-115">Element</span></span>|<span data-ttu-id="23a17-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="23a17-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="23a17-117">EntrySelectedBy Element för CustomEntry för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="23a17-117">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="23a17-118">Definierar vilka typer av .NET som använder den här anpassade posten eller villkor som måste finnas för den här posten som ska användas.</span><span class="sxs-lookup"><span data-stu-id="23a17-118">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="23a17-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="23a17-119">Text Value</span></span>

<span data-ttu-id="23a17-120">Ange namnet på val av uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="23a17-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="23a17-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="23a17-121">Remarks</span></span>

<span data-ttu-id="23a17-122">Varje anpassad kontrolldefinition måste ha minst ett namn, val av set eller Urvalsvillkoret som definierats.</span><span class="sxs-lookup"><span data-stu-id="23a17-122">Each custom control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="23a17-123">Inställningarna används vanligtvis när du vill definiera en grupp med objekt som används i flera vyer.</span><span class="sxs-lookup"><span data-stu-id="23a17-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="23a17-124">Du kanske exempelvis vill skapa en tabell och en listvy för samma uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="23a17-124">For example, you may want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="23a17-125">Mer information om hur du definierar inställningarna finns i [definiera val av anger](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="23a17-125">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="23a17-126">Mer information om komponenter för en anpassad kontroll vy finns i [skapar anpassade kontroller](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="23a17-126">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="23a17-127">Se även</span><span class="sxs-lookup"><span data-stu-id="23a17-127">See Also</span></span>

[<span data-ttu-id="23a17-128">EntrySelectedBy Element för CustomEntry för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="23a17-128">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="23a17-129">Skapa anpassade kontroller</span><span class="sxs-lookup"><span data-stu-id="23a17-129">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="23a17-130">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="23a17-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
