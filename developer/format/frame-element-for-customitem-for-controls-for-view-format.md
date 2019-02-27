---
title: RAM-Element för CustomItem för kontroller för vy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849485"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a>Frame-element för CustomItem för Controls för View (format)

Definierar hur data visas, till exempel ändra datatypen till vänster eller höger. Det här elementet används när du definierar kontroller som kan användas av en vy.

Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) kontroller Element (Format) kontroll konfigurationselement för kontroller för att visa (Format) anpassad kontroll Element för kontroll för kontroller för att visa (Format) CustomEntries Element för Anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för kontroller för att visa (Format) CustomItem Element för CustomEntry för kontroller för att visa (Format) RAM-Element för CustomItem för kontroller för att visa (Format)

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
|[FirstLineHanging Element av bildruta från kontrollerna för Visa (Format)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger hur många tecken som den första raden ska flyttas till vänster.|
|[FirstLineIndent Element av bildruta från kontrollerna för Visa (Format)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger hur många tecken som den första raden ska flyttas till höger.|
|[LeftIndent Element av bildruta från kontrollerna för Visa (Format)](./leftindent-element-for-frame-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger hur många tecken som data ska flyttas från vänster marginal.|
|[RightIndent Element av bildruta från kontrollerna för Visa (Format)](./rightindent-element-for-frame-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Anger hur många tecken som data ska flyttas från höger marginal.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomItem Element för CustomEntry för kontroller för att visa (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Definierar vilka data som visas av kontrollen och hur de visas.|

## <a name="remarks"></a>Anmärkningar

Du kan inte ange den [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) och [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) element i samma `Frame` element.

## <a name="see-also"></a>Se även

[FirstLineHanging Element av bildruta från kontrollerna för Visa (Format)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[FirstLineIndent Element av bildruta från kontrollerna för Visa (Format)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[LeftIndent Element av bildruta från kontrollerna för Visa (Format)](./leftindent-element-for-frame-for-controls-for-view-format.md)

[RightIndent Element av bildruta från kontrollerna för Visa (Format)](./rightindent-element-for-frame-for-controls-for-view-format.md)

[CustomItem Element för CustomEntry för kontroller för att visa (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
