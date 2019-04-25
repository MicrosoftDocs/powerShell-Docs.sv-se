---
title: ListItems som finns Element för ListEntry för ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c1da6d-acc7-4fe8-9e7d-6dcddc2787cd
caps.latest.revision: 9
ms.openlocfilehash: c25f18489d9c7abd8889758499dbbacd6ee29304
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065248"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a>ListItems-element för ListEntry för ListControl (format)

Definierar egenskaperna och skript vars värden visas i raderna i listvyn.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ListControl Element (Format) ListEntries konfigurationselement för listan kontroll (Format) ListEntry elementet för ListControl (Format) ListItems som finns Element för ListControl (Format)

## <a name="syntax"></a>Syntax

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs de attribut och underordnade element överordnade elementet i den `ListItems` element. Det finns ingen gräns för antalet underordnade element som kan anges. Ordningen på de underordnade elementen definierar ordningen att värden visas i listvyn.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ListItem Element för ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Element som krävs.<br /><br /> Definierar egenskapen eller skript som vars värde visas i listvyn.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ListEntry Element för ListControl (Format)](./listentry-element-for-listcontrol-format.md)|Innehåller en definition av listvyn.|

## <a name="remarks"></a>Anmärkningar

Mer information om den här typen av vy finns i [skapar en listvy](./creating-a-list-view.md).

## <a name="example"></a>Exempel

Det här exemplet visar XML-element som definierar tre rader i listvyn.

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

[ListEntry Element för ListControl (Format)](./listentry-element-for-listcontrol-format.md)

[ListItem Element för ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Skapa en listvy](./creating-a-list-view.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
