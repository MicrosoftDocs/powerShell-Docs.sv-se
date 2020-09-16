---
title: Filer för anpassad formatering | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a9633e2ee18e1817459645b4a5950ea8a622850b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784358"
---
# <a name="custom-formatting-files"></a><span data-ttu-id="34b0f-102">Anpassade formateringsfiler</span><span class="sxs-lookup"><span data-stu-id="34b0f-102">Custom Formatting Files</span></span>

<span data-ttu-id="34b0f-103">Visnings formatet för de objekt som returneras av cmdlets, Functions och scripts definieras med hjälp av formateringsattribut (format.ps1XML-filer).</span><span class="sxs-lookup"><span data-stu-id="34b0f-103">The display format for the objects returned by cmdlets, functions, and scripts are defined using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="34b0f-104">Flera av de här filerna tillhandahålls av Windows PowerShell för att definiera standard visnings formatet för de objekt som returneras av Windows PowerShell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="34b0f-104">Several of these files are provided by Windows PowerShell to define the default display format for those objects returned by Windows PowerShell cmdlets.</span></span> <span data-ttu-id="34b0f-105">Men du kan också skapa egna filer för att skriva över standard visnings formaten eller definiera visningen av objekt som returneras av dina egna kommandon.</span><span class="sxs-lookup"><span data-stu-id="34b0f-105">However, you can also create your own custom formatting files to overwrite the default display formats or to define the display of objects returned by your own commands.</span></span>

<span data-ttu-id="34b0f-106">Windows PowerShell använder datan i dessa filer för att avgöra vad som visas och hur data formateras.</span><span class="sxs-lookup"><span data-stu-id="34b0f-106">Windows PowerShell uses the data in these formatting files to determine what is displayed and how the data is formatted.</span></span> <span data-ttu-id="34b0f-107">De data som visas kan innehålla egenskaperna för ett objekt eller värdet för ett skript block.</span><span class="sxs-lookup"><span data-stu-id="34b0f-107">The displayed data can include the properties of an object or the value of a script block.</span></span>  <span data-ttu-id="34b0f-108">Skript block används om du vill visa ett värde som inte är tillgängligt direkt från egenskaperna för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="34b0f-108">Script blocks are used if you want to display some value that is not available directly from the properties of an object.</span></span> <span data-ttu-id="34b0f-109">Du kanske exempelvis vill lägga till värdet för två egenskaper för ett objekt och Visa summan som en separat del av data.</span><span class="sxs-lookup"><span data-stu-id="34b0f-109">For example, you may want to add the value of two properties of an object and display the sum as a separate piece of data.</span></span> <span data-ttu-id="34b0f-110">När du skriver din egen fil format måste du definiera *vyer* för de objekt som du vill visa.</span><span class="sxs-lookup"><span data-stu-id="34b0f-110">When you write your own formatting file, you will need to define *views* for the objects that you want to display.</span></span> <span data-ttu-id="34b0f-111">Du kan definiera en enskild vy för varje objekt, du kan definiera en enskild vy för flera objekt, eller så kan du definiera flera vyer för samma objekt.</span><span class="sxs-lookup"><span data-stu-id="34b0f-111">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="34b0f-112">Det finns ingen gräns för hur många vyer du kan definiera.</span><span class="sxs-lookup"><span data-stu-id="34b0f-112">There is no limit to the number of views that you can define.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="34b0f-113">Filer formateras inte med de element som returneras till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="34b0f-113">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="34b0f-114">När ett objekt returneras till pipelinen är alla medlemmar i objektet tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="34b0f-114">When an object is returned to the pipeline, all members of that object are available.</span></span>

## <a name="format-views"></a><span data-ttu-id="34b0f-115">Formatera vyer</span><span class="sxs-lookup"><span data-stu-id="34b0f-115">Format Views</span></span>

<span data-ttu-id="34b0f-116">Vyer för formatering kan visa objekt i tabell format, ett List format, ett brett format och ett anpassat format.</span><span class="sxs-lookup"><span data-stu-id="34b0f-116">Formatting views can display objects in a table format, a list format, a wide format, and a custom format.</span></span> <span data-ttu-id="34b0f-117">För det mesta beskrivs varje format definition av en uppsättning XML-taggar som beskriver en vy.</span><span class="sxs-lookup"><span data-stu-id="34b0f-117">For the most part, each formatting definition is described by a set of XML tags that describe a view.</span></span> <span data-ttu-id="34b0f-118">Varje vy innehåller namnet på vyn, de objekt som använder vyn och elementen i vyn, till exempel kolumn-och rad information för en tabellvy.</span><span class="sxs-lookup"><span data-stu-id="34b0f-118">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="34b0f-119">Följande vyer är tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="34b0f-119">The following views are available.</span></span>

