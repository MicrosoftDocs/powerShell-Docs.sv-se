---
title: Elementet TypeName för EntrySelectedBy för ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5e7b73db5aa597d96141454008c5c58b1827df24
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780227"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="327fb-102">TypeName-element för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="327fb-102">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="327fb-103">Anger en .NET-typ som använder den här posten i list visningen.</span><span class="sxs-lookup"><span data-stu-id="327fb-103">Specifies a .NET type that uses this entry of the list view.</span></span> <span data-ttu-id="327fb-104">Det finns ingen gräns för antalet typer som kan anges för en List post.</span><span class="sxs-lookup"><span data-stu-id="327fb-104">There is no limit to the number of types that can be specified for a list entry.</span></span>

<span data-ttu-id="327fb-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) ListEntries-element (format) ListEntry-element (format) EntrySelectedBy-element för ListEntry (format) elementet TypeName för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="327fb-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="327fb-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="327fb-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="327fb-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="327fb-107">Attributes and Elements</span></span>

<span data-ttu-id="327fb-108">I följande avsnitt beskrivs attribut, underordnade element och `TypeName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="327fb-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="327fb-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="327fb-109">Attributes</span></span>

<span data-ttu-id="327fb-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="327fb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="327fb-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="327fb-111">Child Elements</span></span>

<span data-ttu-id="327fb-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="327fb-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="327fb-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="327fb-113">Parent Elements</span></span>

|<span data-ttu-id="327fb-114">Element</span><span class="sxs-lookup"><span data-stu-id="327fb-114">Element</span></span>|<span data-ttu-id="327fb-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="327fb-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="327fb-116">EntrySelectedBy-element för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="327fb-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="327fb-117">Definierar de .NET-typer som använder den här List posten eller det villkor som måste finnas för att den här posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="327fb-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="327fb-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="327fb-118">Text Value</span></span>

<span data-ttu-id="327fb-119">Ange det fullständigt kvalificerade namnet för .NET-typen, t. ex `System.IO.DirectoryInfo` ..</span><span class="sxs-lookup"><span data-stu-id="327fb-119">Specify the fully-qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="327fb-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="327fb-120">Remarks</span></span>

<span data-ttu-id="327fb-121">Varje List post måste ha minst ett typ namn, en urvals uppsättning eller ett urvals villkor definierat.</span><span class="sxs-lookup"><span data-stu-id="327fb-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="327fb-122">Mer information om hur det här elementet används i en listvy finns i [listvyn](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="327fb-122">For more information about how this element is used in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="327fb-123">Exempel</span><span class="sxs-lookup"><span data-stu-id="327fb-123">Example</span></span>

<span data-ttu-id="327fb-124">I följande exempel visas hur du anger en markerings uppsättning för en post i en listvy.</span><span class="sxs-lookup"><span data-stu-id="327fb-124">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="327fb-125">Se även</span><span class="sxs-lookup"><span data-stu-id="327fb-125">See Also</span></span>

[<span data-ttu-id="327fb-126">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="327fb-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="327fb-127">EntrySelectedBy-element för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="327fb-127">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="327fb-128">SelectionSetName-element för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="327fb-128">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="327fb-129">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="327fb-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
