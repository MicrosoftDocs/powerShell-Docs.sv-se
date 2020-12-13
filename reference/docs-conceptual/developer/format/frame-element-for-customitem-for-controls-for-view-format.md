---
ms.date: 09/13/2016
ms.topic: reference
title: Frame-element för CustomItem för Controls för View (format)
description: Frame-element för CustomItem för Controls för View (format)
ms.openlocfilehash: 6f26e19a6894ac213b924108a56cb80f9ffd1143
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652204"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a>Frame-element för CustomItem för Controls för View (format)

Definierar hur data visas, till exempel att flytta data till vänster eller höger. Det här elementet används när du definierar kontroller som kan användas av en vy.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) kontroll element (format) styr element (format) för kontroll element för View (format) CustomControl-element för kontroll för Control for View (format) CustomEntries element för CustomControl for View (format) CustomEntry-elementet för CustomEntries for Controls for View (format) CustomItem-elementet for CustomEntry for Controls for View (format) Frame element for CustomItem for Controls for View (format)

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
|[FirstLineHanging-element för kontroll bild av vyer (format)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger hur många tecken den första raden flyttas till vänster.|
|[FirstLineIndent-element för kontroll bild av vyer (format)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger hur många tecken den första raden flyttas till höger.|
|[LeftIndent-element för kontroll bild av vyer (format)](./leftindent-element-for-frame-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger hur många tecken data flyttas bort från vänstermarginalen.|
|[RightIndent-element för kontroll bild av vyer (format)](./rightindent-element-for-frame-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger hur många tecken data flyttas bort från högermarginalen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomItem-element för CustomEntry för Controls för View (format)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Definierar vilka data som visas av kontrollen och hur de visas.|

## <a name="remarks"></a>Kommentarer

Du kan inte ange [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) och [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) -elementen i samma `Frame` element.

## <a name="see-also"></a>Se även

[FirstLineHanging-element för kontroll bild av vyer (format)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[FirstLineIndent-element för kontroll bild av vyer (format)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[LeftIndent-element för kontroll bild av vyer (format)](./leftindent-element-for-frame-for-controls-for-view-format.md)

[RightIndent-element för kontroll bild av vyer (format)](./rightindent-element-for-frame-for-controls-for-view-format.md)

[CustomItem-element för CustomEntry för Controls för View (format)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
