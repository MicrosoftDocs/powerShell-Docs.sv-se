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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358717"
---
# <a name="wide-view-groupby"></a>Bred vy (gruppbaserad)

Det här exemplet visar hur du implementerar en bred vy som visar grupper av [system. serviceprocess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -objekt som returneras av `Get-Service`-cmdleten. Mer information om komponenterna i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).

### <a name="to-load-this-formatting-file"></a>Läsa in den här format filen

1. Kopiera XML-filen från exempel avsnittet i det här avsnittet till en textfil.

2. Spara text filen. Se till att lägga till tillägget `format.ps1xml` i filen för att identifiera det som en format fil.

3. Öppna Windows PowerShell och kör följande kommando för att läsa in formaterings filen i den aktuella sessionen: `Update-formatdata -prependpath PathToFormattingFile`.

   > [!WARNING]
   > Den här format filen definierar visningen av ett objekt som redan har definierats av en Windows PowerShell-formateringsattribut. Du måste använda parametern `prependPath` när du kör cmdleten och du kan inte läsa in den här format filen som en modul.

## <a name="demonstrates"></a>Visat

Den här format filen visar följande XML-element:

- Vyns [namn](./name-element-for-view-format.md) -element.

- [ViewSelectedBy](./viewselectedby-element-format.md) -elementet som definierar vilka objekt som visas i vyn.

- Det [groupby](./groupby-element-for-view-format.md) -element som definierar när en ny grupp visas.

- Det [WideItem](./wideitem-element-for-widecontrol-format.md) -element som definierar vilken egenskap som visas i vyn.

## <a name="example"></a>Exempel

Följande XML-kod definierar en bred vy som visar objekt grupper. Varje ny grupp startas när värdet för egenskapen [system. serviceprocess. ServiceController. ServiceType](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) ändras.

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

I följande exempel visas hur Windows PowerShell visar [system. serviceprocess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -objekt efter den här format filen har lästs in.

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

## <a name="see-also"></a>Se även

[Exempel på filer som ska formateras](./examples-of-formatting-files.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
