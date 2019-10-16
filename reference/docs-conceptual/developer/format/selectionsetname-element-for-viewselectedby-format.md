---
title: SelectionSetName-element för ViewSelectedBy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358817"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a><span data-ttu-id="ec5c2-102">SelectionSetName-element för ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="ec5c2-102">SelectionSetName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="ec5c2-103">Anger en uppsättning .NET-objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-103">Specifies a set of .NET objects that are displayed by the view.</span></span>

<span data-ttu-id="ec5c2-104">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ViewSelectedBy-element (format) element för ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="ec5c2-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) SelectionSetName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ec5c2-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ec5c2-105">Syntax</span></span>

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ec5c2-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="ec5c2-106">Attributes and Elements</span></span>

<span data-ttu-id="ec5c2-107">I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet för elementet `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ec5c2-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="ec5c2-108">Attributes</span></span>

<span data-ttu-id="ec5c2-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ec5c2-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="ec5c2-110">Child Elements</span></span>

<span data-ttu-id="ec5c2-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ec5c2-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="ec5c2-112">Parent Elements</span></span>

|<span data-ttu-id="ec5c2-113">Element</span><span class="sxs-lookup"><span data-stu-id="ec5c2-113">Element</span></span>|<span data-ttu-id="ec5c2-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ec5c2-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ec5c2-115">ViewSelectedBy-element (format)</span><span class="sxs-lookup"><span data-stu-id="ec5c2-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="ec5c2-116">Definierar de .NET-objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ec5c2-117">Text värde</span><span class="sxs-lookup"><span data-stu-id="ec5c2-117">Text Value</span></span>

<span data-ttu-id="ec5c2-118">Ange namnet på den markerings uppsättning som definieras av `Name`-elementet för urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-118">Specify the name of the selection set that is defined by the `Name` element for the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="ec5c2-119">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="ec5c2-119">Remarks</span></span>

<span data-ttu-id="ec5c2-120">Du kan använda urvals uppsättningar när du har en uppsättning relaterade objekt som du vill referera till genom att använda ett enda namn, till exempel en uppsättning objekt som är relaterade till arv.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-120">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="ec5c2-121">Mer information om hur du definierar och refererar till urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="ec5c2-121">For more information about defining and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="ec5c2-122">Exempel</span><span class="sxs-lookup"><span data-stu-id="ec5c2-122">Example</span></span>

<span data-ttu-id="ec5c2-123">I följande exempel visas hur du anger en urvals uppsättning för en listvy.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-123">The following example shows how to specify a selection set for a list view.</span></span> <span data-ttu-id="ec5c2-124">Samma schema används för tabeller, breda och anpassade vyer.</span><span class="sxs-lookup"><span data-stu-id="ec5c2-124">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="ec5c2-125">Se även</span><span class="sxs-lookup"><span data-stu-id="ec5c2-125">See Also</span></span>

[<span data-ttu-id="ec5c2-126">Definiera urvals uppsättningar</span><span class="sxs-lookup"><span data-stu-id="ec5c2-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="ec5c2-127">ViewSelectedBy-element (format)</span><span class="sxs-lookup"><span data-stu-id="ec5c2-127">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="ec5c2-128">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="ec5c2-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
