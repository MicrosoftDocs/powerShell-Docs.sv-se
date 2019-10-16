---
title: CustomControlName-element för ExpressionBinding för CustomControl för View (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355302"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a><span data-ttu-id="47141-102">CustomControlName-element för ExpressionBinding för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="47141-102">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>

<span data-ttu-id="47141-103">Anger namnet på en gemensam kontroll eller en visnings kontroll.</span><span class="sxs-lookup"><span data-stu-id="47141-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="47141-104">Det här elementet används när du definierar en anpassad kontrol vy.</span><span class="sxs-lookup"><span data-stu-id="47141-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="47141-105">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) CustomControl-element för View (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) CustomItem Element för CustomEntry för View (format) ExpressionBinding-element för CustomItem (format) CustomControlName-elementet för uttrycks bindning för CustomItem (format)</span><span class="sxs-lookup"><span data-stu-id="47141-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem (Format) CustomControlName Element for Expression Binding for CustomItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="47141-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="47141-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="47141-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="47141-107">Attributes and Elements</span></span>

<span data-ttu-id="47141-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `CustomControlName`.</span><span class="sxs-lookup"><span data-stu-id="47141-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="47141-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="47141-109">Attributes</span></span>

<span data-ttu-id="47141-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="47141-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="47141-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="47141-111">Child Elements</span></span>

<span data-ttu-id="47141-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="47141-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="47141-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="47141-113">Parent Elements</span></span>

|<span data-ttu-id="47141-114">Element</span><span class="sxs-lookup"><span data-stu-id="47141-114">Element</span></span>|<span data-ttu-id="47141-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="47141-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="47141-116">ExpressionBinding-element för CustomItem (format)</span><span class="sxs-lookup"><span data-stu-id="47141-116">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="47141-117">Definierar de data som visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="47141-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="47141-118">Text värde</span><span class="sxs-lookup"><span data-stu-id="47141-118">Text Value</span></span>

<span data-ttu-id="47141-119">Ange namnet på kontrollen.</span><span class="sxs-lookup"><span data-stu-id="47141-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="47141-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="47141-120">Remarks</span></span>

<span data-ttu-id="47141-121">Du kan skapa vanliga kontroller som kan användas av alla vyer i en fil format och du kan skapa visnings kontroller som kan användas av en speciell vy.</span><span class="sxs-lookup"><span data-stu-id="47141-121">You can create common controls that can be used by all the views of a formatting file and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="47141-122">Namnen på dessa kontroller anges med följande element.</span><span class="sxs-lookup"><span data-stu-id="47141-122">The names of these controls are specified by the following elements.</span></span>

- [<span data-ttu-id="47141-123">Namn element för kontroll för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="47141-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="47141-124">Namn element för kontroll för vy (format)</span><span class="sxs-lookup"><span data-stu-id="47141-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="47141-125">Se även</span><span class="sxs-lookup"><span data-stu-id="47141-125">See Also</span></span>

[<span data-ttu-id="47141-126">Namn element för kontroll för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="47141-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="47141-127">Namn element för kontroll för vy (format)</span><span class="sxs-lookup"><span data-stu-id="47141-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="47141-128">ExpressionBinding-element för CustomItem (format)</span><span class="sxs-lookup"><span data-stu-id="47141-128">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="47141-129">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="47141-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
