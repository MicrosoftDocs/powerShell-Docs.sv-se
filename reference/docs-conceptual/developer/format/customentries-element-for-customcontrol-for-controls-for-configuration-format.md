---
ms.date: 09/13/2016
ms.topic: reference
title: CustomEntries-element för CustomControl för Controls för Configuration (format)
description: CustomEntries-element för CustomControl för Controls för Configuration (format)
ms.openlocfilehash: 86c2b517d0d7075a355a3190a14e25d9dd4fe374
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655393"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a>CustomEntries-element för CustomControl för Controls för Configuration (format)

Innehåller definitionerna för en gemensam kontroll. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för konfiguration (format)

## <a name="syntax"></a>Syntax

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `CustomEntries` elementets överordnade element. Du måste ange ett eller flera underordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntry-element för CustomControl för Controls för Configuration (format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Ger en definition av den gemensamma kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomControl-element för kontroll av konfiguration (format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|Definierar en gemensam kontroll.|

## <a name="remarks"></a>Kommentarer

I de flesta fall har en kontroll bara en definition som definieras i ett enda `CustomEntry` element. Det är dock möjligt att ha flera definitioner om du vill använda samma kontroll för att visa olika .NET-objekt. I dessa fall kan du definiera ett- `CustomEntry` element för varje objekt eller uppsättning objekt.

## <a name="see-also"></a>Se även

[CustomControl-element för kontroll av konfiguration (format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[CustomEntry-element för CustomControl för Controls för Configuration (format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
