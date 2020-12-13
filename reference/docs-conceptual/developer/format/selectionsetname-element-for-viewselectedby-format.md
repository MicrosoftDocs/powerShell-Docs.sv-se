---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName-element för ViewSelectedBy (format)
description: SelectionSetName-element för ViewSelectedBy (format)
ms.openlocfilehash: a1a1816761715a138bcb3c2bd4cb9dbbb2f9cb92
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654915"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a><span data-ttu-id="5ce3f-103">SelectionSetName-element för ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="5ce3f-103">SelectionSetName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="5ce3f-104">Anger en uppsättning .NET-objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="5ce3f-104">Specifies a set of .NET objects that are displayed by the view.</span></span>

<span data-ttu-id="5ce3f-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ViewSelectedBy-element (format) element för ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="5ce3f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) SelectionSetName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5ce3f-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="5ce3f-106">Syntax</span></span>

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5ce3f-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="5ce3f-107">Attributes and Elements</span></span>

<span data-ttu-id="5ce3f-108">I följande avsnitt beskrivs attributen, underordnade element och `SelectionSetName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="5ce3f-108">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5ce3f-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="5ce3f-109">Attributes</span></span>

<span data-ttu-id="5ce3f-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="5ce3f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5ce3f-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="5ce3f-111">Child Elements</span></span>

<span data-ttu-id="5ce3f-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="5ce3f-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5ce3f-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="5ce3f-113">Parent Elements</span></span>

|<span data-ttu-id="5ce3f-114">Element</span><span class="sxs-lookup"><span data-stu-id="5ce3f-114">Element</span></span>|<span data-ttu-id="5ce3f-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5ce3f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5ce3f-116">ViewSelectedBy-element (format)</span><span class="sxs-lookup"><span data-stu-id="5ce3f-116">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="5ce3f-117">Definierar de .NET-objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="5ce3f-117">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5ce3f-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="5ce3f-118">Text Value</span></span>

<span data-ttu-id="5ce3f-119">Ange namnet på den markerings uppsättning som definieras av `Name` elementet för urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="5ce3f-119">Specify the name of the selection set that is defined by the `Name` element for the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="5ce3f-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="5ce3f-120">Remarks</span></span>

<span data-ttu-id="5ce3f-121">Du kan använda urvals uppsättningar när du har en uppsättning relaterade objekt som du vill referera till genom att använda ett enda namn, till exempel en uppsättning objekt som är relaterade till arv.</span><span class="sxs-lookup"><span data-stu-id="5ce3f-121">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="5ce3f-122">Mer information om hur du definierar och refererar till urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="5ce3f-122">For more information about defining and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="5ce3f-123">Exempel</span><span class="sxs-lookup"><span data-stu-id="5ce3f-123">Example</span></span>

<span data-ttu-id="5ce3f-124">I följande exempel visas hur du anger en urvals uppsättning för en listvy.</span><span class="sxs-lookup"><span data-stu-id="5ce3f-124">The following example shows how to specify a selection set for a list view.</span></span> <span data-ttu-id="5ce3f-125">Samma schema används för tabeller, breda och anpassade vyer.</span><span class="sxs-lookup"><span data-stu-id="5ce3f-125">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="5ce3f-126">Se även</span><span class="sxs-lookup"><span data-stu-id="5ce3f-126">See Also</span></span>

[<span data-ttu-id="5ce3f-127">Definiera valuppsättningar</span><span class="sxs-lookup"><span data-stu-id="5ce3f-127">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="5ce3f-128">ViewSelectedBy-element (format)</span><span class="sxs-lookup"><span data-stu-id="5ce3f-128">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="5ce3f-129">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="5ce3f-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
