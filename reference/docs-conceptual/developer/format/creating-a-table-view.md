---
ms.date: 09/13/2016
ms.topic: reference
title: Skapa en tabellvy
description: Skapa en tabellvy
ms.openlocfilehash: 035d42f7968a9e8babec692a7a5873e24b36cd97
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660303"
---
# <a name="creating-a-table-view"></a><span data-ttu-id="a1052-103">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="a1052-103">Creating a Table View</span></span>

<span data-ttu-id="a1052-104">I en tabellvy visas data i en eller flera kolumner.</span><span class="sxs-lookup"><span data-stu-id="a1052-104">A table view displays data in one or more columns.</span></span> <span data-ttu-id="a1052-105">Varje rad i tabellen representerar ett .NET-objekt och varje kolumn i tabellen representerar en egenskap för objektet eller ett skript värde.</span><span class="sxs-lookup"><span data-stu-id="a1052-105">Each row in the table represents a .NET object, and each column of the table represents a property of the object or a script value.</span></span> <span data-ttu-id="a1052-106">Du kan definiera en tabellvy som visar alla egenskaper för ett objekt eller en delmängd av egenskaperna för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="a1052-106">You can define a table view that displays all the properties of an object or a subset of the properties of an object.</span></span>

## <a name="a-table-view-display"></a><span data-ttu-id="a1052-107">Visa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="a1052-107">A Table View Display</span></span>

<span data-ttu-id="a1052-108">I följande exempel visas hur Windows PowerShell visar objektet [system. serviceprocess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) som returneras av cmdleten [Get-service](/powershell/module/microsoft.powershell.management/get-service) .</span><span class="sxs-lookup"><span data-stu-id="a1052-108">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="a1052-109">För det här objektet har Windows PowerShell definierat en tabellvy som visar `Status` egenskapen, `Name` egenskapen (den här egenskapen är en alias egenskap för `ServiceName` egenskapen) och `DisplayName` egenskapen.</span><span class="sxs-lookup"><span data-stu-id="a1052-109">For this object, Windows PowerShell has defined a table view that displays the `Status` property, the `Name` property (this property is an alias property for the `ServiceName` property), and the `DisplayName` property.</span></span> <span data-ttu-id="a1052-110">Varje rad i tabellen representerar ett objekt som returneras av cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a1052-110">Each row in the table represents an object returned by the cmdlet.</span></span>

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a><span data-ttu-id="a1052-111">Definiera tabellvy</span><span class="sxs-lookup"><span data-stu-id="a1052-111">Defining the Table View</span></span>

