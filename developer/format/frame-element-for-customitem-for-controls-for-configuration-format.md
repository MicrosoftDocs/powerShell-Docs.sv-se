---
title: RAM-Element för CustomItem för kontroller för konfiguration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065571"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a>Frame-element för CustomItem för Controls för Configuration (format)

Definierar hur data visas, till exempel ändra datatypen till vänster eller höger. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

Konfigurationselementet Element (Format) kontroller av (Format) kontroll konfigurationselement för kontroller för (Format) anpassad kontroll konfigurationselement för kontroll för (Format) CustomEntries konfigurationselement för anpassad kontroll för konfiguration ( Format) CustomEntry Element för anpassad kontroll för kontroller för (Format) CustomItem konfigurationselement för CustomEntry för kontroller för ramens konfigurationselement för CustomItem för kontroller för konfiguration (Format)

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
|[FirstLineHanging Element för ramens för kontroller för konfiguration (Format)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger hur många tecken som den första raden av data ska flyttas till vänster.|
|[FirstLineIndent Element för ramens för kontroller för konfiguration (Format)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger hur många tecken som den första raden av data ska flyttas till höger.|
|[LeftIndent Element för ramens för kontroller för konfiguration (Format)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger hur många tecken som data ska flyttas från vänster marginal.|
|[RightIndent Element för ramens för kontroller för konfiguration (Format)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger hur många tecken som data ska flyttas från höger marginal.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomItem Element för CustomEntry för kontroller för konfiguration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Definierar vilka data som visas av kontrollen och hur de visas.|

## <a name="remarks"></a>Anmärkningar

Du kan inte ange den [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) och [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) element i samma `Frame` element.

## <a name="see-also"></a>Se även

[FirstLineHanging Element för ramens för kontroller för konfiguration (Format)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[FirstLineIndent Element för ramens för kontroller för konfiguration (Format)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[LeftIndent Element för ramens för kontroller för konfiguration (Format)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[RightIndent Element för ramens för kontroller för konfiguration (Format)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[CustomItem Element för CustomEntry för kontroller för konfiguration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
