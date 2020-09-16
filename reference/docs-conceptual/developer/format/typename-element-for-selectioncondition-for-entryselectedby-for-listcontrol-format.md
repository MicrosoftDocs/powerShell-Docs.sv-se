---
title: Elementet TypeName för SelectionCondition för EntrySelectedBy för ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: bc58d630e65b316f9223bf3c529f928358e38ebc
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787384"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="756d4-102">TypeName-element för SelectionCondition för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="756d4-102">TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="756d4-103">Anger en .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="756d4-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="756d4-104">När den här typen finns används List posten.</span><span class="sxs-lookup"><span data-stu-id="756d4-104">When this type is present, the list entry is used.</span></span>

<span data-ttu-id="756d4-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) ListEntries-element för ListControl (format) ListEntry-element för ListEntries för ListControl (format) EntrySelectedBy-element för ListEntry för ListControl (format) SelectionCondition-element för EntrySelectedBy (format) ListControl-element för SelectionCondition för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="756d4-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format) SelectionCondition Element for EntrySelectedBy for ListControl (Format) TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="756d4-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="756d4-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="756d4-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="756d4-107">Attributes and Elements</span></span>

<span data-ttu-id="756d4-108">I följande avsnitt beskrivs attribut, underordnade element och `TypeName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="756d4-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="756d4-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="756d4-109">Attributes</span></span>

<span data-ttu-id="756d4-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="756d4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="756d4-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="756d4-111">Child Elements</span></span>

<span data-ttu-id="756d4-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="756d4-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="756d4-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="756d4-113">Parent Elements</span></span>

|<span data-ttu-id="756d4-114">Element</span><span class="sxs-lookup"><span data-stu-id="756d4-114">Element</span></span>|<span data-ttu-id="756d4-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="756d4-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="756d4-116">SelectionCondition-element för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="756d4-116">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="756d4-117">Definierar det villkor som måste finnas för att den här List posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="756d4-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="756d4-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="756d4-118">Text Value</span></span>

<span data-ttu-id="756d4-119">Ange det fullständigt kvalificerade namnet för .NET-typen, t `System.IO.DirectoryInfo` . ex..</span><span class="sxs-lookup"><span data-stu-id="756d4-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="756d4-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="756d4-120">Remarks</span></span>

<span data-ttu-id="756d4-121">Urvals villkoret kan ange valfritt antal .NET-typer eller markerings uppsättningar, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="756d4-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="756d4-122">Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="756d4-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="756d4-123">Mer information om andra komponenter i en listvy finns i [skapa en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="756d4-123">For more information about other the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="756d4-124">Se även</span><span class="sxs-lookup"><span data-stu-id="756d4-124">See Also</span></span>

[<span data-ttu-id="756d4-125">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="756d4-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="756d4-126">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="756d4-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="756d4-127">SelectionCondition-element för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="756d4-127">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="756d4-128">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="756d4-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
