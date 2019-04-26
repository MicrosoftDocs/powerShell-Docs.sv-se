---
title: Skapa en listvy | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c7a40ca-1786-46f0-bab5-6ce229daa7ee
caps.latest.revision: 14
ms.openlocfilehash: 25d24063501196d44e0f806a55bb699c82f771ce
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066863"
---
# <a name="creating-a-list-view"></a><span data-ttu-id="e98ab-102">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="e98ab-102">Creating a List View</span></span>

<span data-ttu-id="e98ab-103">En listvy visar data i en enda kolumn (i sekventiell ordning).</span><span class="sxs-lookup"><span data-stu-id="e98ab-103">A list view displays data in a single column (in sequential order).</span></span> <span data-ttu-id="e98ab-104">Data som visas i listan kan vara värdet för en egenskap för .NET eller värdet för ett skript.</span><span class="sxs-lookup"><span data-stu-id="e98ab-104">The data displayed in the list can be the value of a .NET property or the value of a script.</span></span>

## <a name="a-list-view-display"></a><span data-ttu-id="e98ab-105">Visa en lista över vyn</span><span class="sxs-lookup"><span data-stu-id="e98ab-105">A List View Display</span></span>

<span data-ttu-id="e98ab-106">Följande utdata visar hur Windows PowerShell visar egenskaperna för [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objekt som returneras av den [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e98ab-106">The following output shows how Windows PowerShell displays the properties of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects that are returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="e98ab-107">I det här exemplet är returnerades tre objekt, med varje objekt avgränsas från det föregående objektet med en tom rad.</span><span class="sxs-lookup"><span data-stu-id="e98ab-107">In this example, three objects were returned, with each object separated from the preceding object by a blank line.</span></span>

```powershell
Get-Service | format-list
```

```output
Name                : AEADIFilters
DisplayName         : Andrea ADI Filters Service
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess

Name                : AeLookupSvc
DisplayName         : Application Experience
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32ShareProcess

Name                : AgereModemAudio
DisplayName         : Agere Modem Call Progress Audio
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess
...
```

## <a name="defining-the-list-view"></a><span data-ttu-id="e98ab-108">Definiera listvyn</span><span class="sxs-lookup"><span data-stu-id="e98ab-108">Defining the List View</span></span>

<span data-ttu-id="e98ab-109">Följande XML visas listan Visa schemat för att visa flera egenskaper för den [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objekt.</span><span class="sxs-lookup"><span data-stu-id="e98ab-109">The following XML shows the list view schema for displaying several properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="e98ab-110">Du måste ange varje egenskap som du vill ska visas i listvyn.</span><span class="sxs-lookup"><span data-stu-id="e98ab-110">You must specify each property that you want displayed in the list view.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

<span data-ttu-id="e98ab-111">Följande XML-element används för att definiera en listvy:</span><span class="sxs-lookup"><span data-stu-id="e98ab-111">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="e98ab-112">Den [visa](./view-element-format.md) elementet har det överordnade elementet i listvyn.</span><span class="sxs-lookup"><span data-stu-id="e98ab-112">The [View](./view-element-format.md) element is the parent element of the list view.</span></span> <span data-ttu-id="e98ab-113">(Detta är samma överordnade element för tabellen, bred och anpassade vyer.)</span><span class="sxs-lookup"><span data-stu-id="e98ab-113">(This is the same parent element for the table, wide, and custom control views.)</span></span>

- <span data-ttu-id="e98ab-114">Den [namn](./name-element-for-view-format.md) elementet anger namnet på vyn.</span><span class="sxs-lookup"><span data-stu-id="e98ab-114">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="e98ab-115">Det här elementet krävs för alla vyer.</span><span class="sxs-lookup"><span data-stu-id="e98ab-115">This element is required for all views.</span></span>

- <span data-ttu-id="e98ab-116">Den [ViewSelectedBy](./viewselectedby-element-format.md) elementet definierar de objekt som använder vyn.</span><span class="sxs-lookup"><span data-stu-id="e98ab-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="e98ab-117">Det här elementet krävs.</span><span class="sxs-lookup"><span data-stu-id="e98ab-117">This element is required.</span></span>

- <span data-ttu-id="e98ab-118">Den [GroupBy](./groupby-element-for-view-format.md) elementet definierar när en ny grupp med objekt visas.</span><span class="sxs-lookup"><span data-stu-id="e98ab-118">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="e98ab-119">En ny grupp har startats när värdet för en specifik egenskap eller ett skript ändras.</span><span class="sxs-lookup"><span data-stu-id="e98ab-119">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="e98ab-120">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="e98ab-120">This element is optional.</span></span>

- <span data-ttu-id="e98ab-121">Den [kontroller](./controls-element-for-view-format.md) elementet definierar de anpassade kontroller som definieras av listvyn.</span><span class="sxs-lookup"><span data-stu-id="e98ab-121">The [Controls](./controls-element-for-view-format.md) element defines the custom controls that are defined by the list view.</span></span> <span data-ttu-id="e98ab-122">Kontroller ger dig ett sätt som specificerar hur data visas.</span><span class="sxs-lookup"><span data-stu-id="e98ab-122">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="e98ab-123">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="e98ab-123">This element is optional.</span></span> <span data-ttu-id="e98ab-124">En vy kan definiera egna anpassade kontroller eller använda vanliga kontroller som kan användas av alla vyer i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="e98ab-124">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="e98ab-125">Mer information om anpassade kontroller finns i [skapar anpassade kontroller](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="e98ab-125">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="e98ab-126">Den [ListControl](./listcontrol-element-format.md) elementet definierar vad som visas i vyn och hur den formateras.</span><span class="sxs-lookup"><span data-stu-id="e98ab-126">The [ListControl](./listcontrol-element-format.md) element defines what is displayed in the view and how it is formatted.</span></span> <span data-ttu-id="e98ab-127">Precis som alla andra vyer, en listvy kan visa värdena för objektegenskaper eller värden som genererats av skriptet.</span><span class="sxs-lookup"><span data-stu-id="e98ab-127">Similar to all other views, a list view can display the values of object properties or values generated by script.</span></span>

<span data-ttu-id="e98ab-128">Ett exempel på en fullständig formatering fil som definierar en enkel lista vy finns i [listvyn (grundläggande)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="e98ab-128">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-list-view"></a><span data-ttu-id="e98ab-129">Att tillhandahålla definitioner för din listvy</span><span class="sxs-lookup"><span data-stu-id="e98ab-129">Providing Definitions for Your List View</span></span>

<span data-ttu-id="e98ab-130">Listvyer kan tillhandahålla en eller flera definitioner med hjälp av de underordnade elementen i den [ListControl](./listcontrol-element-format.md) element.</span><span class="sxs-lookup"><span data-stu-id="e98ab-130">List views can provide one or more definitions by using the child elements of the [ListControl](./listcontrol-element-format.md) element.</span></span> <span data-ttu-id="e98ab-131">Vyn har vanligtvis bara en definition.</span><span class="sxs-lookup"><span data-stu-id="e98ab-131">Typically, a view will have only one definition.</span></span> <span data-ttu-id="e98ab-132">I följande exempel visas vyn ger en enda definition som visar flera egenskaper för den [System.Diagnostics.Process? Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) objekt.</span><span class="sxs-lookup"><span data-stu-id="e98ab-132">In the following example, the view provides a single definition that displays several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="e98ab-133">En listvy kan visa värdet för en egenskap eller värdet för ett skript (visas inte i det här exemplet).</span><span class="sxs-lookup"><span data-stu-id="e98ab-133">A list view can display the value of a property or the value of a script (not shown in the example).</span></span>

```xml
<ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>

```

<span data-ttu-id="e98ab-134">Följande XML-element kan användas för att ange definitioner för en listvy:</span><span class="sxs-lookup"><span data-stu-id="e98ab-134">The following XML elements can be used to provide definitions for a list view:</span></span>

- <span data-ttu-id="e98ab-135">Den [ListControl](./listcontrol-element-format.md) elementet och dess underordnade element definierar vad som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="e98ab-135">The [ListControl](./listcontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="e98ab-136">Den [ListEntries](./listentries-element-for-listcontrol-format.md) elementet innehåller definitioner av vyn.</span><span class="sxs-lookup"><span data-stu-id="e98ab-136">The [ListEntries](./listentries-element-for-listcontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="e98ab-137">I de flesta fall har en vy endast en definition.</span><span class="sxs-lookup"><span data-stu-id="e98ab-137">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="e98ab-138">Det här elementet krävs.</span><span class="sxs-lookup"><span data-stu-id="e98ab-138">This element is required.</span></span>

- <span data-ttu-id="e98ab-139">Den [ListEntry](./listentry-element-for-listcontrol-format.md) elementet innehåller en definition för vyn.</span><span class="sxs-lookup"><span data-stu-id="e98ab-139">The [ListEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="e98ab-140">Minst en [ListEntry](./listentry-element-for-listcontrol-format.md) krävs, men det finns ingen högsta gräns för antalet element som du kan lägga till.</span><span class="sxs-lookup"><span data-stu-id="e98ab-140">At least one [ListEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="e98ab-141">I de flesta fall har en vy endast en definition.</span><span class="sxs-lookup"><span data-stu-id="e98ab-141">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="e98ab-142">Den [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elementet anger de objekt som visas som en viss definition.</span><span class="sxs-lookup"><span data-stu-id="e98ab-142">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="e98ab-143">Det här elementet är valfritt och krävs bara när du definierar flera [ListEntry](./listentry-element-for-listcontrol-format.md) element som visar olika objekt.</span><span class="sxs-lookup"><span data-stu-id="e98ab-143">This element is optional and is needed only when you define multiple [ListEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="e98ab-144">Den [ListItems som finns](./listitems-element-for-listentry-for-listcontrol-format.md) elementet anger egenskaperna och skript vars värden visas i raderna i listvyn.</span><span class="sxs-lookup"><span data-stu-id="e98ab-144">The [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies the properties and scripts whose values are displayed in the rows of the list view.</span></span>

- <span data-ttu-id="e98ab-145">Den [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) elementet anger en egenskap eller ett skript som vars värde visas i en rad i listvyn.</span><span class="sxs-lookup"><span data-stu-id="e98ab-145">The [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies a property or script whose value is displayed in a row of the list view.</span></span> <span data-ttu-id="e98ab-146">En listvy måste ange minst en egenskap eller skript.</span><span class="sxs-lookup"><span data-stu-id="e98ab-146">A list view must specify at least one property or script.</span></span> <span data-ttu-id="e98ab-147">Det finns ingen högsta gräns för hur många rader som kan anges.</span><span class="sxs-lookup"><span data-stu-id="e98ab-147">There is no maximum limit to the number of rows that can be specified.</span></span>

- <span data-ttu-id="e98ab-148">Den [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elementet anger egenskapen vars värde visas i raden.</span><span class="sxs-lookup"><span data-stu-id="e98ab-148">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="e98ab-149">Du måste ange en egenskap eller ett skript, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="e98ab-149">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="e98ab-150">Den [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) elementet anger skriptet vars värde visas i raden.</span><span class="sxs-lookup"><span data-stu-id="e98ab-150">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="e98ab-151">Du måste ange ett skript eller en egenskap, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="e98ab-151">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="e98ab-152">Den [etikett](./label-element-for-listitem-for-listcontrol-format.md) elementet anger etiketten som visas till vänster om värdet för egenskapen eller skript på raden.</span><span class="sxs-lookup"><span data-stu-id="e98ab-152">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element specifies the label that is displayed to the left of the property or script value in the row.</span></span> <span data-ttu-id="e98ab-153">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="e98ab-153">This element is optional.</span></span> <span data-ttu-id="e98ab-154">Om en etikett inte anges visas namnet på egenskapen eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="e98ab-154">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="e98ab-155">Ett komplett exempel finns i [listvyn (etiketter)](./list-view-labels.md).</span><span class="sxs-lookup"><span data-stu-id="e98ab-155">For a complete example, see [List View (Labels)](./list-view-labels.md).</span></span>

- <span data-ttu-id="e98ab-156">Den [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) elementet anger ett villkor som måste finnas för raden som ska visas.</span><span class="sxs-lookup"><span data-stu-id="e98ab-156">The [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) element specifies a condition that must exist for the row to be displayed.</span></span> <span data-ttu-id="e98ab-157">Läs mer om att lägga till villkor listvyn [definiera villkor för att visa Data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e98ab-157">For more information about adding conditions to the list view, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span> <span data-ttu-id="e98ab-158">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="e98ab-158">This element is optional.</span></span>

- <span data-ttu-id="e98ab-159">Den [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) elementet anger ett mönster som används för att visa värdet för egenskapen eller skript.</span><span class="sxs-lookup"><span data-stu-id="e98ab-159">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a pattern that is used to display the value of the property or script.</span></span> <span data-ttu-id="e98ab-160">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="e98ab-160">This element is optional.</span></span>

<span data-ttu-id="e98ab-161">Ett exempel på en fullständig formatering fil som definierar en enkel lista vy finns i [listvyn (grundläggande)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="e98ab-161">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-list-view"></a><span data-ttu-id="e98ab-162">Definiera de objekt som använder listvyn</span><span class="sxs-lookup"><span data-stu-id="e98ab-162">Defining the Objects That Use the List View</span></span>

<span data-ttu-id="e98ab-163">Det finns två sätt att definiera vilka .NET-objekt använder listvyn.</span><span class="sxs-lookup"><span data-stu-id="e98ab-163">There are two ways to define which .NET objects use the list view.</span></span> <span data-ttu-id="e98ab-164">Du kan använda den [ViewSelectedBy](./viewselectedby-element-format.md) element för att definiera de objekt som kan visas av alla definitioner av vyn eller du kan använda den [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element för att definiera vilka objekt visas som en viss definition för vyn.</span><span class="sxs-lookup"><span data-stu-id="e98ab-164">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="e98ab-165">I de flesta fall har endast en definition i en vy så objekt definieras vanligtvis av den [ViewSelectedBy](./viewselectedby-element-format.md) element.</span><span class="sxs-lookup"><span data-stu-id="e98ab-165">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="e98ab-166">I följande exempel visas hur du definierar de objekt som visas genom att visa listan med de [ViewSelectedBy](./viewselectedby-element-format.md) och [TypeName](./typename-element-for-viewselectedby-format.md) element.</span><span class="sxs-lookup"><span data-stu-id="e98ab-166">The following example shows how to define the objects that are displayed by the list view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="e98ab-167">Det finns ingen gräns för hur många [TypeName](./typename-element-for-viewselectedby-format.md) element att du kan ange och deras inbördes ordning är inte särskilt stor.</span><span class="sxs-lookup"><span data-stu-id="e98ab-167">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="e98ab-168">Följande XML-element kan användas för att ange objekt som används av listvyn:</span><span class="sxs-lookup"><span data-stu-id="e98ab-168">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="e98ab-169">Den [ViewSelectedBy](./viewselectedby-element-format.md) elementet definierar vilka objekt visas i listvyn.</span><span class="sxs-lookup"><span data-stu-id="e98ab-169">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="e98ab-170">Den [TypeName](./typename-element-for-viewselectedby-format.md) elementet anger .NET-objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="e98ab-170">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="e98ab-171">Det fullständigt kvalificerade typnamnet .NET krävs.</span><span class="sxs-lookup"><span data-stu-id="e98ab-171">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="e98ab-172">Du måste ange minst en typ eller val som angetts för vyn, men det finns inget högsta antal element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="e98ab-172">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="e98ab-173">Ett exempel på en fullständig formatering fil, se [listvyn (grundläggande)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="e98ab-173">For an example of a complete formatting file, see [List View (Basic)](./list-view-basic.md).</span></span>

<span data-ttu-id="e98ab-174">I följande exempel används den [ViewSelectedBy](./viewselectedby-element-format.md) och [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element.</span><span class="sxs-lookup"><span data-stu-id="e98ab-174">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="e98ab-175">Använd val av där du har en uppsättning objekt som visas med flera vyer, till exempel när du definierar en listvy och en tabellvy för samma objekt.</span><span class="sxs-lookup"><span data-stu-id="e98ab-175">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="e98ab-176">Läs mer om hur du skapar en [definiera val av uppsättningar](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="e98ab-176">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="e98ab-177">Följande XML-element kan användas för att ange objekt som används av listvyn:</span><span class="sxs-lookup"><span data-stu-id="e98ab-177">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="e98ab-178">Den [ViewSelectedBy](./viewselectedby-element-format.md) elementet definierar vilka objekt visas i listvyn.</span><span class="sxs-lookup"><span data-stu-id="e98ab-178">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="e98ab-179">Den [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementet anger en uppsättning objekt som kan visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="e98ab-179">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="e98ab-180">Du måste ange minst en markering set eller typ för vyn, men det finns inget högsta antal element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="e98ab-180">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="e98ab-181">I följande exempel visas hur du definierar de objekt som visas av en viss definition av visa listan med de [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element.</span><span class="sxs-lookup"><span data-stu-id="e98ab-181">The following example shows how to define the objects displayed by a specific definition of the list view using the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element.</span></span> <span data-ttu-id="e98ab-182">Med det här elementet kan ange du namnet på .NET objektet, val av flera objekt eller ett val av villkor som anger när definitionen används.</span><span class="sxs-lookup"><span data-stu-id="e98ab-182">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="e98ab-183">Mer information om hur du skapar ett urval villkor finns i [definiera villkor för att visa Data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e98ab-183">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

<span data-ttu-id="e98ab-184">Följande XML-element kan användas för att ange objekt som används av en viss definition av listvyn:</span><span class="sxs-lookup"><span data-stu-id="e98ab-184">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="e98ab-185">Den [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) elementet definierar vilka objekt visas i definitionen.</span><span class="sxs-lookup"><span data-stu-id="e98ab-185">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="e98ab-186">Den [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) elementet anger .NET-objekt som visas när definitionen.</span><span class="sxs-lookup"><span data-stu-id="e98ab-186">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="e98ab-187">När du använder det här elementet krävs det fullständigt kvalificerade typnamnet för .NET.</span><span class="sxs-lookup"><span data-stu-id="e98ab-187">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="e98ab-188">Du måste ange minst en typ, val av set eller urvalsvillkoret för definitionen, men det finns inget högsta antal element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="e98ab-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="e98ab-189">Den [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (visas inte) anger en uppsättning objekt som kan visas av denna definition.</span><span class="sxs-lookup"><span data-stu-id="e98ab-189">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="e98ab-190">Du måste ange minst en typ, val av set eller urvalsvillkoret för definitionen, men det finns inget högsta antal element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="e98ab-190">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="e98ab-191">Den [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (visas inte) anger ett villkor som måste finnas för den här definitionen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="e98ab-191">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="e98ab-192">Du måste ange minst en typ, val av set eller urvalsvillkoret för definitionen, men det finns inget högsta antal element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="e98ab-192">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="e98ab-193">Läs mer om hur du definierar villkoren för val av [definiera villkor för att visa Data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e98ab-193">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-list-view"></a><span data-ttu-id="e98ab-194">Visa grupper med objekt i en listvy</span><span class="sxs-lookup"><span data-stu-id="e98ab-194">Displaying Groups of Objects in a List View</span></span>

<span data-ttu-id="e98ab-195">Du kan avgränsa de objekt som visas i listvyn i grupper.</span><span class="sxs-lookup"><span data-stu-id="e98ab-195">You can separate the objects that are displayed by the list view into groups.</span></span> <span data-ttu-id="e98ab-196">Detta innebär inte att du definierar en grupp, endast att Windows PowerShell startar en ny grupp när en specifik egenskap eller ett skript ändras.</span><span class="sxs-lookup"><span data-stu-id="e98ab-196">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="e98ab-197">I följande exempel visas en ny grupp har startats när värdet för den [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) egenskapsändringar.</span><span class="sxs-lookup"><span data-stu-id="e98ab-197">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="e98ab-198">Följande XML-element används för att definiera när en grupp startas:</span><span class="sxs-lookup"><span data-stu-id="e98ab-198">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="e98ab-199">Den [GroupBy](./groupby-element-for-view-format.md) elementet definierar egenskapen eller skript som startar den nya gruppen och definierar hur gruppen visas.</span><span class="sxs-lookup"><span data-stu-id="e98ab-199">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="e98ab-200">Den [PropertyName](./propertyname-element-for-groupby-format.md) elementet anger den egenskap som startar en ny grupp när dess värde ändras.</span><span class="sxs-lookup"><span data-stu-id="e98ab-200">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="e98ab-201">Du måste ange en egenskap eller ett skript för att starta gruppen, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="e98ab-201">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="e98ab-202">Den [ScriptBlock](./scriptblock-element-for-groupby-format.md) elementet anger det skript som startar en ny grupp när dess värde ändras.</span><span class="sxs-lookup"><span data-stu-id="e98ab-202">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="e98ab-203">Du måste ange ett skript eller en egenskap för att starta gruppen, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="e98ab-203">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="e98ab-204">Den [etikett](./label-element-for-groupby-format.md) elementet definierar en etikett som visas i början av varje grupp.</span><span class="sxs-lookup"><span data-stu-id="e98ab-204">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="e98ab-205">Förutom den text som anges av det här elementet, visar det värde som utlöste den nya gruppen och lägger till en tom rad före och efter etiketten i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e98ab-205">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="e98ab-206">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="e98ab-206">This element is optional.</span></span>

- <span data-ttu-id="e98ab-207">Den [anpassad kontroll](./customcontrol-element-for-groupby-format.md) elementet definierar en kontroll som används för att visa data.</span><span class="sxs-lookup"><span data-stu-id="e98ab-207">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="e98ab-208">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="e98ab-208">This element is optional.</span></span>

- <span data-ttu-id="e98ab-209">Den [CustomControlName](./customcontrolname-element-for-groupby-format.md) elementet anger ett vanligt eller visa kontroll som används för att visa data.</span><span class="sxs-lookup"><span data-stu-id="e98ab-209">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="e98ab-210">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="e98ab-210">This element is optional.</span></span>

<span data-ttu-id="e98ab-211">Ett exempel på en fullständig formatering fil som definierar grupper finns i [listvyn (GroupBy)](./list-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="e98ab-211">For an example of a complete formatting file that defines groups, see [List View (GroupBy)](./list-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="e98ab-212">Med hjälp av formatsträngar</span><span class="sxs-lookup"><span data-stu-id="e98ab-212">Using Format Strings</span></span>

<span data-ttu-id="e98ab-213">Formatering strängar kan läggas till en vy för att ytterligare definiera hur data visas.</span><span class="sxs-lookup"><span data-stu-id="e98ab-213">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="e98ab-214">I följande exempel visas hur du definierar en formateringssträngen för värdet för den `StartTime` egenskapen.</span><span class="sxs-lookup"><span data-stu-id="e98ab-214">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

<span data-ttu-id="e98ab-215">Följande XML-element kan användas för att ange ett:</span><span class="sxs-lookup"><span data-stu-id="e98ab-215">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="e98ab-216">Den [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) elementet anger de data som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="e98ab-216">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="e98ab-217">Den [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elementet anger egenskapen vars värde visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="e98ab-217">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="e98ab-218">Du måste ange en egenskap eller ett skript, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="e98ab-218">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="e98ab-219">Den [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) elementet anger ett formatmönster som definierar hur värdet för egenskapen eller skript visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="e98ab-219">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

- <span data-ttu-id="e98ab-220">Den [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (visas inte) anger skriptet vars värde visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="e98ab-220">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="e98ab-221">Du måste ange ett skript eller en egenskap, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="e98ab-221">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="e98ab-222">I följande exempel visas den `ToString` metoden anropas för att formatera värdet för skriptet.</span><span class="sxs-lookup"><span data-stu-id="e98ab-222">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="e98ab-223">Skript kan anropa någon-metod för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="e98ab-223">Scripts can call any method of an object.</span></span> <span data-ttu-id="e98ab-224">Därför, om ett objekt har en metod som `ToString`, som har formateringsparametrar, skriptet kan anropa metoden för att formatera utdatavärdet för skriptet.</span><span class="sxs-lookup"><span data-stu-id="e98ab-224">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="e98ab-225">Följande XML-element som kan användas för att anropa den `ToString` metoden:</span><span class="sxs-lookup"><span data-stu-id="e98ab-225">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="e98ab-226">Den [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) elementet anger de data som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="e98ab-226">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="e98ab-227">Den [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (visas inte) anger skriptet vars värde visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="e98ab-227">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="e98ab-228">Du måste ange ett skript eller en egenskap, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="e98ab-228">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="e98ab-229">Se även</span><span class="sxs-lookup"><span data-stu-id="e98ab-229">See Also</span></span>

[<span data-ttu-id="e98ab-230">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e98ab-230">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/writing-a-windows-powershell-cmdlet.md)
