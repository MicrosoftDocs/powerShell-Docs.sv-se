---
title: Justerings element för TableColumnHeader för TableControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1bf395b84af90d725c14b2f0ef569f72b5fcc613
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783933"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="686e8-102">Alignment-element för TableColumnHeader för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="686e8-102">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="686e8-103">Definierar hur data i en kolumn rubrik visas.</span><span class="sxs-lookup"><span data-stu-id="686e8-103">Defines how the data in a column header is displayed.</span></span>

<span data-ttu-id="686e8-104">Konfigurations element (format) ViewDefinitions element (format) View-element (format) TableControl element (format) TableHeaders element (format) TableColumnHeader element (format) justerings element för TableColumnHeader (format)</span><span class="sxs-lookup"><span data-stu-id="686e8-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element (Format) TableColumnHeader Element (Format) Alignment Element for TableColumnHeader (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="686e8-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="686e8-105">Syntax</span></span>

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="686e8-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="686e8-106">Attributes and Elements</span></span>

<span data-ttu-id="686e8-107">I följande avsnitt beskrivs attributen, underordnade element och `Alignment` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="686e8-107">The following sections describe the attributes, child elements, and parent element of the `Alignment` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="686e8-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="686e8-108">Attributes</span></span>

<span data-ttu-id="686e8-109">Inga.</span><span class="sxs-lookup"><span data-stu-id="686e8-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="686e8-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="686e8-110">Child Elements</span></span>

<span data-ttu-id="686e8-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="686e8-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="686e8-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="686e8-112">Parent Elements</span></span>

|<span data-ttu-id="686e8-113">Element</span><span class="sxs-lookup"><span data-stu-id="686e8-113">Element</span></span>|<span data-ttu-id="686e8-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="686e8-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="686e8-115">TableColumnHeader-element (format)</span><span class="sxs-lookup"><span data-stu-id="686e8-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="686e8-116">Definierar en etikett, bredd och justering för data i en kolumn i tabellen.</span><span class="sxs-lookup"><span data-stu-id="686e8-116">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="686e8-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="686e8-117">Text Value</span></span>

<span data-ttu-id="686e8-118">Ange ett av följande värden.</span><span class="sxs-lookup"><span data-stu-id="686e8-118">Specify one of the following values.</span></span> <span data-ttu-id="686e8-119">De här värdena är inte skiftlägeskänsliga.</span><span class="sxs-lookup"><span data-stu-id="686e8-119">These values are not case-sensitive.</span></span>

<span data-ttu-id="686e8-120">Vänster justerar data som visas i kolumnen till vänster detta är standardvärdet om det här elementet inte har angetts.</span><span class="sxs-lookup"><span data-stu-id="686e8-120">Left Aligns the data displayed in the column on the left This is the default if this element is not specified.</span></span>

<span data-ttu-id="686e8-121">Högerjusterar de data som visas i kolumnen till höger.</span><span class="sxs-lookup"><span data-stu-id="686e8-121">Right Aligns the data displayed in the column on the right.</span></span>

<span data-ttu-id="686e8-122">Center centrerar de data som visas i kolumnen.</span><span class="sxs-lookup"><span data-stu-id="686e8-122">Center Centers the data displayed in the column.</span></span>

## <a name="remarks"></a><span data-ttu-id="686e8-123">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="686e8-123">Remarks</span></span>

<span data-ttu-id="686e8-124">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="686e8-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="686e8-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="686e8-125">Example</span></span>

<span data-ttu-id="686e8-126">I det här exemplet visas ett `TableColumnHeader` element vars data justeras till vänster.</span><span class="sxs-lookup"><span data-stu-id="686e8-126">This example shows a `TableColumnHeader` element whose data is aligned on the left.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="686e8-127">Se även</span><span class="sxs-lookup"><span data-stu-id="686e8-127">See Also</span></span>

[<span data-ttu-id="686e8-128">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="686e8-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="686e8-129">TableColumnHeader-element (format)</span><span class="sxs-lookup"><span data-stu-id="686e8-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="686e8-130">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="686e8-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
