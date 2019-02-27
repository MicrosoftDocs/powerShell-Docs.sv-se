---
title: AutoSize-Element för WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: def37479-7b6e-40cf-bc81-0f7cbc651b31
caps.latest.revision: 11
ms.openlocfilehash: 6dbaef5886a0600bd9fe96dbc8d21f00a674dfcf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847574"
---
# <a name="autosize-element-for-widecontrol-format"></a><span data-ttu-id="575fc-102">AutoSize-element för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="575fc-102">AutoSize Element for WideControl (Format)</span></span>

<span data-ttu-id="575fc-103">Anger om kolumnstorlek och antalet kolumner justeras beroende på storleken på data.</span><span class="sxs-lookup"><span data-stu-id="575fc-103">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>

<span data-ttu-id="575fc-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) WideControl Element (Format) Autosize konfigurationselement för WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="575fc-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) Autosize Element for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="575fc-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="575fc-105">Syntax</span></span>

```xml
<AutoSize/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="575fc-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="575fc-106">Attributes and Elements</span></span>

<span data-ttu-id="575fc-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `AutoSize` element.</span><span class="sxs-lookup"><span data-stu-id="575fc-107">The following sections describe attributes, child elements, and the parent element of the `AutoSize` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="575fc-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="575fc-108">Attributes</span></span>

<span data-ttu-id="575fc-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="575fc-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="575fc-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="575fc-110">Child Elements</span></span>

<span data-ttu-id="575fc-111">Inga</span><span class="sxs-lookup"><span data-stu-id="575fc-111">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="575fc-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="575fc-112">Parent Elements</span></span>

|<span data-ttu-id="575fc-113">Element</span><span class="sxs-lookup"><span data-stu-id="575fc-113">Element</span></span>|<span data-ttu-id="575fc-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="575fc-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="575fc-115">WideControl Element (Format)</span><span class="sxs-lookup"><span data-stu-id="575fc-115">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="575fc-116">Definierar en bred (enstaka värde) listformat för vyn.</span><span class="sxs-lookup"><span data-stu-id="575fc-116">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="575fc-117">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="575fc-117">Remarks</span></span>

<span data-ttu-id="575fc-118">När du definierar en bred vy, kan du lägga till den `AutoSize` element eller [antal_kolumner anger](./columnnumber-element-for-widecontrol-format.md) element, men du kan inte lägga till båda.</span><span class="sxs-lookup"><span data-stu-id="575fc-118">When defining a wide view, you can add the `AutoSize` element or the [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element, but you cannot add both.</span></span>

<span data-ttu-id="575fc-119">Mer information om komponenter för en bred vy finns i [skapar en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="575fc-119">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="575fc-120">Ett exempel på en bred vy finns i [bred vy (grundläggande)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="575fc-120">For an example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="575fc-121">Se även</span><span class="sxs-lookup"><span data-stu-id="575fc-121">See Also</span></span>

[<span data-ttu-id="575fc-122">Antal_kolumner anger Element för WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="575fc-122">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="575fc-123">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="575fc-123">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="575fc-124">WideControl Element (Format)</span><span class="sxs-lookup"><span data-stu-id="575fc-124">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="575fc-125">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="575fc-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
