---
title: Listvy (GroupBy) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7956d13e196454a3f6da185e9be74f9d3cb8ef63
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773410"
---
# <a name="list-view-groupby"></a><span data-ttu-id="be050-102">Listvy (gruppbaserad)</span><span class="sxs-lookup"><span data-stu-id="be050-102">List View (GroupBy)</span></span>

<span data-ttu-id="be050-103">Det här exemplet visar hur du implementerar en listvy som separerar rader i listan till grupper.</span><span class="sxs-lookup"><span data-stu-id="be050-103">This example shows how to implement a list view that separates the rows of the list into groups.</span></span> <span data-ttu-id="be050-104">I den här List visningen visas egenskaperna för [system. serviceprocess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -objekt som returneras av [Get-service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) -cmdleten.</span><span class="sxs-lookup"><span data-stu-id="be050-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="be050-105">Mer information om komponenterna i en listvy finns i [skapa en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="be050-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="be050-106">Läsa in den här format filen</span><span class="sxs-lookup"><span data-stu-id="be050-106">To load this formatting file</span></span>

1. <span data-ttu-id="be050-107">Kopiera XML-filen från exempel avsnittet i det här avsnittet till en textfil.</span><span class="sxs-lookup"><span data-stu-id="be050-107">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="be050-108">Spara textfilen.</span><span class="sxs-lookup"><span data-stu-id="be050-108">Save the text file.</span></span> <span data-ttu-id="be050-109">Se till att lägga till `format.ps1xml` tillägget i filen för att identifiera det som en format fil.</span><span class="sxs-lookup"><span data-stu-id="be050-109">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="be050-110">Öppna Windows PowerShell och kör följande kommando för att läsa in formaterings filen i den aktuella sessionen: `Update-formatdata -prependpath PathToFormattingFile` .</span><span class="sxs-lookup"><span data-stu-id="be050-110">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="be050-111">Den här format filen definierar visningen av ett objekt som redan har definierats av en Windows PowerShell-textfil.</span><span class="sxs-lookup"><span data-stu-id="be050-111">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="be050-112">Du måste använda `prependPath` parametern när du kör cmdleten och du kan inte läsa in den här format filen som en modul.</span><span class="sxs-lookup"><span data-stu-id="be050-112">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="be050-113">Demonstrationer</span><span class="sxs-lookup"><span data-stu-id="be050-113">Demonstrates</span></span>

<span data-ttu-id="be050-114">Den här format filen visar följande XML-element:</span><span class="sxs-lookup"><span data-stu-id="be050-114">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="be050-115">Vyns [namn](./name-element-for-view-format.md) -element.</span><span class="sxs-lookup"><span data-stu-id="be050-115">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="be050-116">[ViewSelectedBy](./viewselectedby-element-format.md) -elementet som definierar vilka objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="be050-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="be050-117">Det [groupby](./viewselectedby-element-format.md) -element som definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="be050-117">The [GroupBy](./viewselectedby-element-format.md) element that defines how a new group of objects is displayed.</span></span>

- <span data-ttu-id="be050-118">Det [ListControl](./listcontrol-element-format.md) -element som definierar vilken egenskap som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="be050-118">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="be050-119">Det [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) -element som definierar vad som visas i en rad i listvyn.</span><span class="sxs-lookup"><span data-stu-id="be050-119">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="be050-120">Elementet [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) som definierar vilken egenskap som visas.</span><span class="sxs-lookup"><span data-stu-id="be050-120">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="be050-121">Exempel</span><span class="sxs-lookup"><span data-stu-id="be050-121">Example</span></span>

<span data-ttu-id="be050-122">Följande XML-kod definierar en listvy som startar en ny grupp när värdet för egenskapen [system. serviceprocess. ServiceController. status](/dotnet/api/System.ServiceProcess.ServiceController.Status) ändras.</span><span class="sxs-lookup"><span data-stu-id="be050-122">The following XML defines a list view that starts a new group whenever the value of the [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) property changes.</span></span> <span data-ttu-id="be050-123">När varje grupp startas visas en anpassad etikett som innehåller det nya värdet för egenskapen.</span><span class="sxs-lookup"><span data-stu-id="be050-123">When each group is started, a custom label is displayed that includes the new value of the property.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <Name>System.ServiceProcess.ServiceController</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <PropertyName>Status</PropertyName>
        <Label>New Service Status</Label>
      </GroupBy>
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
                <PropertyName>ServiceType</PropertyName>
              </ListItem>
            </ListItems>
          </ListEntry>
        </ListEntries>
      </ListControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

<span data-ttu-id="be050-124">I följande exempel visas hur Windows PowerShell visar [system. serviceprocess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -objekt efter den här format filen har lästs in.</span><span class="sxs-lookup"><span data-stu-id="be050-124">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span> <span data-ttu-id="be050-125">Tomma rader som lagts till före och efter grupp etiketten läggs automatiskt till av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="be050-125">The blank lines added before and after the group label are automatically added by Windows PowerShell.</span></span>

```powershell
Get-Service f*
```

```output
   New Service Status: Stopped

Name        : Fax
DisplayName : Fax
ServiceType : Win32OwnProcess

   New Service Status: Running

Name        : FCSAM
DisplayName : Microsoft Antimalware Service
ServiceType : Win32OwnProcess

   New Service Status: Stopped

Name        : fdPHost
DisplayName : Function Discovery Provider Host
ServiceType : Win32ShareProcess

   New Service Status: Running

Name        : FDResPub
DisplayName : Function Discovery Resource Publication
ServiceType : Win32ShareProcess

Name        : FontCache
DisplayName : Windows Font Cache Service
ServiceType : Win32ShareProcess

   New Service Status: Stopped

Name        : FontCache3.0.0.0
DisplayName : Windows Presentation Foundation Font Cache 3.0.0.0
ServiceType : Win32OwnProcess

   New Service Status: Running

Name        : FSysAgent
DisplayName : Microsoft Forefront System Agent
ServiceType : Win32OwnProcess

Name        : FwcAgent
DisplayName : Firewall Client Agent
ServiceType : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="be050-126">Se även</span><span class="sxs-lookup"><span data-stu-id="be050-126">See Also</span></span>

[<span data-ttu-id="be050-127">Exempel på formateringsfiler</span><span class="sxs-lookup"><span data-stu-id="be050-127">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="be050-128">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="be050-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
