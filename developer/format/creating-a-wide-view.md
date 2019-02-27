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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848561"
---
# <a name="creating-a-wide-view"></a><span data-ttu-id="f7bcf-102">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="f7bcf-102">Creating a Wide View</span></span>

<span data-ttu-id="f7bcf-103">En bred vy visar ett värde för varje objekt som visas.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-103">A wide view displays a single value for each object that is displayed.</span></span> <span data-ttu-id="f7bcf-104">Värdet som visas kan vara värdet för en egenskap för .NET-objekt eller värdet för ett skript.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-104">The displayed value can be the value of a .NET object property or the value of a script.</span></span> <span data-ttu-id="f7bcf-105">Som standard finns ingen etikett eller rubrik för den här vyn.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-105">By default, there is no label or header for this view.</span></span>

## <a name="a-wide-view-display"></a><span data-ttu-id="f7bcf-106">En bred vy visning</span><span class="sxs-lookup"><span data-stu-id="f7bcf-106">A Wide View Display</span></span>

<span data-ttu-id="f7bcf-107">I följande exempel visas hur Windows PowerShell visar den [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objekt som returneras av den [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet när dess utdata skickas till den [ Formatet hela](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-107">The following example shows how Windows PowerShell displays the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object that is returned by the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet when its output is piped to the [Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet.</span></span> <span data-ttu-id="f7bcf-108">(Som standard den [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returnerar en tabellvy.) I det här exemplet är de två kolumnerna används för att visa namnet på processen för varje returnerade objektet.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-108">(By default, the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns a table view.) In this example, the two columns are used to display the name of the process for each returned object.</span></span> <span data-ttu-id="f7bcf-109">Objektets egenskapens namn visas inte, endast värdet för egenskapen.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-109">The name of the object's property is not displayed, only the value of the property.</span></span>

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

## <a name="defining-the-wide-view"></a><span data-ttu-id="f7bcf-110">Definiera bred vy</span><span class="sxs-lookup"><span data-stu-id="f7bcf-110">Defining the Wide View</span></span>

<span data-ttu-id="f7bcf-111">Följande XML visar bred vy schemat för den [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objekt.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-111">The following XML shows the wide view schema for the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

<span data-ttu-id="f7bcf-112">Följande XML-element används för att definiera en bred vy:</span><span class="sxs-lookup"><span data-stu-id="f7bcf-112">The following XML elements are used to define a wide view:</span></span>

- <span data-ttu-id="f7bcf-113">Den [visa](./view-element-format.md) elementet har det överordnade elementet i bred vy.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-113">The [View](./view-element-format.md) element is the parent element of the wide view.</span></span> <span data-ttu-id="f7bcf-114">(Detta är samma överordnade element för tabell, lista och anpassad kontroll vyer.)</span><span class="sxs-lookup"><span data-stu-id="f7bcf-114">(This is the same parent element for the table, list, and custom control views.)</span></span>

- <span data-ttu-id="f7bcf-115">Den [namn](./name-element-for-view-format.md) elementet anger namnet på vyn.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-115">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="f7bcf-116">Det här elementet krävs för alla vyer.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-116">This element is required for all views.</span></span>

- <span data-ttu-id="f7bcf-117">Den [ViewSelectedBy](./viewselectedby-element-format.md) elementet definierar de objekt som använder vyn.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-117">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="f7bcf-118">Det här elementet krävs.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-118">This element is required.</span></span>

- <span data-ttu-id="f7bcf-119">Den [GroupBy](./groupby-element-for-view-format.md) elementet definierar när en ny grupp med objekt visas.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-119">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="f7bcf-120">En ny grupp har startats när värdet för en specifik egenskap eller ett skript ändras.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-120">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="f7bcf-121">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-121">This element is optional.</span></span>

- <span data-ttu-id="f7bcf-122">Den [kontroller](./controls-element-for-view-format.md) element definierar de anpassade kontroller som definieras av bred vy.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-122">The [Controls](./controls-element-for-view-format.md) elements defines the custom controls that are defined by the wide view.</span></span> <span data-ttu-id="f7bcf-123">Kontroller ger dig ett sätt som specificerar hur data visas.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-123">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="f7bcf-124">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-124">This element is optional.</span></span> <span data-ttu-id="f7bcf-125">En vy kan definiera egna anpassade kontroller eller använda vanliga kontroller som kan användas av alla vyer i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-125">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="f7bcf-126">Mer information om anpassade kontroller finns i [skapar anpassade kontroller](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="f7bcf-126">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="f7bcf-127">Den [WideControl](./widecontrol-element-format.md) elementet och dess underordnade element definierar vad som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-127">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span> <span data-ttu-id="f7bcf-128">I föregående exempel vyn har utformats för att visa den [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) egenskapen.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-128">In the preceding example, the view is designed to display the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span>

<span data-ttu-id="f7bcf-129">Ett exempel på en fullständig formatering fil som definierar en enkel bred vy finns i [bred vy (grundläggande)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="f7bcf-129">For an example of a complete formatting file that defines a simple wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-wide-view"></a><span data-ttu-id="f7bcf-130">Att tillhandahålla definitioner för din bred vy</span><span class="sxs-lookup"><span data-stu-id="f7bcf-130">Providing Definitions for Your Wide View</span></span>

<span data-ttu-id="f7bcf-131">Brett vyer kan ge en eller flera definitioner med hjälp av de underordnade elementen i den [WideControl](./widecontrol-element-format.md) element.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-131">Wide views can provide one or more definitions by using the child elements of the [WideControl](./widecontrol-element-format.md) element.</span></span> <span data-ttu-id="f7bcf-132">Vyn har vanligtvis bara en definition.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-132">Typically, a view will have only one definition.</span></span> <span data-ttu-id="f7bcf-133">I följande exempel visas vyn ger en enda definition som visar värdet för den [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) egenskapen.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-133">In the following example, the view provides a single definition that displays the value of the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span> <span data-ttu-id="f7bcf-134">En bred vy kan visa värdet för en egenskap eller värdet för ett skript (visas inte i det här exemplet).</span><span class="sxs-lookup"><span data-stu-id="f7bcf-134">A wide view can display the value of a property or the value of a script (not shown in the example).</span></span>

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

<span data-ttu-id="f7bcf-135">Följande XML-element kan användas för att ange definitioner för en bred vy:</span><span class="sxs-lookup"><span data-stu-id="f7bcf-135">The following XML elements can be used to provide definitions for a wide view:</span></span>

- <span data-ttu-id="f7bcf-136">Den [WideControl](./widecontrol-element-format.md) elementet och dess underordnade element definierar vad som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-136">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="f7bcf-137">Den [AutoSize](./autosize-element-for-widecontrol-format.md) elementet anger om kolumnstorlek och antalet kolumner justeras beroende på storleken på data.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-137">The [AutoSize](./autosize-element-for-widecontrol-format.md) element specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span> <span data-ttu-id="f7bcf-138">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-138">This element is optional.</span></span>

- <span data-ttu-id="f7bcf-139">Den [antal_kolumner anger](./columnnumber-element-for-widecontrol-format.md) elementet anger antalet kolumner som visas i bred vy.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-139">The [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element specifies the number of columns displayed in the wide view.</span></span> <span data-ttu-id="f7bcf-140">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-140">This element is optional.</span></span>

- <span data-ttu-id="f7bcf-141">Den [WideEntries](./wideentries-element-for-widecontrol-format.md) elementet innehåller definitioner av vyn.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-141">The [WideEntries](./wideentries-element-for-widecontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="f7bcf-142">I de flesta fall har en vy endast en definition.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-142">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="f7bcf-143">Det här elementet krävs.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-143">This element is required.</span></span>

- <span data-ttu-id="f7bcf-144">Den [WideEntry](./wideentry-element-for-widecontrol-format.md) elementet innehåller en definition för vyn.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-144">The [WideEntry](./wideentry-element-for-widecontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="f7bcf-145">Minst en [WideEntry](./wideentry-element-for-widecontrol-format.md) krävs, men det finns ingen högsta gräns för antalet element som du kan lägga till.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-145">At least one [WideEntry](./wideentry-element-for-widecontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="f7bcf-146">I de flesta fall har en vy endast en definition.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-146">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="f7bcf-147">Den [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) elementet anger de objekt som visas som en viss definition.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-147">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="f7bcf-148">Det här elementet är valfritt och krävs bara när du definierar flera [WideEntry](./wideentry-element-for-widecontrol-format.md) element som visar olika objekt.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-148">This element is optional and is needed only when you define multiple [WideEntry](./wideentry-element-for-widecontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="f7bcf-149">Den [WideItem](./wideitem-element-for-widecontrol-format.md) elementet anger de data som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-149">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span> <span data-ttu-id="f7bcf-150">Till skillnad från andra typer av vyer, kan en bred kontroll Visa endast ett objekt.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-150">In contrast to other types of views, a wide control can display only one item.</span></span>

- <span data-ttu-id="f7bcf-151">Den [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) elementet anger egenskapen vars värde visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-151">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="f7bcf-152">Du måste ange en egenskap eller ett skript, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-152">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="f7bcf-153">Den [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) elementet anger skriptet vars värde visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-153">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="f7bcf-154">Du måste ange ett skript eller en egenskap, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-154">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="f7bcf-155">Den [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) elementet anger ett mönster som används för att visa data.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-155">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a pattern that is used to display the data.</span></span> <span data-ttu-id="f7bcf-156">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-156">This element is optional.</span></span>

<span data-ttu-id="f7bcf-157">Ett exempel på en fullständig formatering fil som definierar en bred vy-definition finns i [bred vy (grundläggande)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="f7bcf-157">For an example of a complete formatting file that defines a wide view definition, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-wide-view"></a><span data-ttu-id="f7bcf-158">Definiera de objekt som använder bred vy</span><span class="sxs-lookup"><span data-stu-id="f7bcf-158">Defining the Objects That Use the Wide View</span></span>

<span data-ttu-id="f7bcf-159">Det finns två sätt att definiera vilka .NET-objekt använder bred vy.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-159">There are two ways to define which .NET objects use the wide view.</span></span> <span data-ttu-id="f7bcf-160">Du kan använda den [ViewSelectedBy](./viewselectedby-element-format.md) element för att definiera de objekt som kan visas av alla definitioner av vyn eller du kan använda den [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element för att definiera vilka objekt visas som en viss definition för vyn.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-160">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="f7bcf-161">I de flesta fall har endast en definition i en vy så objekt definieras vanligtvis av den [ViewSelectedBy](./viewselectedby-element-format.md) element.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-161">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="f7bcf-162">I följande exempel visas hur du definierar de objekt som visas som en bred vy med hjälp av den [ViewSelectedBy](./viewselectedby-element-format.md) och [TypeName](./typename-element-for-viewselectedby-format.md) element.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-162">The following example shows how to define the objects that are displayed by the wide view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="f7bcf-163">Det finns ingen gräns för hur många [TypeName](./typename-element-for-viewselectedby-format.md) element att du kan ange och deras inbördes ordning är inte särskilt stor.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-163">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="f7bcf-164">Följande XML-element kan användas för att ange objekt som används av bred vy:</span><span class="sxs-lookup"><span data-stu-id="f7bcf-164">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="f7bcf-165">Den [ViewSelectedBy](./viewselectedby-element-format.md) elementet definierar vilka objekt visas i bred vy.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-165">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="f7bcf-166">Den [TypeName](./typename-element-for-viewselectedby-format.md) elementet anger .NET som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-166">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the view.</span></span> <span data-ttu-id="f7bcf-167">Det fullständigt kvalificerade typnamnet .NET krävs.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-167">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="f7bcf-168">Du måste ange minst en typ eller val som angetts för vyn, men det finns inget högsta antal element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-168">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="f7bcf-169">Ett exempel på en fullständig formatering fil, se [bred vy (grundläggande)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="f7bcf-169">For an example of a complete formatting file, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

<span data-ttu-id="f7bcf-170">I följande exempel används den [ViewSelectedBy](./viewselectedby-element-format.md) och [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-170">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="f7bcf-171">Använd val av där du har en uppsättning objekt som visas med flera vyer, till exempel när du definierar en bred vy och en tabellvy för samma objekt.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-171">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a wide view and a table view for the same objects.</span></span> <span data-ttu-id="f7bcf-172">Läs mer om hur du skapar en [definiera val av uppsättningar](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="f7bcf-172">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="f7bcf-173">Följande XML-element kan användas för att ange objekt som används av bred vy:</span><span class="sxs-lookup"><span data-stu-id="f7bcf-173">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="f7bcf-174">Den [ViewSelectedBy](./viewselectedby-element-format.md) elementet definierar vilka objekt visas i bred vy.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-174">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="f7bcf-175">Den [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementet anger en uppsättning objekt som kan visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-175">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="f7bcf-176">Du måste ange minst en markering set eller typ för vyn, men det finns inget högsta antal element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-176">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="f7bcf-177">I följande exempel visas hur du definierar de objekt som visas av en viss definition av en bred vy med hjälp av den [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-177">The following example shows how to define the objects displayed by a specific definition of the wide view using the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element.</span></span> <span data-ttu-id="f7bcf-178">Med det här elementet kan ange du namnet på .NET objektet, val av flera objekt eller ett val av villkor som anger när definitionen används.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-178">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="f7bcf-179">Mer information om hur du skapar ett urval villkor finns i [definiera villkor för att visa Data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f7bcf-179">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

<span data-ttu-id="f7bcf-180">Följande XML-element kan användas för att ange objekt som används av en viss definition av bred vy:</span><span class="sxs-lookup"><span data-stu-id="f7bcf-180">The following XML elements can be used to specify the objects that are used by a specific definition of the wide view:</span></span>

- <span data-ttu-id="f7bcf-181">Den [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) elementet definierar vilka objekt visas i definitionen.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-181">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="f7bcf-182">Den [TypeName](./typename-element-for-viewselectedby-format.md) elementet anger .NET som visas när definitionen.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-182">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the definition.</span></span> <span data-ttu-id="f7bcf-183">När du använder det här elementet krävs det fullständigt kvalificerade typnamnet för .NET.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-183">When using this element the fully qualified .NET type name is required.</span></span> <span data-ttu-id="f7bcf-184">Du måste ange minst en typ, val av set eller urvalsvillkoret för definitionen, men det finns inget högsta antal element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-184">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="f7bcf-185">Den [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element (visas inte) anger en uppsättning objekt som kan visas av denna definition.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-185">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="f7bcf-186">Du måste ange minst en typ, val av set eller urvalsvillkoret för definitionen, men det finns inget högsta antal element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-186">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="f7bcf-187">Den [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) element (visas inte) anger ett villkor som måste finnas för den här definitionen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-187">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="f7bcf-188">Du måste ange minst en typ, val av set eller urvalsvillkoret för definitionen, men det finns inget högsta antal element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="f7bcf-189">Läs mer om hur du definierar villkoren för val av [definiera villkor för att visa Data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f7bcf-189">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-wide-view"></a><span data-ttu-id="f7bcf-190">Visa grupper med objekt i en bred vy</span><span class="sxs-lookup"><span data-stu-id="f7bcf-190">Displaying Groups of objects in a Wide View</span></span>

<span data-ttu-id="f7bcf-191">Du kan avgränsa de objekt som visas i bred vy i grupper.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-191">You can separate the objects that are displayed by the wide view into groups.</span></span> <span data-ttu-id="f7bcf-192">Detta innebär inte att du definierar en grupp, endast att Windows PowerShell startar en ny grupp när en specifik egenskap eller ett skript ändras.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-192">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="f7bcf-193">I följande exempel visas en ny grupp har startats när värdet för den [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) egenskapsändringar.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-193">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="f7bcf-194">Följande XML-element används för att definiera när en grupp startas:</span><span class="sxs-lookup"><span data-stu-id="f7bcf-194">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="f7bcf-195">Den [GroupBy](./groupby-element-for-view-format.md) elementet definierar egenskapen eller skript som startar den nya gruppen och definierar hur gruppen visas.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-195">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="f7bcf-196">Den [PropertyName](./propertyname-element-for-groupby-format.md) elementet anger den egenskap som startar en ny grupp när dess värde ändras.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-196">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="f7bcf-197">Du måste ange en egenskap eller ett skript för att starta gruppen, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-197">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="f7bcf-198">Den [ScriptBlock](./scriptblock-element-for-groupby-format.md) elementet anger det skript som startar en ny grupp när dess värde ändras.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-198">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="f7bcf-199">Du måste ange ett skript eller en egenskap för att starta gruppen, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-199">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="f7bcf-200">Den [etikett](./label-element-for-groupby-format.md) elementet definierar en etikett som visas i början av varje grupp.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-200">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="f7bcf-201">Förutom den text som anges av det här elementet, visar det värde som utlöste den nya gruppen och lägger till en tom rad före och efter etiketten i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-201">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="f7bcf-202">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-202">This element is optional.</span></span>

- <span data-ttu-id="f7bcf-203">Den [anpassad kontroll](./customcontrol-element-for-groupby-format.md) elementet definierar en kontroll som används för att visa data.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-203">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="f7bcf-204">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-204">This element is optional.</span></span>

- <span data-ttu-id="f7bcf-205">Den [CustomControlName](./customcontrolname-element-for-groupby-format.md) elementet anger ett vanligt eller visa kontroll som används för att visa data.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-205">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="f7bcf-206">Det här elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-206">This element is optional.</span></span>

<span data-ttu-id="f7bcf-207">Ett exempel på en fullständig formatering fil som definierar grupper finns i [bred vy (GroupBy)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="f7bcf-207">For an example of a complete formatting file that defines groups, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="f7bcf-208">Med hjälp av formatsträngar</span><span class="sxs-lookup"><span data-stu-id="f7bcf-208">Using Format Strings</span></span>

<span data-ttu-id="f7bcf-209">Formatering strängar kan läggas till en bred vy för att ytterligare definiera hur data visas.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-209">Formatting strings can be added to a wide view to further define how the data is displayed.</span></span> <span data-ttu-id="f7bcf-210">I följande exempel visas hur du definierar en formateringssträngen för värdet för den `StartTime` egenskapen.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-210">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

<span data-ttu-id="f7bcf-211">Följande XML-element kan användas för att ange ett:</span><span class="sxs-lookup"><span data-stu-id="f7bcf-211">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="f7bcf-212">Den [WideItem](./wideitem-element-for-widecontrol-format.md) elementet anger de data som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-212">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="f7bcf-213">Den [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) elementet anger egenskapen vars värde visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-213">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="f7bcf-214">Du måste ange en egenskap eller ett skript, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-214">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="f7bcf-215">Den [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) elementet anger ett formatmönster som definierar hur värdet för egenskapen eller skript visas i vyn</span><span class="sxs-lookup"><span data-stu-id="f7bcf-215">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view</span></span>

- <span data-ttu-id="f7bcf-216">Den [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (visas inte) anger skriptet vars värde visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-216">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="f7bcf-217">Du måste ange ett skript eller en egenskap, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-217">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="f7bcf-218">I följande exempel visas den `ToString` metoden anropas för att formatera värdet för skriptet.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-218">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="f7bcf-219">Skript kan anropa någon-metod för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-219">Scripts can call any method of an object.</span></span> <span data-ttu-id="f7bcf-220">Därför, om ett objekt har en metod som `ToString`, som har formateringsparametrar, skriptet kan anropa metoden för att formatera utdatavärdet för skriptet.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-220">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

<span data-ttu-id="f7bcf-221">Följande XML-element som kan användas för att anropa den `ToString` metoden:</span><span class="sxs-lookup"><span data-stu-id="f7bcf-221">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="f7bcf-222">Den [WideItem](./wideitem-element-for-widecontrol-format.md) elementet anger de data som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-222">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="f7bcf-223">Den [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (visas inte) anger skriptet vars värde visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-223">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="f7bcf-224">Du måste ange ett skript eller en egenskap, men du kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="f7bcf-224">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="f7bcf-225">Se även</span><span class="sxs-lookup"><span data-stu-id="f7bcf-225">See Also</span></span>

[<span data-ttu-id="f7bcf-226">Bred vy (grundläggande)</span><span class="sxs-lookup"><span data-stu-id="f7bcf-226">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="f7bcf-227">Bred vy (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="f7bcf-227">Wide View (GroupBy)</span></span>](./wide-view-groupby.md)

[<span data-ttu-id="f7bcf-228">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="f7bcf-228">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
