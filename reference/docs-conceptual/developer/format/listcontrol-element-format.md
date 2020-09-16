---
title: ListControl-element (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0173b9797bffcca74f1a32903686f771366ebb1b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785735"
---
# <a name="listcontrol-element-format"></a><span data-ttu-id="d83e0-102">ListControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="d83e0-102">ListControl Element (Format)</span></span>

<span data-ttu-id="d83e0-103">Definierar ett List format för vyn.</span><span class="sxs-lookup"><span data-stu-id="d83e0-103">Defines a list format for the view.</span></span>

<span data-ttu-id="d83e0-104">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) ListControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="d83e0-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d83e0-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d83e0-105">Syntax</span></span>

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="d83e0-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="d83e0-106">Attributes and Elements</span></span>

<span data-ttu-id="d83e0-107">I följande avsnitt beskrivs attributen, underordnade element och `ListControl` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="d83e0-107">The following sections describe the attributes, child elements, and the parent element of the `ListControl` element.</span></span> <span data-ttu-id="d83e0-108">Det här elementet får bara innehålla ett enda underordnat element.</span><span class="sxs-lookup"><span data-stu-id="d83e0-108">This element must contain only a single child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d83e0-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="d83e0-109">Attributes</span></span>

<span data-ttu-id="d83e0-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="d83e0-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d83e0-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="d83e0-111">Child Elements</span></span>

|<span data-ttu-id="d83e0-112">Element</span><span class="sxs-lookup"><span data-stu-id="d83e0-112">Element</span></span>|<span data-ttu-id="d83e0-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d83e0-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d83e0-114">ListEntries-element (format)</span><span class="sxs-lookup"><span data-stu-id="d83e0-114">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="d83e0-115">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="d83e0-115">Required element.</span></span><br /><br /> <span data-ttu-id="d83e0-116">Innehåller definitionerna för listvyn.</span><span class="sxs-lookup"><span data-stu-id="d83e0-116">Provides the definitions of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d83e0-117">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="d83e0-117">Parent Elements</span></span>

|<span data-ttu-id="d83e0-118">Element</span><span class="sxs-lookup"><span data-stu-id="d83e0-118">Element</span></span>|<span data-ttu-id="d83e0-119">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d83e0-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d83e0-120">View-element (format)</span><span class="sxs-lookup"><span data-stu-id="d83e0-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="d83e0-121">Definierar en vy som används för att visa medlemmar i ett eller flera objekt.</span><span class="sxs-lookup"><span data-stu-id="d83e0-121">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d83e0-122">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="d83e0-122">Remarks</span></span>

<span data-ttu-id="d83e0-123">Mer information om hur du skapar en listvy finns i [skapa en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="d83e0-123">For more information about creating a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="d83e0-124">Exempel</span><span class="sxs-lookup"><span data-stu-id="d83e0-124">Example</span></span>

<span data-ttu-id="d83e0-125">I det här exemplet visas en listvy för objektet [system. serviceprocess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="d83e0-125">This example shows a list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d83e0-126">Se även</span><span class="sxs-lookup"><span data-stu-id="d83e0-126">See Also</span></span>

[<span data-ttu-id="d83e0-127">View-element (format)</span><span class="sxs-lookup"><span data-stu-id="d83e0-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="d83e0-128">ListEntries-element (format)</span><span class="sxs-lookup"><span data-stu-id="d83e0-128">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="d83e0-129">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="d83e0-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="d83e0-130">Skriva en Windows PowerShell-formatering och en typ fil</span><span class="sxs-lookup"><span data-stu-id="d83e0-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
