---
title: Listvy (Basic) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 918f381c-43e6-4594-a468-a40bfa8a16d6
caps.latest.revision: 7
ms.openlocfilehash: 3c94d8e98f179286112a417230fce659dc0b614c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354392"
---
# <a name="list-view-basic"></a><span data-ttu-id="2fa20-102">Listvy (grundläggande)</span><span class="sxs-lookup"><span data-stu-id="2fa20-102">List View (Basic)</span></span>

<span data-ttu-id="2fa20-103">I det här exemplet visas hur du implementerar en grundläggande listvy som visar [system. serviceprocess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -objekt som returneras av [Get-service](/powershell/module/microsoft.powershell.management/get-service) -cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2fa20-103">This example shows how to implement a basic list view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="2fa20-104">Mer information om komponenterna i en listvy finns i [skapa en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="2fa20-104">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="2fa20-105">Läsa in den här format filen</span><span class="sxs-lookup"><span data-stu-id="2fa20-105">To load this formatting file</span></span>

1. <span data-ttu-id="2fa20-106">Kopiera XML-filen från exempel avsnittet i det här avsnittet till en textfil.</span><span class="sxs-lookup"><span data-stu-id="2fa20-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="2fa20-107">Spara textfilen.</span><span class="sxs-lookup"><span data-stu-id="2fa20-107">Save the text file.</span></span> <span data-ttu-id="2fa20-108">Se till att lägga till `format.ps1xml`-tillägget till filen för att identifiera det som en format fil.</span><span class="sxs-lookup"><span data-stu-id="2fa20-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="2fa20-109">Öppna Windows PowerShell och kör följande kommando för att läsa in formaterings filen i den aktuella sessionen: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="2fa20-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="2fa20-110">Den här format filen definierar visningen av ett objekt som redan har definierats av en Windows PowerShell-textfil.</span><span class="sxs-lookup"><span data-stu-id="2fa20-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="2fa20-111">Du måste använda parametern `prependPath` när du kör cmdleten, och du kan inte läsa in den här format filen som en modul.</span><span class="sxs-lookup"><span data-stu-id="2fa20-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="2fa20-112">Demonstrationer</span><span class="sxs-lookup"><span data-stu-id="2fa20-112">Demonstrates</span></span>

<span data-ttu-id="2fa20-113">Den här format filen visar följande XML-element:</span><span class="sxs-lookup"><span data-stu-id="2fa20-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="2fa20-114">Vyns [namn](./name-element-for-view-format.md) -element.</span><span class="sxs-lookup"><span data-stu-id="2fa20-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="2fa20-115">[ViewSelectedBy](./viewselectedby-element-format.md) -elementet som definierar vilka objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="2fa20-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="2fa20-116">Det [ListControl](./listcontrol-element-format.md) -element som definierar vilken egenskap som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="2fa20-116">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="2fa20-117">Det [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) -element som definierar vad som visas i en rad i listvyn.</span><span class="sxs-lookup"><span data-stu-id="2fa20-117">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="2fa20-118">Elementet [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) som definierar vilken egenskap som visas.</span><span class="sxs-lookup"><span data-stu-id="2fa20-118">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="2fa20-119">Exempel</span><span class="sxs-lookup"><span data-stu-id="2fa20-119">Example</span></span>

<span data-ttu-id="2fa20-120">Följande XML-kod definierar en listvy som visar fyra egenskaper för [system. serviceprocess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -objekt.</span><span class="sxs-lookup"><span data-stu-id="2fa20-120">The following XML defines a list view that displays four properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="2fa20-121">På varje rad visas namnet på egenskapen följt av egenskapens värde.</span><span class="sxs-lookup"><span data-stu-id="2fa20-121">In each row, the name of the property is displayed followed by the value of the property.</span></span>

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

<span data-ttu-id="2fa20-122">I följande exempel visas hur Windows PowerShell visar [system. serviceprocess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -objekt efter den här format filen har lästs in.</span><span class="sxs-lookup"><span data-stu-id="2fa20-122">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2fa20-123">Se även</span><span class="sxs-lookup"><span data-stu-id="2fa20-123">See Also</span></span>

[<span data-ttu-id="2fa20-124">Exempel på filer som ska formateras</span><span class="sxs-lookup"><span data-stu-id="2fa20-124">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="2fa20-125">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="2fa20-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
