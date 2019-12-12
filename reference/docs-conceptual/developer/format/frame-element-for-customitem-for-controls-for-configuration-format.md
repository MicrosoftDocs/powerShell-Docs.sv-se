---
title: Ram element för CustomItem för kontroll av konfiguration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354987"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a>Frame-element för CustomItem för Controls för Configuration (format)

Definierar hur data visas, till exempel att flytta data till vänster eller höger. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

Konfigurations element (format) styr element i konfigurations-(format) kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för konfiguration ( Format) CustomEntry-element för CustomControl for Controls for Configuration (format) CustomItem-element för CustomEntry för Controls för konfigurations ram element för CustomItem för kontroll av konfiguration (format)

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
|[FirstLineHanging-element för ram för kontroll av konfiguration (format)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger hur många tecken den första raden med data flyttas till vänster.|
|[FirstLineIndent-element för ram för kontroll av konfiguration (format)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger hur många tecken den första raden med data flyttas till höger.|
|[LeftIndent-element för ram för kontroll av konfiguration (format)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger hur många tecken data flyttas bort från vänstermarginalen.|
|[RightIndent-element för ram för kontroll av konfiguration (format)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Anger hur många tecken data flyttas bort från högermarginalen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomItem-element för CustomEntry för kontroller för konfiguration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Definierar vilka data som visas av kontrollen och hur de visas.|

## <a name="remarks"></a>Anmärkningar

Du kan inte ange [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) och [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) -elementen i samma `Frame`-element.

## <a name="see-also"></a>Se även

[FirstLineHanging-element för ram för kontroll av konfiguration (format)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[FirstLineIndent-element för ram för kontroll av konfiguration (format)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[LeftIndent-element för ram för kontroll av konfiguration (format)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[RightIndent-element för ram för kontroll av konfiguration (format)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[CustomItem-element för CustomEntry för kontroller för konfiguration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
