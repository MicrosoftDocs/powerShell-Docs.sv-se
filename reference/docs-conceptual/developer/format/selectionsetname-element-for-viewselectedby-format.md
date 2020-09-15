---
title: SelectionSetName-element för ViewSelectedBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: f6410b463bcb00d2758849c2f7e13cd839277e50
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772611"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a><span data-ttu-id="c629e-102">SelectionSetName-element för ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="c629e-102">SelectionSetName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="c629e-103">Anger en uppsättning .NET-objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="c629e-103">Specifies a set of .NET objects that are displayed by the view.</span></span>

<span data-ttu-id="c629e-104">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ViewSelectedBy-element (format) element för ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="c629e-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) SelectionSetName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c629e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c629e-105">Syntax</span></span>

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c629e-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="c629e-106">Attributes and Elements</span></span>

<span data-ttu-id="c629e-107">I följande avsnitt beskrivs attributen, underordnade element och `SelectionSetName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="c629e-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c629e-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="c629e-108">Attributes</span></span>

<span data-ttu-id="c629e-109">Inga.</span><span class="sxs-lookup"><span data-stu-id="c629e-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c629e-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="c629e-110">Child Elements</span></span>

<span data-ttu-id="c629e-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="c629e-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c629e-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="c629e-112">Parent Elements</span></span>

|<span data-ttu-id="c629e-113">Element</span><span class="sxs-lookup"><span data-stu-id="c629e-113">Element</span></span>|<span data-ttu-id="c629e-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c629e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c629e-115">ViewSelectedBy-element (format)</span><span class="sxs-lookup"><span data-stu-id="c629e-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="c629e-116">Definierar de .NET-objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="c629e-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c629e-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="c629e-117">Text Value</span></span>

<span data-ttu-id="c629e-118">Ange namnet på den markerings uppsättning som definieras av `Name` elementet för urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="c629e-118">Specify the name of the selection set that is defined by the `Name` element for the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="c629e-119">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="c629e-119">Remarks</span></span>

<span data-ttu-id="c629e-120">Du kan använda urvals uppsättningar när du har en uppsättning relaterade objekt som du vill referera till genom att använda ett enda namn, till exempel en uppsättning objekt som är relaterade till arv.</span><span class="sxs-lookup"><span data-stu-id="c629e-120">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="c629e-121">Mer information om hur du definierar och refererar till urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="c629e-121">For more information about defining and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="c629e-122">Exempel</span><span class="sxs-lookup"><span data-stu-id="c629e-122">Example</span></span>

<span data-ttu-id="c629e-123">I följande exempel visas hur du anger en urvals uppsättning för en listvy.</span><span class="sxs-lookup"><span data-stu-id="c629e-123">The following example shows how to specify a selection set for a list view.</span></span> <span data-ttu-id="c629e-124">Samma schema används för tabeller, breda och anpassade vyer.</span><span class="sxs-lookup"><span data-stu-id="c629e-124">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="c629e-125">Se även</span><span class="sxs-lookup"><span data-stu-id="c629e-125">See Also</span></span>

[<span data-ttu-id="c629e-126">Definiera valuppsättningar</span><span class="sxs-lookup"><span data-stu-id="c629e-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="c629e-127">ViewSelectedBy-element (format)</span><span class="sxs-lookup"><span data-stu-id="c629e-127">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="c629e-128">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="c629e-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
