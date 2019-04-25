---
title: RAM-Element för CustomItem för kontroller för konfiguration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065571"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="54856-102">Frame-element för CustomItem för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="54856-102">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="54856-103">Definierar hur data visas, till exempel ändra datatypen till vänster eller höger.</span><span class="sxs-lookup"><span data-stu-id="54856-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="54856-104">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="54856-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="54856-105">Konfigurationselementet Element (Format) kontroller av (Format) kontroll konfigurationselement för kontroller för (Format) anpassad kontroll konfigurationselement för kontroll för (Format) CustomEntries konfigurationselement för anpassad kontroll för konfiguration ( Format) CustomEntry Element för anpassad kontroll för kontroller för (Format) CustomItem konfigurationselement för CustomEntry för kontroller för ramens konfigurationselement för CustomItem för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="54856-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="54856-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="54856-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="54856-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="54856-107">Attributes and Elements</span></span>

<span data-ttu-id="54856-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `Frame` element.</span><span class="sxs-lookup"><span data-stu-id="54856-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="54856-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="54856-109">Attributes</span></span>

<span data-ttu-id="54856-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="54856-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="54856-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="54856-111">Child Elements</span></span>

|<span data-ttu-id="54856-112">Element</span><span class="sxs-lookup"><span data-stu-id="54856-112">Element</span></span>|<span data-ttu-id="54856-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="54856-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="54856-114">Element som krävs</span><span class="sxs-lookup"><span data-stu-id="54856-114">Required Element</span></span>|
|[<span data-ttu-id="54856-115">FirstLineHanging Element för ramens för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="54856-115">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="54856-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="54856-116">Optional element.</span></span><br /><br /> <span data-ttu-id="54856-117">Anger hur många tecken som den första raden av data ska flyttas till vänster.</span><span class="sxs-lookup"><span data-stu-id="54856-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="54856-118">FirstLineIndent Element för ramens för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="54856-118">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="54856-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="54856-119">Optional element.</span></span><br /><br /> <span data-ttu-id="54856-120">Anger hur många tecken som den första raden av data ska flyttas till höger.</span><span class="sxs-lookup"><span data-stu-id="54856-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="54856-121">LeftIndent Element för ramens för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="54856-121">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="54856-122">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="54856-122">Optional element.</span></span><br /><br /> <span data-ttu-id="54856-123">Anger hur många tecken som data ska flyttas från vänster marginal.</span><span class="sxs-lookup"><span data-stu-id="54856-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="54856-124">RightIndent Element för ramens för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="54856-124">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="54856-125">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="54856-125">Optional element.</span></span><br /><br /> <span data-ttu-id="54856-126">Anger hur många tecken som data ska flyttas från höger marginal.</span><span class="sxs-lookup"><span data-stu-id="54856-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="54856-127">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="54856-127">Parent Elements</span></span>

|<span data-ttu-id="54856-128">Element</span><span class="sxs-lookup"><span data-stu-id="54856-128">Element</span></span>|<span data-ttu-id="54856-129">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="54856-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="54856-130">CustomItem Element för CustomEntry för kontroller för konfiguration</span><span class="sxs-lookup"><span data-stu-id="54856-130">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="54856-131">Definierar vilka data som visas av kontrollen och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="54856-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="54856-132">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="54856-132">Remarks</span></span>

<span data-ttu-id="54856-133">Du kan inte ange den [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) och [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) element i samma `Frame` element.</span><span class="sxs-lookup"><span data-stu-id="54856-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="54856-134">Se även</span><span class="sxs-lookup"><span data-stu-id="54856-134">See Also</span></span>

[<span data-ttu-id="54856-135">FirstLineHanging Element för ramens för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="54856-135">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="54856-136">FirstLineIndent Element för ramens för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="54856-136">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="54856-137">LeftIndent Element för ramens för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="54856-137">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="54856-138">RightIndent Element för ramens för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="54856-138">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="54856-139">CustomItem Element för CustomEntry för kontroller för konfiguration</span><span class="sxs-lookup"><span data-stu-id="54856-139">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="54856-140">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="54856-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
