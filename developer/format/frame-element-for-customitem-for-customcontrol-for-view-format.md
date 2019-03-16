---
title: RAM-Element för CustomItem för anpassad kontroll för vy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: 925ef86e61801f5a66f89dd25e0756f00dd35155
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054789"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a>Frame-element för CustomItem för CustomControl för View (format)

Definierar hur data visas, till exempel ändra datatypen till vänster eller höger. Det här elementet används när du definierar en anpassad kontroll vy.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) anpassad kontroll Element (Format) CustomEntries konfigurationselement för anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för vyn (Format) CustomItem elementet för CustomEntry för CustomControlView (Format) RAM-elementet för CustomItem för anpassad kontroll för vy (Format)

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

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `Frame` element.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|`CustomItem Element`|Element som krävs|
|[FirstLineHanging Element](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Anger hur många tecken som den första raden av data ska flyttas till vänster.|
|[FirstLineIndent Element](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Anger hur många tecken som den första raden av data ska flyttas till höger.|
|[LeftIndent Element](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Anger hur många tecken som data ska flyttas från vänster marginal.|
|[RightIndent Element](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Anger hur många tecken som data ska flyttas från höger marginal.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomItem Element för CustomEntry för vy (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Definierar vilka data som visas av kontrollen och hur de visas.|

## <a name="remarks"></a>Anmärkningar

Du kan inte ange den [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) och [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) element i samma `Frame` element.

## <a name="see-also"></a>Se även

[FirstLineHanging Element](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[FirstLineIndent Element](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[LeftIndent Element](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[RightIndent Element](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[CustomItem Element för CustomEntry för vy (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
