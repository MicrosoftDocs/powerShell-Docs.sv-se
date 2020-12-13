---
ms.date: 09/13/2016
ms.topic: reference
title: Control-element för Controls för Configuration (format)
description: Control-element för Controls för Configuration (format)
ms.openlocfilehash: 43424de025cb89d81533e973abd7c39c09533747
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655660"
---
# <a name="control-element-for-controls-for-configuration-format"></a>Control-element för Controls för Configuration (format)

Definierar en gemensam kontroll som kan användas av alla vyer i format filen och det namn som används för att referera till kontrollen.

Konfigurations element (format) styr element i konfigurations-(format) kontroll element för konfigurations inställningar (format)

## <a name="syntax"></a>Syntax

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attributen, underordnade element och `Control` elementets överordnade element. Du måste ange ett av varje underordnat element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomControl-element för Control för Controls för Configuration (format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|Nödvändigt element.<br /><br /> Definierar kontrollen.|
|[Namn element för kontroll av konfiguration (format)](./name-element-for-control-for-controls-for-configuration-format.md)|Nödvändigt element.<br /><br /> Anger det namn som ska användas för att referera till kontrollen.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[Kontrollerar konfigurations element (format)](./controls-element-for-configuration-format.md)|Definierar de vanliga kontroller som kan användas av alla vyer i formaterings filen eller av andra kontroller.|

## <a name="remarks"></a>Kommentarer

Det namn som ges till den här kontrollen kan refereras till i följande element:

- [ExpressionBinding-element för CustomItem (format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [GroupBy-element för vy (format)](./groupby-element-for-view-format.md)

## <a name="see-also"></a>Se även

[Kontrollerar konfigurations element (format)](./controls-element-for-configuration-format.md)

[CustomControl-element för kontroll av konfiguration (format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[ExpressionBinding-element för CustomItem (format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[GroupBy-element för vy (format)](./groupby-element-for-view-format.md)

[Name-element för Control för Controls för Configuration (format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
