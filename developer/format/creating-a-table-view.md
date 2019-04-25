---
title: Skapa en tabellvy | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f405afb-70b5-4fe0-9986-bc07401d93fd
caps.latest.revision: 23
ms.openlocfilehash: 862f942facafff6cea66c4f8f1040772c6a62ec3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066846"
---
# <a name="creating-a-table-view"></a><span data-ttu-id="3b9c8-102">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="3b9c8-102">Creating a Table View</span></span>

<span data-ttu-id="3b9c8-103">En tabellvy visar data i en eller flera kolumner.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-103">A table view displays data in one or more columns.</span></span> <span data-ttu-id="3b9c8-104">Varje rad i tabellen representerar ett .NET-objekt och varje kolumn i tabellen representerar en egenskap för objektet eller ett skriptvärde.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-104">Each row in the table represents a .NET object, and each column of the table represents a property of the object or a script value.</span></span> <span data-ttu-id="3b9c8-105">Du kan definiera en tabellvy som visar alla egenskaper för ett objekt eller en delmängd av egenskaperna för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-105">You can define a table view that displays all the properties of an object or a subset of the properties of an object.</span></span>

## <a name="a-table-view-display"></a><span data-ttu-id="3b9c8-106">En tabell visa visning</span><span class="sxs-lookup"><span data-stu-id="3b9c8-106">A Table View Display</span></span>

