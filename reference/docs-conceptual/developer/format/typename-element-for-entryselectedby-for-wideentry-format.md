---
title: Elementet TypeName för EntrySelectedBy för WideEntry (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81a91c74-6229-4b64-aa2b-9123e8b7e9e5
caps.latest.revision: 11
ms.openlocfilehash: be35f6e9e2ad0b2d9a21a91c053aa0f70cafaf9c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353559"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="6afb8-102">TypeName-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="6afb8-102">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="6afb8-103">Anger en .NET-typ för definitionen.</span><span class="sxs-lookup"><span data-stu-id="6afb8-103">Specifies a .NET type for the definition.</span></span> <span data-ttu-id="6afb8-104">Definitionen används när det här objektet visas.</span><span class="sxs-lookup"><span data-stu-id="6afb8-104">The definition is used whenever this object is displayed.</span></span>

<span data-ttu-id="6afb8-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) WideEntries-element (format) WideEntry-element (format) EntrySelectedBy-element för WideEntry (format) elementet TypeName för WideEntry ( Formatering</span><span class="sxs-lookup"><span data-stu-id="6afb8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) TypeName Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6afb8-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="6afb8-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6afb8-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="6afb8-107">Attributes and Elements</span></span>

<span data-ttu-id="6afb8-108">I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet för elementet `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="6afb8-108">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6afb8-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="6afb8-109">Attributes</span></span>

<span data-ttu-id="6afb8-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="6afb8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6afb8-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="6afb8-111">Child Elements</span></span>

<span data-ttu-id="6afb8-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="6afb8-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6afb8-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="6afb8-113">Parent Elements</span></span>

|<span data-ttu-id="6afb8-114">Element</span><span class="sxs-lookup"><span data-stu-id="6afb8-114">Element</span></span>|<span data-ttu-id="6afb8-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6afb8-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6afb8-116">EntrySelectedBy-element för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="6afb8-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="6afb8-117">Definierar de .NET-typer som använder den här breda posten eller det villkor som måste finnas för att den här posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="6afb8-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6afb8-118">Text värde</span><span class="sxs-lookup"><span data-stu-id="6afb8-118">Text Value</span></span>

<span data-ttu-id="6afb8-119">Ange det fullständigt kvalificerade namnet för .NET-typen, t. ex. `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="6afb8-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="6afb8-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="6afb8-120">Remarks</span></span>

<span data-ttu-id="6afb8-121">Varje bred post måste innehålla en eller flera .NET-typer, en urvals uppsättning eller ett urvals villkor som måste finnas för att definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="6afb8-121">Each wide entry must specify one or more .NET types, a selection set, or the selection condition that must exist for the definition to be used.</span></span>

<span data-ttu-id="6afb8-122">Mer information om andra komponenter i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="6afb8-122">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6afb8-123">Se även</span><span class="sxs-lookup"><span data-stu-id="6afb8-123">See Also</span></span>

[<span data-ttu-id="6afb8-124">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="6afb8-124">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="6afb8-125">EntrySelectedBy-element för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="6afb8-125">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="6afb8-126">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="6afb8-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
