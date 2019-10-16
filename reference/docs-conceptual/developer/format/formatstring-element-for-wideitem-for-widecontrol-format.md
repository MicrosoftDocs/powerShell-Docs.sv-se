---
title: FormatString-element för WideItem för WideControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5bc6ea26-3ca6-4bab-8a13-29189821ba15
caps.latest.revision: 7
ms.openlocfilehash: a1dc145864a6904fd4af6c3b9187819c49e224b0
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354546"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="86eb8-102">FormatString-element för WideItem för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="86eb8-102">FormatString Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="86eb8-103">Anger ett format mönster som definierar hur egenskapen eller skriptets värde visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="86eb8-103">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

<span data-ttu-id="86eb8-104">Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) WideEntries-element (format) WideEntry-element för WideControl (format) WideItem-element för WideControl (format) FormatString-element för WideItem för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="86eb8-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element for WideControl (Format) WideItem Element for WideControl (Format) FormatString Element for WideItem for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="86eb8-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="86eb8-105">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="86eb8-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="86eb8-106">Attributes and Elements</span></span>

<span data-ttu-id="86eb8-107">I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet för elementet `FormatString`.</span><span class="sxs-lookup"><span data-stu-id="86eb8-107">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="86eb8-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="86eb8-108">Attributes</span></span>

<span data-ttu-id="86eb8-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="86eb8-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="86eb8-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="86eb8-110">Child Elements</span></span>

<span data-ttu-id="86eb8-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="86eb8-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="86eb8-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="86eb8-112">Parent Elements</span></span>

|<span data-ttu-id="86eb8-113">Element</span><span class="sxs-lookup"><span data-stu-id="86eb8-113">Element</span></span>|<span data-ttu-id="86eb8-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="86eb8-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="86eb8-115">WideItem-element för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="86eb8-115">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="86eb8-116">Definierar egenskapen eller skriptet vars värde visas i en rad i list visningen.</span><span class="sxs-lookup"><span data-stu-id="86eb8-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="86eb8-117">Text värde</span><span class="sxs-lookup"><span data-stu-id="86eb8-117">Text Value</span></span>

<span data-ttu-id="86eb8-118">Ange mönstret som används för att formatera data.</span><span class="sxs-lookup"><span data-stu-id="86eb8-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="86eb8-119">Du kan till exempel använda det här mönstret för att formatera värdet för alla egenskaper som är av typen [system. TimeSpan](/dotnet/api/System.TimeSpan): {0: MMM} {0: DD} {0: hh}: {0: mm}.</span><span class="sxs-lookup"><span data-stu-id="86eb8-119">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="86eb8-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="86eb8-120">Remarks</span></span>

<span data-ttu-id="86eb8-121">Format strängar kan användas för att skapa tabellvyer, listvyer, breda vyer eller anpassade vyer.</span><span class="sxs-lookup"><span data-stu-id="86eb8-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="86eb8-122">Mer information om hur du formaterar ett värde som visas i en vy finns i [Formatera data som visas](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="86eb8-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="86eb8-123">Mer information om hur du använder format strängar i breda vyer finns i [skapa en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="86eb8-123">For more information about using format strings in wide views, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="86eb8-124">Exempel</span><span class="sxs-lookup"><span data-stu-id="86eb8-124">Example</span></span>

<span data-ttu-id="86eb8-125">I följande exempel visas hur du definierar en format sträng för värdet för egenskapen `StartTime`.</span><span class="sxs-lookup"><span data-stu-id="86eb8-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="86eb8-126">Se även</span><span class="sxs-lookup"><span data-stu-id="86eb8-126">See Also</span></span>

[<span data-ttu-id="86eb8-127">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="86eb8-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="86eb8-128">WideItem-element för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="86eb8-128">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="86eb8-129">Skriva en Windows PowerShell-formatering och en typ fil</span><span class="sxs-lookup"><span data-stu-id="86eb8-129">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