<span data-ttu-id="a1052-112">Följande XML visar schemat för tabellvy för att visa [system. serviceprocess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -objekt.</span><span class="sxs-lookup"><span data-stu-id="a1052-112">The following XML shows the table view schema for displaying the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="a1052-113">Du måste ange varje egenskap som du vill ska visas i vyn tabell.</span><span class="sxs-lookup"><span data-stu-id="a1052-113">You must specify each property that you want displayed in the table view.</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>
      <TableColumnHeader>
        <Width>8</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>18</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>38</Width>
      </TableColumnHeader>
    </TableHeaders>
    <TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>
  </TableControl>
</View>
```

<span data-ttu-id="a1052-114">Följande XML-element används för att definiera en listvy:</span><span class="sxs-lookup"><span data-stu-id="a1052-114">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="a1052-115">Elementet [View](./view-element-format.md) är det överordnade elementet i vyn tabell.</span><span class="sxs-lookup"><span data-stu-id="a1052-115">The [View](./view-element-format.md) element is the parent element of the table view.</span></span> <span data-ttu-id="a1052-116">(Detta är samma överordnade element för vyerna lista, bred och anpassad.)</span><span class="sxs-lookup"><span data-stu-id="a1052-116">(This is the same parent element for the list, wide, and custom control views.)</span></span>

- <span data-ttu-id="a1052-117">Elementet [Name](./name-element-for-view-format.md) anger namnet på vyn.</span><span class="sxs-lookup"><span data-stu-id="a1052-117">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="a1052-118">Det här elementet krävs för alla vyer.</span><span class="sxs-lookup"><span data-stu-id="a1052-118">This element is required for all views.</span></span>

- <span data-ttu-id="a1052-119">[ViewSelectedBy](./viewselectedby-element-format.md) -elementet definierar de objekt som använder vyn.</span><span class="sxs-lookup"><span data-stu-id="a1052-119">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="a1052-120">Det här elementet är obligatoriskt.</span><span class="sxs-lookup"><span data-stu-id="a1052-120">This element is required.</span></span>

- <span data-ttu-id="a1052-121">Elementet [groupby](./groupby-element-for-view-format.md) (visas inte i det här exemplet) definierar när en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="a1052-121">The [GroupBy](./groupby-element-for-view-format.md) element (not shown in this example) defines when a new group of objects is displayed.</span></span> <span data-ttu-id="a1052-122">En ny grupp startas när värdet för en speciell egenskap eller skript ändras.</span><span class="sxs-lookup"><span data-stu-id="a1052-122">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="a1052-123">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="a1052-123">This element is optional.</span></span>

- <span data-ttu-id="a1052-124">Elementet [Controls](./controls-element-for-view-format.md) (visas inte i det här exemplet) definierar de anpassade kontroller som definieras av tabellvy.</span><span class="sxs-lookup"><span data-stu-id="a1052-124">The [Controls](./controls-element-for-view-format.md) element (not shown in this example) defines the custom controls that are defined by the table view.</span></span> <span data-ttu-id="a1052-125">Kontrollerna ger dig ett sätt att ytterligare ange hur data ska visas.</span><span class="sxs-lookup"><span data-stu-id="a1052-125">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="a1052-126">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="a1052-126">This element is optional.</span></span> <span data-ttu-id="a1052-127">En vy kan definiera egna anpassade kontroller, eller så kan den använda vanliga kontroller som kan användas av vilken vy som helst i format filen.</span><span class="sxs-lookup"><span data-stu-id="a1052-127">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="a1052-128">Mer information om anpassade kontroller finns i [skapa anpassade kontroller](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="a1052-128">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="a1052-129">[HideTableHeaders](./hidetableheaders-element-format.md) -elementet (visas inte i det här exemplet) anger att tabellen inte kommer att visa några etiketter överst i tabellen.</span><span class="sxs-lookup"><span data-stu-id="a1052-129">The [HideTableHeaders](./hidetableheaders-element-format.md) element (not show in this example) specifies that the table will not show any labels at the top of the table.</span></span> <span data-ttu-id="a1052-130">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="a1052-130">This element is optional.</span></span>

- <span data-ttu-id="a1052-131">Det [TableControl](./tablecontrol-element-format.md) -element som definierar tabellens rubrik och rad information.</span><span class="sxs-lookup"><span data-stu-id="a1052-131">The [TableControl](./tablecontrol-element-format.md) element that defines the header and row information of the table.</span></span> <span data-ttu-id="a1052-132">I likhet med alla andra vyer kan en tabellvy Visa värdena för objekt egenskaper eller värden som genereras av skript.</span><span class="sxs-lookup"><span data-stu-id="a1052-132">Similar to all other views, a table view can display the values of object properties or values generated by scripts.</span></span>

## <a name="defining-column-headers"></a><span data-ttu-id="a1052-133">Definiera kolumn rubriker</span><span class="sxs-lookup"><span data-stu-id="a1052-133">Defining Column Headers</span></span>

1. <span data-ttu-id="a1052-134">[TableHeaders](./tableheaders-element-format.md) -elementet och dess underordnade element definierar vad som visas överst i tabellen.</span><span class="sxs-lookup"><span data-stu-id="a1052-134">The [TableHeaders](./tableheaders-element-format.md) element and its child elements define what is displayed at the top of the table.</span></span>

2. <span data-ttu-id="a1052-135">[TableColumnHeader](./tablecolumnheader-element-format.md) -elementet definierar vad som visas överst i en kolumn i tabellen.</span><span class="sxs-lookup"><span data-stu-id="a1052-135">The [TableColumnHeader](./tablecolumnheader-element-format.md) element defines what is displayed at the top of a column of the table.</span></span> <span data-ttu-id="a1052-136">Ange dessa element i den ordning som du vill att rubrikerna ska visas.</span><span class="sxs-lookup"><span data-stu-id="a1052-136">Specify these elements in the order that you want the headers displayed.</span></span>

   <span data-ttu-id="a1052-137">Det finns ingen gräns för hur många element du kan använda, men antalet [TableColumnHeader](./tablecolumnheader-element-format.md) -element i din tabellvy måste vara lika med antalet [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) -element som du använder.</span><span class="sxs-lookup"><span data-stu-id="a1052-137">There is no limit to the number of these element that you can use, but the number of [TableColumnHeader](./tablecolumnheader-element-format.md) elements in your table view must equal the number of [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) elements that you use.</span></span>

3. <span data-ttu-id="a1052-138">Elementet [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) anger texten som visas.</span><span class="sxs-lookup"><span data-stu-id="a1052-138">The [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the text that is displayed.</span></span> <span data-ttu-id="a1052-139">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="a1052-139">This element is optional.</span></span>

4. <span data-ttu-id="a1052-140">Elementet [width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) anger bredden (i tecken) för kolumnen.</span><span class="sxs-lookup"><span data-stu-id="a1052-140">The [Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the width (in characters) of the column.</span></span> <span data-ttu-id="a1052-141">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="a1052-141">This element is optional.</span></span>

5. <span data-ttu-id="a1052-142">Elementet [Alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) anger hur etiketten visas.</span><span class="sxs-lookup"><span data-stu-id="a1052-142">The [Alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies how the label is displayed.</span></span> <span data-ttu-id="a1052-143">Etiketten kan justeras till vänster, till höger eller centrerad.</span><span class="sxs-lookup"><span data-stu-id="a1052-143">The label can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="a1052-144">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="a1052-144">This element is optional.</span></span>

## <a name="defining-the-table-rows"></a><span data-ttu-id="a1052-145">Definiera tabell rader</span><span class="sxs-lookup"><span data-stu-id="a1052-145">Defining the Table Rows</span></span>

<span data-ttu-id="a1052-146">Tabellvyer kan tillhandahålla en eller flera definitioner som anger vilka data som visas i raderna i tabellen med hjälp av de underordnade elementen i [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) -elementet.</span><span class="sxs-lookup"><span data-stu-id="a1052-146">Table views can provide one or more definitions that specify what data is displayed in the rows of the table by using the child elements of the [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="a1052-147">Observera att du kan ange flera definitioner för raderna i tabellen, men rubrikerna för raderna förblir desamma, oavsett vilken rad definition som används.</span><span class="sxs-lookup"><span data-stu-id="a1052-147">Notice that you can specify multiple definitions for the rows of the table, but the headers for the rows remains the same, regardless of what row definition is used.</span></span> <span data-ttu-id="a1052-148">Normalt har en tabell bara en definition.</span><span class="sxs-lookup"><span data-stu-id="a1052-148">Typically, a table will have only one definition.</span></span>

<span data-ttu-id="a1052-149">I följande exempel tillhandahåller vyn en enda definition som visar värdena för flera egenskaper för [system. Diagnostics. process? Displayproperty = FullName](/dotnet/api/System.Diagnostics.Process) -objekt.</span><span class="sxs-lookup"><span data-stu-id="a1052-149">In the following example, the view provides a single definition that displays the values of several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="a1052-150">En tabellvy kan visa värdet för en egenskap eller värdet för ett skript (visas inte i exemplet) i dess rader.</span><span class="sxs-lookup"><span data-stu-id="a1052-150">A table view can display the value of a property or the value of a script (not shown in the example) in its rows.</span></span>

```xml
<TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>

```

<span data-ttu-id="a1052-151">Följande XML-element kan användas för att tillhandahålla definitioner för en rad:</span><span class="sxs-lookup"><span data-stu-id="a1052-151">The following XML elements can be used to provide definitions for a row:</span></span>

- <span data-ttu-id="a1052-152">[TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) -elementet och dess underordnade element definierar vad som visas i tabellens rader.</span><span class="sxs-lookup"><span data-stu-id="a1052-152">The [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element and its child elements define what is displayed in the rows of the table.</span></span>

- <span data-ttu-id="a1052-153">[TableRowEntry](./listentry-element-for-listcontrol-format.md) -elementet tillhandahåller en definition av raden.</span><span class="sxs-lookup"><span data-stu-id="a1052-153">The [TableRowEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the row.</span></span> <span data-ttu-id="a1052-154">Minst en [TableRowEntry](./listentry-element-for-listcontrol-format.md) krävs. Det finns dock ingen övre gräns för antalet element som du kan lägga till.</span><span class="sxs-lookup"><span data-stu-id="a1052-154">At least one [TableRowEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="a1052-155">I de flesta fall har en vy bara en definition.</span><span class="sxs-lookup"><span data-stu-id="a1052-155">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="a1052-156">[EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) -elementet anger de objekt som visas av en bestämd definition.</span><span class="sxs-lookup"><span data-stu-id="a1052-156">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="a1052-157">Det här elementet är valfritt och behövs bara när du definierar flera [TableRowEntry](./listentry-element-for-listcontrol-format.md) -element som visar olika objekt.</span><span class="sxs-lookup"><span data-stu-id="a1052-157">This element is optional and is needed only when you define multiple [TableRowEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="a1052-158">Elementet [wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) anger att text som överskrider kolumn bredden visas på nästa rad.</span><span class="sxs-lookup"><span data-stu-id="a1052-158">The [Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) element specifies that text that exceeds the column width is displayed on the next line.</span></span> <span data-ttu-id="a1052-159">Som standard är text som överskrider kolumn bredden trunkerad.</span><span class="sxs-lookup"><span data-stu-id="a1052-159">By default, text that exceeds the column width is truncated.</span></span>

- <span data-ttu-id="a1052-160">[TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) -elementet definierar de egenskaper eller skript vars värden visas på raden.</span><span class="sxs-lookup"><span data-stu-id="a1052-160">The [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) element defines the properties or scripts whose values are displayed in the row.</span></span>

- <span data-ttu-id="a1052-161">[TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -elementet definierar egenskapen eller skriptet vars värde visas i kolumnen i raden.</span><span class="sxs-lookup"><span data-stu-id="a1052-161">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="a1052-162">Ett [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -element krävs för varje kolumn i raden.</span><span class="sxs-lookup"><span data-stu-id="a1052-162">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="a1052-163">Den första posten visas i första kolumnen, den andra posten i den andra kolumnen och så vidare.</span><span class="sxs-lookup"><span data-stu-id="a1052-163">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="a1052-164">Elementet [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) anger den egenskap vars värde visas i raden.</span><span class="sxs-lookup"><span data-stu-id="a1052-164">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="a1052-165">Du måste ange antingen en egenskap eller ett skript, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="a1052-165">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="a1052-166">[Script block](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) -elementet anger det skript vars värde visas i raden.</span><span class="sxs-lookup"><span data-stu-id="a1052-166">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="a1052-167">Du måste ange antingen ett skript eller en egenskap, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="a1052-167">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="a1052-168">[FormatString](./label-element-for-listitem-for-listcontrol-format.md) -elementet anger ett format mönster som definierar hur egenskapen eller skriptets värde visas.</span><span class="sxs-lookup"><span data-stu-id="a1052-168">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span> <span data-ttu-id="a1052-169">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="a1052-169">This element is optional.</span></span>

- <span data-ttu-id="a1052-170">Elementet [Alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) anger hur värdet för egenskapen eller skriptet visas.</span><span class="sxs-lookup"><span data-stu-id="a1052-170">The [Alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies how the value of the property or script is displayed.</span></span> <span data-ttu-id="a1052-171">Värdet kan justeras till vänster, till höger eller centreras.</span><span class="sxs-lookup"><span data-stu-id="a1052-171">The value can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="a1052-172">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="a1052-172">This element is optional.</span></span>

## <a name="defining-the-objects-that-use-the-table-view"></a><span data-ttu-id="a1052-173">Definiera de objekt som använder vyn tabellvy</span><span class="sxs-lookup"><span data-stu-id="a1052-173">Defining the Objects That Use the Table View</span></span>

<span data-ttu-id="a1052-174">Det finns två sätt att definiera vilka .NET-objekt som använder vyn tabellvy.</span><span class="sxs-lookup"><span data-stu-id="a1052-174">There are two ways to define which .NET objects use the table view.</span></span> <span data-ttu-id="a1052-175">Du kan använda [ViewSelectedBy](./viewselectedby-element-format.md) -elementet för att definiera de objekt som kan visas av alla definitioner i vyn, eller så kan du använda elementet [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) för att definiera vilka objekt som visas med en bestämd definition av vyn.</span><span class="sxs-lookup"><span data-stu-id="a1052-175">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="a1052-176">I de flesta fall har en vy bara en definition, så objekt definieras vanligt vis av [ViewSelectedBy](./viewselectedby-element-format.md) -elementet.</span><span class="sxs-lookup"><span data-stu-id="a1052-176">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="a1052-177">I följande exempel visas hur du definierar de objekt som visas i vyn tabell med hjälp av elementen [ViewSelectedBy](./viewselectedby-element-format.md) och [TypeName](./typename-element-for-viewselectedby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="a1052-177">The following example shows how to define the objects that are displayed by the table view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="a1052-178">Det finns ingen gräns för antalet element i [TypeName](./typename-element-for-viewselectedby-format.md) som du kan ange, och deras ordning är inte signifikant.</span><span class="sxs-lookup"><span data-stu-id="a1052-178">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="a1052-179">Följande XML-element kan användas för att ange de objekt som används i vyn tabellvy:</span><span class="sxs-lookup"><span data-stu-id="a1052-179">The following XML elements can be used to specify the objects that are used by the table view:</span></span>

- <span data-ttu-id="a1052-180">[ViewSelectedBy](./viewselectedby-element-format.md) -elementet definierar vilka objekt som visas i list visningen.</span><span class="sxs-lookup"><span data-stu-id="a1052-180">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="a1052-181">Elementet [TypeName](./typename-element-for-viewselectedby-format.md) anger det .net-objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="a1052-181">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="a1052-182">Fullständigt kvalificerat .NET-typnamn måste anges.</span><span class="sxs-lookup"><span data-stu-id="a1052-182">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="a1052-183">Du måste ange minst en typ eller urvals uppsättning för vyn, men det finns inget maximalt antal element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="a1052-183">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="a1052-184">I följande exempel används elementen [ViewSelectedBy](./viewselectedby-element-format.md) och [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="a1052-184">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="a1052-185">Använd markerings uppsättningar där du har en relaterad uppsättning objekt som visas med flera vyer, till exempel när du definierar en listvy och en tabellvy för samma objekt.</span><span class="sxs-lookup"><span data-stu-id="a1052-185">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="a1052-186">Mer information om hur du skapar en urvals uppsättning finns i [definiera urvals uppsättningar](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="a1052-186">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="a1052-187">Följande XML-element kan användas för att ange de objekt som används av list visningen:</span><span class="sxs-lookup"><span data-stu-id="a1052-187">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="a1052-188">[ViewSelectedBy](./viewselectedby-element-format.md) -elementet definierar vilka objekt som visas i list visningen.</span><span class="sxs-lookup"><span data-stu-id="a1052-188">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="a1052-189">[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) -elementet anger en uppsättning objekt som kan visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="a1052-189">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="a1052-190">Du måste ange minst en markerings uppsättning eller typ för vyn, men det finns inget maximalt antal element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="a1052-190">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="a1052-191">I följande exempel visas hur du definierar de objekt som visas av en bestämd definition i vyn tabell med hjälp av [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) -elementet.</span><span class="sxs-lookup"><span data-stu-id="a1052-191">The following example shows how to define the objects displayed by a specific definition of the table view using the [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="a1052-192">Med det här elementet kan du ange objektets .NET-typnamn, en urvals uppsättning objekt eller ett markerings villkor som anger när definitionen används.</span><span class="sxs-lookup"><span data-stu-id="a1052-192">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="a1052-193">Mer information om hur du skapar ett urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="a1052-193">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

> [!NOTE]
> <span data-ttu-id="a1052-194">När du skapar flera definitioner av tabellvy kan du inte ange olika kolumn rubriker.</span><span class="sxs-lookup"><span data-stu-id="a1052-194">When creating multiple definitions of the table view you cannot specify different column headers.</span></span> <span data-ttu-id="a1052-195">Du kan bara ange vad som visas i raderna i tabellen, till exempel vilka objekt som visas.</span><span class="sxs-lookup"><span data-stu-id="a1052-195">You can specify only what is displayed in the rows of the table, such as what objects are displayed.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

<span data-ttu-id="a1052-196">Följande XML-element kan användas för att ange de objekt som används av en bestämd definition av listvyn:</span><span class="sxs-lookup"><span data-stu-id="a1052-196">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="a1052-197">[EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) -elementet definierar vilka objekt som visas av definitionen.</span><span class="sxs-lookup"><span data-stu-id="a1052-197">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="a1052-198">Elementet [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) anger det .net-objekt som visas av definitionen.</span><span class="sxs-lookup"><span data-stu-id="a1052-198">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="a1052-199">När du använder det här elementet krävs det fullständigt kvalificerade .NET-typ namnet.</span><span class="sxs-lookup"><span data-stu-id="a1052-199">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="a1052-200">Du måste ange minst en typ, markerings uppsättning eller urvals villkor för definitionen, men det finns inget maximalt antal element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="a1052-200">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="a1052-201">[SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) -elementet (visas inte) anger en uppsättning objekt som kan visas av den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="a1052-201">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="a1052-202">Du måste ange minst en typ, markerings uppsättning eller urvals villkor för definitionen, men det finns inget maximalt antal element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="a1052-202">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="a1052-203">[SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) -elementet (visas inte) anger ett villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="a1052-203">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="a1052-204">Du måste ange minst en typ, markerings uppsättning eller urvals villkor för definitionen, men det finns inget maximalt antal element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="a1052-204">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="a1052-205">Mer information om hur du definierar urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="a1052-205">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="a1052-206">Använda format strängar</span><span class="sxs-lookup"><span data-stu-id="a1052-206">Using Format Strings</span></span>

<span data-ttu-id="a1052-207">Du kan lägga till format strängar i en vy för att ytterligare definiera hur data visas.</span><span class="sxs-lookup"><span data-stu-id="a1052-207">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="a1052-208">I följande exempel visas hur du definierar en format sträng för `StartTime` egenskapens värde.</span><span class="sxs-lookup"><span data-stu-id="a1052-208">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

<span data-ttu-id="a1052-209">Följande XML-element kan användas för att ange ett format mönster:</span><span class="sxs-lookup"><span data-stu-id="a1052-209">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="a1052-210">[TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -elementet definierar egenskapen eller skriptet vars värde visas i kolumnen i raden.</span><span class="sxs-lookup"><span data-stu-id="a1052-210">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="a1052-211">Ett [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -element krävs för varje kolumn i raden.</span><span class="sxs-lookup"><span data-stu-id="a1052-211">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="a1052-212">Den första posten visas i första kolumnen, den andra posten i den andra kolumnen och så vidare.</span><span class="sxs-lookup"><span data-stu-id="a1052-212">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="a1052-213">Elementet [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) anger den egenskap vars värde visas i raden.</span><span class="sxs-lookup"><span data-stu-id="a1052-213">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="a1052-214">Du måste ange antingen en egenskap eller ett skript, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="a1052-214">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="a1052-215">[FormatString](./label-element-for-listitem-for-listcontrol-format.md) -elementet anger ett format mönster som definierar hur egenskapen eller skriptets värde visas.</span><span class="sxs-lookup"><span data-stu-id="a1052-215">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="a1052-216">I följande exempel `ToString` kallas metoden för att formatera skriptets värde.</span><span class="sxs-lookup"><span data-stu-id="a1052-216">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="a1052-217">Skript kan anropa vilken metod som helst av ett objekt.</span><span class="sxs-lookup"><span data-stu-id="a1052-217">Scripts can call any method of an object.</span></span> <span data-ttu-id="a1052-218">Om ett objekt har en metod, till exempel `ToString` , som har format parametrar, kan skriptet anropa metoden för att formatera utdata för skriptet.</span><span class="sxs-lookup"><span data-stu-id="a1052-218">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="a1052-219">Följande XML-element kan användas för att anropa- `ToString` metoden:</span><span class="sxs-lookup"><span data-stu-id="a1052-219">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="a1052-220">[TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -elementet definierar egenskapen eller skriptet vars värde visas i kolumnen i raden.</span><span class="sxs-lookup"><span data-stu-id="a1052-220">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="a1052-221">Ett [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -element krävs för varje kolumn i raden.</span><span class="sxs-lookup"><span data-stu-id="a1052-221">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="a1052-222">Den första posten visas i första kolumnen, den andra posten i den andra kolumnen och så vidare.</span><span class="sxs-lookup"><span data-stu-id="a1052-222">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="a1052-223">[Script block](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) -elementet anger det skript vars värde visas i raden.</span><span class="sxs-lookup"><span data-stu-id="a1052-223">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="a1052-224">Du måste ange antingen ett skript eller en egenskap, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="a1052-224">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="a1052-225">Se även</span><span class="sxs-lookup"><span data-stu-id="a1052-225">See Also</span></span>

[<span data-ttu-id="a1052-226">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="a1052-226">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
