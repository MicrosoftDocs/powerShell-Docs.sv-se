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
ms.openlocfilehash: 2bb62ab3e4fa1db9b3af8c82eb9035aa4f3e31c0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849702"
---
# <a name="list-view-labels"></a><span data-ttu-id="a51e3-102">Listvy (etiketter)</span><span class="sxs-lookup"><span data-stu-id="a51e3-102">List View (Labels)</span></span>

<span data-ttu-id="a51e3-103">Det här exemplet visar hur du implementerar en listvy som visar en anpassad etikett för varje rad i listan.</span><span class="sxs-lookup"><span data-stu-id="a51e3-103">This example shows how to implement a list view that displays a custom label for each row of the list.</span></span> <span data-ttu-id="a51e3-104">I den här listan visas egenskaperna för den [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objekt som returneras av den [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a51e3-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="a51e3-105">Läs mer om komponenterna i en listvy, [skapar en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="a51e3-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>
<span data-ttu-id="a51e3-106">Det här exemplet visar hur du implementerar en listvy som visar en anpassad etikett för varje rad i listan.</span><span class="sxs-lookup"><span data-stu-id="a51e3-106">This example shows how to implement a list view that displays a custom label for each row of the list.</span></span> <span data-ttu-id="a51e3-107">I den här listan visas egenskaperna för den [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objekt som returneras av den [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a51e3-107">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="a51e3-108">Läs mer om komponenterna i en listvy, [skapar en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="a51e3-108">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="a51e3-109">Att läsa in den här formatering filen</span><span class="sxs-lookup"><span data-stu-id="a51e3-109">To load this formatting file</span></span>

1. <span data-ttu-id="a51e3-110">Kopiera XML-filen från avsnittet exempel i den här artikeln i en textfil.</span><span class="sxs-lookup"><span data-stu-id="a51e3-110">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="a51e3-111">Spara filen.</span><span class="sxs-lookup"><span data-stu-id="a51e3-111">Save the text file.</span></span> <span data-ttu-id="a51e3-112">Se till att lägga till den `format.ps1xml` tillägg till filen för att identifiera den som en formatering fil.</span><span class="sxs-lookup"><span data-stu-id="a51e3-112">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="a51e3-113">Öppna Windows PowerShell och kör följande kommando för att läsa in filen formatering i den aktuella sessionen: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="a51e3-113">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="a51e3-114">Den här formatering filen definierar visning av ett objekt som redan har definierats av en formatering Windows PowerShell-fil.</span><span class="sxs-lookup"><span data-stu-id="a51e3-114">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="a51e3-115">Du måste använda den `prependPath` parameter när du kör cmdlet: en, och du kan inte läsa in den här formateringen filen som en modul.</span><span class="sxs-lookup"><span data-stu-id="a51e3-115">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="a51e3-116">Visar</span><span class="sxs-lookup"><span data-stu-id="a51e3-116">Demonstrates</span></span>

<span data-ttu-id="a51e3-117">Den här formatering filen visar följande XML-element:</span><span class="sxs-lookup"><span data-stu-id="a51e3-117">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="a51e3-118">Den [namn](./name-element-for-view-format.md) element för vyn.</span><span class="sxs-lookup"><span data-stu-id="a51e3-118">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="a51e3-119">Den [ViewSelectedBy](./viewselectedby-element-format.md) -element som definierar vilka objekt visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="a51e3-119">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="a51e3-120">Den [ListControl](./listcontrol-element-format.md) element som definierar vilka egenskapen visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="a51e3-120">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="a51e3-121">Den [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) -element som definierar vad som visas i en rad i listvyn.</span><span class="sxs-lookup"><span data-stu-id="a51e3-121">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="a51e3-122">Den [etikett](./label-element-for-listitem-for-listcontrol-format.md) -element som definierar vad som visas i en rad i listvyn.</span><span class="sxs-lookup"><span data-stu-id="a51e3-122">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="a51e3-123">Den [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element som definierar vilken egenskap visas.</span><span class="sxs-lookup"><span data-stu-id="a51e3-123">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="a51e3-124">Exempel</span><span class="sxs-lookup"><span data-stu-id="a51e3-124">Example</span></span>

<span data-ttu-id="a51e3-125">Följande XML-filen definierar en listvy som visar en egen etikett på varje rad.</span><span class="sxs-lookup"><span data-stu-id="a51e3-125">The following XML defines a list view that displays a custom label in each row.</span></span> <span data-ttu-id="a51e3-126">I det här fallet innehåller etiketten egenskapsnamnet med varje versal bokstav och ordet ”property”.</span><span class="sxs-lookup"><span data-stu-id="a51e3-126">In this case, the label includes the property name with each letter capitalized and the word "property".</span></span> <span data-ttu-id="a51e3-127">På varje rad visas namnet på egenskapen följt av värdet för egenskapen.</span><span class="sxs-lookup"><span data-stu-id="a51e3-127">In each row, the name of the property is displayed followed by the value of the property.</span></span>

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

<span data-ttu-id="a51e3-128">I följande exempel visas hur Windows PowerShell visar den [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objekt när den här formatfilen har lästs in.</span><span class="sxs-lookup"><span data-stu-id="a51e3-128">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a51e3-129">Se även</span><span class="sxs-lookup"><span data-stu-id="a51e3-129">See Also</span></span>

[<span data-ttu-id="a51e3-130">Exempel på formatering filer</span><span class="sxs-lookup"><span data-stu-id="a51e3-130">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="a51e3-131">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="a51e3-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
