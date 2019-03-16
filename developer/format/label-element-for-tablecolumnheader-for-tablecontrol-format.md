---
title: Etikettera Element för TableColumnHeader för TableControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 09183a538c179f19347c3f1ed45b4ad38c2ca451
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054517"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a>Label-element för TableColumnHeader för TableControl (format)

Definierar den etikett som visas överst i en kolumn. Det här elementet används när du definierar en tabellvy.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableHeaders konfigurationselement för TableControl (Format) TableColumnHeader elementet för TableHeaders för TableControl (Format) etikett elementet för TableColumnHeader för TableControl (Format)

## <a name="syntax"></a>Syntax

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `Label` element. Endast en etikett är tillåten för varje kolumn.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

Ingen.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[TableColumnHeader Element för TableHeaders för TableControl (Format)](./tablecolumnheader-element-format.md)|Definierar en etikett, bredd och justering av data för en kolumn i tabellen.|

## <a name="text-value"></a>Textvärde

Ange vilken text som visas överst i kolumnen i tabellen. Det finns inga specialtecken för kolumnetiketten.

## <a name="remarks"></a>Anmärkningar

Om ingen etikett har angetts används namnet på egenskapen vars värde visas på raderna.

Läs mer om komponenterna i en tabellvy, [skapar en tabellvy](./creating-a-table-view.md).

## <a name="example"></a>Exempel

Det här exemplet visar en `TableColumnHeader` element vars etikett är ”kolumn 1”.

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>Se även

[Skapa en tabellvy](./creating-a-table-view.md)

[TableColumnHeader Element (Format)](./tablecolumnheader-element-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
