---
title: WideControl Element (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849492"
---
# <a name="widecontrol-element-format"></a>WideControl-element (format)

Definierar en bred (enstaka värde) listformat för vyn. Den här vyn visar ett enda egenskapsvärdet eller skriptvärde för varje objekt.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) WideControl konfigurationselement (Format)

## <a name="syntax"></a>Syntax

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs de attribut och underordnade element överordnade elementet i den `WideControl` element. Du kan inte ange den `AutoSize` och `ColumnNumber` element på samma gång.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[AutoSize-Element för WideControl (Format)](./autosize-element-for-widecontrol-format.md)|Valfritt element.<br /><br /> Anger om kolumnstorlek och antalet kolumner justeras beroende på storleken på data.|
|[Antal_kolumner anger Element för WideControl (Format)](./columnnumber-element-for-widecontrol-format.md)|Valfritt element.<br /><br /> Anger antalet kolumner som visas i bred vy.|
|[WideEntries Element (Format)](./wideentries-element-for-widecontrol-format.md)|Element som krävs.<br /><br /> Innehåller definitioner av bred vy.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Visa Element (Format)](./view-element-format.md)|Definierar en vy som används för att visa en eller flera .NET-objekt.|

## <a name="remarks"></a>Anmärkningar

När du definierar en bred vy, kan du lägga till den `AutoSize` element eller `ColumnNumber` men du kan inte lägga till båda.

Endast en definition som krävs för varje bred vy i de flesta fall, men det är möjligt att ha flera definitioner om du vill använda samma vy för att visa olika .NET-objekt. I sådana fall kan ange du en definition av separat för varje objekt eller en uppsättning objekt.

Mer information om komponenter för en bred vy finns i [bred vy komponenter](./creating-a-wide-view.md).

## <a name="example"></a>Exempel

I följande exempel visas en `WideControl` element som används för att visa en egenskap för den [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objekt.

```xml
<View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>...</WideEntries>
  </WideControl>
</View>
```

Exempel på en bred vy, se [bred vy (grundläggande)](./wide-view-basic.md).

## <a name="see-also"></a>Se även

[AutoSize-Element för WideControl (Format)](./autosize-element-for-widecontrol-format.md)

[Antal_kolumner anger Element för WideControl (Format)](./columnnumber-element-for-widecontrol-format.md)

[Visa Element (Format)](./view-element-format.md)

[WideEntries Element (Format)](./wideentries-element-for-widecontrol-format.md)

[Bred vy (grundläggande)](./wide-view-basic.md)

[Skapa en bred vy](./creating-a-wide-view.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
