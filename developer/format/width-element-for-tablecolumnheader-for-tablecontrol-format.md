---
title: Bredd-Element för TableColumnHeader för TableControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94eb0535-8002-4f17-9a2b-4be75ec20e5c
caps.latest.revision: 18
ms.openlocfilehash: 4a25c9d81df670dc10955065bfb66766cdb1bd33
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083628"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="9afc1-102">Width-element för TableColumnHeader för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="9afc1-102">Width Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="9afc1-103">Anger bredden (i antal tecken) för en kolumn.</span><span class="sxs-lookup"><span data-stu-id="9afc1-103">Defines the width (in characters) of a column.</span></span>

<span data-ttu-id="9afc1-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableHeaders konfigurationselement för TableControl (Format) TableColumnHeader elementet TableHeaders för TableControl (Format) bredd-elementet för TableColumnHeader för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="9afc1-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element TableHeaders for TableControl (Format) Width Element for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9afc1-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9afc1-105">Syntax</span></span>

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9afc1-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="9afc1-106">Attributes and Elements</span></span>

<span data-ttu-id="9afc1-107">I följande avsnitt beskrivs de attribut och underordnade element överordnade elementet i den `Width` element som används när du definierar kolumnrubriker.</span><span class="sxs-lookup"><span data-stu-id="9afc1-107">The following sections describe the attributes, child elements, and parent element of the `Width` element used when defining column headers.</span></span>

### <a name="attributes"></a><span data-ttu-id="9afc1-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="9afc1-108">Attributes</span></span>

<span data-ttu-id="9afc1-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="9afc1-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9afc1-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="9afc1-110">Child Elements</span></span>

<span data-ttu-id="9afc1-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="9afc1-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9afc1-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="9afc1-112">Parent Elements</span></span>

|<span data-ttu-id="9afc1-113">Element</span><span class="sxs-lookup"><span data-stu-id="9afc1-113">Element</span></span>|<span data-ttu-id="9afc1-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="9afc1-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9afc1-115">TableColumnHeader Element för TableHeaders för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="9afc1-115">TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="9afc1-116">Definierar en etikett, bredd och justering av data för en kolumn i tabellen.</span><span class="sxs-lookup"><span data-stu-id="9afc1-116">Defines a label, width, and alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9afc1-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="9afc1-117">Text Value</span></span>

<span data-ttu-id="9afc1-118">Ange en bredd (i antal tecken) som är större än längden på de visade egenskapsvärdena när de är på alla möjliga.</span><span class="sxs-lookup"><span data-stu-id="9afc1-118">When at all possible, specify a width (in characters) that is greater than the length of the displayed property values.</span></span>

## <a name="remarks"></a><span data-ttu-id="9afc1-119">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="9afc1-119">Remarks</span></span>

<span data-ttu-id="9afc1-120">Läs mer om komponenterna i en tabellvy, [skapar en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="9afc1-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="9afc1-121">Exempel</span><span class="sxs-lookup"><span data-stu-id="9afc1-121">Example</span></span>

<span data-ttu-id="9afc1-122">I följande exempel visas en `TableColumnHeader` element vars bredd är 16 tecken.</span><span class="sxs-lookup"><span data-stu-id="9afc1-122">The following example shows a `TableColumnHeader` element whose width is 16 characters.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="9afc1-123">Se även</span><span class="sxs-lookup"><span data-stu-id="9afc1-123">See Also</span></span>

[<span data-ttu-id="9afc1-124">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="9afc1-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="9afc1-125">TableColumnHeader Element för TableHeader för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="9afc1-125">TableColumnHeader Element for TableHeader for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="9afc1-126">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="9afc1-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
