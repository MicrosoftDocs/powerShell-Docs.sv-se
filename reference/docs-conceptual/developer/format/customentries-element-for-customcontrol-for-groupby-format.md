---
title: CustomEntries-element för CustomControl for GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2221d1bb94159697ff10466e4606d6d54e117e30
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785956"
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
