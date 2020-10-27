---
ms.date: 09/13/2016
ms.topic: reference
title: CustomEntries-element för CustomControl för View (format)
description: CustomEntries-element för CustomControl för View (format)
ms.openlocfilehash: 6e757bccdface2503667f8786462a2b43134a07d
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92649974"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a>CustomEntries-element för CustomControl för View (format)

Innehåller definitionerna för vyn anpassad kontroll. Vyn anpassad kontroll måste ange en eller flera definitioner.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) CustomControl-element (format) element (format) CustomEntries-element för CustomControl för vy (format)

## <a name="syntax"></a>Syntax

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `CustomControlEntries` elementets överordnade element. Du måste ange ett eller flera underordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntry-element för CustomEntries för vy (format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Nödvändigt element.<br /><br /> Innehåller en definition av den anpassade kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomControl-element för View (format)](./customcontrol-element-for-view-format.md)|Nödvändigt element.<br /><br /> Definierar ett anpassat kontroll format för vyn.|

## <a name="remarks"></a>Kommentarer

I de flesta fall har en kontroll bara en definition som definieras i ett enda `CustomEntry` element. Det är dock möjligt att ha flera definitioner om du vill använda samma kontroll för att visa olika .NET-objekt. I dessa fall kan du definiera ett- `CustomEntry` element för varje objekt eller uppsättning objekt.

## <a name="see-also"></a>Se även

[CustomControl-element för View (format)](./customcontrol-element-for-view-format.md)

[CustomEntry-element för CustomEntries för vy (format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
