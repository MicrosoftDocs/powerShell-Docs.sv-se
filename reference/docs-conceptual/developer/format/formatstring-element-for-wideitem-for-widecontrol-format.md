---
ms.date: 09/13/2016
ms.topic: reference
title: FormatString-element för WideItem för WideControl (format)
description: FormatString-element för WideItem för WideControl (format)
ms.openlocfilehash: f67a18e3ec4f1323e7f9be8904db518c679d53e5
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667886"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="4e695-103">FormatString-element för WideItem för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="4e695-103">FormatString Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="4e695-104">Anger ett format mönster som definierar hur egenskapen eller skriptets värde visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="4e695-104">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

<span data-ttu-id="4e695-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) WideEntries-element (format) WideEntry-element för WideControl (format) WideItem-element för WideControl (format) FormatString-element för WideItem för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="4e695-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element for WideControl (Format) WideItem Element for WideControl (Format) FormatString Element for WideItem for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4e695-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="4e695-106">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4e695-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="4e695-107">Attributes and Elements</span></span>

<span data-ttu-id="4e695-108">I följande avsnitt beskrivs attributen, underordnade element och `FormatString` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="4e695-108">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4e695-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="4e695-109">Attributes</span></span>

<span data-ttu-id="4e695-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="4e695-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4e695-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="4e695-111">Child Elements</span></span>

<span data-ttu-id="4e695-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="4e695-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4e695-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="4e695-113">Parent Elements</span></span>

|<span data-ttu-id="4e695-114">Element</span><span class="sxs-lookup"><span data-stu-id="4e695-114">Element</span></span>|<span data-ttu-id="4e695-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4e695-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4e695-116">WideItem-element för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="4e695-116">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="4e695-117">Definierar egenskapen eller skriptet vars värde visas i en rad i list visningen.</span><span class="sxs-lookup"><span data-stu-id="4e695-117">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4e695-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="4e695-118">Text Value</span></span>

<span data-ttu-id="4e695-119">Ange mönstret som används för att formatera data.</span><span class="sxs-lookup"><span data-stu-id="4e695-119">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="4e695-120">Du kan till exempel använda det här mönstret för att formatera värdet för alla egenskaper som är av typen [system. TimeSpan](/dotnet/api/System.TimeSpan): {0: MMM} {0: DD} {0: hh}: {0: mm}.</span><span class="sxs-lookup"><span data-stu-id="4e695-120">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="4e695-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="4e695-121">Remarks</span></span>

<span data-ttu-id="4e695-122">Format strängar kan användas för att skapa tabellvyer, listvyer, breda vyer eller anpassade vyer.</span><span class="sxs-lookup"><span data-stu-id="4e695-122">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="4e695-123">Mer information om hur du formaterar ett värde som visas i en vy finns i [Formatera data som visas](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="4e695-123">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="4e695-124">Mer information om hur du använder format strängar i breda vyer finns i [skapa en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="4e695-124">For more information about using format strings in wide views, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="4e695-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="4e695-125">Example</span></span>

<span data-ttu-id="4e695-126">I följande exempel visas hur du definierar en format sträng för `StartTime` egenskapens värde.</span><span class="sxs-lookup"><span data-stu-id="4e695-126">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="4e695-127">Se även</span><span class="sxs-lookup"><span data-stu-id="4e695-127">See Also</span></span>

[<span data-ttu-id="4e695-128">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="4e695-128">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="4e695-129">WideItem-element för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="4e695-129">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="4e695-130">Skriva en Windows PowerShell-formatering och en typ fil</span><span class="sxs-lookup"><span data-stu-id="4e695-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
