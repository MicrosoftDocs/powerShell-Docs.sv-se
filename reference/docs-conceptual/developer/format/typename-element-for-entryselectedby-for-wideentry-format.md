---
ms.date: 09/13/2016
ms.topic: reference
title: TypeName-element för EntrySelectedBy för WideEntry (format)
description: TypeName-element för EntrySelectedBy för WideEntry (format)
ms.openlocfilehash: 2e0facd6ff7c6fec96dabf488449a8502429bcff
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654784"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="ea635-103">TypeName-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ea635-103">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="ea635-104">Anger en .NET-typ för definitionen.</span><span class="sxs-lookup"><span data-stu-id="ea635-104">Specifies a .NET type for the definition.</span></span> <span data-ttu-id="ea635-105">Definitionen används när det här objektet visas.</span><span class="sxs-lookup"><span data-stu-id="ea635-105">The definition is used whenever this object is displayed.</span></span>

<span data-ttu-id="ea635-106">Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) WideEntries-element (format) WideEntry element (format) EntrySelectedBy-element för WideEntry (format) element för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ea635-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) TypeName Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ea635-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="ea635-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ea635-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="ea635-108">Attributes and Elements</span></span>

<span data-ttu-id="ea635-109">I följande avsnitt beskrivs attributen, underordnade element och `TypeName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="ea635-109">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ea635-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="ea635-110">Attributes</span></span>

<span data-ttu-id="ea635-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="ea635-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ea635-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="ea635-112">Child Elements</span></span>

<span data-ttu-id="ea635-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="ea635-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ea635-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="ea635-114">Parent Elements</span></span>

|<span data-ttu-id="ea635-115">Element</span><span class="sxs-lookup"><span data-stu-id="ea635-115">Element</span></span>|<span data-ttu-id="ea635-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ea635-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ea635-117">EntrySelectedBy-element för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ea635-117">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="ea635-118">Definierar de .NET-typer som använder den här breda posten eller det villkor som måste finnas för att den här posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="ea635-118">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ea635-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="ea635-119">Text Value</span></span>

<span data-ttu-id="ea635-120">Ange det fullständigt kvalificerade namnet för .NET-typen, t `System.IO.DirectoryInfo` . ex..</span><span class="sxs-lookup"><span data-stu-id="ea635-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="ea635-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="ea635-121">Remarks</span></span>

<span data-ttu-id="ea635-122">Varje bred post måste innehålla en eller flera .NET-typer, en urvals uppsättning eller ett urvals villkor som måste finnas för att definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="ea635-122">Each wide entry must specify one or more .NET types, a selection set, or the selection condition that must exist for the definition to be used.</span></span>

<span data-ttu-id="ea635-123">Mer information om andra komponenter i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="ea635-123">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ea635-124">Se även</span><span class="sxs-lookup"><span data-stu-id="ea635-124">See Also</span></span>

[<span data-ttu-id="ea635-125">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="ea635-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="ea635-126">EntrySelectedBy-element för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ea635-126">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="ea635-127">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="ea635-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
