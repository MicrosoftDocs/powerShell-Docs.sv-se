---
title: SelectionSetName Element för ViewSelectedBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848449"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a><span data-ttu-id="60c8b-102">SelectionSetName-element för ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="60c8b-102">SelectionSetName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="60c8b-103">Anger en uppsättning med .NET-objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="60c8b-103">Specifies a set of .NET objects that are displayed by the view.</span></span>

<span data-ttu-id="60c8b-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ViewSelectedBy Element (Format) SelectionSetName konfigurationselement för ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="60c8b-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) SelectionSetName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="60c8b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="60c8b-105">Syntax</span></span>

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="60c8b-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="60c8b-106">Attributes and Elements</span></span>

<span data-ttu-id="60c8b-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `SelectionSetName` element.</span><span class="sxs-lookup"><span data-stu-id="60c8b-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="60c8b-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="60c8b-108">Attributes</span></span>

<span data-ttu-id="60c8b-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="60c8b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="60c8b-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="60c8b-110">Child Elements</span></span>

<span data-ttu-id="60c8b-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="60c8b-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="60c8b-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="60c8b-112">Parent Elements</span></span>

|<span data-ttu-id="60c8b-113">Element</span><span class="sxs-lookup"><span data-stu-id="60c8b-113">Element</span></span>|<span data-ttu-id="60c8b-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="60c8b-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="60c8b-115">ViewSelectedBy Element (Format)</span><span class="sxs-lookup"><span data-stu-id="60c8b-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="60c8b-116">Definierar de .NET-objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="60c8b-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="60c8b-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="60c8b-117">Text Value</span></span>

<span data-ttu-id="60c8b-118">Ange namnet på val av uppsättningen som definieras av den `Name` element för val av.</span><span class="sxs-lookup"><span data-stu-id="60c8b-118">Specify the name of the selection set that is defined by the `Name` element for the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="60c8b-119">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="60c8b-119">Remarks</span></span>

<span data-ttu-id="60c8b-120">Du kan använda inställningarna när du har en uppsättning relaterade objekt som du vill referera till med hjälp av ett enda namn, till exempel en uppsättning objekt som är relaterade genom arv.</span><span class="sxs-lookup"><span data-stu-id="60c8b-120">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="60c8b-121">Läs mer om hur du definierar och referera till val av uppsättningar [definiera anger av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="60c8b-121">For more information about defining and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="60c8b-122">Exempel</span><span class="sxs-lookup"><span data-stu-id="60c8b-122">Example</span></span>

<span data-ttu-id="60c8b-123">I följande exempel visas hur du anger ett urval som angetts för en listvy.</span><span class="sxs-lookup"><span data-stu-id="60c8b-123">The following example shows how to specify a selection set for a list view.</span></span> <span data-ttu-id="60c8b-124">Samma schema används för tabellen, bred och anpassade vyer.</span><span class="sxs-lookup"><span data-stu-id="60c8b-124">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="60c8b-125">Se även</span><span class="sxs-lookup"><span data-stu-id="60c8b-125">See Also</span></span>

[<span data-ttu-id="60c8b-126">Definiera inställningarna</span><span class="sxs-lookup"><span data-stu-id="60c8b-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="60c8b-127">ViewSelectedBy Element (Format)</span><span class="sxs-lookup"><span data-stu-id="60c8b-127">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="60c8b-128">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="60c8b-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
