---
title: ListItems-element för ListEntry för ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c1da6d-acc7-4fe8-9e7d-6dcddc2787cd
caps.latest.revision: 9
ms.openlocfilehash: c25f18489d9c7abd8889758499dbbacd6ee29304
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354343"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a>ListItems-element för ListEntry för ListControl (format)

Definierar de egenskaper och skript vars värden visas i raderna i listvyn.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl element (format) element för List kontroll (format) ListEntry-element för ListControl (format) ListItems-element för ListControl (format)

## <a name="syntax"></a>Syntax

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `ListItems`-elementet. Det finns ingen gräns för antalet underordnade element som kan anges. Ordningen på underordnade element definierar i vilken ordning värdena visas i listvyn.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ListItem-element för ListControl (format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Nödvändigt element.<br /><br /> Definierar egenskapen eller skriptet vars värde visas i list visningen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ListEntry-element för ListControl (format)](./listentry-element-for-listcontrol-format.md)|Ger en definition av listvyn.|

## <a name="remarks"></a>Anmärkningar

Mer information om den här typen av vy finns i [skapa en listvy](./creating-a-list-view.md).

## <a name="example"></a>Exempel

I det här exemplet visas de XML-element som definierar tre rader i listvyn.

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>.NetTypeProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>.NetTypeProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
  </ListEntry>
```

## <a name="see-also"></a>Se även

[ListEntry-element för ListControl (format)](./listentry-element-for-listcontrol-format.md)

[ListItem-element för ListControl (format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Skapa en listvy](./creating-a-list-view.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
