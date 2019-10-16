---
title: DefaultSettings-element (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: bc95c62222eb2806f92499257a397c2e4ec5dbab
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355134"
---
# <a name="defaultsettings-element-format"></a><span data-ttu-id="928c1-102">DefaultSettings-element (format)</span><span class="sxs-lookup"><span data-stu-id="928c1-102">DefaultSettings Element (Format)</span></span>

<span data-ttu-id="928c1-103">Definierar vanliga inställningar som gäller för alla vyer i formaterings filen.</span><span class="sxs-lookup"><span data-stu-id="928c1-103">Defines common settings that apply to all the views of the formatting file.</span></span> <span data-ttu-id="928c1-104">Vanliga inställningar är att visa fel, figursätta text i tabeller, definiera hur samlingar expanderas och mycket mer.</span><span class="sxs-lookup"><span data-stu-id="928c1-104">Common settings include displaying errors, wrapping text in tables, defining how collections are expanded, and more.</span></span>

<span data-ttu-id="928c1-105">Konfigurations element (format) DefaultSettings-element (format)</span><span class="sxs-lookup"><span data-stu-id="928c1-105">Configuration Element (Format) DefaultSettings Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="928c1-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="928c1-106">Syntax</span></span>

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="928c1-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="928c1-107">Attributes and Elements</span></span>

<span data-ttu-id="928c1-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `DefaultSettings`.</span><span class="sxs-lookup"><span data-stu-id="928c1-108">The following sections describe attributes, child elements, and the parent element of the `DefaultSettings` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="928c1-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="928c1-109">Attributes</span></span>

<span data-ttu-id="928c1-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="928c1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="928c1-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="928c1-111">Child Elements</span></span>

|<span data-ttu-id="928c1-112">Element</span><span class="sxs-lookup"><span data-stu-id="928c1-112">Element</span></span>|<span data-ttu-id="928c1-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="928c1-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="928c1-114">DisplayError-element (format)</span><span class="sxs-lookup"><span data-stu-id="928c1-114">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)|<span data-ttu-id="928c1-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="928c1-115">Optional element.</span></span><br /><br /> <span data-ttu-id="928c1-116">Anger att strängen #ERR visas när ett fel inträffar när en del av data visas.</span><span class="sxs-lookup"><span data-stu-id="928c1-116">Specifies that the string #ERR is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="928c1-117">EnumerableExpansions-element (format)</span><span class="sxs-lookup"><span data-stu-id="928c1-117">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="928c1-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="928c1-118">Optional element.</span></span><br /><br /> <span data-ttu-id="928c1-119">Definierar de olika sätt som .NET-objekt expanderas när de visas i en vy.</span><span class="sxs-lookup"><span data-stu-id="928c1-119">Defines the different ways that .NET objects are expanded when they are displayed in a view.</span></span>|
|[<span data-ttu-id="928c1-120">PropertyCountForTable (format)</span><span class="sxs-lookup"><span data-stu-id="928c1-120">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)|<span data-ttu-id="928c1-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="928c1-121">Optional element.</span></span><br /><br /> <span data-ttu-id="928c1-122">Anger det minsta antalet egenskaper som ett objekt måste ha för att visa objektet i en tabellvy.</span><span class="sxs-lookup"><span data-stu-id="928c1-122">Specifies the minimum number of properties that an object must have to display the object in a table view.</span></span>|
|[<span data-ttu-id="928c1-123">ShowError-element (format)</span><span class="sxs-lookup"><span data-stu-id="928c1-123">ShowError Element (Format)</span></span>](./showerror-element-format.md)|<span data-ttu-id="928c1-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="928c1-124">Optional element.</span></span><br /><br /> <span data-ttu-id="928c1-125">Anger att den fullständiga fel posten visas när ett fel inträffar när en del av data visas.</span><span class="sxs-lookup"><span data-stu-id="928c1-125">Specifies that the full error record is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="928c1-126">WrapTables-element (format)</span><span class="sxs-lookup"><span data-stu-id="928c1-126">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)|<span data-ttu-id="928c1-127">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="928c1-127">Optional element.</span></span><br /><br /> <span data-ttu-id="928c1-128">Anger att data i en tabell flyttas till nästa rad om den inte passar in i kolumnens bredd.</span><span class="sxs-lookup"><span data-stu-id="928c1-128">Specifies that data in a table is moved to the next line if it does not fit into the width of the column.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="928c1-129">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="928c1-129">Parent Elements</span></span>

|<span data-ttu-id="928c1-130">Element</span><span class="sxs-lookup"><span data-stu-id="928c1-130">Element</span></span>|<span data-ttu-id="928c1-131">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="928c1-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="928c1-132">Konfigurations element</span><span class="sxs-lookup"><span data-stu-id="928c1-132">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="928c1-133">Representerar det översta elementet i en textfil.</span><span class="sxs-lookup"><span data-stu-id="928c1-133">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="928c1-134">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="928c1-134">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="928c1-135">Se även</span><span class="sxs-lookup"><span data-stu-id="928c1-135">See Also</span></span>

[<span data-ttu-id="928c1-136">Konfigurations element</span><span class="sxs-lookup"><span data-stu-id="928c1-136">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="928c1-137">DisplayError-element (format)</span><span class="sxs-lookup"><span data-stu-id="928c1-137">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)

[<span data-ttu-id="928c1-138">EnumerableExpansions-element (format)</span><span class="sxs-lookup"><span data-stu-id="928c1-138">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)

[<span data-ttu-id="928c1-139">PropertyCountForTable (format)</span><span class="sxs-lookup"><span data-stu-id="928c1-139">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)

[<span data-ttu-id="928c1-140">ShowError-element (format)</span><span class="sxs-lookup"><span data-stu-id="928c1-140">ShowError Element (Format)</span></span>](./showerror-element-format.md)

[<span data-ttu-id="928c1-141">WrapTables-element (format)</span><span class="sxs-lookup"><span data-stu-id="928c1-141">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)

[<span data-ttu-id="928c1-142">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="928c1-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
