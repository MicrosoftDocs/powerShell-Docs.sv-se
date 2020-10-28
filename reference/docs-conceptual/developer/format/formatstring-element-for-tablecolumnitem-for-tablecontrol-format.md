---
ms.date: 09/13/2016
ms.topic: reference
title: FormatString-element för TableColumnItem för TableControl (format)
description: FormatString-element för TableColumnItem för TableControl (format)
ms.openlocfilehash: 3d386e61ac321c05e0b298019c2298f76b391b21
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667903"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a>FormatString-element för TableColumnItem för TableControl (format)

Anger ett format mönster som definierar hur tabellens egenskaps-eller skript värde visas.

Konfigurations element (format) ViewDefinitions element (format) Visa element (format) TableControl-element (format) TableRowEntries-element (format) TableRowEntry-element (format) TableColumnItems element (format) TableColumnItem element (format) FormatString-element för TableColumnItem (format)

## <a name="syntax"></a>Syntax

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `FormatString` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[TableColumnItem-element (format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|Definierar egenskapen eller skriptet vars värde visas i kolumnen på raden.|

## <a name="text-value"></a>Textvärde

Ange mönstret som används för att formatera data. Det här mönstret kan till exempel användas för att formatera värdet för en egenskap som är av typen [system. TimeSpan](/dotnet/api/System.TimeSpan): {0: MMM} {0: DD} {0: hh}: {0: mm}.

## <a name="remarks"></a>Kommentarer

Format strängar kan användas för att skapa tabellvyer, listvyer, breda vyer eller anpassade vyer. Mer information om hur du formaterar ett värde som visas i en vy finns i [Formatera data som visas](./formatting-displayed-data.md).

Mer information om komponenterna i en tabellvy finns i [tabellvy](./creating-a-table-view.md).

## <a name="example"></a>Exempel

I följande exempel visas hur du definierar en format sträng för `StartTime` egenskapens värde.

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a>Se även

[Skapa en tabellvy](./creating-a-table-view.md)

[Formatera data som visas](./formatting-displayed-data.md)

[TableColumnItem-element (format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
