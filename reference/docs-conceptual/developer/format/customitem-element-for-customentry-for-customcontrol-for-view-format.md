---
ms.date: 09/13/2016
ms.topic: reference
title: CustomItem-element för CustomEntry för CustomControl för View (format)
description: CustomItem-element för CustomEntry för CustomControl för View (format)
ms.openlocfilehash: 9090a3ada5316ba5ddb4a9c46eee37c11982ae6e
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666747"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a>CustomItem-element för CustomEntry för CustomControl för View (format)

Definierar vilka data som visas i vyn anpassad kontroll och hur den visas. Det här elementet används när du definierar en anpassad kontrol vy.

Konfigurations element (format) ViewDefinitions element (format) View element (format) CustomControl element (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) CustomItem-element för CustomEntry för View (format)

## <a name="syntax"></a>Syntax

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och `CustomItem` elementets överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[ExpressionBinding-element för CustomItem för CustomControl för View (format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Definierar de data som visas av kontrollen.|
|[Frame-element för CustomItem för CustomControl för View (format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Definierar vilka data som visas i vyn anpassad kontroll och hur den visas.|
|[Rad matnings element för CustomItem för anpassad kontroll för vy (format)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|Valfritt element.<br /><br /> Lägger till en tom rad i visningen av kontrollen.|
|[Text element för CustomItem för CustomControl för vy (format)](./text-element-for-customitem-for-customview-for-view-format.md)|Valfritt element.<br /><br /> Anger ytterligare text för de data som visas i kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntry-element för CustomEntries för CustomControl för View (format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Innehåller en definition av den anpassade kontrollen.|

## <a name="remarks"></a>Kommentarer

## <a name="see-also"></a>Se även

[CustomEntry-element för CustomEntries för vy (format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[ExpressionBinding-element för CustomItem för CustomControl för View (format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[Frame-element för CustomItem för CustomControl för View (format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[NewLine-element för CustomItem för CustomControl för View (format)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[Text element för CustomItem för CustomControl för vy (format)](./text-element-for-customitem-for-customview-for-view-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
