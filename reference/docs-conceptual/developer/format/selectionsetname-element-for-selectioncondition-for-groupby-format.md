---
title: SelectionSetName-element för SelectionCondition for GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6d0263aa335287f20be5b94a8eb65696d06d82a8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772628"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="f0bb2-102">SelectionSetName-element för SelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="f0bb2-102">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="f0bb2-103">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="f0bb2-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="f0bb2-104">När någon av typerna i den här uppsättningen finns, uppfylls villkoret och objektet visas med hjälp av den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="f0bb2-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="f0bb2-105">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="f0bb2-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="f0bb2-106">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element for CustomControl for groupby (format) EntrySelectedBy-element för CustomEntry (format) SelectionCondition element for EntrySelectedBy för groupby (format) SelectionSetName element for SelectionCondition</span><span class="sxs-lookup"><span data-stu-id="f0bb2-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f0bb2-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="f0bb2-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f0bb2-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="f0bb2-108">Attributes and Elements</span></span>

<span data-ttu-id="f0bb2-109">I följande avsnitt beskrivs attribut, underordnade element och `SelectionSetName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="f0bb2-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f0bb2-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="f0bb2-110">Attributes</span></span>

<span data-ttu-id="f0bb2-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="f0bb2-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f0bb2-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="f0bb2-112">Child Elements</span></span>

<span data-ttu-id="f0bb2-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="f0bb2-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f0bb2-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="f0bb2-114">Parent Elements</span></span>

|<span data-ttu-id="f0bb2-115">Element</span><span class="sxs-lookup"><span data-stu-id="f0bb2-115">Element</span></span>|<span data-ttu-id="f0bb2-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f0bb2-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f0bb2-117">SelectionCondition-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="f0bb2-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="f0bb2-118">Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="f0bb2-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f0bb2-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="f0bb2-119">Text Value</span></span>

<span data-ttu-id="f0bb2-120">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="f0bb2-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="f0bb2-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="f0bb2-121">Remarks</span></span>

<span data-ttu-id="f0bb2-122">Urvals uppsättningar är vanliga grupper av .NET-objekt som kan användas av alla vyer som format filen definierar.</span><span class="sxs-lookup"><span data-stu-id="f0bb2-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="f0bb2-123">Mer information om hur du skapar och refererar till urvals uppsättningar finns i [definiera urvals uppsättningar](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="f0bb2-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="f0bb2-124">När det här elementet har angetts kan du inte ange elementet [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="f0bb2-124">When this element is specified, you cannot specify the [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) element.</span></span> <span data-ttu-id="f0bb2-125">Mer information om hur du definierar urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f0bb2-125">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f0bb2-126">Se även</span><span class="sxs-lookup"><span data-stu-id="f0bb2-126">See Also</span></span>

[<span data-ttu-id="f0bb2-127">TypeName-element för SelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="f0bb2-127">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="f0bb2-128">SelectionCondition-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="f0bb2-128">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="f0bb2-129">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="f0bb2-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="f0bb2-130">Definiera valuppsättningar</span><span class="sxs-lookup"><span data-stu-id="f0bb2-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="f0bb2-131">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="f0bb2-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
