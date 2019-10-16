---
title: CustomItem-element för CustomEntry för kontroll av konfiguration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355246"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a>CustomItem-element för CustomEntry för Controls för Configuration (format)

Definierar vilka data som visas av kontrollen och hur de visas. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

Konfigurations element (format) styr element i konfigurations-(format) kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för konfiguration ( Format) CustomEntry-element för CustomControl for Controls for Configuration (format) CustomItem-element för CustomEntry för kontroller för konfiguration

## <a name="syntax"></a>Syntax

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `CustomItem`. Mer information finns i kommentarer.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ExpressionBinding-element för CustomItem för kontroller för konfiguration (format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Definierar de data som visas av kontrollen.|
|[Ram element för CustomItem för kontroll av konfiguration (format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Definierar hur data visas, till exempel att flytta data till vänster eller höger.|
|[Rad matnings element för CustomItem för kontroll av konfiguration (format)](./newline-element-for-customitem-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Lägger till en tom rad i visningen av kontrollen.|
|[Text element för CustomItem för konfigurations kontroller (format)](./text-element-for-customitem-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Lägger till text, till exempel parenteser eller hakparenteser, för att Visa kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntry-element för CustomControl för kontroller för konfiguration (format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Ger en definition av kontrollen.|

## <a name="remarks"></a>Anmärkningar

Tänk på följande när du anger underordnade element i `CustomItem`-elementet:

- De underordnade elementen måste läggas till i följande ordning: `ExpressionBinding`, `NewLine`, `Text` och `Frame`.

- Det finns ingen övre gräns för antalet sekvenser som du kan ange.

- I varje sekvens finns det ingen övre gräns för antalet `ExpressionBinding`-element som du kan använda.

## <a name="see-also"></a>Se även

[ExpressionBinding-element för CustomItem för kontroller för konfiguration (format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Ram element för CustomItem för kontroll av konfiguration (format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[Rad matnings element för CustomItem för kontroll av konfiguration (format)](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[Text element för CustomItem för konfigurations kontroller (format)](./text-element-for-customitem-for-controls-for-configuration-format.md)

[Skriva en fil med PowerShell-formatering](./writing-a-powershell-formatting-file.md)
