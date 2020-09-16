---
title: CustomControlName-element för ExpressionBinding för CustomControl för View (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6f1ffca045b7efcecb4dce4e788a8c508fa6ef08
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783763"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a><span data-ttu-id="a2e62-102">CustomControlName-element för ExpressionBinding för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="a2e62-102">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>

<span data-ttu-id="a2e62-103">Anger namnet på en gemensam kontroll eller en visnings kontroll.</span><span class="sxs-lookup"><span data-stu-id="a2e62-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="a2e62-104">Det här elementet används när du definierar en anpassad kontrol vy.</span><span class="sxs-lookup"><span data-stu-id="a2e62-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="a2e62-105">Konfigurations element (format) ViewDefinitions-element (format) Visa element (format) CustomControl-element för View (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) CustomItem-element för CustomEntry för View (format) ExpressionBinding-element för CustomItem (format)</span><span class="sxs-lookup"><span data-stu-id="a2e62-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem (Format) CustomControlName Element for Expression Binding for CustomItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a2e62-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="a2e62-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a2e62-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="a2e62-107">Attributes and Elements</span></span>

<span data-ttu-id="a2e62-108">I följande avsnitt beskrivs attribut, underordnade element och `CustomControlName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="a2e62-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a2e62-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="a2e62-109">Attributes</span></span>

<span data-ttu-id="a2e62-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="a2e62-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a2e62-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="a2e62-111">Child Elements</span></span>

<span data-ttu-id="a2e62-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="a2e62-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a2e62-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="a2e62-113">Parent Elements</span></span>

|<span data-ttu-id="a2e62-114">Element</span><span class="sxs-lookup"><span data-stu-id="a2e62-114">Element</span></span>|<span data-ttu-id="a2e62-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a2e62-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a2e62-116">ExpressionBinding-element för CustomItem (format)</span><span class="sxs-lookup"><span data-stu-id="a2e62-116">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="a2e62-117">Definierar de data som visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="a2e62-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a2e62-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="a2e62-118">Text Value</span></span>

<span data-ttu-id="a2e62-119">Ange namnet på kontrollen.</span><span class="sxs-lookup"><span data-stu-id="a2e62-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="a2e62-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="a2e62-120">Remarks</span></span>

<span data-ttu-id="a2e62-121">Du kan skapa vanliga kontroller som kan användas av alla vyer i en fil format och du kan skapa visnings kontroller som kan användas av en speciell vy.</span><span class="sxs-lookup"><span data-stu-id="a2e62-121">You can create common controls that can be used by all the views of a formatting file and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="a2e62-122">Namnen på dessa kontroller anges med följande element.</span><span class="sxs-lookup"><span data-stu-id="a2e62-122">The names of these controls are specified by the following elements.</span></span>

- [<span data-ttu-id="a2e62-123">Name-element för Control för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="a2e62-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="a2e62-124">Name-element för Control för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="a2e62-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="a2e62-125">Se även</span><span class="sxs-lookup"><span data-stu-id="a2e62-125">See Also</span></span>

[<span data-ttu-id="a2e62-126">Name-element för Control för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="a2e62-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="a2e62-127">Name-element för Control för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="a2e62-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="a2e62-128">ExpressionBinding-element för CustomItem (format)</span><span class="sxs-lookup"><span data-stu-id="a2e62-128">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="a2e62-129">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="a2e62-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
