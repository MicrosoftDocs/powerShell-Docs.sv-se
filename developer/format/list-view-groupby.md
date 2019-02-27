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
ms.openlocfilehash: ad7ea457fe0f67bfa41f6bf81f36d4b2e4a76cb3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849716"
---
# <a name="list-view-groupby"></a>Listvy (gruppbaserad)

Det här exemplet visar hur du implementerar en listvy som avgränsar raderna i listan i grupper. I den här listan visas egenskaperna för den [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objekten som returneras av den [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet. Läs mer om komponenterna i en listvy, [skapar en listvy](./creating-a-list-view.md).
Det här exemplet visar hur du implementerar en listvy som avgränsar raderna i listan i grupper. I den här listan visas egenskaperna för den [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objekten som returneras av den [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet. Läs mer om komponenterna i en listvy, [skapar en listvy](./creating-a-list-view.md).

### <a name="to-load-this-formatting-file"></a>Att läsa in den här formatering filen

1. Kopiera XML-filen från avsnittet exempel i den här artikeln i en textfil.

2. Spara filen. Se till att lägga till den `format.ps1xml` tillägg till filen för att identifiera den som en formatering fil.

3. Öppna Windows PowerShell och kör följande kommando för att läsa in filen formatering i den aktuella sessionen: `Update-formatdata -prependpath PathToFormattingFile`.

   > [!WARNING]
   > Den här formatering filen definierar visning av ett objekt som redan har definierats av en formatering Windows PowerShell-fil. Du måste använda den `prependPath` parameter när du kör cmdlet: en, och du kan inte läsa in den här formateringen filen som en modul.

## <a name="demonstrates"></a>Visar

Den här formatering filen visar följande XML-element:

- Den [namn](./name-element-for-view-format.md) element för vyn.

- Den [ViewSelectedBy](./viewselectedby-element-format.md) -element som definierar vilka objekt visas i vyn.

- Den [GroupBy](./viewselectedby-element-format.md) element som definierar hur en ny grupp med objekt visas.

- Den [ListControl](./listcontrol-element-format.md) element som definierar vilka egenskapen visas i vyn.

- Den [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) -element som definierar vad som visas i en rad i listvyn.

- Den [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element som definierar vilken egenskap visas.

## <a name="example"></a>Exempel

Följande XML-filen definierar en listvy som startar en ny grupp när värdet för den [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) egenskapsändringar. När varje grupp har startats visas en anpassad etikett med det nya värdet för egenskapen.

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

I följande exempel visas hur Windows PowerShell visar den [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objekt när den här formatfilen har lästs in. Tomma rader har lagts till före och efter Gruppetikett läggs automatiskt med Windows PowerShell.

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

[Exempel på formatering filer](./examples-of-formatting-files.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
