---
title: FormatString-Element för TableColumnItem för TableControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a150731-d4b4-4d63-8db5-f14d463c8c37
caps.latest.revision: 13
ms.openlocfilehash: b7e1d0adc43254141056a729e1c1cc9699b6ac9b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065645"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a>FormatString-element för TableColumnItem för TableControl (format)

Anger ett formatmönster som definierar hur värdet för egenskapen eller ett skript för tabellen visas.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem konfigurationselement (Format) FormatString-Element för TableColumnItem (Format)

## <a name="syntax"></a>Syntax

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `FormatString` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[TableColumnItem Element (Format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|Definierar egenskapen eller skript som vars värde visas i kolumnen i raden.|

## <a name="text-value"></a>Textvärde

Ange mönstret som används för att formatera data. Det här mönstret kan till exempel användas för att formatera värdet för en egenskap som är av typen [System.Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {0:HH}: {0:mm}.

## <a name="remarks"></a>Anmärkningar

Formatsträngar kan användas när du skapar tabellvyer, listvyer, brett vyer eller anpassade vyer. Mer information om hur du formaterar ett värde som visas i en vy finns i [formatering visas Data](./formatting-displayed-data.md).

Läs mer om komponenterna i en tabellvy, [tabellvy](./creating-a-table-view.md).

## <a name="example"></a>Exempel

I följande exempel visas hur du definierar en formateringssträngen för värdet för den `StartTime` egenskapen.

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a>Se även

[Skapa en tabellvy](./creating-a-table-view.md)

[Formatering visas Data](./formatting-displayed-data.md)

[TableColumnItem Element (Format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
