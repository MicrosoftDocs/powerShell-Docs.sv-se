---
title: Listvy (Basic) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 74ff8f6eee0a9358c123455aa00736a11e7f085d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783559"
---
# <a name="list-view-basic"></a><span data-ttu-id="99da2-102">Listvy (grundläggande)</span><span class="sxs-lookup"><span data-stu-id="99da2-102">List View (Basic)</span></span>

<span data-ttu-id="99da2-103">I det här exemplet visas hur du implementerar en grundläggande listvy som visar [system. serviceprocess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -objekt som returneras av [Get-service](/powershell/module/microsoft.powershell.management/get-service) -cmdleten.</span><span class="sxs-lookup"><span data-stu-id="99da2-103">This example shows how to implement a basic list view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="99da2-104">Mer information om komponenterna i en listvy finns i [skapa en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="99da2-104">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="99da2-105">Läsa in den här format filen</span><span class="sxs-lookup"><span data-stu-id="99da2-105">To load this formatting file</span></span>

1. <span data-ttu-id="99da2-106">Kopiera XML-filen från exempel avsnittet i det här avsnittet till en textfil.</span><span class="sxs-lookup"><span data-stu-id="99da2-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="99da2-107">Spara textfilen.</span><span class="sxs-lookup"><span data-stu-id="99da2-107">Save the text file.</span></span> <span data-ttu-id="99da2-108">Se till att lägga till `format.ps1xml` tillägget i filen för att identifiera det som en format fil.</span><span class="sxs-lookup"><span data-stu-id="99da2-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="99da2-109">Öppna Windows PowerShell och kör följande kommando för att läsa in formaterings filen i den aktuella sessionen: `Update-formatdata -prependpath PathToFormattingFile` .</span><span class="sxs-lookup"><span data-stu-id="99da2-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="99da2-110">Den här format filen definierar visningen av ett objekt som redan har definierats av en Windows PowerShell-textfil.</span><span class="sxs-lookup"><span data-stu-id="99da2-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="99da2-111">Du måste använda `prependPath` parametern när du kör cmdleten och du kan inte läsa in den här format filen som en modul.</span><span class="sxs-lookup"><span data-stu-id="99da2-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="99da2-112">Demonstrationer</span><span class="sxs-lookup"><span data-stu-id="99da2-112">Demonstrates</span></span>

<span data-ttu-id="99da2-113">Den här format filen visar följande XML-element:</span><span class="sxs-lookup"><span data-stu-id="99da2-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="99da2-114">Vyns [namn](./name-element-for-view-format.md) -element.</span><span class="sxs-lookup"><span data-stu-id="99da2-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="99da2-115">[ViewSelectedBy](./viewselectedby-element-format.md) -elementet som definierar vilka objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="99da2-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="99da2-116">Det [ListControl](./listcontrol-element-format.md) -element som definierar vilken egenskap som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="99da2-116">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="99da2-117">Det [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) -element som definierar vad som visas i en rad i listvyn.</span><span class="sxs-lookup"><span data-stu-id="99da2-117">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="99da2-118">Elementet [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) som definierar vilken egenskap som visas.</span><span class="sxs-lookup"><span data-stu-id="99da2-118">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="99da2-119">Exempel</span><span class="sxs-lookup"><span data-stu-id="99da2-119">Example</span></span>

<span data-ttu-id="99da2-120">Följande XML-kod definierar en listvy som visar fyra egenskaper för [system. serviceprocess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -objekt.</span><span class="sxs-lookup"><span data-stu-id="99da2-120">The following XML defines a list view that displays four properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="99da2-121">På varje rad visas namnet på egenskapen följt av egenskapens värde.</span><span class="sxs-lookup"><span data-stu-id="99da2-121">In each row, the name of the property is displayed followed by the value of the property.</span></span>

```xml
<Configuration>
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
</Configuration>
```

<span data-ttu-id="99da2-122">I följande exempel visas hur Windows PowerShell visar [system. serviceprocess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -objekt efter den här format filen har lästs in.</span><span class="sxs-lookup"><span data-stu-id="99da2-122">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
Name        : Fax
DisplayName : Fax
Status      : Stopped
ServiceType : Win32OwnProcess

Name        : FCSAM
DisplayName : Microsoft Antimalware Service
Status      : Running
ServiceType : Win32OwnProcess

Name        : fdPHost
DisplayName : Function Discovery Provider Host
Status      : Stopped
ServiceType : Win32ShareProcess

Name        : FDResPub
DisplayName : Function Discovery Resource Publication
Status      : Running
ServiceType : Win32ShareProcess

Name        : FontCache
DisplayName : Windows Font Cache Service
Status      : Running
ServiceType : Win32ShareProcess

Name        : FontCache3.0.0.0
DisplayName : Windows Presentation Foundation Font Cache 3.0.0.0
Status      : Stopped
ServiceType : Win32OwnProcess

Name        : FSysAgent
DisplayName : Microsoft Forefront System Agent
Status      : Running
ServiceType : Win32OwnProcess

Name        : FwcAgent
DisplayName : Firewall Client Agent
Status      : Running
ServiceType : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="99da2-123">Se även</span><span class="sxs-lookup"><span data-stu-id="99da2-123">See Also</span></span>

[<span data-ttu-id="99da2-124">Exempel på formateringsfiler</span><span class="sxs-lookup"><span data-stu-id="99da2-124">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="99da2-125">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="99da2-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
