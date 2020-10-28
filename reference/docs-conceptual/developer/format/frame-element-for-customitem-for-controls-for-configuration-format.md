---
ms.date: 09/13/2016
ms.topic: reference
title: Frame-element för CustomItem för Controls för Configuration (format)
description: Frame-element för CustomItem för Controls för Configuration (format)
ms.openlocfilehash: 85d095b9b0c25b68b2353bce56b85333aff91b98
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92652243"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a>Frame-element för CustomItem för Controls för Configuration (format)

Definierar hur data visas, till exempel att flytta data till vänster eller höger. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för Configuration (format) CustomEntry-element för CustomControl för Controls (format) CustomItem-element för CustomEntry för Controls (format) för konfigurations ram element för CustomItem.

## <a name="syntax"></a>Syntax

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `Frame` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|`CustomItem Element`|Nödvändigt element|
|[FirstLineHanging-element för Frame för Controls för Configuration (format)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger hur många tecken den första raden med data flyttas till vänster.|
|[FirstLineIndent-element för Frame för Controls för Configuration (format)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger hur många tecken den första raden med data flyttas till höger.|
|[LeftIndent-element för Frame för Controls för Configuration (format)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger hur många tecken data flyttas bort från vänstermarginalen.|
|[RightIndent-element för Frame för Controls för Configuration (format)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger hur många tecken data flyttas bort från högermarginalen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomItem-element för CustomEntry för kontroller för konfiguration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Definierar vilka data som visas av kontrollen och hur de visas.|

## <a name="remarks"></a>Kommentarer

Du kan inte ange [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) och [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) -elementen i samma `Frame` element.

## <a name="see-also"></a>Se även

[FirstLineHanging-element för Frame för Controls för Configuration (format)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[FirstLineIndent-element för Frame för Controls för Configuration (format)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[LeftIndent-element för Frame för Controls för Configuration (format)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[RightIndent-element för Frame för Controls för Configuration (format)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[CustomItem-element för CustomEntry för kontroller för konfiguration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
