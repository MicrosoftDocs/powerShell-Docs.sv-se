---
ms.date: 09/13/2016
ms.topic: reference
title: Översikt över formateringsfiler
description: Översikt över formateringsfiler
ms.openlocfilehash: 769a86d274ef3b35a322d76e2f03cb551d9204a1
ms.sourcegitcommit: 04faa7dc1122bce839295d4891bd8b2f0ecb06ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97879144"
---
# <a name="formatting-file-overview"></a><span data-ttu-id="11742-103">Översikt över formateringsfiler</span><span class="sxs-lookup"><span data-stu-id="11742-103">Formatting File Overview</span></span>

<span data-ttu-id="11742-104">Visnings formatet för de objekt som returneras av kommandon (cmdlets, Functions och scripts) definieras med hjälp av formateringsattribut (format.ps1XML-filer).</span><span class="sxs-lookup"><span data-stu-id="11742-104">The display format for the objects that are returned by commands (cmdlets, functions, and scripts) are defined by using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="11742-105">Flera av de här filerna tillhandahålls av PowerShell för att definiera visnings formatet för de objekt som returneras av PowerShell-kommandon, till exempel [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -objektet som returnerades av `Get-Process` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="11742-105">Several of these files are provided by PowerShell to define the display format for those objects returned by PowerShell-provided commands, such as the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object returned by the `Get-Process` cmdlet.</span></span> <span data-ttu-id="11742-106">Men du kan också skapa egna filer för att skriva över standardformat, eller så kan du skriva en anpassad formatering för att definiera visningen av objekt som returneras av dina egna kommandon.</span><span class="sxs-lookup"><span data-stu-id="11742-106">However, you can also create your own custom formatting files to overwrite the default display formats or you can write a custom formatting file to define the display of objects returned by your own commands.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="11742-107">Filer formateras inte med de element som returneras till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="11742-107">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="11742-108">När ett objekt returneras till pipelinen är alla medlemmar i objektet tillgängliga även om några inte visas.</span><span class="sxs-lookup"><span data-stu-id="11742-108">When an object is returned to the pipeline, all members of that object are available even if some are not displayed.</span></span>

<span data-ttu-id="11742-109">PowerShell använder data i dessa filer för att avgöra vad som visas och hur de data som visas är formaterade.</span><span class="sxs-lookup"><span data-stu-id="11742-109">PowerShell uses the data in these formatting files to determine what is displayed and how the displayed data is formatted.</span></span> <span data-ttu-id="11742-110">De data som visas kan innehålla egenskaperna för ett objekt eller ett skripts värde.</span><span class="sxs-lookup"><span data-stu-id="11742-110">The displayed data can include the properties of an object or the value of a script.</span></span> <span data-ttu-id="11742-111">Skript används om du vill visa ett värde som inte är tillgängligt direkt från egenskaperna för ett objekt, t. ex. genom att lägga till värdet för två egenskaper för ett objekt och sedan Visa summan som en del av data.</span><span class="sxs-lookup"><span data-stu-id="11742-111">Scripts are used if you want to display some value that is not available directly from the properties of an object, such as adding the value of two properties of an object and then displaying the sum as a piece of data.</span></span> <span data-ttu-id="11742-112">Formatering av visade data görs genom att definiera vyer för de objekt som du vill visa.</span><span class="sxs-lookup"><span data-stu-id="11742-112">Formatting of the displayed data is done by defining views for the objects that you want to display.</span></span> <span data-ttu-id="11742-113">Du kan definiera en enskild vy för varje objekt, du kan definiera en enskild vy för flera objekt, eller så kan du definiera flera vyer för samma objekt.</span><span class="sxs-lookup"><span data-stu-id="11742-113">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="11742-114">Det finns ingen gräns för hur många vyer du kan definiera.</span><span class="sxs-lookup"><span data-stu-id="11742-114">There is no limit to the number of views that you can define.</span></span>

## <a name="common-features-of-formatting-files"></a><span data-ttu-id="11742-115">Vanliga funktioner i att formatera filer</span><span class="sxs-lookup"><span data-stu-id="11742-115">Common Features of Formatting Files</span></span>

<span data-ttu-id="11742-116">Varje fil format kan definiera följande komponenter som kan delas över alla vyer som definieras av filen:</span><span class="sxs-lookup"><span data-stu-id="11742-116">Each formatting file can define the following components that can be shared across all the views defined by the file:</span></span>

- <span data-ttu-id="11742-117">Standard konfigurations inställning, till exempel om data som visas i rader med tabeller ska visas på nästa rad, om data är längre än kolumnens bredd.</span><span class="sxs-lookup"><span data-stu-id="11742-117">Default configuration setting, such as whether the data displayed in the rows of tables will be displayed on the next line if the data is longer than the width of the column.</span></span> <span data-ttu-id="11742-118">Mer information om de här inställningarna finns i [definiera vanliga konfigurations inställningar](./defining-common-configuration-features.md).</span><span class="sxs-lookup"><span data-stu-id="11742-118">For more information about these settings, see [Defining Common Configuration Settings](./defining-common-configuration-features.md).</span></span>

- <span data-ttu-id="11742-119">Objekt uppsättningar som kan visas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="11742-119">Sets of objects that can be displayed by any of the views of the formatting file.</span></span> <span data-ttu-id="11742-120">Mer information om dessa uppsättningar (kallas *urvals uppsättningar*) finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="11742-120">For more information about these sets (referred to as *selection sets*), see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

- <span data-ttu-id="11742-121">Vanliga kontroller som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="11742-121">Common controls that can be used by all the views of the formatting file.</span></span> <span data-ttu-id="11742-122">Kontrollerna ger dig bättre kontroll över hur data visas.</span><span class="sxs-lookup"><span data-stu-id="11742-122">Controls give you finer control on how data is displayed.</span></span> <span data-ttu-id="11742-123">Mer information om kontroller finns i [definiera anpassade kontroller](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="11742-123">For more information about controls, see [Defining Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="formatting-views"></a><span data-ttu-id="11742-124">Formatera vyer</span><span class="sxs-lookup"><span data-stu-id="11742-124">Formatting Views</span></span>

<span data-ttu-id="11742-125">Vyer för formatering kan visa objekt i tabell format, list format, brett format och anpassat format.</span><span class="sxs-lookup"><span data-stu-id="11742-125">Formatting views can display objects in a table format, list format, wide format, and custom format.</span></span> <span data-ttu-id="11742-126">För det mesta beskrivs varje format definition av en uppsättning XML-taggar som beskriver vyn.</span><span class="sxs-lookup"><span data-stu-id="11742-126">For the most part, each formatting definition is described by a set of XML tags that describe the view.</span></span> <span data-ttu-id="11742-127">Varje vy innehåller namnet på vyn, de objekt som använder vyn och elementen i vyn, till exempel kolumn-och rad information för en tabellvy.</span><span class="sxs-lookup"><span data-stu-id="11742-127">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="11742-128">I Tabellvy visas egenskaperna för ett objekt eller ett skript Blocks värde i en eller flera kolumner.</span><span class="sxs-lookup"><span data-stu-id="11742-128">Table View Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="11742-129">Varje kolumn representerar en enskild egenskap hos objektet eller ett skript värde.</span><span class="sxs-lookup"><span data-stu-id="11742-129">Each column represents a single property of the object or a script value.</span></span> <span data-ttu-id="11742-130">Du kan definiera en tabellvy som visar alla egenskaper för ett objekt, en delmängd av egenskaperna för ett objekt eller en kombination av egenskaper och skript värden.</span><span class="sxs-lookup"><span data-stu-id="11742-130">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script values.</span></span> <span data-ttu-id="11742-131">Varje rad i tabellen representerar ett returnerat objekt.</span><span class="sxs-lookup"><span data-stu-id="11742-131">Each row of the table represents a returned object.</span></span> <span data-ttu-id="11742-132">Att skapa en tabellvy liknar när du rör ett objekt till `Format-Table` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="11742-132">Creating a table view is very similar to when you pipe an object to the `Format-Table` cmdlet.</span></span> <span data-ttu-id="11742-133">Mer information om den här vyn finns i [tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="11742-133">For more information about this view, see [Table View](./creating-a-table-view.md).</span></span>

<span data-ttu-id="11742-134">Listvy visar egenskaperna för ett objekt eller ett skript värde i en kolumn.</span><span class="sxs-lookup"><span data-stu-id="11742-134">List View Lists the properties of an object or a script value in a single column.</span></span> <span data-ttu-id="11742-135">Varje rad i listan visar en valfri etikett eller egenskaps namnet följt av värdet för egenskapen eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="11742-135">Each row of the list displays an optional label or the property name followed by the value of the property or script.</span></span> <span data-ttu-id="11742-136">Att skapa en listvy är mycket likt att skicka ett objekt till `Format-List` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="11742-136">Creating a list view is very similar to piping an object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="11742-137">Mer information om den här vyn finns i [listvyn](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="11742-137">For more information about this view, see [List View](./creating-a-list-view.md).</span></span>

<span data-ttu-id="11742-138">Wide View visar en enskild egenskap för ett objekt eller ett skript värde i en eller flera kolumner.</span><span class="sxs-lookup"><span data-stu-id="11742-138">Wide View Lists a single property of an object or a script value in one or more columns.</span></span> <span data-ttu-id="11742-139">Det finns ingen etikett eller rubrik för den här vyn.</span><span class="sxs-lookup"><span data-stu-id="11742-139">There is no label or header for this view.</span></span> <span data-ttu-id="11742-140">Att skapa en bred vy påminner mycket om att skicka ett objekt till `Format-Wide` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="11742-140">Creating a wide view is very similar to piping an object to the `Format-Wide` cmdlet.</span></span> <span data-ttu-id="11742-141">Mer information om den här vyn finns i [wide View](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="11742-141">For more information about this view, see [Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="11742-142">Anpassad vy visar en anpassningsbar vy av objekt egenskaper eller skript värden som inte följer den stela strukturen i tabellvyer, listvyer eller breda vyer.</span><span class="sxs-lookup"><span data-stu-id="11742-142">Custom View Displays a customizable view of object properties or script values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="11742-143">Du kan definiera en fristående anpassad vy eller definiera en anpassad vy som används av en annan vy, till exempel en tabellvy eller listvy.</span><span class="sxs-lookup"><span data-stu-id="11742-143">You can define a stand-alone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="11742-144">Att skapa en anpassad vy är mycket likt att skicka ett objekt till `Format-Custom` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="11742-144">Creating a custom view is very similar to piping an object to the `Format-Custom` cmdlet.</span></span> <span data-ttu-id="11742-145">Mer information om den här vyn finns i [anpassad vy](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="11742-145">For more information about this view, see [Custom View](./creating-custom-controls.md).</span></span>

## <a name="components-of-a-view"></a><span data-ttu-id="11742-146">Komponenter i en vy</span><span class="sxs-lookup"><span data-stu-id="11742-146">Components of a View</span></span>

<span data-ttu-id="11742-147">I följande XML-exempel visas de grundläggande XML-komponenterna i en vy.</span><span class="sxs-lookup"><span data-stu-id="11742-147">The following XML examples show the basic XML components of a view.</span></span> <span data-ttu-id="11742-148">De enskilda XML-elementen varierar beroende på vilken vy du vill skapa, men de grundläggande komponenterna i vyerna är samma.</span><span class="sxs-lookup"><span data-stu-id="11742-148">The individual XML elements vary depending on which view you want to create, but the basic components of the views are all the same.</span></span>

<span data-ttu-id="11742-149">För att börja med, har varje vy ett- `Name` element som anger ett eget användarvänligt namn som används för att referera till vyn.</span><span class="sxs-lookup"><span data-stu-id="11742-149">To start with, each view has a `Name` element that specifies a user friendly name that is used to reference the view.</span></span> <span data-ttu-id="11742-150">ett `ViewSelectedBy` element som definierar vilka .net-objekt som visas i vyn och ett *kontroll* element som definierar vyn.</span><span class="sxs-lookup"><span data-stu-id="11742-150">a `ViewSelectedBy` element that defines which .NET objects are displayed by the view, and a *control* element that defines the view.</span></span>

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

<span data-ttu-id="11742-151">I kontroll elementet kan du definiera ett eller flera *post* element.</span><span class="sxs-lookup"><span data-stu-id="11742-151">Within the control element, you can define one or more *entry* elements.</span></span> <span data-ttu-id="11742-152">Om du använder flera definitioner måste du ange vilka .NET-objekt som ska använda varje definition.</span><span class="sxs-lookup"><span data-stu-id="11742-152">If you use multiple definitions, you must specify which .NET objects use each definition.</span></span> <span data-ttu-id="11742-153">Vanligt vis behövs bara en post, med bara en definition, för varje kontroll.</span><span class="sxs-lookup"><span data-stu-id="11742-153">Typically only one entry, with only one definition, is needed for each control.</span></span>

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

<span data-ttu-id="11742-154">I varje post element i en vy anger du de *objekts* element som definierar de .net-egenskaper eller skript som visas i den vyn.</span><span class="sxs-lookup"><span data-stu-id="11742-154">Within each entry element of a view, you specify the *item* elements that define the .NET properties or scripts that are displayed by that view.</span></span>

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

<span data-ttu-id="11742-155">Som du ser i föregående exempel kan format filen innehålla flera vyer, en vy kan innehålla flera definitioner och varje definition kan innehålla flera objekt.</span><span class="sxs-lookup"><span data-stu-id="11742-155">As shown in the preceding examples, the formatting file can contain multiple views, a view can contain multiple definitions, and each definition can contain multiple items.</span></span>

## <a name="example-of-a-table-view"></a><span data-ttu-id="11742-156">Exempel på en tabellvy</span><span class="sxs-lookup"><span data-stu-id="11742-156">Example of a Table View</span></span>

<span data-ttu-id="11742-157">I följande exempel visas de XML-taggar som används för att definiera en tabellvy som innehåller två kolumner.</span><span class="sxs-lookup"><span data-stu-id="11742-157">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="11742-158">[ViewDefinitions](./viewdefinitions-element-format.md) -elementet är behållar elementet för alla vyer som definierats i format filen.</span><span class="sxs-lookup"><span data-stu-id="11742-158">The [ViewDefinitions](./viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="11742-159">Elementet [View](./view-element-format.md) definierar den aktuella vyn för tabeller, listor, bred eller anpassad.</span><span class="sxs-lookup"><span data-stu-id="11742-159">The [View](./view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="11742-160">I varje [View](./view-element-format.md) -element anger elementet [Name](./name-element-for-view-format.md) namnet på vyn, [ViewSelectedBy](./viewselectedby-element-format.md) -elementet definierar de objekt som använder vyn och de olika kontroll elementen (till exempel `TableControl` elementet som visas i följande exempel) definierar typen för vyn.</span><span class="sxs-lookup"><span data-stu-id="11742-160">Within each [View](./view-element-format.md) element, the [Name](./name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element shown in the following example) define the type of the view.</span></span>

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
    </TableControl>
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a><span data-ttu-id="11742-161">Se även</span><span class="sxs-lookup"><span data-stu-id="11742-161">See Also</span></span>

[<span data-ttu-id="11742-162">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="11742-162">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="11742-163">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="11742-163">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="11742-164">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="11742-164">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="11742-165">Skapa anpassade kontroller</span><span class="sxs-lookup"><span data-stu-id="11742-165">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="11742-166">Skriva en PowerShell-formatering och en typ fil</span><span class="sxs-lookup"><span data-stu-id="11742-166">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
