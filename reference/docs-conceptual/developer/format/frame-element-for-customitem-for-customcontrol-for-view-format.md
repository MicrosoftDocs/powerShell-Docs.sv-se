---
title: Frame-element för CustomItem för CustomControl för vy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: 925ef86e61801f5a66f89dd25e0756f00dd35155
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354973"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a>Frame-element för CustomItem för CustomControl för View (format)

Definierar hur data visas, till exempel att flytta data till vänster eller höger. Det här elementet används när du definierar en anpassad kontrol vy.

Konfigurations element (format) ViewDefinitions element (format) View element (format) CustomControl element (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) CustomItem-element för CustomEntry för CustomControlView (format) för CustomItem för CustomControl för vy (format)

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

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `Frame`-elementet.

### <a name="attributes"></a>Attribut

Ingen.

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

## <a name="remarks"></a>Anmärkningar

Du kan inte ange [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) och [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) -elementen i samma `Frame`-element.

## <a name="see-also"></a>Se även

[FirstLineHanging-element](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[FirstLineIndent-element](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[LeftIndent-element](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[RightIndent-element](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[CustomItem-element för CustomEntry för vy (format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
