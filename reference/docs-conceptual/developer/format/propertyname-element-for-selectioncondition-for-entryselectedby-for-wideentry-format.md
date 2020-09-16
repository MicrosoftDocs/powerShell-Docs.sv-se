---
title: PropertyName-element för SelectionCondition för EntrySelectedBy för WideEntry (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ca2106dbbd8da345e71e83a3ead3cf7a1cb44cb4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773121"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="de90b-102">PropertyName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="de90b-102">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="de90b-103">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="de90b-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="de90b-104">När den här egenskapen finns eller när den utvärderas `true` , uppfylls villkoret och definitionen används.</span><span class="sxs-lookup"><span data-stu-id="de90b-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="de90b-105">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) WideControl-element (format) WideEntries-element (format) WideEntry-element (format) EntrySelectedBy-element för WideEntry (format) SelectionCondition element for EntrySelectedBy för WideEntry (format) PropertyName-element för SelectionCondition för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="de90b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="de90b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="de90b-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

```

## <a name="attributes-and-elements"></a><span data-ttu-id="de90b-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="de90b-107">Attributes and Elements</span></span>

<span data-ttu-id="de90b-108">I följande avsnitt beskrivs attribut, underordnade element och `PropertyName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="de90b-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="de90b-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="de90b-109">Attributes</span></span>

<span data-ttu-id="de90b-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="de90b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="de90b-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="de90b-111">Child Elements</span></span>

<span data-ttu-id="de90b-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="de90b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="de90b-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="de90b-113">Parent Elements</span></span>

|<span data-ttu-id="de90b-114">Element</span><span class="sxs-lookup"><span data-stu-id="de90b-114">Element</span></span>|<span data-ttu-id="de90b-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="de90b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="de90b-116">SelectionCondition-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="de90b-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="de90b-117">Definierar det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="de90b-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="de90b-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="de90b-118">Text Value</span></span>

<span data-ttu-id="de90b-119">Ange .NET-egenskaps namnet.</span><span class="sxs-lookup"><span data-stu-id="de90b-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="de90b-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="de90b-120">Remarks</span></span>

<span data-ttu-id="de90b-121">Urvals villkoret måste innehålla minst ett egenskaps namn eller ett skript som ska utvärderas, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="de90b-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="de90b-122">Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="de90b-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="de90b-123">Mer information om andra komponenter i en bred vy finns i [wide View](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="de90b-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="de90b-124">Se även</span><span class="sxs-lookup"><span data-stu-id="de90b-124">See Also</span></span>

[<span data-ttu-id="de90b-125">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="de90b-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="de90b-126">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="de90b-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="de90b-127">Script block-element för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="de90b-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="de90b-128">SelectionCondition-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="de90b-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="de90b-129">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="de90b-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
