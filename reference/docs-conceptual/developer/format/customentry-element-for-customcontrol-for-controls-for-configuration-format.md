---
title: CustomEntry-element för CustomControl för kontroll av konfiguration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 8b9d18bbb1abce8135f4c27418ad54a1736eb5a6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785939"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="a6d78-102">CustomEntry-element för CustomControl för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="a6d78-102">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="a6d78-103">Ger en definition av den gemensamma kontrollen.</span><span class="sxs-lookup"><span data-stu-id="a6d78-103">Provides a definition of the common control.</span></span> <span data-ttu-id="a6d78-104">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="a6d78-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="a6d78-105">Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för Configuration (format) CustomEntry-element för CustomControl för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="a6d78-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a6d78-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="a6d78-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="a6d78-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="a6d78-107">Attributes and Elements</span></span>

<span data-ttu-id="a6d78-108">I följande avsnitt beskrivs attribut, underordnade element och `CustomEntry` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="a6d78-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="a6d78-109">Du måste ange de objekt som ska visas av definitionen.</span><span class="sxs-lookup"><span data-stu-id="a6d78-109">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="a6d78-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="a6d78-110">Attributes</span></span>

<span data-ttu-id="a6d78-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="a6d78-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a6d78-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="a6d78-112">Child Elements</span></span>

|<span data-ttu-id="a6d78-113">Element</span><span class="sxs-lookup"><span data-stu-id="a6d78-113">Element</span></span>|<span data-ttu-id="a6d78-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a6d78-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a6d78-115">EntrySelectedBy-element för CustomEntry för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="a6d78-115">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="a6d78-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="a6d78-116">Optional element.</span></span><br /><br /> <span data-ttu-id="a6d78-117">Definierar de .NET-typer som använder definitionen av den gemensamma kontrollen eller villkoret som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="a6d78-117">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="a6d78-118">CustomItem-element för CustomEntry för kontroller för konfiguration</span><span class="sxs-lookup"><span data-stu-id="a6d78-118">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="a6d78-119">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="a6d78-119">Required element.</span></span><br /><br /> <span data-ttu-id="a6d78-120">Definierar vilka data som visas av kontrollen och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="a6d78-120">Defines what data is displayed by the control and how it is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a6d78-121">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="a6d78-121">Parent Elements</span></span>

|<span data-ttu-id="a6d78-122">Element</span><span class="sxs-lookup"><span data-stu-id="a6d78-122">Element</span></span>|<span data-ttu-id="a6d78-123">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a6d78-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a6d78-124">CustomEntries-element för CustomControl för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="a6d78-124">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="a6d78-125">Innehåller definitionerna för den gemensamma kontrollen.</span><span class="sxs-lookup"><span data-stu-id="a6d78-125">Provides the definitions of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a6d78-126">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="a6d78-126">Remarks</span></span>

<span data-ttu-id="a6d78-127">I de flesta fall krävs bara en definition för varje gemensam anpassad kontroll, men det är möjligt att ha flera definitioner om du vill använda samma kontroll för att visa olika .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="a6d78-127">In most cases, only one definition is required for each common custom control, but it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="a6d78-128">I dessa fall kan du ange en separat definition för varje objekt eller uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="a6d78-128">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="a6d78-129">Se även</span><span class="sxs-lookup"><span data-stu-id="a6d78-129">See Also</span></span>

[<span data-ttu-id="a6d78-130">CustomEntries-element för CustomControl för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="a6d78-130">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="a6d78-131">CustomItem-element för CustomEntry för kontroller för konfiguration</span><span class="sxs-lookup"><span data-stu-id="a6d78-131">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="a6d78-132">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="a6d78-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
