---
title: Bred vy (GroupBy) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e53714f0b4240b5fe7f62cccda83af1e5badd33c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785004"
---
# <a name="wide-view-groupby"></a><span data-ttu-id="cd1c8-102">Bred vy (gruppbaserad)</span><span class="sxs-lookup"><span data-stu-id="cd1c8-102">Wide View (GroupBy)</span></span>

<span data-ttu-id="cd1c8-103">Det här exemplet visar hur du implementerar en bred vy som visar grupper av [system. serviceprocess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -objekt som returneras av `Get-Service` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="cd1c8-103">This example shows how to implement a wide view that displays groups of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="cd1c8-104">Mer information om komponenterna i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="cd1c8-104">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="cd1c8-105">Läsa in den här format filen</span><span class="sxs-lookup"><span data-stu-id="cd1c8-105">To load this formatting file</span></span>

1. <span data-ttu-id="cd1c8-106">Kopiera XML-filen från exempel avsnittet i det här avsnittet till en textfil.</span><span class="sxs-lookup"><span data-stu-id="cd1c8-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="cd1c8-107">Spara textfilen.</span><span class="sxs-lookup"><span data-stu-id="cd1c8-107">Save the text file.</span></span> <span data-ttu-id="cd1c8-108">Se till att lägga till `format.ps1xml` tillägget i filen för att identifiera det som en format fil.</span><span class="sxs-lookup"><span data-stu-id="cd1c8-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="cd1c8-109">Öppna Windows PowerShell och kör följande kommando för att läsa in formaterings filen i den aktuella sessionen: `Update-formatdata -prependpath PathToFormattingFile` .</span><span class="sxs-lookup"><span data-stu-id="cd1c8-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="cd1c8-110">Den här format filen definierar visningen av ett objekt som redan har definierats av en Windows PowerShell-formateringsattribut.</span><span class="sxs-lookup"><span data-stu-id="cd1c8-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting files.</span></span> <span data-ttu-id="cd1c8-111">Du måste använda `prependPath` parametern när du kör cmdleten och du kan inte läsa in den här format filen som en modul.</span><span class="sxs-lookup"><span data-stu-id="cd1c8-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="cd1c8-112">Demonstrationer</span><span class="sxs-lookup"><span data-stu-id="cd1c8-112">Demonstrates</span></span>

<span data-ttu-id="cd1c8-113">Den här format filen visar följande XML-element:</span><span class="sxs-lookup"><span data-stu-id="cd1c8-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="cd1c8-114">Vyns [namn](./name-element-for-view-format.md) -element.</span><span class="sxs-lookup"><span data-stu-id="cd1c8-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="cd1c8-115">[ViewSelectedBy](./viewselectedby-element-format.md) -elementet som definierar vilka objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="cd1c8-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="cd1c8-116">Det [groupby](./groupby-element-for-view-format.md) -element som definierar när en ny grupp visas.</span><span class="sxs-lookup"><span data-stu-id="cd1c8-116">The [GroupBy](./groupby-element-for-view-format.md) element that defines when a new group is displayed.</span></span>

- <span data-ttu-id="cd1c8-117">Det [WideItem](./wideitem-element-for-widecontrol-format.md) -element som definierar vilken egenskap som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="cd1c8-117">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="cd1c8-118">Exempel</span><span class="sxs-lookup"><span data-stu-id="cd1c8-118">Example</span></span>

<span data-ttu-id="cd1c8-119">Följande XML-kod definierar en bred vy som visar objekt grupper.</span><span class="sxs-lookup"><span data-stu-id="cd1c8-119">The following XML defines a wide view that displays groups of objects.</span></span> <span data-ttu-id="cd1c8-120">Varje ny grupp startas när värdet för egenskapen [system. serviceprocess. ServiceController. ServiceType](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) ändras.</span><span class="sxs-lookup"><span data-stu-id="cd1c8-120">Each new group is started when the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

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

<span data-ttu-id="cd1c8-121">I följande exempel visas hur Windows PowerShell visar [system. serviceprocess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -objekt efter den här format filen har lästs in.</span><span class="sxs-lookup"><span data-stu-id="cd1c8-121">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="cd1c8-122">Se även</span><span class="sxs-lookup"><span data-stu-id="cd1c8-122">See Also</span></span>

[<span data-ttu-id="cd1c8-123">Exempel på formateringsfiler</span><span class="sxs-lookup"><span data-stu-id="cd1c8-123">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="cd1c8-124">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="cd1c8-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
