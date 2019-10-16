---
title: SelectionSetName-element för EntrySelectedBy för kontroll av konfiguration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42143d1e-7cda-4c4a-b568-fa1951bb9417
caps.latest.revision: 6
ms.openlocfilehash: 9060ee54d6f88c7f910b16cf5c9b87f37844b736
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355778"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="530a8-102">SelectionSetName-element för EntrySelectedBy för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="530a8-102">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="530a8-103">Anger en uppsättning av .NET-typer som använder den här definitionen av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="530a8-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="530a8-104">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="530a8-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="530a8-105">Konfigurations element (format) styr element i konfigurations-(format) kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för konfiguration ( Format) CustomEntry-element för CustomControl for Controls for Configuration (format) EntrySelectedBy element for CustomEntry for Controls for Configuration (format) SelectionSetName element for EntrySelectedBy for Controls (format)</span><span class="sxs-lookup"><span data-stu-id="530a8-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="530a8-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="530a8-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="530a8-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="530a8-107">Attributes and Elements</span></span>

<span data-ttu-id="530a8-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="530a8-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="530a8-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="530a8-109">Attributes</span></span>

<span data-ttu-id="530a8-110">Inga</span><span class="sxs-lookup"><span data-stu-id="530a8-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="530a8-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="530a8-111">Child Elements</span></span>

<span data-ttu-id="530a8-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="530a8-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="530a8-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="530a8-113">Parent Elements</span></span>

|<span data-ttu-id="530a8-114">Element</span><span class="sxs-lookup"><span data-stu-id="530a8-114">Element</span></span>|<span data-ttu-id="530a8-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="530a8-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="530a8-116">EntrySelectedBy-element för CustomEntry för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="530a8-116">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="530a8-117">Definierar de .NET-typer som använder den här kontroll definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="530a8-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="530a8-118">Text värde</span><span class="sxs-lookup"><span data-stu-id="530a8-118">Text Value</span></span>

<span data-ttu-id="530a8-119">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="530a8-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="530a8-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="530a8-120">Remarks</span></span>

<span data-ttu-id="530a8-121">Varje kontroll definition måste ha minst ett typ namn, en markerings uppsättning eller ett urvals villkor definierat.</span><span class="sxs-lookup"><span data-stu-id="530a8-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="530a8-122">Urvals uppsättningar används vanligt vis när du vill definiera en grupp objekt som används i flera vyer.</span><span class="sxs-lookup"><span data-stu-id="530a8-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="530a8-123">Mer information om hur du definierar urvals uppsättningar finns i [definiera urvals uppsättningar](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="530a8-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="530a8-124">Se även</span><span class="sxs-lookup"><span data-stu-id="530a8-124">See Also</span></span>

[<span data-ttu-id="530a8-125">EntrySelectedBy-element för CustomEntry för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="530a8-125">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="530a8-126">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="530a8-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
