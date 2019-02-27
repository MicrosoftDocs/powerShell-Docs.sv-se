---
title: SelectionSetName Element för EntrySelectedBy för EnumerableExpansion (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 936d09f2-2c48-49e8-ab2d-0c8729199a2e
caps.latest.revision: 8
ms.openlocfilehash: 8ba8931ea5e34f610878351396cad42023393ad6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851536"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="0c576-102">SelectionSetName-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="0c576-102">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="0c576-103">Anger uppsättningen med .NET-typer som byggs med den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="0c576-103">Specifies the set of .NET types that are expanded by this definition.</span></span>

<span data-ttu-id="0c576-104">Elementet (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy konfigurationselement för EnumerableExpansion (Format) SelectionSetName elementet för EntrySelectedBy för EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="0c576-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0c576-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0c576-105">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="0c576-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="0c576-106">Attributes and Elements</span></span>

<span data-ttu-id="0c576-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `SelectionSetName` element.</span><span class="sxs-lookup"><span data-stu-id="0c576-107">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0c576-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="0c576-108">Attributes</span></span>

<span data-ttu-id="0c576-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="0c576-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0c576-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="0c576-110">Child Elements</span></span>

<span data-ttu-id="0c576-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="0c576-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0c576-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="0c576-112">Parent Elements</span></span>

|<span data-ttu-id="0c576-113">Element</span><span class="sxs-lookup"><span data-stu-id="0c576-113">Element</span></span>|<span data-ttu-id="0c576-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0c576-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0c576-115">EntrySelectedBy Element för EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="0c576-115">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="0c576-116">Definierar de .NET samling objekt som byggs med den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="0c576-116">Defines the .NET collection objects that are expanded by this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0c576-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="0c576-117">Text Value</span></span>

<span data-ttu-id="0c576-118">Ange namnet på val av uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="0c576-118">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="0c576-119">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="0c576-119">Remarks</span></span>

<span data-ttu-id="0c576-120">Varje definition måste ange en eller flera namn, en eller ett val av villkor.</span><span class="sxs-lookup"><span data-stu-id="0c576-120">Each definition must specify one or more type names, a selection set, or a selection condition.</span></span>

<span data-ttu-id="0c576-121">Inställningarna används vanligtvis när du vill definiera en grupp med objekt som används i flera vyer.</span><span class="sxs-lookup"><span data-stu-id="0c576-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="0c576-122">Du kanske vill skapa en tabell och en listvy för samma uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="0c576-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="0c576-123">Mer information om hur du definierar inställningarna finns i [definiera anger av objekt för en vy](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="0c576-123">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0c576-124">Se även</span><span class="sxs-lookup"><span data-stu-id="0c576-124">See Also</span></span>

[<span data-ttu-id="0c576-125">Definiera inställningarna</span><span class="sxs-lookup"><span data-stu-id="0c576-125">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="0c576-126">EntrySelectedBy Element för EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="0c576-126">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)

[<span data-ttu-id="0c576-127">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="0c576-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
