---
title: Skapa en bred vy | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d4303c5-b451-4ccb-9831-b17a17ceac20
caps.latest.revision: 16
ms.openlocfilehash: 651de5d3bc2619f20438f3951ac5a8c4b0bf46d4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359073"
---
# <a name="creating-a-wide-view"></a><span data-ttu-id="c42dd-102">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="c42dd-102">Creating a Wide View</span></span>

<span data-ttu-id="c42dd-103">En bred vy visar ett enda värde för varje objekt som visas.</span><span class="sxs-lookup"><span data-stu-id="c42dd-103">A wide view displays a single value for each object that is displayed.</span></span> <span data-ttu-id="c42dd-104">Det visade värdet kan vara värdet för en .NET-objekt egenskap eller ett skripts värde.</span><span class="sxs-lookup"><span data-stu-id="c42dd-104">The displayed value can be the value of a .NET object property or the value of a script.</span></span> <span data-ttu-id="c42dd-105">Som standard finns det ingen etikett eller rubrik för den här vyn.</span><span class="sxs-lookup"><span data-stu-id="c42dd-105">By default, there is no label or header for this view.</span></span>

## <a name="a-wide-view-display"></a><span data-ttu-id="c42dd-106">En bred vy-skärm</span><span class="sxs-lookup"><span data-stu-id="c42dd-106">A Wide View Display</span></span>

