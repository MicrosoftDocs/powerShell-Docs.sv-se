---
title: CustomControl-element för vy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 660e8fd6531862790a2af7ab27a82e073c230693
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786058"
---
# <a name="customcontrol-element-for-view-format"></a><span data-ttu-id="64368-102">CustomControl-element för View (format)</span><span class="sxs-lookup"><span data-stu-id="64368-102">CustomControl Element for View (Format)</span></span>

<span data-ttu-id="64368-103">Definierar ett anpassat kontroll format för vyn.</span><span class="sxs-lookup"><span data-stu-id="64368-103">Defines a custom control format for the view.</span></span>

<span data-ttu-id="64368-104">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) CustomControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="64368-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="64368-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="64368-105">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="64368-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="64368-106">Attributes and Elements</span></span>

<span data-ttu-id="64368-107">I följande avsnitt beskrivs attribut, underordnade element och `CustomControl` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="64368-107">The following sections describe attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="64368-108">Du måste ange ett underordnat element.</span><span class="sxs-lookup"><span data-stu-id="64368-108">You must specify one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="64368-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="64368-109">Attributes</span></span>

<span data-ttu-id="64368-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="64368-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="64368-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="64368-111">Child Elements</span></span>

|<span data-ttu-id="64368-112">Element</span><span class="sxs-lookup"><span data-stu-id="64368-112">Element</span></span>|<span data-ttu-id="64368-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="64368-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="64368-114">CustomEntries-element för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="64368-114">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="64368-115">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="64368-115">Required element.</span></span><br /><br /> <span data-ttu-id="64368-116">Innehåller definitionerna för vyn anpassad kontroll.</span><span class="sxs-lookup"><span data-stu-id="64368-116">Provides the definitions of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="64368-117">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="64368-117">Parent Elements</span></span>

|<span data-ttu-id="64368-118">Element</span><span class="sxs-lookup"><span data-stu-id="64368-118">Element</span></span>|<span data-ttu-id="64368-119">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="64368-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="64368-120">View-element (format)</span><span class="sxs-lookup"><span data-stu-id="64368-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="64368-121">Definierar en vy som används för att visa ett eller flera .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="64368-121">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="64368-122">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="64368-122">Remarks</span></span>

<span data-ttu-id="64368-123">I de flesta fall krävs bara en definition för varje kontroll, men det är möjligt att ange flera definitioner om du vill använda samma vy för att visa olika .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="64368-123">In most cases, only one definition is required for each control view, but it is possible to provide multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="64368-124">I dessa fall kan du ange en separat definition för varje objekt eller uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="64368-124">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="64368-125">Se även</span><span class="sxs-lookup"><span data-stu-id="64368-125">See Also</span></span>

[<span data-ttu-id="64368-126">CustomEntries-element för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="64368-126">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="64368-127">View-element (format)</span><span class="sxs-lookup"><span data-stu-id="64368-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="64368-128">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="64368-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
