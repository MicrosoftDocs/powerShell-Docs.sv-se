---
ms.date: 09/13/2016
ms.topic: reference
title: TypeName-element för EntrySelectedBy för ListControl (format)
description: TypeName-element för EntrySelectedBy för ListControl (format)
ms.openlocfilehash: 6fc5a2385fde3140abbc984e3da6a4dda483b2a8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645661"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="ea214-103">TypeName-element för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="ea214-103">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="ea214-104">Anger en .NET-typ som använder den här posten i list visningen.</span><span class="sxs-lookup"><span data-stu-id="ea214-104">Specifies a .NET type that uses this entry of the list view.</span></span> <span data-ttu-id="ea214-105">Det finns ingen gräns för antalet typer som kan anges för en List post.</span><span class="sxs-lookup"><span data-stu-id="ea214-105">There is no limit to the number of types that can be specified for a list entry.</span></span>

<span data-ttu-id="ea214-106">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) ListEntries-element (format) ListEntry-element (format) EntrySelectedBy-element för ListEntry (format) elementet TypeName för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="ea214-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ea214-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="ea214-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ea214-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="ea214-108">Attributes and Elements</span></span>

<span data-ttu-id="ea214-109">I följande avsnitt beskrivs attribut, underordnade element och `TypeName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="ea214-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ea214-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="ea214-110">Attributes</span></span>

<span data-ttu-id="ea214-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="ea214-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ea214-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="ea214-112">Child Elements</span></span>

<span data-ttu-id="ea214-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="ea214-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ea214-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="ea214-114">Parent Elements</span></span>

|<span data-ttu-id="ea214-115">Element</span><span class="sxs-lookup"><span data-stu-id="ea214-115">Element</span></span>|<span data-ttu-id="ea214-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ea214-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ea214-117">EntrySelectedBy-element för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ea214-117">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="ea214-118">Definierar de .NET-typer som använder den här List posten eller det villkor som måste finnas för att den här posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="ea214-118">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ea214-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="ea214-119">Text Value</span></span>

<span data-ttu-id="ea214-120">Ange det fullständigt kvalificerade namnet för .NET-typen, t. ex `System.IO.DirectoryInfo` ..</span><span class="sxs-lookup"><span data-stu-id="ea214-120">Specify the fully-qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="ea214-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="ea214-121">Remarks</span></span>

<span data-ttu-id="ea214-122">Varje List post måste ha minst ett typ namn, en urvals uppsättning eller ett urvals villkor definierat.</span><span class="sxs-lookup"><span data-stu-id="ea214-122">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="ea214-123">Mer information om hur det här elementet används i en listvy finns i [listvyn](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="ea214-123">For more information about how this element is used in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="ea214-124">Exempel</span><span class="sxs-lookup"><span data-stu-id="ea214-124">Example</span></span>

<span data-ttu-id="ea214-125">I följande exempel visas hur du anger en markerings uppsättning för en post i en listvy.</span><span class="sxs-lookup"><span data-stu-id="ea214-125">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="ea214-126">Se även</span><span class="sxs-lookup"><span data-stu-id="ea214-126">See Also</span></span>

[<span data-ttu-id="ea214-127">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="ea214-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="ea214-128">EntrySelectedBy-element för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ea214-128">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="ea214-129">SelectionSetName-element för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ea214-129">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="ea214-130">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="ea214-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
