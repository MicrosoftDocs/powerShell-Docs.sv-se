---
title: Ram element för CustomItem för kontroller för vy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354980"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a>Frame-element för CustomItem för Controls för View (format)

Definierar hur data visas, till exempel att flytta data till vänster eller höger. Det här elementet används när du definierar kontroller som kan användas av en vy.

Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) styr element för Controls (format) CustomControl-element för kontroll för Control for View (format) CustomEntries-element för CustomControl för visnings-(format) CustomEntry-element för CustomEntries för Controls for View (format) CustomItem-elementet for CustomEntry for Controls for View (format) Frame element for CustomItem for Controls for View (format)

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

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `Frame`.

### <a name="attributes"></a>Attribut

Ingen.

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
|[CustomItem-element för CustomEntry för kontroller för vy (format)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Definierar vilka data som visas av kontrollen och hur de visas.|

## <a name="remarks"></a>Anmärkningar

Du kan inte ange [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) och [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) -elementen i samma `Frame`-element.

## <a name="see-also"></a>Se även

[FirstLineHanging-element för kontroll bild av vyer (format)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[FirstLineIndent-element för kontroll bild av vyer (format)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[LeftIndent-element för kontroll bild av vyer (format)](./leftindent-element-for-frame-for-controls-for-view-format.md)

[RightIndent-element för kontroll bild av vyer (format)](./rightindent-element-for-frame-for-controls-for-view-format.md)

[CustomItem-element för CustomEntry för kontroller för vy (format)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
