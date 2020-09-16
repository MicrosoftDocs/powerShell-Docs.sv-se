---
title: DefaultSettings-element (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7da7948fc0814e38a8f3910596e223470ec27d75
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787741"
---
# <a name="defaultsettings-element-format"></a><span data-ttu-id="d8471-102">DefaultSettings-element (format)</span><span class="sxs-lookup"><span data-stu-id="d8471-102">DefaultSettings Element (Format)</span></span>

<span data-ttu-id="d8471-103">Definierar vanliga inställningar som gäller för alla vyer i formaterings filen.</span><span class="sxs-lookup"><span data-stu-id="d8471-103">Defines common settings that apply to all the views of the formatting file.</span></span> <span data-ttu-id="d8471-104">Vanliga inställningar är att visa fel, figursätta text i tabeller, definiera hur samlingar expanderas och mycket mer.</span><span class="sxs-lookup"><span data-stu-id="d8471-104">Common settings include displaying errors, wrapping text in tables, defining how collections are expanded, and more.</span></span>

<span data-ttu-id="d8471-105">Konfigurations element (format) DefaultSettings-element (format)</span><span class="sxs-lookup"><span data-stu-id="d8471-105">Configuration Element (Format) DefaultSettings Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d8471-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="d8471-106">Syntax</span></span>

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d8471-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="d8471-107">Attributes and Elements</span></span>

<span data-ttu-id="d8471-108">I följande avsnitt beskrivs attribut, underordnade element och `DefaultSettings` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="d8471-108">The following sections describe attributes, child elements, and the parent element of the `DefaultSettings` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d8471-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="d8471-109">Attributes</span></span>

<span data-ttu-id="d8471-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="d8471-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d8471-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="d8471-111">Child Elements</span></span>

|<span data-ttu-id="d8471-112">Element</span><span class="sxs-lookup"><span data-stu-id="d8471-112">Element</span></span>|<span data-ttu-id="d8471-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d8471-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d8471-114">DisplayError-element (format)</span><span class="sxs-lookup"><span data-stu-id="d8471-114">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)|<span data-ttu-id="d8471-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="d8471-115">Optional element.</span></span><br /><br /> <span data-ttu-id="d8471-116">Anger att strängen #ERR visas när ett fel inträffar när en del av data visas.</span><span class="sxs-lookup"><span data-stu-id="d8471-116">Specifies that the string #ERR is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="d8471-117">EnumerableExpansions-element (format)</span><span class="sxs-lookup"><span data-stu-id="d8471-117">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="d8471-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="d8471-118">Optional element.</span></span><br /><br /> <span data-ttu-id="d8471-119">Definierar de olika sätt som .NET-objekt expanderas när de visas i en vy.</span><span class="sxs-lookup"><span data-stu-id="d8471-119">Defines the different ways that .NET objects are expanded when they are displayed in a view.</span></span>|
|[<span data-ttu-id="d8471-120">PropertyCountForTable (format)</span><span class="sxs-lookup"><span data-stu-id="d8471-120">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)|<span data-ttu-id="d8471-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="d8471-121">Optional element.</span></span><br /><br /> <span data-ttu-id="d8471-122">Anger det minsta antalet egenskaper som ett objekt måste ha för att visa objektet i en tabellvy.</span><span class="sxs-lookup"><span data-stu-id="d8471-122">Specifies the minimum number of properties that an object must have to display the object in a table view.</span></span>|
|[<span data-ttu-id="d8471-123">ShowError-element (format)</span><span class="sxs-lookup"><span data-stu-id="d8471-123">ShowError Element (Format)</span></span>](./showerror-element-format.md)|<span data-ttu-id="d8471-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="d8471-124">Optional element.</span></span><br /><br /> <span data-ttu-id="d8471-125">Anger att den fullständiga fel posten visas när ett fel inträffar när en del av data visas.</span><span class="sxs-lookup"><span data-stu-id="d8471-125">Specifies that the full error record is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="d8471-126">WrapTables-element (format)</span><span class="sxs-lookup"><span data-stu-id="d8471-126">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)|<span data-ttu-id="d8471-127">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="d8471-127">Optional element.</span></span><br /><br /> <span data-ttu-id="d8471-128">Anger att data i en tabell flyttas till nästa rad om den inte passar in i kolumnens bredd.</span><span class="sxs-lookup"><span data-stu-id="d8471-128">Specifies that data in a table is moved to the next line if it does not fit into the width of the column.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d8471-129">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="d8471-129">Parent Elements</span></span>

|<span data-ttu-id="d8471-130">Element</span><span class="sxs-lookup"><span data-stu-id="d8471-130">Element</span></span>|<span data-ttu-id="d8471-131">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d8471-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d8471-132">Konfigurations element</span><span class="sxs-lookup"><span data-stu-id="d8471-132">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="d8471-133">Representerar det översta elementet i en textfil.</span><span class="sxs-lookup"><span data-stu-id="d8471-133">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d8471-134">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="d8471-134">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="d8471-135">Se även</span><span class="sxs-lookup"><span data-stu-id="d8471-135">See Also</span></span>

[<span data-ttu-id="d8471-136">Konfigurations element</span><span class="sxs-lookup"><span data-stu-id="d8471-136">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="d8471-137">DisplayError-element (format)</span><span class="sxs-lookup"><span data-stu-id="d8471-137">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)

[<span data-ttu-id="d8471-138">EnumerableExpansions-element (format)</span><span class="sxs-lookup"><span data-stu-id="d8471-138">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)

[<span data-ttu-id="d8471-139">PropertyCountForTable (format)</span><span class="sxs-lookup"><span data-stu-id="d8471-139">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)

[<span data-ttu-id="d8471-140">ShowError-element (format)</span><span class="sxs-lookup"><span data-stu-id="d8471-140">ShowError Element (Format)</span></span>](./showerror-element-format.md)

[<span data-ttu-id="d8471-141">WrapTables-element (format)</span><span class="sxs-lookup"><span data-stu-id="d8471-141">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)

[<span data-ttu-id="d8471-142">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="d8471-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
