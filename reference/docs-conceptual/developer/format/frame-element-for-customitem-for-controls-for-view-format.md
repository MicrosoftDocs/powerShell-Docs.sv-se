---
title: Ram element för CustomItem för kontroller för vy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5ade36c183a026cb9001a2abbe91d31638a87108
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773461"
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
