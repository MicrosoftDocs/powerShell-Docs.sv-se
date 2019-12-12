---
title: EnumerableExpansion-element (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358973"
---
# <a name="enumerableexpansion-element-format"></a><span data-ttu-id="bdd41-102">EnumerableExpansion-element (format)</span><span class="sxs-lookup"><span data-stu-id="bdd41-102">EnumerableExpansion Element (Format)</span></span>

<span data-ttu-id="bdd41-103">Definierar hur vissa .NET Collection-objekt expanderas när de visas i en vy.</span><span class="sxs-lookup"><span data-stu-id="bdd41-103">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="bdd41-104">Konfigurations element (format) DefaultSettings-element (format) EnumerableExpansions-element (format) element för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="bdd41-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bdd41-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="bdd41-105">Syntax</span></span>

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bdd41-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="bdd41-106">Attributes and Elements</span></span>

<span data-ttu-id="bdd41-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `EnumerableExpansion`-elementet.</span><span class="sxs-lookup"><span data-stu-id="bdd41-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansion` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bdd41-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="bdd41-108">Attributes</span></span>

<span data-ttu-id="bdd41-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="bdd41-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bdd41-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="bdd41-110">Child Elements</span></span>

|<span data-ttu-id="bdd41-111">Element</span><span class="sxs-lookup"><span data-stu-id="bdd41-111">Element</span></span>|<span data-ttu-id="bdd41-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="bdd41-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bdd41-113">EntrySelectedBy-element för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="bdd41-113">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="bdd41-114">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="bdd41-114">Optional element.</span></span><br /><br /> <span data-ttu-id="bdd41-115">Definierar vilka .NET-samlings objekt som expanderas av den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="bdd41-115">Defines which .NET collection objects are expanded by this definition.</span></span>|
|[<span data-ttu-id="bdd41-116">Expandera element (format)</span><span class="sxs-lookup"><span data-stu-id="bdd41-116">Expand Element (Format)</span></span>](./expand-element-format.md)|<span data-ttu-id="bdd41-117">Anger hur Collection-objektet expanderas för den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="bdd41-117">Specifies how the collection object is expanded for this definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bdd41-118">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="bdd41-118">Parent Elements</span></span>

|<span data-ttu-id="bdd41-119">Element</span><span class="sxs-lookup"><span data-stu-id="bdd41-119">Element</span></span>|<span data-ttu-id="bdd41-120">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="bdd41-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bdd41-121">EnumerableExpansions-element (format)</span><span class="sxs-lookup"><span data-stu-id="bdd41-121">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="bdd41-122">Definierar de olika sätt som .NET-samlings objekt expanderas när de visas i en vy.</span><span class="sxs-lookup"><span data-stu-id="bdd41-122">Defines the different ways that .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bdd41-123">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="bdd41-123">Remarks</span></span>

<span data-ttu-id="bdd41-124">Det här elementet används för att definiera hur samlings objekt och objekten i samlingen ska visas.</span><span class="sxs-lookup"><span data-stu-id="bdd41-124">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="bdd41-125">I det här fallet refererar ett samlings objekt till alla objekt som stöder **system. Collections. ICollection** -gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="bdd41-125">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="bdd41-126">Standard beteendet är att endast visa egenskaperna för objekten i samlingen.</span><span class="sxs-lookup"><span data-stu-id="bdd41-126">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="bdd41-127">Se även</span><span class="sxs-lookup"><span data-stu-id="bdd41-127">See Also</span></span>

[<span data-ttu-id="bdd41-128">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="bdd41-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
