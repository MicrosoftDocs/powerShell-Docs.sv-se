---
title: Listvy (GroupBy) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2e66c86-83a7-4148-8575-c28d6d429d4f
caps.latest.revision: 6
ms.openlocfilehash: ad7ea457fe0f67bfa41f6bf81f36d4b2e4a76cb3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849716"
---
# <a name="list-view-groupby"></a><span data-ttu-id="e521c-102">Listvy (gruppbaserad)</span><span class="sxs-lookup"><span data-stu-id="e521c-102">List View (GroupBy)</span></span>

<span data-ttu-id="e521c-103">Det här exemplet visar hur du implementerar en listvy som avgränsar raderna i listan i grupper.</span><span class="sxs-lookup"><span data-stu-id="e521c-103">This example shows how to implement a list view that separates the rows of the list into groups.</span></span> <span data-ttu-id="e521c-104">I den här listan visas egenskaperna för den [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objekten som returneras av den [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e521c-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="e521c-105">Läs mer om komponenterna i en listvy, [skapar en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="e521c-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>
<span data-ttu-id="e521c-106">Det här exemplet visar hur du implementerar en listvy som avgränsar raderna i listan i grupper.</span><span class="sxs-lookup"><span data-stu-id="e521c-106">This example shows how to implement a list view that separates the rows of the list into groups.</span></span> <span data-ttu-id="e521c-107">I den här listan visas egenskaperna för den [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objekten som returneras av den [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e521c-107">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="e521c-108">Läs mer om komponenterna i en listvy, [skapar en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="e521c-108">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="e521c-109">Att läsa in den här formatering filen</span><span class="sxs-lookup"><span data-stu-id="e521c-109">To load this formatting file</span></span>

1. <span data-ttu-id="e521c-110">Kopiera XML-filen från avsnittet exempel i den här artikeln i en textfil.</span><span class="sxs-lookup"><span data-stu-id="e521c-110">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="e521c-111">Spara filen.</span><span class="sxs-lookup"><span data-stu-id="e521c-111">Save the text file.</span></span> <span data-ttu-id="e521c-112">Se till att lägga till den `format.ps1xml` tillägg till filen för att identifiera den som en formatering fil.</span><span class="sxs-lookup"><span data-stu-id="e521c-112">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="e521c-113">Öppna Windows PowerShell och kör följande kommando för att läsa in filen formatering i den aktuella sessionen: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="e521c-113">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="e521c-114">Den här formatering filen definierar visning av ett objekt som redan har definierats av en formatering Windows PowerShell-fil.</span><span class="sxs-lookup"><span data-stu-id="e521c-114">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="e521c-115">Du måste använda den `prependPath` parameter när du kör cmdlet: en, och du kan inte läsa in den här formateringen filen som en modul.</span><span class="sxs-lookup"><span data-stu-id="e521c-115">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="e521c-116">Visar</span><span class="sxs-lookup"><span data-stu-id="e521c-116">Demonstrates</span></span>

<span data-ttu-id="e521c-117">Den här formatering filen visar följande XML-element:</span><span class="sxs-lookup"><span data-stu-id="e521c-117">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="e521c-118">Den [namn](./name-element-for-view-format.md) element för vyn.</span><span class="sxs-lookup"><span data-stu-id="e521c-118">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="e521c-119">Den [ViewSelectedBy](./viewselectedby-element-format.md) -element som definierar vilka objekt visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="e521c-119">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="e521c-120">Den [GroupBy](./viewselectedby-element-format.md) element som definierar hur en ny grupp med objekt visas.</span><span class="sxs-lookup"><span data-stu-id="e521c-120">The [GroupBy](./viewselectedby-element-format.md) element that defines how a new group of objects is displayed.</span></span>

- <span data-ttu-id="e521c-121">Den [ListControl](./listcontrol-element-format.md) element som definierar vilka egenskapen visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="e521c-121">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="e521c-122">Den [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) -element som definierar vad som visas i en rad i listvyn.</span><span class="sxs-lookup"><span data-stu-id="e521c-122">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="e521c-123">Den [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element som definierar vilken egenskap visas.</span><span class="sxs-lookup"><span data-stu-id="e521c-123">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="e521c-124">Exempel</span><span class="sxs-lookup"><span data-stu-id="e521c-124">Example</span></span>

<span data-ttu-id="e521c-125">Följande XML-filen definierar en listvy som startar en ny grupp när värdet för den [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) egenskapsändringar.</span><span class="sxs-lookup"><span data-stu-id="e521c-125">The following XML defines a list view that starts a new group whenever the value of the [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) property changes.</span></span> <span data-ttu-id="e521c-126">När varje grupp har startats visas en anpassad etikett med det nya värdet för egenskapen.</span><span class="sxs-lookup"><span data-stu-id="e521c-126">When each group is started, a custom label is displayed that includes the new value of the property.</span></span>

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

<span data-ttu-id="e521c-127">I följande exempel visas hur Windows PowerShell visar den [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objekt när den här formatfilen har lästs in.</span><span class="sxs-lookup"><span data-stu-id="e521c-127">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span> <span data-ttu-id="e521c-128">Tomma rader har lagts till före och efter Gruppetikett läggs automatiskt med Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e521c-128">The blank lines added before and after the group label are automatically added by Windows PowerShell.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e521c-129">Se även</span><span class="sxs-lookup"><span data-stu-id="e521c-129">See Also</span></span>

[<span data-ttu-id="e521c-130">Exempel på formatering filer</span><span class="sxs-lookup"><span data-stu-id="e521c-130">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="e521c-131">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="e521c-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
