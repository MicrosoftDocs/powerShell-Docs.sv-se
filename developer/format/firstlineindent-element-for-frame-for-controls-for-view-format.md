---
title: FirstLineIndent Element för ramens för kontroller för att visa (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec63f4f9-8858-4529-8646-ffbbc278f83e
caps.latest.revision: 7
ms.openlocfilehash: 694c5baaa5e90a772257276ba139d90acf7ec0e3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845635"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-view-format"></a><span data-ttu-id="cad12-102">FirstLineIndent-element för Frame för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="cad12-102">FirstLineIndent Element for Frame for Controls for View (Format)</span></span>

<span data-ttu-id="cad12-103">Anger hur många tecken som den första raden av data ska flyttas till höger.</span><span class="sxs-lookup"><span data-stu-id="cad12-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="cad12-104">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="cad12-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="cad12-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) kontroller Element (Format) kontroll konfigurationselement för kontroller för att visa (Format) anpassad kontroll Element för kontroll för kontroller för att visa (Format) CustomEntries Element för Anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för kontroller för att visa (Format) CustomItem Element för CustomEntry för kontroller för att visa (Format) RAM-Element för CustomItem för kontroller för att visa (Format) FirstLineIndent Element i ramen kontroller av vy (Format)</span><span class="sxs-lookup"><span data-stu-id="cad12-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format) FirstLineIndent Element of Frame of Controls of View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cad12-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="cad12-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cad12-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="cad12-107">Attributes and Elements</span></span>

<span data-ttu-id="cad12-108">I följande avsnitt beskrivs attribut, underordnade element och överordnade elementet i den `FirstLineIndent` element.</span><span class="sxs-lookup"><span data-stu-id="cad12-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cad12-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="cad12-109">Attributes</span></span>

<span data-ttu-id="cad12-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="cad12-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cad12-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="cad12-111">Child Elements</span></span>

<span data-ttu-id="cad12-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="cad12-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cad12-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="cad12-113">Parent Elements</span></span>

|<span data-ttu-id="cad12-114">Element</span><span class="sxs-lookup"><span data-stu-id="cad12-114">Element</span></span>|<span data-ttu-id="cad12-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="cad12-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cad12-116">Ramens Element för CustomItem för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="cad12-116">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="cad12-117">Definierar hur data visas, till exempel ändra datatypen till vänster eller höger.</span><span class="sxs-lookup"><span data-stu-id="cad12-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="cad12-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="cad12-118">Text Value</span></span>

<span data-ttu-id="cad12-119">Ange antalet tecken som du vill flytta den första raden av data.</span><span class="sxs-lookup"><span data-stu-id="cad12-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="cad12-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="cad12-120">Remarks</span></span>

<span data-ttu-id="cad12-121">Om det här elementet har angetts, du kan inte ange den [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) element.</span><span class="sxs-lookup"><span data-stu-id="cad12-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="cad12-122">Se även</span><span class="sxs-lookup"><span data-stu-id="cad12-122">See Also</span></span>

[<span data-ttu-id="cad12-123">FirstLineHanging Element för ramens för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="cad12-123">FirstLineHanging Element for Frame for Controls for View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="cad12-124">Ramens Element för CustomItem för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="cad12-124">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="cad12-125">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="cad12-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
