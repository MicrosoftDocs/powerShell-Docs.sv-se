---
title: Expandera element (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: faa0314b-f6f1-44fd-ad2b-b00cbe38923f
caps.latest.revision: 9
ms.openlocfilehash: 8b924c989133b47e4d95d8429778003c76595d58
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358970"
---
# <a name="expand-element-format"></a><span data-ttu-id="fe3b6-102">Expand-element (format)</span><span class="sxs-lookup"><span data-stu-id="fe3b6-102">Expand Element (Format)</span></span>

<span data-ttu-id="fe3b6-103">Anger hur Collection-objektet expanderas för den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="fe3b6-103">Specifies how the collection object is expanded for this definition.</span></span>

<span data-ttu-id="fe3b6-104">Konfigurations element (format) DefaultSettings-element (format) EnumerableExpansions-element (format) EnumerableExpansion-element (format) Expand-element (format)</span><span class="sxs-lookup"><span data-stu-id="fe3b6-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) Expand Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fe3b6-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="fe3b6-105">Syntax</span></span>

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fe3b6-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="fe3b6-106">Attributes and Elements</span></span>

<span data-ttu-id="fe3b6-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `Expand`.</span><span class="sxs-lookup"><span data-stu-id="fe3b6-107">The following sections describe attributes, child elements, and the parent element of the `Expand` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fe3b6-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="fe3b6-108">Attributes</span></span>

<span data-ttu-id="fe3b6-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="fe3b6-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fe3b6-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="fe3b6-110">Child Elements</span></span>

<span data-ttu-id="fe3b6-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="fe3b6-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fe3b6-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="fe3b6-112">Parent Elements</span></span>

|<span data-ttu-id="fe3b6-113">Element</span><span class="sxs-lookup"><span data-stu-id="fe3b6-113">Element</span></span>|<span data-ttu-id="fe3b6-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="fe3b6-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fe3b6-115">EnumerableExpansion-element (format)</span><span class="sxs-lookup"><span data-stu-id="fe3b6-115">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="fe3b6-116">Definierar hur vissa .NET Collection-objekt expanderas när de visas i en vy.</span><span class="sxs-lookup"><span data-stu-id="fe3b6-116">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fe3b6-117">Text värde</span><span class="sxs-lookup"><span data-stu-id="fe3b6-117">Text Value</span></span>

<span data-ttu-id="fe3b6-118">Ange ett av följande värden:</span><span class="sxs-lookup"><span data-stu-id="fe3b6-118">Specify one of the following values:</span></span>

- <span data-ttu-id="fe3b6-119">EnumOnly: visar endast egenskaperna för objekten i samlingen.</span><span class="sxs-lookup"><span data-stu-id="fe3b6-119">EnumOnly: Displays only the properties of the objects in the collection.</span></span>

- <span data-ttu-id="fe3b6-120">CoreOnly: visar endast egenskaperna för objektet samling.</span><span class="sxs-lookup"><span data-stu-id="fe3b6-120">CoreOnly: Displays only the properties of the collection object.</span></span>

- <span data-ttu-id="fe3b6-121">Båda: visar egenskaperna för objekten i samlingen och egenskaperna för objektet samling.</span><span class="sxs-lookup"><span data-stu-id="fe3b6-121">Both: Displays the properties of the objects in the collection and the properties of the collection object.</span></span>

## <a name="remarks"></a><span data-ttu-id="fe3b6-122">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="fe3b6-122">Remarks</span></span>

<span data-ttu-id="fe3b6-123">Det här elementet används för att definiera hur samlings objekt och objekten i samlingen ska visas.</span><span class="sxs-lookup"><span data-stu-id="fe3b6-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="fe3b6-124">I det här fallet refererar ett samlings objekt till alla objekt som stöder **system. Collections. ICollection** -gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="fe3b6-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="fe3b6-125">Standard beteendet är att endast visa egenskaperna för objekten i samlingen.</span><span class="sxs-lookup"><span data-stu-id="fe3b6-125">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="fe3b6-126">Se även</span><span class="sxs-lookup"><span data-stu-id="fe3b6-126">See Also</span></span>

[<span data-ttu-id="fe3b6-127">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="fe3b6-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
