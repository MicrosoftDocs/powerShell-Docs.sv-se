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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358817"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a><span data-ttu-id="f3706-102">SelectionSetName-element för ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="f3706-102">SelectionSetName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="f3706-103">Anger en uppsättning .NET-objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="f3706-103">Specifies a set of .NET objects that are displayed by the view.</span></span>

<span data-ttu-id="f3706-104">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ViewSelectedBy-element (format) element för ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="f3706-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) SelectionSetName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f3706-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f3706-105">Syntax</span></span>

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f3706-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="f3706-106">Attributes and Elements</span></span>

<span data-ttu-id="f3706-107">I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `SelectionSetName`-elementet.</span><span class="sxs-lookup"><span data-stu-id="f3706-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f3706-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="f3706-108">Attributes</span></span>

<span data-ttu-id="f3706-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="f3706-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f3706-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="f3706-110">Child Elements</span></span>

<span data-ttu-id="f3706-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="f3706-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f3706-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="f3706-112">Parent Elements</span></span>

|<span data-ttu-id="f3706-113">Element</span><span class="sxs-lookup"><span data-stu-id="f3706-113">Element</span></span>|<span data-ttu-id="f3706-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f3706-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f3706-115">ViewSelectedBy-element (format)</span><span class="sxs-lookup"><span data-stu-id="f3706-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="f3706-116">Definierar de .NET-objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="f3706-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f3706-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="f3706-117">Text Value</span></span>

<span data-ttu-id="f3706-118">Ange namnet på den markerings uppsättning som definieras av `Name`-elementet för markerings uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="f3706-118">Specify the name of the selection set that is defined by the `Name` element for the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="f3706-119">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="f3706-119">Remarks</span></span>

<span data-ttu-id="f3706-120">Du kan använda urvals uppsättningar när du har en uppsättning relaterade objekt som du vill referera till genom att använda ett enda namn, till exempel en uppsättning objekt som är relaterade till arv.</span><span class="sxs-lookup"><span data-stu-id="f3706-120">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="f3706-121">Mer information om hur du definierar och refererar till urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="f3706-121">For more information about defining and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="f3706-122">Exempel</span><span class="sxs-lookup"><span data-stu-id="f3706-122">Example</span></span>

<span data-ttu-id="f3706-123">I följande exempel visas hur du anger en urvals uppsättning för en listvy.</span><span class="sxs-lookup"><span data-stu-id="f3706-123">The following example shows how to specify a selection set for a list view.</span></span> <span data-ttu-id="f3706-124">Samma schema används för tabeller, breda och anpassade vyer.</span><span class="sxs-lookup"><span data-stu-id="f3706-124">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="f3706-125">Se även</span><span class="sxs-lookup"><span data-stu-id="f3706-125">See Also</span></span>

[<span data-ttu-id="f3706-126">Definiera urvals uppsättningar</span><span class="sxs-lookup"><span data-stu-id="f3706-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="f3706-127">ViewSelectedBy-element (format)</span><span class="sxs-lookup"><span data-stu-id="f3706-127">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="f3706-128">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="f3706-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
