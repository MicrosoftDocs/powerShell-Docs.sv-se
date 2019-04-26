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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083747"
---
# <a name="wide-view-basic"></a>Bred vy (grundläggande)

Det här exemplet visar hur du implementerar en grundläggande bred vy som visar den [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objekten som returneras av den `Get-Service` cmdlet. Mer information om komponenter för en bred vy finns i [skapar en bred vy](./creating-a-wide-view.md).

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

- Den [WideItem](./wideitem-element-for-widecontrol-format.md) element som definierar vilka egenskapen visas i vyn.

## <a name="example"></a>Exempel

Följande XML-filen definierar en bred vy som visar värdet för den [System.Serviceprocess.Servicecontroller.Servicename](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) egenskapen.

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

I följande exempel visas hur Windows PowerShell visar den [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objekt när den här formatfilen har lästs in.

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

[Exempel på formatering filer](./examples-of-formatting-files.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
