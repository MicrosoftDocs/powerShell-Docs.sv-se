---
title: ListItem-element för ListItems för ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356016"
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

I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `ListItem`-elementet. Det går bara att ange en egenskap eller ett skript.

### <a name="attributes"></a>Attribut

Inga

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[FormatString-element för ListItem för ListControl (format)](./formatstring-element-for-listitem-for-listcontrol-format.md)|Valfritt element.<br /><br /> Anger en format sträng som definierar hur egenskapen eller skriptets värde visas.|
|[ItemSelectionCondition-element för ListItem för ListControl (format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|Valfritt element.<br /><br /> Definierar det villkor som måste finnas för att listobjektet ska kunna användas.|
|[Etikett element för ListItem för ListControl (format)](./label-element-for-listitem-for-listcontrol-format.md)|Valfritt element<br /><br /> Anger etiketten som visas till vänster om egenskapen eller skriptets värde på raden.|
|[PropertyName-element för ListItem för ListControl (format)](./propertyname-element-for-listitem-for-listcontrol-format.md)|Valfritt element.<br /><br /> Anger den .NET-egenskap vars värde visas på raden.|
|[Script block-element för ListItem för ListControl (format)](./scriptblock-element-for-listitem-for-listcontrol-format.md)|Valfritt element.<br /><br /> Anger det skript vars värde visas i raden.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ListItems-element för List kontroll (format)](./listitems-element-for-listentry-for-listcontrol-format.md)|Definierar egenskaper och skript vars värden visas i listvyn.|

## <a name="remarks"></a>Anmärkningar

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
