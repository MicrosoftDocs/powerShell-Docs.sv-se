---
title: EnumerableExpansions Element (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50c33892-2ade-44c2-906c-81e5f5ca21f2
caps.latest.revision: 9
ms.openlocfilehash: 1ecbda8a3b623757517019105e3b1ee46ccbb55c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066098"
---
# <a name="enumerableexpansions-element-format"></a><span data-ttu-id="8965e-102">EnumerableExpansions-element (format)</span><span class="sxs-lookup"><span data-stu-id="8965e-102">EnumerableExpansions Element (Format)</span></span>

<span data-ttu-id="8965e-103">Definierar hur .NET samling objekt visas när de visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="8965e-103">Defines how .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="8965e-104">Elementet (Format) DefaultSettings Element (Format) EnumerableExpansions konfigurationselement (Format)</span><span class="sxs-lookup"><span data-stu-id="8965e-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8965e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="8965e-105">Syntax</span></span>

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8965e-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="8965e-106">Attributes and Elements</span></span>

<span data-ttu-id="8965e-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `EnumerableExpansions` element.</span><span class="sxs-lookup"><span data-stu-id="8965e-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansions` element.</span></span> <span data-ttu-id="8965e-108">Det finns ingen gräns för antalet underordnade element som du kan använda.</span><span class="sxs-lookup"><span data-stu-id="8965e-108">There is no limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="8965e-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="8965e-109">Attributes</span></span>

<span data-ttu-id="8965e-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="8965e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8965e-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="8965e-111">Child Elements</span></span>

|<span data-ttu-id="8965e-112">Element</span><span class="sxs-lookup"><span data-stu-id="8965e-112">Element</span></span>|<span data-ttu-id="8965e-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8965e-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8965e-114">EnumerableExpansion Element (Format)</span><span class="sxs-lookup"><span data-stu-id="8965e-114">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="8965e-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="8965e-115">Optional element.</span></span><br /><br /> <span data-ttu-id="8965e-116">Definierar de specifika .NET samling objekt som visas när de visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="8965e-116">Defines the specific .NET collection objects that are expanded when they are displayed in a view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8965e-117">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="8965e-117">Parent Elements</span></span>

|<span data-ttu-id="8965e-118">Element</span><span class="sxs-lookup"><span data-stu-id="8965e-118">Element</span></span>|<span data-ttu-id="8965e-119">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8965e-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8965e-120">DefaultSettings Element (Format)</span><span class="sxs-lookup"><span data-stu-id="8965e-120">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="8965e-121">Definierar gemensamma inställningar som gäller för alla vyer i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="8965e-121">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8965e-122">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="8965e-122">Remarks</span></span>

<span data-ttu-id="8965e-123">Det här elementet används för att definiera hur samlingen och objekt i samlingen visas.</span><span class="sxs-lookup"><span data-stu-id="8965e-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="8965e-124">I det här fallet en samling objekt refererar till ett objekt som stöder den **System.Collections.ICollection** gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="8965e-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="8965e-125">Se även</span><span class="sxs-lookup"><span data-stu-id="8965e-125">See Also</span></span>

[<span data-ttu-id="8965e-126">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="8965e-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
