---
ms.date: 09/13/2016
ms.topic: reference
title: CustomControl-element för Control för Controls för Configuration (format)
description: CustomControl-element för Control för Controls för Configuration (format)
ms.openlocfilehash: 631995c6a50c0f020cb2e991cfbf58a09a75cc72
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649999"
---
# <a name="customcontrol-element-for-control-for-controls-for-configuration-format"></a>CustomControl-element för Control för Controls för Configuration (format)

Definierar en kontroll. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för kontroll av CustomControl-element (format) för kontroll av konfiguration (format)

## <a name="syntax"></a>Syntax

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och `CustomControl` elementets överordnade element. Elementet måste ha minst ett underordnat element. Det finns ingen övre gräns för antalet underordnade element som kan anges.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntries-element för CustomControl för konfiguration (format)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|Nödvändigt element.<br /><br /> Tillhandahåller definitioner för en kontroll.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Control-element för Controls för Configuration (format)](./control-element-for-controls-for-configuration-format.md)|Definierar en gemensam kontroll som kan användas av alla vyer i format filen och det namn som används för att referera till kontrollen.|

## <a name="remarks"></a>Kommentarer

## <a name="see-also"></a>Se även

[Control-element för Controls för Configuration (format)](./control-element-for-controls-for-configuration-format.md)

[CustomEntries-element för CustomControl för konfiguration (format)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
