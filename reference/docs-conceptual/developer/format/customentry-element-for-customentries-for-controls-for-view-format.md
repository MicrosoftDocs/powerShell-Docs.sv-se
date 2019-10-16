---
title: CustomEntry-element för CustomEntries för kontroller för vy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6739205-2bc9-4507-b2af-d19d548c2057
caps.latest.revision: 6
ms.openlocfilehash: b92b99d88992cf13dbf7bfbe88aad603615f3138
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355260"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a><span data-ttu-id="6e04f-102">CustomEntry-element för CustomEntries för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="6e04f-102">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

<span data-ttu-id="6e04f-103">Ger en definition av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="6e04f-103">Provides a definition of the control.</span></span> <span data-ttu-id="6e04f-104">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="6e04f-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="6e04f-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) styr element för Controls (format) CustomControl-element för kontroll för Control for View (format) CustomEntries-element för CustomControl för visnings-(format) CustomEntry-element för CustomEntries för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="6e04f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6e04f-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="6e04f-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6e04f-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="6e04f-107">Attributes and Elements</span></span>

<span data-ttu-id="6e04f-108">I följande avsnitt beskrivs attribut, underordnade element och de överordnade elementen för elementet `CustomEntry`.</span><span class="sxs-lookup"><span data-stu-id="6e04f-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6e04f-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="6e04f-109">Attributes</span></span>

<span data-ttu-id="6e04f-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="6e04f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6e04f-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="6e04f-111">Child Elements</span></span>

|<span data-ttu-id="6e04f-112">Element</span><span class="sxs-lookup"><span data-stu-id="6e04f-112">Element</span></span>|<span data-ttu-id="6e04f-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6e04f-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6e04f-114">EntrySelectedBy-element för CustomEntry för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="6e04f-114">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="6e04f-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="6e04f-115">Optional element.</span></span><br /><br /> <span data-ttu-id="6e04f-116">Definierar de .NET-typer som använder den här kontroll definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="6e04f-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="6e04f-117">CustomItem-element för CustomEntry för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="6e04f-117">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="6e04f-118">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="6e04f-118">Required element.</span></span><br /><br /> <span data-ttu-id="6e04f-119">Definierar hur kontrollen visar data.</span><span class="sxs-lookup"><span data-stu-id="6e04f-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6e04f-120">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="6e04f-120">Parent Elements</span></span>

|<span data-ttu-id="6e04f-121">Element</span><span class="sxs-lookup"><span data-stu-id="6e04f-121">Element</span></span>|<span data-ttu-id="6e04f-122">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6e04f-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6e04f-123">CustomEntries-element för CustomControl för vy (format)</span><span class="sxs-lookup"><span data-stu-id="6e04f-123">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="6e04f-124">Innehåller definitionerna för kontrollen.</span><span class="sxs-lookup"><span data-stu-id="6e04f-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6e04f-125">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="6e04f-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="6e04f-126">Se även</span><span class="sxs-lookup"><span data-stu-id="6e04f-126">See Also</span></span>

[<span data-ttu-id="6e04f-127">CustomEntries-element för CustomControl för vy (format)</span><span class="sxs-lookup"><span data-stu-id="6e04f-127">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="6e04f-128">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="6e04f-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
