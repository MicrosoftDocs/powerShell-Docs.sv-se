---
title: Namn element för kontroll för vy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26437467-d578-4e8d-8cdd-17dfe644957a
caps.latest.revision: 7
ms.openlocfilehash: 7e24aa60f7abae5768707d2527826c452b709002
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355995"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a><span data-ttu-id="79293-102">Name-element för Control för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="79293-102">Name Element for Control for Controls for View (Format)</span></span>

<span data-ttu-id="79293-103">Anger kontrollens namn.</span><span class="sxs-lookup"><span data-stu-id="79293-103">Specifies the name of the control.</span></span>

<span data-ttu-id="79293-104">Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) styr element för att visa (format)-elementet för kontroll av visnings namn (format)</span><span class="sxs-lookup"><span data-stu-id="79293-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) Name Element for Control for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="79293-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="79293-105">Syntax</span></span>

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="79293-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="79293-106">Attributes and Elements</span></span>

<span data-ttu-id="79293-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `Name`-elementet.</span><span class="sxs-lookup"><span data-stu-id="79293-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="79293-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="79293-108">Attributes</span></span>

<span data-ttu-id="79293-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="79293-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="79293-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="79293-110">Child Elements</span></span>

<span data-ttu-id="79293-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="79293-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="79293-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="79293-112">Parent Elements</span></span>

|<span data-ttu-id="79293-113">Element</span><span class="sxs-lookup"><span data-stu-id="79293-113">Element</span></span>|<span data-ttu-id="79293-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="79293-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="79293-115">Kontroll element för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="79293-115">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)|<span data-ttu-id="79293-116">Definierar en kontroll som kan användas av vyn och det namn som används för att referera till kontrollen.</span><span class="sxs-lookup"><span data-stu-id="79293-116">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="79293-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="79293-117">Text Value</span></span>

<span data-ttu-id="79293-118">Ange det namn som ska användas för att referera till kontrollen.</span><span class="sxs-lookup"><span data-stu-id="79293-118">Specify the name that is used to reference the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="79293-119">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="79293-119">Remarks</span></span>

<span data-ttu-id="79293-120">Namnet som anges här kan användas i följande element för att referera till den här kontrollen.</span><span class="sxs-lookup"><span data-stu-id="79293-120">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="79293-121">När du skapar en tabell, lista, bred eller anpassad flikkontroll, kan kontrollen anges med följande element: [groupby-element för vy (format)](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="79293-121">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="79293-122">När du skapar en annan kontroll som kan användas av en vy, kan den här kontrollen anges av följande element: [ExpressionBinding-element för CustomItem för kontroller för visning (format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="79293-122">When creating another control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="79293-123">Se även</span><span class="sxs-lookup"><span data-stu-id="79293-123">See Also</span></span>

[<span data-ttu-id="79293-124">GroupBy-element för vy (format)</span><span class="sxs-lookup"><span data-stu-id="79293-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="79293-125">ExpressionBinding-element för CustomItem för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="79293-125">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="79293-126">Kontroll element för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="79293-126">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)

[<span data-ttu-id="79293-127">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="79293-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
