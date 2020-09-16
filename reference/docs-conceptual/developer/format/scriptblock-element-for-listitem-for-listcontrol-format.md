---
title: Script block-element för ListItem för ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 249d3e36b4246b7baa410815122f8e30340f1862
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785463"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a>ScriptBlock-element för ListItem för ListControl (format)

Anger det skript vars värde visas i raden.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) ListEntries-element för ListControl (format) ListEntry-element för ListEntries för ListControl (format) ListItems element for ListEntry for ListControl (format) ListItem element for ListItems for ListControl (format) script block element for ListItem for ListControl for (format)

## <a name="syntax"></a>Syntax

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och `ScriptBlock` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ListItem-element (format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Definierar egenskapen eller skriptet vars värde visas i en rad i list visningen.|

## <a name="text-value"></a>Textvärde

Ange det skript vars värde visas på raden.

## <a name="remarks"></a>Kommentarer

När det här elementet har angetts kan du inte ange elementet [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) .

Mer information om hur du anger skript i listvyn finns i [listvyn](./creating-a-list-view.md).

## <a name="example"></a>Exempel

I följande exempel visas hur du anger den egenskap vars värde visas.

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a>Se även

[PropertyName-element för ListItem för ListControl (format)](./propertyname-element-for-listitem-for-listcontrol-format.md)

[Skapa en listvy](./creating-a-list-view.md)

[ListItem-element för ListItems för ListControl (format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
