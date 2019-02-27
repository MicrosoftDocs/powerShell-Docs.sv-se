---
title: Listvy (grundläggande) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 918f381c-43e6-4594-a468-a40bfa8a16d6
caps.latest.revision: 7
ms.openlocfilehash: 1c683693c331ccfaf7355a0dd51801ed6fd39b3b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844928"
---
# <a name="list-view-basic"></a><span data-ttu-id="26fca-102">Listvy (grundläggande)</span><span class="sxs-lookup"><span data-stu-id="26fca-102">List View (Basic)</span></span>

<span data-ttu-id="26fca-103">Det här exemplet visar hur du implementerar en grundläggande listvy som visar den [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objekten som returneras av den [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="26fca-103">This example shows how to implement a basic list view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="26fca-104">Läs mer om komponenterna i en listvy, [skapar en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="26fca-104">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>
<span data-ttu-id="26fca-105">Det här exemplet visar hur du implementerar en grundläggande listvy som visar den [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objekten som returneras av den [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="26fca-105">This example shows how to implement a basic list view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="26fca-106">Läs mer om komponenterna i en listvy, [skapar en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="26fca-106">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="26fca-107">Att läsa in den här formatering filen</span><span class="sxs-lookup"><span data-stu-id="26fca-107">To load this formatting file</span></span>

1. <span data-ttu-id="26fca-108">Kopiera XML-filen från avsnittet exempel i den här artikeln i en textfil.</span><span class="sxs-lookup"><span data-stu-id="26fca-108">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="26fca-109">Spara filen.</span><span class="sxs-lookup"><span data-stu-id="26fca-109">Save the text file.</span></span> <span data-ttu-id="26fca-110">Se till att lägga till den `format.ps1xml` tillägg till filen för att identifiera den som en formatering fil.</span><span class="sxs-lookup"><span data-stu-id="26fca-110">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="26fca-111">Öppna Windows PowerShell och kör följande kommando för att läsa in filen formatering i den aktuella sessionen: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="26fca-111">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="26fca-112">Den här formatering filen definierar visning av ett objekt som redan har definierats av en formatering Windows PowerShell-fil.</span><span class="sxs-lookup"><span data-stu-id="26fca-112">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="26fca-113">Du måste använda den `prependPath` parameter när du kör cmdlet: en, och du kan inte läsa in den här formateringen filen som en modul.</span><span class="sxs-lookup"><span data-stu-id="26fca-113">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="26fca-114">Visar</span><span class="sxs-lookup"><span data-stu-id="26fca-114">Demonstrates</span></span>

<span data-ttu-id="26fca-115">Den här formatering filen visar följande XML-element:</span><span class="sxs-lookup"><span data-stu-id="26fca-115">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="26fca-116">Den [namn](./name-element-for-view-format.md) element för vyn.</span><span class="sxs-lookup"><span data-stu-id="26fca-116">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="26fca-117">Den [ViewSelectedBy](./viewselectedby-element-format.md) -element som definierar vilka objekt visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="26fca-117">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="26fca-118">Den [ListControl](./listcontrol-element-format.md) element som definierar vilka egenskapen visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="26fca-118">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="26fca-119">Den [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) -element som definierar vad som visas i en rad i listvyn.</span><span class="sxs-lookup"><span data-stu-id="26fca-119">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="26fca-120">Den [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element som definierar vilken egenskap visas.</span><span class="sxs-lookup"><span data-stu-id="26fca-120">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="26fca-121">Exempel</span><span class="sxs-lookup"><span data-stu-id="26fca-121">Example</span></span>

<span data-ttu-id="26fca-122">Följande XML-filen definierar en listvy som visar fyra egenskaperna för den [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objekt.</span><span class="sxs-lookup"><span data-stu-id="26fca-122">The following XML defines a list view that displays four properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="26fca-123">På varje rad visas namnet på egenskapen följt av värdet för egenskapen.</span><span class="sxs-lookup"><span data-stu-id="26fca-123">In each row, the name of the property is displayed followed by the value of the property.</span></span>

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

<span data-ttu-id="26fca-124">I följande exempel visas hur Windows PowerShell visar den [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objekt när den här formatfilen har lästs in.</span><span class="sxs-lookup"><span data-stu-id="26fca-124">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="26fca-125">Se även</span><span class="sxs-lookup"><span data-stu-id="26fca-125">See Also</span></span>

[<span data-ttu-id="26fca-126">Exempel på formatering filer</span><span class="sxs-lookup"><span data-stu-id="26fca-126">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="26fca-127">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="26fca-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
