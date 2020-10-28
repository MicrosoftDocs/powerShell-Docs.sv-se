---
ms.date: 09/13/2016
ms.topic: reference
title: FirstLineHanging-element för Frame för Controls för Configuration (format)
description: FirstLineHanging-element för Frame för Controls för Configuration (format)
ms.openlocfilehash: 94d59ef7b54e036f76e38a3b06b769700443b9fb
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655229"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-configuration-format"></a><span data-ttu-id="87ede-103">FirstLineHanging-element för Frame för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="87ede-103">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>

<span data-ttu-id="87ede-104">Anger hur många tecken den första raden med data flyttas till vänster.</span><span class="sxs-lookup"><span data-stu-id="87ede-104">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="87ede-105">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="87ede-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="87ede-106">Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för konfiguration (format) CustomEntry-element för CustomControl for Controls for Configuration (format) CustomItem-elementet för CustomEntry for Controls for Control List element for CustomItem for Controls for Configuration (format) FirstLineHanging element for Frame for Controls for Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="87ede-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format) FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="87ede-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="87ede-107">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="87ede-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="87ede-108">Attributes and Elements</span></span>

<span data-ttu-id="87ede-109">I följande avsnitt beskrivs attribut, underordnade element och `FirstLineHanging` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="87ede-109">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="87ede-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="87ede-110">Attributes</span></span>

<span data-ttu-id="87ede-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="87ede-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="87ede-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="87ede-112">Child Elements</span></span>

<span data-ttu-id="87ede-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="87ede-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="87ede-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="87ede-114">Parent Elements</span></span>

|<span data-ttu-id="87ede-115">Element</span><span class="sxs-lookup"><span data-stu-id="87ede-115">Element</span></span>|<span data-ttu-id="87ede-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="87ede-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="87ede-117">Frame-element för CustomItem för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="87ede-117">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="87ede-118">Definierar hur data visas, till exempel att flytta data till vänster eller höger.</span><span class="sxs-lookup"><span data-stu-id="87ede-118">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="87ede-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="87ede-119">Text Value</span></span>

<span data-ttu-id="87ede-120">Ange antalet tecken som du vill flytta den första raden i data.</span><span class="sxs-lookup"><span data-stu-id="87ede-120">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="87ede-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="87ede-121">Remarks</span></span>

<span data-ttu-id="87ede-122">Om det här elementet har angetts kan du inte ange `FirstLineIndent` elementet.</span><span class="sxs-lookup"><span data-stu-id="87ede-122">If this element is specified, you cannot specify the `FirstLineIndent` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="87ede-123">Se även</span><span class="sxs-lookup"><span data-stu-id="87ede-123">See Also</span></span>

[<span data-ttu-id="87ede-124">Frame-element för CustomItem för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="87ede-124">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="87ede-125">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="87ede-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
