---
ms.date: 09/13/2016
ms.topic: reference
title: FormatString-element för WideItem för WideControl (format)
description: FormatString-element för WideItem för WideControl (format)
ms.openlocfilehash: f67a18e3ec4f1323e7f9be8904db518c679d53e5
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667886"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a>FormatString-element för WideItem för WideControl (format)

Anger ett format mönster som definierar hur egenskapen eller skriptets värde visas i vyn.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) WideEntries-element (format) WideEntry-element för WideControl (format) WideItem-element för WideControl (format) FormatString-element för WideItem för WideControl (format)

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
|[WideItem-element för WideControl (format)](./wideitem-element-for-widecontrol-format.md)|Definierar egenskapen eller skriptet vars värde visas i en rad i list visningen.|

## <a name="text-value"></a>Textvärde

Ange mönstret som används för att formatera data. Du kan till exempel använda det här mönstret för att formatera värdet för alla egenskaper som är av typen [system. TimeSpan](/dotnet/api/System.TimeSpan): {0: MMM} {0: DD} {0: hh}: {0: mm}.

## <a name="remarks"></a>Kommentarer

Format strängar kan användas för att skapa tabellvyer, listvyer, breda vyer eller anpassade vyer. Mer information om hur du formaterar ett värde som visas i en vy finns i [Formatera data som visas](./formatting-displayed-data.md).

Mer information om hur du använder format strängar i breda vyer finns i [skapa en bred vy](./creating-a-wide-view.md).

## <a name="example"></a>Exempel

I följande exempel visas hur du definierar en format sträng för `StartTime` egenskapens värde.

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a>Se även

[Skapa en bred vy](./creating-a-wide-view.md)

[WideItem-element för WideControl (format)](./wideitem-element-for-widecontrol-format.md)

[Skriva en Windows PowerShell-formatering och en typ fil](./writing-a-powershell-formatting-file.md)
