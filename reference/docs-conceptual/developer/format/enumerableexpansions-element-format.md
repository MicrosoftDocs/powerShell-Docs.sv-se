---
title: EnumerableExpansions-element (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2b536b1ab9b34b0089d0a38d3c5dc7a937176443
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774022"
---
# <a name="enumerableexpansions-element-format"></a><span data-ttu-id="5a456-102">EnumerableExpansions-element (format)</span><span class="sxs-lookup"><span data-stu-id="5a456-102">EnumerableExpansions Element (Format)</span></span>

<span data-ttu-id="5a456-103">Definierar hur .NET-samlings objekt expanderas när de visas i en vy.</span><span class="sxs-lookup"><span data-stu-id="5a456-103">Defines how .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="5a456-104">Konfigurations element (format) DefaultSettings-element (format) EnumerableExpansions-element (format)</span><span class="sxs-lookup"><span data-stu-id="5a456-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5a456-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5a456-105">Syntax</span></span>

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5a456-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="5a456-106">Attributes and Elements</span></span>

<span data-ttu-id="5a456-107">I följande avsnitt beskrivs attribut, underordnade element och `EnumerableExpansions` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="5a456-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansions` element.</span></span> <span data-ttu-id="5a456-108">Det finns ingen gräns för antalet underordnade element som du kan använda.</span><span class="sxs-lookup"><span data-stu-id="5a456-108">There is no limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="5a456-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="5a456-109">Attributes</span></span>

<span data-ttu-id="5a456-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="5a456-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5a456-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="5a456-111">Child Elements</span></span>

|<span data-ttu-id="5a456-112">Element</span><span class="sxs-lookup"><span data-stu-id="5a456-112">Element</span></span>|<span data-ttu-id="5a456-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5a456-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5a456-114">EnumerableExpansion-element (format)</span><span class="sxs-lookup"><span data-stu-id="5a456-114">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="5a456-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="5a456-115">Optional element.</span></span><br /><br /> <span data-ttu-id="5a456-116">Definierar de olika .NET-samlings objekt som expanderas när de visas i en vy.</span><span class="sxs-lookup"><span data-stu-id="5a456-116">Defines the specific .NET collection objects that are expanded when they are displayed in a view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5a456-117">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="5a456-117">Parent Elements</span></span>

|<span data-ttu-id="5a456-118">Element</span><span class="sxs-lookup"><span data-stu-id="5a456-118">Element</span></span>|<span data-ttu-id="5a456-119">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5a456-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5a456-120">DefaultSettings-element (format)</span><span class="sxs-lookup"><span data-stu-id="5a456-120">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="5a456-121">Definierar vanliga inställningar som gäller för alla vyer i formaterings filen.</span><span class="sxs-lookup"><span data-stu-id="5a456-121">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5a456-122">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="5a456-122">Remarks</span></span>

<span data-ttu-id="5a456-123">Det här elementet används för att definiera hur samlings objekt och objekten i samlingen ska visas.</span><span class="sxs-lookup"><span data-stu-id="5a456-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="5a456-124">I det här fallet refererar ett samlings objekt till alla objekt som stöder  **system. Collections. ICollection** -gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="5a456-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="5a456-125">Se även</span><span class="sxs-lookup"><span data-stu-id="5a456-125">See Also</span></span>

[<span data-ttu-id="5a456-126">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="5a456-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
