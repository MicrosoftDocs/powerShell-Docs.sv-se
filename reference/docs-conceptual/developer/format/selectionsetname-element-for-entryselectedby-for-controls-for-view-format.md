---
title: SelectionSetName-element för EntrySelectedBy för kontroller för vy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5c762a626fff746266919d1f7fcb991a8cdbcdf2
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787554"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="959e8-102">SelectionSetName-element för EntrySelectedBy för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="959e8-102">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="959e8-103">Anger en uppsättning av .NET-typer som använder den här definitionen av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="959e8-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="959e8-104">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="959e8-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="959e8-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) styr element för Controls (format) CustomControl-element för kontroll för Control for View (format) CustomEntries-element för CustomControl for Controls for View (format) CustomEntry-elementet för CustomEntries for Controls for View (format) EntrySelectedBy-elementet for CustomEntry for Controls for View (format) SelectionSetName element for EntrySelectedBy for Controls for View (format)</span><span class="sxs-lookup"><span data-stu-id="959e8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="959e8-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="959e8-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="959e8-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="959e8-107">Attributes and Elements</span></span>

<span data-ttu-id="959e8-108">I följande avsnitt beskrivs attribut, underordnade element och `SelectionSetName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="959e8-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="959e8-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="959e8-109">Attributes</span></span>

<span data-ttu-id="959e8-110">Inget</span><span class="sxs-lookup"><span data-stu-id="959e8-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="959e8-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="959e8-111">Child Elements</span></span>

<span data-ttu-id="959e8-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="959e8-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="959e8-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="959e8-113">Parent Elements</span></span>

|<span data-ttu-id="959e8-114">Element</span><span class="sxs-lookup"><span data-stu-id="959e8-114">Element</span></span>|<span data-ttu-id="959e8-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="959e8-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="959e8-116">EntrySelectedBy-element för CustomEntry för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="959e8-116">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="959e8-117">Definierar de .NET-typer som använder den här kontroll definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="959e8-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="959e8-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="959e8-118">Text Value</span></span>

<span data-ttu-id="959e8-119">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="959e8-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="959e8-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="959e8-120">Remarks</span></span>

<span data-ttu-id="959e8-121">Varje kontroll definition måste ha minst ett typ namn, en markerings uppsättning eller ett urvals villkor definierat.</span><span class="sxs-lookup"><span data-stu-id="959e8-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="959e8-122">Urvals uppsättningar används vanligt vis när du vill definiera en grupp objekt som används i flera vyer.</span><span class="sxs-lookup"><span data-stu-id="959e8-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="959e8-123">Mer information om hur du definierar urvals uppsättningar finns i [definiera urvals uppsättningar](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="959e8-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="959e8-124">Se även</span><span class="sxs-lookup"><span data-stu-id="959e8-124">See Also</span></span>

[<span data-ttu-id="959e8-125">EntrySelectedBy-element för CustomEntry för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="959e8-125">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="959e8-126">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="959e8-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
