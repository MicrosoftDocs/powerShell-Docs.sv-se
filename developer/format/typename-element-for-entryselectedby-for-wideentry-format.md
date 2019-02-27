---
title: TypeName-Element för EntrySelectedBy för WideEntry (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81a91c74-6229-4b64-aa2b-9123e8b7e9e5
caps.latest.revision: 11
ms.openlocfilehash: be35f6e9e2ad0b2d9a21a91c053aa0f70cafaf9c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851466"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="11c6d-102">TypeName-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="11c6d-102">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="11c6d-103">Anger en .NET-typ för definitionen.</span><span class="sxs-lookup"><span data-stu-id="11c6d-103">Specifies a .NET type for the definition.</span></span> <span data-ttu-id="11c6d-104">Definitionen används när det här objektet visas.</span><span class="sxs-lookup"><span data-stu-id="11c6d-104">The definition is used whenever this object is displayed.</span></span>

<span data-ttu-id="11c6d-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy konfigurationselement för WideEntry (Format) TypeName-elementet för WideEntry ( Format)</span><span class="sxs-lookup"><span data-stu-id="11c6d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) TypeName Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="11c6d-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="11c6d-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="11c6d-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="11c6d-107">Attributes and Elements</span></span>

<span data-ttu-id="11c6d-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `TypeName` element.</span><span class="sxs-lookup"><span data-stu-id="11c6d-108">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="11c6d-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="11c6d-109">Attributes</span></span>

<span data-ttu-id="11c6d-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="11c6d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="11c6d-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="11c6d-111">Child Elements</span></span>

<span data-ttu-id="11c6d-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="11c6d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="11c6d-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="11c6d-113">Parent Elements</span></span>

|<span data-ttu-id="11c6d-114">Element</span><span class="sxs-lookup"><span data-stu-id="11c6d-114">Element</span></span>|<span data-ttu-id="11c6d-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="11c6d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="11c6d-116">EntrySelectedBy Element för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="11c6d-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="11c6d-117">Definierar vilka typer av .NET som använder den här wide posten eller villkor som måste finnas för den här posten som ska användas.</span><span class="sxs-lookup"><span data-stu-id="11c6d-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="11c6d-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="11c6d-118">Text Value</span></span>

<span data-ttu-id="11c6d-119">Ange det fullständigt kvalificerade namnet för .NET-typ, till exempel `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="11c6d-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="11c6d-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="11c6d-120">Remarks</span></span>

<span data-ttu-id="11c6d-121">Varje post i wide måste ange en eller flera typer i .NET eller en Urvalsvillkoret som måste finnas för definitionen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="11c6d-121">Each wide entry must specify one or more .NET types, a selection set, or the selection condition that must exist for the definition to be used.</span></span>

<span data-ttu-id="11c6d-122">Mer information om andra komponenter för en bred vy finns i [skapar en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="11c6d-122">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="11c6d-123">Se även</span><span class="sxs-lookup"><span data-stu-id="11c6d-123">See Also</span></span>

[<span data-ttu-id="11c6d-124">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="11c6d-124">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="11c6d-125">EntrySelectedBy Element för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="11c6d-125">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="11c6d-126">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="11c6d-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
