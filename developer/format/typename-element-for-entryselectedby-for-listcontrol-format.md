---
title: TypeName-Element för EntrySelectedBy för ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33c7345c-b808-4c1e-bd54-cb870b407432
caps.latest.revision: 14
ms.openlocfilehash: 3f0c0ba1fe85d70557e67a30b3a9a59a33043475
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846888"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="f14ec-102">TypeName-element för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="f14ec-102">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="f14ec-103">Anger ett .NET-typ som använder den här posten i listvyn.</span><span class="sxs-lookup"><span data-stu-id="f14ec-103">Specifies a .NET type that uses this entry of the list view.</span></span> <span data-ttu-id="f14ec-104">Det finns ingen gräns för hur många typer som kan anges för en listpost.</span><span class="sxs-lookup"><span data-stu-id="f14ec-104">There is no limit to the number of types that can be specified for a list entry.</span></span>

<span data-ttu-id="f14ec-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy konfigurationselement för ListEntry (Format) TypeName-elementet för EntrySelectedBy för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="f14ec-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f14ec-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f14ec-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f14ec-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="f14ec-107">Attributes and Elements</span></span>

<span data-ttu-id="f14ec-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `TypeName` element.</span><span class="sxs-lookup"><span data-stu-id="f14ec-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f14ec-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="f14ec-109">Attributes</span></span>

<span data-ttu-id="f14ec-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="f14ec-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f14ec-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="f14ec-111">Child Elements</span></span>

<span data-ttu-id="f14ec-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="f14ec-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f14ec-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="f14ec-113">Parent Elements</span></span>

|<span data-ttu-id="f14ec-114">Element</span><span class="sxs-lookup"><span data-stu-id="f14ec-114">Element</span></span>|<span data-ttu-id="f14ec-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f14ec-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f14ec-116">EntrySelectedBy Element för ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="f14ec-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="f14ec-117">Definierar vilka typer av .NET som använder den här posten eller villkor som måste finnas för den här posten som ska användas.</span><span class="sxs-lookup"><span data-stu-id="f14ec-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f14ec-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="f14ec-118">Text Value</span></span>

<span data-ttu-id="f14ec-119">Ange det fullständigt kvalificerade namnet på .NET-typ som `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="f14ec-119">Specify the fully-qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="f14ec-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="f14ec-120">Remarks</span></span>

<span data-ttu-id="f14ec-121">Varje listpost måste ha minst ett namn, val av set eller Urvalsvillkoret som definierats.</span><span class="sxs-lookup"><span data-stu-id="f14ec-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="f14ec-122">Läs mer om hur det här elementet används i en listvy [listvyn](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="f14ec-122">For more information about how this element is used in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f14ec-123">Exempel</span><span class="sxs-lookup"><span data-stu-id="f14ec-123">Example</span></span>

<span data-ttu-id="f14ec-124">I följande exempel visas hur du anger ett urval som angetts för en post av en listvy.</span><span class="sxs-lookup"><span data-stu-id="f14ec-124">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="f14ec-125">Se även</span><span class="sxs-lookup"><span data-stu-id="f14ec-125">See Also</span></span>

[<span data-ttu-id="f14ec-126">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="f14ec-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="f14ec-127">EntrySelectedBy Element för ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="f14ec-127">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="f14ec-128">SelectionSetName Element för EnrtySelectedBy för ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="f14ec-128">SelectionSetName Element for EnrtySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="f14ec-129">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="f14ec-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
