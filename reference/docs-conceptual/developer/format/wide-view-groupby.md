---
title: Bred vy (GroupBy) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39388197-4ff9-4889-aa32-526011afa1f6
caps.latest.revision: 6
ms.openlocfilehash: e95ec550a7815a76a8bd7f9526dfa405a9644360
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358717"
---
# <a name="wide-view-groupby"></a><span data-ttu-id="2f6bf-102">Bred vy (gruppbaserad)</span><span class="sxs-lookup"><span data-stu-id="2f6bf-102">Wide View (GroupBy)</span></span>

<span data-ttu-id="2f6bf-103">Det här exemplet visar hur du implementerar en bred vy som visar grupper av [system. serviceprocess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -objekt som returneras av `Get-Service`-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2f6bf-103">This example shows how to implement a wide view that displays groups of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="2f6bf-104">Mer information om komponenterna i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="2f6bf-104">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="2f6bf-105">Läsa in den här format filen</span><span class="sxs-lookup"><span data-stu-id="2f6bf-105">To load this formatting file</span></span>

1. <span data-ttu-id="2f6bf-106">Kopiera XML-filen från exempel avsnittet i det här avsnittet till en textfil.</span><span class="sxs-lookup"><span data-stu-id="2f6bf-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="2f6bf-107">Spara textfilen.</span><span class="sxs-lookup"><span data-stu-id="2f6bf-107">Save the text file.</span></span> <span data-ttu-id="2f6bf-108">Se till att lägga till `format.ps1xml`-tillägget till filen för att identifiera det som en format fil.</span><span class="sxs-lookup"><span data-stu-id="2f6bf-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="2f6bf-109">Öppna Windows PowerShell och kör följande kommando för att läsa in formaterings filen i den aktuella sessionen: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="2f6bf-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="2f6bf-110">Den här format filen definierar visningen av ett objekt som redan har definierats av en Windows PowerShell-formateringsattribut.</span><span class="sxs-lookup"><span data-stu-id="2f6bf-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting files.</span></span> <span data-ttu-id="2f6bf-111">Du måste använda parametern `prependPath` när du kör cmdleten, och du kan inte läsa in den här format filen som en modul.</span><span class="sxs-lookup"><span data-stu-id="2f6bf-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="2f6bf-112">Demonstrationer</span><span class="sxs-lookup"><span data-stu-id="2f6bf-112">Demonstrates</span></span>

<span data-ttu-id="2f6bf-113">Den här format filen visar följande XML-element:</span><span class="sxs-lookup"><span data-stu-id="2f6bf-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="2f6bf-114">Vyns [namn](./name-element-for-view-format.md) -element.</span><span class="sxs-lookup"><span data-stu-id="2f6bf-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="2f6bf-115">[ViewSelectedBy](./viewselectedby-element-format.md) -elementet som definierar vilka objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="2f6bf-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="2f6bf-116">Det [groupby](./groupby-element-for-view-format.md) -element som definierar när en ny grupp visas.</span><span class="sxs-lookup"><span data-stu-id="2f6bf-116">The [GroupBy](./groupby-element-for-view-format.md) element that defines when a new group is displayed.</span></span>

- <span data-ttu-id="2f6bf-117">Det [WideItem](./wideitem-element-for-widecontrol-format.md) -element som definierar vilken egenskap som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="2f6bf-117">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="2f6bf-118">Exempel</span><span class="sxs-lookup"><span data-stu-id="2f6bf-118">Example</span></span>

<span data-ttu-id="2f6bf-119">Följande XML-kod definierar en bred vy som visar objekt grupper.</span><span class="sxs-lookup"><span data-stu-id="2f6bf-119">The following XML defines a wide view that displays groups of objects.</span></span> <span data-ttu-id="2f6bf-120">Varje ny grupp startas när värdet för egenskapen [system. serviceprocess. ServiceController. ServiceType](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) ändras.</span><span class="sxs-lookup"><span data-stu-id="2f6bf-120">Each new group is started when the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

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

<span data-ttu-id="2f6bf-121">I följande exempel visas hur Windows PowerShell visar [system. serviceprocess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -objekt efter den här format filen har lästs in.</span><span class="sxs-lookup"><span data-stu-id="2f6bf-121">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2f6bf-122">Se även</span><span class="sxs-lookup"><span data-stu-id="2f6bf-122">See Also</span></span>

[<span data-ttu-id="2f6bf-123">Exempel på filer som ska formateras</span><span class="sxs-lookup"><span data-stu-id="2f6bf-123">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="2f6bf-124">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="2f6bf-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
