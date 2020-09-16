---
title: FormatString-element för TableColumnItem för TableControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 848583e697d0ab7bd5b017c14c47aba3c51a3c17
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781553"
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
