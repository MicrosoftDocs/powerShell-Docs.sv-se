---
ms.date: 09/13/2016
ms.topic: reference
title: Bred vy (gruppbaserad)
description: Bred vy (gruppbaserad)
ms.openlocfilehash: 807bea2a5d44c38e2c9977f792bea2fb9bca0fc3
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667682"
---
# <a name="wide-view-groupby"></a><span data-ttu-id="0f9dd-103">Bred vy (gruppbaserad)</span><span class="sxs-lookup"><span data-stu-id="0f9dd-103">Wide View (GroupBy)</span></span>

<span data-ttu-id="0f9dd-104">Det här exemplet visar hur du implementerar en bred vy som visar grupper av [system. serviceprocess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -objekt som returneras av `Get-Service` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="0f9dd-104">This example shows how to implement a wide view that displays groups of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="0f9dd-105">Mer information om komponenterna i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="0f9dd-105">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="0f9dd-106">Läsa in den här format filen</span><span class="sxs-lookup"><span data-stu-id="0f9dd-106">To load this formatting file</span></span>

1. <span data-ttu-id="0f9dd-107">Kopiera XML-filen från exempel avsnittet i det här avsnittet till en textfil.</span><span class="sxs-lookup"><span data-stu-id="0f9dd-107">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="0f9dd-108">Spara textfilen.</span><span class="sxs-lookup"><span data-stu-id="0f9dd-108">Save the text file.</span></span> <span data-ttu-id="0f9dd-109">Se till att lägga till `format.ps1xml` tillägget i filen för att identifiera det som en format fil.</span><span class="sxs-lookup"><span data-stu-id="0f9dd-109">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="0f9dd-110">Öppna Windows PowerShell och kör följande kommando för att läsa in formaterings filen i den aktuella sessionen: `Update-formatdata -prependpath PathToFormattingFile` .</span><span class="sxs-lookup"><span data-stu-id="0f9dd-110">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="0f9dd-111">Den här format filen definierar visningen av ett objekt som redan har definierats av en Windows PowerShell-formateringsattribut.</span><span class="sxs-lookup"><span data-stu-id="0f9dd-111">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting files.</span></span> <span data-ttu-id="0f9dd-112">Du måste använda `prependPath` parametern när du kör cmdleten och du kan inte läsa in den här format filen som en modul.</span><span class="sxs-lookup"><span data-stu-id="0f9dd-112">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="0f9dd-113">Demonstrationer</span><span class="sxs-lookup"><span data-stu-id="0f9dd-113">Demonstrates</span></span>

<span data-ttu-id="0f9dd-114">Den här format filen visar följande XML-element:</span><span class="sxs-lookup"><span data-stu-id="0f9dd-114">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="0f9dd-115">Vyns [namn](./name-element-for-view-format.md) -element.</span><span class="sxs-lookup"><span data-stu-id="0f9dd-115">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="0f9dd-116">[ViewSelectedBy](./viewselectedby-element-format.md) -elementet som definierar vilka objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="0f9dd-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="0f9dd-117">Det [groupby](./groupby-element-for-view-format.md) -element som definierar när en ny grupp visas.</span><span class="sxs-lookup"><span data-stu-id="0f9dd-117">The [GroupBy](./groupby-element-for-view-format.md) element that defines when a new group is displayed.</span></span>

- <span data-ttu-id="0f9dd-118">Det [WideItem](./wideitem-element-for-widecontrol-format.md) -element som definierar vilken egenskap som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="0f9dd-118">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="0f9dd-119">Exempel</span><span class="sxs-lookup"><span data-stu-id="0f9dd-119">Example</span></span>

<span data-ttu-id="0f9dd-120">Följande XML-kod definierar en bred vy som visar objekt grupper.</span><span class="sxs-lookup"><span data-stu-id="0f9dd-120">The following XML defines a wide view that displays groups of objects.</span></span> <span data-ttu-id="0f9dd-121">Varje ny grupp startas när värdet för egenskapen [system. serviceprocess. ServiceController. ServiceType](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) ändras.</span><span class="sxs-lookup"><span data-stu-id="0f9dd-121">Each new group is started when the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Configuration>
  <ViewDefinitions>
    <View>
      <Name>ServiceWideView</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <Label>Service Type</Label>
        <PropertyName>ServiceType</PropertyName>
      </GroupBy>
      <WideControl>
        <WideEntries>
          <WideEntry>
            <WideItem>
              <PropertyName>ServiceName</PropertyName>
            </WideItem>
          </WideEntry>
        </WideEntries>
      </WideControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

<span data-ttu-id="0f9dd-122">I följande exempel visas hur Windows PowerShell visar [system. serviceprocess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -objekt efter den här format filen har lästs in.</span><span class="sxs-lookup"><span data-stu-id="0f9dd-122">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
   Service Type: Win32OwnProcess

Fax                             FCSAM

   Service Type: Win32ShareProcess

fdPHost                         FDResPub
FontCache

   Service Type: Win32OwnProcess

FontCache3.0.0.0                FSysAgent
FwcAgent
```

## <a name="see-also"></a><span data-ttu-id="0f9dd-123">Se även</span><span class="sxs-lookup"><span data-stu-id="0f9dd-123">See Also</span></span>

[<span data-ttu-id="0f9dd-124">Exempel på formateringsfiler</span><span class="sxs-lookup"><span data-stu-id="0f9dd-124">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="0f9dd-125">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="0f9dd-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