<span data-ttu-id="34b0f-120">I Tabellvy visas egenskaperna för ett objekt eller ett skript Blocks värde i en eller flera kolumner.</span><span class="sxs-lookup"><span data-stu-id="34b0f-120">Table view Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="34b0f-121">Varje kolumn representerar en egenskap hos objektet eller ett skript Blocks värde.</span><span class="sxs-lookup"><span data-stu-id="34b0f-121">Each column represents a property of the object or a script block value.</span></span> <span data-ttu-id="34b0f-122">Du kan definiera en tabellvy som visar alla egenskaper för ett objekt, en delmängd av egenskaperna för ett objekt eller en kombination av egenskaper och skript Blocks värden.</span><span class="sxs-lookup"><span data-stu-id="34b0f-122">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script block values.</span></span> <span data-ttu-id="34b0f-123">Varje rad i tabellen representerar ett returnerat objekt.</span><span class="sxs-lookup"><span data-stu-id="34b0f-123">Each row of the table represents a returned object.</span></span> <span data-ttu-id="34b0f-124">Mer information om den här vyn finns i [tabellvy](../format/creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="34b0f-124">For more information about this view, see [Table View](../format/creating-a-table-view.md).</span></span>

<span data-ttu-id="34b0f-125">Listvy visar egenskaperna för ett objekt eller ett skript Blocks värde i en kolumn.</span><span class="sxs-lookup"><span data-stu-id="34b0f-125">List view Lists the properties of an object or a script block value in a single column.</span></span> <span data-ttu-id="34b0f-126">Varje rad i listan visar en valfri etikett eller egenskaps namnet följt av värdet för egenskapen eller skript blocket.</span><span class="sxs-lookup"><span data-stu-id="34b0f-126">Each row of the list displays an optional label or the property name followed by the value of the property or script block.</span></span> <span data-ttu-id="34b0f-127">Mer information om den här vyn finns i [listvyn](../format/creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="34b0f-127">For more information about this view, see [List View](../format/creating-a-list-view.md).</span></span>

<span data-ttu-id="34b0f-128">Wide View visar en enskild egenskap för ett objekt eller ett skript Blocks värde i en eller flera kolumner.</span><span class="sxs-lookup"><span data-stu-id="34b0f-128">Wide view Lists a single property of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="34b0f-129">Det finns ingen etikett eller rubrik för den här vyn.</span><span class="sxs-lookup"><span data-stu-id="34b0f-129">There is no label or header for this view.</span></span> <span data-ttu-id="34b0f-130">Mer information om den här vyn finns i [wide View](../format/creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="34b0f-130">For more information about this view, see [Wide View](../format/creating-a-wide-view.md).</span></span>

<span data-ttu-id="34b0f-131">Anpassad vy visar en anpassningsbar vy av objekt egenskaper eller skript Blocks värden som inte följer den stela strukturen i tabellvyer, listvyer eller breda vyer.</span><span class="sxs-lookup"><span data-stu-id="34b0f-131">Custom view Displays a customizable view of object properties or script block values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="34b0f-132">Du kan definiera en fristående anpassad vy, eller så kan du definiera en anpassad vy som används av en annan vy, till exempel en tabellvy eller listvy.</span><span class="sxs-lookup"><span data-stu-id="34b0f-132">You can define a standalone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="34b0f-133">Mer information om den här vyn finns i [anpassad vy](../format/creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="34b0f-133">For more information about this view, see [Custom View](../format/creating-custom-controls.md).</span></span>

## <a name="view-xml-elements"></a><span data-ttu-id="34b0f-134">Visa XML-element</span><span class="sxs-lookup"><span data-stu-id="34b0f-134">View XML Elements</span></span>

<span data-ttu-id="34b0f-135">I följande exempel visas de XML-taggar som används för att definiera en tabellvy som innehåller två kolumner.</span><span class="sxs-lookup"><span data-stu-id="34b0f-135">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="34b0f-136">[ViewDefinitions](../format/viewdefinitions-element-format.md) -elementet är behållar elementet för alla vyer som definierats i format filen.</span><span class="sxs-lookup"><span data-stu-id="34b0f-136">The [ViewDefinitions](../format/viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="34b0f-137">Elementet [View](../format/view-element-format.md) definierar den aktuella vyn för tabeller, listor, bred eller anpassad.</span><span class="sxs-lookup"><span data-stu-id="34b0f-137">The [View](../format/view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="34b0f-138">I varje vy anger [Name](../format/name-element-for-view-format.md) -elementet namnet på vyn, [ViewSelectedBy](../format/viewselectedby-element-format.md) -elementet definierar de objekt som använder vyn och de olika kontroll elementen (till exempel `TableControl` elementet) definierar formatet för vyn.</span><span class="sxs-lookup"><span data-stu-id="34b0f-138">Within each view, the [Name](../format/name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](../format/viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element) define the format of the view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="34b0f-139">Se även</span><span class="sxs-lookup"><span data-stu-id="34b0f-139">See Also</span></span>

[<span data-ttu-id="34b0f-140">Tabellvy</span><span class="sxs-lookup"><span data-stu-id="34b0f-140">Table View</span></span>](../format/creating-a-table-view.md)

[<span data-ttu-id="34b0f-141">Listvy</span><span class="sxs-lookup"><span data-stu-id="34b0f-141">List View</span></span>](../format/creating-a-list-view.md)

[<span data-ttu-id="34b0f-142">Bred vy</span><span class="sxs-lookup"><span data-stu-id="34b0f-142">Wide View</span></span>](../format/creating-a-wide-view.md)

[<span data-ttu-id="34b0f-143">Anpassad vy</span><span class="sxs-lookup"><span data-stu-id="34b0f-143">Custom View</span></span>](../format/creating-custom-controls.md)

[<span data-ttu-id="34b0f-144">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="34b0f-144">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
