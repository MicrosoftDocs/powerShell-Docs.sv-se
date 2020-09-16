---
title: CustomControl-element för kontroll för konfiguration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5aacf824421dfce19f1f495fc0a95e766cdbaf8b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786092"
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
