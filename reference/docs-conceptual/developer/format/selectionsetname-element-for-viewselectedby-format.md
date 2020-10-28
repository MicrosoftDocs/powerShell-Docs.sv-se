---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName-element för ViewSelectedBy (format)
description: SelectionSetName-element för ViewSelectedBy (format)
ms.openlocfilehash: a1a1816761715a138bcb3c2bd4cb9dbbb2f9cb92
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92654915"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a><span data-ttu-id="64b1a-103">SelectionSetName-element för ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="64b1a-103">SelectionSetName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="64b1a-104">Anger en uppsättning .NET-objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="64b1a-104">Specifies a set of .NET objects that are displayed by the view.</span></span>

<span data-ttu-id="64b1a-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ViewSelectedBy-element (format) element för ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="64b1a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) SelectionSetName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="64b1a-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="64b1a-106">Syntax</span></span>

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="64b1a-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="64b1a-107">Attributes and Elements</span></span>

<span data-ttu-id="64b1a-108">I följande avsnitt beskrivs attributen, underordnade element och `SelectionSetName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="64b1a-108">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="64b1a-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="64b1a-109">Attributes</span></span>

<span data-ttu-id="64b1a-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="64b1a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="64b1a-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="64b1a-111">Child Elements</span></span>

<span data-ttu-id="64b1a-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="64b1a-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="64b1a-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="64b1a-113">Parent Elements</span></span>

|<span data-ttu-id="64b1a-114">Element</span><span class="sxs-lookup"><span data-stu-id="64b1a-114">Element</span></span>|<span data-ttu-id="64b1a-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="64b1a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="64b1a-116">ViewSelectedBy-element (format)</span><span class="sxs-lookup"><span data-stu-id="64b1a-116">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="64b1a-117">Definierar de .NET-objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="64b1a-117">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="64b1a-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="64b1a-118">Text Value</span></span>

<span data-ttu-id="64b1a-119">Ange namnet på den markerings uppsättning som definieras av `Name` elementet för urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="64b1a-119">Specify the name of the selection set that is defined by the `Name` element for the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="64b1a-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="64b1a-120">Remarks</span></span>

<span data-ttu-id="64b1a-121">Du kan använda urvals uppsättningar när du har en uppsättning relaterade objekt som du vill referera till genom att använda ett enda namn, till exempel en uppsättning objekt som är relaterade till arv.</span><span class="sxs-lookup"><span data-stu-id="64b1a-121">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="64b1a-122">Mer information om hur du definierar och refererar till urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="64b1a-122">For more information about defining and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="64b1a-123">Exempel</span><span class="sxs-lookup"><span data-stu-id="64b1a-123">Example</span></span>

<span data-ttu-id="64b1a-124">I följande exempel visas hur du anger en urvals uppsättning för en listvy.</span><span class="sxs-lookup"><span data-stu-id="64b1a-124">The following example shows how to specify a selection set for a list view.</span></span> <span data-ttu-id="64b1a-125">Samma schema används för tabeller, breda och anpassade vyer.</span><span class="sxs-lookup"><span data-stu-id="64b1a-125">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="64b1a-126">Se även</span><span class="sxs-lookup"><span data-stu-id="64b1a-126">See Also</span></span>

[<span data-ttu-id="64b1a-127">Definiera valuppsättningar</span><span class="sxs-lookup"><span data-stu-id="64b1a-127">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="64b1a-128">ViewSelectedBy-element (format)</span><span class="sxs-lookup"><span data-stu-id="64b1a-128">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="64b1a-129">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="64b1a-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
