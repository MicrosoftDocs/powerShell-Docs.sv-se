---
ms.date: 09/13/2016
ms.topic: reference
title: CustomControl-element för View (format)
description: CustomControl-element för View (format)
ms.openlocfilehash: 41352be55f0c03b2eaca0dbe2d7345e7cf804a7c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655469"
---
# <a name="customcontrol-element-for-view-format"></a>CustomControl-element för View (format)

Definierar ett anpassat kontroll format för vyn.

Konfigurations element (format) ViewDefinitions element (format) Visa element (format) CustomControl-element (format)

## <a name="syntax"></a>Syntax

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `CustomControl` elementets överordnade element. Du måste ange ett underordnat element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntries-element för CustomControl för View (format)](./customentries-element-for-customcontrol-for-view-format.md)|Nödvändigt element.<br /><br /> Innehåller definitionerna för vyn anpassad kontroll.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[View-element (format)](./view-element-format.md)|Definierar en vy som används för att visa ett eller flera .NET-objekt.|

## <a name="remarks"></a>Kommentarer

I de flesta fall krävs bara en definition för varje kontroll, men det är möjligt att ange flera definitioner om du vill använda samma vy för att visa olika .NET-objekt. I dessa fall kan du ange en separat definition för varje objekt eller uppsättning objekt.

## <a name="see-also"></a>Se även

[CustomEntries-element för CustomControl för View (format)](./customentries-element-for-customcontrol-for-view-format.md)

[View-element (format)](./view-element-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
