---
title: AutoSize-element för WideControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: def37479-7b6e-40cf-bc81-0f7cbc651b31
caps.latest.revision: 11
ms.openlocfilehash: 6dbaef5886a0600bd9fe96dbc8d21f00a674dfcf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359102"
---
# <a name="autosize-element-for-widecontrol-format"></a><span data-ttu-id="de052-102">AutoSize-element för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="de052-102">AutoSize Element for WideControl (Format)</span></span>

<span data-ttu-id="de052-103">Anger om kolumn storleken och antalet kolumner justeras baserat på data storleken.</span><span class="sxs-lookup"><span data-stu-id="de052-103">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>

<span data-ttu-id="de052-104">Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) element för AutoSize för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="de052-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) Autosize Element for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="de052-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="de052-105">Syntax</span></span>

```xml
<AutoSize/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="de052-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="de052-106">Attributes and Elements</span></span>

<span data-ttu-id="de052-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `AutoSize`-elementet.</span><span class="sxs-lookup"><span data-stu-id="de052-107">The following sections describe attributes, child elements, and the parent element of the `AutoSize` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="de052-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="de052-108">Attributes</span></span>

<span data-ttu-id="de052-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="de052-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="de052-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="de052-110">Child Elements</span></span>

<span data-ttu-id="de052-111">Inga</span><span class="sxs-lookup"><span data-stu-id="de052-111">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="de052-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="de052-112">Parent Elements</span></span>

|<span data-ttu-id="de052-113">Element</span><span class="sxs-lookup"><span data-stu-id="de052-113">Element</span></span>|<span data-ttu-id="de052-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="de052-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="de052-115">WideControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="de052-115">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="de052-116">Definierar ett brett List format (enskilt värde) för vyn.</span><span class="sxs-lookup"><span data-stu-id="de052-116">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="de052-117">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="de052-117">Remarks</span></span>

<span data-ttu-id="de052-118">När du definierar en bred vy kan du lägga till `AutoSize`-elementet eller [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) -elementet, men du kan inte lägga till båda.</span><span class="sxs-lookup"><span data-stu-id="de052-118">When defining a wide view, you can add the `AutoSize` element or the [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element, but you cannot add both.</span></span>

<span data-ttu-id="de052-119">Mer information om komponenterna i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="de052-119">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="de052-120">Ett exempel på en bred vy finns i [wide View (grundläggande)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="de052-120">For an example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="de052-121">Se även</span><span class="sxs-lookup"><span data-stu-id="de052-121">See Also</span></span>

[<span data-ttu-id="de052-122">ColumnNumber-element för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="de052-122">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="de052-123">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="de052-123">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="de052-124">WideControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="de052-124">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="de052-125">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="de052-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
