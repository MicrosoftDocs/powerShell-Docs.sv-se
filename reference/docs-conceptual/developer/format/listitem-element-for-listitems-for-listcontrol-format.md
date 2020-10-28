---
ms.date: 09/13/2016
ms.topic: reference
title: ListItem-element för ListItems för ListControl (format)
description: ListItem-element för ListItems för ListControl (format)
ms.openlocfilehash: 999491b7851aa4fa21667ad376d7e9853500ca08
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666560"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a>ListItem-element för ListItems för ListControl (format)

Definierar egenskapen eller skriptet vars värde visas i en rad i list visningen.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) ListEntries-element för ListControl (format) ListEntry-element för ListControl (format) ListItems-element för ListControl (format) ListItem för ListControl-element (format)

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

I följande avsnitt beskrivs attributen, underordnade element och `ListItem` elementets överordnade element. Det går bara att ange en egenskap eller ett skript.

### <a name="attributes"></a>Attribut

Inget

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[FormatString-element för ListItem för ListControl (format)](./formatstring-element-for-listitem-for-listcontrol-format.md)|Valfritt element.<br /><br /> Anger en format sträng som definierar hur egenskapen eller skriptets värde visas.|
|[ItemSelectionCondition-element för ListItem för ListControl (format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|Valfritt element.<br /><br /> Definierar det villkor som måste finnas för att listobjektet ska kunna användas.|
|[Label-element för ListItem för ListControl (format)](./label-element-for-listitem-for-listcontrol-format.md)|Valfritt element<br /><br /> Anger etiketten som visas till vänster om egenskapen eller skriptets värde på raden.|
|[PropertyName-element för ListItem för ListControl (format)](./propertyname-element-for-listitem-for-listcontrol-format.md)|Valfritt element.<br /><br /> Anger den .NET-egenskap vars värde visas på raden.|
|[ScriptBlock-element för ListItem för ListControl (format)](./scriptblock-element-for-listitem-for-listcontrol-format.md)|Valfritt element.<br /><br /> Anger det skript vars värde visas i raden.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ListItems-element för List kontroll (format)](./listitems-element-for-listentry-for-listcontrol-format.md)|Definierar egenskaper och skript vars värden visas i listvyn.|

## <a name="remarks"></a>Kommentarer

Mer information om komponenterna i en listvy finns i [skapa en listvy](./creating-a-list-view.md).

## <a name="example"></a>Exempel

I det här exemplet visas de XML-element som definierar tre rader i listvyn. De två första raderna visar värdet för en .NET-egenskap och den sista raden visar ett värde som skapats av ett skript.

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

[ListItems-element (format)](./listitems-element-for-listentry-for-listcontrol-format.md)

[FormatString-element för ListItem (format)](./formatstring-element-for-listitem-for-listcontrol-format.md)

[Etikett element för ListItem (format)](./label-element-for-listitem-for-listcontrol-format.md)

[PropertyName-element för ListItem (format)](./propertyname-element-for-listitem-for-listcontrol-format.md)

[Script block-element för ListItem (format)](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[Skapa en listvy](./creating-a-list-view.md)

[Skriva en Windows PowerShell-formatering och en typ fil](./writing-a-powershell-formatting-file.md)
