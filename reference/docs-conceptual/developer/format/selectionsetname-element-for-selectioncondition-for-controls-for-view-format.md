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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353804"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="b5e2b-102">SelectionSetName-element för SelectionCondition för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="b5e2b-102">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="b5e2b-103">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="b5e2b-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="b5e2b-104">När någon av typerna i den här uppsättningen finns, uppfylls villkoret och objektet visas med den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="b5e2b-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="b5e2b-105">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="b5e2b-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="b5e2b-106">Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) styr element för Controls (format) CustomControl-element för kontroll för Control for View (format) CustomEntries-element för CustomControl for Controls for View (format) CustomEntry-elementet för CustomEntries for Controls for View (format) EntrySelectedBy-elementet for CustomEntry for Controls for View (format) SelectionCondition element for EntrySelectedBy for Controls for View ( Format) SelectionSetName-element för SelectionCondition för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="b5e2b-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b5e2b-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="b5e2b-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b5e2b-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="b5e2b-108">Attributes and Elements</span></span>

<span data-ttu-id="b5e2b-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `SelectionSetName`-elementet.</span><span class="sxs-lookup"><span data-stu-id="b5e2b-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b5e2b-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="b5e2b-110">Attributes</span></span>

<span data-ttu-id="b5e2b-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="b5e2b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b5e2b-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="b5e2b-112">Child Elements</span></span>

<span data-ttu-id="b5e2b-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="b5e2b-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b5e2b-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="b5e2b-114">Parent Elements</span></span>

|<span data-ttu-id="b5e2b-115">Element</span><span class="sxs-lookup"><span data-stu-id="b5e2b-115">Element</span></span>|<span data-ttu-id="b5e2b-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b5e2b-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b5e2b-117">SelectionCondition-element för EntrySelectedBy för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="b5e2b-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="b5e2b-118">Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="b5e2b-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b5e2b-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="b5e2b-119">Text Value</span></span>

<span data-ttu-id="b5e2b-120">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="b5e2b-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="b5e2b-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="b5e2b-121">Remarks</span></span>

<span data-ttu-id="b5e2b-122">Urvals uppsättningar är vanliga grupper av .NET-objekt som kan användas av alla vyer som format filen definierar.</span><span class="sxs-lookup"><span data-stu-id="b5e2b-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="b5e2b-123">Mer information om hur du skapar och refererar till urvals uppsättningar finns i [definiera urvals uppsättningar](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="b5e2b-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="b5e2b-124">Urvals villkoret kan ange en urvals uppsättning eller en .NET-typ, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="b5e2b-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="b5e2b-125">Mer information om hur du använder urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="b5e2b-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b5e2b-126">Se även</span><span class="sxs-lookup"><span data-stu-id="b5e2b-126">See Also</span></span>

[<span data-ttu-id="b5e2b-127">SelectionCondition-element för EntrySelectedBy för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="b5e2b-127">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="b5e2b-128">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="b5e2b-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="b5e2b-129">Definiera urvals uppsättningar</span><span class="sxs-lookup"><span data-stu-id="b5e2b-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="b5e2b-130">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="b5e2b-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
