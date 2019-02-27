---
title: CustomControlName Element för ExpressionBinding för kontroller för att visa (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4b6ee11e-9086-41d2-afd3-42fb9f24da69
caps.latest.revision: 7
ms.openlocfilehash: bf1d57447f9018f1535af14466427aaeabc048f3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846531"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="dbf09-102">CustomControlName-element för ExpressionBinding för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="dbf09-102">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="dbf09-103">Anger namnet på en gemensam kontroll eller en kontroll.</span><span class="sxs-lookup"><span data-stu-id="dbf09-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="dbf09-104">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="dbf09-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="dbf09-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) kontroller Element (Format) kontroll konfigurationselement för kontroller för att visa (Format) anpassad kontroll Element för kontroll för kontroller för att visa (Format) CustomEntries Element för Anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för kontroller för att visa (Format) CustomItem Element för CustomEntry för kontroller för att visa (Format) ExpressionBinding Element för CustomItem för kontroller för att visa (Format) CustomControlName Element för ExpressionBindine för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="dbf09-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) CustomControlName Element for ExpressionBindine for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dbf09-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="dbf09-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dbf09-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="dbf09-107">Attributes and Elements</span></span>

<span data-ttu-id="dbf09-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `CustomControlName` element.</span><span class="sxs-lookup"><span data-stu-id="dbf09-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dbf09-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="dbf09-109">Attributes</span></span>

<span data-ttu-id="dbf09-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="dbf09-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dbf09-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="dbf09-111">Child Elements</span></span>

<span data-ttu-id="dbf09-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="dbf09-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="dbf09-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="dbf09-113">Parent Elements</span></span>

|<span data-ttu-id="dbf09-114">Element</span><span class="sxs-lookup"><span data-stu-id="dbf09-114">Element</span></span>|<span data-ttu-id="dbf09-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="dbf09-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dbf09-116">ExpressionBinding Element för CustomItem för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="dbf09-116">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="dbf09-117">Definierar de data som visas i kontrollen.</span><span class="sxs-lookup"><span data-stu-id="dbf09-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="dbf09-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="dbf09-118">Text Value</span></span>

<span data-ttu-id="dbf09-119">Ange namnet på kontrollen.</span><span class="sxs-lookup"><span data-stu-id="dbf09-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="dbf09-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="dbf09-120">Remarks</span></span>

<span data-ttu-id="dbf09-121">Du kan skapa vanliga kontroller som kan användas av alla vyer av en formatering fil och du kan skapa vyn kontroller som kan användas av en specifik vy.</span><span class="sxs-lookup"><span data-stu-id="dbf09-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="dbf09-122">Följande element ange namnen på de här kontrollerna:</span><span class="sxs-lookup"><span data-stu-id="dbf09-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="dbf09-123">Namnelement för kontroll för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="dbf09-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="dbf09-124">Namnelement för kontroll för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="dbf09-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="dbf09-125">Se även</span><span class="sxs-lookup"><span data-stu-id="dbf09-125">See Also</span></span>

[<span data-ttu-id="dbf09-126">Namnelement för kontroll för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="dbf09-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="dbf09-127">Namnelement för kontroll för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="dbf09-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="dbf09-128">ExpressionBinding Element för CustomItem för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="dbf09-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="dbf09-129">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="dbf09-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
