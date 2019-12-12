---
title: CustomEntries-element för CustomControl för kontroller för vy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359025"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a><span data-ttu-id="b5845-102">CustomEntries-element för CustomControl för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="b5845-102">CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

<span data-ttu-id="b5845-103">Innehåller definitionerna för kontrollen.</span><span class="sxs-lookup"><span data-stu-id="b5845-103">Provides the definitions for the control.</span></span> <span data-ttu-id="b5845-104">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="b5845-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="b5845-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) styr element för Controls (format) CustomControl-element för kontroll för Control for View (format) CustomEntries-element för CustomControl för Visa kontroller (format)</span><span class="sxs-lookup"><span data-stu-id="b5845-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b5845-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="b5845-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b5845-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="b5845-107">Attributes and Elements</span></span>

<span data-ttu-id="b5845-108">I följande avsnitt beskrivs attribut, underordnade element och överordnade element i `CustomEntries`-elementet.</span><span class="sxs-lookup"><span data-stu-id="b5845-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="b5845-109">Det finns ingen övre gräns för antalet underordnade element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="b5845-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="b5845-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="b5845-110">Attributes</span></span>

<span data-ttu-id="b5845-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="b5845-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b5845-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="b5845-112">Child Elements</span></span>

|<span data-ttu-id="b5845-113">Element</span><span class="sxs-lookup"><span data-stu-id="b5845-113">Element</span></span>|<span data-ttu-id="b5845-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b5845-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b5845-115">CustomEntry-element för CustomEntries för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="b5845-115">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="b5845-116">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="b5845-116">Required element.</span></span><br /><br /> <span data-ttu-id="b5845-117">Ger en definition av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="b5845-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b5845-118">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="b5845-118">Parent Elements</span></span>

|<span data-ttu-id="b5845-119">Element</span><span class="sxs-lookup"><span data-stu-id="b5845-119">Element</span></span>|<span data-ttu-id="b5845-120">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b5845-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b5845-121">CustomControl-element för kontroll för vy (format)</span><span class="sxs-lookup"><span data-stu-id="b5845-121">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="b5845-122">Definierar den kontroll som används i vyn.</span><span class="sxs-lookup"><span data-stu-id="b5845-122">Defines the control used by the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b5845-123">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="b5845-123">Remarks</span></span>

<span data-ttu-id="b5845-124">I de flesta fall har en kontroll bara en definition som anges i ett enda `CustomEntry`-element.</span><span class="sxs-lookup"><span data-stu-id="b5845-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="b5845-125">Det är dock möjligt att tillhandahålla flera definitioner om du vill använda samma kontroll för att visa olika .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="b5845-125">However, it is possible to provide multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="b5845-126">I dessa fall kan du definiera ett `CustomEntry`-element för varje objekt eller uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="b5845-126">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5845-127">Se även</span><span class="sxs-lookup"><span data-stu-id="b5845-127">See Also</span></span>

[<span data-ttu-id="b5845-128">CustomEntry-element för CustomEntries för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="b5845-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="b5845-129">CustomControl-element för kontroll för vy (format)</span><span class="sxs-lookup"><span data-stu-id="b5845-129">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="b5845-130">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="b5845-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
