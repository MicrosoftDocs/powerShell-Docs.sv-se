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
ms.openlocfilehash: c178c4a48f9595001bcc249d5f55886fa54bb9f2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356023"
---
# <a name="list-view-groupby"></a>Listvy (gruppbaserad)

Det här exemplet visar hur du implementerar en listvy som separerar rader i listan till grupper. I den här List visningen visas egenskaperna för [system. serviceprocess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -objekt som returneras av [Get-service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) -cmdleten. Mer information om komponenterna i en listvy finns i [skapa en listvy](./creating-a-list-view.md).

### <a name="to-load-this-formatting-file"></a>Läsa in den här format filen

1. Kopiera XML-filen från exempel avsnittet i det här avsnittet till en textfil.

2. Spara text filen. Se till att lägga till tillägget `format.ps1xml` i filen för att identifiera det som en format fil.

3. Öppna Windows PowerShell och kör följande kommando för att läsa in formaterings filen i den aktuella sessionen: `Update-formatdata -prependpath PathToFormattingFile`.

   > [!WARNING]
   > Den här format filen definierar visningen av ett objekt som redan har definierats av en Windows PowerShell-textfil. Du måste använda parametern `prependPath` när du kör cmdleten och du kan inte läsa in den här format filen som en modul.

## <a name="demonstrates"></a>Visat

Den här format filen visar följande XML-element:

- Vyns [namn](./name-element-for-view-format.md) -element.

- [ViewSelectedBy](./viewselectedby-element-format.md) -elementet som definierar vilka objekt som visas i vyn.

- Det [groupby](./viewselectedby-element-format.md) -element som definierar hur en ny grupp av objekt visas.

- Det [ListControl](./listcontrol-element-format.md) -element som definierar vilken egenskap som visas i vyn.

- Det [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) -element som definierar vad som visas i en rad i listvyn.

- Elementet [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) som definierar vilken egenskap som visas.

## <a name="example"></a>Exempel

Följande XML-kod definierar en listvy som startar en ny grupp när värdet för egenskapen [system. serviceprocess. ServiceController. status](/dotnet/api/System.ServiceProcess.ServiceController.Status) ändras. När varje grupp startas visas en anpassad etikett som innehåller det nya värdet för egenskapen.

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

I följande exempel visas hur Windows PowerShell visar [system. serviceprocess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -objekt efter den här format filen har lästs in. Tomma rader som lagts till före och efter grupp etiketten läggs automatiskt till av Windows PowerShell.

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

## <a name="see-also"></a>Se även

[Exempel på filer som ska formateras](./examples-of-formatting-files.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
