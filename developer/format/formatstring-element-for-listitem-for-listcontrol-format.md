---
title: FormatString-Element för ListItem för ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd2cac66-88bb-449f-9d47-bd2cd4fe1801
caps.latest.revision: 13
ms.openlocfilehash: e6024ec4f7fc490c92408047c8c15c775e45bf9d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065634"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a><span data-ttu-id="7d149-102">FormatString-element för ListItem för ListControl  (format)</span><span class="sxs-lookup"><span data-stu-id="7d149-102">FormatString Element for ListItem for ListControl  (Format)</span></span>

<span data-ttu-id="7d149-103">Anger ett formatmönster som definierar hur värdet för egenskapen eller skript visas.</span><span class="sxs-lookup"><span data-stu-id="7d149-103">Specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="7d149-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ListControl Element (Format) ListEntries konfigurationselement för ListControl (Format) ListEntry elementet för ListControl (Format) ListItems som finns Element för ListControl (Format) ListItem Element för ListControl (Format) FormatString-elementet för ListItem för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7d149-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem Element for ListControl (Format) FormatString Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7d149-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7d149-105">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7d149-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="7d149-106">Attributes and Elements</span></span>

<span data-ttu-id="7d149-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `FormatString` element.</span><span class="sxs-lookup"><span data-stu-id="7d149-107">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7d149-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="7d149-108">Attributes</span></span>

<span data-ttu-id="7d149-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="7d149-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7d149-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="7d149-110">Child Elements</span></span>

<span data-ttu-id="7d149-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="7d149-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7d149-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="7d149-112">Parent Elements</span></span>

|<span data-ttu-id="7d149-113">Element</span><span class="sxs-lookup"><span data-stu-id="7d149-113">Element</span></span>|<span data-ttu-id="7d149-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d149-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7d149-115">ListItem Element (Format)</span><span class="sxs-lookup"><span data-stu-id="7d149-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="7d149-116">Definierar egenskapen eller skript som vars värde visas i en rad i listvyn.</span><span class="sxs-lookup"><span data-stu-id="7d149-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7d149-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="7d149-117">Text Value</span></span>

<span data-ttu-id="7d149-118">Ange mönstret som används för att formatera data.</span><span class="sxs-lookup"><span data-stu-id="7d149-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="7d149-119">Du kan till exempel använda det här mönstret ska formateras värdet för en egenskap som är av typen [System.Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {0:HH}: {0:mm}.</span><span class="sxs-lookup"><span data-stu-id="7d149-119">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="7d149-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="7d149-120">Remarks</span></span>

<span data-ttu-id="7d149-121">Formatsträngar kan användas när du skapar tabellvyer, listvyer, brett vyer eller anpassade vyer.</span><span class="sxs-lookup"><span data-stu-id="7d149-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="7d149-122">Mer information om hur du formaterar ett värde som visas i en vy finns i [formatering visas Data](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="7d149-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="7d149-123">Läs mer om hur du använder formatsträngar i listvyer [skapar listvyn](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="7d149-123">For more information about using format strings in list views, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="7d149-124">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d149-124">Example</span></span>

<span data-ttu-id="7d149-125">I följande exempel visas hur du definierar en formateringssträngen för värdet för den `StartTime` egenskapen.</span><span class="sxs-lookup"><span data-stu-id="7d149-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a><span data-ttu-id="7d149-126">Se även</span><span class="sxs-lookup"><span data-stu-id="7d149-126">See Also</span></span>

[<span data-ttu-id="7d149-127">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="7d149-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="7d149-128">ListItem Element (Format)</span><span class="sxs-lookup"><span data-stu-id="7d149-128">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="7d149-129">Skriva ett Windows PowerShell formatering och skriver fil</span><span class="sxs-lookup"><span data-stu-id="7d149-129">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