<span data-ttu-id="3b9c8-107">I följande exempel visas hur Windows PowerShell visar den [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objekt som returneras av den [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-107">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="3b9c8-108">För det här objektet Windows PowerShell har definierat en tabellvy som visar den `Status` egenskapen den `Name` egenskapen (den här egenskapen är en egenskap för alias för den `ServiceName` egenskapen), och `DisplayName` egenskapen.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-108">For this object, Windows PowerShell has defined a table view that displays the `Status` property, the `Name` property (this property is an alias property for the `ServiceName` property), and the `DisplayName` property.</span></span> <span data-ttu-id="3b9c8-109">Varje rad i tabellen representerar ett objekt som returneras av cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-109">Each row in the table represents an object returned by the cmdlet.</span></span>

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a><span data-ttu-id="3b9c8-110">Definiera tabellvyn</span><span class="sxs-lookup"><span data-stu-id="3b9c8-110">Defining the Table View</span></span>

<span data-ttu-id="3b9c8-111">Följande XML visar Visa tabellschemat för att visa den [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objekt.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-111">The following XML shows the table view schema for displaying the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="3b9c8-112">Du måste ange varje egenskap som du vill ska visas i tabellvyn.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-112">You must specify each property that you want displayed in the table view.</span></span>

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

<span data-ttu-id="3b9c8-113">Följande XML-element används för att definiera en listvy:</span><span class="sxs-lookup"><span data-stu-id="3b9c8-113">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="3b9c8-114">Den [visa](./view-element-format.md) elementet har det överordnade elementet i tabellvyn.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-114">The [View](./view-element-format.md) element is the parent element of the table view.</span></span> <span data-ttu-id="3b9c8-115">(Detta är samma överordnade element lista, bred och anpassade vyer.)</span><span class="sxs-lookup"><span data-stu-id="3b9c8-115">(This is the same parent element for the list, wide, and custom control views.)</span></span>

- <span data-ttu-id="3b9c8-116">Den [namn](./name-element-for-view-format.md) elementet anger namnet på vyn.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-116">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="3b9c8-117">Det här elementet krävs för alla vyer.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-117">This element is required for all views.</span></span>

- <span data-ttu-id="3b9c8-118">Den [ViewSelectedBy](./viewselectedby-element-format.md) elementet definierar de objekt som använder vyn.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-118">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="3b9c8-119">Det här elementet krävs.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-119">This element is required.</span></span>

- <span data-ttu-id="3b9c8-120">Den [GroupBy](./groupby-element-for-view-format.md) (visas inte i det här exemplet)-elementet definierar när en ny grupp med objekt visas.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-120">The [GroupBy](./groupby-element-for-view-format.md) element (not shown in this example) defines when a new group of objects is displayed.</span></span> <span data-ttu-id="3b9c8-121">En ny grupp har startats när värdet för en specifik egenskap eller ett skript ändras.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-121">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="3b9c8-122">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-122">This element is optional.</span></span>

- <span data-ttu-id="3b9c8-123">Den [kontroller](./controls-element-for-view-format.md) (visas inte i det här exemplet)-elementet definierar de anpassade kontroller som definieras av tabellvyn.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-123">The [Controls](./controls-element-for-view-format.md) element (not shown in this example) defines the custom controls that are defined by the table view.</span></span> <span data-ttu-id="3b9c8-124">Kontroller ger dig ett sätt som specificerar hur data visas.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-124">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="3b9c8-125">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-125">This element is optional.</span></span> <span data-ttu-id="3b9c8-126">En vy kan definiera egna anpassade kontroller eller använda vanliga kontroller som kan användas av alla vyer i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-126">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="3b9c8-127">Mer information om anpassade kontroller finns i [skapar anpassade kontroller](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="3b9c8-127">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="3b9c8-128">Den [HideTableHeaders](./hidetableheaders-element-format.md) element (inte visas i det här exemplet) anger att tabellen inte visar alla etiketter överst i tabellen.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-128">The [HideTableHeaders](./hidetableheaders-element-format.md) element (not show in this example) specifies that the table will not show any labels at the top of the table.</span></span> <span data-ttu-id="3b9c8-129">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-129">This element is optional.</span></span>

- <span data-ttu-id="3b9c8-130">Den [TableControl](./tablecontrol-element-format.md) element som definierar informationen som rubrik och raden i tabellen.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-130">The [TableControl](./tablecontrol-element-format.md) element that defines the header and row information of the table.</span></span> <span data-ttu-id="3b9c8-131">Precis som alla andra vyer, en tabellvy kan visa värdena för objektegenskaper eller värden som genererats av skript.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-131">Similar to all other views, a table view can display the values of object properties or values generated by scripts.</span></span>

## <a name="defining-column-headers"></a><span data-ttu-id="3b9c8-132">Definiera kolumnrubriker</span><span class="sxs-lookup"><span data-stu-id="3b9c8-132">Defining Column Headers</span></span>

1. <span data-ttu-id="3b9c8-133">Den [TableHeaders](./tableheaders-element-format.md) elementet och dess underordnade element definierar vad som visas överst i tabellen.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-133">The [TableHeaders](./tableheaders-element-format.md) element and its child elements define what is displayed at the top of the table.</span></span>

2. <span data-ttu-id="3b9c8-134">Den [TableColumnHeader](./tablecolumnheader-element-format.md) elementet definierar vad som visas överst i en kolumn i tabellen.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-134">The [TableColumnHeader](./tablecolumnheader-element-format.md) element defines what is displayed at the top of a column of the table.</span></span> <span data-ttu-id="3b9c8-135">Ange de här elementen i den ordning som du vill att de rubriker som visas.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-135">Specify these elements in the order that you want the headers displayed.</span></span>

   <span data-ttu-id="3b9c8-136">Det finns ingen gräns för hur många av dessa element som du kan använda, men antalet [TableColumnHeader](./tablecolumnheader-element-format.md) element i tabellvyn måste vara lika med antalet [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) element som du använder.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-136">There is no limit to the number of these element that you can use, but the number of [TableColumnHeader](./tablecolumnheader-element-format.md) elements in your table view must equal the number of [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) elements that you use.</span></span>

3. <span data-ttu-id="3b9c8-137">Den [etikett](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) elementet anger den text som visas.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-137">The [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the text that is displayed.</span></span> <span data-ttu-id="3b9c8-138">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-138">This element is optional.</span></span>

4. <span data-ttu-id="3b9c8-139">Den [bredd](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) elementet anger bredden (i antal tecken) för kolumnen.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-139">The [Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the width (in characters) of the column.</span></span> <span data-ttu-id="3b9c8-140">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-140">This element is optional.</span></span>

5. <span data-ttu-id="3b9c8-141">Den [justering](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) elementet anger hur etiketten visas.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-141">The [Alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies how the label is displayed.</span></span> <span data-ttu-id="3b9c8-142">Etiketten kan justeras till vänster till höger, eller centrerad.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-142">The label can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="3b9c8-143">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-143">This element is optional.</span></span>

## <a name="defining-the-table-rows"></a><span data-ttu-id="3b9c8-144">Definiera tabellraderna</span><span class="sxs-lookup"><span data-stu-id="3b9c8-144">Defining the Table Rows</span></span>

<span data-ttu-id="3b9c8-145">Tabellvyer kan ge en eller flera definitioner som anger vilka data som visas i raderna i tabellen med hjälp av de underordnade elementen i den [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-145">Table views can provide one or more definitions that specify what data is displayed in the rows of the table by using the child elements of the [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="3b9c8-146">Observera att du kan ange flera definitioner för raderna i tabellen, men rubrikerna för rader förblir detsamma oavsett vilken raddefinition används.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-146">Notice that you can specify multiple definitions for the rows of the table, but the headers for the rows remains the same, regardless of what row definition is used.</span></span> <span data-ttu-id="3b9c8-147">En tabell har vanligtvis bara en definition.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-147">Typically, a table will have only one definition.</span></span>

<span data-ttu-id="3b9c8-148">I följande exempel visas vyn ger en enda definition som visar värdena för flera egenskaper för den [System.Diagnostics.Process? Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) objekt.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-148">In the following example, the view provides a single definition that displays the values of several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="3b9c8-149">En tabellvy kan visa värdet för en egenskap eller värdet för ett skript (visas inte i det här exemplet) i sina rader.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-149">A table view can display the value of a property or the value of a script (not shown in the example) in its rows.</span></span>

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

<span data-ttu-id="3b9c8-150">Följande XML-element kan användas för att ange definitioner för en rad:</span><span class="sxs-lookup"><span data-stu-id="3b9c8-150">The following XML elements can be used to provide definitions for a row:</span></span>

- <span data-ttu-id="3b9c8-151">Den [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) elementet och dess underordnade element definierar vad som visas i raderna i tabellen.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-151">The [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element and its child elements define what is displayed in the rows of the table.</span></span>

- <span data-ttu-id="3b9c8-152">Den [TableRowEntry](./listentry-element-for-listcontrol-format.md) elementet innehåller en definition av raden.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-152">The [TableRowEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the row.</span></span> <span data-ttu-id="3b9c8-153">Minst en [TableRowEntry](./listentry-element-for-listcontrol-format.md) krävs, men det finns ingen högsta gräns för antalet element som du kan lägga till.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-153">At least one [TableRowEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="3b9c8-154">I de flesta fall har en vy endast en definition.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-154">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="3b9c8-155">Den [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) elementet anger de objekt som visas som en viss definition.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-155">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="3b9c8-156">Det här elementet är valfritt och krävs bara när du definierar flera [TableRowEntry](./listentry-element-for-listcontrol-format.md) element som visar olika objekt.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-156">This element is optional and is needed only when you define multiple [TableRowEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="3b9c8-157">Den [omsluta](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) elementet anger att text som överskrider kolumnbredden visas på nästa rad.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-157">The [Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) element specifies that text that exceeds the column width is displayed on the next line.</span></span> <span data-ttu-id="3b9c8-158">Som standard trunkeras text som överskrider kolumnbredden.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-158">By default, text that exceeds the column width is truncated.</span></span>

- <span data-ttu-id="3b9c8-159">Den [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) elementet definierar de egenskaper eller skript som vars värden visas i raden.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-159">The [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) element defines the properties or scripts whose values are displayed in the row.</span></span>

- <span data-ttu-id="3b9c8-160">Den [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elementet definierar egenskapen eller skript som vars värde visas i kolumnen i raden.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-160">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="3b9c8-161">En [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element krävs för varje kolumn i raden.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-161">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="3b9c8-162">Den första posten visas i första kolumnen, den andra posten i den andra kolumnen och så vidare.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-162">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="3b9c8-163">Den [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) elementet anger egenskapen vars värde visas i raden.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-163">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="3b9c8-164">Du måste ange en egenskap eller ett skript, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-164">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="3b9c8-165">Den [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) elementet anger skriptet vars värde visas i raden.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-165">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="3b9c8-166">Du måste ange ett skript eller en egenskap, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-166">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="3b9c8-167">Den [FormatString](./label-element-for-listitem-for-listcontrol-format.md) elementet anger ett formatmönster som definierar hur värdet för egenskapen eller skript visas.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-167">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span> <span data-ttu-id="3b9c8-168">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-168">This element is optional.</span></span>

- <span data-ttu-id="3b9c8-169">Den [justering](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) elementet anger hur värdet för egenskapen eller skript visas.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-169">The [Alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies how the value of the property or script is displayed.</span></span> <span data-ttu-id="3b9c8-170">Värdet kan justeras till vänster till höger, eller centrerad.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-170">The value can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="3b9c8-171">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-171">This element is optional.</span></span>

## <a name="defining-the-objects-that-use-the-table-view"></a><span data-ttu-id="3b9c8-172">Definiera de objekt som använder tabellvyn</span><span class="sxs-lookup"><span data-stu-id="3b9c8-172">Defining the Objects That Use the Table View</span></span>

<span data-ttu-id="3b9c8-173">Det finns två sätt att definiera vilka .NET-objekt använder tabellvyn.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-173">There are two ways to define which .NET objects use the table view.</span></span> <span data-ttu-id="3b9c8-174">Du kan använda den [ViewSelectedBy](./viewselectedby-element-format.md) element för att definiera de objekt som kan visas av alla definitioner av vyn eller du kan använda den [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element för att definiera vilka objekt visas som en viss definition för vyn.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-174">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="3b9c8-175">I de flesta fall har endast en definition i en vy så objekt definieras vanligtvis av den [ViewSelectedBy](./viewselectedby-element-format.md) element.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-175">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="3b9c8-176">I följande exempel visas hur du definierar de objekt som visas genom att visa tabellen med den [ViewSelectedBy](./viewselectedby-element-format.md) och [TypeName](./typename-element-for-viewselectedby-format.md) element.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-176">The following example shows how to define the objects that are displayed by the table view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="3b9c8-177">Det finns ingen gräns för hur många [TypeName](./typename-element-for-viewselectedby-format.md) element att du kan ange och deras inbördes ordning är inte särskilt stor.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-177">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="3b9c8-178">Följande XML-element kan användas för att ange objekt som används av tabellvyn:</span><span class="sxs-lookup"><span data-stu-id="3b9c8-178">The following XML elements can be used to specify the objects that are used by the table view:</span></span>

- <span data-ttu-id="3b9c8-179">Den [ViewSelectedBy](./viewselectedby-element-format.md) elementet definierar vilka objekt visas i listvyn.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-179">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="3b9c8-180">Den [TypeName](./typename-element-for-viewselectedby-format.md) elementet anger .NET-objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-180">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="3b9c8-181">Det fullständigt kvalificerade typnamnet .NET krävs.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-181">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="3b9c8-182">Du måste ange minst en typ eller val som angetts för vyn, men det finns inget högsta antal element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-182">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="3b9c8-183">I följande exempel används den [ViewSelectedBy](./viewselectedby-element-format.md) och [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-183">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="3b9c8-184">Använd val av där du har en uppsättning objekt som visas med flera vyer, till exempel när du definierar en listvy och en tabellvy för samma objekt.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-184">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="3b9c8-185">Läs mer om hur du skapar en [definiera val av uppsättningar](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="3b9c8-185">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="3b9c8-186">Följande XML-element kan användas för att ange objekt som används av listvyn:</span><span class="sxs-lookup"><span data-stu-id="3b9c8-186">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="3b9c8-187">Den [ViewSelectedBy](./viewselectedby-element-format.md) elementet definierar vilka objekt visas i listvyn.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-187">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="3b9c8-188">Den [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementet anger en uppsättning objekt som kan visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-188">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="3b9c8-189">Du måste ange minst en markering set eller typ för vyn, men det finns inget högsta antal element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-189">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="3b9c8-190">I följande exempel visas hur du definierar de objekt som visas av en viss definition av tabellen vy med den [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-190">The following example shows how to define the objects displayed by a specific definition of the table view using the [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="3b9c8-191">Med det här elementet kan ange du namnet på .NET objektet, val av flera objekt eller ett val av villkor som anger när definitionen används.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-191">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="3b9c8-192">Mer information om hur du skapar ett urval villkor finns i [definiera villkor för att visa Data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="3b9c8-192">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

> [!NOTE]
> <span data-ttu-id="3b9c8-193">När du skapar flera definitioner av tabellvyn kan du inte ange olika kolumnrubriker.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-193">When creating multiple definitions of the table view you cannot specify different column headers.</span></span> <span data-ttu-id="3b9c8-194">Du kan ange bara vad som visas på raderna i tabellen, till exempel vilka objekt visas.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-194">You can specify only what is displayed in the rows of the table, such as what objects are displayed.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

<span data-ttu-id="3b9c8-195">Följande XML-element kan användas för att ange objekt som används av en viss definition av listvyn:</span><span class="sxs-lookup"><span data-stu-id="3b9c8-195">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="3b9c8-196">Den [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) elementet definierar vilka objekt visas i definitionen.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-196">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="3b9c8-197">Den [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) elementet anger .NET-objekt som visas när definitionen.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-197">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="3b9c8-198">När du använder det här elementet krävs det fullständigt kvalificerade typnamnet för .NET.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-198">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="3b9c8-199">Du måste ange minst en typ, val av set eller urvalsvillkoret för definitionen, men det finns inget högsta antal element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-199">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="3b9c8-200">Den [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (visas inte) anger en uppsättning objekt som kan visas av denna definition.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-200">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="3b9c8-201">Du måste ange minst en typ, val av set eller urvalsvillkoret för definitionen, men det finns inget högsta antal element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-201">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="3b9c8-202">Den [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (visas inte) anger ett villkor som måste finnas för den här definitionen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-202">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="3b9c8-203">Du måste ange minst en typ, val av set eller urvalsvillkoret för definitionen, men det finns inget högsta antal element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-203">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="3b9c8-204">Läs mer om hur du definierar villkoren för val av [definiera villkor för att visa Data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="3b9c8-204">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="3b9c8-205">Med hjälp av formatsträngar</span><span class="sxs-lookup"><span data-stu-id="3b9c8-205">Using Format Strings</span></span>

<span data-ttu-id="3b9c8-206">Formatering strängar kan läggas till en vy för att ytterligare definiera hur data visas.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-206">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="3b9c8-207">I följande exempel visas hur du definierar en formateringssträngen för värdet för den `StartTime` egenskapen.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-207">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

<span data-ttu-id="3b9c8-208">Följande XML-element kan användas för att ange ett:</span><span class="sxs-lookup"><span data-stu-id="3b9c8-208">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="3b9c8-209">Den [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elementet definierar egenskapen eller skript som vars värde visas i kolumnen i raden.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-209">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="3b9c8-210">En [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element krävs för varje kolumn i raden.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-210">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="3b9c8-211">Den första posten visas i första kolumnen, den andra posten i den andra kolumnen och så vidare.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-211">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="3b9c8-212">Den [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) elementet anger egenskapen vars värde visas i raden.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-212">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="3b9c8-213">Du måste ange en egenskap eller ett skript, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-213">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="3b9c8-214">Den [FormatString](./label-element-for-listitem-for-listcontrol-format.md) elementet anger ett formatmönster som definierar hur värdet för egenskapen eller skript visas.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-214">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="3b9c8-215">I följande exempel visas den `ToString` metoden anropas för att formatera värdet för skriptet.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-215">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="3b9c8-216">Skript kan anropa någon-metod för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-216">Scripts can call any method of an object.</span></span> <span data-ttu-id="3b9c8-217">Därför, om ett objekt har en metod som `ToString`, som har formateringsparametrar, skriptet kan anropa metoden för att formatera utdatavärdet för skriptet.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-217">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="3b9c8-218">Följande XML-element som kan användas för att anropa den `ToString` metoden:</span><span class="sxs-lookup"><span data-stu-id="3b9c8-218">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="3b9c8-219">Den [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) elementet definierar egenskapen eller skript som vars värde visas i kolumnen i raden.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-219">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="3b9c8-220">En [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element krävs för varje kolumn i raden.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-220">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="3b9c8-221">Den första posten visas i första kolumnen, den andra posten i den andra kolumnen och så vidare.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-221">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="3b9c8-222">Den [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) elementet anger skriptet vars värde visas i raden.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-222">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="3b9c8-223">Du måste ange ett skript eller en egenskap, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="3b9c8-223">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="3b9c8-224">Se även</span><span class="sxs-lookup"><span data-stu-id="3b9c8-224">See Also</span></span>

[<span data-ttu-id="3b9c8-225">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="3b9c8-225">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
