---
title: Anpassad formatering filer | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 85d27545-8097-4010-9947-6d8b3ce2eac0
caps.latest.revision: 15
ms.openlocfilehash: 71c1c181058c5646c817b90d9832976a78c6c7de
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850038"
---
# <a name="custom-formatting-files"></a><span data-ttu-id="92948-102">Anpassade formateringsfiler</span><span class="sxs-lookup"><span data-stu-id="92948-102">Custom Formatting Files</span></span>

<span data-ttu-id="92948-103">Visningsformatet för objekten som returneras av cmdlet: ar, funktioner och skript definieras med hjälp av formatering (filer format.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="92948-103">The display format for the objects returned by cmdlets, functions, and scripts are defined using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="92948-104">Flera av de här filerna tillhandahålls av Windows PowerShell för att definiera visningsformat standard för de objekt som returneras av Windows PowerShell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="92948-104">Several of these files are provided by Windows PowerShell to define the default display format for those objects returned by Windows PowerShell cmdlets.</span></span> <span data-ttu-id="92948-105">Du kan också skapa dina egna anpassade formatering filer att skriva över format som standard visas eller för att definiera visningen av objekten som returneras av dina egna kommandon.</span><span class="sxs-lookup"><span data-stu-id="92948-105">However, you can also create your own custom formatting files to overwrite the default display formats or to define the display of objects returned by your own commands.</span></span>

<span data-ttu-id="92948-106">Windows PowerShell använder data i dessa formatering filer för att avgöra vad som visas och hur informationen har formaterats.</span><span class="sxs-lookup"><span data-stu-id="92948-106">Windows PowerShell uses the data in these formatting files to determine what is displayed and how the data is formatted.</span></span> <span data-ttu-id="92948-107">Data som visas kan innehålla egenskaperna för ett objekt eller värdet för ett skriptblock.</span><span class="sxs-lookup"><span data-stu-id="92948-107">The displayed data can include the properties of an object or the value of a script block.</span></span>  <span data-ttu-id="92948-108">Skriptblocken används om du vill visa ett värde som inte är tillgänglig direkt från egenskaperna för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="92948-108">Script blocks are used if you want to display some value that is not available directly from the properties of an object.</span></span> <span data-ttu-id="92948-109">Du kanske vill lägga till värdet för två egenskaper för ett objekt och visa summan som en separat del av data.</span><span class="sxs-lookup"><span data-stu-id="92948-109">For example, you may want to add the value of two properties of an object and display the sum as a separate piece of data.</span></span> <span data-ttu-id="92948-110">När du skriver din egen formatering fil du behöver definiera *vyer* för de objekt som du vill visa.</span><span class="sxs-lookup"><span data-stu-id="92948-110">When you write your own formatting file, you will need to define *views* for the objects that you want to display.</span></span> <span data-ttu-id="92948-111">Du kan definiera en vy för varje objekt, kan du definiera en vy för flera objekt eller du kan definiera flera vyer för samma objekt.</span><span class="sxs-lookup"><span data-stu-id="92948-111">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="92948-112">Det finns ingen gräns för antal vyer som du kan definiera.</span><span class="sxs-lookup"><span data-stu-id="92948-112">There is no limit to the number of views that you can define.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="92948-113">Formatering filer styr inte den del av ett objekt som returneras till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="92948-113">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="92948-114">Alla medlemmar i objektet är tillgängliga när ett objekt returneras till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="92948-114">When an object is returned to the pipeline, all members of that object are available.</span></span>

## <a name="format-views"></a><span data-ttu-id="92948-115">Formatet vyer</span><span class="sxs-lookup"><span data-stu-id="92948-115">Format Views</span></span>

<span data-ttu-id="92948-116">Formatering vyer kan visa objekt i ett tabellformat, ett listformat, ett brett format och ett anpassat format.</span><span class="sxs-lookup"><span data-stu-id="92948-116">Formatting views can display objects in a table format, a list format, a wide format, and a custom format.</span></span> <span data-ttu-id="92948-117">För det mesta beskrivs varje formatering definition av en uppsättning XML-taggar som beskriver en vy.</span><span class="sxs-lookup"><span data-stu-id="92948-117">For the most part, each formatting definition is described by a set of XML tags that describe a view.</span></span> <span data-ttu-id="92948-118">Varje vy innehåller namnet på vyn objekt som använder vyn och element i vyn, till exempel kolumn- och information för en tabellvy.</span><span class="sxs-lookup"><span data-stu-id="92948-118">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="92948-119">Följande vyer är tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="92948-119">The following views are available.</span></span>

<span data-ttu-id="92948-120">Tabellvy visas egenskaperna för ett objekt eller ett skript block värde i en eller flera kolumner.</span><span class="sxs-lookup"><span data-stu-id="92948-120">Table view Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="92948-121">Varje kolumn representerar en egenskap för objektet eller ett skript block-värde.</span><span class="sxs-lookup"><span data-stu-id="92948-121">Each column represents a property of the object or a script block value.</span></span> <span data-ttu-id="92948-122">Du kan definiera en tabellvy som visar alla egenskaper för ett objekt, en delmängd av egenskaperna för ett objekt eller en kombination av egenskaper och värden för skript-block.</span><span class="sxs-lookup"><span data-stu-id="92948-122">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script block values.</span></span> <span data-ttu-id="92948-123">Varje rad i tabellen representerar en returnerade objektet.</span><span class="sxs-lookup"><span data-stu-id="92948-123">Each row of the table represents a returned object.</span></span> <span data-ttu-id="92948-124">Mer information om den här vyn finns i [tabellvy](../format/creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="92948-124">For more information about this view, see [Table View](../format/creating-a-table-view.md).</span></span>

<span data-ttu-id="92948-125">Listvyn visas egenskaperna för ett objekt eller ett skript block värde i en enda kolumn.</span><span class="sxs-lookup"><span data-stu-id="92948-125">List view Lists the properties of an object or a script block value in a single column.</span></span> <span data-ttu-id="92948-126">Varje rad i listan visar en valfri etikett eller egenskapens namn följt av värdet för den egenskapen eller skript.</span><span class="sxs-lookup"><span data-stu-id="92948-126">Each row of the list displays an optional label or the property name followed by the value of the property or script block.</span></span> <span data-ttu-id="92948-127">Mer information om den här vyn finns i [listvyn](../format/creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="92948-127">For more information about this view, see [List View](../format/creating-a-list-view.md).</span></span>

<span data-ttu-id="92948-128">Bred vy innehåller en enda egenskap för ett objekt eller ett skript block värde i en eller flera kolumner.</span><span class="sxs-lookup"><span data-stu-id="92948-128">Wide view Lists a single property of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="92948-129">Det finns ingen etikett eller rubrik för den här vyn.</span><span class="sxs-lookup"><span data-stu-id="92948-129">There is no label or header for this view.</span></span> <span data-ttu-id="92948-130">Mer information om den här vyn finns i [bred vy](../format/creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="92948-130">For more information about this view, see [Wide View](../format/creating-a-wide-view.md).</span></span>

<span data-ttu-id="92948-131">Anpassad vy visar en anpassningsbar objektegenskaper eller skript block värden som inte följer den fasta strukturen för tabellvyer, listvyer eller wide vyer.</span><span class="sxs-lookup"><span data-stu-id="92948-131">Custom view Displays a customizable view of object properties or script block values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="92948-132">Du kan definiera en anpassad vy för fristående eller du kan definiera en anpassad vy som används av en annan vy, till exempel en tabell eller listvy.</span><span class="sxs-lookup"><span data-stu-id="92948-132">You can define a standalone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="92948-133">Mer information om den här vyn finns i [anpassad vy](../format/creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="92948-133">For more information about this view, see [Custom View](../format/creating-custom-controls.md).</span></span>

## <a name="view-xml-elements"></a><span data-ttu-id="92948-134">Visa XML-element</span><span class="sxs-lookup"><span data-stu-id="92948-134">View XML Elements</span></span>

<span data-ttu-id="92948-135">I följande exempel visar XML-taggar som används för att definiera en tabellvy som innehåller två kolumner.</span><span class="sxs-lookup"><span data-stu-id="92948-135">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="92948-136">Den [ViewDefinitions](../format/viewdefinitions-element-format.md) elementet är elementet behållare för alla vyer som definieras i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="92948-136">The [ViewDefinitions](../format/viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="92948-137">Den [visa](../format/view-element-format.md) elementet definierar viss tabell, lista, brett eller anpassade vy.</span><span class="sxs-lookup"><span data-stu-id="92948-137">The [View](../format/view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="92948-138">I varje vy i [namn](../format/name-element-for-view-format.md) elementet anger namnet på vyn, den [ViewSelectedBy](../format/viewselectedby-element-format.md) elementet definierar de objekt som använder vyn och de olika kontrollelementen (som den `TableControl` elementet) definierar formatet för vyn.</span><span class="sxs-lookup"><span data-stu-id="92948-138">Within each view, the [Name](../format/name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](../format/viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element) define the format of the view.</span></span>

```xml
ViewDefinitions
  <View>
    <Name>Name of View</Name>
    <ViewSelectedBy>
      <TypeName>Object to display using this view</TypeName>
      <TypeName>Object to display using this view</TypeName>
    </ViewSelectedBy>
    <TableControl>
      <TableHeaders>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
      </TableHeaders>
      <TableRowEntries>
        <TableRowEntry>
          <TableColumnItems>
            <TableColumnItem>
              <PropertyName>Header for column 1</PropertyName>
            </TableColumnItem>
            <TableColumnItem>
              <PropertyName>Header for column 2</PropertyName>
            </TableColumnItem>
          </TableColumnItems>
        </TableRowEntry>
      </TableRowEntries>
    </TableControl)
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a><span data-ttu-id="92948-139">Se även</span><span class="sxs-lookup"><span data-stu-id="92948-139">See Also</span></span>

[<span data-ttu-id="92948-140">Tabellvy</span><span class="sxs-lookup"><span data-stu-id="92948-140">Table View</span></span>](../format/creating-a-table-view.md)

[<span data-ttu-id="92948-141">Listvy</span><span class="sxs-lookup"><span data-stu-id="92948-141">List View</span></span>](../format/creating-a-list-view.md)

[<span data-ttu-id="92948-142">Bred vy</span><span class="sxs-lookup"><span data-stu-id="92948-142">Wide View</span></span>](../format/creating-a-wide-view.md)

[<span data-ttu-id="92948-143">Anpassad vy</span><span class="sxs-lookup"><span data-stu-id="92948-143">Custom View</span></span>](../format/creating-custom-controls.md)

[<span data-ttu-id="92948-144">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="92948-144">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
