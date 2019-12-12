---
title: Bred vy (Basic) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9abb63b8-6d02-4e24-9c0e-2d15a04e9051
caps.latest.revision: 8
ms.openlocfilehash: 7a36f548a3eccdf2c9cad04a8bfe28bf4e8d6dfd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358724"
---
# <a name="wide-view-basic"></a><span data-ttu-id="eea54-102">Bred vy (grundläggande)</span><span class="sxs-lookup"><span data-stu-id="eea54-102">Wide View (Basic)</span></span>

<span data-ttu-id="eea54-103">Det här exemplet visar hur du implementerar en grundläggande bred vy som visar [system. serviceprocess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -objekt som returneras av `Get-Service`-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="eea54-103">This example shows how to implement a basic wide view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="eea54-104">Mer information om komponenterna i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="eea54-104">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="eea54-105">Läsa in den här format filen</span><span class="sxs-lookup"><span data-stu-id="eea54-105">To load this formatting file</span></span>

1. <span data-ttu-id="eea54-106">Kopiera XML-filen från exempel avsnittet i det här avsnittet till en textfil.</span><span class="sxs-lookup"><span data-stu-id="eea54-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="eea54-107">Spara textfilen.</span><span class="sxs-lookup"><span data-stu-id="eea54-107">Save the text file.</span></span> <span data-ttu-id="eea54-108">Se till att lägga till `format.ps1xml`-tillägget till filen för att identifiera det som en format fil.</span><span class="sxs-lookup"><span data-stu-id="eea54-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="eea54-109">Öppna Windows PowerShell och kör följande kommando för att läsa in formaterings filen i den aktuella sessionen: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="eea54-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="eea54-110">Den här format filen definierar visningen av ett objekt som redan har definierats av en Windows PowerShell-textfil.</span><span class="sxs-lookup"><span data-stu-id="eea54-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="eea54-111">Du måste använda parametern `prependPath` när du kör cmdleten, och du kan inte läsa in den här format filen som en modul.</span><span class="sxs-lookup"><span data-stu-id="eea54-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="eea54-112">Demonstrationer</span><span class="sxs-lookup"><span data-stu-id="eea54-112">Demonstrates</span></span>

<span data-ttu-id="eea54-113">Den här format filen visar följande XML-element:</span><span class="sxs-lookup"><span data-stu-id="eea54-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="eea54-114">Vyns [namn](./name-element-for-view-format.md) -element.</span><span class="sxs-lookup"><span data-stu-id="eea54-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="eea54-115">[ViewSelectedBy](./viewselectedby-element-format.md) -elementet som definierar vilka objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="eea54-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="eea54-116">Det [WideItem](./wideitem-element-for-widecontrol-format.md) -element som definierar vilken egenskap som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="eea54-116">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="eea54-117">Exempel</span><span class="sxs-lookup"><span data-stu-id="eea54-117">Example</span></span>

<span data-ttu-id="eea54-118">Följande XML-kod definierar en bred vy som visar värdet för egenskapen [system. serviceprocess. ServiceController. ServiceName](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) .</span><span class="sxs-lookup"><span data-stu-id="eea54-118">The following XML defines a wide view that displays the value of the [System.Serviceprocess.Servicecontroller.Servicename](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) property.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Configuration>
  <ViewDefinitions>
    <View>
      <Name>ServiceWideView</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
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

<span data-ttu-id="eea54-119">I följande exempel visas hur Windows PowerShell visar [system. serviceprocess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -objekt efter den här format filen har lästs in.</span><span class="sxs-lookup"><span data-stu-id="eea54-119">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
Fax                      FCSAM
fdPHost                  FDResPub
FontCache                FontCache3.0.0.0
FSysAgent                FwcAgent
```

## <a name="see-also"></a><span data-ttu-id="eea54-120">Se även</span><span class="sxs-lookup"><span data-stu-id="eea54-120">See Also</span></span>

[<span data-ttu-id="eea54-121">Exempel på filer som ska formateras</span><span class="sxs-lookup"><span data-stu-id="eea54-121">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="eea54-122">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="eea54-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
