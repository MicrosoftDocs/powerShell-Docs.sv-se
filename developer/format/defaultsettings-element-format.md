---
title: DefaultSettings Element (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: bc95c62222eb2806f92499257a397c2e4ec5dbab
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059073"
---
# <a name="defaultsettings-element-format"></a><span data-ttu-id="3c202-102">DefaultSettings-element (format)</span><span class="sxs-lookup"><span data-stu-id="3c202-102">DefaultSettings Element (Format)</span></span>

<span data-ttu-id="3c202-103">Definierar gemensamma inställningar som gäller för alla vyer i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="3c202-103">Defines common settings that apply to all the views of the formatting file.</span></span> <span data-ttu-id="3c202-104">Vanliga inställningar inkluderar visar fel, radbrytning i tabeller, definiera hur samlingar har expanderats och mycket annat.</span><span class="sxs-lookup"><span data-stu-id="3c202-104">Common settings include displaying errors, wrapping text in tables, defining how collections are expanded, and more.</span></span>

<span data-ttu-id="3c202-105">Konfigurationselementet Element (Format) DefaultSettings (Format)</span><span class="sxs-lookup"><span data-stu-id="3c202-105">Configuration Element (Format) DefaultSettings Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3c202-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="3c202-106">Syntax</span></span>

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3c202-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="3c202-107">Attributes and Elements</span></span>

<span data-ttu-id="3c202-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `DefaultSettings` element.</span><span class="sxs-lookup"><span data-stu-id="3c202-108">The following sections describe attributes, child elements, and the parent element of the `DefaultSettings` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3c202-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="3c202-109">Attributes</span></span>

<span data-ttu-id="3c202-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="3c202-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3c202-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="3c202-111">Child Elements</span></span>

|<span data-ttu-id="3c202-112">Element</span><span class="sxs-lookup"><span data-stu-id="3c202-112">Element</span></span>|<span data-ttu-id="3c202-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3c202-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3c202-114">DisplayError Element (Format)</span><span class="sxs-lookup"><span data-stu-id="3c202-114">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)|<span data-ttu-id="3c202-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="3c202-115">Optional element.</span></span><br /><br /> <span data-ttu-id="3c202-116">Anger att strängen #ERR visas när ett fel uppstår medan du visar en typ av data.</span><span class="sxs-lookup"><span data-stu-id="3c202-116">Specifies that the string #ERR is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="3c202-117">EnumerableExpansions Element (Format)</span><span class="sxs-lookup"><span data-stu-id="3c202-117">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="3c202-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="3c202-118">Optional element.</span></span><br /><br /> <span data-ttu-id="3c202-119">Definierar hur .NET objekt visas när de visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="3c202-119">Defines the different ways that .NET objects are expanded when they are displayed in a view.</span></span>|
|[<span data-ttu-id="3c202-120">PropertyCountForTable (Format)</span><span class="sxs-lookup"><span data-stu-id="3c202-120">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)|<span data-ttu-id="3c202-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="3c202-121">Optional element.</span></span><br /><br /> <span data-ttu-id="3c202-122">Anger det minsta antalet egenskaper som ett objekt måste ha för att visa objektet i en tabellvy.</span><span class="sxs-lookup"><span data-stu-id="3c202-122">Specifies the minimum number of properties that an object must have to display the object in a table view.</span></span>|
|[<span data-ttu-id="3c202-123">ShowError-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="3c202-123">ShowError Element (Format)</span></span>](./showerror-element-format.md)|<span data-ttu-id="3c202-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="3c202-124">Optional element.</span></span><br /><br /> <span data-ttu-id="3c202-125">Anger att en fullständig Felpost visas när ett fel uppstår medan du visar en typ av data.</span><span class="sxs-lookup"><span data-stu-id="3c202-125">Specifies that the full error record is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="3c202-126">WrapTables Element (Format)</span><span class="sxs-lookup"><span data-stu-id="3c202-126">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)|<span data-ttu-id="3c202-127">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="3c202-127">Optional element.</span></span><br /><br /> <span data-ttu-id="3c202-128">Anger att data i en tabell har flyttats till nästa rad om det inte passar i bredden på kolumnen.</span><span class="sxs-lookup"><span data-stu-id="3c202-128">Specifies that data in a table is moved to the next line if it does not fit into the width of the column.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3c202-129">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="3c202-129">Parent Elements</span></span>

|<span data-ttu-id="3c202-130">Element</span><span class="sxs-lookup"><span data-stu-id="3c202-130">Element</span></span>|<span data-ttu-id="3c202-131">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3c202-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3c202-132">Konfigurationselement</span><span class="sxs-lookup"><span data-stu-id="3c202-132">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="3c202-133">Representerar det översta elementet i en formatering fil.</span><span class="sxs-lookup"><span data-stu-id="3c202-133">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3c202-134">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="3c202-134">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="3c202-135">Se även</span><span class="sxs-lookup"><span data-stu-id="3c202-135">See Also</span></span>

[<span data-ttu-id="3c202-136">Konfigurationselement</span><span class="sxs-lookup"><span data-stu-id="3c202-136">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="3c202-137">DisplayError Element (Format)</span><span class="sxs-lookup"><span data-stu-id="3c202-137">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)

[<span data-ttu-id="3c202-138">EnumerableExpansions Element (Format)</span><span class="sxs-lookup"><span data-stu-id="3c202-138">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)

[<span data-ttu-id="3c202-139">PropertyCountForTable (Format)</span><span class="sxs-lookup"><span data-stu-id="3c202-139">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)

[<span data-ttu-id="3c202-140">ShowError-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="3c202-140">ShowError Element (Format)</span></span>](./showerror-element-format.md)

[<span data-ttu-id="3c202-141">WrapTables Element (Format)</span><span class="sxs-lookup"><span data-stu-id="3c202-141">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)

[<span data-ttu-id="3c202-142">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="3c202-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
