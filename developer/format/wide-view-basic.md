---
title: Bred vy (grundläggande) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9abb63b8-6d02-4e24-9c0e-2d15a04e9051
caps.latest.revision: 8
ms.openlocfilehash: 7a36f548a3eccdf2c9cad04a8bfe28bf4e8d6dfd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849688"
---
# <a name="wide-view-basic"></a><span data-ttu-id="d057b-102">Bred vy (grundläggande)</span><span class="sxs-lookup"><span data-stu-id="d057b-102">Wide View (Basic)</span></span>

<span data-ttu-id="d057b-103">Det här exemplet visar hur du implementerar en grundläggande bred vy som visar den [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objekten som returneras av den `Get-Service` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d057b-103">This example shows how to implement a basic wide view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="d057b-104">Mer information om komponenter för en bred vy finns i [skapar en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="d057b-104">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="d057b-105">Att läsa in den här formatering filen</span><span class="sxs-lookup"><span data-stu-id="d057b-105">To load this formatting file</span></span>

1. <span data-ttu-id="d057b-106">Kopiera XML-filen från avsnittet exempel i den här artikeln i en textfil.</span><span class="sxs-lookup"><span data-stu-id="d057b-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="d057b-107">Spara filen.</span><span class="sxs-lookup"><span data-stu-id="d057b-107">Save the text file.</span></span> <span data-ttu-id="d057b-108">Se till att lägga till den `format.ps1xml` tillägg till filen för att identifiera den som en formatering fil.</span><span class="sxs-lookup"><span data-stu-id="d057b-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="d057b-109">Öppna Windows PowerShell och kör följande kommando för att läsa in filen formatering i den aktuella sessionen: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="d057b-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="d057b-110">Den här formatering filen definierar visning av ett objekt som redan har definierats av en formatering Windows PowerShell-fil.</span><span class="sxs-lookup"><span data-stu-id="d057b-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="d057b-111">Du måste använda den `prependPath` parameter när du kör cmdlet: en, och du kan inte läsa in den här formateringen filen som en modul.</span><span class="sxs-lookup"><span data-stu-id="d057b-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="d057b-112">Visar</span><span class="sxs-lookup"><span data-stu-id="d057b-112">Demonstrates</span></span>

<span data-ttu-id="d057b-113">Den här formatering filen visar följande XML-element:</span><span class="sxs-lookup"><span data-stu-id="d057b-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="d057b-114">Den [namn](./name-element-for-view-format.md) element för vyn.</span><span class="sxs-lookup"><span data-stu-id="d057b-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="d057b-115">Den [ViewSelectedBy](./viewselectedby-element-format.md) -element som definierar vilka objekt visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="d057b-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="d057b-116">Den [WideItem](./wideitem-element-for-widecontrol-format.md) element som definierar vilka egenskapen visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="d057b-116">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="d057b-117">Exempel</span><span class="sxs-lookup"><span data-stu-id="d057b-117">Example</span></span>

<span data-ttu-id="d057b-118">Följande XML-filen definierar en bred vy som visar värdet för den [System.Serviceprocess.Servicecontroller.Servicename](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) egenskapen.</span><span class="sxs-lookup"><span data-stu-id="d057b-118">The following XML defines a wide view that displays the value of the [System.Serviceprocess.Servicecontroller.Servicename](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) property.</span></span>

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

<span data-ttu-id="d057b-119">I följande exempel visas hur Windows PowerShell visar den [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objekt när den här formatfilen har lästs in.</span><span class="sxs-lookup"><span data-stu-id="d057b-119">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
Fax                      FCSAM
fdPHost                  FDResPub
FontCache                FontCache3.0.0.0
FSysAgent                FwcAgent
```

## <a name="see-also"></a><span data-ttu-id="d057b-120">Se även</span><span class="sxs-lookup"><span data-stu-id="d057b-120">See Also</span></span>

[<span data-ttu-id="d057b-121">Exempel på formatering filer</span><span class="sxs-lookup"><span data-stu-id="d057b-121">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="d057b-122">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="d057b-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
