---
ms.date: 09/13/2016
ms.topic: reference
title: TypeName-element för SelectionCondition för GroupBy (format)
description: TypeName-element för SelectionCondition för GroupBy (format)
ms.openlocfilehash: 096d2355e113a7e44cc6ae31ea23efc3f01080a0
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664626"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="85418-103">TypeName-element för SelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="85418-103">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="85418-104">Anger en .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="85418-104">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="85418-105">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="85418-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="85418-106">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element for CustomControl for groupby (format) EntrySelectedBy-element för CustomEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="85418-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="85418-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="85418-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="85418-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="85418-108">Attributes and Elements</span></span>

<span data-ttu-id="85418-109">I följande avsnitt beskrivs attribut, underordnade element och `TypeName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="85418-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="85418-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="85418-110">Attributes</span></span>

<span data-ttu-id="85418-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="85418-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="85418-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="85418-112">Child Elements</span></span>

<span data-ttu-id="85418-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="85418-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="85418-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="85418-114">Parent Elements</span></span>

|<span data-ttu-id="85418-115">Element</span><span class="sxs-lookup"><span data-stu-id="85418-115">Element</span></span>|<span data-ttu-id="85418-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="85418-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="85418-117">SelectionCondition-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="85418-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="85418-118">Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="85418-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="85418-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="85418-119">Text Value</span></span>

<span data-ttu-id="85418-120">Ange det fullständigt kvalificerade namnet för .NET-typen, t `System.IO.DirectoryInfo` . ex..</span><span class="sxs-lookup"><span data-stu-id="85418-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="85418-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="85418-121">Remarks</span></span>

<span data-ttu-id="85418-122">När det här elementet har angetts kan du inte ange `SelectionSetName` elementet.</span><span class="sxs-lookup"><span data-stu-id="85418-122">When this element is specified, you cannot specify the `SelectionSetName` element.</span></span> <span data-ttu-id="85418-123">Mer information om hur du definierar urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="85418-123">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="85418-124">Se även</span><span class="sxs-lookup"><span data-stu-id="85418-124">See Also</span></span>

[<span data-ttu-id="85418-125">SelectionCondition-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="85418-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="85418-126">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="85418-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
