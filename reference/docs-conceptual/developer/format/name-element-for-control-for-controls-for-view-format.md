---
title: Namn element för kontroll för vy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 109f3a40606dbe82322decf0c69d2367c75175f6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781094"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a><span data-ttu-id="a3640-102">Name-element för Control för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="a3640-102">Name Element for Control for Controls for View (Format)</span></span>

<span data-ttu-id="a3640-103">Anger kontrollens namn.</span><span class="sxs-lookup"><span data-stu-id="a3640-103">Specifies the name of the control.</span></span>

<span data-ttu-id="a3640-104">Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) styr element för att visa (format)-elementet för kontroll av visnings namn (format)</span><span class="sxs-lookup"><span data-stu-id="a3640-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) Name Element for Control for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a3640-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a3640-105">Syntax</span></span>

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a3640-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="a3640-106">Attributes and Elements</span></span>

<span data-ttu-id="a3640-107">I följande avsnitt beskrivs attribut, underordnade element och `Name` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="a3640-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a3640-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="a3640-108">Attributes</span></span>

<span data-ttu-id="a3640-109">Inga.</span><span class="sxs-lookup"><span data-stu-id="a3640-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a3640-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="a3640-110">Child Elements</span></span>

<span data-ttu-id="a3640-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="a3640-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a3640-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="a3640-112">Parent Elements</span></span>

|<span data-ttu-id="a3640-113">Element</span><span class="sxs-lookup"><span data-stu-id="a3640-113">Element</span></span>|<span data-ttu-id="a3640-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a3640-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a3640-115">Kontroll element för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="a3640-115">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)|<span data-ttu-id="a3640-116">Definierar en kontroll som kan användas av vyn och det namn som används för att referera till kontrollen.</span><span class="sxs-lookup"><span data-stu-id="a3640-116">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a3640-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="a3640-117">Text Value</span></span>

<span data-ttu-id="a3640-118">Ange det namn som ska användas för att referera till kontrollen.</span><span class="sxs-lookup"><span data-stu-id="a3640-118">Specify the name that is used to reference the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="a3640-119">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="a3640-119">Remarks</span></span>

<span data-ttu-id="a3640-120">Namnet som anges här kan användas i följande element för att referera till den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="a3640-120">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="a3640-121">När du skapar en tabell, lista, bred eller anpassad flikkontroll, kan kontrollen anges med följande element: [groupby-element för vy (format)](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="a3640-121">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="a3640-122">När du skapar en annan kontroll som kan användas av en vy, kan den här kontrollen anges av följande element: [ExpressionBinding-element för CustomItem för kontroller för visning (format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="a3640-122">When creating another control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="a3640-123">Se även</span><span class="sxs-lookup"><span data-stu-id="a3640-123">See Also</span></span>

[<span data-ttu-id="a3640-124">GroupBy-element för View (format)</span><span class="sxs-lookup"><span data-stu-id="a3640-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="a3640-125">ExpressionBinding-element för CustomItem för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="a3640-125">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="a3640-126">Kontroll element för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="a3640-126">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)

[<span data-ttu-id="a3640-127">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="a3640-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
