---
ms.date: 09/13/2016
ms.topic: reference
title: CustomEntries-element för CustomControl för Controls för View (format)
description: CustomEntries-element för CustomControl för Controls för View (format)
ms.openlocfilehash: 43187294a407d08f765f8c42aba25d13dba6d901
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652375"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a>CustomEntries-element för CustomControl för Controls för View (format)

Innehåller definitionerna för kontrollen. Det här elementet används när du definierar kontroller som kan användas av en vy.

Konfigurations element (format) ViewDefinitions element (format) Visa element (format) styr element (format) kontroll element (format) styr element (format) kontroll element för Controls för View (format) CustomControl-element för kontroll för kontroller för View (format) CustomEntries-element för CustomControl för kontroller (format)

## <a name="syntax"></a>Syntax

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `CustomEntries` elementets överordnade element. Det finns ingen övre gräns för antalet underordnade element som kan anges.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntry-element för CustomEntries för Controls för View (format)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Nödvändigt element.<br /><br /> Ger en definition av kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomControl-element för Control för Controls för View (format)](./customcontrol-element-for-control-for-controls-for-view-format.md)|Definierar den kontroll som används i vyn.|

## <a name="remarks"></a>Kommentarer

I de flesta fall har en kontroll bara en definition som anges i ett enda `CustomEntry` element. Det är dock möjligt att tillhandahålla flera definitioner om du vill använda samma kontroll för att visa olika .NET-objekt. I dessa fall kan du definiera ett- `CustomEntry` element för varje objekt eller uppsättning objekt.

## <a name="see-also"></a>Se även

[CustomEntry-element för CustomEntries för Controls för View (format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[CustomControl-element för Control för Controls för View (format)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
