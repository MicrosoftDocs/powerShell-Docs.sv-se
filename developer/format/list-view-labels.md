---
title: Listvy (etiketter) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53442bb1-74a3-49f9-9150-3bc3081a7565
caps.latest.revision: 6
ms.openlocfilehash: 27de41c88e224f7610c10a764e51524016ecc8cb
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794832"
---
# <a name="list-view-labels"></a>Listvy (etiketter)

Det här exemplet visar hur du implementerar en listvy som visar en anpassad etikett för varje rad i listan. I den här listan visas egenskaperna för den [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objekt som returneras av den [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet. Läs mer om komponenterna i en listvy, [skapar en listvy](./creating-a-list-view.md).

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

- Den [ListControl](./listcontrol-element-format.md) element som definierar vilka egenskapen visas i vyn.

- Den [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) -element som definierar vad som visas i en rad i listvyn.

- Den [etikett](./label-element-for-listitem-for-listcontrol-format.md) -element som definierar vad som visas i en rad i listvyn.

- Den [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element som definierar vilken egenskap visas.

## <a name="example"></a>Exempel

Följande XML-filen definierar en listvy som visar en egen etikett på varje rad. I det här fallet innehåller etiketten egenskapsnamnet med varje versal bokstav och ordet ”property”. På varje rad visas namnet på egenskapen följt av värdet för egenskapen.

```xml
<Configuration>
  <ViewDefinitions>
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
            <Label>NAME property</Label>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <Label>DISPLAYNAME property</Label>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <Label>STATUS property</Label>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <Label>SERVICETYPE property</Label>
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

I följande exempel visas hur Windows PowerShell visar den [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objekt när den här formatfilen har lästs in.

```powershell
Get-Service f*
```

```output
NAME property        : Fax
DISPLAYNAME property : Fax
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FCSAM
DISPLAYNAME property : Microsoft Antimalware Service
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : fdPHost
DISPLAYNAME property : Function Discovery Provider Host
STATUS property      : Stopped
SERVICETYPE property : Win32ShareProcess

NAME property        : FDResPub
DISPLAYNAME property : Function Discovery Resource Publication
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache
DISPLAYNAME property : Windows Font Cache Service
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache3.0.0.0
DISPLAYNAME property : Windows Presentation Foundation Font Cache 3.0.0.0
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FSysAgent
DISPLAYNAME property : Microsoft Forefront System Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : FwcAgent
DISPLAYNAME property : Firewall Client Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess
```

## <a name="see-also"></a>Se även

[Exempel på formatering filer](./examples-of-formatting-files.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
