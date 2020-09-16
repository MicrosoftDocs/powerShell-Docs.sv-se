---
title: SelectionSetName-element för EntrySelectedBy för kontroll av konfiguration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 72072d8d13e6ca22afdb9bca2e0237d29ba0594f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787571"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="3c020-102">SelectionSetName-element för EntrySelectedBy för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="3c020-102">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="3c020-103">Anger en uppsättning av .NET-typer som använder den här definitionen av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="3c020-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="3c020-104">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="3c020-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="3c020-105">Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för Configuration (format) CustomEntry-element för CustomControl för Controls (format) EntrySelectedBy-element för CustomEntry för Controls (format) SelectionSetName-element för EntrySelectedBy för Controls (format)-element</span><span class="sxs-lookup"><span data-stu-id="3c020-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3c020-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="3c020-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="3c020-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="3c020-107">Attributes and Elements</span></span>

<span data-ttu-id="3c020-108">I följande avsnitt beskrivs attribut, underordnade element och `SelectionSetName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="3c020-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3c020-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="3c020-109">Attributes</span></span>

<span data-ttu-id="3c020-110">Inget</span><span class="sxs-lookup"><span data-stu-id="3c020-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="3c020-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="3c020-111">Child Elements</span></span>

<span data-ttu-id="3c020-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="3c020-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3c020-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="3c020-113">Parent Elements</span></span>

|<span data-ttu-id="3c020-114">Element</span><span class="sxs-lookup"><span data-stu-id="3c020-114">Element</span></span>|<span data-ttu-id="3c020-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3c020-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3c020-116">EntrySelectedBy-element för CustomEntry för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="3c020-116">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="3c020-117">Definierar de .NET-typer som använder den här kontroll definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="3c020-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3c020-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="3c020-118">Text Value</span></span>

<span data-ttu-id="3c020-119">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="3c020-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="3c020-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="3c020-120">Remarks</span></span>

<span data-ttu-id="3c020-121">Varje kontroll definition måste ha minst ett typ namn, en markerings uppsättning eller ett urvals villkor definierat.</span><span class="sxs-lookup"><span data-stu-id="3c020-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="3c020-122">Urvals uppsättningar används vanligt vis när du vill definiera en grupp objekt som används i flera vyer.</span><span class="sxs-lookup"><span data-stu-id="3c020-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="3c020-123">Mer information om hur du definierar urvals uppsättningar finns i [definiera urvals uppsättningar](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="3c020-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3c020-124">Se även</span><span class="sxs-lookup"><span data-stu-id="3c020-124">See Also</span></span>

[<span data-ttu-id="3c020-125">EntrySelectedBy-element för CustomEntry för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="3c020-125">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="3c020-126">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="3c020-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
