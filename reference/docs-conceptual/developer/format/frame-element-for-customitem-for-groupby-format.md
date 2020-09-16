---
title: Ram element för CustomItem for GroupBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1568236ff7b6142f7e41be70a3ae5e28307cf790
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785769"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a>Frame-element för CustomItem för GroupBy (format)

Definierar hur data visas, till exempel att flytta data till vänster eller höger. Det här elementet används när du definierar hur en ny grupp av objekt visas.

Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för visnings-(format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry element for CustomControl for groupby (format) CustomItem-element för CustomEntry

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
|[FirstLineHanging-element för Frame för GroupBy (format)](./firstlinehanging-element-for-frame-for-groupby-format.md)|Valfritt element.<br /><br /> Anger hur många tecken den första raden med data flyttas till vänster.|
|[FirstLineIndent-element för Frame för GroupBy (format)](./firstlineindent-element-for-frame-for-groupby-format.md)|Valfritt element.<br /><br /> Anger hur många tecken den första raden med data flyttas till höger.|
|[LeftIndent-element för Frame för GroupBy (format)](./leftindent-element-for-frame-for-groupby-format.md)|Valfritt element.<br /><br /> Anger hur många tecken data flyttas bort från vänstermarginalen.|
|[RightIndent-element för inramad groupby (format)](./rightindent-element-for-frame-for-groupby-format.md) RightIndent-element|Valfritt element.<br /><br /> Anger hur många tecken data flyttas bort från högermarginalen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomItem-element för CustomEntry för GroupBy (format)](./customitem-element-for-customentry-for-groupby-format.md)|Definierar vilka data som visas av kontrollen och hur de visas.|

## <a name="remarks"></a>Kommentarer

Du kan inte ange [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) och [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) -elementen i samma `Frame` element.

## <a name="see-also"></a>Se även

[FirstLineHanging-element för Frame för GroupBy (format)](./firstlinehanging-element-for-frame-for-groupby-format.md)

[FirstLineIndent-element för Frame för GroupBy (format)](./firstlineindent-element-for-frame-for-groupby-format.md)

[LeftIndent-element för Frame för GroupBy (format)](./leftindent-element-for-frame-for-groupby-format.md)

[RightIndent-element för Frame för GroupBy (format)](./rightindent-element-for-frame-for-groupby-format.md)

[CustomItem-element för CustomEntry för GroupBy (format)](./customitem-element-for-customentry-for-groupby-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
