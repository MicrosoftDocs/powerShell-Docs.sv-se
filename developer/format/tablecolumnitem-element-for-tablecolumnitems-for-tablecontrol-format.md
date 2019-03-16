---
title: TableColumnItem Element för TableColumnItems för TableControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 159f943f6bfb33c5403b5714380631351523789f
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056999"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a>TableColumnItem-element för TableColumnItems för TableControl (format)

Definierar egenskapen eller skript som vars värde visas i kolumnen i raden.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableRowEntries konfigurationselement för TableControl (Format) TableRowEntry elementet för TableRowEntries för TableControl (Format) TableColumnItems Element för TableControlEntry för TableControl (Format) TableColumnItem elementet för TableColumnItems för TableControl (Format)

## <a name="syntax"></a>Syntax

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs de attribut och underordnade element överordnade elementet i den `TableColumnItem` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Justering Element för TableColumnItem för TableControl (Format)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|Valfritt element.<br /><br /> Definierar hur data i en kolumn i raden visas.|
|[FormatString-Element för TableColumnItem för TableControl (Format)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|Anger ett formatmönster som används för att formatera data i kolumnen i raden.|
|[PropertyName-Element för TableColumnItem för TableControl (Format)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|Valfritt element.<br /><br /> Anger namnet på egenskapen vars värde visas.|
|[ScriptBlock Element för TableColumnItem för TableControl (Format)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|Valfritt element.<br /><br /> Anger skriptet vars värde visas i kolumnen i en rad.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[TableColumnItems Element för TableControlEntry för TableControl (Format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|Definierar egenskaper eller skript som vars värden visas i raden.|

## <a name="remarks"></a>Anmärkningar

Du kan ange en egenskap för ett objekt eller ett skript i varje kolumn i raden. Om inga underordnade element anges objektet är en platshållare och inga data visas.

Läs mer om komponenterna i en tabellvy, [skapar en tabellvy](./creating-a-table-view.md).

## <a name="example"></a>Exempel

Det här exemplet visar en `TableColumnItem` element som visar värdet för den `Status` egenskapen för den [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objekt.

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a>Se även

[Skapa en tabellvy](./creating-a-table-view.md)

[Justering Element för TableColumnItem för TableControl (Format)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[TableColumnItems Element (Format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[FormatString-Element för TableColumnItem för TableControl (Format)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[PropertyName-Element för TableColumnItem för TableControl (Format)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[ScriptBlock Element för TableColumnItem för TableControl (Format)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
