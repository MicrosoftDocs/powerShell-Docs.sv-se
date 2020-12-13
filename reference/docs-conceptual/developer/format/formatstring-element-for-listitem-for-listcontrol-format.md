---
ms.date: 09/13/2016
ms.topic: reference
title: FormatString-element för ListItem för ListControl  (format)
description: FormatString-element för ListItem för ListControl  (format)
ms.openlocfilehash: 1c16da92928ea632241942f4f2c63390c4fea706
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667920"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a>FormatString-element för ListItem för ListControl  (format)

Anger ett format mönster som definierar hur egenskapen eller skriptets värde visas.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) ListEntries-element för ListControl (format) ListEntry-element för ListControl (format) ListItems-element för ListControl (format) ListItem-element för ListControl (format) FormatString-element för ListItem (format)

## <a name="syntax"></a>Syntax

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och `FormatString` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

Inga.

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ListItem-element (format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Definierar egenskapen eller skriptet vars värde visas i en rad i list visningen.|

## <a name="text-value"></a>Textvärde

Ange mönstret som används för att formatera data. Du kan till exempel använda det här mönstret för att formatera värdet för alla egenskaper som är av typen [system. TimeSpan](/dotnet/api/System.TimeSpan): {0: MMM} {0: DD} {0: hh}: {0: mm}.

## <a name="remarks"></a>Kommentarer

Format strängar kan användas för att skapa tabellvyer, listvyer, breda vyer eller anpassade vyer. Mer information om hur du formaterar ett värde som visas i en vy finns i [Formatera data som visas](./formatting-displayed-data.md).

Mer information om hur du använder format strängar i listvyer finns i [skapa listvy](./creating-a-list-view.md).

## <a name="example"></a>Exempel

I följande exempel visas hur du definierar en format sträng för `StartTime` egenskapens värde.

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a>Se även

[Skapa en listvy](./creating-a-list-view.md)

[ListItem-element (format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Skriva en Windows PowerShell-formatering och en typ fil](./writing-a-powershell-formatting-file.md)
