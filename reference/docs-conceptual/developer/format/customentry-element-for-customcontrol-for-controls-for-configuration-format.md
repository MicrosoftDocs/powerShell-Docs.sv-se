---
title: CustomEntry-element för CustomControl för kontroll av konfiguration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dfba86f-29b2-473c-9e98-9d679176acce
caps.latest.revision: 11
ms.openlocfilehash: 497485a388d1cdc834ecc1d1079b0714a7d7f9db
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355274"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="84acb-102">CustomEntry-element för CustomControl för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="84acb-102">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="84acb-103">Ger en definition av den gemensamma kontrollen.</span><span class="sxs-lookup"><span data-stu-id="84acb-103">Provides a definition of the common control.</span></span> <span data-ttu-id="84acb-104">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="84acb-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="84acb-105">Konfigurations element (format) styr element i konfigurations-(format) kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för konfiguration ( Format) CustomEntry-element för CustomControl för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="84acb-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="84acb-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="84acb-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="84acb-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="84acb-107">Attributes and Elements</span></span>

<span data-ttu-id="84acb-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `CustomEntry`-elementet.</span><span class="sxs-lookup"><span data-stu-id="84acb-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="84acb-109">Du måste ange de objekt som ska visas av definitionen.</span><span class="sxs-lookup"><span data-stu-id="84acb-109">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="84acb-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="84acb-110">Attributes</span></span>

<span data-ttu-id="84acb-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="84acb-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="84acb-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="84acb-112">Child Elements</span></span>

|<span data-ttu-id="84acb-113">Element</span><span class="sxs-lookup"><span data-stu-id="84acb-113">Element</span></span>|<span data-ttu-id="84acb-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="84acb-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="84acb-115">EntrySelectedBy-element för CustomEntry för kontroller för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="84acb-115">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="84acb-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="84acb-116">Optional element.</span></span><br /><br /> <span data-ttu-id="84acb-117">Definierar de .NET-typer som använder definitionen av den gemensamma kontrollen eller villkoret som måste finnas för att den här kontrollen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="84acb-117">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="84acb-118">CustomItem-element för CustomEntry för kontroller för konfiguration</span><span class="sxs-lookup"><span data-stu-id="84acb-118">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="84acb-119">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="84acb-119">Required element.</span></span><br /><br /> <span data-ttu-id="84acb-120">Definierar vilka data som visas av kontrollen och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="84acb-120">Defines what data is displayed by the control and how it is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="84acb-121">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="84acb-121">Parent Elements</span></span>

|<span data-ttu-id="84acb-122">Element</span><span class="sxs-lookup"><span data-stu-id="84acb-122">Element</span></span>|<span data-ttu-id="84acb-123">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="84acb-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="84acb-124">CustomEntries-element för CustomControl för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="84acb-124">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="84acb-125">Innehåller definitionerna för den gemensamma kontrollen.</span><span class="sxs-lookup"><span data-stu-id="84acb-125">Provides the definitions of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="84acb-126">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="84acb-126">Remarks</span></span>

<span data-ttu-id="84acb-127">I de flesta fall krävs bara en definition för varje gemensam anpassad kontroll, men det är möjligt att ha flera definitioner om du vill använda samma kontroll för att visa olika .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="84acb-127">In most cases, only one definition is required for each common custom control, but it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="84acb-128">I dessa fall kan du ange en separat definition för varje objekt eller uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="84acb-128">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="84acb-129">Se även</span><span class="sxs-lookup"><span data-stu-id="84acb-129">See Also</span></span>

[<span data-ttu-id="84acb-130">CustomEntries-element för CustomControl för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="84acb-130">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="84acb-131">CustomItem-element för CustomEntry för kontroller för konfiguration</span><span class="sxs-lookup"><span data-stu-id="84acb-131">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="84acb-132">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="84acb-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
