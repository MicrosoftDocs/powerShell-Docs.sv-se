---
ms.date: 09/13/2016
ms.topic: reference
title: FirstLineHanging-element för Frame för GroupBy (format)
description: FirstLineHanging-element för Frame för GroupBy (format)
ms.openlocfilehash: 6a4ded9cced484440636aee694cd8381b2889ba8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652268"
---
# <a name="firstlinehanging-element-for-frame-for-groupby-format"></a><span data-ttu-id="88554-103">FirstLineHanging-element för Frame för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="88554-103">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>

<span data-ttu-id="88554-104">Anger hur många tecken den första raden med data flyttas till vänster.</span><span class="sxs-lookup"><span data-stu-id="88554-104">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="88554-105">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="88554-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="88554-106">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry element for CustomControl for groupby (format) CustomItem-element för CustomEntry-element (format) för CustomItem för (format)</span><span class="sxs-lookup"><span data-stu-id="88554-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format) FirstLineHanging Element for Frame for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="88554-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="88554-107">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="88554-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="88554-108">Attributes and Elements</span></span>

<span data-ttu-id="88554-109">I följande avsnitt beskrivs attribut, underordnade element och `FirstLineHanging` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="88554-109">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="88554-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="88554-110">Attributes</span></span>

<span data-ttu-id="88554-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="88554-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="88554-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="88554-112">Child Elements</span></span>

<span data-ttu-id="88554-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="88554-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="88554-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="88554-114">Parent Elements</span></span>

|<span data-ttu-id="88554-115">Element</span><span class="sxs-lookup"><span data-stu-id="88554-115">Element</span></span>|<span data-ttu-id="88554-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="88554-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="88554-117">Frame-element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="88554-117">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="88554-118">Definierar hur data visas, till exempel att flytta data till vänster eller höger.</span><span class="sxs-lookup"><span data-stu-id="88554-118">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="88554-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="88554-119">Text Value</span></span>

<span data-ttu-id="88554-120">Ange antalet tecken som du vill flytta den första raden i data.</span><span class="sxs-lookup"><span data-stu-id="88554-120">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="88554-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="88554-121">Remarks</span></span>

<span data-ttu-id="88554-122">Om det här elementet har angetts kan du inte ange [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) -elementet.</span><span class="sxs-lookup"><span data-stu-id="88554-122">If this element is specified, you cannot specify the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="88554-123">Se även</span><span class="sxs-lookup"><span data-stu-id="88554-123">See Also</span></span>

[<span data-ttu-id="88554-124">FirstLineIndent-element för Frame för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="88554-124">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="88554-125">Frame-element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="88554-125">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="88554-126">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="88554-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
