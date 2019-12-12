---
title: Listvy (etiketter) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53442bb1-74a3-49f9-9150-3bc3081a7565
caps.latest.revision: 6
ms.openlocfilehash: 27de41c88e224f7610c10a764e51524016ecc8cb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354378"
---
# <a name="list-view-labels"></a><span data-ttu-id="b203b-102">Listvy (etiketter)</span><span class="sxs-lookup"><span data-stu-id="b203b-102">List View (Labels)</span></span>

<span data-ttu-id="b203b-103">I det här exemplet visas hur du implementerar en listvy som visar en anpassad etikett för varje rad i listan.</span><span class="sxs-lookup"><span data-stu-id="b203b-103">This example shows how to implement a list view that displays a custom label for each row of the list.</span></span> <span data-ttu-id="b203b-104">I den här List visningen visas egenskaperna för [system. serviceprocess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -objektet som returneras av [Get-service-](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b203b-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="b203b-105">Mer information om komponenterna i en listvy finns i [skapa en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="b203b-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="b203b-106">Läsa in den här format filen</span><span class="sxs-lookup"><span data-stu-id="b203b-106">To load this formatting file</span></span>

1. <span data-ttu-id="b203b-107">Kopiera XML-filen från exempel avsnittet i det här avsnittet till en textfil.</span><span class="sxs-lookup"><span data-stu-id="b203b-107">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="b203b-108">Spara textfilen.</span><span class="sxs-lookup"><span data-stu-id="b203b-108">Save the text file.</span></span> <span data-ttu-id="b203b-109">Se till att lägga till `format.ps1xml`-tillägget till filen för att identifiera det som en format fil.</span><span class="sxs-lookup"><span data-stu-id="b203b-109">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="b203b-110">Öppna Windows PowerShell och kör följande kommando för att läsa in formaterings filen i den aktuella sessionen: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="b203b-110">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="b203b-111">Den här format filen definierar visningen av ett objekt som redan har definierats av en Windows PowerShell-textfil.</span><span class="sxs-lookup"><span data-stu-id="b203b-111">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="b203b-112">Du måste använda parametern `prependPath` när du kör cmdleten, och du kan inte läsa in den här format filen som en modul.</span><span class="sxs-lookup"><span data-stu-id="b203b-112">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="b203b-113">Demonstrationer</span><span class="sxs-lookup"><span data-stu-id="b203b-113">Demonstrates</span></span>

<span data-ttu-id="b203b-114">Den här format filen visar följande XML-element:</span><span class="sxs-lookup"><span data-stu-id="b203b-114">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="b203b-115">Vyns [namn](./name-element-for-view-format.md) -element.</span><span class="sxs-lookup"><span data-stu-id="b203b-115">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="b203b-116">[ViewSelectedBy](./viewselectedby-element-format.md) -elementet som definierar vilka objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="b203b-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="b203b-117">Det [ListControl](./listcontrol-element-format.md) -element som definierar vilken egenskap som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="b203b-117">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="b203b-118">Det [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) -element som definierar vad som visas i en rad i listvyn.</span><span class="sxs-lookup"><span data-stu-id="b203b-118">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="b203b-119">Det [etikett](./label-element-for-listitem-for-listcontrol-format.md) element som definierar vad som visas i en rad i listvyn.</span><span class="sxs-lookup"><span data-stu-id="b203b-119">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="b203b-120">Elementet [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) som definierar vilken egenskap som visas.</span><span class="sxs-lookup"><span data-stu-id="b203b-120">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="b203b-121">Exempel</span><span class="sxs-lookup"><span data-stu-id="b203b-121">Example</span></span>

<span data-ttu-id="b203b-122">Följande XML-kod definierar en listvy som visar en anpassad etikett på varje rad.</span><span class="sxs-lookup"><span data-stu-id="b203b-122">The following XML defines a list view that displays a custom label in each row.</span></span> <span data-ttu-id="b203b-123">I det här fallet innehåller etiketten egenskaps namnet med varje versal och ordet "Property".</span><span class="sxs-lookup"><span data-stu-id="b203b-123">In this case, the label includes the property name with each letter capitalized and the word "property".</span></span> <span data-ttu-id="b203b-124">På varje rad visas namnet på egenskapen följt av egenskapens värde.</span><span class="sxs-lookup"><span data-stu-id="b203b-124">In each row, the name of the property is displayed followed by the value of the property.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
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
            <Label>NAME property</Label>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <Label>DISPLAYNAME property</Label>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <Label>STATUS property</Label>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <Label>SERVICETYPE property</Label>
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

<span data-ttu-id="b203b-125">I följande exempel visas hur Windows PowerShell visar [system. serviceprocess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -objekt efter den här format filen har lästs in.</span><span class="sxs-lookup"><span data-stu-id="b203b-125">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
NAME property        : Fax
DISPLAYNAME property : Fax
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FCSAM
DISPLAYNAME property : Microsoft Antimalware Service
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : fdPHost
DISPLAYNAME property : Function Discovery Provider Host
STATUS property      : Stopped
SERVICETYPE property : Win32ShareProcess

NAME property        : FDResPub
DISPLAYNAME property : Function Discovery Resource Publication
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache
DISPLAYNAME property : Windows Font Cache Service
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache3.0.0.0
DISPLAYNAME property : Windows Presentation Foundation Font Cache 3.0.0.0
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FSysAgent
DISPLAYNAME property : Microsoft Forefront System Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : FwcAgent
DISPLAYNAME property : Firewall Client Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="b203b-126">Se även</span><span class="sxs-lookup"><span data-stu-id="b203b-126">See Also</span></span>

[<span data-ttu-id="b203b-127">Exempel på filer som ska formateras</span><span class="sxs-lookup"><span data-stu-id="b203b-127">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="b203b-128">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="b203b-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
