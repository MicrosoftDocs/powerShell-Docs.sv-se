---
title: SelectionSetName-element för SelectionCondition för CustomControl för View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c7fdd92475ba24d27e61371d1c6b54fa1a55647c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787520"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="c32c0-102">SelectionSetName-element för SelectionCondition för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="c32c0-102">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="c32c0-103">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="c32c0-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="c32c0-104">När någon av typerna i den här uppsättningen finns, uppfylls villkoret och objektet visas med den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="c32c0-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="c32c0-105">Det här elementet används när du definierar en anpassad kontrol vy.</span><span class="sxs-lookup"><span data-stu-id="c32c0-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="c32c0-106">Konfigurations element (format) ViewDefinitions element (format) View element (format) CustomControl element (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) EntrySelectedBy-element för CustomEntry för View (format)</span><span class="sxs-lookup"><span data-stu-id="c32c0-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c32c0-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="c32c0-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c32c0-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="c32c0-108">Attributes and Elements</span></span>

<span data-ttu-id="c32c0-109">I följande avsnitt beskrivs attribut, underordnade element och `SelectionSetName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="c32c0-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c32c0-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="c32c0-110">Attributes</span></span>

<span data-ttu-id="c32c0-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="c32c0-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c32c0-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="c32c0-112">Child Elements</span></span>

<span data-ttu-id="c32c0-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="c32c0-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c32c0-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="c32c0-114">Parent Elements</span></span>

|<span data-ttu-id="c32c0-115">Element</span><span class="sxs-lookup"><span data-stu-id="c32c0-115">Element</span></span>|<span data-ttu-id="c32c0-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c32c0-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c32c0-117">SelectionCondition-element för EntrySelectedBy för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="c32c0-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="c32c0-118">Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="c32c0-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c32c0-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="c32c0-119">Text Value</span></span>

<span data-ttu-id="c32c0-120">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="c32c0-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="c32c0-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="c32c0-121">Remarks</span></span>

<span data-ttu-id="c32c0-122">Urvals uppsättningar är vanliga grupper av .NET-objekt som kan användas av alla vyer som format filen definierar.</span><span class="sxs-lookup"><span data-stu-id="c32c0-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="c32c0-123">Mer information om hur du skapar och refererar till urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="c32c0-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="c32c0-124">Urvals villkoret kan ange en urvals uppsättning eller en .NET-typ, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="c32c0-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="c32c0-125">Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="c32c0-125">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c32c0-126">Se även</span><span class="sxs-lookup"><span data-stu-id="c32c0-126">See Also</span></span>

[<span data-ttu-id="c32c0-127">SelectionCondition-element för EntrySelectedBy för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="c32c0-127">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="c32c0-128">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="c32c0-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="c32c0-129">Definiera valuppsättningar</span><span class="sxs-lookup"><span data-stu-id="c32c0-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="c32c0-130">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="c32c0-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
