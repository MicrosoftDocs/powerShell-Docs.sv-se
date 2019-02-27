---
title: FirstLineIndent Element för ramens för GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33be3b9e-53c8-433f-8c11-c65b0d46744c
caps.latest.revision: 6
ms.openlocfilehash: 9ba6fc1b9924a4b0d5b56ee15290a2293217403c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848603"
---
# <a name="firstlineindent-element-for-frame-for-groupby-format"></a><span data-ttu-id="2e75b-102">FirstLineIndent-element för Frame för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="2e75b-102">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>

<span data-ttu-id="2e75b-103">Anger hur många tecken som den första raden av data ska flyttas till höger.</span><span class="sxs-lookup"><span data-stu-id="2e75b-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="2e75b-104">Det här elementet används när du definierar hur en ny grupp med objekt visas.</span><span class="sxs-lookup"><span data-stu-id="2e75b-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="2e75b-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för Visa (Format) anpassad kontroll elementet för GroupBy (Format) CustomEntries Element för anpassad kontroll för GroupBy (Format) CustomEntry elementet för Anpassad kontroll för GroupBy (Format) CustomItem elementet för CustomEntry för GroupBy (Format) RAM-elementet för CustomItem för GroupBy (Format) FirstLineIndent elementet för ramens för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="2e75b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format) FirstLineIndent Element for Frame for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2e75b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="2e75b-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2e75b-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="2e75b-107">Attributes and Elements</span></span>

<span data-ttu-id="2e75b-108">I följande avsnitt beskrivs attribut, underordnade element och överordnade elementet i den `FirstLineIndent` element.</span><span class="sxs-lookup"><span data-stu-id="2e75b-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2e75b-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="2e75b-109">Attributes</span></span>

<span data-ttu-id="2e75b-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="2e75b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2e75b-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="2e75b-111">Child Elements</span></span>

<span data-ttu-id="2e75b-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="2e75b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2e75b-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="2e75b-113">Parent Elements</span></span>

|<span data-ttu-id="2e75b-114">Element</span><span class="sxs-lookup"><span data-stu-id="2e75b-114">Element</span></span>|<span data-ttu-id="2e75b-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2e75b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2e75b-116">Ramens Element för CustomItem för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="2e75b-116">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="2e75b-117">Definierar hur data visas, till exempel ändra datatypen till vänster eller höger.</span><span class="sxs-lookup"><span data-stu-id="2e75b-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2e75b-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="2e75b-118">Text Value</span></span>

<span data-ttu-id="2e75b-119">Ange antalet tecken som du vill flytta den första raden av data.</span><span class="sxs-lookup"><span data-stu-id="2e75b-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="2e75b-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="2e75b-120">Remarks</span></span>

<span data-ttu-id="2e75b-121">Om det här elementet har angetts, du kan inte ange den [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) element.</span><span class="sxs-lookup"><span data-stu-id="2e75b-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="2e75b-122">Se även</span><span class="sxs-lookup"><span data-stu-id="2e75b-122">See Also</span></span>

[<span data-ttu-id="2e75b-123">FirstLineHanging Element för ramens för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="2e75b-123">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="2e75b-124">Ramens Element för CustomItem för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="2e75b-124">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="2e75b-125">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="2e75b-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
