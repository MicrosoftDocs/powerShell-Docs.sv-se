---
title: FormatString-element för TableColumnItem för TableControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a150731-d4b4-4d63-8db5-f14d463c8c37
caps.latest.revision: 13
ms.openlocfilehash: b7e1d0adc43254141056a729e1c1cc9699b6ac9b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355022"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a>FormatString-element för TableColumnItem för TableControl (format)

Anger ett format mönster som definierar hur tabellens egenskaps-eller skript värde visas.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) TableControl-element (format) TableRowEntries-element (format) TableRowEntry-element (format) TableColumnItems element (format) TableColumnItem-element (format) FormatString-element för TableColumnItem (format)

## <a name="syntax"></a>Syntax

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `FormatString`.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[TableColumnItem-element (format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|Definierar egenskapen eller skriptet vars värde visas i kolumnen på raden.|

## <a name="text-value"></a>Text värde

Ange mönstret som används för att formatera data. Det här mönstret kan till exempel användas för att formatera värdet för en egenskap som är av typen [system. TimeSpan](/dotnet/api/System.TimeSpan): {0: MMM} {0: DD} {0: hh}: {0: mm}.

## <a name="remarks"></a>Anmärkningar

Format strängar kan användas för att skapa tabellvyer, listvyer, breda vyer eller anpassade vyer. Mer information om hur du formaterar ett värde som visas i en vy finns i [Formatera data som visas](./formatting-displayed-data.md).

Mer information om komponenterna i en tabellvy finns i [tabellvy](./creating-a-table-view.md).

## <a name="example"></a>Exempel

I följande exempel visas hur du definierar en format sträng för värdet för egenskapen `StartTime`.

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

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
