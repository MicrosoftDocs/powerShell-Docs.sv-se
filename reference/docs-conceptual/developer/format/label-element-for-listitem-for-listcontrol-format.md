---
title: Etikett element för ListItem för ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ad80cc0478e7567b12d264ab661d843248ba48e1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783644"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a>Label-element för ListItem för ListControl (format)

Anger etiketten som visas till vänster om egenskapen eller skriptets värde på raden.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) ListEntries-element för ListControl (format) ListEntry-element för ListControl (format) ListItems för ListEntry för ListControl-element (format) ListItem element for ListItems for ListControl (format) ListItem-element för ListControl (format)

## <a name="syntax"></a>Syntax

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och `Label` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ListItem-element för ListItems för ListControl (format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Definierar egenskapen eller skriptet vars värde visas i en rad i list visningen.|

## <a name="text-value"></a>Textvärde

Ange etiketten som ska visas till vänster om egenskapen eller värdet för skriptet.

## <a name="remarks"></a>Kommentarer

Om en etikett inte anges visas namnet på egenskapen eller skriptet. Mer information om hur du använder etiketter i en listvy finns i [skapa en listvy](./creating-a-list-view.md).

## <a name="example"></a>Exempel

I följande exempel visas hur du lägger till en etikett till en rad.

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a>Se även

[Skapa en listvy](./creating-a-list-view.md)

[ListItem-element (format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
