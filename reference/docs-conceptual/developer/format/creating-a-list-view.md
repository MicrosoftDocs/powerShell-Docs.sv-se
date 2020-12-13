---
ms.date: 09/13/2016
ms.topic: reference
title: Skapa en listvy
description: Skapa en listvy
ms.openlocfilehash: c34c4fddc27d4fd016fba37fc465924d693756a5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655646"
---
# <a name="creating-a-list-view"></a><span data-ttu-id="51abb-103">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="51abb-103">Creating a List View</span></span>

<span data-ttu-id="51abb-104">En listvy visar data i en enskild kolumn (i ordningsföljd).</span><span class="sxs-lookup"><span data-stu-id="51abb-104">A list view displays data in a single column (in sequential order).</span></span> <span data-ttu-id="51abb-105">De data som visas i listan kan vara värdet för en .NET-egenskap eller ett skripts värde.</span><span class="sxs-lookup"><span data-stu-id="51abb-105">The data displayed in the list can be the value of a .NET property or the value of a script.</span></span>

## <a name="a-list-view-display"></a><span data-ttu-id="51abb-106">Visa en listvy</span><span class="sxs-lookup"><span data-stu-id="51abb-106">A List View Display</span></span>

<span data-ttu-id="51abb-107">Följande utdata visar hur Windows PowerShell visar egenskaperna för [system. serviceprocess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -objekt som returneras av [Get-service](/powershell/module/microsoft.powershell.management/get-service) -cmdleten.</span><span class="sxs-lookup"><span data-stu-id="51abb-107">The following output shows how Windows PowerShell displays the properties of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects that are returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="51abb-108">I det här exemplet returnerades tre objekt, där varje objekt skiljs från föregående objekt med en tom rad.</span><span class="sxs-lookup"><span data-stu-id="51abb-108">In this example, three objects were returned, with each object separated from the preceding object by a blank line.</span></span>

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

## <a name="defining-the-list-view"></a><span data-ttu-id="51abb-109">Definiera listvyn</span><span class="sxs-lookup"><span data-stu-id="51abb-109">Defining the List View</span></span>

<span data-ttu-id="51abb-110">Följande XML visar schemat för List visning för att visa flera egenskaper för [system. serviceprocess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -objekt.</span><span class="sxs-lookup"><span data-stu-id="51abb-110">The following XML shows the list view schema for displaying several properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="51abb-111">Du måste ange varje egenskap som du vill ska visas i listvyn.</span><span class="sxs-lookup"><span data-stu-id="51abb-111">You must specify each property that you want displayed in the list view.</span></span>

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

<span data-ttu-id="51abb-112">Följande XML-element används för att definiera en listvy:</span><span class="sxs-lookup"><span data-stu-id="51abb-112">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="51abb-113">Elementet [View](./view-element-format.md) är det överordnade elementet i list visningen.</span><span class="sxs-lookup"><span data-stu-id="51abb-113">The [View](./view-element-format.md) element is the parent element of the list view.</span></span> <span data-ttu-id="51abb-114">(Detta är samma överordnade element för vyerna tabell, bred och anpassad kontroll.)</span><span class="sxs-lookup"><span data-stu-id="51abb-114">(This is the same parent element for the table, wide, and custom control views.)</span></span>

- <span data-ttu-id="51abb-115">Elementet [Name](./name-element-for-view-format.md) anger namnet på vyn.</span><span class="sxs-lookup"><span data-stu-id="51abb-115">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="51abb-116">Det här elementet krävs för alla vyer.</span><span class="sxs-lookup"><span data-stu-id="51abb-116">This element is required for all views.</span></span>

- <span data-ttu-id="51abb-117">[ViewSelectedBy](./viewselectedby-element-format.md) -elementet definierar de objekt som använder vyn.</span><span class="sxs-lookup"><span data-stu-id="51abb-117">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="51abb-118">Det här elementet är obligatoriskt.</span><span class="sxs-lookup"><span data-stu-id="51abb-118">This element is required.</span></span>

- <span data-ttu-id="51abb-119">Elementet [groupby](./groupby-element-for-view-format.md) definierar när en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="51abb-119">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="51abb-120">En ny grupp startas när värdet för en speciell egenskap eller skript ändras.</span><span class="sxs-lookup"><span data-stu-id="51abb-120">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="51abb-121">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="51abb-121">This element is optional.</span></span>

- <span data-ttu-id="51abb-122">Elementet [Controls](./controls-element-for-view-format.md) definierar de anpassade kontroller som definieras av list visningen.</span><span class="sxs-lookup"><span data-stu-id="51abb-122">The [Controls](./controls-element-for-view-format.md) element defines the custom controls that are defined by the list view.</span></span> <span data-ttu-id="51abb-123">Kontrollerna ger dig ett sätt att ytterligare ange hur data ska visas.</span><span class="sxs-lookup"><span data-stu-id="51abb-123">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="51abb-124">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="51abb-124">This element is optional.</span></span> <span data-ttu-id="51abb-125">En vy kan definiera egna anpassade kontroller, eller så kan den använda vanliga kontroller som kan användas av vilken vy som helst i format filen.</span><span class="sxs-lookup"><span data-stu-id="51abb-125">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="51abb-126">Mer information om anpassade kontroller finns i [skapa anpassade kontroller](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="51abb-126">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="51abb-127">[ListControl](./listcontrol-element-format.md) -elementet definierar vad som visas i vyn och hur det formateras.</span><span class="sxs-lookup"><span data-stu-id="51abb-127">The [ListControl](./listcontrol-element-format.md) element defines what is displayed in the view and how it is formatted.</span></span> <span data-ttu-id="51abb-128">På samma sätt som för alla andra vyer kan en listvy Visa värdena för objekt egenskaper eller värden som genereras av skript.</span><span class="sxs-lookup"><span data-stu-id="51abb-128">Similar to all other views, a list view can display the values of object properties or values generated by script.</span></span>

<span data-ttu-id="51abb-129">Ett exempel på en hel format fil som definierar en enkel listvy finns i [listvyn (grundläggande)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="51abb-129">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-list-view"></a><span data-ttu-id="51abb-130">Tillhandahålla definitioner för listvyn</span><span class="sxs-lookup"><span data-stu-id="51abb-130">Providing Definitions for Your List View</span></span>

<span data-ttu-id="51abb-131">Listvyer kan tillhandahålla en eller flera definitioner genom att använda de underordnade elementen i [ListControl](./listcontrol-element-format.md) -elementet.</span><span class="sxs-lookup"><span data-stu-id="51abb-131">List views can provide one or more definitions by using the child elements of the [ListControl](./listcontrol-element-format.md) element.</span></span> <span data-ttu-id="51abb-132">En vy är vanligt vis bara en definition.</span><span class="sxs-lookup"><span data-stu-id="51abb-132">Typically, a view will have only one definition.</span></span> <span data-ttu-id="51abb-133">I följande exempel tillhandahåller vyn en enda definition som visar flera egenskaper för [system. Diagnostics. process? Displayproperty = FullName](/dotnet/api/System.Diagnostics.Process) -objekt.</span><span class="sxs-lookup"><span data-stu-id="51abb-133">In the following example, the view provides a single definition that displays several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="51abb-134">En listvy kan visa värdet för en egenskap eller ett skripts värde (visas inte i exemplet).</span><span class="sxs-lookup"><span data-stu-id="51abb-134">A list view can display the value of a property or the value of a script (not shown in the example).</span></span>

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

<span data-ttu-id="51abb-135">Följande XML-element kan användas för att tillhandahålla definitioner för en listvy:</span><span class="sxs-lookup"><span data-stu-id="51abb-135">The following XML elements can be used to provide definitions for a list view:</span></span>

- <span data-ttu-id="51abb-136">[ListControl](./listcontrol-element-format.md) -elementet och dess underordnade element definierar vad som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="51abb-136">The [ListControl](./listcontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="51abb-137">[ListEntries](./listentries-element-for-listcontrol-format.md) -elementet innehåller definitionerna för vyn.</span><span class="sxs-lookup"><span data-stu-id="51abb-137">The [ListEntries](./listentries-element-for-listcontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="51abb-138">I de flesta fall har en vy bara en definition.</span><span class="sxs-lookup"><span data-stu-id="51abb-138">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="51abb-139">Det här elementet är obligatoriskt.</span><span class="sxs-lookup"><span data-stu-id="51abb-139">This element is required.</span></span>

- <span data-ttu-id="51abb-140">[ListEntry](./listentry-element-for-listcontrol-format.md) -elementet ger en definition av vyn.</span><span class="sxs-lookup"><span data-stu-id="51abb-140">The [ListEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="51abb-141">Minst en [ListEntry](./listentry-element-for-listcontrol-format.md) krävs. Det finns dock ingen övre gräns för antalet element som du kan lägga till.</span><span class="sxs-lookup"><span data-stu-id="51abb-141">At least one [ListEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="51abb-142">I de flesta fall har en vy bara en definition.</span><span class="sxs-lookup"><span data-stu-id="51abb-142">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="51abb-143">[EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) -elementet anger de objekt som visas av en bestämd definition.</span><span class="sxs-lookup"><span data-stu-id="51abb-143">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="51abb-144">Det här elementet är valfritt och behövs bara när du definierar flera [ListEntry](./listentry-element-for-listcontrol-format.md) -element som visar olika objekt.</span><span class="sxs-lookup"><span data-stu-id="51abb-144">This element is optional and is needed only when you define multiple [ListEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="51abb-145">[ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) -elementet anger de egenskaper och skript vars värden visas i raderna i listvyn.</span><span class="sxs-lookup"><span data-stu-id="51abb-145">The [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies the properties and scripts whose values are displayed in the rows of the list view.</span></span>

- <span data-ttu-id="51abb-146">[ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) -elementet anger en egenskap eller ett skript vars värde visas i en rad i list visningen.</span><span class="sxs-lookup"><span data-stu-id="51abb-146">The [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies a property or script whose value is displayed in a row of the list view.</span></span> <span data-ttu-id="51abb-147">En listvy måste ange minst en egenskap eller ett skript.</span><span class="sxs-lookup"><span data-stu-id="51abb-147">A list view must specify at least one property or script.</span></span> <span data-ttu-id="51abb-148">Det finns ingen övre gräns för antalet rader som kan anges.</span><span class="sxs-lookup"><span data-stu-id="51abb-148">There is no maximum limit to the number of rows that can be specified.</span></span>

- <span data-ttu-id="51abb-149">Elementet [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) anger den egenskap vars värde visas i raden.</span><span class="sxs-lookup"><span data-stu-id="51abb-149">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="51abb-150">Du måste ange antingen en egenskap eller ett skript, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="51abb-150">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="51abb-151">[Script block](./scriptblock-element-for-listitem-for-listcontrol-format.md) -elementet anger det skript vars värde visas i raden.</span><span class="sxs-lookup"><span data-stu-id="51abb-151">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="51abb-152">Du måste ange antingen ett skript eller en egenskap, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="51abb-152">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="51abb-153">Elementet [Label](./label-element-for-listitem-for-listcontrol-format.md) anger etiketten som visas till vänster om egenskapen eller skriptets värde i raden.</span><span class="sxs-lookup"><span data-stu-id="51abb-153">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element specifies the label that is displayed to the left of the property or script value in the row.</span></span> <span data-ttu-id="51abb-154">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="51abb-154">This element is optional.</span></span> <span data-ttu-id="51abb-155">Om en etikett inte anges visas namnet på egenskapen eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="51abb-155">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="51abb-156">Ett fullständigt exempel finns i [listvyn (etiketter)](./list-view-labels.md).</span><span class="sxs-lookup"><span data-stu-id="51abb-156">For a complete example, see [List View (Labels)](./list-view-labels.md).</span></span>

- <span data-ttu-id="51abb-157">[ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) -elementet anger ett villkor som måste finnas för att raden ska visas.</span><span class="sxs-lookup"><span data-stu-id="51abb-157">The [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) element specifies a condition that must exist for the row to be displayed.</span></span> <span data-ttu-id="51abb-158">Mer information om hur du lägger till villkor i listvyn finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="51abb-158">For more information about adding conditions to the list view, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span> <span data-ttu-id="51abb-159">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="51abb-159">This element is optional.</span></span>

- <span data-ttu-id="51abb-160">Elementet [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) anger ett mönster som används för att visa värdet för egenskapen eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="51abb-160">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a pattern that is used to display the value of the property or script.</span></span> <span data-ttu-id="51abb-161">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="51abb-161">This element is optional.</span></span>

<span data-ttu-id="51abb-162">Ett exempel på en hel format fil som definierar en enkel listvy finns i [listvyn (grundläggande)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="51abb-162">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-list-view"></a><span data-ttu-id="51abb-163">Definiera de objekt som använder list visningen</span><span class="sxs-lookup"><span data-stu-id="51abb-163">Defining the Objects That Use the List View</span></span>

<span data-ttu-id="51abb-164">Det finns två sätt att definiera vilka .NET-objekt som ska använda List visningen.</span><span class="sxs-lookup"><span data-stu-id="51abb-164">There are two ways to define which .NET objects use the list view.</span></span> <span data-ttu-id="51abb-165">Du kan använda [ViewSelectedBy](./viewselectedby-element-format.md) -elementet för att definiera de objekt som kan visas av alla definitioner i vyn, eller så kan du använda elementet [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) för att definiera vilka objekt som visas med en bestämd definition av vyn.</span><span class="sxs-lookup"><span data-stu-id="51abb-165">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="51abb-166">I de flesta fall har en vy bara en definition, så objekt definieras vanligt vis av [ViewSelectedBy](./viewselectedby-element-format.md) -elementet.</span><span class="sxs-lookup"><span data-stu-id="51abb-166">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="51abb-167">I följande exempel visas hur du definierar de objekt som visas i list visningen med hjälp av elementen [ViewSelectedBy](./viewselectedby-element-format.md) och [TypeName](./typename-element-for-viewselectedby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="51abb-167">The following example shows how to define the objects that are displayed by the list view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="51abb-168">Det finns ingen gräns för antalet element i [TypeName](./typename-element-for-viewselectedby-format.md) som du kan ange, och deras ordning är inte signifikant.</span><span class="sxs-lookup"><span data-stu-id="51abb-168">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="51abb-169">Följande XML-element kan användas för att ange de objekt som används av list visningen:</span><span class="sxs-lookup"><span data-stu-id="51abb-169">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="51abb-170">[ViewSelectedBy](./viewselectedby-element-format.md) -elementet definierar vilka objekt som visas i list visningen.</span><span class="sxs-lookup"><span data-stu-id="51abb-170">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="51abb-171">Elementet [TypeName](./typename-element-for-viewselectedby-format.md) anger det .net-objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="51abb-171">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="51abb-172">Fullständigt kvalificerat .NET-typnamn måste anges.</span><span class="sxs-lookup"><span data-stu-id="51abb-172">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="51abb-173">Du måste ange minst en typ eller urvals uppsättning för vyn, men det finns inget maximalt antal element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="51abb-173">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="51abb-174">Ett exempel på en hel format fil finns i [listvyn (grundläggande)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="51abb-174">For an example of a complete formatting file, see [List View (Basic)](./list-view-basic.md).</span></span>

<span data-ttu-id="51abb-175">I följande exempel används elementen [ViewSelectedBy](./viewselectedby-element-format.md) och [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="51abb-175">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="51abb-176">Använd markerings uppsättningar där du har en relaterad uppsättning objekt som visas med flera vyer, till exempel när du definierar en listvy och en tabellvy för samma objekt.</span><span class="sxs-lookup"><span data-stu-id="51abb-176">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="51abb-177">Mer information om hur du skapar en urvals uppsättning finns i [definiera urvals uppsättningar](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="51abb-177">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="51abb-178">Följande XML-element kan användas för att ange de objekt som används av list visningen:</span><span class="sxs-lookup"><span data-stu-id="51abb-178">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="51abb-179">[ViewSelectedBy](./viewselectedby-element-format.md) -elementet definierar vilka objekt som visas i list visningen.</span><span class="sxs-lookup"><span data-stu-id="51abb-179">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="51abb-180">[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) -elementet anger en uppsättning objekt som kan visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="51abb-180">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="51abb-181">Du måste ange minst en markerings uppsättning eller typ för vyn, men det finns inget maximalt antal element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="51abb-181">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="51abb-182">I följande exempel visas hur du definierar de objekt som visas av en bestämd definition av list visningen med hjälp av [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) -elementet.</span><span class="sxs-lookup"><span data-stu-id="51abb-182">The following example shows how to define the objects displayed by a specific definition of the list view using the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element.</span></span> <span data-ttu-id="51abb-183">Med det här elementet kan du ange objektets .NET-typnamn, en urvals uppsättning objekt eller ett markerings villkor som anger när definitionen används.</span><span class="sxs-lookup"><span data-stu-id="51abb-183">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="51abb-184">Mer information om hur du skapar ett urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="51abb-184">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

<span data-ttu-id="51abb-185">Följande XML-element kan användas för att ange de objekt som används av en bestämd definition av listvyn:</span><span class="sxs-lookup"><span data-stu-id="51abb-185">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="51abb-186">[EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) -elementet definierar vilka objekt som visas av definitionen.</span><span class="sxs-lookup"><span data-stu-id="51abb-186">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="51abb-187">Elementet [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) anger det .net-objekt som visas av definitionen.</span><span class="sxs-lookup"><span data-stu-id="51abb-187">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="51abb-188">När du använder det här elementet krävs det fullständigt kvalificerade .NET-typ namnet.</span><span class="sxs-lookup"><span data-stu-id="51abb-188">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="51abb-189">Du måste ange minst en typ, markerings uppsättning eller urvals villkor för definitionen, men det finns inget maximalt antal element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="51abb-189">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="51abb-190">[SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) -elementet (visas inte) anger en uppsättning objekt som kan visas av den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="51abb-190">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="51abb-191">Du måste ange minst en typ, markerings uppsättning eller urvals villkor för definitionen, men det finns inget maximalt antal element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="51abb-191">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="51abb-192">[SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) -elementet (visas inte) anger ett villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="51abb-192">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="51abb-193">Du måste ange minst en typ, markerings uppsättning eller urvals villkor för definitionen, men det finns inget maximalt antal element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="51abb-193">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="51abb-194">Mer information om hur du definierar urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="51abb-194">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-list-view"></a><span data-ttu-id="51abb-195">Visa grupper av objekt i en listvy</span><span class="sxs-lookup"><span data-stu-id="51abb-195">Displaying Groups of Objects in a List View</span></span>

<span data-ttu-id="51abb-196">Du kan separera de objekt som visas i list visningen i grupper.</span><span class="sxs-lookup"><span data-stu-id="51abb-196">You can separate the objects that are displayed by the list view into groups.</span></span> <span data-ttu-id="51abb-197">Det innebär inte att du definierar en grupp, bara att Windows PowerShell startar en ny grupp när värdet för en speciell egenskap eller skript ändras.</span><span class="sxs-lookup"><span data-stu-id="51abb-197">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="51abb-198">I följande exempel startas en ny grupp när värdet för egenskapen [system. serviceprocess. ServiceController. ServiceType](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) ändras.</span><span class="sxs-lookup"><span data-stu-id="51abb-198">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="51abb-199">Följande XML-element används för att definiera när en grupp startas:</span><span class="sxs-lookup"><span data-stu-id="51abb-199">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="51abb-200">Elementet [groupby](./groupby-element-for-view-format.md) definierar egenskapen eller skriptet som startar den nya gruppen och definierar hur gruppen visas.</span><span class="sxs-lookup"><span data-stu-id="51abb-200">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="51abb-201">Elementet [PropertyName](./propertyname-element-for-groupby-format.md) anger den egenskap som startar en ny grupp när dess värde ändras.</span><span class="sxs-lookup"><span data-stu-id="51abb-201">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="51abb-202">Du måste ange en egenskap eller ett skript för att starta gruppen, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="51abb-202">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="51abb-203">[Script block](./scriptblock-element-for-groupby-format.md) -elementet anger det skript som startar en ny grupp när dess värde ändras.</span><span class="sxs-lookup"><span data-stu-id="51abb-203">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="51abb-204">Du måste ange ett skript eller en egenskap för att starta gruppen, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="51abb-204">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="51abb-205">Elementet [Label](./label-element-for-groupby-format.md) definierar en etikett som visas i början av varje grupp.</span><span class="sxs-lookup"><span data-stu-id="51abb-205">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="51abb-206">Utöver den text som anges av det här elementet visar Windows PowerShell värdet som utlöste den nya gruppen och lägger till en tom rad före och efter etiketten.</span><span class="sxs-lookup"><span data-stu-id="51abb-206">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="51abb-207">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="51abb-207">This element is optional.</span></span>

- <span data-ttu-id="51abb-208">[CustomControl](./customcontrol-element-for-groupby-format.md) -elementet definierar en kontroll som används för att visa data.</span><span class="sxs-lookup"><span data-stu-id="51abb-208">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="51abb-209">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="51abb-209">This element is optional.</span></span>

- <span data-ttu-id="51abb-210">[CustomControlName](./customcontrolname-element-for-groupby-format.md) -elementet anger en common-eller View-kontroll som används för att visa data.</span><span class="sxs-lookup"><span data-stu-id="51abb-210">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="51abb-211">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="51abb-211">This element is optional.</span></span>

<span data-ttu-id="51abb-212">Ett exempel på en hel format fil som definierar grupper finns i [listvyn (groupby)](./list-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="51abb-212">For an example of a complete formatting file that defines groups, see [List View (GroupBy)](./list-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="51abb-213">Använda format strängar</span><span class="sxs-lookup"><span data-stu-id="51abb-213">Using Format Strings</span></span>

<span data-ttu-id="51abb-214">Du kan lägga till format strängar i en vy för att ytterligare definiera hur data visas.</span><span class="sxs-lookup"><span data-stu-id="51abb-214">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="51abb-215">I följande exempel visas hur du definierar en format sträng för `StartTime` egenskapens värde.</span><span class="sxs-lookup"><span data-stu-id="51abb-215">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

<span data-ttu-id="51abb-216">Följande XML-element kan användas för att ange ett format mönster:</span><span class="sxs-lookup"><span data-stu-id="51abb-216">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="51abb-217">[ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) -elementet anger de data som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="51abb-217">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="51abb-218">Elementet [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) anger den egenskap vars värde visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="51abb-218">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="51abb-219">Du måste ange antingen en egenskap eller ett skript, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="51abb-219">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="51abb-220">[FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) -elementet anger ett format mönster som definierar hur egenskapen eller skriptets värde visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="51abb-220">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

- <span data-ttu-id="51abb-221">[Script block](./scriptblock-element-for-listitem-for-listcontrol-format.md) -elementet (visas inte) anger det skript vars värde visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="51abb-221">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="51abb-222">Du måste ange antingen ett skript eller en egenskap, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="51abb-222">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="51abb-223">I följande exempel `ToString` kallas metoden för att formatera skriptets värde.</span><span class="sxs-lookup"><span data-stu-id="51abb-223">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="51abb-224">Skript kan anropa vilken metod som helst av ett objekt.</span><span class="sxs-lookup"><span data-stu-id="51abb-224">Scripts can call any method of an object.</span></span> <span data-ttu-id="51abb-225">Om ett objekt har en metod, till exempel `ToString` , som har format parametrar, kan skriptet anropa metoden för att formatera utdata för skriptet.</span><span class="sxs-lookup"><span data-stu-id="51abb-225">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="51abb-226">Följande XML-element kan användas för att anropa- `ToString` metoden:</span><span class="sxs-lookup"><span data-stu-id="51abb-226">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="51abb-227">[ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) -elementet anger de data som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="51abb-227">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="51abb-228">[Script block](./scriptblock-element-for-listitem-for-listcontrol-format.md) -elementet (visas inte) anger det skript vars värde visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="51abb-228">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="51abb-229">Du måste ange antingen ett skript eller en egenskap, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="51abb-229">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="51abb-230">Se även</span><span class="sxs-lookup"><span data-stu-id="51abb-230">See Also</span></span>

[<span data-ttu-id="51abb-231">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="51abb-231">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/writing-a-windows-powershell-cmdlet.md)
