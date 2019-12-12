---
title: Ram element för CustomItem för kontroll av konfiguration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354987"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="045de-102">Frame-element för CustomItem för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="045de-102">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="045de-103">Definierar hur data visas, till exempel att flytta data till vänster eller höger.</span><span class="sxs-lookup"><span data-stu-id="045de-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="045de-104">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="045de-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="045de-105">Konfigurations element (format) styr element i konfigurations-(format) kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för konfiguration ( Format) CustomEntry-element för CustomControl for Controls for Configuration (format) CustomItem-element för CustomEntry för Controls för konfigurations ram element för CustomItem för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="045de-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="045de-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="045de-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="045de-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="045de-107">Attributes and Elements</span></span>

<span data-ttu-id="045de-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `Frame`-elementet.</span><span class="sxs-lookup"><span data-stu-id="045de-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="045de-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="045de-109">Attributes</span></span>

<span data-ttu-id="045de-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="045de-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="045de-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="045de-111">Child Elements</span></span>

|<span data-ttu-id="045de-112">Element</span><span class="sxs-lookup"><span data-stu-id="045de-112">Element</span></span>|<span data-ttu-id="045de-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="045de-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="045de-114">Nödvändigt element</span><span class="sxs-lookup"><span data-stu-id="045de-114">Required Element</span></span>|
|[<span data-ttu-id="045de-115">FirstLineHanging-element för ram för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="045de-115">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="045de-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="045de-116">Optional element.</span></span><br /><br /> <span data-ttu-id="045de-117">Anger hur många tecken den första raden med data flyttas till vänster.</span><span class="sxs-lookup"><span data-stu-id="045de-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="045de-118">FirstLineIndent-element för ram för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="045de-118">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="045de-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="045de-119">Optional element.</span></span><br /><br /> <span data-ttu-id="045de-120">Anger hur många tecken den första raden med data flyttas till höger.</span><span class="sxs-lookup"><span data-stu-id="045de-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="045de-121">LeftIndent-element för ram för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="045de-121">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="045de-122">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="045de-122">Optional element.</span></span><br /><br /> <span data-ttu-id="045de-123">Anger hur många tecken data flyttas bort från vänstermarginalen.</span><span class="sxs-lookup"><span data-stu-id="045de-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="045de-124">RightIndent-element för ram för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="045de-124">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="045de-125">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="045de-125">Optional element.</span></span><br /><br /> <span data-ttu-id="045de-126">Anger hur många tecken data flyttas bort från högermarginalen.</span><span class="sxs-lookup"><span data-stu-id="045de-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="045de-127">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="045de-127">Parent Elements</span></span>

|<span data-ttu-id="045de-128">Element</span><span class="sxs-lookup"><span data-stu-id="045de-128">Element</span></span>|<span data-ttu-id="045de-129">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="045de-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="045de-130">CustomItem-element för CustomEntry för kontroller för konfiguration</span><span class="sxs-lookup"><span data-stu-id="045de-130">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="045de-131">Definierar vilka data som visas av kontrollen och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="045de-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="045de-132">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="045de-132">Remarks</span></span>

<span data-ttu-id="045de-133">Du kan inte ange [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) och [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) -elementen i samma `Frame`-element.</span><span class="sxs-lookup"><span data-stu-id="045de-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="045de-134">Se även</span><span class="sxs-lookup"><span data-stu-id="045de-134">See Also</span></span>

[<span data-ttu-id="045de-135">FirstLineHanging-element för ram för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="045de-135">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="045de-136">FirstLineIndent-element för ram för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="045de-136">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="045de-137">LeftIndent-element för ram för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="045de-137">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="045de-138">RightIndent-element för ram för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="045de-138">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="045de-139">CustomItem-element för CustomEntry för kontroller för konfiguration</span><span class="sxs-lookup"><span data-stu-id="045de-139">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="045de-140">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="045de-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
