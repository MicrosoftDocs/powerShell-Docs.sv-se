---
ms.date: 09/13/2016
ms.topic: reference
title: CustomItem-element för CustomEntry för Controls för Configuration (format)
description: CustomItem-element för CustomEntry för Controls för Configuration (format)
ms.openlocfilehash: 06c399e982b6ac0fba9c11e20c468fe8bef6f694
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666781"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a>CustomItem-element för CustomEntry för Controls för Configuration (format)

Definierar vilka data som visas av kontrollen och hur de visas. Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.

Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för Configuration (format) CustomEntry-element för CustomControl för Controls (format) CustomItem-element för CustomEntry för kontroller för konfiguration

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

I följande avsnitt beskrivs attribut, underordnade element och `CustomItem` elementets överordnade element. Mer information finns i kommentarer.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ExpressionBinding-element för CustomItem för Controls för Configuration (format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Definierar de data som visas av kontrollen.|
|[Frame-element för CustomItem för Controls för Configuration (format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Definierar hur data visas, till exempel att flytta data till vänster eller höger.|
|[NewLine-element för CustomItem för Controls för Configuration (format)](./newline-element-for-customitem-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Lägger till en tom rad i visningen av kontrollen.|
|[Text-element för CustomItem för Controls för Configuration (format)](./text-element-for-customitem-for-controls-for-configuration-format.md)|Valfritt element.<br /><br /> Lägger till text, till exempel parenteser eller hakparenteser, för att Visa kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntry-element för CustomControl för Controls för Configuration (format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Ger en definition av kontrollen.|

## <a name="remarks"></a>Kommentarer

`CustomItem`Tänk på följande när du anger elementets underordnade element:

- De underordnade elementen måste läggas till i följande ordning: `ExpressionBinding` , `NewLine` , `Text` och `Frame` .

- Det finns ingen övre gräns för antalet sekvenser som du kan ange.

- I varje sekvens finns det ingen övre gräns för antalet `ExpressionBinding` element som du kan använda.

## <a name="see-also"></a>Se även

[ExpressionBinding-element för CustomItem för Controls för Configuration (format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Frame-element för CustomItem för Controls för Configuration (format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[NewLine-element för CustomItem för Controls för Configuration (format)](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[Text-element för CustomItem för Controls för Configuration (format)](./text-element-for-customitem-for-controls-for-configuration-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
