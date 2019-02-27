---
title: CustomControlName Element för ExpressionBinding för anpassad kontroll för vy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849919"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a><span data-ttu-id="6616b-102">CustomControlName-element för ExpressionBinding för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="6616b-102">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>

<span data-ttu-id="6616b-103">Anger namnet på en gemensam kontroll eller en kontroll.</span><span class="sxs-lookup"><span data-stu-id="6616b-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="6616b-104">Det här elementet används när du definierar en anpassad kontroll vy.</span><span class="sxs-lookup"><span data-stu-id="6616b-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="6616b-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) anpassad kontroll konfigurationselement för Visa (Format) CustomEntries elementet för anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för CustomItem vy (Format) Element för CustomEntry för vyn (Format) ExpressionBinding elementet för CustomItem (Format) CustomControlName Element för uttrycket bindningen för CustomItem (Format)</span><span class="sxs-lookup"><span data-stu-id="6616b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem (Format) CustomControlName Element for Expression Binding for CustomItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6616b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="6616b-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6616b-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="6616b-107">Attributes and Elements</span></span>

<span data-ttu-id="6616b-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `CustomControlName` element.</span><span class="sxs-lookup"><span data-stu-id="6616b-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6616b-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="6616b-109">Attributes</span></span>

<span data-ttu-id="6616b-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="6616b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6616b-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="6616b-111">Child Elements</span></span>

<span data-ttu-id="6616b-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="6616b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6616b-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="6616b-113">Parent Elements</span></span>

|<span data-ttu-id="6616b-114">Element</span><span class="sxs-lookup"><span data-stu-id="6616b-114">Element</span></span>|<span data-ttu-id="6616b-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6616b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6616b-116">ExpressionBinding Element för CustomItem (Format)</span><span class="sxs-lookup"><span data-stu-id="6616b-116">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="6616b-117">Definierar de data som visas i kontrollen.</span><span class="sxs-lookup"><span data-stu-id="6616b-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6616b-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="6616b-118">Text Value</span></span>

<span data-ttu-id="6616b-119">Ange namnet på kontrollen.</span><span class="sxs-lookup"><span data-stu-id="6616b-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="6616b-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="6616b-120">Remarks</span></span>

<span data-ttu-id="6616b-121">Du kan skapa vanliga kontroller som kan användas av alla vyer av en formatering fil och du kan skapa vyn kontroller som kan användas av en specifik vy.</span><span class="sxs-lookup"><span data-stu-id="6616b-121">You can create common controls that can be used by all the views of a formatting file and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="6616b-122">Namnen på de här kontrollerna anges av följande element.</span><span class="sxs-lookup"><span data-stu-id="6616b-122">The names of these controls are specified by the following elements.</span></span>

- [<span data-ttu-id="6616b-123">Namnelement för kontroll för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="6616b-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="6616b-124">Namnelement för kontroll för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="6616b-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="6616b-125">Se även</span><span class="sxs-lookup"><span data-stu-id="6616b-125">See Also</span></span>

[<span data-ttu-id="6616b-126">Namnelement för kontroll för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="6616b-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="6616b-127">Namnelement för kontroll för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="6616b-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="6616b-128">ExpressionBinding Element för CustomItem (Format)</span><span class="sxs-lookup"><span data-stu-id="6616b-128">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="6616b-129">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="6616b-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
