---
title: Etikett element för TableColumnHeader för TableControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 09183a538c179f19347c3f1ed45b4ad38c2ca451
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356044"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a>Label-element för TableColumnHeader för TableControl (format)

Definierar etiketten som visas överst i en kolumn. Det här elementet används när du definierar en tabellvy.

Konfigurations element (format) ViewDefinitions element (format) View element (format) TableControl element (format) TableHeaders-element för TableControl (format) TableColumnHeader element för TableHeaders för TableControl (format) etikett element för TableColumnHeader för TableControl (format)

## <a name="syntax"></a>Syntax

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet för elementet `Label`. Endast en etikett tillåts för varje kolumn.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[TableColumnHeader-element för TableHeaders för TableControl (format)](./tablecolumnheader-element-format.md)|Definierar en etikett, bredd och justering för data i en kolumn i tabellen.|

## <a name="text-value"></a>Text värde

Ange texten som visas överst i kolumnen i tabellen. Det finns inga begränsade tecken för kolumn etiketten.

## <a name="remarks"></a>Anmärkningar

Om ingen etikett anges används namnet på den egenskap vars värde visas i raderna.

Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).

## <a name="example"></a>Exempel

Det här exemplet visar ett `TableColumnHeader`-element vars etikett är "kolumn 1".

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>Se även

[Skapa en tabellvy](./creating-a-table-view.md)

[TableColumnHeader-element (format)](./tablecolumnheader-element-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
