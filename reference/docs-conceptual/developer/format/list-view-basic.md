---
title: Listvy (Basic) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 74ff8f6eee0a9358c123455aa00736a11e7f085d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783559"
---
# <a name="list-view-basic"></a>Listvy (grundläggande)

I det här exemplet visas hur du implementerar en grundläggande listvy som visar [system. serviceprocess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -objekt som returneras av [Get-service](/powershell/module/microsoft.powershell.management/get-service) -cmdleten. Mer information om komponenterna i en listvy finns i [skapa en listvy](./creating-a-list-view.md).

### <a name="to-load-this-formatting-file"></a>Läsa in den här format filen

1. Kopiera XML-filen från exempel avsnittet i det här avsnittet till en textfil.

2. Spara textfilen. Se till att lägga till `format.ps1xml` tillägget i filen för att identifiera det som en format fil.

3. Öppna Windows PowerShell och kör följande kommando för att läsa in formaterings filen i den aktuella sessionen: `Update-formatdata -prependpath PathToFormattingFile` .

   > [!WARNING]
   > Den här format filen definierar visningen av ett objekt som redan har definierats av en Windows PowerShell-textfil. Du måste använda `prependPath` parametern när du kör cmdleten och du kan inte läsa in den här format filen som en modul.

## <a name="demonstrates"></a>Demonstrationer

Den här format filen visar följande XML-element:

- Vyns [namn](./name-element-for-view-format.md) -element.

- [ViewSelectedBy](./viewselectedby-element-format.md) -elementet som definierar vilka objekt som visas i vyn.

- Det [ListControl](./listcontrol-element-format.md) -element som definierar vilken egenskap som visas i vyn.

- Det [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) -element som definierar vad som visas i en rad i listvyn.

- Elementet [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) som definierar vilken egenskap som visas.

## <a name="example"></a>Exempel

Följande XML-kod definierar en listvy som visar fyra egenskaper för [system. serviceprocess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -objekt. På varje rad visas namnet på egenskapen följt av egenskapens värde.

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

I följande exempel visas hur Windows PowerShell visar [system. serviceprocess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -objekt efter den här format filen har lästs in.

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

## <a name="see-also"></a>Se även

[Exempel på formateringsfiler](./examples-of-formatting-files.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
