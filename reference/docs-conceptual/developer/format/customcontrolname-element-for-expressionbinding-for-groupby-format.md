---
title: CustomControlName-element för ExpressionBinding for GroupBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359039"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="1dcf6-102">CustomControlName-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="1dcf6-102">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="1dcf6-103">Anger namnet på en gemensam kontroll eller en visnings kontroll.</span><span class="sxs-lookup"><span data-stu-id="1dcf6-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="1dcf6-104">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="1dcf6-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="1dcf6-105">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element för CustomControl for GroupBy (format) CustomItem-element för CustomEntry för GroupBy (format) ExpressionBinding-element för CustomItem för GroupBy (format) CustomControlName-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="1dcf6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1dcf6-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="1dcf6-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1dcf6-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="1dcf6-107">Attributes and Elements</span></span>

<span data-ttu-id="1dcf6-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `CustomControlName`-elementet.</span><span class="sxs-lookup"><span data-stu-id="1dcf6-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1dcf6-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="1dcf6-109">Attributes</span></span>

<span data-ttu-id="1dcf6-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="1dcf6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1dcf6-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="1dcf6-111">Child Elements</span></span>

<span data-ttu-id="1dcf6-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="1dcf6-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1dcf6-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="1dcf6-113">Parent Elements</span></span>

|<span data-ttu-id="1dcf6-114">Element</span><span class="sxs-lookup"><span data-stu-id="1dcf6-114">Element</span></span>|<span data-ttu-id="1dcf6-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1dcf6-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1dcf6-116">ExpressionBinding-element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="1dcf6-116">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="1dcf6-117">Definierar de data som visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="1dcf6-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1dcf6-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="1dcf6-118">Text Value</span></span>

<span data-ttu-id="1dcf6-119">Ange namnet på kontrollen.</span><span class="sxs-lookup"><span data-stu-id="1dcf6-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="1dcf6-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="1dcf6-120">Remarks</span></span>

<span data-ttu-id="1dcf6-121">Du kan skapa vanliga kontroller som kan användas av alla vyer i en fil format och du kan skapa visnings kontroller som kan användas av en speciell vy.</span><span class="sxs-lookup"><span data-stu-id="1dcf6-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="1dcf6-122">Följande element anger namnen på dessa kontroller:</span><span class="sxs-lookup"><span data-stu-id="1dcf6-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="1dcf6-123">Namn element för kontroll för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="1dcf6-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="1dcf6-124">Namn element för kontroll för vy (format)</span><span class="sxs-lookup"><span data-stu-id="1dcf6-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="1dcf6-125">Se även</span><span class="sxs-lookup"><span data-stu-id="1dcf6-125">See Also</span></span>

[<span data-ttu-id="1dcf6-126">Namn element för kontroll för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="1dcf6-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="1dcf6-127">Namn element för kontroll för vy (format)</span><span class="sxs-lookup"><span data-stu-id="1dcf6-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="1dcf6-128">ExpressionBinding-element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="1dcf6-128">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="1dcf6-129">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="1dcf6-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
