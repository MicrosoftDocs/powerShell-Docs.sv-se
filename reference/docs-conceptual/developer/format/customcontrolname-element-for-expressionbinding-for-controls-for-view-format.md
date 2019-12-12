---
title: CustomControlName-element för ExpressionBinding för kontroller för vy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4b6ee11e-9086-41d2-afd3-42fb9f24da69
caps.latest.revision: 7
ms.openlocfilehash: bf1d57447f9018f1535af14466427aaeabc048f3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359053"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="3d8f7-102">CustomControlName-element för ExpressionBinding för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="3d8f7-102">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="3d8f7-103">Anger namnet på en gemensam kontroll eller en visnings kontroll.</span><span class="sxs-lookup"><span data-stu-id="3d8f7-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="3d8f7-104">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="3d8f7-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="3d8f7-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) styr element för Controls (format) CustomControl-element för kontroll för Control for View (format) CustomEntries-element för CustomControl för visnings-(format) CustomEntry-element för CustomEntries for Controls for View (format) CustomItem-elementet for CustomEntry for Controls for View (format) ExpressionBinding element for CustomItem for Controls for View (format) CustomControlName Element för ExpressionBindine för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="3d8f7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) CustomControlName Element for ExpressionBindine for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3d8f7-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="3d8f7-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3d8f7-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="3d8f7-107">Attributes and Elements</span></span>

<span data-ttu-id="3d8f7-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `CustomControlName`-elementet.</span><span class="sxs-lookup"><span data-stu-id="3d8f7-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3d8f7-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="3d8f7-109">Attributes</span></span>

<span data-ttu-id="3d8f7-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="3d8f7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3d8f7-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="3d8f7-111">Child Elements</span></span>

<span data-ttu-id="3d8f7-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="3d8f7-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3d8f7-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="3d8f7-113">Parent Elements</span></span>

|<span data-ttu-id="3d8f7-114">Element</span><span class="sxs-lookup"><span data-stu-id="3d8f7-114">Element</span></span>|<span data-ttu-id="3d8f7-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3d8f7-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3d8f7-116">ExpressionBinding-element för CustomItem för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="3d8f7-116">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="3d8f7-117">Definierar de data som visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="3d8f7-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3d8f7-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="3d8f7-118">Text Value</span></span>

<span data-ttu-id="3d8f7-119">Ange namnet på kontrollen.</span><span class="sxs-lookup"><span data-stu-id="3d8f7-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="3d8f7-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="3d8f7-120">Remarks</span></span>

<span data-ttu-id="3d8f7-121">Du kan skapa vanliga kontroller som kan användas av alla vyer i en fil format och du kan skapa visnings kontroller som kan användas av en speciell vy.</span><span class="sxs-lookup"><span data-stu-id="3d8f7-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="3d8f7-122">Följande element anger namnen på dessa kontroller:</span><span class="sxs-lookup"><span data-stu-id="3d8f7-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="3d8f7-123">Namn element för kontroll för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="3d8f7-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="3d8f7-124">Namn element för kontroll för vy (format)</span><span class="sxs-lookup"><span data-stu-id="3d8f7-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="3d8f7-125">Se även</span><span class="sxs-lookup"><span data-stu-id="3d8f7-125">See Also</span></span>

[<span data-ttu-id="3d8f7-126">Namn element för kontroll för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="3d8f7-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="3d8f7-127">Namn element för kontroll för vy (format)</span><span class="sxs-lookup"><span data-stu-id="3d8f7-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="3d8f7-128">ExpressionBinding-element för CustomItem för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="3d8f7-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="3d8f7-129">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="3d8f7-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
