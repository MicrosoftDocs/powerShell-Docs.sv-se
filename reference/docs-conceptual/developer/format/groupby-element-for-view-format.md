---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy-element för View (format)
description: GroupBy-element för View (format)
ms.openlocfilehash: d8ca93a3b2c1490928885579919c07f5eb274cd8
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92652099"
---
# <a name="groupby-element-for-view-format"></a>GroupBy-element för View (format)

Definierar hur en ny grupp av objekt visas. Det här elementet används när du definierar en tabell, en lista, en bred eller en anpassad vy.

Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för vy (format)

## <a name="syntax"></a>Syntax

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a>Attribut och element

I följande avsnitt beskrivs attribut, underordnade element och överordnade element.

### <a name="attributes"></a>Attribut

Inga.

### <a name="child-elements"></a>Underordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[CustomControl-element för GroupBy (format)](./customcontrol-element-for-groupby-format.md)|Valfritt element.<br /><br /> Definierar den anpassade kontrollen som visar nya grupper.|
|[CustomControlName-element för GroupBy (format)](./customcontrolname-element-for-groupby-format.md)|Valfritt element.<br /><br /> Anger namnet på en kontroll som används för att visa den nya gruppen.|
|[Label-element för GroupBy (format)](./label-element-for-groupby-format.md)|Valfritt element.<br /><br /> Anger en etikett som visas när en ny grupp påträffas.|
|[PropertyName-element för GroupBy (format)](./propertyname-element-for-groupby-format.md)|Valfritt element.<br /><br /> Anger .NET-egenskapen som startar en ny grupp när dess värde ändras.|
|[ScriptBlock-element för GroupBy (format)](./scriptblock-element-for-groupby-format.md)|Valfritt element.<br /><br /> Anger det skript som startar en ny grupp när dess värde ändras.|

### <a name="parent-elements"></a>Överordnade element

|Element|Beskrivning|
|-------------|-----------------|
|[View-element (format)](./view-element-format.md)|Definierar en vy som visar ett eller flera .NET-objekt.|

## <a name="remarks"></a>Kommentarer

När du definierar hur en ny grupp av objekt visas måste du ange den egenskap eller det skript som ska starta den nya gruppen. Du kan dock inte ange båda.

## <a name="see-also"></a>Se även

[CustomControlName-element för GroupBy (format)](./customcontrolname-element-for-groupby-format.md)

[Label-element för GroupBy (format)](./label-element-for-groupby-format.md)

[PropertyName-element för GroupBy (format)](./propertyname-element-for-groupby-format.md)

[ScriptBlock-element för GroupBy (format)](./scriptblock-element-for-groupby-format.md)

[View-element (format)](./view-element-format.md)

[Skriva en PowerShell-formateringsfil](./writing-a-powershell-formatting-file.md)
