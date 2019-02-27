---
title: ListItem Element för ListItems som finns för ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846223"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a>ListItem-element för ListItems för ListControl (format)

Definierar egenskapen eller skript som vars värde visas i en rad i listvyn.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ListControl Element (Format) ListEntries konfigurationselement för ListControl (Format) ListEntry elementet för ListControl (Format) ListItems som finns Element för ListControl (Format) ListItem för ListControl elementet (Format)

## <a name="syntax"></a>Syntax

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs de attribut och underordnade element överordnade elementet i den `ListItem` element. Endast en egenskap eller skript kan anges.

### <a name="attributes"></a>Attribut

Inga

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[FormatString-Element för ListItem för ListControl (Format)](./formatstring-element-for-listitem-for-listcontrol-format.md)|Valfritt element.<br /><br /> Anger en formatsträng som definierar hur värdet för egenskapen eller ett skript ska visas.|
|[ItemSelectionCondition Element för ListItem för ListControl (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|Valfritt element.<br /><br /> Definierar de villkor som måste finnas för det här objektet i listan som ska användas.|
|[Etikettelement för ListItem för ListControl (Format)](./label-element-for-listitem-for-listcontrol-format.md)|Valfritt element<br /><br /> Anger etiketten som visas till vänster om värdet för egenskapen eller skript på raden.|
|[PropertyName-Element för ListItem för ListControl (Format)](./propertyname-element-for-listitem-for-listcontrol-format.md)|Valfritt element.<br /><br /> Anger egenskapen .NET vars värde visas i raden.|
|[ScriptBlock Element för ListItem för ListControl (Format)](./scriptblock-element-for-listitem-for-listcontrol-format.md)|Valfritt element.<br /><br /> Anger skriptet vars värde visas i raden.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ListItems som finns Element för listkontroll (Format)](./listitems-element-for-listentry-for-listcontrol-format.md)|Definierar egenskaperna och skript vars värden visas i listvyn.|

## <a name="remarks"></a>Anmärkningar

Läs mer om komponenterna i en listvy, [skapar en listvy](./creating-a-list-view.md).

## <a name="example"></a>Exempel

Det här exemplet visar XML-element som definierar tre rader i listvyn. De två första raderna visa värdet för en egenskap för .NET och den sista raden visar ett värde av ett skript.

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>DotNetProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>DotNetProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
    </ListItems>
</ListEntry>

```

## <a name="see-also"></a>Se även

[ListItems som finns Element (Format)](./listitems-element-for-listentry-for-listcontrol-format.md)

[FormatString-Element för ListItem (Format)](./formatstring-element-for-listitem-for-listcontrol-format.md)

[Etikettelement för ListItem (Format)](./label-element-for-listitem-for-listcontrol-format.md)

[PropertyName-Element för ListItem (Format)](./propertyname-element-for-listitem-for-listcontrol-format.md)

[ScriptBlock Element för ListItem (Format)](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[Skapa en listvy](./creating-a-list-view.md)

[Skriva ett Windows PowerShell formatering och skriver fil](./writing-a-powershell-formatting-file.md)
