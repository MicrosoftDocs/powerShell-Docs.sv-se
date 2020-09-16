---
title: CustomControlName-element för ExpressionBinding for GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 06e612b25accf81467108ca48500943153efd575
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786007"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="8ced5-102">CustomControlName-element för ExpressionBinding för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="8ced5-102">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="8ced5-103">Anger namnet på en gemensam kontroll eller en visnings kontroll.</span><span class="sxs-lookup"><span data-stu-id="8ced5-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="8ced5-104">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="8ced5-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="8ced5-105">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element for CustomControl for groupby (format) CustomItem-element för CustomEntry (format) ExpressionBinding element for CustomItem för groupby (format) CustomControlName element for ExpressionBinding</span><span class="sxs-lookup"><span data-stu-id="8ced5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8ced5-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="8ced5-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8ced5-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="8ced5-107">Attributes and Elements</span></span>

<span data-ttu-id="8ced5-108">I följande avsnitt beskrivs attribut, underordnade element och `CustomControlName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="8ced5-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8ced5-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="8ced5-109">Attributes</span></span>

<span data-ttu-id="8ced5-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="8ced5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8ced5-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="8ced5-111">Child Elements</span></span>

<span data-ttu-id="8ced5-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="8ced5-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8ced5-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="8ced5-113">Parent Elements</span></span>

|<span data-ttu-id="8ced5-114">Element</span><span class="sxs-lookup"><span data-stu-id="8ced5-114">Element</span></span>|<span data-ttu-id="8ced5-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8ced5-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8ced5-116">ExpressionBinding-element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="8ced5-116">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="8ced5-117">Definierar de data som visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="8ced5-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8ced5-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="8ced5-118">Text Value</span></span>

<span data-ttu-id="8ced5-119">Ange namnet på kontrollen.</span><span class="sxs-lookup"><span data-stu-id="8ced5-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="8ced5-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="8ced5-120">Remarks</span></span>

<span data-ttu-id="8ced5-121">Du kan skapa vanliga kontroller som kan användas av alla vyer i en fil format och du kan skapa visnings kontroller som kan användas av en speciell vy.</span><span class="sxs-lookup"><span data-stu-id="8ced5-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="8ced5-122">Följande element anger namnen på dessa kontroller:</span><span class="sxs-lookup"><span data-stu-id="8ced5-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="8ced5-123">Name-element för Control för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="8ced5-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="8ced5-124">Name-element för Control för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="8ced5-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="8ced5-125">Se även</span><span class="sxs-lookup"><span data-stu-id="8ced5-125">See Also</span></span>

[<span data-ttu-id="8ced5-126">Name-element för Control för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="8ced5-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="8ced5-127">Name-element för Control för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="8ced5-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="8ced5-128">ExpressionBinding-element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="8ced5-128">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="8ced5-129">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="8ced5-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
