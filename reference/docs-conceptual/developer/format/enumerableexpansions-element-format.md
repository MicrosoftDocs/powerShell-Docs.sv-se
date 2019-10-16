---
title: EnumerableExpansions-element (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50c33892-2ade-44c2-906c-81e5f5ca21f2
caps.latest.revision: 9
ms.openlocfilehash: 1ecbda8a3b623757517019105e3b1ee46ccbb55c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354735"
---
# <a name="enumerableexpansions-element-format"></a><span data-ttu-id="45eb8-102">EnumerableExpansions-element (format)</span><span class="sxs-lookup"><span data-stu-id="45eb8-102">EnumerableExpansions Element (Format)</span></span>

<span data-ttu-id="45eb8-103">Definierar hur .NET-samlings objekt expanderas när de visas i en vy.</span><span class="sxs-lookup"><span data-stu-id="45eb8-103">Defines how .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="45eb8-104">Konfigurations element (format) DefaultSettings-element (format) EnumerableExpansions-element (format)</span><span class="sxs-lookup"><span data-stu-id="45eb8-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="45eb8-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="45eb8-105">Syntax</span></span>

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="45eb8-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="45eb8-106">Attributes and Elements</span></span>

<span data-ttu-id="45eb8-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `EnumerableExpansions`.</span><span class="sxs-lookup"><span data-stu-id="45eb8-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansions` element.</span></span> <span data-ttu-id="45eb8-108">Det finns ingen gräns för antalet underordnade element som du kan använda.</span><span class="sxs-lookup"><span data-stu-id="45eb8-108">There is no limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="45eb8-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="45eb8-109">Attributes</span></span>

<span data-ttu-id="45eb8-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="45eb8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="45eb8-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="45eb8-111">Child Elements</span></span>

|<span data-ttu-id="45eb8-112">Element</span><span class="sxs-lookup"><span data-stu-id="45eb8-112">Element</span></span>|<span data-ttu-id="45eb8-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="45eb8-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="45eb8-114">EnumerableExpansion-element (format)</span><span class="sxs-lookup"><span data-stu-id="45eb8-114">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="45eb8-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="45eb8-115">Optional element.</span></span><br /><br /> <span data-ttu-id="45eb8-116">Definierar de olika .NET-samlings objekt som expanderas när de visas i en vy.</span><span class="sxs-lookup"><span data-stu-id="45eb8-116">Defines the specific .NET collection objects that are expanded when they are displayed in a view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="45eb8-117">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="45eb8-117">Parent Elements</span></span>

|<span data-ttu-id="45eb8-118">Element</span><span class="sxs-lookup"><span data-stu-id="45eb8-118">Element</span></span>|<span data-ttu-id="45eb8-119">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="45eb8-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="45eb8-120">DefaultSettings-element (format)</span><span class="sxs-lookup"><span data-stu-id="45eb8-120">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="45eb8-121">Definierar vanliga inställningar som gäller för alla vyer i formaterings filen.</span><span class="sxs-lookup"><span data-stu-id="45eb8-121">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="45eb8-122">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="45eb8-122">Remarks</span></span>

<span data-ttu-id="45eb8-123">Det här elementet används för att definiera hur samlings objekt och objekten i samlingen ska visas.</span><span class="sxs-lookup"><span data-stu-id="45eb8-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="45eb8-124">I det här fallet refererar ett samlings objekt till alla objekt som stöder **system. Collections. ICollection** -gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="45eb8-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="45eb8-125">Se även</span><span class="sxs-lookup"><span data-stu-id="45eb8-125">See Also</span></span>

[<span data-ttu-id="45eb8-126">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="45eb8-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
