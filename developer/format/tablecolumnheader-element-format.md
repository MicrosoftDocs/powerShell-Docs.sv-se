---
title: TableColumnHeader Element (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: d3ad7fa563def17d43ce4dc64d155b65b650521f
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057883"
---
# <a name="tablecolumnheader-element-format"></a>TableColumnHeader-element (format)

Definierar etiketten, bredden på kolumnen och justering för etiketten för en kolumn i tabellen.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableHeaders konfigurationselement för TableControl (Format) TableColumnHeader elementet för TableHeaders för TableControl (Format)

## <a name="syntax"></a>Syntax

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `TableColumnHeader` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Etikettelement för TableColumnHeader för TableControl (Format)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|Valfritt element.<br /><br /> Definierar den etikett som visas överst i kolumnen. Om ingen etikett har angetts används namnet på egenskapen vars värde visas på raderna.|
|[Bredd-Element för TableColumnHeader för TableControl (Format)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|Element som krävs.<br /><br /> Anger bredden (i antal tecken) för kolumnen.|
|[Justering Element för TableColumnHeader för TableControl (Format)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|Valfritt element.<br /><br /> Anger hur kolumnen etiketten ska visas. Om ingen justering anges justeras etiketten till vänster.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[TableHeaders Element (Format)](./tableheaders-element-format.md)|Definierar kolumner i en tabellvy.|

## <a name="remarks"></a>Anmärkningar

Ange en rubrik för varje kolumn i tabellen. Kolumnerna i ordningen som de `TableColumnHeader` element har definierats.

En tabell måste ha samma antal `TableColumnHeader` element som `TableRowEntry` element. Kolumnrubriken definierar hur texten längst upp i tabellen visas. Rad posterna definierar vilka data som visas i raderna i tabellen.

Läs mer om komponenterna i en tabellvy, [tabellvy](./creating-a-table-view.md).

## <a name="example"></a>Exempel

I följande exempel visas två `TableColumnHeader` element. Det första elementet definierar en kolumn vars etikett är ”kolumn 1”, har en bredd på 16 tecken och vars etikett har justerats till vänster. Det andra elementet definierar en kolumn vars etikett är ”kolumn 2”, bredd är 10 tecken och vars etikett centreras i kolumnen.

```xml
<TableHeaders>
  <TableColumnHeader>
    <Label>Column 1</Label)
    <Width>16</Width>
    <Alignment>Left</Alignment>
  </TableColumnHeader>
    <TableColumnHeader>
    <Label>Column 2</Label)
    <Width>10</Width>
    <Alignment>Centered</Alignment>
  </TableColumnHeader>
</TableHeaders>
```

## <a name="see-also"></a>Se även

[Justering Element för TableColumnHeader för TableControl (Format)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Skapa en tabellvy](./creating-a-table-view.md)

[Etikettelement för TableColumnHeader för TableControl (Format)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[TableHeaders Element för TableControl (Format)](./tableheaders-element-format.md)

[Bredden för TableColumnHeader för TableControl elementet (Format)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
