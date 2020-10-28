---
ms.date: 09/13/2016
ms.topic: reference
title: CustomItem-element för CustomEntry för Controls för View (format)
description: CustomItem-element för CustomEntry för Controls för View (format)
ms.openlocfilehash: 67bff97c27cfedf046b17eea438efcd66ae2ee4a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666764"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a>CustomItem-element för CustomEntry för Controls för View (format)

Definierar vilka data som visas av kontrollen och hur de visas. Det här elementet används när du definierar kontroller som kan användas av en vy.

Konfigurations element (format) ViewDefinitions element (format) (format) styr element (format) styr element (format) kontroll element för Controls (format) CustomControl-element för Control for View (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för Controls (format) CustomItem-element för CustomEntry för Controls (format)

## <a name="syntax"></a>Syntax

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `CustomItem` elementets överordnade element. Mer information finns i kommentarer.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ExpressionBinding-element för CustomItem för Controls för View (format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Definierar de data som visas av kontrollen.|
|[Frame-element för CustomItem för Controls för View (format)](./frame-element-for-customitem-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Definierar hur data visas, till exempel att flytta data till vänster eller höger.|
|[NewLine-element för CustomItem för Controls för View (format)](./newline-element-for-customitem-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Lägger till en tom rad i visningen av kontrollen.|
|[Text-element för CustomItem för Controls för View (format)](./text-element-for-customitem-for-controls-for-view-format.md)|Valfritt element.<br /><br /> Lägger till text, till exempel parenteser eller hakparenteser, för att Visa kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntry-element för CustomEntries för Controls för View (format)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Ger en definition av kontrollen.|

## <a name="remarks"></a>Kommentarer

`CustomItem`Tänk på följande när du anger elementets underordnade element:

- De underordnade elementen måste läggas till i följande ordning: `ExpressionBinding` , `NewLine` , `Text` och `Frame` .

- Det finns ingen övre gräns för antalet sekvenser som du kan ange.

- I varje sekvens finns det ingen övre gräns för antalet `ExpressionBinding` element som du kan använda.

## <a name="see-also"></a>Se även

[ExpressionBinding-element för CustomItem för Controls för View (format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Frame-element för CustomItem för Controls för View (format)](./frame-element-for-customitem-for-controls-for-view-format.md)

[NewLine-element för CustomItem för Controls för View (format)](./newline-element-for-customitem-for-controls-for-view-format.md)

[Text-element för CustomItem för Controls för View (format)](./text-element-for-customitem-for-controls-for-view-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
