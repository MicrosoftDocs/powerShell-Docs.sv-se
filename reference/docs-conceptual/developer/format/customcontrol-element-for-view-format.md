---
title: CustomControl-element för vy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354777"
---
# <a name="customcontrol-element-for-view-format"></a><span data-ttu-id="5b49f-102">CustomControl-element för View (format)</span><span class="sxs-lookup"><span data-stu-id="5b49f-102">CustomControl Element for View (Format)</span></span>

<span data-ttu-id="5b49f-103">Definierar ett anpassat kontroll format för vyn.</span><span class="sxs-lookup"><span data-stu-id="5b49f-103">Defines a custom control format for the view.</span></span>

<span data-ttu-id="5b49f-104">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) CustomControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="5b49f-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5b49f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5b49f-105">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5b49f-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="5b49f-106">Attributes and Elements</span></span>

<span data-ttu-id="5b49f-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `CustomControl`.</span><span class="sxs-lookup"><span data-stu-id="5b49f-107">The following sections describe attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="5b49f-108">Du måste ange ett underordnat element.</span><span class="sxs-lookup"><span data-stu-id="5b49f-108">You must specify one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5b49f-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="5b49f-109">Attributes</span></span>

<span data-ttu-id="5b49f-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="5b49f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5b49f-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="5b49f-111">Child Elements</span></span>

|<span data-ttu-id="5b49f-112">Element</span><span class="sxs-lookup"><span data-stu-id="5b49f-112">Element</span></span>|<span data-ttu-id="5b49f-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b49f-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5b49f-114">CustomEntries-element för CustomControl för vy (format)</span><span class="sxs-lookup"><span data-stu-id="5b49f-114">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="5b49f-115">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="5b49f-115">Required element.</span></span><br /><br /> <span data-ttu-id="5b49f-116">Innehåller definitionerna för vyn anpassad kontroll.</span><span class="sxs-lookup"><span data-stu-id="5b49f-116">Provides the definitions of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5b49f-117">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="5b49f-117">Parent Elements</span></span>

|<span data-ttu-id="5b49f-118">Element</span><span class="sxs-lookup"><span data-stu-id="5b49f-118">Element</span></span>|<span data-ttu-id="5b49f-119">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b49f-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5b49f-120">Visa element (format)</span><span class="sxs-lookup"><span data-stu-id="5b49f-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="5b49f-121">Definierar en vy som används för att visa ett eller flera .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="5b49f-121">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5b49f-122">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="5b49f-122">Remarks</span></span>

<span data-ttu-id="5b49f-123">I de flesta fall krävs bara en definition för varje kontroll, men det är möjligt att ange flera definitioner om du vill använda samma vy för att visa olika .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="5b49f-123">In most cases, only one definition is required for each control view, but it is possible to provide multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="5b49f-124">I dessa fall kan du ange en separat definition för varje objekt eller uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="5b49f-124">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="5b49f-125">Se även</span><span class="sxs-lookup"><span data-stu-id="5b49f-125">See Also</span></span>

[<span data-ttu-id="5b49f-126">CustomEntries-element för CustomControl för vy (format)</span><span class="sxs-lookup"><span data-stu-id="5b49f-126">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5b49f-127">Visa element (format)</span><span class="sxs-lookup"><span data-stu-id="5b49f-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="5b49f-128">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="5b49f-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
