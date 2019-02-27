---
title: 'Formatering: översikt | Microsoft Docs'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe888fee-1fe9-459f-9d62-35732c19a7f8
caps.latest.revision: 13
ms.openlocfilehash: d418cff70c1197aa3c331eed909f49198da139e9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851921"
---
# <a name="formatting-file-overview"></a><span data-ttu-id="1e10d-102">Översikt över formateringsfiler</span><span class="sxs-lookup"><span data-stu-id="1e10d-102">Formatting File Overview</span></span>

<span data-ttu-id="1e10d-103">Visningsformatet för de objekt som returneras av kommandon (cmdlet: ar, funktioner och skript) definieras med hjälp av formatering (filer format.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="1e10d-103">The display format for the objects that are returned by commands (cmdlets, functions, and scripts) are defined by using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="1e10d-104">Flera av de här filerna tillhandahålls av PowerShell för att definiera visningsformat för de objekt som returneras av förutsatt att PowerShell kommandon, till exempel den [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objektet som returneras av den `Get-Process` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1e10d-104">Several of these files are provided by PowerShell to define the display format for those objects returned by PowerShell-provided commands, such as the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object returned by the `Get-Process` cmdlet.</span></span> <span data-ttu-id="1e10d-105">Men du kan också skapa dina egna anpassade formatering filer om du vill skriva över format som standard visas eller du kan skriva en anpassad formatering fil för att definiera visningen av objekten som returneras av dina egna kommandon.</span><span class="sxs-lookup"><span data-stu-id="1e10d-105">However, you can also create your own custom formatting files to overwrite the default display formats or you can write a custom formatting file to define the display of objects returned by your own commands.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1e10d-106">Formatering filer styr inte den del av ett objekt som returneras till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="1e10d-106">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="1e10d-107">När ett objekt returneras till pipelinen kan är alla medlemmar i objektet tillgängliga även om vissa inte visas.</span><span class="sxs-lookup"><span data-stu-id="1e10d-107">When an object is returned to the pipeline, all members of that object are available even if some are not displayed.</span></span>

<span data-ttu-id="1e10d-108">PowerShell använder data i dessa formatering filer för att avgöra vad som visas och hur data som visas är formaterad.</span><span class="sxs-lookup"><span data-stu-id="1e10d-108">PowerShell uses the data in these formatting files to determine what is displayed and how the displayed data is formatted.</span></span> <span data-ttu-id="1e10d-109">Data som visas kan innehålla egenskaperna för ett objekt eller värdet för ett skript.</span><span class="sxs-lookup"><span data-stu-id="1e10d-109">The displayed data can include the properties of an object or the value of a script.</span></span> <span data-ttu-id="1e10d-110">Skript används om du vill visa ett värde som inte är tillgänglig direkt från egenskaperna för ett objekt, till exempel att lägga till värdet för två egenskaper för ett objekt och sedan visa summan som en typ av data.</span><span class="sxs-lookup"><span data-stu-id="1e10d-110">Scripts are used if you want to display some value that is not available directly from the properties of an object, such as adding the value of two properties of an object and then displaying the sum as a piece of data.</span></span> <span data-ttu-id="1e10d-111">Formatering av data som visas gör du genom att definiera vyer för de objekt som du vill visa.</span><span class="sxs-lookup"><span data-stu-id="1e10d-111">Formatting of the displayed data is done by defining views for the objects that you want to display.</span></span> <span data-ttu-id="1e10d-112">Du kan definiera en vy för varje objekt, kan du definiera en vy för flera objekt eller du kan definiera flera vyer för samma objekt.</span><span class="sxs-lookup"><span data-stu-id="1e10d-112">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="1e10d-113">Det finns ingen gräns för antal vyer som du kan definiera.</span><span class="sxs-lookup"><span data-stu-id="1e10d-113">There is no limit to the number of views that you can define.</span></span>

## <a name="common-features-of-formatting-files"></a><span data-ttu-id="1e10d-114">Vanliga funktioner av formatering filer</span><span class="sxs-lookup"><span data-stu-id="1e10d-114">Common Features of Formatting Files</span></span>

<span data-ttu-id="1e10d-115">Varje formatering fil kan definiera följande komponenter som kan delas mellan alla vyer som definieras av filen:</span><span class="sxs-lookup"><span data-stu-id="1e10d-115">Each formatting file can define the following components that can be shared across all the views defined by the file:</span></span>

- <span data-ttu-id="1e10d-116">Som standard konfigurationsinställning, till exempel om data som visas i raderna i tabellerna ska visas på nästa rad om data är längre än bredden på kolumnen.</span><span class="sxs-lookup"><span data-stu-id="1e10d-116">Default configuration setting, such as whether the data displayed in the rows of tables will be displayed on the next line if the data is longer than the width of the column.</span></span> <span data-ttu-id="1e10d-117">Mer information om dessa inställningar finns i [definierar gemensamma konfigurationsinställningar](./defining-common-configuration-features.md).</span><span class="sxs-lookup"><span data-stu-id="1e10d-117">For more information about these settings, see [Defining Common Configuration Settings](./defining-common-configuration-features.md).</span></span>

- <span data-ttu-id="1e10d-118">Uppsättningar med objekt som kan visas med någon av vyerna i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="1e10d-118">Sets of objects that can be displayed by any of the views of the formatting file.</span></span> <span data-ttu-id="1e10d-119">Mer information om dessa uppsättningar (kallas *val av uppsättningar*), se [definiera anger av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="1e10d-119">For more information about these sets (referred to as *selection sets*), see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

- <span data-ttu-id="1e10d-120">Vanliga kontroller som kan användas av alla vyer i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="1e10d-120">Common controls that can be used by all the views of the formatting file.</span></span> <span data-ttu-id="1e10d-121">Kontroller ger mer detaljerad kontroll på hur data visas.</span><span class="sxs-lookup"><span data-stu-id="1e10d-121">Controls give you finer control on how data is displayed.</span></span> <span data-ttu-id="1e10d-122">Mer information om kontroller finns i [definiera anpassade kontroller](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="1e10d-122">For more information about controls, see [Defining Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="formatting-views"></a><span data-ttu-id="1e10d-123">Formatering vyer</span><span class="sxs-lookup"><span data-stu-id="1e10d-123">Formatting Views</span></span>

<span data-ttu-id="1e10d-124">Formatering vyer kan visa objekt i ett tabellformat listformat, brett format och anpassat format.</span><span class="sxs-lookup"><span data-stu-id="1e10d-124">Formatting views can display objects in a table format, list format, wide format, and custom format.</span></span> <span data-ttu-id="1e10d-125">För det mesta beskrivs varje formatering definition av en uppsättning XML-taggar som beskriver vyn.</span><span class="sxs-lookup"><span data-stu-id="1e10d-125">For the most part, each formatting definition is described by a set of XML tags that describe the view.</span></span> <span data-ttu-id="1e10d-126">Varje vy innehåller namnet på vyn objekt som använder vyn och element i vyn, till exempel kolumn- och information för en tabellvy.</span><span class="sxs-lookup"><span data-stu-id="1e10d-126">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="1e10d-127">Visa Tabellistor egenskaperna för ett objekt eller ett skript block värde i en eller flera kolumner.</span><span class="sxs-lookup"><span data-stu-id="1e10d-127">Table View Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="1e10d-128">Varje kolumn representerar en enskild egenskap för objektet eller ett skriptvärde.</span><span class="sxs-lookup"><span data-stu-id="1e10d-128">Each column represents a single property of the object or a script value.</span></span> <span data-ttu-id="1e10d-129">Du kan definiera en tabellvy som visar alla egenskaper för ett objekt, en delmängd av egenskaperna för ett objekt eller en kombination av egenskaper och värden för skriptet.</span><span class="sxs-lookup"><span data-stu-id="1e10d-129">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script values.</span></span> <span data-ttu-id="1e10d-130">Varje rad i tabellen representerar en returnerade objektet.</span><span class="sxs-lookup"><span data-stu-id="1e10d-130">Each row of the table represents a returned object.</span></span> <span data-ttu-id="1e10d-131">Skapa en tabellvy liknar när du skicka ett objekt för att den `Format-Table` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1e10d-131">Creating a table view is very similar to when you pipe an object to the `Format-Table` cmdlet.</span></span> <span data-ttu-id="1e10d-132">Mer information om den här vyn finns i [tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="1e10d-132">For more information about this view, see [Table View](./creating-a-table-view.md).</span></span>

<span data-ttu-id="1e10d-133">Lista visas egenskaperna för ett objekt eller ett skriptvärde i en enda kolumn.</span><span class="sxs-lookup"><span data-stu-id="1e10d-133">List View Lists the properties of an object or a script value in a single column.</span></span> <span data-ttu-id="1e10d-134">Varje rad i listan visar en valfri etikett eller egenskapens namn följt av värdet för egenskapen eller skript.</span><span class="sxs-lookup"><span data-stu-id="1e10d-134">Each row of the list displays an optional label or the property name followed by the value of the property or script.</span></span> <span data-ttu-id="1e10d-135">Skapa en listvy liknar att skicka ett objekt för att den `Format-List` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1e10d-135">Creating a list view is very similar to piping an object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="1e10d-136">Mer information om den här vyn finns i [listvyn](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="1e10d-136">For more information about this view, see [List View](./creating-a-list-view.md).</span></span>

<span data-ttu-id="1e10d-137">Bred vy innehåller en enda egenskap för ett objekt eller ett skriptvärde i en eller flera kolumner.</span><span class="sxs-lookup"><span data-stu-id="1e10d-137">Wide View Lists a single property of an object or a script value in one or more columns.</span></span> <span data-ttu-id="1e10d-138">Det finns ingen etikett eller rubrik för den här vyn.</span><span class="sxs-lookup"><span data-stu-id="1e10d-138">There is no label or header for this view.</span></span> <span data-ttu-id="1e10d-139">Skapa en bred vy liknar att skicka ett objekt för att den `Format-Wide` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1e10d-139">Creating a wide view is very similar to piping an object to the `Format-Wide` cmdlet.</span></span> <span data-ttu-id="1e10d-140">Mer information om den här vyn finns i [bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="1e10d-140">For more information about this view, see [Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="1e10d-141">Anpassad vy visar en anpassningsbar objektegenskaper eller skript värden som inte följer den fasta strukturen för tabellvyer, listvyer eller wide vyer.</span><span class="sxs-lookup"><span data-stu-id="1e10d-141">Custom View Displays a customizable view of object properties or script values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="1e10d-142">Du kan definiera en anpassad vy som är fristående eller du kan definiera en anpassad vy som används av en annan vy, till exempel en tabell eller listvy.</span><span class="sxs-lookup"><span data-stu-id="1e10d-142">You can define a stand-alone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="1e10d-143">Skapa en anpassad vy liknar att skicka ett objekt för att den `Format-Custom` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1e10d-143">Creating a custom view is very similar to piping an object to the `Format-Custom` cmdlet.</span></span> <span data-ttu-id="1e10d-144">Mer information om den här vyn finns i [anpassad vy](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="1e10d-144">For more information about this view, see [Custom View](./creating-custom-controls.md).</span></span>

## <a name="components-of-a-view"></a><span data-ttu-id="1e10d-145">Komponenterna i en vy</span><span class="sxs-lookup"><span data-stu-id="1e10d-145">Components of a View</span></span>

<span data-ttu-id="1e10d-146">I följande XML-exempel visas XML grundkomponenterna i en vy.</span><span class="sxs-lookup"><span data-stu-id="1e10d-146">The following XML examples show the basic XML components of a view.</span></span> <span data-ttu-id="1e10d-147">Enskilda XML-elementen varierar beroende på vilken vy som du vill skapa men grundkomponenterna i vyerna är likadana.</span><span class="sxs-lookup"><span data-stu-id="1e10d-147">The individual XML elements vary depending on which view you want to create, but the basic components of the views are all the same.</span></span>

<span data-ttu-id="1e10d-148">Börja med varje vy har en `Name` element som anger ett användarvänligt namn som används för att referera till vyn.</span><span class="sxs-lookup"><span data-stu-id="1e10d-148">To start with, each view has a `Name` element that specifies a user friendly name that is used to reference the view.</span></span> <span data-ttu-id="1e10d-149">en `ViewSelectedBy` -element som definierar vilka .NET-objekt visas i vyn, och en *kontroll* element som definierar vyn.</span><span class="sxs-lookup"><span data-stu-id="1e10d-149">a `ViewSelectedBy` element that defines which .NET objects are displayed by the view, and a *control* element that defines the view.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <ListControl>...</ListControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <WideControl>...</WideControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <CustomControl>...</CustomControl>
  </View>
</ViewDefinitions>

```

<span data-ttu-id="1e10d-150">I control-elementet kan du definiera en eller flera *post* element.</span><span class="sxs-lookup"><span data-stu-id="1e10d-150">Within the control element, you can define one or more *entry* elements.</span></span> <span data-ttu-id="1e10d-151">Om du använder flera definitioner, måste du ange vilka .NET-objekt använder varje definition.</span><span class="sxs-lookup"><span data-stu-id="1e10d-151">If you use multiple definitions, you must specify which .NET objects use each definition.</span></span> <span data-ttu-id="1e10d-152">Vanligtvis krävs bara en post med endast en definition för varje kontroll.</span><span class="sxs-lookup"><span data-stu-id="1e10d-152">Typically only one entry, with only one definition, is needed for each control.</span></span>

```xml
<ListControl>
  <ListEntries>
    <ListEntry>
      <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
  </ListEntries>
</ListControl>

```

<span data-ttu-id="1e10d-153">Inom varje post element i en vy som du anger den *objekt* element som definierar egenskaper för .NET eller skript som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="1e10d-153">Within each entry element of a view, you specify the *item* elements that define the .NET properties or scripts that are displayed by that view.</span></span>

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

<span data-ttu-id="1e10d-154">I föregående exempel visas formatering filen kan innehålla flera vyer, en vy kan innehålla flera definitioner och varje definition kan innehålla flera objekt.</span><span class="sxs-lookup"><span data-stu-id="1e10d-154">As shown in the preceding examples, the formatting file can contain multiple views, a view can contain multiple definitions, and each definition can contain multiple items.</span></span>

## <a name="example-of-a-table-view"></a><span data-ttu-id="1e10d-155">Exempel på en tabellvy</span><span class="sxs-lookup"><span data-stu-id="1e10d-155">Example of a Table View</span></span>

<span data-ttu-id="1e10d-156">I följande exempel visar XML-taggar som används för att definiera en tabellvy som innehåller två kolumner.</span><span class="sxs-lookup"><span data-stu-id="1e10d-156">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="1e10d-157">Den [ViewDefinitions](./viewdefinitions-element-format.md) elementet är elementet behållare för alla vyer som definieras i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="1e10d-157">The [ViewDefinitions](./viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="1e10d-158">Den [visa](./view-element-format.md) elementet definierar viss tabell, lista, brett eller anpassade vy.</span><span class="sxs-lookup"><span data-stu-id="1e10d-158">The [View](./view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="1e10d-159">Inom varje [visa](./view-element-format.md) element, den [namn](./name-element-for-view-format.md) elementet anger namnet på vyn, den [ViewSelectedBy](./viewselectedby-element-format.md) elementet definierar de objekt som använder vyn och de olika styra element (till exempel den `TableControl` element som visas i följande exempel) definiera typ av vy.</span><span class="sxs-lookup"><span data-stu-id="1e10d-159">Within each [View](./view-element-format.md) element, the [Name](./name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element shown in the following example) define the type of the view.</span></span>

```xml
<ViewDefinitions>
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

## <a name="see-also"></a><span data-ttu-id="1e10d-160">Se även</span><span class="sxs-lookup"><span data-stu-id="1e10d-160">See Also</span></span>

[<span data-ttu-id="1e10d-161">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="1e10d-161">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="1e10d-162">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="1e10d-162">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="1e10d-163">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="1e10d-163">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="1e10d-164">Skapa anpassade kontroller</span><span class="sxs-lookup"><span data-stu-id="1e10d-164">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="1e10d-165">Skriva ett PowerShell-formatering och typer fil</span><span class="sxs-lookup"><span data-stu-id="1e10d-165">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