<span data-ttu-id="c42dd-107">I följande exempel visas hur Windows PowerShell visar objektet [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) som returneras av cmdleten [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) när dess utdata är skickas till den [format breda](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c42dd-107">The following example shows how Windows PowerShell displays the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object that is returned by the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet when its output is piped to the [Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet.</span></span> <span data-ttu-id="c42dd-108">(Som standard returnerar cmdleten [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) en tabellvy.) I det här exemplet används de två kolumnerna för att visa namnet på processen för varje returnerat objekt.</span><span class="sxs-lookup"><span data-stu-id="c42dd-108">(By default, the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns a table view.) In this example, the two columns are used to display the name of the process for each returned object.</span></span> <span data-ttu-id="c42dd-109">Namnet på objektets egenskap visas inte, bara egenskapens värde.</span><span class="sxs-lookup"><span data-stu-id="c42dd-109">The name of the object's property is not displayed, only the value of the property.</span></span>

```
Get-Process | format-wide
AEADISRV                     agrsmsvc
Ati2evxx                     Ati2evxx
audiodg                      CCC
CcmExec                      communicator
Crypserv                     csrss
csrss                        DevDtct2
DM1Service                   dpupdchk
dwm                          DxStudio
EXCEL                        explorer
GoogleToolbarNotifier        GrooveMonitor
hpqwmiex                     hpservice
Idle                         InoRpc
InoRT                        InoTask
ipoint                       lsass
lsm                          MOM
MSASCui                      notepad
...                          ...

```

## <a name="defining-the-wide-view"></a><span data-ttu-id="c42dd-110">Definiera den breda vyn</span><span class="sxs-lookup"><span data-stu-id="c42dd-110">Defining the Wide View</span></span>

<span data-ttu-id="c42dd-111">Följande XML visar wide View-schemat för objektet [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="c42dd-111">The following XML shows the wide view schema for the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <GroupBy>...</GroupBy>
  <Controls>...</Controls>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

<span data-ttu-id="c42dd-112">Följande XML-element används för att definiera en bred vy:</span><span class="sxs-lookup"><span data-stu-id="c42dd-112">The following XML elements are used to define a wide view:</span></span>

- <span data-ttu-id="c42dd-113">Elementet [View](./view-element-format.md) är det överordnade elementet i den breda vyn.</span><span class="sxs-lookup"><span data-stu-id="c42dd-113">The [View](./view-element-format.md) element is the parent element of the wide view.</span></span> <span data-ttu-id="c42dd-114">(Detta är samma överordnade element för vyerna tabell, lista och anpassad kontroll.)</span><span class="sxs-lookup"><span data-stu-id="c42dd-114">(This is the same parent element for the table, list, and custom control views.)</span></span>

- <span data-ttu-id="c42dd-115">Elementet [Name](./name-element-for-view-format.md) anger namnet på vyn.</span><span class="sxs-lookup"><span data-stu-id="c42dd-115">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="c42dd-116">Det här elementet krävs för alla vyer.</span><span class="sxs-lookup"><span data-stu-id="c42dd-116">This element is required for all views.</span></span>

- <span data-ttu-id="c42dd-117">[ViewSelectedBy](./viewselectedby-element-format.md) -elementet definierar de objekt som använder vyn.</span><span class="sxs-lookup"><span data-stu-id="c42dd-117">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="c42dd-118">Det här elementet är obligatoriskt.</span><span class="sxs-lookup"><span data-stu-id="c42dd-118">This element is required.</span></span>

- <span data-ttu-id="c42dd-119">Elementet [groupby](./groupby-element-for-view-format.md) definierar när en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="c42dd-119">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="c42dd-120">En ny grupp startas när värdet för en speciell egenskap eller skript ändras.</span><span class="sxs-lookup"><span data-stu-id="c42dd-120">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="c42dd-121">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="c42dd-121">This element is optional.</span></span>

- <span data-ttu-id="c42dd-122">[Kontroll](./controls-element-for-view-format.md) elementen definierar de anpassade kontroller som definieras av den breda vyn.</span><span class="sxs-lookup"><span data-stu-id="c42dd-122">The [Controls](./controls-element-for-view-format.md) elements defines the custom controls that are defined by the wide view.</span></span> <span data-ttu-id="c42dd-123">Kontrollerna ger dig ett sätt att ytterligare ange hur data ska visas.</span><span class="sxs-lookup"><span data-stu-id="c42dd-123">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="c42dd-124">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="c42dd-124">This element is optional.</span></span> <span data-ttu-id="c42dd-125">En vy kan definiera egna anpassade kontroller, eller så kan den använda vanliga kontroller som kan användas av vilken vy som helst i format filen.</span><span class="sxs-lookup"><span data-stu-id="c42dd-125">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="c42dd-126">Mer information om anpassade kontroller finns i [skapa anpassade kontroller](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="c42dd-126">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="c42dd-127">[WideControl](./widecontrol-element-format.md) -elementet och dess underordnade element definierar vad som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="c42dd-127">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span> <span data-ttu-id="c42dd-128">I föregående exempel är vyn utformad för att visa egenskapen [system. Diagnostics. process. processname](/dotnet/api/System.Diagnostics.Process.ProcessName) .</span><span class="sxs-lookup"><span data-stu-id="c42dd-128">In the preceding example, the view is designed to display the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span>

<span data-ttu-id="c42dd-129">Ett exempel på en hel format fil som definierar en enkel bred vy finns i [wide View (grundläggande)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="c42dd-129">For an example of a complete formatting file that defines a simple wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-wide-view"></a><span data-ttu-id="c42dd-130">Tillhandahålla definitioner för din bred vy</span><span class="sxs-lookup"><span data-stu-id="c42dd-130">Providing Definitions for Your Wide View</span></span>

<span data-ttu-id="c42dd-131">Breda vyer kan tillhandahålla en eller flera definitioner genom att använda de underordnade elementen i [WideControl](./widecontrol-element-format.md) -elementet.</span><span class="sxs-lookup"><span data-stu-id="c42dd-131">Wide views can provide one or more definitions by using the child elements of the [WideControl](./widecontrol-element-format.md) element.</span></span> <span data-ttu-id="c42dd-132">En vy är vanligt vis bara en definition.</span><span class="sxs-lookup"><span data-stu-id="c42dd-132">Typically, a view will have only one definition.</span></span> <span data-ttu-id="c42dd-133">I följande exempel tillhandahåller vyn en enda definition som visar värdet för egenskapen [system. Diagnostics. process. processname](/dotnet/api/System.Diagnostics.Process.ProcessName) .</span><span class="sxs-lookup"><span data-stu-id="c42dd-133">In the following example, the view provides a single definition that displays the value of the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span> <span data-ttu-id="c42dd-134">En bred vy kan visa värdet för en egenskap eller ett skripts värde (visas inte i exemplet).</span><span class="sxs-lookup"><span data-stu-id="c42dd-134">A wide view can display the value of a property or the value of a script (not shown in the example).</span></span>

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber></ColumnNumber>
  <WideEntries>
    <WideEntry>
      <WideItem>
        <PropertyName>ProcessName</PropertyName>
      </WideItem>
    </WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="c42dd-135">Följande XML-element kan användas för att tillhandahålla definitioner för en bred vy:</span><span class="sxs-lookup"><span data-stu-id="c42dd-135">The following XML elements can be used to provide definitions for a wide view:</span></span>

- <span data-ttu-id="c42dd-136">[WideControl](./widecontrol-element-format.md) -elementet och dess underordnade element definierar vad som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="c42dd-136">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="c42dd-137">Elementet [AutoSize](./autosize-element-for-widecontrol-format.md) anger om kolumn storleken och antalet kolumner justeras baserat på data storleken.</span><span class="sxs-lookup"><span data-stu-id="c42dd-137">The [AutoSize](./autosize-element-for-widecontrol-format.md) element specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span> <span data-ttu-id="c42dd-138">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="c42dd-138">This element is optional.</span></span>

- <span data-ttu-id="c42dd-139">[ColumnNumber](./columnnumber-element-for-widecontrol-format.md) -elementet anger antalet kolumner som visas i den breda vyn.</span><span class="sxs-lookup"><span data-stu-id="c42dd-139">The [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element specifies the number of columns displayed in the wide view.</span></span> <span data-ttu-id="c42dd-140">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="c42dd-140">This element is optional.</span></span>

- <span data-ttu-id="c42dd-141">[WideEntries](./wideentries-element-for-widecontrol-format.md) -elementet innehåller definitionerna för vyn.</span><span class="sxs-lookup"><span data-stu-id="c42dd-141">The [WideEntries](./wideentries-element-for-widecontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="c42dd-142">I de flesta fall har en vy bara en definition.</span><span class="sxs-lookup"><span data-stu-id="c42dd-142">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="c42dd-143">Det här elementet är obligatoriskt.</span><span class="sxs-lookup"><span data-stu-id="c42dd-143">This element is required.</span></span>

- <span data-ttu-id="c42dd-144">[WideEntry](./wideentry-element-for-widecontrol-format.md) -elementet ger en definition av vyn.</span><span class="sxs-lookup"><span data-stu-id="c42dd-144">The [WideEntry](./wideentry-element-for-widecontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="c42dd-145">Minst en [WideEntry](./wideentry-element-for-widecontrol-format.md) krävs. Det finns dock ingen övre gräns för antalet element som du kan lägga till.</span><span class="sxs-lookup"><span data-stu-id="c42dd-145">At least one [WideEntry](./wideentry-element-for-widecontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="c42dd-146">I de flesta fall har en vy bara en definition.</span><span class="sxs-lookup"><span data-stu-id="c42dd-146">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="c42dd-147">[EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) -elementet anger de objekt som visas av en bestämd definition.</span><span class="sxs-lookup"><span data-stu-id="c42dd-147">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="c42dd-148">Det här elementet är valfritt och behövs bara när du definierar flera [WideEntry](./wideentry-element-for-widecontrol-format.md) -element som visar olika objekt.</span><span class="sxs-lookup"><span data-stu-id="c42dd-148">This element is optional and is needed only when you define multiple [WideEntry](./wideentry-element-for-widecontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="c42dd-149">[WideItem](./wideitem-element-for-widecontrol-format.md) -elementet anger de data som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="c42dd-149">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span> <span data-ttu-id="c42dd-150">Till skillnad från andra typer av vyer kan en bred kontroll bara visa ett objekt.</span><span class="sxs-lookup"><span data-stu-id="c42dd-150">In contrast to other types of views, a wide control can display only one item.</span></span>

- <span data-ttu-id="c42dd-151">Elementet [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) anger den egenskap vars värde visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="c42dd-151">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="c42dd-152">Du måste ange antingen en egenskap eller ett skript, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="c42dd-152">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="c42dd-153">[Script block](./scriptblock-element-for-wideitem-for-widecontrol-format.md) -elementet anger det skript vars värde visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="c42dd-153">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="c42dd-154">Du måste ange antingen ett skript eller en egenskap, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="c42dd-154">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="c42dd-155">Elementet [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) anger ett mönster som används för att visa data.</span><span class="sxs-lookup"><span data-stu-id="c42dd-155">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a pattern that is used to display the data.</span></span> <span data-ttu-id="c42dd-156">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="c42dd-156">This element is optional.</span></span>

<span data-ttu-id="c42dd-157">Ett exempel på en hel format fil som definierar en bred visnings definition finns i [wide View (grundläggande)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="c42dd-157">For an example of a complete formatting file that defines a wide view definition, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-wide-view"></a><span data-ttu-id="c42dd-158">Definiera de objekt som använder wide View</span><span class="sxs-lookup"><span data-stu-id="c42dd-158">Defining the Objects That Use the Wide View</span></span>

<span data-ttu-id="c42dd-159">Det finns två sätt att definiera vilka .NET-objekt som använder wide-vyn.</span><span class="sxs-lookup"><span data-stu-id="c42dd-159">There are two ways to define which .NET objects use the wide view.</span></span> <span data-ttu-id="c42dd-160">Du kan använda [ViewSelectedBy](./viewselectedby-element-format.md) -elementet för att definiera de objekt som kan visas av alla definitioner i vyn, eller så kan du använda elementet [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) för att definiera vilka objekt som visas med en bestämd definition av vyn.</span><span class="sxs-lookup"><span data-stu-id="c42dd-160">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="c42dd-161">I de flesta fall har en vy bara en definition, så objekt definieras vanligt vis av [ViewSelectedBy](./viewselectedby-element-format.md) -elementet.</span><span class="sxs-lookup"><span data-stu-id="c42dd-161">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="c42dd-162">I följande exempel visas hur du definierar de objekt som visas i den breda vyn med hjälp av elementen [ViewSelectedBy](./viewselectedby-element-format.md) och [TypeName](./typename-element-for-viewselectedby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="c42dd-162">The following example shows how to define the objects that are displayed by the wide view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="c42dd-163">Det finns ingen gräns för antalet element i [TypeName](./typename-element-for-viewselectedby-format.md) som du kan ange, och deras ordning är inte signifikant.</span><span class="sxs-lookup"><span data-stu-id="c42dd-163">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="c42dd-164">Följande XML-element kan användas för att ange de objekt som används i den breda vyn:</span><span class="sxs-lookup"><span data-stu-id="c42dd-164">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="c42dd-165">[ViewSelectedBy](./viewselectedby-element-format.md) -elementet definierar vilka objekt som visas i den breda vyn.</span><span class="sxs-lookup"><span data-stu-id="c42dd-165">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="c42dd-166">Elementet [TypeName](./typename-element-for-viewselectedby-format.md) anger det .net som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="c42dd-166">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the view.</span></span> <span data-ttu-id="c42dd-167">Fullständigt kvalificerat .NET-typnamn måste anges.</span><span class="sxs-lookup"><span data-stu-id="c42dd-167">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="c42dd-168">Du måste ange minst en typ eller urvals uppsättning för vyn, men det finns inget maximalt antal element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="c42dd-168">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="c42dd-169">Ett exempel på en hel format fil finns i [wide View (grundläggande)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="c42dd-169">For an example of a complete formatting file, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

<span data-ttu-id="c42dd-170">I följande exempel används elementen [ViewSelectedBy](./viewselectedby-element-format.md) och [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) .</span><span class="sxs-lookup"><span data-stu-id="c42dd-170">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="c42dd-171">Använd markerings uppsättningar där du har en relaterad uppsättning objekt som visas med flera vyer, till exempel när du definierar en bred vy och en tabellvy för samma objekt.</span><span class="sxs-lookup"><span data-stu-id="c42dd-171">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a wide view and a table view for the same objects.</span></span> <span data-ttu-id="c42dd-172">Mer information om hur du skapar en urvals uppsättning finns i [definiera urvals uppsättningar](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="c42dd-172">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="c42dd-173">Följande XML-element kan användas för att ange de objekt som används i den breda vyn:</span><span class="sxs-lookup"><span data-stu-id="c42dd-173">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="c42dd-174">[ViewSelectedBy](./viewselectedby-element-format.md) -elementet definierar vilka objekt som visas i den breda vyn.</span><span class="sxs-lookup"><span data-stu-id="c42dd-174">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="c42dd-175">[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) -elementet anger en uppsättning objekt som kan visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="c42dd-175">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="c42dd-176">Du måste ange minst en markerings uppsättning eller typ för vyn, men det finns inget maximalt antal element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="c42dd-176">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="c42dd-177">I följande exempel visas hur du definierar de objekt som visas av en bestämd definition av den breda vyn med hjälp av [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) -elementet.</span><span class="sxs-lookup"><span data-stu-id="c42dd-177">The following example shows how to define the objects displayed by a specific definition of the wide view using the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element.</span></span> <span data-ttu-id="c42dd-178">Med det här elementet kan du ange objektets .NET-typnamn, en urvals uppsättning objekt eller ett markerings villkor som anger när definitionen används.</span><span class="sxs-lookup"><span data-stu-id="c42dd-178">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="c42dd-179">Mer information om hur du skapar ett urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="c42dd-179">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

<span data-ttu-id="c42dd-180">Följande XML-element kan användas för att ange de objekt som används av en bestämd definition av den breda vyn:</span><span class="sxs-lookup"><span data-stu-id="c42dd-180">The following XML elements can be used to specify the objects that are used by a specific definition of the wide view:</span></span>

- <span data-ttu-id="c42dd-181">[EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) -elementet definierar vilka objekt som visas av definitionen.</span><span class="sxs-lookup"><span data-stu-id="c42dd-181">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="c42dd-182">Elementet [TypeName](./typename-element-for-viewselectedby-format.md) anger det .net som visas av definitionen.</span><span class="sxs-lookup"><span data-stu-id="c42dd-182">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the definition.</span></span> <span data-ttu-id="c42dd-183">När du använder det här elementet krävs fullständigt kvalificerat .NET-typnamn.</span><span class="sxs-lookup"><span data-stu-id="c42dd-183">When using this element the fully qualified .NET type name is required.</span></span> <span data-ttu-id="c42dd-184">Du måste ange minst en typ, markerings uppsättning eller urvals villkor för definitionen, men det finns inget maximalt antal element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="c42dd-184">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="c42dd-185">[SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) -elementet (visas inte) anger en uppsättning objekt som kan visas av den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="c42dd-185">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="c42dd-186">Du måste ange minst en typ, markerings uppsättning eller urvals villkor för definitionen, men det finns inget maximalt antal element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="c42dd-186">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="c42dd-187">[SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) -elementet (visas inte) anger ett villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="c42dd-187">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="c42dd-188">Du måste ange minst en typ, markerings uppsättning eller urvals villkor för definitionen, men det finns inget maximalt antal element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="c42dd-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="c42dd-189">Mer information om hur du definierar urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="c42dd-189">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-wide-view"></a><span data-ttu-id="c42dd-190">Visa grupper av objekt i en bred vy</span><span class="sxs-lookup"><span data-stu-id="c42dd-190">Displaying Groups of objects in a Wide View</span></span>

<span data-ttu-id="c42dd-191">Du kan separera de objekt som visas i den breda vyn i grupper.</span><span class="sxs-lookup"><span data-stu-id="c42dd-191">You can separate the objects that are displayed by the wide view into groups.</span></span> <span data-ttu-id="c42dd-192">Det innebär inte att du definierar en grupp, bara att Windows PowerShell startar en ny grupp när värdet för en speciell egenskap eller skript ändras.</span><span class="sxs-lookup"><span data-stu-id="c42dd-192">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="c42dd-193">I följande exempel startas en ny grupp när värdet för egenskapen [system. serviceprocess. ServiceController. ServiceType](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) ändras.</span><span class="sxs-lookup"><span data-stu-id="c42dd-193">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="c42dd-194">Följande XML-element används för att definiera när en grupp startas:</span><span class="sxs-lookup"><span data-stu-id="c42dd-194">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="c42dd-195">Elementet [groupby](./groupby-element-for-view-format.md) definierar egenskapen eller skriptet som startar den nya gruppen och definierar hur gruppen visas.</span><span class="sxs-lookup"><span data-stu-id="c42dd-195">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="c42dd-196">Elementet [PropertyName](./propertyname-element-for-groupby-format.md) anger den egenskap som startar en ny grupp när dess värde ändras.</span><span class="sxs-lookup"><span data-stu-id="c42dd-196">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="c42dd-197">Du måste ange en egenskap eller ett skript för att starta gruppen, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="c42dd-197">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="c42dd-198">[Script block](./scriptblock-element-for-groupby-format.md) -elementet anger det skript som startar en ny grupp när dess värde ändras.</span><span class="sxs-lookup"><span data-stu-id="c42dd-198">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="c42dd-199">Du måste ange ett skript eller en egenskap för att starta gruppen, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="c42dd-199">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="c42dd-200">Elementet [Label](./label-element-for-groupby-format.md) definierar en etikett som visas i början av varje grupp.</span><span class="sxs-lookup"><span data-stu-id="c42dd-200">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="c42dd-201">Utöver den text som anges av det här elementet visar Windows PowerShell värdet som utlöste den nya gruppen och lägger till en tom rad före och efter etiketten.</span><span class="sxs-lookup"><span data-stu-id="c42dd-201">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="c42dd-202">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="c42dd-202">This element is optional.</span></span>

- <span data-ttu-id="c42dd-203">[CustomControl](./customcontrol-element-for-groupby-format.md) -elementet definierar en kontroll som används för att visa data.</span><span class="sxs-lookup"><span data-stu-id="c42dd-203">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="c42dd-204">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="c42dd-204">This element is optional.</span></span>

- <span data-ttu-id="c42dd-205">[CustomControlName](./customcontrolname-element-for-groupby-format.md) -elementet anger en common-eller View-kontroll som används för att visa data.</span><span class="sxs-lookup"><span data-stu-id="c42dd-205">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="c42dd-206">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="c42dd-206">This element is optional.</span></span>

<span data-ttu-id="c42dd-207">Ett exempel på en hel format fil som definierar grupper finns i [wide View (groupby)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="c42dd-207">For an example of a complete formatting file that defines groups, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="c42dd-208">Använda format strängar</span><span class="sxs-lookup"><span data-stu-id="c42dd-208">Using Format Strings</span></span>

<span data-ttu-id="c42dd-209">Format strängar kan läggas till i en bred vy för att ytterligare definiera hur data visas.</span><span class="sxs-lookup"><span data-stu-id="c42dd-209">Formatting strings can be added to a wide view to further define how the data is displayed.</span></span> <span data-ttu-id="c42dd-210">I följande exempel visas hur du definierar en format sträng för värdet för egenskapen `StartTime`.</span><span class="sxs-lookup"><span data-stu-id="c42dd-210">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

<span data-ttu-id="c42dd-211">Följande XML-element kan användas för att ange ett format mönster:</span><span class="sxs-lookup"><span data-stu-id="c42dd-211">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="c42dd-212">[WideItem](./wideitem-element-for-widecontrol-format.md) -elementet anger de data som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="c42dd-212">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="c42dd-213">Elementet [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) anger den egenskap vars värde visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="c42dd-213">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="c42dd-214">Du måste ange antingen en egenskap eller ett skript, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="c42dd-214">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="c42dd-215">[FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) -elementet anger ett format mönster som definierar hur egenskapen eller skriptets värde visas i vyn</span><span class="sxs-lookup"><span data-stu-id="c42dd-215">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view</span></span>

- <span data-ttu-id="c42dd-216">[Script block](./scriptblock-element-for-wideitem-for-widecontrol-format.md) -elementet (visas inte) anger det skript vars värde visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="c42dd-216">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="c42dd-217">Du måste ange antingen ett skript eller en egenskap, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="c42dd-217">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="c42dd-218">I följande exempel kallas metoden `ToString` för att formatera skriptets värde.</span><span class="sxs-lookup"><span data-stu-id="c42dd-218">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="c42dd-219">Skript kan anropa vilken metod som helst av ett objekt.</span><span class="sxs-lookup"><span data-stu-id="c42dd-219">Scripts can call any method of an object.</span></span> <span data-ttu-id="c42dd-220">Det innebär att om ett objekt har en metod, till exempel `ToString`, som har formateringsegenskaper, kan skriptet anropa metoden för att formatera utdata för skriptet.</span><span class="sxs-lookup"><span data-stu-id="c42dd-220">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

<span data-ttu-id="c42dd-221">Följande XML-element kan användas för att anropa metoden `ToString`:</span><span class="sxs-lookup"><span data-stu-id="c42dd-221">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="c42dd-222">[WideItem](./wideitem-element-for-widecontrol-format.md) -elementet anger de data som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="c42dd-222">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="c42dd-223">[Script block](./scriptblock-element-for-wideitem-for-widecontrol-format.md) -elementet (visas inte) anger det skript vars värde visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="c42dd-223">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="c42dd-224">Du måste ange antingen ett skript eller en egenskap, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="c42dd-224">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="c42dd-225">Se även</span><span class="sxs-lookup"><span data-stu-id="c42dd-225">See Also</span></span>

[<span data-ttu-id="c42dd-226">Bred vy (grundläggande)</span><span class="sxs-lookup"><span data-stu-id="c42dd-226">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="c42dd-227">Bred vy (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="c42dd-227">Wide View (GroupBy)</span></span>](./wide-view-groupby.md)

[<span data-ttu-id="c42dd-228">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="c42dd-228">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
