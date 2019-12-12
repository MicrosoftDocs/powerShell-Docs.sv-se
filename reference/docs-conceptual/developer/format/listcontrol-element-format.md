---
title: ListControl-element (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37beeb0b-7a81-4747-becb-e309e17278fb
caps.latest.revision: 12
ms.openlocfilehash: 7a117c25b0d117dc846ba8e060e31e838b5edd52
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354371"
---
# <a name="listcontrol-element-format"></a><span data-ttu-id="38052-102">ListControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="38052-102">ListControl Element (Format)</span></span>

<span data-ttu-id="38052-103">Definierar ett List format för vyn.</span><span class="sxs-lookup"><span data-stu-id="38052-103">Defines a list format for the view.</span></span>

<span data-ttu-id="38052-104">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) ListControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="38052-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="38052-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="38052-105">Syntax</span></span>

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="38052-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="38052-106">Attributes and Elements</span></span>

<span data-ttu-id="38052-107">I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `ListControl`-elementet.</span><span class="sxs-lookup"><span data-stu-id="38052-107">The following sections describe the attributes, child elements, and the parent element of the `ListControl` element.</span></span> <span data-ttu-id="38052-108">Det här elementet får bara innehålla ett enda underordnat element.</span><span class="sxs-lookup"><span data-stu-id="38052-108">This element must contain only a single child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="38052-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="38052-109">Attributes</span></span>

<span data-ttu-id="38052-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="38052-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="38052-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="38052-111">Child Elements</span></span>

|<span data-ttu-id="38052-112">Element</span><span class="sxs-lookup"><span data-stu-id="38052-112">Element</span></span>|<span data-ttu-id="38052-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="38052-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="38052-114">ListEntries-element (format)</span><span class="sxs-lookup"><span data-stu-id="38052-114">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="38052-115">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="38052-115">Required element.</span></span><br /><br /> <span data-ttu-id="38052-116">Innehåller definitionerna för listvyn.</span><span class="sxs-lookup"><span data-stu-id="38052-116">Provides the definitions of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="38052-117">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="38052-117">Parent Elements</span></span>

|<span data-ttu-id="38052-118">Element</span><span class="sxs-lookup"><span data-stu-id="38052-118">Element</span></span>|<span data-ttu-id="38052-119">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="38052-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="38052-120">Visa element (format)</span><span class="sxs-lookup"><span data-stu-id="38052-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="38052-121">Definierar en vy som används för att visa medlemmar i ett eller flera objekt.</span><span class="sxs-lookup"><span data-stu-id="38052-121">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="38052-122">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="38052-122">Remarks</span></span>

<span data-ttu-id="38052-123">Mer information om hur du skapar en listvy finns i [skapa en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="38052-123">For more information about creating a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="38052-124">Exempel</span><span class="sxs-lookup"><span data-stu-id="38052-124">Example</span></span>

<span data-ttu-id="38052-125">I det här exemplet visas en listvy för objektet [system. serviceprocess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="38052-125">This example shows a list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>...</ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="38052-126">Se även</span><span class="sxs-lookup"><span data-stu-id="38052-126">See Also</span></span>

[<span data-ttu-id="38052-127">Visa element (format)</span><span class="sxs-lookup"><span data-stu-id="38052-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="38052-128">ListEntries-element (format)</span><span class="sxs-lookup"><span data-stu-id="38052-128">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="38052-129">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="38052-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="38052-130">Skriva en Windows PowerShell-formatering och en typ fil</span><span class="sxs-lookup"><span data-stu-id="38052-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
