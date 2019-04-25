---
title: CustomItem Element för CustomEntry för kontroller för konfiguration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066438"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a>CustomItem-element för CustomEntry för Controls för Configuration (format)

Definierar vilka data som visas av kontrollen och hur de visas. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.

Konfigurationselementet Element (Format) kontroller av (Format) kontroll konfigurationselement för kontroller för (Format) anpassad kontroll konfigurationselement för kontroll för (Format) CustomEntries konfigurationselement för anpassad kontroll för konfiguration ( Format) CustomEntry Element för anpassad kontroll för kontroller för (Format) CustomItem konfigurationselement för CustomEntry för kontroller för konfiguration

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

I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `CustomItem` element. Mer information finns i kommentarer.

### <a name="attributes"></a>Attribut

Ingen.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ExpressionBinding Element för CustomItem för kontroller för konfiguration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Definierar de data som visas i kontrollen.|
|[Ramens Element för CustomItem för kontroller för konfiguration (Format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Definierar hur data visas, till exempel ändra datatypen till vänster eller höger.|
|[Ny rad-Element för CustomItem för kontroller för konfiguration (Format)](./newline-element-for-customitem-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Lägger till en tom rad visningen av kontrollen.|
|[Textelement för CustomItem för kontroller för konfiguration (Format)](./text-element-for-customitem-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Lägger till text, till exempel parenteser eller hakparenteser, visning av kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntry Element för anpassad kontroll för kontroller för konfiguration (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Innehåller en definition av kontrollen.|

## <a name="remarks"></a>Anmärkningar

När du anger de underordnade elementen i den `CustomItem` element, Tänk på följande:

- De underordnade elementen måste läggas till i följande ordning: `ExpressionBinding`, `NewLine`, `Text`, och `Frame`.

- Det finns ingen högsta gräns för antalet sekvenser som du kan ange.

- Det finns ingen högsta gräns för antalet i varje sekvens `ExpressionBinding` element som du kan använda.

## <a name="see-also"></a>Se även

[ExpressionBinding Element för CustomItem för kontroller för konfiguration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Ramens Element för CustomItem för kontroller för konfiguration (Format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[Ny rad-Element för CustomItem för kontroller för konfiguration (Format)](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[Textelement för CustomItem för kontroller för konfiguration (Format)](./text-element-for-customitem-for-controls-for-configuration-format.md)

[Skriva ett PowerShell formatering fil](./writing-a-powershell-formatting-file.md)
