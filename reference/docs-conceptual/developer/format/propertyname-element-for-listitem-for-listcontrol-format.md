---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName-element för ListItem för ListControl (format)
description: PropertyName-element för ListItem för ListControl (format)
ms.openlocfilehash: 30cd48f9549e1a091776cd5f8395e1a71314ea1b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92665982"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a>PropertyName-element för ListItem för ListControl (format)

Anger den .NET-egenskap vars värde visas i listan.

Konfigurations element (format) ViewDefinitions element (format) Visa element (format) ListControl-element (format) ListEntries-element (format) ListEntry-element (format) ListItems element (format) ListItem element (format) PropertyName-element för ListItem (format)

## <a name="syntax"></a>Syntax

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och `PropertyName` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ListItem-element (format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Definierar egenskapen eller skriptet vars värde visas i raden i listvyn.|

## <a name="text-value"></a>Textvärde

Ange namnet på den egenskap vars värde visas.

## <a name="remarks"></a>Kommentarer

När det här elementet har angetts kan du inte ange [script block](./scriptblock-element-for-listitem-for-listcontrol-format.md) -elementet.

Förutom att Visa egenskap svärdet kan du också ange en etikett för värdet eller en format sträng som kan användas för att ändra visningen av värdet. Mer information om hur du anger data i en listvy finns i [skapa en listvy](./creating-a-list-view.md).

## <a name="example"></a>Exempel

I följande exempel visas hur du anger den etikett och egenskap vars värde visas.

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a>Se även

[ScriptBlock-element för ListItem för ListControl (format)](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[Skapa en listvy](./creating-a-list-view.md)

[ListItem-element för ListControl (format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
