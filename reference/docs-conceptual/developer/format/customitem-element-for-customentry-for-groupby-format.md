---
ms.date: 09/13/2016
ms.topic: reference
title: CustomItem-element för CustomEntry för GroupBy (format)
description: CustomItem-element för CustomEntry för GroupBy (format)
ms.openlocfilehash: 5db23ad4dad5bd66ea64b9c6e91b8224a4aa4eca
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645990"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a>CustomItem-element för CustomEntry för GroupBy (format)

Definierar vilka data som visas i vyn anpassad kontroll och hur den visas. Det här elementet används när du definierar hur en ny grupp av objekt visas.

Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for groupby (format) CustomItem-element för CustomEntry för GroupBy (format)

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
|[ExpressionBinding-element för CustomItem för GroupBy (format)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Valfritt element.<br /><br /> Definierar de data som visas av kontrollen.|
|[Frame-element för CustomItem för GroupBy (format)](./frame-element-for-customitem-for-groupby-format.md)|Valfritt element.<br /><br /> Definierar vilka data som visas i vyn anpassad kontroll och hur den visas.|
|[NewLine-element för CustomItem för GroupBy (format)](./newline-element-for-customitem-for-groupby-format.md)|Valfritt element.<br /><br /> Lägger till en tom rad i visningen av kontrollen.|
|[Text-element för CustomItem för GroupBy (format)](./text-element-for-customitem-for-groupby-format.md)|Valfritt element.<br /><br /> Anger ytterligare text för de data som visas i kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomEntry-element för CustomControl för GroupBy (format)](./customentry-element-for-customcontrol-for-groupby-format.md)|Innehåller en definition av den anpassade kontrollen.|

## <a name="remarks"></a>Kommentarer

## <a name="see-also"></a>Se även

[CustomEntry-element för CustomControl för GroupBy (format)](./customentry-element-for-customcontrol-for-groupby-format.md)

[ExpressionBinding-element för CustomItem för GroupBy (format)](./expressionbinding-element-for-customitem-for-groupby-format.md)

[Frame-element för CustomItem för GroupBy (format)](./frame-element-for-customitem-for-groupby-format.md)

[NewLine-element för CustomItem för GroupBy (format)](./newline-element-for-customitem-for-groupby-format.md)

[Text-element för CustomItem för GroupBy (format)](./text-element-for-customitem-for-groupby-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
