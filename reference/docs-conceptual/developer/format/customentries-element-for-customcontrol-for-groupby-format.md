---
ms.date: 09/13/2016
ms.topic: reference
title: CustomEntries-element för CustomControl för GroupBy (format)
description: CustomEntries-element för CustomControl för GroupBy (format)
ms.openlocfilehash: cde59d38b83930cb64a3a0040891783e4ab96723
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666798"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a>CustomEntries-element för CustomControl för GroupBy (format)

Innehåller definitionerna för kontrollen. Det här elementet används när du definierar hur en ny grupp av objekt visas.

Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl för GroupBy (format)

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
|[CustomEntry-element för CustomControl för GroupBy (format)](./customentry-element-for-customcontrol-for-groupby-format.md)|Nödvändigt element.<br /><br /> Ger en definition av kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomControl-element för GroupBy (format)](./customcontrol-element-for-groupby-format.md)|Definierar den anpassade kontrollen som visar den nya gruppen.|

## <a name="remarks"></a>Kommentarer

I de flesta fall har en kontroll bara en definition som anges i ett enda `CustomEntry` element. Det är dock möjligt att tillhandahålla flera definitioner om du vill använda samma kontroll för att visa olika grupper. I dessa fall kan du definiera ett- `CustomEntry` element för en grupp.

## <a name="see-also"></a>Se även

[CustomEntry-element för CustomEntries för Controls för View (format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[CustomControl-element för GroupBy (format)](./customcontrol-element-for-groupby-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
