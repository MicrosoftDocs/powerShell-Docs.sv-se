---
title: Frame-element för CustomItem för CustomControl för vy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4864ea1a865f77c9de6e495d7e8296e81c19b366
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781451"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a>Frame-element för CustomItem för CustomControl för View (format)

Definierar hur data visas, till exempel att flytta data till vänster eller höger. Det här elementet används när du definierar en anpassad kontrol vy.

Konfigurations element (format) ViewDefinitions element (format) Visa element (format) CustomControl element (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) CustomItem-element för CustomEntry för CustomControlView (format) för CustomItem för CustomControl för View (format)

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
|[FirstLineHanging-element](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Anger hur många tecken den första raden med data flyttas till vänster.|
|[FirstLineIndent-element](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Anger hur många tecken den första raden med data flyttas till höger.|
|[LeftIndent-element](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Anger hur många tecken data flyttas bort från vänstermarginalen.|
|[RightIndent-element](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Anger hur många tecken data flyttas bort från högermarginalen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomItem-element för CustomEntry för vy (format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Definierar vilka data som visas av kontrollen och hur de visas.|

## <a name="remarks"></a>Kommentarer

Du kan inte ange [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) och [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) -elementen i samma `Frame` element.

## <a name="see-also"></a>Se även

[FirstLineHanging-element](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[FirstLineIndent-element](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[LeftIndent-element](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[RightIndent-element](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[CustomItem-element för CustomEntry för vy (format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
