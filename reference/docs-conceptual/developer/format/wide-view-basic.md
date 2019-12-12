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
# <a name="wide-view-basic"></a>Bred vy (grundläggande)

Det här exemplet visar hur du implementerar en grundläggande bred vy som visar [system. serviceprocess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -objekt som returneras av `Get-Service`-cmdleten. Mer information om komponenterna i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).

### <a name="to-load-this-formatting-file"></a>Läsa in den här format filen

1. Kopiera XML-filen från exempel avsnittet i det här avsnittet till en textfil.

2. Spara textfilen. Se till att lägga till `format.ps1xml`-tillägget till filen för att identifiera det som en format fil.

3. Öppna Windows PowerShell och kör följande kommando för att läsa in formaterings filen i den aktuella sessionen: `Update-formatdata -prependpath PathToFormattingFile`.

   > [!WARNING]
   > Den här format filen definierar visningen av ett objekt som redan har definierats av en Windows PowerShell-textfil. Du måste använda parametern `prependPath` när du kör cmdleten, och du kan inte läsa in den här format filen som en modul.

## <a name="demonstrates"></a>Demonstrationer

Den här format filen visar följande XML-element:

- Vyns [namn](./name-element-for-view-format.md) -element.

- [ViewSelectedBy](./viewselectedby-element-format.md) -elementet som definierar vilka objekt som visas i vyn.

- Det [WideItem](./wideitem-element-for-widecontrol-format.md) -element som definierar vilken egenskap som visas i vyn.

## <a name="example"></a>Exempel

Följande XML-kod definierar en bred vy som visar värdet för egenskapen [system. serviceprocess. ServiceController. ServiceName](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) .

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

I följande exempel visas hur Windows PowerShell visar [system. serviceprocess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -objekt efter den här format filen har lästs in.

```powershell
Get-Service f*
```

```output
Fax                      FCSAM
fdPHost                  FDResPub
FontCache                FontCache3.0.0.0
FSysAgent                FwcAgent
```

## <a name="see-also"></a>Se även

[Exempel på filer som ska formateras](./examples-of-formatting-files.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
