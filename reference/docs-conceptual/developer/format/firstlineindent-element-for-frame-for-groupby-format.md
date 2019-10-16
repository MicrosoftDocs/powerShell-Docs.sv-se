---
title: FirstLineIndent-element för inramad GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33be3b9e-53c8-433f-8c11-c65b0d46744c
caps.latest.revision: 6
ms.openlocfilehash: 9ba6fc1b9924a4b0d5b56ee15290a2293217403c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354581"
---
# <a name="firstlineindent-element-for-frame-for-groupby-format"></a><span data-ttu-id="5c04e-102">FirstLineIndent-element för Frame för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="5c04e-102">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>

<span data-ttu-id="5c04e-103">Anger hur många tecken den första raden med data flyttas till höger.</span><span class="sxs-lookup"><span data-stu-id="5c04e-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="5c04e-104">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="5c04e-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="5c04e-105">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element för CustomControl for GroupBy (format) CustomItem-element för CustomEntry för GroupBy (format)-ram element för CustomItem för GroupBy (format) FirstLineIndent-element för ram for GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="5c04e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format) FirstLineIndent Element for Frame for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5c04e-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="5c04e-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5c04e-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="5c04e-107">Attributes and Elements</span></span>

<span data-ttu-id="5c04e-108">I följande avsnitt beskrivs attribut, underordnade element och ett överordnat element för elementet `FirstLineIndent`.</span><span class="sxs-lookup"><span data-stu-id="5c04e-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5c04e-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="5c04e-109">Attributes</span></span>

<span data-ttu-id="5c04e-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="5c04e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5c04e-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="5c04e-111">Child Elements</span></span>

<span data-ttu-id="5c04e-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="5c04e-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5c04e-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="5c04e-113">Parent Elements</span></span>

|<span data-ttu-id="5c04e-114">Element</span><span class="sxs-lookup"><span data-stu-id="5c04e-114">Element</span></span>|<span data-ttu-id="5c04e-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5c04e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5c04e-116">Ram element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="5c04e-116">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="5c04e-117">Definierar hur data visas, till exempel att flytta data till vänster eller höger.</span><span class="sxs-lookup"><span data-stu-id="5c04e-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5c04e-118">Text värde</span><span class="sxs-lookup"><span data-stu-id="5c04e-118">Text Value</span></span>

<span data-ttu-id="5c04e-119">Ange antalet tecken som du vill flytta den första raden i data.</span><span class="sxs-lookup"><span data-stu-id="5c04e-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="5c04e-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="5c04e-120">Remarks</span></span>

<span data-ttu-id="5c04e-121">Om det här elementet har angetts kan du inte ange [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) -elementet.</span><span class="sxs-lookup"><span data-stu-id="5c04e-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="5c04e-122">Se även</span><span class="sxs-lookup"><span data-stu-id="5c04e-122">See Also</span></span>

[<span data-ttu-id="5c04e-123">FirstLineHanging-element för inramad GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="5c04e-123">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="5c04e-124">Ram element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="5c04e-124">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="5c04e-125">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="5c04e-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
