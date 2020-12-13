---
ms.date: 09/13/2016
ms.topic: reference
title: FormatString-element för ListItem för ListControl  (format)
description: FormatString-element för ListItem för ListControl  (format)
ms.openlocfilehash: 1c16da92928ea632241942f4f2c63390c4fea706
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667920"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a><span data-ttu-id="5b357-103">FormatString-element för ListItem för ListControl  (format)</span><span class="sxs-lookup"><span data-stu-id="5b357-103">FormatString Element for ListItem for ListControl  (Format)</span></span>

<span data-ttu-id="5b357-104">Anger ett format mönster som definierar hur egenskapen eller skriptets värde visas.</span><span class="sxs-lookup"><span data-stu-id="5b357-104">Specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="5b357-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) ListEntries-element för ListControl (format) ListEntry-element för ListControl (format) ListItems-element för ListControl (format) ListItem-element för ListControl (format) FormatString-element för ListItem (format)</span><span class="sxs-lookup"><span data-stu-id="5b357-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem Element for ListControl (Format) FormatString Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5b357-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="5b357-106">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5b357-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="5b357-107">Attributes and Elements</span></span>

<span data-ttu-id="5b357-108">I följande avsnitt beskrivs attributen, underordnade element och `FormatString` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="5b357-108">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5b357-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="5b357-109">Attributes</span></span>

<span data-ttu-id="5b357-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="5b357-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5b357-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="5b357-111">Child Elements</span></span>

<span data-ttu-id="5b357-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="5b357-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5b357-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="5b357-113">Parent Elements</span></span>

|<span data-ttu-id="5b357-114">Element</span><span class="sxs-lookup"><span data-stu-id="5b357-114">Element</span></span>|<span data-ttu-id="5b357-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b357-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5b357-116">ListItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="5b357-116">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="5b357-117">Definierar egenskapen eller skriptet vars värde visas i en rad i list visningen.</span><span class="sxs-lookup"><span data-stu-id="5b357-117">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5b357-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="5b357-118">Text Value</span></span>

<span data-ttu-id="5b357-119">Ange mönstret som används för att formatera data.</span><span class="sxs-lookup"><span data-stu-id="5b357-119">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="5b357-120">Du kan till exempel använda det här mönstret för att formatera värdet för alla egenskaper som är av typen [system. TimeSpan](/dotnet/api/System.TimeSpan): {0: MMM} {0: DD} {0: hh}: {0: mm}.</span><span class="sxs-lookup"><span data-stu-id="5b357-120">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="5b357-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="5b357-121">Remarks</span></span>

<span data-ttu-id="5b357-122">Format strängar kan användas för att skapa tabellvyer, listvyer, breda vyer eller anpassade vyer.</span><span class="sxs-lookup"><span data-stu-id="5b357-122">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="5b357-123">Mer information om hur du formaterar ett värde som visas i en vy finns i [Formatera data som visas](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="5b357-123">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="5b357-124">Mer information om hur du använder format strängar i listvyer finns i [skapa listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="5b357-124">For more information about using format strings in list views, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="5b357-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="5b357-125">Example</span></span>

<span data-ttu-id="5b357-126">I följande exempel visas hur du definierar en format sträng för `StartTime` egenskapens värde.</span><span class="sxs-lookup"><span data-stu-id="5b357-126">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a><span data-ttu-id="5b357-127">Se även</span><span class="sxs-lookup"><span data-stu-id="5b357-127">See Also</span></span>

[<span data-ttu-id="5b357-128">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="5b357-128">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="5b357-129">ListItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="5b357-129">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="5b357-130">Skriva en Windows PowerShell-formatering och en typ fil</span><span class="sxs-lookup"><span data-stu-id="5b357-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
