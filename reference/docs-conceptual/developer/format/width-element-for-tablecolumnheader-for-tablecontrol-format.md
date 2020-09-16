---
title: Bredd element för TableColumnHeader för TableControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e9540d3d351041ad7cb98a21bb360ebea7eca117
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779921"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="6ff16-102">Width-element för TableColumnHeader för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="6ff16-102">Width Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="6ff16-103">Definierar bredden (i tecken) för en kolumn.</span><span class="sxs-lookup"><span data-stu-id="6ff16-103">Defines the width (in characters) of a column.</span></span>

<span data-ttu-id="6ff16-104">Konfigurations element (format) ViewDefinitions element (format) View-element (format) TableControl element (format) TableHeaders-element för TableControl (format) TableColumnHeader element TableHeaders för TableControl (format) width-element för TableColumnHeader (format)</span><span class="sxs-lookup"><span data-stu-id="6ff16-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element TableHeaders for TableControl (Format) Width Element for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6ff16-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6ff16-105">Syntax</span></span>

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6ff16-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="6ff16-106">Attributes and Elements</span></span>

<span data-ttu-id="6ff16-107">I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet för det `Width` element som används när kolumn rubriker definieras.</span><span class="sxs-lookup"><span data-stu-id="6ff16-107">The following sections describe the attributes, child elements, and parent element of the `Width` element used when defining column headers.</span></span>

### <a name="attributes"></a><span data-ttu-id="6ff16-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="6ff16-108">Attributes</span></span>

<span data-ttu-id="6ff16-109">Inga.</span><span class="sxs-lookup"><span data-stu-id="6ff16-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6ff16-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="6ff16-110">Child Elements</span></span>

<span data-ttu-id="6ff16-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="6ff16-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6ff16-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="6ff16-112">Parent Elements</span></span>

|<span data-ttu-id="6ff16-113">Element</span><span class="sxs-lookup"><span data-stu-id="6ff16-113">Element</span></span>|<span data-ttu-id="6ff16-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6ff16-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6ff16-115">TableColumnHeader-element för TableHeaders för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="6ff16-115">TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="6ff16-116">Definierar en etikett, bredd och justering för data i en kolumn i tabellen.</span><span class="sxs-lookup"><span data-stu-id="6ff16-116">Defines a label, width, and alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6ff16-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="6ff16-117">Text Value</span></span>

<span data-ttu-id="6ff16-118">När som helst kan du ange en bredd (i tecken) som är större än längden på de visade egenskapsvärdena.</span><span class="sxs-lookup"><span data-stu-id="6ff16-118">When at all possible, specify a width (in characters) that is greater than the length of the displayed property values.</span></span>

## <a name="remarks"></a><span data-ttu-id="6ff16-119">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="6ff16-119">Remarks</span></span>

<span data-ttu-id="6ff16-120">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="6ff16-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="6ff16-121">Exempel</span><span class="sxs-lookup"><span data-stu-id="6ff16-121">Example</span></span>

<span data-ttu-id="6ff16-122">I följande exempel visas ett `TableColumnHeader` element vars bredd är 16 tecken.</span><span class="sxs-lookup"><span data-stu-id="6ff16-122">The following example shows a `TableColumnHeader` element whose width is 16 characters.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="6ff16-123">Se även</span><span class="sxs-lookup"><span data-stu-id="6ff16-123">See Also</span></span>

[<span data-ttu-id="6ff16-124">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="6ff16-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="6ff16-125">TableColumnHeader-element för TableHeader för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="6ff16-125">TableColumnHeader Element for TableHeader for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="6ff16-126">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="6ff16-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
