---
title: EnumerableExpansion-element (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 81a8959c19502a2e56f4cfa48a1e480509d84b6e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774056"
---
# <a name="enumerableexpansion-element-format"></a><span data-ttu-id="6506e-102">EnumerableExpansion-element (format)</span><span class="sxs-lookup"><span data-stu-id="6506e-102">EnumerableExpansion Element (Format)</span></span>

<span data-ttu-id="6506e-103">Definierar hur vissa .NET Collection-objekt expanderas när de visas i en vy.</span><span class="sxs-lookup"><span data-stu-id="6506e-103">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="6506e-104">Konfigurations element (format) DefaultSettings-element (format) EnumerableExpansions-element (format) element för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="6506e-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6506e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6506e-105">Syntax</span></span>

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6506e-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="6506e-106">Attributes and Elements</span></span>

<span data-ttu-id="6506e-107">I följande avsnitt beskrivs attribut, underordnade element och `EnumerableExpansion` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="6506e-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansion` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6506e-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="6506e-108">Attributes</span></span>

<span data-ttu-id="6506e-109">Inga.</span><span class="sxs-lookup"><span data-stu-id="6506e-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6506e-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="6506e-110">Child Elements</span></span>

|<span data-ttu-id="6506e-111">Element</span><span class="sxs-lookup"><span data-stu-id="6506e-111">Element</span></span>|<span data-ttu-id="6506e-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6506e-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6506e-113">EntrySelectedBy-element för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="6506e-113">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="6506e-114">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="6506e-114">Optional element.</span></span><br /><br /> <span data-ttu-id="6506e-115">Definierar vilka .NET-samlings objekt som expanderas av den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="6506e-115">Defines which .NET collection objects are expanded by this definition.</span></span>|
|[<span data-ttu-id="6506e-116">Expand-element (format)</span><span class="sxs-lookup"><span data-stu-id="6506e-116">Expand Element (Format)</span></span>](./expand-element-format.md)|<span data-ttu-id="6506e-117">Anger hur Collection-objektet expanderas för den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="6506e-117">Specifies how the collection object is expanded for this definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6506e-118">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="6506e-118">Parent Elements</span></span>

|<span data-ttu-id="6506e-119">Element</span><span class="sxs-lookup"><span data-stu-id="6506e-119">Element</span></span>|<span data-ttu-id="6506e-120">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6506e-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6506e-121">EnumerableExpansions-element (format)</span><span class="sxs-lookup"><span data-stu-id="6506e-121">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="6506e-122">Definierar de olika sätt som .NET-samlings objekt expanderas när de visas i en vy.</span><span class="sxs-lookup"><span data-stu-id="6506e-122">Defines the different ways that .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6506e-123">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="6506e-123">Remarks</span></span>

<span data-ttu-id="6506e-124">Det här elementet används för att definiera hur samlings objekt och objekten i samlingen ska visas.</span><span class="sxs-lookup"><span data-stu-id="6506e-124">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="6506e-125">I det här fallet refererar ett samlings objekt till alla objekt som stöder  **system. Collections. ICollection** -gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="6506e-125">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="6506e-126">Standard beteendet är att endast visa egenskaperna för objekten i samlingen.</span><span class="sxs-lookup"><span data-stu-id="6506e-126">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="6506e-127">Se även</span><span class="sxs-lookup"><span data-stu-id="6506e-127">See Also</span></span>

[<span data-ttu-id="6506e-128">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="6506e-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
