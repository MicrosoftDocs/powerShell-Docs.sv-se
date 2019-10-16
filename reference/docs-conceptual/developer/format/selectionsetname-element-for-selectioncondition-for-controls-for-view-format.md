---
title: SelectionSetName-element för SelectionCondition för kontroller för vy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: daea8c6f-873a-4639-9eee-599642822958
caps.latest.revision: 6
ms.openlocfilehash: 697f2ea284393ebddd77a862c408f27f3d332900
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353804"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="c4d6c-102">SelectionSetName-element för SelectionCondition för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="c4d6c-102">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="c4d6c-103">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="c4d6c-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="c4d6c-104">När någon av typerna i den här uppsättningen finns, uppfylls villkoret och objektet visas med den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="c4d6c-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="c4d6c-105">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="c4d6c-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="c4d6c-106">Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) styr element för Controls (format) CustomControl-element för kontroll för Control for View (format) CustomEntries-element för CustomControl for Controls for View (format) CustomEntry-elementet för CustomEntries for Controls for View (format) EntrySelectedBy-elementet for CustomEntry for Controls for View (format) SelectionCondition element for EntrySelectedBy for Controls for View ( Format) SelectionSetName-element för SelectionCondition för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="c4d6c-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c4d6c-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="c4d6c-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c4d6c-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="c4d6c-108">Attributes and Elements</span></span>

<span data-ttu-id="c4d6c-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="c4d6c-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c4d6c-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="c4d6c-110">Attributes</span></span>

<span data-ttu-id="c4d6c-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="c4d6c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c4d6c-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="c4d6c-112">Child Elements</span></span>

<span data-ttu-id="c4d6c-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="c4d6c-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c4d6c-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="c4d6c-114">Parent Elements</span></span>

|<span data-ttu-id="c4d6c-115">Element</span><span class="sxs-lookup"><span data-stu-id="c4d6c-115">Element</span></span>|<span data-ttu-id="c4d6c-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c4d6c-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c4d6c-117">SelectionCondition-element för EntrySelectedBy för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="c4d6c-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="c4d6c-118">Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="c4d6c-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c4d6c-119">Text värde</span><span class="sxs-lookup"><span data-stu-id="c4d6c-119">Text Value</span></span>

<span data-ttu-id="c4d6c-120">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="c4d6c-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="c4d6c-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="c4d6c-121">Remarks</span></span>

<span data-ttu-id="c4d6c-122">Urvals uppsättningar är vanliga grupper av .NET-objekt som kan användas av alla vyer som format filen definierar.</span><span class="sxs-lookup"><span data-stu-id="c4d6c-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="c4d6c-123">Mer information om hur du skapar och refererar till urvals uppsättningar finns i [definiera urvals uppsättningar](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="c4d6c-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="c4d6c-124">Urvals villkoret kan ange en urvals uppsättning eller en .NET-typ, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="c4d6c-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="c4d6c-125">Mer information om hur du använder urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="c4d6c-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c4d6c-126">Se även</span><span class="sxs-lookup"><span data-stu-id="c4d6c-126">See Also</span></span>

[<span data-ttu-id="c4d6c-127">SelectionCondition-element för EntrySelectedBy för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="c4d6c-127">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="c4d6c-128">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="c4d6c-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="c4d6c-129">Definiera urvals uppsättningar</span><span class="sxs-lookup"><span data-stu-id="c4d6c-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="c4d6c-130">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="c4d6c-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
