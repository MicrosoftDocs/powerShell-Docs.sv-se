---
title: SelectionSetName-element för SelectionCondition for GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b9a4912-d755-42f3-8058-53c0797e28e4
caps.latest.revision: 6
ms.openlocfilehash: 371913eda2b09ff6788494b68738f2ad53ccb115
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353727"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="95ba7-102">SelectionSetName-element för SelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="95ba7-102">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="95ba7-103">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="95ba7-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="95ba7-104">När någon av typerna i den här uppsättningen finns, uppfylls villkoret och objektet visas med hjälp av den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="95ba7-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="95ba7-105">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="95ba7-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="95ba7-106">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element för CustomControl for GroupBy (format) EntrySelectedBy-element för CustomEntry för GroupBy (format) SelectionCondition-element för EntrySelectedBy för GroupBy (format) SelectionSetName-element för SelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="95ba7-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="95ba7-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="95ba7-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="95ba7-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="95ba7-108">Attributes and Elements</span></span>

<span data-ttu-id="95ba7-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `SelectionSetName`-elementet.</span><span class="sxs-lookup"><span data-stu-id="95ba7-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="95ba7-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="95ba7-110">Attributes</span></span>

<span data-ttu-id="95ba7-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="95ba7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="95ba7-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="95ba7-112">Child Elements</span></span>

<span data-ttu-id="95ba7-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="95ba7-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="95ba7-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="95ba7-114">Parent Elements</span></span>

|<span data-ttu-id="95ba7-115">Element</span><span class="sxs-lookup"><span data-stu-id="95ba7-115">Element</span></span>|<span data-ttu-id="95ba7-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="95ba7-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="95ba7-117">SelectionCondition-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="95ba7-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="95ba7-118">Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="95ba7-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="95ba7-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="95ba7-119">Text Value</span></span>

<span data-ttu-id="95ba7-120">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="95ba7-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="95ba7-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="95ba7-121">Remarks</span></span>

<span data-ttu-id="95ba7-122">Urvals uppsättningar är vanliga grupper av .NET-objekt som kan användas av alla vyer som format filen definierar.</span><span class="sxs-lookup"><span data-stu-id="95ba7-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="95ba7-123">Mer information om hur du skapar och refererar till urvals uppsättningar finns i [definiera urvals uppsättningar](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="95ba7-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="95ba7-124">När det här elementet har angetts kan du inte ange elementet [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="95ba7-124">When this element is specified, you cannot specify the [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) element.</span></span> <span data-ttu-id="95ba7-125">Mer information om hur du definierar urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="95ba7-125">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="95ba7-126">Se även</span><span class="sxs-lookup"><span data-stu-id="95ba7-126">See Also</span></span>

[<span data-ttu-id="95ba7-127">Elementet TypeName för SelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="95ba7-127">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="95ba7-128">SelectionCondition-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="95ba7-128">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="95ba7-129">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="95ba7-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="95ba7-130">Definiera urvals uppsättningar</span><span class="sxs-lookup"><span data-stu-id="95ba7-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="95ba7-131">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="95ba7-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
