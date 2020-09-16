---
title: Expandera element (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: deee832254bb8a774ee2c1f5bd451d3ced1bd47a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783661"
---
# <a name="expand-element-format"></a><span data-ttu-id="6abdc-102">Expand-element (format)</span><span class="sxs-lookup"><span data-stu-id="6abdc-102">Expand Element (Format)</span></span>

<span data-ttu-id="6abdc-103">Anger hur Collection-objektet expanderas för den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="6abdc-103">Specifies how the collection object is expanded for this definition.</span></span>

<span data-ttu-id="6abdc-104">Konfigurations element (format) DefaultSettings-element (format) EnumerableExpansions-element (format) EnumerableExpansion-element (format) Expand-element (format)</span><span class="sxs-lookup"><span data-stu-id="6abdc-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) Expand Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6abdc-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6abdc-105">Syntax</span></span>

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6abdc-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="6abdc-106">Attributes and Elements</span></span>

<span data-ttu-id="6abdc-107">I följande avsnitt beskrivs attribut, underordnade element och `Expand` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="6abdc-107">The following sections describe attributes, child elements, and the parent element of the `Expand` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6abdc-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="6abdc-108">Attributes</span></span>

<span data-ttu-id="6abdc-109">Inga.</span><span class="sxs-lookup"><span data-stu-id="6abdc-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6abdc-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="6abdc-110">Child Elements</span></span>

<span data-ttu-id="6abdc-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="6abdc-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6abdc-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="6abdc-112">Parent Elements</span></span>

|<span data-ttu-id="6abdc-113">Element</span><span class="sxs-lookup"><span data-stu-id="6abdc-113">Element</span></span>|<span data-ttu-id="6abdc-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6abdc-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6abdc-115">EnumerableExpansion-element (format)</span><span class="sxs-lookup"><span data-stu-id="6abdc-115">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="6abdc-116">Definierar hur vissa .NET Collection-objekt expanderas när de visas i en vy.</span><span class="sxs-lookup"><span data-stu-id="6abdc-116">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6abdc-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="6abdc-117">Text Value</span></span>

<span data-ttu-id="6abdc-118">Ange ett av följande värden:</span><span class="sxs-lookup"><span data-stu-id="6abdc-118">Specify one of the following values:</span></span>

- <span data-ttu-id="6abdc-119">EnumOnly: visar endast egenskaperna för objekten i samlingen.</span><span class="sxs-lookup"><span data-stu-id="6abdc-119">EnumOnly: Displays only the properties of the objects in the collection.</span></span>

- <span data-ttu-id="6abdc-120">CoreOnly: visar endast egenskaperna för objektet samling.</span><span class="sxs-lookup"><span data-stu-id="6abdc-120">CoreOnly: Displays only the properties of the collection object.</span></span>

- <span data-ttu-id="6abdc-121">Båda: visar egenskaperna för objekten i samlingen och egenskaperna för objektet samling.</span><span class="sxs-lookup"><span data-stu-id="6abdc-121">Both: Displays the properties of the objects in the collection and the properties of the collection object.</span></span>

## <a name="remarks"></a><span data-ttu-id="6abdc-122">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="6abdc-122">Remarks</span></span>

<span data-ttu-id="6abdc-123">Det här elementet används för att definiera hur samlings objekt och objekten i samlingen ska visas.</span><span class="sxs-lookup"><span data-stu-id="6abdc-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="6abdc-124">I det här fallet refererar ett samlings objekt till alla objekt som stöder  **system. Collections. ICollection** -gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="6abdc-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="6abdc-125">Standard beteendet är att endast visa egenskaperna för objekten i samlingen.</span><span class="sxs-lookup"><span data-stu-id="6abdc-125">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="6abdc-126">Se även</span><span class="sxs-lookup"><span data-stu-id="6abdc-126">See Also</span></span>

[<span data-ttu-id="6abdc-127">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="6abdc-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
